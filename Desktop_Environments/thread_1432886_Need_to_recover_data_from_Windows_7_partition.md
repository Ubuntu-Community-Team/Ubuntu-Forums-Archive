---
title: "Need to recover data from Windows 7 partition"
date: 2010-03-18
forum: Desktop Environments
---

### Post by rkuper on 2010-03-18
So here is the deal.

I formatted my wifes Windows 7 Laptop and replaced it with Ubuntu 9.10. Evidently i did not get all of her pictures off of the machine before formatting it(even though i told her to move anything she wanted to keep into the folder i created for her called BACKUP). So to make a long story short i am looking for a utility that can recover NTFS file system that works with Ubuntu 9.10.

Thanks in advance.

---

### Post by dbowlin17 on 2010-03-18
look, did you reformat the entire hard drive, or do you have a dual booting system? the way to find out, is to go to places. if you see some ___ GB file system, you have dual boot. Otherwise, you wiped out all her data and don't have any (easy) way to access it, especially with it possibly already having been written over.

---

### Post by oldfred on 2010-03-18
You may be able to recover some data at best. Anything that was written over is gone, but Ubuntu is a relatively small install so the additional space used by Windows may still be there.

Do  you use or do anything with the drive as every activity is writing data. From another drive or liveCD download and run testdisk and/or photorec. They are in the repositories so you can download directly.

repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

