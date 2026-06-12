---
title: "Removing lost+found directory"
date: 2006-08-15
forum: Desktop Environments
---

### Post by 3ntity on 2006-08-15
Hello,
I recently formatted a partition that used to have Breezy installed on it (long live Dapper!) but through the partition manager (and also through Partition Magic 8, under windows) it appears that 900MB are still in use! How is this possible? I tried reformatting several time, but it stays like that... Are there actually any files still present? If so, how do i delete them? When i cd to that partition, nothing appears in it:
```
__@____:/media/hdb1$ ls -l
total 0

```
What to do, what to do?
Thanks in advance :)

---

### Post by DoctorMO on 2006-08-16
Can you post a screen shot?

---

### Post by 3ntity on 2006-08-17
> **DoctorMO said:**
> Can you post a screen shot?
Post a screen shot of what exactly? Of the folder as seen in the file browser or...? But, will do :)

---

### Post by givré on 2006-08-17
ls -al ?

---

### Post by jazzgossen on 2006-08-17
In what way does it appear that 900 MB are still in use? What does "du" give you if you run it in the suspicious directory?

---

### Post by 3ntity on 2006-08-22
Hmm... the folder seems to have disappeared, without me having done anything to it (well, I tried deleting it through the File Browser, to no avail... Maybe it realized during a bootup that the folder wasn't meant to be there and did away with it ;) ). Sorry for replying so late, I've been extremely busy (studying :/)... I'll check the partition out in partition magic again, and if it still shows up as using 900MB, i'll post a screenshot of that, but it could just be a little bug in that program, right?
```
____@____:/media/hdb1$ du
4       .
____@____:/media/hdb1$ ls -al
total 8
drwxr-xr-x 2 root root 4096 2006-08-15 22:14 .
drwxr-xr-x 9 root root 4096 2006-08-15 16:00 ..

```
Thanks guys :)

---

### Post by 3ntity on 2006-08-22
Hello again, 
Here's a screenshot of what partition magic shows me. The partition i'm referring to is /Ubuntu_Data. As you can see it says Used MB: 911.5MB, whilst if i 'explore' the hard drive, no files appear. Maybe a bug, as i suggested before? I've tried formatting it through partition magic, but the same thing shows up every time. I hope my drive's not (partially) corrupted :/
Thanks for any help :)

---

### Post by givré on 2006-08-22
1: partition magic don't format ext3 really good, so it's not your partition which is corrupted, but simply partition magic who don't do his job correctly.
2: As show your screenshot, this appear to definitly be a bug in partition magic : Your partition has a size of 30 Mb and he say that 911 Mb are use. I guess it's more 0.911 Mo (unused(27,084Mo)+use(0.911Mo) seams to give me the good size ;) )
In conclusion don't use partition magic, it's the worst partitionner in the world.
Try Gparted LiveCD [www.gparted.sourceforge.net/livecd.php](www.gparted.sourceforge.net/livecd.php)

---

### Post by 3ntity on 2006-09-04
> **givré said:**
> ... **Your partition has a size of 30 Mb** and he say that 911 Mb are use. I guess it's more 0.911 Mo (unused(27,084Mo)+use(0.911Mo) seams to give me the good size ;) ) ...
[www.gparted.sourceforge.net/livecd.php](www.gparted.sourceforge.net/livecd.php)
Actually: that partition is 27996MB big, or 30GB, of which 911MB appear used, which is the problem. (27,996 does not stand for ~28, but for 27996. Only in Belgium and France does 27,996 mean ~28, I think.) 
Might give GParted a shot, I don't have much time at the moment though :/

---

