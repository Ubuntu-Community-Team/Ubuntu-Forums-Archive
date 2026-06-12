---
title: "Dual Screen Using Xinerama"
date: 2009-09-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by simpleprojectz on 2009-09-11
Hi all,

I have Dell system with two video cards:

[LIST]
[*]VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller
[*]VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000]
[/LIST]
I do want to have dual screens but I wasn't able to do that. I update to latest Karmic Alpha release -looking for additional compatibility on the XServer (no clue why I thought that), but the things is it still doesn' t work.

I just wanna now, is it possible to make it work? 
If so, should I set the " onboard" video card as the default one (on the Bios Setup)?

I changed and tried several xorg.conf files and I get to the point were settings made it  works for one display -I tried also setting up one screen at the time, just to validate that it works in a "standalone manual configuration" way, but only Intel video card works. Even default configuration seems to fail.

[COLOR=Blue]** Help will be really appreciated. Even if the answer is NO **(so I can stop trying)[/COLOR]

**Important Info:**

[LIST]
[*]*lspci (with "Auto" as the Default Video Controller on the Bios Setup)*
[/LIST]
 01:01.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)


[LIST]
[*]*lspci (with "OnBoard" as the Default Video Controller on the Bios Setup)*
[/LIST]
 01:01.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)


[LIST]
[*]*xorg.conf file*
[/LIST]
 Section "Device"
    Identifier    "nVidia NV18"
    Driver        "nvidia"
    BusID        "PCI:1:1:0"
    Screen        0
    Option        "NoLogo" "True"
EndSection

Section "Device"
    Identifier    "Intel 82865G"
    Driver        "intel"
    BusID        "PCI:0:2:0"
    Screen        1
EndSection

Section "Monitor"
    Identifier    "Acer V173 Left"
EndSection

Section "Monitor"
    Identifier    "Acer V173 Right"
EndSection

Section "Screen"
    Identifier    "Screen Left"
    Device        "nVidia NV18"
    Monitor        "Acer V173 Left"
    Option        "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier    "Screen Right"
    Device        "Intel 82865G"
    Monitor        "Acer V173 Right"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        0 "Screen Left"
    Screen        1 "Screen Right" RightOf "Screen Left"
    Option        "Xinerama" "true"
EndSection

[LIST]
[*]*Error*
[/LIST]
[I]Now I'm getting this -non fatal- error during the boot time

[/I][0.354845] pci 0000:01:01:0: BAR6: address space collision on of device [0xfea0000 - 0xfea1fffff]

---

