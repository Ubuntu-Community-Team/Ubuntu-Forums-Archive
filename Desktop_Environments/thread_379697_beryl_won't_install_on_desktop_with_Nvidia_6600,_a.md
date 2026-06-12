---
title: "beryl won't install on desktop with Nvidia 6600, and missing functions on laptop"
date: 2007-03-08
forum: Desktop Environments
---

### Post by xboxbman on 2007-03-08
This one's a double header. 
First question :  
 I've had beryl running on my laptop for some time now, and the missus, after a system upgrade, has requested i install it on the home computer.  My home cputer has an AMD 64 +3000 cpu and an nvidia 6600 graphics card, with a gig of RAM.  Certainly enough to run Beryl.  After following the HOWTO i found here :[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+beryl+edgy](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+beryl+edgy)

but it gives me this error when I try to run it:
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing

how do I get said texture support?

and question 2:  beryl is running on my laptop beautifully, except that when I minimize things, they don't appear on the taskbar at the bottom.  I'd like them to.  I like the cool thumbnail that appears as you place the mouse over it, and think it would be a handy feature.  Any ideas as to what's causing this?

---

### Post by xboxbman on 2007-03-09
bump

---

### Post by Nakkis on 2007-03-09
Post the output of this command please. 

```
cat /etc/X11/xorg.conf
```

---

### Post by xboxbman on 2007-03-09
> **Nakkis said:**
> Post the output of this command please. 

```
cat /etc/X11/xorg.conf
```

for the laptop

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection



Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"

EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x854" "1280x800" "1280x768" "1200x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x854" "1280x800" "1280x768" "1200x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x854" "1280x800" "1280x768" "1200x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x854" "1280x800" "1280x768" "1200x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x854" "1280x800" "1280x768" "1200x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x854" "1280x800" "1280x768" "1200x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


i'm at school now till later this afternoon, will post desktop's results then, thanks for helping

---

### Post by xboxbman on 2007-03-09
and from my desktop

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
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
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
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL 1703FP"
    HorizSync       28.0 - 49.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "DELL 1703FP"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

also, when i type "bery" in terminal it gives me this:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing

---

### Post by xboxbman on 2007-03-10
bump

---

### Post by ffxr on 2007-03-10
heres is the relevant parts of my xorg.conf.. maybe you could troubleshoot by using some or even all, of my settings.. i spent hours researching this and now have a bug free, & excellent beryl experience.. i use the prop nvidia drivers btw..

```

Section "Module"
    Load           "dbe"
    Load           "extmod"
	
	SubSection  "extmod"
      	Option    "omit xfree86-dga"   # don't initialise the DGA extension
    	EndSubSection

    Load           "freetype"
    Load           "glx"
    Load           "type1"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7100 GS"
    Option 	   "RenderAccel" "true"
    Option         "TripleBuffer" "true" ##only use this with lots of video ram
    Option         "AllowGLXWithComposite" "On"
    Option         "Coolbits"    "true"  ## enables you to use AA settings in nvidia-settings 
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "true"

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1680x1050" "1280x1024" "1024x768" "800x600"
        ViewPort    0 0
    EndSubsection
   EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

---

### Post by jimbo99 on 2007-03-11
na

---

### Post by xboxbman on 2007-03-11
> **jimbo99 said:**
> na

What?

---

