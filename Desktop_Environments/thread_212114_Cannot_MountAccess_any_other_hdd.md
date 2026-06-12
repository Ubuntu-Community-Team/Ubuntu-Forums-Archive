---
title: "Cannot Mount/Access any other hdd"
date: 2006-07-09
forum: Desktop Environments
---

### Post by pmagill on 2006-07-09
Hey guys I'm a real linux newbie and a bit new to forum posting.

I have been unable to access my windows partition or my fat32 partition since day 1 of my Ubuntu Dapper Drake 6.06 Install.  

Primary hd has 1 50gb ntfs partition and 1 Fat32 (for sharing between both)
slave hd has my ubuntu linux partitions which i think are fine

I have been googling my brains out up till now and would rather just ask someone rather than a search engine.

Contents of fstab (i think this is needed)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

I would love to keep using Ubuntu but I am too used to the lousy windows os that it has left me brain-dead to almost any other OS, although I learn quick so please be patient with me....thx in advance Pat

---

### Post by aysiu on 2006-07-09
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) should help.

Post back any questions you may have.

---

### Post by pmagill on 2006-07-09
wow thats quick response..

trying this now...fingers crossed

---

### Post by pmagill on 2006-07-09
Great stuff!!!

I had found that site before but thought that I could not handle it, I guess I've surprised myself thx again great forum great os I'm on my way

---

### Post by aysiu on 2006-07-09
Awesome. Copy and paste is the way to go. Glad it worked out for you.

---

