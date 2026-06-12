---
title: "cant install fallout under wine"
date: 2007-04-14
forum: Gaming &amp; Leisure
---

### Post by hempa on 2007-04-14
hi i am trying to install fallout but wine cant open the install.exe file. i can run the fallout setup file so that i can play as long as the cd is in the cd rom but how can i install the game on my computer so that i dont need the cd??

---

### Post by xopher on 2007-04-14
You could rip the cd to an iso-file, then mount the iso-file, and add it as a drive in winecfg.

---

### Post by hempa on 2007-04-14
ok i have ripped to iso but i need some help with adding it as an extra drive (im really new to this)

---

### Post by lakersforce on 2007-04-14
Make an iso of the cd (in Gnome right-click the cd icon and choose the appropiate menu item).
After the image is done open a terminal.

```
sudo mkdir /media/cdimage
```
then navigate to where your iso file is and type
```
sudo mount -o loop yourisoimage.iso /media/cdimage
```


If your cd contains somekind of security like securom you cant copy it.

EDIT: you have to setup winecfg to find the cdimage dir. That is straightforward though.

---

### Post by hempa on 2007-04-14
hello again when i wrote the commands you gave me i got this

armcandy@armcandy-desktop:~$ sudo mount -o loop /home/armcandy/FALLOEME.iso/media/cdimage
Password:
mount: can't find /home/armcandy/FALLOEME.iso/media/cdimage in /etc/fstab or /etc/mtab
armcandy@armcandy-desktop:~$

is the iso supposed to be in the media/cdimage folder? i have checked and the folder is there in /media and i have tried to copy the iso to that folder but it says i am not allowed to write to that folder. now the iso is in /home/armcandy
i need a little bit more help, i feel like a retard but i am really new to this

---

### Post by lakersforce on 2007-04-14
It is because of a typo! There should be a space between like this: ".iso /media...". You wrote it like this ".iso/media...".

---

