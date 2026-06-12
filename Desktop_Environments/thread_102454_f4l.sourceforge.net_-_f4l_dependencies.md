---
title: "f4l.sourceforge.net - f4l dependencies"
date: 2005-12-12
forum: Desktop Environments
---

### Post by the_it on 2005-12-12
Hi! I'm trying to get f4l (flash 4 linux, though they're bound to change their name) to run okay on ubuntu.  Actually, I can install it and run it, and I'm not really expecting much of it yet since it has just started beta, but while I install the debs, it tries to look for things outside of our repositories (or doesn't directly recognize the dependencies).  In particular, a sudo dpkg -i f4l......deb does

```
dilnet@dlntbldr:~$ sudo dpkg -i f4l_0.2-1_i386.deb
Password:
Selecting previously deselected package f4l.
(Reading database ... 193328 files and directories currently installed.)
Unpacking f4l (from f4l_0.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of f4l:
 f4l depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libqt3c102-mt (>= 3:3.3.4-3); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libxrender1 (>= 1:0.9.0-2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing f4l (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 f4l
```

Like I said I can actually run the thing and I don't expect it to be functional just yet, nevertheless, can I satisfy the dependencies? I'm left with a package marked as broken.

---

