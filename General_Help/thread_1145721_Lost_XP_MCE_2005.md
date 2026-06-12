---
title: "Lost XP MCE 2005"
date: 2009-05-01
forum: General Help
---

### Post by woodier on 2009-05-01
I installed, side by side, Ubantu 9.04 desktop with XP MCE 2005 on sda of my HP Media Center (sdb is ok). Now, I can't boot the XP MCE 2005. I'm able to get a directory listing only in the "[Data]" partition, which includes the OS. What should be my next course of action, since I really need some of the files on sda?
 
:~$ sudo fdisk -l 
 
 
Disk /dev/sda: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x5b825b82 
 
 
Device Boot Start End Blocks Id System 
/dev/sda1 * 1 30075 241577406 44 Unknown 
/dev/sda2 30076 30401 2618595 5 Extended 
/dev/sda5 30076 30379 2441848+ 83 Linux 
/dev/sda6 30380 30401 176683+ 82 Linux swap / Solaris 
 
 
Disk /dev/sdb: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
 
=========================================================
 
 
&#65279;TestDisk 6.11.2, Data Recovery Utility, April 2009 
Christophe GRENIER <grenier@cgsecurity.org> 
[http://www.cgsecurity.org](http://www.cgsecurity.org) 
 
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63 
Partition Start End Size in sectors 
D HPFS - NTFS 0 1 1 30074 254 63 483154812 
D HPFS - NTFS 6171 0 1 18295 254 63 194788125 
D HPFS - NTFS 18296 1 1 30400 254 63 194466762 [Data] 
D HPFS - NTFS 18296 1 2 30400 254 63 194466761 
D Linux 30075 1 1 30378 254 63 4883697 
D Linux Swap 30379 1 1 30400 254 63 353367 
 
 
Structure: Ok. Use Up/Down Arrow keys to select partition. 
Use Left/Right Arrow keys to CHANGE partition characteristics: 
*=Primary bootable P=Primary L=Logical E=Extended D=Deleted 
Keys A: add partition, L: load backup, T: change type, P: list files, 
Enter: to continue 
NTFS, 247 GB / 230 GiB 
 
 
Any help will be greatly appreciated.
 
**EDIT:**
 
**Is it possible to recover data from the 2 ntfs partitions that were overwritten by the linux installation?**

---

### Post by salvachn on 2009-05-07
I'm afraid its a tough proposition, but fear not. Look here: [http://ubuntuforums.org/archive/index.php/t-916137.html](http://ubuntuforums.org/archive/index.php/t-916137.html)
I think a Windows based software will accomplish the tack better.

---

