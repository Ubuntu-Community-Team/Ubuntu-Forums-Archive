---
title: "Smaller buttons, and no images on them ?"
date: 2005-10-29
forum: Desktop Environments
---

### Post by jvictor on 2005-10-29
Does anyone know of themes with smaller buttons, and no images on them ? Or atleast how to remove the icons on the buttons .. ?

---

### Post by Qrk on 2005-10-29
System-->Preferences-->Menus and Toolbars

This changes Gnome, but not firefox or other applications. (evolution is changed)

---

### Post by jvictor on 2005-10-30
Well thats not what i want, I want the icons removed on the close buttons in dialogue windows

---

### Post by jvictor on 2005-10-30
Add this as the first line of your theme's gtkrc file ; buttons will b smaller & wont have icons on them :)

```
gtk-icon-sizes = "gtk-large-toolbar=24,24:panel-menu=20,20:gtk-menu=14,14:gtk-button=1,1"
```

Check out the file as the proof of concept :)

---

