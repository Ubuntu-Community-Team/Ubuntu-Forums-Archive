---
title: "usb dvd writer driver needed"
date: 2010-10-11
forum: Desktop Environments
---

### Post by tapas_mishra on 2010-10-11
I am having a USB DVD writer 
not sure in lspci output which one is pointing to that here is the complete output of lspci -vnn
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f6c00000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at efe8 [size=8]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, fast devsel, latency 0
    Memory at f6b00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6f60 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6f80 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 6fa0 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) (prog-if 20)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: c0000000-c01fffff
    Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Dell Device [1028:02cf]
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f6900000-f69fffff
    Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Dell Device [1028:02cf]
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f6800000-f68fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Dell Device [1028:02cf]
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f6600000-f67fffff
    Prefetchable memory behind bridge: 00000000f0100000-00000000f03fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Dell Device [1028:02cf]
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6f00 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6f20 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 6f40 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) (prog-if 20)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Capabilities: [50] Subsystem: Dell Device [1028:02cf]

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:2928] (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device [1028:02cf]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
    I/O ports at 6e70 [size=8]
    I/O ports at 6e78 [size=4]
    I/O ports at 6e80 [size=8]
    I/O ports at 6e88 [size=4]
    I/O ports at 6ea0 [size=16]
    I/O ports at 6e90 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCIe advanced features <?>
    Kernel driver in use: ata_piix



```Which one of the above is pointing to USB Dvd write so that I search the driver for it?

---

### Post by Elaztic on 2010-10-11
Hi.

If you want to see an USB device you should use the command

```
lsusb
```

instead of ```
lspci
```.

Are you sure you need a driver an not just need to mount it via /etc/fstab?

You might want to have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=764146]("http://ubuntuforums.org/showthread.php?t=764146")

---

### Post by tapas_mishra on 2010-10-11
I looked at that thread after three four discussions there is nothing in it./etc/fstab would be required to edit if I always want the device to be automounted which is not the case.
I plugged in the USB DVD writer and then unplugged it in both cases stored the output of lsusb the difference is 
```

13fd:1640 Initio Corporation
```
This should be my DVD writer.What driver I need for this to work?

---

