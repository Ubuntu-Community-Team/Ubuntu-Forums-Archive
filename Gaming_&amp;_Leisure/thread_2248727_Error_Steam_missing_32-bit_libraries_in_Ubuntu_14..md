---
title: "Error: Steam missing 32-bit libraries in Ubuntu 14.04 64-bit"
date: 2014-10-16
forum: Gaming &amp; Leisure
---

### Post by Jere_Tuominen on 2014-10-16
```
ERROR
You are missing the following 32-bit libraries, and Steam may not run:
libXtst.so.6
libXrandr.so.2
libpangoft2-1.0.so.0
libpangocairo-1.0.so.0
libatk-1.0.so.0
libcairo.so.2
libpangoft2-1.0.so.0
libtiff.so.4
libbz2.so.1.0
libpangocairo-1.0.so.0
libXrandr.so.2
libcairo.so.2


```

Hi,

I've installed Steam through "Ubuntu After Install" software. When I try to run Steam I get the error shown above. I have tried the following forum threads without success. The missing libraries list has got a little shorter, but not all gone. What to do?

[http://ubuntuforums.org/showthread.php?t=2233005](http://ubuntuforums.org/showthread.php?t=2233005)
[http://ubuntuforums.org/showthread.php?t=2242632](http://ubuntuforums.org/showthread.php?t=2242632)

My computer setup:
Computer: Lenovo Thinkpad T61
Memory: 1,9 GiB
Processor: Intel Core 2 Duo CPU T7500 @ 2.20GHz x 2
Graphics: Quadro NVS 140M/PCIe/SSE2
OS type: 64-bit
Harddisk: 115,9 Gt

Thanks for your support!

---

### Post by dannyboy79 on 2014-10-16
first let's see what graphics card you have and what driver you're using. what does this command return?
```
sudo lspci -v
```
and
```
sudo lshw -C video
```

---

### Post by Jere_Tuominen on 2014-10-17
sudo lspci -v

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0a <?>


00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d4000000-d6ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: [88] Subsystem: Lenovo Device 20b2
	Capabilities: [80] Power Management version 3
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [140] Root Complex Link
	Kernel driver in use: pcieport


00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fe200000 (32-bit, non-prefetchable) [size=128K]
	Memory at fe225000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1840 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Kernel driver in use: e1000e


00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd


00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo Thinkpad T61/R61
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd


00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fe226c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: ehci-pci


00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at fe220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo ThinkPad T61/R61
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport


00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: dc100000-df2fffff
	Prefetchable memory behind bridge: 00000000dfd00000-00000000dfdfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo ThinkPad T61/R61
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport


00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d8000000-d9ffffff
	Prefetchable memory behind bridge: 00000000dfa00000-00000000dfafffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo ThinkPad T61/R61
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport


00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d0000000-d1ffffff
	Prefetchable memory behind bridge: 00000000df700000-00000000df7fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo ThinkPad T61/R61
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport


00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=14, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: cc000000-cdffffff
	Prefetchable memory behind bridge: 00000000df400000-00000000df4fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo ThinkPad T61/R61
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport


00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 18a0 [size=32]
	Kernel driver in use: uhci_hcd


00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 18c0 [size=32]
	Kernel driver in use: uhci_hcd


00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18e0 [size=32]
	Kernel driver in use: uhci_hcd


00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fe227000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci-pci


00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
	I/O behind bridge: 00008000-0000bfff
	Memory behind bridge: f8100000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
	Capabilities: [50] Subsystem: Lenovo ThinkPad T61/R61


00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 03)
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: lpc_ich


00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4
	I/O ports at 0170 [size=8]
	I/O ports at 0374
	I/O ports at 1830 [size=16]
	Kernel driver in use: ata_piix


00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 47
	I/O ports at 1c48 [size=8]
	I/O ports at 1c1c [size=4]
	I/O ports at 1c40 [size=8]
	I/O ports at 1c18 [size=4]
	I/O ports at 1c20 [size=32]
	Memory at fe226000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/4 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Kernel driver in use: ahci


00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Lenovo ThinkPad T61/R61
	Flags: medium devsel, IRQ 11
	Memory at fe227400 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c60 [size=32]


01:00.0 VGA compatible controller: NVIDIA Corporation G86M [Quadro NVS 140M] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at d6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at d4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia


03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1011
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at df2fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-1f-3b-ff-ff-8b-2a-3f
	Kernel driver in use: iwl4965


15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
	Subsystem: Lenovo ThinkPad R61
	Physical Slot: 1
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at f8100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
	Memory window 0: f4000000-f7ffffff (prefetchable)
	Memory window 1: 80000000-83ffffff
	I/O window 0: 00008000-000080ff
	I/O window 1: 00008400-000084ff
	16-bit legacy interface ports at 0001
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: yenta_cardbus


15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) (prog-if 10 [OHCI])
	Subsystem: Lenovo ThinkPad R61
	Physical Slot: 1
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at f8101000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: firewire_ohci



```

sudo lshw -C video

```

  *-display               
       description: VGA compatible controller
       product: G86M [Quadro NVS 140M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:50 memory:d6000000-d6ffffff memory:e0000000-efffffff memory:d4000000-d5ffffff ioport:2000(size=128)

```

---

### Post by MikeCyber on 2014-10-17
I would remove and install the installer from the steam website. But your card might be to weak/old, why not update your system?

---

### Post by oldrocker99 on 2014-10-17
I have had some Steam launcher problems when I used the Ubuntu Software Center, but not when I downloaded the client form steampowered.com.

---

### Post by R33D3M33R on 2014-10-17
@Jere_Tuominen: look at this thread: [http://ubuntuforums.org/showthread.php?t=2241926](http://ubuntuforums.org/showthread.php?t=2241926)
I would suggest following the given advices and install from website.

---

