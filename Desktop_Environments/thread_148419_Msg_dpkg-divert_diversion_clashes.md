---
title: "Msg: dpkg-divert: diversion clashes ?"
date: 2006-03-22
forum: Desktop Environments
---

### Post by BigDeal on 2006-03-22
I tried to install Nvidia drivers from previous thread:  

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

and system returns the following message:

.....
unpacking nvidia-glx (from ...nvidia-glx_1.0.7667-0ubuntu25.1_i386.deb)
dpkg-divert: 'diversion of /usr/lib/libGL.so.1 to /usr/lib/libGL.so.1.xlibmesa by nvidia-glx' clashes with 'diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.7667-0ubuntu25.1_i386.deb (--unpack) subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
/var/cache/apt/archives/nvidia-glx_1.0.7667-0ubuntu25.1_i386.deb

That was caused from an unsuccessfull installation of ATI X1600 which I changed again to Nvidia 6800. 

Any help please  ??? :(

---

### Post by hw-tph on 2006-03-22
Try removing the offending package: **sudo apt-get remove --purge xorg-driver-fglrx**


Håkan

---

### Post by BigDeal on 2006-03-22
Let's try this:

sudo apt-get remove --purge xorg-driver-fglrx

msg is:

Package xorg-driver-fglrx is not installed, so not removed...

Next try to: 

sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`

same error message...

grrrrr ](*,)

---

### Post by BigDeal on 2006-03-22
Anyone with an idea ? I need some HELP !!!

---

