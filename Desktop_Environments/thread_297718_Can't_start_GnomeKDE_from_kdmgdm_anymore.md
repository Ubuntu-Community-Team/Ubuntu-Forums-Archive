---
title: "Can't start Gnome/KDE from kdm/gdm anymore"
date: 2006-11-11
forum: Desktop Environments
---

### Post by Case_f on 2006-11-11
This weird thing happened to me, literally overnight. I can't log into any DE using either gdm or kdm. Kdm throws me back to the login screen just a second or so after logging in (I can't see any DE splashscreen or any sign of it actually starting), gdm says that it couldn't start session and starts xterm. Funny thing is that if I run gnome-session or startkde from that xterm, it starts just fine (although gnome-session complains something about dbus and gnome-volume-manager and also desktop background is just plain grey, but everything seems to work). If disable graphical login and just use console login and then run startx (while having 'exec /usr/bin/startkde' in ~/.xinitrc), again KDE starts without any errors. I can't find any error messages in system logs. Tried to make new user and logging in, no luck. Even tried purging kdm, gdm, even whole Xorg and installing again...nothing. Still the same results. I\ve lost several hours over this today (and basically resigned to using the startx way for now).

Any ideas what the hell is going on here?

---

### Post by gazj on 2006-11-11
very strange, have really no idea, although its unlikely that both gdm and kdm are to fault, why not try xdm or wdm out of intrest.

let us know the result

---

### Post by Case_f on 2006-11-11
I forgot to mention that Xdm doesn't work either. I didn't try any other login manager, seemed pointless to me.

---

### Post by Case_f on 2006-11-16
Well, it seems it is a DBUS issue after all...I just found out that although dbus-daemon is starting fine, the DBUS_SESSION_BUS_ADDRESS variable is empty and therefore every program using DBUS says 'Unable to determine the address of the message bus'. Which is probably why the graphical login doesn't work, I guess. I've checked all the config/starting files related to DBUS and everything seems to be fine and/or working (/etc/init.d/dbus, /etc/X11/Xsession.d/75dbus_dbus_launch...)

Any idea, anyone?

---

