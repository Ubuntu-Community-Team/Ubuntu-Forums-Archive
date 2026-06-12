---
title: "Resizing partition which Ubuntu is installed on"
date: 2005-12-21
forum: General Help
---

### Post by shirike on 2005-12-21
I've got Ubuntu installed on a single drive (plus swap) with several Windows NTFS partitions but I've got myself a new larger drive and would like to delete those Windows NTFS partitions and allow Linux to use the whole drive - how can I do this?

---

### Post by jdtanner on 2005-12-21
I believe you can use 'parted' or 'gparted'. Think of the latter as a GNU version of Partition Manager.

Cheers,
JohnT

---

### Post by alamba on 2005-12-21
I almost posted a reply to this thread earlier and stopped cos it's difficult to answer to the line "allow Linux to use the whole drive". 

Allow it in what way? You can use gparted to delete the NTFS partitions and then create a ext3 partition and use it to save your files. That's one way of letting linux use that space.

Another would be to create another swap partition and allow linux to use it as swap.

Another would be to integrate it with the / partition and let the system use the space as per it's own descretion.

Not sure what you want to use the space for.

Akshay

---

### Post by shirike on 2005-12-21
I want the entire drive to be available for use by Linux as a single partition (excluding the swap partition) - I can use gparted to resize the current Linux partition after formatting the existing partitions?

---

### Post by jdtanner on 2005-12-21
I think (!) that you should be able to delete any existing partitions using (g)parted, and then resize your existing / partition to take up the free space. You are probably best reading the (g)parted man page (*man parted* at the command line), and maybe you should carry out your work using a livecd rather than resizing from the distro that is currently using the disk?

Cheers,
JohnT

---

