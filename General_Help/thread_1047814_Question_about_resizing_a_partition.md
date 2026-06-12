---
title: "Question about resizing a partition"
date: 2009-01-22
forum: General Help
---

### Post by Explosion85 on 2009-01-22
I have an 80GB hard drive with 3 partitions:

Ubuntu (ext3)
Windows XP (NTFS)
Swapfile

I've been using Ubuntu exclusively for the past few months and I want to steal some of the free space from the Windows XP partition and move it to my Ubuntu partition. 

Is this possible? If so, how can I do this?

---

### Post by grndslm on 2009-01-22
gparted livecd

EDIT: make sure to defrag windows before using the livecd

---

### Post by svrkispm on 2009-01-22
use for ex. [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/"), it has nice GUI, pretty self-explanatory - you can move and resize your partitions with mouse.

be sure to backup your data before that and to defragment the windows partition, afaik it should speed up the whole operation.

---

### Post by caljohnsmith on 2009-01-22
If the Ubuntu partition comes physically before the XP partition on the drive, I would not recommend resizing the XP partition from the beginning in order to gain extra space for Ubuntu's partition; if you do that Windows won't be bootable after that. But if you want to mess with hacking Windows afterwards, I've read you can get XP booting after moving the starting point of its partition, but it takes quite a bit of work; also I don't know how reliable the technique is. You might want to consider resizing XP from its end, and then just create a data partition with that space that you can use with Ubuntu.

---

### Post by grndslm on 2009-01-22
Also, think about creating a separate partition for you /home directory.  You'll thank me later.

---

