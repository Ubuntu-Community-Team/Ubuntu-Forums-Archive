---
title: "problems with xsession"
date: 2005-08-12
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-08-12
today i rebooted my machine, and logged back in to ubuntu and when i logged in it gave me some error about my account being only logged in for 10 seconds and there was more to this error:


/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "root"
/etc/gdm/Xsession: Beginning session setup...
Xsession: unable to start X session --- no "/root/.xsession" file, no 
"/root/.Xsession" file, no session managers, no window managers, and no 
terminal emulators found; aborting.
Syntax error



i log in as root all the time, and i think before i rebooted today i moved a folder by accident and im not sure which folder it was.  Is th ere any way to fix this ?

---

### Post by Stormy Eyes on 2005-08-12
I usually help with .xsession issues, but I can't help you with this because I *never* login as root.

---

### Post by DarkManX4lf on 2005-08-12
well this doesnt only apply to root, this happens to my regular user accounts too....

---

### Post by DarkManX4lf on 2005-08-13
ok so i installed kde and i can login to kde fine, but i cant login to gnome i can only go into gnome failsafe...how do i fix  gnome ?

---

