---
title: "Internal Harddrive Partitions do not show up"
date: 2013-11-15
forum: Desktop Environments
---

### Post by Niko.com.au on 2013-11-15
I have two accounts on my ubuntu 12.04. On my main account, any internal harddrive partitions do not appear and the sidebar in the home folder doesn't appear either. To get onto any internal partition (except root) I have to manually mount the partition. These problems have only come up quite recently but my other account has none of these problems.
Please Help!

---

### Post by deadflowr on 2013-11-15
How many operating systems on the machine are there?
And how many partitions are you expecting to see?

both
```
sudo fdisk -l
```
and
```
sudo parted -l
```
will show the current system partitioning layout.

---

