---
title: "Can't use gedit as root user"
date: 2006-02-14
forum: Desktop Environments
---

### Post by the_duce on 2006-02-14
I can't use gedit as root user in gnome.

---

### Post by the_duce on 2006-02-14
this is the warning I get: 


Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gedit:8200): Gtk-WARNING **: cannot open display:
root@ubuntu:/home/sean2551#

---

### Post by taurus on 2006-02-14
Instead of "su -" to root, try running this from a user account,

sudo gedit

---

### Post by the_duce on 2006-02-14
Thanks, Thats a newbie error.

---

### Post by taurus on 2006-02-14
Since you are a newbie, I strongly recommand you don't log into root directly because one wrong command can wipe out your system...  Instead, use sudo whenever you can and even with that, you still have to be careful on what you execute with sudo!

---

