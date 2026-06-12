---
title: "partition not listed"
date: 2008-12-11
forum: General Help
---

### Post by pennyminstrel on 2008-12-11
Just what I hope is a small question........

I'm trying to move the mount point of one of my partitions, using the instructions here: [URL="http://https://help.ubuntu.com/community/MoveMountpointHowto"]. I ran sudo fdisk -l to check the information, but my partition isn't listed. I've tried doing it with the partition mounted and not mounted with the same result.

Anybody know why this might be?

thanks
Penny

---

### Post by wizard10000 on 2008-12-11
> **pennyminstrel said:**
> Just what I hope is a small question........

I'm trying to move the mount point of one of my partitions, using the instructions here: [URL="http://https://help.ubuntu.com/community/MoveMountpointHowto"]. I ran sudo fdisk -l to check the information, but my partition isn't listed. I've tried doing it with the partition mounted and not mounted with the same result.

Anybody know why this might be?

Hi, Penny - 

Need a little more information, please - I have a bit of a tough time with the idea that fdisk can't see a mounted partition.

What's the mount point?  Can you give a little information about the missing partition and post the output of fdisk -l?

tanks!

---

### Post by logos34 on 2008-12-11
hmm, fdisk should list all partitions, mounted or not.

try

sudo lshw | grep logical

do you see it listed?

---

### Post by pennyminstrel on 2008-12-12
Hi guys,

I ended up reinstalling everything - there were other reasons for doing that anyway- and now it's showing again, so I suppose the mystery will never be solved, but I do appeciate your responses.

Penny

---

