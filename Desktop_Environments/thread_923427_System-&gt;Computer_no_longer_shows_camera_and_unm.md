---
title: "System-&gt;Computer no longer shows camera and unmounted drives"
date: 2008-09-18
forum: Desktop Environments
---

### Post by slick_rick on 2008-09-18
When I plug my camera in it used to appear in System->Computer, but not anymore.  I can still import photos via the F-Spot photo import thingy, but sometimes I really just want to manage the flash like a disk via a GUI.

Possibly related: /dev/sdc is a drive with two partitions (a swap and a big ext3).  I'm positive of this as is fdisk:

richard@mewtwo:~$ sudo fdisk /dev/sdc
<snip>
Command (m for help): p

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: <snip>

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          32      257008+  82  Linux swap / Solaris
/dev/sdc2              33       24321   195101392+  83  Linux

However for some reason the partitions aren'tt showing up in /dev:
richard@mewtwo:~$ ls -ltr /dev/sd*
brw-rw---- 1 root disk 8, 18 2008-07-19 15:25 /dev/sdb2
brw-rw---- 1 root disk 8, 32 2008-07-19 15:26 /dev/sdc
brw-rw---- 1 root disk 8, 16 2008-07-19 15:26 /dev/sdb
brw-rw---- 1 root disk 8,  0 2008-07-19 15:26 /dev/sda
brw-rw---- 1 root disk 8,  2 2008-07-19 15:26 /dev/sda2
brw-rw---- 1 root disk 8, 17 2008-07-19 15:26 /dev/sdb1
brw-rw---- 1 root disk 8,  5 2008-07-19 15:26 /dev/sda5
brw-rw---- 1 root disk 8,  1 2008-07-19 15:27 /dev/sda1

I used to be able to mount /dev/sdc2 from....  You guessed it, system->computer, but now I can't mount it at all:
richard@mewtwo:~$ sudo mount /dev/sdc2 /mnt
mount: special device /dev/sdc2 does not exist

TIA!

---

