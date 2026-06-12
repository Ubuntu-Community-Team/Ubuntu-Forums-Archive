---
title: "GRUB Error 17  :'("
date: 2009-04-21
forum: General Help
---

### Post by nulall on 2009-04-21
So I was trying to restore some data yesterday on a SD card and somehow it seems I fried my whole system...

When I booted up, I got GRUB error 17.
Per [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) I did the following from the Jaunty LiveCD
```
sudo grub
find /boot/grub/stage1
root (hd0,1)
setup (hd0)
quit
```

That got me past the GRUB error, but the screen would go black and I couldn't fully boot.

Next, I tried the SuperGrubDisk, which only showed me the option of booting to an old Ubuntu 7.10 (I was running Jaunty 9.04 before this issue).  I tried selecting that and it doesn't work either.

I'm not sure where to go next. I'm thinking about re-installing Jaunty, but I'd like to preserve my data, and here's where things get confusing.

I've included below a picture of GParted and the output of fdisk -l, but I think that my problem can be summarized by the fact that sda5 has only really old data on it from my home directory (~1 year old) and sda7 is currently inaccessible with a lot of space. What should I do next? I'm running Testdisk as we speak...

Thanks so much for the help. The sooner, the better, please :(

```
fdisk -l

Disk /dev/sdc: 1010 MB, 1010826752 bytes
32 heads, 61 sectors/track, 1011 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     1651315     1777688   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(1651314, 30, 24)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(1777687, 27, 34)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      221758      619137   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(221757, 23, 51)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(619136, 23, 61)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      957768     1940980   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(957767, 22, 38)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(1940979, 26, 37)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      383547      387811     4161547    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(383546, 24, 9)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(387810, 20, 18)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001e10f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246       38913   302568210    5  Extended
/dev/sda5            1246       11572    82951596   83  Linux
/dev/sda6           38416       38913     4000153+  82  Linux swap / Solaris
/dev/sda7           11573       37710   209953453+  83  Linux
/dev/sda8           37711       38415     5662881   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4009 MB, 4009549824 bytes
128 heads, 63 sectors/track, 971 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0x001c2022

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         971     3915040+   b  W95 FAT32

Disk /dev/sdc: 1010 MB, 1010826752 bytes
32 heads, 61 sectors/track, 1011 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     1651315     1777688   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(1651314, 30, 24)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(1777687, 27, 34)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      221758      619137   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(221757, 23, 51)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(619136, 23, 61)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      957768     1940980   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(957767, 22, 38)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(1940979, 26, 37)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      383547      387811     4161547    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(383546, 24, 9)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(387810, 20, 18)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sde: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b1157

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       20022   160826683+   7  HPFS/NTFS

```

---

### Post by nulall on 2009-04-21
After running TestDisk, I've found all my important/relevant/current files in what is presumptively sda7.
What do I do now?

EDIT: attached picture of sda7 selected in TestDisk with text below stating "EXT3 Large file Sparse superblock Backup superblock, 214 GB / 200 GiB"

---

### Post by nulall on 2009-04-21
For anyone interested, I may have found my answer at [http://www.cgsecurity.org/wiki/Advanced_Find_EXT2_EXT3_Backup_SuperBlock](http://www.cgsecurity.org/wiki/Advanced_Find_EXT2_EXT3_Backup_SuperBlock)

> The location of the backup superblocks are dependent on the filesystem's blocksize, this size is stored in the superblock, so it's not known while searching for backup superblock. To search them, running TestDisk, in the Advanced menu, select the partition and choose Superblock. 

> Now using the value given by TestDisk, you can use fsck to repair your ext2/ext3 filesystem. Ie if TestDisk has found a superblock at block number 24577 and a blocksize of 1024 bytes, run
```

/sbin/fsck.ext3 -b 24577 -B 1024 /dev/hda1
```


will post a follow up after this runs and let you know whether it worked...

---

### Post by unutbu on 2009-04-21
I don't think fsck is the right thing to do yet.
It is your partition table that is messed up, not (as far as I can tell) your filesystems.

Have you already done a "deeper search"? (After doing the quick search, press enter, than select "deeper search".)

After doing the deeper search, use the left/right arrows to change the partition types to primary, extended, logical, or deleted, as appropriate. Use the "p" key to check that each partition is readable. Check the start and end numbers to make sure none of the partitions overlap. 

Then press Enter, and write the partition table to disk.

Using testdisk to rewrite the partition table is safer than using fsck. If you make a mistake writing the partition table, you can use testdisk again to correct it.

fsck can alter your filesystem. If you use the wrong superblock, you can lose data.

---

