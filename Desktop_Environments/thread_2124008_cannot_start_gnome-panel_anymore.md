---
title: "cannot start gnome-panel anymore"
date: 2013-03-09
forum: Desktop Environments
---

### Post by petru.marginean on 2013-03-09
Hi,

Suddenly I cannot start the ''gnome-panel'' (when I login or manually)
I get this error when doing it manually:

```
$> gnome-panel
//...
gnome-panel: symbol lookup error: /usr/lib/gnome-panel/4.0/libwnck-applet.so: undefined symbol: wnck_tasklist_set_orientation
```
That libwnck-applet.so library misses a reference indeed:

```
$> ldd -r /usr/lib/gnome-panel/4.0/libwnck-applet.so >/dev/null
undefined symbol: wnck_tasklist_set_orientation    (/usr/lib/gnome-panel/4.0/libwnck-applet.so)
```
Tried rebooting, reinstalling ''gnome-panel'', and finally I completely remove the lib.
After that I was able to start ''gnome-panel'', but some of the widgets failed to load. 

The most I miss "Window List": 
```

The panel encountered a problem while loading "WnckletFactory::WindowListApplet".

```
Please help,
PM

---

### Post by tgalati4 on 2013-03-09
Sounds like a disk is going bad.  What is the SMART status of the drive?

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

---

### Post by petru.marginean on 2013-03-23
Solved by upgrading to 13.04.

Regards,
PM

---

