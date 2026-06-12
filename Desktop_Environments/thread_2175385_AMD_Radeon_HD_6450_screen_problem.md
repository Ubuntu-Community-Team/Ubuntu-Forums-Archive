---
title: "AMD Radeon HD 6450 screen problem"
date: 2013-09-19
forum: Desktop Environments
---

### Post by ashokshah25 on 2013-09-19
Hello, 

I have an AMD Radeon HD 6450 Video card. Recently there was an update in Ubuntu 13.04 for the fglrx drivers which enabled me to have dual monitor after a long time. However, my screen seems to be chopping off quite a bit of pixels on the right most side. I have tried to use the amdcccle command and increase the screen size, but it does not work. 

Here is the output of lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6450]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Caicos HDMI Audio [Radeon HD 6400 Series]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe (rev 01)
```

Here is my xorg.conf file:
```
Section "ServerLayout"    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection


Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection


Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1440x900"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
EndSection


Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection


Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3200 3200
        Depth     24
    EndSubSection
EndSection


Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection



```


Any help is really appreciated.

Thanks,
Ashok.

---

### Post by Pengwyn44 on 2013-09-19
I have had the same problem and tried all sorts of solutions. If you use the commercial AMD Radeon driver rather the one supplied by 13.04, it makes matters worse.
I have wasted hours on it, so I have replaced the Radeon card with a 512MB ATI Radeon HD 4350 PCI Express (from Ebay). It now works OK.
It cost £24.50.

---

