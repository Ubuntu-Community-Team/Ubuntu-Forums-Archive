---
title: "KDE-Minimal"
date: 2009-10-30
forum: Desktop Environments
---

### Post by joey-elijah on 2009-10-30
I installed KDE-Minimal to see how KDE is doing in 4.3 and with Karmic. 

It installed fine, i logged in but there was no where to enter/configure an internet connection... so i ran nm-applet and used that. Fine.

I've seen a lot of KDE screenshots with gnome apps in but none look as horrific as mine do - does KDE-Minimal miss something out that helps GTK appearance in KDE?

Also when i click a .deb file it opens in archive manager. I'm assuming, again, that i'm missing the KDE equivalent of Gdebi? 

I intended to do a separate install of Kubuntu 910 alongside Ubuntu 9.10 but was advised to just install Kde-minimal instead... i do hope this isn't what KDE is actually like!

---

### Post by benerivo on 2009-10-30
I think karmic uses this package...

[http://packages.ubuntu.com/jaunty/gtk-qt-engine](http://packages.ubuntu.com/jaunty/gtk-qt-engine)

to allow kde4 users to make gtk applications look native to kde4. This is set via the kde system settings options. For the deb file installation it really should be done from a right click on the deb file, but if this doesn't do anything, then it can be done from the command line if you install gdebi-core. Then you can do```
sudo gdebi -i nameoffile.deb
```

---

