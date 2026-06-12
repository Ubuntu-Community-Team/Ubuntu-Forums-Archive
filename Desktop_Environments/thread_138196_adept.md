---
title: "adept"
date: 2006-03-01
forum: Desktop Environments
---

### Post by penquin on 2006-03-01
I am trying to get adept to help install ubuntu over kubuntu.  can anyone help with exactly what I am suppose to do?  I am new to linux and ubuntu.

---

### Post by Beej on 2006-03-01
you need to install the ubuntu-desktop package. When it has installed, log out to the login screen. There should be a menu titled sessions, choose gnome, and then login as normal. Welcome to Ubuntu.

---

### Post by gingermark on 2006-03-01
When ubuntu-desktop is installing you will be asked whether you want to use KDM or GDM. Either will work, the main difference is the environment from which you can directly shutdown / reboot - KDM allows this in KDE, GDM allows this in GNOME.

Of course, you can log out of the environment and then shut down, so this isn't much of an issue. Just giving you a heads up.

---

### Post by Jucato on 2006-03-01
As you will be using Adept, pay special attention to the things that will be installed and/or removed, so that it will be easier to uninstall later. 

Personally, I prefer to use the command line for bulk installation such as this, so that I can copy-paste the name of the packages and save it in a text file for future use. so that if I ever need to uninstall, I just copy-paste the names again and use apt-get remove. :D

---

