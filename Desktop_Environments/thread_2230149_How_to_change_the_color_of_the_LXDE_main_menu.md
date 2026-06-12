---
title: "How to change the color of the LXDE main menu?"
date: 2014-06-17
forum: Desktop Environments
---

### Post by Pablo_San_Martn on 2014-06-17
I have installed a dark theme and was wondering how the main menu background and letter colors can be changed, and also those of the menu which appears when you left click an item. I have been looking in other threads and in the Lubuntu official documentation but cannot find a way to do it. Also, is there any dark monocrome icon set that could be used for this?

---

### Post by bapoumba on 2014-06-17
icons are in usr/share/icons

I recall having a look a while ago for someone and did not find the main menu icon there. I think I found it in the Quantal set, but I cannot retreive my post again. You'd need to download the files and have a look for yourself, then maybe adjust the colors to your liking.
[http://lubuntublog.blogspot.fr/p/artwork.html](http://lubuntublog.blogspot.fr/p/artwork.html)

---

### Post by Pablo_San_Martn on 2014-06-18
Thanks bapouma.

What about customising th colors of the main menu, as the background and entries?

I also found out there seems to be a bug in 14.04 which doesn't allow color customisation yet: [https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316384](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316384)

---

### Post by bapoumba on 2014-06-18
Looks like the package is in Trusty already, in universe [http://packages.ubuntu.com/trusty/lxsession](http://packages.ubuntu.com/trusty/lxsession)

---

### Post by Pablo_San_Martn on 2014-06-19
True!

Just delete the entry **iGtk/ColorScheme=** from **~/.config/lxsession/Lubuntu/desktop.conf**, and then your settings will be saved :D

---

