---
title: "Problems with startx using an MGA G200eW WPCM450"
date: 2014-05-22
forum: Desktop Environments
---

### Post by Alec_Olson on 2014-05-22
Hi there,
We have been running an Ubuntu Server and I have been trying to get the Ubuntu Desktop using Xforwading. We are able to run other programs using Xforwarding, so it seems to be a problem with startx.  I've tied to solve this problem on my own, but I can't figure it out.  If you have any questions let me know.

Output of:

startx:
```


X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux JH-T610 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=/dev/mapper/raid1-root ro quiet
Build Date: 16 April 2014  01:36:29PM
xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.30.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu May 22 12:37:52 2014
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension Present
Initializing built-in extension DRI3
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
xf86TokenToOptinfo: table is NULL
xf86TokenToOptinfo: table is NULL
```

sudo lspci -v:
```

00:00.0 Host bridge: Intel Corporation 5520 I/O Hub to ESI Port (rev 13)    Subsystem: Dell Device 0237
    Flags: fast devsel, IRQ 15
    Capabilities: [60] MSI: Enable- Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot-), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Access Control Services
    Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>


00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: da000000-ddffffff
    Capabilities: [40] Subsystem: Dell Device 0237
    Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot-), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Access Control Services
    Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
    Kernel driver in use: pcieport


00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: [40] Subsystem: Dell Device 0237
    Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot+), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Access Control Services
    Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
    Kernel driver in use: pcieport


00:04.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 4 (rev 13) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: [40] Subsystem: Dell Device 0237
    Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot+), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Access Control Services
    Kernel driver in use: pcieport


00:05.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 5 (rev 13) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: [40] Subsystem: Dell Device 0237
    Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot+), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Access Control Services
    Kernel driver in use: pcieport


00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: [40] Subsystem: Dell Device 0237
    Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot+), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Access Control Services
    Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
    Kernel driver in use: pcieport


00:09.0 PCI bridge: Intel Corporation 7500/5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 13) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Capabilities: [40] Subsystem: Dell Device 0237
    Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot+), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Access Control Services
    Kernel driver in use: pcieport


00:0a.0 PCI bridge: Intel Corporation 7500/5520/5500/X58 I/O Hub PCI Express Root Port 10 (rev 13) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000f000-0000ffff
    Memory behind bridge: df100000-df1fffff
    Capabilities: [40] Subsystem: Dell Device 0237
    Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot-), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Access Control Services
    Kernel driver in use: pcieport


00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 13) (prog-if 00 [8259])
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: i7core_edac


00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13) (prog-if 00 [8259])
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00


00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13) (prog-if 00 [8259])
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00


00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell PowerEdge T610 USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ec40 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd


00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell PowerEdge T610 USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ec60 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd


00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell PowerEdge T610 USB EHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at df0fe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci


00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell PowerEdge T610 USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at ec80 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd


00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell PowerEdge T610 USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at eca0 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd


00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell PowerEdge T610 USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at ecc0 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd


00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell PowerEdge T610 USB UHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at ece0 [size=32]
    Capabilities: [50] PCI Advanced Features
    Kernel driver in use: uhci_hcd


00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell PowerEdge T610 USB EHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at df0ff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci


00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
    Memory behind bridge: de000000-deffffff
    Prefetchable memory behind bridge: 00000000d9800000-00000000d9ffffff
    Capabilities: [50] Subsystem: Dell Device 0237


00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
    Subsystem: Dell Device 0237
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich


00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA Controller [IDE mode] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell PowerEdge T610 SATA IDE Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23
    I/O ports at ec10 [size=8]
    I/O ports at ec08 [size=4]
    I/O ports at ec18 [size=8]
    I/O ports at ec0c [size=4]
    I/O ports at ec20 [size=16]
    I/O ports at ec30 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ata_piix


01:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
    Subsystem: Dell PowerEdge T610 BCM5709 Gigabit Ethernet
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at da000000 (64-bit, non-prefetchable) [size=32M]
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Vital Product Data
    Capabilities: [58] MSI: Enable- Count=1/16 Maskable- 64bit+
    Capabilities: [a0] MSI-X: Enable+ Count=9 Masked-
    Capabilities: [ac] Express Endpoint, MSI 00
    Capabilities: [100] Device Serial Number 78-2b-cb-ff-fe-30-da-e2
    Capabilities: [110] Advanced Error Reporting
    Capabilities: [150] Power Budgeting <?>
    Capabilities: [160] Virtual Channel
    Kernel driver in use: bnx2


01:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
    Subsystem: Dell PowerEdge T610 BCM5709 Gigabit Ethernet
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at dc000000 (64-bit, non-prefetchable) [size=32M]
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Vital Product Data
    Capabilities: [58] MSI: Enable- Count=1/16 Maskable- 64bit+
    Capabilities: [a0] MSI-X: Enable+ Count=9 Masked-
    Capabilities: [ac] Express Endpoint, MSI 00
    Capabilities: [100] Device Serial Number 78-2b-cb-ff-fe-30-da-e4
    Capabilities: [110] Advanced Error Reporting
    Capabilities: [150] Power Budgeting <?>
    Capabilities: [160] Virtual Channel
    Kernel driver in use: bnx2


02:00.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS 2108 [Liberator] (rev 05)
    Subsystem: Dell PERC H700 Integrated
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at fc00 [size=256]
    Memory at df1bc000 (64-bit, non-prefetchable) [size=16K]
    Memory at df1c0000 (64-bit, non-prefetchable) [size=256K]
    Expansion ROM at df100000 [disabled] [size=256K]
    Capabilities: [50] Power Management version 3
    Capabilities: [68] Express Endpoint, MSI 00
    Capabilities: [d0] Vital Product Data
    Capabilities: [a8] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [c0] MSI-X: Enable+ Count=15 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [138] Power Budgeting <?>
    Kernel driver in use: megaraid_sas


08:03.0 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200eW WPCM450 (rev 0a) (prog-if 00 [VGA controller])
    Subsystem: Dell PowerEdge T610 MGA G200eW WPCM450
    Flags: bus master, medium devsel, latency 32, IRQ 10
    Memory at d9800000 (32-bit, prefetchable) [size=8M]
    Memory at de7fc000 (32-bit, non-prefetchable) [size=16K]
    Memory at de800000 (32-bit, non-prefetchable) [size=8M]
    [virtual] Expansion ROM at de000000 [disabled] [size=64K]
    Capabilities: [dc] Power Management version 1


fe:00.0 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:00.1 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:02.0 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:02.1 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:02.2 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:02.3 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 1 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:02.4 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 1 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:02.5 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 1 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:03.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:03.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Target Address Decoder (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:03.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller RAS Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:03.4 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Test Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:04.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:04.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Address (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:04.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Rank (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:04.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Thermal Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:05.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:05.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Address (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:05.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Rank (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:05.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Thermal Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:06.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:06.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Address (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:06.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Rank (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


fe:06.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Thermal Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:00.0 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:00.1 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:02.0 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:02.1 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:02.2 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:02.3 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 1 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:02.4 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 1 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:02.5 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 1 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:03.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:03.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Target Address Decoder (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:03.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller RAS Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:03.4 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Test Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:04.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:04.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Address (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:04.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Rank (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:04.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Thermal Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:05.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:05.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Address (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:05.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Rank (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:05.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Thermal Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:06.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:06.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Address (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:06.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Rank (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


ff:06.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Thermal Control (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0
```

