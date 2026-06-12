---
title: "Select solid background color - limited colors available"
date: 2015-04-11
forum: Desktop Environments
---

### Post by awr on 2015-04-11
Trying to set a background color in Ubuntu Gnome 14.10 via All Settings\Background\Background\Colours.  I want to select black, but there are only 14 colours to choose from and black isn't one of them.  Does the default Gnome interface in Ubuntu lack any ability to pick your own wallpaper colour?

---

### Post by mcduck on 2015-04-11
Not just in Ubuntu. :D

Gnome devs have decided that selecting the colors should be left to advanced users and system admins only ;)

Anyway, it does (obviously) support any color you want, and in addition to that also horizontal and vertical color fades, placing image over the color background (either using image with alpha channel or by changing the image transparency through settings, various background scaling modes and even animated backgrounds (which are whole different beast to configure yourself...), but the actual options for everything have been left out of the user interface.

For full control over the stuff install *dconf-editor*, and then use that to browse to *org.gnome.desktop.background* and you'll find all the settings.

---

### Post by awr on 2015-04-11
Thanks mcduck,

I actually stumbled across dconf-editor and found the setting a few minutes ago and figured I should post an update here.  You beat me to it!  Strange that functionality isn't included in the gnome tweak tool or the background settings though.

---

