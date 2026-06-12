---
title: "Best file system?"
date: 2008-12-22
forum: Desktop Environments
---

### Post by eshant_engineer on 2008-12-22
I want to install ubuntu as primary OS but at the same time i want to access windows xp through virtualbox under ubuntu.

I currently have XP only in my system and NTFS in each drive.

there are 4 partitions in 80 gb HDD,c: for OS & app,d: for games/movies,e: for softwares and download location and f: for songs and video songs

So what are the recommendations for installing ubuntu 8.10? what should be the file systems individually for each drive? please help me soon

---

### Post by night_fox on 2008-12-22
Use Ext3. Reiserfs is meant to be 10-15 times quicker though if you have loads and loads of smaller files. The reason I dont use it is that it continually defrags itself.

---

### Post by night_fox on 2008-12-22
Ubuntu is able to read ntfs, so partition your c drive to have a small Ubuntu partition (10 gig will do). Make this Ext3 and keep the rest ntfs

---

### Post by eshant_engineer on 2008-12-22
c: drive capacity is 18.5 GB so what should be the right size?
and for virtualbox whether ex3 or reiserfs?

---

### Post by Achetar on 2008-12-22
I prefer reiserfs4, but that is nearly impossible to install to, so go with either reiserfs3 (usually just called reiserfs) or ext3/4

---

### Post by eshant_engineer on 2008-12-22
means virtualbox will work on any FS?

---

