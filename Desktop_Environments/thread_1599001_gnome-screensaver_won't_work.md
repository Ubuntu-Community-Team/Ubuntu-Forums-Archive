---
title: "gnome-screensaver won't work"
date: 2010-10-17
forum: Desktop Environments
---

### Post by Swiftjay on 2010-10-17
K, so here's what happened.

I wanted to get a screensaver as my background so I installed xscreensaver didn't work out to the way I wanted to so I removed it

apt-get remove xscreensaver then it asked for some other packages to be removed so I did apt-get autoremove

xscreensaver was still there working instead of gnome-screensaver so I did a command search to find folders of xscreensaver and remove them


whereis xscreensaver and it did remove them, but gnome-screensaver still doesn't start up.

i've tried this command gnome-Message: screensaver-command --activate but I get this error:
Message: Screensaver is not running!


I've tried googling for a way to start gnome-screensaver in terminal but no joy, anyone know how to get this to start.

---

### Post by Swiftjay on 2010-10-17
*bump* still having problems any ideas, anyone?

---

### Post by Swiftjay on 2010-10-19
> **Swiftjay said:**
> *bump* still having problems any ideas, anyone?

Solved my problem for anyone who may have issues like this in the future, go to System> administrator> synaptic package and remove xscreensaver and gnome-screensaver from there and re-install gnome-screensaver and that gives you back the screen saver.

---

