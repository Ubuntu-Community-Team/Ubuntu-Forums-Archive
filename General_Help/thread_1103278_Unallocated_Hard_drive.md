---
title: "Unallocated Hard drive"
date: 2009-03-22
forum: General Help
---

### Post by nrama on 2009-03-22
I have a dual boot system running Ubuntu 8.04 and Mandriva 2008.1. After a number of operations,too numerous to enumerate I have ended up with the following situation,It all started with an attempt to fix a chronic problem of error 18 after about 30 or so reboots. . When I boot into Ubuntu and go into partition editor (gparted) I get a dismal gray bar with "unallocated 74.53 GiB".Using the live Disk is no better.Booting into Mandriva, the control center shows the disk partition information clearly as expected with the entire disk partitioned per fdisk -l as follows;

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2449 19671561 83 Linux
/dev/sda2 2450 7850 43383532+ 83 Linux
/dev/sda3 7851 8215 2931862+ 82 Linux swap / Solaris
/dev/sda4 8216 9730 12169237+ f W95 Ext'd (LBA)
/dev/sda5 8216 8767 4433908+ 83 Linux
/dev/sda6 8768 8896 1036161 82 Linux swap / Solaris
/dev/sda7 8897 9729 6691041 83 Linux

Sda1,2, & 3 are used by Ubuntu and the rest by Mandriva
I have tried everything I can think of short of reinstalling and destroying the existing partition table,which I am loath to do.

The computer works perfectly in all other respects under both the OSes. I shall be grateful for any pointers to resolve this niggly problem.

---

