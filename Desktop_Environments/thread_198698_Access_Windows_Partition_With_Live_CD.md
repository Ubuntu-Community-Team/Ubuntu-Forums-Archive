---
title: "Access Windows Partition With Live CD"
date: 2006-06-17
forum: Desktop Environments
---

### Post by I3rianL on 2006-06-17
Is there any way I can access and change the files on my Windows NTFS partition and do a virus scan using the Ubuntu 6.06 live cd?

---

### Post by RavenOfOdin on 2006-06-17
How many system partitions do you have?
If you have a FAT32 part with the two others, you can just move the files you want tested over to it, then scan them with AVG (or some other virus scanner) from Linux.

---

### Post by raptros-v76 on 2006-06-17
there isnt really a way to write to an ntfs partition.  can the linux virus scanner detect a windows virus?

---

### Post by RavenOfOdin on 2006-06-17
[QUOTE=raptros-v76] can the linux virus scanner detect a windows virus?[/QUOTE]

It should be able to, this is one of the main reasons a Linux virus scanner is useful on a dual boot system.

If you wish, you may test that hypothesis with a VCL (Virus creation laboratory) or some file that you know to be contaminated.

---

### Post by raptros-v76 on 2006-06-17
where can i get a vcl?

---

### Post by I3rianL on 2006-06-17
The problem is that I cant log on to windows.  When I try to log on it immediately logs off.  Is there any way to transfer the files to another computer or an external drive without logging on to windows?

---

### Post by RavenOfOdin on 2006-06-17
@I3rianL: A startup file may be corrupted, then.

I suggest entering Safe Mode (press and hold F5 before Windows starts up, if you have XP) and if possible performing a system restore to last known good date.  

@Raptros: I don't recall any exact sites. I'm sorry.

---

### Post by RRS on 2006-06-17
[QUOTE=I3rianL]The problem is that I cant log on to windows.  When I try to log on it immediately logs off.  Is there any way to transfer the files to another computer or an external drive without logging on to windows?[/QUOTE]

I'd suggest using the Knoppix live cd;
[http://www.knopper.net/knoppix/index-en.html]("http://www.knopper.net/knoppix/index-en.html")

It's got a few more "rescue" oriented tools then the Ubuntu live disc.

Besides moving your files to another drive or computer you should be able to use it to create a new partition on the same drive(if it's big enough) and copy them there also.

---

