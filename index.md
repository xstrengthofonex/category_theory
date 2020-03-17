Category
========

Category consists of objects and arrows that go between them.
An object can be drawn as circle or point and an arrow is an arrow.
The essence of category is composition.

If there is an arrow from A to B and another arrow from B to C, there
there must be an arrow that goes from A to C.

![alt category-diagram-1](https://docs.google.com/drawings/d/e/2PACX-1vTZ-DkeUq_PsBe1my9sI9H2dYCwF-YOxnQ-xm3bAfGsleIGUVImEMG2HRPX4CuLpuVE-uCcP19GJNhv/pub?w=697&amp;h=234)

Arrows as functions
-------------------

Think of an arrow as a function. 
You have a function f that takes an argument of type A and returns B.
You have another function g that takes a B and returns a C.
You can compose them by passing the result of g to f.
g o f can be read as g after f.
```python
from typing import TypeVar

A = TypeVar("A")
B = TypeVar("B")
C = TypeVar("C")

def f(a: A) -> B:
    pass

def g(b: B) -> C:
    pass

def g_after_f(a: A) -> C:
    return g(f(a)) 
```
A concrete example:

```python
def str_after_round(a: float) -> str:
    return str(round(a))
```

In Haskel double colons means "has a type of...".
```
f :: A -> B
g :: B -> C
```
Their composition is:
```
g . f
```

Properties of Composition
-------------------------

Composition is associative. If you have three morphism, f, g, and h, that can be
composed, you don't need parentheses to compose them.
```
f :: A -> B
g :: B -> C
h :: C -> D
h . (g . f) == (h . g) . f == h . g . f
```
For every object, there is an arrow which is a unit of composition. This arrow
loops back from the object to itself.
```
f . id A = f

id ::  a -> a
```

```python
from typing import TypeVar

T = TypeVar("T")

def identity(x: T) -> T:
    return x
```

Types and Functions
===================
