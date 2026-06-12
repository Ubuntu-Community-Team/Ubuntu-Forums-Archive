---
title: "Can someone examine my syslog please?"
date: 2005-04-23
forum: Desktop Environments
---

### Post by denzilla on 2005-04-23
Anything not right in this log?

[HTML]Apr 23 10:59:34 localhost kernel: BIOS-provided physical RAM map:
Apr 23 10:59:34 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 23 10:59:34 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 23 10:59:34 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 23 10:59:34 localhost kernel:  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
Apr 23 10:59:34 localhost kernel:  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
Apr 23 10:59:34 localhost kernel:  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
Apr 23 10:59:34 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Apr 23 10:59:34 localhost kernel: 511MB LOWMEM available.
Apr 23 10:59:34 localhost kernel: On node 0 totalpages: 131056
Apr 23 10:59:34 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Apr 23 10:59:34 localhost kernel:   Normal zone: 126960 pages, LIFO batch:16
Apr 23 10:59:34 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Apr 23 10:59:34 localhost kernel: DMI 2.2 present.
Apr 23 10:59:34 localhost kernel: ACPI: RSDP (v000 VIA694                                ) @ 0x000f6dc0
Apr 23 10:59:34 localhost kernel: ACPI: RSDT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
Apr 23 10:59:34 localhost kernel: ACPI: FADT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
Apr 23 10:59:34 localhost kernel: ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
Apr 23 10:59:34 localhost kernel: ACPI: PM-Timer IO Port: 0x4008
Apr 23 10:59:34 localhost kernel: Built 1 zonelists
Apr 23 10:59:34 localhost kernel: Kernel command line: root=/dev/hda1 ro quiet splash
Apr 23 10:59:34 localhost kernel: Local APIC disabled by BIOS -- you can enable it with "lapic"
Apr 23 10:59:34 localhost kernel: mapped APIC to ffffd000 (01406000)
Apr 23 10:59:34 localhost kernel: Initializing CPU#0
Apr 23 10:59:34 localhost kernel: PID hash table entries: 2048 (order: 11, 32768 bytes)
Apr 23 10:59:34 localhost kernel: Detected 1666.722 MHz processor.
Apr 23 10:59:34 localhost kernel: Using pmtmr for high-res timesource
Apr 23 10:59:34 localhost kernel: Console: colour VGA+ 80x25
Apr 23 10:59:34 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 23 10:59:34 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 23 10:59:34 localhost kernel: Memory: 511772k/524224k available (1436k kernel code, 11812k reserved, 754k data, 224k init, 0k highmem)
Apr 23 10:59:34 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 23 10:59:34 localhost kernel: Calibrating delay loop... 3301.37 BogoMIPS (lpj=1650688)
Apr 23 10:59:34 localhost kernel: Security Framework v1.0.0 initialized
Apr 23 10:59:34 localhost kernel: SELinux:  Disabled at boot.
Apr 23 10:59:34 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Apr 23 10:59:34 localhost kernel: CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000
Apr 23 10:59:34 localhost kernel: CPU: After vendor identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000
Apr 23 10:59:34 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Apr 23 10:59:34 localhost kernel: CPU: L2 Cache: 256K (64 bytes/line)
Apr 23 10:59:34 localhost kernel: CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000020 00000000 00000000
Apr 23 10:59:34 localhost kernel: CPU: AMD Athlon(tm) XP 2000+ stepping 02
Apr 23 10:59:34 localhost kernel: Enabling fast FPU save and restore... done.
Apr 23 10:59:34 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Apr 23 10:59:34 localhost kernel: Checking 'hlt' instruction... OK.
Apr 23 10:59:34 localhost kernel: Checking for popad bug... OK.
Apr 23 10:59:34 localhost kernel: ACPI: Looking for DSDT in initrd... not found!
Apr 23 10:59:34 localhost kernel: ACPI: setting ELCR to 0200 (from 0e20)
Apr 23 10:59:34 localhost kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Apr 23 10:59:34 localhost kernel: Freeing initrd memory: 4248k freed
Apr 23 10:59:34 localhost kernel: NET: Registered protocol family 16
Apr 23 10:59:34 localhost kernel: EISA bus registered
Apr 23 10:59:34 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfb440, last bus=1
Apr 23 10:59:34 localhost kernel: PCI: Using configuration type 1
Apr 23 10:59:34 localhost kernel: mtrr: v2.0 (20020519)
Apr 23 10:59:34 localhost kernel: ACPI: Subsystem revision 20050211
Apr 23 10:59:34 localhost kernel: ACPI: Interpreter enabled
Apr 23 10:59:34 localhost kernel: ACPI: Using PIC for interrupt routing
Apr 23 10:59:34 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Apr 23 10:59:34 localhost kernel: PCI: Probing PCI hardware (bus 00)
Apr 23 10:59:34 localhost kernel: PCI: Via IRQ fixup
Apr 23 10:59:34 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 23 10:59:34 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Apr 23 10:59:34 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Apr 23 10:59:34 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
Apr 23 10:59:34 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
Apr 23 10:59:34 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 23 10:59:34 localhost kernel: pnp: PnP ACPI init
Apr 23 10:59:34 localhost kernel: pnp: PnP ACPI: found 12 devices
Apr 23 10:59:34 localhost kernel: PnPBIOS: Disabled by ACPI PNP
Apr 23 10:59:34 localhost kernel: PCI: Using ACPI for IRQ routing
Apr 23 10:59:34 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
Apr 23 10:59:34 localhost kernel: ** causes a device to stop working, it is probably because the
Apr 23 10:59:34 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
Apr 23 10:59:34 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
Apr 23 10:59:34 localhost kernel: ** behavior.  If this argument makes the device work again,
Apr 23 10:59:34 localhost kernel: ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
Apr 23 10:59:34 localhost kernel: ** so I can fix the driver.
Apr 23 10:59:34 localhost kernel: audit: initializing netlink socket (disabled)
Apr 23 10:59:34 localhost kernel: audit(1114268343.229:0): initialized
Apr 23 10:59:34 localhost kernel: VFS: Disk quotas dquot_6.5.1
Apr 23 10:59:34 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 23 10:59:34 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Apr 23 10:59:34 localhost kernel: devfs: boot_options: 0x0
Apr 23 10:59:34 localhost kernel: Initializing Cryptographic API
Apr 23 10:59:34 localhost kernel: Applying VIA southbridge workaround.
Apr 23 10:59:34 localhost kernel: PCI: Disabling Via external APIC routing
Apr 23 10:59:34 localhost kernel: isapnp: Scanning for PnP cards...
Apr 23 10:59:34 localhost kernel: isapnp: No Plug & Play device found
Apr 23 10:59:34 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 23 10:59:34 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 23 10:59:34 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Apr 23 10:59:34 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 23 10:59:34 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 23 10:59:34 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 23 10:59:34 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 23 10:59:34 localhost kernel: io scheduler noop registered
Apr 23 10:59:34 localhost kernel: io scheduler anticipatory registered
Apr 23 10:59:34 localhost kernel: io scheduler deadline registered
Apr 23 10:59:34 localhost kernel: io scheduler cfq registered
Apr 23 10:59:34 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Apr 23 10:59:34 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Apr 23 10:59:34 localhost kernel: EISA: Probing bus 0 at eisa0
Apr 23 10:59:34 localhost kernel: Cannot allocate resource for EISA slot 4
Apr 23 10:59:34 localhost kernel: Cannot allocate resource for EISA slot 5
Apr 23 10:59:34 localhost kernel: Cannot allocate resource for EISA slot 6
Apr 23 10:59:34 localhost kernel: EISA: Detected 0 cards.
Apr 23 10:59:34 localhost kernel: NET: Registered protocol family 2
Apr 23 10:59:34 localhost kernel: IP: routing cache hash table of 4096 buckets, 32Kbytes
Apr 23 10:59:34 localhost kernel: TCP: Hash tables configured (established 32768 bind 65536)
Apr 23 10:59:34 localhost kernel: NET: Registered protocol family 8
Apr 23 10:59:34 localhost kernel: NET: Registered protocol family 20
Apr 23 10:59:34 localhost kernel: Restarting tasks...<6> Strange, kswapd0 not stopped
Apr 23 10:59:34 localhost kernel:  Strange, kseriod not stopped
Apr 23 10:59:34 localhost kernel:  done
Apr 23 10:59:34 localhost kernel: ACPI wakeup devices: 
Apr 23 10:59:34 localhost kernel: SLPB PCI0 USB0 USB1 MODM UAR1 UAR2 LPT1 
Apr 23 10:59:34 localhost kernel: ACPI: (supports S0 S1 S4 S5)
Apr 23 10:59:34 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Apr 23 10:59:34 localhost kernel: RAMDISK: Loading 4248KiB [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^Hdone.
Apr 23 10:59:34 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Apr 23 10:59:34 localhost kernel: Freeing unused kernel memory: 224k freed
Apr 23 10:59:34 localhost kernel: ACPI: CPU0 (power states: C1[C1] C2[C2])
Apr 23 10:59:34 localhost kernel: ACPI: Processor [CPU0] (supports 2 throttling states)
Apr 23 10:59:34 localhost kernel: NET: Registered protocol family 1
Apr 23 10:59:34 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 23 10:59:34 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 23 10:59:34 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:07.1
Apr 23 10:59:34 localhost kernel: VP_IDE: chipset revision 6
Apr 23 10:59:34 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Apr 23 10:59:34 localhost kernel: VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
Apr 23 10:59:34 localhost kernel:     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
Apr 23 10:59:34 localhost kernel:     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:DMA
Apr 23 10:59:34 localhost kernel: Probing IDE interface ide0...
Apr 23 10:59:34 localhost kernel: hda: WDC WD400EB-00CPF0, ATA DISK drive
Apr 23 10:59:34 localhost kernel: elevator: using anticipatory as default io scheduler
Apr 23 10:59:34 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 23 10:59:34 localhost kernel: hda: max request size: 128KiB
Apr 23 10:59:34 localhost kernel: hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Apr 23 10:59:34 localhost kernel: hda: cache flushes not supported
Apr 23 10:59:34 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Apr 23 10:59:34 localhost kernel: Probing IDE interface ide1...
Apr 23 10:59:34 localhost kernel: hdc: SONY CD-RW CRX210E1, ATAPI CD/DVD-ROM drive
Apr 23 10:59:34 localhost kernel: hdd: IDE DVD-ROM 16X, ATAPI CD/DVD-ROM drive
Apr 23 10:59:34 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Apr 23 10:59:34 localhost kernel: Probing IDE interface ide2...
Apr 23 10:59:34 localhost kernel: Probing IDE interface ide3...
Apr 23 10:59:34 localhost kernel: Probing IDE interface ide4...
Apr 23 10:59:34 localhost kernel: Probing IDE interface ide5...
Apr 23 10:59:34 localhost kernel: Stopping tasks: ==|
Apr 23 10:59:34 localhost kernel: Freeing memory...  ^H-^H\^H|^H/^Hdone (455 pages freed)
Apr 23 10:59:34 localhost kernel: Restarting tasks... done
Apr 23 10:59:34 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Apr 23 10:59:34 localhost kernel: kjournald starting.  Commit interval 5 seconds
Apr 23 10:59:34 localhost kernel: Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1
Apr 23 10:59:34 localhost kernel: EXT3 FS on hda1, internal journal
Apr 23 10:59:34 localhost kernel: hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache
Apr 23 10:59:34 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Apr 23 10:59:34 localhost kernel: hdd: ATAPI 44X DVD-ROM drive, 512kB Cache
Apr 23 10:59:34 localhost kernel: parport_pc: VIA 686A/8231 detected
Apr 23 10:59:34 localhost kernel: parport_pc: probing current configuration
Apr 23 10:59:34 localhost kernel: parport_pc: Current parallel port base: 0x378
Apr 23 10:59:34 localhost kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
Apr 23 10:59:34 localhost kernel: parport_pc: VIA parallel port: io=0x378, irq=7
Apr 23 10:59:34 localhost kernel: lp0: using parport0 (interrupt-driven).
Apr 23 10:59:34 localhost kernel: mice: PS/2 mouse device common for all mice
Apr 23 10:59:34 localhost kernel: input: PS/2 Logitech Mouse on isa0060/serio1
Apr 23 10:59:34 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Apr 23 10:59:34 localhost kernel: nvidia: module license 'NVIDIA' taints kernel.
Apr 23 10:59:34 localhost kernel: ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Apr 23 10:59:34 localhost kernel: PCI: setting IRQ 11 as level-triggered
Apr 23 10:59:34 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 11 (level, low) -> IRQ 11
Apr 23 10:59:34 localhost kernel: NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
Apr 23 10:59:34 localhost kernel: Capability LSM initialized
Apr 23 10:59:34 localhost kernel: ts: Compaq touchscreen protocol output
Apr 23 10:59:34 localhost kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
Apr 23 10:59:34 localhost kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Apr 23 10:59:34 localhost kernel: cdrom: open failed.
Apr 23 10:59:34 localhost kernel: cdrom: open failed.
Apr 23 10:59:34 localhost kernel: Real Time Clock Driver v1.12
Apr 23 10:59:34 localhost kernel: input: PC Speaker
Apr 23 10:59:34 localhost kernel: inserting floppy driver for 2.6.10-5-386
Apr 23 10:59:34 localhost kernel: Floppy drive(s): fd0 is 1.44M
Apr 23 10:59:34 localhost kernel: FDC 0 is a post-1991 82077
Apr 23 10:59:34 localhost kernel: agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
Apr 23 10:59:34 localhost kernel: agpgart: Maximum main memory to use for agp memory: 439M
Apr 23 10:59:34 localhost kernel: agpgart: AGP aperture is 32M @ 0xe0000000
Apr 23 10:59:34 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Apr 23 10:59:34 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 23 10:59:34 localhost kernel: shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 23 10:59:34 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
Apr 23 10:59:34 localhost kernel: pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 23 10:59:34 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
Apr 23 10:59:34 localhost kernel: usbcore: registered new driver usbfs
Apr 23 10:59:34 localhost kernel: usbcore: registered new driver hub
Apr 23 10:59:34 localhost kernel: USB Universal Host Controller Interface driver v2.2
Apr 23 10:59:34 localhost kernel: ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
Apr 23 10:59:34 localhost kernel: PCI: setting IRQ 5 as level-triggered
Apr 23 10:59:34 localhost kernel: ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 5 (level, low) -> IRQ 5
Apr 23 10:59:34 localhost kernel: uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Apr 23 10:59:34 localhost kernel: uhci_hcd 0000:00:07.2: irq 5, io base 0xd400
Apr 23 10:59:34 localhost kernel: uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Apr 23 10:59:34 localhost kernel: hub 1-0:1.0: USB hub found
Apr 23 10:59:34 localhost kernel: hub 1-0:1.0: 2 ports detected
Apr 23 10:59:34 localhost kernel: ACPI: PCI interrupt 0000:00:07.3[D] -> GSI 5 (level, low) -> IRQ 5
Apr 23 10:59:34 localhost kernel: uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Apr 23 10:59:34 localhost kernel: uhci_hcd 0000:00:07.3: irq 5, io base 0xd800
Apr 23 10:59:34 localhost kernel: uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
Apr 23 10:59:34 localhost kernel: hub 2-0:1.0: USB hub found
Apr 23 10:59:34 localhost kernel: hub 2-0:1.0: 2 ports detected
Apr 23 10:59:34 localhost kernel: ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
Apr 23 10:59:34 localhost kernel: PCI: setting IRQ 10 as level-triggered
Apr 23 10:59:34 localhost kernel: ACPI: PCI interrupt 0000:00:07.5[C] -> GSI 10 (level, low) -> IRQ 10
Apr 23 10:59:34 localhost kernel: PCI: Setting latency timer of device 0000:00:07.5 to 64
Apr 23 10:59:34 localhost kernel: natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
Apr 23 10:59:34 localhost kernel:   originally by Donald Becker <becker@scyld.com>
Apr 23 10:59:34 localhost kernel:   [http://www.scyld.com/network/natsemi.html](http://www.scyld.com/network/natsemi.html)
Apr 23 10:59:34 localhost kernel:   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
Apr 23 10:59:34 localhost kernel: ACPI: PCI interrupt 0000:00:11.0[A] -> GSI 11 (level, low) -> IRQ 11
Apr 23 10:59:34 localhost kernel: natsemi eth0: NatSemi DP8381[56] at 0xe5000000 (0000:00:11.0), 00:09:5b:05:2b:9e, IRQ 11, port TP.
Apr 23 10:59:34 localhost kernel: eth0: DSPCFG accepted after 0 usec.
Apr 23 10:59:34 localhost kernel: eth0: link up.
Apr 23 10:59:34 localhost kernel: eth0: Setting full-duplex based on negotiated link capability.
Apr 23 10:59:34 localhost kernel: NET: Registered protocol family 17
Apr 23 10:59:34 localhost kernel: NET: Registered protocol family 10
Apr 23 10:59:34 localhost kernel: Disabled Privacy Extensions on device c02f0500(lo)
Apr 23 10:59:34 localhost kernel: IPv6 over IPv4 tunneling driver
Apr 23 10:59:35 localhost udev[5511]: creating device node '/dev/vcs7'
Apr 23 10:59:35 localhost udev[5513]: creating device node '/dev/vcsa7'
Apr 23 10:59:35 localhost udev[5537]: removing device node '/dev/vcsa2'
Apr 23 10:59:35 localhost udev[5582]: removing device node '/dev/vcs6'
Apr 23 10:59:35 localhost udev[5590]: removing device node '/dev/vcs5'
Apr 23 10:59:35 localhost udev[5598]: removing device node '/dev/vcsa5'
Apr 23 10:59:35 localhost udev[5606]: removing device node '/dev/vcsa4'
Apr 23 10:59:35 localhost udev[5637]: removing device node '/dev/vcsa6'
Apr 23 10:59:35 localhost udev[5645]: removing device node '/dev/vcs4'
Apr 23 10:59:35 localhost udev[5653]: removing device node '/dev/vcsa3'
Apr 23 10:59:35 localhost udev[5661]: removing device node '/dev/vcs2'
Apr 23 10:59:35 localhost udev[5679]: removing device node '/dev/vcs3'
Apr 23 10:59:35 localhost udev[5745]: removing device node '/dev/vcs7'
Apr 23 10:59:35 localhost udev[5751]: removing device node '/dev/vcsa7'
Apr 23 10:59:36 localhost kernel: ACPI: Power Button (FF) [PWRF]
Apr 23 10:59:36 localhost kernel: ACPI: Sleep Button (CM) [SLPB]
Apr 23 10:59:36 localhost kernel: ibm_acpi: ec object not found
Apr 23 10:59:36 localhost udev[5921]: creating device node '/dev/vcs7'
Apr 23 10:59:36 localhost udev[5923]: creating device node '/dev/vcsa7'
Apr 23 10:59:37 localhost kernel: apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Apr 23 10:59:37 localhost kernel: apm: overridden by ACPI.
Apr 23 10:59:39 localhost kernel: agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Apr 23 10:59:39 localhost kernel: agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Apr 23 10:59:39 localhost kernel: agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Apr 23 10:59:39 localhost kernel: agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Apr 23 10:59:39 localhost kernel: agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Apr 23 10:59:39 localhost kernel: agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Apr 23 10:59:42 localhost postfix/master[6272]: daemon started -- version 2.1.5
Apr 23 10:59:42 localhost anacron[6432]: Anacron 2.3 started on 2005-04-23
Apr 23 10:59:42 localhost anacron[6432]: Will run job `cron.daily' in 5 min.
Apr 23 10:59:42 localhost anacron[6432]: Jobs will be executed sequentially
Apr 23 10:59:42 localhost /usr/sbin/cron[6453]: (CRON) INFO (pidfile fd = 3)
Apr 23 10:59:42 localhost /usr/sbin/cron[6454]: (CRON) STARTUP (fork ok)
Apr 23 10:59:43 localhost /usr/sbin/cron[6454]: (CRON) INFO (Running @reboot jobs)
Apr 23 10:59:43 localhost udev[6483]: creating device node '/dev/vcs2'
Apr 23 10:59:43 localhost udev[6485]: creating device node '/dev/vcs3'
Apr 23 10:59:43 localhost udev[6487]: creating device node '/dev/vcsa2'
Apr 23 10:59:43 localhost udev[6491]: creating device node '/dev/vcsa3'
Apr 23 10:59:43 localhost udev[6493]: creating device node '/dev/vcs5'
Apr 23 10:59:43 localhost udev[6497]: creating device node '/dev/vcsa4'
Apr 23 10:59:43 localhost udev[6499]: creating device node '/dev/vcs6'
Apr 23 10:59:43 localhost udev[6489]: creating device node '/dev/vcs4'
Apr 23 10:59:43 localhost udev[6501]: creating device node '/dev/vcsa6'
Apr 23 10:59:43 localhost udev[6495]: creating device node '/dev/vcsa5'
Apr 23 10:59:43 localhost kernel: eth0: no IPv6 routers present
Apr 23 11:00:01 localhost gconfd (jr-6629): starting (version 2.10.0), pid 6629 user 'jr'
Apr 23 11:00:01 localhost gconfd (jr-6629): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr 23 11:00:01 localhost gconfd (jr-6629): Resolved address "xml:readwrite:/home/jr/.gconf" to a writable configuration source at position 1
Apr 23 11:00:01 localhost gconfd (jr-6629): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr 23 11:00:11 localhost gconfd (jr-6629): Resolved address "xml:readwrite:/home/jr/.gconf" to a writable configuration source at position 0[/HTML]

---

### Post by nad on 2005-04-23
Please post your logs in a code box (<code>...</code>) next time.

Apr 23 10:59:34 localhost kernel: Cannot allocate resource for EISA slot 4
Apr 23 10:59:34 localhost kernel: Cannot allocate resource for EISA slot 5
Apr 23 10:59:34 localhost kernel: Cannot allocate resource for EISA slot 6
Apr 23 10:59:34 localhost kernel: EISA: Detected 0 cards.

Are you having problems? You may want to include one or more of the boot parameters acpi=off | noapic | pci=usepirqmask as you have a via chipset.

Dan M

---

### Post by denzilla on 2005-04-23
I just read where someone was advised to examine their syslog and thought I'd take a look at mine.

Is it advisable to tun off acpi and apm with Linux? seems like its more trouble than its worth to enable it. Any cons to it being disabled?

*I turned acpi and apm off in bios and that error you detected isn't there anymore, but I did see this:

"Apr 23 12:30:57 localhost kernel: Restarting tasks...<6> Strange, kswapd0 not stopped
Apr 23 12:30:57 localhost kernel:  Strange, kpnpbiosd not stopped
Apr 23 12:30:57 localhost kernel:  Strange, kseriod not stopped"

---

### Post by nad on 2005-04-23
You may want to leave apm on. The kernel may kick out some warnings but your computer will not poweroff without it. You will have to manually turn off the box.

Dan M

---

### Post by alastair on 2005-04-23
No - everything looks OK.

---

