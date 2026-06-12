---
title: "can not sut down dapper 6.0.6"
date: 2006-06-04
forum: Desktop Environments
---

### Post by gabrielp on 2006-06-04
I did a clean install to Dapper ,but can not perform shut down ,
When I chhose sut down i get up to :Shutting down LVM Volume groups
                                                          Will now halt ,
And thats it ,I hear a click but computer does not shut down ,
I tried noacpi and noapm at grub with no success .
Thanks for your help .

---

### Post by Peter76 on 2006-06-04
Hi, I just gave a solution to this problem here: [http://www.ubuntuforums.org/showthread.php?t=187186](http://www.ubuntuforums.org/showthread.php?t=187186)

Good luck

---

### Post by gabrielp on 2006-06-04
Sorry it did not work ,can i downgrade to breezy kernel?

---

### Post by Peter76 on 2006-06-04
can you post the output of dmesg?

---

### Post by gabrielp on 2006-06-04
[QUOTE=Peter76]can you post the output of dmesg?[/QUOTE]
gabi@gabi-desktop:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-686 (buildd@rothera) (gcc version 4.0.3  (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001ffb0000 (usable)
[4294667.296000]  BIOS-e820: 000000001ffb0000 - 000000001ffbe000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001ffbe000 - 000000001fff0000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001fff0000 - 0000000020000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000ff780
[4294667.296000] On node 0 totalpages: 130992
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126896 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v002 ACPIAM                                ) @ 0x00 0fb1e0
[4294667.296000] ACPI: XSDT (v001 A M I  OEMXSDT  0x06000516 MSFT 0x00000097) @ 0x1ffb0100
[4294667.296000] ACPI: FADT (v003 A M I  OEMFACP  0x06000516 MSFT 0x00000097) @ 0x1ffb0290
[4294667.296000] ACPI: MADT (v001 A M I  OEMAPIC  0x06000516 MSFT 0x00000097) @ 0x1ffb0390
[4294667.296000] ACPI: OEMB (v001 A M I  AMI_OEM  0x06000516 MSFT 0x00000097) @ 0x1ffbe040
[4294667.296000] ACPI: MCFG (v001 A M I  OEMMCFG  0x06000516 MSFT 0x00000097) @ 0x1ffb6b70
[4294667.296000] ACPI: DSDT (v001  A0319 A0319001 0x00000001 INTL 0x02002026) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:4 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:df b80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 2677.815 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294668.764000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes )
[4294668.764000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.773000] Memory: 507384k/523968k available (2101k kernel code, 15940k re served, 592k data, 332k init, 0k highmem)
[4294668.773000] Checking if this processor honours the WP bit even in superviso r mode... Ok.
[4294668.833000] Calibrating delay using timer specific routine.. 5357.08 BogoMI PS (lpj=2678540)
[4294668.833000] Security Framework v1.0.0 initialized
[4294668.833000] SELinux:  Disabled at boot.
[4294668.833000] Mount-cache hash table entries: 512
[4294668.833000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 0 0000000 0000651d 00000000 00000000
[4294668.833000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00 000000 0000651d 00000000 00000000
[4294668.833000] monitor/mwait feature present.
[4294668.833000] using mwait in idle threads.
[4294668.833000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294668.833000] CPU: L2 cache: 1024K
[4294668.833000] CPU: Hyper-Threading is disabled
[4294668.833000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080  0000651d 00000000 00000000
[4294668.833000] mtrr: v2.0 (20020519)
[4294668.833000] Enabling fast FPU save and restore... done.
[4294668.833000] Enabling unmasked SIMD FPU exception support... done.
[4294668.833000] Checking 'hlt' instruction... OK.
[4294668.837000] SMP alternatives: switching to UP code
[4294668.837000] checking if image is initramfs... it is
[4294669.383000] Freeing initrd memory: 6798k freed
[4294669.388000] ACPI: Looking for DSDT ... not found!
[4294669.391000] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 01
[4294669.391000] Total of 1 processors activated (5357.08 BogoMIPS).
[4294669.391000] ENABLING IO-APIC IRQs
[4294669.391000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294669.502000] Brought up 1 CPUs
[4294669.502000] NET: Registered protocol family 16
[4294669.502000] EISA bus registered
[4294669.502000] ACPI: bus type pci registered
[4294669.502000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=4
[4294669.502000] PCI: Using MMCONFIG
[4294669.503000] ACPI: Subsystem revision 20051216
[4294669.513000] ACPI: Interpreter enabled
[4294669.513000] ACPI: Using IOAPIC for interrupt routing
[4294669.515000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.515000] PCI: Probing PCI hardware (bus 00)
[4294669.518000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294669.519000] Boot video device is 0000:04:00.0
[4294669.519000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.519000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.522000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[4294669.522000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[4294669.523000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[4294669.523000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[4294669.531000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15 )
[4294669.531000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15 )
[4294669.532000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 10 11 12 14 15 )
[4294669.532000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15 )
[4294669.532000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15)  *0, disabled.
[4294669.533000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15 )
[4294669.533000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15)  *0, disabled.
[4294669.533000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15 )
[4294669.533000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.533000] pnp: PnP ACPI init
[4294669.540000] pnp: PnP ACPI: found 18 devices
[4294669.540000] PnPBIOS: Disabled by ACPI PNP
[4294669.540000] PCI: Using ACPI for IRQ routing
[4294669.540000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps , post a report
[4294669.556000] pnp: 00:06: ioport range 0x290-0x297 has been reserved
[4294669.557000] PCI: Bridge: 0000:00:01.0
[4294669.557000]   IO window: e000-efff
[4294669.557000]   MEM window: cdf00000-cfffffff
[4294669.557000]   PREFETCH window: d0000000-dfffffff
[4294669.557000] PCI: Bridge: 0000:00:1c.0
[4294669.557000]   IO window: d000-dfff
[4294669.557000]   MEM window: disabled.
[4294669.557000]   PREFETCH window: disabled.
[4294669.557000] PCI: Bridge: 0000:00:1c.1
[4294669.557000]   IO window: c000-cfff
[4294669.557000]   MEM window: cde00000-cdefffff
[4294669.557000]   PREFETCH window: disabled.
[4294669.557000] PCI: Bridge: 0000:00:1e.0
[4294669.557000]   IO window: b000-bfff
[4294669.557000]   MEM window: cdd00000-cddfffff
[4294669.557000]   PREFETCH window: disabled.
[4294669.557000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> I RQ 169
[4294669.557000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294669.557000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> I RQ 169
[4294669.557000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294669.557000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> I RQ 177
[4294669.557000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[4294669.557000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294669.558000] audit: initializing netlink socket (disabled)
[4294669.558000] audit(1149450396.556:1): initialized
[4294669.558000] VFS: Disk quotas dquot_6.5.1
[4294669.558000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.558000] Initializing Cryptographic API
[4294669.558000] io scheduler noop registered
[4294669.558000] io scheduler anticipatory registered
[4294669.558000] io scheduler deadline registered
[4294669.558000] io scheduler cfq registered
[4294669.558000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> I RQ 169
[4294669.558000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294669.558000] assign_interrupt_mode Found MSI capability
[4294669.558000] Allocate Port Service[pcie00]
[4294669.558000] Allocate Port Service[pcie03]
[4294669.558000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> I RQ 169
[4294669.558000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294669.558000] assign_interrupt_mode Found MSI capability
[4294669.558000] Allocate Port Service[pcie00]
[4294669.558000] Allocate Port Service[pcie02]
[4294669.558000] Allocate Port Service[pcie03]
[4294669.558000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> I RQ 177
[4294669.558000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[4294669.558000] assign_interrupt_mode Found MSI capability
[4294669.558000] Allocate Port Service[pcie00]
[4294669.558000] Allocate Port Service[pcie02]
[4294669.558000] Allocate Port Service[pcie03]
[4294669.559000] isapnp: Scanning for PnP cards...
[4294669.914000] isapnp: No Plug & Play device found
[4294669.935000] Real Time Clock Driver v1.12
[4294669.935000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 i rq 1,12
[4294669.937000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.937000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.937000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shari ng enabled
[4294669.937000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.940000] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.940000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294669.941000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.941000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294669.941000] mice: PS/2 mouse device common for all mice
[4294669.941000] EISA: Probing bus 0 at eisa.0
[4294669.941000] Cannot allocate resource for EISA slot 8
[4294669.941000] EISA: Detected 0 cards.
[4294669.941000] NET: Registered protocol family 2
[4294669.951000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294669.951000] TCP established hash table entries: 32768 (order: 6, 393216 byt es)
[4294669.951000] TCP bind hash table entries: 32768 (order: 6, 393216 bytes)
[4294669.951000] TCP: Hash tables configured (established 32768 bind 32768)
[4294669.951000] TCP reno registered
[4294669.951000] TCP bic registered
[4294669.951000] NET: Registered protocol family 1
[4294669.951000] NET: Registered protocol family 8
[4294669.951000] NET: Registered protocol family 20
[4294669.951000] Using IPI No-Shortcut mode
[4294669.951000] ACPI wakeup devices:
[4294669.951000] P0P1 P0P3 P0P4 P0P5 P0P6 P0P7 PS2K PS2M UAR1 USB1 USB2 USB3 USB 4 EUSB MC97
[4294669.951000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.951000] Freeing unused kernel memory: 332k freed
[4294669.964000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294669.997000] vga16fb: initializing
[4294669.997000] vga16fb: mapped to 0xc00a0000
[4294670.212000] Console: switching to colour frame buffer device 80x25
[4294670.212000] fb0: VGA16 VGA frame buffer device
[4294671.383000] Capability LSM initialized
[4294671.417000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294672.001000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294672.001000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> I RQ 217
[4294672.001000] ICH6: chipset revision 3
[4294672.001000] ICH6: not 100% native mode: will probe irqs later
[4294672.002000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb: DMA
[4294672.002000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd: pio
[4294672.002000] Probing IDE interface ide0...
[4294672.267000] hda: MAXTOR 6L040J2, ATA DISK drive
[4294672.675000] hdb: HL-DT-STDVDRRW GWA-4161B, ATAPI CD/DVD-ROM drive
[4294672.727000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.736000] Probing IDE interface ide1...
[4294673.262000] hda: max request size: 128KiB
[4294673.269000] hda: 78177792 sectors (40027 MB) w/1819KiB Cache, CHS=65535/16/ 63, UDMA(100)
[4294673.270000] hda: cache flushes supported
[4294673.270000]  hda: hda1 hda2 < hda5 hda6 >
[4294673.292000] hdb: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA( 33)
[4294673.292000] Uniform CD-ROM driver Revision: 3.20
[4294673.536000] SCSI subsystem initialized
[4294673.538000] ACPI: bus type scsi registered
[4294673.538000] libata version 1.20 loaded.
[4294673.540000] ata_piix 0000:00:1f.2: version 1.05
[4294673.540000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[4294673.540000] ata_pci_init_one: NO_LEGACY == 0
[4294673.540000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> I RQ 225
[4294673.540000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294673.540000] ata1: PATA max UDMA/133 cmd 0xA800 ctl 0xA402 bmdma 0x9400 irq 225
[4294673.540000] ata2: PATA max UDMA/133 cmd 0xA000 ctl 0x9802 bmdma 0x9408 irq 225
[4294673.710000] ata1: dev 0 cfg 00:045a 49:2f00 82:346b 83:7fe9 84:4773 85:3469  86:3c01 87:4763 88:207f 93:0000
[4294673.710000] ata1: dev 0 ATA-7, max UDMA/133, 160836480 sectors: LBA48
[4294673.711000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdff95540
[4294673.716000] ata1: dev 0 configured for UDMA/133
[4294673.716000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdff95540
[4294673.722000] scsi0 : ata_piix
[4294674.904000] ata2: disabling port
[4294674.904000] scsi1 : ata_piix
[4294674.904000]   Vendor: ATA       Model: HDS728080PLA380   Rev: PF2O
[4294674.904000]   Type:   Direct-Access                      ANSI SCSI revision : 05
[4294674.912000] Driver 'sd' needs updating - please use bus_type methods
[4294674.913000] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[4294674.913000] SCSI device sda: drive cache: write back
[4294674.916000] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[4294674.916000] SCSI device sda: drive cache: write back
[4294674.916000]  sda: sda1 sda2 < sda5 sda6 >
[4294674.960000] sd 0:0:0:0: Attached scsi disk sda
[4294675.217000] usbcore: registered new driver usbfs
[4294675.217000] usbcore: registered new driver hub
[4294675.219000] USB Universal Host Controller Interface driver v2.3
[4294675.219000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> I RQ 233
[4294675.219000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.219000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294675.220000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus num ber 1
[4294675.220000] uhci_hcd 0000:00:1d.0: irq 233, io base 0x00008000
[4294675.222000] hub 1-0:1.0: USB hub found
[4294675.222000] hub 1-0:1.0: 2 ports detected
[4294675.276000] ieee1394: Initialized config rom entry `ip1394'
[4294675.323000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> I RQ 225
[4294675.323000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.323000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294675.323000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus num ber 2
[4294675.324000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x00008400
[4294675.324000] hub 2-0:1.0: USB hub found
[4294675.324000] hub 2-0:1.0: 2 ports detected
[4294675.425000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> I RQ 217
[4294675.425000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294675.425000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294675.425000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus num ber 3
[4294675.425000] uhci_hcd 0000:00:1d.2: irq 217, io base 0x00008800
[4294675.426000] hub 3-0:1.0: USB hub found
[4294675.426000] hub 3-0:1.0: 2 ports detected
[4294675.527000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> I RQ 169
[4294675.527000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294675.527000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294675.527000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus num ber 4
[4294675.527000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x00009000
[4294675.528000] hub 4-0:1.0: USB hub found
[4294675.528000] hub 4-0:1.0: 2 ports detected
[4294675.529000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294675.632000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> I RQ 233
[4294675.632000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.632000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294675.632000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.632000] PCI: cache line size of 128 is not supported by device 0000:00: 1d.7
[4294675.632000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus num ber 5
[4294675.632000] ehci_hcd 0000:00:1d.7: irq 233, io mem 0xcdcffc00
[4294675.636000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 De c 2004
[4294675.636000] hub 5-0:1.0: USB hub found
[4294675.636000] hub 5-0:1.0: 8 ports detected
[4294675.738000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294675.738000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 21 (level, low) -> I RQ 50
[4294675.789000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[50]  MMIO=[cddff8 00-cddfffff]  Max Packet=[2048]
[4294675.818000] Probing IDE interface ide1...
[4294676.044000] usb 1-1: device not accepting address 2, error -71
[4294676.434000] Attempting manual resume
[4294676.467000] EXT3-fs: mounted filesystem with ordered data mode.
[4294676.485000] kjournald starting.  Commit interval 5 seconds
[4294676.779000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[4294677.050000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0001080000008225]
[4294677.124000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[4294682.220000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294683.875000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294683.880000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294683.938000] Linux agpgart interface v0.101 (c) Dave Jones
[4294683.967000] agpgart: Detected an Intel 915G Chipset.
[4294683.986000] agpgart: AGP aperture is 256M @ 0x0
[4294684.110000] hw_random: RNG not detected
[4294684.435000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> I RQ 169
[4294684.435000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294684.732000] input: PC Speaker as /class/input/input1
[4294684.891000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> I RQ 177
[4294684.891000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[4294684.891000] sky2 v0.15 addr 0xcdefc000 irq 177 Yukon-EC (0xb6) rev 2
[4294684.891000] sky2 eth0: addr 00:15:f2:2c:f2:04
[4294684.961000] parport: PnPBIOS parport detected.
[4294684.961000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTA TE,COMPAT,EPP,ECP,DMA]
[4294684.973000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[4294685.279000] Linux video capture interface: v1.00
[4294685.368000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera fo und. Type Flexcam 100 (SPCA561A)
[4294685.373000] usbcore: registered new driver spca5xx
[4294685.373000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57. 08 registered
[4294685.382000] ts: Compaq touchscreen protocol output
[4294685.777000] sky2 eth0: enabling interface
[4294685.961000] lp0: using parport0 (interrupt-driven).
[4294685.997000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294685.997000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294685.997000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294686.331000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294686.331000] apm: overridden by ACPI.
[4294686.513000] Adding 1510064k swap on /dev/hda5.  Priority:-1 extents:1 acros s:1510064k
[4294686.926000] NET: Registered protocol family 17
[4294687.262000] EXT3 FS on hda1, internal journal
[4294687.389000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294687.389000] md: bitmap version 4.39
[4294687.463000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control bo th
[4294687.864000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294688.531000] cdrom: open failed.
[4294691.451000] kjournald starting.  Commit interval 5 seconds
[4294691.452000] EXT3 FS on hda6, internal journal
[4294691.452000] EXT3-fs: mounted filesystem with ordered data mode.
[4294691.501000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294691.562000] NTFS volume version 3.1.
[4294691.686000] NTFS volume version 3.1.
[4294697.398000] ACPI: Power Button (FF) [PWRF]
[4294697.398000] ACPI: Power Button (CM) [PWRB]
[4294697.486000] ibm_acpi: ec object not found
[4294697.506000] pcc_acpi: loading...
[4294702.443000] ppdev: user-space parallel port driver
[4294702.738000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294702.738000] apm: disabled on user request.
[4294705.337000] Bluetooth: Core ver 2.8
[4294705.337000] NET: Registered protocol family 31
[4294705.337000] Bluetooth: HCI device and connection manager initialized
[4294705.337000] Bluetooth: HCI socket layer initialized
[4294705.499000] Bluetooth: L2CAP ver 2.8
[4294705.499000] Bluetooth: L2CAP socket layer initialized
[4294705.502000] Bluetooth: RFCOMM socket layer initialized
[4294705.502000] Bluetooth: RFCOMM TTY layer initialized
[4294705.502000] Bluetooth: RFCOMM ver 1.7
[4294707.285000] NET: Registered protocol family 10
[4294707.285000] lo: Disabled Privacy Extensions
[4294707.285000] IPv6 over IPv4 tunneling driver
[4294717.638000] eth0: no IPv6 routers present
gabi@gabi-desktop:~$

---

### Post by Peter76 on 2006-06-04
Pff you have a bit newer hardware than me... Could be a bios setting having to do with the power settings. I'll ponder a bit on htis and see if I come up with something. 
Good luck

---

