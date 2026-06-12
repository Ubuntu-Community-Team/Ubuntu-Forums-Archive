---
title: "1024 x 768 x 100 Hz video mode with NVidia videocard"
date: 2006-07-01
forum: Desktop Environments
---

### Post by JohnRus on 2006-07-01
When i was use generic "nv" driver (was automaticaly setuped when Ubuntu installed), i was made some changes in xorg.org and i have 1024*768*100 video mode working correctly. 

But when i install nvidia-glx, only 1024*768*85 working - eyes damaged(((


This is my xorg.conf. Whats false?

```

# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    #Screen         "Default Screen" 0 0
    Screen         "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us,ru"
    Option         "XkbOptions" "grp:alt_shift_toggle"
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

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
    Modeline "1024x768_100.00"	113.31 1024 1096 1208 1392 768 769 772 814 -HSync +Vsync
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    #Driver         "nvidia"            # only 1024 768 85Hz working(((
    Driver         "nv"                    # 1024 768 100Hz working fine
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "SyncMaster"
    DefaultDepth    24	
    SubSection "Display"
	Depth		24
	Modes		"1024x768"
    EndSubSection
EndSection


```

Big thanks for Your support!)

---

### Post by tseliot on 2006-07-01
Add the part I put in red:

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "SyncMaster"
    DefaultDepth    24	
    SubSection "Display"
	Depth		24
	Modes		"1024x768[COLOR="Red"]_100[/COLOR]"
    EndSubSection
EndSection

```

Then log out, press CTRL+ALT+Backspace and log in

---

### Post by JohnRus on 2006-07-01
Thank You, 

helped.

---

