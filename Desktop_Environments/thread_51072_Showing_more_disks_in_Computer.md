---
title: "Showing more disks in Computer"
date: 2005-07-22
forum: Desktop Environments
---

### Post by DiGiTaLFX on 2005-07-22
Hi

Don't know if anyone's tried BeatriX but in that, if you open up Computer from Places, you get a list of all the various partitions that aren't related to the system (e.g. all of the windows partitions I have). Is there any way that I can set up Ubuntu to do this too? I don't really wanna use them all the time, but when I do its so much easier just to mount it through there than the console.

Thanks

DiGiTaLFX

---

### Post by elfece on 2005-07-22
I had the same problem and to fix it i add "user" in the mount option.

Look this is the line to mount my 1º windows partition in /etc/fstab

/dev/hda1       /media/WinXP    ntfs    user,nls=utf8,umask=0222 0       0

just add "user" and you can acces to that partition in "Equipo" (sorry, i have ubuntu in spanish), and there is a trick (i don't know any other way) to add anything that you want to the "places" menu: go to the "change wallpaper" click "add wallpaper" and at the left side you will see all what is shown in places, and with the "add" button you can customize your "places" menu

Sorry about my english!!!


(I'm a linux noob!)

---

### Post by glandula on 2005-07-22
[QUOTE=][/QUOTE]
 nice tips. anyone know how to add more places to the 'root' of the left pane in nautilus if you use the tree view?

---

### Post by DiGiTaLFX on 2005-07-22
Wayhey! Cheers dude thats what I needed to know. Also good to hear how to add things to the places menu. Its cool that its customisable.

---

