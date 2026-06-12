---
title: "Emerald doesn't start with Compiz Fusion"
date: 2007-07-15
forum: Desktop Effects &amp; Customization
---

### Post by StevenX on 2007-07-15
I've updated to Compiz Fusion, from Beryl but am having trouble getting the Emerald Window decoration to work at startup.

I I just type "emerald --replace," into a terminal or Alt+F2 window then my Emerald theme appears fine. However if I put the "-c emerald &," bit (not sure if that's exactly right - but you know what bit I mean) in the end of my "compiz --replace," start-up command I'm stuck with my Metacity theme. Even if I put "emerald --replace," as its own startup command it won't load (even though the command would work on its own from ALT+F2. Also, using Beryl Manager and selecting Emerald as the Window decorator, I have to select "Reload Window Decorator," before it will work.

Does anyone have any idea how to just make it work? Nothing I've dug up so far has been much help..

---

### Post by PurposeOfReason on 2007-07-15
Have you tried?

```

compiz --replace -c emerald &

```

Or bring up the beryl manager and make sure that compiz is still selected as your window manager.

---

### Post by StevenX on 2007-07-15
> **PurposeOfReason said:**
> Have you tried?

```

compiz --replace -c emerald &

```

Or bring up the beryl manager and make sure that compiz is still selected as your window manager.

That command doesn't work. The "&," makes the difference. If there's an "&," symbol in the command, Compiz won't start...

---

### Post by PurposeOfReason on 2007-07-15
Still put that in your sessions and restart X. I've always done it that way with no problems.

---

### Post by hyperair on 2007-07-16
Go to CompizConfig Settings Manager, and in the Window Decoration plugin, under "Command", put "emerald --replace" That worked for me. Removed the need to put "-c emerald"

---

### Post by StevenX on 2007-07-16
> **hyperair said:**
> Go to CompizConfig Settings Manager, and in the Window Decoration plugin, under "Command", put "emerald --replace" That worked for me. Removed the need to put "-c emerald"

Tried that - no luck :(

---

### Post by hyperair on 2007-07-16
Okay... so that's weird. You're using debs from Vorian's repo or Trevino's?

---

### Post by walkerk on 2007-07-16
so you say that without the '&' it works fine?

i load compiz fusion and emerald w/out the &
```
compiz --replace -c emerald
```

otherwise try
```
compiz --replace
emerald --replace
```

also, i see you still have beryl (whether its only the manager or not) and i had similar problems. my fix was to completely remove everything compiz and beyl related (not emerald) and re-installing compiz fusion.

---

### Post by StevenX on 2007-07-17
> **walkerk said:**
> so you say that without the '&' it works fine?

i load compiz fusion and emerald w/out the &
```
compiz --replace -c emerald
```

otherwise try
```
compiz --replace
emerald --replace
```

also, i see you still have beryl (whether its only the manager or not) and i had similar problems. my fix was to completely remove everything compiz and beyl related (not emerald) and re-installing compiz fusion.

Neither of those works.
I've not tried complete uninstallation yet - that could be next on the list...

Also, I was using Trevino's reps, but am now using Vorian's I think.

---

### Post by hyperair on 2007-07-17
What happens when you try out those commands? Does the screen blink or anything? Perhaps a hang for a few seconds?

---

### Post by StevenX on 2007-07-19
> **hyperair said:**
> What happens when you try out those commands? Does the screen blink or anything? Perhaps a hang for a few seconds?

When I do "compiz --replace," it doesn't hang or anything.. The following output is produced..

```
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)
Adding plugin rotate (rotate)
Adding plugin scaleaddon (scaleaddon)
Adding plugin fade (fade)
Adding plugin firepaint (firepaint)
Adding plugin group (group)
Adding plugin inotify (inotify)
Adding plugin glib (glib)
Adding plugin resize (resize)
Adding plugin imgjpeg (imgjpeg)
Adding plugin thumbnail (thumbnail)
Adding plugin trailfocus (trailfocus)
Adding plugin place (place)
Adding plugin decoration (decoration)
Adding plugin dbus (dbus)
Adding plugin addhelper (addhelper)
Adding plugin annotate (annotate)
Adding plugin cubereflex (cubereflex)
Adding plugin ring (ring)
Adding plugin bench (bench)
Adding plugin vpswitch (vpswitch)
Adding plugin regex (regex)
Adding plugin snap (snap)
Adding plugin resizeinfo (resizeinfo)
Adding plugin plane (plane)
Adding plugin switcher (switcher)
Adding plugin crashhandler (crashhandler)
Adding plugin extrawm (extrawm)
Adding plugin cube (cube)
Adding plugin splash (splash)
Adding plugin screenshot (screenshot)
Adding plugin showdesktop (showdesktop)
Adding plugin clone (clone)
Adding plugin zoom (zoom)
Adding plugin text (text)
Adding plugin png (png)
Adding plugin wall (wall)
Adding plugin video (video)
Adding plugin mblur (mblur)
Adding plugin svg (svg)
Adding plugin wobbly (wobbly)
Adding plugin opacify (opacify)
Adding plugin expo (expo)
Adding plugin minimize (minimize)
Adding core settings (General Options)
Adding plugin reflex (reflex)
Adding plugin blur (blur)
Adding plugin neg (neg)
Adding plugin move (move)
Adding plugin fs (fs)
Adding plugin fadedesktop (fadedesktop)
Adding plugin animation (animation)
Adding plugin water (water)
Adding plugin put (put)
Adding plugin winrules (winrules)
Adding plugin scale (scale)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing resize options...done
Initializing imgjpeg options...done
Initializing place options...done

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)
Initializing decoration options...done
Initializing ring options...done
Initializing snap options...done
Initializing resizeinfo options...done
Initializing zoom options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing svg options...done
Initializing wobbly options...done
Initializing reflex options...done
Initializing move options...done
Initializing fadedesktop options...done
Initializing animation options...done
Initializing fade options...done
Initializing cube options...done
Initializing expo options...done
Initializing scale options...done
Initializing rotate options...done
Initializing cubereflex options...done


(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6393): Wnck-WARNING **: Unhandled action type (nil)



```

When I do "emerald --replace," my Emerald theme does come up, but I get the following:

```
(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6505): Wnck-WARNING **: Unhandled action type (nil)

```

---

### Post by hyperair on 2007-07-20
Don't bother about the wnck warning, seriously. I get that too and mine works fine. So what's wrong then?

---

