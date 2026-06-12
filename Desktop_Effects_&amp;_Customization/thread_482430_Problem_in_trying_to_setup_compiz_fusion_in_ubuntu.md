---
title: "Problem in trying to setup compiz fusion in ubuntu 7.0.4"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by yinglcs2 on 2007-06-23
Hi,

I am trying to following this posing on how to install on ubuntu:
'http://ubuntuforums.org/showthread.php?t=481615&page=2' 

but at the end when I run 'compiz --replace' in a terminal, I get this error message:
Can some one please tell me how can I fix my problem?
```

Adding plugin addhelper (addhelper)
Adding core settings (General Options)
Adding plugin extrawm (extrawm)
Adding plugin mblur (mblur)
Adding plugin snow (snow)
Adding plugin glib (glib)
Adding plugin fs (fs)
Adding plugin dbus (dbus)
Adding plugin neg (neg)
Adding plugin wobbly (wobbly)
Adding plugin vpswitch (vpswitch)
Adding plugin reflex (reflex)
Adding plugin opacify (opacify)
Adding plugin imgjpeg (imgjpeg)
Adding plugin fade (fade)
Adding plugin svg (svg)
Adding plugin expo (expo)
Adding plugin text (text)
Adding plugin trailfocus (trailfocus)
Adding plugin resizeinfo (resizeinfo)
Adding plugin fakeargb (fakeargb)
Adding plugin ring (ring)
Adding plugin crashhandler (crashhandler)
Adding plugin zoom (zoom)
Adding plugin switcher (switcher)
Adding plugin cube (cube)
Adding plugin bench (bench)
Adding plugin put (put)
Adding plugin video (video)
Adding plugin splash (splash)
Adding plugin cubereflex (cubereflex)
Adding plugin fadedesktop (fadedesktop)
Adding plugin wall (wall)
Adding plugin place (place)
Adding plugin minimize (minimize)
Adding plugin group (group)
Adding plugin blur (blur)
Adding plugin snap (snap)
Adding plugin firepaint (firepaint)
Adding plugin scaleaddon (scaleaddon)
Adding plugin scale (scale)
Adding plugin plane (plane)
Adding plugin winrules (winrules)
Adding plugin screenshot (screenshot)
Adding plugin clone (clone)
Adding plugin decoration (decoration)
Adding plugin regex (regex)
Adding plugin resize (resize)
Adding plugin png (png)
Adding plugin animation (animation)
Adding plugin tile (tile)
Adding plugin inotify (inotify)
Adding plugin annotate (annotate)
Adding plugin thumbnail (thumbnail)
Adding plugin move (move)
Adding plugin rotate (rotate)
Adding plugin water (water)
Adding plugin showdesktop (showdesktop)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing zoom options...done
Initializing place options...done
Initializing minimize options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity

```

---

### Post by yinglcs2 on 2007-06-23
I think I resolve my problem by upgrading my libdecorator

But how can I make it to use 'compiz everytime I log in'?
I don't want to do 'Alt F2 and type 'compiz --replace'?

Thank you.

---

### Post by llamakc on 2007-06-23
You can add it in System | Preferences | Sessions in Gnome (if you're using Gnome).

---

### Post by yinglcs2 on 2007-06-23
Thanks, it works!

I have another question in compiz fusion. What is the short cut key/mouse event for switching desktop top?

In beryl, I can switch desktop by just using the mouse wheel , how can I do the same in compiz fusion?

Thank you.

---

### Post by llamakc on 2007-06-23
It's a plugin. Run "ccsm" from the terminal or ALT-F2, or from your menu System |  Preferences | CompizConfig Settings Manager

Enable Viewport Mouse Switch.

I had to logout/login for it to start working.

---

### Post by yinglcs2 on 2007-06-23
Thanks again, it works again.

* I use to able to rotate my desktop cube by pressing both left-right mouse button in beryl. How can I do that in compiz fusion?

* and when I unfold the desktop cube, how can I show reflection? and how can I configure it just show 4 desktops ? right now, it shows desktops infinitely.

Thank you.

---

### Post by llamakc on 2007-06-23
I dunno. Reflection isn't working for me either yet. I'm gonna change the color of my skydome and see if that allows the reflection to show up.

---

### Post by yinglcs2 on 2007-06-23
I appreciate your help. Another question, 

how can I group certain windows together? and how can I flip the group windows like some demo that I saw?

Thank you.

---

### Post by llamakc on 2007-06-23
Use the plugins that allow that sort of functionality. In the DEMO video, they preface each plugin's performance with its name on the screen. Watch the demo, and enable said plugin.

---

### Post by llamakc on 2007-06-23
BTW, reflection is a plugin and just needs to be enabled. Works fine.

---

