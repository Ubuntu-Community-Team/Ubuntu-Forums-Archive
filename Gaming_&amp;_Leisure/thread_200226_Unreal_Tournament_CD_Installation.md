---
title: "Unreal Tournament CD Installation"
date: 2006-06-19
forum: Gaming &amp; Leisure
---

### Post by Moonshine on 2006-06-19
I have the 7 CD to install Unreal Tournament, however, when the installer asks for the next disk, i can't eject disk one. I've tried to eject it by doing 'eject /dev/cdrom but then i get this error

> umount: /media/cdrom-1: device is busy
umount: /media/cdrom-1: device is busy
Error: umount failed
eject: unmount of `/media/cdrom-1' failed


When I try the eject button on the computer case nothing happens.


Thanks for any help!

---

### Post by lucia_engel on 2006-06-20
This may sound stupid but um....did you try rebooting?

---

### Post by polpak on 2006-06-20
[QUOTE=Moonshine]I have the 7 CD to install Unreal Tournament, however, when the installer asks for the next disk, i can't eject disk one. 
[/QUOTE]

The problem I believe is that you ran the installer from the CD. Therefore the drive is in use and cannot be ejected. Try copying the installer to your home directory and run it from there. It worked fine for me.

---

