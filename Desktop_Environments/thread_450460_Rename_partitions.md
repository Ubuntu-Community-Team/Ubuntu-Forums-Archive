---
title: "Rename partitions"
date: 2007-05-21
forum: Desktop Environments
---

### Post by antiserious on 2007-05-21
Hi, first post here. I installed Ubuntu Studio 7.04 in a dual-boot with XP and it did a fine job of mounting all partitions (2 h/d's), but I'd love to rename a few of them. Some names were picked up, but there are a few 'Disk1_VOL1' types that I would really prefer to change. Can someone please point me to a guide, or explain how I can change the names in Gnome? 
 
Thanks in advance - so far I'm liking this, despite my normal preference for KDE.

---

### Post by earobinson on 2007-05-21
Disk names aren't really prevalent in Ubuntu, what I bet your talking about is the folder it mounts to's name.

can you type ```
cat /etc/fstab
``` in the terminal and past the output here for us.

---

### Post by antiserious on 2007-05-21
In fstab the names show as expected (dev/hda1, dev/hdb2, etc), although the Windows partitions also have UUID's, and  those that I have assigned names in Windows (Backup, etc) display as named. However, the Windows partitions with just drive letter designations display as 'Disk1_VOL1', and so on. Perhaps I should just go into XP and assign names to those partitions as well.
 
Guess I was hoping for an easy option from linux. It's not a big deal.
 
*edit - the naming in XP worked, and Ubuntu now picks those up. I was a bit surprised, since SUSE/KDE allowed me to rename any desktop icons I wanted, but it's all sorted out now.*

---

### Post by earobinson on 2007-05-21
you might have been able to do it in gparted, that is somethign that shoudl be more easy you are right.

---

