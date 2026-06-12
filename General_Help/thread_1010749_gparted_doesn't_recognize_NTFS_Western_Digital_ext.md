---
title: "gparted doesn't recognize NTFS Western Digital external"
date: 2008-12-14
forum: General Help
---

### Post by PWill21 on 2008-12-14
I apologize if the following issues have been addressed, but I haven't been able to get them to work together to solve my main problem.

What I'm trying to do is backup my PS3 files (via the PS3 backup utility) onto a 250GB Western Digital external hard drive. The WD drive has 110GB of free space, yet the file system on the WD is NFTS which the PS3 does not recognize (FAT32), so I know I need to partition it but I also have no problem with a complete format. The only real roadblock is that gparted doesn't recognize the WD drive on my laptop (running 8.04). The drive does show up mounted on my desktop upon plugin via USB, files are there and readable, etc. Ultimately I would just like to format the WD drive to FAT32. Any ideas as to why gparted doesn't see the drive?

---

### Post by caljohnsmith on 2008-12-14
How about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/[COLOR="Red"]sdX[/COLOR] print
```
And replace "sdX" above with your WD HDD.

---

