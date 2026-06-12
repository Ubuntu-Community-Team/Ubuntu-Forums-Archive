---
title: "File system for Windows and Ubuntu"
date: 2006-06-13
forum: Desktop Environments
---

### Post by keke21 on 2006-06-13
Any particularly good file system that works well under both Windows (XP) and Ubuntu (6.06)?

I'm using FAT32 because it's the only one that offers easy access by both.

---

### Post by johnnymac on 2006-06-13
I believe ext3 now works with windows if you get plugins for it.  I'm sure if you do a google search for "Windows ext3" you'll snag it.

---

### Post by temcat on 2006-06-13
[QUOTE=johnnymac]I believe ext3 now works with windows if you get plugins for it.  I'm sure if you do a google search for "Windows ext3" you'll snag it.[/QUOTE]

I have ext3 driver installed on Windows. Works OK, but causes annoying filesystem checks on Linux bootup from time to time, because it's actually for ext2 (with which ext3 is compatible) and does not support journaling.

---

### Post by Andykvakk on 2006-06-13
I'm using this program from [http://www.fs-driver.org](http://www.fs-driver.org). This enables ext2/ext3 drives in windows and you can read and write to the drives, one bad thing is that all users can access all the directories and files of an Ext2/ext3 volume, but for me this is no problem since i am the only user of my computer.

Good luck :-)

---

### Post by exclipy on 2006-06-13
I agree with all three replies above.

---

### Post by raist78 on 2006-06-13
I'm using ext2 as shared partition and fs-driver as Andykvakk. That's a quite good solution ;-) Never had a problem

---

### Post by keke21 on 2006-06-13
[QUOTE=raist78]I'm using ext2 as shared partition and fs-driver as Andykvakk. That's a quite good solution ;-) Never had a problem[/QUOTE] I've noticed with FAT32 that a nearly-full 100+GiB partition gets really, really slow.

Does the same happen with ext2?

---

### Post by exclipy on 2006-06-14
FAT32 isn't supposed to be bigger than 32GB, is it?  At least, WinXP doesn't let you make them that big, I think because of bad performance.  Though that's what I'm thinking of doing on my external 80GB drive... how slow is really really slow?

I can't imagine ext2 to have big performance losses like that at all.

---

### Post by keke21 on 2006-06-14
[QUOTE=exclipy]FAT32 isn't supposed to be bigger than 32GB, is it?  At least, WinXP doesn't let you make them that big, I think because of bad performance.  Though that's what I'm thinking of doing on my external 80GB drive... how slow is really really slow?

I can't imagine ext2 to have big performance losses like that at all.[/QUOTE] It never got bad until I had to do multiple simultanious write operations. Performance did degrade, though, as the partition started to get files into the thousands and filled over 40GiB.

FAT32's supposed to be able to reach something like 2TiB, but that's not going to happen. I was just hoping it wouldn't slow down at the point where it is now.

Also, what's the best file system for Ubuntu? I've been using ext3 so far. I think it was the default choice.

---

### Post by TigerWolf on 2006-06-14
There is some limit for FAT32 in windows but there is some sort of workaround but its very tedious. Definately use ext3 and then get the windows app that can use it, thats what im doing.

---

### Post by exclipy on 2006-06-14
[QUOTE=keke21]Also, what's the best file system for Ubuntu? I've been using ext3 so far. I think it was the default choice.[/QUOTE]

Between Reiserfs, ext3, xfs, etc. there really isn't much difference for a desktop user.  You can find benchmarks if you're looking for one to put on a high performance server, but ext3 is as good a choice as any for a desktop.


Does anyone know how to make a 80GB FAT32 partition?  When I tried to make one in parted, Windows didn't recognise it.

---

### Post by keke21 on 2006-06-15
[QUOTE=exclipy]Between Reiserfs, ext3, xfs, etc. there really isn't much difference for a desktop user.  You can find benchmarks if you're looking for one to put on a high performance server, but ext3 is as good a choice as any for a desktop.


Does anyone know how to make a 80GB FAT32 partition?  When I tried to make one in parted, Windows didn't recognise it.[/QUOTE]
Many hard drive manufacturers create freely-downloadable programs for partitioning their drives. I used Maxtor's to create a 200GB FAT32 partition.

I'm going to convert it to NTFS4. After getting over 1500 files and filling 50GB, the FAT32 disk has really started to slow down.

---

### Post by viper52b on 2006-06-15
I used to use FAT32 (and I liked it) untill i bumped into the maximum file size limit of 4 GB.  Which means I often had problems when I tried to get some DVD ISO's on my hard disk.  This is what i believe the biggest problem of FAT32 (I haven't really noticed a big difference in speeds though, and i've been using 160 GB partitions...)

Switched to linux only now so haven't had that problem since :p.

But like most people, i would recommend ext3 for linux - windows.  As filesystem type for linux only, i would really recommend ReiserFS! Not for performance (which is good, but not extremely better then other filesystem types), but for the ease of use when you get into trouble.  ReiserFStools let you (most of the time) recover most of your files when you've screwed something up :).

Greetz

---

### Post by keke21 on 2006-06-15
What I think you're describing is a large partition with relatively few files. Right now, my ex-FAT32 partition has over 6000 files in different directories. I turned it into NTFS3 since then.

I'll try ReiserFS. I'm not too fond of the drivers for NTFS on Linux and EXT2 on Windows. Their sites state that they completely bypass security and allow anyone to access any file. That was a problem for FAT32, but I didn't use FAT32 for my main Windows partition.

I think I'll end up using EXT2 for storage partitions and ReiserFS/NTFS for my operating system installations.

---

