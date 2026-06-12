---
title: "Speaker not performing well"
date: 2010-10-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mahmoodkamal on 2010-10-01
I have Dell Inspiron 6000. my speaker sound is very bad, I cannot understand a word spoken if I run a video clip, with a lot of noise.


mahmood@mahmood-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mahmood@mahmood-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec38 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, fast devsel, latency 0
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at bf60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	Memory behind bridge: dfd00000-dfdfffff
	Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ed00 [size=256]
	I/O ports at ec40 [size=64]
	Memory at dfebfe00 (32-bit, non-prefetchable) [size=512]
	Memory at dfebfd00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
	Subsystem: Conexant Systems, Inc. Device 5423
	Flags: medium devsel, IRQ 17
	I/O ports at ee00 [size=256]
	I/O ports at ec80 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
	Subsystem: Dell Device 0188
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ahci

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 0188
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at dfdfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 168, IRQ 19
	Memory at dfd00000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 80000000-83fff000 (prefetchable)
	Memory window 1: 84000000-87fff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dfdfc800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17mahmood@mahmood-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mahmood@mahmood-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec38 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, fast devsel, latency 0
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at bf60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	Memory behind bridge: dfd00000-dfdfffff
	Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ed00 [size=256]
	I/O ports at ec40 [size=64]
	Memory at dfebfe00 (32-bit, non-prefetchable) [size=512]
	Memory at dfebfd00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
	Subsystem: Conexant Systems, Inc. Device 5423
	Flags: medium devsel, IRQ 17
	I/O ports at ee00 [size=256]
	I/O ports at ec80 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
	Subsystem: Dell Device 0188
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ahci

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 0188
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at dfdfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 168, IRQ 19
	Memory at dfd00000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 80000000-83fff000 (prefetchable)
	Memory window 1: 84000000-87fff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dfdfc800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17) (prog-if 01)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at dfdfc700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 2722
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at dfdfd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

mahmood@mahmood-laptop:~$ 
) (prog-if 01)
	Subsystem: Dell Device 0188
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at dfdfc700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 2722
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at dfdfd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

mahmood@mahmood-laptop:~$

---

### Post by ptptaylor on 2010-10-02
If you plug in headphones do you experience the same low performance? 
It could be a damaged speaker. Also have you tried in a different environment eg windows?

---

### Post by mahmoodkamal on 2010-10-02
yes, the problem is same with headphones.

---

