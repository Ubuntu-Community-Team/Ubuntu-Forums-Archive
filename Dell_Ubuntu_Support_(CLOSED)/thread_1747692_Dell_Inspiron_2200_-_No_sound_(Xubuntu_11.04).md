---
title: "Dell Inspiron 2200 - No sound (Xubuntu 11.04)"
date: 2011-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by blind486 on 2011-05-02
Hi guys, New here and New to Ubuntu. I just revived this old laptop and used Xubuntu 11.04 to make it lightweight. My problem is it doesn't have sounds on, I've already max out the mixers.

Here are my specs:

Dell Inspiron 2200

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
    Subsystem: Dell Device 01a4
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 01a4
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ec38 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Dell Device 01a4
    Flags: bus master, fast devsel, latency 0
    Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01a4
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at bf80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01a4
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at bf60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01a4
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at bf40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01a4
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at bf20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
    Subsystem: Dell Device 01a4
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dfd00000-dfdfffff
    Prefetchable memory behind bridge: 0000000020000000-0000000023ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
    Subsystem: Dell Device 01a4
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 01a4
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at bfa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 01a4
    Flags: medium devsel, IRQ 10
    I/O ports at 10c0 [size=32]
    Kernel modules: i2c-i801

02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
    Subsystem: Dell Device 01a4
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at dfd00000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: 24000000-27fff000
    I/O window 0: 0000d000-0000d0ff
    I/O window 1: 0000d400-0000d4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
    Subsystem: Dell Device 01a4
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at dfdff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at df40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

```Hope i get a reply and thanks.

---

### Post by wb8dxx on 2011-06-29
I had the same problem. I found out that the sound preferences dialog defaults to output muted. Try opening Preferences->Sound and checking to see if the Output volume box at the top of the form is checked.

HTH

---

