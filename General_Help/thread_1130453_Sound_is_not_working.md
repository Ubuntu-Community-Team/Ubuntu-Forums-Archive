---
title: "Sound is not working"
date: 2009-04-19
forum: General Help
---

### Post by Bill Roberts on 2009-04-19
Sound was working with the integrated audio on my motherboard, but quit working after a reboot.  I had not changed any settings at the time it quit working.

I have tried different speakers and a new sound card, but nothing has helped.  

I'm stuck.

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [94] HyperTransport: #1a
	Capabilities: [60] HyperTransport: Retry Mode
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [d0] HyperTransport: #1c

00:01.0 ISA bridge: nVidia Corporation Device 075d (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 2f00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 2900 [size=64]
	I/O ports at 2d00 [size=64]
	I/O ports at 2e00 [size=64]
	Capabilities: [44] Power Management version 2

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f8d80000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f8d7f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f8d7ec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=00a0
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f8d7d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f8d7e800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=00a0
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f462:7374
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: pata_amd
	Kernel modules: pata_acpi, pata_amd, ata_generic

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f8e00000-f8efffff
	Capabilities: [b8] Subsystem: Micro-Star International Co., Ltd. Device 7374
	Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-

00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2299
	I/O ports at a080 [size=8]
	I/O ports at a000 [size=4]
	I/O ports at 9c00 [size=8]
	I/O ports at 9880 [size=4]
	I/O ports at 9800 [size=16]
	Memory at f8d7a000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [44] Power Management version 2
	Capabilities: [8c] SATA HBA <?>
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
	Capabilities: [ec] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: ahci
	Kernel modules: pata_acpi, ahci, ata_generic

00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2298
	Memory at f8d7c000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 9480 [size=8]
	Memory at f8d7e400 (32-bit, non-prefetchable) [size=256]
	Memory at f8d7e000 (32-bit, non-prefetchable) [size=16]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/4 Enable+
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f8f00000-f9ffffff
	Prefetchable memory behind bridge: 00000000be000000-00000000cfffffff
	Capabilities: [40] Subsystem: Micro-Star International Co., Ltd. Device 7374
	Capabilities: [48] Power Management version 2
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
	Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Subsystem: Micro-Star International Co., Ltd. Device 7374
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Subsystem: Micro-Star International Co., Ltd. Device 7374
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:13.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Capabilities: [40] Subsystem: Micro-Star International Co., Ltd. Device 7374
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: [40] Subsystem: Micro-Star International Co., Ltd. Device 7374
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

01:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 1014
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at bc00 [size=32]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0) (prog-if 10)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f8eff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at b880 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

02:00.0 VGA compatible controller: nVidia Corporation Device 084d (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7374
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at be000000 (64-bit, prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at f8fe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 0960
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at feae0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

05:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 01)
	Subsystem: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at febfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [68] Power Management version 2
	Capabilities: [50] Express Legacy Endpoint, MSI 01
	Kernel driver in use: ahci
	Kernel modules: ahci

05:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=16]
	Capabilities: [68] Power Management version 2
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_acpi, ata_generic, pata_jmicron

---

### Post by rob356 on 2009-04-19
Not trying to make you look stupid :D but have you made sure that ALL the channels in the audio mixer are unmuted and turned up? You can do that by right clicking on the audio icon next to the time and selecting volume control. I had the same problem where an obscure channel got muted on reboot.

---

