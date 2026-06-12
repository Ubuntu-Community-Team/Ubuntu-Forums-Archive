---
title: "How do I resize a ext3 partition"
date: 2006-09-27
forum: Desktop Environments
---

### Post by willz06jw on 2006-09-27
Thanks for looking at my problem,

I am trying to resize an Ext3 partition from 60 gigs to use all of the 140 gigs of free space from the command line (im using SSH).  

First I don't know the names of the partitions
Second I don't know jack about expanding partitions through the command line in SSH.

This help is really appreciated,
Thanks!,

William Howard

---

### Post by whizbaby on 2006-09-27
The command 
**parted**
does quite good for that purpose. If not there **apt-get install parted**.
(**man parted**, for a manual, but I think you knew that)

---

### Post by Cable on 2006-09-27
If you want a GUI use gparted in GNOME and qtparted in KDE.

---

### Post by tagra123 on 2006-09-27
resize2fs is the command I think you are looking for. It will allow the fielsystem to use the free space in the partition.

---

### Post by willz06jw on 2006-09-27
This was a big help -- but I couldn't figure out how to unmount the  hard drive via SSH and then be able to resize it.  I bet I will need to do this locally.  

I did find a good parted help page though for anyone interested:
[http://www.gnu.org/software/parted/manual/parted.html](http://www.gnu.org/software/parted/manual/parted.html)

Thanks again,
Will the Ill

---

