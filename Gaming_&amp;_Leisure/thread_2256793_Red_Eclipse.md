---
title: "Red Eclipse"
date: 2014-12-14
forum: Gaming &amp; Leisure
---

### Post by kccv42 on 2014-12-14
How is Red Eclipse? Does it run well?

---

### Post by oldrocker99 on 2014-12-15
You did already ask that question in your "What is the best game for Linux?" thread. It is somewhat frowned upon to duplicate posts here.

---

### Post by kccv42 on 2014-12-15
I just want to know if it runs smooth.

I also editied my other post in the other thread so that it would not be a duplicate.

---

### Post by oldrocker99 on 2014-12-15
Red Eclipse should run just fine on practically every computer made in the past three years, and probably a lot of older machines as well. We have no idea of what your rig is. Please post the output of
```
lspci -v
```
Then you can get some more specific advice. On a 2011 post on Red Eclipse's forum, they say that the requirements are pretty minimal (512MB RAM, Intel Pentium 4 or equivalent, and 32MB of video ram--there are cell phones much more powerful than that).

So yeah, it should run like a race horse.

---

### Post by kccv42 on 2014-12-15
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 90200000-903fffff
    Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
    Capabilities: <access denied>

00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 90100000-901fffff
    Prefetchable memory behind bridge: 0000000090500000-00000000906fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 90700000-907fffff
    Prefetchable memory behind bridge: 0000000090000000-00000000900fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at 4038 [size=8]
    I/O ports at 404c [size=4]
    I/O ports at 4030 [size=8]
    I/O ports at 4048 [size=4]
    I/O ports at 4010 [size=16]
    Memory at 90408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at 90407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at 90408600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at 90406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at 90408500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: 66MHz, medium devsel

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at 90400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at 90405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at 90404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at 90408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at 90300000 (32-bit, non-prefetchable) [size=64K]
    Memory at 90200000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon

02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Hewlett-Packard Company U98Z062.12 802.11bgn Wireless Half-size Mini PCIe Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 90100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1604
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at 2000 [size=256]
    Memory at 90010000 (64-bit, prefetchable) [size=4K]
    Memory at 90000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 90020000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

```

---

### Post by oldrocker99 on 2014-12-15
OK, what you have is a Mobility Radeon 4225/4250, which is supported (pretty well) with the open-source 'radeon' driver. It is likely already installed on your system. I'd give Red Eclipse a shot, if I were you.

---

### Post by kccv42 on 2014-12-15
Ok. Is the Mobility Radeon 4225/4250 a decent graphic card for instensive gaming like black ops?

---

### Post by kostkon on 2014-12-15
> **kccv42 said:**
> Ok. Is the Mobility Radeon 4225/4250 a decent graphic card for instensive gaming like black ops?
Unfortunately, no.

For games like this, you need a desktop computer with a decent processor and graphics card.

---

### Post by kccv42 on 2014-12-16
What is a good graphic card?

---

### Post by oldrocker99 on 2014-12-17
If you have a desktop PC, you can't go very wrong with the nVidia 750ti, which is ~$140. It doesn't require an external power connector, and it's fast enough for nearly every game.

---

### Post by kccv42 on 2014-12-18
So i am basically screwed with a bad graghic card. How much memory does my card have?

---

