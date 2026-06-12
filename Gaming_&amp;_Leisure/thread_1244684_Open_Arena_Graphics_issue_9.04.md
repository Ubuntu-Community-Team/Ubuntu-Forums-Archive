---
title: "Open Arena Graphics issue 9.04"
date: 2009-08-19
forum: Gaming &amp; Leisure
---

### Post by Xoanan on 2009-08-19
Hi All

The graphics for Open Arena no longer display properly in Open Arena after my upgrade to 9.04.  Any ideas?:popcorn:

---

### Post by commodore256 on 2009-08-20
Try turning compiz off by installing the compiz fusion icon and change the window manager to metacity.

I think I had the same problem and that helped me.

---

### Post by Xoanan on 2009-08-20
> **commodore256 said:**
> Try turning compiz off by installing the compiz fusion icon and change the window manager to metacity.

I think I had the same problem and that helped me.

I am still using xfwm at this time; I installed compiz once and my system ran to slowly for it. Would installing metacity work w/o compiz?

---

### Post by Perfect Storm on 2009-08-20
You can use fusion-icon to disable compiz/reselect metacity. 

Another option;
There's a script thread on the game forum which you can use with eg. games which disable compiz and launch the game.

---

### Post by Xoanan on 2009-08-20
> **Artificial Intelligence said:**
> You can use fusion-icon to disable compiz/reselect metacity. 

Another option;
There's a script thread on the game forum which you can use with eg. games which disable compiz and launch the game.

That's cool but, I am currently not using either compiz or metacity.  I am only using the xfwm which is the default Window manager for Xubuntu.

---

### Post by Perfect Storm on 2009-08-20
You can use fusion-icon to switch to xfwm default as well AFAIK.

---

### Post by Xoanan on 2009-08-20
> **Artificial Intelligence said:**
> You can use fusion-icon to switch to xfwm default as well AFAIK.

Again that's cool too; but, if all I am using is xfwm, what exactly am I switching to? Compiz Fusion is not installed on my machine at all.  Do I need compiz to play the game?:popcorn:

---

### Post by Xoanan on 2009-08-22
Installed Compiz Fusion Icon and Compiz; I can switch easily from Compiz, XFWM and Metacity.  There appears to be no difference in the graphics of the game.

---

### Post by hikaricore on 2009-08-22
It's possible you've all overlooked it possibly being driver issue?
Do other 3d games work properly?  Also info about your hardware and current driver would be nice.

---

### Post by Xoanan on 2009-08-22
> **hikaricore said:**
> It's possible you've all overlooked it possibly being driver issue?
Do other 3d games work properly?  Also info about your hardware and current driver would be nice.

Here we go

```
xoanan@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
	Flags: bus master, fast devsel, latency 0
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
	Subsystem: Intel Corporation Device 4332
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: ff800000-ff8fffff
	Prefetchable memory behind bridge: f6a00000-f6afffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Intel Corporation 82801AA IDE Controller
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
	Subsystem: Intel Corporation 82801AA USB Controller
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at ef80 [size=32]
	Kernel driver in use: uhci_hcd

00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
	Subsystem: Intel Corporation 82801AA SMBus Controller
	Flags: medium devsel, IRQ 10
	I/O ports at efa0 [size=16]
	Kernel modules: i2c-i801

01:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
	Subsystem: Ensoniq ES1371 [AudioPCI-97]
	Flags: bus master, slow devsel, latency 64, IRQ 10
	I/O ports at df00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ENS1371
	Kernel modules: snd-ens1371

01:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
	Subsystem: Device 4554:434e
	Flags: bus master, medium devsel, latency 64, IRQ 3
	I/O ports at d800 [size=256]
	Memory at ff8f7c00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at f6a00000 [disabled] [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: dmfe
	Kernel modules: dmfe

01:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: Giga-byte Technology Device e934
	Flags: bus master, slow devsel, latency 64, IRQ 9
	Memory at ff8f8000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci

xoanan@ubuntu:~$ 

```

---

### Post by Xoanan on 2009-08-25
I don't do this very often.

BUMP

---

### Post by Xoanan on 2010-01-06
graphics issue resolved

---

