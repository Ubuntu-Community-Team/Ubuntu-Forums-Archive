---
title: "dual view issues"
date: 2005-10-11
forum: Desktop Environments
---

### Post by inz on 2005-10-11
Hello.
I am returning to ubuntu after I gave up on linux initially, mainly because I can run WoW on it with cedega now, but this is irrelevant, my issue is this:

I have two monitors on my computer-table, and in Windows I have had WoW running on the right one, and everything else on the left one. I am trying to configure dualview with xinerama, but everything spans over both monitors when I would rather have the gnome desktop on one, and just an additional blank one on the other one that I could reach with my mouse, has anyone got any experience with this? Any links, pointers, how-tos? I've searched for a while, but can only find points to do what I have just done, which just doesn't cut it

Maximizing firefox on this setup, well... It is absurd. ;)

---

### Post by HermanAB on 2005-10-11
In file /etc/X11/xorg.conf:
Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    Screen "screen1" LeftOf "screen2"
    Screen "screen2" RightOf "screen1"
    Option "Xinerama"
EndSection

Have a look at this guide:
[http://www.aerospacesoftware.com/fubar-howto.html](http://www.aerospacesoftware.com/fubar-howto.html)

It is in the middle somewhere.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by inz on 2005-10-12
If anyone stumbles onto my topic and wants a solution, it is this:

```
Section "Device"
        Identifier      "NVIDIA Corporation NV35 [GeForce FX 5900XT]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        BoardName       "NVIDIA GeForce FX5900XT"
        Option          "TwinView"      "true"
        Option          "RenderAccel"   "true"
        Option          "UseEdidFreqs"  "true"
        Option          "SecondMonitorHorizSync"     "30-69"
        Option          "SecondMonitorVertRefresh"   "50-120"
        Option          "MetaModes"                  "1024x768,1024x768"
        Option          "TwinViewOrientation"        "LeftOf"

```

The Option "Xinerama" thing didn't work for me as the xorg xinerama thingie seems to crash with nvidias own twinview. at least that is the impression I got, I am not using it at all now, and couldn't be happier. :)

---

