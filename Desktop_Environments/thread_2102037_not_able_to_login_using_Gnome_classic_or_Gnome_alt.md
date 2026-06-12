---
title: "not able to login using Gnome classic or Gnome although Gnome with no effects"
date: 2013-01-06
forum: Desktop Environments
---

### Post by howhy on 2013-01-06
Well i was working on maya when suddenly my keyboard and mouse stopped responding so i had to press the system reset button. After that i recovered my system using fsck.

I even tried rm -rf .gnome/.gconfd from my home directory in a virtual teminal (by pressing CTRL + ALT+F1)

But I still was not able to login with Gnome classic or just gnome selected, however if i change desktop environment to Gnome with no effects or unity everything works fine...

What might be wrong , since I am new to Ubuntu and still learning I need some help to get back to Gnome classic. Even Gnome with no effects is fine but I do not like the close, minimize and restore button on the left ..

---

### Post by Frogs Hair on 2013-01-06
> Well i was working on maya

Are you using Mint or Ubuntu ? They are not identical though Mint is Ubuntu based.

---

### Post by howhy on 2013-01-06
> **Frogs Hair said:**
> Are you using Mint or Ubuntu ? They are not identical though Mint is Ubuntu based.
I am using Ubuntu 12.04...

---

### Post by Frogs Hair on 2013-01-06
Sorry, I thinking Mint Maya . Are you able to use Ubuntu or Ubuntu 2D . I ask because 2D doesn't use Compiz. What is the output of ```
lspci -v
```

---

### Post by howhy on 2013-01-07
> **Frogs Hair said:**
> Sorry, I thinking Mint Maya . Are you able to use Ubuntu or Ubuntu 2D . I ask because 2D doesn't use Compiz. What is the output of ```
lspci -v
```

```
howhy@UbuntuDesk:~$ lspci -v
00:00.0 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: NVIDIA Corporation MCP55 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: NVIDIA Corporation MCP55 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: nv_tco, i2c-nforce2

00:01.2 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: 66MHz, fast devsel

00:02.0 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 IDE interface: NVIDIA Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:05.0 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at dc00 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:05.1 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:05.2 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at c400 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at bc00 [size=8]
	I/O ports at b800 [size=4]
	I/O ports at b400 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:06.0 PCI bridge: NVIDIA Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Capabilities: <access denied>

00:06.1 Audio device: NVIDIA Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81f6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:08.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 46
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at b000 [size=8]
	Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Memory at fe028000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0a.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0b.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0c.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0d.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0e.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0f.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

07:00.0 VGA compatible controller: NVIDIA Corporation G80 [GeForce 8800 GTS] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: BFG Tech Device 040f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ac00 [size=128]
	[virtual] Expansion ROM at fbfe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_173, nvidia_current, nouveau, nvidiafb

``` with maya I meant 3d modeling software Autodesk Maya ;)

---

