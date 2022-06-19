# pydantic-regex

[![pypi](https://img.shields.io/pypi/v/pydantic-regex.svg)](https://pypi.org/pypi/pydantic-regex)
[![downloads](https://pepy.tech/badge/pydantic-regex/month)](https://pepy.tech/project/pydantic-regex)
[![versions](https://img.shields.io/pypi/pyversions/pydantic-regex.svg)](https://github.com/ohiliazov/pydantic-regex)
[![license](https://img.shields.io/github/license/ohiliazov/pydantic-regex.svg)](https://github.com/ohiliazov/pydantic-regex/blob/master/LICENSE)

Easily convert regular expressions to *pydantic* models! 

## Installation

Install using `pip install -U pydantic-regex`.

## A Simple Example

```python
from pydantic_regex import RegexBaseModel


class User(RegexBaseModel):
    __regex__ = (
        r"My name is (?P<first_name>\w+) (?P<last_name>\w+), "
        r"I'm (?P<age>\d+) years old."
    )
    first_name: str
    last_name: str
    age: int


user = User.parse_regex("My name is John Doe, I'm 30 years old.")
print(user)
# > first_name='John' last_name='Doe' age=30

print(user.first_name)
# > John
```
