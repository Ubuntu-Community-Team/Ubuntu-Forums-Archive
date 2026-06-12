---
title: "Ubuntu Freezing"
date: 2005-08-06
forum: Desktop Environments
---

### Post by hiruzzolo on 2005-08-06
Hi everyone.. I have this big problem! Ubuntu keeps freezing after less than 5 minutes i log in.. It is completely freezed and you can't do anything but to reset.. I can't really find out what it is.. I thought it could be the video card, but I used that on another pc, always running Ubuntu, without problems! Moreover other distros worked quite well in my pc! I am quite a newbie,sorry!

My computer is:
Amd Sempron 2400+
512 mega ram
Ati radeon 7000
 ](*,)  ](*,)

---

### Post by amohanty on 2005-08-06
Boot into failsafe mode and see if it happens again. If so, reboot and post the results of :

>> dmesg | tail -n 50

If not, are you starting any applications or programs at login?
Did you save your session while logging out at any time?

AM

---

### Post by hiruzzolo on 2005-08-07
I did what you said but it still keeps on freezing.. >> dmesg | tail -n 50
 creates a blank file.. Then I tried to understand if it was some program .. and maybe it could be firefox because it is always open when it freezes, but I have to try more.. anyway I found after it freezes in the next session to redo everything I did before it freezed and it doesn't freeze now, but it freezes 5 minutes later... I can't really understand!
 ](*,)  ](*,)  ](*,) 
PS:sorry for my english

---

### Post by astoltz on 2005-08-07
Maybe it's just X that's locked up.  Can you switch to another terminal by pressing ctrl+alt+F1?  If you can, login and try entering "top" at the prompt (no quotes).  Top has a column for %CPU - see if that's maxed out at 100 and, if so, what app is causing it.

---

