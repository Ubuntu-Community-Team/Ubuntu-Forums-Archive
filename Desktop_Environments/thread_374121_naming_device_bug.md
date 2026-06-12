---
title: "naming device bug"
date: 2007-03-02
forum: Desktop Environments
---

### Post by paul_mb on 2007-03-02
Hi, I recently installed ubuntu 6.10 edgy eft and encountered a bug: I have 5 partition on my HDD: 1Xntfs, 1xswap 1xreiserfs 2xfat32.
When they are displayed on desktop I see hda1,hda6 but hda5 has a weird name (some random characters).I attached a screenshot for the details.
pls help.

---

### Post by paul_mb on 2007-03-04
does anyone have a clue???
I heard is a "characters set" problem, so far noone knew a solution , at leat give me a clue. here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=eba508c3-6ea3-4e69-ae24-5390cbffdaee /               reiserfs notail          0       1
# /dev/hda1
UUID=3414AA6814AA2CB4 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=70CE-5FA5  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=A8E2-3E87  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=539db73b-a52c-4df8-bee5-81e5fda575c7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```
and another screenshot, maybe that will help .

---

### Post by mannheim on 2007-03-04
I think part of the answer is that the name that appears for the drive on the desktop is the volume label, if the volume has a label. If there's no label, then you get "hda6" or whatever.

I'm guessing that the FAT filesystem on hda5 has a volume label (perhaps one that gets screwed up along the way).

---

### Post by paul_mb on 2007-03-05
nope. in Qtparted I see at both fat32 partitions in the label section :"NO NAME" , and hda3(root) has "No label".

---

### Post by mannheim on 2007-03-05
In the "Device Manager", what is the entry for "volume.label" for this device?

---

### Post by paul_mb on 2007-03-05
_w
!K{Z! 

these character apear at volume.label and also apear at volume.policy.desired_mount_point and info.product, the twin partition has an empty string at volume label, yet in qtparted both have "no name".
man , this is weird.](*,) 
ps: With the same partition table I had ubuntu 5.10 with no problems.

---

### Post by mannheim on 2007-03-06
I think that the string in "info.product" and "desired_mount_point" are both derived from volume.label. The trouble with the label might be something to do with [this bug in launchpad]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/33794"). (Apparently, fat volumes have two labels -- a long and a short one -- just as filenames in fat have a short and a long version. So maybe only the long version is corrupt and the short version is empty.) Whether or not it is the same bug, the comments there tell you how to reset the label, which might be worth a shot. 

If the problem stems from the character encoding, then perhaps this should be reported as a new bug. Since version 5.10, I think the way that mounted volumes are given names has changed (but I may be remembering wrong).

---

