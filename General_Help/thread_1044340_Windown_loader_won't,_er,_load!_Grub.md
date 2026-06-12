---
title: "Windown loader won't, er, load! Grub"
date: 2009-01-19
forum: General Help
---

### Post by joey-elijah on 2009-01-19
I finally managed to fix my grub issues, but the windows loader won't load from grub now. 

I've tried working out the grub (X,Y) for the partition windows is on, but i get nowhere. 

It's on a partition called "sdb2" - one of MANY partitions i have. I' made too many paritions a while back, but whenever i try to merge them or foramt i get a warning that it'll render any 'os' on the drive unbootable. So i'm stuck with about 80GB of unsuable space! Ack!

Anyway, can anyone kindly help?

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x682a8121

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3033    24362541   83  Linux
/dev/sda2            3034        6881    30903296    7  HPFS/NTFS
/dev/sda3           10833       17895    56726528    7  HPFS/NTFS
/dev/sda4           17896       19457    12546765    5  Extended
/dev/sda5           17896       19457    12546733+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              26        5140    41078784    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7087ef7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS
joey@ibex:~$ 

```

Windows 7 is on a 42.1GB Partition (places) - which shows up as 39~GB in paritions etc so i assume it's the right one.

---

### Post by logos34 on 2009-01-19
What's on  sdb1? If it's also a bootable windows system c: partition, maybe the bootfiles for both OS's are there (i.e  if you installed windows 7 after whatever is on sdb1, the bootfiles will be located there). At least it's got the boot flag ('*').

gksudo gedit /boot/grub/menu.lst

try one of these entries (if you're booting from sda you'll need 'map' lines for windows):

> title windows 7
root (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1 

Or 

> title windows 7
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

or maybe the drive is being seen in third postition by the Bios, in which case:

> root (hd2,1)
map (hd0) (hd2)
map (hd2) (hd0)


Or 
> 
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)

etc.

---

### Post by joey-elijah on 2009-01-19
cheers! will try and see now!

---

