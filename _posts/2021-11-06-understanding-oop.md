---
layout: post
title: "Object Oriented Programming in Python from Scratch"
---

The link below is a good explanation on Object Oriented Programming concepts in Python. Presented by Raymond Hettinger, a Python core developer and a brilliant teacher, the video goes over understanding the OOP code writing style that we came to know today from scratch.

[PyConEstonia 2020: 'Object Oriented Programming from scratch (four times)' by Raymond Hettinger](https://www.youtube.com/watch?v=8moWQ1561FY)

By starting from the absolute building blocks of the Python programming language in the first instance, he then iterates by adding more complexity to address the problems which arises from the previous.

This post documents the codes and explanations which I find useful for future reference.

## Understanding Namespace

Namespace is a collection of names and details of the objects referenced by the names.

Namespaces can be implemented several ways in Python. In this example, four different ways were demonstrated.

### Using dict()

```python
>>> d = dict()
>>> d['foo'] = 'bar'
>>> d['foo']
'bar'
```

### Using globals()

Whenever we declare a variable and assign a value to it, it is saved somewhere. This somewhere is in globals().

```python
>>> x = 10
>>> globals()['x']
10
>>> globals()['x'] = 11
>>> x
11
```

### Using SimpleNamespace

```python
>>> from types import SimpleNamespace
>>> ns = SimpleNamespace(x=99, y=100)
>>> ns
namespace(x=99, y=100)
>>> ns.x
99
>>> ns.y
100
```

### Emulating Dictionaries with Hash Table

Emulating how a dictionary work can be done by creating a hash table.

```python
>>> n = 8
>>> karr = [[] for i in range(n)]
>>> varr = [[] for i in range(n)]
>>> n
8
>>> karr
[[], [], [], [], [], [], [], []]
>>> varr
[[], [], [], [], [], [], [], []]
>>> key, value = 'foo', 'bar'
>>> i = hash(key) % n
>>> i
4
>>> karr[i].append(key)
>>> varr[i].append(value)
>>> karr
[[], [], [], [], ['foo'], [], [], []]
>>> varr
[[], [], [], [], ['bar'], [], [], []]
```