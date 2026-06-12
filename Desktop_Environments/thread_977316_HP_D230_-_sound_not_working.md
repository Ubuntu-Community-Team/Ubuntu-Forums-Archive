---
title: "HP D230 - sound not working"
date: 2008-11-10
forum: Desktop Environments
---

### Post by carlo bolzonello on 2008-11-10
Hello all, 

i have installed 8.10 on a HP D230 desktop, however the sound does not work.Its is on board and a sound max I have run the  following command, lspci -v

the following is the output:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
	Subsystem: GVC/BCM Advanced Research Device 2179
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
	Subsystem: GVC/BCM Advanced Research Device 2179
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
	Subsystem: GVC/BCM Advanced Research Device 2179
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e400 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
	Subsystem: GVC/BCM Advanced Research Device 2179
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
	Subsystem: GVC/BCM Advanced Research Device 2179
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ec00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: GVC/BCM Advanced Research Device 2179
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dff7bc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dfd00000-dfdfffff
	Prefetchable memory behind bridge: 30000000-300fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: GVC/BCM Advanced Research Device 2179
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at fc00 [size=16]
	Memory at 30100000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
	Subsystem: GVC/BCM Advanced Research Device 2179
	Flags: medium devsel, IRQ 11
	I/O ports at 0c00 [size=32]
	Kernel modules: i2c-i801

03:0a.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
	Subsystem: GVC/BCM Advanced Research Device 2179
	Flags: bus master, fast devsel, latency 32, IRQ 19
	Memory at dfdfe000 (32-bit, non-prefetchable) [size=8K]
	Expansion ROM at 30000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

03:0d.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 10)
	Subsystem: Intel Corporation Device 0070
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at dfdfc000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at dc00 [size=64]
	Memory at dfd80000 (32-bit, non-prefetchable) [size=128K]
	Expansion ROM at 30020000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100, eepro100

i than ran the following aplay -l and received the following output:
aplay: device_list:215: no soundcards found...

can anyone help please

---

### Post by carlo bolzonello on 2008-11-14
hello all,

i have opend a bug report for this, Ubunutu will fix it soon i hope. :)

---

