---
title: "Acer One Netbook remix install - error 17"
date: 2009-06-10
forum: General Help
---

### Post by tinawina on 2009-06-10
Hello all - 

I have an Acer Aspire One that came loaded with Windows XP Home. I was looking around for a Linux distro to load onto it and first tried Kuki Linux but didn't like it. I then found Ubuntu's netbook remix and really really liked it. Installed without a hitch, has been working great. 

I ran update manager yesterday and it said there wasn't enough space on the hdd to install updates -- free up some space. I booted into XP and ran partition magic. I resized my C: drive from approx 150g to 100g and chose to allocate the 50g to what I thought was my ubuntu hdd. Seemed to go well. Rebooted and have been getting the Grub Loading please wait - Error 17 message ever since. And nothing works on the computer.

I am booted into Ubuntu Live from my USB stick and have been looking around for answers. One that I could handle was  simply to reinstall Ubuntu. At the partition stage I noticed this configuration and I figure this has to have something to do with my woes:

/dev/sda1 ..... Windows NT ..... FAT32 ..... 4.9gb
/dev/sda2 ..... Windows XP home ...... NTFS ..... 139.2gb
/dev/sda6 ..... (ext3) ...... 2.3gb
/dev/sda7 ..... (linux-swap) ..... 172.5mb
/dev/sda5 ..... (ext3) ...... 2.3gb
/dev/sda8 ..... (linux-swap) .... 172.5mb

I'm a complete n00b! but seems like the order here could have something to do with grub not knowing what to load? And sda4 is missing. 

I would like to just have XP and ubuntu loaded up -- looks to me like Kuki is still on my hdd. How can i get rid of the Kuki partition, and just have xp and ubuntu with a 50/50 split of hdd resources between them? Oh - and how do i actually get my computer to give me that pretty screen with the choice to boot into XP or Ubuntu?? The computer is pretty much dead now execpt if I insert my Live usb.

THANKS FOR YOUR HELP!!

---

### Post by tinawina on 2009-06-10
More info about my system. Appreciate any help - thanks!


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638       18805   145934460    7  HPFS/NTFS
/dev/sda3           18806       19457     5237190    f  W95 Ext'd (LBA)
/dev/sda5           19132       19435     2441848+  83  Linux
/dev/sda6           18806       19109     2441817   83  Linux
/dev/sda7           19110       19131      176683+  82  Linux swap / Solaris
/dev/sda8           19436       19457      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4039 MB, 4039114752 bytes
125 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      415919      447748   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(415918, 36, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(447747, 120, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       55855      155943   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(55854, 42, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(155942, 71, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      241234      488877   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(241233, 109, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(488876, 58, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      225884      226958     4161547    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(225883, 70, 43)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(226957, 64, 8)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

