---
title: "Removing kubuntu"
date: 2005-08-16
forum: Desktop Environments
---

### Post by Brunellus on 2005-08-16
So in a fit of experimentation, I did an apt-get install kubuntu-desktop.

I've decided I'd rather stick with gnome and/or XFCE, and would like to remove KDE.  I tried just removing kubuntu-desktop, but sadly, apt just wants to remove the metapackage and not all the dependencies that existed before.

At the moment, I'm left with hunting down all the individual KDE packages, making a list of them, and piping that list into apt to remove them all, then apt-get installing ubuntu-desktop again to take care of any 'accidental' removals of common dependencies.  does anyone have a more elegant solution?

---

### Post by yongyi on 2005-08-16
try this:
sudo apt-get --purge remove kdelibs4 libarts1

---

### Post by zAo on 2005-08-16
This above will not remove all players.

Use debfoster:
```
apt-get install debfoster
debfoster
``` 
and follw the instructions CAREFULLY!

---

### Post by Brunellus on 2005-08-16
[QUOTE=zAo]This above will not remove all players.

Use debfoster:
```
apt-get install debfoster
debfoster
``` 
and follw the instructions CAREFULLY![/QUOTE]

Do I run debfoster after removing the kde libs, or before?

---

### Post by Brunellus on 2005-08-17
fixed, using debfoster.  ran it, picked my packages, and it uninstalled kubuntu entirely.  

Thanks!

now, back to GNOME

---

