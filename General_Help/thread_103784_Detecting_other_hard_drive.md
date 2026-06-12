---
title: "Detecting other hard drive"
date: 2005-12-14
forum: General Help
---

### Post by Fatstink on 2005-12-14
I have my linux partition on a 30 GB hard drive and I have windows partitioned on a 40 GB to have 1/2 ntfs and 1/2 fat32 so that I can share between linux and windows on the fat32 for music and such.  Where would my 40 GB harddrive be listed?

---

### Post by aysiu on 2005-12-14
You have to mount it.

In the Konsole, type ```
sudo fdisk -l
``` to find out where your FAT partition is in the partition table, then follow these directions:

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

The directions assume it's at /dev/hda1, but you'll know where it really is from *sudo fdisk -l*.
Oh, and substitute *kwrite* for *gedit*.

---

### Post by Fatstink on 2005-12-14
Okay I did that but it won't let me write/save anything to it.  I am trying to transfer music stored on my friends computer, over the network and onto my other windows partition or do I have to go through windows to write it to my FAT32 partition???

---

### Post by randum_idiot on 2005-12-14
hey, i have 3 partitons on my computer...

10 gig MS WIN 2000  -->FAT 32
  4 gig MS WIN98se   -->FAT 32
  4 gig UBUNTU

I have it all running well etc, but how do you get it to detect BOTH of those windows partitions? I read the instructions to get the WIN2000 going but i dont know how 2 get both automatically mounted on startup

Oh yes, if possible, how do you get windows to detect ubuntu's partition

thanx

---

### Post by randum_idiot on 2005-12-14
bump^^

---

### Post by aysiu on 2005-12-14
[QUOTE=Fatstink]Okay I did that but it won't let me write/save anything to it.  I am trying to transfer music stored on my friends computer, over the network and onto my other windows partition or do I have to go through windows to write it to my FAT32 partition???[/QUOTE] Can you post the output of these three commands? ```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by aysiu on 2005-12-14
[QUOTE=randum_idiot]hey, i have 3 partitons on my computer...

10 gig MS WIN 2000  -->FAT 32
  4 gig MS WIN98se   -->FAT 32
  4 gig UBUNTU

I have it all running well etc, but how do you get it to detect BOTH of those windows partitions? I read the instructions to get the WIN2000 going but i dont know how 2 get both automatically mounted on startup[/quote] [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)
Just make two separate mount points. 
One can be /media/windows2000
The other can be /media/windows98

> 
Oh yes, if possible, how do you get windows to detect ubuntu's partition Good luck.

> bump Did you really have to bump the thread after *five minutes*?

---

### Post by randum_idiot on 2005-12-14
sorry, just havnt alor of time 2 do this, so yea, lol

---

### Post by aysiu on 2005-12-14
[QUOTE=randum_idiot]sorry, just havnt alor of time 2 do this, so yea, lol[/QUOTE] Okay. Well, I'm here. Let me walk you through this. Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by randum_idiot on 2005-12-14
o, nah, its okay, i understand what u meant (how to do it) thanx 4 that

---

### Post by Fatstink on 2005-12-14
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2       /media/windows  vfat    iocharset=utf8,umask=000 0      0

---

### Post by Fatstink on 2005-12-14
I went through windows and added all the music I wanted on my Fat32 partition.  And I can't get to it

---

