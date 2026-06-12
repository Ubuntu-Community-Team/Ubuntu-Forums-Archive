---
title: "Errors with Pymol 1.3"
date: 2010-11-12
forum: Education &amp; Science
---

### Post by The Phoenix on 2010-11-12
I need pymol 1.3 for a research project however when I try to run it I get the following error:
[FONT="Fixedsys"]
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/pymol/__init__.py", line 433, in launch_gui
    sys.modules[self.invocation.options.gui].__init__(self,poll,skin)
TypeError: module.__init__() takes at most 2 arguments (3 given)[/FONT]

The pymol view window launches but the main GUI window does not. I installed it from source using their directions.(using setup.py + setup2.py) When I got this error I then tried installing using 'make install' but that add several errors and would not complete the installation. Can anyone help with this? I am fine with either installation, I just need one of them to work.

---

