---
title: "using gnome setting without gnome"
date: 2009-02-19
forum: Desktop Environments
---

### Post by mathfeel on 2009-02-19
Is it possible to load the gtkrc and icons setting for gtk-2 apps without running gnome-setting-daemon?

I would like to be able to use alternative wm without most of my apps looking ugly.

---

### Post by m_duck on 2009-02-19
You can edit your ~/.gtkrc-2.0 file directly (google for how because I can't remember) or using a graphical theme manager. I find it easiest using lxappearance which is in the repos for Intrepid:```
sudo apt-get install lxappearance
```You can choose a GTK theme, icons, font sizes with this.

Alternatively there is GTK theme switch (launch with "switch2") or gtk ch theme```
sudo apt-get install gtk-theme-switch
sudo apt-get install gtk-chtheme
```

---

