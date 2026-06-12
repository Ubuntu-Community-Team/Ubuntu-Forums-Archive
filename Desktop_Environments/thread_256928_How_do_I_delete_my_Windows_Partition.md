---
title: "How do I delete my Windows Partition?"
date: 2006-09-13
forum: Desktop Environments
---

### Post by cobbweb on 2006-09-13
Hello, 
   Right now I have a 40Gb hard drive with both Ubuntu and Windows installed on it. I would like to delete my Windows partion (ganna run it in VMWare... never use windows anyway) and then be able to use the partition i just deleted and add it onto my Ubuntu partition. I went to the disk manager to see if I could just formate my Windows Partition but that was not an option with the GUI panel. Does anyone have a solution for this? Thanks for the help, any suggestions are welcome, 
 
 Cobbweb

---

### Post by RobsterUK on 2006-09-13
I would recommend using a GParted live CD, which you can get from:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I recently used this to reduce the size of my windows partition and increase the size of the linux one which was after it. GParted moves the start of the Linux partition and moves all the data to the new start point.

Or if you don't have a CD writer I think you can do it using GParted on the Ubuntu live CD

---

### Post by cobbweb on 2006-09-13
> **RobsterUK said:**
> I would recommend using a GParted live CD, which you can get from:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I recently used this to reduce the size of my windows partition and increase the size of the linux one which was after it. GParted moves the start of the Linux partition and moves all the data to the new start point.

Or if you don't have a CD writer I think you can do it using GParted on the Ubuntu live CD


 Ok so this is just like the partitioner that comes on the Ubuntu cd? Then in order to do what im trying to do would I just then format my Windows partition to and resize my Ubuntu partition? Im a little confused on how I can add my windows partition to my Ubuntu partition. Sorry for the boneheadness... 
   Thanks,
 
Cobbweb

---

### Post by jpkotta on 2006-09-13
Use cfdisk.  It's easy to use.```
sudo cfdisk /dev/hda
```

---

