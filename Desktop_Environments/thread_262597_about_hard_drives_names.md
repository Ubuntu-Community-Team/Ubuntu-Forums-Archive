---
title: "about hard drives names"
date: 2006-09-21
forum: Desktop Environments
---

### Post by mfarouk30 on 2006-09-21
hello 

i need a help in the following problem 

1. the names that i set to partitions is not correct

see the images

i need a solution

---

### Post by az on 2006-09-21
System - Administration - Disks


Change them there.

---

### Post by mfarouk30 on 2006-09-21
> **azz said:**
> System - Administration - Disks


Change them there.

the names is ok in System - Administration - Disks

but on the desktop it is wrong

---

### Post by kflorek on 2006-09-22
My Ubuntu install picked up the desktop names from the names of the partitions. e2label can change a partition name.

 You need to know the device name. To change the name of partition hda4 to "big" you would do:

e2label /dev/hda4 big

 in a terminal screen.

To get the partition name without changing it:

e2label /dev/hda

e2label is in the package e2fsprogs.

Some distros (Fedora) use the partition names rather than device names to set up things (like booting the OS :eek: ), so watch out if you have more than one OS.

---

