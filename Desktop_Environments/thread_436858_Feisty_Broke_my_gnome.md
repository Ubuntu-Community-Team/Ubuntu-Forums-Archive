---
title: "Feisty Broke my gnome"
date: 2007-05-08
forum: Desktop Environments
---

### Post by redbluemangle on 2007-05-08
Now when I log i get "I've detected penals already running" and the "This session alstes less than 10 seconds" and the log for that error is:
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "brian"
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/home:/tmp/.ICE-unix/25931
Initializing gnome-mount extension
```

I've tried deleting .gnome and .gnome2 from my home folder and also using apt to uninstall and reinstalling gnome(ubuntu-desktop) when I do that it only removed a 45kb package :-/

I'm stuck using KDE which I greatly dislike.

I

---

### Post by ozorba on 2007-05-08
Try this from the command line:

sudo aptitude remove ubuntu-desktop

to remove and

sudo aptitude install ubuntu-desktop 

to reinstall the gnome.

---

### Post by mlind on 2007-05-08
Make a backup of your ~/.gconf directory and the remove it and restart xserver. Does the problem persist?

---

