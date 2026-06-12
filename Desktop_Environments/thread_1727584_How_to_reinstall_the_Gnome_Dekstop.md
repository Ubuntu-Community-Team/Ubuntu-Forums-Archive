---
title: "How to reinstall the Gnome Dekstop"
date: 2011-04-12
forum: Desktop Environments
---

### Post by romy.mathew on 2011-04-12
I have some problem with Apache2 Server that hold my login screen to stop showing login screen, I need to enter the dekstop via

1.Alt+Ctl+F1, 
2.sudo service gdm-stop
3.startx

By Mistake I deleted some library files to fix the above issue and got much worse as many of my dekstop icon seems to be removed for ever and many not responding to my clicks

I need to a have a fresh Gnome Dekstop

---

### Post by coffeecat on 2011-04-12
If you re-install the metapackage ubuntu-desktop, that should bring in the stuff you deleted. Everything that makes up the Ubuntu version of the gnome desktop is a dependency (or dependency of a dependency) of ubuntu-desktop.

---

