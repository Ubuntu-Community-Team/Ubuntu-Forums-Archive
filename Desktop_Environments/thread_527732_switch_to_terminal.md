---
title: "switch to terminal"
date: 2007-08-16
forum: Desktop Environments
---

### Post by md5hash on 2007-08-16
hello, how can i disable GDM from loading.. i need the text based login only, but i dont want to uninstall the GDM, i just dont want to start it automatically.

thnkx

---

### Post by merlinus on 2007-08-16
This may work:

/etc/X11/default-display-manager

Comment out /usr/sbin/gdm

-merlin

---

### Post by RedSquirrel on 2007-08-20
> **md5hash said:**
> hello, how can i disable GDM from loading.. i need the text based login only, but i dont want to uninstall the GDM, i just dont want to start it automatically.

thnkx

The way I achieve this is to do:

```
sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/K13gdm
```If you change your mind and you want gdm to run on boot, just do:

```
sudo mv /etc/rc2.d/K13gdm /etc/rc2.d/S13gdm
```


EDIT:

If you want to run gdm after you have logged in to the console, just run:

```
sudo /etc/init.d/gdm start
```

You can also setup ~/.xinitrc and run 'startx' to start X.

[You probably already knew these things, but I thought I would add them just in case. ;)]

---

