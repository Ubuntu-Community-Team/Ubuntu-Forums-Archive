---
title: "Typing of the Dead"
date: 2006-09-01
forum: Gaming &amp; Leisure
---

### Post by bilu on 2006-09-01
Hi,

This is my first post in a Linux forum, although I've managed myself pretty well so far just by searching and reading without needing to ask for help directly. Answers are usually out there.

The only thing that's getting me frustrated right now is installing one of the funniest games I've ever played, The Typing of the Dead.

Wine and Cedega still feel too brittle IMHO, but for this game it's worth the effort, at least so far.

Seems to work with Cedega 4.4, 4.3.2, 4.2.1, 4.2, 4.1.1, 4.1, 4.0.1, 4.0 ... :-({|= 
[http://cedegawiki.sweetleafstudios.com/wiki/The_Typing_of_the_Dead](http://cedegawiki.sweetleafstudios.com/wiki/The_Typing_of_the_Dead)

Also seems to work with Cedega 5.0.3
[http://transgaming.org/gamesdb/screenshots/single.mhtml?screenshot_id=1028](http://transgaming.org/gamesdb/screenshots/single.mhtml?screenshot_id=1028)

It also seemed to work with WineCVS back in 2004, but with fast music :)
[http://bugs.winehq.org/show_bug.cgi?id=2361](http://bugs.winehq.org/show_bug.cgi?id=2361)

I've tried Cedega 5.2.5, CedegaCVS, latest Wine from Wine repositories. I haven't tested WineCVS yet.

Cedega was the only one that finished installing the game. When I run it I allways get the message "No graphic support device" no matter what options I choose. I have a GeforceFX Go5200 with 64 MB of video memory with the 1.0-8762 drivers.

The relevant parts of xorg.conf:

```
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

Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS" "off"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"

#    Option         "NoFlip" "True"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "MetaModes" "1280x1024, 1024x768"
    Option         "UseEdidFreqs" "True"
    Option         "VertRefresh" "60"
    Option         "AllowGLXWithComposite" "True"
    Option         "XvmcUsesTextures" "True"
    Option         "RenderAccel" "True"
    Option         "NoRenderExtension" "False"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Maybe I'm not posting in the right place. Maybe I should start by playing with WineCVS, search for help in Wine forums and file bugs as needed. 

But feedback is welcome anyway :D

Thanks in advance,
Bruno

---

