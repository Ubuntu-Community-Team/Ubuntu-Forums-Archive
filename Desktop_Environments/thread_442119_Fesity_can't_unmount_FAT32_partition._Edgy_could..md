---
title: "Fesity can't unmount FAT32 partition. Edgy could."
date: 2007-05-13
forum: Desktop Environments
---

### Post by benton on 2007-05-13
Hi there,

I have a dual-boot setup. Feisty detects my Windows FAT32 partition and shows a desktop icon for it. Right clicking on it and choosing "Unmount" gives me the following error:

**umount: /media/hda1 mount does not match fstab**

I'm translating the message to english from my native language, so it may be a little different.

However I *can* unmount the partition manually, with this command:

sudo umount /media/hda1/

So is there a place I can configure the correct umount command for this partition? Obviously Feisty is trying an erroneous command when using the "Unmount" option in the context menu.

Here's my fstab for reference:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=4eb26aaa-660b-4a7b-a2a8-0165933e0403 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=38F1-DC43  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=5c5c0cc7-174f-49e3-ba2a-c6cd24fed8d1 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Thanks in advance,

-Benton

---

