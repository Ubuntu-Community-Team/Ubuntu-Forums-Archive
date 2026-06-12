---
title: "Compiz-fusion won't start / failed to open device"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by AriciU on 2007-06-26
Beryl with emerald worked perfectly.

I've got compiz-fusion and emerald from [Trevino's repositories](http://3v1n0.tuxfamily.org/)

I've installed compiz-fusion with all the other stuff needed for it. Set beryl to use Metacity. Closed beryl-manager. Ran "compiz --replace" in the console and got this error:

> Adding core settings (General Options)
Adding plugin annotate (annotate)
Adding plugin blur (blur)
Adding plugin clone (clone)
Adding plugin cube (cube)
Adding plugin dbus (dbus)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin fs (fs)
Adding plugin glib (glib)
Adding plugin inotify (inotify)
Adding plugin minimize (minimize)
Adding plugin move (move)
Adding plugin place (place)
Adding plugin plane (plane)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin resize (resize)
Adding plugin rotate (rotate)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin video (video)
Adding plugin water (water)
Adding plugin wobbly (wobbly)
Adding plugin zoom (zoom)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin imgjpeg (imgjpeg)
Adding plugin neg (neg)
Adding plugin opacify (opacify)
Adding plugin put (put)
Adding plugin resizeinfo (resizeinfo)
Adding plugin ring (ring)
Adding plugin scaleaddon (scaleaddon)
Adding plugin snap (snap)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin vpswitch (vpswitch)
Adding plugin wall (wall)
Adding plugin winrules (winrules)
Adding plugin addhelper (addhelper)
Adding plugin bench (bench)
Adding plugin crashhandler (crashhandler)
Adding plugin cubereflex (cubereflex)
Adding plugin extrawm (extrawm)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin group (group)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin showdesktop (showdesktop)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin fakeargb (fakeargb)
Adding plugin snow (snow)
Adding plugin tile (tile)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Here is my xorg.conf also:

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    Option "AIGLX" "False"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "dbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "GeForce 6800 GT"
    Driver         "nvidia"
    Option "AllowGLXWithComposite" "True"
    Option "AddARGBGLXVisuals" "True"
    Option "DisableGLXRootClipping" "True"
    Option "RenderAccel" "True" 
    Option "DamageEvents" "True"
    Option "UseEvents" "False"
    Option "TripleBuffer" "True" 
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 6800 GT"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    
SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


---

### Post by AriciU on 2007-06-26
FIXED

> 

_**Troubleshooting**_
**Effects aren't visible**
if compiz --replace prints to terminal
```

/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity

```

Upgrade from Synaptic your libdecoration to version 0.5.

---

### Post by kustavo on 2007-07-29
**[SIZE="3"]undefined symbol: decor_apply_gravity[/SIZE]** 

[http://codigosecreto.blogspot.com/2007/07/soluo-erro-undefined.html](http://codigosecreto.blogspot.com/2007/07/soluo-erro-undefined.html)
[B]Translation:
Update libdecoration0 for version 1:0.5xxx[/B]

---

