---
title: "Updatirng to drapper"
date: 2006-05-15
forum: Desktop Environments
---

### Post by Paradoxx on 2006-05-15
I want to update to drapper from breezy, but i just can't.

I've tried to change "breezy" to "drapper" in the sources.list, but that didn't work

I also tried the command "gksudo update-manager -d" with out any luck...

Can any help me ?

EDIT: Ups... Titel sould be "Updating to drapper"

---

### Post by bluevoodoo1 on 2006-05-15
Here's an easy guide to follow...
[http://www.psychocats.net/ubuntu/dapper.php](http://www.psychocats.net/ubuntu/dapper.php)

---

### Post by Ramses de Norre on 2006-05-15
The name is 'dapper' ;)
And what error did you get with the update manager?

---

### Post by Paradoxx on 2006-05-15
[QUOTE=Ramses de Norre]The name is 'dapper' ;)
And what error did you get with the update manager?[/QUOTE]

aaah... thats the problem, stupid me :D 

Thank you both for your replys

---

### Post by bluevoodoo1 on 2006-05-15
[QUOTE=Ramses de Norre]The name is 'dapper' ;)
And what error did you get with the update manager?[/QUOTE]

HAHA! I didn't even notice that!

---

### Post by ori.livneh on 2006-05-15
or in one command:

> sudo sed -i s/breezy/dapper/g /etc/apt/sources.list && sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by aysiu on 2006-05-15
[QUOTE=ori.livneh]or in one command:[/QUOTE] Can you modify that so that it detects how many and which one(s) of these a user is running: Gnome, KDE, XFCE, and then install the appropriate package(s) (ubuntu-desktop, kubuntu-desktop, xubuntu-desktop, respectively) before changing up the sources.list?

---

### Post by ori.livneh on 2006-05-15
aysiu, not sure what you mean. why would you need to install ubuntu-desktop or kubuntu-desktop if the user is already running Gnome or KDE, respectively?

---

### Post by aysiu on 2006-05-15
[QUOTE=ori.livneh]aysiu, not sure what you mean. why would you need to install ubuntu-desktop or kubuntu-desktop if the user is already running Gnome or KDE, respectively?[/QUOTE] Read the description: > **The Ubuntu desktop system**
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, [i]it is recommended that you keep it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).[/i] Emphasis added. Making sure you have the proper -desktop package installed before the upgrade ensures that you not only get newer versions of what you already have installed but that you get the full Dapper experience.

It's also likely that you'll get dist-upgrade breakage.

---

