---
title: "Compiz in ubuntu ultimate 1.5 not working"
date: 2007-11-08
forum: Desktop Environments
---

### Post by D3PART3D on 2007-11-08
Hey guys :)

Why won't my compiz work?

I installed my nvidia drivers, and tried to run compiz. I typed compiz --replace, but nothing happens, I just get the following in the terminal:

[I]Adding plugin snap (snap)
Adding plugin thumbnail (thumbnail)
Adding plugin scaleaddon (scaleaddon)
Adding plugin group (group)
Adding plugin crashhandler (crashhandler)
Adding plugin place (place)
Adding plugin wall (wall)
Adding plugin fadedesktop (fadedesktop)
Adding plugin resize (resize)
Adding plugin switcher (switcher)
Adding plugin scale (scale)
Adding plugin winrules (winrules)
Adding plugin neg (neg)
Adding plugin water (water)
Adding plugin move (move)
Adding plugin ring (ring)
Adding plugin resizeinfo (resizeinfo)
Adding plugin glib (glib)
Adding plugin expo (expo)
Adding plugin cubereflex (cubereflex)
Adding plugin imgjpeg (imgjpeg)
Adding plugin vpswitch (vpswitch)
Adding plugin wobbly (wobbly)
Adding plugin annotate (annotate)
Adding plugin reflex (reflex)
Adding plugin screenshot (screenshot)
Adding plugin bench (bench)
Adding plugin splash (splash)
Adding plugin minimize (minimize)
Adding plugin decoration (decoration)
Adding plugin showdesktop (showdesktop)
Adding plugin fs (fs)
Adding plugin rotate (rotate)
Adding plugin opacify (opacify)
Adding plugin cube (cube)
Adding plugin svg (svg)
Adding plugin regex (regex)
Adding plugin mblur (mblur)
Adding plugin blur (blur)
Adding plugin put (put)
Adding plugin zoom (zoom)
Adding plugin fade (fade)
Adding plugin clone (clone)
Adding plugin text (text)
Adding plugin trailfocus (trailfocus)
Adding plugin firepaint (firepaint)
Adding plugin dbus (dbus)
Adding plugin plane (plane)
Adding plugin inotify (inotify)
Adding plugin addhelper (addhelper)
Adding core settings (General Options)
Adding plugin animation (animation)
Adding plugin video (video)
Adding plugin png (png)
Adding plugin extrawm (extrawm)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
Initializing place options...done
Initializing resize options...done
Initializing move options...done
Initializing vpswitch options...done
Initializing minimize options...done
/usr/bin/compiz: line 686:  6235 Segmentation fault      (core dumped) $*


[/I]

:(

Thanks.

---

### Post by overdrank on 2007-11-09
Hi and welcome, what is the model of graphics card? Have you verified that you are using the correct driver in the xorg? Use this command ```
cat /etc/X11/xorg.conf
``` in the terminal located under applications, accessories,terminal. Make sure you are using the nvidia driver instead of the nv. It will be under device, driver. Good luck!

---

