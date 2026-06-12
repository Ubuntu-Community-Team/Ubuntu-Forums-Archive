---
title: "Totem loads GNOME over Windowmaker"
date: 2007-12-30
forum: Desktop Effects &amp; Customization
---

### Post by MrSylak on 2007-12-30
I did an install of Xubuntu, and customized it to use Windowmaker and installed the non-free video codecs and such, but i have an issue with totem where when i launch it in windowmaker, it seems to load a GNOME system and changed the desktop to the GNOME settings, as well as skin Thunar. Is there a way to isloate the cause and mabey prevent this from happening without switching from totem to another media player?

---

### Post by reacocard on 2007-12-30
what's happening is totem is causing gnome-settings-daemon to load up, which includes settings for gtk theme and the desktop background. I don't know of any way to stop it loading, but I hope this information helps you find a workaround.

---

