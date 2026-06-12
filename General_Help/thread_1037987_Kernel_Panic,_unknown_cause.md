---
title: "Kernel Panic, unknown cause"
date: 2009-01-12
forum: General Help
---

### Post by EateryOfPiza on 2009-01-12
Hi,

I'm running Ubuntu 8.04 x86_64 with latest updates applied on a Lenovo T61p.

Over the past 24 hours or so, I've been getting a lot of kernel panics, around 6 so far. I look in the various files located in /var/log, and can't really find anything useful.

For the first two kernel panics, the last line in the logs before restart was this cronjob I had running every 5 minutes, so I commented out that line on /etc/crontab. But the kernel panics still show up, and the last line before restart were both -- Mark -- messages.

I suspect it might have something to do with the 2.6.24-23-generic kernel, since that is the last thing I remember changing.

How do I go about debugging this?

Thanks

---

### Post by Titan8990 on 2009-01-12
Post the result of the following:


dmesg

---

### Post by EateryOfPiza on 2009-01-12
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@crested) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Nov 27 18:13:46 UTC 2008 (Ubuntu 2.6.24-23.46-generic)
[    0.000000] Command line: root=UUID=6928a936-1909-4f10-b20d-e4603517e20d ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfeb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfeb0000 - 00000000bfecc000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfecc000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 786096) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1294336) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1294336
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F68D0 checksum 0
[    0.000000] ACPI: RSDP 000F68D0, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT BFEBB74B, 009C (r1 LENOVO TP-7L        2090  LTP        0)
[    0.000000] ACPI: FACP BFEBB800, 00F4 (r3 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20070126]
[    0.000000] ACPI: DSDT BFEBBC1D, FF05 (r1 LENOVO TP-7L        2090 MSFT  3000000)
[    0.000000] ACPI: FACS BFEE4000, 0040
[    0.000000] ACPI: SSDT BFEBB9B4, 0269 (r1 LENOVO TP-7L        2090 MSFT  3000000)
[    0.000000] ACPI: ECDT BFECBB22, 0052 (r1 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI: TCPA BFECBB74, 0032 (r2 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI: APIC BFECBBA6, 0068 (r1 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI: MCFG BFECBC0E, 003C (r1 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI: HPET BFECBC4A, 0038 (r1 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI: SLIC BFECBDF0, 0176 (r1 LENOVO TP-7L        2090  LTP        0)
[    0.000000] ACPI: BOOT BFECBF66, 0028 (r1 LENOVO TP-7L        2090  LTP        1)
[    0.000000] ACPI: ASF! BFECBF8E, 0072 (r16 LENOVO TP-7L        2090 PTL         1)
[    0.000000] ACPI: SSDT BFEE271B, 025F (r1 LENOVO TP-7L        2090 INTL 20050513)
[    0.000000] ACPI: SSDT BFEE297A, 00A6 (r1 LENOVO TP-7L        2090 INTL 20050513)
[    0.000000] ACPI: SSDT BFEE2A20, 04F7 (r1 LENOVO TP-7L        2090 INTL 20050513)
[    0.000000] ACPI: SSDT BFEE2F17, 08BD (r1 LENOVO TP-7L        2090 INTL 20050513)
[    0.000000] ACPI: SSDT BFEE37D4, 069C (r1 LENOVO TP-7L        2090 INTL 20050513)
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad T61
[    0.000000] ACPI: Added _OSI(Linux)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000013c000000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 786096) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1294336) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000013c000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1294336
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   786096
[    0.000000]     0:  1048576 ->  1294336
[    0.000000] On node 0 totalpages: 1031757
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1222 pages reserved
[    0.000000]   DMA zone: 2719 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767720 pages, LIFO batch:31
[    0.000000]   Normal zone: 3360 pages used for memmap
[    0.000000]   Normal zone: 242400 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 00000000000d4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d4000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000bfeb0000 - 00000000bfecc000
[    0.000000] swsusp: Registered nosave memory region: 00000000bfecc000 - 00000000bff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000bff00000 - 00000000c0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000c0000000 - 00000000f0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000f4000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f4000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec10000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec10000 - 00000000fed00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fed00000 - 00000000fed14000
[    0.000000] swsusp: Registered nosave memory region: 00000000fed14000 - 00000000fed1a000
[    0.000000] swsusp: Registered nosave memory region: 00000000fed1a000 - 00000000fed1c000
[    0.000000] swsusp: Registered nosave memory region: 00000000fed1c000 - 00000000fed90000
[    0.000000] swsusp: Registered nosave memory region: 00000000fed90000 - 00000000fee00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000ff000000
[    0.000000] swsusp: Registered nosave memory region: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:30000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1012839
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=6928a936-1909-4f10-b20d-e4603517e20d ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   18.214658] Marking TSC unstable due to TSCs unsynchronized
[   18.214660] time.c: Detected 2493.762 MHz processor.
[   18.216608] Console: colour VGA+ 80x25
[   18.216611] console [tty0] enabled
[   18.216630] Checking aperture...
[   18.216649] Calgary: detecting Calgary via BIOS EBDA area
[   18.216650] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   18.216652] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   18.252041] Placing software IO TLB between 0x103b000 - 0x503b000
[   18.286540] Memory: 3977568k/5177344k available (2491k kernel code, 149460k reserved, 1317k data, 320k init)
[   18.286570] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   18.364415] Calibrating delay using timer specific routine.. 4992.91 BogoMIPS (lpj=9985820)
[   18.364442] Security Framework initialized
[   18.364448] SELinux:  Disabled at boot.
[   18.364457] AppArmor: AppArmor initialized
[   18.364460] Failure registering capabilities with primary security module.
[   18.364723] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   18.367075] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   18.368179] Mount-cache hash table entries: 256
[   18.368285] Initializing cgroup subsys ns
[   18.368289] Initializing cgroup subsys cpuacct
[   18.368302] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.368304] CPU: L2 cache: 6144K
[   18.368305] CPU 0/0 -> Node 0
[   18.368306] using mwait in idle threads.
[   18.368308] CPU: Physical Processor ID: 0
[   18.368309] CPU: Processor Core ID: 0
[   18.368314] CPU0: Thermal monitoring enabled (TM2)
[   18.368325] SMP alternatives: switching to UP code
[   18.369019] Early unpacking initramfs... done
[   18.627455] ACPI: Core revision 20070126
[   18.627512] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.684537] Using local APIC timer interrupts.
[   18.724579] APIC timer calibration result 12468806
[   18.724580] Detected 12.468 MHz APIC timer.
[   18.724644] SMP alternatives: switching to SMP code
[   18.725229] Booting processor 1/2 APIC 0x1
[   18.736437] Initializing CPU#1
[   18.812970] Calibrating delay using timer specific routine.. 4987.55 BogoMIPS (lpj=9975101)
[   18.812975] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.812976] CPU: L2 cache: 6144K
[   18.812977] CPU 1/1 -> Node 0
[   18.812979] CPU: Physical Processor ID: 0
[   18.812979] CPU: Processor Core ID: 1
[   18.812984] CPU1: Thermal monitoring enabled (TM2)
[   18.813716] Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz stepping 06
[   18.813242] Brought up 2 CPUs
[   18.813317] CPU0 attaching sched-domain:
[   18.813319]  domain 0: span 03
[   18.813320]   groups: 01 02
[   18.813322]   domain 1: span 03
[   18.813323]    groups: 03
[   18.813324] CPU1 attaching sched-domain:
[   18.813325]  domain 0: span 03
[   18.813326]   groups: 02 01
[   18.813328]   domain 1: span 03
[   18.813328]    groups: 03
[   18.813504] net_namespace: 120 bytes
[   18.813788] Time: 15:12:04  Date: 01/12/09
[   18.813812] NET: Registered protocol family 16
[   18.813958] ACPI: bus type pci registered
[   18.814015] PCI: Using configuration type 1
[   18.815343] ACPI: EC: EC description table is found, configuring boot EC
[   18.819380] ACPI: BIOS _OSI(Linux) query honored via DMI
[   18.820638] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   18.898884] ACPI: Interpreter enabled
[   18.898886] ACPI: (supports S0 S3 S4 S5)
[   18.898898] ACPI: Using IOAPIC for interrupt routing
[   18.906550] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[   18.906551] ACPI: EC: driver started in poll mode
[   18.906689] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.907843] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   18.907849] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   18.909514] PCI: Transparent bridge - 0000:00:1e.0
[   18.909612] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.909774] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   18.909882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   18.909989] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   18.910096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[   18.910202] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[   18.910311] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[   18.910419] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   18.913481] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[   18.913662] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[   18.913842] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[   18.914021] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[   18.914201] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[   18.914380] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[   18.914558] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[   18.914738] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[   18.915504] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   18.915657] ACPI: Power Resource [PUBS] (on)
[   18.915704] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.915727] pnp: PnP ACPI init
[   18.915732] ACPI: bus type pnp registered
[   18.916770] pnpacpi: exceeded the max number of mem resources: 12
[   18.919645] pnp: PnP ACPI: found 11 devices
[   18.919646] ACPI: ACPI bus type pnp unregistered
[   18.919812] PCI: Using ACPI for IRQ routing
[   18.919813] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.932290] NET: Registered protocol family 8
[   18.932291] NET: Registered protocol family 20
[   18.932314] PCI-GART: No AMD northbridge found.
[   18.932321] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   18.932323] hpet0: 3 64-bit timers, 14318180 Hz
[   18.933348] AppArmor: AppArmor Filesystem Enabled
[   18.936267] Time: hpet clocksource has been installed.
[   18.936275] Switched to high resolution mode on CPU 0
[   18.937544] Switched to high resolution mode on CPU 1
[   18.944253] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   18.944255] system 00:00: iomem range 0xc0000-0xc3fff has been reserved
[   18.944257] system 00:00: iomem range 0xc4000-0xc7fff has been reserved
[   18.944259] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[   18.944260] system 00:00: iomem range 0xcc000-0xcffff has been reserved
[   18.944262] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[   18.944264] system 00:00: iomem range 0x0-0x0 could not be reserved
[   18.944265] system 00:00: iomem range 0x0-0x0 could not be reserved
[   18.944267] system 00:00: iomem range 0x0-0x0 could not be reserved
[   18.944268] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[   18.944270] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[   18.944272] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[   18.944276] system 00:02: ioport range 0x164e-0x164f has been reserved
[   18.944277] system 00:02: ioport range 0x1000-0x107f has been reserved
[   18.944279] system 00:02: ioport range 0x1180-0x11bf has been reserved
[   18.944280] system 00:02: ioport range 0x800-0x80f has been reserved
[   18.944282] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[   18.944284] system 00:02: ioport range 0x1600-0x165f could not be reserved
[   18.944286] system 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   18.944288] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   18.944289] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   18.944291] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   18.944293] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[   18.944295] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
[   18.944626] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0
[   18.944627] PCI: Bridge: 0000:00:01.0
[   18.944629]   IO window: 2000-2fff
[   18.944631]   MEM window: d0000000-d2ffffff
[   18.944633]   PREFETCH window: e0000000-efffffff
[   18.944636] PCI: Bridge: 0000:00:1c.0
[   18.944640]   IO window: 3000-3fff
[   18.944645]   MEM window: dc100000-df2fffff
[   18.944651]   PREFETCH window: dfd00000-dfdfffff
[   18.944656] PCI: Bridge: 0000:00:1c.1
[   18.944660]   IO window: 4000-4fff
[   18.944667]   MEM window: d4000000-d7dfffff
[   18.944671]   PREFETCH window: dfa00000-dfafffff
[   18.944681] PCI: Bridge: 0000:00:1c.2
[   18.944683]   IO window: 5000-5fff
[   18.944688]   MEM window: fc000000-fdffffff
[   18.944694]   PREFETCH window: f8000000-f80fffff
[   18.944701] PCI: Bridge: 0000:00:1c.3
[   18.944704]   IO window: 6000-6fff
[   18.944711]   MEM window: d8000000-d9ffffff
[   18.944717]   PREFETCH window: df700000-df7fffff
[   18.944722] PCI: Bridge: 0000:00:1c.4
[   18.944727]   IO window: 7000-7fff
[   18.944731]   MEM window: cc000000-cdffffff
[   18.944735]   PREFETCH window: df400000-df4fffff
[   18.944744] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[   18.944745]   IO window: 00008000-000080ff
[   18.944749]   IO window: 00008400-000084ff
[   18.944756]   PREFETCH window: f4000000-f7ffffff
[   18.944763]   MEM window: c4000000-c7ffffff
[   18.944768] PCI: Bridge: 0000:00:1e.0
[   18.944773]   IO window: 8000-bfff
[   18.944780]   MEM window: f8100000-fbffffff
[   18.944786]   PREFETCH window: f4000000-f7ffffff
[   18.944801] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.944804] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.944825] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 20
[   18.944829] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.944854] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 21
[   18.944859] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.944884] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 22
[   18.944889] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   18.944916] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 23
[   18.944921] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   18.944949] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 20 (level, low) -> IRQ 20
[   18.944956] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   18.944970] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[   18.944977] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.944995] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.945003] PCI: Setting latency timer of device 0000:15:00.0 to 64
[   18.945012] NET: Registered protocol family 2
[   18.980270] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.981107] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   18.984396] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   18.984963] TCP: Hash tables configured (established 524288 bind 65536)
[   18.984965] TCP reno registered
[   18.996279] checking if image is initramfs... it is
[   19.542254] Freeing initrd memory: 7562k freed
[   19.544878] Simple Boot Flag at 0x35 set to 0x1
[   19.546070] audit: initializing netlink socket (disabled)
[   19.546086] audit(1231773124.220:1): initialized
[   19.547769] VFS: Disk quotas dquot_6.5.1
[   19.547841] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   19.547928] io scheduler noop registered
[   19.547930] io scheduler anticipatory registered
[   19.547931] io scheduler deadline registered
[   19.548010] io scheduler cfq registered (default)
[   19.554057] Boot video device is 0000:01:00.0
[   19.554197] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   19.554224] assign_interrupt_mode Found MSI capability
[   19.554246] Allocate Port Service[0000:00:01.0:pcie00]
[   19.554277] Allocate Port Service[0000:00:01.0:pcie02]
[   19.554347] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.554406] assign_interrupt_mode Found MSI capability
[   19.554449] Allocate Port Service[0000:00:1c.0:pcie00]
[   19.554474] Allocate Port Service[0000:00:1c.0:pcie02]
[   19.554569] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   19.554623] assign_interrupt_mode Found MSI capability
[   19.554666] Allocate Port Service[0000:00:1c.1:pcie00]
[   19.554693] Allocate Port Service[0000:00:1c.1:pcie02]
[   19.554785] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   19.554839] assign_interrupt_mode Found MSI capability
[   19.554882] Allocate Port Service[0000:00:1c.2:pcie00]
[   19.554907] Allocate Port Service[0000:00:1c.2:pcie02]
[   19.555004] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   19.555058] assign_interrupt_mode Found MSI capability
[   19.555101] Allocate Port Service[0000:00:1c.3:pcie00]
[   19.555127] Allocate Port Service[0000:00:1c.3:pcie02]
[   19.555222] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   19.555276] assign_interrupt_mode Found MSI capability
[   19.555319] Allocate Port Service[0000:00:1c.4:pcie00]
[   19.555343] Allocate Port Service[0000:00:1c.4:pcie02]
[   19.573983] Real Time Clock Driver v1.12ac
[   19.574055] hpet_resources: 0xfed00000 is busy
[   19.574089] Linux agpgart interface v0.102
[   19.574090] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.574917] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.574967] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.575034] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   19.582813] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.582817] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.591275] mice: PS/2 mouse device common for all mice
[   19.591304] cpuidle: using governor ladder
[   19.591305] cpuidle: using governor menu
[   19.591407] NET: Registered protocol family 1
[   19.591478] registered taskstats version 1
[   19.591575]   Magic number: 9:627:234
[   19.591580]   hash matches device ttyv4
[   19.591613] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   19.591615] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.591616] EDD information not available.
[   19.591621] Freeing unused kernel memory: 320k freed
[   19.593325] Write protecting the kernel read-only data: 1036k
[   19.597595] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.721666] fuse init (API version 7.9)
[   20.731747] ACPI: SSDT BFEE1B32, 0306 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[   20.731978] ACPI: SSDT BFEE1EBD, 085E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[   20.735637] Monitor-Mwait will be used to enter C-1 state
[   20.735639] Monitor-Mwait will be used to enter C-2 state
[   20.735641] Monitor-Mwait will be used to enter C-3 state
[   20.735731] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   20.735734] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.735907] ACPI: SSDT BFEE1A6A, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[   20.736120] ACPI: SSDT BFEE1E38, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[   20.740655] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   20.740658] ACPI: Processor [CPU1] (supports 8 throttling states)
[   20.743260] ACPI: Thermal Zone [THM0] (55 C)
[   20.744627] ACPI: Thermal Zone [THM1] (43 C)
[   20.897565] usbcore: registered new interface driver usbfs
[   20.897583] usbcore: registered new interface driver hub
[   20.897611] usbcore: registered new device driver usb
[   20.898468] USB Universal Host Controller Interface driver v3.0
[   20.898510] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 20
[   20.898521] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   20.898526] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   20.898720] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   20.898757] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[   20.898852] usb usb1: configuration #1 chosen from 1 choice
[   20.898866] hub 1-0:1.0: USB hub found
[   20.898870] hub 1-0:1.0: 2 ports detected
[   20.981979] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   20.981982] Copyright (c) 1999-2006 Intel Corporation.
[   21.000508] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   21.000520] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   21.000523] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   21.000538] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   21.000572] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[   21.000651] usb usb2: configuration #1 chosen from 1 choice
[   21.000667] hub 2-0:1.0: USB hub found
[   21.000672] hub 2-0:1.0: 2 ports detected
[   21.002416] SCSI subsystem initialized
[   21.037993] libata version 3.00 loaded.
[   21.104885] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 20
[   21.104900] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   21.106110] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1e:37:88:ac:fa
[   21.202576] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   21.203298] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 22
[   21.204935] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   21.204943] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   21.204981] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[   21.208910] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   21.208920] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfe226400
[   21.240051] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   21.253559] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.253642] usb usb3: configuration #1 chosen from 1 choice
[   21.253659] hub 3-0:1.0: USB hub found
[   21.253664] hub 3-0:1.0: 4 ports detected
[   21.264599] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 19
[   21.265935] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   21.265943] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.265991] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   21.269915] ehci_hcd 0000:00:1d.7: debug port 1
[   21.269925] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   21.269936] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe226800
[   21.276250] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.276319] usb usb4: configuration #1 chosen from 1 choice
[   21.276336] hub 4-0:1.0: USB hub found
[   21.276340] hub 4-0:1.0: 6 ports detected
[   21.295753] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 17
[   21.295760] PCI: Setting latency timer of device 0000:15:00.1 to 64
[   21.295565] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.295575] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   21.295580] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.295595] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   21.295629] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[   21.295698] usb usb5: configuration #1 chosen from 1 choice
[   21.295714] hub 5-0:1.0: USB hub found
[   21.295718] hub 5-0:1.0: 2 ports detected
[   21.348800] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   21.363780] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[   21.363787] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   21.363792] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.363808] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   21.363835] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[   21.363909] usb usb6: configuration #1 chosen from 1 choice
[   21.363923] hub 6-0:1.0: USB hub found
[   21.363927] hub 6-0:1.0: 2 ports detected
[   21.379471] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   21.379479] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   21.379482] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   21.379494] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   21.379528] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[   21.379592] usb usb7: configuration #1 chosen from 1 choice
[   21.379605] hub 7-0:1.0: USB hub found
[   21.379608] hub 7-0:1.0: 2 ports detected
[   21.393767] ata_piix 0000:00:1f.2: version 2.12
[   21.393772] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   21.417181] Clocksource tsc unstable (delta = -342366831 ns)
[   21.433569] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   21.434452] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[   21.434487] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.434850] scsi0 : ata_piix
[   21.434984] scsi1 : ata_piix
[   21.435684] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1c30 irq 14
[   21.435686] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1c38 irq 15
[   21.459006] usb 1-2: configuration #1 chosen from 1 choice
[   21.469177] ata1.00: HPA unlocked: 390719855 -> 390721968, native 390721968
[   21.469181] ata1.00: ATA-8: Hitachi HTS722020K9SA00, DC4OC76A, max UDMA/133
[   21.469182] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   21.471816] ata1.00: configured for UDMA/133
[   21.492212] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72202 DC4O PQ: 0 ANSI: 5
[   21.496623] Driver 'sd' needs updating - please use bus_type methods
[   21.496655] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   21.496663] sd 0:0:0:0: [sda] Write Protect is off
[   21.496664] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.496674] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.496703] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   21.496710] sd 0:0:0:0: [sda] Write Protect is off
[   21.496711] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.496721] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.496723]  sda: sda1 sda2 sda3
[   21.503584] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.505563] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.619465] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b032a1ea964]
[   22.239692] EXT3-fs: INFO: recovery required on readonly filesystem.
[   22.239695] EXT3-fs: write access will be enabled during recovery.
[   23.651529] kjournald starting.  Commit interval 5 seconds
[   23.652082] EXT3-fs: sda1: orphan cleanup on readonly fs
[   23.652087] ext3_orphan_cleanup: deleting unreferenced inode 90188
[   23.652131] ext3_orphan_cleanup: deleting unreferenced inode 3637287
[   23.652136] EXT3-fs: sda1: 2 orphan inodes deleted
[   23.652137] EXT3-fs: recovery complete.
[   23.654729] EXT3-fs: mounted filesystem with ordered data mode.
[   27.130546] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.232595] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.294370] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   27.562271] Non-volatile memory driver v1.2
[   27.584903] ricoh-mmc: Ricoh MMC Controller disabling driver
[   27.584904] ricoh-mmc: Copyright(c) Philip Langdale
[   27.584934] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   27.584952] ricoh-mmc: Controller is now disabled.
[   27.685157] iTCO_vendor_support: vendor-support=0
[   27.687142] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   27.687205] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   27.687238] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.709516] input: Power Button (FF) as /devices/virtual/input/input3
[   27.764992] ACPI: Power Button (FF) [PWRF]
[   27.765036] input: Lid Switch as /devices/virtual/input/input4
[   27.797837] ACPI: Lid Switch [LID]
[   27.797877] input: Sleep Button (CM) as /devices/virtual/input/input5
[   27.798699] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   27.827143] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k2
[   27.827145] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[   27.856833] ACPI: Sleep Button (CM) [SLPB]
[   27.856908] ACPI: WMI-Acer: Mapper loaded
[   27.895526] ACPI: Battery Slot [BAT0] (battery present)
[   27.929689] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   27.929693] Socket status: 30000006
[   27.929696] pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
[   27.929698] pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
[   27.929699] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   27.936297] ACPI: Battery Slot [BAT1] (battery present)
[   27.938920] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   27.984925] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   27.986538] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   27.998895] ACPI: AC Adapter [AC] (on-line)
[   28.040586] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   28.315791] nvidia: module license 'NVIDIA' taints kernel.
[   28.369511] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   28.369515] serio: Synaptics pass-through port at isa0060/serio1/input0
[   28.575289] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.575298] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   28.575398] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   28.575939] sdhci: Secure Digital Host Controller Interface driver
[   28.575941] sdhci: Copyright(c) Pierre Ossman
[   28.577332] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 21)
[   28.577369] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 18
[   28.579903] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   28.579916] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   28.579983] mmc0: SDHCI at 0xf8101800 irq 18 DMA
[   28.608021] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   28.619802] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   28.619804] thinkpad_acpi: http://ibm-acpi.sf.net/
[   28.619805] thinkpad_acpi: ThinkPad BIOS 7LETA9WW (2.09 ), EC 7KHT24WW-1.08
[   28.619807] thinkpad_acpi: Lenovo ThinkPad T61p
[   28.620771] thinkpad_acpi: radio switch found; radios are enabled
[   28.624565] thinkpad_acpi: acpi_bus_get_device(bay) failed: -19
[   28.624644] thinkpad_acpi: disabling subdriver bay
[   28.636472] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   28.636768] input: ThinkPad Extra Buttons as /devices/virtual/input/input9
[   28.747701] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 2.3.5kds
[   28.747704] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   28.747835] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   28.747866] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   28.749468] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   28.797497] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   28.797718] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   28.798057] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   28.844551] input: 4965AGN as /devices/pci0000:00/0000:00:1c.1/0000:03:00.0/input/input10
[   28.931904] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 17
[   28.931909] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   28.933444] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   29.881514] lp: driver loaded but no devices found
[   29.927336] thinkpad_ec: thinkpad_ec 0.36 loaded.
[   29.929611] tp_smapi 0.36 loading...
[   29.929703] tp_smapi successfully loaded (smapi_port=0xb2).
[   29.983028] Adding 8000360k swap on /dev/sda2.  Priority:-1 extents:1 across:8000360k
[   30.040664] EXT3 FS on sda1, internal journal
[   30.113041] kjournald starting.  Commit interval 5 seconds
[   30.113583] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   30.113901] EXT3 FS on sda3, internal journal
[   30.113903] EXT3-fs: recovery complete.
[   30.113905] EXT3-fs: mounted filesystem with ordered data mode.
[   30.286160] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.521232] ACPI: ACPI Dock Station Driver 
[   30.527295] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   30.527300] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   30.527317] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   30.527329] ACPI: \_SB_.PCI0.SATA.SCND.MSTR: found ejectable bay
[   30.527332] ACPI: \_SB_.PCI0.SATA.SCND.MSTR: Adding notify handler
[   30.527343] ACPI: Error installing bay notify handler
[   30.527345] ACPI: Bay [\_SB_.PCI0.SATA.SCND.MSTR] Added
[   31.369443] ppdev: user-space parallel port driver
[   31.402719] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   31.439302] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input11
[   31.576785] audit(1231773159.921:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5680 profile="/usr/sbin/cupsd" namespace="default"
[   31.576858] audit(1231773159.921:3): type=1503 operation="inode_permission" requested_mask="w::" denied_mask="w::" name="/etc/krb5.conf" pid=5680 profile="/usr/sbin/cupsd" namespace="default"
[   32.060406] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input12
[   32.115611] tun: Universal TUN/TAP device driver, 1.6
[   32.115614] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   32.476624] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   32.476633] vboxdrv: Successfully done.
[   32.476637] vboxdrv: Found 2 processor cores.
[   32.477457] VBoxDrv: dbg - g_abExecMemory=ffffffff88d24640
[   32.477514] vboxdrv: fAsync=1 offMin=0x1388ed offMax=0x1388ed
[   32.478039] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   32.478045] vboxdrv: Successfully loaded version 2.1.0 (interface 0x000a0008).
[   32.808202] NET: Registered protocol family 10
[   32.808817] lo: Disabled Privacy Extensions
[   33.331754] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   33.331897] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 40100102, writing 40100106)
[   33.422524] Bluetooth: Core ver 2.11
[   33.422999] NET: Registered protocol family 31
[   33.423005] Bluetooth: HCI device and connection manager initialized
[   33.423012] Bluetooth: HCI socket layer initialized
[   33.453083] Bluetooth: L2CAP ver 2.9
[   33.453091] Bluetooth: L2CAP socket layer initialized
[   33.597292] Registered led device: iwl-phy0:radio
[   33.597334] Registered led device: iwl-phy0:assoc
[   33.597365] Registered led device: iwl-phy0:RX
[   33.597396] Registered led device: iwl-phy0:TX
[   33.599659] Bluetooth: RFCOMM socket layer initialized
[   33.599679] Bluetooth: RFCOMM TTY layer initialized
[   33.599683] Bluetooth: RFCOMM ver 1.8
[   33.646392] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.693270] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   33.693280] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   33.700694] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.712005] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   36.195092] NET: Registered protocol family 17
[   41.831016] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input13
[   44.138354] eth0: no IPv6 routers present
[   49.901863] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input14
[   60.091750] CPU0 attaching NULL sched-domain.
[   60.091760] CPU1 attaching NULL sched-domain.
[   60.104419] CPU0 attaching sched-domain:
[   60.104422]  domain 0: span 03
[   60.104424]   groups: 01 02
[   60.104426]   domain 1: span 03
[   60.104427]    groups: 03
[   60.104428] CPU1 attaching sched-domain:
[   60.104429]  domain 0: span 03
[   60.104430]   groups: 02 01
[   60.104431]   domain 1: span 03
[   60.104432]    groups: 03
[   65.459253] CPU0 attaching NULL sched-domain.
[   65.459260] CPU1 attaching NULL sched-domain.
[   65.460558] CPU0 attaching sched-domain:
[   65.460560]  domain 0: span 03
[   65.460562]   groups: 01 02
[   65.460563]   domain 1: span 03
[   65.460564]    groups: 03
[   65.460566] CPU1 attaching sched-domain:
[   65.460567]  domain 0: span 03
[   65.460567]   groups: 02 01
[   65.460569]   domain 1: span 03
[   65.460577]    groups: 03
[   93.994357] CPU0 attaching NULL sched-domain.
[   93.994361] CPU1 attaching NULL sched-domain.
[   94.698096] CPU0 attaching sched-domain:
[   94.698102]  domain 0: span 03
[   94.698103]   groups: 01 02
[   94.698105]   domain 1: span 03
[   94.698106]    groups: 03
[   94.698107] CPU1 attaching sched-domain:
[   94.698108]  domain 0: span 03
[   94.698109]   groups: 02 01
[   94.698110]   domain 1: span 03
[   94.698111]    groups: 03
[  106.824819] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input15

