---
title: "[SOLVED] where are the background images in gnome stored??"
date: 2007-09-28
forum: Desktop Environments
---

### Post by rbprogrammer on 2007-09-28
i have a nice red background that was a default option in gnome (see attachment)... now i want to know where that image is saved so that i can use it on my other computer

---

### Post by rbprogrammer on 2007-09-28
whoops, here is the attachment

---

### Post by Wolki on 2007-09-28
> **rbprogrammer said:**
> whoops, here is the attachment

That's ubuntu smooth chocolate, one of the Ubuntu Feisty default wallpapers. Find it at /usr/share/backgrounds/ubuntu-smooth-chocolate.png
New GNOME appearance tool (in 2.20/gutsy) shows the location on the tooltip, I'm not exactly sure how it was before. You should find the filename of the currently used desktop background in gconf-editor under "/desktop/gnome/background/picture_filename". The file containing the wallpaper list is ~/.gnome2/backgrounds.xml

---

### Post by mcduck on 2007-09-28
All the default wallpapers are in /usr/share/backgrounds, but you can of course keep your own images where ever you want.

---

