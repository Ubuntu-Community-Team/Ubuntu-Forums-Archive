---
title: "Root partition reporting wrong filesize after move from root.disk file"
date: 2009-12-05
forum: Desktop Environments
---

### Post by oneindelijk on 2009-12-05
Hi, 

I first installed Ubuntu9.10 from within Windows 7.
When I noticed that the Ubuntu installer created a situation whereby Ubuntu resided in the same partition and booted from a loop device, instead of from a separated partition, I tried to move the installation (since I fully configured it the way I wanted) to a new partition using dd (running a live cd).
After a whole lot of figuring out, I managed to boot into the OS, but the OS now reports the filesize of the loop device instead of the partition.
The partition manager also reports the disk being fuller than the actual size of the data.
In numbers:
[ATTACH]138714[/ATTACH]
System Monitor reports:
12.2 Gb Total  1,3 Gb Free    754 Mb Available
While Gparted reports:
19.93 Gb Total 18.22 Gb Used    1.31 Unused

Any ideas what this causes ?
Is the system still running from some kind of image ?

---

### Post by hal10000 on 2009-12-05
I never did a wuni installation, but i don't think that it is possible to copy (or move) the files from the wubi-installation to a real partition.

I guess you have to reinstall it.

---

### Post by oneindelijk on 2009-12-05
The moved installation does seem to work properly. I just updated from **.14 to **.16 and that too seems to work fine (except for some problems probably caused by lack of disk space.)
The mounted loop device did contain a fully working OS, I believe...

---

### Post by hal10000 on 2009-12-05
Maybe it works, but since you copied the wubi-**image** to your new partition, you can not use the remaining part of that partition, it will be lost.

---

