---
title: "Norton Ghost alternative?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by naked on 2006-06-30
I'm wanting to create an "image" or a specific partition for backup purposes.  Is there a way to do this, and then "reinstall" it on another computer?

L

---

### Post by newman on 2006-06-30
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by six on 2006-07-03
I've been looking for exactly the same thing the last couple days, because Ghost 2003 doesn't like Linux partitions, despite it's claims. At first, my Ghost didn't even like the Ubuntus, but after patching some late 2004 updates, it seemed OK again. However, it still didn't like Fedora Core 5 - it always drops out with a (well known about) error.

I came across the partimage utility via another route today, but this associated (GPL) site is a real gem as well:

[http://www.sysresccd.org]("http://www.sysresccd.org")

It lets you create a bootable CD (or USB stick) with partimage on it, and several other utilities, like qtparted.

I've just successfully backed-up and restored my FC5 partition using it. The gzip default is fast - better even that Ghost.

I intend to backup all my other distro installations (including Ubuntu, Kubuntu, Edubuntu and Xubuntu :D ) with it pronto!

EDIT: Some people recommend G4L or G4U, but they seem to only work with more than one HDD or over a network/server. The good thing about Partimage is, it let me backup my /dev/hda12 and /dev/hda13 /boot and / partitions to /dev/hda2 (formatted as FAT32) on the same HDD. You'll have to mount your backup partition manually to be able to write to it, like so:

mkdir /mnt/fat32
mount -t vfat /dev/hda2 /mnt/fat32

---

### Post by ardchoille on 2006-07-03
[QUOTE=naked]I'm wanting to create an "image" or a specific partition for backup purposes.  Is there a way to do this, and then "reinstall" it on another computer?

L[/QUOTE]
I have been using partimage for a while and it does the job very well.

[http://partimage.org/Main_Page](http://partimage.org/Main_Page)

Partimage is included on the System Rescue CD, along with a good collection of other admin tools, and I feel that every Linux user should have a copy of this awesome LiveCD:
[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

---

### Post by insanedc on 2006-07-03
I tried all of the free alternatives, and they all leave much to be desired. I bought Acronis Disk Image for $29 from newegg and it has works GREAT! A wealth of features, works very quick (100 GB backup in about an hour) and is very RELIABLE. In my opinion, well worth the purchase price. The free ones just don't cut it.

---

### Post by wgaprotest on 2006-09-27
Insanedc, I also love Acronis for my windows drive, but it's having trouble reading lots of sectors from my other drive, the one that houses my ubuntu lamp server. And I just reinstalled it last night, after my most recent linux install, to see if it would work on the linux drive.

So now I'm trying with partimage. There's nothing that beats an exact image of a working system for backups.

---

### Post by lagagnon on 2006-09-27
> **insanedc said:**
> I tried all of the free alternatives, and they all leave much to be desired. ....The free ones just don't cut it.
I would have to disagree. PartImage does exactly what the original poster wants and does it well and fast. I think what you mean is that it simply does not have a pretty GUI.

---

