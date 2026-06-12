---
title: "Gparted with locked partition"
date: 2006-02-06
forum: Desktop Environments
---

### Post by JeffBlouin on 2006-02-06
I one more little problem:

I have linux installed onat HDA2 (ext3) 30 gigs and Windows on HDA1 (ntfs) 5 gigs
and I want to resize HDA2 to make an HDA3 fat32 partion to share files between  win and linux.  The problem is that there is a lock sign infront of HDA2 and I cannot do anything to that partition (like resizing it)

any idea?

Thanks!
Jeffblouin

---

### Post by Denis on 2006-02-06
Ik looks like the partition is locked because you are currently reading from that partition, it is mounted on / (root directory). When you want to format a partition (and I guess it's also true for a resize), the partition may not be mounted. 

Since this partion is mounted when you are running your operation sytem, you have to use an other operation system or a live CD to make changes. The best thing to do is to get a live CD (Ubuntu, Knoppix or whatever), boot from the CD and use that system to do the adjustments on that partition.

I hope this helps you out.

---

### Post by Ramses de Norre on 2006-02-06
[http://www.fs-driver.org/]("http://www.fs-driver.org/")
This program allows you to read and write safely on an ext2 or ext3 partition from windows. I think it might be a better way to communicate between them. It works perfect for me.

---