### Post by hiruzzolo on 2005-08-08
no,sorry,I can't.. The pc is completely freezed, i can't do anything but reset.. I was thinking that my pc has an Integrated video card (but linux don't have the drivers for this one), and I use another video card that I put... Could be this a problem?! I don't really know what to think..

---

### Post by amohanty on 2005-08-08
> >> dmesg | tail -n 50 

Dont type the '>>' its meant to represent the prompt. Just type:
dmesg | tail -n 50

AM

---

### Post by hiruzzolo on 2005-08-09
Hi! I tried to use kubuntu but it has the same problem! Here I tried to do what you said to me.. This are the results:

intel8x0: clocking to 48000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
ohci_hcd 0000:00:03.0: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:03.0: irq 20, pci mem 0xcfffd000
ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
ohci_hcd 0000:00:03.1: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:03.1: irq 21, pci mem 0xcfffe000
ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ACPI: PCI interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:03.2: Silicon Integrated Systems [SiS] USB 2.0 Controller
ehci_hcd 0000:00:03.2: irq 23, pci mem 0xcffff000
ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
PCI: cache line size of 64 is not supported by device 0000:00:03.2
ehci_hcd 0000:00:03.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 6 ports detected
sis900.c: v1.08.07 11/02/2003
ACPI: PCI interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
0000:00:04.0: Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 19, 00:0b:6a:d0:42:79.
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
eth1: RealTek RTL8139 at 0xd000, 00:05:5d:2c:90:f4, IRQ 17
eth1:  Identified 8139 chip type 'RTL-8139C'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
eth1: link up, 10Mbps, half-duplex, lpa 0x0000
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS not found.
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[drm] Initialized radeon 1.14.0 20050125 on minor 0: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Device is in legacy mode, falling back to 2.x
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
eth1: no IPv6 routers present 

What do you think about it? :mad:

---

### Post by blind0wl on 2005-08-09
You might want to try turning off ACPI when booting up.  In grub, ESC when you are asked to and edit the kernel line....add acpi=off to the end of it.  BTW...read the instructions at the bottom of the screen in grub on how to edit properly...

---

### Post by rogeriovinhal on 2005-08-09
Hey, I also have the freezing problem, but it is not everytime about 5 minutes after boot, it is completely random.
I typed the command you said and here is my output:
```

apm: overridden by ACPI.
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 19 (level, high) -> IRQ 19
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
mtrr: 0xc0000000,0x8000000 overlaps existing 0xc0000000,0x1000000
[fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 116387840
[fglrx] max   LFB = 116387840
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
eth0: no IPv6 routers present
hdc: lost interrupt
hdd: set_drive_speed_status: status=0x58 { DriveReady SeekComplete DataRequest }ide: failed opcode was 100
ide1: Drive 1 didn't accept speed setting. Oh, well.
hdd: lost interrupt
mtrr: no MTRR for c0000000,400000 found
mtrr: no MTRR for c0400000,200000 found
mtrr: no MTRR for c0600000,100000 found
mtrr: no MTRR for c0700000,1000 found
mtrr: 0xc0000000,0x8000000 overlaps existing 0xc0000000,0x1000000
[fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 116387840
[fglrx] max   LFB = 116387840
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768

```

---

### Post by Lux Perpetua on 2005-08-09
Starting today (after more than a week of normal use), Ubuntu started freezing on me. It's happened twice so far. Both times it happened, I had used "new login" to login as a different user and logged out back into my normal account, which I hadn't done before today. Other than that, I'm pretty sure the only change in my installation is that I installed the 'Sawfish' window manager (but Gnome/Metacity was running during both freezes). It didn't seem like the freezes were triggered by anything; they  were random.

Output of dmesg | tail -n 50, in case it means something to someone:
```

PCI: Setting latency timer of device 0000:02:00.0 to 64
eth0: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCIX:100MHz:32-bit) 10/100/1000BaseT Ethernet 00:11:25:b4:25:06
eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Yenta: CardBus bridge found at 0000:04:00.0 [1014:056c]
Yenta: ISA IRQ mask 0x0438, PCI irq 16
Socket status: 30000006
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:04:02.0[A] -> GSI 21 (level, low) -> IRQ 21
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth1: duplicate address detected!
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: IBM ThinkPad ACPI Extras v0.8
ibm_acpi: http://ibm-acpi.sf.net/
ibm_acpi: dock device not present
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 805 MBytes.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[fglrx] module loaded - fglrx 8.14.13 [Jun  8 2005] on minor 0
allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.
[fglrx] free  PCIe = 54804480
[fglrx] max   PCIe = 54804480
[fglrx] free  LFB = 108908544
[fglrx] max   LFB = 108908544
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total PCIe = 16384
ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
IBM machine detected. Enabling interrupts during APM calls.
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
cs: IO port probe 0x0100-0x04ff: excluding 0x370-0x377 0x3f0-0x3ff 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: excluding 0xcf8-0xcff
cs: IO port probe 0x0a00-0x0aff: clean.

```

---

### Post by hiruzzolo on 2005-08-16
Hi! Now I found a way to not freeze anymore, but now I don't have the 3d accelleration anymore(I think).. In /etc/X11/xorg.conf I changed the device driver to vesa.. But not to have 3d accelleration is a big problem! What do you think about it?

---

### Post by yaye on 2005-08-16
[QUOTE=hiruzzolo]Hi! Now I found a way to not freeze anymore, but now I don't have the 3d accelleration anymore(I think).. In /etc/X11/xorg.conf I changed the device driver to vesa.. But not to have 3d accelleration is a big problem! What do you think about it?[/QUOTE]

Hello,

Would you happen to be using an Nvidia AGP graphics card?

Ian

---

### Post by hiruzzolo on 2005-08-16
Hello! Sorry, I didn't tell you what video card I have. It is ati radeon ve/7000 (64 mb).. So it wouldn't make sense using nvidia drivers.. And the ati drivers that ubuntu installs as default have some bug, as I said.. What do you think?

---

### Post by yaye on 2005-08-16
[QUOTE=hiruzzolo]Hello! Sorry, I didn't tell you what video card I have. It is ati radeon ve/7000 (64 mb).. So it wouldn't make sense using nvidia drivers.. And the ati drivers that ubuntu installs as default have some bug, as I said.. What do you think?[/QUOTE]

My mistake.  When I clicked on the link, it took me to the top of a page.  I didn't realize it was the top of the second page of the thread.  I've had a problem with lockups in the past while using an Nvidia card with Fedora, Xandros and Ubuntu.  I found the solution, by reading the Nvidia release notes, was to add an option to the "Device" section of the xorg.conf file. I added:

Option "NvAGP"  "1"

below the Driver "nvidia" line.  This cured all lockups I had in Fedora, and when it occurred in the other distros, I added the same line and the lockups were gone.  I don't know whether the ATI driver has a similar option. You may want to contact ATI about it or read the release notes for the driver to see what options you can set to correct the problem.  Good Luck.

Ian

---

### Post by crispingatiesa on 2005-08-16
[QUOTE=hiruzzolo]Hi everyone.. I have this big problem! Ubuntu keeps freezing after less than 5 minutes i log in.. It is completely freezed and you can't do anything but to reset.. I can't really find out what it is.. I thought it could be the video card, but I used that on another pc, always running Ubuntu, without problems! Moreover other distros worked quite well in my pc! I am quite a newbie,sorry!

My computer is:
Amd Sempron 2400+
512 mega ram
Ati radeon 7000
 ](*,)  ](*,)[/QUOTE]

