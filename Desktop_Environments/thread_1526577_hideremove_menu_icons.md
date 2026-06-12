---
title: "hide/remove menu icons"
date: 2010-07-08
forum: Desktop Environments
---

### Post by Krajisnik on 2010-07-08
Hi,

I'm looking for a way to hide the icons in the Gnome menu bar.
Searching on the net didn't help me ...

The only thing i've found is the gconf-editor and unchecking /desktop/gnome/interface/menus_have_icons, but that only affects the System menu and not Applications and Places...

Example:
[IMG]http://i261.photobucket.com/albums/ii61/sbs-zarko/menu_applications.jpg[/IMG]
Must be like:
[IMG]http://i261.photobucket.com/albums/ii61/sbs-zarko/menu_system.jpg[/IMG]

Anyone knows how to disable them ?

I'm running Ubuntu 10.04LTS with Gnome 2.30

Thanks in advance.

---

### Post by Dr_Willis on 2010-07-08
Ages ago (like years ago?) there used to be a gnome setting/check box  to hide all the icons. I not seen that same setting  in recent gnome releases.  

I will look about some more,  It might be a gconf setting variable.

---

### Post by Krajisnik on 2010-07-08
> **Dr_Willis said:**
> Ages ago (like years ago?) there used to be a gnome setting/check box  to hide all the icons. I not seen that same setting  in recent gnome releases.  

I will look about some more,  It might be a gconf setting variable.
I think this used to be in the old version of Ubuntu/Gnome...
It was in menu System -> Preferences -> Appearance -> Tab Interface

This Tab isn't available anymore...

---

### Post by mcduck on 2010-07-08
> **Dr_Willis said:**
> Ages ago (like years ago?) there used to be a gnome setting/check box  to hide all the icons. I not seen that same setting  in recent gnome releases.  

I will look about some more,  It might be a gconf setting variable.
It was *exactly* the same setting as the gconf key already mentioned. (The appearance menu also had an option that changed the very same gconf key).

Sadly that option stopped working correctly when Gnome cleaned some of the unnecessary icons from the menus. So now we'll just have to hope that somebody fixes this setting in future Gnome releases...

edit: I think it *might* be possible to disable menu icons in the GTK theme, but I'm definitely not an expert in GTK theming so you'll have to wait for somebody else to confirmation & instructions.

---

### Post by hornedfiend on 2011-01-03
So...still nothing about this? I'd really like the icons removed too. They seems to clutter and slow down the menus (appearing later than the menus which causes small freezes)

---

### Post by joel.markshalayenka on 2011-04-25
I would like to chip in and agree with all the opinion above. The icons loading every time a menu opens makes the interface sluggish.

I've even been testing FVWM and other less flashy less noob-friendly GUIs. The simplicity of the menus makes them much faster to draw and contributes to an impression of using a fast computer.

UBUNTU... Please bring back the remove menu icons option!! :D

---

