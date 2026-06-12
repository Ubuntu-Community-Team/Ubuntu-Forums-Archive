---
title: "autoremoved too much ?"
date: 2007-01-15
forum: Desktop Environments
---

### Post by GoldWing on 2007-01-15
I have used the apt-get autoremove (is that something that is not safe :-k ? )
It seems apt-get removed a few packages I still needed; after restart my laptop, I can't go in X anymore. When I launch startx manually, nothing happens (10 seconds of dark screen).

My Xorg.log file show that a lot of fonts are missing, other errors are not relevant I think.
How can I reinstall the necessary fonts ?
What else do I need to check so that my gui starts again (standard Gnome btw).

Oh yes, 6.10 is my version.

---

### Post by taurus on 2007-01-15
```
sudo aptitude update
sudo aptitude install xorg
startx
```

---

### Post by GoldWing on 2007-01-15
Thanks, that installed a whole lot of missing fonts.
Xorg works great again.
One thing I am still missing is the 'wifi' icon on my taskbar (I could chose and configure the networks with it). What package was that ?

---

### Post by taurus on 2007-01-15
```
sudo aptitude install network-manager network-manager-gnome
```

---

