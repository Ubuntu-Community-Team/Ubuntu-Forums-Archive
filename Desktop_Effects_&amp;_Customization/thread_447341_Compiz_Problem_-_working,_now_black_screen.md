---
title: "Compiz Problem - working, now black screen"
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by ecrissman on 2007-05-17
I installed Compiz on Feisty today and it was running perfectly, not even a glitch.  Then I tried installing screenlets and on reboot my monitor went black.  Now I can only log in to a terminal.  Has anyone else had this problem and how can I fix it with command line? 

I am running a Feisty on a new laptop pc with an ATI Xpress 200M card and 1G memory. I am four days new to Linux but I can make my way through the terminal okay.

Any suggestions? How can I disable Compiz and will I be able to restore the desktop/effects?

Thanks.

I managed to login to gnome failsafe and got this error (~/.xsessions-errors file)
Here is the error message:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w
/var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l
":0" "eric"
SESSION_MANAGER=local/our-notebook:/tmp/.ICE-unix/5717
Window manager warning: "" found in configuration database is not a
valid value for keybinding "toggle_shaded"
start: Need to be root
Initializing gnome-mount extension
Unable to open desktop file
file:///home/eric/Desktop/Google-googleearth.desktop for panel launcher:
No such file or directory

(gnome-power-manager:5778): GnomeUI-WARNING **: While connecting to
session manager:
IO error occured opening connection.

(compiz-tray-icon:5779): GnomeUI-WARNING **: While connecting to session
manager:
IO error occured opening connection.

(search:5774): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```

---

