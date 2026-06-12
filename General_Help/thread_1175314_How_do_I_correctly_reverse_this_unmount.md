---
title: "How do I correctly reverse this unmount?"
date: 2009-06-01
forum: General Help
---

### Post by heroes_on_a_half_shell on 2009-06-01
_Caveat: _ 
I already went through the process to automount a pre-existing ext3 "Data" partition.

_Incorrect Action on My Part: _
I used ```
sudo nautilus
``` and clicked the eject button next to my /media/Data aka /dev/sda4 in the left-hand pane.

_Problem:_  
Upon restart, the drive no longer automounts, but I can see it in the nautilus left-hand pane.

```
sudo mount -a
``` yields: "mount: mount point /media/Data does not exist"

```
sudo fdisk -l
``` yields:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536   83  Linux
/dev/sda2            6080       16827    86333310   83  Linux
/dev/sda3   *       16828       22564    46082048    7  HPFS/NTFS
/dev/sda4           22565       36481   111788302+  83  Linux

line I inserted into /etc/fstab (which worked previously):

/dev/sda4	/media/Data	ext3	defaults	0	2

_Preferred Solution:_
Anything which does not screw up my system.  I've been running Jaunty for about 2 weeks, and it has quickly become my favorite release (Ubuntu since 7.04)

_My Next Guess?:_
```
sudo mkdir /media/Data
sudo mount -a
```

---

