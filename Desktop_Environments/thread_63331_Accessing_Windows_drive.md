---
title: "Accessing Windows drive"
date: 2005-09-07
forum: Desktop Environments
---

### Post by dancavallaro on 2005-09-07
I'm not sure if this is in the right forum, but I'll ask anyway. I have WIndows XP on my primary HD, and Ubuntu on my secondary drive. From Ubuntu, how can I get access to my primary (Windows) drive to access my music?

---

### Post by eraclito on 2005-09-07
[QUOTE=dancavallaro]I'm not sure if this is in the right forum, but I'll ask anyway. I have WIndows XP on my primary HD, and Ubuntu on my secondary drive. From Ubuntu, how can I get access to my primary (Windows) drive to access my music?[/QUOTE]

which file system have you got on win partition? (fat32 or ntfs)

whit fat32 it is easy: you have to edit you /etc/fstab and mount win partition

something like:

/dev/hda1 /media/windows vfat auto,rw,umask=000 0 0 

in the second case... big trouble  :-? 

eraclito

---

### Post by invisage01 on 2005-09-07
check the unofficial guide.. it's quite easy to do.. ntfs will only be read only though.. if you create a fat32 partition you should be able to get read/write access to it..

---

### Post by dancavallaro on 2005-09-07
my windows partition is NTFS... that's fine if it's read-only thought, i just wanna access my music

---

### Post by toonie on 2005-09-07
Hi,

just follow these simple steps:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows) 

Greetings,
Toonie

---

