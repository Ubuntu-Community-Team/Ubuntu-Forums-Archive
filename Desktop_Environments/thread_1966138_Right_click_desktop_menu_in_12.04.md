---
title: "Right click desktop menu in 12.04"
date: 2012-04-26
forum: Desktop Environments
---

### Post by footspa on 2012-04-26
Is the right click desktop menu still using openbox in Lubuntu 12.04? 

In previous versions of Lubuntu this menu could be edited with OBmenu or directly editing the /.config/openbox/menu.xml file.

How do I edit this menu in 12.04? Thanks.

---

### Post by footspa on 2012-04-26
It appears the menu.xml file that needs to be modified in now found at /usr/share/lubuntu/openbox

---

### Post by ankspo71 on 2012-04-27
In Lubuntu 12.04 the right click menu is using LXDE's own right click menu, but it can easily be switched to openbox's menu.

To enable the openbox menu, right click on the desktop, then choose Desktop Preferences, click on Advance tab, then enable "Show menus provided by window managers when desktop is clicked"

To disable the openbox menu again, right click on the desktop, then choose System, then choose Desktop Settings, click on Advance tab, then disable "Show menus provided by window managers when desktop is clicked"

OBmenu should still work fine editing the openbox right click menu. I haven't tried it myself though.

---

### Post by footspa on 2012-06-22
> **ankspo71 said:**
> To enable the openbox menu, right click on the desktop, then choose Desktop Preferences, click on Advance tab, then enable "Show menus provided by window managers when desktop is clicked"

To disable the openbox menu again, right click on the desktop, then choose System, then choose Desktop Settings, click on Advance tab, then disable "Show menus provided by window managers when desktop is clicked"

OBmenu should still work fine editing the openbox right click menu. I haven't tried it myself though.

The above doesn't work. It simply disables any kind of right click menu.

Does anyone know how to restore the OB right click menu? The LXDE right click menu is horrible.

---

