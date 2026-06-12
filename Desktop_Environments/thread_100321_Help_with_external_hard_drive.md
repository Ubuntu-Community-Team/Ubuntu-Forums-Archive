---
title: "Help with external hard drive"
date: 2005-12-07
forum: Desktop Environments
---

### Post by awtomlinson on 2005-12-07
i will soon have a 300gb external hard drive.  this backup drive will store my music, pics, docs, etc to be shared between winxp & breezy.  i want to make the drive fat32 for compatibility reasons, but i have heard that winxp can recognize fat32 partitions only up to 32gb.  i have also heard that winxp can read larger fat32 partitions if the drive was formatted by another os (linux).  can anyone give me some recommendations?  i definitely don't want a bunch of 32gb partitions on this 300gb drive.

---

### Post by frodon on 2005-12-07
No, i have 2 70Go FAT32 partitions so i confirm that you're not limited to 32Go. However i don't advice you to format 300Go in FAT32 because it doesn't support files larger than 4Go and it also doesn't support unix rights.
If i was you i would format between 200Go and 250Go with ext3 FS and between 50Go and 100Go with FAT32 FS to share easily files between the 2 OS.

---

### Post by awtomlinson on 2005-12-07
but winxp can't read ext3.  i normally use reiserfs with linux.  my shared files will never be bigger than 4 gb, but the folders will be.  any thoughts?

---

### Post by frodon on 2005-12-07
Yes it can : 
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
and
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

However i think the write support isn't enough safe for the moment but no problem for read access.

---

### Post by aysiu on 2005-12-07
[QUOTE=awtomlinson]i have heard that winxp can recognize fat32 partitions only up to 32gb.[/quote] Up until only a few days ago I'd spent months using a 100 GB FAT32 partition to share documents between Windows XP and Ubuntu.

> i have also heard that winxp can read larger fat32 partitions if the drive was formatted by another os (linux). My 100 GB FAT32 partition was formatted using Mandriva's DiskDrake.  

> can anyone give me some recommendations?  i definitely don't want a bunch of 32gb partitions on this 300gb drive. I'd recommend making 100 GB of it NTFS, 100 GB of it FAT32, and 100 GB of it Ext3.

Do you have any files bigger than 4 GB?

---

### Post by awtomlinson on 2005-12-07
no files bigger than 4 gb, but directories/folders, yes.  i would like to keep a chunk available for windows games, but the majority i would like to be fat32 for shared docs, music, pics, etc. for both operating systems.  or should this be ext3?  i want the most compatible format for both systems, so please no linux biases!

---

### Post by aysiu on 2005-12-07
FAT32 is the only filesystem that I know of that's 100% compatible for read/write between Windows *and* Linux.

The only reason I advise against using all 300 GB for FAT is that FAT gets fragmented so easily.

---

### Post by frodon on 2005-12-07
And FAT32 doen't support unix rights and ownership therefore you will have 777 rights on it under linux which is not a secure way to use a partition.
There isn't a perfect choice i think, try to know what you think your needs will be and then decide ...

---

### Post by awtomlinson on 2005-12-07
this is a windows question, so i apologize.  but, would games stored on the external drive run slow or normal speed?

---

### Post by stalefries on 2006-04-24
Definitely slow, especially if it's USB. YOu won't get near the same speed as internal.

---

