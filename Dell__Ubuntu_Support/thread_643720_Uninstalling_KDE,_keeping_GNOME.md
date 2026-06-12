---
title: "Uninstalling KDE, keeping GNOME"
date: 2007-12-18
forum: Dell  Ubuntu Support
---

### Post by ons21nesh on 2007-12-18
Hi, loads of posts on keeping Gnome and KDE, but cant find one on uninstalling/getting rid of KDE.
tried KDE out, prefer GNOME (newbie, i know)

i used Aptitude to install the KDE environment, then to uninstall i used 

sudo aptitude remove kubuntu-desktop

didnt work out, :(, KDE is still in options during log in screen and shutdown screen and boot screen both show KUBUNTU...help


Thanks in advance !!!

---

### Post by pbcartwright on 2007-12-18
kdm is the login manager for KDE, try uninstalling kdm

---

### Post by Zalbor on 2007-12-18
Now that you've removed kubuntu-desktop, the rest of the KDE packages must be auto-removable.
I use Synaptic myself, and it has a place where you can see which packages are auto-removable. There must be one in aptitude too. Simply removing all these should fix it. I've done exactly the same in the past.

---

