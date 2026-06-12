---
title: "Pause at boot (bootchart inside)"
date: 2008-12-03
forum: General Help
---

### Post by l1nuxb0x on 2008-12-03
I've had this issue for some time, during boot there is a pause for about 15 seconds where nothing seems to happen. Some information about scsi is up on the screen, it seems like it's trying to read a disk, but gives up after a while.

[IMG]http://i99.photobucket.com/albums/l303/l1nuxb0x/intrepid-20081203-2.png[/IMG]

Everything else boots up quick, but it seems like I could have a 25 second boot if this scsi hangup wasn't happening. My boot time sits at 39 seconds right now.

Everything looks good, except those scsi_eh processes. The pause starts at ~5 seconds and last to ~20 seconds, at which point the system continues to show boot messages again.

Here's my dmesg
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7fef0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37821000 - 37fef9bf
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F7F60, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: DSDT 7FEF3180, 5271 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FEF0000, 0040
[    0.000000] ACPI: HPET 7FEF8540, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: WDRT 7FEF85C0, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: MCFG 7FEF8680, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC 7FEF8440, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037821000 - 0037fef9bf]          RAMDISK ==> [0037821000 - 0037fef9bf]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f3f90] 000f3f90
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fef0
[    0.000000] On node 0 totalpages: 523919
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292050 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:50100000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519313
[    0.000000] Kernel command line: root=UUID=6e3d54dd-f38a-4e95-babe-df669a951c0f ro nosplash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2399.949 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2062556k/2096064k available (2572k kernel code, 32344k reserved, 1160k data, 424k init, 1178560k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4799.89 BogoMIPS (lpj=9599796)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017633] ACPI: Core revision 20080609
[    0.018698] ACPI: Checking initramfs for custom DSDT
[    0.296271] ENABLING IO-APIC IRQs
[    0.296550] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.337556] CPU0: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[    0.340021] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4799.99 BogoMIPS (lpj=9599980)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.424558] CPU1: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[    0.425362] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.428043] Brought up 2 CPUs
[    0.428133] Total of 2 processors activated (9599.88 BogoMIPS).
[    0.428249] CPU0 attaching sched-domain:
[    0.428251]  domain 0: span 0-1 level MC
[    0.428253]   groups: 0 1
[    0.428258] CPU1 attaching sched-domain:
[    0.428260]  domain 0: span 0-1 level MC
[    0.428262]   groups: 1 0
[    0.428322] net_namespace: 840 bytes
[    0.428322] Booting paravirtualized kernel on bare hardware
[    0.428432] Time: 15:46:17  Date: 12/03/08
[    0.428547] NET: Registered protocol family 16
[    0.428658] EISA bus registered
[    0.428658] ACPI: bus type pci registered
[    0.428658] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.428658] PCI: MCFG area at e0000000 reserved in E820
[    0.428658] PCI: Using MMCONFIG for extended config space
[    0.428658] PCI: Using configuration type 1 for base access
[    0.433064] ACPI: EC: Look up EC in DSDT
[    0.440631] ACPI: Interpreter enabled
[    0.440725] ACPI: (supports S0 S1 S3 S4 S5)
[    0.441052] ACPI: Using IOAPIC for interrupt routing
[    0.448192] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.448828] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448935] pci 0000:00:03.0: PME# disabled
[    0.449185] PCI: 0000:00:0a.0 reg 10 io port: [fc00, fc7f]
[    0.449236] PCI: 0000:00:0a.1 reg 10 io port: [f800, f83f]
[    0.449252] PCI: 0000:00:0a.1 reg 20 io port: [f400, f43f]
[    0.449257] PCI: 0000:00:0a.1 reg 24 io port: [f000, f03f]
[    0.449276] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.449382] pci 0000:00:0a.1: PME# disabled
[    0.452055] PCI: 0000:00:0b.0 reg 10 32bit mmio: [cffff000, cfffffff]
[    0.452084] pci 0000:00:0b.0: supports D1
[    0.452085] pci 0000:00:0b.0: supports D2
[    0.452087] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.452194] pci 0000:00:0b.0: PME# disabled
[    0.452310] PCI: 0000:00:0b.1 reg 10 32bit mmio: [cfffe000, cfffe0ff]
[    0.452340] pci 0000:00:0b.1: supports D1
[    0.452342] pci 0000:00:0b.1: supports D2
[    0.452343] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.452450] pci 0000:00:0b.1: PME# disabled
[    0.452579] PCI: 0000:00:0d.0 reg 20 io port: [ec00, ec0f]
[    0.452620] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.452624] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.452629] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.452634] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.452638] PCI: 0000:00:0e.0 reg 20 io port: [d800, d80f]
[    0.452643] PCI: 0000:00:0e.0 reg 24 32bit mmio: [cfffd000, cfffdfff]
[    0.452684] PCI: 0000:00:0e.1 reg 10 io port: [9e0, 9e7]
[    0.452688] PCI: 0000:00:0e.1 reg 14 io port: [be0, be3]
[    0.452693] PCI: 0000:00:0e.1 reg 18 io port: [960, 967]
[    0.452698] PCI: 0000:00:0e.1 reg 1c io port: [b60, b63]
[    0.452702] PCI: 0000:00:0e.1 reg 20 io port: [c400, c40f]
[    0.452707] PCI: 0000:00:0e.1 reg 24 32bit mmio: [cfffc000, cfffcfff]
[    0.452748] PCI: 0000:00:0e.2 reg 10 io port: [c000, c007]
[    0.452752] PCI: 0000:00:0e.2 reg 14 io port: [bc00, bc03]
[    0.452757] PCI: 0000:00:0e.2 reg 18 io port: [b800, b807]
[    0.452761] PCI: 0000:00:0e.2 reg 1c io port: [b400, b403]
[    0.452766] PCI: 0000:00:0e.2 reg 20 io port: [b000, b00f]
[    0.452771] PCI: 0000:00:0e.2 reg 24 32bit mmio: [cfffb000, cfffbfff]
[    0.452865] PCI: 0000:00:11.0 reg 10 32bit mmio: [cfffa000, cfffafff]
[    0.452870] PCI: 0000:00:11.0 reg 14 io port: [ac00, ac07]
[    0.452874] PCI: 0000:00:11.0 reg 18 32bit mmio: [cfff9000, cfff90ff]
[    0.452879] PCI: 0000:00:11.0 reg 1c 32bit mmio: [cfff8000, cfff800f]
[    0.452904] pci 0000:00:11.0: supports D1
[    0.452906] pci 0000:00:11.0: supports D2
[    0.452907] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.453015] pci 0000:00:11.0: PME# disabled
[    0.453148] PCI: 0000:01:00.0 reg 10 32bit mmio: [cc000000, ccffffff]
[    0.453153] PCI: 0000:01:00.0 reg 14 32bit mmio: [b0000000, bfffffff]
[    0.453164] PCI: 0000:01:00.0 reg 1c 64bit mmio: [ca000000, cbffffff]
[    0.453169] PCI: 0000:01:00.0 reg 24 io port: [8c00, 8c7f]
[    0.453174] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.453223] PCI: bridge 0000:00:03.0 io port: [8000, 8fff]
[    0.453226] PCI: bridge 0000:00:03.0 32bit mmio: [ca000000, cdffffff]
[    0.453230] PCI: bridge 0000:00:03.0 64bit mmio pref: [b0000000, bfffffff]
[    0.453266] PCI: 0000:02:07.0 reg 10 32bit mmio: [cfeff000, cfeff7ff]
[    0.453272] PCI: 0000:02:07.0 reg 14 32bit mmio: [cfef8000, cfefbfff]
[    0.453305] pci 0000:02:07.0: supports D1
[    0.453307] pci 0000:02:07.0: supports D2
[    0.453308] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot
[    0.453413] pci 0000:02:07.0: PME# disabled
[    0.453530] PCI: 0000:02:09.0 reg 10 io port: [9c00, 9c3f]
[    0.453565] pci 0000:02:09.0: supports D1
[    0.453566] pci 0000:02:09.0: supports D2
[    0.453601] PCI: 0000:02:0a.0 reg 10 io port: [9800, 98ff]
[    0.453611] PCI: 0000:02:0a.0 reg 14 64bit mmio: [cfefc000, cfefdfff]
[    0.453617] PCI: 0000:02:0a.0 reg 1c io port: [9400, 94ff]
[    0.453630] PCI: 0000:02:0a.0 reg 30 32bit mmio: [0, 7ffff]
[    0.453669] pci 0000:00:0f.0: transparent bridge
[    0.453766] PCI: bridge 0000:00:0f.0 io port: [9000, 9fff]
[    0.453769] PCI: bridge 0000:00:0f.0 32bit mmio: [cfe00000, cfefffff]
[    0.453779] bus 00 -> node 0
[    0.453785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.454342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.518152] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.520197] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[    0.520863] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[    0.521528] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[    0.522192] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 10 *11 14 15)
[    0.522855] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.523643] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.524437] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.525228] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.525891] ACPI: PCI Interrupt Link [LMC1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.526680] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.527346] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.528150] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.528940] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.529603] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.532001] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 *10 11 14 15)
[    0.532632] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[    0.533299] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[    0.534002] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.534522] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.534991] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.535460] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.535929] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0
[    0.536438] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[    0.536956] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[    0.537475] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.537993] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[    0.538600] ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0, disabled.
[    0.539255] ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0
[    0.539861] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.540532] ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.
[    0.541187] ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.
[    0.541843] ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.
[    0.542498] ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0
[    0.543104] ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.
[    0.543759] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0
[    0.544347] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0
[    0.544953] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
[    0.545424] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.545424] pnp: PnP ACPI init
[    0.545424] ACPI: bus type pnp registered
[    0.549563] pnp: PnP ACPI: found 13 devices
[    0.549563] ACPI: ACPI bus type pnp unregistered
[    0.549563] PnPBIOS: Disabled by ACPI PNP
[    0.549563] PCI: Using ACPI for IRQ routing
[    0.556043] NET: Registered protocol family 8
[    0.556142] NET: Registered protocol family 20
[    0.556258] NetLabel: Initializing
[    0.556258] NetLabel:  domain hash size = 128
[    0.556258] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.556358] NetLabel:  unlabeled traffic allowed by default
[    0.556464] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.556741] hpet0: 3 32-bit timers, 25000000 Hz
[    0.558593] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.558698]    actual entries 65620
[    0.558857] AppArmor: AppArmor Filesystem Enabled
[    0.558978] ACPI: RTC can wake from S4
[    0.560039] Switched to high resolution mode on CPU 0
[    0.561555] Switched to high resolution mode on CPU 1
[    0.563978] system 00:00: ioport range 0x1000-0x107f has been reserved
[    0.564093] system 00:00: ioport range 0x1080-0x10ff has been reserved
[    0.564211] system 00:00: ioport range 0x1400-0x147f has been reserved
[    0.564316] system 00:00: ioport range 0x1480-0x14ff has been reserved
[    0.564421] system 00:00: ioport range 0x1800-0x187f has been reserved
[    0.564526] system 00:00: ioport range 0x1880-0x18ff has been reserved
[    0.564637] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.564742] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.564846] system 00:02: ioport range 0x880-0x88f has been reserved
[    0.564959] system 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.565102] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[    0.565208] system 00:0c: iomem range 0xdf800-0xdffff has been reserved
[    0.565314] system 00:0c: iomem range 0xf0000-0xfbfff could not be reserved
[    0.565421] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.565528] system 00:0c: iomem range 0x7fef0000-0x7fefffff could not be reserved
[    0.565670] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.565810] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.565916] system 00:0c: iomem range 0x100000-0x7feeffff could not be reserved
[    0.566057] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.566198] system 00:0c: iomem range 0xd0000000-0xdfffffff could not be reserved
[    0.566339] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.566480] system 00:0c: iomem range 0xfeff0000-0xfeff0000 could not be reserved
[    0.601682] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.601785] pci 0000:00:03.0:   IO window: 0x8000-0x8fff
[    0.601886] pci 0000:00:03.0:   MEM window: 0xca000000-0xcdffffff
[    0.601990] pci 0000:00:03.0:   PREFETCH window: 0x000000b0000000-0x000000bfffffff
[    0.602134] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:02
[    0.602237] pci 0000:00:0f.0:   IO window: 0x9000-0x9fff
[    0.602338] pci 0000:00:0f.0:   MEM window: 0xcfe00000-0xcfefffff
[    0.602442] pci 0000:00:0f.0:   PREFETCH window: 0x00000080000000-0x000000800fffff
[    0.602591] pci 0000:00:03.0: setting latency timer to 64
[    0.602596] pci 0000:00:0f.0: setting latency timer to 64
[    0.602599] bus: 00 index 0 io port: [0, ffff]
[    0.602694] bus: 00 index 1 mmio: [0, ffffffff]
[    0.602791] bus: 01 index 0 io port: [8000, 8fff]
[    0.602888] bus: 01 index 1 mmio: [ca000000, cdffffff]
[    0.602986] bus: 01 index 2 mmio: [b0000000, bfffffff]
[    0.603085] bus: 01 index 3 mmio: [0, 0]
[    0.603178] bus: 02 index 0 io port: [9000, 9fff]
[    0.603275] bus: 02 index 1 mmio: [cfe00000, cfefffff]
[    0.603374] bus: 02 index 2 mmio: [80000000, 800fffff]
[    0.603472] bus: 02 index 3 io port: [0, ffff]
[    0.603567] bus: 02 index 4 mmio: [0, ffffffff]
[    0.603668] NET: Registered protocol family 2
[    0.616083] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.616399] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.616773] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.617012] TCP: Hash tables configured (established 131072 bind 65536)
[    0.617118] TCP reno registered
[    0.624118] NET: Registered protocol family 1
[    0.624330] checking if image is initramfs... it is
[    1.191068] Freeing initrd memory: 7994k freed
[    1.192177] audit: initializing netlink socket (disabled)
[    1.192296] type=2000 audit(1228319177.188:1): initialized
[    1.197309] highmem bounce pool size: 64 pages
[    1.197409] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.199818] VFS: Disk quotas dquot_6.5.1
[    1.199985] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.200184] msgmni has been set to 1743
[    1.200389] io scheduler noop registered
[    1.200483] io scheduler anticipatory registered
[    1.200584] io scheduler deadline registered
[    1.200687] io scheduler cfq registered (default)
[    1.200938] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0e.1: Disabling HT MSI mapping<6>pci 0000:00:0e.2: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:11.0: Disabling HT MSI mapping<7>pci 0000:01:00.0: Boot video device
[    1.217312] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.217347] pcieport-driver 0000:00:03.0: found MSI capability
[    1.217478] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.217521] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.217867] isapnp: Scanning for PnP cards...
[    1.570688] isapnp: No Plug & Play device found
[    1.600199] hpet_resources: 0xfeff0000 is busy
[    1.600271] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.600496] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.601209] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.602763] brd: module loaded
[    1.602908] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.603147] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.603251] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.603815] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.608753] mice: PS/2 mouse device common for all mice
[    1.608964] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.609092] rtc0: alarms up to one year, y3k, hpet irqs
[    1.609318] EISA: Probing bus 0 at eisa.0
[    1.609416] Cannot allocate resource for EISA slot 1
[    1.609529] Cannot allocate resource for EISA slot 8
[    1.609626] EISA: Detected 0 cards.
[    1.609719] cpuidle: using governor ladder
[    1.609814] cpuidle: using governor menu
[    1.610333] TCP cubic registered
[    1.610442] Using IPI No-Shortcut mode
[    1.610690] registered taskstats version 1
[    1.610912]   Magic number: 4:89:790
[    1.611071] rtc_cmos 00:05: setting system clock to 2008-12-03 15:46:18 UTC (1228319178)
[    1.611215] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.611317] EDD information not available.
[    1.611591] Freeing unused kernel memory: 424k freed
[    1.611718] Write protecting the kernel text: 2576k
[    1.611835] Write protecting the kernel read-only data: 936k
[    1.629329] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.693412] fuse init (API version 7.9)
[    1.710729] processor ACPI0007:00: registered as cooling_device0
[    1.710834] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.711087] processor ACPI0007:01: registered as cooling_device1
[    2.067760] usbcore: registered new interface driver usbfs
[    2.067879] usbcore: registered new interface driver hub
[    2.068041] usbcore: registered new device driver usb
[    2.069807] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.070160] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[    2.070266] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 23 (level, low) -> IRQ 23
[    2.070420] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.070423] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.070623] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.070778] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xcffff000
[    2.092053] No dock devices found.
[    2.105700] SCSI subsystem initialized
[    2.127873] usb usb1: configuration #1 chosen from 1 choice
[    2.128009] hub 1-0:1.0: USB hub found
[    2.129719] hub 1-0:1.0: 10 ports detected
[    2.130448] libata version 3.00 loaded.
[    2.337443] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 22
[    2.337553] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 22 (level, low) -> IRQ 22
[    2.337707] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.337710] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.337833] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    2.337991] ehci_hcd 0000:00:0b.1: debug port 1
[    2.338090] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    2.338101] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xcfffe000
[    2.512039] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    2.524033] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.524310] usb usb2: configuration #1 chosen from 1 choice
[    2.524436] hub 2-0:1.0: USB hub found
[    2.524533] hub 2-0:1.0: 10 ports detected
[    2.580036] hub 1-0:1.0: unable to enumerate USB device on port 1
[    2.732275] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    2.732313] sata_nv 0000:00:0e.0: version 3.5
[    2.732630] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
[    2.732736] sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21
[    2.732880] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    2.733153] sata_nv 0000:00:0e.0: setting latency timer to 64
[    2.733403] scsi0 : sata_nv
[    2.733720] scsi1 : sata_nv
[    2.733952] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[    2.734060] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[    2.948054] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    3.062437] ata1: SATA link down (SStatus 0 SControl 300)
[    3.080826] usb 2-1: configuration #1 chosen from 1 choice
[    3.081148] hub 2-1:1.0: USB hub found
[    3.081360] hub 2-1:1.0: 4 ports detected
[    3.390457] ata2: SATA link down (SStatus 0 SControl 300)
[    3.390904] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
[    3.391009] sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20
[    3.391153] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    3.391276] sata_nv 0000:00:0e.1: setting latency timer to 64
[    3.391359] scsi2 : sata_nv
[    3.391713] scsi3 : sata_nv
[    3.392142] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[    3.392250] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[    3.488369] usb 2-1.1: new low speed USB device using ehci_hcd and address 4
[    3.605819] usb 2-1.1: configuration #1 chosen from 1 choice
[    3.692372] usb 2-1.4: new full speed USB device using ehci_hcd and address 5
[    3.805593] usb 2-1.4: configuration #1 chosen from 1 choice
[    3.868058] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.876171] ata3.00: ATA-7: WDC WD740ADFD-60NLR1, 20.07P20, max UDMA/133
[    3.876290] ata3.00: 145226112 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.892180] ata3.00: configured for UDMA/133
[    4.108032] usb 1-4: new full speed USB device using ohci_hcd and address 3
[    4.222436] ata4: SATA link down (SStatus 0 SControl 300)
[    4.222629] scsi 2:0:0:0: Direct-Access     ATA      WDC WD740ADFD-60 20.0 PQ: 0 ANSI: 5
[    4.223170] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 23
[    4.223274] sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 23 (level, low) -> IRQ 23
[    4.223418] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    4.223542] sata_nv 0000:00:0e.2: setting latency timer to 64
[    4.223630] scsi4 : sata_nv
[    4.223972] scsi5 : sata_nv
[    4.224204] ata5: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 23
[    4.224313] ata6: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 23
[    4.324158] usb 1-4: configuration #1 chosen from 1 choice
[    4.554437] ata5: SATA link down (SStatus 0 SControl 300)
[    4.882457] ata6: SATA link down (SStatus 0 SControl 300)
[    4.882631] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.883096] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 22
[    4.883200] forcedeth 0000:00:11.0: PCI INT A -> Link[AMAC] -> GSI 22 (level, low) -> IRQ 22
[    4.883348] forcedeth 0000:00:11.0: setting latency timer to 64
[    4.883364] nv_probe: set workaround bit for reversed mac addr
[    4.916858] usbcore: registered new interface driver hiddev
[    4.920340] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:0b.1/usb2/2-1/2-1.1/2-1.1:1.0/input/input2
[    4.924984] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.1-1.1
[    4.928497] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.1/usb2/2-1/2-1.4/2-1.4:1.0/input/input3
[    4.936471] input,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:0b.1-1.4
[    4.940700] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.1/usb2/2-1/2-1.4/2-1.4:1.1/input/input4
[    4.949060] input,hiddev96,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:0b.1-1.4
[    4.949490] usbcore: registered new interface driver usbhid
[    4.949592] usbhid: v2.6:USB HID core driver
[    5.401009] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:00:f7:89
[    5.401156] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[    5.401638] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    5.401745] ohci1394 0000:02:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    5.401892] ohci1394 0000:02:07.0: setting latency timer to 64
[    5.451592] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[cfeff000-cfeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.452547] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    5.452651] aic79xx 0000:02:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    6.724475] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0d4a649500044b03]
[   20.676566] scsi6 : Adaptec AIC79XX PCI-X SCSI HBA DRIVER, Rev 3.0
[   20.676568]         <Adaptec 29320LP Ultra320 SCSI adapter>
[   20.676569]         aic7901A: Ultra320 Wide Channel A, SCSI Id=7, PCI 33 or 66Mhz, 512 SCBs
[   20.683214] pata_amd 0000:00:0d.0: version 0.3.10
[   20.683248] pata_amd 0000:00:0d.0: setting latency timer to 64
[   20.684253] scsi7 : pata_amd
[   20.684529] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[   20.685278] scsi8 : pata_amd
[   20.685978] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[   20.686086] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[   20.856300] ata7.00: ATAPI: HL-DT-ST RW/DVD GCC-4480B, 1.02, max UDMA/33
[   20.856423] ata7.01: ATAPI: BENQ    DVD DD DW1625, BBIA, max UDMA/33
[   20.856537] ata7: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[   20.856541] ata7: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[   20.872245] ata7.00: configured for UDMA/33
[   20.888496] ata7.01: configured for UDMA/33
[   20.888619] ata8: port disabled. ignoring.
[   20.888632] scsi: waiting for bus probes to complete ...
[   21.707431] scsi 6:0:4:0: Direct-Access     COMPAQ   BD018222CA       B016 PQ: 0 ANSI: 2
[   21.707582] scsi target6:0:4: asynchronous
[   21.707680] scsi6:A:4:0: Tagged Queuing enabled.  Depth 32
[   21.707835] scsi target6:0:4: Beginning Domain Validation
[   21.709635] scsi target6:0:4: wide asynchronous
[   21.710886] scsi target6:0:4: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 63)
[   21.711817] scsi target6:0:4: Domain Validation skipping write tests
[   21.711924] scsi target6:0:4: Ending Domain Validation
[   22.484303] scsi 6:0:9:0: Direct-Access     SEAGATE  ST173404LC       0004 PQ: 0 ANSI: 3
[   22.484453] scsi target6:0:9: asynchronous
[   22.484559] scsi6:A:9:0: Tagged Queuing enabled.  Depth 32
[   22.484709] scsi target6:0:9: Beginning Domain Validation
[   22.489285] scsi target6:0:9: wide asynchronous
[   22.493431] scsi target6:0:9: FAST-80 WIDE SCSI 160.0 MB/s DT (12.5 ns, offset 63)
[   22.500861] scsi target6:0:9: Ending Domain Validation
[   24.041811] scsi 6:0:4:0: Attached scsi generic sg1 type 0
[   24.044384] scsi 6:0:9:0: Attached scsi generic sg2 type 0
[   24.044968] scsi 7:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4480B 1.02 PQ: 0 ANSI: 5
[   24.045182] scsi 7:0:0:0: Attached scsi generic sg3 type 5
[   24.047187] scsi 7:0:1:0: CD-ROM            BENQ     DVD DD DW1625    BBIA PQ: 0 ANSI: 5
[   24.047404] scsi 7:0:1:0: Attached scsi generic sg4 type 5
[   24.049769] Driver 'sd' needs updating - please use bus_type methods
[   24.049935] sd 2:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
[   24.050056] sd 2:0:0:0: [sda] Write Protect is off
[   24.050154] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.050179] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.050382] sd 2:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
[   24.050501] sd 2:0:0:0: [sda] Write Protect is off
[   24.050599] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.050624] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.050772]  sda: sda1
[   24.058897] sd 2:0:0:0: [sda] Attached SCSI disk
[   24.077440] Driver 'sr' needs updating - please use bus_type methods
[   24.271613] sd 6:0:4:0: [sdb] 35565080 512-byte hardware sectors (18209 MB)
[   24.274864] sd 6:0:4:0: [sdb] Write Protect is off
[   24.274965] sd 6:0:4:0: [sdb] Mode Sense: af 00 10 08
[   24.276362] sd 6:0:4:0: [sdb] Write cache: enabled, read cache: enabled, supports DPO and FUA
[   24.276959] sd 6:0:4:0: [sdb] 35565080 512-byte hardware sectors (18209 MB)
[   24.280185] sd 6:0:4:0: [sdb] Write Protect is off
[   24.280286] sd 6:0:4:0: [sdb] Mode Sense: af 00 10 08
[   24.281684] sd 6:0:4:0: [sdb] Write cache: enabled, read cache: enabled, supports DPO and FUA
[   24.281833]  sdb: sdb1 sdb2 < sdb5 >
[   24.297680] sd 6:0:4:0: [sdb] Attached SCSI disk
[   24.298842] sd 6:0:9:0: [sdc] 143374738 512-byte hardware sectors (73408 MB)
[   24.300227] sd 6:0:9:0: [sdc] Write Protect is off
[   24.300338] sd 6:0:9:0: [sdc] Mode Sense: 9f 00 10 08
[   24.301646] sd 6:0:9:0: [sdc] Write cache: enabled, read cache: enabled, supports DPO and FUA
[   24.302618] sd 6:0:9:0: [sdc] 143374738 512-byte hardware sectors (73408 MB)
[   24.304002] sd 6:0:9:0: [sdc] Write Protect is off
[   24.304108] sd 6:0:9:0: [sdc] Mode Sense: 9f 00 10 08
[   24.305424] sd 6:0:9:0: [sdc] Write cache: enabled, read cache: enabled, supports DPO and FUA
[   24.305574]  sdc: sdc1
[   24.314543] sd 6:0:9:0: [sdc] Attached SCSI disk
[   24.319090] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   24.319197] Uniform CD-ROM driver Revision: 3.20
[   24.319359] sr 7:0:0:0: Attached scsi CD-ROM sr0
[   24.332948] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   24.333122] sr 7:0:1:0: Attached scsi CD-ROM sr1
[   24.653206] PM: Starting manual resume from disk
[   24.653304] PM: Resume from partition 8:21
[   24.653306] PM: Checking hibernation image.
[   24.657347] PM: Resume from disk failed.
[   24.699673] kjournald starting.  Commit interval 5 seconds
[   24.699791] EXT3-fs: mounted filesystem with ordered data mode.
[   31.084882] udevd version 124 started
[   31.496949] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.519666] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.583660] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   31.604071] ACPI: Power Button (FF) [PWRF]
[   31.604229] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   31.632019] ACPI: Power Button (CM) [PWRB]
[   31.675263] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400
[   31.675381] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000
[   31.760119] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
[   31.800256] Linux agpgart interface v0.103
[   32.237157] nvidia: module license 'NVIDIA' taints kernel.
[   32.517479] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[   32.517617] nvidia 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
[   32.517799] nvidia 0000:01:00.0: setting latency timer to 64
[   32.517917] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   32.532672] Found: SST 49LF040B
[   32.532766] ck804xrom @fff80000: Found 1 x8 devices at 0x0 in 8-bit bank
[   32.648989] using fwh lock/unlock method
[   32.649087] number of JEDEC chips: 1
[   32.649179] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
[   32.760185] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   33.327541] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   33.327656] EMU10K1_Audigy 0000:02:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   33.329953] EMU10K1_Audigy 0000:02:09.0: setting latency timer to 64
[   33.332909] Audigy2 value: Special config.
[   34.111562] lp: driver loaded but no devices found
[   34.246994] Adding 779112k swap on /dev/sdb5.  Priority:-1 extents:1 across:779112k
[   34.563771] EXT3 FS on sdb1, internal journal
[   34.946714] type=1505 audit(1228337211.947:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=6191
[   35.079683] type=1505 audit(1228337212.079:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=6199
[   35.079821] type=1505 audit(1228337212.079:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=6199
[   35.178607] ip_tables: (C) 2000-2006 Netfilter Core Team

This part in particular seems to be where it hangs

> [    6.724475] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0d4a649500044b03]
[   20.676566] scsi6 : Adaptec AIC79XX PCI-X SCSI HBA DRIVER, Rev 3.0
[   20.676568]         <Adaptec 29320LP Ultra320 SCSI adapter>
[   20.676569]         aic7901A: Ultra320 Wide Channel A, SCSI Id=7, PCI 33 or 66Mhz, 512 SCBs

So if I where to guess I'd say it takes 15 seconds to load the scsi card driver

---

### Post by l1nuxb0x on 2008-12-03
I've found some stuff on google about a programmed delay on the adaptec card. 

[http://bugzilla.kernel.org/show_bug.cgi?id=8141](http://bugzilla.kernel.org/show_bug.cgi?id=8141)
[https://bugs.launchpad.net/linux/+bug/79542](https://bugs.launchpad.net/linux/+bug/79542)

this bit on particular interests me

> > CONFIG_AIC79XX_RESET_DELAY_MS
>
> I suspect you have this set to around 15000. You can make the boot
> sequence shorter by reducing this value. I believe Red Hat configures
> it down to the default 5000. 

So now I'm trying to figure out how to change this without having to go through the hassle of rebuilding/recompiling a kernel that is working perfect otherwise.

---

### Post by l1nuxb0x on 2008-12-03
Ok I found my Kconfig file but it's alreayd set to the 5 second delay!

So perhaps this is not my issue

---

### Post by Dittie on 2008-12-03
I actually have this problem as well with 8.10. However, it completely pauses and doesn't continue on until I press a key. Doesn't matter what key it is, just some key. Have to do that usually 3 times before it goes off on its own and finishes booting.

But everything else is working for the most part, so I didn't want to mess with it :P

---

### Post by l1nuxb0x on 2008-12-04
Hey dittie, thanks for the response. I'm not sure what would need a key stroke on boot, do you see anything in "dmesg" that asks you to press a key?

---

### Post by Dittie on 2008-12-04
No, not a thing. It does the this in both ubuntu and kubuntu 8.10. So I figure its a kernel thing, just not quite sure why it would happen. 8.04's kernel booted up quick and without a problem.

---

### Post by l1nuxb0x on 2008-12-04
Yeah that's weird, I didn't think there was anything that would require the user to hit a key while it boots

---

### Post by l1nuxb0x on 2008-12-04
WOW Great success!!!

I looked at the options for the adaptec SCSI card and found an option called reset scsi bus @ IC initialization which I set to disabled and that completely cut out that BS waiting time!!

However I don't know if this is going to cause other problems, for example I haven't tried windows yet but I sure hope it is fixed!!

Check out my new, 23 second bootchart!

[IMG]http://i99.photobucket.com/albums/l303/l1nuxb0x/intrepid-20081204-1.png[/IMG]

---

### Post by l1nuxb0x on 2008-12-05
I booted windows today, not having any troubles, I'm gonna mark this solved

---

### Post by chk9 on 2008-12-27
Glad it works for you.

Two questions:

 Q1:
How do you make those cool charts?

 Q2:
Where did you make your SCSI setting changes?

Have Fun,
Chris.

---

### Post by l1nuxb0x on 2008-12-28
> **chk9 said:**
> Glad it works for you.

Two questions:

 Q1:
How do you make those cool charts?

 Q2:
Where did you make your SCSI setting changes?

Have Fun,
Chris.

hey chk9,

to make the charts, install bootchart through apt-get or the synaptic package manager. I found a bunch of older write ups that talk about downloading a tar.gz and doing the old "make" and "install" deal, I never had any luck with that. Turns out it's as easy as *sudo apt-get install bootchart*

And I have an adaptec scsi controller that goes in a PCI slot and runs my scsi drives, everytime the computer boots it says something like "hit ctrl-A to enter scsi config". From there I believe it was under advanced settings.

Let me know if you have anymore questions.

---

### Post by Zer0Nin3r on 2009-09-03
> **Dittie said:**
> No, not a thing. It does the this in both ubuntu and kubuntu 8.10. So I figure its a kernel thing, just not quite sure why it would happen. 8.04's kernel booted up quick and without a problem.

I would venture to say that I've been experiencing similar problems since 8.10.  Wasn't there before.  Anyway, I have an excruciating 1.5 min wait...

In a first instance I saw this in my log:

```
Aug 30 23:54:17 ubuntu kernel: [   15.892398] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
Aug 30 23:54:17 ubuntu kernel: [   15.892411] resource map sanity check conflict: 0xff000000 0xffffffff 0xfff80000 0xfff80fff pnp 00:0b
Aug 30 23:54:17 ubuntu kernel: [   15.892419] ------------[ cut here ]------------
Aug 30 23:54:17 ubuntu kernel: [   15.892421] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390()
Aug 30 23:54:17 ubuntu kernel: [   15.892423] Modules linked in: ck804xrom(+) mtd chipreg parport_pc(+) parport joydev map_funcs hid_logitech ff_memless usbhid usb_storage ohci1394 ieee1394 forcedeth fbcon tileblit font bitblit softcursor
Aug 30 23:54:17 ubuntu kernel: [   15.892439] Pid: 978, comm: modprobe Not tainted 2.6.28-11-generic #42-Ubuntu
Aug 30 23:54:17 ubuntu kernel: [   15.892441] Call Trace:
Aug 30 23:54:17 ubuntu kernel: [   15.892447]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90
Aug 30 23:54:17 ubuntu kernel: [   15.892451]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Aug 30 23:54:17 ubuntu kernel: [   15.892454]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Aug 30 23:54:17 ubuntu kernel: [   15.892457]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390
Aug 30 23:54:17 ubuntu kernel: [   15.892462]  [<ffffffffa00e22db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
Aug 30 23:54:17 ubuntu kernel: [   15.892465]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
Aug 30 23:54:17 ubuntu kernel: [   15.892469]  [<ffffffffa00e22db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
Aug 30 23:54:17 ubuntu kernel: [   15.892473]  [<ffffffffa00e8041>] init_ck804xrom+0x41/0x59 [ck804xrom]
Aug 30 23:54:17 ubuntu kernel: [   15.892476]  [<ffffffffa00e8000>] ? init_ck804xrom+0x0/0x59 [ck804xrom]
Aug 30 23:54:17 ubuntu kernel: [   15.892480]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
Aug 30 23:54:17 ubuntu kernel: [   15.892483]  [<ffffffff802d0225>] ? __vunmap+0xc5/0x110
Aug 30 23:54:17 ubuntu kernel: [   15.892486]  [<ffffffff802d02c5>] ? vfree+0x25/0x30
Aug 30 23:54:17 ubuntu kernel: [   15.892490]  [<ffffffff8027eee8>] ? load_module+0x11c8/0x11d0
Aug 30 23:54:17 ubuntu kernel: [   15.892494]  [<ffffffff8027ef9d>] sys_init_module+0xad/0x1e0
Aug 30 23:54:17 ubuntu kernel: [   15.892497]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Aug 30 23:54:17 ubuntu kernel: [   15.892569] ---[ end trace b5d5a74c356b6753 ]---
```

In a more recent instance I was able to pull this:

```
Sep  2 23:31:07 192 kernel: [   17.111027] nvidia: module license 'NVIDIA' taints kernel.
Sep  2 23:31:07 192 kernel: [   17.365847] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Sep  2 23:31:07 192 kernel: [   17.365854] nvidia 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
Sep  2 23:31:07 192 kernel: [   17.367328] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.16  Sat Jan 24 19:01:41 PST 2009
Sep  2 23:31:07 192 kernel: [   17.382453] ppdev: user-space parallel port driver
Sep  2 23:31:07 192 kernel: [   17.390693] scsi10 : SBP-2 IEEE-1394
Sep  2 23:31:07 192 kernel: [   17.564991] resource map sanity check conflict: 0xff000000 0xffffffff 0xfff80000 0xfff80fff pnp 00:0b
Sep  2 23:31:07 192 kernel: [   17.564999] ------------[ cut here ]------------
Sep  2 23:31:07 192 kernel: [   17.565001] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390()
Sep  2 23:31:07 192 kernel: [   17.565003] Modules linked in: ck804xrom(+) mtd snd_timer snd_seq_device psmouse mac80211 chipreg joydev snd sbp2(+) ppdev eeprom_93cx6 map_funcs nvidia(P) soundcore snd_page_alloc k8temp i2c_nforce2 pcspkr serio_raw wacom hid_logitech parport_pc parport cfg80211 ff_memless usbhid ohci1394 ieee1394 forcedeth fbcon tileblit font bitblit softcursor
Sep  2 23:31:07 192 kernel: [   17.565023] Pid: 955, comm: modprobe Tainted: P           2.6.28-11-generic #42-Ubuntu
Sep  2 23:31:07 192 kernel: [   17.565025] Call Trace:
Sep  2 23:31:07 192 kernel: [   17.565031]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90
Sep  2 23:31:07 192 kernel: [   17.565035]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Sep  2 23:31:07 192 kernel: [   17.565037]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Sep  2 23:31:07 192 kernel: [   17.565040]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390
Sep  2 23:31:07 192 kernel: [   17.565044]  [<ffffffffa096d2db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
Sep  2 23:31:07 192 kernel: [   17.565047]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
Sep  2 23:31:07 192 kernel: [   17.565050]  [<ffffffffa096d2db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
Sep  2 23:31:07 192 kernel: [   17.565054]  [<ffffffffa0973041>] init_ck804xrom+0x41/0x59 [ck804xrom]
Sep  2 23:31:07 192 kernel: [   17.565058]  [<ffffffffa0973000>] ? init_ck804xrom+0x0/0x59 [ck804xrom]
Sep  2 23:31:07 192 kernel: [   17.565061]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
Sep  2 23:31:07 192 kernel: [   17.565065]  [<ffffffff802424b2>] ? enqueue_entity+0x122/0x2b0
Sep  2 23:31:07 192 kernel: [   17.565067]  [<ffffffff8024870b>] ? enqueue_task_fair+0x7b/0x80
Sep  2 23:31:07 192 kernel: [   17.565070]  [<ffffffff8023e2a9>] ? wakeup_preempt_entity+0x59/0x60
Sep  2 23:31:07 192 kernel: [   17.565073]  [<ffffffff80249330>] ? check_preempt_wakeup+0x210/0x230
Sep  2 23:31:07 192 kernel: [   17.565075]  [<ffffffff8024a3cc>] ? try_to_wake_up+0x12c/0x2e0
Sep  2 23:31:07 192 kernel: [   17.565080]  [<ffffffff8027ef9d>] sys_init_module+0xad/0x1e0
Sep  2 23:31:07 192 kernel: [   17.565083]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Sep  2 23:31:07 192 kernel: [   17.565085] ---[ end trace 5a1e9023c4f7424e ]---
```

I'm mystified.

**Update**

I was able to solve the problem.  It had to do with the ethernet ports being activated, but nothing plugged into them.  I was able to solve this problem via this [bug report]("http://https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/355299").

---

