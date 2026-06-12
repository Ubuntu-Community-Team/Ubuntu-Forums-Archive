---
title: "repartitioning problem"
date: 2006-01-14
forum: General Help
---

### Post by ruzle0 on 2006-01-14
i have a disk with these partitions, listed in the physical order they lie on the disk:
/dev/hda9  ext3    30GB    ubuntu root & home
/dev/hda5  fat32   12GB    to share with windows install on other disk
/dev/hda6  ext3      6GB    root of another distro
/dev/hda7  swap     1GB
/dev/hda8  ext3    30GB    home of other distro

i have decided to stick with ubuntu and want to use the space from the old distro by merging hda6 into hda5 and then reformat hda8 to clean it, but probably keep it as a separate partition.
the problem is if i want to remove one of the partitions (using Gparted) i need to unmount the partitions of a higher number. as my root is hda9 this is a problem.

so is it possible or worth while to rename the partition my system runs off, or is there another way to go about it.
failing that i was thinking about simply resizing hda5 and 6 with one to the minimum size then ignoring it, but if i can learn something more elegant all the better

---

### Post by fourchannel on 2006-01-14
im not too familiar with resizing partitions, and especially with logical ones. but you might try fdisk instead of gparted.
 
```
$ sudo fdisk /dev/hda
```
 
but fdisk is not nearly as safety conscious as gparted, and if you don't know what you are doing you can easily corrupt the entire drive. but...
 
in fdisk, no changes are made until you type 'w' , and likewise, you can exit fdisk with 'q'

---

