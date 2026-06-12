---
title: "udev permissions for external harddisk"
date: 2008-05-11
forum: Desktop Environments
---

### Post by gmaniac on 2008-05-11
Hi.
I have an external harddisk which i partitioned and formatted to xfs and ntfs.
All i want is the xfs partition to be writable by anyone when it gets auto mounted.
Strangely the ntfs has correct permissions.

To change the default permissions I have tried something like 
BUS=="usb",   ATTRS{product}=="Basics Desktop", MODE=”0666”
on a 10-local-rules file but to no avail. 

Anyone with udev experience??

---

