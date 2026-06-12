---
title: "Ati 9550 Xinerama fails; fglrxinfo fails"
date: 2009-02-03
forum: General Help
---

### Post by dirthead on 2009-02-03
Hi,

I installed Ubuntu 8.10 onto my manager's desktop machine. He has an Ati 9550 video card attached to two monitors. Both monitors show the same desktop. I tried enabling xinerama so his desktop would be across both monitors. No go. I think the drivers are not installed correctly. I installed them from the menu and they are the proprietary drivers. I don't think they are installed correctly because of the fglrxinfo output below. I've seen many posts where people get this card working with dual monitors. Can anybody shed some light on what I'm doing wrong? The xorg.conf is at the end.

```

strecker@strecker-desktop:/etc/X11$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Here's the lswh output:

```

strecker@strecker-desktop:/etc/X11$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: RV350 AS [Radeon 9550]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AS [Radeon 9550] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 mingnt=8

```

```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[0]-1" LeftOf "aticonfig-Screen[0]-0"
        Option "Xinerama" "true"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      0
        Option "DDCMode" "True"
        Option "MonitorLayout" "CRT,LCD"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-1"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
        Option "DDCMode" "True"
        Option "MonitorLayout" "CRT,LCD"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-1"
        Device     "aticonfig-Device[0]-1"
        Monitor    "aticonfig-Monitor[0]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option "Xinerama" "true"
        Option  "AIGLX" "off"
EndSection

```

---

### Post by dirthead on 2009-02-05
I ripped out the proprietary drivers that came with Ubuntu and installed the latest drivers from ATI. I was able to get the dual monitors working after that. I tried using the Catalyst application but it didn't seem to save my changes. I found a post, somewhere deep in the internet, that said to open the screen resolution app, after using Catalyst, and hit 'Apply'. Somehow that saves the changes from Catalyst. I don't know how, but it worked.

---

### Post by garethyoung on 2009-03-08
Hi, I'm having the same problems with my Radeon 9550. I want to run dual screens and have had no luck. I'm new to ubuntu and would appreciate it if you could perhaps post a step by step walk through.

Many thanks

---

