---
title: "Help With Grub Plz"
date: 2009-06-07
forum: General Help
---

### Post by ShapeShifter499 on 2009-06-07
Hi, My name is Lance and I need help with grub. I'm thinking to get rid of two partitions, one that has windows xp(about 30 gb) and the other with Acer Recovery(about 4 gb). Now my questions, one how do I do this without messing up grub?, two should I get rid of the Acer Recovery partition?, And last, if I copy all of my windows xp files using a live cd or something can I just put them back onto another partition in the same format and use windows xp again?


BELOW IS INFO ABOUT MY LAPTOP/NETBOOK

I have a Acer Aspire One Netbook that has 120 GB total storage, 1 GB ram, web cam, 8.9 inch screen, one mouse touch pad, built-in wireless(no G3/G4 cell wireless). 3 usb ports, 2 memory card slots, one ethernet port, one vga port, and one headphone and microphone port. In the color blue.

WHAT OPERATING SYSTEM ON IT

Three Partitions

First Partiton: Windows recovery for acer 

Second Partition: Windows XP SP3

Third Partition: Ubuntu 8.10---Updated--->Ubuntu 9.04----Installed Extra---->Ubuntu Studio----Installed Extra---->Ubuntu Netbook Remix---NOW--->Ubuntu Netbook Remix Studio Edition

---

### Post by Crafty Kisses on 2009-06-07
To get a better look at this so I can help you, you need to boot into the Linux partition and run the following commands:
```
sudo fdisk -l
sudo fdisk -lu
```
That can give me the information I and other need to help you out further.

---

### Post by ShapeShifter499 on 2009-06-07
BELOW IS WHAT SHOWED WHEN I TYPED: sudo fdisk -l

lance@lance-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        5736    40957717+   7  HPFS/NTFS
/dev/sda3            5737       14593    71143852+   5  Extended
/dev/sda5            9747       14593    38933496   83  Linux
/dev/sda6            5737        9724    32033547   83  Linux
/dev/sda7            9725        9746      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order


BELOW IS WHAT SHOWED WHEN I TYPED: sudo fdisk -l

lance@lance-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    10233404     5116671   12  Compaq diagnostics
/dev/sda2   *    10233405    92148839    40957717+   7  HPFS/NTFS
/dev/sda3        92148840   234436544    71143852+   5  Extended
/dev/sda5       156569553   234436544    38933496   83  Linux
/dev/sda6        92148966   156216059    32033547   83  Linux
/dev/sda7       156216123   156569489      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by ShapeShifter499 on 2009-06-07
*bump*

---

### Post by ShapeShifter499 on 2009-06-08
*bump*

---

