---
title: "System keeps locking up, top says &quot;Xorg&quot; is doing it"
date: 2009-04-28
forum: General Help
---

### Post by tegnoto89 on 2009-04-28
What is xorg and how can I fix this?

---

### Post by tommcd on 2009-04-28
Xorg enables the graphical desktop. 
Please post the motherboard chipset and the video chipset your computer uses.  If you do not know this stuff then open a terminal and run:
```
lspci -v
```
and post the output here.

Also post the version of Ubuntu you are using. 

Have you installed any drivers for your video card? And what video card do you have?

You really need to post more info than just a half sentence blurb if you really want useful help.

---

### Post by tegnoto89 on 2009-04-28
lspci -v:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0000000-d2ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0, IRQ 215
	Memory at fe200000 (32-bit, non-prefetchable) [size=128K]
	Memory at fe225000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1840 [size=32]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1860 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T60
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fe226c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fe220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: dc100000-df2fffff
	Prefetchable memory behind bridge: 00000000dfd00000-00000000dfdfffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d4000000-d7dfffff
	Prefetchable memory behind bridge: 00000000dfa00000-00000000dfafffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d8000000-d9ffffff
	Prefetchable memory behind bridge: 00000000df700000-00000000df7fffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=14, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: cc000000-cdffffff
	Prefetchable memory behind bridge: 00000000df400000-00000000df4fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 18a0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 18c0 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 18e0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe227000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
	I/O behind bridge: 00008000-0000bfff
	Memory behind bridge: f8100000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
	Subsystem: Lenovo Unknown device 20b6
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1830 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 217
	I/O ports at 1c48 [size=8]
	I/O ports at 1c1c [size=4]
	I/O ports at 1c40 [size=8]
	I/O ports at 1c18 [size=4]
	I/O ports at 1c20 [size=32]
	Memory at fe226000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Lenovo ThinkPad T61
	Flags: medium devsel, IRQ 11
	Memory at fe227400 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c60 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
	Subsystem: Intel Corporation Turbo Memory Controller
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at df2ffc00 (32-bit, non-prefetchable) [size=1K]
	I/O ports at 3000 [size=128]
	[virtual] Expansion ROM at dfd00000 [disabled] [size=64K]
	Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Lenovo ThinkPad T51
	Flags: bus master, fast devsel, latency 0, IRQ 216
	Memory at d7dfe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
	Subsystem: Lenovo Unknown device 20c6
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at f8100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
	Memory window 0: f4000000-f7fff000 (prefetchable)
	Memory window 1: c0000000-c3fff000
	I/O window 0: 00008000-000080ff
	I/O window 1: 00008400-000084ff
	16-bit legacy interface ports at 0001

15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) (prog-if 10 [OHCI])
	Subsystem: Lenovo Unknown device 20c7
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at f8101000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
	Subsystem: Lenovo Unknown device 20c8
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at f8101800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
	Subsystem: Lenovo Unknown device 20c9
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at f8101c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
	Subsystem: Lenovo Unknown device 20ca
	Flags: medium devsel, IRQ 11
	Memory at f8102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
	Subsystem: Lenovo Unknown device 20cb
	Flags: medium devsel, IRQ 11
	Memory at f8102400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```


I'm not sure what video card I have...  How can I find that out?  And I'm using Hardy.

---

