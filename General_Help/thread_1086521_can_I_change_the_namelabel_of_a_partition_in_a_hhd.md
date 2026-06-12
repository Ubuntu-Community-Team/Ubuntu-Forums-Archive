---
title: "can I change the name/label of a partition in a hhd while saving all data"
date: 2009-03-04
forum: General Help
---

### Post by ozguitarplayer on 2009-03-04
Hi, I need to change the name of a partition formatted to fat32 that is an extended partition of a hhd.

Can this be done while saving all data in the partition..and if it can be done then how..?

---

### Post by gracc on 2009-03-06
Yep no worries,
Make sure you have the partition editor Gparted) downloaded from synaptic.
Make sure the drive you are renaming is unmounted.

top of desktop goto :

system -> administration -> Partition editor

In the partition editor:

Select the hard drive at top right of window.
List of partitions is displayed for that drive.

Left click to highlight the partition in the list that you want to rename.

Then at the top of the Partition editor window :
partition -> Label
Enter new name in the pop up box.
click ok

Select Apply at top of window,apply in pop up window again , then close next pop up window.

Highlight the same partition again.
partition -> Manage flags -> boot -> close     (tick the boot option)

THEN :

Highlight the same partition again.
partition -> Manage flags -> boot -> close     (UNTICK the boot option)

Finished

my first time here, hope that is clear enough if not , call

catcha

---

### Post by ozguitarplayer on 2009-03-06
perfect, thanks gracc...

---

### Post by gracc on 2009-03-06
glad to be of help.

You can do exactly the same with sd cards and usb sticks.
However but leave the the boot option ticked.

---

