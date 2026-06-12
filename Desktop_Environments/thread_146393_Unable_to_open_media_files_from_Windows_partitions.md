---
title: "Unable to open media files from Windows partitions"
date: 2006-03-18
forum: Desktop Environments
---

### Post by bluemike807 on 2006-03-18
Hi, I set up my machine to dual-boot Windows and Ubuntu. Easy enough, and I've mounted the other windows partitions (one is my actual windows partition and the other is a storage drive, both are NTFS). 

I can explore and read certain things easily enough (ie. text files), but if I try to open a media file, from one of these partitions,say an .mp3 with Rythmbox, it gives the error that it isnt a proper file.
Likewise if I open a movie.

Help?

---

### Post by catlett on 2006-03-18
I'm not an expert by any means but if you are running Ubuntu and your trying to access data from your windows partition that is NTFS, it won't work. Ubuntu uses Fat32 format. It is not compatable with NTFS formats. If you really wanted access to data on your NTFS volumes you would have to convert them to FAT32. Before you do anything like convert your active windows parttion to FAT32 do some research into the process and effects of conversion to be safe. Or more importantly do a backup of your whole system so you can just reinstall in case of a problem.Hope this helps. If not there are plenty of helpful people in this community who are far brighter than I am who will help. Good luck.

---

### Post by Ramses de Norre on 2006-03-18
You certainly can read ntfs! You just can't write on it.
No need for reformating if you just need to be able to read the files.
For your problem: did you install the right codecs? [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

