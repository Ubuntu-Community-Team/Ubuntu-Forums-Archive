---
title: "Game Window Resizing."
date: 2007-12-26
forum: Gaming &amp; Leisure
---

### Post by Dwiman89 on 2007-12-26
HI I resently got Neverwinter NIghts installed. I need help getting the window smaller. The game normally runs full screen. This presents problems because I have dual monitors.Thanks to cogadh, I was able to get it playing in a window by editing the nwn.ini file, under  the [Display Options] section, by changing the entry "Fullscreen=1" to "Fullscreen=0" then adding the line "AllowWindowedMode=1".
The game may play in a window but it is really big, and wont allow me to just resize it. i was screwing around and added AllowWindowResize=1 under the display section. it didnt work so I deleated the line. I dont know how this stuff works that was just experimentation. please help me with this. The window is so big its unplayable because it so bad stretched wide ways that the game is distorted.
Here is the INI file that i changed to get it to not play fullscreen. 
```
[Sound Options]
Speaker Type=-1
SoundFX Volume=0.60
Voice Volume=0.85
Music Volume=0.60
2D3D Bias=0.00
Number 3D Voices=16
Number 2D Voices=16
3D Provider=
Environment Effects=0
DisableSound=0

[Display Options]
UseLargeFont=0
RefreshRate=0
BitsPerPixels=32
Height=600
Width=800
TexturePack=3
FullScreen=0
AllowWindowedMode=1

[Video Options]
Enable CreatureEnvironmentMapping=1
Enable TextureAnimations=1
EnableSkyboxes=2
CreatureShadowDetail=2
Gamma=1.000000
VideoQualitySetting=3
EnableEnvironmentShadows=1
EnableFastGrass=0
EnableGrass=1
CreatureWindSetting=2
Enable AnisotropicFiltering=0
Enable Truform=0
EnableVisualEffectsHigh=1
NumShadowCastingLights=3
ShinyWater=1
Enable VSync=0
AntiAliasing Mode=0
NumDynamicLights=8
``` 

Here is what it look like...
[http://photo.ringo.com/247/247200887O410804847.jpg]("http://photo.ringo.com/247/247200887O410804847.jpg")
[http://photo.ringo.com/247/247200892O353682009.jpg]("http://photo.ringo.com/247/247200892O353682009.jpg")

Thanks for your help.

---

### Post by Dwiman89 on 2007-12-26
Please Help!!!

---

### Post by autocrosser on 2007-12-26
I plat UT2k4 with a dual monitor unit & I modded my xorg.conf to play the game only on one monitor by changing my metamodes.

This is in my device section:

Option         "MetaModes" "1280x1024_75,1280x1024_75;1280x1024_75,NULL;1024x768,1024x768;800x600,800x600"

notice the second mode--runs one monitor with the second one "null"

I have only played neverwinter several years ago & don't know if there would be a option in the game to choose resolution like in UT.....


Hope this helps!!

---

### Post by Dwiman89 on 2007-12-26
Which Device section?
```
Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

```

I thought that would be under the screen section:

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1024x768" "800x600" "720x400" "640x480" "1x1"
    EndSubSection
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1024x768 +1024+0, CRT-1: nvidia-auto-sel$
EndSection

```
Messing with Xorg.conf really scares me. Ive messed it up a bunch getting dual screens working....

---

### Post by autocrosser on 2007-12-27
I posted the wrong xorg---my current one looks like this in the device & screen sections:

Section "Device"
    Identifier    "Videocard0"
    Driver        "nvidia"
    Vendorname    "NVIDIA Corporation"
    Boardname    "GeForce 7600 GS"
    Option        "RenderAccel"    "true"
    Option        "CursorShadow"    "true"
    Option        "Backingstore"    "true"
    Option        "RandRRotation"    "true"
    Option        "Coolbits"    "1"
    Option        "TripleBuffer"    "true"
    Option        "AllowDDCCI"    "true"
    Option        "MultisampleCompatibility"    "true"
    Option        "UseEdidFreqs"    "true"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "false"
        Option          "IncludeImplicitMetaModes" "false"
        Option          "FlatPanelProperties" "Scaling = Centered"
    #Option         "HWcursor" "false"
    #Option         "SWcursor" "true"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
    #Enable 32-bit ARGB GLX Visuals
    Option        "AddARGBGLXVisuals"    "true"
    Option        "TwinView"    "1"
    Option        "metamodes"    "CRT-0: 1280x1024_75 +0+0, CRT-1: 1280x1024_75 +1280+0; CRT-0: 1280x1024_75 +0+0, CRT-1: NULL; CRT-0: 1024x768 +0+0, CRT-1: 1024x768 +1024+0; CRT-0: 800x600 +0+0, CRT-1: 800x600 +800+0"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Modes        "1600x1200"    "1280x1024"    "1024x768"    "800x600"    "640x480"
    EndSubSection
EndSection

---

