---
title: "[SOLVED] grub boot issues, error 17"
date: 2008-12-03
forum: General Help
---

### Post by Person98 on 2008-12-03
recently one of my hard drives quit on me, however it was the hard drive that grub ran off of so i lost access to my linux partitions, i pulled the malfunctioning hard drive out, but now i get a Error 17 from grub, is there a way to re configure grub on the other harddrive sudo fdisk -lu gave me:

Disk /dev/sda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16514064 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x84810ebe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    15711569     7855753+  83  Linux
/dev/sda2        15711570    16498754      393592+   5  Extended
/dev/sda5        15711633    16498754      393561   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x918a918a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312560639   156280288+   7  HPFS/NTFS

sda is my linux drive and sdb is a windows partution, i can boot windows still by selecting it in my bios but linux just won't go, any help would be appreciated thanks

---

