---
title: "Quick dual monitor question"
date: 2007-05-11
forum: Desktop Environments
---

### Post by Hobo Joe on 2007-05-11
Ok, so I recently upgraded my computer, and this time, knowing the weakness of ATi + Linux, I got an nVidia.
First off, I would like to say, kudos the the creators of Envy and the nVidia control panel(probably made by nVidia, but I have no idea), it was the easiest thing in the world to set up, including the dual monitors, but there is one thing.
It's not a 'problem' per say, but more of a personal preference. I would like to figure out how to get it set up so that when I maximize a window it will maximize to only ONE of my screens, at the moment, it's spans across both screens which I don't really like, especially considering my monitors are both CRT's and they are different sizes. :P

I'm running Feisty, with TwinView for dual monitor setup.

---

### Post by Nythain on 2007-05-12
i would suggest setting up dual x screens WITH xinerama... the only down side, is its going to be two desktops, you will be able to drag windows from one to the other, but they will have seperate backgrounds, instead of one image spanning the two

---

### Post by zaf on 2007-05-12
> would like to figure out how to get it set up so that when I maximize a window it will maximize to only ONE of my screens, at the moment, it's spans across both screens which I don't really like, especially considering my monitors are both CRT's and they are different sizes. :P

Hmmm, thats odd, since that should be how it is already. Maximizing windows is the responsibility of the Window Manager (eg KWin for KDE, Metacity for Gnome, etc, etc). So the question is, why is your window manager maximizing the windows across two screens. Assuming you haven't configured your Window manager to do this (Some strange people actually want this behavour), then I'm guessing the Window manager isn't getting the Xinerama information. The nvidia twinview driver publishes xinerama information to the X window manager, so the window manager can learn the layout of the various screens.

I'm going to run through the basics here, sorry:
1) Are you using the NVidia driver (not the open source nv driver). I'm assuming so, since you've mentioned the nvidia config utility
2) With the nvidia config utility (nvidia-settings):
   Under "X Server Display Configuration", is the Display Configuration set to "TwinView"?
3) Under the "X Screen 0" setting, does the "Displays" values list two monitors?
4) Since configuring it all, and getting it all working, have you tried rebooting?
5) What window manager are you using?

---

### Post by zaf on 2007-05-12
> **Nythain said:**
> i would suggest setting up dual x screens WITH xinerama... the only down side, is its going to be two desktops, you will be able to drag windows from one to the other, but they will have seperate backgrounds, instead of one image spanning the two

The problem with that would be OpenGL acceleration. You only get it on one screen (so those pretty X Screensavers don't work). I prefer using TwinView, it works well, TwinView publishes xinerama info to the X server so the Window Managers know which window is which. Using KDE + TwinView, I can have different backgrounds on different monitors.

---

### Post by Hobo Joe on 2007-05-12
> **zaf said:**
> The problem with that would be OpenGL acceleration. You only get it on one screen (so those pretty X Screensavers don't work). I prefer using TwinView, it works well, TwinView publishes xinerama info to the X server so the Window Managers know which window is which. Using KDE + TwinView, I can have different backgrounds on different monitors.

I don't really mind having one image across both, but it would be nice to be able to set this up while still using twinview.

I'm using beryl.

---

### Post by Hobo Joe on 2007-05-12
Also, another thing I noticed, Ubuntu isn't saving any of my view settings.(or X settings, whichever it is) Whenever I reboot, or even quick reboot, it sets itself back at 1024X768 with only one monitor, and I have to put all my settings back.

One more small thing I would like, is that when new windows open, if there is a way to have them open, not in the middle of both sreens, but in the middle of the 'absolute' screen. That would be great. :)

---

### Post by notquitemichael on 2007-05-12
about the saving the settings;
you need to open nvidia-settings as root (i.e. sudo nvidia-settings) and in the screen configureation file you need to click "save to xorg.conf" or something of the like.

about the window placement:
the problem may be beryl go into the settings - window management - place windows, and make sure it's set to intelligent.

i've got your setup with twinview and two different sized monitors and my windows maximise correctly so it should be possible. (although vlc seems to randomly pick where it's fullscreen output is.)

---

### Post by Hobo Joe on 2007-05-12
Well, the window placement worked, but windows still maximize across both screens....

As for the saving settings, I already had tried it, for some reason, it's not saving to the xorg, I know I could manually paste it into my xorg, but I'm afraid of messing somthing up. D:

Here is my current xorg:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:37:58 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
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
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
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
    Option         "XkbOptions" "lv3:ralt_switch"
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

							# /dev/input/event
							# for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"	# Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"

							# /dev/input/event
							# for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"	# Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"

							# /dev/input/event
							# for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"	# Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

And the one that the nVidia control panel shows up when i click on 'preview'

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:38:28 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
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
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
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
    ModelName      "ViewSonic A72f-2"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1152x864 +1152+0, CRT-1: 1152x864 +0+0; CRT-0: nvidia-auto-select +800+0, CRT-1: 800x600 +0+0; CRT-0: nvidia-auto-select +640+0, CRT-1: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

Being a noob to linux, I don't know if it it's really safe to paste that over, so if someone could tell me if it's good or not, that would be awesome.

---

### Post by Hobo Joe on 2007-05-12
Ok, I fixed the problems, with a bit help.
(if you are running beryl, shut it down while you do this, for me, I had some wierd crashes if I changed these settings while it was on)
1. Open nVidia control panel with root by 'sudo nvidia-settings'
2. Set secondary monitor to 'twinview'
3. Save settings with 'save to X configuration'
4. Reboot.
Now both monitors should be separate so if you maximize, it will only maximize to one, and if you open a program, it will no longer open in the 'seam' between the two monitors, but in the center of the primary.

---

### Post by Nythain on 2007-05-13
can you post what your xorg.conf ultimately looked like, because im still totally struggling with getting this twinview to behave as zaf says it can... any way i can get your to post your xorg.conf also zaf so i can compare and see what im doin wrong

---

### Post by Hobo Joe on 2007-05-13
Sure thing man.(I'm still not sure about getting sepparate images on each screen, if that's one of the things you wanted to do, what I did is get an image that is the same resolution as my monitors, and then set it to 'tile', that way it's not stretched.)

Xorg.conf:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Apr  4 23:40:17 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Apr  4 23:39:44 PDT 2007
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
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
    Screen      0  "Screen0" 0 0
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
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic A72f-2"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1152x864_75 +1152+0, CRT-1: 1152x864_75 +0+0; CRT-0: nvidia-auto-select +800+0, CRT-1: 800x600 +0+0; CRT-0: nvidia-auto-select +640+0, CRT-1: 640x480 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

