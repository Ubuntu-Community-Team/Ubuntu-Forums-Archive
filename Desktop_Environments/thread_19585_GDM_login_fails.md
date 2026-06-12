---
title: "GDM login fails"
date: 2005-03-12
forum: Desktop Environments
---

### Post by Dacobi on 2005-03-12
When logging in with gdm I get an error saying that my X session lasted less than 10 seconds and the following errors are written in ~.xsession-errors:

dacobi@Zentipede:~$ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "dacobi"
/etc/gdm/Xsession: Beginning session setup...
Xlib: connection to ":0.0" refused by server
Xlib: Protocol not supported by server

xrdb: Can't open display ':0'
Xlib: connection to ":0.0" refused by server
Xlib: Protocol not supported by server

xrdb: Can't open display ':0'
Xlib: connection to ":0.0" refused by server
Xlib: Protocol not supported by server

xrdb: Can't open display ':0'
Xlib: connection to ":0.0" refused by server
Xlib: Protocol not supported by server

xrdb: Can't open display ':0'
Xlib: connection to ":0.0" refused by server
Xlib: Protocol not supported by server


(gnome-session:4356): Gtk-WARNING **: cannot open display:

startx works just fine.

I using Hoary, just upgraded from debian unstable.

Any ideas as to what may be the problem?

/Dacobi

---

