---
title: "Mounting and .iso on CDROM?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by tenxt on 2006-09-26
I read some post about mounting and .iso but i didnt work for me. This is what i get in terminal:

sudo mount -o loop -t iso9660 1.iso /cdrom
mount: wrong fs type, bad option, bad superblock on /dev/loop4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by orb9220 on 2006-09-26
sudo mount -t iso9660 -o loop <FILENAME.iso> /media/cdrom

So sudo mount -o loop -t iso9660 1.iso /cdrom becomes
   sudo mount -o loop -t iso9660 1.iso /media/cdrom

and is your iso named 1.iso?

---

### Post by tenxt on 2006-09-26
yes the iso name is 1.iso, and i tried the way u said and i get same error.


sudo mount -o loop -t iso9660 1.iso /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/loop4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by meng on 2006-09-26
Is it possible that 1.iso is not actually an ISO? Just curious, it may explain that error message. OTOH, 1.iso sounds like it's an ISO you created yourself (which clearly means that it IS an ISO!)

---

### Post by orb9220 on 2006-09-26
No yours is 
sudo mount -o loop -t iso9660 1.iso /media/cdrom mine would be
sudo mount -t iso9660 -o loop 1.iso /media/cdrom

you have to copy and paste commands given in forums so you don't enter mistakes.

---

