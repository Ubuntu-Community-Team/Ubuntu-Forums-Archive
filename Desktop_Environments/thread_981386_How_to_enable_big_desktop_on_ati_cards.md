---
title: "How to enable big desktop on ati cards"
date: 2008-11-13
forum: Desktop Environments
---

### Post by rizwanrafique on 2008-11-13
Hello,
Trying to enable big desktop for two monitors on an ATI Redeon card that has one vga and one dvi output port.

Have been fighting with this for few hours now. After much surfing and searching through forums and irc :-)

Here is my xorg.conf. It's basically a copy from somewhere I found.

Any clues/ideas? No idea what I'm doing wrong.

```

Section "ServerLayout"
    Identifier "Default Layout"
    Screen 0 "aticonfig-Screen[0]" 0 0
    InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
    Identifier "Keyboard0"
    Driver "kbd"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
EndSection

Section "Monitor"
    Identifier "aticonfig-Monitor[0]"
    Option "VendorName" "ATI Proprietary Driver"
    Option "ModelName" "Generic Autodetecting Monitor"
    Option "DPMS" "true"
EndSection

Section "Device"
    Identifier "aticonfig-Device[0]"
    Driver "fglrx"
    Option "EnableMonitor" "crt2,lvds"
    Option "VideoOverlay" "on"
    Option "OpenGLOverlay" "off"
    Option "DesktopSetup" "horizontal"
    Option "Capabilities" "0x00000800"
    Option "Mode2" "1280x1024"
    Option "VRefresh2" "60"
    Option "Centermode" "off"
    Option "PseudoColorVisuals" "off"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]"
    Device "aticonfig-Device[0]"
    Monitor "aticonfig-Monitor[0]"
    DefaultDepth 24
    SubSection "Display"
        Viewport 0 0
        Depth 24
    EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection 
```

Mainly I followed these links and they all seem to make sense.

[http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)
[http://forums.fedoraforum.org/showthread.php?t=162188](http://forums.fedoraforum.org/showthread.php?t=162188)
[http://jen3ral.wordpress.com/2008/04/27/ubuntu-804-ati-big-desktop/](http://jen3ral.wordpress.com/2008/04/27/ubuntu-804-ati-big-desktop/)

Oh yes, I'm on Ubuntu 8.10 with fglrx driver. And I've tried this with compiz on and off.

Any pointers will be highly appreciated.

Thanks,
Rizwan

---

### Post by rizwanrafique on 2008-11-14
hmm, bump :-)

---

