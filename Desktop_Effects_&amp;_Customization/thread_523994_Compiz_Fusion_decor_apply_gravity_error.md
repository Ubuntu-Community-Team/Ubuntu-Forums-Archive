---
title: "Compiz Fusion decor_apply_gravity error"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by guguma on 2007-08-12
When I run 

```
compiz --replace
``` or
```
compiz --replace -c emerald
``` or
```
compiz --replace --indirect-rendering -c emerald
```

I get this 

```
lord@brother:~$ Backend     : ini
Integration : true
Profile     : default
Adding plugin reflex (reflex)
Adding plugin glib (glib)
Adding plugin firepaint (firepaint)
Adding plugin scaleaddon (scaleaddon)
Adding plugin place (place)
Adding core settings (General Options)
Adding plugin gotovp (gotovp)
Adding plugin dbus (dbus)
Adding plugin wobbly (wobbly)
Adding plugin resizeinfo (resizeinfo)
Adding plugin neg (neg)
Adding plugin decoration (decoration)
Adding plugin move (move)
Adding plugin svg (svg)
Adding plugin video (video)
Adding plugin mblur (mblur)
Adding plugin blur (blur)
Adding plugin cube (cube)
Adding plugin scalefilter (scalefilter)
Adding plugin inotify (inotify)
Adding plugin vpswitch (vpswitch)
Adding plugin zoom (zoom)
Adding plugin crashhandler (crashhandler)
Adding plugin fs (fs)
Adding plugin screenshot (screenshot)
Adding plugin imgjpeg (imgjpeg)
Adding plugin addhelper (addhelper)
Adding plugin gears (gears)
Adding plugin group (group)
Adding plugin bench (bench)
Adding plugin showdesktop (showdesktop)
Adding plugin clone (clone)
Adding plugin wall (wall)
Adding plugin minimize (minimize)
Adding plugin ring (ring)
Adding plugin winrules (winrules)
Adding plugin rotate (rotate)
Adding plugin water (water)
Adding plugin cubereflex (cubereflex)
Adding plugin resize (resize)
Adding plugin snap (snap)
Adding plugin expo (expo)
Adding plugin regex (regex)
Adding plugin animation (animation)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin workarounds (workarounds)
Adding plugin fade (fade)
Adding plugin extrawm (extrawm)
Adding plugin plane (plane)
Adding plugin switcher (switcher)
Adding plugin scale (scale)
Adding plugin trailfocus (trailfocus)
Adding plugin put (put)
Adding plugin splash (splash)
Adding plugin fadedesktop (fadedesktop)
Adding plugin annotate (annotate)
Adding plugin ezoom (ezoom)
Adding plugin png (png)
Adding plugin opacify (opacify)
Initializing core options...done
Initializing place options...done
Initializing decoration options...done
Initializing move options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing zoom options...done
Initializing minimize options...done
Initializing resize options...done
Initializing workarounds options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing switcher options...done
Initializing scale options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity


```

The end line 

/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity

What is wrong with this. I cannot start compiz fusion. 

Please Help

---

### Post by guguma on 2007-08-12
This is solved with the new HOWTO posted. It turned out to be a problem with the repositories.

---

### Post by Mr Frosti on 2007-08-13
A link to the new HOWTO please?

edit: [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

---

### Post by guguma on 2007-08-14
The one I used is this one:

[http://ubuntuforums.org/showthread.p...z+fusion+howto](http://ubuntuforums.org/showthread.p...z+fusion+howto)


I also used this to remove all my wrong doings:
[http://news.softpedia.com/news/How-t...tu-58113.shtml](http://news.softpedia.com/news/How-t...tu-58113.shtml)

---

