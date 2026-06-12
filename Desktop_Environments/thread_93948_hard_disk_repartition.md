---
title: "hard disk repartition"
date: 2005-11-23
forum: Desktop Environments
---

### Post by shizow on 2005-11-23
my hard disk has three windows partitions, which i like to delete and use the free disk space in linux
there is a primary windows partiton and a extended with two logical drives

sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hda2            1276        5287    32226390    f  W95 Ext'd (LBA)
/dev/hda3            5288       24792   156673912+  83  Linux
/dev/hda5            1276        2550    10241406    b  W95 FAT32
/dev/hda6            2551        5099    20474811    b  W95 FAT32
/dev/hda7            5100        5287     1510078+  82  Linux swap / Solaris


how can i delete all windows partitions without destroying my data on linux partitions?

---

### Post by Pablo_Escobar on 2005-11-23
> sudo apt-get install gparted for Gnome
> sudo apt-get install qtparted for KDE

Then launch the g or qtparted. Unmount the Windows partitions (it can be done from the program). Delete this 2 extended partitions and create a brand new one (ext3 or reiserfs). 
If You played with PartitionMagic under M$ then it should be easy to operate the g(qt)parted.

---

### Post by shizow on 2005-11-23
[QUOTE=Pablo_Escobar]for Gnome
 for KDE

Then launch the g or qtparted. Unmount the Windows partitions (it can be done from the program). Delete this 2 extended partitions and create a brand new one (ext3 or reiserfs). 
If You played with PartitionMagic under M$ then it should be easy to operate the g(qt)parted.[/QUOTE]

but is it safe to destroy the primary windows partitions? does this conflict with the bootloader in the MBR

---

### Post by Pablo_Escobar on 2005-11-23
AFAIK when the Grub is at MBR (not on the 1st partition) it's safe to manipulate partitions, because erasing it won't touch MBR.
But that's only my point of view.
It's better for someone to verify it, because partitioning can be sometimes troublesome :)

---

### Post by shizow on 2005-11-23
i deleted the two logical drives in my extended partition 
and now my disk looks like this
sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hda2            1276        5287    32226390    f  W95 Ext'd (LBA)
/dev/hda3            5288       24792   156673912+  83  Linux
/dev/hda5            5100        5287     1510078+  82  Linux swap / Solaris

can i really delete the first primary ACTIVE windows partiton without destroying data on the linux partitons?

somehow is the swap partition part of the windows extended partition, how can mode the swap partition out of the extended partition?

---

### Post by shizow on 2005-11-23
ok now i deleted all windows partitions and made a new swap partition

sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         261     2096451   82  Linux swap / Solaris
/dev/hda3            5288       24792   156673912+  83  Linux


the only thing i want to do now is 
resize the /dev/hda3 to fill upthe space between the two partitions which is free now

is it safe to resize partiiton with qtparted, qtparted says sometimes something like dont make operations with mounted harddisk
how should i resize without mounting?

---

### Post by Pablo_Escobar on 2005-11-23
You won't be able to resize the root partition - / while booting from it and that seems to be the case You're speaking of.
This volume must be mounted because heh, You work on it :)
The only way is to:
1. Get a LiveCD with partitioning capabilities (Knoppix f.e.), boot from it, resize the partition and reboot
2. Get the drive to another PC, connect it, and resize the partition from an OS which can understand ext3 or reiserfs - just be sure the drive isn't mounted.

---

### Post by shizow on 2005-12-07
i tried it with knoppix, but it seems that i cannot resize to partition, maybe because i want to resize the partition with space which lies before the partition??

---

### Post by Pablo_Escobar on 2005-12-07
You can't do it that way. The partition has to be a closed block. You can try to move other partition thus freeing the space after the one You want to resize.

---

