---
title: "2nd EXT3 hard drive"
date: 2006-07-03
forum: Desktop Environments
---

### Post by nabberuk on 2006-07-03
i have ubuntu 6.06 installed on my 40gb hdd (hdc) and i have a 160gb hdd (hdd) that i would like to get up and running for my data files. 

When i go into System > Administration > Disks the 160gb is greyed out and i cannot format/partition or do anything with it. At the moment there are no partitions on this hard drive.

I've tried various things using fdisk and cfdisk. nothing seems to work though. so any pointers on how to format it into one big ext3 partiition.

thankful for any help.

nath

---

### Post by tonyr on 2006-07-03
Try **System->Administration->Gnome Partition Editor** and see what that says.
In a terminal, what does **sudo fdisk -l** report?

---

### Post by nabberuk on 2006-07-03
i dont have the gnome partition editor, couldn't find the package either. 
The output from fdisk is;

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4664    37463548+  83  Linux
/dev/hdc2            4665        4865     1614532+   5  Extended
/dev/hdc5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdd: 163.9 GB, 163928604672 bytes
1 heads, 63 sectors/track, 5082112 cylinders
Units = cylinders of 63 * 512 = 32256 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1           1           0+  83  Linux


many thanks.
nath

---

### Post by tonyr on 2006-07-03
The name of the Gnome Partition Editor package is **gparted**.  It is not (or used
to be not) included in the default installation.  I don't recall which repository it is in,
but you may have to add **universe** and/or **multiverse** repositories.  You
can do this in **Synaptic** or by editting **/etc/apt/sources.list** directly.

It looks like you did **something** with **fdisk**, because there is Linux
partition defined for **hdd** (although it is **very** strange).

---

### Post by nabberuk on 2006-07-03
couldnt find gparted in the package manager, but just did a apt-get from the terminal. It is sooooo much easier with gparted to sort it all out!

Many thanks for your help!

---