```

---

### Post by Titan8990 on 2009-01-12
Add this to the end of your kernel line in /boot/grub/menu.lst:


acpi=off


So it should look something like this:


```
title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa ro quiet splash acpi=off
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

```

---

### Post by albinootje on 2009-01-12
> **EateryOfPiza said:**
> 
[   18.916770] pnpacpi: exceeded the max number of mem resources: 12
[   18.919645] pnp: PnP ACPI: found 11 devices
[   18.919646] ACPI: ACPI bus type pnp unregistered
[   18.919812] PCI: Using ACPI for IRQ routing
[   18.919813] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report


See here :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Try the various kernel boot options, e.g. "noapic nolapic", and report back.

---

### Post by EateryOfPiza on 2009-01-12
What effects will that boot parameter have? If I turn off ACPI, will I lose the ability to suspend? What about speedstepping? I use KPowersave to lock the processor into a low performance state to save battery. Also, what would happen my ability to control brightness (again to save battery) or force a battery to discharge (to stop the BIOS from completely discharging my drive bay battery and damange it)?

Either way, I will do it tonight when I go to bed and see if it kernel panics again. The issue tends to happen when I'm not at the computer.

---

### Post by Robstarusa on 2009-01-12
Hi,

This started happening to me yesterday!

I have a Thinkpad T61.

You don't have the 4965AGN connected to an 802.11n access point do you?

Can you try using a wired link & see if the kernel panics still occur?

---

### Post by albinootje on 2009-01-12
> **EateryOfPiza said:**
> What effects will that boot parameter have? If I turn off ACPI, will I lose the ability to suspend?


In my opinion the extra boot options in this situation is the first step to find out where the problem is exactly.

---

### Post by EateryOfPiza on 2009-01-12
> **Robstarusa said:**
> 
You don't have the 4965AGN connected to an 802.11n access point do you?

Can you try using a wired link & see if the kernel panics still occur?

That was one of the first things I thought of, but yes, the kernel panic occurred on both a wired and wireless connection.

---

### Post by EateryOfPiza on 2009-01-12
I just tried booting with acpi=off. Here is the relevant grub option.

```
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (acpi=off)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6928a936-1909-4f10-b20d-e4603517e20d ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

