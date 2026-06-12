---
title: "Different Wallpaper on each Desktop"
date: 2011-01-16
forum: Desktop Environments
---

### Post by silameth on 2011-01-16
I have tried to follow instructions on an old post from 2008 but on my 11.04 there is no section for desktop images and it is system>preferences>CompizConfig Settings Manager not system>preferences>advanced desktop settings

Any help here would be appreciated.

---

### Post by Krytarik on 2011-01-16
You have to install the package "compiz-fusion-plugins-extra" and restart Compiz.
```
sudo apt-get install compiz-fusion-plugins-extra
compiz --replace

```
Note that if you run those plugin you apparently cannot have the usual shortcuts on the desktop.

[http://wiki.compiz.org/Plugins/Wallpaper](http://wiki.compiz.org/Plugins/Wallpaper)

Guide: [http://ubuntuguide.net/different-wallpapers-on-each-workspace-in-ubuntu](http://ubuntuguide.net/different-wallpapers-on-each-workspace-in-ubuntu)

---

