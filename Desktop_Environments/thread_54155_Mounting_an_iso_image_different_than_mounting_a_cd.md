---
title: "Mounting an iso image different than mounting a cd with an iso image???"
date: 2005-08-03
forum: Desktop Environments
---

### Post by NoTiG on 2005-08-03
I tried to mount an image:

```
 sudo mount -t iso9660 -o loop,ro /home/notig/Share/Diablo_CD1.iso /mnt/Diablo
``` 

And it successfully mounts, but when i run 

wine /mnt/Diablo/INSTALLER.EXE 

it says

please insert install disk (iso1 is the install disk) . 

However I burned the ISO onto a cd, and i 

sudo mount /dev/cdrom /mnt/Diablo

that works just fine. and when i run the installer from wine it works as it should. so my question is why is there a difference??? If i mounted them shouldnt it be the same????

---

### Post by Juergen on 2005-08-03
I only can guess here, but IMHO the data should be the same.

But as a copy protection (to avoid beeing run from a 'virtual disk' proggy) the installer might somehow check the properties of the device.
There might be a significant difference.

---

### Post by NoTiG on 2005-08-03
Is it wine that is checking or the installer through wine though? I tried looking in the config file for wine to see if i could tell . When I use a cd instead of the ISO image, and mount the CD to /mnt/Diablo, and then run install it works... and when it asks me for the next cd i dont even have to mount it to /mnt/Diablo... it finds it at /media/cdrom0 . I tried replacing /dev/cdrom with a symbolic link to /mnt/Diablo and it didnt work. I tried replacing the /media/cdrom0 directory with a symbolic link to /mnt/Diablo and it didnt work either. Not sure what to do. I Have a cd writer but i didnt want to waste cd's when i could just mount them. ANd i did end up burning a couple but i think one is bad. so either it was a bad burn or the iso file (the second one) is corrupt , in which case i will end up wasting more cd's just to find out.

---

