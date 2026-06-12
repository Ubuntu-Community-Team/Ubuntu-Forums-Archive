---
title: "Screen resolution problem"
date: 2011-03-21
forum: Desktop Environments
---

### Post by z3uSS on 2011-03-21
Hy guys , i've just upgraded the lucid distro to the last update, and as usual i had the same problem with my nvidia driver. I did the same thing i've always did, reinstall manualy the driver, man edited xconf file and nvidia-setting-rc file ... but this time it doesn't work. Every time i reboot my screen resolution keeps going down to 800x600 ... even if i sudo edit nvidia-settings, xorg.conf, or .nvidia-settings-rc files. I really don't understand why ... does anyone had the same problem ? or maybe an solution ?

---

### Post by Grenage on 2011-03-21
Could you please post your xorg.conf?  Your monitor model and desired res would be a bonus.

---

### Post by z3uSS on 2011-03-21
here is xorg.conf:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GT"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


and the ress i want is the one mentioned in the xorg.conf above.

I have an laptop VAIO VGN-FZ31M so i can't give u an model name. 

here is also the rc file saved in my account and the root account also:

#
# /home/tbbt/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Mon Mar 21 11:26:03 2011
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = No
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = Graphics_Card_(GPU_0),Yes,1000

# Attributes:

0/CursorShadow=0
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/SyncToVBlank=0
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/AllowFlipping=1
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=0
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/DigitalVibrance[DFP-0]=0
0/GPUScaling[DFP-0]=131073
0/OverscanCompensation[DFP-0]=0
0/XVideoTextureBrightness=0
0/XVideoTextureContrast=0
0/XVideoTextureHue=0
0/XVideoTextureSaturation=0
0/XVideoTextureSyncToVBlank=1
0/XVideoSyncToDisplay=65536

---

### Post by realzippy on 2011-03-21
add

Option      "IgnoreEDID" "on"

to xorg.conf's device section,like:


```
Section "Device"
Identifier "Device0"
Driver "nvidia"
Option      "IgnoreEDID" "on"
VendorName "NVIDIA Corporation"
BoardName "GeForce 8400M GT"
EndSection
```

...not know if it works,but remember some older vaio thread where it helped.

---

### Post by z3uSS on 2011-03-21
tried that .. still same problem. and this is wierd ... because until last update it went all just fine. now it seems i have to rebuild my desktop every time i boot ...that's just plain stupid...

anyone else with an ideea ? i googled all day ... still no solution found...

LE: after editing xorg file i got the feelling that the problem is with the rc file ... not with the xorg one. it just refuses to load the setings from xorg ... even if i man put the resolution i want. can anyone help me here ?

---

### Post by realzippy on 2011-03-21
maybe nvidia-bug-report gives a clue,run:

```
sudo nvidia-bug-report.sh
```

and post the file created in your user's directory.

Doubt that nvidia-settings.rc causes this.....
btw,have you upgraded to Maverick or Natty?

---

