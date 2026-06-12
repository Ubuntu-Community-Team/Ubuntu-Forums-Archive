---
title: "Possible bug?"
date: 2007-09-23
forum: Desktop Environments
---

### Post by gubemton on 2007-09-23
I only started using Linux recently and I am still an Uber Noob. I can no longer boot from the hd and have to rely on the boot disk. I looked around and found problems with hd's that won't automount... Now I can't even see the hd in media storage. I don't know if this helps:

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fec0000 end: 000000003ffc0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003ffc0000 size: 000000000000e000 end: 000000003ffce000 type: 3
[    0.000000] copy_e820_map() start: 000000003ffce000 size: 0000000000022000 end: 000000003fff0000 type: 4
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000010000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000480000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffce000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262080
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262080
[    0.000000] On node 0 totalpages: 262080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32449 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb090
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x06000409 MSFT 0x00000097) @ 0x3ffc0000
[    0.000000] ACPI: FADT (v001 A M I  OEMFACP  0x06000409 MSFT 0x00000097) @ 0x3ffc0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x06000409 MSFT 0x00000097) @ 0x3ffc0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x06000409 MSFT 0x00000097) @ 0x3ffce040
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x06000409 MSFT 0x00000097) @ 0x3ffc5ff0
[    0.000000] ACPI: DSDT (v001  A0045 A0045001 0x00000001 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[    0.000000] Detected 3006.990 MHz processor.
[   55.834280] Built 1 zonelists.  Total pages: 260033
[   55.834284] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[   55.834473] mapped APIC to ffffd000 (fee00000)
[   55.834475] mapped IOAPIC to ffffc000 (fec00000)
[   55.834478] Enabling fast FPU save and restore... done.
[   55.834481] Enabling unmasked SIMD FPU exception support... done.
[   55.834489] Initializing CPU#0
[   55.834545] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   55.835544] Console: colour VGA+ 80x25
[   55.835861] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   55.836190] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   55.856788] Memory: 1028020k/1048320k available (1992k kernel code, 19684k reserved, 893k data, 328k init, 130816k highmem)
[   55.856798] virtual kernel memory layout:
[   55.856800]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   55.856801]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   55.856802]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   55.856803]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   55.856804]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   55.856805]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   55.856806]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   55.856809] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   55.934393] Calibrating delay using timer specific routine.. 6019.13 BogoMIPS (lpj=12038277)
[   55.934434] Security Framework v1.0.0 initialized
[   55.934439] SELinux:  Disabled at boot.
[   55.934456] Mount-cache hash table entries: 512
[   55.934592] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   55.934601] monitor/mwait feature present.
[   55.934603] using mwait in idle threads.
[   55.934609] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   55.934612] CPU: L2 cache: 1024K
[   55.934615] CPU: Physical Processor ID: 0
[   55.934617] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   55.934627] Compat vDSO mapped to ffffe000.
[   55.934631] Remapping vsyscall page to ffffe000
[   55.934646] Checking 'hlt' instruction... OK.
[   55.950455] SMP alternatives: switching to UP code
[   55.950797] Early unpacking initramfs... done
[   56.228848] ACPI: Core revision 20060707
[   56.229010] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   56.242793] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[   56.242814] SMP alternatives: switching to SMP code
[   56.242916] Booting processor 1/1 eip 3000
[   56.253209] Initializing CPU#1
[   56.333757] Calibrating delay using timer specific routine.. 6014.12 BogoMIPS (lpj=12028241)
[   56.333766] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   56.333773] monitor/mwait feature present.
[   56.333780] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   56.333783] CPU: L2 cache: 1024K
[   56.333785] CPU: Physical Processor ID: 0
[   56.333788] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   56.334060] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[   56.334102] Total of 2 processors activated (12033.25 BogoMIPS).
[   56.334249] ENABLING IO-APIC IRQs
[   56.334430] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   56.481530] checking TSC synchronization across 2 CPUs: passed.
[    0.003995] Brought up 2 CPUs
[    0.089343] migration_cost=100
[    0.089632] Booting paravirtualized kernel on bare hardware
[    0.089708] Time: 16:04:32  Date: 08/23/107
[    0.089739] NET: Registered protocol family 16
[    0.089829] EISA bus registered
[    0.089834] ACPI: bus type pci registered
[    0.090080] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=4
[    0.090083] PCI: Using configuration type 1
[    0.090085] Setting up standard PCI resources
[    0.107119] ACPI: Interpreter enabled
[    0.107123] ACPI: Using IOAPIC for interrupt routing
[    0.108294] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.108302] PCI: Probing PCI hardware (bus 00)
[    0.109053] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.109057] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.109303] Boot video device is 0000:04:00.0
[    0.109877] PCI: Transparent bridge - 0000:00:1e.0
[    0.109938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.112801] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.113117] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.113484] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.113792] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.121885] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.122167] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.122450] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.122735] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.123017] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.123298] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.123578] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.123897] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.124024] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.124037] pnp: PnP ACPI init
[    0.130518] pnp: PnP ACPI: found 19 devices
[    0.130523] PnPBIOS: Disabled by ACPI PNP
[    0.130578] PCI: Using ACPI for IRQ routing
[    0.130582] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.146429] NET: Registered protocol family 8
[    0.146432] NET: Registered protocol family 20
[    0.147284] pnp: 00:08: ioport range 0x290-0x297 has been reserved
[    0.147647] PCI: Bridge: 0000:00:01.0
[    0.147651]   IO window: e000-efff
[    0.147655]   MEM window: cff00000-cfffffff
[    0.147659]   PREFETCH window: d0000000-dfffffff
[    0.147663] PCI: Bridge: 0000:00:1c.0
[    0.147666]   IO window: d000-dfff
[    0.147671]   MEM window: disabled.
[    0.147674]   PREFETCH window: disabled.
[    0.147679] PCI: Bridge: 0000:00:1c.1
[    0.147682]   IO window: c000-cfff
[    0.147687]   MEM window: cfe00000-cfefffff
[    0.147691]   PREFETCH window: disabled.
[    0.147697] PCI: Bridge: 0000:00:1e.0
[    0.147699]   IO window: b000-bfff
[    0.147705]   MEM window: cfd00000-cfdfffff
[    0.147709]   PREFETCH window: 50000000-500fffff
[    0.147727] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.147733] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.147758] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.147765] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.147788] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    0.147794] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.147806] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.147835] NET: Registered protocol family 2
[    0.191754] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.191882] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.192458] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.192713] TCP: Hash tables configured (established 131072 bind 65536)
[    0.192716] TCP reno registered
[    0.207814] checking if image is initramfs... it is
[    0.754716] Freeing initrd memory: 6965k freed
[    0.755328] audit: initializing netlink socket (disabled)
[    0.755344] audit(1190563472.476:1): initialized
[    0.755444] highmem bounce pool size: 64 pages
[    0.755539] VFS: Disk quotas dquot_6.5.1
[    0.755559] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.755608] io scheduler noop registered
[    0.755611] io scheduler anticipatory registered
[    0.755614] io scheduler deadline registered
[    0.755629] io scheduler cfq registered (default)
[    0.755863] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.755904] assign_interrupt_mode Found MSI capability
[    0.755908] Allocate Port Service[0000:00:01.0:pcie00]
[    0.756009] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.756053] assign_interrupt_mode Found MSI capability
[    0.756056] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.756093] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.756202] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.756245] assign_interrupt_mode Found MSI capability
[    0.756248] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.756286] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.756459] isapnp: Scanning for PnP cards...
[    1.107622] isapnp: No Plug & Play device found
[    1.134844] Real Time Clock Driver v1.12ac
[    1.134902] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.135023] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.135171] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.135812] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.136056] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.136241] mice: PS/2 mouse device common for all mice
[    1.136897] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.137049] input: Macintosh mouse button emulation as /class/input/input0
[    1.137092] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.137097] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.137310] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.137312] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    1.139748] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.139754] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.139869] EISA: Probing bus 0 at eisa.0
[    1.139901] EISA: Detected 0 cards.
[    1.169938] TCP cubic registered
[    1.169948] NET: Registered protocol family 1
[    1.169972] Starting balanced_irq
[    1.169979] Using IPI No-Shortcut mode
[    1.170069] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.170131] Time: tsc clocksource has been installed.
[    1.170157] ACPI: (supports S0 S1 S3 S4 S5)
[    1.170218]   Magic number: 7:955:85
[    1.170499] Freeing unused kernel memory: 328k freed
[    2.392621] Capability LSM initialized
[    2.438044] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.003300] usbcore: registered new interface driver usbfs
[    3.003334] usbcore: registered new interface driver hub
[    3.003383] usbcore: registered new device driver usb
[    3.101175] SCSI subsystem initialized
[    3.109753] libata version 2.20 loaded.
[    3.116610] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.116634] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    3.116662] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.116741] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    3.171446] Floppy drive(s): fd0 is 1.44M
[    3.173083] USB Universal Host Controller Interface driver v3.0
[    3.176016] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.204144] FDC 0 is a post-1991 82077
[    3.209928] ieee1394: Initialized config rom entry `ip1394'
[    3.217842] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    3.217870] scsi0 : ata_piix
[    3.546898] ata1.00: ATAPI, max MWDMA2
[    3.658160] end_request: I/O error, dev fd0, sector 0
[    3.720031] ata1.00: configured for MWDMA2
[    3.720046] scsi1 : ata_piix
[    3.720126] ata2: port disabled. ignoring.
[    3.721221] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4120B 2.00 PQ: 0 ANSI: 5
[    3.722515] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.722544] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    3.722563] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.722602] ata3: SATA max UDMA/133 cmd 0x0001ac00 ctl 0x0001a882 bmdma 0x0001a400 irq 19
[    3.722635] ata4: SATA max UDMA/133 cmd 0x0001a800 ctl 0x0001a482 bmdma 0x0001a408 irq 19
[    3.722648] scsi2 : ata_piix
[    4.025933] ata3.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    4.025936] ata3.00: ATA-6: ST3200822AS, 3.01, max UDMA/133
[    4.025939] ata3.00: 390721968 sectors, multi 16: LBA48
[    4.038025] ata3.01: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[    4.038030] ata3.01: ATA-7: WDC WD3200AAKS-75SBA0, 12.01B01, max UDMA/133
[    4.038033] ata3.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.049880] ata3.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    4.049883] ata3.00: configured for UDMA/133
[    4.062884] ata3.01: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[    4.062889] ata3.01: configured for UDMA/133
[    4.062895] scsi3 : ata_piix
[    4.231371] ATA: abnormal status 0x7F on port 0x0001a807
[    4.231481] scsi 2:0:0:0: Direct-Access     ATA      ST3200822AS      3.01 PQ: 0 ANSI: 5
[    4.231634] scsi 2:0:1:0: Direct-Access     ATA      WDC WD3200AAKS-7 12.0 PQ: 0 ANSI: 5
[    4.232541] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    4.232555] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.232560] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.232878] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.232912] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00009880
[    4.233077] usb usb1: configuration #1 chosen from 1 choice
[    4.233128] hub 1-0:1.0: USB hub found
[    4.233141] hub 1-0:1.0: 2 ports detected
[    4.244960] sr0: scsi3-mmc drive: 27x/32x writer cd/rw xa/form2 cdda tray
[    4.244965] Uniform CD-ROM driver Revision: 3.20
[    4.245022] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.249077] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    4.249108] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    4.249135] scsi 2:0:1:0: Attached scsi generic sg2 type 0
[    4.337207] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    4.337224] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.337229] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.337264] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.337292] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009c00
[    4.337415] usb usb2: configuration #1 chosen from 1 choice
[    4.337470] hub 2-0:1.0: USB hub found
[    4.337480] hub 2-0:1.0: 2 ports detected
[    4.445008] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    4.445023] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.445028] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.445062] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.445094] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a000
[    4.445232] usb usb3: configuration #1 chosen from 1 choice
[    4.445294] hub 3-0:1.0: USB hub found
[    4.445305] hub 3-0:1.0: 2 ports detected
[    4.552854] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    4.552869] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.552875] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.552908] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.552940] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000a080
[    4.553095] usb usb4: configuration #1 chosen from 1 choice
[    4.553152] hub 4-0:1.0: USB hub found
[    4.553163] hub 4-0:1.0: 2 ports detected
[    4.580687] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    4.660783] 8139cp 0000:01:0a.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.660788] 8139cp 0000:01:0a.0: Try the "8139too" driver instead.
[    4.663688] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[    4.664917] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    4.664931] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.664936] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.664971] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.665006] ehci_hcd 0000:00:1d.7: debug port 1
[    4.665014] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    4.665023] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xcfcff800
[    4.668892] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.668995] usb usb5: configuration #1 chosen from 1 choice
[    4.669034] hub 5-0:1.0: USB hub found
[    4.669043] hub 5-0:1.0: 8 ports detected
[    4.713445] 8139too Fast Ethernet driver 0.9.28
[    4.715542] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[cfdff000-cfdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.732560] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    4.732599] sda: Write Protect is off
[    4.732604] sda: Mode Sense: 00 3a 00 00
[    4.732640] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.733927] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    4.733948] sda: Write Protect is off
[    4.733951] sda: Mode Sense: 00 3a 00 00
[    4.733982] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.733989]  sda: sda2 < >
[    4.750244] sd 2:0:0:0: Attached scsi disk sda
[    4.751045] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[    4.751081] sdb: Write Protect is off
[    4.751085] sdb: Mode Sense: 00 3a 00 00
[    4.751112] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.752310] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[    4.752330] sdb: Write Protect is off
[    4.752334] sdb: Mode Sense: 00 3a 00 00
[    4.752378] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.752383]  sdb: sdb1
[    4.754760] sd 2:0:1:0: Attached scsi disk sdb
[    4.760410] end_request: I/O error, dev fd0, sector 0
[    4.776664] pata_it821x: controller in pass through mode.
[    4.776694] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 20 (level, low) -> IRQ 21
[    4.776719] PCI: Setting latency timer of device 0000:01:03.0 to 64
[    4.776786] ata5: PATA max UDMA/133 cmd 0x0001bc00 ctl 0x0001b482 bmdma 0x0001b000 irq 21
[    4.776840] ata6: PATA max UDMA/133 cmd 0x0001b400 ctl 0x0001b082 bmdma 0x0001b008 irq 21
[    4.776861] scsi4 : pata_it821x
[    4.946281] ATA: abnormal status 0x8 on port 0x0001bc07
[    4.946309] scsi5 : pata_it821x
[    4.994000] ISO 9660 Extensions: Microsoft Joliet Level 3
[    5.029371] ISO 9660 Extensions: RRIP_1991A
[    5.060854] Registering unionfs 20060916-2203
[    5.060860] unionfs: debugging is not enabled
[    5.068211] loop: loaded (max 8 devices)
[    5.114210] ATA: abnormal status 0x8 on port 0x0001b407
[    5.114326] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 21 (level, low) -> IRQ 22
[    5.114747] eth0: RealTek RTL8139 at 0xf8848c00, 00:50:ba:d1:df:00, IRQ 22
[    5.114751] eth0:  Identified 8139 chip type 'RTL-8139B'
[    5.123822] usb 1-2: device not accepting address 2, error -71
[    5.188913] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher
[    5.938514] usb 1-2: new low speed USB device using uhci_hcd and address 4
[    6.002590] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00900701010025ec]
[    6.132933] usb 1-2: configuration #1 chosen from 1 choice
[    6.377811] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    6.623681] usb 2-1: configuration #1 chosen from 1 choice
[    6.626712] usbcore: registered new interface driver hiddev
[    6.641107] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[    6.641141] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-2
[    6.641163] usbcore: registered new interface driver usbhid
[    6.641168] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   51.753275] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   55.065865] Linux agpgart interface v0.102 (c) Dave Jones
[   55.118035] agpgart: Detected an Intel 915G Chipset.
[   55.135320] agpgart: AGP aperture is 256M @ 0x0
[   55.399822] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   55.407104] parport: PnPBIOS parport detected.
[   55.407215] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   55.410772] input: PC Speaker as /class/input/input3
[   55.608112] iTCO_vendor_support: vendor-support=0
[   55.609847] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   55.609972] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[   55.610026] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   55.687088] NET: Registered protocol family 17
[   55.938660] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   56.113237] intel_rng: FWH not detected
[   56.761452] Linux video capture interface: v2.00
[   56.976291] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   56.976311] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   56.976344] sky2 0000:02:00.0: v1.13 addr 0xcfefc000 irq 17 Yukon-EC (0xb6) rev 1
[   56.976471] sky2 eth1: addr 00:11:2f:2a:d6:a0
[   57.052510] w9968cf: V4L driver for W996[87]CF JPEG USB Dual Mode Camera Chip 1:1.33-basic
[   57.133812] sky2 eth1: enabling interface
[   57.135628] sky2 eth1: ram buffer 48K
[   57.313243] ovcamchip: v2.27 for Linux 2.6 : OV camera chip I2C driver
[   57.405328] usb 2-1: W996[87]CF JPEG USB Dual Mode Camera detected
[   57.405372] usb 2-1: V4L device registered as /dev/video0
[   57.945434] ovcamchip: Camera chip is an OV7620
[   59.148551] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   59.148573] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   59.272013] NET: Registered protocol family 10
[   59.272120] lo: Disabled Privacy Extensions
[   59.272231] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   60.953487] usb 2-1: OV7620 image sensor initialized
[   60.953506] usbcore: registered new interface driver w9968cf
[   61.167307] fuse init (API version 7.8)
[   67.861661] input: Power Button (FF) as /class/input/input4
[   67.861702] ACPI: Power Button (FF) [PWRF]
[   67.861785] input: Power Button (CM) as /class/input/input5
[   67.861816] ACPI: Power Button (CM) [PWRB]
[   67.966463] No dock devices found.
[   67.986135] Using specific hotkey driver
[   68.041301] ibm_acpi: ec object not found
[   68.224067] pcc_acpi: loading...
[   69.540881] eth0: no IPv6 routers present
[   75.531227] lp0: using parport0 (interrupt-driven).
[   75.603207] ppdev: user-space parallel port driver
[   81.868234] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   81.868240] apm: disabled - APM is not SMP safe.
[   83.849242] Bluetooth: Core ver 2.11
[   83.849314] NET: Registered protocol family 31
[   83.849318] Bluetooth: HCI device and connection manager initialized
[   83.849323] Bluetooth: HCI socket layer initialized
[   84.056290] Bluetooth: L2CAP ver 2.8
[   84.056296] Bluetooth: L2CAP socket layer initialized
[   84.078884] Bluetooth: RFCOMM socket layer initialized
[   84.078901] Bluetooth: RFCOMM TTY layer initialized
[   84.078904] Bluetooth: RFCOMM ver 1.8
[   89.062503] [drm] Initialized drm 1.1.0 20060810
[   89.131649] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   89.131950] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   89.656739] eth0: no IPv6 routers present
[   91.082351] [drm] Setting GART location based on new memory map
[   91.082821] [drm] Loading R300 Microcode
[   91.082871] [drm] writeback test succeeded in 1 usecs
[ 2141.465201] attempt to access beyond end of device
[ 2141.465209] sda2: rw=0, want=4, limit=2
[ 2141.465437] EXT3-fs: unable to read superblock
[ 2637.991841] cramfs: wrong magic
[ 2637.992045] attempt to access beyond end of device
[ 2637.992051] sda2: rw=0, want=66, limit=2
[ 2637.992229] isofs_fill_super: bread failed, dev=sda2, iso_blknum=16, block=32
[ 2637.997776] SQUASHFS error: Can't find a SQUASHFS superblock on sda2
[ 2638.000644] attempt to access beyond end of device
[ 2638.000655] sda2: rw=0, want=4, limit=2
[ 2638.001042] EXT3-fs: unable to read superblock
[ 2718.429118] NTFS driver 2.1.28 [Flags: R/O MODULE].
[ 2718.457555] NTFS volume version 3.1.
[ 2781.047379] cramfs: wrong magic
[ 2781.063993] Unable to identify CD-ROM format.
[ 2781.067883] SQUASHFS error: Can't find a SQUASHFS superblock on sda
[ 2781.068357] VFS: Can't find ext3 filesystem on dev sda.
[ 2781.068819] NTFS-fs warning (device sda): is_boot_sector_ntfs(): Invalid boot sector checksum.
[ 2781.068827] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[ 2781.068832] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[ 2781.068838] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[14684.767963] JFS: nTxBlock = 8090, nTxLock = 64721
[14684.995268] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[14684.995902] SGI XFS Quota Management subsystem
[14685.336887] program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO
[14685.382798] end_request: I/O error, dev fd0, sector 0
[14685.406761] end_request: I/O error, dev fd0, sector 0

---

### Post by ddrichardson on 2007-09-23
The output of ```
sudo fdisk -l
``` and /etc/fstab would help. It's not just hard disk either ther seem to be cd and floppy problems too.

---

### Post by gubemton on 2007-09-23
/dev/sda2 /storage ext3 defaults 0 0

is the fstab but I've tried to change it already but I don't think I did it right.

---

### Post by gubemton on 2007-09-23
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       24321   195358401    5  Extended

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

---

### Post by ddrichardson on 2007-09-24
There seems to have been a problem with the partition table, the MBR most likely has become corrupted. There's a [guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") on the Wiki.

---

