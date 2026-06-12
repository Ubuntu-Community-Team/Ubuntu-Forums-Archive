---
title: "USB disk not found (ipod rockbox)"
date: 2006-09-24
forum: Desktop Environments
---

### Post by jocke1s on 2006-09-24
Hi all,

This is VERY frustrating.

When I connect my 30Gb ipod video with rockbox on it it doesn't show anywhere on ubuntu (dapper).

sudo fdisk -l doesn't show anything

dmesg is echoed at the end.

This is a ubuntu/linux stopper for me. I have to be able to connect my ipod!!!

Any ideas howto:
make it work?
Format it, if thats the problem?
Do I need some software to make it work?

/Ask2

dmesg gives:
 dmesg
[17179569.184000] Linux version 2.6.15-27-k7 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffec000 (usable)
[17179569.184000]  BIOS-e820: 000000003ffec000 - 000000003ffef000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffef000 - 000000003ffff000 (reserved)
[17179569.184000]  BIOS-e820: 000000003ffff000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 262124
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32748 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f6da0
[17179569.184000] ACPI: RSDT (v001 ASUS   A7V266   0x30303031 MSFT 0x31313031) @ 0x3ffec000
[17179569.184000] ACPI: FADT (v001 ASUS   A7V266   0x30303031 MSFT 0x31313031) @ 0x3ffec080
[17179569.184000] ACPI: BOOT (v001 ASUS   A7V266   0x30303031 MSFT 0x31313031) @ 0x3ffec040
[17179569.184000] ACPI: DSDT (v001   ASUS A7V266   0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xe408
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01945000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1208.909 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.976000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.976000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.048000] Memory: 1027208k/1048496k available (2103k kernel code, 20592k reserved, 599k data, 332k init, 130992k highmem)
[17179570.048000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.128000] Calibrating delay using timer specific routine.. 2420.26 BogoMIPS (lpj=4840530)
[17179570.128000] Security Framework v1.0.0 initialized
[17179570.128000] SELinux:  Disabled at boot.
[17179570.128000] Mount-cache hash table entries: 512
[17179570.128000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179570.128000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179570.128000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.128000] CPU: L2 Cache: 256K (64 bytes/line)
[17179570.128000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[17179570.128000] mtrr: v2.0 (20020519)
[17179570.128000] Enabling fast FPU save and restore... done.
[17179570.128000] Checking 'hlt' instruction... OK.
[17179570.144000] SMP alternatives: switching to UP code
[17179570.144000] checking if image is initramfs... it is
[17179571.056000] Freeing initrd memory: 6776k freed
[17179571.076000] ACPI: Looking for DSDT ... not found!
[17179571.076000] ACPI: setting ELCR to 0200 (from 0820)
[17179571.100000] CPU0: AMD Athlon(TM)Processor stepping 02
[17179571.100000] SMP motherboard not detected.
[17179571.100000] Local APIC not detected. Using dummy APIC emulation.
[17179571.100000] Brought up 1 CPUs
[17179571.100000] NET: Registered protocol family 16
[17179571.100000] EISA bus registered
[17179571.100000] ACPI: bus type pci registered
[17179571.104000] PCI: PCI BIOS revision 2.10 entry at 0xf0ed0, last bus=1
[17179571.104000] PCI: Using configuration type 1
[17179571.104000] ACPI: Subsystem revision 20051216
[17179571.108000] ACPI: Interpreter enabled
[17179571.108000] ACPI: Using PIC for interrupt routing
[17179571.108000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179571.108000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.108000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.108000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179571.108000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.108000] PCI: Probing PCI hardware (bus 00)
[17179571.108000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.112000] Boot video device is 0000:01:00.0
[17179571.112000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.120000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179571.124000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.124000] pnp: PnP ACPI init
[17179571.132000] pnp: PnP ACPI: found 12 devices
[17179571.132000] PnPBIOS: Disabled by ACPI PNP
[17179571.132000] PCI: Using ACPI for IRQ routing
[17179571.132000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.144000] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[17179571.144000] pnp: 00:02: ioport range 0xe800-0xe80f has been reserved
[17179571.144000] pnp: 00:02: ioport range 0x290-0x291 has been reserved
[17179571.144000] pnp: 00:02: ioport range 0x370-0x373 has been reserved
[17179571.144000] PCI: Bridge: 0000:00:01.0
[17179571.144000]   IO window: disabled.
[17179571.144000]   MEM window: ee000000-efdfffff
[17179571.144000]   PREFETCH window: eff00000-fbffffff
[17179571.144000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.144000] Simple Boot Flag at 0x3a set to 0x1
[17179571.144000] audit: initializing netlink socket (disabled)
[17179571.144000] audit(1159080896.140:1): initialized
[17179571.144000] highmem bounce pool size: 64 pages
[17179571.144000] VFS: Disk quotas dquot_6.5.1
[17179571.144000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.144000] Initializing Cryptographic API
[17179571.144000] io scheduler noop registered
[17179571.144000] io scheduler anticipatory registered
[17179571.144000] io scheduler deadline registered
[17179571.144000] io scheduler cfq registered
[17179571.144000] isapnp: Scanning for PnP cards...
[17179571.500000] isapnp: No Plug & Play device found
[17179571.520000] Real Time Clock Driver v1.12
[17179571.524000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179571.524000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.524000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.524000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.524000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.524000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.524000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.528000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.528000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.528000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.528000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.528000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.528000] mice: PS/2 mouse device common for all mice
[17179571.528000] EISA: Probing bus 0 at eisa.0
[17179571.528000] EISA: Detected 0 cards.
[17179571.532000] NET: Registered protocol family 2
[17179571.568000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.568000] TCP established hash table entries: 262144 (order: 9, 3145728 bytes)
[17179571.580000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[17179571.584000] TCP: Hash tables configured (established 262144 bind 65536)
[17179571.584000] TCP reno registered
[17179571.584000] TCP bic registered
[17179571.584000] NET: Registered protocol family 1
[17179571.584000] NET: Registered protocol family 8
[17179571.584000] NET: Registered protocol family 20
[17179571.584000] Using IPI No-Shortcut mode
[17179571.584000] ACPI wakeup devices:
[17179571.584000] PCI0 PCI1 UAR1 UAR2 USB0 USB1 USB2
[17179571.584000] ACPI: (supports S0 S1 S4 S5)
[17179571.584000] Freeing unused kernel memory: 332k freed
[17179571.672000] vga16fb: initializing
[17179571.672000] vga16fb: mapped to 0xc00a0000
[17179571.796000] Console: switching to colour frame buffer device 80x25
[17179571.796000] fb0: VGA16 VGA frame buffer device
[17179571.836000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.952000] Capability LSM initialized
[17179573.868000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179573.868000] VP_IDE: chipset revision 6
[17179573.868000] VP_IDE: not 100% native mode: will probe irqs later
[17179573.868000] VP_IDE: VIA vt8233 (rev 00) IDE UDMA100 controller on pci0000:00:11.1
[17179573.868000]     ide0: BM-DMA at 0xb400-0xb407, BIOS settings: hda:DMA, hdb:DMA
[17179573.868000]     ide1: BM-DMA at 0xb408-0xb40f, BIOS settings: hdc:DMA, hdd:pio
[17179573.868000] Probing IDE interface ide0...
[17179574.284000] hda: WDC WD800BB-00CAA0, ATA DISK drive
[17179574.564000] hdb: FUJITSU MPG3409AH E, ATA DISK drive
[17179574.620000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.656000] Probing IDE interface ide1...
[17179575.520000] hdc: SONY DVD RW DW-U10A, ATAPI CD/DVD-ROM drive
[17179576.192000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.204000] hda: max request size: 128KiB
[17179576.228000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.228000] hda: cache flushes not supported
[17179576.228000]  hda: hda1
[17179576.248000] hdb: max request size: 128KiB
[17179576.248000] hdb: 80063424 sectors (40992 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.248000] hdb: cache flushes not supported
[17179576.248000]  hdb: hdb1 hdb2 hdb3<6>hdc: ATAPI 32X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache, UDMA(33)
[17179576.248000] Uniform CD-ROM driver Revision: 3.20
[17179576.248000]
[17179576.732000] usbcore: registered new driver usbfs
[17179576.732000] usbcore: registered new driver hub
[17179576.736000] USB Universal Host Controller Interface driver v2.3
[17179576.736000] PCI: Enabling device 0000:00:0f.0 (0014 -> 0015)
[17179576.736000] **** SET: Misaligned resource pointer: df880922 Type 07 Len 0
[17179576.736000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179576.736000] PCI: setting IRQ 11 as level-triggered
[17179576.736000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179576.736000] PCI: Via IRQ fixup for 0000:00:0f.0, from 255 to 11
[17179576.736000] uhci_hcd 0000:00:0f.0: UHCI Host Controller
[17179576.736000] uhci_hcd 0000:00:0f.0: new USB bus registered, assigned bus number 1
[17179576.736000] uhci_hcd 0000:00:0f.0: irq 11, io base 0x0000d400
[17179576.736000] hub 1-0:1.0: USB hub found
[17179576.736000] hub 1-0:1.0: 2 ports detected
[17179576.840000] PCI: Enabling device 0000:00:0f.1 (0014 -> 0015)
[17179576.840000] **** SET: Misaligned resource pointer: df8807a2 Type 07 Len 0
[17179576.840000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179576.840000] PCI: setting IRQ 5 as level-triggered
[17179576.840000] ACPI: PCI Interrupt 0000:00:0f.1[B] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179576.840000] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 5
[17179576.840000] uhci_hcd 0000:00:0f.1: UHCI Host Controller
[17179576.840000] uhci_hcd 0000:00:0f.1: new USB bus registered, assigned bus number 2
[17179576.840000] uhci_hcd 0000:00:0f.1: irq 5, io base 0x0000d000
[17179576.840000] hub 2-0:1.0: USB hub found
[17179576.840000] hub 2-0:1.0: 2 ports detected
[17179576.944000] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179576.944000] uhci_hcd 0000:00:11.2: UHCI Host Controller
[17179576.944000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 3
[17179576.944000] uhci_hcd 0000:00:11.2: irq 5, io base 0x0000b000
[17179576.944000] hub 3-0:1.0: USB hub found
[17179576.944000] hub 3-0:1.0: 2 ports detected
[17179576.944000] PCI: Enabling device 0000:00:0f.2 (0014 -> 0016)
[17179576.944000] **** SET: Misaligned resource pointer: df880262 Type 07 Len 0
[17179576.944000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179576.944000] ACPI: PCI Interrupt 0000:00:0f.2[C] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179576.944000] PCI: Via IRQ fixup for 0000:00:0f.2, from 255 to 11
[17179576.944000] ehci_hcd 0000:00:0f.2: EHCI Host Controller
[17179577.048000] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179577.048000] uhci_hcd 0000:00:11.3: UHCI Host Controller
[17179577.048000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 4
[17179577.048000] uhci_hcd 0000:00:11.3: irq 5, io base 0x0000a800
[17179577.048000] hub 4-0:1.0: USB hub found
[17179577.048000] hub 4-0:1.0: 2 ports detected
[17179577.152000] ACPI: PCI Interrupt 0000:00:11.4[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179577.152000] uhci_hcd 0000:00:11.4: UHCI Host Controller
[17179577.152000] uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus number 5
[17179577.152000] uhci_hcd 0000:00:11.4: irq 5, io base 0x0000a400
[17179577.152000] hub 5-0:1.0: USB hub found
[17179577.152000] hub 5-0:1.0: 2 ports detected
[17179577.260000] ehci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 6
[17179577.260000] ehci_hcd 0000:00:0f.2: irq 11, io mem 0xed800000
[17179577.260000] ehci_hcd 0000:00:0f.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[17179577.260000] hub 6-0:1.0: USB hub found
[17179577.260000] hub 6-0:1.0: 4 ports detected
[17179577.440000] Attempting manual resume
[17179577.464000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179577.464000] SGI XFS Quota Management subsystem
[17179577.464000] XFS mounting filesystem hdb1
[17179577.572000] Ending clean XFS mount for filesystem: hdb1
[17179577.776000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[17179577.916000] hub 3-2:1.0: USB hub found
[17179577.920000] hub 3-2:1.0: 4 ports detected
[17179579.148000] usb 6-4: new high speed USB device using ehci_hcd and address 4
[17179579.624000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[17179579.748000] usb 1-2: device descriptor read/64, error -71
[17179579.972000] usb 1-2: device descriptor read/64, error -71
[17179580.188000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[17179580.312000] usb 1-2: device descriptor read/64, error -71
[17179580.540000] usb 1-2: device descriptor read/64, error -71
[17179580.756000] usb 1-2: new low speed USB device using uhci_hcd and address 4
[17179581.172000] usb 1-2: device not accepting address 4, error -71
[17179581.284000] usb 1-2: new low speed USB device using uhci_hcd and address 5
[17179581.700000] usb 1-2: device not accepting address 5, error -71
[17179581.940000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[17179591.768000] irda_init()
[17179591.768000] NET: Registered protocol family 23
[17179591.808000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.836000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[17179591.836000] agpgart: AGP aperture is 32M @ 0xfc000000
[17179592.228000] PCI: Enabling device 0000:00:05.0 (0084 -> 0085)
[17179592.228000] **** SET: Misaligned resource pointer: f740aae2 Type 07 Len 0
[17179592.228000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[17179592.228000] PCI: setting IRQ 9 as level-triggered
[17179592.228000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179592.548000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.552000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.568000] usbcore: registered new driver hiddev
[17179592.584000] input: Logitech USB Receiver as /class/input/input1
[17179592.584000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0f.1-1
[17179592.584000] usbcore: registered new driver usbhid
[17179592.584000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179593.040000] PCI: Enabling device 0000:00:10.0 (0014 -> 0017)
[17179593.040000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179593.040000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[17179593.040000] 0000:00:10.0: 3Com PCI 3c905B Cyclone 100baseTx at f88c4000. Vers LK1.1.19
[17179593.072000] input: PC Speaker as /class/input/input2
[17179593.092000] Floppy drive(s): fd0 is 1.44M
[17179593.132000] FDC 0 is a post-1991 82077
[17179593.228000] parport: PnPBIOS parport detected.
[17179593.228000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179593.252000] parport0: Printer, Canon i850
[17179593.508000] nvidia: module license 'NVIDIA' taints kernel.
[17179593.840000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179593.840000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179593.856000] ts: Compaq touchscreen protocol output
[17179594.536000] SCSI subsystem initialized
[17179594.572000] Initializing USB Mass Storage driver...
[17179594.576000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179594.576000] usb-storage: device found at 4
[17179594.576000] usb-storage: waiting for device to settle before scanning
[17179594.576000] usbcore: registered new driver usb-storage
[17179594.576000] USB Mass Storage support registered.
[17179594.640000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179594.924000] lp0: using parport0 (interrupt-driven).
[17179595.012000] Adding 2048276k swap on /dev/hdb2.  Priority:-1 extents:1 across:2048276k
[17179595.356000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179595.356000] md: bitmap version 4.39
[17179595.696000] NET: Registered protocol family 17
[17179595.820000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179596.260000] cdrom: open failed.
[17179596.708000] kjournald starting.  Commit interval 5 seconds
[17179596.708000] EXT3 FS on hdb3, internal journal
[17179596.708000] EXT3-fs: mounted filesystem with ordered data mode.
[17179596.712000] XFS mounting filesystem hda1
[17179596.824000] Ending clean XFS mount for filesystem: hda1
[17179598.220000] NET: Registered protocol family 10
[17179598.220000] lo: Disabled Privacy Extensions
[17179598.220000] IPv6 over IPv4 tunneling driver
[17179599.612000]   Vendor: HDT72252  Model: 5DLAT80           Rev: V44O
[17179599.612000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179599.616000] usb-storage: device scan complete
[17179599.640000] Driver 'sd' needs updating - please use bus_type methods
[17179599.684000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179599.684000] sda: assuming drive cache: write through
[17179599.720000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179599.720000] sda: assuming drive cache: write through
[17179599.720000]  sda: sda1 sda2
[17179599.780000] sd 0:0:0:0: Attached scsi disk sda
[17179599.836000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179603.040000] ACPI: Power Button (FF) [PWRF]
[17179603.040000] ACPI: Power Button (CM) [PWRB]
[17179603.208000] ibm_acpi: ec object not found
[17179603.252000] pcc_acpi: loading...
[17179603.868000] powernow: No powernow capabilities detected
[17179606.820000] ppdev: user-space parallel port driver
[17179607.848000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179607.848000] apm: overridden by ACPI.
[17179608.200000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179608.200000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179608.200000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179608.784000] eth0: no IPv6 routers present
[17179632.180000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179632.676000] XFS mounting filesystem sda2
[17179632.816000] Ending clean XFS mount for filesystem: sda2
[17179854.484000] usb 1-2: new low speed USB device using uhci_hcd and address 6
[17179854.608000] usb 1-2: device descriptor read/64, error -71
[17179854.832000] usb 1-2: device descriptor read/64, error -71
[17179855.048000] usb 1-2: new low speed USB device using uhci_hcd and address 7
[17179855.172000] usb 1-2: device descriptor read/64, error -71
[17179855.400000] usb 1-2: device descriptor read/64, error -71
[17179855.616000] usb 1-2: new low speed USB device using uhci_hcd and address 8
[17179856.032000] usb 1-2: device not accepting address 8, error -71
[17179856.144000] usb 1-2: new low speed USB device using uhci_hcd and address 9
[17179856.560000] usb 1-2: device not accepting address 9, error -71
[17181071.116000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17181789.844000] usb 1-1: new low speed USB device using uhci_hcd and address 10
[17181789.968000] usb 1-1: device descriptor read/64, error -71
[17181790.192000] usb 1-1: device descriptor read/64, error -71
[17181790.408000] usb 1-1: new low speed USB device using uhci_hcd and address 11
[17181790.532000] usb 1-1: device descriptor read/64, error -71
[17181790.760000] usb 1-1: device descriptor read/64, error -71
[17181790.976000] usb 1-1: new low speed USB device using uhci_hcd and address 12
[17181791.392000] usb 1-1: device not accepting address 12, error -71
[17181791.504000] usb 1-1: new low speed USB device using uhci_hcd and address 13
[17181791.920000] usb 1-1: device not accepting address 13, error -71
[17183122.184000] usb 3-2: USB disconnect, address 2

---

