---
title: "3ddesk background"
date: 2007-02-19
forum: Desktop Environments
---

### Post by agiamba on 2007-02-19
any idea how to make a picture in the background while switched between desktops with 3ddesk? its just black space right now and id like to add a picture

---

### Post by Lderan on 2007-02-19
I think its in the 3ddesk config file, its in the /etc/3ddesktop/ folder. 
Not at my ubuntu computer so I can't check. 
I think it can also be done from the terminal.

---

### Post by agiamba on 2007-02-21
hmmm sorry i couldnt find it in there. anyone know what the command is?

---

### Post by Lunovis on 2007-03-03
As Ledran said you'll find the config-file in /etc/3ddesktop/3ddesktop.conf.

just put 

default_background 	/yourpath/picture.jpg

above your view definitions. This defines bg for all views.

---

