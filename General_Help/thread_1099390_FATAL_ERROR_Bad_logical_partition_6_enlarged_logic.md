---
title: "FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap"
date: 2009-03-18
forum: General Help
---

### Post by Revelation60 on 2009-03-18
Hi,

I want to install Arch Linux next to my Ubuntu, but I am unable to install because I get an error from cfdisk:

FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap.

This is the output of fdisk -l:

ben@PCBEN:~$ sudo fdisk /dev/sda -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Unit = cylinders of 16065 * 512 = 8225280 bytes
Disk-ID: 0xecbde5ed

 Device  Boot   Begin             End     Blocks    ID  System
/dev/sda1   *           1        5100    40960000    7  HPFS/NTFS
/dev/sda2            5100       80875   608662687+   7  HPFS/NTFS
/dev/sda3           80876       88524    61440592+   5  Uitgebreid
/dev/sda4           88525       91073    20474842+  83  Linux
/dev/sda5           80876       81052     1421689+  82  Linux 
swap
/dev/sda6           84691       87239    20474811   83  Linux
/dev/sda7           87240       88524    10321762+  83  Linux


I have no clue on how to fix this. Can someone please help me?

---

