---
title: "Buffer I/O  error on one partition in Ubuntu 8.04"
date: 2009-03-05
forum: General Help
---

### Post by guptavis on 2009-03-05
Hi  all,
I have ubuntu hardy 8.04 and Windows Xp.
windows hanged and i had to restart. i started ubuntu and remounted all the ntfs drives by force mount.
In windows one fat partition cannot be accesed. it says need to format before opening. even chkdisk gives the same message.
in UBuntu Fat partition shows up but has no files and slows down the system a LOT whenever accessed. and cannot be used.
but Dc++ shows 8.8 GB still shared.
```

vishal@vishal-ubuntu:~$ sudo fsck /dev/sda1
[sudo] password for vishal: 
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Got 241664 bytes instead of 5236076 at 16384
vishal@vishal-ubuntu:~$ 

```

the fat partition is first partition (sda1) 10GB on my second hard drive. other partitions on that drive work fine. screenshots of Gparted, fstab, properties window (sometimes shows 45 items totaling 8.8 GB and sometimes shows blank), dc++is shown.

ive been searching like crazy on the forum andon the net but cant find the solution. some ofthe data on that partition is really important.
Please advise on how to solve this... Thanks!

---

