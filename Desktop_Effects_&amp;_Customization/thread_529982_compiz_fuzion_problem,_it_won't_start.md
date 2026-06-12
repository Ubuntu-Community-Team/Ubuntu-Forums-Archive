---
title: "compiz fuzion problem, it won't start"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by nwadams on 2007-08-19
this is the output for compiz --replace

```
compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)
Backend     : gconf
Integration : true
Profile     : default
Adding plugin fadedesktop (fadedesktop)
Adding plugin scale (scale)
Adding plugin rotate (rotate)
Adding plugin winrules (winrules)
Adding plugin clone (clone)
Adding plugin dbus (dbus)
Adding plugin opacify (opacify)
Adding plugin scaleaddon (scaleaddon)
Adding plugin plane (plane)
Adding plugin firepaint (firepaint)
Adding plugin switcher (switcher)
Adding plugin thumbnail (thumbnail)
Adding plugin decoration (decoration)
Adding plugin move (move)
Adding plugin screenshot (screenshot)
Adding plugin crashhandler (crashhandler)
Adding plugin svg (svg)
Adding plugin bench (bench)
Adding plugin regex (regex)
Adding plugin png (png)
Adding plugin wobbly (wobbly)
Adding plugin splash (splash)
Adding plugin expo (expo)
Adding plugin resizeinfo (resizeinfo)
Adding plugin neg (neg)
Adding core settings (General Options)
Adding plugin ring (ring)
Adding plugin place (place)
Adding plugin mblur (mblur)
Adding plugin zoom (zoom)
Adding plugin vpswitch (vpswitch)
Adding plugin addhelper (addhelper)
Adding plugin blur (blur)
Adding plugin put (put)
Adding plugin wall (wall)
Adding plugin text (text)
Adding plugin fs (fs)
Adding plugin annotate (annotate)
Adding plugin reflex (reflex)
Adding plugin minimize (minimize)
Adding plugin imgjpeg (imgjpeg)
Adding plugin snap (snap)
Adding plugin trailfocus (trailfocus)
Adding plugin inotify (inotify)
Adding plugin fade (fade)
Adding plugin water (water)
Adding plugin cube (cube)

Adding plugin group (group)
Adding plugin extrawm (extrawm)
Adding plugin glib (glib)
Adding plugin cubereflex (cubereflex)
Adding plugin video (video)
Adding plugin showdesktop (showdesktop)
Adding plugin resize (resize)
Adding plugin animation (animation)
Initializing core options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing move options...done
Initializing screenshot options...done
Initializing svg options...done

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7088): Wnck-WARNING **: Unhandled action type (nil)
Initializing wobbly options...done
Initializing neg options...done
Initializing ring options...done
Initializing place options...done
Initializing zoom options...done
Initializing annotate options...done
Initializing minimize options...done
Initializing snap options...done
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing resize options...done
Initializing animation options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
Segmentation fault (core dumped)
```

---

### Post by Ek0nomik on 2007-08-19
Hopefully a few of these will help:

[http://ubuntuforums.org/showthread.php?t=524491](http://ubuntuforums.org/showthread.php?t=524491)

[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

[http://forum.compiz-fusion.org/showthread.php?t=2074](http://forum.compiz-fusion.org/showthread.php?t=2074)

---

