---
title: "Cedega OpenGL Direct Rendering Test Failed"
date: 2007-06-13
forum: Gaming &amp; Leisure
---

### Post by ExodusC on 2007-06-13
Hi, I'm very new to Linux, and these forums.  I tried a few distros and decided to stick with Ubuntu.  I've had a friend help me get things going, and I've not had any problems- up until now.  I installed Cedega, and I failed running the OpenGL Direct Rendering test.  I ran some searches, and only turned up a few answers.  I believe it's because I'm running Compiz, which came installed on my distro (Ubuntu Fiesty Fawn 7.04 i386) by default, and it seems to be locking OpenGL direct rendering from other applications-- or at least thats what I interpreted from some other posts.  (I'm running an NVIDIA GeForce 7800GTX if there have been any known issues with the 7000 series.)

Here's my xorg.conf file, in case something is wrong there, which I also saw might be a problem:

```
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
    Load           "ddc"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
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
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 7800GTX"
    Driver         "nv"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 7800GTX"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Hopefully someone can help me figure this out, I appreciate any support I can get.

---

### Post by slimdog360 on 2007-06-13
turn off compiz and see if it works. system-->preferences-->desktop effects.

edit: scrap that, I didn't look at your xorg.conf file. You dont have the nvidia drivers installed, system-->administration-->restricted drivers.

---

### Post by ExodusC on 2007-06-13
> **slimdog360 said:**
> turn off compiz and see if it works. system-->preferences-->desktop effects.

edit: scrap that, I didn't look at your xorg.conf file. You dont have the nvidia drivers installed, system-->administration-->restricted drivers.

Thanks! That second solution worked.  Going to see how well Cedega performs now.

---

