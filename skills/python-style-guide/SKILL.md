---
name: python-style-guide
description: "Enforce Python code style: use uv, type hints, docstrings, and avoid print statements in production code."
license: MIT
metadata:
  author: wangxiaokangty
  version: "1.0.0"
---

# Python 代码风格规范

## 包管理
- 始终使用 `uv` 而不是 `pip`
- 依赖写入 `pyproject.toml`，不使用 `requirements.txt`

## 类型注解
- 所有函数参数和返回值都必须有类型注解
- 使用 `from __future__ import annotations` 支持前向引用

## 文档字符串
- 所有公开函数和类必须有 docstring
- 格式：Google style

## 代码规范
- 不在生产代码中使用 `print()`，改用 `logging`
- 使用 `ruff` 做 lint 和格式化
- 异常必须具体，不写裸 `except:`

## 示例

好的写法：
```python
from __future__ import annotations
import logging

logger = logging.getLogger(__name__)

def add(a: int, b: int) -> int:
    """将两个整数相加。

    Args:
        a: 第一个整数
        b: 第二个整数

    Returns:
        两数之和
    """
    return a + b
```

不好的写法：
```python
def add(a, b):
    print(f"adding {a} and {b}")
    return a + b
```
