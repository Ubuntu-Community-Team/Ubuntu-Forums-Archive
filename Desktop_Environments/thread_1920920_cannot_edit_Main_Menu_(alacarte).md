---
title: "cannot edit Main Menu (alacarte)"
date: 2012-02-05
forum: Desktop Environments
---

### Post by irishetalon007 on 2012-02-05
Recently, alacarte stopped working.

Can't Edit menus from either of the 3 methods:
terminal: alacarte
System-Preferences-Main Menu
(right click upper taskbar) Edit Menus

Here's the output I get when I type it in terminal:

> jordan@jordan-AOA150:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 20, in <module>
    import cgi, os
  File "/usr/lib/python2.6/cgi.py", line 49, in <module>
    import mimetools
  File "/usr/lib/python2.6/mimetools.py", line 6, in <module>
    import tempfile
  File "/usr/lib/python2.6/tempfile.py", line 34, in <module>
    from random import Random as _Random
  File "/usr/lib/python2.6/random.py", line 42, in <module>
    from __future__ import division
ImportError: cannot import name division

So, I tried deleting the line in random.py that says "from __future__ import division" and now I can edit menus. However, I have no idea why that line wouldn't let me open alacarte, or whether I'm hurting other computer functions by deleting that line.

Any ideas?

---

