---
title: "Can't get dual head with 10.4 on new Dell Optiplex 780"
date: 2010-08-13
forum: Desktop Environments
---

### Post by bethafin on 2010-08-13
Friends, 

I just got a new Dell Optiplex 780 tower. I installed Ubuntu 10.4 LTS (32-bit) without any problems but I am unable to detect my second monitor. Going through Preferences/Monitors and clicking on "Detect monitors" does not find the second monitor. 

The system has two video inputs, one integrated VGA-type (the one that works) and one in the PCI slot DVI-type. 

The exact same setup (same monitors, same cables) worked beautifully on Karmic Koala. 

Does anyone know how I can get 10.4 LTS work with dual heads?

Any help would be greatly appreciated.

Thanks
Ethan

Below is the output of my lspci and hwinfo:

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)



13: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2e12
  Unique ID: _Znp.SFJq_fZRtDB
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel 4 Series Chipset Integrated Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2e12 "4 Series Chipset Integrated Graphics Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0420
  Revision: 0x03
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xfe800000-0xfebfffff (rw,non-prefetchable)
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  I/O Ports: 0xecb0-0xecb7 (rw)
  IRQ: 33 (6860 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00002E12sv00001028sd00000420bc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 02.1: 0380 Display controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2e13
  Unique ID: ruGf.zhgSuVs59r0
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: graphics card
  Model: "Intel 4 Series Chipset Integrated Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2e13 "4 Series Chipset Integrated Graphics Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0420
  Revision: 0x03
  Memory Range: 0xfe700000-0xfe7fffff (rw,non-prefetchable)
  Module Alias: "pci:v00008086d00002E13sv00001028sd00000420bc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by ddemarco on 2010-08-20
This worked for me. This goes into /etc/X11/xorg.conf. If it doesn't exist, create it and use the below stuff.
 
 
```

# sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
Section "Module"
Load "bitmap"
Load "extmod"
Load "vbe"
EndSection
Section "Device"
BoardName "Intel"
Driver "intel"
Identifier "Device[0]"
VendorName "Intel"
Option "monitor-VGA1" "vga"
Option "monitor-DVI1" "dvi"
EndSection
Section "Device"
BoardName "Intel"
Driver "intel"
Identifier "Device[1]"
VendorName "Intel"
Option "monitor-VGA1" "vga"
Option "monitor-DVI1" "dvi"
EndSection
Section "Monitor"
Identifier "vga"
Option "DPMS"
Option "LeftOf" "dvi"
EndSection
Section "Monitor"
Identifier "dvi"
Option "DPMS"
# Option "LeftOf" "vga"
EndSection
Section "Screen"
Device "Device[0]"
Identifier "First"
Monitor "dvi"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1680x1050"
Virtual 3360 1050
EndSubSection
EndSection
Section "Screen"
Device "Device[1]"
Identifier "Second"
Monitor "vga"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1680x1050"
Virtual 3360 1050
EndSubSection
EndSection
Section "ServerLayout"
Identifier "Layout[all]"
Option "AIGLX" "true"
Screen 0 "First" 
EndSection
Section "DRI"
Mode 0666
EndSection
Section "Extensions"
Option "Composite" "Enable"
Option "RENDER" "Enable"
EndSection
 
 

```

---

### Post by mehturt on 2010-08-25
I have a similar problem with Dell D630..
I am able to use my Samsung SyncMaster 2443 via VGA1, but always blank screen via DVI1.
The xorg.conf did not help.

---

