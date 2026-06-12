---
title: "No surround via HDMI"
date: 2011-01-16
forum: Desktop Environments
---

### Post by fabianneke on 2011-01-16
Hello,

I have a mediacenter PC that is connected to a surround receiver via HDMI, but all i can send over the HDMI link is stereo sound, no surround.

I checked the following:
- latest alsa driver is installed :
mediacenter:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
- system -> preferences -> sound :
In "profile" on the hardware tab, it only says analog or digital stereo, not possible to select something like surround or 5.1 channel sound


When issuing the command 'alsamixer', i see the following hardware displayed:
- card: HDA Intel
- chip: Intel IbexPeak HDMI


Complete hardware list:
mediacenter:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 8383
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 8383
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at cc00 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 8383
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f7cfb000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 8383
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f7cfa000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 840b
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f7cf4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: f0000000-f01fffff
	Prefetchable memory behind bridge: 00000000f0200000-00000000f03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f7e00000-f7efffff
	Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f7d00000-f7dfffff
	Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 8383
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f7cf9000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Memory behind bridge: f7f00000-f7ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 8383
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8383
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
	I/O ports at b880 [size=8]
	I/O ports at b800 [size=4]
	I/O ports at b480 [size=8]
	I/O ports at b400 [size=4]
	I/O ports at b080 [size=16]
	I/O ports at b000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 8383
	Flags: medium devsel, IRQ 3
	Memory at f7cf8000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8383
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
	I/O ports at c880 [size=8]
	I/O ports at c800 [size=4]
	I/O ports at c480 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c080 [size=16]
	I/O ports at c000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 8432
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at d800 [size=256]
	Memory at f6fff000 (64-bit, prefetchable) [size=4K]
	Memory at f6ff8000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at f7de0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

02:00.0 IDE interface: VIA Technologies, Inc. PATA IDE Host Controller (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 838f
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=16]
	Expansion ROM at f7ef0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: pata_via
	Kernel modules: pata_via

04:01.0 Network controller: RaLink RT2800 802.11n PCI
	Subsystem: Linksys Device 0067
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f7ff0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2800pci
	Kernel modules: rt2860sta, rt2800pci



Does anyone have an idea how i can enable surround over my HDMI link?

Thanks a lot,


Fabian

---

### Post by fabianneke on 2011-01-23
hello,

After reading around on google, i found out that it might be the hdmi controller that is not capable of sending surround sound.I have no idea how i can check that. Anyone who knows?

In case this is the problem, would anyone happen to know a basic graphic card (only used for watching movies (up to 1080p)) that supports surround over HDMI in ubuntu?

Thanks a lot,

Fabian

---

### Post by fabianneke on 2011-01-28
anyone?

---

