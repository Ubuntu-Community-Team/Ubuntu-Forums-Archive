---
title: "Problem with mounting"
date: 2006-08-15
forum: Desktop Environments
---

### Post by GregaS on 2006-08-15
I tried to mount a DVD yesterday and I got this error:

[img]http://www3.shrani.si/files/error821516.png[/img]

I thought that DVD is broken, so I inserted another one and that one was working. Today I connected digital camera to USB port and I got the same error message. Both the DVD and digital camera are working in windows. Help please.

---

### Post by GregaS on 2006-08-16
Help??? I can't open any DVDs anymore :( Could ntfs-3g have something to do with this?

---

### Post by GregaS on 2006-08-16
BTW my cd-rom works fine, but dvd-rom is not working.

---

### Post by GregaS on 2006-08-17
Is really reinstalling kubuntu the only way???

---

### Post by givré on 2006-08-17
ok, will try to see in deep your problem.
Since i don't have kubuntu, i'll have to guess a bit.
I think that in kde land, removable device are manage by ivman, is that right?
If it is, i suggest you to kill it and to start it again in debug mode (or non daemon) in a terminal (have a look at man ivman). 
In that way you will know what's happens behind.
Say me how it works.

---

### Post by CnorthMSU on 2006-08-17
Are you trying to read a data DVD or a movie DVD? That may make a big difference.

---

### Post by GregaS on 2006-08-17
I've solved the DVD error. In "system settings" under "Disk & Filesystems" and I added new optical device. But I still have problem with Digital Camera. I tried the same but it's not working. This is screenshot of my Disk & Filesystems:

[[img]http://www3.shrani.si/thumbs/disk830892.png[/img]](http://www3.shrani.si/o.php?disk830892.png)

---

### Post by GregaS on 2006-08-18
I found out today that floppy drive has the same problem.

---

