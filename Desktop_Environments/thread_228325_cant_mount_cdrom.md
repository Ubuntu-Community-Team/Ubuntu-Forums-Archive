---
title: "cant mount cdrom"
date: 2006-08-03
forum: Desktop Environments
---

### Post by polloz on 2006-08-03
hello,

i have the following problem. i did a clean install of kubuntu, everything went well. the problem is that when i put a cd in de drive, nothing happens. i tried using different cd's, but the problem persists. i also have a windows xp partition, and when i log into it, de cdrom does work. what might the problem be? i look into the folder /media/cdrom/ but theres nothing inside, although i have already inserted a cd in the machine. help please.
thanks,

polloz

---

### Post by orb9220 on 2006-08-03
open up a terminal and type   gedit /etc/fstab

Copy what is in that file then paste it here in a post so people can see.

This will show us if your cdrom is being monted and to where.

---

### Post by polloz on 2006-08-03
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1    /media/Windows_XP  ntfs  nls=utf8,umask=0222 0    0

---

### Post by orb9220 on 2006-08-03
Well it shows that you have a scsi cdrom? Is that correct and it is being mapped to your /media/cdrom0 folder.

If it is scsi try searching on forums for scsi cdrom and see if others have problems.

Mine is hdc which is an ide drive type.

Sorry I couldn't be more help.

---

### Post by redbull_monsta on 2006-08-03
Some IDE cdrom drives show up as SCSI due to their internals...

Try mounting the cdrom manually

mount /dev/scd0 /media/cdrom0 - then try to browse the folder or do an ls of the directory 

ls -l /media/cdrom0

---

### Post by polloz on 2006-08-05
hi,

i've triend to mount it manually as you said, but it still doesn't work. what can the problem be? it works perfectly in my windows partiton. yesterday, the cdrom suddenly started working, but when i inserted an audio cd, i couldnt play the music, or at least couldn't hear it. then i inserted a dvd movie and everything went fine, i was able to watch the movie hear its audio. now i've upgraded to kubuntu 3.5.4 and the error is back. help please.
thanks everyone for their help

---

### Post by polloz on 2006-08-05
bump

---

