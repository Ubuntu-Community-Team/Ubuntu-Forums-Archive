---
title: "Editing system files"
date: 2005-04-29
forum: Desktop Environments
---

### Post by mig_l on 2005-04-29
Hi

how can i edit /boot/grub/menu.lst ?

i just want to change the default boot, and comment some entries (like memory test, is not that usefull...)

i have tried with kate editor but doesn´t save... :roll: 

i know i must have root privileges... but how can i do this in the X (graphical mode)?

---

### Post by Juergen on 2005-04-29
Just open a konsole and type```
sudo kate /boot/grub/menu.lst
```It will ask for your (user-)password, and then kate should open...

If you don't like the idea of using a shell at all, create a new program-launcher that starts 'gksudo kate' 
(I don't know what's it called in KDE, kdesudo instead of gksudo?)

---

### Post by petertc on 2005-04-29
open konqueror 
browse to the file you want to open 
do a rh mouse click on it then down to actions and edit as root
enter your password when required this will then open the files as root so you can alter it. 
Hope this helps

---

### Post by mig_l on 2005-04-29
[QUOTE=petertc]open konqueror 
browse to the file you want to open 
do a rh mouse click on it then down to actions and edit as root
enter your password when required this will then open the files as root so you can alter it. 
Hope this helps[/QUOTE]
 is that simple? :)
I will try it when i get home!

Thank´s to you both!

---

### Post by mig_l on 2005-04-29
[QUOTE=petertc]open konqueror 
browse to the file you want to open 
do a rh mouse click on it then down to actions and edit as root
enter your password when required this will then open the files as root so you can alter it. 
Hope this helps[/QUOTE]
 thanks works just fine!

:D

---

