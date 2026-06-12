---
title: "Problem with fstab"
date: 2008-04-20
forum: Desktop Environments
---

### Post by maaylix on 2008-04-20
PROBLEM SOLVED, I overlooked something obvious, sry, this may be deleted 
====================================

Recently I created a FAT32 partition with gparted to use as a share partition between my dual boot Windows Xp/Ubuntu 7.10 machine.

The partition was created successfully, Windows recognized it and so did Ubuntu, the problem is that I can't get it to mount automatically when Ubuntu boots. Here is how my fstab looks:

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4ef594a2-245e-43ce-9e41-ef891a54118f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=045de847-3e25-4d5c-bc1d-9b75912eefad /home           ext3    defaults        0       2
# /dev/sda1
#UUID=0E5CA86F5CA852EF /media/sda1     ntfs    defaults,umask=007,gid=46 0       0
# /dev/sdb1
#UUID=8640B42940B4223B /media/sdb1     ntfs    defaults,umask=007,gid=46 0       0
# /dev/sdb3
UUID=15f2b045-e728-48c2-9ebb-e8e944552e4e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda3 /mnt/Share vfat defaults 0 3


```

The last line was my attempt to get Ubuntu to load my FAT32 partition automatically, as after creating the new partition, fstab had nothing related to it (no line referring to the new partition)

Before editing fstab I created the new directory by typing:

```
 mkdir /mnt/Share
```

Thing is that with the current fstab, Ubuntu doesn't recognize my Fat32 partition, only by adding ''#'' in front of the fat32 partition line, am I able to access it.

---

### Post by sdennie on 2008-04-20
I think if you change the part that says "defaults" to "defaults,auto" it will mount it at boot time.

Edit:

Oh, I also notice that you have pass set to 3 (the last number on the line describing /dev/sda1).  I don't know if that's valid.  You may have to change that to 2.

---

