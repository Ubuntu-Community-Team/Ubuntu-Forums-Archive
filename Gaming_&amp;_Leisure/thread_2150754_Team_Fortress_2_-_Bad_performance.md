---
title: "Team Fortress 2 - Bad performance"
date: 2013-06-02
forum: Gaming &amp; Leisure
---

### Post by xbanane on 2013-06-02
Hi!

I use Ubuntu 12.04 LTS, GPU: AMD Radeon 6800, AMD CatalystSoftwareSuite Version 12.11 Beta Release

I sometime have a bad performence: FPS <20, some textures are missing

Screenshots:
[http://steamcommunity.com/sharedfiles/filedetails/?id=128112532](http://steamcommunity.com/sharedfiles/filedetails/?id=128112532)
[http://steamcommunity.com/sharedfiles/filedetails/?id=133068651](http://steamcommunity.com/sharedfiles/filedetails/?id=133068651)
[http://steamcommunity.com/sharedfiles/filedetails/?id=141220526](http://steamcommunity.com/sharedfiles/filedetails/?id=141220526)
[http://steamcommunity.com/sharedfiles/filedetails/?id=149918635](http://steamcommunity.com/sharedfiles/filedetails/?id=149918635)

Everything is OK when I reboot my system.


Can someone help me that I have a "stable" Team Fortress 2?



banane

---

### Post by AppleSlayer12 on 2013-06-02
I don't have that problem, but my guess is it's just your drivers (not entirely sure). I would check that first.

---

### Post by xbanane on 2013-06-03
ok, thanks.

---

### Post by xbanane on 2013-06-04
Tried all of them out but TF2 only supports the one I am currently using:

---

### Post by efflandt on 2013-06-05
Your **Additional Drivers** does NOT show which video drivers you are using, it shows that you are not using any of those.

Note that the only one that is Activated (green) says "This driver is activated, but not currently in use."  Did you try to use some method other than Additional Drivers to install some other drivers?

If you **sudo lspci -v** what does the output related to video show for **Kernel driver in use:** and **Kernel modules:**

---

### Post by xbanane on 2013-06-06
Thanks for you reply!

I've tried all of these listed and the beta- and non-beta drivers from the official amd-homepage.

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fe600000-fe6fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 844d
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 54
    Memory at fe707000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe706000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 840b
    Flags: bus master, fast devsel, latency 0, IRQ 55
    Memory at fe700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 844d
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 844d
    Capabilities: [a0] Power Management version 2

00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: d0100000-d01fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 844d
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Memory behind bridge: fe500000-fe5fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 844d
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 844d
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe705000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 844d
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: lpc_ich

00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 844d
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at f0d0 [size=8]
    I/O ports at f0c0 [size=4]
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f090 [size=16]
    I/O ports at f080 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: medium devsel, IRQ 4
    Memory at fe704000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 844d
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f030 [size=16]
    I/O ports at f020 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts XT [ATI Radeon HD 6800 Series] (prog-if 00 [VGA controller])
    Subsystem: Hightech Information System Ltd. Device 2305
    Flags: bus master, fast devsel, latency 0, IRQ 57
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe620000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at fe600000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_experimental_12, radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Barts HDMI Audio [Radeon HD 6800 Series]
    Subsystem: Hightech Information System Ltd. Device aa88
    Flags: bus master, fast devsel, latency 0, IRQ 56
    Memory at fe640000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

03:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=03, secondary=04, subordinate=04, sec-latency=32
    Capabilities: [c0] Subsystem: ASUSTeK Computer Inc. Device 8489

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 53
    I/O ports at d000 [size=256]
    Memory at d0004000 (64-bit, prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at d0010000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169

06:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fe500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [50] Power Management version 3
    Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [a0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
    Capabilities: [150] Latency Tolerance Reporting
    Kernel driver in use: xhci_hcd
```

---

### Post by xbanane on 2013-06-06
-- duplicate --

---

### Post by MrBackhand on 2013-06-07
It probably is a driver but it is possible your local game cache is corrupted as well. Have you tried verifying the integrity of the game cache of TF2?  Also, do you get the same texture issues at other resolutions such as 1280x1024 or 1024x768?  I have similar texture tearing in Killing Floor sometimes when I run it at 1680x1050 but I never have the problem at 1280x1024.  I am using an NVidia Geforce GTX 550 Ti.

---

### Post by xbanane on 2013-06-26
No, isn't working.

---

### Post by R33D3M33R on 2013-06-26
Open Catalyst Control Center, and click information. Take a screenshot, upload it somewhere and paste the image on the forum.

---

### Post by xbanane on 2013-06-28
[IMG]http://i.imgur.com/gAhlRzu.png[/IMG]

---

### Post by R33D3M33R on 2013-06-28
The driver seems to be installed OK, the next thing I would try is disable Tear Free&Vertical refresh and also disable Catalyst A. I. You can find all of these settings in CCC.

---

### Post by xbanane on 2013-07-03
Nope. Still won't work.

---

