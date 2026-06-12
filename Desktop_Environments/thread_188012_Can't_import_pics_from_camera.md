---
title: "Can't import pics from camera"
date: 2006-06-03
forum: Desktop Environments
---

### Post by ms30290 on 2006-06-03
Hi, My camera ( USB - creative pccam-750) is recognized when I plug it but I get the following error when I click "import photos" :
An error occurred in the io-library ('Could not lock the device'): Camera is already in use.

Looks like USB is claimed by usbfs. Don't know where to go from here.

dmesg output looks like this:
dad@ubuntubox:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-686 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000003ff75000 (usable)
[4294667.296000]  BIOS-e820: 000000003ff75000 - 000000003ff77000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000003ff77000 - 000000003ff98000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000003ff98000 - 0000000040000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec90000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000] 127MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000fe710
[4294667.296000] On node 0 totalpages: 262005
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 32629 pages, LIFO batch:7
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000febc0
[4294667.296000] ACPI: RSDT (v001 DELL    WS 650  0x00000008 ASL  0x00000061) @ 0x000fd4d9
[4294667.296000] ACPI: FADT (v001 DELL    WS 650  0x00000008 ASL  0x00000061) @ 0x000fd511
[4294667.296000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffefa6f
[4294667.296000] ACPI: MADT (v001 DELL    WS 650  0x00000008 ASL  0x00000061) @ 0x000fd585
[4294667.296000] ACPI: BOOT (v001 DELL    WS 650  0x00000008 ASL  0x00000061) @ 0x000fd609
[4294667.296000] ACPI: ASF! (v016 DELL    WS 650  0x00000008 ASL  0x00000061) @ 0x000fd631
[4294667.296000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:2 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x06] enabled)
[4294667.296000] Processor #6 15:2 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[4294667.296000] Processor #1 15:2 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] enabled)
[4294667.296000] Processor #7 15:2 APIC version 20
[4294667.296000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: IOAPIC (id[0x09] address[0xfec80000] gsi_base[24])
[4294667.296000] IOAPIC[1]: apic_id 9, version 32, address 0xfec80000, GSI 24-47[4294667.296000] ACPI: IOAPIC (id[0x0a] address[0xfec80800] gsi_base[48])
[4294667.296000] IOAPIC[2]: apic_id 10, version 32, address 0xfec80800, GSI 48-71
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 3 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/sda1 ro quiet splash vga=791
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] mapped IOAPIC to ffffb000 (fec80000)
[4294667.296000] mapped IOAPIC to ffffa000 (fec80800)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 2392.707 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour dummy device 80x25
[4294669.283000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294669.284000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.319000] Memory: 1026744k/1048020k available (2101k kernel code, 20592k reserved, 592k data, 332k init, 130516k highmem)
[4294669.319000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.379000] Calibrating delay using timer specific routine.. 4788.03 BogoMIPS (lpj=2394016)
[4294669.379000] Security Framework v1.0.0 initialized
[4294669.379000] SELinux:  Disabled at boot.
[4294669.379000] Mount-cache hash table entries: 512
[4294669.379000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294669.379000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294669.379000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294669.379000] CPU: L2 cache: 512K
[4294669.379000] CPU: Hyper-Threading is disabled
[4294669.379000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[4294669.379000] mtrr: v2.0 (20020519)
[4294669.379000] Enabling fast FPU save and restore... done.
[4294669.379000] Enabling unmasked SIMD FPU exception support... done.
[4294669.379000] Checking 'hlt' instruction... OK.
[4294669.383000] SMP alternatives: switching to UP code
[4294669.383000] checking if image is initramfs... it is
[4294669.926000] Freeing initrd memory: 6799k freed
[4294669.940000] ACPI: Looking for DSDT ... not found!
[4294669.968000] CPU0: Intel(R) Xeon(TM) CPU 2.40GHz stepping 09
[4294669.968000] SMP alternatives: switching to SMP code
[4294669.969000] Booting processor 1/1 eip 3000
[4294669.979000] Initializing CPU#1
[4294670.040000] Calibrating delay using timer specific routine.. 4783.90 BogoMIPS (lpj=2391952)
[4294670.040000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.040000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.040000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294670.040000] CPU: L2 cache: 512K
[4294670.040000] CPU: Hyper-Threading is disabled
[4294670.040000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[4294670.040000] CPU1: Intel(R) Xeon(TM) CPU 2.40GHz stepping 09
[4294670.040000] SMP alternatives: switching to SMP code
[4294670.040000] Booting processor 2/6 eip 3000
[4294670.050000] Initializing CPU#2
[4294670.111000] Calibrating delay using timer specific routine.. 4783.89 BogoMIPS (lpj=2391945)
[4294670.111000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.111000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.111000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294670.111000] CPU: L2 cache: 512K
[4294670.111000] CPU: Hyper-Threading is disabled
[4294670.111000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[4294670.111000] CPU2: Intel(R) Xeon(TM) CPU 2.40GHz stepping 09
[4294670.111000] SMP alternatives: switching to SMP code
[4294670.111000] Booting processor 3/7 eip 3000
[4294670.121000] Initializing CPU#3
[4294670.182000] Calibrating delay using timer specific routine.. 4783.99 BogoMIPS (lpj=2391998)
[4294670.182000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.182000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.182000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294670.182000] CPU: L2 cache: 512K
[4294670.182000] CPU: Hyper-Threading is disabled
[4294670.182000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[4294670.182000] CPU3: Intel(R) Xeon(TM) CPU 2.40GHz stepping 09
[4294670.182000] Total of 4 processors activated (19139.82 BogoMIPS).
[4294670.182000] ENABLING IO-APIC IRQs
[4294670.182000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294670.293000] checking TSC synchronization across 4 CPUs: passed.
[4294670.296000] Brought up 4 CPUs
[4294670.296000] NET: Registered protocol family 16
[4294670.296000] EISA bus registered
[4294670.296000] ACPI: bus type pci registered
[4294670.309000] PCI: PCI BIOS revision 2.10 entry at 0xfbdda, last bus=5
[4294670.309000] PCI: Using configuration type 1
[4294670.310000] ACPI: Subsystem revision 20051216
[4294670.336000] ACPI: Interpreter enabled
[4294670.336000] ACPI: Using IOAPIC for interrupt routing
[4294670.339000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.339000] PCI: Probing PCI hardware (bus 00)
[4294670.339000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294670.357000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[4294670.357000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[4294670.357000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294670.357000] Boot video device is 0000:01:00.0
[4294670.358000] PCI: Transparent bridge - 0000:00:1e.0
[4294670.358000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.675000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294670.681000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1.PCI2._PRT]
[4294670.686000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1.PCI3._PRT]
[4294670.692000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[4294670.716000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294670.717000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294670.718000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)[4294670.719000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)[4294670.719000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[4294670.720000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[4294670.721000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[4294670.722000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294670.722000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.722000] pnp: PnP ACPI init
[4294670.757000] pnp: PnP ACPI: found 12 devices
[4294670.757000] PnPBIOS: Disabled by ACPI PNP
[4294670.757000] PCI: Using ACPI for IRQ routing
[4294670.757000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.778000] pnp: 00:0b: ioport range 0x800-0x85f could not be reserved
[4294670.778000] pnp: 00:0b: ioport range 0xc00-0xc7f has been reserved
[4294670.778000] pnp: 00:0b: ioport range 0x860-0x8ff could not be reserved
[4294670.779000] PCI: Bridge: 0000:00:01.0
[4294670.779000]   IO window: disabled.
[4294670.779000]   MEM window: fc000000-fdffffff
[4294670.779000]   PREFETCH window: f0000000-f7ffffff
[4294670.779000] PCI: Bridge: 0000:02:1d.0
[4294670.779000]   IO window: e000-efff
[4294670.779000]   MEM window: fe500000-fe6fffff
[4294670.779000]   PREFETCH window: disabled.
[4294670.779000] PCI: Bridge: 0000:02:1f.0
[4294670.779000]   IO window: d000-dfff
[4294670.779000]   MEM window: fe300000-fe4fffff
[4294670.779000]   PREFETCH window: disabled.
[4294670.779000] PCI: Bridge: 0000:00:02.0
[4294670.779000]   IO window: d000-efff
[4294670.779000]   MEM window: fe100000-fe6fffff
[4294670.779000]   PREFETCH window: disabled.
[4294670.779000] PCI: Bridge: 0000:00:1e.0
[4294670.779000]   IO window: disabled.
[4294670.779000]   MEM window: disabled.
[4294670.779000]   PREFETCH window: disabled.
[4294670.779000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294670.779000] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[4294670.779000] Simple Boot Flag at 0x7a set to 0x1
[4294670.780000] audit: initializing netlink socket (disabled)
[4294670.780000] audit(1149341904.778:1): initialized
[4294670.780000] highmem bounce pool size: 64 pages
[4294670.780000] VFS: Disk quotas dquot_6.5.1
[4294670.780000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.780000] Initializing Cryptographic API
[4294670.780000] io scheduler noop registered
[4294670.780000] io scheduler anticipatory registered
[4294670.780000] io scheduler deadline registered
[4294670.780000] io scheduler cfq registered
[4294670.781000] isapnp: Scanning for PnP cards...
[4294671.138000] isapnp: No Plug & Play device found
[4294671.160000] Real Time Clock Driver v1.12
[4294671.160000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294671.162000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.162000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.162000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.162000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.162000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.165000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.165000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.166000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.166000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.166000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.166000] mice: PS/2 mouse device common for all mice
[4294671.166000] EISA: Probing bus 0 at eisa.0
[4294671.166000] EISA: Detected 0 cards.
[4294671.167000] NET: Registered protocol family 2
[4294671.177000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.177000] TCP established hash table entries: 262144 (order: 9, 3145728 bytes)
[4294671.180000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[4294671.181000] TCP: Hash tables configured (established 262144 bind 65536)
[4294671.181000] TCP reno registered
[4294671.181000] TCP bic registered
[4294671.181000] NET: Registered protocol family 1
[4294671.181000] NET: Registered protocol family 8
[4294671.181000] NET: Registered protocol family 20
[4294671.181000] Starting balanced_irq
[4294671.181000] Using IPI No-Shortcut mode
[4294671.181000] ACPI wakeup devices:
[4294671.181000] VBTN PCI0 USB0 USB1 USB2 PCI1 PCI2 PCI3 PCI4  KBD
[4294671.181000] ACPI: (supports S0 S1 S3 S4 S5)
[4294671.181000] Freeing unused kernel memory: 332k freed
[4294671.205000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.243000] vesafb: framebuffer at 0xf0000000, mapped to 0xf8880000, using 3072k, total 131072k
[4294671.243000] vesafb: mode is 1024x768x16, linelength=2048, pages=1
[4294671.243000] vesafb: protected mode interface info at c000:e4e0
[4294671.243000] vesafb: scrolling: redraw
[4294671.243000] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[4294671.243000] vesafb: Mode is VGA compatible
[4294671.286000] Console: switching to colour frame buffer device 128x48
[4294671.286000] fb0: VESA VGA frame buffer device
[4294672.306000] Capability LSM initialized
[4294673.031000] SCSI subsystem initialized
[4294673.032000] Fusion MPT base driver 3.03.04
[4294673.032000] Copyright (c) 1999-2005 LSI Logic Corporation
[4294673.035000] Fusion MPT SPI Host driver 3.03.04
[4294673.035000] ACPI: PCI Interrupt 0000:04:0e.0[A] -> GSI 50 (level, low) -> IRQ 169
[4294673.035000] mptbase: Initiating ioc0 bringup
[4294673.153000] ioc0: 53C1030: Capabilities={Initiator}
[4294673.413000] scsi0 : ioc0: LSI53C1030, FwRev=01011800h, Ports=1, MaxQ=222, IRQ=169
[4294673.413000]   Vendor: LSILOGIC  Model: RAID ARRAY    IS  Rev: 1000
[4294673.413000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4294676.673000] Driver 'sd' needs updating - please use bus_type methods
[4294676.674000] SCSI device sda: 141950976 512-byte hdwr sectors (72679 MB)
[4294676.674000] SCSI device sda: drive cache: write back
[4294676.675000] SCSI device sda: 141950976 512-byte hdwr sectors (72679 MB)
[4294676.675000] SCSI device sda: drive cache: write back
[4294676.675000]  sda: sda1 sda2 < sda5 >
[4294676.687000] sd 0:0:0:0: Attached scsi disk sda
[4294676.931000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294676.931000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294676.931000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
[4294676.931000] ICH4: chipset revision 1
[4294676.931000] ICH4: not 100% native mode: will probe irqs later
[4294676.931000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294676.931000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[4294676.931000] Probing IDE interface ide0...
[4294677.195000] hda: Maxtor 6E040L0, ATA DISK drive
[4294677.807000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294677.810000] Probing IDE interface ide1...
[4294678.482000] hdc: TSSTcorpCD/DVDW TS-H552U, ATAPI CD/DVD-ROM drive
[4294678.890000] hdd: PLEXTOR CD-R PX-W4824A, ATAPI CD/DVD-ROM drive
[4294678.956000] ide1 at 0x170-0x177,0x376 on irq 15
[4294678.969000] hda: max request size: 128KiB
[4294678.971000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294678.971000] hda: cache flushes supported
[4294678.971000]  hda: hda1
[4294678.977000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294678.977000] Uniform CD-ROM driver Revision: 3.20
[4294691.263000] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 4096kB Cache, UDMA(33)
[4294691.335000] usbcore: registered new driver usbfs
[4294691.335000] usbcore: registered new driver hub
[4294691.337000] USB Universal Host Controller Interface driver v2.3
[4294691.337000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
[4294691.337000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294691.337000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294691.337000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294691.337000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x0000ff80
[4294691.338000] hub 1-0:1.0: USB hub found
[4294691.338000] hub 1-0:1.0: 2 ports detected
[4294691.439000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[4294691.439000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294691.439000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294691.439000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294691.439000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000ff60
[4294691.440000] hub 2-0:1.0: USB hub found
[4294691.440000] hub 2-0:1.0: 2 ports detected
[4294691.541000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[4294691.541000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294691.541000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294691.541000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294691.541000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x0000ff40
[4294691.542000] hub 3-0:1.0: USB hub found
[4294691.542000] hub 3-0:1.0: 2 ports detected
[4294691.643000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
[4294691.643000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294691.643000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294691.643000] ehci_hcd 0000:00:1d.7: debug port 1
[4294691.643000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294691.643000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294691.644000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xfe700800
[4294691.648000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294691.649000] hub 4-0:1.0: USB hub found
[4294691.649000] hub 4-0:1.0: 6 ports detected
[4294691.831000] Attempting manual resume
[4294691.868000] EXT3-fs: mounted filesystem with ordered data mode.
[4294691.869000] kjournald starting.  Commit interval 5 seconds
[4294696.607000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294698.312000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294698.365000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294698.429000] input: PC Speaker as /class/input/input1
[4294698.436000] hw_random: RNG not detected
[4294698.441000] Linux agpgart interface v0.101 (c) Dave Jones
[4294698.443000] agpgart: Detected an Intel E7505 Chipset.
[4294698.450000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294698.535000] Floppy drive(s): fd0 is 1.44M
[4294698.574000] FDC 0 is a post-1991 82077
[4294698.687000] nvidia: module license 'NVIDIA' taints kernel.
[4294698.695000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
[4294698.696000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[4294698.786000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[4294698.821000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
[4294698.821000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294698.855000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[4294698.855000] Copyright (c) 1999-2005 Intel Corporation.
[4294698.864000] ts: Compaq touchscreen protocol output
[4294698.883000] parport: PnPBIOS parport detected.
[4294698.883000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294699.132000] intel8x0_measure_ac97_clock: measured 50313 usecs
[4294699.132000] intel8x0: clocking to 48000
[4294699.133000] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 24 (level, low) -> IRQ 217
[4294699.405000] e1000: 0000:03:0e.0: e1000_probe: (PCI-X:100MHz:64-bit) 00:0d:56:c5:07:c2
[4294699.431000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[4294699.593000] lp0: using parport0 (interrupt-driven).
[4294699.660000] Adding 2907724k swap on /dev/sda5.  Priority:-1 extents:1 across:2907724k
[4294699.705000] EXT3 FS on sda1, internal journal
[4294699.862000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294699.862000] md: bitmap version 4.39
[4294700.244000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294700.682000] NET: Registered protocol family 17
[4294700.820000] cdrom: hdd: mrw address space DMA selected
[4294701.040000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[4294702.685000] NET: Registered protocol family 10
[4294702.686000] lo: Disabled Privacy Extensions
[4294702.686000] IPv6 over IPv4 tunneling driver
[4294706.749000] ACPI: Power Button (FF) [PWRF]
[4294706.749000] ACPI: Power Button (CM) [VBTN]
[4294706.900000] ibm_acpi: ec object not found
[4294706.924000] pcc_acpi: loading...
[4294710.420000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294710.420000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4294710.420000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[4294713.482000] eth0: no IPv6 routers present
[4294723.349000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294723.572000] ISO 9660 Extensions: RRIP_1991A
[4294723.851000] cdrom: hdd: mrw address space DMA selected
[4294723.906000] UDF-fs: No VRS found
[4294723.923000] cdrom: hdd: mrw address space DMA selected
[4294723.930000] UDF-fs: No VRS found
[4294723.950000] cdrom: hdd: mrw address space DMA selected
[4294723.955000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294723.956000] ISO 9660 Extensions: RRIP_1991A
[4295266.314000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4295266.607000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4295266.654000] NTFS volume version 3.1.
[4302165.019000] usb 3-1: new full speed USB device using uhci_hcd and address 2[4302165.474000] Linux video capture interface: v1.00
[4302165.505000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type Creative PC-CAM 750 (SPCA504+unknown CCD)
[4302165.507000] usbcore: registered new driver spca5xx
[4302165.507000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[4302174.610000] usb 3-1: usbfs: interface 0 claimed by usbfs while 'gthumb' sets config #1
[4302714.332000] usb 3-1: USB disconnect, address 2
[4302716.532000] usb 3-1: new full speed USB device using uhci_hcd and address 3[4302716.667000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type Creative PC-CAM 750 (SPCA504+unknown CCD)
[4302721.525000] usb 3-1: usbfs: interface 0 claimed by usbfs while 'gthumb' sets config #1
dad@ubuntubox:~$

---

### Post by tonyr on 2006-06-03
Your camera may have shown up as the mounted usb device **/media/removeable**
(or maybe it's /mnt/removeable, I have too many linuxen in my head).  You should
be able to type **mount** on the command line and see waht it says about that.
If it's there, you should be able to navigate down into that to where the pictures are and
simply copy them somewhere else of your own devising.

---

### Post by tonyr on 2006-06-03
Um...this pccam-750 seems to be schizophrenic: it can be either a webcam or
a still photo camera.  Your system may be thinking it's a webcam.  I've never
had a webcam, so I don't know what to do in that case.

EDIT: I looked up the specs on your camera. Apparently it has modes that can
be set, webcam and stills.  As a guess I would say have it on and set to
stills mode before you plug it in.  (but I'm sort of waving my hands around
in the dark here...)

---

### Post by ms30290 on 2006-06-03
Hi TonyR,
  Schytzophrenic??!! --  too funny.  Yes, it was both a webcam and a camera under Windows.  I really only have used it as a camera.  I tried turning it on before plugging in USB cable but no difference.  I also do not see it anywhere under /mount or /media.
  As a side bar - thank you. I think one of the many strong points of Ubuntu is its forums.  I  stepped away to eat dinner and when I got back - BAM!!

---

### Post by tonyr on 2006-06-03
When I plug in my camera, I get the **Photo card detected** box, but I also
get a **usbdisk** icon on my desktop.  I choose **ignore** in the box, and I can
open(double-left-click) the **usbdisk** icon to a file browser, then I can
navigate down to where the pictures are.  The total path for my situation
is **usbdisk->DCIM->100OLYMP** (my camera is an Olympus C-5000 Zoom).

It turns out that the camera/usbdevice is actually mounted on **/media/sda1**.

Nothing like that for you?
(Sorry, been gone for awhile upgrading my Mother-in-Law's computer.)

---

### Post by ms30290 on 2006-06-06
Unfortunately - no joy. It may be time just to get a new camera. My only confusion was that it has worked with linux in the past. Will continue on and keep my eye on the forums. I must say that this has been the only problem I personally have encountered with Dapper so far (and this isn't really that much of a problem - just a head scratcher).

---

### Post by martin_prior on 2006-10-07
Did you manage to fis this problem? I have the same except my camera is a kodak ez200.

Thanks for any input.

Regards

Martin Prior

---

### Post by hollerith on 2007-01-29
I've got the Kodak EZ200.  I've spent hundreds of hours trying to make the damn thing work with Linux over the years.  mxhaard is the only one who has been bothered to tackle the spca types.  It does work now in Edgy out-of-the-box ... the picture in gqcam is AWFUL.  The gthumb thing is gthumb trying to be clever and import the photos from the internal memory, some pants proto-usb memory.  Just select ignore.  You won't be able to import though.  It should have been mounted as a filesystem.  It isn't.  


Just give up,  I have and I'm a happy guy now - just like Joe 

:guitar: .  


(obscure Zappa reference)

---

### Post by Robin T Cox on 2007-01-29
The easiest way to transfer photos from your digital camera is to get a cheap card reader.

[http://en.wikipedia.org/wiki/Card_reader](http://en.wikipedia.org/wiki/Card_reader)

Use it to transfer the photos from your camera's SD card to your computer.

---

### Post by undertakingyou on 2007-02-20
I was having the same issues and found that if I ran gthumb as sudo I could then import no problem.  I figured it must be a permissions issue.

I fixed this same issue by editing two files.  The first was the libgphoto2.rules file and the next was the permissions.rules file.  

Both are in /etc/udev/rules.d

I set the "MODE" to "0666" on all entries in the libgphoto2.rules file
And in the permissions.rules file I changed the "USB" line to "MODE="0666""

That has cleared it all up for me.

---

### Post by hollerith on 2007-04-09
@Robin - The EZ200 does not have an SD card!

Running as sudo and/or modifiying udev rules has no effect for me (edgy 6.10).  Still the same old lock error even under sudo.

---

### Post by g8m on 2007-04-10
Dont know much about camara's. But I have a edgy and feisty install. If I plug it in feisty, I can import the photos, if I plug it in edgy I get some error about not being able to allocate the camera.

---

