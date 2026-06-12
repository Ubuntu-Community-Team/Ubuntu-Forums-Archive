---
title: "Recognistion of cd"
date: 2009-04-11
forum: General Help
---

### Post by simonlugi on 2009-04-11
I have recently installed kubuntu 8.01.
When I inserted a music cd into my machine, it was not recognized by Dolphin, however I could play it by running Amarok (Play Audio CD).

I also wanted to rip to mp3 format using Sound juicer. 
SJ does not convert to mp3 even though under Preferences > Edit profile it shows mp3 is available.

---

### Post by Gen2ly on 2009-04-11
What's your /etc/fstab show for cd/dvd settings?

---

### Post by pbpersson on 2009-04-11
for MP3 format, did you install kubuntu-restricted-extras?

---

### Post by rotary12 on 2009-04-11
> **simonlugi said:**
> I have recently installed kubuntu 8.01.
When I inserted a music cd into my machine, it was not recognized by Dolphin, however I could play it by running Amarok (Play Audio CD).

I also wanted to rip to mp3 format using Sound juicer. 
SJ does not convert to mp3 even though under Preferences > Edit profile it shows mp3 is available.

I have the same problem it recognize a data CD but not a music CD

---

### Post by simonlugi on 2009-04-12
> **Dirk.R.Gently said:**
> What's your /etc/fstab show for cd/dvd settings?

Copy of fstab below

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7cd880ea-5f42-40b7-817e-74d18a8abee6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=519a6af6-2c6f-4f5a-83e1-a60bd1cc93ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by simonlugi on 2009-04-12
> **pbpersson said:**
> for MP3 format, did you install kubuntu-restricted-extras?

IN adept I have all the boxes ticked under Kubuntu software and under third party software I have Restricted Multiverse  

There isnt a repository specifically called "Kubuntu restricted extras"

---

