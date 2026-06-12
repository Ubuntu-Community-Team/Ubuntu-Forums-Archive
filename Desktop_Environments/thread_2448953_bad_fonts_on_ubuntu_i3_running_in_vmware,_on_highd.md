---
title: "bad fonts on ubuntu i3 running in vmware, on highdpi monitor"
date: 2020-08-17
forum: Desktop Environments
---

### Post by toerktumlare on 2020-08-17
Installed latest ubuntu and i3 in a vm on my macbook with retina screen.

set my resolution to ```
xrandr --output Virtual1 --mode 2560x1600
```

Fonts looked really bad so read in the i3 manual and set the dpi, and also read on archlinux wiki [https://wiki.archlinux.org/index.php/HiDPI#X_Resources](https://wiki.archlinux.org/index.php/HiDPI#X_Resources) that some settings where required for fonts to look better. 

```

Xft.dpi: 192

Xft.autohint: 0
Xft.antialias: 1
Xft.hinting: 1
Xft.hintstyle: hintslight
Xft.rgba: rgb
Xft.lcdfilter: lcddefault

```

But fonts still look blurry and not as crisp if using just gnome-desktop

---

