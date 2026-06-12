---
title: "gdm doesn't start"
date: 2008-06-25
forum: Desktop Environments
---

### Post by super.rad on 2008-06-25
I did a fresh install of ubuntu hardy then decided to change to xubuntu so I installed all the xubuntu files then deleted gnome. gdm is still installed but whenever i start the computer or restart it doesn't automatically load I have to log in from the command line and then run: 
```
sudo /usr/sbin/gdm
``` 
how can I get it to automatically start up?
Thanks

---

### Post by mempman on 2008-06-25
Go into Settings>Admin>login, and select the option that will load up gdm automatcially.

---

### Post by p_quarles on 2008-06-26
GDM should run automatically and by default if it's installed. First thing to try is to make sure it's configured to run:
```
sudo dpkg-reconfigure gdm
```
If it still doesn't work, it may be that it is trying to run too soon (I say this because it works fine if you run it manually). Try running the startup script manually:
```
sudo /etc/init.d/gdm start
```
and see what happens. If that also works, it may just be a matter of reducing its priority during the runlevel 2 initialization sequence.

---

### Post by super.rad on 2008-06-26
thanks alot, p_quarles worked perfectly

---

