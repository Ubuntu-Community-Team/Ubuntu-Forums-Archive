---
title: "e2fsck reports errors. How bad are they and what should I do about them?"
date: 2016-06-27
forum: Desktop Environments
---

### Post by cornellg on 2016-06-27
Hi all,

I want to shrink a logical volume with an ext4 fs and needed to check its stability beforehand. e2fsck returns these errors:
```

sudo e2fsck -f /dev/ubuntu/CornellHomeLV 
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 1573549 has zero dtime.  Fix<y>? no
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? no
Inode 1573624 was part of the orphaned inode list.  IGNORED.
Inode 1573704 was part of the orphaned inode list.  IGNORED.
Inode 6816782 was part of the orphaned inode list.  IGNORED.
Inode 6816785 was part of the orphaned inode list.  IGNORED.
Inode 6816786 was part of the orphaned inode list.  IGNORED.
Inode 6817130 was part of the orphaned inode list.  IGNORED.
Inode 6817136 was part of the orphaned inode list.  IGNORED.
Inode 6817141 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  +529169 -(6325776--6325779) -(6327796--6327799) -(27425797--27425800) -28360197 -(28360200--28360203) -65116701 -(65117210--65117213)
Fix<y>? no
Free blocks count wrong for group #16 (23095, counted=23096).
Fix<y>? no
Free blocks count wrong (124293372, counted=124293373).
Fix<y>? no
Inode bitmap differences:  -1573187 -1573549 -1573624 -1573704 -6816782 -(6816785--6816786) -6817130 -6817136 -6817141 -15469970 -23333138 -23335442 -23335570
Fix<y>? no
Free inodes count wrong for group #1888 (8183, counted=8182).
Fix<y>? no
Free inodes count wrong for group #2848 (7990, counted=7987).
Fix<y>? no
Free inodes count wrong (32749843, counted=32749839).
Fix<y>? no

/dev/ubuntu/CornellHomeLV: ********** WARNING: Filesystem still has errors **********

/dev/ubuntu/CornellHomeLV: 18157/32768000 files (1.7% non-contiguous), 6778628/131072000 blocks
```

Should I just go ahead and let it fix them or can this have negative consequences? 
I believe the errors are due to numerous reboots of varying sorts as a result of system freezes caused by the nvidia drivers. A few days prior to those I made a backup of the partition using rsync -aAXv. That backup does not contain the errors when I use e2fsck. Is there a way to find out precisely what files are/might be corrupted and simply retrieve them from the backup? Or will all be well if I just let e2fsck do its magic? 

I would love some advice. Needless to say I have not yet shrunk the volume.
Many thanks!

---

### Post by sudodus on 2016-06-27
0. ***Backup*** all data, that you cannot afford to lose. This is ***always important***, particularly when doing this kind of operation.

1. I think that you can ***let e2fsck fix the system*** (answer y instead of n). I have let if fix things several times, and it has been successful many times and failed only once, and then I could rely on the backup.

2. While you are at it, you might as well ***check for bad sectors*** (physical defects) by adding the option -c to your command line.

```
sudo e2fsck -cf /dev/ubuntu/CornellHomeLV
```

[COLOR="#696969"]From ```
man e2fsck
```

```
       -c     This option causes e2fsck to use badblocks(8) program  to  do  a
              read-only  scan  of  the device in order to find any bad blocks.
              If any bad blocks are found, they are added  to  the  bad  block
              inode  to  prevent them from being allocated to a file or direc&#8208;
              tory.  If this option is specified twice,  then  the  bad  block
              scan will be done using a non-destructive read-write test.
```
[/COLOR]

---

### Post by cornellg on 2016-06-27
Thanks sudodus,

It worked fine. I will check for bad sectors too, sounds like a good precaution.

Gracias!

---

