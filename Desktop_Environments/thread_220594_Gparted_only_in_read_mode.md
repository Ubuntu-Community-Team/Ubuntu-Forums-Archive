---
title: "Gparted only in read mode"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Dearhell on 2006-07-21
I would like to repartitionate the HD with gparted (getting some free space from my linux partition in order to install windows).

But gparted only works to me in read mode, it says:

> /dev/hdc can't be opened - label disk unknown

I only have a HD, with linux in one single partition. 

What can I do?

---

### Post by catlett on 2006-07-21
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) I use gparted live. You have to download it and burn the iso to a cd. Then restart your computer and boot to the cd. Then gparted will run. The advantage to this is that your hard drive is not mounted. Gparted cannot format your drive if the system is running off of it. It needs to unmount your drive but if you only have 1 and it is running the OS then gparted cannot unmount it then.
Try gparted live. If you still get the error post the error here.

---

