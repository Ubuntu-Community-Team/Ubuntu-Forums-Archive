---
title: "ubunto kiosk"
date: 2006-09-21
forum: Desktop Environments
---

### Post by fenixracer on 2006-09-21
looking for some direction on locking down a guest profile on a ubunto system.  This is my first linux setup so there may be something i missing.  Basically We took a Dell desktop wiped out windows and loaded ubunto and we are turning it into a kiosk. The guest account will only be able to use the four icons on the desktop but don't want them to be able to change anything.  Like I said this is my first experiance with linux i'm really impressed with it.

---

### Post by lagagnon on 2006-09-30
Applications, System Tools, Configuration Editor, desktop, gnome, lockdown.

But that only locks command line, printing and save to disk. It is a good start though!

I would then remove superfluous stuff using the Alacarte Menu Editor. Also, set up a guest account and in guest properties remove groups you don't want that user to have access to.

---

### Post by aysiu on 2006-10-01
KDE has *kiosktool*, which is in the repositories.

For Gnome, I think there's this:
[http://www.gnome.org/projects/sabayon/](http://www.gnome.org/projects/sabayon/)

---

### Post by ardchoille on 2006-10-01
One thing that I do for my other users is:

If you want to remove some menu items and have those menu items only available to the admin user, copy the desired menu items from /usr/share/applications to the /.local/share/applications folder in the admin user's $HOME and then remove them from the /usr/share/applications dir. That will take the desired menu items out of the other users' menus but leave them in the admin users' menus.

---

