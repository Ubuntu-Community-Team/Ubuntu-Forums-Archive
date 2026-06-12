---
title: "Dell to Monitor Help"
date: 2010-12-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by msnmatt08 on 2010-12-23
I'm running a Dell Inspiron 1210 with Ubuntu 10.10 on it. I have a Magnavox tv that I use as a monitor, it has a PC mode. I connect the 2 using a VGA cable. I had no problems with it reading my monitor when I had Windows but I just switched to Linux. Now that I have switched, it can't pick my monitor up. Any ideas why?

Here's my lspci -v output:

00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
    Subsystem: Dell Device 02b1
    Flags: bus master, fast devsel, latency 0

[B]00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 02b1
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at d8100000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at d0000000 (32-bit, non-prefetchable) [size=128M]
    Memory at d8380000 (32-bit, non-prefetchable) [size=128K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>[/B]

00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
    Subsystem: Dell Device 02b1
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d83a0000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 3f800000-3fbfffff
    Prefetchable memory behind bridge: d8400000-d84fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d8000000-d80fffff
    Prefetchable memory behind bridge: 3fc00000-3fdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07) (prog-if 00 [UHCI])
    Subsystem: Dell Device 02b1
    Flags: bus master, fast devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07) (prog-if 00 [UHCI])
    Subsystem: Dell Device 02b1
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07) (prog-if 00 [UHCI])
    Subsystem: Dell Device 02b1
    Flags: bus master, fast devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07) (prog-if 20 [EHCI])
    Subsystem: Dell Device 02b1
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at d83a4000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
    Subsystem: Dell Device 02b1
    Flags: fast devsel
    Kernel modules: lpc_sch

00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07) (prog-if 80 [Master])
    Subsystem: Dell Device 02b1
    Flags: bus master, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: pata_sch
    Kernel modules: pata_sch

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Dell Device 02b1
    Flags: bus master, fast devsel, latency 0, IRQ 40
    I/O ports at 2000 [size=256]
    Memory at d8410000 (64-bit, prefetchable) [size=4K]
    Memory at d8400000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at d8420000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Broadcom Corporation Device 04b5
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d8000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb



Thanks in advance.

---

### Post by mikewhatever on 2010-12-24
The thread is marked as solved so that I hope you've found a solution. Intel doesn't support gma500 on Linux and I wouldn't be too surprised if it didn't work. I remember once having to run **xrandr --auto** to activate the hdmi ouput, not sure if it works for VGA.

---

