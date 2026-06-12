---
title: "Screen tearing with Intel (SOLVED)"
date: 2016-02-03
forum: Desktop Environments
---

### Post by Fugeno_Skritaz on 2016-02-03
Hi. I've been using ubuntu and it's spins for a long time now and I have some problems with all of them.

I am running a 7 years old machine with Dual core 2.5 GHz CPU, 2 GB DDR2 RAM and Intel G33/31 chipset graphics. these are mid-to-low end specs.

Here are the problems I encounter :

Unity/Ubuntu: lag and freeze

Ubuntu GNOME: Screen flickers when I click the activities button or change wallpaper

Xubuntu: Screen tearing.  the window manager tweaks has an option to enable vsync and it works but doesn't work when I play videos full-screen.

Ubuntu MATE: the application menu has a huge delay in loading app icons at startup and screen tearing in all window managers (except compiz). 

Lubuntu: dull look and docky doesn't work properly. openbox has minor screen tearing issues (only while dragging and moving windows)

Kubuntu: Haven't tried it yet because I think my system is too weak to run KDE. 

My system is 100% trouble free when I run Elementary OS 0.2 Luna which uses the Pantheon desktop environment and I have no issues of screen tearing when I use compiz. compiz works smooth and fast for me . 

Can anybody recommend what desktop environment should I use that works like a charm out of the box?? Or a way to resolve my problems (especially the GNOME flickering problem because I love GNOME)

---

### Post by blueridgedog on 2016-02-03
Can you post the device section of your /etc/X11/xorg.conf file?  Since you are using an intel graphic chip, this may help:

[http://askubuntu.com/questions/418398/tear-free-disabled-in-intel-graphics-tearing-in-xubuntu/469653#469653](http://askubuntu.com/questions/418398/tear-free-disabled-in-intel-graphics-tearing-in-xubuntu/469653#469653)

---

### Post by Fugeno_Skritaz on 2016-02-03
Thanks for the link. Although it seems to partially help my problem. 

When I do a terminal command :

```
cat /var/log/Xorg.0.log
```

I get a long output where one of the lines says :

17.681] (==) intel(0): TearFree disabled

which is a good thing because now I know that this feature has been disabled.

But the problem is that I dont have a xorg.conf file in my /etc/X11 directory :( So what should I do?

---

### Post by blueridgedog on 2016-02-03
I have been out of the Ubuntu distro for a while....I am not certain how it loads its config at this point.  Perhaps others can help.  If you can enable TearFree, it may help.

---

### Post by Fugeno_Skritaz on 2016-02-03
Hi. using some online tutorials, I was able to create a Xorg.conf file. But editing it doesnt seem to help. Here is the output of my Xorg.conf file

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "DRI"                    # <str>
        #Option     "Present"                # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "VSync"                  # [<bool>]
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "ReprobeOutputs"         # [<bool>]
        #Option     "DeleteUnusedDP12Displays"     # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "VirtualHeads"           # <i>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

---

### Post by vasa1 on 2016-02-03
> **Fugeno_Skritaz said:**
> ...
My system is 100% trouble free when I run Elementary OS 0.2 Luna which uses the Pantheon desktop environment and I have no issues of screen tearing when I use compiz. compiz works smooth and fast for me . 

Can anybody recommend what desktop environment should I use that works like a charm out of the box?? Or a way to resolve my problems (especially the GNOME flickering problem because I love GNOME)
Elementary OS 0.2 Luna works for you. So why the need to change?

---

### Post by Fugeno_Skritaz on 2016-02-04
> **vasa1 said:**
> Elementary OS 0.2 Luna works for you. So why the need to change?

Because of two reasons:

1. Luna is based on 12.04 LTS and so it doesn't offer MTP/android support. 

2. Google Chrome is ending support for all 12.04 *buntus and all 32-bit Linux distros.

I could have tried Freya but I think it's going to be a resources devourer

---

### Post by Fugeno_Skritaz on 2016-02-16
Hi. I have figured the way out to eliminate screen tearing. I had to create a file by the name "xorg.conf" in /usr/share/X11/xorg.conf.d and edit it with a text editor as in the link posted in the first reply by blueridgedog :)

I want to thank you all for the help :) and I have changed the topic name to a more appropriate one to help other users facing the same issue that I did

---

