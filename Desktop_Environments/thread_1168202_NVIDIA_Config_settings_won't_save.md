---
title: "NVIDIA Config settings won't save"
date: 2009-05-23
forum: Desktop Environments
---

### Post by CompanyCalls405 on 2009-05-23
When I first started Ubuntu 9.04 the default resolution was 800x600. I had to download some NVIDIA graphics drivers to let me use 1024x768. That all worked fine, but the problem is that when rebooting, my configuration settings were not saved and I was back at 800x600 and I had to once again open nvida settings and reconfigure.

I found a thread here that dealt with my exact problem:

[http://ubuntuforums.org/showthread.php?t=471256](http://ubuntuforums.org/showthread.php?t=471256)

I did exactly what was said, opening it in terminal with 'sudo' including renaming the save file 'xorg.conf.backup', but still, when I reboot, I'm back to 800x600.

Not sure if this is relevant but when I boot via terminal I get several error messages within the terminal:

> ERROR: Unable to assign attribute CursorShadow specified on line 20 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 21 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 22 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 23 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 24 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 25 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 26 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 27 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 28 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 29 of configuration
       file '/home/kit/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 30 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 31 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 32 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 33 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 34 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 35 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 36 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 37 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 38 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 39 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 40 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 41 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 42 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 43 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 44 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 45 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       46 of configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       47 of configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 48 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).
Thanks in advance for any help.

---

### Post by fillintheblanks on 2009-05-23
after you reboot do your saved settings load when you type 

> nvidia-settings -l

---

### Post by Stenrad on 2009-05-23
Hi there!

Have you tried running the following command:-

```
gksudo nvidia-settings
```

Regards,

Stenrad.

---

### Post by CompanyCalls405 on 2009-05-23
> **Stenrad said:**
> Hi there!

Have you tried running the following command:-

```
gksudo nvidia-settings
```Regards,

Stenrad.

I ran that and saved. Still after a reboot it remains the same. It seems to be saving to '/etc/X11/xorg.conf'
is that correct?

Also, this is the 'Save X Configuration "Preview"

> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 60.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
EndSection

Section "Screen"

# Removed Option "metamodes" "1024x768 +0+0; 1024x768_60 +0+0;+0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0; 1024x768_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



>  			 				nvidia-settings -l 			 		

When I type this I'm given the exact same ERRORS from the bottom of my original post.

---

### Post by jordanmthomas on 2009-05-24
Install Gentoo

---

