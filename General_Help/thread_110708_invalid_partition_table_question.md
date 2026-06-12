---
title: "invalid partition table question"
date: 2005-12-31
forum: General Help
---

### Post by linuxted on 2005-12-31
My setup seems to work but I'm very nervous about the "Disk /dev/hdb doesn't contain a valid partition table" line when I do an "fdisk -l".   Am I doing something wrong here (I suspect since I'm using the entire 120Gb as a partition, mkfs is doing something weird)?   Here is the detail...

I have an 80Gb primary hard drive for Linux and a 120Gb drive I use for backups only.  I partitioned the 80Gb with Ubuntu during install and the 120Gb with the following command:

/sbin/mkfs -t ext3 /dev/hdb

When I run fdisk -l I get:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        9729    77899185    5  Extended
/dev/hda5              32        9729    77899153+  8e  Linux LVM

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdb doesn't contain a valid partition table


****************************************************

Am I doing something wrong here?

Thanks for the help

---

### Post by zoiks on 2005-12-31
"/sbin/mkfs -t ext3 /dev/hdb"

Usually the proper way to partition and format is to first make a partition(s), then format the partition (i.e. put a file system on a partition).  In this case it looks like you put the filesystem on the drive device itself (as opposed to the partition).

I don't know anything about doing that sort of thing (maybe it's something people do?), but if you are willing to lose your data on hdb, you can start over by repartitioning your drive (from the command line you can use fdisk) with 1 big partition as partition number 1 (just take up the whole drive), then repeat the mkfs command you entered using /dev/hdb1 instead.  You shouldn't get complaints any more after that.

---

### Post by zoiks on 2005-12-31
Oh, and you can probably use System|Administration|Disks to accomplish this with a user-friendly gui.  Just make sure the target disk/partitions are unmounted.

---

### Post by linuxted on 2005-12-31
[QUOTE=zoiks]"/sbin/mkfs -t ext3 /dev/hdb"

Usually the proper way to partition and format is to first make a partition(s), then format the partition (i.e. put a file system on a partition).  In this case it looks like you put the filesystem on the drive device itself (as opposed to the partition).

I don't know anything about doing that sort of thing (maybe it's something people do?), but if you are willing to lose your data on hdb, you can start over by repartitioning your drive (from the command line you can use fdisk) with 1 big partition as partition number 1 (just take up the whole drive), then repeat the mkfs command you entered using /dev/hdb1 instead.  You shouldn't get complaints any more after that.[/QUOTE]

Thank you for your reply.  I do not mind losing the data on the drive, I want to do it right.  I will try the fdisk route and report back.  Again, I do appreciate the help!

---

### Post by linuxted on 2006-01-01
[QUOTE=linuxted]Thank you for your reply.  I do not mind losing the data on the drive, I want to do it right.  I will try the fdisk route and report back.  Again, I do appreciate the help![/QUOTE]

Well it whacked out my system, but after a rebuild I finally got it to work  (my fault).


Thanks for the help

---

