---
title: "bottom panel quit responding"
date: 2014-09-15
forum: Desktop Environments
---

### Post by bobnw on 2014-09-15
Xbuntu 14 desktop

The bottom panel quit responding but the top panel still works.  The windows buttons on the bottom panel do not work,  but the windows can be openned from Ksysguard.   The "show desktop" widget and other widgets on the bottom panel also do not respond.

Any ideas?

Thanks

---

### Post by ibjsb4 on 2014-09-15
Thats odd ..

As far as I know the panels do not operate separator.  They are both xfce4-panel, so both should work or not at all.

Try this in terminal:
```
killall xfce4-panel
```
Or just reboot your system.

If that does nothing, you could try a reinstall of the panel package.
```
sudo apt-get install --reinstall xfce4-panel
```
There should also be a hidden panel configuration file in your home directory.  Have you done anything to that?

And a tip.
Edit your first post and tag it Xubuntu.  That will help get the right people to chime in (I run a different system).

---

