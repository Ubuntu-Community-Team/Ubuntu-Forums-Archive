---
title: "Can't install new Ati drivers"
date: 2005-02-18
forum: Desktop Environments
---

### Post by Gangsta on 2005-02-18
Hi,

i cant install the new ati drivers for xorg , this is the message i get:

dpkg -i fglrx-6-8-0_8.10.19-2_i386.deb
(Reading database ... 64957 files and directories currently installed.)
Unpacking fglrx-6-8-0 (from fglrx-6-8-0_8.10.19-2_i386.deb) ...
dpkg: error processing fglrx-6-8-0_8.10.19-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-6-8-0_8.10.19-2_i386.deb

can somebody help me please.

---

### Post by bobmitch on 2005-02-18
[QUOTE=Gangsta]Hi,

i cant install the new ati drivers for xorg , this is the message i get:

dpkg -i fglrx-6-8-0_8.10.19-2_i386.deb
(Reading database ... 64957 files and directories currently installed.)
Unpacking fglrx-6-8-0 (from fglrx-6-8-0_8.10.19-2_i386.deb) ...
dpkg: error processing fglrx-6-8-0_8.10.19-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-6-8-0_8.10.19-2_i386.deb

can somebody help me please.[/QUOTE]

Try this:

dpkg -i --force-overwrite fglrx-6-8-0_8.10.19-2_i386.deb

---

### Post by Gangsta on 2005-02-19
Thnx it worked, 

Now i need to search how to get the 3d accel on :P

---

### Post by bobmitch on 2005-02-19
Try following the quick guide I wrote [here](http://ubuntuforums.org/showthread.php?t=15990).

The main step to getting 3d accel working is to run the fglrxconfig script to generate a proper xorg.conf file.  (Or xfree config if you are on warty).

Good luck.

---

