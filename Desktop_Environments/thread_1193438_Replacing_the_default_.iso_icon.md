---
title: "Replacing the default .iso icon"
date: 2009-06-21
forum: Desktop Environments
---

### Post by Bohemenian on 2009-06-21
I'm using the High Contrast Inverse icon set (HighContrastLargePrintInverse folder), but it bugs me that the set doesn't have a .iso icon. I've modified the icon set to inherit the Human icons instead of the default gnome ones. But I've come up clean searching the Human and icons folders for "iso" etc.

Does anyone know where I can find the default .iso icon, and where to put a replacement one in my HighContrastLargePrintInverse folder, and under what name?

---

### Post by benerivo on 2009-06-21
You can use```
locate dvd
```to find the default icon. I'm not sure which one it actually is, but /usr/share/icons/Human/scalable/devices/gnome-dev-cdrom.svg should be fine.

I would use this icon as default by right clicking on a .iso file and setting its icon that way, rather than moving a picture in to a folder, but you may have to put it in the folder for each size (eg. 32x32, scalable, etc.). I would guess, that just using the same file name (gnome-dev-cdrom.svg) might work, and that you should just copy and paste.

---

### Post by Bohemenian on 2009-06-23
Thx for the tip, but I found the icon, so I'm good with the way I planned to do it first.

The default icon for .iso files is in /usr/share/icons/gnome/scalable/mimetypes/application-x-cd-image.svg. 
Just put a file that can be used as an icon in the HighContrastLargePrintInverse/48x48/mimetypes folder under the name application-x-cd-image.xxx if you want to replace the default icon (and you're using the High Contrast Inverse icon theme, otherwise just put it in the corresponding folder for your icon theme. Yeah, you get it ^^).

---

