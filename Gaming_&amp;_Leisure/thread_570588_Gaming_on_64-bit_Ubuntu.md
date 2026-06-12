---
title: "Gaming on 64-bit Ubuntu"
date: 2007-10-08
forum: Gaming &amp; Leisure
---

### Post by Dark Aspect on 2007-10-08
Seems easy enough with [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") but how do I run epsxe160 and mupen64 with a 64-bit OS?With .mupen64 I get this error:

./mupen64: error while loading shared libraries: libSDL-1.2.so.0: wrong ELF class: ELFCLASS64

I was also wondering if there is not a zsnes compiled for 64-bit user because I can't find one.getlibs installed 32-bit zsnes but it won't come up after the installation.

---

### Post by SpoZen on 2007-10-08
I'm getting a similar error when i try to run a python based game called [Interstate Outlaws]("http://www.interstateoutlaws.com/"): 

```
Error: failed to load module "ioInit"
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.4/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.4/apport/__init__.py", line 1, in ?
    from apport.report import Report
  File "/var/lib/python-support/python2.4/apport/report.py", line 14, in ?
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.4/subprocess.py", line 376, in ?
    import select
ImportError: /usr/lib/python2.4/lib-dynload/select.so: wrong ELF class: ELFCLASS64

Original exception was:
Traceback (most recent call last):
  File "/home/martin/Desktop/Outlaws-0.1.1a-linux/Outlaws-0.1.1a/ioData/scripts/ioInit.py", line 4, in ?
    import socket
  File "/usr/lib/python2.4/socket.py", line 45, in ?
    import _socket
ImportError: /usr/lib/python2.4/lib-dynload/_socket.so: wrong ELF class: ELFCLASS64
ALERT: crystalspace.application.celstart:  Can't create behaviour 'ioInit' for entity 'ioInit'!

crystalspace.application.celstart:  Can't create behaviour 'ioInit' for entity 'ioInit'!

``` 

I didnt work at all before using getlibs on it. 
Im running 64 bit kubuntu feisty.

---

### Post by Sockerdrickan on 2007-10-08
Use pSX and do this
sudo apt-get install ia32-libs*

---

### Post by Dark Aspect on 2007-10-08
> **Tux0r said:**
> Use pSX and do this
sudo apt-get install ia32-libs*

Great thanks that helped a lot.zsnes and mupen64 work great now.

---

