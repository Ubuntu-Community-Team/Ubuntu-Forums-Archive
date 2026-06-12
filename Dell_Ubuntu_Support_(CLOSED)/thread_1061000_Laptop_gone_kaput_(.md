---
title: "Laptop gone kaput :("
date: 2009-02-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sabretooth16 on 2009-02-05
Hi there,

I have a Dell e1505 laptop on which I installed ubuntu for the first time. The hard drive has two dell partitions,and another large one that I had win xp media center installed, and another one that was a ntfs partition for data files. I used a ubuntu live cd to install ubuntu 8.04 on this data partition. While installing, it failed to install grub boot loader, and after a couple of tries it installed bootloader to /dev/sda2 which was my xp installation. 

After this, I wasn't able to boot into xp. When I turned the computer on the grub menu showed up, then ubuntu ran fine, but upon selecting xp the grub menu reloaded. In ubuntu I edited the menu.lst file changing root->rootnoverify and added 'makeactive' and checkloader (hd0,1)+1. 
Didn't fix anything. Then I booted into one of the dell partitions, and aborted the system checks that it was doing. After that, the computer just showed "bad pbr sig". I used my xp cd to boot, then ran fixmbr, now instead of the pbr message it shows "error loading operating system". This is the current state. 

Oh, and when I previously typed fdisk -l on ubuntu,it showed all partitions with the xp partitions with * and file system as hpfs/ntfs. I had tried mounting this partition with mount, but it said it didn't have valid ntfs. I think the problem started when during installation I chose /dev/sda2 instead of the 'hd0' it had by default, perhaps it corrupted the ntfs drive?

I realize that I may have done stuff in a haste, but I really needed to get one file immediately (which unfortunately I have to reproduce within an hour). Now the first thing I'm going to try is use the ubuntu live cd to boot again and install grub. Any suggestions would be most appreciated.

---

