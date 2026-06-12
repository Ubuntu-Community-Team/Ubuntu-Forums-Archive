---
title: "How do I view my ubuntu drives in windows when I click on &quot;My Computer?"
date: 2009-05-07
forum: General Help
---

### Post by skaught78 on 2009-05-07
No access to them in windows. Is there a way to get the partitioned drive to show up in windows?

---

### Post by antmenj on 2009-05-07
What file system are you using on your ubuntu partition?

You would have selected the type when you installed ubuntu.

---

### Post by geirha on 2009-05-07
This driver should allow you to see ext2 and ext3 filesystems at least.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by colau on 2009-05-07
> **geirha said:**
> This driver should allow you to see ext2 and ext3 filesystems at least.
[http://www.fs-driver.org/](http://www.fs-driver.org/)
I am not sure whether this ext2Ifs driver will work or not.

---

### Post by dandnsmith on 2009-05-07
Reading the FAQ, release notes etc
1. it won't work on 'new' style FS with 256 byte inodes
2. it may not work for ext3 - depends on circs

It has the advantage of one tool I tried recently (Linux Reader) of not needing to extract files to read them (also, LR is confusing in that multiple linux partitions seem not to be readily identifiable).
I'm still intending to chase down an older tool I had which allowed direct inspection (but I've lost the info due to system rebuilds).

Just found the one I was looking for: [explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by salvachn on 2009-05-07
EXT2IFS won't work with loopback devices, so if you have installed Ubuntu inside Windows, its quite a tough task. And remember not to mount swap partitions!

---

### Post by konqueror7 on 2009-05-07
try [ext2fsd]("http://sourceforge.net/projects/ext2fsd/")...

---

