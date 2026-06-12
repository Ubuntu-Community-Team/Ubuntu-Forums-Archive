---
title: "files on shared partition not accessible from xp"
date: 2009-01-04
forum: General Help
---

### Post by xm4ss4cr3 on 2009-01-04
I always used ubuntu as the only os on all my laptops and desktops, but now for the first time i made a dualboot.
The harddisk is partitioned as followed:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3822    30700183+   7  HPFS/NTFS
/dev/sda2            3823       19457   125588137+   5  Extended
/dev/sda5            3823        7765    31672116   83  Linux
/dev/sda6            7766        8373     4883728+  82  Linux swap / Solaris
/dev/sda7            8374       19457    89032198+   b  W95 FAT32

```
sda7 is mounted as /data and both windows and ubuntu can access that partition. Now I want to use that partition to save my files to and be able to use them from both windows and linux.
As I said, both windows and linux can access the partition fine. Both can put files on them. The only problem is that xp can't see files put there on linux.
If I create files under linux, linux can view them, access them and everything, but xp can't (can't even see them). But files created under xp are fine for both linux and xp.

I think it  has something to do with the permissions, but after a couple of hours googling and such I still had no succes...

---

### Post by HermanAB on 2009-01-04
First see how the partitions are mounted:
$ sudo mount

then look at the file permissions:
$ ls -al /where/ever/it/is/*

If the permissions are not proper, change /etc/fstab, umount and mount again.

Hope that helps!

Herman

---

### Post by poltiser on 2009-01-04
:P Easy!
I have 3 drives with (NTFS+Ext3+Ext3+Ext3;NTFS+NTFS+Ext3+swap;NTFS+Ext3)
all shared between WinXPHomeSP3 and Ubuntu8.1, read and write in every direction...
I use Acronis Disk Director 10 to create and maintain partitions in all drives and systems; I do not let Ubuntu format partitions - everything is done in Acronis DD10.
It works.
XP <-> U8.1 thanks to Windows XP extension and of course NTFS-3g of linux. It is more than a year from last disaster (motherboard burned by electrical surge during the storm...) and main data collection (pictures, music, documents etc.)is few years old...
Acronis has OSS (Operating System selector) - works along GRUB and prevents crushes, and free tool to re-write MBR... I believe you can use trial run to try on your system.
Good luck.
;)

---

### Post by xm4ss4cr3 on 2009-01-05
tried HermanAB's option first and it worked! :D
changed the umask to read and write acces to everyone (i'm the only one using my laptop and i want to share all the files with myself under xp, so i don't care if everyone van acces it)

thanks!

---

