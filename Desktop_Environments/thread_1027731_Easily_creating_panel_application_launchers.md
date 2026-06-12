---
title: "Easily creating panel application launchers"
date: 2009-01-01
forum: Desktop Environments
---

### Post by pestie on 2009-01-01
I've been a die-hard KDE fan for several years now, but after trying to come to terms with the disaster that is KDE 4.1, I'm switching my preferred desktop environment to Xubuntu, an environment I've been very happy with on my ancient laptop and now on my new (but still not very powerful) Lenovo S10 "netbook." But there's one thing I can't seem to figure out. I like to have a few of my most common applications as quick-launch items on the panel. I know how to add a "Launcher" to the panel and configure it by hand, but isn't there some easier way to get an item that's already in the applications menu to show on the panel?

---

### Post by hollywoodb on 2009-01-01
As far as I know the "by hand" method you are using is the only proper way to create launchers in the Xfce 4.4.x panel.

The Xfce menu is auto-generated from desktop files such as the ones in /usr/share/applications.  You can create new menu items by putting desktop files in ~/.local/share/applications.  The panel does not use these desktop files for its applets.  As it is I'm hoping this is addressed in Xfce 4.6.

---

