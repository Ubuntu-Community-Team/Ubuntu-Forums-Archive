---
title: "Usb support on Nvidia NForce chipset"
date: 2006-03-01
forum: Desktop Environments
---

### Post by delmonte on 2006-03-01
Greeting all

I've got a annoying problem. I'm running ubunti 5.10 with a 32 bit kernel (2.6.12-10-386) install on my AMD64 Shuttle case with a multi flash card reader on the front. Have got accelerated graphic, sound and network working without a flaw but no USB working at all.

with lsusb i receive not output.

lspci give me the following:
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 358 5
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 358 5
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 358 5
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at e700 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <available only to root>

0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 358 5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at ec000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e200 [size=8]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00e a (rev a1)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 358 5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at e300 [size=256]
        I/O ports at e400 [size=128]
        Memory at ec001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2) (pr og-if 8a [Master SecP PriP])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 358 5
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        Memory behind bridge: e8000000-eaffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: eb000000-ebffffff

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f1 (rev a2) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248,  IRQ 16
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

0000:02:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 46) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at eb000000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at d000 [size=128]
        Capabilities: <available only to root>

I'm kind of puzzled why it's not working...

Any idea?

Thanks for the help

Math

---

