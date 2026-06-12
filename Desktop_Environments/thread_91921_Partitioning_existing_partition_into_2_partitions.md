---
title: "Partitioning existing partition into 2 partitions"
date: 2005-11-18
forum: Desktop Environments
---

### Post by n!x on 2005-11-18
I would like to have my existing partition (ext3) partitioned into 2 partitons so that I could share a FAT32 partition with my XP laptop.

My Ubuntu server is having 1 (one) partition (ext3), a 120 GB drive and I would like to have about 100 GB partitioned into a FAT32 format so that I can share it over my local network.

I would appreciate some help to avoid deleting my Ubuntu installation.

Is it possible to partition it without deleting my Ubuntu installation? And how?

Thanks in advance!

/n!x

---

### Post by daller on 2005-11-18
[QUOTE=n!x]I would like to have my existing partition (ext3) partitioned into 2 partitons so that I could share a FAT32 partition with my XP laptop.

My Ubuntu server is having 1 (one) partition (ext3), a 120 GB drive and I would like to have about 100 GB partitioned into a FAT32 format so that I can share it over my local network.

I would appreciate some help to avoid deleting my Ubuntu installation.

Is it possible to partition it without deleting my Ubuntu installation? And how?

Thanks in advance!

/n!x[/QUOTE]

Gparted it is...

Install gparted, it's an excelent partitioner...

...If you are talking about a mounted partition, you may have to use a live-cd - but you can install it there as well...

Good luck!

---

### Post by daller on 2005-11-18
Wow, you wanna share it in a network?

...Then you don't have to change it into FAT32, do you?

---

### Post by n!x on 2005-11-18
Yes I want to share it on a network - can I share a drive(ext3) over a network(smb) without having to partition it to FAT32?

---

### Post by n!x on 2005-11-18
I seems that I don't have to partition it to FAT32 to share it over smb.

Thanks for help!

---

