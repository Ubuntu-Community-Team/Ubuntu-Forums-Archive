---
title: "Best filesystem for Linux-only external drive?"
date: 2009-01-09
forum: General Help
---

### Post by 50words on 2009-01-09
I have a 160GB Western Digital Passport that I use exclusively with computers running Ubuntu. I originally formatted it to NTFS, but I kept having to plug it into a Windows machine to fix filesystem errors that prevented me from using the drive.

I copy files larger than 4GB, so FAT32 is out.

Of the remaining options, what is the best filesystem to use for an external drive that will only be used with Linux computers? ext3?

---

### Post by avtolle on 2009-01-09
I'd go with ext3 for Linux only systems to use the drive.

---

### Post by tuxxy on 2009-01-09
Ext3

---

### Post by stchman on 2009-01-09
> **50words said:**
> I have a 160GB Western Digital Passport that I use exclusively with computers running Ubuntu. I originally formatted it to NTFS, but I kept having to plug it into a Windows machine to fix filesystem errors that prevented me from using the drive.

I copy files larger than 4GB, so FAT32 is out.

Of the remaining options, what is the best filesystem to use for an external drive that will only be used with Linux computers? ext3?

I agree, EXT3 will be your best choice for Linux only machines.  Be warned that if you do this Windows machines will not be able to read these disks unless special software is installed.

---

### Post by theozzlives on 2009-01-09
^5 on ext3

---

### Post by Amranu on 2009-01-09
I'm going to go against everyone and say xfs, since it's specifically designed to handle copying large files etc.

---

### Post by heindsight on 2009-01-09
I use xfs one my 1TB external drive, mostly because of this: [http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

---

### Post by 50words on 2009-01-11
I formatted to ext3 for now. This is primarily a backup drive, only occasionally used to transfer large files between my work and home computers.

If I have any issues, I will give xfs a try, instead.

Not being able to use the drive with Windows computers is a plus, really. Kind of a low-tech extra layer of security.

Thanks for your comments!

---

