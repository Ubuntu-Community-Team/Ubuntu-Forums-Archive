---
title: "USB Ports Not Working"
date: 2008-12-06
forum: Desktop Environments
---

### Post by gsv_ on 2008-12-06
USB ports simply don't work at all. Here are my system details: 

```

root@ubuntu:~# lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 2a26
	Kernel modules: shpchp

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at bc000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil, pata_acpi, ata_generic

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: 66MHz, medium devsel
	Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: 66MHz, medium devsel
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: 66MHz, medium devsel
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: bus master, 66MHz, medium devsel, latency 64
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f900 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_acpi, ata_generic, pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01)
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 2a27
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 5
	Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ATI IXP AC97 controller
	Kernel modules: snd-atiixp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at ee00 [size=256]
	Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fde00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at dc00 [size=256]
	Memory at fddff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too

02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 2a26
	Flags: bus master, stepping, medium devsel, latency 64
	Memory at fddfe000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at df00 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel modules: ohci1394

02:09.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
	Subsystem: Motorola Device 3020
	Flags: bus master, stepping, medium devsel, latency 64
	Memory at fddfd000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at da00 [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: serial

root@ubuntu:~# 

```


```

root@ubuntu:~# uname -a
Linux ubuntu 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
root@ubuntu:~# 

```

```

root@ubuntu:~# dmesg|grep -i usb
[    1.268169] usbcore: registered new interface driver usbfs
[    1.268241] usbcore: registered new interface driver hub
[    1.277310] usbcore: registered new device driver usb
[    1.313941] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
root@ubuntu:~# 

```

So basically I have an ATI SB400 Chipset...any ideas?

---

### Post by gsv_ on 2008-12-07
I really hate to bump, but does nobody know the answer to this? 

I've spent hours on this issue, and I'm just sick of this.

And if it helps at all, I have an EXE file for Windows that installs the necessary drivers, and can probably get the 'raw' driver files as well...

---

### Post by android6011 on 2009-01-04
bump...

ive had the same problem with the last 3 ubuntu releases ive tried, as well as the latest slackware, fedora and opensuse.

any ideas anyone?

---

### Post by SysKoll on 2009-10-11
Same problem here with a Compaq PC equipped with the same chipset. In my own lspci -v output, I have exactly the same USB controller, and lshw shows it to me as UNCLAIMED, meaning, I think, that no driver is controlling it.

Ubuntu folks, USB is not working on machines equipped with the ATI SB400 chipset!

EDIT: I checked the BIOS and a more recent version was available. I updated the BIOS, and joy, the USB now works!

---

