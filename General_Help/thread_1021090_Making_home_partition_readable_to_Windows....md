---
title: "Making home partition readable to Windows..."
date: 2008-12-24
forum: General Help
---

### Post by ChocoTuar on 2008-12-24
I recently reformatted my hard drive and reinstalled Ibex on top of Windows XP (dual boot). I thought it would be a good idea to make my home folder readable to both Windows and Ubuntu, so I made it its own little partition and set the mount point for Ubuntu. The problem is, I can't seem to get the permissions right for Windows to be able to read the entire partition. All of the files inside the home directory are readable to all people, but it only shows about half of the directories, and can't see any of the files within.

What else would you need to know in order to help me?

---

### Post by namegame on 2008-12-24
If the file system of your /home partition is ext2 or ext3, the following link has 3 solutions.

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

I use Explore2fs and it works quite well.

---

### Post by ChocoTuar on 2008-12-28
No, I made it FAT32 so both OS's could read/write to it. Windows seems to mount the partition fine, it just can't see all of the files and folders. Only some.

---

### Post by taurus on 2008-12-28
Using fat32 filesystem for /home will never work because of permissions and ownership.

So, use ext2/3 filesystem for /home and use fs-driver to read it under windows then.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by c1rcu17 on 2008-12-28
fs-driver.com is the best.

---

