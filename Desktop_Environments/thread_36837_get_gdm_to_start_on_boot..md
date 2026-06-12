---
title: "get gdm to start on boot."
date: 2005-05-24
forum: Desktop Environments
---

### Post by ntnwwnet on 2005-05-24
gnome (or the default desktop) used to start on boot.
now it doesn't.
i accidentally removed it from startup.
and i don't know how.
how do i add it to the startup list again?


ty for your help.

---

### Post by ntnwwnet on 2005-05-24
[QUOTE=ntnwwnet]gnome (or the default desktop) used to start on boot.
now it doesn't.
i accidentally removed it from startup.
and i don't know how.
how do i add it to the startup list again?


ty for your help.[/QUOTE]
 i forgot to add:

after disabling it, i rebooted the machine. now i can login at the "command line"

i need to know how to start it while in a non-gui

---

### Post by Xian on 2005-05-24
[QUOTE=ntnwwnet]i need to know how to start it while in a non-gui[/QUOTE]
If you install it in APT, a config session should run where you can select which DM to use during boot, and then all that should just automagically happen.

Or, you can shortcut this if you have GDM currently installed:
```
$ sudo dpkg-reconfigure gdm
```

---

### Post by ntnwwnet on 2005-05-24
thanks for all your help.

i ended up starting up gdm

/etc/rc2.d/K13GDM

and installing kde instead.


thanks!


<3 ubuntu!

---

