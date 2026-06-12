---
title: "Using import with Stackless Python"
date: 2009-01-21
forum: General Help
---

### Post by ross9885 on 2009-01-21
Something strange has been happening:
  First, in the python 2.5.2 interpreter, ```
import pygame
``` fails after working fine since I first installed it, along with several other major python modules like gd and cairo. The standard python libs still worked, like math and sys. 
sys.path is
['', '/usr/local/lib/python25.zip', '/usr/local/lib/python2.5', '/usr/local/lib/python2.5/plat-linux2', '/usr/local/lib/python2.5/lib-tk', '/usr/local/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/local/share/crystalspace-1.9/bindings/python']
  According to Synaptic, all the appropriate packages are installed and there doesn't seem to be any missing files when I locate|grep around. The most recent "weird" thing I did relating to packages was to install the Stackless module from a tarball which changed my Python interpreter to:
Python 2.5.2 Stackless 3.1b3 060516 (release25-maint, Jan 20 2009, 11:46:41)
For the sake of troubleshooting, I would like to uninstall Stackless but I can't see any obvious way to do that. Any help would be much appreciated,
  Dan.

---

### Post by snova on 2009-01-21
Where did you install Stackless to? The default is /usr/local, if you didn't specify a prefix.

Chances are, the problem is that the installation of Stackless can't use the libraries for CPython.

Try starting the interpreter as **/usr/bin/python2.5**, and attempting that import again.

---

