---
title: "can't login after install"
date: 2007-07-29
forum: Desktop Environments
---

### Post by shrndegruv on 2007-07-29
I can't login to the regular gnome session after an install.  I can log in to the failsafe.

[/quote]
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp
 -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mharris"
/etc/gdm/Xsession: Beginning session setup...
bash: no job control in this shell
bash: /home/mharris/.xinitrc: No such file or directory
[/quote]

that is the error in .xsession-error.  

Note that my /home partition was previously in use by another distro.  Im coming back to ubuntu...

---

### Post by pbcartwright on 2007-07-30
sounds like your /home settings are in conflict with your ubuntu setup, I've had that happen when I previously had KDE installed, and then installed gnome. 2 things you can try:
1. create a new user and try to log in to that account, then you can copy your old settings over, a little at a time..
2. rename or remove the .gnome folder or .gnome2 and maybe even .gconfd then try to restart gnome

---

### Post by shrndegruv on 2007-07-30
good idea; will try when I get home

---

