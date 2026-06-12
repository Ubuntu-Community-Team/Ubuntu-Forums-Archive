---
title: "Compiz Fusion CCSM doesn't work"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by Solvax on 2007-08-16
```
christoph@Solvaxonline38a1:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Backend     : gconf
Integration : true
Profile     : default
Adding plugin svg (Svg)
Adding plugin png (Png)
Adding plugin minimize (Minimize Effect)
Adding plugin inotify (Inotify)
Adding plugin snap (Snapping Windows)
Adding plugin scaleaddon (Scale Addons)
Adding plugin expo (Expo)
Adding plugin animation (Animations)
Adding plugin screenshot (Screenshot)
Adding plugin fadedesktop (Fade to Desktop)
Adding plugin splash (Splash)
Adding plugin addhelper (ADD Helper)
Adding plugin clone (Clone Output)
Adding core settings (General Options)
Adding plugin dbus (Dbus)
Adding plugin extrawm (Extra WM Actions)
Adding plugin fade (Fading Windows)
Adding plugin water (Water Effect)
Adding plugin place (Place Windows)
Adding plugin mblur (Motion blur)
Adding plugin cubereflex (Cube Reflection)
Adding plugin resize (Resize Window)
Adding plugin ring (Ring Switcher)
Adding plugin group (Group and Tab Windows)
Adding plugin rotate (Rotate Cube)
Adding plugin switcher (Application Switcher)
Adding plugin fs (Userspace File System)
Adding plugin wobbly (Wobbly Windows)
Adding plugin regex (Regex Matching)
Adding plugin blur (Blur Windows)
Adding plugin neg (Negative)
Adding plugin zoom (Zoom Desktop)
Adding plugin bench (Benchmark)
Adding plugin crashhandler (Crash handler)
Adding plugin firepaint (Paint fire on the screen)
Adding plugin cube (Desktop Cube)
Adding plugin annotate (Annotate)
Adding plugin trailfocus (Trailfocus)
Adding plugin move (Move Window)
Adding plugin video (Video Playback)
Adding plugin opacify (Opacify)
Adding plugin showdesktop (Show desktop)
Adding plugin decoration (Window Decoration)
Adding plugin vpswitch (Viewport mouse switch)
Adding plugin imgjpeg (JPEG)
Adding plugin scale (Scale)
Adding plugin reflex (Reflection)
Adding plugin thumbnail (Window Previews)
Adding plugin put (Put)
Adding plugin text (Text)
Adding plugin wall (Desktop Wall)
Adding plugin winrules (Window Rules)
Adding plugin plane (Desktop Plane)
Adding plugin glib (GLib)
Adding plugin resizeinfo (Resize Info)
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 84, in __init__
    self.ResetMainWidgets()
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 178, in ResetMainWidgets
    self.BuildTable(pluginsVPort)
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 230, in BuildTable
    pluginEnable.set_sensitive(self.Context.AutoSort)
AttributeError: 'compizconfig.Context' object has no attribute 'AutoSort'
christoph@Solvaxonline38a1:~$ 

```

This is the error i get...
The Compiz Fusion Settings Manager doesn't work.
What can i do about this?

Thanks in advance

~Solvax

---

### Post by Solvax on 2007-08-16
found the solution by now
you have to change some line in windows.py

---

