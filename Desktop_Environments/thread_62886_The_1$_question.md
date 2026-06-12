---
title: "The 1$ question"
date: 2005-09-06
forum: Desktop Environments
---

### Post by one_ro on 2005-09-06
How do one enter Gnome having installed Kubuntu?

---

### Post by apokryphos on 2005-09-06
[QUOTE=one_ro]How do one enter Gnome having installed Kubuntu?[/QUOTE]
Make sure GNOME is installed; then logout of KDE, at the KDM (the login screen) change the session to "GNOME".

---

### Post by az on 2005-09-06
Install gnome by installing the ubuntu-desktop package.

---

### Post by one_ro on 2005-09-06
[QUOTE=azz]Install gnome by installing the ubuntu-desktop package.[/QUOTE]

A-ha-aaaa...

---

### Post by ryke on 2005-09-06
hi... is there any problem on having KDE and Gnome installed? (my kubuntu is ok now; I would like to try gnome, but my first priority is to keep kubuntu working properly ;-)
thanx

---

### Post by ltmon on 2005-09-06
[QUOTE=ryke]hi... is there any problem on having KDE and Gnome installed? (my kubuntu is ok now; I would like to try gnome, but my first priority is to keep kubuntu working properly ;-)
thanx[/QUOTE]

Just:

sudo apt-get install ubuntu-desktop

and you're good to go.  It shouldn't mess with your KDE desktop at all.

During the install you will be asked if you want to use GDM or continue using KDM (this is the login screen).  It doesn't matter too much which you choose.

Cheers,

L.

---

### Post by Mishura on 2005-09-06
Desktop enviroments pretty much stick to themselves, not messing up anything.  If you got a good Display manager installed (KDM, GDM, the ghastly XDM..) you can switch em up.  I've had at least 7 WMs installed at one time so its alright.

---

### Post by ryke on 2005-09-07
ok, thanx for your help... I'll try Gnome following your indications.
regards

---