I have a similar problem when I changed my mobo and processotr. The problem happens to be a missconfiguration of the ram (wrong FSB speed)

1. Check if you have made changes to your memory or mobo, processor recently.

2. Check you are not having a high temperature problem (Sempron CPUs have a known problem when  you try to escale them back in Linux)

3. Related with 2. above (Semprons have problems with powernow in Linux)

Luck

---

### Post by sal on 2005-08-16
[QUOTE=yaye]My mistake.  When I clicked on the link, it took me to the top of a page.  I didn't realize it was the top of the second page of the thread.  I've had a problem with lockups in the past while using an Nvidia card with Fedora, Xandros and Ubuntu.  I found the solution, by reading the Nvidia release notes, was to add an option to a section of the xorg.conf file. I added:

Option "NvAGP"  "1"

below the line lines that have "nvidia" then the memory total on the card.  This cured all lockups I had in Fedora, and when it occurred in the other distros, I added the same line and the lockups were gone.  I don't know whether the ATI driver has a similar option. You may want to contact ATI about it or read the release notes for the driver to see what options you can set to correct the problem.  Good Luck.

Ian[/QUOTE]


i have an nvidia PCI geforce FX 5200 with the option NvAGP 0 because the card is pci. would the NvAGP 1 help me with this lock up problem as well even though im using a pci vido card?

---

### Post by speedsix on 2005-08-16
I had exactly the same problem..

