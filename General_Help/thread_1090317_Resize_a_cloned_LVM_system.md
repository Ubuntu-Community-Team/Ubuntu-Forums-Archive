---
title: "Resize a cloned LVM system"
date: 2009-03-08
forum: General Help
---

### Post by nubian on 2009-03-08
Hi guys,
I have a 2Gb LVM Ubuntu Hardy which I cloned to a 4Gb hdd using ddrescue, it's working great but I need to somehow make use of the extra 2Gb physical size. The current setup is this (cfdisk):

sda1 Primary Linux ext3 254.99MB
sda5 Logical Linux LVM 1891.82
     Pri/Log Free Space 2187.93

how do I go about expanding sda5 so it uses the extra 2Gb free space without losing the data already in there?

Thanks in advance.

---

### Post by dleifer on 2009-03-15
It is a safer and probably easier idea to create a new sda6 partition out of the freespace on the drive.  You can add that partition to your VG/LV without impacting your data.  You get the same effect without the risk to your current data.

I would recommend backing up your data anyway.  It's only 2GB after all.

Roughly,
- fdisk the freespace as /dev/sda6
- vgextend VG /dev/sda6
- lvresize -L +2G LV
- resize2fs LV

Replace "VG" and "LV" with the names of your vg and lv.  I'm assuming your LV filesystem is ext2 or ext3 so use resize2fs.  If you are using reiserfs then resize_reiserfs.

---

