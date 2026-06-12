---
title: "Screen trouble"
date: 2007-10-24
forum: Desktop Environments
---

### Post by yyz on 2007-10-24
Hello,

 I've just made a clean install of **Ubuntu Gutsy Gibbon 7.10**. 

_The problem:_

The screen is far on the right (about 1-inch of the left part of my monitor remains blank-black), so I can't see what's going on, on the right side of my desktop.
I tried to look for a solution for my own by altering my monitor settings; the h/v position/phase/clock etc, but how disappointedly none gave me a solution :(

I appreciate any support given on this, thanks in advance :) !



yyz

---

### Post by TeaSwigger on 2007-10-24
May be helpful if you'd post the contents of your /etc/X11/xorg.conf file, and specify what graphics card and monitor you're using.

---

### Post by yyz on 2007-10-24
```

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "NEC CI"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "NEC CI"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

```

---

### Post by yyz on 2007-10-24
Its a Packard Bell monitor
Graphics card is SiS.

Thanks

---

### Post by yyz on 2007-10-24
> **yyz said:**
> Its a Packard Bell monitor
Graphics card is SiS.

Thanks

I'm sure its a simple issue, anyone?

---

### Post by yyz on 2007-10-24
If this problem continues, its going to be very bad for me :( (
Can someone find a solution for this plszz !!

---

### Post by yyz on 2007-10-24
buMp

---

### Post by TeaSwigger on 2007-10-24
You'll get it fixed. :)

Boy wish I was more of an expert. Not enough folks to go around I guess. Well let's see if I can help any more anyway... 

Ok the part we care about is this::

> Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "NEC CI"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "NEC CI"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

It isn't specifying your video card, it's just saying "generic." That could be a key. Evidently a default config that is working but not well enough. You say it's an SiS. What model exactly? The monitor is identified as an NEC but you say it's a Packard; that could just be that NEC made it for Packard but I don't know. Let's focus on the video card first. And what computer is this on? Chipset?

---

### Post by TeaSwigger on 2007-10-24
Hello again, I was searching and found this for you, please look it over:
[http://ubuntuforums.org/showthread.php?t=394373&highlight=SiS+video+driver](http://ubuntuforums.org/showthread.php?t=394373&highlight=SiS+video+driver)
If it's way too confusing or not on the mark post back and we'll look further into it. :)

---

### Post by yyz on 2007-10-25
TeaSwigger thank you very much, I have it fixed now :) :) :)

---

### Post by TeaSwigger on 2007-10-25
> **yyz said:**
> TeaSwigger thank you very much, I have it fixed now :) :) :)

Beautiful! If you would, post what fixed it and/or mark the thread [SOLVED] - the option's in "thread tools" up above your first post, so if others are having the same problem they might try this. Enjoy the ubuntu :)

---

