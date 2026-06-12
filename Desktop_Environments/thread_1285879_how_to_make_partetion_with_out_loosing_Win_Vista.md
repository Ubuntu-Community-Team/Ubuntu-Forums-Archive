---
title: "how to make partetion with out loosing Win Vista"
date: 2009-10-08
forum: Desktop Environments
---

### Post by tester22 on 2009-10-08
hi every body i need your suggations to make a **backup partetion** on my **win vista** operating system computer. i got total 500GB HDD, but the size of **C: is 470GB** in which win vista installed & the size of **D: is 30 GB** in which **Factory image** is there by the manufacturar. this both are very very important for me, i never ever like to loose, this is brand new computer.
 
So with out **loosing/deleting** win vista in C: partetion, i want to make another backup partetion of **size 400GB** for backup important files saperately & remaining 70 GB for live win vista. so which tools i have to use and how to do this all.
 
Thanks in advanced for your suggations.

---

### Post by ArcaVex on 2009-10-09
Acronis partition expert will do what you require. Of course it depends how much space you are using already on the C:  (Vista) partition.

Resizing from 470GB to 70 may cause you to lose files (if you are using say 80GB)
Perhaps back up your important files onto a DVD first, then resize.

alternatively if you are going to install linux then the install will provide partition resizing anyway.

---

### Post by LinLux451 on 2009-10-10
I would run a defrag on Vista, backup all the important stuff to a DVD, then boot up with a Live! disk and see how things work from there. The live! disks come with gparted now, but don't quote me. Things are always a little funny with editing existing partitions, but if you back up everything you should be okay.

---

### Post by oldfred on 2009-10-10
How are you backing up your Vista partition? If it is 470GB you need a large partition for the backup on an external drive.

IF has been said that it is best to use the Vista patitioner to resize but it it not vital anymore as long as you use current updated versions.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

Windows Vista - partition your hard drive using Disk Management
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

