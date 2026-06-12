---
title: "FAT32 Partition"
date: 2006-08-31
forum: Desktop Environments
---

### Post by flemmingesm on 2006-08-31
If I format a partition to the FAT32 filesystem, using Gnome Partition Editor, shouldn't I get access to the drive from both Ubuntu and XP ?
I don't seem to be able to mount the partition in Ubuntu... It works fine in XP...

Flemming Mørup
Denmark

---

### Post by Jussi Kukkonen on 2006-08-31
> I don't seem to be able to mount the partition in Ubuntu...
Being a little more verbal about this part would help: Did you try it on command line? If yes, what was the exact command and what was the repsonse?

If you didn't, try
```
mount -t vfat /dev/<devicename> /media/<mountpoint>
```
You need to have created the mount point previously, though.

---

