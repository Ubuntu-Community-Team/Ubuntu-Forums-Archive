---
title: "Ubuntu 19.01 / Gnome keeps locking my screen"
date: 2020-04-01
forum: Desktop Environments
---

### Post by bjohas on 2020-04-01
I have disabled all screen locking / dimming / power saving (both from Settings, but also checking gnomesettings on the commandline). Nevertheless Ubuntu 19.10 / Gnome keeps randomly locking screen. (Started about 3 weeks ago when I temporarily changed settings to faster locking, but despite having changed the settings back, the locking still happens.) 


The only pattern I can detect is that the lock happens when I've left the screen idle and then get back to the screen. I.e., the lock happens as soon as I touch the mouse (not before). However, that's not the only time, and it's not consistent either.  During some hours it'll happen e.g. 5-10 times, then not happen at all for another hour.

This is really disruptive ...... please help!

---

### Post by bjohas on 2020-04-19
I wasn't able to find a fix via the Ubuntu / gnome-settings, but it did occur to me that I could uninstall the screensaver itself:
```
sudo apt remove gnome-screensaver
```
While that has completely disabled the screen saver, it's also definitely stopped the accidental locks. (Locking by closing laptop lid and via keyboard shortcut etc still works.)

---

