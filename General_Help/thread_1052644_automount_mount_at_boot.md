---
title: "automount/ mount at boot?"
date: 2009-01-27
forum: General Help
---

### Post by Shadowfaux on 2009-01-27
Hey, just switched to ubuntu after a major component crash that seen me lose my motherboard. I replaced that and my hdd since I wanted to keep what I had on my hdd. But only issue i have had is that I never had my old drive attached when i installed ubuntu and now I have to manually mount it every time I startup since what I mainly use is stored there.
I tried to get it to mount at startup using guides I found through google and the forum here and what I found about adding to fstab hasn't worked it seems.

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=778617e6-6be6-45d9-8e8c-2e06b121ec9f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=12eb80c4-43cd-45e9-b846-bfd6b0ed7f46 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb1	/media/xp	ntfs	user,auto,rw		0	0
```
As you can see I tried to mount sdb1 (which is what the drive comes under in System Monitor) to /media/xp since that's what the drive was called before. I'm not 100% about the <type> for it, but the one that is mentioned under System Monitor doesn't work either (fuseblk). Anyone have any idea's where I'm going wrong?

---

### Post by -kg- on 2009-01-28
Ooops!

```
#/dev/sdb1	/media/xp	ntfs	user,auto,rw		0	0
```

Try removing the # from in front of the line.  The pound sign makes the line a comment.

---

### Post by Shadowfaux on 2009-02-01
Thank you! should have known that but obviously messed it up, again thank you.

---

