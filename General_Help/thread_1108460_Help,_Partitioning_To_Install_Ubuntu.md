---
title: "Help, Partitioning To Install Ubuntu"
date: 2009-03-27
forum: General Help
---

### Post by Cresar on 2009-03-27
Well, I'm ready for my first ubuntu installation with Windows XP and this is my question:
Are the partition with Partition Magic, as Ext3, after the C: / not to lose my windows ....
In this partition, it has to be logical or primary?
A portion of the partition where installing ubuntu, the Ext3 format I need to do another swap partition or otherwise?

---

### Post by rjl6591 on 2009-03-27
You need two partitions for linux - one for the ext3 filesystem, one for swap. They can be either logical or primary.

---

### Post by sam1948 on 2009-03-27
i have lots of experience with gparted
which have a live cd version and i also thing exists in the ubuntu live cd

run that program 
make the XP drive smaller
live about 12 Gb free space
create new partition with about 10 Gb as ext3 for the root mount point "/"
and the rest as swap partition

now during the ubuntu installation select manual partitioning and set the ext3 partition as "/" and to be formated

good luck

---

### Post by goettlek on 2009-03-27
What Sam did is what I did on my first installation. I wanted to dual boot Vista and Ubuntu Studio so I shrunk my Windows partition down by 20GB and then a bit more for swap. I left it as free space and then when it came to the part where it asked where to install to, I pointed to "Guided - Use the largest contiguous free space" and selected the remaining free space as swap space.

---

### Post by sam1948 on 2009-03-28
I can't be more agree (:

---

### Post by Cresar on 2009-03-28
Well, as you are, are from the windows partition to install Ubuntu in Ext3 (I'll give you about 15-20 Gb since my intention is not always live in unn ubuntu since I gammer) and then during installation, are also another partition manually interchange format 430Mb ....
This is well ¿
> cambiar

---

