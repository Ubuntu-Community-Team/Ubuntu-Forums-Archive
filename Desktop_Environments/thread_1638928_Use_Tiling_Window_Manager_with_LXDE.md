---
title: "Use Tiling Window Manager with LXDE?"
date: 2010-12-06
forum: Desktop Environments
---

### Post by K_REY_C on 2010-12-06
I know that it is possible to run awesome window manager in gnome... but is it possible to do this in LXDE? Is there anyway to use any tiling window manager in LXDE (as is possible in gnome)? 

Thanks.

---

### Post by 3Miro on 2010-12-06
Window managers are mix and match. The default would be more stable, but you should be able to run any window manager with any DE. I have seen KDE + Metacity and have tried Gnome + OpenBox and XFCE + Compiz myself.

Find you the executable for the windows manager that you want and then try:

```
 windows_manager --replace 
```
For example:
```
metacity --replace
compiz --replace
kwin --replace
```

---

### Post by K_REY_C on 2010-12-06
Great! Thanks! Found where to change. Via GUI in lxde in "Desktop Session Settings" (here: [http://wiki.lxde.org/en/LXSession_Edit](http://wiki.lxde.org/en/LXSession_Edit) ) and go to the Advanced Options tab to change:
"openbox-lxde" to your desired window manager.

Thanks so much.

---

