---
title: "Partition table error - in swap - by installing Ubuntu studio"
date: 2007-10-26
forum: Desktop Environments
---

### Post by dy_wen on 2007-10-26
Hi,

Glad to say that I am a happy Ubuntu user for about two years now approximately. But last weekend I tried to install Ubuntu Studio, Gutsy Gibbon version, AMD 64, and now I have an error in my partition table.

As you can see later on, I have a dual boot as I share this computer with my better half (he likes to game, tss tss, I did convince him to intensely use The Gimp, Open Office etc :D)

The solution for my problem is quite complex, as none of these work:
- Gparted
- Qtparted
- Partition Magic on windoozzz

They all complain about my partition table error and they say that my whole hardddrive is non allocated - they are WRONG!

Fdisk does work - pfew! And it has provided me with the following info:


Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ac98ac9

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4463    35841928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2            4464       10542    48822952+   b  W95 FAT32
Partition 2 does not end on cylinder boundary.
/dev/hda3           10542       10906     2931862+  82  Linux swap / Solaris
/dev/hda4           10907       19929    72477247+   5  Extended
/dev/hda5           10907       12365    11719386   83  Linux
/dev/hda6           12366       19929    60757798+  83  Linux

lMy partition lay-out:
hda1= xp
hda2=data, in fat 32 (neutral zone between xp and linux)
hda3=swap
hda4=extended partition
hda5=root ubuntu system
hda6=home sweet home
Partiotion info (yes ze windooz again - I'm really trying everything) says this about my swap:

Error #113: Primary partition starting at 169341165 overlaps previous partition.:

Other complexifying factor: we do not have the XP cd, as it came preinstalled.

I do not mind reinstalling ubuntustudio, but I cannot as during the reinstall it does not see all these partitions.

I give you, forum, a complex bone to chew on - please accept the challenge ole!

---

### Post by chunderbunny on 2007-10-27
It's been a while since I used fdisk on anything, but have you tried cfdisk? It's like fdisk (and thus may actually work) but has a UI designed to be used by humans. 

Failing that have you tried booting from a lIveCD and fixing the partition table without mounting any part of the disk? 

In either case, it's probably a good idea to back up your data first. Messing around with partition tables can get you into trouble. Often it's easier to simply wipe the disk and start from scratch.

---

### Post by dy_wen on 2007-10-27
Hi, chunderb,

I'm afraid that cdisk does not want to run either...

      FATAL ERROR: Bad primary partition 2: logical partitions overlap
                          Press any key to exit cfdisk

The problem with reinstalling everything is the fact that I don't have the xp cd - because it was preinstalled by the shop where the computer was bought.

I'ld love to start afresh, but then I have to find a way to backup the whole windooz system, because it is still used for gaming.

Hmm it's really not easy, I know...

---

### Post by nightingale2k1 on 2008-07-17
Hi,
i am facing the same problem and i don't know how to do. 
i want to install linux mint 5, replacing the Daryna one. But it seems the swap partition got overlaped and i have no idea how to fix this error. 

plz help me. thx

---

