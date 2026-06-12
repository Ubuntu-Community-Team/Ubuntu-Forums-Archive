---
title: "mounted dvd - strange ownership - ideas?"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Pawel Stolowski on 2006-09-01
I've a strange problem with one dvd disc (Quake 4) that I inserted today into my dvd drive. When inserted, the disc is automounted but the contents is not readable for regular user - this is caused by wrong ownership&permissions of the /media/cdrom0 directory:

lrwxrwxrwx 1 root root    6 2006-05-20 15:46 cdrom -> cdrom0
drwx------ 5  400  401 2048 2006-05-05 02:18 cdrom0

But this is very strange since it happens *only* for this particular dvd disc (i just tried another dvd disc and permissions were set correctly).

Here is cdrom entry from my /etc/fstab (the default created by Ubuntu):
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Did anyone notice similiar problem? What is the reason one dvd disc has different permissions than any other?

---

### Post by gatiba on 2007-01-11
I was having your exact same problem...
I deleted the subdirectories (cdrom0, cdrom1, dvdrecorder) in /media, and it automatically recreated the directories with the right permissions...

---

