---
title: "Not able to move window control to the right in Ubuntu 14.10"
date: 2014-11-24
forum: Desktop Environments
---

### Post by cdysthe on 2014-11-24
Hi,

I am not able to move window control to the right using Tweak Tool in Ubuntu 14.10. I check the check-box but nothing happens and when I open Tweak Tool again the window controls are still set to left. This worked in 14.04 and below. How can I fix this?

---

### Post by buzzingrobot on 2014-11-24
That function in Tweak Tool does not work in 14.10.  I'm not aware of any other way to move the controls.

---

### Post by cdysthe on 2014-11-24
> **buzzingrobot said:**
> That function in Tweak Tool does not work in 14.10.  I'm not aware of any other way to move the controls.

Thanks. That sucks. I guess I'm heading back to 12.04. I just can't stand having the controls on the left.

---

### Post by kansasnoob on 2014-11-24
Are you using the Unity desktop environment or something else?

---

### Post by cdysthe on 2014-11-24
> **kansasnoob said:**
> Are you using the Unity desktop environment or something else?

Using a stock Ubuntu 14.10 install with Unity.

---

### Post by CantankRus on 2014-11-25
This changed in 14.04  
**gtk-window-decorator** is no longer used and the unity compiz plugin
now draws the decorations to allow the implementation of menus in the titlebar.
You have to disable the entire unity plugin to use the old Window Decoration plugin
Only option is to not use unity (the fallback sessions use the **gtk-window-decorator**), or get used to lefthand side.

When using the **gtk-window-decorator** you can still put buttons on the right...
```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

---

