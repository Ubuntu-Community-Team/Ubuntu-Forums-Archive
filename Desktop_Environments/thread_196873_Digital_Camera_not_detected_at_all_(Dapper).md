---
title: "Digital Camera not detected at all (Dapper)"
date: 2006-06-14
forum: Desktop Environments
---

### Post by richardq on 2006-06-14
I've plugged and un-plugged the USB connector for my Canon 350D camera and nothing happens. Also, F-Spot and GThumb do not detect any camera from which to grab photos.

Is there something else I have to install? Simply no response from the system.

---

### Post by weijie90 on 2006-06-14
[QUOTE=richardq]I've plugged and un-plugged the USB connector for my Canon 350D camera and nothing happens. Also, F-Spot and GThumb do not detect any camera from which to grab photos.

Is there something else I have to install? Simply no response from the system.[/QUOTE]


please plug in your camera, press any buttons necessary, and start the terminal.
post whatever the command dmesg shows.

---

### Post by richardq on 2006-06-15
[QUOTE=weijie90]please plug in your camera, press any buttons necessary, and start the terminal.
post whatever the command dmesg shows.[/QUOTE]

Here you go:

```
richard@ubuntu:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-686 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2 006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000003f72fc00 (usable)
[4294667.296000]  BIOS-e820: 000000003f72fc00 - 000000003f730000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000003f730000 - 000000003f740000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000003f740000 - 000000003f7f0000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000003f7f0000 - 000000003f800000 (reserved)
[4294667.296000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fed13000 - 00000000fed1a000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fed1c000 - 00000000feda0000 (reserved)
[4294667.296000] 119MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000ff780
[4294667.296000] On node 0 totalpages: 259887
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 30511 pages, LIFO batch:7
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f4e50
[4294667.296000] ACPI: RSDT (v001 INTEL  D915GAV  0x20040609 MSFT 0x00000097) @ 0x3f730000
[4294667.296000] ACPI: FADT (v002 INTEL  D915GAV  0x20040609 MSFT 0x00000097) @ 0x3f730200
[4294667.296000] ACPI: MADT (v001 INTEL  D915GAV  0x20040609 MSFT 0x00000097) @ 0x3f730390
[4294667.296000] ACPI: MCFG (v001 INTEL  D915GAV  0x20040609 MSFT 0x00000097) @ 0x3f730400
[4294667.296000] ACPI: ASF! (v016 LEGEND I865PASF 0x00000001 INTL 0x02002026) @ 0x3f735f10
[4294667.296000] ACPI: TCPA (v001 INTEL  TBLOEMID 0x00000001 MSFT 0x00000097) @ 0x3f735fb0
[4294667.296000] ACPI: WDDT (v001 INTEL  OEMWDDT  0x00000001 INTL 0x02002026) @ 0x3f735fe4
[4294667.296000] ACPI: DSDT (v001 INTEL  D915GAV  0x00000001 INTL 0x02002026) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x408
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:3 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 40000000 (gap: 3f800000:a0800000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/sda6 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 2934.257 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.305000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.305000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.331000] Memory: 1018260k/1039548k available (2101k kernel code, 20512k reserved, 592k data, 332k init, 122044k highmem)
[4294667.331000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.392000] Calibrating delay using timer specific routine.. 5871.91 BogoMIPS (lpj=2935956)
[4294667.392000] Security Framework v1.0.0 initialized
[4294667.392000] SELinux:  Disabled at boot.
[4294667.392000] Mount-cache hash table entries: 512
[4294667.392000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[4294667.392000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[4294667.392000] monitor/mwait feature present.
[4294667.392000] using mwait in idle threads.
[4294667.392000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294667.392000] CPU: L2 cache: 1024K
[4294667.392000] CPU: Hyper-Threading is disabled
[4294667.392000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000 00000000
[4294667.392000] mtrr: v2.0 (20020519)
[4294667.392000] Enabling fast FPU save and restore... done.
[4294667.392000] Enabling unmasked SIMD FPU exception support... done.
[4294667.392000] Checking 'hlt' instruction... OK.
[4294667.396000] SMP alternatives: switching to UP code
[4294667.396000] checking if image is initramfs... it is
[4294667.990000] Freeing initrd memory: 6799k freed
[4294667.996000] ACPI: Looking for DSDT ... not found!
[4294668.006000] CPU0: Intel(R) Pentium(R) 4 CPU 2.93GHz stepping 04
[4294668.006000] Total of 1 processors activated (5871.91 BogoMIPS).
[4294668.006000] ENABLING IO-APIC IRQs
[4294668.006000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294668.117000] Brought up 1 CPUs
[4294668.117000] NET: Registered protocol family 16
[4294668.117000] EISA bus registered
[4294668.117000] ACPI: bus type pci registered
[4294668.118000] PCI: Using MMCONFIG
[4294668.118000] ACPI: Subsystem revision 20051216
[4294670.129000] ACPI: Interpreter enabled
[4294670.129000] ACPI: Using IOAPIC for interrupt routing
[4294670.129000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.129000] PCI: Probing PCI hardware (bus 00)
[4294670.132000] Boot video device is 0000:00:02.0
[4294670.133000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294670.134000] PCI: Transparent bridge - 0000:00:1e.0
[4294670.134000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.137000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[4294670.137000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[4294670.143000] ACPI: Power Resource [URP1] (off)
[4294670.143000] ACPI: Power Resource [FDDP] (off)
[4294670.143000] ACPI: Power Resource [LPTP] (off)
[4294670.143000] ACPI: Power Resource [URP2] (off)
[4294670.144000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[4294670.145000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[4294670.146000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294670.147000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294670.147000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[4294670.148000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294670.148000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294670.149000] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[4294670.149000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294670.150000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294670.150000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.150000] pnp: PnP ACPI init
[4294670.157000] pnp: PnP ACPI: found 13 devices
[4294670.157000] PnPBIOS: Disabled by ACPI PNP
[4294670.157000] PCI: Using ACPI for IRQ routing
[4294670.157000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.159000] pnp: 00:0b: ioport range 0x400-0x47f could not be reserved
[4294670.159000] pnp: 00:0b: ioport range 0x680-0x6ff has been reserved
[4294670.159000] pnp: 00:0b: ioport range 0x500-0x53f has been reserved
[4294670.159000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[4294670.159000] PCI: Bridge: 0000:00:01.0
[4294670.159000]   IO window: disabled.
[4294670.159000]   MEM window: ff200000-ff2fffff
[4294670.159000]   PREFETCH window: bf900000-bf9fffff
[4294670.159000] PCI: Bridge: 0000:00:1c.0
[4294670.159000]   IO window: disabled.
[4294670.159000]   MEM window: ff600000-ff6fffff
[4294670.159000]   PREFETCH window: bfd00000-bfdfffff
[4294670.159000] PCI: Bridge: 0000:00:1c.1
[4294670.159000]   IO window: disabled.
[4294670.159000]   MEM window: ff500000-ff5fffff
[4294670.159000]   PREFETCH window: bfc00000-bfcfffff
[4294670.159000] PCI: Bridge: 0000:00:1c.2
[4294670.159000]   IO window: disabled.
[4294670.159000]   MEM window: ff400000-ff4fffff
[4294670.159000]   PREFETCH window: bfb00000-bfbfffff
[4294670.159000] PCI: Bridge: 0000:00:1c.3
[4294670.159000]   IO window: disabled.
[4294670.159000]   MEM window: ff300000-ff3fffff
[4294670.159000]   PREFETCH window: bfa00000-bfafffff
[4294670.159000] PCI: Bridge: 0000:00:1e.0
[4294670.159000]   IO window: b000-bfff
[4294670.159000]   MEM window: ff700000-ff7fffff
[4294670.159000]   PREFETCH window: bfe00000-bfefffff
[4294670.159000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294670.159000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294670.159000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[4294670.159000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294670.159000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 169
[4294670.159000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[4294670.159000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[4294670.159000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[4294670.159000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 193
[4294670.159000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[4294670.159000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294670.160000] audit: initializing netlink socket (disabled)
[4294670.160000] audit(1150353606.158:1): initialized
[4294670.160000] highmem bounce pool size: 64 pages
[4294670.160000] VFS: Disk quotas dquot_6.5.1
[4294670.160000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.160000] Initializing Cryptographic API
[4294670.160000] io scheduler noop registered
[4294670.160000] io scheduler anticipatory registered
[4294670.160000] io scheduler deadline registered
[4294670.160000] io scheduler cfq registered
[4294670.160000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294670.160000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294670.160000] assign_interrupt_mode Found MSI capability
[4294670.160000] Allocate Port Service[pcie00]
[4294670.160000] Allocate Port Service[pcie03]
[4294670.160000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[4294670.160000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294670.160000] assign_interrupt_mode Found MSI capability
[4294670.161000] Allocate Port Service[pcie00]
[4294670.161000] Allocate Port Service[pcie02]
[4294670.161000] Allocate Port Service[pcie03]
[4294670.161000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 169
[4294670.161000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[4294670.161000] assign_interrupt_mode Found MSI capability
[4294670.161000] Allocate Port Service[pcie00]
[4294670.161000] Allocate Port Service[pcie02]
[4294670.161000] Allocate Port Service[pcie03]
[4294670.161000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[4294670.161000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[4294670.161000] assign_interrupt_mode Found MSI capability
[4294670.161000] Allocate Port Service[pcie00]
[4294670.161000] Allocate Port Service[pcie02]
[4294670.161000] Allocate Port Service[pcie03]
[4294670.161000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 193
[4294670.161000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[4294670.161000] assign_interrupt_mode Found MSI capability
[4294670.161000] Allocate Port Service[pcie00]
[4294670.161000] Allocate Port Service[pcie02]
[4294670.161000] Allocate Port Service[pcie03]
[4294670.161000] isapnp: Scanning for PnP cards...
[4294670.516000] isapnp: No Plug & Play device found
[4294670.536000] Real Time Clock Driver v1.12
[4294670.536000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[4294670.536000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[4294670.538000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.538000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.538000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.538000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.541000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.541000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.541000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.541000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.542000] mice: PS/2 mouse device common for all mice
[4294670.542000] EISA: Probing bus 0 at eisa.0
[4294670.542000] EISA: Detected 0 cards.
[4294670.542000] NET: Registered protocol family 2
[4294670.551000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.552000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[4294670.553000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[4294670.554000] TCP: Hash tables configured (established 131072 bind 65536)
[4294670.554000] TCP reno registered
[4294670.554000] TCP bic registered
[4294670.554000] NET: Registered protocol family 1
[4294670.554000] NET: Registered protocol family 8
[4294670.554000] NET: Registered protocol family 20
[4294670.554000] Using IPI No-Shortcut mode
[4294670.554000] ACPI wakeup devices:
[4294670.554000] PEGP P0P2 AC97 USB0 USB1 USB2 USB3 USB7 UAR1 PEX1 PEX2 PEX3 PEX4 AZAL PWRB
[4294670.554000] ACPI: (supports S0 S1 S3 S4 S5)
[4294670.554000] Freeing unused kernel memory: 332k freed
[4294670.728000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294670.940000] vga16fb: initializing
[4294670.940000] vga16fb: mapped to 0xc00a0000
[4294671.053000] Console: switching to colour frame buffer device 80x25
[4294671.053000] fb0: VGA16 VGA frame buffer device
[4294672.195000] Capability LSM initialized
[4294672.312000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294673.059000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294673.059000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 185
[4294673.059000] ICH6: chipset revision 3
[4294673.059000] ICH6: not 100% native mode: will probe irqs later
[4294673.059000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[4294673.059000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[4294673.059000] Probing IDE interface ide0...
[4294673.732000] hda: BENQ DVD DUAL DW1610, ATAPI CD/DVD-ROM drive
[4294673.988000] hdb: WDC WD1600JB-00FUA0, ATA DISK drive
[4294674.041000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.059000] Probing IDE interface ide1...
[4294674.588000] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294674.588000] Uniform CD-ROM driver Revision: 3.20
[4294674.595000] hdb: max request size: 1024KiB
[4294674.596000] hdb: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[4294674.597000] hdb: cache flushes supported
[4294674.598000]  hdb: hdb1 hdb2 < hdb5 >
[4294675.058000] SCSI subsystem initialized
[4294675.064000] ACPI: bus type scsi registered
[4294675.064000] libata version 1.20 loaded.
[4294675.066000] ata_piix 0000:00:1f.2: version 1.05
[4294675.066000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[4294675.066000] ata_pci_init_one: NO_LEGACY == 0
[4294675.066000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 193
[4294675.066000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294675.066000] ata1: PATA max UDMA/133 cmd 0xE800 ctl 0xE402 bmdma 0xD800 irq 193
[4294675.066000] ata2: PATA max UDMA/133 cmd 0xE000 ctl 0xDC02 bmdma 0xD808 irq 193
[4294675.220000] ata1: dev 0 cfg 00:427a 49:2f00 82:346b 83:7f61 84:4003 85:3469 86:3c41 87:4003 88:207f 93:0000
[4294675.220000] ata1: dev 0 ATA-6, max UDMA/133, 312581808 sectors: LBA48
[4294675.221000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe66e0
[4294675.227000] ata1: dev 0 configured for UDMA/133
[4294675.227000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe66e0
[4294675.232000] scsi0 : ata_piix
[4294676.406000] ata2: disabling port
[4294676.406000] scsi1 : ata_piix
[4294676.406000]   Vendor: ATA       Model: WDC WD1600JD-22H  Rev: 08.0
[4294676.406000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294676.415000] Driver 'sd' needs updating - please use bus_type methods
[4294676.416000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294676.416000] SCSI device sda: drive cache: write back
[4294676.419000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294676.419000] SCSI device sda: drive cache: write back
[4294676.419000]  sda: sda1 sda2 sda3 < sda5 sda6 >
[4294676.463000] sd 0:0:0:0: Attached scsi disk sda
[4294676.835000] usbcore: registered new driver usbfs
[4294676.835000] usbcore: registered new driver hub
[4294676.840000] USB Universal Host Controller Interface driver v2.3
[4294676.840000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 58
[4294676.840000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294676.840000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294676.841000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294676.841000] uhci_hcd 0000:00:1d.0: irq 58, io base 0x0000c800
[4294676.843000] hub 1-0:1.0: USB hub found
[4294676.843000] hub 1-0:1.0: 2 ports detected
[4294676.914000] ieee1394: Initialized config rom entry `ip1394'
[4294676.944000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[4294676.944000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294676.944000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294676.945000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294676.945000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000cc00
[4294676.945000] hub 2-0:1.0: USB hub found
[4294676.945000] hub 2-0:1.0: 2 ports detected
[4294677.046000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[4294677.046000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294677.046000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294677.047000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294677.047000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x0000d000
[4294677.047000] hub 3-0:1.0: USB hub found
[4294677.047000] hub 3-0:1.0: 2 ports detected
[4294677.148000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[4294677.148000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294677.148000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294677.149000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294677.149000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000d400
[4294677.149000] hub 4-0:1.0: USB hub found
[4294677.149000] hub 4-0:1.0: 2 ports detected
[4294677.252000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[4294677.253000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 58
[4294677.253000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294677.253000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294677.253000] ehci_hcd 0000:00:1d.7: debug port 1
[4294677.253000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294677.254000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294677.254000] ehci_hcd 0000:00:1d.7: irq 58, io mem 0xffa3bc00
[4294677.257000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294677.258000] hub 5-0:1.0: USB hub found
[4294677.258000] hub 5-0:1.0: 8 ports detected
[4294677.360000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294677.360000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 21 (level, low) -> IRQ 66
[4294677.360000] PCI: Via IRQ fixup for 0000:06:00.0, from 3 to 2
[4294677.414000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[66]  MMIO=[ff7ff800-ff7fffff]  Max Packet=[2048]
[4294677.451000] Probing IDE interface ide1...
[4294677.723000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[4294678.173000] Attempting manual resume
[4294678.200000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.231000] kjournald starting.  Commit interval 5 seconds
[4294678.362000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[4294678.679000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00406300000006e7]
[4294678.735000] usb 4-2: new low speed USB device using uhci_hcd and address 2
[4294696.799000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294715.359000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294715.369000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294717.584000] hw_random: RNG not detected
[4294717.585000] Linux agpgart interface v0.101 (c) Dave Jones
[4294717.594000] agpgart: Detected an Intel 915G Chipset.
[4294717.595000] agpgart: Detected 7932K stolen memory.
[4294717.612000] agpgart: AGP aperture is 256M @ 0xd0000000
[4294718.761000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294718.761000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294720.820000] input: PC Speaker as /class/input/input1
[4294720.858000] usbcore: registered new driver hiddev
[4294720.878000] input: Microsoft Basic Optical Mouse as /class/input/input2
[4294720.879000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.2-1
[4294720.879000] usbcore: registered new driver usbhid
[4294720.879000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294720.916000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[4294720.916000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294720.916000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 74
[4294720.936000] e100: eth0: e100_probe: addr 0xff7fe000, irq 74, MAC addr 00:11:11:8F:51:08
[4294721.944000] input: Wacom Graphire3 as /class/input/input3
[4294722.485000] Floppy drive(s): fd0 is 1.44M
[4294722.498000] FDC 0 is a post-1991 82077
[4294722.502000] parport: PnPBIOS parport detected.
[4294722.502000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[4294722.931000] usbcore: registered new driver wacom
[4294722.931000] drivers/usb/input/wacom.c: v1.44:USB Wacom Graphire and Wacom Intuos tablet driver
[4294724.286000] ts: Compaq touchscreen protocol output
[4294726.736000] Intel ISA PCIC probe: not found.
[4294727.159000] lp0: using parport0 (interrupt-driven).
[4294727.394000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294727.394000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294727.394000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294727.867000] Adding 2931820k swap on /dev/sda5.  Priority:-1 extents:1 across:2931820k
[4294728.006000] EXT3 FS on sda6, internal journal
[4294728.490000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294728.490000] md: bitmap version 4.39
[4294729.313000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294730.376000] cdrom: open failed.
[4294731.342000] kjournald starting.  Commit interval 5 seconds
[4294731.342000] EXT3 FS on sda2, internal journal
[4294731.342000] EXT3-fs: mounted filesystem with ordered data mode.
[4294731.343000] kjournald starting.  Commit interval 5 seconds
[4294731.344000] EXT3 FS on hdb5, internal journal
[4294731.344000] EXT3-fs: mounted filesystem with ordered data mode.
[4294731.399000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294731.463000] NTFS volume version 3.1.
[4294731.523000] NTFS volume version 3.1.
[4294732.044000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4294732.573000] CSLIP: code copyright 1989 Regents of the University of California
[4294732.585000] PPP generic driver version 2.4.2
[4294732.628000] NET: Registered protocol family 17
[4294732.668000] NET: Registered protocol family 10
[4294732.668000] lo: Disabled Privacy Extensions
[4294732.668000] IPv6 over IPv4 tunneling driver
[4294735.564000] ACPI: Power Button (FF) [PWRF]
[4294735.564000] ACPI: Power Button (CM) [PWRB]
[4294736.680000] ibm_acpi: ec object not found
[4294737.476000] pcc_acpi: loading...
[4294738.218000] NET: Registered protocol family 24
[4294742.755000] ip_tables: (C) 2000-2002 Netfilter core team
[4294743.320000] eth0: no IPv6 routers present
[4294815.294000] ppdev: user-space parallel port driver
[4294818.511000] [drm] Initialized drm 1.0.1 20051102
[4294818.538000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294818.539000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294818.539000] [drm] Initialized i915 1.4.0 20060119 on minor 0:
[4294821.577000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294821.577000] apm: overridden by ACPI.
[4294824.848000] Bluetooth: Core ver 2.8
[4294824.848000] NET: Registered protocol family 31
[4294824.848000] Bluetooth: HCI device and connection manager initialized
[4294824.848000] Bluetooth: HCI socket layer initialized
[4294824.891000] Bluetooth: L2CAP ver 2.8
[4294824.891000] Bluetooth: L2CAP socket layer initialized
[4294824.948000] Bluetooth: RFCOMM socket layer initialized
[4294824.948000] Bluetooth: RFCOMM TTY layer initialized
[4294824.948000] Bluetooth: RFCOMM ver 1.7
[4295374.083000] usb 5-2: new high speed USB device using ehci_hcd and address 5
richard@ubuntu:~$
 
```

---

### Post by bluenova on 2006-06-15
Have you set this in the 350D camera menu?

> On the last screen > Connection > Print/PTP

[IMG]http://www.dpreview.com/reviews/CanonEOS350D/Images/Captures/350d_062.gif[/IMG]

---

### Post by richardq on 2006-06-15
[QUOTE=bluenova]Have you set this in the 350D camera menu?

> On the last screen > Connection > Print/PTP

[IMG]http://www.dpreview.com/reviews/CanonEOS350D/Images/Captures/350d_062.gif[/IMG][/QUOTE]

Right now the camera is showing 'PC Connection' not Print/PTP. 

I'm now at work (XP-only :<) and as such I can't try it out right now. Should it be set to Print/PTP for detection in Linux? It connects with my XP machine at home and at work no problem on the 'PC Connection' setting.

Incidentally, this is really the last barrier keeping me from fully moving to Linux at home (that is assuming ufraw + Gimp + F-Spot) can fulfill my photographic needs.

---

### Post by weijie90 on 2006-06-16
hmm.. i have absolutely no idea, unless dmesg has more to say than "[4295374.083000] usb 5-2: new high speed USB device using ehci_hcd and address 5". Did you use dmesg to quickly? this could let some messages to be left out.

mabye you could try Print/PTP.

---

### Post by bluenova on 2006-06-16
Yes, it should be Print/PTP with Linux and PC Connection with Windows. I have the 350D and it connects fine when in Print/PTP mode. Incidently, I use ufraw, Gimp and Digikam (for organisation).

---

### Post by richardq on 2006-06-16
[QUOTE=bluenova]Yes, it should be Print/PTP with Linux and PC Connection with Windows. I have the 350D and it connects fine when in Print/PTP mode. Incidently, I use ufraw, Gimp and Digikam (for organisation).[/QUOTE]

Yes. It worked in PrintPTP Mode! thanks for the help.

Also, I tried ufraw and it took me a lot of fiddling to get the colour balanced properly. The original interpretation 'camera wb' was overly dark. I tried to overcome by adjusting the gamma and also trying out the other wb settings to no avail. Can you point me to any good sources of info on what some reasonable starting point settings (in ufraw) for the 350D might be? Or maybe let me know what kind of settings you use to do your importing?

---

### Post by bluenova on 2006-06-16
I had the same problem, and found somebody who made a profile for the 350D which was much better. I'm away for the weekend, but if you can wait till I'm home on monday I can send it to you. PM me your email addy. Also to add, check out gimp-dcraw for easy raw imports.

---

