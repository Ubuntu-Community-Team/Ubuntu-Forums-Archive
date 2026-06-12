---
title: "Ubuntu sees only first 32Gb of a FAT32 volume"
date: 2006-09-17
forum: Desktop Environments
---

### Post by talkingwires on 2006-09-17
I have two 60Gb hard drives: one is split into NTFS and Ext3 partitions, for Windows and Ubuntu, and the other is a single 60Gb FAT32 partition for shared files. Now, as you probably know Windows can't format a FAT32 partition larger than 32GB, but has no problem reading one. Unfortunately, Ubuntu does! Windows can see the full 60Gb partition, but Ubuntu has it capped at 32GB.

At first, I thought I'd incorrectly formatted it, but a quick check in Partition Magic shows the entire volume is formatted. How can I fix this?

---

### Post by lagagnon on 2006-09-17
Please read:

[http://support.microsoft.com/kb/184006/](http://support.microsoft.com/kb/184006/)

---

