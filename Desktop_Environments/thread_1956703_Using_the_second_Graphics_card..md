---
title: "Using the second Graphics card."
date: 2012-04-11
forum: Desktop Environments
---

### Post by rewolff on 2012-04-11
The fan on my main graphics card stopped. So I've been using a pciE-x1 card in the meanwhile. This morning the "fixed" card came back, so I decided to keep the x1 card, for another monitor I have lying around anyway. 

The card is seen in lspci: ```
01:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
04:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
04:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)

```
The card is seen by X when it starts up: 

```
[    70.416] (--) PCI:*(0:1:0:0) 1002:9498:1043:0324 rev 0, Mem @ 0xc0000000/268435456, 0xfe8e0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
[    70.416] (--) PCI: (0:4:0:0) 1002:7146:17af:2058 rev 0, Mem @ 0xd0000000/268435456, 0xfebe0000/65536, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    70.416] (--) PCI: (0:4:0:1) 1002:7166:17af:2059 rev 0, Mem @ 0xfebf0000/65536

```
but then it isn't used. 
The "big" card does have the asterix to indicate that its the default, I guess. 

I've searched the internet, and I find lots of people who modify xorg.conf (I don't have one), re-init it with aticonfig (I don't have that, it's for the now-outdated binary driver, right?), etc etc. 

I've tried adding ```
Section "Screen"
    Identifier     "Screen 1"
    Device         "Device0"
    #Monitor        "My Monitor"
EndSection

Section "Screen"
    Identifier     "Screen 2"
    Device         "Device1"
    #Monitor        "My Monitor"
EndSection



Section "Device"
Identifier "Device0"
Driver "radeon"
#VendorName "NVIDIA Corporation"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "Device1"
Driver "radeon"
#VendorName "NVIDIA Corporation"
BusID "PCI:4:0:0"
EndSection

Section "ServerFlags"
    Option "Xinerama" "true"
EndSection


Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Screen 1"
        Screen          "Screen 2" LeftOf "Screen 1"
        #InputDevice "WizardPen Tablet" "SendCoreEvents"
        #InputDevice "touchscreen" "CorePointer"
EndSection


```to my xorg.conf. That eventually gives me 3 screens, but then I can't put them in the proper videomode using xrandr. Without "xinerama" I can't move windows between the two most important screens (The third is further away). 

Isn't there some simple way to say: "Use the second card too"?

---

