---
title: "[SOLVED] Mount more partitions on startup"
date: 2006-08-06
forum: Desktop Environments
---

### Post by siriusfox on 2006-08-06
My hard drive has a number of partitions. The problem I'm having, is on startup only one partition aside from the boot partition is being mounted. And even if I manually mount one of the other partitions, It doesn't show the icon on the desktop.

How do I ad partitions to be mounted on startup, and make thoes paritions apear as icons on the desktop?

-siriusfox

---

### Post by neilp85 on 2006-08-06
You need to add each partition to your /etc/fstab file. The type of partition will determine how you want to mount them. I believe if your mountpoint is something like /media/partition1, /media/partition2, etc... they should automatically show up on your desktop even if you mount them manually

---

