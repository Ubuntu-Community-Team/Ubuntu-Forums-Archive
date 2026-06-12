---
title: "need assistance with camera install"
date: 2006-01-02
forum: Desktop Environments
---

### Post by lost1234 on 2006-01-02
I have version 5.04, which is 2.6.10
I am trying to install SN9C102 driver for my web camera, SN9C102-1-24

when I run make I get:
**************************************************************************
* Building Video4Linux2 driver v1.24 for SN9C10x PC Camera Controllers...*
* Official Linux 2.6.10 is the minimum version for this driver.          *
* Read the documentation "sn9c102.txt" for more informations.            *
* Type "make help" for a list of available targets.                      *
**************************************************************************

make -C /lib/modules/`uname -r`/build M=/home/gd/sn9c102-1.24 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
 
Could anyone tell me what I need to do to fix this, I really want to use the camera.
I am unfamiliar with ubuntu or linux
I am running under gnome.

---

### Post by Lord Illidan on 2006-01-02
Try running ```
sudo make
```

Is there a configure script there?

---

### Post by cwaldbieser on 2006-01-02
[QUOTE=lost1234]I have version 5.04, which is 2.6.10
I am trying to install SN9C102 driver for my web camera, SN9C102-1-24

when I run make I get:
**************************************************************************
* Building Video4Linux2 driver v1.24 for SN9C10x PC Camera Controllers...*
* Official Linux 2.6.10 is the minimum version for this driver.          *
* Read the documentation "sn9c102.txt" for more informations.            *
* Type "make help" for a list of available targets.                      *
**************************************************************************

make -C /lib/modules/`uname -r`/build M=/home/gd/sn9c102-1.24 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
 
Could anyone tell me what I need to do to fix this, I really want to use the camera.
I am unfamiliar with ubuntu or linux
I am running under gnome.[/QUOTE]

You need to install the "linux-headers" package that matches the version of the kernel you are using ("uname -r" at the terminal to find the kernel version).

---

