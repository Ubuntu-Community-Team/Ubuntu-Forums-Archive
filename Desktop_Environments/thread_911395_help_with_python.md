---
title: "help with python"
date: 2008-09-05
forum: Desktop Environments
---

### Post by prokaryot on 2008-09-05
Hi, I am trying to write some python script. But when I use shutil module I get this:

---------

Traceback (most recent call last):
  File "/home/dhalsim/workspace/pygame-deneme1/src/deneme-shutil.py", line 2, in <module>
    from shutil import *
  File "/usr/lib/python2.5/shutil.py", line 3, in <module>
    XXX The functions here don't copy the resource fork or other metadata on Mac.
AttributeError: 'module' object has no attribute 'copyfile'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.5/site-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.5/site-packages/apport/report.py", line 21, in <module>
    import fileutils
  File "/usr/lib/python2.5/site-packages/apport/fileutils.py", line 223, in <module>
    import unittest, tempfile, os, shutil, sys, time
  File "/usr/lib/python2.5/shutil.py", line 3, in <module>
    XXX The functions here don't copy the resource fork or other metadata on Mac.
AttributeError: 'module' object has no attribute 'copyfile'

Original exception was:
Traceback (most recent call last):
  File "/home/dhalsim/workspace/pygame-deneme1/src/deneme-shutil.py", line 2, in <module>
    from shutil import *
  File "/usr/lib/python2.5/shutil.py", line 3, in <module>
    XXX The functions here don't copy the resource fork or other metadata on Mac.
AttributeError: 'module' object has no attribute 'copyfile'

---------

I can work with other modules but if I import shutil, it gives this error. I try anything reinstall python python-dev... It is working on my friends computer but not in me.

which package should be reinstalled?

---

