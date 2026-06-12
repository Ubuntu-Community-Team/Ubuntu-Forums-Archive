---
title: "Inspiron 6400 dual boot with media direct, windows 7"
date: 2009-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by agst on 2009-07-26
Hi, I'm new here:smile:
 
I had spent the last 2 weeks trying to get the right setup. I have a Dell Inspiron 6400 laptop and wanted to dual boot Ubuntu 9.04 with Windows 7. After a lot of trouble and many installations (and following some threads in here, thanks!) I finally got Win 7 to boot when I pressed the power button and Ubuntu to boot when I pressed the Media Direct button.
 
However I installed some applications and then I noticed GParted wasn't installed anymore. So I installed it again only to find out it said my whole hard drive was unpartitioned! I can boot to Win 7 fine, I can get to the grub menu and boot Ubuntu but it doesn't finish loading. I get some weird colors at the top of the screen that flash 3 or 4 times and then it just hangs. I have tried safe mode and it does the same thing.
 
I can see all of my partitions using a live cd (sometimes only!!) PLEASE HELP!!!
 
I don't know if it stopped working because I installed some of the KDE apps, is that possible?  I was told in the other forum that it may be a video setup problem with the apps I installed.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        5228    41945715    7  HPFS/NTFS
/dev/sda3            5229        6448     9799650   83  Linux
/dev/sda4            6449       19457   104494792+   5  Extended
/dev/sda5            6449        6934     3903763+  82  Linux swap / Solaris
/dev/sda6            6935       19457   100590966   83  Linux

---

