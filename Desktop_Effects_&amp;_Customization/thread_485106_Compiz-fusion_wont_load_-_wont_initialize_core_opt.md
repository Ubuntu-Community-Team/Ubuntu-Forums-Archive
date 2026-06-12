---
title: "Compiz-fusion wont load - wont initialize core options due to &quot;toggle_shading&quot;"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by mortuk on 2007-06-26
Hey all

Followed the post [http://ubuntuforums.org/showthread.php?t=481314]("http://ubuntuforums.org/showthread.php?t=481314") and ran into a few problems when trying to run

I alt+F2 and run

```
compiz --replace
```

> chris@zubuntu:~$ compiz --replaceAdding plugin blur (blur)
Adding plugin scale (scale)
Adding plugin decoration (decoration)
Adding plugin screenshot (screenshot)
Adding core settings (General Options)
Adding plugin snow (snow)
Adding plugin glib (glib)
Adding plugin extrawm (extrawm)
Adding plugin regex (regex)
Adding plugin imgjpeg (imgjpeg)
Adding plugin trailfocus (trailfocus)
Adding plugin opacify (opacify)
Adding plugin winrules (winrules)
Adding plugin video (video)
Adding plugin put (put)
Adding plugin fade (fade)
Adding plugin resizeinfo (resizeinfo)
Adding plugin mblur (mblur)
Adding plugin minimize (minimize)
Adding plugin switcher (switcher)
Adding plugin addhelper (addhelper)
Adding plugin tile (tile)
Adding plugin place (place)
Adding plugin ring (ring)
Adding plugin wall (wall)
Adding plugin text (text)
Adding plugin zoom (zoom)
Adding plugin firepaint (firepaint)
Adding plugin rotate (rotate)
Adding plugin png (png)
Adding plugin reflex (reflex)
Adding plugin fs (fs)
Adding plugin resize (resize)
Adding plugin fadedesktop (fadedesktop)
Adding plugin annotate (annotate)
Adding plugin cubereflex (cubereflex)
Adding plugin water (water)
Adding plugin bench (bench)
Adding plugin showdesktop (showdesktop)
Adding plugin splash (splash)
Adding plugin group (group)
Adding plugin wobbly (wobbly)
Adding plugin snap (snap)
Adding plugin move (move)
Adding plugin thumbnail (thumbnail)
Adding plugin dbus (dbus)
Adding plugin vpswitch (vpswitch)
Adding plugin neg (neg)
Adding plugin cube (cube)
Adding plugin inotify (inotify)
Adding plugin animation (animation)
Adding plugin scaleaddon (scaleaddon)
Adding plugin crashhandler (crashhandler)
Adding plugin plane (plane)
Adding plugin clone (clone)
Adding plugin fakeargb (fakeargb)
Adding plugin expo (expo)
Adding plugin svg (svg)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
/usr/bin/compiz: line 671: 21492 Segmentation fault      (core dumped) $*
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

..and stops there until I ctrl+c out

any ideas?

---

### Post by AriciU on 2007-06-26
Go to System / Administration / Synaptic packet manager and search for "libdecoration". You will find 2 entries, libdecoration and libdecoration-dev. Mark them both and click apply. It will update to version 0.5 if you don't have it already.

---

### Post by quaid on 2007-06-29
same problem here and i do and installed everything and compiz still want to work

---

