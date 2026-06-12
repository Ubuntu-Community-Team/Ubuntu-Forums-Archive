---
title: "Windows refusing to boot from Grub menu"
date: 2009-05-17
forum: General Help
---

### Post by samk115 on 2009-05-17
Hi. I have just installed 9.04. Now windows is refusing to boot from the grub menu. Grub is installed on the linux harddrive instead of the windows hard drive, does that make any differnece? Also my windows harddrive is IDE and my Linux is SATA, prehaps some sort of conflict?

Heres my sudo fdisk -l output:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19977efb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a0a4a4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       72584   583030948+   7  HPFS/NTFS
/dev/sdb2           72585       77825    42098332+   5  Extended
/dev/sdb5           72585       72957     2996091   82  Linux swap / Solaris
/dev/sdb6           72958       77825    39102178+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS




Any help would be cool!

OH by the way, SDa is my windows, SDb is my Linux/media(partions) and SDc is my external

---

### Post by cybergalvez on 2009-05-17
it makes all the difference in the world, Windows is to stupid to figure out how to boot off of anyting but the first drive, so you have to fool it by telling it its onthe first one.  You need to tell windows its is the first HD (even though its not) 
by using the map command,  Here is the relivent secion from my /boot/grub/menu.lst 

title		Windows XP
map		(hd0) (hd2)
map		(hd2) (hd0)
root		(hd2,0)
makeactive
chainloader	+1
savedefault

Hope it helps

---

