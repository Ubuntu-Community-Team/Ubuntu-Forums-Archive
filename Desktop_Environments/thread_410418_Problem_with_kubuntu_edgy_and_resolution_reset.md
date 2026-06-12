---
title: "Problem with kubuntu edgy and resolution reset"
date: 2007-04-15
forum: Desktop Environments
---

### Post by nanog on 2007-04-15
I have an old box that I've moved to a new workstation with a dell 2001fp monitor. I cannot figure out how to get xorg to use the optimal 1600x1200 resolution. It insists on resetting to 1280x1024. I've tried every trick I know (e.g. sudo dpkg-reconfigure xserver-xorg etc.) and am completely stumped. Its running updated kubuntu edgy (upgraded all the way from breezy). Anyone have any ideas? I am very close to wiping it.


relevant section of xorg:
```
Section "Device"
  identifier "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
  boardname "Intel 915"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
  vendorname "Intel"
EndSection

Section "Monitor"
  identifier "DELL 2001FP"
  vendorname "Dell"
  modelname "Dell 2001FP (Analog)"
  HorizSync 31-80
  VertRefresh 56-76
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
  Monitor "DELL 2001FP"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1600x1200@60"
  EndSubSection
EndSection
```

915resolution -l output:
```
#
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 24 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

```

915resolution:
```

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=5a
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1600
YRESO=1200
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=24
```

lspci:
```
00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem
03:08.0 Ethernet controller
```

---

### Post by nanog on 2007-04-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/80611](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/80611) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Apparently its a known bug that has still not been fixed in edgy.

Adding **Option "NoDDC"** to my xorg.conf worked. Man this was exasperating!

```

Section "Device"
  identifier "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
  boardname "Intel 915"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
  vendorname "Intel"
EndSection

Section "Monitor"
	Identifier "DELL 2001FP"
        HorizSync 30-76
        VertRefresh 50-75
        Option "DPMS"
        Option "NoDDC"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
  Monitor "DELL 2001FP"
  DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1600x1200@60" 
EndSubSection
EndSection

```

---

