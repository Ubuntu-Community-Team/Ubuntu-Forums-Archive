---
title: "DESKTOP icons missing...."
date: 2010-03-20
forum: Desktop Environments
---

### Post by venkatad on 2010-03-20
hi I could not see my desktop, how ever cairo is coming up so that I can do some browsing over internet. I tried these commands:
nautilus &   --not solved the problem

I went to gconf-editor and checked nautilus preference -show desktop is already checked.

re installed nautilus-- no help

when i try thru failsafe error reads:
gnome-5234 can not display desktop something like this....

Pls suggest me some solution

TIA

---

### Post by ajgreeny on 2010-03-20
If you see just a black desktop, but with the panels still showing, and many application windows also appearing, unless they are maximised, this is probably caused by an ATI graphics card, using the open source driver, with a resolution above 1024x768 at 24 bit colour, and with desktop effects enabled.

If I am correct, and you do have an ATI card, you have a few options:-
1  Run without compiz - possible, but you may prefer to have the effects enabled.
2  Use a lower resolution - again possible, but frankly, silly if you have a bigger screen than 1024x768.
3  Use a lower colour depth of 16, which you can enable in xorg.conf - very possible and my chosen way to overcome this problem.

Here is the content of my xorg.conf showing how I enable the lower colour depth  in order to use compiz when I choose.
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
    Option         "AccelMethod" "UXA"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```Change any of the figures (mine) to fit your system and try that out.

---

