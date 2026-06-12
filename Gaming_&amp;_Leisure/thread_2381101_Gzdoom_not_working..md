---
title: "Gzdoom not working."
date: 2017-12-26
forum: Gaming &amp; Leisure
---

### Post by Hewjr100 on 2017-12-26
Need some help here. Had to install Gzdoom with a .deb package, because the PPA onlysupports Ubuntu 17.04 & 16.04, currently using 17.10.  When installed, launcher is created, but when I click on it nothing happens.  Nothing happens when I invoke from terminal, but I do get the following:

```
GZDoom g3.2.4 -2017-12-16 20:24:48 -0500 - SDL version
Compiled on Dec 172017


M_LoadDefaults: Loadsystem defaults.
Aborted (coredumped)
```

This is what Gzdoom.desktop looks like:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=GZDoom
Comment=AdvancedDoom source port.
Exec=gzdoom
Icon=/usr/share/pixmaps/gzdoom.png
Terminal=false
Categories=Game
```

Henry

---

### Post by Hewjr100 on 2017-12-28
Update I removedgzdoom and instead installed getdeb ppa.  Installed from there and gzdoomworks.  The only problem I am having is how to run .pk3 and .wadfiles that must me dragged and dropped on gzdoom.exe or whatever itis in Ubuntu.  In windows this worked, but in Ubuntu 17.04 draggingand dropping gzdoom on launcher does not work.  How do I remedy this?

Henry

---

