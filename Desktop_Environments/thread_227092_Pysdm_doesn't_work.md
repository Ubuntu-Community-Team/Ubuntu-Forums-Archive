---
title: "Pysdm doesn't work"
date: 2006-08-01
forum: Desktop Environments
---

### Post by sloboda on 2006-08-01
Hi!
I've installed pysdm on my ubuntu dapper, but it doesn't work.
Here is the output (I'm on a notebook):```
[sergej@ildeposito ~]$ sudo pysdm
Password:
Not suitable dev for hda
Not suitable dev for hda1
Not suitable dev for hda2
Not suitable dev for hda3
Not suitable dev for hda4
Not suitable dev for hda5
Not suitable dev for hda6
Not suitable dev for sda
Not suitable dev for sda1
Not suitable dev for sda2
Traceback (most recent call last):
  File "pysdm.py", line 457, in ?
    main()
  File "pysdm.py", line 452, in main
    main_window = Mainwindow()
  File "pysdm.py", line 47, in __init__
    SimpleGladeApp.__init__(self, path, root, domain, **kwargs)
  File "/usr/share/pysdm/SimpleGladeApp.py", line 108, in __init__
    self.new()
  File "pysdm.py", line 64, in new
    self.refresh_partitions(self, None)
  File "pysdm.py", line 219, in refresh_partitions
    if is_mountable(self.blocks[partition].dev):
AttributeError: Block instance has no attribute 'dev'
[sergej@ildeposito ~]$
```What's wrong??

Sergej

---

### Post by scantan on 2006-10-08
I'm experiencing the exact same problem.

Here's my PySDM output:

```
Not suitable dev for hda
Not suitable dev for hda1
Not suitable dev for hda2
Not suitable dev for hda4
Not suitable dev for hda5
Not suitable dev for hda6
Not suitable dev for hda7
Not suitable dev for hda8
Not suitable dev for hdb
Not suitable dev for hdb1
Not suitable dev for hdb2
Not suitable dev for hdb3
Not suitable dev for hdb5
Traceback (most recent call last):
  File "pysdm.py", line 457, in ?
    main()
  File "pysdm.py", line 452, in main
    main_window = Mainwindow()
  File "pysdm.py", line 47, in __init__
    SimpleGladeApp.__init__(self, path, root, domain, **kwargs)
  File "/usr/share/pysdm/SimpleGladeApp.py", line 108, in __init__
    self.new()
  File "pysdm.py", line 64, in new
    self.refresh_partitions(self, None)
  File "pysdm.py", line 219, in refresh_partitions
    if is_mountable(self.blocks[partition].dev):
AttributeError: Block instance has no attribute 'dev'
```

scantan

---

