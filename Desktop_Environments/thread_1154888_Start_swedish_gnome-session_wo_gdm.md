---
title: "Start swedish gnome-session w/o gdm?"
date: 2009-05-10
forum: Desktop Environments
---

### Post by Ursa on 2009-05-10
What commands or variables do I need to launch gnome desktop in swedish with startx?
I thought that it would use $LANG but this didn't work:

(in .xsession and .xinitrc)
export LANG=se_SE.UTF-8
dbus-launch --exit-with-session gnome-session

The language package is installed and worked fine until I disabled gdm on startup, after that it used the default language. (And I want to know how to fix it without changing default language)

What I want to know is where in the desktop startup process the language is defined and how to change it to swedish for one user.

It seems like a very simple thing to do but I just can't find out how! :D

---