Xorg.1.log:

```
[171655.210]X.Org X Server 1.15.1
Release Date: 2014-04-13
[171655.210] X Protocol Version 11, Revision 0
[171655.210] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[171655.210] Current Operating System: Linux JH-T610 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64
[171655.210] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=/dev/mapper/raid1-root ro quiet
[171655.210] Build Date: 16 April 2014  01:36:29PM
[171655.210] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support)
[171655.210] Current version of pixman: 0.30.2
[171655.210]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[171655.210] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[171655.210] (==) Log file: "/var/log/Xorg.1.log", Time: Thu May 22 12:37:52 2014
[171655.211] (==) Using config file: "/etc/X11/xorg.conf"
[171655.211] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[171655.211] (==) ServerLayout "X.org Configured"
[171655.211] (**) |-->Screen "Screen0" (0)
[171655.211] (**) |   |-->Monitor "Monitor0"
[171655.211] (**) |   |-->Device "Card0"
[171655.211] (**) |-->Input Device "Mouse0"
[171655.211] (**) |-->Input Device "Keyboard0"
[171655.211] (==) Automatically adding devices
[171655.211] (==) Automatically enabling devices
[171655.211] (==) Automatically adding GPU devices
[171655.211] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[171655.211]     Entry deleted from font path.
[171655.211] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[171655.211]     Entry deleted from font path.
[171655.211] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[171655.211]     Entry deleted from font path.
[171655.211] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[171655.211]     Entry deleted from font path.
[171655.211] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[171655.212]     Entry deleted from font path.
[171655.212] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[171655.212]     Entry deleted from font path.
[171655.212] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[171655.212]     Entry deleted from font path.
[171655.212] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[171655.212]     Entry deleted from font path.
[171655.212] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[171655.212]     Entry deleted from font path.
[171655.212] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[171655.212]     Entry deleted from font path.
[171655.212] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[171655.212] (**) ModulePath set to "/usr/lib/xorg/modules"
[171655.212] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[171655.212] (WW) Disabling Mouse0
[171655.212] (WW) Disabling Keyboard0
[171655.212] (II) Loader magic: 0x7f414c970d60
[171655.212] (II) Module ABI versions:
[171655.212]     X.Org ANSI C Emulation: 0.4
[171655.212]     X.Org Video Driver: 15.0
[171655.212]     X.Org XInput driver : 20.0
[171655.212]     X.Org Server Extension : 8.0
[171655.215] (--) PCI:*(0:8:3:0) 102b:0532:1028:0237 rev 10, Mem @ 0xd9800000/8388608, 0xde7fc000/16384, 0xde800000/8388608, BIOS @ 0x????????/65536
[171655.215] Initializing built-in extension Generic Event Extension
[171655.215] Initializing built-in extension SHAPE
[171655.215] Initializing built-in extension MIT-SHM
[171655.215] Initializing built-in extension XInputExtension
[171655.215] Initializing built-in extension XTEST
[171655.215] Initializing built-in extension BIG-REQUESTS
[171655.215] Initializing built-in extension SYNC
[171655.215] Initializing built-in extension XKEYBOARD
[171655.215] Initializing built-in extension XC-MISC
[171655.215] Initializing built-in extension SECURITY
[171655.215] Initializing built-in extension XINERAMA
[171655.215] Initializing built-in extension XFIXES
[171655.215] Initializing built-in extension RENDER
[171655.215] Initializing built-in extension RANDR
[171655.215] Initializing built-in extension COMPOSITE
[171655.215] Initializing built-in extension DAMAGE
[171655.215] Initializing built-in extension MIT-SCREEN-SAVER
[171655.215] Initializing built-in extension DOUBLE-BUFFER
[171655.215] Initializing built-in extension RECORD
[171655.215] Initializing built-in extension DPMS
[171655.215] Initializing built-in extension Present
[171655.215] Initializing built-in extension DRI3
[171655.215] Initializing built-in extension X-Resource
[171655.215] Initializing built-in extension XVideo
[171655.215] Initializing built-in extension XVideo-MotionCompensation
[171655.215] Initializing built-in extension SELinux
[171655.215] Initializing built-in extension XFree86-VidModeExtension
[171655.215] Initializing built-in extension XFree86-DGA
[171655.215] Initializing built-in extension XFree86-DRI
[171655.215] Initializing built-in extension DRI2
[171655.215] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[171655.215] (WW) "xmir" is not to be loaded by default. Skipping.
[171655.215] (II) LoadModule: "glx"
[171655.216] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[171655.216] (II) Module glx: vendor="X.Org Foundation"
[171655.216]     compiled for 1.15.1, module version = 1.0.0
[171655.216]     ABI class: X.Org Server Extension, version 8.0
[171655.216] (==) AIGLX enabled
[171655.216] Loading extension GLX
[171655.216] (II) LoadModule: "mga"
[171655.217] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[171655.217] (II) Module mga: vendor="X.Org Foundation"
[171655.217]     compiled for 1.15.0, module version = 1.6.3
[171655.217]     Module class: X.Org Video Driver
[171655.217]     ABI class: X.Org Video Driver, version 15.0
[171655.217] (II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
    mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
    mgag200 SE A PCI, mgag200 SE B PCI, mgag200 EV Maxim,
    mgag200 ER SH7757, mgag200 eW Nuvoton, mgag200eH, mgag400, mgag550
[171655.217] (--) using VT number 9


[171655.264] (II) Loading sub module "vgahw"
[171655.264] (II) LoadModule: "vgahw"
[171655.264] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[171655.264] (II) Module vgahw: vendor="X.Org Foundation"
[171655.264]     compiled for 1.15.1, module version = 0.1.0
[171655.264]     ABI class: X.Org Video Driver, version 15.0
[171655.264] (--) MGA(0): Chipset: "mgag200 eW Nuvoton"
[171655.264] (II) MGA(0): HW cursor is not supported with video redirection onG200 server chips.
 If you don't intend to use video redirection enable with Option "HWCursor" "On"
[171655.264] xf86TokenToOptinfo: table is NULL
[171655.264] xf86TokenToOptinfo: table is NULL
[171655.264] (==) MGA(0): Using SW cursor
[171655.264] (--) MGA(0): Linear framebuffer at 0xD9800000
[171655.264] (--) MGA(0): MMIO registers at 0xDE7FC000
[171655.264] (--) MGA(0): Pseudo-DMA transfer window at 0xDE800000
[171655.264] (II) MGA(0): MAPPED Framebuffer D9800000 800000 to 7F41457E9000.
[171655.264] (II) MGA(0): UNMAPPING framebuffer 0x7F41457E9000, 0x800000.
[171655.265] (II) MGA(0): MAPPED Framebuffer D9800000 800000 to 7F41457E9000.
[171655.298] (II) MGA(0): UNMAPPING framebuffer 0x7F41457E9000, 0x800000.
[171655.298] (**) MGA(0): Depth 16, (--) framebuffer bpp 16
[171655.298] (==) MGA(0): RGB weight 565
[171655.298] (**) MGA(0): Option "HWcursor" "off"
[171655.298] (**) MGA(0): Enabling KVM
[171655.298] (==) MGA(0): Using AGP 1x mode
[171655.298] (==) MGA(0): Using XAA acceleration
[171655.299] (--) MGA(0): Video BIOS info block at offset 0x07D40
[171655.299] (==) MGA(0): VideoRAM: 8128 kByte
[171655.299] (II) Loading sub module "ddc"
[171655.299] (II) LoadModule: "ddc"
[171655.299] (II) Module "ddc" already built-in
[171655.299] (II) Loading sub module "i2c"
[171655.299] (II) LoadModule: "i2c"
[171655.299] (II) Module "i2c" already built-in
[171655.299] (II) MGA(0): MAPPED Framebuffer D9800000 7f0000 to 7F41457F9000.
[171655.299] (II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[171655.301] (II) MGA(0): I2C bus "DDC P1" initialized.
[171655.301] (II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
[171655.304] (II) Loading sub module "vbe"
[171655.304] (II) LoadModule: "vbe"
[171655.304] (II) Loading /usr/lib/xorg/modules/libvbe.so
[171655.304] (II) Module vbe: vendor="X.Org Foundation"
[171655.304]     compiled for 1.15.1, module version = 1.1.0
[171655.304]     ABI class: X.Org Video Driver, version 15.0
[171655.304] (II) Loading sub module "int10"
[171655.304] (II) LoadModule: "int10"
[171655.304] (II) Loading /usr/lib/xorg/modules/libint10.so
[171655.305] (II) Module int10: vendor="X.Org Foundation"
[171655.305]     compiled for 1.15.1, module version = 1.0.0
[171655.305]     ABI class: X.Org Video Driver, version 15.0
[171655.305] (II) MGA(0): initializing int10
[171655.305] (II) MGA(0): Primary V_BIOS segment is: 0xc000
[171655.305] (II) MGA(0): VESA BIOS detected
[171655.305] (II) MGA(0): VESA VBE Version 3.0
[171655.305] (II) MGA(0): VESA VBE Total Mem: 8192 kB
[171655.305] (II) MGA(0): VESA VBE OEM: Matrox Graphics Inc.
[171655.305] (II) MGA(0): VESA VBE OEM Software Rev: 3.8
[171655.305] (II) MGA(0): VESA VBE OEM Vendor: Matrox
[171655.305] (II) MGA(0): VESA VBE OEM Product: MGA-G200
[171655.305] (II) MGA(0): VESA VBE OEM Product Rev: 00
[171655.349] (II) MGA(0): VESA VBE DDC supported
[171655.349] (II) MGA(0): VESA VBE DDC Level none
[171655.349] (II) MGA(0): VESA VBE DDC transfer in appr. 0 sec.
[171655.392] (II) MGA(0): VESA VBE DDC read failed
[171655.729] (II) MGA(0): UNMAPPING framebuffer 0x7F41457F9000, 0x7F0000.
[171655.730] (==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
[171655.730] (==) MGA(0): Min pixel clock is 18 MHz
[171655.730] (--) MGA(0): Max pixel clock is 203 MHz
[171655.730] (II) MGA(0): Monitor0: Using default hsync range of 31.50-48.00 kHz
[171655.730] (II) MGA(0): Monitor0: Using default vrefresh range of 50.00-70.00 Hz
[171655.730] (II) MGA(0): Monitor0: Using default maximum pixel clock of 65.00 MHz
[171655.730] (WW) MGA(0): Unable to estimate virtual size
[171655.730] (II) MGA(0): Clock range:  18.75 to 203.40 MHz
[171655.730] (II) MGA(0): Not using default mode "640x350" (vrefresh out of range)
[171655.730] (II) MGA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "640x400" (vrefresh out of range)
[171655.730] (II) MGA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "720x400" (vrefresh out of range)
[171655.730] (II) MGA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "640x480" (vrefresh out of range)
[171655.730] (II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "640x480" (vrefresh out of range)
[171655.730] (II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "640x480" (vrefresh out of range)
[171655.730] (II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "400x300" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "800x600" (vrefresh out of range)
[171655.730] (II) MGA(0): Not using default mode "400x300" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "800x600" (vrefresh out of range)
[171655.730] (II) MGA(0): Not using default mode "400x300" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "800x600" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "400x300" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1024x768i" (vrefresh out of range)
[171655.730] (II) MGA(0): Not using default mode "512x384i" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "512x384" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1024x768" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "512x384" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1024x768" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "512x384" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1024x768" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "512x384" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1152x864" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1280x960" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "640x480" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1280x960" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "640x480" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1280x1024" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "640x512" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1280x1024" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "640x512" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1280x1024" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "640x512" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
[171655.730] (II) MGA(0): Not using default mode "800x600" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
[171655.730] (II) MGA(0): Not using default mode "800x600" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
[171655.730] (II) MGA(0): Not using default mode "800x600" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
[171655.730] (II) MGA(0): Not using default mode "800x600" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "800x600" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "896x672" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "896x672" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "928x696" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "928x696" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "960x720" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[171655.730] (II) MGA(0): Not using default mode "960x720" (doublescan mode not supported)
[171655.730] (II) MGA(0): Not using default mode "832x624" (hsync out of range)
[171655.730] (II) MGA(0): Not using default mode "416x312" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1152x864" (hsync out of range)
[171655.731] (II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1152x864" (hsync out of range)
[171655.731] (II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1152x864" (hsync out of range)
[171655.731] (II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1152x864" (hsync out of range)
[171655.731] (II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1152x864" (hsync out of range)
[171655.731] (II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1152x864" (hsync out of range)
[171655.731] (II) MGA(0): Not using default mode "576x432" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1360x768" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "680x384" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1360x768" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "680x384" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "700x525" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "700x525" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "700x525" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "700x525" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1440x900" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "720x450" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1600x1024" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "800x512" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "840x525" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "840x525" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "840x525" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "840x525" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[171655.731] (II) MGA(0): Not using default mode "840x525" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1920x1080" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "960x540" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1920x1200" (width too large for virtual size)
[171655.731] (II) MGA(0): Not using default mode "960x600" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[171655.731] (II) MGA(0): Not using default mode "960x720" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[171655.731] (II) MGA(0): Not using default mode "1024x768" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[171655.731] (II) MGA(0): Not using default mode "1024x768" (doublescan mode not supported)
[171655.731] (II) MGA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[171655.731] (II) MGA(0): Not using default mode "1024x768" (doublescan mode not supported)
[171655.731] (--) MGA(0): Has SDRAM
[171655.731] (--) MGA(0): Virtual size is 1024x768 (pitch 1024)
[171655.731] (**) MGA(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[171655.731] (II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz zd)
[171655.731] (**) MGA(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[171655.731] (II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz zd)
[171655.731] (**) MGA(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[171655.731] (II) MGA(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz zd)
[171655.731] (**) MGA(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[171655.731] (II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz zd)
[171655.731] (==) MGA(0): DPI set to (96, 96)
[171655.731] (II) MGA(0): YDstOrg is set to 0
[171655.731] (II) Loading sub module "fb"
[171655.731] (II) LoadModule: "fb"
[171655.732] (II) Loading /usr/lib/xorg/modules/libfb.so
[171655.732] (II) Module fb: vendor="X.Org Foundation"
[171655.732]     compiled for 1.15.1, module version = 1.0.0
[171655.732]     ABI class: X.Org ANSI C Emulation, version 0.4
[171655.732] (II) MGA(0): MAPPED Framebuffer D9800000 7f0000 to 7F41455D5000.
[171655.732] (II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[171656.071] (--) MGA(0): 64 DWORD fifo
[171656.081] (==) MGA(0): Default visual is TrueColor
[171656.081] (EE) MGA(0): [drm] Direct rendering only supported with G200/G400/G450/G550.
[171656.081] (II) MGA(0): Using 3296 lines for offscreen memory.
[171656.081] (==) MGA(0): Backing store enabled
[171656.081] (==) MGA(0): Silken mouse enabled
[171656.081] (==) MGA(0): DPMS enabled
[171656.081] (WW) MGA(0): Direct rendering disabled
[171656.081] (==) RandR enabled
[171656.085] (II) SELinux: Disabled on system
[171656.085] (II) AIGLX: Screen 0 is not DRI2 capable
[171656.085] (EE) AIGLX: reverting to software rendering
[171656.095] (II) AIGLX: Loaded and initialized swrast
[171656.095] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[171656.135] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[171656.157] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[171656.157] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[171656.157] (II) LoadModule: "evdev"
[171656.157] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[171656.157] (II) Module evdev: vendor="X.Org Foundation"
[171656.157]     compiled for 1.15.0, module version = 2.8.2
[171656.157]     Module class: X.Org XInput Driver
[171656.157]     ABI class: X.Org XInput driver, version 20.0
[171656.157] (II) Using input driver 'evdev' for 'Power Button'
[171656.157] (**) Power Button: always reports core events
[171656.157] (**) evdev: Power Button: Device: "/dev/input/event0"
[171656.157] (--) evdev: Power Button: Vendor 0 Product 0x1
[171656.157] (--) evdev: Power Button: Found keys
[171656.157] (II) evdev: Power Button: Configuring as keyboard
[171656.157] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[171656.157] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[171656.157] (**) Option "xkb_rules" "evdev"
[171656.157] (**) Option "xkb_model" "pc105"
[171656.157] (**) Option "xkb_layout" "us"
[171656.512] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[171656.664] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[171656.692] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[171656.720] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[171656.748] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[171656.778] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
```

