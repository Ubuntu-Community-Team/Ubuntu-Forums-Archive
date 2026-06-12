---
title: "Quod Libet and Animated On-Screen Display plugin"
date: 2006-01-19
forum: General Help
---

### Post by malte on 2006-01-19
Have you tried installing the osd plugin in quodlibet? It does not work, printing a strange error message on quodlibet start:
```
Traceback (most recent call last):
  File "/usr/lib/quodlibet/quodlibet.zip/plugins.py", line 163, in rescan
  File "/home/malte/.quodlibet/plugins/animosd.py", line 13, in ?
    from parse import XMLFromPattern
ImportError: No module named parse
```
I think this is the cause of what it's talking about, line 13 of the file:
```
from parse import XMLFromPattern
```
Is it possible to fix this?

Thank you!

---