[Thread here](http://www.ubuntuforums.org/showthread.php?t=42545) 

I ditched the ati 7000 and bought a cheap nvidia card and it's been perfect.

---

### Post by pirast on 2005-08-16
I opened a bug report some time ago because there was the same problem on my father's pc:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=10579](http://bugzilla.ubuntu.com/show_bug.cgi?id=10579)

Martin

---

### Post by hiruzzolo on 2005-08-16
Hi I tried to install mepis (don't kill me please! :P ) and all it is ok... I post the xorg part about the drivers here so maybe we can find how to fix it in ubuntu:

Section "Device"
 #Option "sw_cursor" # needed for some ati cards
 #Option "hw_cursor"
 #Option "NoAccel"
 #Option "ShowCache"
 #Option "ShadowFB"
 #Option "UseFBDev"
 #Option "Rotate"
 #Option "NoUseBios" # needed for some Savage cards
  Option "UseInternalAGPGART" "no"
# nvidia special options, use with care
  Option "CursorShadow" "1"
  Option "CursorShadowAlpha" "63"
  Option "CursorShadowYOffset" "2"
  Option "CursorShadowXOffset" "4"
  Option "FlatPanelProperties" "Scaling = native"
  Option "NoLogo" "false"
  Option "IgnoreEdid" "true" # needs to be true for some nvidia cards
  Identifier  "Card0"
  Driver "radeon"
  BoardName "unknown"
 #BusID  "PCI:1:0:0"
EndSection

---

### Post by pirast on 2005-08-16
Maybe anybody could try if it freezes in Breezy?

Martin

---

### Post by yaye on 2005-08-16
[QUOTE=sal]i have an nvidia PCI geforce FX 5200 with the option NvAGP 0 because the card is pci. would the NvAGP 1 help me with this lock up problem as well even though im using a pci vido card?[/QUOTE]

If you have a PCI card, I don't think changing to "1" will correct the problem.  I originally tried "0" ( I think this disables the AGP features of the driver). When it ran without lockups, I then tried "1" , which enables some form of AGP support.  Almost a year ago, I was helping a Xandros user ( mtdub ) to solve this problem on the Xandros Forums.  He tried the "0" option and still had lockups.  He tried swapping out components, and it was not until he changed the system board, while keeping the other original components, that he was able to get X running with the Nvidia card.  Here is the thread:

[http://forums.xandros.com/viewtopic.php?t=8435&postdays=0&postorder=asc&start=0](http://forums.xandros.com/viewtopic.php?t=8435&postdays=0&postorder=asc&start=0)  

Ian

---

### Post by yaye on 2005-09-25
[QUOTE=hiruzzolo]Hi I tried to install mepis (don't kill me please! :P ) and all it is ok... I post the xorg part about the drivers here so maybe we can find how to fix it in ubuntu:

Section "Device"
 #Option "sw_cursor" # needed for some ati cards
 #Option "hw_cursor"
 #Option "NoAccel"
 #Option "ShowCache"
 #Option "ShadowFB"
 #Option "UseFBDev"
 #Option "Rotate"
 #Option "NoUseBios" # needed for some Savage cards
**  Option "UseInternalAGPGART" "no"**
# nvidia special options, use with care
  Option "CursorShadow" "1"
  Option "CursorShadowAlpha" "63"
  Option "CursorShadowYOffset" "2"
  Option "CursorShadowXOffset" "4"
  Option "FlatPanelProperties" "Scaling = native"
  Option "NoLogo" "false"
  Option "IgnoreEdid" "true" # needs to be true for some nvidia cards
  Identifier  "Card0"
  Driver "radeon"
  BoardName "unknown"
 #BusID  "PCI:1:0:0"
EndSection[/QUOTE]

Check to see if the bold text:

Option "UseInternalAGPGART" "no"

is in the Ubuntu xorg.conf file.  If it is not there, you could try adding it, then restart X to see if the lockups no longer occur.  Save a copy of the original xorg.conf file before you may any changes.

Ian

---

### Post by hiruzzolo on 2005-10-17
Sorry, the last advice didn't work.. Now I'm trying to solve this problem in Breezy but it is always the same and it makes me sad because it is a huge problem! any other advices?

---

### Post by yaye on 2005-10-21
[QUOTE=hiruzzolo]Sorry, the last advice didn't work.. Now I'm trying to solve this problem in Breezy but it is always the same and it makes me sad because it is a huge problem! any other advices?[/QUOTE]

I don't use Mepis, so I don't know much about it.  If the the ATI card is working without lockups in Mepis, you could print out the xorg.conf files of each and compare them for differences, then add the lines that are in the Mepis version to the Ubuntu version.  You could also try replacing the Ubuntu xorg.conf file with the one from Mepis.  You can use Crl-Alt-Backspace to shutdown and restart the xserver without rebooting the computer. Good Luck.

Ian

---

