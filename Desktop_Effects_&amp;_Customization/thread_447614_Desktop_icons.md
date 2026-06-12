---
title: "Desktop icons"
date: 2007-05-18
forum: Desktop Effects &amp; Customization
---

### Post by sefs on 2007-05-18
Hi all.  I want to reduce the size of my desktop icons when they are placed on the desktop to about the size they are at in windows so they are neater and smaller.  Is there a setting somewhere that this can be automatically handled by gnome?

Thanks.

---

### Post by Kobalt on 2007-05-18
Press Alt+F2 then enter *gconf-editor*. From there go to : apps > nautilus > icon_view. Change the icon size value to what you'd like : 100% = normal, 75% = small, 50% = smaller, etc...

---

### Post by sefs on 2007-05-18
Feisty is a bit different.

Its seems to be now under default_zoom_level, there was no icon size value.  
but that other key was set to standard , and i changed it to small to get the desired effect.

Thanks.

> **Kobalt said:**
> Press Alt+F2 then enter *gconf-editor*. From there go to : apps > nautilus > icon_view. Change the icon size value to what you'd like : 100% = normal, 75% = small, 50% = smaller, etc...

---

### Post by Kobalt on 2007-05-18
Good to know.

---

