---
title: "gnome theme standard ?"
date: 2011-05-02
forum: Desktop Environments
---

### Post by sameerkof on 2011-05-02
while installing gnome theme standard getting this error what to do ? 

E: /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build2_i386.deb: trying to overwrite '/usr/share/themes/HighContrast/index.theme', which is also in package gnome-accessibility-themes-extras 3.0.0-0ubuntu1~build2

---

### Post by Krytarik on 2011-05-02
> **sameerkof said:**
> 
E: /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build2_i386.deb: trying to overwrite '/usr/share/themes/HighContrast/index.theme', which is also in package **gnome-accessibility-themes-extras** 3.0.0-0ubuntu1~build2
The solution is obvious, purge the mentioned package:
```
sudo apt-get purge gnome-accessibility-themes-extras
```Also see here for more tips on Gnome 3:
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)

Greetings.

---

