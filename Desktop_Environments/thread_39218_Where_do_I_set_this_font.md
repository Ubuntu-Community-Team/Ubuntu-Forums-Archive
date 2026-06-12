---
title: "Where do I set this font?"
date: 2005-06-03
forum: Desktop Environments
---

### Post by wikki on 2005-06-03
This is what the menus in a lot of applications look like I can't find where to set this font.  This particular application is xmms.

---

### Post by Alexander Kirillov on 2005-06-03
[QUOTE=wikki]This is what the menus in a lot of applications look like I can't find where to set this font.  This particular application is xmms.[/QUOTE]
 XMMS - and other simialr apps - use oder toolkit, gtk1 (as opposed to modern GNOME apps which use gtk2). For this reason, font settings in preferences->fonts do not affect these apps. 

The only way to fix this is by manually editing config file. See some discussion here
[http://ubuntuforums.org/showthread.php?t=3790&page=8](http://ubuntuforums.org/showthread.php?t=3790&page=8)
(scroll down to posts 74, 75) or here (for Mandrake, but should work for Ubuntu, too)
[http://www.linuxcompatible.org/thread27498-1.html](http://www.linuxcompatible.org/thread27498-1.html)

You can also do it for a single user rather than globally: [http://www.ubuntulinux.org/wiki/Gtk1Fonts](http://www.ubuntulinux.org/wiki/Gtk1Fonts)

---

### Post by wikki on 2005-06-03
Excellent.  I've got it now.

---

