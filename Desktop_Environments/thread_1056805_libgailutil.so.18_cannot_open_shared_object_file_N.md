---
title: "libgailutil.so.18: cannot open shared object file: No suck file or directory"
date: 2009-02-01
forum: Desktop Environments
---

### Post by Natovr on 2009-02-01
Hello,
I've had some problems lately after I installed a few language packages. First, I noticed Nautilus wouldn't open. I tried to open it in Terminal but Gnome's Terminal wouldn't open. So I edited one of the launchers in the panel to point to xterm. Starting gnome-terminal and nautilus gives this:

$ nautilus
nautilus: error while loading shared library: libgailutil.so.18: cannot open shared object file: No such file or directory

$ gnome-terminal
gnome-terminal: error while loading shared library: libgailutil.so.18: cannot open shared object file: No such file or directory

how do I get that library back? help would be much appreciated :D

---

### Post by Natovr on 2009-02-01
Bump

---

### Post by Natovr on 2009-02-01
I solved it.. I made a bad mistake :| I added the jaunty repo to install OpenOffice 3
I re-installed Ubuntu swiftly after realizing what I've done.. it was the easiest way at the time o_o

:frown:

BTW, I found a howto on how to install OO3, so I'll use that :|

:oops:

---

### Post by seish on 2009-02-03
which package do I need to reinstall to get the library?

---

### Post by Jp81 on 2009-02-03
> **seish said:**
> which package do I need to reinstall to get the library?
[http://packages.ubuntu.com/jaunty/libgail18](http://packages.ubuntu.com/jaunty/libgail18)
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/302913](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/302913)

---

