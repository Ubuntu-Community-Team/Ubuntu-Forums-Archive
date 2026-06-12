---
title: "FlightGear Freezes upon Startup and Hangs up Computer"
date: 2010-07-10
forum: Gaming &amp; Leisure
---

### Post by dale6998 on 2010-07-10
Hey All,

I just downloaded flightgear, and freshly installed Ubuntu 10 and all the updates that Ubuntu suggested.  Whenever I click on Flightgear from the games menu, some real blocky garbled output shows up on screen, and the computer becomes unresponsive.  I have to do a hard shutdown (ouch!)...

Here's the output of lspci -v

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
    Subsystem: Hewlett-Packard Company Device 2a00
    Flags: bus master, fast devsel, latency 0
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
    Subsystem: Hewlett-Packard Company Device 2a00
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Memory at d8200000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>
    Kernel modules: i915

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a01
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a01
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a01
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 2a01
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d8280000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: d8000000-d80fffff
    Prefetchable memory behind bridge: d8100000-d81fffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 2a01
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f000 [size=16]
    Memory at 80000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a01
    Flags: medium devsel, IRQ 255
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a02
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at e000 [size=256]
    I/O ports at e400 [size=64]
    Memory at d8281000 (32-bit, non-prefetchable) [size=512]
    Memory at d8282000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46) (prog-if 10)
    Subsystem: VIA Technologies, Inc. Device e8e9
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at d8000000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at c000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

01:0a.0 Communication controller: 3Com Corp, Modem Division WinModem
    Subsystem: 3Com Corp, Modem Division Device 0081
    Flags: medium devsel, IRQ 255
    Memory at d8118000 (32-bit, prefetchable) [size=64]
    Memory at d8100000 (32-bit, prefetchable) [size=64K]
    Memory at d8110000 (32-bit, prefetchable) [size=32K]
    Capabilities: <access denied>

01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 2a01
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at c400 [size=256]
    Memory at d8001000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp




Any ideas?
Thanks

---

