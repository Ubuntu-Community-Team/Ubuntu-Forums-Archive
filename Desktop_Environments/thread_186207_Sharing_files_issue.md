---
title: "Sharing files issue"
date: 2006-06-01
forum: Desktop Environments
---

### Post by mighk on 2006-06-01
hi, i need to access files in my ubuntu partition whilst running edubuntu, (it's a long story)](*,) ](*,)

---

### Post by Sutekh on 2006-06-02
[quote=mighk]hi, i need to access files in my ubuntu partition whilst running edubuntu, (it's a long story)](*,) ](*,)[/quote]
So Ubuntu and Edubuntu are on separate partitions?

First you need to identify the location of the Ubuntu partition.
```
sudo fdisk -l
```
will list the partitions on your hard discs.

Say, for this example the Ubuntu partition existed on **/dev/hda1**.  Next create a folder to mount it to.
```
sudo mkdir /mnt/hda1
```
Finally mount the Ubuntu partition using
```
sudo mount /dev/hda1 /mnt/hda1 -t ext3
```
Then you should be set.

---

### Post by mighk on 2007-01-31
thanks sutekh, that's a winner
mighk

---

