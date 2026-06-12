---
title: "gnome-power-manager freezes 9.10"
date: 2009-11-08
forum: Desktop Environments
---

### Post by kt7 on 2009-11-08
**System: **

Fresh and updated Ubuntu 9.10 amd64 on Amilo laptop:
Linux 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

Previous version, 9.04, did not have this problem. 
I have external monitor attached to laptop + usb keyboarda and mouse. 

**Problem description:**

Mouse starts to freeze from time to time, things become slower,  then apps start to freeze. Can still move from virtual screen to another, but can't do anything. Ctrl+Alt+Backspace don't work. Shutting down power is only way. 

**Solution:**

kill gnome-power-manager.

**UPDATE:**

nope. gnome-power-manager made things only worse. 9.10 still freezes same way when I have lots of network traffic (scp or torrents). When looking movie, system goes to crawl, but survives.

**UPDATE2**

This seems to be  [bug 270798]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798"). 

setting kernel parameters "nolapic acpi=off" solved the problem. In file /etc/defalut/grub set GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic acpi=off" then sudo update-grub.

---

