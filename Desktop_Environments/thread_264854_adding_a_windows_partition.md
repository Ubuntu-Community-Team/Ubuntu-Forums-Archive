---
title: "adding a windows partition"
date: 2006-09-25
forum: Desktop Environments
---

### Post by rarstar on 2006-09-25
hi all

bit of a noob question, here goes...

i installed ubuntu on a 30g drive, keeping the default settings for partitioning and formatting, and allowing it to use the whole disk... i now need to 'reclaim' some of the space to stick a windows2000 or mce partition on there.

is there a quick way of reclaiming a few gigs, and not affecting how the system will boot? hopefully, i want a choice on boot up of loading ubuntu or windows.

i know it's easier to install windows first, then let linux configure the booting, but i'd appreciate any help, so windows doesn't overwrite the boot config.

cheers
rar

---

### Post by timmeeej on 2006-09-25
install gparted to resize your ext3 partition and create free space. Install Windows in the free space. Windows will overwrite your MBR, so your system will automaticly boot into Windows. 

To recovery Ubuntu and Grub follow this guide:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by rarstar on 2006-09-25
thanks, just what i was looking for

cheers
rar

---

