---
title: "Partitioning"
date: 2006-09-17
forum: Desktop Environments
---

### Post by ART_Adventures on 2006-09-17
I installed Ubuntu from the Live CD. I had told the install to make a parition for the whole of my second hard disk and to format it using FAT32, but it never did this.

Can anybody tell me how I can format this disk using FAT32? I would like the disk to be usuable by windows and linux. There is a tool on System | Administration | Discs. And this lets me format partitions, but FAT32 does not appear to be one of the valid types. It mentions VFAT, but I don't know what this or and whether it can also be used by Windows.

Can anybody help?

Thanks.

---

### Post by pay on 2006-09-17
I think that windows can read VFAT, but I've never actually tried. You can partition with FAT32 by using Partition Magic or the Windows CD but I dont think that there is any open source program that will allow you to make a FAT32 partition because FAT32 is a proprietary format i believe.

---

### Post by wieman01 on 2006-09-17
I know another solution. There is a Windows driver that enables you to access & read files on a Linux files system (ext2/3). There are other but I have just found this one:

[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm")

---

### Post by indytim on 2006-09-17
ART_Adventures:

First, a FAT32 partiion is readable by both Windows and Linux. So, you should have no problems reading files across the 2 operating systems.  One thing to be aware of is the size limitation on FAT32 files. I'm not certain about the upper limit, but I do know that it is less than a full DVD (~4.2G).

With respect to formatting, an alternative is to use GParted Live.  Download the iso and burn to a CD.  Boot to the CD and you can do the formatting of GParted without having to go through the entire Ubuntu Live startup.  GParted Live can be found at [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

I just used it last night to re-format my NTFS partiton and re-install Windows 2000Pro.

Hope this helps.

IndyTim

---

### Post by imhdd on 2006-09-17
I've found the best way to prepare your hard drive is to go to Maxtor and Western Digital web sites and download their disk utilities. These utilities allow you partition and format quickly.

These are free utilities, fast download, and unzip to a floppy.

---

### Post by ART_Adventures on 2006-09-17
Thanks for the replies everybody.

I think I might start by trying GParted. If I dowload this iso, does ubuntu have any software to burn it to a CD/DVD?

Thanks.

---

### Post by wieman01 on 2006-09-17
> sudo apt-get gparted
It's in the repositories, mate. Or try Synaptic.

---

### Post by pay on 2006-09-18
You can burn it to a CD/DVD with k3b or gnomebake.

---

