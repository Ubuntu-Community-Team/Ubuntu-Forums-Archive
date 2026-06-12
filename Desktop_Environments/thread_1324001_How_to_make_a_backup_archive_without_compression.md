---
title: "How to make a backup archive without compression"
date: 2009-11-12
forum: Desktop Environments
---

### Post by ario on 2009-11-12
Hi Guys.
I have all of my valuable documents on one of my partitons mounted on you say /home/documents.
I used to backup all the file in this patition using brasero disk burner or Nero Linux software on 2 DVDs. Just add half of my files and folders to a dvd and another half of my files and folder to another dvd compilation and then clicking burn.
Now **the problem is some of my files have a path more than 255 characters long.** This cause an error of "could not create disk image" in brasero and a warning of "Disk may not usable in some OS's" in Nero Linux.
**I can not decrease those type of my files paths. I decided to archive all them into an image file.** split that file in 4GB parts and then burn them into 2 dvds.
**Archiving files take a whole day to complete.** I can not pay about 10 hours to do this. I can not use rsync or grsync either. Because I want to backup my files on a DVD (A read only volume).
**All I need is a file archiver (I prefer it with a GUI front end) that have an special option to not compress files and just put them all in archive.** (So it will be faster to complete).
Any suggestions?
Thanks for your attention guys:)

---

### Post by wojox on 2009-11-12
Gnome File Roller aka Archive Manager

---

### Post by ario on 2009-11-12
Thanks. I used gnome file ruller but there was no options to set level of compressions.
**I need to archive my files without any compressions**. I do not have 8 to 9 hours of time to compress the hole partition. **I also don't want to use partimage**. Because then I can not extract any of my files from archive if a bit of archive corrupt.
Any other suggestions?
Thanks for your attention guys.

---

### Post by ario on 2009-11-12
Solved!
I used 
```
7z a -t7z -v4g -mx0 /home/MyName/documents.7z /home/documents
```
to backup my /home/documents folder. It also splits output file to 4GB files.
Thanks God:D

---

