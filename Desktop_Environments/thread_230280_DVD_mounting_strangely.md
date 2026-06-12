---
title: "DVD mounting strangely"
date: 2006-08-05
forum: Desktop Environments
---

### Post by SuperSack56 on 2006-08-05
I'm running the 64-bit edition of 6.06 on my desktop (running gnome). Whenever I insert a video dvd into the dvd drive (it's an rw, i believe a Plextor), the "DVD-ROM Disc" icon pops up on the desktop, and when I click it, I get the CD/DVD Creator Folder window. If I run a 
```
sudo mount /dev/dvd /media/dvd
```
it correctly mounts the drive into /media/dvd and I can view the files there.  It seems as though it knows there's a dvd present, and is capable of mounting it, but the system thinks that the disc is empty.

My laptop (32bit dapper) acts correctly- it recognizes the disc, opens up totem, and begins playing.

Is it possible to get the correct behavior out of my desktop? Thanks!

---

### Post by SuperSack56 on 2006-08-14
Does anybody have any thoughts? Is there any additional information i should provide?

---

### Post by Watcher on 2006-08-24
I have the same problem as you (I also have a Plextor as dvd-drive). I've got a couple ideas I'm gonna try and see if they maybe solve the problem.

---

### Post by carontis on 2006-08-24
Try check in fstab file ( /etc/fstab) and see if it reports correctly your dvdrw, if not you'll have to add some line of knowldge for it. If you want you can send here the fstab. For your knowledge I send you the line that should appears in your fstab, and if not there, copy this one and include it in your but respecting the alphabetical order (hda1-hdb1 hdc-hdc1 etc):

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

hope it fix the problem.

---

### Post by SuperSack56 on 2006-08-26
Still no luck. Here's my fstab:


matt@mythbox:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdb1       /cache          ext3    defaults        0       2
/dev/hdb2       /data           xfs     defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/hdd1       /data/dvd       xfs     defaults        0       2



any further thoughts? Watcher, any luck?

---

### Post by Watcher on 2006-08-27
Still no luck ... :(

I tried changing /dev/hda to /dev/dvd in my fstab file. But that didn't change much to the problem (I actually made it worse). Also I tried removing the /dev/hda line completly from fstab, again no luck. Then I tried with changing the udf,iso9660 bit to auto. No change.

I did however noticed that it only occurs with some dvd's here. I can read dvd's I bought in a store (like moviedvd's or games) just fine, they mount without trouble. Most of my cd's (both bought audiocd's and self burned one's (data and audio)) also work without trouble. I actually only happens when I use dvd's I burned myself (linux or windows doesn't make a difference here). I can however acces the data if I mount it again in a terminal (sudo mount /dev/dvd /media/dvd) :-k .

I'm gonna dig deeper and google some more after I'm done with my exams. But can you see what type of Plextor drive you have?

---

### Post by SuperSack56 on 2006-08-27
> **Watcher said:**
> Still no luck ... :(

I tried changing /dev/hda to /dev/dvd in my fstab file. But that didn't change much to the problem (I actually made it worse). Also I tried removing the /dev/hda line completly from fstab, again no luck. Then I tried with changing the udf,iso9660 bit to auto. No change.
I tried a few fstab things similar to what you mentioned, also no luck.

> I did however noticed that it only occurs with some dvd's here. I can read dvd's I bought in a store (like moviedvd's or games) just fine, they mount without trouble. Most of my cd's (both bought audiocd's and self burned one's (data and audio)) also work without trouble. I actually only happens when I use dvd's I burned myself (linux or windows doesn't make a difference here). 
I tried a data disc and several movies with the same result :cry: 
> I can however acces the data if I mount it again in a terminal (sudo mount /dev/dvd /media/dvd) :-k .
I also tried the /dev/dvd mounting thing, which correctly mounts it to /media/dvd...

> But can you see what type of Plextor drive you have?
PX-712A

---

### Post by Watcher on 2006-08-29
I got a 708A. Time to once again ask my good friend google for assistance :)

---

### Post by twowheeler on 2006-08-29
> **SuperSack56 said:**
> 

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/hdd1       /data/dvd       xfs     defaults        0       2



Hmm, not that I am any expert, but that does not look right.  Are there two drives, one that is CD-only, and one with DVD capabilities?  I have one CD/DVD drive in this machine, and the fstab entry looks like:

> /dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0   0

On this machine, the movie player (gxine in my case) pops up and plays correctly when a dvd is inserted.

A couple of questions come to mind.  Why is the media type shown as xfs instead of iso9660?  Also why does it list the device as hdd1?  That would be the first partition on the hdd drive, no?  It may be getting confused by the partition reference.  Maybe you should change to /dev/hdd and iso9660 as an experiment.

---

### Post by Watcher on 2006-08-29
This is mine fstab, I do wonder what that ro is for in yours ...

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/windows-c ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb	/media/cdrom1	udf,iso9660 user,noauto	0	0
/dev/sdb3	/media/backup	vfat	iocharset=utf8,umask=000	0	0


hda is my dvd-drive, hdb my cd only drive. Rest I think explains itself ...

---

### Post by Atomic Dog on 2006-08-29
For kicks and giggles try:

/dev/hdc /media/cdrom0 auto user,noauto 0 0

seriously, try using it in fstab and reboot.  I bet it will cure it.

---

### Post by asplode on 2006-08-30
> **Watcher said:**
> This is mine fstab, I do wonder what that ro is for

the ro line makes it Read Only

---

