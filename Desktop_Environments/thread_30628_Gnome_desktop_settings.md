---
title: "Gnome desktop settings"
date: 2005-04-29
forum: Desktop Environments
---

### Post by Jin on 2005-04-29
Where is the gnome desktop settings saved? I was thinking making a script that would restore the way it looks when I reinstall ubuntu.

is it the /etc/gnome/ folder?

Cheers
Jin

---

### Post by nad on 2005-04-29
No. Gnome settings are contained in a virtual database of xml files. App settings are stored in your home directory at .gconf and read by the daemon at .gconfd.

Please see Help -> Desktop -> System Administrators Guide for a detailed description.

Please post back your results as I am certain that others would like to know how to do this.

---

### Post by Alexander Kirillov on 2005-04-29
[QUOTE=nad]No. Gnome settings are contained in a virtual database of xml files. App settings are stored in your home directory at .gconf and read by the daemon at .gconfd.

Please see Help -> Desktop -> System Administrators Guide for a detailed description.

Please post back your results as I am certain that others would like to know how to do this.[/QUOTE]
 And also in ~/.gnome2

---

