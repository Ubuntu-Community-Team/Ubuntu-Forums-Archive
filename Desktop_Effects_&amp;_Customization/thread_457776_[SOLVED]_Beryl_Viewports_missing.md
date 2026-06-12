---
title: "[SOLVED] Beryl Viewports missing"
date: 2007-05-29
forum: Desktop Effects &amp; Customization
---

### Post by psyopper on 2007-05-29
RESOLVED - SEE LAST POST

Hi all,

Got Beryl up and running but something seems to be missing... like my other three viewports... :(

Not a biggie, I really only use one viewport at a time, it's more like I want to figure out why it isn't working the way it should. Since a picture is worth a thousand words I'll show you two! The screenshot is 1280x1024 so to save some love for the dialup users I'll post it as a link, click at your leisure.

[Screenshot missing viewports.]("http://www.pbupload.com/data/500/Screenshot.png")
[Screenshot showing memory problems]("http://www.pbupload.com/data/500/Screenshot1.png")

The first is pretty self explanatory, the cobe only shows one viewport, the other three are "missing" The second screenshot shows what happens whey you try to do anything on those missing viewports. Yes, I can switch to them, they are just unusable. 

I have ensured that Beryl-General has Number of Desktops = 1, Horizontal Virtual Size = 4. Is there a way to rename some Beryl config file to make Beryl start from scratch?

Any ideas?

Since the question is invariable, here's my x11.conf:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
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
    Load           "dbe"
    Load           "ddc"
#   Load	   "dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "v4l"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option	   "YAxisMapping" "6 7"
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
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "PNY GForce 6200"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "PNY GForce 6200"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"

#added by me
    Option         "AllowDDCCI" "True"
    Option         "Coolbits" "1"
# end added by me    
    
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

```

---

### Post by mbradlcu on 2007-05-29
here's my xorg.conf vid-card section, it works for me:
> 
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GS"
    Option  "AddARGBGLXVisuals" "True"
    Option  "DisableGLXRootClipping"    "True"


O and looking at your post it seems one of us may have the Options listed in the wrong section..

---

### Post by psyopper on 2007-05-29
Nope.

It seems that mine are in the wrong place. But apparently not really because they are working fine. Symantically speaking they should be with the video device but I suppose that since the Screen points to the Device it applies those switches. Could be hand with multiple monitors on a single device...

Anywho, I put them where they belong and added your 'Option "DisableGLXRootClipping" "True"' switch and am still having the same problem. 

I don't really think it's an XOrg thing, it renders great. I think it's got something to do with the default number of Gnome viewports enabled but I'll be darned if I can find where that is. It's got to be somewhere in System-Preferences. Of course I'm asking the question so the likelyhood of having the answer goes down...

:)

---

### Post by mbradlcu on 2007-05-29
well the gnome window settings a-la num_workspaces can be found using the gconf-editor under, apps -> metacity -> general / num_workspaces but I don't think this has any effect because beryl overrides it.. but you may find something in there that will,, sorry I can't be more help here.

---

### Post by psyopper on 2007-05-29
Resolved!

[http://forum.beryl-project.org/viewtopic.php?f=36&t=6135]("http://forum.beryl-project.org/viewtopic.php?f=36&t=6135")

For those too lazy to click...

Beryl Settings Manager -> General -> Desktop Background tab -> Desktop Manager Supports Viewports

Uncheck this box and all is well!

---

