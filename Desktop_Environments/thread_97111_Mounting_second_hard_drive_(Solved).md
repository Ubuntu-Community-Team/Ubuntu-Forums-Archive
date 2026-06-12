---
title: "Mounting second hard drive (Solved)"
date: 2005-11-30
forum: Desktop Environments
---

### Post by Zodiac on 2005-11-30
I have a slave harddrive that is formatted in FAT32 and partitioned into one humongous section. 

I am trying to mount it, but when I do I get an error saying that I don't have access to do so.

Am I perhaps doing to incorrectly, or is something else going on?

Any help is appreciated thanks!!!

---

### Post by teaker1s on 2005-11-30
'sudo' in front of the command to gain root permission

---

### Post by Zodiac on 2005-11-30
I'm pretty sure I did.... I wish I was in front of the comp to give er a try...

I hope thats the answer! :)

---

### Post by aysiu on 2005-11-30
```
sudo fdisk -l
``` will tell you the location of your FAT32 partition. [These instructions](http://www.ubuntuguide.org/#automountfat) will help you mount it properly, but they assume your partition is located at /dev/hda1 (adjust accordingly).

If you need to know where the terminal is: Applications > Accessories > Terminal

---

### Post by Zodiac on 2005-11-30
[QUOTE=aysiu]```
sudo fdisk -l
``` will tell you the location of your FAT32 partition. [These instructions](http://www.ubuntuguide.org/#automountfat) will help you mount it properly, but they assume your partition is located at /dev/hda1 (adjust accordingly).

If you need to know where the terminal is: Applications > Accessories > Terminal[/QUOTE]

Well I gave it a try, and I didn't get a single error... it just didn't work.

What do ya think?

Oh yea, it was hdb.

---

### Post by aysiu on 2005-11-30
It can't just be hdb. It has to hdb1 or hdb2, etc. Can you post (copy and paste) the output of these three command? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by Zodiac on 2005-11-30
Wow aysiu you were absolutely correct.... it was hdb1. 

Thanks for the awesome help everyone!

w00t!

---

