---
title: "Which format for Ubuntu partition?"
date: 2009-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by OldGrantonian on 2009-11-01
I have a Dell Inspiron 6400 with Windows Vista Home Premium. My drive is formatted in NTFS.

I want to use gParted to create a Ubuntu partition. I need to know which format to use for the new partition. 

I have options such as:

ext2, 3, 4
fat32
hfs
ntfs

Am I correct in assuming that the new partition will be a primary partition, rather than an extended partition?

---

### Post by howefield on 2009-11-01
> **OldGrantonian said:**
> Am I correct in assuming that the new partition will be a primary partition, rather than an extended partition?

Linux can be installed into either primary or extended.

Choose either of the ext file systems. ext4 is the default for Karmic.

---

### Post by Odemia on 2009-11-01
For your root linux partition ext3 or ext4 would be suggested.  Some people complain about ext4, it is fairly new but I have had no problems with it.  If you want to be a little conservative use ext3, it has been around long enough that it is solid.

If you want to share files between the two partitions easily, create a ntfs or fat32 partition.  They should be easy to mount in windows and linux.  Ext partitions can be a pain to mount from windows (at least last I tried, which is several years ago now).

I suggest taking a look at [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) it has some insight into common problems with dual boot set-ups.

As for primary vs extended,  linux can boot from extended partitions as long as the boot loader (GRUB or LILO) is on the primary partition.  If you aren't planning on having a separate boot partition make the linux partition a primary partition.

---

### Post by Ichido on 2009-11-03
I'm now running 9.10 Karmic on both of my Dell 1525n laptops using ext3 file system:D
The only "problem" is a false "Hard Drive Failure Imminent" warning, which I turned off.

---

### Post by DynastyX on 2009-11-03
> **Ichido said:**
> I'm now running 9.10 Karmic on both of my Dell 1525n laptops using ext3 file system:D
The only "problem" is a false "Hard Drive Failure Imminent" warning, which I turned off.

I get this same warning with my install, granted I'm not on a Dell... How did you make it work correctly?

---

### Post by Jekshadow on 2009-11-03
> **DynastyX said:**
> I get this same warning with my install, granted I'm not on a Dell... How did you make it work correctly?

Only way is to turn it off. I've been getting that since Alpha 4 (when I started trying Karmic), and it still has not been fixed.

---

