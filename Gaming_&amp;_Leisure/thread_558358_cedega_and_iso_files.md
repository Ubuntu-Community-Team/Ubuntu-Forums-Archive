---
title: "cedega and iso files"
date: 2007-09-23
forum: Gaming &amp; Leisure
---

### Post by Chadwick17 on 2007-09-23
Ok, I actually have a couple of questions here. First off is there a way to have cedega read .iso images of games that I have? I have a ton of hard disk space and would like to store Starcraft/Warcraft isos in a folder and just have cedega read them from there so I don't have to spin up the cd drive every time. 

I tried to get cedega to read iso files by installing AcetonelISO2 but I don't see anyway to get cedega to read from the virtual drives that AcetoneISO2 sets up. So if its not possible for cedega to read those virtual drives is there an easy way to rid myself of AcetoneISO2 and all of the KDE krap it installed as well?

Thanks!

---

### Post by DoktorSeven on 2007-09-23
sudo mount -t iso9660 -o loop /path/to/youriso.iso /media/cdrom

---

### Post by bulletxt on 2007-09-24
first of all you are a bit confused.

1) cedega makes you select the file installer, so just browse to the virtual-drive/X and select it.

2) if for any reason you don't like to point to virtual-drive/X, you can allways chooes to mount the image where you prefer. under utilies there is a nice voice called: generic mount


3) if you still want to remove KDE (and kde is everything but not krap as your ignorance thinks) remove kdelibs4c2a from synaptic

---

### Post by Chadwick17 on 2007-09-24
Actually its looking for the CD when I want to run the game and I can't seem to change where it looks besides /media/cdrom

I know I can install it from any location but actually running it from any location is the problem. So I just use Gmount-iso to mount it to the cdrom location and its fine.

I realize I need the KDE stuff now for Amarok, so I'll just keep it there for now. I apologize about the krap comment but it just seems like it loaded a ton of stuff that I didn't want for one simple program... I don't need konsole or konquerer but it got installed anyway...thank god for synaptic!

---

