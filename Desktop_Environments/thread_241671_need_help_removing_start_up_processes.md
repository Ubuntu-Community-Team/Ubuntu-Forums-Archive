---
title: "need help removing start up processes"
date: 2006-08-22
forum: Desktop Environments
---

### Post by afbase on 2006-08-22
I would like to know how to remove certain processes out on start up.  I looked at /etc/fstab, but that only deals with mounting hard drives.  I would like to remove gnome-desktop from start up.  I run a server and i figure that i really don't need that to start up when i turn on the computer.

---

### Post by r4ik on 2006-08-22
Try,

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

It might be what you want.

Good luck !

---

### Post by nanotube on 2006-08-22
startup scripts are all stored in /etc/init.d
and are linked to from directories of the form /etc/rcX.d (where X is a number). 
For example /etc/rc2.d is the dir for runlevel 2, which is the default on ubuntu.

the script that starts the gui is called "gdm"

the best way to play with the startup scripts is to install package "sysv-rc-conf"
run it as root, and then you can just untick the checkboxes for gdm for all runlevels. that will remove the links to /etc/init.d/gdm from all the runlevel dirs, and that way your machine will start in console mode.

if, later on, you do decide to start up the gui manually on occasion, all it would take is
```
sudo /etc/init.d/gdm start
```

have fun. :)

---

### Post by nanotube on 2006-08-22
> **r4ik said:**
> Try,

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

It might be what you want.

Good luck !

note: that link gives info for uninstall of the desktop environment and all accompanying packages, not just stop it from running on bootup. if that is what the original poster wants to do, then have at it. but if you want to just stop it from starting on boot, but still have the opportunity to start it at some point, do the sysv-rc-conf as i mentioned.

---

### Post by OffHand on 2006-08-22
```
sudo apt-get install bum
```

---

