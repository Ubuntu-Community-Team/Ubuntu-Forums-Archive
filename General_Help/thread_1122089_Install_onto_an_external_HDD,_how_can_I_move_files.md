---
title: "Install onto an external HDD, how can I move files from existing PC onto the OS"
date: 2009-04-10
forum: General Help
---

### Post by BagginsWBA on 2009-04-10
Basically I have a work laptop which was given to me by work which came with alot of security settings etc, and to get around it I've install Ubuntu onto an external hard-drive and run off that, as it is an external hard-drive I thought I might still be able to see it in my computer and be able to drag and drop files from my existing OS (windows xp) on the external hard-drive containing Ubuntu, however this appears not possible as it does not appear in my computer but I can see it in remove hardware and in my device manager, thus leads to my question of;

Is it possible to be able to move a large amount of files onto the external hard-drive for ubuntu (it is mostly my music collection so if I were ever to get fired from work I wouldn't lose it when they took my laptop off me) ? 

Thank you. 

J x

---

### Post by dcstar on 2009-04-10
> **BagginsWBA said:**
> Basically I have a work laptop which was given to me by work which came with alot of security settings etc, and to get around it I've install Ubuntu onto an external hard-drive and run off that, as it is an external hard-drive I thought I might still be able to see it in my computer and be able to drag and drop files from my existing OS (windows xp) on the external hard-drive containing Ubuntu, however this appears not possible as it does not appear in my computer but I can see it in remove hardware and in my device manager, thus leads to my question of;

Is it possible to be able to move a large amount of files onto the external hard-drive for ubuntu (it is mostly my music collection so if I were ever to get fired from work I wouldn't lose it when they took my laptop off me) ? 

Thank you. 

J x

AFAIK there is a Windows program to read EXT2/3 filesystems, you will have to find it and install it.

---

### Post by Firestem4 on 2009-04-10
The Driver is located here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

It should not be very difficult to get it to work. Just follow the documentation.

Alternatively you can also use ntfs-3g to access NTFS volumes from Linux.

edit: I dont know if ntfs is preloaded in Ubuntu but I am sure its in the repositories.)

```
mount -t ntfs-3g /dev/sda1 /mnt
```

(change sda1 to match whatever is the correct drive)

Hope this helped.

---

### Post by callie510 on 2009-04-11
Yes, NTFS-3g is preinstalled with the latest versions of Ubuntu. I THINK that even the Live CD natively supports NTFS drives - I believe I have mounted my windows drives while booted onto the Live CD. 

So yeah, what you want to do is pretty easy either from Ubuntu or Windows: 

Looking at an NTFS drive in Ubuntu:
1) click on drive in "Places" to mount it, or use the command line as noted above
2) Open up the drive (from places or the desktop) and drag and drop your files

Looking at an ext3 drive in Windows
1) Install the fs-driver
2) Pick drive letters for your ubuntu drives
3) Go open them up in My Computer and drag & drop your files
side note: I don't know if fs-driver works with Windows Vista..... your best bet if you have Vista is to access your NTFS drive from within Ubuntu.


I have an ntfs partition and two ext3 partitions that share lots of files in both operating systems.

To move a lot of files, using the command line and some powerful command using cp, dd, or rsync might be more efficient - although I am still a GUI kinda person so I usually just drag & drop. someone else can suggest a good way to do this.

---

### Post by BagginsWBA on 2009-04-11
Aah superb lads, that is working :) Is there a certain place I should drag and drop file so they are easily found ? You are good people, I appreciate it a lot.

J. x

---

### Post by Firestem4 on 2009-04-11
It doesn't matter where you put them. If you access your NTFS volumes from Linux you will see all of the folders.

 For instance my secondary hard drive (non-os) has #RECYCLE; Desktop, Linux Distros, Program Files, etc. Those are mounted at /mnt/(files and etc)

Similar with acessing ext3 from Windows. Put them wherever you will find them. You will however want to put files into /home/(youruser)/ at the very least if you move stuff to your Linux partitions.

---

