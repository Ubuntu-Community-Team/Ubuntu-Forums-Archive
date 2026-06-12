---
title: "Partitioning"
date: 2006-06-25
forum: Desktop Environments
---

### Post by ubuntuubuntu on 2006-06-25
I'm trying to install Ubuntu in my new laptop. It has only Windows XP. In the part of the installation when we have to partition the disk, the partitioner shows four partitions:
#1 primary 41.1 MB fat16 /media/sda1
#1 primary 33.5 GB ntfs /media/sda2
#3 primary 5.0 GB fat32 /media/sda3
pri/log 8.2MB FREE SPACE


What is this fat32 partition? Can I format it and install Ubuntu in it?

---

### Post by jimbob on 2006-06-25
Good question.  Normally the answer is yes however on an XP-only machine I would expect to see only one partition - that being ntfs and taking up the entire disk as M$ selfishly does.

The fat16 and fat32 are mysteries to me - I'll have to defer to those with greater knowledge. 
________________________________       
  If I can't be Mr. Root I won't play ...
_________________________________
[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jimbob on 2006-06-25
Just read another post which talks about a laptop that did not come with an XP recovery CD but instead has recovery info and files (partitions?) on the HDD.

Could this be what those extra fat partitions are?  Did your laptop come with an XP recovery CD?  If not, you may not want to delete that fat32 partition untill you find out what it is.

EDIT:  If it was me, I'd scrub the entire HDD and install Ubuntu.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...
_________________________________
[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jpeirce on 2006-06-25
I know my Dell Latitude D610 came with that 5GB partition for data recovery tools, I don't remember exactly what was on it, I just formatted it all, removed windows and installed ubuntu, problem free.

---

