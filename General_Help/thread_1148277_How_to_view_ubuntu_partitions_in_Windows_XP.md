---
title: "How to view ubuntu partitions in Windows XP"
date: 2009-05-04
forum: General Help
---

### Post by accooper on 2009-05-04
I would like to be able to see what is in my ubuntu partitions when I run Windows XP.  Is there a program that will allow me to do so?

TIA

:guitar:

Andrew

---

### Post by canadiandude007 on 2009-05-04
You probably mean something like this:

[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)

---

### Post by ki87mi on 2009-05-04
that software is for ext2 and ext3, but i haven't find the one for ext4

---

### Post by lucianct on 2009-05-04
ext3 is partially compatible with ext4, so if you don't use advanced features of ext4 you would be able to mount it as ext3 under windows. using the default installation of jaunty and ext2fs i managed to see only the directories in / but not to access them. if you really need to access files from windows you can create an ext3 partition and mount it as /home in jaunty, or save your files on a fat/ntfs partition.

---

