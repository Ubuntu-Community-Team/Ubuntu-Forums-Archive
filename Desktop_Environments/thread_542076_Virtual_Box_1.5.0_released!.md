---
title: "Virtual Box 1.5.0 released!"
date: 2007-09-03
forum: Desktop Environments
---

### Post by Jose Catre-Vandis on 2007-09-03
Released today is the update to 1.5.0 of Virtualbox.

This is full of fixes and goodies:

Sorts out Shared Folders and USB for Xp and Vista guests

Implements a Seamless mode which is an absolute cracker (hence the reason for posting in desktop environments!)

[www.virtualbox.org](www.virtualbox.org)

Just install the new deb over the old one (I used a deb for my initial install on edgy)

then you will need to update the additions in each of your VMs

BTW the 1.5.0 Additions iso is lurking in /usr/share/virtualbox 

**[COLOR="DarkRed"]Vastly improved VM experience[/COLOR]**

---

### Post by maybeway36 on 2007-09-03
You can also use the apt repo, just run the following commands to add it in feisty:
```
sudo su
wget -O - http://www.virtualbox.org/debian/innotek.asc | apt-key add -
echo deb http://www.virtualbox.org/debian feisty non-free >> /etc/apt/sources.list
exit
```

---

