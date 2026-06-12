---
title: "Steam, TF2, Garry's Mod"
date: 2014-01-03
forum: Gaming &amp; Leisure
---

### Post by soloman469 on 2014-01-03
So when I try to open TF2 and Garry's Mod (my two fav games :D) I get an error message saying: Required OpenGL extension "GL_EXT_texture_sRGB_decode" is not supported. Please update your OpenGL driver.

I feel like i've gotten this before but it was in a post from last year which was deleted apparently. Any commands I need to run?

---

### Post by soloman469 on 2014-01-03
*Dramatic bump

---

### Post by dannyboy79 on 2014-01-04
It's poor etiquette to bump prior to waiting 24 hours at least. if you want faster help I would suggest the ubuntu IRC channel on freenode. I see you have a 3450, which drivers are you using?

---

### Post by efflandt on 2014-01-04
What does **glxinfo | grep GL_EXT_texture_sRGB** show? If you do not have glxinfo, install **mesa-utils**.

My old PC still running 10.04 with ATI X1300 graphics (default Radeon driver) shows **GL_EXT_texture_sRGB**, but not **GL_EXT_texture_sRGB_decode**.

But 12.04.3 iso booted on that PC from USB stick shows both functions, even with that old legacy card from before AMD bought ATI. And likewise both functions show up when that USB stick is booted on a newer tablet PC with ATI HD 6250 graphics. So the issue is not that the default Radeon driver does not support GL_EXT_texture_sRGB_decode (maybe the video chip does not).

Are you running the default Radeon driver and is your system up to date, or are you trying to run fglrx driver that no long supports your video chip?

---

### Post by soloman469 on 2014-01-04
So basically I need to install mesa-utils. Done that, now what?

---

### Post by soloman469 on 2014-01-04
and i ran the command you told me to run and it returned: GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB,

---

### Post by soloman469 on 2014-01-04
[COLOR=#800000]**GL_EXT_texture_sRGB**[/COLOR] was shown like that.

---

### Post by mips on 2014-01-04
What GPU are you using and which drivers for that GPU?

I could not launch CSS on a Intel GPU with open-mesa installed.

---

### Post by soloman469 on 2014-01-04
What command can I run to find that?

---

### Post by dannyboy79 on 2014-01-04
lshw -C display

---

### Post by efflandt on 2014-01-04
Run the following and post the output related to your video device (VGA) including what drivers it is using:```
sudo lspci -v
```

---

### Post by soloman469 on 2014-01-04
Ehhhh...: 

```
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
    Subsystem: Dell OptiPlex 745
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>

00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dfd00000-dfefffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: [88] Subsystem: Dell Device 01da
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell OptiPlex 745
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell OptiPlex 745
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff00 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell OptiPlex 745
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at dfffbc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: Dell OptiPlex 745
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: dfc00000-dfcfffff
    Prefetchable memory behind bridge: 00000000d0200000-00000000d03fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell OptiPlex 745
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: dfb00000-dfbfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell OptiPlex 745
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell OptiPlex 745
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell OptiPlex 745
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell OptiPlex 745
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell OptiPlex 745
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Memory behind bridge: dfa00000-dfafffff
    Capabilities: [50] Subsystem: Dell Device 01da

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell OptiPlex 745
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fec0 [size=16]
    I/O ports at ecc0 [size=16]
    Capabilities: [70] Power Management version 3
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    Subsystem: Dell OptiPlex 745
    Flags: medium devsel, IRQ 9
    Memory at dfffbb00 (32-bit, non-prefetchable) [size=256]
    I/O ports at ece0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell OptiPlex 745
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe40 [size=8]
    I/O ports at fe50 [size=4]
    I/O ports at fe60 [size=8]
    I/O ports at fe70 [size=4]
    I/O ports at fed0 [size=16]
    I/O ports at ecd0 [size=16]
    Capabilities: [70] Power Management version 3
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620 LE [Radeon HD 3450] (prog-if 00 [VGA controller])
    Subsystem: Dell OptiPlex 980
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dfdf0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at dc00 [size=256]
    Expansion ROM at dfe00000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
    Subsystem: Dell OptiPlex 745
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at dfbf0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Vital Product Data
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [e8] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-19-b9-ff-fe-4a-8e-a2
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: tg3
    Kernel modules: tg3

04:02.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
    Subsystem: Ralink corp. EW-7108PCg/EW-7128g
    Flags: bus master, slow devsel, latency 64, IRQ 18
    Memory at dfaf8000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: rt61pci
    Kernel modules: rt61pci
```

---

### Post by efflandt on 2014-01-06
I guess it is just fglrx driver in Ubuntu 12.10 and newer that no longer support ATI 4000 and older chips. In 12.04 the fglrx driver shoul.

But I have only run Steam games using nvidia graphics. My PC with ATI X1300 graphics has not been updated from 10.04 to 12.04 yet, and the tablet PC is only 1 GHz 2 core CPU and does not have room for TF2 (32 GB SSD w/Win7 and 32 GB SD w/both Lubuntu and Ubuntu and common /home partition).

---

### Post by soloman469 on 2014-01-12
Bump: Anything else I could try?

---

### Post by dannyboy79 on 2014-01-12
are you running x86 or x86_64bit Ubuntu? If 64bit you could try this driver [http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64](http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64)  BUT first you'll need to remove all versions of fglrx on your system as I am guessing that you installed the driver from the ubuntu repositories.

if you're running 32bit ubuntu than it's this driver: [http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86](http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86)

here's an answer on how to remove the fglrx driver you have installed now. [http://askubuntu.com/questions/160605/what-packages-how-do-i-uninstall-propriety-amd-catalyst-driver](http://askubuntu.com/questions/160605/what-packages-how-do-i-uninstall-propriety-amd-catalyst-driver)

---

