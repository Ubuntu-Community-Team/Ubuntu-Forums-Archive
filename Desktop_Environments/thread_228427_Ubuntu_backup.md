---
title: "Ubuntu backup"
date: 2006-08-03
forum: Desktop Environments
---

### Post by basplayman on 2006-08-03
Hello guys,
I am new with ubuntu and i tried to learn it.
sorry for my english but it is really bad as you can see.
Now my quistion :p
I have now a good ubuntu on a harddisk, but i gonna buy a new pc over 2 weeks and i want this ubuntu with all files and theme's email firefox e.d. on that pc.
so is there a easy program for me that backup all files from ubuntu so i can replace it later with thesame program, so i dont have to install all things again that is pretty anoying.

Greetz bas van den burg (13 years old)

---

### Post by ciscosurfer on 2006-08-03
You need to enable your universe repository first.  

Then copy/paste this command in a terminal to get Simple Backup```
sudo aptitude update && sudo aptitude install sbackup
```

---

### Post by mithras86 on 2006-08-03
Hey Bas, it looks your Dutch, so I'll explain your question in Dutch.

Je eigen persoonlijke bestanden zitten op de partitie /home. Als je die kopieert, heb je bijna al je instellingen terug. Wat je ook kan doen, is een backup maken en die op de nieuwe pc terugzetten. Daarvoor moet je ff kijken, [hier]("http://ubuntuforums.org/showthread.php?t=35087"). Let wel op, de code daar gebruikt is ```
tar cvpzf backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys
```Maar de nieuwe Ubuntu moet je ```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```gebruiken.

Let hierbij wel op dat je dezelfde partitieindeling houdt als op de oude pc. De nummers van de partities moeten namelijk hetzelfde zijn. Als dat niet zo is, moet je na het terugzetten van de partities het bestand /boot/grub/menu.lst aanpassen naar jouw eigen situatie. Ik hoop dat het lukt;)

---

### Post by basplayman on 2006-08-03
thx guys for the answers :).
yes exactly i am dutch.
ok the program from ciscosurfer is great only i must learn how it works :p so i must make a backup with that program and then restore it on the new ubuntu and then it works :confused: 
Good sounds good8-) 
if there are programs that work exactly like that programs you can tell it here then i can try them.

---

### Post by ciscosurfer on 2006-08-03
Here is the [documentation/wiki]("http://sbackup.sourceforge.net/HomePage") for sbackup :grin:

---

### Post by frodon on 2006-08-03
BTW, if you want to transfert your ubuntu installation on a new hardware it can work but it is painful and far more unstable than a fresh install.
So IMHO there's no interest in trying to transfert an ubuntu installation on a new hardware.

If you're just looking for an archive system to keep all your config files for archive the solution given works fine.
For firefox bookmarks you have to export them in a file if you want to transfer them on another computer (go in manage bookmark window to do it).

---

### Post by basplayman on 2006-08-03
@Frodon yes i have thinked of that option but i have heared much negative reactions of that methode, and nvidia drivers e.d.
so i install ubuntu again and backup everything, that is the easiest way i think.
btw are all files in home like: Theme's, my music @ desktop, and the drivers of nvidia glx, or all settings for ubuntu. are all that files in home :-k.
if the answer is yes i will backup home.

---

