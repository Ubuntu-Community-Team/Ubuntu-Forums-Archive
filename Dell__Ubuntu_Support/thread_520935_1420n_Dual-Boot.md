---
title: "1420n Dual-Boot"
date: 2007-08-08
forum: Dell  Ubuntu Support
---

### Post by notwen on 2007-08-08
Here is my partition table. Can someone explain which each partition is, so I can proceed w/ installing WinXP? I'm guessing that sda1-sda3 are needed for my recovery, sda6 is my Linux Ubuntu install. Do the pre-laoded Dellbuntus come w/ swaps(sda5) already made on the HDD? In the end I'm wanting any partitions I need for recovery option, Ubuntu, swap, a 5GB FAT32 share partition, and the freespace for my WinXP installation.

---
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 9 72261 de Dell Utility
/dev/sda2 10 271 2104515 b W95 FAT32
/dev/sda3 * 272 296 200812+ 83 Linux
/dev/sda4 297 19457 153910732+ f W95 Ext'd (LBA)
/dev/sda5 297 617 2578401 82 Linux swap / Solaris
/dev/sda6 618 19457 151332268+ 83 Linux

---

### Post by ticklecricket on 2007-08-09
just shrink your sda6 partition and create new extended partitions in the free space

---

### Post by UObean on 2007-08-09
I just got my 1420N today.  I'm going to be using [this guide](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp) to shrink my partition and install XP.  Seems relatively simple.

---

### Post by notwen on 2007-08-09
Is anyone able to explain -in detail- which each partition actually is? =]

---

### Post by notwen on 2007-08-10
*bump*

---

### Post by UObean on 2007-08-10
I have no idea what the first partition is besides that its a FAT16 partition.  The second partition is where I believe they store all the restore information.  That one is FAT32 on mine.  I believe the OS is installed on the 3rd partition (0,2), Linux swap is on the 5th, and home is on the 6th.  I'd wait to hear from others though, as I'm a big newb. :)

---

### Post by sciurus on 2007-08-10
/dev/sda
1 Dell Utility
2 Dell Recovery
3 /boot
4 Extended partition
5 swap 
6 / (root)

---

### Post by blackhowling on 2007-09-02
I'd be interested in getting this to work as well

---

