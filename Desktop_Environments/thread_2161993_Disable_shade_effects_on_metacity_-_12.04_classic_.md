---
title: "Disable shade effects on metacity - 12.04 classic (no effects)"
date: 2013-07-12
forum: Desktop Environments
---

### Post by ChrisJacque on 2013-07-12
Hello,
I use 12.04 gnome classic no effects, I enabled composition for metacity but I don't like the sahde effects on the menu and info tips, I think they're useless.. How do I disable it?
Thanks

---

### Post by Krytarik on 2013-07-13
To disable Metacity's compositor effects:
```
gconftool-2 /apps/metacity/general/compositor_effects --type bool --set false
```
To re-enable them again, obviously:
```
gconftool-2 /apps/metacity/general/compositor_effects --type bool --set true
```
Regards.

---

### Post by ChrisJacque on 2013-07-14
It worked for me, just what I needed.
Thank you so much!!

---

### Post by ibjsb4 on 2013-07-14
Another way (a GUI way) is to use gconf-editor (yes, it still has its uses).

[ATTACH=CONFIG]244722[/ATTACH]

In terminal:

```
sudo apt-get install gconf-editor
```

---

