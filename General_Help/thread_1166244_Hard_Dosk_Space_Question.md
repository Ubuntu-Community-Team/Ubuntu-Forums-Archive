---
title: "Hard Dosk Space Question"
date: 2009-05-21
forum: General Help
---

### Post by rodocola on 2009-05-21
New to linux!
Recently I installed backtrack on my hard drive. After a couple of days I tried to download a program and got a message of not enough disk space.
I know that I have enough disk space left. Perhaps is not allocated.
My question is, how can move unused disk space to the main partition?
Here is my info:
bt / # fdisk -l
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot Start End Blocks Id System
/dev/hda1 1 365 2931831 83 Linux
/dev/hda2 366 426 489982+ 82 Linux swap
bt / # sfdisk -l
Disk /dev/hda: 155061 cylinders, 16 heads, 63 sectors/track
Warning: The partition table looks like it was made
for C/H/S=*/255/63 (instead of 155061/16/63).
For this listing I'll assume that geometry.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0
Device Boot Start End #cyls #blocks Id System
/dev/hda1 0+ 364 365- 2931831 83 Linux
/dev/hda2 365 425 61 489982+ 82 Linux swap
/dev/hda3 0 - 0 0 0 Empty
/dev/hda4 0 - 0 0 0 Empty

---

### Post by KhurramM on 2009-05-21
Use gparted

This is a gui tool.

Remember the old drill: backup all important data first.

Now repartition as u wish.

---

### Post by rodocola on 2009-05-21
Thanks, I will give that a try.

---

### Post by rodocola on 2009-05-21
Using gparted I found the unallocated space and created a new partition ext2. When I try to download and save a file I dont know how to save it to the hda3 partition.
 
Do I need to mounted so the main hda1 sees it?

---

