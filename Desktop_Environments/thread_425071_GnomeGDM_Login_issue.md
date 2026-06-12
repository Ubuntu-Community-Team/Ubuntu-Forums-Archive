---
title: "Gnome/GDM Login issue"
date: 2007-04-27
forum: Desktop Environments
---

### Post by Rever75 on 2007-04-27
Hi,
  I am running Feisty Fawn and when I boot up my system and try to log into my account from GDM the Xsession or GDM resets. This only happens the first attempt after that all other attempts to login are fine. Here is my .xsession-errors:

> /usr/X11R6/bin/xsetroot:  unable to open display ':0'
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "vieirar"
/etc/gdm/Xsession: Beginning session setup...
xrdb: Connection refused
xrdb: Can't open display ':0'
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open display ':0'

(gnome-session:6105): Gtk-WARNING **: cannot open display:  

Note sure if this is a permissions issue or what. This happens with any user I try to log in with on the first attempt. This only happens when logging into a xsession. I have no issues logging into a console.

---

### Post by phidia on 2007-04-27
You can try this method-run "xhost +localhost" to allow all local connections to connect the the X server instance. Hope that helps.

---

