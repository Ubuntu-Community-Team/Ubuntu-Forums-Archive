---
title: "Compiz Fusion on an nVidia GeForce 6600GT PCIe"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by Patrick-Ruff on 2007-07-31
hey all . . . so after reading every page on the compiz fusion thread I still haven't come up with a solution here . . . 

I followed instructions here [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

and when I run the following command 

```
 compiz --replace -c emerald &

```

I get . . . 

```
patrick@shasta:~$ compiz --replace -c emerald &
[1] 9649
patrick@shasta:~$ Backend     : gconf
Integration : true
Profile     : default
Adding plugin move (move)
Adding plugin clone (clone)
Adding plugin wallpaper (wallpaper)
Adding plugin inotify (inotify)
Adding plugin glib (glib)
Adding plugin text (text)
Adding plugin trailfocus (trailfocus)
Adding plugin scale (scale)
Adding plugin atlantis (atlantis)
Adding plugin video (video)
Adding plugin widget (widget)
Adding plugin screenshot (screenshot)
Adding plugin showdesktop (showdesktop)
Adding plugin notification (notification)
Adding plugin extrawm (extrawm)
Adding plugin decoration (decoration)
Adding plugin minimize (minimize)
Adding plugin quickchange (quickchange)
Adding plugin place (place)
Adding plugin put (put)
Adding plugin scalefilter (scalefilter)
Adding plugin crashhandler (crashhandler)
Adding plugin thumbnail (thumbnail)
Adding plugin opacify (opacify)
Adding plugin wobbly (wobbly)
Adding plugin plane (plane)
Adding plugin addhelper (addhelper)
Adding plugin switcher (switcher)
Adding plugin shift (shift)
Adding plugin ring (ring)
Adding plugin workarounds (workarounds)
Adding plugin visualevent (visualevent)
Adding plugin png (png)
Adding plugin 3d (3d)
Adding plugin wall (wall)
Adding plugin cheatsheet (cheatsheet)
Adding plugin gotovp (gotovp)
Adding core settings (General Options)
Adding plugin rotate (rotate)
Adding plugin snap (snap)
Adding plugin scaleaddon (scaleaddon)
Adding plugin water (water)
Adding plugin neg (neg)
Adding plugin fadedesktop (fadedesktop)
Adding plugin fs (fs)
Adding plugin expo (expo)
Adding plugin splash (splash)
Adding plugin imgjpeg (imgjpeg)
Adding plugin vpswitch (vpswitch)
Adding plugin resize (resize)
Adding plugin animation (animation)
Adding plugin cubecaps (cubecaps)
Adding plugin regex (regex)
Adding plugin firepaint (firepaint)
Adding plugin reflex (reflex)
Adding plugin annotate (annotate)
Adding plugin svg (svg)
Adding plugin group (group)
Adding plugin resizeinfo (resizeinfo)
Adding plugin screensaver (screensaver)
Adding plugin keybinding (keybinding)
Adding plugin kiosk (kiosk)
Adding plugin mousegestures (mousegestures)
Adding plugin gears (gears)
Adding plugin colorfilter (colorfilter)
Adding plugin ezoom (ezoom)
Adding plugin zoom (zoom)
Adding plugin blur (blur)
Adding plugin cubereflex (cubereflex)
Adding plugin winrules (winrules)
Adding plugin flash (flash)
Adding plugin cube (cube)
Adding plugin fade (fade)
Adding plugin bench (bench)
Adding plugin dbus (dbus)
Adding plugin mblur (mblur)
Initializing core options...done
Initializing move options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing minimize options...done
Initializing place options...done
Initializing switcher options...done
Initializing workarounds options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
Initializing wall options...done
Initializing resize options...done
Initializing reflex options...done
Initializing zoom options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing fade options...done
Initializing scale options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```

and here's my xorg.conf

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:39:38 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option "AIGLX" "False"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E773c"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
	Option "AllowGLXWithComposite" "True"
	Option "DisableGLXRootClipping" "True"
Option "DamageEvents" "True"
Option "UseEvents" "False"
Option "TripleBuffer" "True"  
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1152x864_75 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

```


I have some effects but no window decorations . . . idea's please?

---

### Post by aeon on 2007-07-31
try adding this to your xorg.conf and restart x, could help..
```

Section "Screen"
    .....
    .....
    SubSection     "Display"
        Depth       32
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by Patrick-Ruff on 2007-07-31
tried it, didn't change anything. same error.

---

### Post by aeon on 2007-07-31
Beats me... Sorry..

Anyone else got any sugestions?

---

### Post by Patrick-Ruff on 2007-07-31
I love it when people stop trying to help me and I just uninstall ubuntu because of it . . .

---

### Post by userundefine on 2007-07-31
If someone stops helping you, it's probably because they have run out of ideas and would rather let someone else come in rather than lead you astray.

---

### Post by psyopper on 2007-07-31
In the device section add the following line:

```
    Option         "AddARGBGLXVisuals" "True"

```

How have you been a member of this forum for 18 months yet are trolling with your whiny newbie attitude?

---

### Post by Patrick-Ruff on 2007-07-31
that was more like a sarcastic 'this has happened over 50 times in the past' attitude.  but sure.  

I will try your method soon, thank you.

---

### Post by Patrick-Ruff on 2007-08-01
thanks for your help.  your line worked perfectly.

---

### Post by psyopper on 2007-08-01
> **Patrick-Ruff said:**
> thanks for your help.  your line worked perfectly.

You're welcome! Enjoy Compiz Fusion!!

---

