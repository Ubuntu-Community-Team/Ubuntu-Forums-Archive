---
title: "Herd 2 ubuntu 386"
date: 2007-01-16
forum: Development CD/DVD Image Testing
---

### Post by peterthewolf on 2007-01-16
Cannot install to my pc, after choosing keyboard (united kingdom) pc stops with a jagged diagonal display from top right to bottom left.

The dmesg from the pc with dapper installed

[17179569.184000] Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006 (Ubuntu 2.6.17-10.34-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003bfb0000 (usable)
[17179569.184000]  BIOS-e820: 000000003bfb0000 - 000000003bfc0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003bfc0000 - 000000003bff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003bff0000 - 000000003c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 63MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 245680
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 16304 pages, LIFO batch:3
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fa1b0
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x07000610 MSFT 0x00000097) @ 0x3bfb0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x07000610 MSFT 0x00000097) @ 0x3bfb0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x07000610 MSFT 0x00000097) @ 0x3bfb0390
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x07000610 MSFT 0x00000097) @ 0x3bfb0400
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x07000610 MSFT 0x00000097) @ 0x3bfc0040
[17179569.184000] ACPI: DSDT (v001  ALNF4 ALNF4008 0x00000008 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:15 APIC version 16
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3c000000:c2c00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2004.418 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.864000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.864000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.880000] Memory: 964752k/982720k available (1829k kernel code, 17300k reserved, 1038k data, 288k init, 65216k highmem)
[17179569.880000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.960000] Calibrating delay using timer specific routine.. 4014.42 BogoMIPS (lpj=8028846)
[17179569.960000] Security Framework v1.0.0 initialized
[17179569.960000] SELinux:  Disabled at boot.
[17179569.960000] Mount-cache hash table entries: 512
[17179569.960000] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001d
[17179569.960000] CPU: After vendor identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001d
[17179569.960000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.960000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.960000] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001d
[17179569.960000] CPU: AMD Athlon(tm) 64 Processor 3200+ stepping 02
[17179569.960000] Checking 'hlt' instruction... OK.
[17179569.976000] SMP alternatives: switching to UP code
[17179569.976000] Freeing SMP alternatives: 0k freed
[17179569.976000] checking if image is initramfs... it is
[17179570.408000] Freeing initrd memory: 5251k freed
[17179570.408000] ACPI: Core revision 20060707
[17179570.408000] ACPI: Looking for DSDT ... not found!
[17179570.408000] ENABLING IO-APIC IRQs
[17179570.408000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.556000] NET: Registered protocol family 16
[17179570.556000] EISA bus registered
[17179570.556000] ACPI: bus type pci registered
[17179570.556000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179570.556000] PCI: Not using MMCONFIG.
[17179570.556000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[17179570.556000] PCI: Using configuration type 1
[17179570.556000] Setting up standard PCI resources
[17179570.564000] ACPI: Interpreter enabled
[17179570.564000] ACPI: Using IOAPIC for interrupt routing
[17179570.564000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.564000] PCI: Probing PCI hardware (bus 00)
[17179570.568000] Boot video device is 0000:00:05.0
[17179570.568000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0d.0
[17179570.568000] PCI: Transparent bridge - 0000:00:10.0
[17179570.568000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.584000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[17179570.584000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[17179570.592000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179570.592000] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[17179570.592000] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[17179570.592000] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *11
[17179570.592000] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[17179570.592000] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[17179570.592000] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[17179570.592000] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *11
[17179570.596000] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[17179570.596000] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *11
[17179570.596000] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[17179570.596000] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[17179570.596000] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[17179570.596000] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[17179570.596000] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[17179570.596000] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[17179570.596000] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *5
[17179570.600000] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[17179570.600000] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[17179570.600000] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[17179570.600000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.600000] pnp: PnP ACPI init
[17179570.604000] pnp: PnP ACPI: found 16 devices
[17179570.604000] PnPBIOS: Disabled by ACPI PNP
[17179570.604000] PCI: Using ACPI for IRQ routing
[17179570.604000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.616000] pnp: 00:0d: ioport range 0x290-0x29f has been reserved
[17179570.616000] PCI: Bridge: 0000:00:03.0
[17179570.616000]   IO window: disabled.
[17179570.616000]   MEM window: disabled.
[17179570.616000]   PREFETCH window: disabled.
[17179570.616000] PCI: Bridge: 0000:00:04.0
[17179570.616000]   IO window: disabled.
[17179570.616000]   MEM window: disabled.
[17179570.616000]   PREFETCH window: disabled.
[17179570.616000] PCI: Bridge: 0000:00:10.0
[17179570.616000]   IO window: disabled.
[17179570.616000]   MEM window: feb00000-febfffff
[17179570.616000]   PREFETCH window: disabled.
[17179570.616000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[17179570.616000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179570.616000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[17179570.616000] NET: Registered protocol family 2
[17179570.656000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.656000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.656000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.656000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.656000] TCP reno registered
[17179570.656000] audit: initializing netlink socket (disabled)
[17179570.656000] audit(1168943438.656:1): initialized
[17179570.656000] highmem bounce pool size: 64 pages
[17179570.656000] VFS: Disk quotas dquot_6.5.1
[17179570.656000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.656000] Initializing Cryptographic API
[17179570.656000] io scheduler noop registered
[17179570.656000] io scheduler anticipatory registered
[17179570.656000] io scheduler deadline registered
[17179570.656000] io scheduler cfq registered (default)
[17179571.072000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[17179571.072000] pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
[17179571.072000] assign_interrupt_mode Found MSI capability
[17179571.072000] Allocate Port Service[0000:00:03.0:pcie00]
[17179571.072000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179571.072000] pcie_portdrv_probe->Dev[02fb:10de] has invalid IRQ. Check vendor BIOS
[17179571.072000] assign_interrupt_mode Found MSI capability
[17179571.072000] Allocate Port Service[0000:00:04.0:pcie00]
[17179571.072000] isapnp: Scanning for PnP cards...
[17179571.428000] isapnp: No Plug & Play device found
[17179571.444000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.444000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.444000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.444000] mice: PS/2 mouse device common for all mice
[17179571.444000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.444000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.444000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.444000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179571.444000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.448000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.448000] EISA: Probing bus 0 at eisa.0
[17179571.448000] Cannot allocate resource for EISA slot 2
[17179571.448000] Cannot allocate resource for EISA slot 4
[17179571.448000] Cannot allocate resource for EISA slot 5
[17179571.448000] Cannot allocate resource for EISA slot 6
[17179571.448000] EISA: Detected 0 cards.
[17179571.448000] TCP bic registered
[17179571.448000] NET: Registered protocol family 1
[17179571.448000] NET: Registered protocol family 8
[17179571.448000] NET: Registered protocol family 20
[17179571.448000] Using IPI Shortcut mode
[17179571.448000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.448000] Freeing unused kernel memory: 288k freed
[17179571.476000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.616000] Capability LSM initialized
[17179572.644000] ACPI: Getting cpuindex for acpiid 0x2
[17179572.972000] SCSI subsystem initialized
[17179572.972000] libata version 1.20 loaded.
[17179572.972000] sata_nv 0000:00:0e.0: version 0.8
[17179572.972000] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[17179572.972000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 23 (level, low) -> IRQ 201
[17179572.972000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179572.972000] ata1: SATA max UDMA/133 cmd 0xE800 ctl 0xE482 bmdma 0xE000 irq 201
[17179572.972000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE082 bmdma 0xE008 irq 201
[17179573.176000] ata1: SATA link up 3.0 Gbps (SStatus 123)
[17179573.340000] ata1: dev 0 cfg 49:2f00 82:746b 83:7f01 84:4023 85:7468 86:bc01 87:4023 88:40ff
[17179573.340000] ata1: dev 0 ATA-7, max UDMA7, 312581808 sectors: LBA48
[17179573.368000] ata1: dev 0 configured for UDMA/133
[17179573.368000] scsi0 : sata_nv
[17179573.572000] ata2: SATA link down (SStatus 0)
[17179573.572000] scsi1 : sata_nv
[17179573.572000]   Vendor: ATA       Model: SAMSUNG HD160JJ   Rev: ZM10
[17179573.572000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179573.572000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[17179573.572000] NFORCE-MCP51: chipset revision 161
[17179573.572000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[17179573.572000] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[17179573.572000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179573.572000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[17179573.572000] Probing IDE interface ide0...
[17179573.584000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179573.584000] sda: Write Protect is off
[17179573.584000] sda: Mode Sense: 00 3a 00 00
[17179573.584000] SCSI device sda: drive cache: write back
[17179573.588000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179573.588000] sda: Write Protect is off
[17179573.588000] sda: Mode Sense: 00 3a 00 00
[17179573.588000] SCSI device sda: drive cache: write back
[17179573.588000]  sda: sda1 sda2 sda3
[17179573.608000] sd 0:0:0:0: Attached scsi disk sda
[17179574.308000] hda: _NEC DVD_RW ND-4571A, ATAPI CD/DVD-ROM drive
[17179574.980000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.980000] Probing IDE interface ide1...
[17179575.556000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.556000] Uniform CD-ROM driver Revision: 3.20
[17179575.632000] Probing IDE interface ide1...
[17179575.668000] usbcore: registered new driver usbfs
[17179575.668000] usbcore: registered new driver hub
[17179575.672000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[17179575.672000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 22 (level, low) -> IRQ 209
[17179575.672000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[17179575.672000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[17179575.672000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[17179575.672000] ehci_hcd 0000:00:0b.1: debug port 1
[17179575.672000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[17179575.672000] ehci_hcd 0000:00:0b.1: irq 209, io mem 0xfeadfc00
[17179575.672000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.692000] usb usb1: configuration #1 chosen from 1 choice
[17179575.692000] hub 1-0:1.0: USB hub found
[17179575.692000] hub 1-0:1.0: 8 ports detected
[17179575.708000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179575.748000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179575.796000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[17179575.796000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 21 (level, low) -> IRQ 217
[17179575.796000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[17179575.796000] forcedeth: using HIGHDMA
[17179576.316000] eth0: forcedeth.c: subsystem: 01849:0269 bound to 0000:00:14.0
[17179576.316000] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[17179576.316000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 20 (level, low) -> IRQ 225
[17179576.316000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179576.316000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[17179576.316000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[17179576.332000] ohci_hcd 0000:00:0b.0: irq 225, io mem 0xfeade000
[17179576.388000] usb usb2: configuration #1 chosen from 1 choice
[17179576.388000] hub 2-0:1.0: USB hub found
[17179576.388000] hub 2-0:1.0: 8 ports detected
[17179576.552000] Attempting manual resume
[17179576.560000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179576.560000] EXT3-fs: write access will be enabled during recovery.
[17179576.568000] kjournald starting.  Commit interval 5 seconds
[17179576.568000] EXT3-fs: recovery complete.
[17179576.580000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.796000] usb 2-5: new low speed USB device using ohci_hcd and address 2
[17179577.000000] usb 2-5: configuration #1 chosen from 1 choice
[17179584.180000] Floppy drive(s): fd0 is 1.44M
[17179584.196000] input: PC Speaker as /class/input/input1
[17179584.196000] FDC 0 is a post-1991 82077
[17179584.204000] Linux agpgart interface v0.101 (c) Dave Jones
[17179584.260000] nvidia: module license 'NVIDIA' taints kernel.
[17179584.264000] ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 19
[17179584.264000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNEC] -> GSI 19 (level, low) -> IRQ 233
[17179584.264000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[17179584.264000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179584.604000] parport: PnPBIOS parport detected.
[17179584.604000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179584.620000] Real Time Clock Driver v1.12ac
[17179584.636000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179584.640000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179584.644000] Linux video capture interface: v1.00
[17179584.808000] input: GenPS/2 Genius Mouse as /class/input/input2
[17179584.836000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179584.840000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 18
[17179584.840000] ACPI: PCI Interrupt 0000:03:0a.0[A] -> Link [LNKC] -> GSI 18 (level, low) -> IRQ 50
[17179584.840000] saa7130[0]: found at 0000:03:0a.0, rev: 1, irq: 50, latency: 32, mmio: 0xfebffc00
[17179584.840000] saa7130[0]: subsystem: 185b:c901, board: Compro Videomate DVB-T200 [card=71,autodetected]
[17179584.840000] saa7130[0]: board init: gpio is 843f00
[17179584.840000] input: saa7134 IR (Compro Videomate DV as /class/input/input3
[17179584.992000] saa7130[0]: i2c eeprom 00: 5b 18 01 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179584.992000] saa7130[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[17179584.992000] saa7130[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 88 ff ff ff ff
[17179584.992000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179584.992000] saa7130[0]: i2c eeprom 40: ff d0 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[17179584.992000] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[17179584.992000] saa7130[0]: i2c eeprom 60: 30 26 ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179584.992000] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179584.992000] saa7130[0]: registered device video0 [v4l2]
[17179584.992000] saa7130[0]: registered device vbi0
[17179585.032000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[17179585.032000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 23 (level, low) -> IRQ 201
[17179585.032000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[17179585.140000] NET: Registered protocol family 17
[17179585.420000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[17179585.464000] saa7134 ALSA driver for DMA sound loaded
[17179585.464000] saa7130[0]/alsa: saa7130[0] at 0xfebffc00 irq 50 registered as card -1
[17179585.472000] ts: Compaq touchscreen protocol output
[17179585.608000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179586.552000] lp0: using parport0 (interrupt-driven).
[17179586.656000] Adding 2048276k swap on /dev/disk/by-uuid/ed0c1905-4f90-409e-a5dd-8d864b3eefd4.  Priority:-1 extents:1 across:2048276k
[17179586.696000] EXT3 FS on sda1, internal journal
[17179586.856000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179586.856000] SGI XFS Quota Management subsystem
[17179586.916000] XFS mounting filesystem sda3
[17179586.988000] Ending clean XFS mount for filesystem: sda3
[17179588.144000] NET: Registered protocol family 10
[17179588.144000] lo: Disabled Privacy Extensions
[17179588.144000] IPv6 over IPv4 tunneling driver
[17179592.444000] ACPI: Power Button (FF) [PWRF]
[17179592.444000] ACPI: Power Button (CM) [PWRB]
[17179592.528000] ibm_acpi: ec object not found
[17179592.552000] pcc_acpi: loading...
[17179592.812000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179592.812000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
[17179592.812000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8 (1350 mV)
[17179592.812000] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[17179592.812000] cpu_init done, current fid 0xc, vid 0x6
[17179595.076000] i2c_adapter i2c-1: SMBus Quick command not supported, can't probe for chips
[17179595.076000] i2c_adapter i2c-2: SMBus Quick command not supported, can't probe for chips
[17179595.080000] i2c_adapter i2c-3: SMBus Quick command not supported, can't probe for chips
[17179595.476000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[17179595.476000] apm: overridden by ACPI.
[17179599.048000] eth0: no IPv6 routers present
[17179599.364000] Bluetooth: Core ver 2.8
[17179599.364000] NET: Registered protocol family 31
[17179599.364000] Bluetooth: HCI device and connection manager initialized
[17179599.364000] Bluetooth: HCI socket layer initialized
[17179599.384000] Bluetooth: L2CAP ver 2.8
[17179599.384000] Bluetooth: L2CAP socket layer initialized
[17179599.404000] Bluetooth: RFCOMM socket layer initialized
[17179599.404000] Bluetooth: RFCOMM TTY layer initialized
[17179599.404000] Bluetooth: RFCOMM ver 1.7

---

### Post by pochu on 2007-01-16
The bug has been filed at Launchpad (I think, cannot search for it now).

Please report this there.

Thanks
Pochu

---

### Post by Henrik on 2007-01-16
It's this: [https://launchpad.net/ubuntu/+source/console-setup/+bug/73955](https://launchpad.net/ubuntu/+source/console-setup/+bug/73955)

We should probably set up a page of common issues.

---

### Post by caravena on 2007-01-21
Hello,

Report in:
[http://bugzilla.kernel.org/show_bug.cgi?id=7683]("http://bugzilla.kernel.org/show_bug.cgi?id=7683")

---

