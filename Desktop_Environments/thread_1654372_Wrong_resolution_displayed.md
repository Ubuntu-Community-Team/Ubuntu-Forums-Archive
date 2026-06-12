---
title: "Wrong resolution displayed"
date: 2010-12-28
forum: Desktop Environments
---

### Post by arlensen on 2010-12-28
I have the following problem.
I use an Samsung syncmaster 2032mw screen, which has native resolution of 1680x1050. however, the resolution in which I am typing this, is only 1024?

The graphic card in use, is an on-board, Intel 82945G/GZ Integrated Graphics Controller.

The resolution used to be okay, even thought in monitors it was displayed as being 1024x768, it was 1680x1050. At some stage, I was playing an movie, and this resetted my resolution. What I also find quite strange, is that the resolution of the login screen is ok, but of session, once logged on not.

Find below my xorg.conf
```

arl@chandler:/usr/share/xresprobe$ cat xorg.conf
# bare-bones XFree86 config to start the server in probe-only mode
Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    RgbPath        "/etc/X11/rgb.txt"
EndSection
Section "ServerFlags"
    Option "AllowMouseOpenFail"
EndSection
Section "Module"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
    Load    "extmod"
    Load    "freetype"
    Load    "int10"
    Load    "record"
    Load    "vbe"
EndSection
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "keyboard"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection
Section "InputDevice"
    Identifier    "Generic Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
EndSection
Section "Device"
    Identifier    "Generic Device"
    Driver        "::DRIVER::"
EndSection
Section "Monitor"
    Identifier    "SyncMaster"
    Option        "DPMS"
EndSection
Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Device"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Generic Mouse"
EndSection
arl@chandler:/usr/share/xresprobe$ 

```I doubt wether my driver is set correctly

The version I use is 10.10, with all the latest updates. I tried to look up a solution on the internet, but failed. I hope you can help me.

lshw and xorg are also attached, if more info is needed, just let me know.

---

### Post by arlensen on 2010-12-30
Update:

I managed to fix this issue, by removing .gnome2* directories and .config directory, from my users home folder.

Sometimes, sollutions can be so simple.....

Update2:
I can even re-create the problem, by maximising an running video, then the resolution is lost?
But by removing .gnome2/* it is fixed again....

---

