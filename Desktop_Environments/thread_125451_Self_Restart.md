---
title: "Self Restart"
date: 2006-02-04
forum: Desktop Environments
---

### Post by theQmaster on 2006-02-04
My machine runs all the time... from time to time I've noticed that it self restarts. I looked up the system events and I'd seen the following message.
Can anyone tell me what can be wrong ? Looks like a hardware problem.:confused: 


On Thu, Feb 02, 2006 at 05:24:24AM -0600, [email]logcheck@localhost.loca[/email]ldomain wrote:
> This email is sent by logcheck. If you wish to no-longer receive it,
> you can either deinstall the logcheck package or modify its
> configuration file (/etc/logcheck/logcheck.conf).
> 
> Security Events
> =-=-=-=-=-=-=-=
> Feb  2 05:23:49 servername kernel: ** driver failed to call pci_enable_device().  As a temporary
> Feb  2 05:24:03 servername perl: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root
> 
> System Events
> =-=-=-=-=-=-=
> Feb  2 05:23:48 servername syslogd 1.4.1#16ubuntu6: restart.
> Feb  2 05:23:48 servername kernel: Inspecting /boot/System.map-2.6.10-6-686
> Feb  2 05:23:48 servername kernel: Loaded 26814 symbols from /boot/System.map-2.6.10-6-686.
> Feb  2 05:23:48 servername kernel: Symbols match kernel version 2.6.10.
> Feb  2 05:23:48 servername kernel: No module symbols loaded - kernel modules not enabled.
> Feb  2 05:23:48 servername kernel: Linux version 2.6.10-6-686 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Mon Jan 16 18:36:48 UTC 2006
> Feb  2 05:23:49 servername kernel: BIOS-provided physical RAM map:
> Feb  2 05:23:49 servername kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
> Feb  2 05:23:49 servername kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
> Feb  2 05:23:49 servername kernel:  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
> Feb  2 05:23:49 servername kernel:  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
> Feb  2 05:23:49 servername kernel:  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
> Feb  2 05:23:49 servername kernel:  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
> Feb  2 05:23:49 servername kernel:  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
> Feb  2 05:23:49 servername kernel:  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
> Feb  2 05:23:49 servername kernel: 127MB HIGHMEM available.
> Feb  2 05:23:49 servername kernel: 896MB LOWMEM available.
> Feb  2 05:23:49 servername kernel: On node 0 totalpages: 262064
> Feb  2 05:23:49 servername kernel:   DMA zone: 4096 pages, LIFO batch:1
> Feb  2 05:23:49 servername kernel:   Normal zone: 225280 pages, LIFO batch:16
> Feb  2 05:23:49 servername kernel:   HighMem zone: 32688 pages, LIFO batch:7
> Feb  2 05:23:49 servername kernel: DMI 2.3 present.
> Feb  2 05:23:49 servername kernel: ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f8c80
> Feb  2 05:23:49 servername kernel: ACPI: RSDT (v001 A M I  OEMRSDT  0x11000429 MSFT 0x00000097) @ 0x3ffb0000
> Feb  2 05:23:49 servername kernel: ACPI: FADT (v002 A M I  OEMFACP  0x11000429 MSFT 0x00000097) @ 0x3ffb0200
> Feb  2 05:23:49 servername kernel: ACPI: MADT (v001 A M I  OEMAPIC  0x11000429 MSFT 0x00000097) @ 0x3ffb0300
> Feb  2 05:23:49 servername kernel: ACPI: OEMB (v001 A M I  OEMBIOS  0x11000429 MSFT 0x00000097) @ 0x3ffc0040
> Feb  2 05:23:49 servername kernel: ACPI: DSDT (v001  K7UPG K7UPG001 0x00000001 INTL 0x02002026) @ 0x00000000
> Feb  2 05:23:49 servername kernel: ACPI: PM-Timer IO Port: 0x808
> Feb  2 05:23:49 servername kernel: ACPI: Local APIC address 0xfee00000
> Feb  2 05:23:49 servername kernel: ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
> Feb  2 05:23:49 servername kernel: Processor #0 6:10 APIC version 16
> Feb  2 05:23:49 servername kernel: ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
> Feb  2 05:23:49 servername kernel: IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
> Feb  2 05:23:49 servername kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
> Feb  2 05:23:49 servername kernel: ACPI: IRQ0 used by override.
> Feb  2 05:23:49 servername kernel: ACPI: IRQ2 used by override.
> Feb  2 05:23:49 servername kernel: ACPI: IRQ9 used by override.
> Feb  2 05:23:49 servername kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
> Feb  2 05:23:49 servername kernel: Using ACPI (MADT) for SMP configuration information
> Feb  2 05:23:49 servername kernel: Built 1 zonelists
> Feb  2 05:23:49 servername kernel: Kernel command line: root=/dev/sda1 ro quiet splash
> Feb  2 05:23:49 servername kernel: mapped APIC to ffffd000 (fee00000)
> Feb  2 05:23:49 servername kernel: mapped IOAPIC to ffffc000 (fec00000)
> Feb  2 05:23:49 servername kernel: Initializing CPU#0
> Feb  2 05:23:49 servername kernel: PID hash table entries: 4096 (order: 12, 65536 bytes)
> Feb  2 05:23:49 servername kernel: Detected 2084.378 MHz processor.
> Feb  2 05:23:49 servername kernel: Using pmtmr for high-res timesource
> Feb  2 05:23:49 servername kernel: Console: colour VGA+ 80x25
> Feb  2 05:23:49 servername kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
> Feb  2 05:23:49 servername kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
> Feb  2 05:23:49 servername kernel: Memory: 1031280k/1048256k available (1588k kernel code, 16308k reserved, 713k data, 164k init, 130752k highmem)
> Feb  2 05:23:49 servername kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
> Feb  2 05:23:49 servername kernel: Calibrating delay loop... 4120.57 BogoMIPS (lpj=2060288)
> Feb  2 05:23:49 servername kernel: Security Framework v1.0.0 initialized
> Feb  2 05:23:49 servername kernel: SELinux:  Disabled at boot.
> Feb  2 05:23:49 servername kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
> Feb  2 05:23:49 servername kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000
> Feb  2 05:23:49 servername kernel: CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000
> Feb  2 05:23:49 servername kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
> Feb  2 05:23:49 servername kernel: CPU: L2 Cache: 512K (64 bytes/line)
> Feb  2 05:23:49 servername kernel: CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000020 00000000 00000000
> Feb  2 05:23:49 servername kernel: Intel machine check architecture supported.
> Feb  2 05:23:49 servername kernel: Intel machine check reporting enabled on CPU#0.
> Feb  2 05:23:49 servername kernel: CPU: AMD Athlon(tm) XP 2800+ stepping 00
> Feb  2 05:23:49 servername kernel: Enabling fast FPU save and restore... done.
> Feb  2 05:23:49 servername kernel: Enabling unmasked SIMD FPU exception support... done.
> Feb  2 05:23:49 servername kernel: Checking 'hlt' instruction... OK.
> Feb  2 05:23:49 servername kernel: ACPI: Looking for DSDT in initrd... not found!
> Feb  2 05:23:49 servername kernel: ENABLING IO-APIC IRQs
> Feb  2 05:23:49 servername kernel: ..TIMER: vector=0x31 pin1=2 pin2=-1
> Feb  2 05:23:49 servername kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
> Feb  2 05:23:49 servername kernel: Freeing initrd memory: 4528k freed
> Feb  2 05:23:49 servername kernel: NET: Registered protocol family 16
> Feb  2 05:23:49 servername kernel: PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
> Feb  2 05:23:49 servername kernel: PCI: Using configuration type 1
> Feb  2 05:23:49 servername kernel: mtrr: v2.0 (20020519)
> Feb  2 05:23:49 servername kernel: ACPI: Subsystem revision 20050211
> Feb  2 05:23:49 servername kernel: ACPI: Interpreter enabled
> Feb  2 05:23:49 servername kernel: ACPI: Using IOAPIC for interrupt routing
> Feb  2 05:23:49 servername kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
> Feb  2 05:23:49 servername kernel: PCI: Probing PCI hardware (bus 00)
> Feb  2 05:23:49 servername kernel: PCI: Via IRQ fixup
> Feb  2 05:23:49 servername kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
> Feb  2 05:23:49 servername kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
> Feb  2 05:23:49 servername kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
> Feb  2 05:23:49 servername kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
> Feb  2 05:23:49 servername kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
> Feb  2 05:23:49 servername kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
> Feb  2 05:23:49 servername kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
> Feb  2 05:23:49 servername kernel: ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
> Feb  2 05:23:49 servername kernel: ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
> Feb  2 05:23:49 servername kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
> Feb  2 05:23:49 servername kernel: pnp: PnP ACPI init
> Feb  2 05:23:49 servername kernel: pnp: PnP ACPI: found 11 devices
> Feb  2 05:23:49 servername kernel: PnPBIOS: Disabled by ACPI PNP
> Feb  2 05:23:49 servername kernel: PCI: Using ACPI for IRQ routing
> Feb  2 05:23:49 servername kernel: ** PCI interrupts are no longer routed automatically.  If this
> Feb  2 05:23:49 servername kernel: ** causes a device to stop working, it is probably because the
> Feb  2 05:23:49 servername kernel: ** workaround, the "pci=routeirq" argument restores the old
> Feb  2 05:23:49 servername kernel: ** behavior.  If this argument makes the device work again,
> Feb  2 05:23:49 servername kernel: ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
> Feb  2 05:23:49 servername kernel: ** so I can fix the driver.
> Feb  2 05:23:49 servername kernel: audit: initializing netlink socket (disabled)
> Feb  2 05:23:49 servername kernel: audit(1138879435.145:0): initialized
> Feb  2 05:23:49 servername kernel: highmem bounce pool size: 64 pages
> Feb  2 05:23:49 servername kernel: VFS: Disk quotas dquot_6.5.1
> Feb  2 05:23:49 servername kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
> Feb  2 05:23:49 servername kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
> Feb  2 05:23:49 servername kernel: devfs: boot_options: 0x0
> Feb  2 05:23:49 servername kernel: Initializing Cryptographic API
> Feb  2 05:23:49 servername kernel: isapnp: Scanning for PnP cards...
> Feb  2 05:23:49 servername kernel: isapnp: No Plug & Play device found
> Feb  2 05:23:49 servername kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
> Feb  2 05:23:49 servername kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
> Feb  2 05:23:49 servername kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
> Feb  2 05:23:49 servername kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
> Feb  2 05:23:49 servername kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
> Feb  2 05:23:49 servername kernel: io scheduler noop registered
> Feb  2 05:23:49 servername kernel: io scheduler anticipatory registered
> Feb  2 05:23:49 servername kernel: io scheduler deadline registered
> Feb  2 05:23:49 servername kernel: io scheduler cfq registered
> Feb  2 05:23:49 servername kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
> Feb  2 05:23:49 servername kernel: NET: Registered protocol family 2
> Feb  2 05:23:49 servername kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
> Feb  2 05:23:49 servername kernel: TCP: Hash tables configured (established 262144 bind 65536)
> Feb  2 05:23:49 servername kernel: NET: Registered protocol family 8
> Feb  2 05:23:49 servername kernel: NET: Registered protocol family 20
> Feb  2 05:23:49 servername kernel: Restarting tasks...<6> Strange, kswapd0 not stopped
> Feb  2 05:23:49 servername kernel:  Strange, kseriod not stopped
> Feb  2 05:23:49 servername kernel:  done
> Feb  2 05:23:49 servername kernel: ACPI wakeup devices:
> Feb  2 05:23:49 servername kernel: PCI0 UAR1 MC97 USB1 USB2 USB3 USB4 ILAN
> Feb  2 05:23:49 servername kernel: ACPI: (supports S0 S1 S3 S4 S5)
> Feb  2 05:23:49 servername kernel: RAMDISK: cramfs filesystem found at block 0
> Feb  2 05:23:49 servername kernel: RAMDISK: Loading 4528KiB [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
> Feb  2 05:23:49 servername kernel: VFS: Mounted root (cramfs filesystem) readonly.
> Feb  2 05:23:49 servername kernel: Freeing unused kernel memory: 164k freed
> Feb  2 05:23:49 servername kernel: NET: Registered protocol family 1
> Feb  2 05:23:49 servername kernel: SCSI subsystem initialized
> Feb  2 05:23:49 servername kernel: libata version 1.10 loaded.
> Feb  2 05:23:49 servername kernel: sata_via version 1.1
> Feb  2 05:23:49 servername kernel: ACPI: PCI interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
> Feb  2 05:23:49 servername kernel: sata_via(0000:00:0f.0): routed to hard irq line 4
> Feb  2 05:23:49 servername kernel: ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 20
> Feb  2 05:23:49 servername kernel: ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 20
> Feb  2 05:23:49 servername kernel: ata1: dev 0 cfg 49:2f00 82:706b 83:7e01 84:4023 85:7069 86:3c01 87:4023 88:407f
> Feb  2 05:23:49 servername kernel: ata1: dev 0 ATA, max UDMA/133, 156301488 sectors: lba48
> Feb  2 05:23:49 servername kernel: ata1: dev 0 configured for UDMA/133
> Feb  2 05:23:49 servername kernel: scsi0 : sata_via
> Feb  2 05:23:49 servername kernel: ata2: no device found (phy stat 00000000)
> Feb  2 05:23:49 servername kernel: scsi1 : sata_via
> Feb  2 05:23:49 servername kernel: elevator: using anticipatory as default io scheduler
> Feb  2 05:23:49 servername kernel:   Vendor: ATA       Model: WDC WD800JD-00LU  Rev: 06.0
> Feb  2 05:23:49 servername kernel:   Type:   Direct-Access                      ANSI SCSI revision: 05
> Feb  2 05:23:49 servername kernel: SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
> Feb  2 05:23:49 servername kernel: SCSI device sda: drive cache: write back
> Feb  2 05:23:49 servername kernel: SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
> Feb  2 05:23:49 servername kernel: SCSI device sda: drive cache: write back
> Feb  2 05:23:49 servername kernel:  /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
> Feb  2 05:23:49 servername kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
> Feb  2 05:23:49 servername kernel: Stopping tasks: ==|
> Feb  2 05:23:49 servername kernel: Freeing memory...  ^H-^H\^H|^H/^Hdone (395 pages freed)
> Feb  2 05:23:49 servername kernel: Restarting tasks... done
> Feb  2 05:23:49 servername kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
> Feb  2 05:23:49 servername kernel: EXT3-fs: write access will be enabled during recovery.
> Feb  2 05:23:49 servername kernel: EXT3-fs: sda1: orphan cleanup on readonly fs
> Feb  2 05:23:49 servername kernel: kjournald starting.  Commit interval 5 seconds
> Feb  2 05:23:49 servername kernel: ext3_orphan_cleanup: deleting unreferenced inode 8683662
> Feb  2 05:23:49 servername kernel: ext3_orphan_cleanup: deleting unreferenced inode 8684826
> Feb  2 05:23:49 servername kernel: ext3_orphan_cleanup: deleting unreferenced inode 8684993
> Feb  2 05:23:49 servername kernel: ext3_orphan_cleanup: deleting unreferenced inode 8685022
> Feb  2 05:23:49 servername kernel: ext3_orphan_cleanup: deleting unreferenced inode 8650858
> Feb  2 05:23:49 servername kernel: EXT3-fs: sda1: 5 orphan inodes deleted
> Feb  2 05:23:49 servername kernel: EXT3-fs: recovery complete.
> Feb  2 05:23:49 servername kernel: EXT3-fs: mounted filesystem with ordered data mode.
> Feb  2 05:23:49 servername kernel: Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1
> Feb  2 05:23:49 servername kernel: EXT3 FS on sda1, internal journal
> Feb  2 05:23:49 servername kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
> Feb  2 05:23:49 servername kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
> Feb  2 05:23:49 servername kernel: Probing IDE interface ide0...
> Feb  2 05:23:49 servername kernel: Probing IDE interface ide1...
> Feb  2 05:23:49 servername kernel: hdc: Hewlett-Packard CD-Writer Plus 9300, ATAPI CD/DVD-ROM drive
> Feb  2 05:23:49 servername kernel: Probing IDE interface ide2...
> Feb  2 05:23:49 servername kernel: Probing IDE interface ide3...
> Feb  2 05:23:49 servername kernel: Probing IDE interface ide4...
> Feb  2 05:23:49 servername kernel: Probing IDE interface ide5...
> Feb  2 05:23:49 servername kernel: ide1 at 0x170-0x177,0x376 on irq 15
> Feb  2 05:23:49 servername kernel: hdc: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache
> Feb  2 05:23:49 servername kernel: Uniform CD-ROM driver Revision: 3.20
> Feb  2 05:23:49 servername kernel: parport: PnPBIOS parport detected.
> Feb  2 05:23:49 servername kernel: parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
> Feb  2 05:23:49 servername kernel: lp0: using parport0 (interrupt-driven).
> Feb  2 05:23:49 servername kernel: mice: PS/2 mouse device common for all mice
> Feb  2 05:23:49 servername kernel: Linux agpgart interface v0.100 (c) Dave Jones
> Feb  2 05:23:49 servername kernel: nvidia: module license 'NVIDIA' taints kernel.
> Feb  2 05:23:49 servername kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
> Feb  2 05:23:49 servername kernel: NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
> Feb  2 05:23:49 servername kernel: Capability LSM initialized
> Feb  2 05:23:49 servername kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
> Feb  2 05:23:49 servername kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
> Feb  2 05:23:49 servername kernel: Real Time Clock Driver v1.12
> Feb  2 05:23:49 servername kernel: input: PC Speaker
> Feb  2 05:23:49 servername kernel: inserting floppy driver for 2.6.10-6-686
> Feb  2 05:23:49 servername kernel: Floppy drive(s): fd0 is 1.44M
> Feb  2 05:23:49 servername kernel: FDC 0 is a post-1991 82077
> Feb  2 05:23:49 servername kernel: agpgart: Detected VIA KT880 chipset
> Feb  2 05:23:49 servername kernel: agpgart: Maximum main memory to use for agp memory: 941M
> Feb  2 05:23:49 servername kernel: agpgart: AGP aperture is 64M @ 0xe0000000
> Feb  2 05:23:49 servername kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
> Feb  2 05:23:49 servername kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
> Feb  2 05:23:49 servername kernel: shpchp: shpc_init : shpc_cap_offset == 0
> Feb  2 05:23:49 servername kernel: shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
> Feb  2 05:23:49 servername kernel: Evaluate _OSC Set fails. Status = 0x0005
> Feb  2 05:23:49 servername kernel: pciehp: add_host_bridge: status 5
> Feb  2 05:23:49 servername kernel: pciehp: Fails to gain control of native hot-plug
> Feb  2 05:23:49 servername kernel: VP_IDE: IDE controller at PCI slot 0000:00:0f.1
> Feb  2 05:23:49 servername kernel: ACPI: PCI interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
> Feb  2 05:23:49 servername kernel: VP_IDE: chipset revision 6
> Feb  2 05:23:49 servername kernel: VP_IDE: not 100%% native mode: will probe irqs later
> Feb  2 05:23:49 servername kernel: VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
> Feb  2 05:23:49 servername kernel:     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
> Feb  2 05:23:49 servername kernel: VP_IDE: port 0x0170 already claimed by ide1
> Feb  2 05:23:49 servername kernel: Probing IDE interface ide0...
> Feb  2 05:23:49 servername kernel: usbcore: registered new driver usbfs
> Feb  2 05:23:49 servername kernel: usbcore: registered new driver hub
> Feb  2 05:23:49 servername kernel: USB Universal Host Controller Interface driver v2.2
> Feb  2 05:23:49 servername kernel: ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.0: irq 21, io base 0xc000
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
> Feb  2 05:23:49 servername kernel: hub 1-0:1.0: USB hub found
> Feb  2 05:23:49 servername kernel: hub 1-0:1.0: 2 ports detected
> Feb  2 05:23:49 servername kernel: ACPI: PCI interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.1: irq 21, io base 0xc400
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
> Feb  2 05:23:49 servername kernel: hub 2-0:1.0: USB hub found
> Feb  2 05:23:49 servername kernel: hub 2-0:1.0: 2 ports detected
> Feb  2 05:23:49 servername kernel: ACPI: PCI interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.2: irq 21, io base 0xc800
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
> Feb  2 05:23:49 servername kernel: hub 3-0:1.0: USB hub found
> Feb  2 05:23:49 servername kernel: hub 3-0:1.0: 2 ports detected
> Feb  2 05:23:49 servername kernel: ACPI: PCI interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.3: irq 21, io base 0xcc00
> Feb  2 05:23:49 servername kernel: uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
> Feb  2 05:23:49 servername kernel: hub 4-0:1.0: USB hub found
> Feb  2 05:23:49 servername kernel: hub 4-0:1.0: 2 ports detected
> Feb  2 05:23:49 servername kernel: ACPI: PCI interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
> Feb  2 05:23:49 servername kernel: ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
> Feb  2 05:23:49 servername kernel: ehci_hcd 0000:00:10.4: irq 21, pci mem 0xfebff800
> Feb  2 05:23:49 servername kernel: ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
> Feb  2 05:23:49 servername kernel: ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
> Feb  2 05:23:49 servername kernel: hub 5-0:1.0: USB hub found
> Feb  2 05:23:49 servername kernel: hub 5-0:1.0: 8 ports detected
> Feb  2 05:23:49 servername kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
> Feb  2 05:23:49 servername kernel:          Please try dxs_support=1 or dxs_support=4 option
> Feb  2 05:23:49 servername kernel:          and report if it works on your machine.
> Feb  2 05:23:49 servername kernel: ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
> Feb  2 05:23:49 servername kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
> Feb  2 05:23:49 servername kernel: via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
> Feb  2 05:23:49 servername kernel: ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 23
> Feb  2 05:23:49 servername kernel: eth0: VIA Rhine II at 0xd400, 00:0b:6a:b7:c6:dc, IRQ 23.
> Feb  2 05:23:49 servername kernel: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
> Feb  2 05:23:49 servername kernel: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
> Feb  2 05:23:49 servername kernel: ACPI: Power Button (FF) [PWRF]
> Feb  2 05:23:49 servername kernel: ibm_acpi: ec object not found
> Feb  2 05:23:49 servername kernel: apm: BIOS not found.
> Feb  2 05:23:49 servername authdaemond.plain: modules="authpam", daemons=5
> Feb  2 05:23:51 servername postfix/master[5868]: daemon started -- version 2.1.5
> Feb  2 05:23:52 servername hal.hotplug[3439]: timout(10000 ms) waiting for /bus/pci/slots
> Feb  2 05:23:52 servername pci.agent[5984]: Bad PCI agent invocation
> Feb  2 05:24:00 servername anacron[6210]: Anacron 2.3 started on 2006-02-02
> Feb  2 05:24:00 servername anacron[6210]: Will run job `cron.daily' in 5 min.
> Feb  2 05:24:00 servername anacron[6210]: Jobs will be executed sequentially
> Feb  2 05:24:00 servername udev[6222]: creating device node '/dev/vcs7'
> Feb  2 05:24:00 servername udev[6224]: creating device node '/dev/vcsa7'
> Feb  2 05:24:04 servername udev[6357]: removing device node '/dev/vcs1'
> Feb  2 05:24:04 servername udev[6363]: removing device node '/dev/vcsa1'
> Feb  2 05:24:04 servername udev[6384]: creating device node '/dev/vcs1'
> Feb  2 05:24:04 servername udev[6388]: creating device node '/dev/vcs2'
> Feb  2 05:24:04 servername udev[6386]: creating device node '/dev/vcsa1'
> Feb  2 05:24:04 servername udev[6390]: creating device node '/dev/vcs3'
> Feb  2 05:24:04 servername udev[6392]: creating device node '/dev/vcsa2'
> Feb  2 05:24:04 servername udev[6394]: creating device node '/dev/vcs4'
> Feb  2 05:24:04 servername udev[6396]: creating device node '/dev/vcsa3'
> Feb  2 05:24:04 servername udev[6398]: creating device node '/dev/vcs5'
> Feb  2 05:24:04 servername udev[6400]: creating device node '/dev/vcsa4'
> Feb  2 05:24:04 servername udev[6404]: creating device node '/dev/vcsa6'
> Feb  2 05:24:04 servername udev[6406]: creating device node '/dev/vcsa5'
> Feb  2 05:24:04 servername udev[6402]: creating device node '/dev/vcs6'
> Feb  2 05:24:06 servername webmin[6195]: Webmin starting
> Feb  2 05:24:13 servername kdm_greet[6699]: Can't open default user face
> 
:confused:

---

### Post by theQmaster on 2006-02-13
Anyone, any ideas ?

Q

---

### Post by Adrian on 2006-02-13
[QUOTE=theQmaster]Anyone, any ideas ?

Q[/QUOTE]

Looks like a hardware problem to me, but I can't extract any useful information from your log. Has it always been that way or is it something that has started happening recently?

My computer reboots spontaneously from time to time, and that is because the capacitors on the mainboard have started to leak.

---

### Post by dcstar on 2006-02-14
Unless your PC is on a (good) UPS, a power spike/dip can cause a reboot.

---

### Post by theQmaster on 2006-02-14
Thanks Adrian and Thanks dcstar.

I do have an UPS and the computer is fairly new built. A friend suggested that my nvidia driver may not work fine with ACPI feature(power management). I incline to believe him for now. I will try to upgrade the driver first.

Q
[www.goodstockimages.com](www.goodstockimages.com)

---

