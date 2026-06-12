---
title: "Can't save files to desktop and other problems."
date: 2009-04-29
forum: General Help
---

### Post by haertel on 2009-04-29
Ok. Give me some credit- I'm 14 years old, with no proper computer class, with only a little coding knowledge. I'm used to running XP and recently decided to try and give ubuntu a try. I've installed it, but I'm having some problems.
Firstly, every time I try and save a file to the desktop I get a message telling me that there isn't any room in the desktop directory. Why is this? How can I fix it?

Secondly, none of the settings I change (e.g. preferences, toolbar changes, administrative options) maintain themselves after I reboot. I'll set a wallpaper, only to reboot and find it on a default. I have a shrewd suspicion that I'm not giving Ubuntu enough room to save these changes (and also the desktop icons), but I don't know how to fix this. It isn't the size of my hard drive that is the problem- it's 120 gigs.

Any help or suggestions on how to get to know ubuntu better would be greatly appreciated.

Thanks, 

Haertel

---

### Post by kanikilu on 2009-04-29
To me it sounds more like a permissions problem than a disk space problem. 

But, to check, go to a terminal (Applications > Accessories > Terminal) and simply type **df -h**. You'll be able to tell from the output if your partition/disk is full.

---

### Post by haertel on 2009-04-29
> **kanikilu said:**
> To me it sounds more like a permissions problem than a disk space problem. 

But, to check, go to a terminal (Applications > Accessories > Terminal) and simply type **df -h**. You'll be able to tell from the output if your partition/disk is full.
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sdb5     ext3     2403420   2282836         0 100% /
tmpfs        tmpfs      513068         0    513068   0% /lib/init/rw
varrun       tmpfs      513068       104    512964   1% /var/run
varlock      tmpfs      513068         0    513068   0% /var/lock
udev         tmpfs      513068       168    512900   1% /dev
tmpfs        tmpfs      513068        76    512992   1% /dev/shm
lrm          tmpfs      513068      2392    510676   1% /lib/modules/2.6.28-11-generic/volatile
overflow     tmpfs        1024        20      1004   2% /tmp
/dev/sdd1     vfat      498856     64920    433936  14% /media/GARDNER
/dev/sdc1     vfat     3908108   2861188   1046920  74% /media/LEXAR

---

### Post by kanikilu on 2009-04-29
> /dev/sdb5 ext3 2403420 2282836 0 100% /
Well, there's your problem...your root partition is in fact full.

---

### Post by kanikilu on 2009-04-29
I might be doing my math wrong here, but it looks like you only gave your root partition 2GB, is that right? If so, I don't think that's going to be enough for a default Ubuntu install.

Just out of curiosity, can you use the -h switch with df to get "human readable" output? ```
df -h
```

I run Xubuntu on my 4GB netbook, and have to run a tight ship otherwise I get close to filling up the drive.

---

### Post by buchan on 2009-04-29
> **kanikilu said:**
> Well, there's your problem...your root partition is in fact full.

The amount of space you allowed for your root partition is very small if my calculations are correct its only 2GB, if possible I'd resize that partition to at least 5 GB depending on how much you intend to store on your ubuntu system.  
You Also have two other partitions
```
/dev/sdd1 vfat 498856 64920 433936 14% /media/GARDNER
/dev/sdc1 vfat 3908108 2861188 1046920 74% /media/LEXAR
```

that you could be storing things on as well.
Unfortunately you will have to reinstall if you want to use that same disk if you can resize the partition.

---

### Post by haertel on 2009-04-29
> **buchan said:**
> The amount of space you allowed for your root partition is very small if my calculations are correct its only 2GB, if possible I'd resize that partition to at least 5 GB depending on how much you intend to store on your ubuntu system.  
You Also have two other partitions
```
/dev/sdd1 vfat 498856 64920 433936 14% /media/GARDNER
/dev/sdc1 vfat 3908108 2861188 1046920 74% /media/LEXAR
```that you could be storing things on as well.
Unfortunately you will have to reinstall if you want to use that same disk if you can resize the partition.

does this mean that I have to reinstall ubuntu if I want to change the partition size? where is the partition editor?

---

### Post by haertel on 2009-04-29
using GParted Live, I am currently changing the partition size. Let's see if it works.

---

### Post by haertel on 2009-04-30
> **haertel said:**
> using GParted Live, I am currently changing the partition size. Let's see if it works.
it did. it fixed all of my problems, and even enabled my "forward" and "back" buttons, which were previously greyed out, to work. thanks, guys.

---

