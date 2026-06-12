---
title: "Compiz Fusion error on start"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by herbster on 2007-07-26
```
bobby:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugin bench (bench)
Adding plugin gotovp (gotovp)
Adding plugin wall (wall)
Adding plugin resize (resize)
Adding plugin splash (splash)
Adding plugin fade (fade)
Adding plugin text (text)
Adding plugin clone (clone)
Adding plugin zoom (zoom)
Adding plugin neg (neg)
Adding plugin kiosk (kiosk)
Adding plugin winrules (winrules)
Adding plugin regex (regex)
Adding plugin scaleaddon (scaleaddon)
Adding plugin workarounds (workarounds)
Adding plugin water (water)
Adding plugin group (group)
Adding plugin mousegestures (mousegestures)
Adding plugin vpswitch (vpswitch)
Adding plugin minimize (minimize)
Adding plugin firepaint (firepaint)
Adding plugin dbus (dbus)
Adding plugin flash (flash)
Adding plugin video (video)
Adding plugin atlantis (atlantis)
Adding plugin notification (notification)
Adding plugin reflex (reflex)
Adding plugin scale (scale)
Adding core settings (General Options)
Adding plugin plane (plane)
Adding plugin colorfilter (colorfilter)
Adding plugin switcher (switcher)
Adding plugin rotate (rotate)
Adding plugin annotate (annotate)
Adding plugin quickchange (quickchange)
Adding plugin glib (glib)
Adding plugin opacify (opacify)
Adding plugin place (place)
Adding plugin expo (expo)
Adding plugin screenshot (screenshot)
Adding plugin scalefilter (scalefilter)
Adding plugin addhelper (addhelper)
Adding plugin shift (shift)
Adding plugin keybinding (keybinding)
Adding plugin extrawm (extrawm)
Adding plugin inotify (inotify)
Adding plugin fs (fs)
Adding plugin snap (snap)
Adding plugin cubereflex (cubereflex)
Adding plugin crashhandler (crashhandler)
Adding plugin blur (blur)
Adding plugin trailfocus (trailfocus)
Adding plugin move (move)
Adding plugin cube (cube)
Adding plugin svg (svg)
Adding plugin widget (widget)
Adding plugin resizeinfo (resizeinfo)
Adding plugin showdesktop (showdesktop)
Adding plugin wallpaper (wallpaper)
Adding plugin wobbly (wobbly)
Adding plugin put (put)
Adding plugin thumbnail (thumbnail)
Adding plugin imgjpeg (imgjpeg)
Adding plugin decoration (decoration)
Adding plugin fadedesktop (fadedesktop)
Adding plugin screensaver (screensaver)
Adding plugin ring (ring)
Adding plugin mblur (mblur)
Adding plugin cheatsheet (cheatsheet)
Adding plugin png (png)
Adding plugin animation (animation)
Adding plugin 3d (3d)
Initializing core options...done
Initializing resize options...done
Initializing zoom options...done
Initializing minimize options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing place options...done
Initializing move options...done
/usr/bin/compiz: line 777:  3240 Segmentation fault      (core dumped) $*
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "murrine",
```

And Beryl is installed and has worked mint for the longest time. I installed it using Vorian's thread here: [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

Install went fine, can get into the compiz config settings no prob, etc. Just won't start, keeps reverting back to Metacity.

TIA for any help!

---

### Post by herbster on 2007-07-26
Nevermind, it works. Had to reboot!

---

