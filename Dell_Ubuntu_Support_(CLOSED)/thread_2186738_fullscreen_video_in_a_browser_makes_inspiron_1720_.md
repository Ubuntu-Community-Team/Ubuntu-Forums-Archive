---
title: "fullscreen video in a browser makes inspiron 1720 reboot"
date: 2013-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by slippycurb on 2013-11-08
hello, could someone help me here?
watching a video fullscreen in a browser (youtube, rte player, 4od etc) makes ubuntu 13.10 reboot, kind of weird, didnt happen in 13.04. also strangley I cant predict how long it will take before it happens...im not sure if it happens watching a video in vlc yet but il find out in a bit....
here is an lshw....

---

### Post by slippycurb on 2013-11-08
here is an dmesg (cleared before rebooting so its all recent, sorry about the length)```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-12-generic (buildd@komainu) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu7) ) #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 (Ubuntu 3.11.0-12.19-generic 3.11.3)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfe6d7ff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfe6d800-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed1bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feda0000-0x00000000feda5fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Dell Inc. Inspiron 1720                   /0UK437, BIOS A06 01/14/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0xbfe6d max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] total RAM covered: 3071M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b39000, 0x01b39fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35fa8000-0x36fcbfff]
[    0.000000] ACPI: RSDP 000fbbf0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT bfe6f200 0005C (v01 DELL    M08     27D8010E ASL  00000061)
[    0.000000] ACPI: FACP bfe6f09c 000F4 (v04 DELL    M08     27D8010E ASL  00000061)
[    0.000000] ACPI: DSDT bfe6f800 0565E (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS bfe7e000 00040
[    0.000000] ACPI: HPET bfe6f300 00038 (v01 DELL    M08     00000001 ASL  00000061)
[    0.000000] ACPI: APIC bfe6f400 00068 (v01 DELL    M08     27D8010E ASL  00000047)
[    0.000000] ACPI: MCFG bfe6f3c0 0003E (v16 DELL    M08     27D8010E ASL  00000061)
[    0.000000] ACPI: SLIC bfe6f49c 00176 (v01 DELL    M08     27D8010E ASL  00000061)
[    0.000000] ACPI: BOOT bfe6efc0 00028 (v01 DELL    M08     27D8010E ASL  00000061)
[    0.000000] ACPI: SSDT bfe6d9bc 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2178MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b3a000, 0x01b3afff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0xbfe6cfff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xbfe6cfff]
[    0.000000] On node 0 totalpages: 785931
[    0.000000] free_area_init_node: node 0, pgdat c1948bc0, node_mem_map f47a8020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4357 pages used for memmap
[    0.000000]   HighMem zone: 557679 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] e820: [mem 0xc0000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bd0000 s36288 r0 d21056 u57344
[    0.000000] pcpu-alloc: s36288 r0 d21056 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 784147
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=00726d9d-e2e0-48ba-91dc-728ff7714bcf ro splash quiet
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6288224 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000bfe6d)
[    0.000000] Memory: 3083920K/3143724K available (6351K kernel code, 607K rwdata, 2640K rodata, 880K init, 908K bss, 59804K reserved, 2230716K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1962000 - 0xc1a3e000   ( 880 kB)
[    0.000000]       .data : 0xc16341e4 - 0xc1961e00   (3255 kB)
[    0.000000]       .text : 0xc1000000 - 0xc16341e4   (6352 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7008000 soft=f700a000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1994.396 MHz processor
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3988.79 BogoMIPS (lpj=7977584)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.004041] Security Framework initialized
[    0.004062] AppArmor: AppArmor initialized
[    0.004065] Yama: becoming mindful.
[    0.004119] Mount-cache hash table entries: 512
[    0.004392] Initializing cgroup subsys memory
[    0.004405] Initializing cgroup subsys devices
[    0.004408] Initializing cgroup subsys freezer
[    0.004410] Initializing cgroup subsys blkio
[    0.004413] Initializing cgroup subsys perf_event
[    0.004416] Initializing cgroup subsys hugetlb
[    0.004446] CPU: Physical Processor ID: 0
[    0.004448] CPU: Processor Core ID: 0
[    0.004453] mce: CPU supports 6 MCE banks
[    0.004462] CPU0: Thermal monitoring enabled (TM2)
[    0.004476] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.004476] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.004476] tlb_flushall_shift: -1
[    0.004794] Freeing SMP alternatives memory: 28K (c1a3e000 - c1a45000)
[    0.008418] ACPI: Core revision 20130517
[    0.012126] ACPI: All ACPI Tables successfully acquired
[    0.013746] ftrace: allocating 27134 entries in 53 pages
[    0.024106] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024579] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.065236] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz (fam: 06, model: 0f, stepping: 0d)
[    0.068000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.068000] perf_event_intel: PEBS disabled due to CPU errata
[    0.068000] ... version:                2
[    0.068000] ... bit width:              40
[    0.068000] ... generic registers:      2
[    0.068000] ... value mask:             000000ffffffffff
[    0.068000] ... max period:             000000007fffffff
[    0.068000] ... fixed-purpose events:   3
[    0.068000] ... event mask:             0000000700000003
[    0.068000] CPU 1 irqstacks, hard=f70e6000 soft=f70f0000
[    0.068000] smpboot: Booting Node   0, Processors  #1 OK
[    0.008000] Initializing CPU#1
[    0.079156] Brought up 2 CPUs
[    0.079161] smpboot: Total of 2 processors activated (7977.58 BogoMIPS)
[    0.079254] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.084069] devtmpfs: initialized
[    0.084248] EVM: security.selinux
[    0.084250] EVM: security.SMACK64
[    0.084252] EVM: security.capability
[    0.085429] regulator-dummy: no parameters
[    0.085473] RTC time: 23:21:24, date: 11/08/13
[    0.085524] NET: Registered protocol family 16
[    0.085706] EISA bus registered
[    0.085786] ACPI: bus type PCI registered
[    0.085790] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.085859] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.085863] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.085865] PCI: Using MMCONFIG for extended config space
[    0.085867] PCI: Using configuration type 1 for base access
[    0.085880] dmi type 0xB1 record - unknown flag
[    0.085880] bio: create slab <bio-0> at 0
[    0.085880] ACPI: Added _OSI(Module Device)
[    0.085880] ACPI: Added _OSI(Processor Device)
[    0.085880] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.085880] ACPI: Added _OSI(Processor Aggregator Device)
[    0.085880] ACPI: EC: Look up EC in DSDT
[    0.094883] ACPI: SSDT bfe6e4f2 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.095251] ACPI: Dynamic OEM Table Load:
[    0.095255] ACPI: SSDT   (null) 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.095393] ACPI: SSDT bfe6de88 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.095738] ACPI: Dynamic OEM Table Load:
[    0.095741] ACPI: SSDT   (null) 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.096018] ACPI: SSDT bfe6e778 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.096380] ACPI: Dynamic OEM Table Load:
[    0.096384] ACPI: SSDT   (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.096480] ACPI: SSDT bfe6e46d 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.096828] ACPI: Dynamic OEM Table Load:
[    0.096831] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.097065] ACPI: Interpreter enabled
[    0.097078] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.097083] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.097100] ACPI: (supports S0 S3 S4 S5)
[    0.097102] ACPI: Using IOAPIC for interrupt routing
[    0.097132] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.097296] ACPI: No dock devices found.
[    0.145063] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.145070] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.145073] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.167566] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.167755] PCI host bridge to bus 0000:00
[    0.167759] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.167763] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.167766] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.167769] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.167772] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.167775] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xefffffff]
[    0.167778] pci_bus 0000:00: root bus resource [mem 0xf4000000-0xfebfffff]
[    0.167780] pci_bus 0000:00: root bus resource [mem 0xfec10000-0xfecfffff]
[    0.167783] pci_bus 0000:00: root bus resource [mem 0xfed1c000-0xfed1ffff]
[    0.167786] pci_bus 0000:00: root bus resource [mem 0xfed90000-0xfed9ffff]
[    0.167789] pci_bus 0000:00: root bus resource [mem 0xfeda7000-0xfedfffff]
[    0.167791] pci_bus 0000:00: root bus resource [mem 0xfee10000-0xff9fffff]
[    0.167794] pci_bus 0000:00: root bus resource [mem 0xffb00000-0xffefffff]
[    0.167807] pci 0000:00:00.0: [8086:2a00] type 00 class 0x060000
[    0.167955] pci 0000:00:01.0: [8086:2a01] type 01 class 0x060400
[    0.168018] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.168170] pci 0000:00:1a.0: [8086:2834] type 00 class 0x0c0300
[    0.168234] pci 0000:00:1a.0: reg 0x20: [io  0x6f20-0x6f3f]
[    0.170167] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.170217] pci 0000:00:1a.1: [8086:2835] type 00 class 0x0c0300
[    0.170280] pci 0000:00:1a.1: reg 0x20: [io  0x6f00-0x6f1f]
[    0.172085] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.172151] pci 0000:00:1a.7: [8086:283a] type 00 class 0x0c0320
[    0.172180] pci 0000:00:1a.7: reg 0x10: [mem 0xfed1c400-0xfed1c7ff]
[    0.172300] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.174200] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.174260] pci 0000:00:1b.0: [8086:284b] type 00 class 0x040300
[    0.174287] pci 0000:00:1b.0: reg 0x10: [mem 0xfebfc000-0xfebfffff 64bit]
[    0.174404] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.174489] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.174545] pci 0000:00:1c.0: [8086:283f] type 01 class 0x060400
[    0.174667] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.174755] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.174808] pci 0000:00:1c.1: [8086:2841] type 01 class 0x060400
[    0.174930] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.175018] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.175074] pci 0000:00:1c.3: [8086:2845] type 01 class 0x060400
[    0.175196] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.175288] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.175340] pci 0000:00:1d.0: [8086:2830] type 00 class 0x0c0300
[    0.175403] pci 0000:00:1d.0: reg 0x20: [io  0x6f80-0x6f9f]
[    0.177475] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.177523] pci 0000:00:1d.1: [8086:2831] type 00 class 0x0c0300
[    0.177586] pci 0000:00:1d.1: reg 0x20: [io  0x6f60-0x6f7f]
[    0.179522] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.179568] pci 0000:00:1d.2: [8086:2832] type 00 class 0x0c0300
[    0.179631] pci 0000:00:1d.2: reg 0x20: [io  0x6f40-0x6f5f]
[    0.181520] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.181583] pci 0000:00:1d.7: [8086:2836] type 00 class 0x0c0320
[    0.181611] pci 0000:00:1d.7: reg 0x10: [mem 0xfed1c000-0xfed1c3ff]
[    0.181731] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.183631] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.183686] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.183843] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.183896] pci 0000:00:1f.0: [8086:2815] type 00 class 0x060100
[    0.184088] pci 0000:00:1f.0: address space collision: [io  0x1000-0x107f] conflicts with ACPI CPU throttle [??? 0x00001010-0x00001015 flags 0x80000000]
[    0.184096] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.184101] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.184108] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.184259] pci 0000:00:1f.1: [8086:2850] type 00 class 0x01018a
[    0.184279] pci 0000:00:1f.1: reg 0x10: [io  0x01f0-0x01f7]
[    0.184293] pci 0000:00:1f.1: reg 0x14: [io  0x03f4-0x03f7]
[    0.184307] pci 0000:00:1f.1: reg 0x18: [io  0x0170-0x0177]
[    0.184320] pci 0000:00:1f.1: reg 0x1c: [io  0x0374-0x0377]
[    0.184334] pci 0000:00:1f.1: reg 0x20: [io  0x6fa0-0x6faf]
[    0.184480] pci 0000:00:1f.2: [8086:2829] type 00 class 0x010601
[    0.184511] pci 0000:00:1f.2: reg 0x10: [io  0x6eb0-0x6eb7]
[    0.184524] pci 0000:00:1f.2: reg 0x14: [io  0x6eb8-0x6ebb]
[    0.184538] pci 0000:00:1f.2: reg 0x18: [io  0x6ec0-0x6ec7]
[    0.184552] pci 0000:00:1f.2: reg 0x1c: [io  0x6ec8-0x6ecb]
[    0.184566] pci 0000:00:1f.2: reg 0x20: [io  0x6ee0-0x6eff]
[    0.184580] pci 0000:00:1f.2: reg 0x24: [mem 0xfebfb800-0xfebfbfff]
[    0.184654] pci 0000:00:1f.2: PME# supported from D3hot
[    0.184773] pci 0000:00:1f.3: [8086:283e] type 00 class 0x0c0500
[    0.184792] pci 0000:00:1f.3: reg 0x10: [mem 0xfebfb700-0xfebfb7ff]
[    0.184839] pci 0000:00:1f.3: reg 0x20: [io  0x10c0-0x10df]
[    0.185052] pci 0000:01:00.0: [10de:0427] type 00 class 0x030000
[    0.185074] pci 0000:01:00.0: reg 0x10: [mem 0xfd000000-0xfdffffff]
[    0.185098] pci 0000:01:00.0: reg 0x14: [mem 0xf4000000-0xf7ffffff 64bit pref]
[    0.185121] pci 0000:01:00.0: reg 0x1c: [mem 0xfa000000-0xfbffffff 64bit]
[    0.185137] pci 0000:01:00.0: reg 0x24: [io  0xef00-0xef7f]
[    0.185153] pci 0000:01:00.0: reg 0x30: [mem 0xfea00000-0xfea1ffff pref]
[    0.185299] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.185304] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.185308] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
[    0.185314] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff 64bit pref]
[    0.185411] pci 0000:00:1c.0: PCI bridge to [bus 0b]
[    0.185623] pci 0000:0c:00.0: [8086:4222] type 00 class 0x028000
[    0.185682] pci 0000:0c:00.0: reg 0x10: [mem 0xf9fff000-0xf9ffffff]
[    0.186115] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.186230] pci 0000:0c:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.186259] pci 0000:00:1c.1: PCI bridge to [bus 0c]
[    0.186268] pci 0000:00:1c.1:   bridge window [mem 0xf9f00000-0xf9ffffff]
[    0.186403] acpiphp: Slot [1] registered
[    0.186413] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.186420] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.186426] pci 0000:00:1c.3:   bridge window [mem 0xf9c00000-0xf9efffff]
[    0.186435] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xf81fffff 64bit pref]
[    0.186517] pci 0000:03:00.0: [14e4:170c] type 00 class 0x020000
[    0.186541] pci 0000:03:00.0: reg 0x10: [mem 0xf9bfe000-0xf9bfffff]
[    0.186647] pci 0000:03:00.0: supports D1 D2
[    0.186650] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.186717] pci 0000:03:01.0: [1180:0832] type 00 class 0x0c0010
[    0.186744] pci 0000:03:01.0: reg 0x10: [mem 0xf9bfd800-0xf9bfdfff]
[    0.186855] pci 0000:03:01.0: supports D1 D2
[    0.186857] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.186929] pci 0000:03:01.1: [1180:0822] type 00 class 0x080501
[    0.186955] pci 0000:03:01.1: reg 0x10: [mem 0xf9bfd500-0xf9bfd5ff]
[    0.187066] pci 0000:03:01.1: supports D1 D2
[    0.187068] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.187136] pci 0000:03:01.2: [1180:0592] type 00 class 0x088000
[    0.187161] pci 0000:03:01.2: reg 0x10: [mem 0xf9bfd600-0xf9bfd6ff]
[    0.187272] pci 0000:03:01.2: supports D1 D2
[    0.187274] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.187343] pci 0000:03:01.3: [1180:0852] type 00 class 0x088000
[    0.187368] pci 0000:03:01.3: reg 0x10: [mem 0xf9bfd700-0xf9bfd7ff]
[    0.187477] pci 0000:03:01.3: supports D1 D2
[    0.187480] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.187601] pci 0000:00:1e.0: PCI bridge to [bus 03] (subtractive decode)
[    0.187611] pci 0000:00:1e.0:   bridge window [mem 0xf9b00000-0xf9bfffff]
[    0.187620] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.187623] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.187626] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.187629] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.187632] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xefffffff] (subtractive decode)
[    0.187635] pci 0000:00:1e.0:   bridge window [mem 0xf4000000-0xfebfffff] (subtractive decode)
[    0.187638] pci 0000:00:1e.0:   bridge window [mem 0xfec10000-0xfecfffff] (subtractive decode)
[    0.187641] pci 0000:00:1e.0:   bridge window [mem 0xfed1c000-0xfed1ffff] (subtractive decode)
[    0.187644] pci 0000:00:1e.0:   bridge window [mem 0xfed90000-0xfed9ffff] (subtractive decode)
[    0.187647] pci 0000:00:1e.0:   bridge window [mem 0xfeda7000-0xfedfffff] (subtractive decode)
[    0.187650] pci 0000:00:1e.0:   bridge window [mem 0xfee10000-0xff9fffff] (subtractive decode)
[    0.187653] pci 0000:00:1e.0:   bridge window [mem 0xffb00000-0xffefffff] (subtractive decode)
[    0.187686] pci_bus 0000:00: on NUMA node 0
[    0.188310] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.188424] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.188535] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.188645] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.188757] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.188872] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.188987] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.189087] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.189307] ACPI: Enabled 4 GPEs in block 00 to 1F
[    0.192000] ACPI: \_SB_.PCI0: notify handler is installed
[    0.192065] Found 1 acpi root devices
[    0.192808] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.192812] vgaarb: loaded
[    0.192814] vgaarb: bridge control possible 0000:01:00.0
[    0.193356] SCSI subsystem initialized
[    0.193359] ACPI: bus type ATA registered
[    0.193903] libata version 3.00 loaded.
[    0.193903] ACPI: bus type USB registered
[    0.193903] usbcore: registered new interface driver usbfs
[    0.193903] usbcore: registered new interface driver hub
[    0.193903] usbcore: registered new device driver usb
[    0.193903] PCI: Using ACPI for IRQ routing
[    0.197428] PCI: pci_cache_line_size set to 64 bytes
[    0.197533] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.197536] e820: reserve RAM buffer [mem 0xbfe6d800-0xbfffffff]
[    0.197650] NetLabel: Initializing
[    0.197652] NetLabel:  domain hash size = 128
[    0.197653] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.197668] NetLabel:  unlabeled traffic allowed by default
[    0.197683] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.197683] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.197683] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.198123] Switched to clocksource hpet
[    0.205319] AppArmor: AppArmor Filesystem Enabled
[    0.205361] pnp: PnP ACPI init
[    0.205381] ACPI: bus type PNP registered
[    0.205485] pnp 00:00: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.205536] pnp 00:01: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.205581] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.205628] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.205702] system 00:04: [io  0x0c80-0x0cff] could not be reserved
[    0.205707] system 00:04: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.205730] pnp 00:05: [dma 4]
[    0.205756] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.205806] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.205895] system 00:07: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.205900] system 00:07: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.206087] pnp 00:08: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.206091] pnp 00:08: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.206141] system 00:08: [io  0x0900-0x097f] has been reserved
[    0.206145] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.206149] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.206182] pnp 00:09: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.206185] pnp 00:09: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.206189] pnp 00:09: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.206192] pnp 00:09: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.206236] system 00:09: [io  0xf400-0xf4fe] has been reserved
[    0.206240] system 00:09: [io  0x1080-0x10bf] has been reserved
[    0.206243] system 00:09: [io  0x10c0-0x10df] has been reserved
[    0.206247] system 00:09: [io  0x0809] has been reserved
[    0.206251] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.218855] system 00:0a: [mem 0x00000000-0x0009efff] could not be reserved
[    0.218860] system 00:0a: [mem 0x0009f000-0x0009ffff] could not be reserved
[    0.218864] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.218867] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.218871] system 00:0a: [mem 0x00100000-0xbfe6d7ff] could not be reserved
[    0.218874] system 00:0a: [mem 0xbfe6d800-0xbfefffff] has been reserved
[    0.218878] system 00:0a: [mem 0xbff00000-0xbfffffff] has been reserved
[    0.218881] system 00:0a: [mem 0xbff00000-0xc06fffff] could not be reserved
[    0.218885] system 00:0a: [mem 0xfff00000-0xffffffff] has been reserved
[    0.218889] system 00:0a: [mem 0xffa00000-0xffafffff] has been reserved
[    0.218892] system 00:0a: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.218896] system 00:0a: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.218899] system 00:0a: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.218902] system 00:0a: [mem 0xfeda0000-0xfeda3fff] has been reserved
[    0.218906] system 00:0a: [mem 0xfeda4000-0xfeda4fff] has been reserved
[    0.218909] system 00:0a: [mem 0xfeda5000-0xfeda5fff] has been reserved
[    0.218913] system 00:0a: [mem 0xfeda6000-0xfeda6fff] has been reserved
[    0.218916] system 00:0a: [mem 0xfed18000-0xfed1bfff] has been reserved
[    0.218919] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.218924] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.218994] pnp: PnP ACPI: found 11 devices
[    0.218996] ACPI: bus type PNP unregistered
[    0.219001] PnPBIOS: Disabled by ACPI PNP
[    0.256410] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 0b] add_size 1000
[    0.256416] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0b] add_size 200000
[    0.256420] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 0b] add_size 200000
[    0.256434] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 0c] add_size 1000
[    0.256438] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0c] add_size 200000
[    0.256464] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.256469] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.256472] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.256476] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.256479] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.256482] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.256488] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
[    0.256493] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.256497] pci 0000:00:1c.1: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.256501] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.256505] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.256509] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.256513] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.256518] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
[    0.256523] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff 64bit pref]
[    0.256529] pci 0000:00:1c.0: PCI bridge to [bus 0b]
[    0.256533] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.256540] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff]
[    0.256547] pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.256556] pci 0000:00:1c.1: PCI bridge to [bus 0c]
[    0.256560] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.256567] pci 0000:00:1c.1:   bridge window [mem 0xf9f00000-0xf9ffffff]
[    0.256574] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.256583] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.256587] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.256594] pci 0000:00:1c.3:   bridge window [mem 0xf9c00000-0xf9efffff]
[    0.256600] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xf81fffff 64bit pref]
[    0.256610] pci 0000:00:1e.0: PCI bridge to [bus 03]
[    0.256617] pci 0000:00:1e.0:   bridge window [mem 0xf9b00000-0xf9bfffff]
[    0.257479] pci 0000:00:1e.0: setting latency timer to 64
[    0.257485] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.257489] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.257492] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.257494] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.257497] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xefffffff]
[    0.257500] pci_bus 0000:00: resource 9 [mem 0xf4000000-0xfebfffff]
[    0.257503] pci_bus 0000:00: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.257506] pci_bus 0000:00: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.257509] pci_bus 0000:00: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.257512] pci_bus 0000:00: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.257515] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.257517] pci_bus 0000:00: resource 15 [mem 0xffb00000-0xffefffff]
[    0.257520] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.257523] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfeafffff]
[    0.257526] pci_bus 0000:01: resource 2 [mem 0xf4000000-0xf7ffffff 64bit pref]
[    0.257529] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.257532] pci_bus 0000:0b: resource 1 [mem 0xc0000000-0xc01fffff]
[    0.257535] pci_bus 0000:0b: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.257538] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.257541] pci_bus 0000:0c: resource 1 [mem 0xf9f00000-0xf9ffffff]
[    0.257543] pci_bus 0000:0c: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.257546] pci_bus 0000:0d: resource 0 [io  0xd000-0xdfff]
[    0.257549] pci_bus 0000:0d: resource 1 [mem 0xf9c00000-0xf9efffff]
[    0.257552] pci_bus 0000:0d: resource 2 [mem 0xf8000000-0xf81fffff 64bit pref]
[    0.257555] pci_bus 0000:03: resource 1 [mem 0xf9b00000-0xf9bfffff]
[    0.257558] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.257560] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.257563] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.257566] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.257568] pci_bus 0000:03: resource 8 [mem 0xc0000000-0xefffffff]
[    0.257571] pci_bus 0000:03: resource 9 [mem 0xf4000000-0xfebfffff]
[    0.257574] pci_bus 0000:03: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.257577] pci_bus 0000:03: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.257580] pci_bus 0000:03: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.257582] pci_bus 0000:03: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.257585] pci_bus 0000:03: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.257588] pci_bus 0000:03: resource 15 [mem 0xffb00000-0xffefffff]
[    0.257628] NET: Registered protocol family 2
[    0.257816] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.257848] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.257880] TCP: Hash tables configured (established 8192 bind 8192)
[    0.257914] TCP: reno registered
[    0.257917] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.257927] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.257996] NET: Registered protocol family 1
[    0.261025] pci 0000:01:00.0: Boot video device
[    0.261050] PCI: CLS 64 bytes, default 64
[    0.261098] Trying to unpack rootfs image as initramfs...
[    0.645101] Freeing initrd memory: 16528K (f5fa8000 - f6fcc000)
[    0.645188] Simple Boot Flag at 0x79 set to 0x1
[    0.645345] Scanning for low memory corruption every 60 seconds
[    0.645643] Initialise module verification
[    0.645700] audit: initializing netlink socket (disabled)
[    0.645718] type=2000 audit(1383952883.644:1): initialized
[    0.672490] bounce pool size: 64 pages
[    0.672504] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.674348] zbud: loaded
[    0.674414] VFS: Disk quotas dquot_6.5.2
[    0.674474] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.675128] fuse init (API version 7.22)
[    0.675238] msgmni has been set to 1698
[    0.675986] Key type asymmetric registered
[    0.675989] Asymmetric key parser 'x509' registered
[    0.676049] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.676090] io scheduler noop registered
[    0.676093] io scheduler deadline registered (default)
[    0.676130] io scheduler cfq registered
[    0.676275] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.676354] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.676456] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.676558] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.676674] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.676694] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.676790] intel_idle: does not run on family 6 model 15
[    0.676909] ACPI: AC Adapter [AC] (on-line)
[    0.677034] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.677450] ACPI: Lid Switch [LID]
[    0.677496] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.677501] ACPI: Power Button [PBTN]
[    0.677544] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.677548] ACPI: Sleep Button [SBTN]
[    0.677619] ACPI: Requesting acpi_cpufreq
[    0.679125] Monitor-Mwait will be used to enter C-1 state
[    0.679133] Monitor-Mwait will be used to enter C-2 state
[    0.679138] Monitor-Mwait will be used to enter C-3 state
[    0.679142] tsc: Marking TSC unstable due to TSC halts in idle
[    0.679154] ACPI: acpi_idle registered with cpuidle
[    0.685863] thermal LNXTHERM:00: registered as thermal_zone0
[    0.685867] ACPI: Thermal Zone [THM] (66 C)
[    0.685911] GHES: HEST is not enabled!
[    0.686018] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.691212] isapnp: Scanning for PnP cards...
[    0.703333] Linux agpgart interface v0.103
[    0.708506] ACPI: Battery Slot [BAT0] (battery present)
[    0.709683] brd: module loaded
[    0.710552] loop: module loaded
[    0.710689] ata_piix 0000:00:1f.1: version 2.13
[    0.710960] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.711294] scsi0 : ata_piix
[    0.711597] scsi1 : ata_piix
[    0.711700] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.711703] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.712085] libphy: Fixed MDIO Bus: probed
[    0.712207] tun: Universal TUN/TAP device driver, 1.6
[    0.712209] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.712276] PPP generic driver version 2.4.2
[    0.712323] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.712326] ehci-pci: EHCI PCI platform driver
[    0.712564] ehci-pci 0000:00:1a.7: setting latency timer to 64
[    0.712580] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.712587] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.712606] ehci-pci 0000:00:1a.7: debug port 1
[    0.716505] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.716657] ehci-pci 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.716698] ata2: port disabled--ignoring
[    0.728025] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.728048] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.728052] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.728055] usb usb1: Product: EHCI Host Controller
[    0.728057] usb usb1: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    0.728060] usb usb1: SerialNumber: 0000:00:1a.7
[    0.728177] hub 1-0:1.0: USB hub found
[    0.728182] hub 1-0:1.0: 4 ports detected
[    0.728589] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    0.728602] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.728608] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.728625] ehci-pci 0000:00:1d.7: debug port 1
[    0.732528] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.732550] ehci-pci 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.744025] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.744042] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.744045] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.744048] usb usb2: Product: EHCI Host Controller
[    0.744051] usb usb2: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    0.744053] usb usb2: SerialNumber: 0000:00:1d.7
[    0.744163] hub 2-0:1.0: USB hub found
[    0.744168] hub 2-0:1.0: 6 ports detected
[    0.744436] ehci-platform: EHCI generic platform driver
[    0.744446] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.744448] ohci-platform: OHCI generic platform driver
[    0.744456] uhci_hcd: USB Universal Host Controller Interface driver
[    0.744685] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.744690] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.744696] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.744726] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.744763] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.744766] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.744769] usb usb3: Product: UHCI Host Controller
[    0.744772] usb usb3: Manufacturer: Linux 3.11.0-12-generic uhci_hcd
[    0.744775] usb usb3: SerialNumber: 0000:00:1a.0
[    0.744892] hub 3-0:1.0: USB hub found
[    0.744897] hub 3-0:1.0: 2 ports detected
[    0.745224] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.745228] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.745234] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.745276] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.745313] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.745316] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.745319] usb usb4: Product: UHCI Host Controller
[    0.745322] usb usb4: Manufacturer: Linux 3.11.0-12-generic uhci_hcd
[    0.745325] usb usb4: SerialNumber: 0000:00:1a.1
[    0.745430] hub 4-0:1.0: USB hub found
[    0.745435] hub 4-0:1.0: 2 ports detected
[    0.745758] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.745762] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.745768] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.745798] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.745836] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.745839] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.745842] usb usb5: Product: UHCI Host Controller
[    0.745845] usb usb5: Manufacturer: Linux 3.11.0-12-generic uhci_hcd
[    0.745847] usb usb5: SerialNumber: 0000:00:1d.0
[    0.745955] hub 5-0:1.0: USB hub found
[    0.745960] hub 5-0:1.0: 2 ports detected
[    0.746285] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.746290] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.746296] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.746325] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.746362] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.746365] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.746368] usb usb6: Product: UHCI Host Controller
[    0.746371] usb usb6: Manufacturer: Linux 3.11.0-12-generic uhci_hcd
[    0.746373] usb usb6: SerialNumber: 0000:00:1d.1
[    0.746483] hub 6-0:1.0: USB hub found
[    0.746488] hub 6-0:1.0: 2 ports detected
[    0.746813] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.746818] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.746824] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.746853] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.746888] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.746891] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.746894] usb usb7: Product: UHCI Host Controller
[    0.746897] usb usb7: Manufacturer: Linux 3.11.0-12-generic uhci_hcd
[    0.746899] usb usb7: SerialNumber: 0000:00:1d.2
[    0.747005] hub 7-0:1.0: USB hub found
[    0.747010] hub 7-0:1.0: 2 ports detected
[    0.747204] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.750378] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.750384] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.750506] mousedev: PS/2 mouse device common for all mice
[    0.750668] rtc_cmos 00:02: RTC can wake from S4
[    0.750820] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.750855] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.750950] device-mapper: uevent: version 1.0.3
[    0.751019] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.751042] platform eisa.0: Probing EISA bus 0
[    0.751080] platform eisa.0: EISA: Detected 0 cards
[    0.751089] cpufreq-nforce2: No nForce2 chipset.
[    0.751139] cpuidle: using governor ladder
[    0.751205] cpuidle: using governor menu
[    0.751219] ledtrig-cpu: registered to indicate activity on CPUs
[    0.751329] TCP: cubic registered
[    0.751454] NET: Registered protocol family 10
[    0.751689] NET: Registered protocol family 17
[    0.751702] Key type dns_resolver registered
[    0.751890] Using IPI No-Shortcut mode
[    0.751977] PM: Hibernation image not present or could not be loaded.
[    0.751982] Loading module verification certificates
[    0.756558] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 4b7c2664fb134f99aaf5e09f5b6d30d43b5eac95'
[    0.756574] registered taskstats version 1
[    0.758053] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.759604] Key type trusted registered
[    0.761931] Key type encrypted registered
[    0.764600] AppArmor: AppArmor sha1 policy hashing enabled
[    0.765136]   Magic number: 5:894:402
[    0.765179] pci 0000:03:00.0: hash matches
[    0.765243] rtc_cmos 00:02: setting system clock to 2013-11-08 23:21:24 UTC (1383952884)
[    0.767850] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.767852] EDD information not available.
[    0.880409] ata1.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A102, max UDMA/33
[    0.896352] ata1.00: configured for UDMA/33
[    1.049824] isapnp: No Plug & Play device found
[    1.053438] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A102 PQ: 0 ANSI: 5
[    1.056055] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.058370] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.058375] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.058609] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.058748] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.059253] Freeing unused kernel memory: 880K (c1962000 - c1a3e000)
[    1.059301] Write protecting the kernel text: 6356k
[    1.059405] Write protecting the kernel read-only data: 2644k
[    1.059407] NX-protecting the kernel data: 5932k
[    1.074969] systemd-udevd[99]: starting version 204
[    1.122033] libahci: module verification failed: signature and/or required key missing - tainting kernel
[    1.122833] ahci 0000:00:1f.2: version 3.0
[    1.123138] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.123214] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    1.123219] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    1.123225] ahci 0000:00:1f.2: setting latency timer to 64
[    1.136063] scsi2 : ahci
[    1.138675] scsi3 : ahci
[    1.143949] sdhci: Secure Digital Host Controller Interface driver
[    1.143953] sdhci: Copyright(c) Pierre Ossman
[    1.144109] scsi4 : ahci
[    1.144212] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 44
[    1.144215] ata4: DUMMY
[    1.144219] ata5: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 44
[    1.156136] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[    1.156146] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.156154] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.156161] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.196160] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.196210] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    1.196222] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.197375] mmc0: no vqmmc regulator found
[    1.197378] mmc0: no vmmc regulator found
[    1.198472] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    1.205393] usb 2-1: New USB device found, idVendor=0bb4, idProduct=0cb0
[    1.205400] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.205405] usb 2-1: Product: Android Phone
[    1.205410] usb 2-1: Manufacturer: HTC
[    1.205414] usb 2-1: SerialNumber: HT1A5TR06101
[    1.216635] b44 ssb0:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1d:09:c7:d6:c4
[    1.268250] firewire_ohci 0000:03:01.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.320939] usb 2-6: new high-speed USB device number 3 using ehci-pci
[    1.458648] usb 2-6: New USB device found, idVendor=05a9, idProduct=2640
[    1.458655] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.458660] usb 2-6: Product: Laptop Integrated Webcam
[    1.458665] usb 2-6: Manufacturer: OmniVision Technologies, Inc. -2640-07.07.20.3
[    1.464058] ata5: SATA link down (SStatus 0 SControl 300)
[    1.464096] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.467208] usb-storage 2-1:1.0: USB Mass Storage device detected
[    1.467438] scsi5 : usb-storage 2-1:1.0
[    1.467535] usbcore: registered new interface driver usb-storage
[    1.516863] ata3.00: ATA-8: WDC WD2500BEVS-75UST0, 01.01A01, max UDMA/133
[    1.516869] ata3.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32), AA
[    1.517832] ata3.00: configured for UDMA/133
[    1.518033] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-7 01.0 PQ: 0 ANSI: 5
[    1.518239] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.518319] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.518402] sd 2:0:0:0: [sda] Write Protect is off
[    1.518406] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.518428] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.558117]  sda: sda1 sda2
[    1.558596] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.768197] firewire_core 0000:03:01.0: created device fw0: GUID 464fc0002e8ebc70, S400
[    1.842249] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.842254] EXT4-fs (sda1): write access will be enabled during recovery
[    2.466229] scsi 5:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[    2.466608] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    2.475198] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    4.294259] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.294746] EXT4-fs (sda1): 23 orphan inodes deleted
[    4.294749] EXT4-fs (sda1): recovery complete
[    4.454342] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   17.496061] Swap area shorter than signature indicates
[   17.593931] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.736377] systemd-udevd[270]: starting version 204
[   17.848168] wmi: Mapper loaded
[   17.853444] acpi device:31: registered as cooling_device2
[   17.853876] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   17.853971] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input4
[   17.854140] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   17.925690] [drm] Initialized drm 1.1.0 20060810
[   17.955219] cfg80211: Calling CRDA to update world regulatory domain
[   17.990435] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x086700a2
[   17.990440] nouveau  [  DEVICE][0000:01:00.0] Chipset: G86 (NV86)
[   17.990443] nouveau  [  DEVICE][0000:01:00.0] Family : NV50
[   17.991369] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.994114] lp: driver loaded but no devices found
[   18.003490] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[   18.096946] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[   18.096951] nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
[   18.097070] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[   18.097074] nouveau  [   VBIOS][0000:01:00.0] version 60.86.42.00.35
[   18.137103] nouveau  [     PFB][0000:01:00.0] RAM type: DDR2
[   18.137109] nouveau  [     PFB][0000:01:00.0] RAM size: 128 MiB
[   18.137112] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 646 tags
[   18.153646] r592: driver successfully loaded
[   18.181734] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa1
[   18.199889] r852: driver loaded successfully
[   18.215062] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   18.215066] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   18.215108] iwl3945 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[   18.272386] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   18.272391] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.272465] iwl3945 0000:0c:00.0: irq 45 for MSI/MSI-X
[   18.279324] type=1400 audit(1383952902.010:2): apparmor="STATUS" operation="profile_load" parent=322 profile="unconfined" name="/sbin/dhclient" pid=339 comm="apparmor_parser"
[   18.279333] type=1400 audit(1383952902.010:3): apparmor="STATUS" operation="profile_load" parent=322 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=339 comm="apparmor_parser"
[   18.279340] type=1400 audit(1383952902.010:4): apparmor="STATUS" operation="profile_load" parent=322 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=339 comm="apparmor_parser"
[   18.281544] type=1400 audit(1383952902.014:5): apparmor="STATUS" operation="profile_replace" parent=322 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=339 comm="apparmor_parser"
[   18.281556] type=1400 audit(1383952902.014:6): apparmor="STATUS" operation="profile_replace" parent=322 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=339 comm="apparmor_parser"
[   18.281961] type=1400 audit(1383952902.014:7): apparmor="STATUS" operation="profile_replace" parent=322 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=339 comm="apparmor_parser"
[   18.312987] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   18.332712] nouveau  [  PTHERM][0000:01:00.0] FAN control: PWM
[   18.332727] nouveau  [  PTHERM][0000:01:00.0] fan management: disabled
[   18.332732] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[   18.332928] [TTM] Zone  kernel: Available graphics memory: 435320 kiB
[   18.332931] [TTM] Zone highmem: Available graphics memory: 1550678 kiB
[   18.332933] [TTM] Initializing pool allocator
[   18.332939] [TTM] Initializing DMA pool allocator
[   18.332951] nouveau  [     DRM] VRAM: 128 MiB
[   18.332954] nouveau  [     DRM] GART: 1048576 MiB
[   18.332959] nouveau  [     DRM] TMDS table version 2.0
[   18.332962] nouveau  [     DRM] DCB version 4.0
[   18.332965] nouveau  [     DRM] DCB outp 00: 01000323 00010034
[   18.332968] nouveau  [     DRM] DCB outp 01: 02011300 00000028
[   18.332971] nouveau  [     DRM] DCB outp 02: 010223f1 00c0c080
[   18.332974] nouveau  [     DRM] DCB conn 00: 0041
[   18.332978] nouveau  [     DRM] DCB conn 01: 0100
[   18.332980] nouveau  [     DRM] DCB conn 02: 0310
[   18.332983] nouveau  [     DRM] DCB conn 03: 0311
[   18.332986] nouveau  [     DRM] DCB conn 04: 0313
[   18.364106] nouveau W[     DRM] failed to create encoder 0/1/0: -19
[   18.364111] nouveau W[     DRM] TV-1 has no encoders, removing
[   18.364141] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.364143] [drm] No driver support for vblank timestamp query.
[   18.364146] nouveau  [     DRM] ACPI backlight interface available, not registering our own
[   18.364251] nouveau  [     DRM] 3 available performance level(s)
[   18.364256] nouveau  [     DRM] 0: core 169MHz shader 338MHz memory 100MHz voltage 1150mV fanspeed 100%
[   18.364261] nouveau  [     DRM] 1: core 275MHz shader 550MHz memory 200MHz voltage 1150mV fanspeed 100%
[   18.364265] nouveau  [     DRM] 2: core 400MHz shader 800MHz memory 400MHz voltage 1150mV fanspeed 100%
[   18.364269] nouveau  [     DRM] c: core 275MHz shader 550MHz memory 199MHz voltage 1150mV
[   18.377323] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   18.383879] nouveau  [     DRM] MM: using CRYPT for buffer copies
[   18.428820] autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   18.428825]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.428827]    hp_outs=1 (0xa/0x0/0x0/0x0/0x0)
[   18.428829]    mono: mono_out=0x0
[   18.428831]    dig-out=0x21/0x0
[   18.428832]    inputs:
[   18.428835]      Internal Mic=0x17
[   18.428837]      Mic=0xb
[   18.436191] nouveau  [     DRM] allocated 1440x900 fb: 0x60000, bo eff3d400
[   18.436278] fbcon: nouveaufb (fb0) is primary device
[   18.443509] autoconfig: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[   18.443511]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.443512]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.443513]    mono: mono_out=0x0
[   18.443513]    inputs:
[   18.453978] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   18.454081] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   18.616754] Linux video capture interface: v2.00
[   18.648160] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   18.650717] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input7
[   18.652693] usbcore: registered new interface driver uvcvideo
[   18.652694] USB Video Class driver (1.1.1)
[   18.694395] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.787656] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   19.030369] cfg80211: World regulatory domain updated:
[   19.030370] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.030372] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.030374] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.030375] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.030376] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.030377] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.037892] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   19.054794] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa1
[   19.084018] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   19.101296] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   19.374063] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   19.382006] kvm: disabled by bios
[   19.501248] Console: switching to colour frame buffer device 180x56
[   19.504243] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[   19.504245] nouveau 0000:01:00.0: registered panic notifier
[   19.504249] [drm] Initialized nouveau 1.1.1 20120801 for 0000:01:00.0 on minor 0
[   19.625540] Bluetooth: Core ver 2.16
[   19.625590] NET: Registered protocol family 31
[   19.625593] Bluetooth: HCI device and connection manager initialized
[   19.625969] Bluetooth: HCI socket layer initialized
[   19.625974] Bluetooth: L2CAP socket layer initialized
[   19.625982] Bluetooth: SCO socket layer initialized
[   19.646609] Bluetooth: RFCOMM TTY layer initialized
[   19.646623] Bluetooth: RFCOMM socket layer initialized
[   19.646625] Bluetooth: RFCOMM ver 1.11
[   19.716608] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.716613] Bluetooth: BNEP filters: protocol multicast
[   19.716624] Bluetooth: BNEP socket layer initialized
[   20.130813] init: failsafe main process (554) killed by TERM signal
[   20.131276] init: udev-fallback-graphics main process (598) terminated with status 1
[   20.705829] ppdev: user-space parallel port driver
[   20.709141] init: avahi-cups-reload main process (712) terminated with status 1
[   20.765299] type=1400 audit(1383952904.498:8): apparmor="STATUS" operation="profile_load" parent=750 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=755 comm="apparmor_parser"
[   20.765309] type=1400 audit(1383952904.498:9): apparmor="STATUS" operation="profile_load" parent=750 profile="unconfined" name="/usr/sbin/cupsd" pid=755 comm="apparmor_parser"
[   20.766185] type=1400 audit(1383952904.498:10): apparmor="STATUS" operation="profile_replace" parent=750 profile="unconfined" name="/usr/sbin/cupsd" pid=755 comm="apparmor_parser"
[   21.180659] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   21.249652] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.249988] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.257271] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.257635] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.130242] type=1400 audit(1383952905.862:11): apparmor="STATUS" operation="profile_load" parent=808 profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=814 comm="apparmor_parser"
[   27.636704] wlan0: authenticate with 64:66:b3:58:78:5a
[   27.640601] wlan0: send auth to 64:66:b3:58:78:5a (try 1/3)
[   27.642379] wlan0: authenticated
[   27.644180] wlan0: associate with 64:66:b3:58:78:5a (try 1/3)
[   27.647519] wlan0: RX AssocResp from 64:66:b3:58:78:5a (capab=0x411 status=0 aid=2)
[   27.650233] wlan0: associated
[   27.650272] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.650334] cfg80211: Calling CRDA for country: GB
[   27.654654] cfg80211: Regulatory domain changed to country: GB
[   27.654659] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.654661] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   27.654664] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   27.654666] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   27.654669] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   27.654671] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[  299.988160] mce: [Hardware Error]: Machine check events logged
[  609.591510] systemd-hostnamed[3584]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  670.170108] perf samples too long (2513 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
```

---

### Post by slippycurb on 2013-11-08
update: it seems watching videos in vlc fullscreen does Not make it crash.....

---

