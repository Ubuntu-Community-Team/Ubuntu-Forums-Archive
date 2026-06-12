---
title: "Moving partition out of extended?"
date: 2009-03-26
forum: General Help
---

### Post by flameo993 on 2009-03-26
I used to have Windows XP, Windows 7, and Linux 8.04 on my laptop. I deleted Windows XP (my boot partition) and my Linux partition from my laptop. Now all that's left is a partition with Dell MediaDirect and an extended partition with Windows 7 and another NTFS partition I keep my music etc. on. Windows won't boot with Windows 7 in an extended partition, so is there any way for me to get Windows 7 out of the extended? I'm currently using my Ubuntu 8.04 live CD and here's my comfiguration:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe019eb72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
/dev/sda3          208845   625137344   312464250    5  Extended
/dev/sda5          208908   301266944   150529018+   7  HPFS/NTFS
/dev/sda6   *   317942478   619000514   150529018+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   208782, Id=de
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=   208845, size=624928500, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=   208908, size=301058037, Id= 7
/dev/sda6 : start=317942478, size=301058037, Id= 7, bootable

The reasoon sda6 is boot is because I tried making that the boot partition just to see if it would work. sda1 is some random dell utility, sda3 is the extended partition and it contains sda5 (My Media) and sda6 (Windows 7). If I could get sda6 out of sda3 without destroying my data, that would be great.

---

### Post by kestrel1 on 2009-03-26
I would suggest that if you want to keep the install, clone the partition & restore it to a primary, non-extended partition. You could use clonezilla for this: [http://clonezilla.org/](http://clonezilla.org/)

---

