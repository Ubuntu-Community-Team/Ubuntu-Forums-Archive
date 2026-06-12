---
title: "Partitions does not end on cylinder boundary"
date: 2009-03-15
forum: Desktop Environments
---

### Post by 8yun on 2009-03-15
I just noticed, maybe after I installed Windows 7 on my laptop, the partition table show overlapped. Here is output from **sudo fdisk -l**:


laptop:~$ sudo fdisk -l
[sudo] password for roger: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         678     5444608   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             679        2502    14643720   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3            5062       19457   115630200    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4   *        2502        5062    20563200    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5            5062        5323     2094088+  82  Linux swap / Solaris
/dev/sda6            5323       19457   113536048+  83  Linux

Partition table entries are not in disk order


when I run **sudo testdisk** and analyze it, output is:

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Sys=27                   0  32 33   677 242 13   10889216

Bad sector count.
 2 P Linux                  678 150  1  2501 164 63   29287440

Bad relative sector.
 3 E extended              5061 165  1 19456 239 63  231260400
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 4 * HPFS - NTFS           2501 165  1  5061 164 63   41126400
 5 L Linux Swap            5061 166  1  5322  89 63    4188177
   X extended              5322  90  1 19456 239 63  227072160
 6 L Linux                 5322  91  1 19456 239 63  227072097 [NewVol]


 Any idea what is the problem here? how to fix it?  My ubuntu version is 8.10 intrepid.

Roger

---

### Post by vandorjw on 2009-03-15
The easiest way to fix this would be such.

1) Backup everything that is important to you.

2) Insert windows 7 Disk and wipe the system. Delete all partitions, and make a partition for swap **, Ubuntu and windows 7. Install windows 7.

Then when that is done. Install Ubuntu on the partitions that you made with win 7. (Reformat them to ext3)

Many people will have gparted automatically resize their partitions, but I am unsure of this as I feel it might mess up sometimes.

Always plan ahead. :)

Cheers - CC7

---

### Post by 8yun on 2009-03-15
> **cc7gir said:**
> The easiest way to fix this would be such.

1) Backup everything that is important to you.

2) Insert windows 7 Disk and wipe the system. Delete all partitions, and make a partition for swap **, Ubuntu and windows 7. Install windows 7.
ll 
Then when that is done. Install Ubuntu on the partitions that you made with win 7. (Reformat them to ext3)

Many people will have gparted automatically resize their partitions, but I am unsure of this as I feel it might mess up sometimes.

Always plan ahead. :)

Cheers - CC7

Thanks CC7, but it is pain to install everything again. If there is another solution, I would prefer to maintain what it is except the problem. someone said testdisk could fix the problem, however, it didn't work for me. any other idea?

---

### Post by meierfra. on 2009-03-15
Your "fdisk -l" looks perfectly normal.  You can ignore the  "does not end on cylinder boundary" warning.  Partitions used to have to end on "cylindrical" bounds. But these days everything is   calculated in terms of sectors. So from Vista on, Windows started using  partitions which do not end on cylindrical bounds. This does not cause any problems.


The "bad sector count" and "bad relative sector" warning are due to the different geometries (240 versus 255). But again  nobody actually   uses these geometries. So you can also ignore the testdisk warning.


So as far as I can see, there is nothing wrong with your partition table.

---

### Post by 8yun on 2009-03-15
> **meierfra. said:**
> Your "fdisk -l" looks perfectly normal.  You can ignore the  "does not end on cylinder boundary" warning.  Partitions used to have to end on "cylindrical" bounds. But these days everything is   calculated in terms of sectors. from Vista on, Windows started using  partitions which do not end on cylindrical bounds. This does not cause any problems.


The "bad sector count" and "bad relative sector" warning are due to the different geometries (240 versus 255). But again  nobody actually   uses these geometries. So you can also ignore the testdisk warning.


So as far as I can see, there is nothing wrong with your partition table.

Is that so? that is much released. I am so worry about that my data may be corrupted as the partition overlapped. Thanks meierfra.

---

### Post by meierfra. on 2009-03-15
> as the partition overlapped.

I don't see any overlapping partition.

/dev/sda3 is  an extended partition (that is, a container for other partitions) which contains the logical partitions /dev/sda5 and /dev/sda6.

Have a look  at the output of 

```
sudo fdisk -lu 
```

That list starts and end points  in terms of sectors and might give  a little  better picture.

Also   have a look at the partition with gparted

```
sudo apt-get install gparted
gksudo gparted
```

---

### Post by 8yun on 2009-03-15
the command output is:

sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    10891263     5444608   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2        10901520    40188959    14643720   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3        81315360   312575759   115630200    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4   *    40188960    81315359    20563200    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5        81315423    85503599     2094088+  82  Linux swap / Solaris
/dev/sda6        85503663   312575759   113536048+  83  Linux

Partition table entries are not in disk order

it is clear that no overlapped. thank you very much!:popcorn:

---

