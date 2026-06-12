---
title: "Compiz works fine.. but getting warnings in terminal......."
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by sent17inel on 2007-08-29
```
daniel@daniel-desktop:~$ compiz --replace
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)
Adding plugin dbus (dbus)
Adding plugin switcher (switcher)
Adding plugin resize (resize)
Adding plugin annotate (annotate)
Adding plugin rotate (rotate)
Adding plugin minimize (minimize)
Adding plugin cube (cube)
Adding plugin thumbnail (thumbnail)
Adding plugin imgjpeg (imgjpeg)
Adding plugin decoration (decoration)
Adding core settings (General Options)
Adding plugin screenshot (screenshot)
Adding plugin ring (ring)
Adding plugin wobbly (wobbly)
Adding plugin water (water)
Adding plugin scaleaddon (scaleaddon)
Adding plugin put (put)
Adding plugin png (png)
Adding plugin inotify (inotify)
Adding plugin opacify (opacify)
Adding plugin zoom (zoom)
Adding plugin fade (fade)
Adding plugin blur (blur)
Adding plugin video (video)
Adding plugin glib (glib)
Adding plugin fs (fs)
Adding plugin text (text)
Adding plugin scale (scale)
Adding plugin wall (wall)
Adding plugin svg (svg)
Adding plugin regex (regex)
Adding plugin resizeinfo (resizeinfo)
Adding plugin place (place)
Adding plugin expo (expo)
Adding plugin vpswitch (vpswitch)
Adding plugin plane (plane)
Adding plugin clone (clone)
Adding plugin animation (animation)
Adding plugin neg (neg)
Adding plugin winrules (winrules)
Adding plugin snap (snap)
Adding plugin move (move)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
Initializing resize options...done
Initializing annotate options...done
Initializing minimize options...done
Initializing imgjpeg options...done
Initializing decoration options...done
Initializing screenshot options...done
Initializing ring options...done
Initializing wobbly options...done
Initializing water options...done

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8121): Wnck-WARNING **: Unhandled action type (nil)
Initializing zoom options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing svg options...done
Initializing place options...done
Initializing vpswitch options...done
Initializing clone options...done
Initializing animation options...done
Initializing snap options...done
Initializing move options...done
Initializing fade options...done
Initializing cube options...done
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: 
Initializing scale options...done
Initializing switcher options...done
Initializing rotate options...done
Setting Update "opacity_values"
Setting Update "opacity_values"

```

any idea what this means? Everything seems to be working fine.... and by the way.... what is xgl? do i need it?

---

### Post by Inxsible on 2007-08-29
you need to use the alt + F2 and then type in compiz --replace, not in the terminal. I am not sure if that will get rid of the errors, just that it will hide them. mebbe I should try doing it in the terminal and see if i get the same errors.

---

### Post by Inxsible on 2007-08-29
Wow, 
when i type that in the terminal, my system becomes unresponsive. Only the terminal works, i cannot switch between windows and even on the terminal only the keyboard works. I can't use the mouse to drag or drop or anything.

I shall stick to typing the command in the Alt + F2 window dialog :D

---

### Post by sent17inel on 2007-08-30
I rarely type in compiz --replace..... i have it as a session... I just want to know how i can resolve those errrors..... not a way to hide them..............

---

### Post by coolen on 2007-09-08
You could always use emerald instead of the gtk window decorator (add "-c emerald", I think, or get fusion-icon and select it there).
As for XGL, if you don't need it, don't bother. XGL is basically a second X server laid over your normal one, which handles all of your windows. It's basically a GL-enabled window. It was created to support Compiz (and later Beryl), but then AIGLX was created, incorporating this functionality into Xorg, and AIGLX was in turn absorbed into Xorg.
AIGLX (or the newer Xorg) has superceeded XGL in most cases. ATI cards may still require XGL to run Compiz properly, but unless you need it, AIGLX is easier, and conceptually nicer.

---