xorg.conf:

```
Section "ServerLayout"    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection


Section "Module"
    Load  "glx"
EndSection


Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection


Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "SyncOnGreen"            # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "MGASDRAM"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "SetMclk"                # <freq>
        #Option     "OverclockMem"           # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "Rotate"                 # [<str>]
        #Option     "TexturedVideo"          # [<bool>]
        #Option     "Crtc2Half"              # [<bool>]
        #Option     "Crtc2Ram"               # <i>
        #Option     "Int10"                  # [<bool>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DigitalScreen1"         # [<bool>]
        #Option     "DigitalScreen2"         # [<bool>]
        #Option     "TV"                     # [<bool>]
        #Option     "TVStandard"             # [<str>]
        #Option     "CableType"              # [<str>]
        #Option     "NoHal"                  # [<bool>]
        #Option     "SwappedHead"            # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "MergedFB"               # [<bool>]
        #Option     "Monitor2HSync"          # [<str>]
        #Option     "Monitor2VRefresh"       # [<str>]
        #Option     "Monitor2Position"       # [<str>]
        #Option     "MetaModes"              # [<str>]
        #Option     "OldDmaInit"             # [<bool>]
        #Option     "ForcePciDma"            # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "KVM"                    # [<bool>]
    Identifier  "Card0"
    Driver      "mga"
    BusID       "PCI:8:3:0"
    Option      "HWcursor" "off"
EndSection


Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    16
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by QIII on 2014-05-22
Closed, duplicate.

See [http://ubuntuforums.org/showthread.php?t=2225684](http://ubuntuforums.org/showthread.php?t=2225684)

---

