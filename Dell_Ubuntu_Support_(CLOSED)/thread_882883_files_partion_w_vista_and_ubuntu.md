---
title: "files partion w/ vista and ubuntu"
date: 2008-08-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by davidmiller252 on 2008-08-07
I'm getting a new inspiron 1525 pre-installed with vista and with a 250G hdd. I want to keep vista on my computer so I'm planning on dual booting it with ubuntu. the thing is that I want to be able to access files on vista with ubuntu and vice versa. I don't really know how partitions work cross-platform but would it be possible to make a partion in vista with partion magic 8 or some other application like that formatted in FAT32 and be readable by ubuntu?

---

### Post by allenbradley on 2008-08-07
vista has its own in built partition manager which can do rudimentary partitioning, which has a really simple to use gui. After creating thecommon data partition, use the partitioner on ubuntu to create thelinux partition of your choice.

---

### Post by unutbu on 2008-08-07
Linux can read and write all windows filesystem types (fat16, fat32, NTFS). 

Windows can not natively read/write ext3, the native Linux filesystem type, but it can if you install fs-driver [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by davidmiller252 on 2008-08-08
Thanks a lot!
I'll probably just install the Ext2 IFS

---

