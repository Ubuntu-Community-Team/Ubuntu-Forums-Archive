---
title: "2 ATI Cards, 3 Monitors"
date: 2012-09-01
forum: Desktop Environments
---

### Post by ramirezz77 on 2012-09-01
Hello

I am working on the following Problem: I have two ati 5870 cards. On one I have connectet 1 Monitor via DVI, on the other I have connected two via DVI. Unfortunately I cant all of the three working at once. I know there is quite some material in the web on this topic but even do i was trying and searching quite extensively for some time i could not find a solution.

Depending on my xorg.conf file (i tried quite a lot of configurations) only one or the other two are working. with the following xorg.conf file on is displaying the graphical stuff an the other two just a black terminal where i can not start an xserver:

```

Section "Device"
    Identifier "ATI0"
    Driver "radeon"
    BusID "PCI:2:0:0"
    #Option "ZaphodHeads" "DVI-0"
    Screen 0
EndSection


Section "Device"
    Identifier "ATI1"
    Driver "radeon"
    BusID "PCI:7:0:0"
    #Option "ZaphodHeads" "DVI-1"
    Screen 1
EndSection

#-------Monitors Here----------------------
Section "Monitor"
    Identifier "DVI-0"
    # Option "Primary" "On"
    Option "DPMS" "true"
    # Option "PreferredMode" "1920x1200"
    # Option "TargetRefresh" "60"
    # Option "Rotate" "normal"
    # Option "Disable" "false"
EndSection


Section "Monitor"
    Identifier "DVI-1"
    Option "DPMS" "true"
    # Option "PreferredMode" "800x600"
    # Option "TargetRefresh" "60"
    # Option "Rotate" "normal"
    # Option "Disable" "false"
EndSection


Section "Monitor"
    Identifier "DVI-2"
    Option "DPMS" "true"
    # Option "PreferredMode" "800x600"
    # Option "TargetRefresh" "60"
    # Option "Rotate" "normal"
    # Option "Disable" "false"
EndSection

#-------Screens Here---------------------
Section "Screen"
    Identifier "Screen0"
    Device "ATI0"
    Monitor "DVI-0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        #Modes "1920x1200"
    EndSubSection
EndSection


Section "Screen"
    Identifier "Screen1"
    Device "ATI1"
    Monitor "DVI-1"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        #Modes "800x600"
    EndSubSection
EndSection


Section "Screen"
    Identifier "Screen2"
    Device "ATI2"
    Monitor "DVI-2"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        #Modes "1920x1200"
    EndSubSection
EndSection

#---------Server Configuration---------
Section "ServerLayout"
    Identifier "Default Layout"
    Screen "Screen0"
    Screen "Screen1" RightOf "Screen0"
    #Screen "Screen2" RightOf "Screen2"
EndSection


#--------Server Flags----------------
Section "ServerFlags"
 Option "Xinerama" "1"
EndSection

```Video Cards:
```

  *-display               
       description: VGA compatible controller
       product: Cypress XT [Radeon HD 5870]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:87 memory:d0000000-dfffffff memory:fe9e0000-fe9fffff ioport:e000(size=256) memory:fe9c0000-fe9dffff
  *-display
       description: VGA compatible controller
       product: Cypress XT [Radeon HD 5870]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:89 memory:c0000000-cfffffff memory:fe4e0000-fe4fffff ioport:a000(size=256) memory:fe4c0000-fe4dffff

```lspci | grep VGA output:
```

     02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cypress XT [Radeon HD 5870]
07:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cypress XT [Radeon HD 5870]

```But only one monitor seems to be detected:
```

grep 'Output.*connected' /var/log/Xorg.0.log
[  3251.049] (II) RADEON(0): Output DisplayPort-1 disconnected
[  3251.049] (II) RADEON(0): Output HDMI-1 disconnected
[  3251.049] (II) RADEON(0): Output DVI-2 disconnected
[  3251.049] (II) RADEON(0): Output DVI-3 connected

```Any help on this topic would be appreciated. Thank you a lot.

---

### Post by SJR Dorset on 2012-09-03
Have you tried using the proprietary AMD/ATI drivers?

---

### Post by ramirezz77 on 2012-09-11
Thank you for your reply! Yes but I ran into the same problem.

---

### Post by jubajuba on 2013-01-28
I have the same problem on Ubuntu 12.10. I only get the display to show me the two monitors connected to one of the graphic cards. The last card  I've tried the proprietary AMD/ATI driver and to be frank, that the opposite of helping...
gnome-control-center only shows two displays present.

I've got two Radeon HD 7000 cards:
```

twh@eden:~$ sudo lshw -short | grep '\ display\ '
/0/100/1/0                   display        Caicos [Radeon HD 7000 Series]
/0/100/1c.4/0                display        Caicos [Radeon HD 7000 Series]

```dmesg shows the card on 0000:03:00.0 being enabled, and the card on 0000:01:00.0 does not have the same "enabeling device" line.
```

twh@eden:~$ dmesg  | grep '\ radeon\ '
[    2.977084] [drm] radeon defaulting to kernel modesetting.
[    2.977086] [drm] radeon kernel modesetting enabled.
[    2.979869] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    2.979872] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[    2.985385] radeon 0000:01:00.0: irq 45 for MSI/MSI-X
[    2.985394] radeon 0000:01:00.0: radeon: using MSI.
[    3.090874] radeon 0000:01:00.0: WB enabled
[    3.090876] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff88041649ec00
[    3.193406] [drm] Initialized radeon 2.18.0 20080528 for 0000:01:00.0 on minor 0
[    3.193434] radeon 0000:03:00.0: enabling device (0000 -> 0003)
[    3.799310] radeon 0000:03:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    3.799311] radeon 0000:03:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[    3.803819] radeon 0000:03:00.0: irq 49 for MSI/MSI-X
[    3.803836] radeon 0000:03:00.0: radeon: using MSI.
[    3.810188] radeon 0000:03:00.0: WB enabled
[    3.810190] radeon 0000:03:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880412328c00
[    3.892088] [drm] Initialized radeon 2.18.0 20080528 for 0000:03:00.0 on minor 1

```Does anyone have any ideas?

---

