---
title: "gtk+ appearance"
date: 2010-05-17
forum: Desktop Environments
---

### Post by u_kapaley256 on 2010-05-17
Hi,
    I want to apply the qtcurve appearance to gparted in kubuntu karmic
    I have done that to firefox but that was in a custom location which i was able to add to the 'custom search path' for the gtk+    engine.But for the gparted i just know about the path of the executable which is in /usr/sbin.What path should i add to get the desired effect ?
Udayan

---

### Post by Zorael on 2010-05-17
Assuming you have **kcm-gtk** installed you should be able to theme GTK apps by selecting the appropriate setting in System Settings -> Appearance. The problem with gparted is that it's run as root, and as such your user's settings don't apply.

One solution is to simply start System Settings as root and clone your user's settings. Pop up a run box with Alt+F2 and run '**kdesudo systemsettings**'.

Another solution is to make symbolic links in root's home directory to make it use the same settings files as your user does.
```
$ sudo ln -s ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0
$ sudo rm /root/.kde/share/config/kdeglobals
$ sudo ln -s ~/.kde/share/config/kdeglobals /root/.kde/share/config/kdeglobals
$ sudo ln -s ~/.gtk-bookmarks /root/.gtk-bookmarks   # optional
```
Since the files already exist, root should never change ownership of the files to itself. If you start removing **~/.kde** for some reason and when it's recreated settings won't stick, you can recursively change all files under your home directory to yourself to solve that.
```
$ **cd ~**         # IMPORTANT
$ sudo chown $(id -u):$(id -g) $(find -u 0)
```

---

