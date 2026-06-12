---
title: "How can I replace gdm with wdm?"
date: 2006-08-21
forum: Desktop Environments
---

### Post by stani on 2006-08-21
Is it just a matter of
```
sudo apt-get remove gdm
sudo apt-get install wdm
```

I am afraid that something more is needed or not?

---

### Post by aysiu on 2006-08-21
You also have to do Control-Alt-F1, log in, and ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/wdm start
```

---

### Post by cptnapalm on 2006-08-21
Can't you just do this: dpkg-reconfigure wdm

If memory serves, it will bring up a menu for you to select wdm instead of gdm as the display manager.

There is a config file someplace dealing with the *dm and which one to use, but I don't remember it off of the top of my head.

---

### Post by aysiu on 2006-08-21
Oh, yeah, the config file is /etc/X11/default-display-manager

---