```

Booting with acpi=off caused X to fail to start. Ubuntu went through the normal booting sequence, and then when it came to the starting X part, the screen went blank thrice and then came up with a screen that looked like some kind of display error. There was a dialog box that was partially shown on the screen, and it said "Ubuntu is running in low graphics mode. Your screen and graphics card could not be detected." There was some other text, but it was off the screen.

I went to tty2 and tried to startx manually but it failed.

Here is the relevant part from /var/log/messages

```
Jan 12 15:59:35 GAMERA syslogd 1.5.0#1ubuntu1: restart.
Jan 12 15:59:35 GAMERA kernel: Inspecting /boot/System.map-2.6.24-23-generic
Jan 12 15:59:35 GAMERA kernel: Loaded 28514 symbols from /boot/System.map-2.6.24-23-generic.
Jan 12 15:59:35 GAMERA kernel: Symbols match kernel version 2.6.24.
Jan 12 15:59:35 GAMERA kernel: Loaded 36364 symbols from 84 modules.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Linux version 2.6.24-23-generic (buildd@crested) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Nov 27 18:13:46 UTC 2008 (Ubuntu 2.6.24-23.46-generic)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Command line: root=UUID=6928a936-1909-4f10-b20d-e4603517e20d ro quiet splash acpi=off
Jan 12 15:59:35 GAMERA kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfeb0000 (usable)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000bfeb0000 - 00000000bfecc000 (ACPI data)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000bfecc000 - 00000000bff00000 (ACPI NVS)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] end_pfn_map = 1294336
Jan 12 15:59:35 GAMERA kernel: [    0.000000] DMI present.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] No NUMA configuration found
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Faking a node at 0000000000000000-000000013c000000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000013c000000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Zone PFN ranges:
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   DMA             0 ->     4096
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   DMA32        4096 ->  1048576
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   Normal    1048576 ->  1294336
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Movable zone start PFN for each node
Jan 12 15:59:35 GAMERA kernel: [    0.000000] early_node_map[3] active PFN ranges
Jan 12 15:59:35 GAMERA kernel: [    0.000000]     0:        0 ->      157
Jan 12 15:59:35 GAMERA kernel: [    0.000000]     0:      256 ->   786096
Jan 12 15:59:35 GAMERA kernel: [    0.000000]     0:  1048576 ->  1294336
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Jan 12 15:59:35 GAMERA kernel: [    0.000000] MPTABLE: OEM ID: INTEL    MPTABLE: Product ID: Napa ERB     MPTABLE: APIC at: 0xFEE00000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Processor #1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] I/O APIC #2 at 0xFEC00000.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Setting APIC routing to flat
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Processors: 2
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 00000000000d4000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000d4000 - 00000000000e0000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000bfeb0000 - 00000000bfecc000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000bfecc000 - 00000000bff00000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000bff00000 - 00000000c0000000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000c0000000 - 00000000f0000000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000f4000000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000f4000000 - 00000000fec00000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec10000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fec10000 - 00000000fed00000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fed00000 - 00000000fed14000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fed14000 - 00000000fed1a000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fed1a000 - 00000000fed1c000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fed1c000 - 00000000fed90000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fed90000 - 00000000fee00000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000ff000000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000ff000000 - 0000000100000000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:30000000)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1012839
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Policy zone: Normal
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Kernel command line: root=UUID=6928a936-1909-4f10-b20d-e4603517e20d ro quiet splash acpi=off
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Initializing CPU#0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] TSC calibrated against PIT
Jan 12 15:59:35 GAMERA kernel: [    0.000000] time.c: Detected 2493.833 MHz processor.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Console: colour VGA+ 80x25
Jan 12 15:59:35 GAMERA kernel: [    0.000000] console [tty0] enabled
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Checking aperture...
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Placing software IO TLB between 0x103b000 - 0x503b000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Memory: 3977568k/5177344k available (2491k kernel code, 149460k reserved, 1317k data, 320k init)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Calibrating delay using timer specific routine.. 4994.51 BogoMIPS (lpj=9989027)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Security Framework initialized
Jan 12 15:59:35 GAMERA kernel: [    0.000000] SELinux:  Disabled at boot.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] AppArmor: AppArmor initialized
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Failure registering capabilities with primary security module.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Mount-cache hash table entries: 256
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Initializing cgroup subsys ns
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU: L2 cache: 6144K
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU 0/0 -> Node 0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] using mwait in idle threads.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU: Physical Processor ID: 0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU: Processor Core ID: 0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU0: Thermal monitoring enabled (TM2)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] SMP alternatives: switching to UP code
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Early unpacking initramfs... done
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ExtINT not setup in hardware but reported by MP table
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Using local APIC timer interrupts.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Detected 12.469 MHz APIC timer.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] SMP alternatives: switching to SMP code
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Booting processor 1/2 APIC 0x1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Initializing CPU#1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Calibrating delay using timer specific routine.. 4987.64 BogoMIPS (lpj=9975283)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU: L2 cache: 6144K
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU 1/1 -> Node 0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU: Physical Processor ID: 0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU: Processor Core ID: 1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] CPU1: Thermal monitoring enabled (TM2)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz stepping 06
Jan 12 15:59:35 GAMERA kernel: [    0.000000] checking TSC synchronization [CPU#0 -> CPU#1]:
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Measured 412875 cycles TSC warp between CPUs, turning off TSC clock.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Marking TSC unstable due to check_tsc_sync_source failed
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Brought up 2 CPUs
Jan 12 15:59:35 GAMERA kernel: [    0.000000] net_namespace: 120 bytes
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Time: 20:58:50  Date: 01/12/09
Jan 12 15:59:35 GAMERA kernel: [    0.000000] NET: Registered protocol family 16
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Using configuration type 1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ACPI: Interpreter disabled.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 12 15:59:35 GAMERA kernel: [    0.000000] pnp: PnP ACPI: disabled
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Probing PCI hardware
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Transparent bridge - 0000:00:1e.0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] NET: Registered protocol family 8
Jan 12 15:59:35 GAMERA kernel: [    0.000000] NET: Registered protocol family 20
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI-GART: No AMD northbridge found.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hpet0: 3 64-bit timers, 14318180 Hz
Jan 12 15:59:35 GAMERA kernel: [    0.000000] AppArmor: AppArmor Filesystem Enabled
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Bridge: 0000:00:01.0
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   IO window: 2000-2fff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   MEM window: d0000000-d2ffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   PREFETCH window: e0000000-efffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Bridge: 0000:00:1c.0
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   IO window: 3000-3fff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   MEM window: dc100000-df2fffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   PREFETCH window: dfd00000-dfdfffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Bridge: 0000:00:1c.1
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   IO window: 4000-4fff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   MEM window: d4000000-d7dfffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   PREFETCH window: dfa00000-dfafffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Bridge: 0000:00:1c.2
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   IO window: 5000-5fff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   MEM window: fc000000-fdffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   PREFETCH window: f8000000-f80fffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Bridge: 0000:00:1c.3
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   IO window: 6000-6fff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   MEM window: d8000000-d9ffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   PREFETCH window: df700000-df7fffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Bridge: 0000:00:1c.4
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   IO window: 7000-7fff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   MEM window: cc000000-cdffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   PREFETCH window: df400000-df4fffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Bus 22, cardbus bridge: 0000:15:00.0
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   IO window: 00008000-000080ff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   IO window: 00008400-000084ff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   PREFETCH window: f4000000-f7ffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   MEM window: c4000000-c7ffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Bridge: 0000:00:1e.0
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   IO window: 8000-bfff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   MEM window: f8100000-fbffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   PREFETCH window: f4000000-f7ffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] NET: Registered protocol family 2
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Time: hpet clocksource has been installed.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] TCP: Hash tables configured (established 524288 bind 65536)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] TCP reno registered
Jan 12 15:59:35 GAMERA kernel: [    0.000000] checking if image is initramfs... it is
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Freeing initrd memory: 7562k freed
Jan 12 15:59:35 GAMERA kernel: [    0.000000] audit: initializing netlink socket (disabled)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] audit(1231793930.176:1): initialized
Jan 12 15:59:35 GAMERA kernel: [    0.000000] VFS: Disk quotas dquot_6.5.1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] io scheduler noop registered
Jan 12 15:59:35 GAMERA kernel: [    0.000000] io scheduler anticipatory registered
Jan 12 15:59:35 GAMERA kernel: [    0.000000] io scheduler deadline registered
Jan 12 15:59:35 GAMERA kernel: [    0.000000] io scheduler cfq registered (default)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] 0000:00:1a.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Jan 12 15:59:35 GAMERA kernel: [    0.000000] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Jan 12 15:59:35 GAMERA kernel: [    0.000000] assign_interrupt_mode Found MSI capability
Jan 12 15:59:35 GAMERA last message repeated 5 times
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Real Time Clock Driver v1.12ac
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Linux agpgart interface v0.102
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jan 12 15:59:35 GAMERA kernel: [    0.000000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jan 12 15:59:35 GAMERA kernel: [    0.000000] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] PNP: No PS/2 controller found. Probing ports directly.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 12 15:59:35 GAMERA kernel: [    0.000000] mice: PS/2 mouse device common for all mice
Jan 12 15:59:35 GAMERA kernel: [    0.000000] cpuidle: using governor ladder
Jan 12 15:59:35 GAMERA kernel: [    0.000000] cpuidle: using governor menu
Jan 12 15:59:35 GAMERA kernel: [    0.000000] NET: Registered protocol family 1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] registered taskstats version 1
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   Magic number: 9:434:1003
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   hash matches device input0
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   hash matches device ttye2
Jan 12 15:59:35 GAMERA kernel: [    0.000000]   hash matches device vcs
Jan 12 15:59:35 GAMERA kernel: [    0.000000] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 12 15:59:35 GAMERA kernel: [    0.000000] EDD information not available.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Freeing unused kernel memory: 320k freed
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Write protecting the kernel read-only data: 1036k
Jan 12 15:59:35 GAMERA kernel: [    0.000000] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] fuse init (API version 7.9)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] thermal: Unknown symbol acpi_processor_set_thermal_limit
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usbcore: registered new interface driver usbfs
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usbcore: registered new interface driver hub
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usbcore: registered new device driver usb
Jan 12 15:59:35 GAMERA kernel: [    0.000000] USB Universal Host Controller Interface driver v3.0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1a.0: irq 11, io base 0x00001860
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usb usb1: configuration #1 chosen from 1 choice
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 1-0:1.0: USB hub found
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 1-0:1.0: 2 ports detected
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Copyright (c) 1999-2006 Intel Corporation.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] SCSI subsystem initialized
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1a.1: irq 11, io base 0x00001880
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usb usb2: configuration #1 chosen from 1 choice
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 2-0:1.0: USB hub found
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 2-0:1.0: 2 ports detected
Jan 12 15:59:35 GAMERA kernel: [    0.000000] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1e:37:88:ac:fa
Jan 12 15:59:35 GAMERA kernel: [    0.000000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ehci_hcd 0000:00:1a.7: irq 11, io mem 0xfe226400
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usb 1-2: new full speed USB device using uhci_hcd and address 2
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usb usb3: configuration #1 chosen from 1 choice
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 3-0:1.0: USB hub found
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 3-0:1.0: 4 ports detected
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018a0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usb usb4: configuration #1 chosen from 1 choice
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 4-0:1.0: USB hub found
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 4-0:1.0: 2 ports detected
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x000018c0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usb usb5: configuration #1 chosen from 1 choice
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 5-0:1.0: USB hub found
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 5-0:1.0: 2 ports detected
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
Jan 12 15:59:35 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x000018e0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usb usb6: configuration #1 chosen from 1 choice
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 6-0:1.0: USB hub found
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 6-0:1.0: 2 ports detected
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ehci_hcd 0000:00:1d.7: debug port 1
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xfe226800
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usb usb7: configuration #1 chosen from 1 choice
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 7-0:1.0: USB hub found
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hub 7-0:1.0: 6 ports detected
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Jan 12 15:59:35 GAMERA kernel: [    0.000000] scsi0 : ata_piix
Jan 12 15:59:35 GAMERA kernel: [    0.000000] scsi1 : ata_piix
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1c30 irq 14
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1c38 irq 15
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ata1.00: HPA unlocked: 390719855 -> 390721968, native 390721968
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ata1.00: ATA-8: Hitachi HTS722020K9SA00, DC4OC76A, max UDMA/133
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ata1.00: configured for UDMA/133
Jan 12 15:59:35 GAMERA kernel: [    0.000000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72202 DC4O PQ: 0 ANSI: 5
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Driver 'sd' needs updating - please use bus_type methods
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sd 0:0:0:0: [sda] Write Protect is off
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sd 0:0:0:0: [sda] Write Protect is off
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  sda:<6>usb 1-2: new full speed USB device using uhci_hcd and address 3
Jan 12 15:59:35 GAMERA kernel: [    0.000000]  sda1 sda2 sda3
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] usb 1-2: configuration #1 chosen from 1 choice
Jan 12 15:59:35 GAMERA kernel: [    0.000000] kjournald starting.  Commit interval 5 seconds
Jan 12 15:59:35 GAMERA kernel: [    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 12 15:59:35 GAMERA kernel: [    0.000000] iTCO_vendor_support: vendor-support=0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k2
Jan 12 15:59:35 GAMERA kernel: [    0.000000] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 12 15:59:35 GAMERA kernel: [    0.000000] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
Jan 12 15:59:35 GAMERA kernel: [    0.000000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Non-volatile memory driver v1.2
Jan 12 15:59:35 GAMERA kernel: [    0.000000] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sdhci: Secure Digital Host Controller Interface driver
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sdhci: Copyright(c) Pierre Ossman
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Yenta: ISA IRQ mask 0x02b8, PCI irq 10
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Socket status: 30000006
Jan 12 15:59:35 GAMERA kernel: [    0.000000] pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 21)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] mmc0: SDHCI at 0xf8101800 irq 11 DMA
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ricoh-mmc: Ricoh MMC Controller disabling driver
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ricoh-mmc: Copyright(c) Philip Langdale
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ricoh-mmc: Controller is now disabled.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] nvidia: module license 'NVIDIA' taints kernel.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
Jan 12 15:59:35 GAMERA kernel: [    0.000000] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 2.3.5kds
Jan 12 15:59:35 GAMERA kernel: [    0.000000] iwlagn: Copyright(c) 2003-2008 Intel Corporation
Jan 12 15:59:35 GAMERA kernel: [    0.000000] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
Jan 12 15:59:35 GAMERA kernel: [    0.000000] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] serio: Synaptics pass-through port at isa0060/serio1/input0
Jan 12 15:59:35 GAMERA kernel: [    0.000000] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input3
Jan 12 15:59:35 GAMERA kernel: [    0.000000] input: 4965AGN as /devices/pci0000:00/0000:00:1c.1/0000:03:00.0/input/input4
Jan 12 15:59:35 GAMERA kernel: [    0.000000] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
Jan 12 15:59:35 GAMERA kernel: [    0.000000] lp: driver loaded but no devices found
Jan 12 15:59:35 GAMERA kernel: [    0.000000] thinkpad_ec: thinkpad_ec 0.36 loaded.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] tp_smapi 0.36 loading...
Jan 12 15:59:35 GAMERA kernel: [    0.000000] tp_smapi successfully loaded (smapi_port=0xb2).
Jan 12 15:59:35 GAMERA kernel: [    0.000000] Adding 8000360k swap on /dev/sda2.  Priority:-1 extents:1 across:8000360k
Jan 12 15:59:35 GAMERA kernel: [    0.000000] EXT3 FS on sda1, internal journal
Jan 12 15:59:35 GAMERA kernel: [    0.000000] kjournald starting.  Commit interval 5 seconds
Jan 12 15:59:35 GAMERA kernel: [    0.000000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Jan 12 15:59:35 GAMERA kernel: [    0.000000] EXT3 FS on sda3, internal journal
Jan 12 15:59:35 GAMERA kernel: [    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 12 15:59:35 GAMERA kernel: [    0.000000] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 12 15:59:35 GAMERA kernel: [    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
Jan 12 15:59:35 GAMERA kernel: [    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
Jan 12 15:59:35 GAMERA kernel: [    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
Jan 12 15:59:35 GAMERA kernel: [    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
Jan 12 15:59:36 GAMERA kernel: [    0.000000] ppdev: user-space parallel port driver
Jan 12 15:59:36 GAMERA kernel: [    0.000000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Jan 12 15:59:37 GAMERA kernel: [    0.000000] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input5
Jan 12 15:59:37 GAMERA kernel: [    0.000000] audit(1231793977.205:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4987 profile="/usr/sbin/cupsd" namespace="default"
Jan 12 15:59:37 GAMERA kernel: [    0.000000] audit(1231793977.214:3): type=1503 operation="inode_permission" requested_mask="w::" denied_mask="w::" name="/etc/krb5.conf" pid=4987 profile="/usr/sbin/cupsd" namespace="default"
Jan 12 15:59:39 GAMERA kernel: [    0.000000] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input6
Jan 12 15:59:39 GAMERA kernel: [    0.000000] tun: Universal TUN/TAP device driver, 1.6
Jan 12 15:59:39 GAMERA kernel: [    0.000000] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan 12 15:59:41 GAMERA kernel: [    0.000000] VBoxDrv: dbg - g_abExecMemory=ffffffff88cc7640
Jan 12 15:59:41 GAMERA kernel: [    0.000000] vboxdrv: fAsync=1 offMin=0x64b47 offMax=0x64b47
Jan 12 15:59:41 GAMERA kernel: [    0.000000] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Jan 12 15:59:42 GAMERA kernel: [    0.000000] NET: Registered protocol family 10
Jan 12 15:59:42 GAMERA kernel: [    0.000000] lo: Disabled Privacy Extensions
Jan 12 15:59:42 GAMERA dhcdbd: Started up.
Jan 12 15:59:43 GAMERA kernel: [    0.000000] iwlagn: Radio disabled by HW RF Kill switch
Jan 12 15:59:43 GAMERA kernel: [    0.000000] Bluetooth: Core ver 2.11
Jan 12 15:59:43 GAMERA kernel: [    0.000000] NET: Registered protocol family 31
Jan 12 15:59:43 GAMERA kernel: [    0.000000] Bluetooth: HCI device and connection manager initialized
Jan 12 15:59:43 GAMERA kernel: [    0.000000] Bluetooth: HCI socket layer initialized
Jan 12 15:59:43 GAMERA kernel: [    0.000000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 12 15:59:43 GAMERA kernel: [    0.000000] Bluetooth: L2CAP ver 2.9
Jan 12 15:59:43 GAMERA kernel: [    0.000000] Bluetooth: L2CAP socket layer initialized
Jan 12 15:59:43 GAMERA kernel: [    0.000000] Bluetooth: RFCOMM socket layer initialized
Jan 12 15:59:43 GAMERA kernel: [    0.000000] Bluetooth: RFCOMM TTY layer initialized
Jan 12 15:59:43 GAMERA kernel: [    0.000000] Bluetooth: RFCOMM ver 1.8
Jan 12 15:59:43 GAMERA kernel: [    0.000000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 12 15:59:43 GAMERA kernel: [    0.000000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
Jan 12 15:59:43 GAMERA kernel: [    0.000000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
Jan 12 15:59:43 GAMERA kernel: [    0.000000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan 12 15:59:45 GAMERA dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jan 12 15:59:47 GAMERA kernel: [    0.000000] NET: Registered protocol family 17
Jan 12 15:59:49 GAMERA kernel: [    0.000000] NVRM: RmInitAdapter failed! (0x12:0x2b:1598)
Jan 12 15:59:49 GAMERA kernel: [    0.000000] NVRM: rm_init_adapter(0) failed
Jan 12 15:59:58 GAMERA kernel: [    0.000000] NVRM: RmInitAdapter failed! (0x12:0x2b:1598)
Jan 12 15:59:58 GAMERA kernel: [    0.000000] NVRM: rm_init_adapter(0) failed
Jan 12 15:59:59 GAMERA dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jan 12 15:59:59 GAMERA dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jan 12 15:59:59 GAMERA dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jan 12 16:00:07 GAMERA kernel: [    0.000000] NVRM: RmInitAdapter failed! (0x12:0x2b:1598)
Jan 12 16:00:07 GAMERA kernel: [    0.000000] NVRM: rm_init_adapter(0) failed
Jan 12 16:00:12 GAMERA kernel: [    0.000000] mtrr: type mismatch for d1c00000,200000 old: write-back new: write-combining
Jan 12 16:00:12 GAMERA kernel: [    0.000000] mtrr: type mismatch for d1800000,400000 old: write-back new: write-combining
Jan 12 16:00:12 GAMERA kernel: [    0.000000] mtrr: type mismatch for d1000000,800000 old: write-back new: write-combining
Jan 12 16:02:29 GAMERA kernel: [    0.000000] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input7
Jan 12 16:04:01 GAMERA kernel: [    0.000000] NVRM: RmInitAdapter failed! (0x12:0x2b:1598)
Jan 12 16:04:01 GAMERA kernel: [    0.000000] NVRM: rm_init_adapter(0) failed
Jan 12 16:04:26 GAMERA kernel: [    0.000000] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input8
Jan 12 16:04:33 GAMERA kernel: [    0.000000] uhci_hcd 0000:00:1a.0: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
Jan 12 16:04:34 GAMERA kernel: [    0.000000] login[6525]: segfault at 417ed2f0 rip 7fb651ac7d2f rsp 417292e0 error 6
Jan 12 16:04:37 GAMERA kernel: [    0.000000] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input9
Jan 12 16:04:47 GAMERA kernel: [    0.000000] login[6553]: segfault at 414482f0 rip 7f44f4940d2f rsp 413842e0 error 6
Jan 12 16:04:51 GAMERA kernel: [    0.000000] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input10
Jan 12 16:05:00 GAMERA kernel: [    0.000000] login[6584]: segfault at 416ef2f0 rip 7f426d550d2f rsp 4162b2e0 error 6
Jan 12 16:05:06 GAMERA kernel: [    0.000000] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input11
Jan 12 16:05:15 GAMERA kernel: [    0.000000] login[6616]: segfault at 411252f0 rip 7f6269dd7d2f rsp 410612e0 error 6
Jan 12 16:05:25 GAMERA kernel: [    0.000000] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jan 12 16:05:26 GAMERA exiting on signal 15
```

I booted back into the 2.6.24-22-generic kernel.

---

### Post by albinootje on 2009-01-12
> **EateryOfPiza said:**
> I just tried booting with acpi=off.

Can you please file a bug-report at [http://launchpad.net](http://launchpad.net) ?

---

### Post by albinootje on 2009-01-12
See also here, if you haven't already  :
[http://fav.or.it/post/800662/issues-with-ubuntu-810-on-lenovo-t61p-laptop](http://fav.or.it/post/800662/issues-with-ubuntu-810-on-lenovo-t61p-laptop)
"System lock-ups with Intel 4965 wireless"

[http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_T61p](http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_T61p)

---

### Post by EateryOfPiza on 2009-01-12
> **albinootje said:**
> See also here, if you haven't already  :
[http://fav.or.it/post/800662/issues-with-ubuntu-810-on-lenovo-t61p-laptop](http://fav.or.it/post/800662/issues-with-ubuntu-810-on-lenovo-t61p-laptop)
"System lock-ups with Intel 4965 wireless"

[http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_T61p](http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_T61p)

Heh, the Thinkwiki page was what I used to install, and the 4965 issue seems to occur on the 2.6.27 kernel and intrepid, but in any case, I have the hardy backports installed for some reason too.

> **albinootje said:**
> Can you please file a bug-report at [http://launchpad.net](http://launchpad.net) ?

Should I file a bug for the acpi=off crash or for my original kernel panic issue?

---

### Post by albinootje on 2009-01-12
> **EateryOfPiza said:**
>  Should I file a bug for the acpi=off crash or for my original kernel panic issue?

You can provide the information from both cases I think.

Make sure to also post the output of things like :
```

dmesg
lspci -vv
lsusb
sudo lshw -C network
lsmod

```
And of course Lenovo T61p.

---

