---
title: "White Unity menus"
date: 2012-07-13
forum: Desktop Environments
---

### Post by linuxsam777 on 2012-07-13
I am running ubuntu 12.04 with unity, gnome shell, kde and xfce. In unity some random menus show up as white radiance instead of dark ambiance. also I have noticed that libreoffice's menus do not show at the top of the screen, but in the traditional place. Please could you tell me how to fix it because it is anti productive.

---

### Post by lolpenguin on 2012-07-13
To fix the LibreOffice menubar:
```
sudo apt-get install lo-menubar
```
The white menu is cause by a problem with the theme. Try to fix this:
```
sudo apt-get install --reinstall light-themes gtk3-engines-unico
```

---

