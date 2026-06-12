---
title: "NVIDIA issues w/ Xorg using lastest kernel"
date: 2007-12-26
forum: Desktop Environments
---

### Post by tybalt81 on 2007-12-26
I've been struggling with some issues with getting Gnome to come up with linux-2.6.20-16-generic kernel. Everything comes up just fine using the linux-2.6.20-15-generic kernel and Gnome. But I did do some digging and looked into the Xorg log files. And seen a complaint of not being able to find a device (/dev//input/wacom). I also took a look into the Kernel log file and noticed a complaint in there also while using 2.6.20-15 kernel. I haven't noticed it affecting anything as far as I know. But, any support to help remedy these situations would be great. 

Thanks!

---

### Post by thefirstM on 2007-12-26
Just to clarify, GNOME is working fine and starts with no obvious problems, but the /dev/wacom device is not found?  If this is the case, then your problem is nothing to worry about.  Wacom is a device for tablet PCs, and therefore is not necessary unless you have one.

---

