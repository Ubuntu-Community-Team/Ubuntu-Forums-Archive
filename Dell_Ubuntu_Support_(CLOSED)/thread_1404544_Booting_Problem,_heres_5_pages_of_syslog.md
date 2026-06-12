---
title: "Booting Problem, heres 5 pages of syslog"
date: 2010-02-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by linux000019 on 2010-02-11
```
Feb 11 10:52:19 ryan-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="910" x-info="http://www.rsyslog.com"] (re)start
Feb 11 10:52:19 ryan-laptop rsyslogd: rsyslogd's groupid changed to 102
Feb 11 10:52:19 ryan-laptop rsyslogd: rsyslogd's userid changed to 101
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 11 10:52:19 ryan-laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Linux version 2.6.31-19-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 (Ubuntu 2.6.31-19.56-generic)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] KERNEL supported cpus:
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   Intel GenuineIntel
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   AMD AuthenticAMD
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   NSC Geode by NSC
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   Centaur CentaurHauls
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6bf400 (usable)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 000000003f6bf400 - 0000000040000000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] DMI 2.4 present.
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] last_pfn = 0x3f6bf max_arch_pfn = 0x100000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] MTRR default type: uncachable
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   00000-9FFFF write-back
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   A0000-BFFFF uncachable
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   C0000-CFFFF write-protect
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   D0000-EFFFF uncachable
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   F0000-FFFFF write-protect
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] MTRR variable ranges enabled:
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   1 base 03F800000 mask FFF800000 uncachable
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   2 base 03F700000 mask FFFF00000 uncachable
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   3 disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   4 disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   5 disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   6 disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   7 disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] modified physical RAM map:
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000003f6bf400 (usable)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 000000003f6bf400 - 0000000040000000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] RAMDISK: 2f205000 - 2f94ee7c
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: RSDP 000fbf90 00024 (v02 DELL  )
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: XSDT 3f6c1e00 0006C (v01 DELL    M08     27DA0115 ASL  00000061)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: FACP 3f6c1c9c 000F4 (v04 DELL    M08     27DA0115 ASL  00000061)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: DSDT 3f6c2400 06506 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: FACS 3f6d0c00 00040
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: HPET 3f6c1f00 00038 (v01 DELL    M08     00000001 ASL  00000061)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: APIC 3f6c2000 00068 (v01 DELL    M08     27DA0115 ASL  00000047)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: ASF! 3f6c1c00 0007E (v32 DELL    M08     27DA0115 ASL  00000061)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: MCFG 3f6c1fc0 0003E (v16 DELL    M08     27DA0115 ASL  00000061)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: TCPA 3f6c2300 00032 (v01                 00000000 ASL  00000000)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: SLIC 3f6c209c 00176 (v01 DELL    M08     27DA0115 ASL  00000061)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: SSDT 3f6c0f8a 004B6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: SSDT 3f6c0abe 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] 126MB HIGHMEM available.
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] 887MB LOWMEM available.
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   low ram: 0 - 377fe000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   #4 [002f205000 - 002f94ee7c]          RAMDISK ==> [002f205000 - 002f94ee7c]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   #6 [00008a9000 - 00008ac188]              BRK ==> [00008a9000 - 00008ac188]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Zone PFN ranges:
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f6bf
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Movable zone start PFN for each node
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] early_node_map[3] active PFN ranges
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0003f6bf
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] On node 0 totalpages: 259674
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1000000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   HighMem zone: 254 pages used for memmap
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]   HighMem zone: 32195 pages, LIFO batch:7
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Using APIC driver default
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] nr_irqs_gsi: 24
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:b8000000)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257644
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-19-generic root=UUID=4413e0c4-e947-4e74-9100-551f31e65986 ro quiet splash
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Initializing CPU#0
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] allocated 5195500 bytes of page_cgroup
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f6bf)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Memory: 1008764k/1039100k available (4567k kernel code, 29476k reserved, 2141k data, 540k init, 129796k highmem)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] virtual kernel memory layout:
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]       .data : 0xc0575c48 - 0xc078d408   (2141 kB)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575c48   (4567 kB)
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Extended CMOS year: 2000
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Feb 11 10:52:19 ryan-laptop kernel: [    0.000000] Detected 1994.662 MHz processor.
Feb 11 10:52:19 ryan-laptop kernel: [    0.001532] Console: colour VGA+ 80x25
Feb 11 10:52:19 ryan-laptop kernel: [    0.001536] console [tty0] enabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.001708] hpet clockevent registered
Feb 11 10:52:19 ryan-laptop kernel: [    0.001712] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Feb 11 10:52:19 ryan-laptop kernel: [    0.001720] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.32 BogoMIPS (lpj=7978648)
Feb 11 10:52:19 ryan-laptop kernel: [    0.001742] Security Framework initialized
Feb 11 10:52:19 ryan-laptop kernel: [    0.001765] AppArmor: AppArmor initialized
Feb 11 10:52:19 ryan-laptop kernel: [    0.001772] Mount-cache hash table entries: 512
Feb 11 10:52:19 ryan-laptop kernel: [    0.001918] Initializing cgroup subsys ns
Feb 11 10:52:19 ryan-laptop kernel: [    0.001924] Initializing cgroup subsys cpuacct
Feb 11 10:52:19 ryan-laptop kernel: [    0.001928] Initializing cgroup subsys memory
Feb 11 10:52:19 ryan-laptop kernel: [    0.001936] Initializing cgroup subsys freezer
Feb 11 10:52:19 ryan-laptop kernel: [    0.001938] Initializing cgroup subsys net_cls
Feb 11 10:52:19 ryan-laptop kernel: [    0.001954] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb 11 10:52:19 ryan-laptop kernel: [    0.001956] CPU: L2 cache: 1024K
Feb 11 10:52:19 ryan-laptop kernel: [    0.001961] mce: CPU supports 6 MCE banks
Feb 11 10:52:19 ryan-laptop kernel: [    0.001970] CPU0: Thermal monitoring enabled (TM2)
Feb 11 10:52:19 ryan-laptop kernel: [    0.001974] using mwait in idle threads.
Feb 11 10:52:19 ryan-laptop kernel: [    0.001981] Performance Counters: Core2 events, Intel PMU driver.
Feb 11 10:52:19 ryan-laptop kernel: [    0.001990] ... version:                 2
Feb 11 10:52:19 ryan-laptop kernel: [    0.001992] ... bit width:               40
Feb 11 10:52:19 ryan-laptop kernel: [    0.001994] ... generic counters:        2
Feb 11 10:52:19 ryan-laptop kernel: [    0.001996] ... value mask:              000000ffffffffff
Feb 11 10:52:19 ryan-laptop kernel: [    0.001998] ... max period:              000000007fffffff
Feb 11 10:52:19 ryan-laptop kernel: [    0.002000] ... fixed-purpose counters:  3
Feb 11 10:52:19 ryan-laptop kernel: [    0.002001] ... counter mask:            0000000700000003
Feb 11 10:52:19 ryan-laptop kernel: [    0.002005] Checking 'hlt' instruction... OK.
Feb 11 10:52:19 ryan-laptop kernel: [    0.016830] SMP alternatives: switching to UP code
Feb 11 10:52:19 ryan-laptop kernel: [    0.024007] ACPI: Core revision 20090521
Feb 11 10:52:19 ryan-laptop kernel: [    0.036448] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb 11 10:52:19 ryan-laptop kernel: [    0.076884] CPU0: Intel(R) Celeron(R) CPU          550  @ 2.00GHz stepping 01
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] Brought up 1 CPUs
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] Total of 1 processors activated (3989.32 BogoMIPS).
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] CPU0 attaching NULL sched-domain.
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] Booting paravirtualized kernel on bare hardware
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] regulator: core version 0.5
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] Time: 10:52:06  Date: 02/11/10
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] NET: Registered protocol family 16
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] EISA bus registered
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] ACPI: bus type pci registered
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] PCI: MCFG area at f8000000 reserved in E820
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] PCI: Using MMCONFIG for extended config space
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] PCI: Using configuration type 1 for base access
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] bio: create slab <bio-0> at 0
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] ACPI: EC: Look up EC in DSDT
Feb 11 10:52:19 ryan-laptop kernel: [    0.080001] ACPI: BIOS _OSI(Linux) query ignored
Feb 11 10:52:19 ryan-laptop kernel: [    0.114006] ACPI: SSDT 3f6d0c80 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
Feb 11 10:52:19 ryan-laptop kernel: [    0.130188] ACPI: Interpreter enabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.130194] ACPI: (supports S0 S3 S4 S5)
Feb 11 10:52:19 ryan-laptop kernel: [    0.130215] ACPI: Using IOAPIC for interrupt routing
Feb 11 10:52:19 ryan-laptop kernel: [    0.214821] ACPI: ACPI Dock Station Driver: 3 docks/bays found
Feb 11 10:52:19 ryan-laptop kernel: [    0.230896] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb 11 10:52:19 ryan-laptop kernel: [    0.231003] pci 0000:00:02.0: reg 10 64bit mmio: [0xf6e00000-0xf6efffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.231011] pci 0000:00:02.0: reg 18 64bit mmio: [0xe0000000-0xefffffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.231017] pci 0000:00:02.0: reg 20 io port: [0xefe8-0xefef]
Feb 11 10:52:19 ryan-laptop kernel: [    0.231064] pci 0000:00:02.1: reg 10 64bit mmio: [0xf6f00000-0xf6ffffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.231190] pci 0000:00:1a.0: reg 20 io port: [0x6f20-0x6f3f]
Feb 11 10:52:19 ryan-laptop kernel: [    0.231263] pci 0000:00:1a.1: reg 20 io port: [0x6f00-0x6f1f]
Feb 11 10:52:19 ryan-laptop kernel: [    0.231343] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.231414] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Feb 11 10:52:19 ryan-laptop kernel: [    0.231420] pci 0000:00:1a.7: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.231481] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6dfc000-0xf6dfffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.231550] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Feb 11 10:52:19 ryan-laptop kernel: [    0.231555] pci 0000:00:1b.0: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.231653] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Feb 11 10:52:19 ryan-laptop kernel: [    0.231658] pci 0000:00:1c.0: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.231758] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Feb 11 10:52:19 ryan-laptop kernel: [    0.231763] pci 0000:00:1c.1: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.231869] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Feb 11 10:52:19 ryan-laptop kernel: [    0.231874] pci 0000:00:1c.5: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.231945] pci 0000:00:1d.0: reg 20 io port: [0x6f80-0x6f9f]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232024] pci 0000:00:1d.1: reg 20 io port: [0x6f60-0x6f7f]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232098] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232178] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232249] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Feb 11 10:52:19 ryan-laptop kernel: [    0.232255] pci 0000:00:1d.7: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.232442] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Feb 11 10:52:19 ryan-laptop kernel: [    0.232446] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
Feb 11 10:52:19 ryan-laptop kernel: [    0.232451] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
Feb 11 10:52:19 ryan-laptop kernel: [    0.232458] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
Feb 11 10:52:19 ryan-laptop kernel: [    0.232518] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232526] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232535] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232544] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232553] pci 0000:00:1f.1: reg 20 io port: [0x6fa0-0x6faf]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232616] pci 0000:00:1f.2: reg 10 io port: [0x6eb0-0x6eb7]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232625] pci 0000:00:1f.2: reg 14 io port: [0x6eb8-0x6ebb]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232634] pci 0000:00:1f.2: reg 18 io port: [0x6ec0-0x6ec7]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232642] pci 0000:00:1f.2: reg 1c io port: [0x6ec8-0x6ecb]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232651] pci 0000:00:1f.2: reg 20 io port: [0x6ee0-0x6eef]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232660] pci 0000:00:1f.2: reg 24 io port: [0xeff0-0xefff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232694] pci 0000:00:1f.2: PME# supported from D3hot
Feb 11 10:52:19 ryan-laptop kernel: [    0.232699] pci 0000:00:1f.2: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.232729] pci 0000:00:1f.3: reg 10 32bit mmio: [0xf6dfbf00-0xf6dfbfff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.232757] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
Feb 11 10:52:19 ryan-laptop kernel: [    0.233053] pci 0000:0c:00.0: reg 10 32bit mmio: [0xf6cff000-0xf6cfffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.233305] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
Feb 11 10:52:19 ryan-laptop kernel: [    0.233318] pci 0000:0c:00.0: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.233443] pci 0000:00:1c.1: bridge 32bit mmio: [0xf6c00000-0xf6cfffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.233583] pci 0000:09:00.0: reg 10 64bit mmio: [0xf6bf0000-0xf6bfffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.233698] pci 0000:09:00.0: PME# supported from D3hot D3cold
Feb 11 10:52:19 ryan-laptop kernel: [    0.233705] pci 0000:09:00.0: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.233792] pci 0000:00:1c.5: bridge 32bit mmio: [0xf6b00000-0xf6bfffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.233856] pci 0000:03:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.233887] pci 0000:03:01.0: supports D1 D2
Feb 11 10:52:19 ryan-laptop kernel: [    0.233889] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 11 10:52:19 ryan-laptop kernel: [    0.233894] pci 0000:03:01.0: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.233947] pci 0000:03:01.4: reg 10 32bit mmio: [0xf6aff000-0xf6afffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.233956] pci 0000:03:01.4: reg 14 32bit mmio: [0xf6afe800-0xf6afefff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.234014] pci 0000:03:01.4: supports D1 D2
Feb 11 10:52:19 ryan-laptop kernel: [    0.234016] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
Feb 11 10:52:19 ryan-laptop kernel: [    0.234021] pci 0000:03:01.4: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.234096] pci 0000:00:1e.0: transparent bridge
Feb 11 10:52:19 ryan-laptop kernel: [    0.234104] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6a00000-0xf6afffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.234163] pci_bus 0000:00: on NUMA node 0
Feb 11 10:52:19 ryan-laptop kernel: [    0.234168] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb 11 10:52:19 ryan-laptop kernel: [    0.234429] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Feb 11 10:52:19 ryan-laptop kernel: [    0.234569] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Feb 11 10:52:19 ryan-laptop kernel: [    0.234645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Feb 11 10:52:19 ryan-laptop kernel: [    0.234728] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Feb 11 10:52:19 ryan-laptop kernel: [    0.252938] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Feb 11 10:52:19 ryan-laptop kernel: [    0.253065] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *3
Feb 11 10:52:19 ryan-laptop kernel: [    0.253189] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 *10 11)
Feb 11 10:52:19 ryan-laptop kernel: [    0.253311] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Feb 11 10:52:19 ryan-laptop kernel: [    0.253434] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Feb 11 10:52:19 ryan-laptop kernel: [    0.253560] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Feb 11 10:52:19 ryan-laptop kernel: [    0.253686] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Feb 11 10:52:19 ryan-laptop kernel: [    0.253797] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 11 10:52:19 ryan-laptop kernel: [    0.253997] SCSI subsystem initialized
Feb 11 10:52:19 ryan-laptop kernel: [    0.254048] libata version 3.00 loaded.
Feb 11 10:52:19 ryan-laptop kernel: [    0.254119] usbcore: registered new interface driver usbfs
Feb 11 10:52:19 ryan-laptop kernel: [    0.254134] usbcore: registered new interface driver hub
Feb 11 10:52:19 ryan-laptop kernel: [    0.254156] usbcore: registered new device driver usb
Feb 11 10:52:19 ryan-laptop kernel: [    0.254286] ACPI: WMI: Mapper loaded
Feb 11 10:52:19 ryan-laptop kernel: [    0.254288] PCI: Using ACPI for IRQ routing
Feb 11 10:52:19 ryan-laptop kernel: [    0.254626] Bluetooth: Core ver 2.15
Feb 11 10:52:19 ryan-laptop kernel: [    0.254653] NET: Registered protocol family 31
Feb 11 10:52:19 ryan-laptop kernel: [    0.254655] Bluetooth: HCI device and connection manager initialized
Feb 11 10:52:19 ryan-laptop kernel: [    0.254657] Bluetooth: HCI socket layer initialized
Feb 11 10:52:19 ryan-laptop kernel: [    0.254659] NetLabel: Initializing
Feb 11 10:52:19 ryan-laptop kernel: [    0.254661] NetLabel:  domain hash size = 128
Feb 11 10:52:19 ryan-laptop kernel: [    0.254662] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 11 10:52:19 ryan-laptop kernel: [    0.254675] NetLabel:  unlabeled traffic allowed by default
Feb 11 10:52:19 ryan-laptop kernel: [    0.254703] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Feb 11 10:52:19 ryan-laptop kernel: [    0.254708] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Feb 11 10:52:19 ryan-laptop kernel: [    0.261417] pnp: PnP ACPI init
Feb 11 10:52:19 ryan-laptop kernel: [    0.261443] ACPI: bus type pnp registered
Feb 11 10:52:19 ryan-laptop kernel: [    0.305247] pnp 00:0b: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:52:19 ryan-laptop kernel: [    0.305251] pnp 00:0b: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:52:19 ryan-laptop kernel: [    0.305336] pnp 00:0c: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:52:19 ryan-laptop kernel: [    0.305340] pnp 00:0c: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:52:19 ryan-laptop kernel: [    0.305343] pnp 00:0c: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:52:19 ryan-laptop kernel: [    0.305347] pnp 00:0c: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:52:19 ryan-laptop kernel: [    0.326817] pnp: PnP ACPI: found 14 devices
Feb 11 10:52:19 ryan-laptop kernel: [    0.326820] ACPI: ACPI bus type pnp unregistered
Feb 11 10:52:19 ryan-laptop kernel: [    0.326824] PnPBIOS: Disabled by ACPI PNP
Feb 11 10:52:19 ryan-laptop kernel: [    0.326837] system 00:05: ioport range 0xc80-0xcaf has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326840] system 00:05: ioport range 0xcc0-0xcff could not be reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326847] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326853] system 00:0a: ioport range 0xcb0-0xcbb has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326856] system 00:0a: iomem range 0xfed40000-0xfed44fff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326861] system 00:0b: ioport range 0x900-0x97f has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326864] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326869] system 00:0c: ioport range 0xf400-0xf4fe has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326872] system 00:0c: ioport range 0x1080-0x10bf has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326875] system 00:0c: ioport range 0x10c0-0x10df has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326877] system 00:0c: ioport range 0x809-0x809 has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326883] system 00:0d: iomem range 0x0-0x9efff could not be reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326885] system 00:0d: iomem range 0x9f000-0x9ffff could not be reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326888] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326891] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326894] system 00:0d: iomem range 0x100000-0x3f6bf3ff could not be reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326897] system 00:0d: iomem range 0x3f6bf400-0x3f6fffff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326899] system 00:0d: iomem range 0x3f700000-0x3f7fffff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326902] system 00:0d: iomem range 0x3f700000-0x3fefffff could not be reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326905] system 00:0d: iomem range 0xffe00000-0xffffffff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326908] system 00:0d: iomem range 0xffa00000-0xffbfffff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326911] system 00:0d: iomem range 0xfec00000-0xfec0ffff could not be reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326913] system 00:0d: iomem range 0xfee00000-0xfee0ffff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326916] system 00:0d: iomem range 0xfed20000-0xfed3ffff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326919] system 00:0d: iomem range 0xfed45000-0xfed8ffff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326922] system 00:0d: iomem range 0xfeda0000-0xfeda3fff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326925] system 00:0d: iomem range 0xfeda4000-0xfeda4fff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326927] system 00:0d: iomem range 0xfeda5000-0xfeda5fff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326930] system 00:0d: iomem range 0xfeda6000-0xfeda6fff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326933] system 00:0d: iomem range 0xfed18000-0xfed1bfff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.326936] system 00:0d: iomem range 0xf8000000-0xfbffffff has been reserved
Feb 11 10:52:19 ryan-laptop kernel: [    0.361599] AppArmor: AppArmor Filesystem Enabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.361669] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
Feb 11 10:52:19 ryan-laptop kernel: [    0.361671] pci 0000:00:1c.0:   IO window: disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.361677] pci 0000:00:1c.0:   MEM window: disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.361682] pci 0000:00:1c.0:   PREFETCH window: disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.361688] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
Feb 11 10:52:19 ryan-laptop kernel: [    0.361690] pci 0000:00:1c.1:   IO window: disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.361697] pci 0000:00:1c.1:   MEM window: 0xf6c00000-0xf6cfffff
Feb 11 10:52:19 ryan-laptop kernel: [    0.361702] pci 0000:00:1c.1:   PREFETCH window: disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.361707] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
Feb 11 10:52:19 ryan-laptop kernel: [    0.361709] pci 0000:00:1c.5:   IO window: disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.361715] pci 0000:00:1c.5:   MEM window: 0xf6b00000-0xf6bfffff
Feb 11 10:52:19 ryan-laptop kernel: [    0.361721] pci 0000:00:1c.5:   PREFETCH window: disabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.361733] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
Feb 11 10:52:19 ryan-laptop kernel: [    0.361735] pci 0000:03:01.0:   IO window: 0x002000-0x0020ff
Feb 11 10:52:19 ryan-laptop kernel: [    0.361741] pci 0000:03:01.0:   IO window: 0x002400-0x0024ff
Feb 11 10:52:19 ryan-laptop kernel: [    0.361747] pci 0000:03:01.0:   PREFETCH window: 0x40000000-0x43ffffff
Feb 11 10:52:19 ryan-laptop kernel: [    0.361753] pci 0000:03:01.0:   MEM window: 0x44000000-0x47ffffff
Feb 11 10:52:19 ryan-laptop kernel: [    0.361759] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Feb 11 10:52:19 ryan-laptop kernel: [    0.361763] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
Feb 11 10:52:19 ryan-laptop kernel: [    0.361770] pci 0000:00:1e.0:   MEM window: 0xf6a00000-0xf6afffff
Feb 11 10:52:19 ryan-laptop kernel: [    0.361775] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x43ffffff
Feb 11 10:52:19 ryan-laptop kernel: [    0.361793]   alloc irq_desc for 16 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.361795]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.361801] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 11 10:52:19 ryan-laptop kernel: [    0.361808] pci 0000:00:1c.0: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    0.361817]   alloc irq_desc for 17 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.361819]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.361822] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb 11 10:52:19 ryan-laptop kernel: [    0.361827] pci 0000:00:1c.1: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    0.361836] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb 11 10:52:19 ryan-laptop kernel: [    0.361842] pci 0000:00:1c.5: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    0.361851] pci 0000:00:1e.0: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    0.361861] pci 0000:03:01.0: enabling device (0000 -> 0003)
Feb 11 10:52:19 ryan-laptop kernel: [    0.361865]   alloc irq_desc for 19 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.361867]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.361870] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb 11 10:52:19 ryan-laptop kernel: [    0.361881] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361883] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361886] pci_bus 0000:0c: resource 1 mem: [0xf6c00000-0xf6cfffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361888] pci_bus 0000:09: resource 1 mem: [0xf6b00000-0xf6bfffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361891] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361893] pci_bus 0000:03: resource 1 mem: [0xf6a00000-0xf6afffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361896] pci_bus 0000:03: resource 2 pref mem [0x40000000-0x43ffffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361898] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361900] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361903] pci_bus 0000:04: resource 0 io:  [0x2000-0x20ff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361905] pci_bus 0000:04: resource 1 io:  [0x2400-0x24ff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361907] pci_bus 0000:04: resource 2 pref mem [0x40000000-0x43ffffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361910] pci_bus 0000:04: resource 3 mem: [0x44000000-0x47ffffff]
Feb 11 10:52:19 ryan-laptop kernel: [    0.361945] NET: Registered protocol family 2
Feb 11 10:52:19 ryan-laptop kernel: [    0.362040] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb 11 10:52:19 ryan-laptop kernel: [    0.362327] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Feb 11 10:52:19 ryan-laptop kernel: [    0.362869] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb 11 10:52:19 ryan-laptop kernel: [    0.363227] TCP: Hash tables configured (established 131072 bind 65536)
Feb 11 10:52:19 ryan-laptop kernel: [    0.363230] TCP reno registered
Feb 11 10:52:19 ryan-laptop kernel: [    0.363355] NET: Registered protocol family 1
Feb 11 10:52:19 ryan-laptop kernel: [    0.363429] Trying to unpack rootfs image as initramfs...
Feb 11 10:52:19 ryan-laptop kernel: [    0.503991] Switched to high resolution mode on CPU 0
Feb 11 10:52:19 ryan-laptop kernel: [    0.550093] Freeing initrd memory: 7463k freed
Feb 11 10:52:19 ryan-laptop kernel: [    0.555108] cpufreq-nforce2: No nForce2 chipset.
Feb 11 10:52:19 ryan-laptop kernel: [    0.555139] Scanning for low memory corruption every 60 seconds
Feb 11 10:52:19 ryan-laptop kernel: [    0.555252] audit: initializing netlink socket (disabled)
Feb 11 10:52:19 ryan-laptop kernel: [    0.555272] type=2000 audit(1265885526.552:1): initialized
Feb 11 10:52:19 ryan-laptop kernel: [    0.563903] highmem bounce pool size: 64 pages
Feb 11 10:52:19 ryan-laptop kernel: [    0.563909] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Feb 11 10:52:19 ryan-laptop kernel: [    0.565145] VFS: Disk quotas dquot_6.5.2
Feb 11 10:52:19 ryan-laptop kernel: [    0.565198] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb 11 10:52:19 ryan-laptop kernel: [    0.565679] fuse init (API version 7.12)
Feb 11 10:52:19 ryan-laptop kernel: [    0.565756] msgmni has been set to 1732
Feb 11 10:52:19 ryan-laptop kernel: [    0.565927] alg: No test for stdrng (krng)
Feb 11 10:52:19 ryan-laptop kernel: [    0.565938] io scheduler noop registered
Feb 11 10:52:19 ryan-laptop kernel: [    0.565940] io scheduler anticipatory registered
Feb 11 10:52:19 ryan-laptop kernel: [    0.565942] io scheduler deadline registered
Feb 11 10:52:19 ryan-laptop kernel: [    0.565980] io scheduler cfq registered (default)
Feb 11 10:52:19 ryan-laptop kernel: [    0.565994] pci 0000:00:02.0: Boot video device
Feb 11 10:52:19 ryan-laptop kernel: [    0.566268]   alloc irq_desc for 24 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.566270]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.566283] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
Feb 11 10:52:19 ryan-laptop kernel: [    0.566296] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    0.566460]   alloc irq_desc for 25 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.566462]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.566472] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
Feb 11 10:52:19 ryan-laptop kernel: [    0.566484] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    0.566644]   alloc irq_desc for 26 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.566646]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.566655] pcieport-driver 0000:00:1c.5: irq 26 for MSI/MSI-X
Feb 11 10:52:19 ryan-laptop kernel: [    0.566667] pcieport-driver 0000:00:1c.5: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    0.566768] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 11 10:52:19 ryan-laptop kernel: [    0.566856] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 11 10:52:19 ryan-laptop kernel: [    0.567004] ACPI: AC Adapter [AC] (on-line)
Feb 11 10:52:19 ryan-laptop kernel: [    0.567078] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Feb 11 10:52:19 ryan-laptop kernel: [    0.567604] ACPI: Lid Switch [LID]
Feb 11 10:52:19 ryan-laptop kernel: [    0.567645] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Feb 11 10:52:19 ryan-laptop kernel: [    0.567652] ACPI: Power Button [PBTN]
Feb 11 10:52:19 ryan-laptop kernel: [    0.567690] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Feb 11 10:52:19 ryan-laptop kernel: [    0.567693] ACPI: Sleep Button [SBTN]
Feb 11 10:52:19 ryan-laptop kernel: [    0.568410] Monitor-Mwait will be used to enter C-1 state
Feb 11 10:52:19 ryan-laptop kernel: [    0.568434] Monitor-Mwait will be used to enter C-2 state
Feb 11 10:52:19 ryan-laptop kernel: [    0.568452] Monitor-Mwait will be used to enter C-3 state
Feb 11 10:52:19 ryan-laptop kernel: [    0.568459] Marking TSC unstable due to TSC halts in idle
Feb 11 10:52:19 ryan-laptop kernel: [    0.568480] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Feb 11 10:52:19 ryan-laptop kernel: [    0.568504] processor LNXCPU:00: registered as cooling_device0
Feb 11 10:52:19 ryan-laptop kernel: [    0.568508] ACPI: Processor [CPU0] (supports 8 throttling states)
Feb 11 10:52:19 ryan-laptop kernel: [    0.597063] thermal LNXTHERM:01: registered as thermal_zone0
Feb 11 10:52:19 ryan-laptop kernel: [    0.597071] ACPI: Thermal Zone [THM] (60 C)
Feb 11 10:52:19 ryan-laptop kernel: [    0.597118] isapnp: Scanning for PnP cards...
Feb 11 10:52:19 ryan-laptop kernel: [    0.631030] ACPI: Battery Slot [BAT0] (battery present)
Feb 11 10:52:19 ryan-laptop kernel: [    0.631078] ACPI: Battery Slot [BAT1] (battery absent)
Feb 11 10:52:19 ryan-laptop kernel: [    0.982870] isapnp: No Plug & Play device found
Feb 11 10:52:19 ryan-laptop kernel: [    0.983862] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Feb 11 10:52:19 ryan-laptop kernel: [    0.984016] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 11 10:52:19 ryan-laptop kernel: [    0.984458] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 11 10:52:19 ryan-laptop kernel: [    0.985344] brd: module loaded
Feb 11 10:52:19 ryan-laptop kernel: [    0.985723] loop: module loaded
Feb 11 10:52:19 ryan-laptop kernel: [    0.985797] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Feb 11 10:52:19 ryan-laptop kernel: [    0.985896] ata_piix 0000:00:1f.1: version 2.13
Feb 11 10:52:19 ryan-laptop kernel: [    0.985910] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 11 10:52:19 ryan-laptop kernel: [    0.985952] ata_piix 0000:00:1f.1: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    0.986043] scsi0 : ata_piix
Feb 11 10:52:19 ryan-laptop kernel: [    0.986123] scsi1 : ata_piix
Feb 11 10:52:19 ryan-laptop kernel: [    0.988328] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
Feb 11 10:52:19 ryan-laptop kernel: [    0.988331] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
Feb 11 10:52:19 ryan-laptop kernel: [    0.988529] ata2: port disabled. ignoring.
Feb 11 10:52:19 ryan-laptop kernel: [    0.988552]   alloc irq_desc for 18 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.988555]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    0.988561] ata_piix 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb 11 10:52:19 ryan-laptop kernel: [    0.988567] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Feb 11 10:52:19 ryan-laptop kernel: [    1.144261] ata_piix 0000:00:1f.2: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    1.144317] scsi2 : ata_piix
Feb 11 10:52:19 ryan-laptop kernel: [    1.144369] scsi3 : ata_piix
Feb 11 10:52:19 ryan-laptop kernel: [    1.146521] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 18
Feb 11 10:52:19 ryan-laptop kernel: [    1.146529] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 18
Feb 11 10:52:19 ryan-laptop kernel: [    1.147301] Fixed MDIO Bus: probed
Feb 11 10:52:19 ryan-laptop kernel: [    1.147333] PPP generic driver version 2.4.2
Feb 11 10:52:19 ryan-laptop kernel: [    1.147417] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 11 10:52:19 ryan-laptop kernel: [    1.147439]   alloc irq_desc for 22 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    1.147441]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    1.147447] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Feb 11 10:52:19 ryan-laptop kernel: [    1.147464] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    1.147468] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Feb 11 10:52:19 ryan-laptop kernel: [    1.147522] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Feb 11 10:52:19 ryan-laptop kernel: [    1.151431] ehci_hcd 0000:00:1a.7: debug port 1
Feb 11 10:52:19 ryan-laptop kernel: [    1.151438] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Feb 11 10:52:19 ryan-laptop kernel: [    1.151451] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
Feb 11 10:52:19 ryan-laptop kernel: [    1.155732] ata1.00: ATAPI: TEAC CD-ROM CD-224E-N, D.AB, max UDMA/33
Feb 11 10:52:19 ryan-laptop kernel: [    1.164014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Feb 11 10:52:19 ryan-laptop kernel: [    1.164079] usb usb1: configuration #1 chosen from 1 choice
Feb 11 10:52:19 ryan-laptop kernel: [    1.164106] hub 1-0:1.0: USB hub found
Feb 11 10:52:19 ryan-laptop kernel: [    1.164114] hub 1-0:1.0: 4 ports detected
Feb 11 10:52:19 ryan-laptop kernel: [    1.164166]   alloc irq_desc for 20 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    1.164168]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    1.164173] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb 11 10:52:19 ryan-laptop kernel: [    1.164185] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    1.164188] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb 11 10:52:19 ryan-laptop kernel: [    1.164219] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Feb 11 10:52:19 ryan-laptop kernel: [    1.168127] ehci_hcd 0000:00:1d.7: debug port 1
Feb 11 10:52:19 ryan-laptop kernel: [    1.168134] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Feb 11 10:52:19 ryan-laptop kernel: [    1.168149] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
Feb 11 10:52:19 ryan-laptop kernel: [    1.172324] ata1.00: configured for UDMA/33
Feb 11 10:52:19 ryan-laptop kernel: [    1.177071] scsi 0:0:0:0: CD-ROM            TEAC     CD-ROM CD-224E-N D.AB PQ: 0 ANSI: 5
Feb 11 10:52:19 ryan-laptop kernel: [    1.183163] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
Feb 11 10:52:19 ryan-laptop kernel: [    1.183167] Uniform CD-ROM driver Revision: 3.20
Feb 11 10:52:19 ryan-laptop kernel: [    1.183242] sr 0:0:0:0: Attached scsi CD-ROM sr0
Feb 11 10:52:19 ryan-laptop kernel: [    1.183281] sr 0:0:0:0: Attached scsi generic sg0 type 5
Feb 11 10:52:19 ryan-laptop kernel: [    1.184015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Feb 11 10:52:19 ryan-laptop kernel: [    1.184085] usb usb2: configuration #1 chosen from 1 choice
Feb 11 10:52:19 ryan-laptop kernel: [    1.184109] hub 2-0:1.0: USB hub found
Feb 11 10:52:19 ryan-laptop kernel: [    1.184116] hub 2-0:1.0: 6 ports detected
Feb 11 10:52:19 ryan-laptop kernel: [    1.184177] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 11 10:52:19 ryan-laptop kernel: [    1.184197] uhci_hcd: USB Universal Host Controller Interface driver
Feb 11 10:52:19 ryan-laptop kernel: [    1.184222] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb 11 10:52:19 ryan-laptop kernel: [    1.184231] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    1.184234] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Feb 11 10:52:19 ryan-laptop kernel: [    1.184266] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Feb 11 10:52:19 ryan-laptop kernel: [    1.184296] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
Feb 11 10:52:19 ryan-laptop kernel: [    1.184366] usb usb3: configuration #1 chosen from 1 choice
Feb 11 10:52:19 ryan-laptop kernel: [    1.184389] hub 3-0:1.0: USB hub found
Feb 11 10:52:19 ryan-laptop kernel: [    1.184396] hub 3-0:1.0: 2 ports detected
Feb 11 10:52:19 ryan-laptop kernel: [    1.184441]   alloc irq_desc for 21 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    1.184443]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    1.184448] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Feb 11 10:52:19 ryan-laptop kernel: [    1.184455] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    1.184459] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Feb 11 10:52:19 ryan-laptop kernel: [    1.184488] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Feb 11 10:52:19 ryan-laptop kernel: [    1.184525] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
Feb 11 10:52:19 ryan-laptop kernel: [    1.184594] usb usb4: configuration #1 chosen from 1 choice
Feb 11 10:52:19 ryan-laptop kernel: [    1.184617] hub 4-0:1.0: USB hub found
Feb 11 10:52:19 ryan-laptop kernel: [    1.184623] hub 4-0:1.0: 2 ports detected
Feb 11 10:52:19 ryan-laptop kernel: [    1.184667] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb 11 10:52:19 ryan-laptop kernel: [    1.184674] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    1.184678] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb 11 10:52:19 ryan-laptop kernel: [    1.184711] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Feb 11 10:52:19 ryan-laptop kernel: [    1.184739] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
Feb 11 10:52:19 ryan-laptop kernel: [    1.184810] usb usb5: configuration #1 chosen from 1 choice
Feb 11 10:52:19 ryan-laptop kernel: [    1.184833] hub 5-0:1.0: USB hub found
Feb 11 10:52:19 ryan-laptop kernel: [    1.184839] hub 5-0:1.0: 2 ports detected
Feb 11 10:52:19 ryan-laptop kernel: [    1.184881] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Feb 11 10:52:19 ryan-laptop kernel: [    1.184888] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    1.184891] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb 11 10:52:19 ryan-laptop kernel: [    1.184921] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Feb 11 10:52:19 ryan-laptop kernel: [    1.184950] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
Feb 11 10:52:19 ryan-laptop kernel: [    1.185019] usb usb6: configuration #1 chosen from 1 choice
Feb 11 10:52:19 ryan-laptop kernel: [    1.185044] hub 6-0:1.0: USB hub found
Feb 11 10:52:19 ryan-laptop kernel: [    1.185050] hub 6-0:1.0: 2 ports detected
Feb 11 10:52:19 ryan-laptop kernel: [    1.185090] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Feb 11 10:52:19 ryan-laptop kernel: [    1.185097] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    1.185100] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb 11 10:52:19 ryan-laptop kernel: [    1.185125] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Feb 11 10:52:19 ryan-laptop kernel: [    1.185153] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
Feb 11 10:52:19 ryan-laptop kernel: [    1.185224] usb usb7: configuration #1 chosen from 1 choice
Feb 11 10:52:19 ryan-laptop kernel: [    1.185248] hub 7-0:1.0: USB hub found
Feb 11 10:52:19 ryan-laptop kernel: [    1.185254] hub 7-0:1.0: 2 ports detected
Feb 11 10:52:19 ryan-laptop kernel: [    1.185346] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb 11 10:52:19 ryan-laptop kernel: [    1.189002] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 11 10:52:19 ryan-laptop kernel: [    1.189007] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 11 10:52:19 ryan-laptop kernel: [    1.189060] mice: PS/2 mouse device common for all mice
Feb 11 10:52:19 ryan-laptop kernel: [    1.189160] rtc_cmos 00:03: RTC can wake from S4
Feb 11 10:52:19 ryan-laptop kernel: [    1.189189] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Feb 11 10:52:19 ryan-laptop kernel: [    1.189222] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Feb 11 10:52:19 ryan-laptop kernel: [    1.189316] device-mapper: uevent: version 1.0.3
Feb 11 10:52:19 ryan-laptop kernel: [    1.189405] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Feb 11 10:52:19 ryan-laptop kernel: [    1.189477] device-mapper: multipath: version 1.1.0 loaded
Feb 11 10:52:19 ryan-laptop kernel: [    1.189480] device-mapper: multipath round-robin: version 1.0.0 loaded
Feb 11 10:52:19 ryan-laptop kernel: [    1.189585] EISA: Probing bus 0 at eisa.0
Feb 11 10:52:19 ryan-laptop kernel: [    1.189588] EISA: Cannot allocate resource for mainboard
Feb 11 10:52:19 ryan-laptop kernel: [    1.189590] Cannot allocate resource for EISA slot 1
Feb 11 10:52:19 ryan-laptop kernel: [    1.189592] Cannot allocate resource for EISA slot 2
Feb 11 10:52:19 ryan-laptop kernel: [    1.189618] EISA: Detected 0 cards.
Feb 11 10:52:19 ryan-laptop kernel: [    1.189705] cpuidle: using governor ladder
Feb 11 10:52:19 ryan-laptop kernel: [    1.189758] cpuidle: using governor menu
Feb 11 10:52:19 ryan-laptop kernel: [    1.190176] TCP cubic registered
Feb 11 10:52:19 ryan-laptop kernel: [    1.190308] NET: Registered protocol family 10
Feb 11 10:52:19 ryan-laptop kernel: [    1.190659] lo: Disabled Privacy Extensions
Feb 11 10:52:19 ryan-laptop kernel: [    1.190911] NET: Registered protocol family 17
Feb 11 10:52:19 ryan-laptop kernel: [    1.190929] Bluetooth: L2CAP ver 2.13
Feb 11 10:52:19 ryan-laptop kernel: [    1.190930] Bluetooth: L2CAP socket layer initialized
Feb 11 10:52:19 ryan-laptop kernel: [    1.190933] Bluetooth: SCO (Voice Link) ver 0.6
Feb 11 10:52:19 ryan-laptop kernel: [    1.190934] Bluetooth: SCO socket layer initialized
Feb 11 10:52:19 ryan-laptop kernel: [    1.190969] Bluetooth: RFCOMM TTY layer initialized
Feb 11 10:52:19 ryan-laptop kernel: [    1.190972] Bluetooth: RFCOMM socket layer initialized
Feb 11 10:52:19 ryan-laptop kernel: [    1.190974] Bluetooth: RFCOMM ver 1.11
Feb 11 10:52:19 ryan-laptop kernel: [    1.191003] Using IPI No-Shortcut mode
Feb 11 10:52:19 ryan-laptop kernel: [    1.191060] PM: Resume from disk failed.
Feb 11 10:52:19 ryan-laptop kernel: [    1.191072] registered taskstats version 1
Feb 11 10:52:19 ryan-laptop kernel: [    1.191187]   Magic number: 14:199:881
Feb 11 10:52:19 ryan-laptop kernel: [    1.191281] rtc_cmos 00:03: setting system clock to 2010-02-11 10:52:07 UTC (1265885527)
Feb 11 10:52:19 ryan-laptop kernel: [    1.191284] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 11 10:52:19 ryan-laptop kernel: [    1.191286] EDD information not available.
Feb 11 10:52:19 ryan-laptop kernel: [    1.192332] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Feb 11 10:52:19 ryan-laptop kernel: [    1.500045] Clocksource tsc unstable (delta = -302107514 ns)
Feb 11 10:52:19 ryan-laptop kernel: [    1.680030] usb 5-2: new low speed USB device using uhci_hcd and address 2
Feb 11 10:52:19 ryan-laptop kernel: [    1.792090] ata4.00: SATA link down (SStatus 0 SControl 300)
Feb 11 10:52:19 ryan-laptop kernel: [    1.792114] ata4.01: SATA link down (SStatus 0 SControl 0)
Feb 11 10:52:19 ryan-laptop kernel: [    1.855864] usb 5-2: configuration #1 chosen from 1 choice
Feb 11 10:52:19 ryan-laptop kernel: [    1.940119] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 11 10:52:19 ryan-laptop kernel: [    1.940138] ata3.01: SATA link down (SStatus 0 SControl 300)
Feb 11 10:52:19 ryan-laptop kernel: [    2.024998] ata3.00: ATA-8: ST980411ASG, DE14, max UDMA/133
Feb 11 10:52:19 ryan-laptop kernel: [    2.025001] ata3.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
Feb 11 10:52:19 ryan-laptop kernel: [    2.084949] ata3.00: configured for UDMA/133
Feb 11 10:52:19 ryan-laptop kernel: [    2.085062] scsi 2:0:0:0: Direct-Access     ATA      ST980411ASG      DE14 PQ: 0 ANSI: 5
Feb 11 10:52:19 ryan-laptop kernel: [    2.085174] sd 2:0:0:0: Attached scsi generic sg1 type 0
Feb 11 10:52:19 ryan-laptop kernel: [    2.085211] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Feb 11 10:52:19 ryan-laptop kernel: [    2.085252] sd 2:0:0:0: [sda] Write Protect is off
Feb 11 10:52:19 ryan-laptop kernel: [    2.085255] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 11 10:52:19 ryan-laptop kernel: [    2.085276] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 11 10:52:19 ryan-laptop kernel: [    2.085388]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 sda10 >
Feb 11 10:52:19 ryan-laptop kernel: [    2.174887] sd 2:0:0:0: [sda] Attached SCSI disk
Feb 11 10:52:19 ryan-laptop kernel: [    2.174902] Freeing unused kernel memory: 540k freed
Feb 11 10:52:19 ryan-laptop kernel: [    2.175173] Write protecting the kernel text: 4568k
Feb 11 10:52:19 ryan-laptop kernel: [    2.175199] Write protecting the kernel read-only data: 1836k
Feb 11 10:52:19 ryan-laptop kernel: [    2.334067] Linux agpgart interface v0.103
Feb 11 10:52:19 ryan-laptop kernel: [    2.388346] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Feb 11 10:52:19 ryan-laptop kernel: [    2.388596] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Feb 11 10:52:19 ryan-laptop kernel: [    2.391220] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Feb 11 10:52:19 ryan-laptop kernel: [    2.469077] [drm] Initialized drm 1.1.0 20060810
Feb 11 10:52:19 ryan-laptop kernel: [    2.498487] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 11 10:52:19 ryan-laptop kernel: [    2.498493] i915 0000:00:02.0: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    2.500534]   alloc irq_desc for 27 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    2.500538]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    2.500548] i915 0000:00:02.0: irq 27 for MSI/MSI-X
Feb 11 10:52:19 ryan-laptop kernel: [    2.606282] tg3.c:v3.99 (April 20, 2009)
Feb 11 10:52:19 ryan-laptop kernel: [    2.606340] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 11 10:52:19 ryan-laptop kernel: [    2.606350] tg3 0000:09:00.0: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    2.610035] usbcore: registered new interface driver hiddev
Feb 11 10:52:19 ryan-laptop kernel: [    2.620047] tg3 0000:09:00.0: PME# disabled
Feb 11 10:52:19 ryan-laptop kernel: [    2.623182] ohci1394 0000:03:01.4: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb 11 10:52:19 ryan-laptop kernel: [    2.624070] integrated sync not supported
Feb 11 10:52:19 ryan-laptop kernel: [    2.635809] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input5
Feb 11 10:52:19 ryan-laptop kernel: [    2.635882] generic-usb 0003:413C:3012.0001: input,hidraw0: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1d.0-2/input0
Feb 11 10:52:19 ryan-laptop kernel: [    2.635899] usbcore: registered new interface driver usbhid
Feb 11 10:52:19 ryan-laptop kernel: [    2.635902] usbhid: v2.6:USB HID core driver
Feb 11 10:52:19 ryan-laptop kernel: [    2.641749] eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:21:70:90:ca:82
Feb 11 10:52:19 ryan-laptop kernel: [    2.641753] eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1])
Feb 11 10:52:19 ryan-laptop kernel: [    2.641756] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Feb 11 10:52:19 ryan-laptop kernel: [    2.641758] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Feb 11 10:52:19 ryan-laptop kernel: [    2.683715] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f6aff000-f6aff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Feb 11 10:52:19 ryan-laptop kernel: [    3.098534] integrated sync not supported
Feb 11 10:52:19 ryan-laptop kernel: [    3.393028] [drm] TV-16: set mode NTSC 480i 0
Feb 11 10:52:19 ryan-laptop kernel: [    3.535033] [drm] fb0: inteldrmfb frame buffer device
Feb 11 10:52:19 ryan-laptop kernel: [    3.549806] acpi device:3a: registered as cooling_device1
Feb 11 10:52:19 ryan-laptop kernel: [    3.550614] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:37/input/input6
Feb 11 10:52:19 ryan-laptop kernel: [    3.550650] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Feb 11 10:52:19 ryan-laptop kernel: [    3.550789] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
Feb 11 10:52:19 ryan-laptop kernel: [    3.550857] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:3c/input/input7
Feb 11 10:52:19 ryan-laptop kernel: [    3.550879] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Feb 11 10:52:19 ryan-laptop kernel: [    3.550898] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Feb 11 10:52:19 ryan-laptop kernel: [    3.640628] [drm] TV-16: set mode 848x480 1d
Feb 11 10:52:19 ryan-laptop kernel: [    3.747437] [drm] LVDS-8: set mode 1024x768 1e
Feb 11 10:52:19 ryan-laptop kernel: [    3.982656] Console: switching to colour frame buffer device 106x30
Feb 11 10:52:19 ryan-laptop kernel: [    4.248118] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[374fc0000ef2dde1]
Feb 11 10:52:19 ryan-laptop kernel: [    4.287975] PM: Starting manual resume from disk
Feb 11 10:52:19 ryan-laptop kernel: [    4.287979] PM: Resume from partition 8:3
Feb 11 10:52:19 ryan-laptop kernel: [    4.287981] PM: Checking hibernation image.
Feb 11 10:52:19 ryan-laptop kernel: [    4.288266] PM: Resume from disk failed.
Feb 11 10:52:19 ryan-laptop kernel: [    4.291259] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
Feb 11 10:52:19 ryan-laptop kernel: [    4.291263] EXT4-fs (sda2): write access will be enabled during recovery
Feb 11 10:52:19 ryan-laptop kernel: [    4.343721] EXT4-fs (sda2): barriers enabled
Feb 11 10:52:19 ryan-laptop kernel: [    4.360236] kjournald2 starting: pid 362, dev sda2:8, commit interval 5 seconds
Feb 11 10:52:19 ryan-laptop kernel: [    4.360249] EXT4-fs (sda2): delayed allocation enabled
Feb 11 10:52:19 ryan-laptop kernel: [    4.360253] EXT4-fs: file extents enabled
Feb 11 10:52:19 ryan-laptop kernel: [    4.360348] EXT4-fs: mballoc enabled
Feb 11 10:52:19 ryan-laptop kernel: [    4.360361] EXT4-fs (sda2): recovery complete
Feb 11 10:52:19 ryan-laptop kernel: [    4.361505] EXT4-fs (sda2): mounted filesystem with ordered data mode
Feb 11 10:52:19 ryan-laptop kernel: [    4.873794] type=1505 audit(1265885531.180:2): operation="profile_load" pid=385 name=/usr/share/gdm/guest-session/Xsession
Feb 11 10:52:19 ryan-laptop kernel: [    4.877116] type=1505 audit(1265885531.184:3): operation="profile_load" pid=386 name=/sbin/dhclient3
Feb 11 10:52:19 ryan-laptop kernel: [    4.877851] type=1505 audit(1265885531.184:4): operation="profile_load" pid=386 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb 11 10:52:19 ryan-laptop kernel: [    4.878250] type=1505 audit(1265885531.184:5): operation="profile_load" pid=386 name=/usr/lib/connman/scripts/dhclient-script
Feb 11 10:52:19 ryan-laptop kernel: [    4.902575] type=1505 audit(1265885531.208:6): operation="profile_load" pid=387 name=/usr/bin/evince
Feb 11 10:52:19 ryan-laptop kernel: [    4.914648] type=1505 audit(1265885531.220:7): operation="profile_load" pid=387 name=/usr/bin/evince-previewer
Feb 11 10:52:19 ryan-laptop kernel: [    4.921778] type=1505 audit(1265885531.228:8): operation="profile_load" pid=387 name=/usr/bin/evince-thumbnailer
Feb 11 10:52:19 ryan-laptop kernel: [    4.932251] type=1505 audit(1265885531.240:9): operation="profile_load" pid=389 name=/usr/lib/cups/backend/cups-pdf
Feb 11 10:52:19 ryan-laptop kernel: [    4.933111] type=1505 audit(1265885531.240:10): operation="profile_load" pid=389 name=/usr/sbin/cupsd
Feb 11 10:52:19 ryan-laptop kernel: [    5.577260] Adding 1951888k swap on /dev/sda3.  Priority:-1 extents:1 across:1951888k 
Feb 11 10:52:19 ryan-laptop kernel: [    5.771537] udev: starting version 147
Feb 11 10:52:19 ryan-laptop kernel: [    6.448357] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Feb 11 10:52:19 ryan-laptop kernel: [    6.459294] input: Dell WMI hotkeys as /devices/virtual/input/input8
Feb 11 10:52:19 ryan-laptop kernel: [    6.577445] cfg80211: Calling CRDA to update world regulatory domain
Feb 11 10:52:19 ryan-laptop kernel: [    6.628036] lp: driver loaded but no devices found
Feb 11 10:52:19 ryan-laptop kernel: [    6.673440] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
Feb 11 10:52:19 ryan-laptop kernel: [    6.692625] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
Feb 11 10:52:19 ryan-laptop kernel: [    6.780731] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0200]
Feb 11 10:52:19 ryan-laptop kernel: [    6.780758] yenta_cardbus 0000:03:01.0: O2: res at 0x94/0xD4: 00/ea
Feb 11 10:52:19 ryan-laptop kernel: [    6.780760] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst
Feb 11 10:52:19 ryan-laptop kernel: [    6.793856] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Feb 11 10:52:19 ryan-laptop kernel: [    6.793860] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Feb 11 10:52:19 ryan-laptop kernel: [    6.793986] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 11 10:52:19 ryan-laptop kernel: [    6.794001] iwl3945 0000:0c:00.0: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    6.873596] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Feb 11 10:52:19 ryan-laptop kernel: [    6.873600] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
Feb 11 10:52:19 ryan-laptop kernel: [    6.873720]   alloc irq_desc for 28 on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    6.873722]   alloc kstat_irqs on node -1
Feb 11 10:52:19 ryan-laptop kernel: [    6.873756] iwl3945 0000:0c:00.0: irq 28 for MSI/MSI-X
Feb 11 10:52:19 ryan-laptop kernel: [    6.913006] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
Feb 11 10:52:19 ryan-laptop kernel: [    6.913012] yenta_cardbus 0000:03:01.0: Socket status: 30000006
Feb 11 10:52:19 ryan-laptop kernel: [    6.913016] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
Feb 11 10:52:19 ryan-laptop kernel: [    6.913025] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
Feb 11 10:52:19 ryan-laptop kernel: [    6.913028] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
Feb 11 10:52:19 ryan-laptop kernel: [    6.913203] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xf6a00000 - 0xf6afffff
Feb 11 10:52:19 ryan-laptop kernel: [    6.913206] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
Feb 11 10:52:19 ryan-laptop kernel: [    7.104092] phy0: Selected rate control algorithm 'iwl-3945-rs'
Feb 11 10:52:19 ryan-laptop kernel: [    7.161248] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 11 10:52:19 ryan-laptop kernel: [    7.268229] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 11 10:52:19 ryan-laptop kernel: [    7.268259] HDA Intel 0000:00:1b.0: setting latency timer to 64
Feb 11 10:52:19 ryan-laptop kernel: [    7.394046] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Feb 11 10:52:19 ryan-laptop kernel: [    7.395984] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
Feb 11 10:52:19 ryan-laptop kernel: [    7.396783] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Feb 11 10:52:19 ryan-laptop kernel: [    7.397451] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Feb 11 10:52:19 ryan-laptop kernel: [    7.398092] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Feb 11 10:52:19 ryan-laptop kernel: [    7.578300] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
Feb 11 10:52:19 ryan-laptop kernel: [    7.624422] input: HDA Intel Line In at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Feb 11 10:52:19 ryan-laptop kernel: [    7.624498] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Feb 11 10:52:19 ryan-laptop kernel: [    9.814843] EXT4-fs (sda2): internal journal on sda2:8
Feb 11 10:52:19 ryan-laptop kernel: [   10.047671] EXT4-fs (sda10): barriers enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.071054] kjournald2 starting: pid 816, dev sda10:8, commit interval 5 seconds
Feb 11 10:52:19 ryan-laptop kernel: [   10.072304] EXT4-fs (sda10): internal journal on sda10:8
Feb 11 10:52:19 ryan-laptop kernel: [   10.072307] EXT4-fs (sda10): delayed allocation enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.072310] EXT4-fs: file extents enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.076355] EXT4-fs: mballoc enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.076369] EXT4-fs (sda10): mounted filesystem with ordered data mode
Feb 11 10:52:19 ryan-laptop kernel: [   10.454199] EXT4-fs (sda5): barriers enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.455115] kjournald2 starting: pid 827, dev sda5:8, commit interval 5 seconds
Feb 11 10:52:19 ryan-laptop kernel: [   10.455586] EXT4-fs (sda5): internal journal on sda5:8
Feb 11 10:52:19 ryan-laptop kernel: [   10.455589] EXT4-fs (sda5): delayed allocation enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.455592] EXT4-fs: file extents enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.455648] EXT4-fs: mballoc enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.455662] EXT4-fs (sda5): mounted filesystem with ordered data mode
Feb 11 10:52:19 ryan-laptop kernel: [   10.603186] EXT4-fs (sda6): barriers enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.610801] kjournald2 starting: pid 836, dev sda6:8, commit interval 5 seconds
Feb 11 10:52:19 ryan-laptop kernel: [   10.611267] EXT4-fs (sda6): internal journal on sda6:8
Feb 11 10:52:19 ryan-laptop kernel: [   10.611270] EXT4-fs (sda6): delayed allocation enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.611273] EXT4-fs: file extents enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.611766] EXT4-fs: mballoc enabled
Feb 11 10:52:19 ryan-laptop kernel: [   10.611780] EXT4-fs (sda6): mounted filesystem with ordered data mode
Feb 11 10:52:19 ryan-laptop kernel: [   11.209918] EXT4-fs (sda7): barriers enabled
Feb 11 10:52:19 ryan-laptop kernel: [   11.221138] kjournald2 starting: pid 848, dev sda7:8, commit interval 5 seconds
Feb 11 10:52:19 ryan-laptop kernel: [   11.221603] EXT4-fs (sda7): internal journal on sda7:8
Feb 11 10:52:19 ryan-laptop kernel: [   11.221607] EXT4-fs (sda7): delayed allocation enabled
Feb 11 10:52:19 ryan-laptop kernel: [   11.221609] EXT4-fs: file extents enabled
Feb 11 10:52:19 ryan-laptop kernel: [   11.221683] EXT4-fs: mballoc enabled
Feb 11 10:52:19 ryan-laptop kernel: [   11.221697] EXT4-fs (sda7): mounted filesystem with ordered data mode
Feb 11 10:52:19 ryan-laptop kernel: [   12.173717] EXT4-fs (sda8): barriers enabled
Feb 11 10:52:19 ryan-laptop kernel: [   12.174020] kjournald2 starting: pid 866, dev sda8:8, commit interval 5 seconds
Feb 11 10:52:19 ryan-laptop kernel: [   12.174456] EXT4-fs (sda8): internal journal on sda8:8
Feb 11 10:52:19 ryan-laptop kernel: [   12.174459] EXT4-fs (sda8): delayed allocation enabled
Feb 11 10:52:19 ryan-laptop kernel: [   12.174462] EXT4-fs: file extents enabled
Feb 11 10:52:19 ryan-laptop kernel: [   12.174588] EXT4-fs: mballoc enabled
Feb 11 10:52:19 ryan-laptop kernel: [   12.174602] EXT4-fs (sda8): mounted filesystem with ordered data mode
Feb 11 10:52:19 ryan-laptop kernel: [   12.910675] EXT4-fs (sda9): barriers enabled
Feb 11 10:52:19 ryan-laptop kernel: [   12.911031] kjournald2 starting: pid 915, dev sda9:8, commit interval 5 seconds
Feb 11 10:52:19 ryan-laptop kernel: [   12.911484] EXT4-fs (sda9): internal journal on sda9:8
Feb 11 10:52:19 ryan-laptop kernel: [   12.911488] EXT4-fs (sda9): delayed allocation enabled
Feb 11 10:52:19 ryan-laptop kernel: [   12.911491] EXT4-fs: file extents enabled
Feb 11 10:52:19 ryan-laptop kernel: [   12.911672] EXT4-fs: mballoc enabled
Feb 11 10:52:19 ryan-laptop kernel: [   12.911687] EXT4-fs (sda9): mounted filesystem with ordered data mode
Feb 11 10:52:19 ryan-laptop avahi-daemon[932]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Feb 11 10:52:19 ryan-laptop avahi-daemon[932]: Successfully dropped root privileges.
Feb 11 10:52:19 ryan-laptop avahi-daemon[932]: avahi-daemon 0.6.25 starting up.
Feb 11 10:52:19 ryan-laptop avahi-daemon[932]: Successfully called chroot().
Feb 11 10:52:19 ryan-laptop avahi-daemon[932]: Successfully dropped remaining capabilities.
Feb 11 10:52:19 ryan-laptop avahi-daemon[932]: No service file found in /etc/avahi/services.
Feb 11 10:52:19 ryan-laptop avahi-daemon[932]: Network interface enumeration completed.
Feb 11 10:52:19 ryan-laptop avahi-daemon[932]: Registering HINFO record with values 'I686'/'LINUX'.
Feb 11 10:52:19 ryan-laptop avahi-daemon[932]: Server startup complete. Host name is ryan-laptop.local. Local service cookie is 1156299558.
Feb 11 10:52:19 ryan-laptop kernel: [   13.474342] __ratelimit: 3 callbacks suppressed
Feb 11 10:52:19 ryan-laptop kernel: [   13.474345] type=1505 audit(1265914339.780:12): operation="profile_replace" pid=943 name=/usr/share/gdm/guest-session/Xsession
Feb 11 10:52:19 ryan-laptop kernel: [   13.476231] type=1505 audit(1265914339.784:13): operation="profile_replace" pid=944 name=/sbin/dhclient3
Feb 11 10:52:19 ryan-laptop kernel: [   13.476965] type=1505 audit(1265914339.784:14): operation="profile_replace" pid=944 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb 11 10:52:19 ryan-laptop kernel: [   13.477364] type=1505 audit(1265914339.784:15): operation="profile_replace" pid=944 name=/usr/lib/connman/scripts/dhclient-script
Feb 11 10:52:19 ryan-laptop kernel: [   13.483142] type=1505 audit(1265914339.788:16): operation="profile_replace" pid=945 name=/usr/bin/evince
Feb 11 10:52:19 ryan-laptop kernel: [   13.495851] type=1505 audit(1265914339.800:17): operation="profile_replace" pid=945 name=/usr/bin/evince-previewer
Feb 11 10:52:19 ryan-laptop kernel: [   13.503360] type=1505 audit(1265914339.808:18): operation="profile_replace" pid=945 name=/usr/bin/evince-thumbnailer
Feb 11 10:52:19 ryan-laptop kernel: [   13.513464] type=1505 audit(1265914339.820:19): operation="profile_replace" pid=947 name=/usr/lib/cups/backend/cups-pdf
Feb 11 10:52:19 ryan-laptop kernel: [   13.514323] type=1505 audit(1265914339.820:20): operation="profile_replace" pid=947 name=/usr/sbin/cupsd
Feb 11 10:52:19 ryan-laptop kernel: [   13.517158] type=1505 audit(1265914339.824:21): operation="profile_replace" pid=948 name=/usr/sbin/tcpdump
Feb 11 10:52:20 ryan-laptop NetworkManager: <info>  starting...
Feb 11 10:52:20 ryan-laptop NetworkManager: <info>  Trying to start the modem-manager...
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: init!
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0)
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wmaster0, iface: wmaster0)
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wmaster0, iface: wmaster0): no ifupdown configuration found.
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0, iface: eth0)
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: end _init.
Feb 11 10:52:20 ryan-laptop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb 11 10:52:20 ryan-laptop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 11 10:52:20 ryan-laptop NetworkManager: <info>  Found radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
Feb 11 10:52:20 ryan-laptop NetworkManager: <info>  Found radio killswitch rfkill0 (at /sys/devices/virtual/rfkill/rfkill0) (driver <unknown>)
Feb 11 10:52:20 ryan-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: (141171440) ... get_connections.
Feb 11 10:52:20 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: (141171440) ... get_connections (managed=false): return empty list.
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin Sierra
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin Option
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin Generic
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin Huawei
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin Gobi
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin Novatel
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin ZTE
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin Nokia
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin Ericsson MBM
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin Option High-Speed
Feb 11 10:52:20 ryan-laptop modem-manager: Loaded plugin MotoC
Feb 11 10:52:21 ryan-laptop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945')
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (wlan0): now managed
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (wlan0): bringing up device.
Feb 11 10:52:21 ryan-laptop kernel: [   14.964295] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
Feb 11 10:52:21 ryan-laptop anacron[1132]: Anacron 2.3 started on 2010-02-11
Feb 11 10:52:21 ryan-laptop anacron[1132]: Will run job `cron.daily' in 5 min.
Feb 11 10:52:21 ryan-laptop anacron[1132]: Will run job `cron.weekly' in 10 min.
Feb 11 10:52:21 ryan-laptop anacron[1132]: Jobs will be executed sequentially
Feb 11 10:52:21 ryan-laptop init: apport pre-start process (1114) terminated with status 1
Feb 11 10:52:21 ryan-laptop init: apport post-stop process (1134) terminated with status 1
Feb 11 10:52:21 ryan-laptop cron[1119]: (CRON) INFO (pidfile fd = 3)
Feb 11 10:52:21 ryan-laptop cron[1141]: (CRON) STARTUP (fork ok)
Feb 11 10:52:21 ryan-laptop gdm-binary[956]: WARNING: Unable to find users: no seat-id found
Feb 11 10:52:21 ryan-laptop kernel: [   15.426840] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
Feb 11 10:52:21 ryan-laptop cron[1141]: (CRON) INFO (Running @reboot jobs)
Feb 11 10:52:21 ryan-laptop kernel: [   15.498719] Registered led device: iwl-phy0::radio
Feb 11 10:52:21 ryan-laptop kernel: [   15.498737] Registered led device: iwl-phy0::assoc
Feb 11 10:52:21 ryan-laptop kernel: [   15.498789] Registered led device: iwl-phy0::RX
Feb 11 10:52:21 ryan-laptop kernel: [   15.498802] Registered led device: iwl-phy0::TX
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (wlan0): preparing device.
Feb 11 10:52:21 ryan-laptop kernel: [   15.505603] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 11 10:52:21 ryan-laptop kernel: [   15.507013] tg3 0000:09:00.0: PME# disabled
Feb 11 10:52:21 ryan-laptop kernel: [   15.507122]   alloc irq_desc for 29 on node -1
Feb 11 10:52:21 ryan-laptop kernel: [   15.507124]   alloc kstat_irqs on node -1
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Feb 11 10:52:21 ryan-laptop kernel: [   15.507143] tg3 0000:09:00.0: irq 29 for MSI/MSI-X
Feb 11 10:52:21 ryan-laptop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (eth0): carrier is OFF
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3')
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (eth0): now managed
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (eth0): bringing up device.
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (eth0): preparing device.
Feb 11 10:52:21 ryan-laptop kernel: [   15.594774] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Feb 11 10:52:21 ryan-laptop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0
Feb 11 10:52:21 ryan-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  modem-manager is now available
Feb 11 10:52:21 ryan-laptop NetworkManager: <info>  Trying to start the supplicant...
Feb 11 10:52:22 ryan-laptop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Feb 11 10:52:22 ryan-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Feb 11 10:52:22 ryan-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Feb 11 10:52:22 ryan-laptop acpid: client connected from 1237[107:114]
Feb 11 10:52:23 ryan-laptop acpid: client connected from 1185[0:0]
Feb 11 10:52:23 ryan-laptop kernel: [   17.410235] integrated sync not supported
Feb 11 10:52:23 ryan-laptop wpa_supplicant[1164]: CTRL-EVENT-SCAN-RESULTS 
Feb 11 10:52:24 ryan-laptop kernel: [   17.773492] integrated sync not supported
Feb 11 10:52:24 ryan-laptop kernel: [   17.980644] ppdev: user-space parallel port driver
Feb 11 10:52:24 ryan-laptop kernel: [   18.053603] [drm] TV-16: set mode 1024x768 20
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Feb 11 10:52:25 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-0:1.0
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-2
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb6
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb6/6-0:1.0
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb7
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb7/7-0:1.0
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Feb 11 10:52:25 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Feb 11 10:52:25 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:52:25 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:52:25 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:52:25 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Feb 11 10:52:25 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:52:25 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:52:25 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:52:25 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:52:25 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:52:25 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5/5-2
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Device vendor/product is 413C:3012
Feb 11 10:52:25 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:52:25 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb6
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:52:25 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:52:25 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb7
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:52:25 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:52:25 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Feb 11 10:52:25 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Feb 11 10:52:25 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:52:26 ryan-laptop console-kit-daemon[979]: WARNING: Couldn't read /proc/958/environ: Failed to open file '/proc/958/environ': No such file or directory
Feb 11 10:52:28 ryan-laptop pulseaudio[1540]: pid.c: Stale PID file, overwriting.
Feb 11 10:52:30 ryan-laptop kernel: [   24.492078] integrated sync not supported
Feb 11 10:52:31 ryan-laptop kernel: [   24.690257] integrated sync not supported
Feb 11 10:52:31 ryan-laptop kernel: [   24.890335] integrated sync not supported
Feb 11 10:52:33 ryan-laptop kernel: [   27.637809] integrated sync not supported
Feb 11 10:52:44 ryan-laptop wpa_supplicant[1164]: CTRL-EVENT-SCAN-RESULTS 
Feb 11 10:52:44 ryan-laptop gnome-session[1441]: WARNING: Application 'nautilus.desktop' failed to register before timeout
Feb 11 10:53:14 ryan-laptop wpa_supplicant[1164]: CTRL-EVENT-SCAN-RESULTS 
Feb 11 10:53:59 ryan-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Feb 11 10:53:59 ryan-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="929" x-info="http://www.rsyslog.com"] (re)start
Feb 11 10:53:59 ryan-laptop rsyslogd: rsyslogd's groupid changed to 102
Feb 11 10:53:59 ryan-laptop rsyslogd: rsyslogd's userid changed to 101
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Linux version 2.6.31-19-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 (Ubuntu 2.6.31-19.56-generic)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] KERNEL supported cpus:
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   Intel GenuineIntel
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   AMD AuthenticAMD
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   NSC Geode by NSC
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   Centaur CentaurHauls
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6bf400 (usable)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 000000003f6bf400 - 0000000040000000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] DMI 2.4 present.
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] last_pfn = 0x3f6bf max_arch_pfn = 0x100000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] MTRR default type: uncachable
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   00000-9FFFF write-back
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   A0000-BFFFF uncachable
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   C0000-CFFFF write-protect
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   D0000-EFFFF uncachable
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   F0000-FFFFF write-protect
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] MTRR variable ranges enabled:
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   1 base 03F800000 mask FFF800000 uncachable
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   2 base 03F700000 mask FFFF00000 uncachable
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   3 disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   4 disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   5 disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   6 disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   7 disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] modified physical RAM map:
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000003f6bf400 (usable)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 000000003f6bf400 - 0000000040000000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] RAMDISK: 2f205000 - 2f94ee7c
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: RSDP 000fbf90 00024 (v02 DELL  )
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: XSDT 3f6c1e00 0006C (v01 DELL    M08     27DA0115 ASL  00000061)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: FACP 3f6c1c9c 000F4 (v04 DELL    M08     27DA0115 ASL  00000061)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: DSDT 3f6c2400 06506 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: FACS 3f6d0c00 00040
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: HPET 3f6c1f00 00038 (v01 DELL    M08     00000001 ASL  00000061)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: APIC 3f6c2000 00068 (v01 DELL    M08     27DA0115 ASL  00000047)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: ASF! 3f6c1c00 0007E (v32 DELL    M08     27DA0115 ASL  00000061)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: MCFG 3f6c1fc0 0003E (v16 DELL    M08     27DA0115 ASL  00000061)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: TCPA 3f6c2300 00032 (v01                 00000000 ASL  00000000)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: SLIC 3f6c209c 00176 (v01 DELL    M08     27DA0115 ASL  00000061)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: SSDT 3f6c0f8a 004B6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: SSDT 3f6c0abe 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] 126MB HIGHMEM available.
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] 887MB LOWMEM available.
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   low ram: 0 - 377fe000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   #4 [002f205000 - 002f94ee7c]          RAMDISK ==> [002f205000 - 002f94ee7c]
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   #6 [00008a9000 - 00008ac188]              BRK ==> [00008a9000 - 00008ac188]
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Zone PFN ranges:
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f6bf
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Movable zone start PFN for each node
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] early_node_map[3] active PFN ranges
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0003f6bf
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] On node 0 totalpages: 259674
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1000000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   HighMem zone: 254 pages used for memmap
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]   HighMem zone: 32195 pages, LIFO batch:7
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Using APIC driver default
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] nr_irqs_gsi: 24
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:b8000000)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257644
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-19-generic root=UUID=4413e0c4-e947-4e74-9100-551f31e65986 ro quiet splash
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Initializing CPU#0
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] allocated 5195500 bytes of page_cgroup
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f6bf)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Memory: 1008764k/1039100k available (4567k kernel code, 29476k reserved, 2141k data, 540k init, 129796k highmem)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] virtual kernel memory layout:
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]       .data : 0xc0575c48 - 0xc078d408   (2141 kB)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575c48   (4567 kB)
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Extended CMOS year: 2000
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Feb 11 10:53:59 ryan-laptop kernel: [    0.000000] Detected 1994.816 MHz processor.
Feb 11 10:53:59 ryan-laptop kernel: [    0.001530] Console: colour VGA+ 80x25
Feb 11 10:53:59 ryan-laptop kernel: [    0.001534] console [tty0] enabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.001706] hpet clockevent registered
Feb 11 10:53:59 ryan-laptop kernel: [    0.001711] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Feb 11 10:53:59 ryan-laptop kernel: [    0.001718] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.63 BogoMIPS (lpj=7979264)
Feb 11 10:53:59 ryan-laptop kernel: [    0.001740] Security Framework initialized
Feb 11 10:53:59 ryan-laptop kernel: [    0.001765] AppArmor: AppArmor initialized
Feb 11 10:53:59 ryan-laptop kernel: [    0.001772] Mount-cache hash table entries: 512
Feb 11 10:53:59 ryan-laptop kernel: [    0.001920] Initializing cgroup subsys ns
Feb 11 10:53:59 ryan-laptop kernel: [    0.001926] Initializing cgroup subsys cpuacct
Feb 11 10:53:59 ryan-laptop kernel: [    0.001930] Initializing cgroup subsys memory
Feb 11 10:53:59 ryan-laptop kernel: [    0.001937] Initializing cgroup subsys freezer
Feb 11 10:53:59 ryan-laptop kernel: [    0.001939] Initializing cgroup subsys net_cls
Feb 11 10:53:59 ryan-laptop kernel: [    0.001955] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb 11 10:53:59 ryan-laptop kernel: [    0.001958] CPU: L2 cache: 1024K
Feb 11 10:53:59 ryan-laptop kernel: [    0.001963] mce: CPU supports 6 MCE banks
Feb 11 10:53:59 ryan-laptop kernel: [    0.001972] CPU0: Thermal monitoring enabled (TM2)
Feb 11 10:53:59 ryan-laptop kernel: [    0.001976] using mwait in idle threads.
Feb 11 10:53:59 ryan-laptop kernel: [    0.001983] Performance Counters: Core2 events, Intel PMU driver.
Feb 11 10:53:59 ryan-laptop kernel: [    0.001993] ... version:                 2
Feb 11 10:53:59 ryan-laptop kernel: [    0.001994] ... bit width:               40
Feb 11 10:53:59 ryan-laptop kernel: [    0.001996] ... generic counters:        2
Feb 11 10:53:59 ryan-laptop kernel: [    0.001998] ... value mask:              000000ffffffffff
Feb 11 10:53:59 ryan-laptop kernel: [    0.002000] ... max period:              000000007fffffff
Feb 11 10:53:59 ryan-laptop kernel: [    0.002002] ... fixed-purpose counters:  3
Feb 11 10:53:59 ryan-laptop kernel: [    0.002003] ... counter mask:            0000000700000003
Feb 11 10:53:59 ryan-laptop kernel: [    0.002008] Checking 'hlt' instruction... OK.
Feb 11 10:53:59 ryan-laptop kernel: [    0.016829] SMP alternatives: switching to UP code
Feb 11 10:53:59 ryan-laptop kernel: [    0.024007] ACPI: Core revision 20090521
Feb 11 10:53:59 ryan-laptop kernel: [    0.036449] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb 11 10:53:59 ryan-laptop kernel: [    0.076818] CPU0: Intel(R) Celeron(R) CPU          550  @ 2.00GHz stepping 01
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] Brought up 1 CPUs
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] Total of 1 processors activated (3989.63 BogoMIPS).
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] CPU0 attaching NULL sched-domain.
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] Booting paravirtualized kernel on bare hardware
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] regulator: core version 0.5
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] Time: 10:53:46  Date: 02/11/10
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] NET: Registered protocol family 16
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] EISA bus registered
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] ACPI: bus type pci registered
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] PCI: MCFG area at f8000000 reserved in E820
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] PCI: Using MMCONFIG for extended config space
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] PCI: Using configuration type 1 for base access
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] bio: create slab <bio-0> at 0
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] ACPI: EC: Look up EC in DSDT
Feb 11 10:53:59 ryan-laptop kernel: [    0.080001] ACPI: BIOS _OSI(Linux) query ignored
Feb 11 10:53:59 ryan-laptop kernel: [    0.118007] ACPI: SSDT 3f6d0c80 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
Feb 11 10:53:59 ryan-laptop kernel: [    0.134171] ACPI: Interpreter enabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.134177] ACPI: (supports S0 S3 S4 S5)
Feb 11 10:53:59 ryan-laptop kernel: [    0.134197] ACPI: Using IOAPIC for interrupt routing
Feb 11 10:53:59 ryan-laptop kernel: [    0.218801] ACPI: ACPI Dock Station Driver: 3 docks/bays found
Feb 11 10:53:59 ryan-laptop kernel: [    0.234888] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb 11 10:53:59 ryan-laptop kernel: [    0.234995] pci 0000:00:02.0: reg 10 64bit mmio: [0xf6e00000-0xf6efffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.235004] pci 0000:00:02.0: reg 18 64bit mmio: [0xe0000000-0xefffffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.235009] pci 0000:00:02.0: reg 20 io port: [0xefe8-0xefef]
Feb 11 10:53:59 ryan-laptop kernel: [    0.235056] pci 0000:00:02.1: reg 10 64bit mmio: [0xf6f00000-0xf6ffffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.235183] pci 0000:00:1a.0: reg 20 io port: [0x6f20-0x6f3f]
Feb 11 10:53:59 ryan-laptop kernel: [    0.235255] pci 0000:00:1a.1: reg 20 io port: [0x6f00-0x6f1f]
Feb 11 10:53:59 ryan-laptop kernel: [    0.235335] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.235407] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Feb 11 10:53:59 ryan-laptop kernel: [    0.235413] pci 0000:00:1a.7: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.235474] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6dfc000-0xf6dfffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.235543] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Feb 11 10:53:59 ryan-laptop kernel: [    0.235548] pci 0000:00:1b.0: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.235646] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Feb 11 10:53:59 ryan-laptop kernel: [    0.235651] pci 0000:00:1c.0: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.235752] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Feb 11 10:53:59 ryan-laptop kernel: [    0.235757] pci 0000:00:1c.1: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.235863] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Feb 11 10:53:59 ryan-laptop kernel: [    0.235868] pci 0000:00:1c.5: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.235939] pci 0000:00:1d.0: reg 20 io port: [0x6f80-0x6f9f]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236018] pci 0000:00:1d.1: reg 20 io port: [0x6f60-0x6f7f]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236092] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236171] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236242] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Feb 11 10:53:59 ryan-laptop kernel: [    0.236248] pci 0000:00:1d.7: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.236435] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Feb 11 10:53:59 ryan-laptop kernel: [    0.236439] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
Feb 11 10:53:59 ryan-laptop kernel: [    0.236444] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
Feb 11 10:53:59 ryan-laptop kernel: [    0.236451] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
Feb 11 10:53:59 ryan-laptop kernel: [    0.236510] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236519] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236527] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236536] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236545] pci 0000:00:1f.1: reg 20 io port: [0x6fa0-0x6faf]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236609] pci 0000:00:1f.2: reg 10 io port: [0x6eb0-0x6eb7]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236617] pci 0000:00:1f.2: reg 14 io port: [0x6eb8-0x6ebb]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236626] pci 0000:00:1f.2: reg 18 io port: [0x6ec0-0x6ec7]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236635] pci 0000:00:1f.2: reg 1c io port: [0x6ec8-0x6ecb]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236643] pci 0000:00:1f.2: reg 20 io port: [0x6ee0-0x6eef]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236652] pci 0000:00:1f.2: reg 24 io port: [0xeff0-0xefff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236686] pci 0000:00:1f.2: PME# supported from D3hot
Feb 11 10:53:59 ryan-laptop kernel: [    0.236691] pci 0000:00:1f.2: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.236721] pci 0000:00:1f.3: reg 10 32bit mmio: [0xf6dfbf00-0xf6dfbfff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.236749] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
Feb 11 10:53:59 ryan-laptop kernel: [    0.237045] pci 0000:0c:00.0: reg 10 32bit mmio: [0xf6cff000-0xf6cfffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.237297] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
Feb 11 10:53:59 ryan-laptop kernel: [    0.237310] pci 0000:0c:00.0: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.237434] pci 0000:00:1c.1: bridge 32bit mmio: [0xf6c00000-0xf6cfffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.237575] pci 0000:09:00.0: reg 10 64bit mmio: [0xf6bf0000-0xf6bfffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.237691] pci 0000:09:00.0: PME# supported from D3hot D3cold
Feb 11 10:53:59 ryan-laptop kernel: [    0.237697] pci 0000:09:00.0: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.237784] pci 0000:00:1c.5: bridge 32bit mmio: [0xf6b00000-0xf6bfffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.237847] pci 0000:03:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.237878] pci 0000:03:01.0: supports D1 D2
Feb 11 10:53:59 ryan-laptop kernel: [    0.237880] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 11 10:53:59 ryan-laptop kernel: [    0.237886] pci 0000:03:01.0: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.237939] pci 0000:03:01.4: reg 10 32bit mmio: [0xf6aff000-0xf6afffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.237948] pci 0000:03:01.4: reg 14 32bit mmio: [0xf6afe800-0xf6afefff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.238005] pci 0000:03:01.4: supports D1 D2
Feb 11 10:53:59 ryan-laptop kernel: [    0.238008] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
Feb 11 10:53:59 ryan-laptop kernel: [    0.238013] pci 0000:03:01.4: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.238088] pci 0000:00:1e.0: transparent bridge
Feb 11 10:53:59 ryan-laptop kernel: [    0.238096] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6a00000-0xf6afffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.238154] pci_bus 0000:00: on NUMA node 0
Feb 11 10:53:59 ryan-laptop kernel: [    0.238159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb 11 10:53:59 ryan-laptop kernel: [    0.238421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Feb 11 10:53:59 ryan-laptop kernel: [    0.238561] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Feb 11 10:53:59 ryan-laptop kernel: [    0.238636] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Feb 11 10:53:59 ryan-laptop kernel: [    0.238719] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Feb 11 10:53:59 ryan-laptop kernel: [    0.257049] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Feb 11 10:53:59 ryan-laptop kernel: [    0.257176] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *3
Feb 11 10:53:59 ryan-laptop kernel: [    0.257298] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 *10 11)
Feb 11 10:53:59 ryan-laptop kernel: [    0.257421] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
Feb 11 10:53:59 ryan-laptop kernel: [    0.257544] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Feb 11 10:53:59 ryan-laptop kernel: [    0.257670] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Feb 11 10:53:59 ryan-laptop kernel: [    0.257795] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Feb 11 10:53:59 ryan-laptop kernel: [    0.257907] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 11 10:53:59 ryan-laptop kernel: [    0.258107] SCSI subsystem initialized
Feb 11 10:53:59 ryan-laptop kernel: [    0.258159] libata version 3.00 loaded.
Feb 11 10:53:59 ryan-laptop kernel: [    0.258230] usbcore: registered new interface driver usbfs
Feb 11 10:53:59 ryan-laptop kernel: [    0.258245] usbcore: registered new interface driver hub
Feb 11 10:53:59 ryan-laptop kernel: [    0.258266] usbcore: registered new device driver usb
Feb 11 10:53:59 ryan-laptop kernel: [    0.258396] ACPI: WMI: Mapper loaded
Feb 11 10:53:59 ryan-laptop kernel: [    0.258398] PCI: Using ACPI for IRQ routing
Feb 11 10:53:59 ryan-laptop kernel: [    0.258737] Bluetooth: Core ver 2.15
Feb 11 10:53:59 ryan-laptop kernel: [    0.258763] NET: Registered protocol family 31
Feb 11 10:53:59 ryan-laptop kernel: [    0.258765] Bluetooth: HCI device and connection manager initialized
Feb 11 10:53:59 ryan-laptop kernel: [    0.258768] Bluetooth: HCI socket layer initialized
Feb 11 10:53:59 ryan-laptop kernel: [    0.258770] NetLabel: Initializing
Feb 11 10:53:59 ryan-laptop kernel: [    0.258771] NetLabel:  domain hash size = 128
Feb 11 10:53:59 ryan-laptop kernel: [    0.258773] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 11 10:53:59 ryan-laptop kernel: [    0.258785] NetLabel:  unlabeled traffic allowed by default
Feb 11 10:53:59 ryan-laptop kernel: [    0.258814] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Feb 11 10:53:59 ryan-laptop kernel: [    0.258818] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Feb 11 10:53:59 ryan-laptop kernel: [    0.265414] pnp: PnP ACPI init
Feb 11 10:53:59 ryan-laptop kernel: [    0.265438] ACPI: bus type pnp registered
Feb 11 10:53:59 ryan-laptop kernel: [    0.309122] pnp 00:0b: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:53:59 ryan-laptop kernel: [    0.309127] pnp 00:0b: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:53:59 ryan-laptop kernel: [    0.309211] pnp 00:0c: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:53:59 ryan-laptop kernel: [    0.309215] pnp 00:0c: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:53:59 ryan-laptop kernel: [    0.309218] pnp 00:0c: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:53:59 ryan-laptop kernel: [    0.309221] pnp 00:0c: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
Feb 11 10:53:59 ryan-laptop kernel: [    0.331773] pnp: PnP ACPI: found 14 devices
Feb 11 10:53:59 ryan-laptop kernel: [    0.331775] ACPI: ACPI bus type pnp unregistered
Feb 11 10:53:59 ryan-laptop kernel: [    0.331780] PnPBIOS: Disabled by ACPI PNP
Feb 11 10:53:59 ryan-laptop kernel: [    0.331793] system 00:05: ioport range 0xc80-0xcaf has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331796] system 00:05: ioport range 0xcc0-0xcff could not be reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331803] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331809] system 00:0a: ioport range 0xcb0-0xcbb has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331812] system 00:0a: iomem range 0xfed40000-0xfed44fff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331817] system 00:0b: ioport range 0x900-0x97f has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331820] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331825] system 00:0c: ioport range 0xf400-0xf4fe has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331828] system 00:0c: ioport range 0x1080-0x10bf has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331831] system 00:0c: ioport range 0x10c0-0x10df has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331834] system 00:0c: ioport range 0x809-0x809 has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331839] system 00:0d: iomem range 0x0-0x9efff could not be reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331842] system 00:0d: iomem range 0x9f000-0x9ffff could not be reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331844] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331847] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331850] system 00:0d: iomem range 0x100000-0x3f6bf3ff could not be reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331853] system 00:0d: iomem range 0x3f6bf400-0x3f6fffff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331856] system 00:0d: iomem range 0x3f700000-0x3f7fffff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331859] system 00:0d: iomem range 0x3f700000-0x3fefffff could not be reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331862] system 00:0d: iomem range 0xffe00000-0xffffffff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331864] system 00:0d: iomem range 0xffa00000-0xffbfffff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331867] system 00:0d: iomem range 0xfec00000-0xfec0ffff could not be reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331870] system 00:0d: iomem range 0xfee00000-0xfee0ffff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331873] system 00:0d: iomem range 0xfed20000-0xfed3ffff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331876] system 00:0d: iomem range 0xfed45000-0xfed8ffff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331878] system 00:0d: iomem range 0xfeda0000-0xfeda3fff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331881] system 00:0d: iomem range 0xfeda4000-0xfeda4fff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331884] system 00:0d: iomem range 0xfeda5000-0xfeda5fff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331887] system 00:0d: iomem range 0xfeda6000-0xfeda6fff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331890] system 00:0d: iomem range 0xfed18000-0xfed1bfff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.331893] system 00:0d: iomem range 0xf8000000-0xfbffffff has been reserved
Feb 11 10:53:59 ryan-laptop kernel: [    0.366560] AppArmor: AppArmor Filesystem Enabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.366630] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
Feb 11 10:53:59 ryan-laptop kernel: [    0.366632] pci 0000:00:1c.0:   IO window: disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.366639] pci 0000:00:1c.0:   MEM window: disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.366644] pci 0000:00:1c.0:   PREFETCH window: disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.366649] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
Feb 11 10:53:59 ryan-laptop kernel: [    0.366651] pci 0000:00:1c.1:   IO window: disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.366658] pci 0000:00:1c.1:   MEM window: 0xf6c00000-0xf6cfffff
Feb 11 10:53:59 ryan-laptop kernel: [    0.366663] pci 0000:00:1c.1:   PREFETCH window: disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.366669] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
Feb 11 10:53:59 ryan-laptop kernel: [    0.366670] pci 0000:00:1c.5:   IO window: disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.366677] pci 0000:00:1c.5:   MEM window: 0xf6b00000-0xf6bfffff
Feb 11 10:53:59 ryan-laptop kernel: [    0.366682] pci 0000:00:1c.5:   PREFETCH window: disabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.366694] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
Feb 11 10:53:59 ryan-laptop kernel: [    0.366697] pci 0000:03:01.0:   IO window: 0x002000-0x0020ff
Feb 11 10:53:59 ryan-laptop kernel: [    0.366703] pci 0000:03:01.0:   IO window: 0x002400-0x0024ff
Feb 11 10:53:59 ryan-laptop kernel: [    0.366709] pci 0000:03:01.0:   PREFETCH window: 0x40000000-0x43ffffff
Feb 11 10:53:59 ryan-laptop kernel: [    0.366715] pci 0000:03:01.0:   MEM window: 0x44000000-0x47ffffff
Feb 11 10:53:59 ryan-laptop kernel: [    0.366721] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Feb 11 10:53:59 ryan-laptop kernel: [    0.366725] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
Feb 11 10:53:59 ryan-laptop kernel: [    0.366732] pci 0000:00:1e.0:   MEM window: 0xf6a00000-0xf6afffff
Feb 11 10:53:59 ryan-laptop kernel: [    0.366737] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x43ffffff
Feb 11 10:53:59 ryan-laptop kernel: [    0.366754]   alloc irq_desc for 16 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.366756]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.366762] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 11 10:53:59 ryan-laptop kernel: [    0.366769] pci 0000:00:1c.0: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    0.366778]   alloc irq_desc for 17 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.366780]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.366783] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb 11 10:53:59 ryan-laptop kernel: [    0.366788] pci 0000:00:1c.1: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    0.366797] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb 11 10:53:59 ryan-laptop kernel: [    0.366803] pci 0000:00:1c.5: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    0.366812] pci 0000:00:1e.0: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    0.366822] pci 0000:03:01.0: enabling device (0000 -> 0003)
Feb 11 10:53:59 ryan-laptop kernel: [    0.366827]   alloc irq_desc for 19 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.366828]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.366832] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb 11 10:53:59 ryan-laptop kernel: [    0.366842] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366844] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366847] pci_bus 0000:0c: resource 1 mem: [0xf6c00000-0xf6cfffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366849] pci_bus 0000:09: resource 1 mem: [0xf6b00000-0xf6bfffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366852] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366854] pci_bus 0000:03: resource 1 mem: [0xf6a00000-0xf6afffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366857] pci_bus 0000:03: resource 2 pref mem [0x40000000-0x43ffffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366859] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366861] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366864] pci_bus 0000:04: resource 0 io:  [0x2000-0x20ff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366866] pci_bus 0000:04: resource 1 io:  [0x2400-0x24ff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366868] pci_bus 0000:04: resource 2 pref mem [0x40000000-0x43ffffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366871] pci_bus 0000:04: resource 3 mem: [0x44000000-0x47ffffff]
Feb 11 10:53:59 ryan-laptop kernel: [    0.366906] NET: Registered protocol family 2
Feb 11 10:53:59 ryan-laptop kernel: [    0.367001] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb 11 10:53:59 ryan-laptop kernel: [    0.367287] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Feb 11 10:53:59 ryan-laptop kernel: [    0.367829] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb 11 10:53:59 ryan-laptop kernel: [    0.368217] TCP: Hash tables configured (established 131072 bind 65536)
Feb 11 10:53:59 ryan-laptop kernel: [    0.368220] TCP reno registered
Feb 11 10:53:59 ryan-laptop kernel: [    0.368344] NET: Registered protocol family 1
Feb 11 10:53:59 ryan-laptop kernel: [    0.368415] Trying to unpack rootfs image as initramfs...
Feb 11 10:53:59 ryan-laptop kernel: [    0.503974] Switched to high resolution mode on CPU 0
Feb 11 10:53:59 ryan-laptop kernel: [    0.555016] Freeing initrd memory: 7463k freed
Feb 11 10:53:59 ryan-laptop kernel: [    0.560057] cpufreq-nforce2: No nForce2 chipset.
Feb 11 10:53:59 ryan-laptop kernel: [    0.560087] Scanning for low memory corruption every 60 seconds
Feb 11 10:53:59 ryan-laptop kernel: [    0.560196] audit: initializing netlink socket (disabled)
Feb 11 10:53:59 ryan-laptop kernel: [    0.560217] type=2000 audit(1265885626.560:1): initialized
Feb 11 10:53:59 ryan-laptop kernel: [    0.568834] highmem bounce pool size: 64 pages
Feb 11 10:53:59 ryan-laptop kernel: [    0.568840] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Feb 11 10:53:59 ryan-laptop kernel: [    0.570062] VFS: Disk quotas dquot_6.5.2
Feb 11 10:53:59 ryan-laptop kernel: [    0.570116] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb 11 10:53:59 ryan-laptop kernel: [    0.570597] fuse init (API version 7.12)
Feb 11 10:53:59 ryan-laptop kernel: [    0.570674] msgmni has been set to 1732
Feb 11 10:53:59 ryan-laptop kernel: [    0.570844] alg: No test for stdrng (krng)
Feb 11 10:53:59 ryan-laptop kernel: [    0.570856] io scheduler noop registered
Feb 11 10:53:59 ryan-laptop kernel: [    0.570857] io scheduler anticipatory registered
Feb 11 10:53:59 ryan-laptop kernel: [    0.570859] io scheduler deadline registered
Feb 11 10:53:59 ryan-laptop kernel: [    0.570897] io scheduler cfq registered (default)
Feb 11 10:53:59 ryan-laptop kernel: [    0.570911] pci 0000:00:02.0: Boot video device
Feb 11 10:53:59 ryan-laptop kernel: [    0.571188]   alloc irq_desc for 24 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.571190]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.571203] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
Feb 11 10:53:59 ryan-laptop kernel: [    0.571216] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    0.571381]   alloc irq_desc for 25 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.571383]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.571392] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
Feb 11 10:53:59 ryan-laptop kernel: [    0.571404] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    0.571564]   alloc irq_desc for 26 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.571566]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.571575] pcieport-driver 0000:00:1c.5: irq 26 for MSI/MSI-X
Feb 11 10:53:59 ryan-laptop kernel: [    0.571587] pcieport-driver 0000:00:1c.5: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    0.571689] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 11 10:53:59 ryan-laptop kernel: [    0.571777] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 11 10:53:59 ryan-laptop kernel: [    0.571927] ACPI: AC Adapter [AC] (on-line)
Feb 11 10:53:59 ryan-laptop kernel: [    0.572017] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Feb 11 10:53:59 ryan-laptop kernel: [    0.572487] ACPI: Lid Switch [LID]
Feb 11 10:53:59 ryan-laptop kernel: [    0.572528] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Feb 11 10:53:59 ryan-laptop kernel: [    0.572535] ACPI: Power Button [PBTN]
Feb 11 10:53:59 ryan-laptop kernel: [    0.572573] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Feb 11 10:53:59 ryan-laptop kernel: [    0.572576] ACPI: Sleep Button [SBTN]
Feb 11 10:53:59 ryan-laptop kernel: [    0.573260] Monitor-Mwait will be used to enter C-1 state
Feb 11 10:53:59 ryan-laptop kernel: [    0.573285] Monitor-Mwait will be used to enter C-2 state
Feb 11 10:53:59 ryan-laptop kernel: [    0.573303] Monitor-Mwait will be used to enter C-3 state
Feb 11 10:53:59 ryan-laptop kernel: [    0.573310] Marking TSC unstable due to TSC halts in idle
Feb 11 10:53:59 ryan-laptop kernel: [    0.573330] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Feb 11 10:53:59 ryan-laptop kernel: [    0.573355] processor LNXCPU:00: registered as cooling_device0
Feb 11 10:53:59 ryan-laptop kernel: [    0.573358] ACPI: Processor [CPU0] (supports 8 throttling states)
Feb 11 10:53:59 ryan-laptop kernel: [    0.601804] thermal LNXTHERM:01: registered as thermal_zone0
Feb 11 10:53:59 ryan-laptop kernel: [    0.601812] ACPI: Thermal Zone [THM] (55 C)
Feb 11 10:53:59 ryan-laptop kernel: [    0.601860] isapnp: Scanning for PnP cards...
Feb 11 10:53:59 ryan-laptop kernel: [    0.635789] ACPI: Battery Slot [BAT0] (battery present)
Feb 11 10:53:59 ryan-laptop kernel: [    0.635836] ACPI: Battery Slot [BAT1] (battery absent)
Feb 11 10:53:59 ryan-laptop kernel: [    0.984616] isapnp: No Plug & Play device found
Feb 11 10:53:59 ryan-laptop kernel: [    0.985605] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Feb 11 10:53:59 ryan-laptop kernel: [    0.985744] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 11 10:53:59 ryan-laptop kernel: [    0.986183] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 11 10:53:59 ryan-laptop kernel: [    0.987067] brd: module loaded
Feb 11 10:53:59 ryan-laptop kernel: [    0.987447] loop: module loaded
Feb 11 10:53:59 ryan-laptop kernel: [    0.987520] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Feb 11 10:53:59 ryan-laptop kernel: [    0.987619] ata_piix 0000:00:1f.1: version 2.13
Feb 11 10:53:59 ryan-laptop kernel: [    0.987632] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 11 10:53:59 ryan-laptop kernel: [    0.987675] ata_piix 0000:00:1f.1: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    0.987767] scsi0 : ata_piix
Feb 11 10:53:59 ryan-laptop kernel: [    0.987848] scsi1 : ata_piix
Feb 11 10:53:59 ryan-laptop kernel: [    0.990058] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
Feb 11 10:53:59 ryan-laptop kernel: [    0.990061] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
Feb 11 10:53:59 ryan-laptop kernel: [    0.990260] ata2: port disabled. ignoring.
Feb 11 10:53:59 ryan-laptop kernel: [    0.990284]   alloc irq_desc for 18 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.990286]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    0.990293] ata_piix 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb 11 10:53:59 ryan-laptop kernel: [    0.990299] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Feb 11 10:53:59 ryan-laptop kernel: [    1.144263] ata_piix 0000:00:1f.2: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    1.144318] scsi2 : ata_piix
Feb 11 10:53:59 ryan-laptop kernel: [    1.144370] scsi3 : ata_piix
Feb 11 10:53:59 ryan-laptop kernel: [    1.146632] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 18
Feb 11 10:53:59 ryan-laptop kernel: [    1.146640] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 18
Feb 11 10:53:59 ryan-laptop kernel: [    1.147412] Fixed MDIO Bus: probed
Feb 11 10:53:59 ryan-laptop kernel: [    1.147444] PPP generic driver version 2.4.2
Feb 11 10:53:59 ryan-laptop kernel: [    1.147528] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 11 10:53:59 ryan-laptop kernel: [    1.147550]   alloc irq_desc for 22 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    1.147552]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    1.147558] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Feb 11 10:53:59 ryan-laptop kernel: [    1.147575] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    1.147579] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Feb 11 10:53:59 ryan-laptop kernel: [    1.147631] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Feb 11 10:53:59 ryan-laptop kernel: [    1.151535] ehci_hcd 0000:00:1a.7: debug port 1
Feb 11 10:53:59 ryan-laptop kernel: [    1.151543] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Feb 11 10:53:59 ryan-laptop kernel: [    1.151556] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
Feb 11 10:53:59 ryan-laptop kernel: [    1.155836] ata1.00: ATAPI: TEAC CD-ROM CD-224E-N, D.AB, max UDMA/33
Feb 11 10:53:59 ryan-laptop kernel: [    1.168014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Feb 11 10:53:59 ryan-laptop kernel: [    1.168081] usb usb1: configuration #1 chosen from 1 choice
Feb 11 10:53:59 ryan-laptop kernel: [    1.168106] hub 1-0:1.0: USB hub found
Feb 11 10:53:59 ryan-laptop kernel: [    1.168115] hub 1-0:1.0: 4 ports detected
Feb 11 10:53:59 ryan-laptop kernel: [    1.168167]   alloc irq_desc for 20 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    1.168169]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    1.168174] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb 11 10:53:59 ryan-laptop kernel: [    1.168185] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    1.168189] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb 11 10:53:59 ryan-laptop kernel: [    1.168219] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Feb 11 10:53:59 ryan-laptop kernel: [    1.172136] ehci_hcd 0000:00:1d.7: debug port 1
Feb 11 10:53:59 ryan-laptop kernel: [    1.172143] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Feb 11 10:53:59 ryan-laptop kernel: [    1.172158] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
Feb 11 10:53:59 ryan-laptop kernel: [    1.176335] ata1.00: configured for UDMA/33
Feb 11 10:53:59 ryan-laptop kernel: [    1.180839] scsi 0:0:0:0: CD-ROM            TEAC     CD-ROM CD-224E-N D.AB PQ: 0 ANSI: 5
Feb 11 10:53:59 ryan-laptop kernel: [    1.187127] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
Feb 11 10:53:59 ryan-laptop kernel: [    1.187130] Uniform CD-ROM driver Revision: 3.20
Feb 11 10:53:59 ryan-laptop kernel: [    1.187207] sr 0:0:0:0: Attached scsi CD-ROM sr0
Feb 11 10:53:59 ryan-laptop kernel: [    1.187245] sr 0:0:0:0: Attached scsi generic sg0 type 5
Feb 11 10:53:59 ryan-laptop kernel: [    1.188016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Feb 11 10:53:59 ryan-laptop kernel: [    1.188086] usb usb2: configuration #1 chosen from 1 choice
Feb 11 10:53:59 ryan-laptop kernel: [    1.188110] hub 2-0:1.0: USB hub found
Feb 11 10:53:59 ryan-laptop kernel: [    1.188117] hub 2-0:1.0: 6 ports detected
Feb 11 10:53:59 ryan-laptop kernel: [    1.188178] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 11 10:53:59 ryan-laptop kernel: [    1.188196] uhci_hcd: USB Universal Host Controller Interface driver
Feb 11 10:53:59 ryan-laptop kernel: [    1.188221] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb 11 10:53:59 ryan-laptop kernel: [    1.188230] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    1.188234] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Feb 11 10:53:59 ryan-laptop kernel: [    1.188267] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Feb 11 10:53:59 ryan-laptop kernel: [    1.188298] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
Feb 11 10:53:59 ryan-laptop kernel: [    1.188368] usb usb3: configuration #1 chosen from 1 choice
Feb 11 10:53:59 ryan-laptop kernel: [    1.188391] hub 3-0:1.0: USB hub found
Feb 11 10:53:59 ryan-laptop kernel: [    1.188398] hub 3-0:1.0: 2 ports detected
Feb 11 10:53:59 ryan-laptop kernel: [    1.188443]   alloc irq_desc for 21 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    1.188445]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    1.188450] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Feb 11 10:53:59 ryan-laptop kernel: [    1.188457] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    1.188461] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Feb 11 10:53:59 ryan-laptop kernel: [    1.188490] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Feb 11 10:53:59 ryan-laptop kernel: [    1.188526] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
Feb 11 10:53:59 ryan-laptop kernel: [    1.188597] usb usb4: configuration #1 chosen from 1 choice
Feb 11 10:53:59 ryan-laptop kernel: [    1.188619] hub 4-0:1.0: USB hub found
Feb 11 10:53:59 ryan-laptop kernel: [    1.188625] hub 4-0:1.0: 2 ports detected
Feb 11 10:53:59 ryan-laptop kernel: [    1.188671] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb 11 10:53:59 ryan-laptop kernel: [    1.188678] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    1.188682] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb 11 10:53:59 ryan-laptop kernel: [    1.188714] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Feb 11 10:53:59 ryan-laptop kernel: [    1.188743] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
Feb 11 10:53:59 ryan-laptop kernel: [    1.188814] usb usb5: configuration #1 chosen from 1 choice
Feb 11 10:53:59 ryan-laptop kernel: [    1.188837] hub 5-0:1.0: USB hub found
Feb 11 10:53:59 ryan-laptop kernel: [    1.188843] hub 5-0:1.0: 2 ports detected
Feb 11 10:53:59 ryan-laptop kernel: [    1.188886] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Feb 11 10:53:59 ryan-laptop kernel: [    1.188893] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    1.188896] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb 11 10:53:59 ryan-laptop kernel: [    1.188926] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Feb 11 10:53:59 ryan-laptop kernel: [    1.188954] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
Feb 11 10:53:59 ryan-laptop kernel: [    1.189025] usb usb6: configuration #1 chosen from 1 choice
Feb 11 10:53:59 ryan-laptop kernel: [    1.189049] hub 6-0:1.0: USB hub found
Feb 11 10:53:59 ryan-laptop kernel: [    1.189055] hub 6-0:1.0: 2 ports detected
Feb 11 10:53:59 ryan-laptop kernel: [    1.189095] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Feb 11 10:53:59 ryan-laptop kernel: [    1.189102] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    1.189106] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb 11 10:53:59 ryan-laptop kernel: [    1.189131] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Feb 11 10:53:59 ryan-laptop kernel: [    1.189159] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
Feb 11 10:53:59 ryan-laptop kernel: [    1.189230] usb usb7: configuration #1 chosen from 1 choice
Feb 11 10:53:59 ryan-laptop kernel: [    1.189255] hub 7-0:1.0: USB hub found
Feb 11 10:53:59 ryan-laptop kernel: [    1.189260] hub 7-0:1.0: 2 ports detected
Feb 11 10:53:59 ryan-laptop kernel: [    1.189352] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb 11 10:53:59 ryan-laptop kernel: [    1.192541] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 11 10:53:59 ryan-laptop kernel: [    1.192547] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 11 10:53:59 ryan-laptop kernel: [    1.192599] mice: PS/2 mouse device common for all mice
Feb 11 10:53:59 ryan-laptop kernel: [    1.192698] rtc_cmos 00:03: RTC can wake from S4
Feb 11 10:53:59 ryan-laptop kernel: [    1.192728] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Feb 11 10:53:59 ryan-laptop kernel: [    1.192761] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Feb 11 10:53:59 ryan-laptop kernel: [    1.192855] device-mapper: uevent: version 1.0.3
Feb 11 10:53:59 ryan-laptop kernel: [    1.192944] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Feb 11 10:53:59 ryan-laptop kernel: [    1.193016] device-mapper: multipath: version 1.1.0 loaded
Feb 11 10:53:59 ryan-laptop kernel: [    1.193018] device-mapper: multipath round-robin: version 1.0.0 loaded
Feb 11 10:53:59 ryan-laptop kernel: [    1.193123] EISA: Probing bus 0 at eisa.0
Feb 11 10:53:59 ryan-laptop kernel: [    1.193125] EISA: Cannot allocate resource for mainboard
Feb 11 10:53:59 ryan-laptop kernel: [    1.193128] Cannot allocate resource for EISA slot 1
Feb 11 10:53:59 ryan-laptop kernel: [    1.193130] Cannot allocate resource for EISA slot 2
Feb 11 10:53:59 ryan-laptop kernel: [    1.193156] EISA: Detected 0 cards.
Feb 11 10:53:59 ryan-laptop kernel: [    1.193243] cpuidle: using governor ladder
Feb 11 10:53:59 ryan-laptop kernel: [    1.193295] cpuidle: using governor menu
Feb 11 10:53:59 ryan-laptop kernel: [    1.193702] TCP cubic registered
Feb 11 10:53:59 ryan-laptop kernel: [    1.193842] NET: Registered protocol family 10
Feb 11 10:53:59 ryan-laptop kernel: [    1.194196] lo: Disabled Privacy Extensions
Feb 11 10:53:59 ryan-laptop kernel: [    1.194442] NET: Registered protocol family 17
Feb 11 10:53:59 ryan-laptop kernel: [    1.194459] Bluetooth: L2CAP ver 2.13
Feb 11 10:53:59 ryan-laptop kernel: [    1.194461] Bluetooth: L2CAP socket layer initialized
Feb 11 10:53:59 ryan-laptop kernel: [    1.194463] Bluetooth: SCO (Voice Link) ver 0.6
Feb 11 10:53:59 ryan-laptop kernel: [    1.194465] Bluetooth: SCO socket layer initialized
Feb 11 10:53:59 ryan-laptop kernel: [    1.194494] Bluetooth: RFCOMM TTY layer initialized
Feb 11 10:53:59 ryan-laptop kernel: [    1.194497] Bluetooth: RFCOMM socket layer initialized
Feb 11 10:53:59 ryan-laptop kernel: [    1.194498] Bluetooth: RFCOMM ver 1.11
Feb 11 10:53:59 ryan-laptop kernel: [    1.194530] Using IPI No-Shortcut mode
Feb 11 10:53:59 ryan-laptop kernel: [    1.194587] PM: Resume from disk failed.
Feb 11 10:53:59 ryan-laptop kernel: [    1.194599] registered taskstats version 1
Feb 11 10:53:59 ryan-laptop kernel: [    1.194705]   Magic number: 14:199:881
Feb 11 10:53:59 ryan-laptop kernel: [    1.194807] rtc_cmos 00:03: setting system clock to 2010-02-11 10:53:47 UTC (1265885627)
Feb 11 10:53:59 ryan-laptop kernel: [    1.194810] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 11 10:53:59 ryan-laptop kernel: [    1.194812] EDD information not available.
Feb 11 10:53:59 ryan-laptop kernel: [    1.196114] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Feb 11 10:53:59 ryan-laptop kernel: [    1.500047] Clocksource tsc unstable (delta = -297819366 ns)
Feb 11 10:53:59 ryan-laptop kernel: [    1.684034] usb 5-2: new low speed USB device using uhci_hcd and address 2
Feb 11 10:53:59 ryan-laptop kernel: [    1.796089] ata4.00: SATA link down (SStatus 0 SControl 300)
Feb 11 10:53:59 ryan-laptop kernel: [    1.796112] ata4.01: SATA link down (SStatus 0 SControl 0)
Feb 11 10:53:59 ryan-laptop kernel: [    1.859869] usb 5-2: configuration #1 chosen from 1 choice
Feb 11 10:53:59 ryan-laptop kernel: [    1.940119] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 11 10:53:59 ryan-laptop kernel: [    1.940139] ata3.01: SATA link down (SStatus 0 SControl 300)
Feb 11 10:53:59 ryan-laptop kernel: [    2.022091] ata3.00: ATA-8: ST980411ASG, DE14, max UDMA/133
Feb 11 10:53:59 ryan-laptop kernel: [    2.022094] ata3.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
Feb 11 10:53:59 ryan-laptop kernel: [    2.082230] ata3.00: configured for UDMA/133
Feb 11 10:53:59 ryan-laptop kernel: [    2.082342] scsi 2:0:0:0: Direct-Access     ATA      ST980411ASG      DE14 PQ: 0 ANSI: 5
Feb 11 10:53:59 ryan-laptop kernel: [    2.082454] sd 2:0:0:0: Attached scsi generic sg1 type 0
Feb 11 10:53:59 ryan-laptop kernel: [    2.082490] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Feb 11 10:53:59 ryan-laptop kernel: [    2.082532] sd 2:0:0:0: [sda] Write Protect is off
Feb 11 10:53:59 ryan-laptop kernel: [    2.082535] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 11 10:53:59 ryan-laptop kernel: [    2.082556] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 11 10:53:59 ryan-laptop kernel: [    2.082668]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 sda10 >
Feb 11 10:53:59 ryan-laptop kernel: [    2.188191] sd 2:0:0:0: [sda] Attached SCSI disk
Feb 11 10:53:59 ryan-laptop kernel: [    2.188206] Freeing unused kernel memory: 540k freed
Feb 11 10:53:59 ryan-laptop kernel: [    2.188481] Write protecting the kernel text: 4568k
Feb 11 10:53:59 ryan-laptop kernel: [    2.188508] Write protecting the kernel read-only data: 1836k
Feb 11 10:53:59 ryan-laptop kernel: [    2.355974] Linux agpgart interface v0.103
Feb 11 10:53:59 ryan-laptop kernel: [    2.360154] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Feb 11 10:53:59 ryan-laptop kernel: [    2.360363] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Feb 11 10:53:59 ryan-laptop kernel: [    2.362957] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Feb 11 10:53:59 ryan-laptop kernel: [    2.419782] tg3.c:v3.99 (April 20, 2009)
Feb 11 10:53:59 ryan-laptop kernel: [    2.419843] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 11 10:53:59 ryan-laptop kernel: [    2.419854] tg3 0000:09:00.0: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    2.433126] tg3 0000:09:00.0: PME# disabled
Feb 11 10:53:59 ryan-laptop kernel: [    2.467307] usbcore: registered new interface driver hiddev
Feb 11 10:53:59 ryan-laptop kernel: [    2.481115] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input5
Feb 11 10:53:59 ryan-laptop kernel: [    2.481228] generic-usb 0003:413C:3012.0001: input,hidraw0: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1d.0-2/input0
Feb 11 10:53:59 ryan-laptop kernel: [    2.481245] usbcore: registered new interface driver usbhid
Feb 11 10:53:59 ryan-laptop kernel: [    2.481249] usbhid: v2.6:USB HID core driver
Feb 11 10:53:59 ryan-laptop kernel: [    2.499727] eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:21:70:90:ca:82
Feb 11 10:53:59 ryan-laptop kernel: [    2.499732] eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1])
Feb 11 10:53:59 ryan-laptop kernel: [    2.499734] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Feb 11 10:53:59 ryan-laptop kernel: [    2.499737] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Feb 11 10:53:59 ryan-laptop kernel: [    2.511158] ohci1394 0000:03:01.4: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb 11 10:53:59 ryan-laptop kernel: [    2.549949] [drm] Initialized drm 1.1.0 20060810
Feb 11 10:53:59 ryan-laptop kernel: [    2.565385] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f6aff000-f6aff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Feb 11 10:53:59 ryan-laptop kernel: [    2.567973] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 11 10:53:59 ryan-laptop kernel: [    2.567980] i915 0000:00:02.0: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    2.569947]   alloc irq_desc for 27 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    2.569951]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    2.569961] i915 0000:00:02.0: irq 27 for MSI/MSI-X
Feb 11 10:53:59 ryan-laptop kernel: [    2.676280] integrated sync not supported
Feb 11 10:53:59 ryan-laptop kernel: [    3.131513] integrated sync not supported
Feb 11 10:53:59 ryan-laptop kernel: [    3.429485] [drm] TV-16: set mode NTSC 480i 0
Feb 11 10:53:59 ryan-laptop kernel: [    3.568900] [drm] fb0: inteldrmfb frame buffer device
Feb 11 10:53:59 ryan-laptop kernel: [    3.584955] acpi device:3a: registered as cooling_device1
Feb 11 10:53:59 ryan-laptop kernel: [    3.585601] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:37/input/input6
Feb 11 10:53:59 ryan-laptop kernel: [    3.585637] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Feb 11 10:53:59 ryan-laptop kernel: [    3.585688] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
Feb 11 10:53:59 ryan-laptop kernel: [    3.585752] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:3c/input/input7
Feb 11 10:53:59 ryan-laptop kernel: [    3.585774] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Feb 11 10:53:59 ryan-laptop kernel: [    3.585793] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Feb 11 10:53:59 ryan-laptop kernel: [    3.671703] [drm] TV-16: set mode 848x480 1d
Feb 11 10:53:59 ryan-laptop kernel: [    3.777395] [drm] LVDS-8: set mode 1024x768 1e
Feb 11 10:53:59 ryan-laptop kernel: [    4.038104] Console: switching to colour frame buffer device 106x30
Feb 11 10:53:59 ryan-laptop kernel: [    4.092156] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[374fc0000ef2dde1]
Feb 11 10:53:59 ryan-laptop kernel: [    4.344378] PM: Starting manual resume from disk
Feb 11 10:53:59 ryan-laptop kernel: [    4.344383] PM: Resume from partition 8:3
Feb 11 10:53:59 ryan-laptop kernel: [    4.344385] PM: Checking hibernation image.
Feb 11 10:53:59 ryan-laptop kernel: [    4.344706] PM: Resume from disk failed.
Feb 11 10:53:59 ryan-laptop kernel: [    4.347929] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
Feb 11 10:53:59 ryan-laptop kernel: [    4.347933] EXT4-fs (sda2): write access will be enabled during recovery
Feb 11 10:53:59 ryan-laptop kernel: [    4.365400] EXT4-fs (sda2): barriers enabled
Feb 11 10:53:59 ryan-laptop kernel: [    4.426480] kjournald2 starting: pid 393, dev sda2:8, commit interval 5 seconds
Feb 11 10:53:59 ryan-laptop kernel: [    4.426499] EXT4-fs (sda2): delayed allocation enabled
Feb 11 10:53:59 ryan-laptop kernel: [    4.426502] EXT4-fs: file extents enabled
Feb 11 10:53:59 ryan-laptop kernel: [    4.426593] EXT4-fs: mballoc enabled
Feb 11 10:53:59 ryan-laptop kernel: [    4.426606] EXT4-fs (sda2): recovery complete
Feb 11 10:53:59 ryan-laptop kernel: [    4.427818] EXT4-fs (sda2): mounted filesystem with ordered data mode
Feb 11 10:53:59 ryan-laptop kernel: [    4.920316] type=1505 audit(1265885631.225:2): operation="profile_load" pid=416 name=/usr/share/gdm/guest-session/Xsession
Feb 11 10:53:59 ryan-laptop kernel: [    4.923574] type=1505 audit(1265885631.225:3): operation="profile_load" pid=417 name=/sbin/dhclient3
Feb 11 10:53:59 ryan-laptop kernel: [    4.924332] type=1505 audit(1265885631.229:4): operation="profile_load" pid=417 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb 11 10:53:59 ryan-laptop kernel: [    4.924736] type=1505 audit(1265885631.229:5): operation="profile_load" pid=417 name=/usr/lib/connman/scripts/dhclient-script
Feb 11 10:53:59 ryan-laptop kernel: [    4.982570] type=1505 audit(1265885631.285:6): operation="profile_load" pid=418 name=/usr/bin/evince
Feb 11 10:53:59 ryan-laptop kernel: [    4.994592] type=1505 audit(1265885631.297:7): operation="profile_load" pid=418 name=/usr/bin/evince-previewer
Feb 11 10:53:59 ryan-laptop kernel: [    5.001650] type=1505 audit(1265885631.305:8): operation="profile_load" pid=418 name=/usr/bin/evince-thumbnailer
Feb 11 10:53:59 ryan-laptop kernel: [    5.012134] type=1505 audit(1265885631.317:9): operation="profile_load" pid=420 name=/usr/lib/cups/backend/cups-pdf
Feb 11 10:53:59 ryan-laptop kernel: [    5.012992] type=1505 audit(1265885631.317:10): operation="profile_load" pid=420 name=/usr/sbin/cupsd
Feb 11 10:53:59 ryan-laptop kernel: [    5.733105] udev: starting version 147
Feb 11 10:53:59 ryan-laptop kernel: [    5.764522] Adding 1951888k swap on /dev/sda3.  Priority:-1 extents:1 across:1951888k 
Feb 11 10:53:59 ryan-laptop kernel: [    6.561636] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Feb 11 10:53:59 ryan-laptop kernel: [    6.577096] input: Dell WMI hotkeys as /devices/virtual/input/input8
Feb 11 10:53:59 ryan-laptop kernel: [    6.732232] cfg80211: Calling CRDA to update world regulatory domain
Feb 11 10:53:59 ryan-laptop kernel: [    6.981478] lp: driver loaded but no devices found
Feb 11 10:53:59 ryan-laptop kernel: [    7.096096] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
Feb 11 10:53:59 ryan-laptop kernel: [    7.115195] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
Feb 11 10:53:59 ryan-laptop kernel: [    7.161121] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0200]
Feb 11 10:53:59 ryan-laptop kernel: [    7.161149] yenta_cardbus 0000:03:01.0: O2: res at 0x94/0xD4: 00/ea
Feb 11 10:53:59 ryan-laptop kernel: [    7.161152] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst
Feb 11 10:53:59 ryan-laptop kernel: [    7.288980] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
Feb 11 10:53:59 ryan-laptop kernel: [    7.288985] yenta_cardbus 0000:03:01.0: Socket status: 30000006
Feb 11 10:53:59 ryan-laptop kernel: [    7.288989] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
Feb 11 10:53:59 ryan-laptop kernel: [    7.288999] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
Feb 11 10:53:59 ryan-laptop kernel: [    7.289002] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
Feb 11 10:53:59 ryan-laptop kernel: [    7.289177] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xf6a00000 - 0xf6afffff
Feb 11 10:53:59 ryan-laptop kernel: [    7.289179] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
Feb 11 10:53:59 ryan-laptop kernel: [    7.415360] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Feb 11 10:53:59 ryan-laptop kernel: [    7.415364] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Feb 11 10:53:59 ryan-laptop kernel: [    7.415492] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 11 10:53:59 ryan-laptop kernel: [    7.415508] iwl3945 0000:0c:00.0: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    7.498893] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Feb 11 10:53:59 ryan-laptop kernel: [    7.498897] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
Feb 11 10:53:59 ryan-laptop kernel: [    7.499016]   alloc irq_desc for 28 on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    7.499018]   alloc kstat_irqs on node -1
Feb 11 10:53:59 ryan-laptop kernel: [    7.499130] iwl3945 0000:0c:00.0: irq 28 for MSI/MSI-X
Feb 11 10:53:59 ryan-laptop kernel: [    7.624383] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 11 10:53:59 ryan-laptop kernel: [    7.758034] phy0: Selected rate control algorithm 'iwl-3945-rs'
Feb 11 10:53:59 ryan-laptop kernel: [    8.165481] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Feb 11 10:53:59 ryan-laptop kernel: [    8.167418] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
Feb 11 10:53:59 ryan-laptop kernel: [    8.168223] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Feb 11 10:53:59 ryan-laptop kernel: [    8.168895] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Feb 11 10:53:59 ryan-laptop kernel: [    8.169546] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Feb 11 10:53:59 ryan-laptop kernel: [    8.248056] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 11 10:53:59 ryan-laptop kernel: [    8.248086] HDA Intel 0000:00:1b.0: setting latency timer to 64
Feb 11 10:53:59 ryan-laptop kernel: [    8.403193] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
Feb 11 10:53:59 ryan-laptop kernel: [    8.452400] input: HDA Intel Line In at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Feb 11 10:53:59 ryan-laptop kernel: [    8.452476] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Feb 11 10:53:59 ryan-laptop kernel: [   10.199322] EXT4-fs (sda2): internal journal on sda2:8
Feb 11 10:53:59 ryan-laptop kernel: [   10.360848] EXT4-fs (sda10): barriers enabled
Feb 11 10:53:59 ryan-laptop kernel: [   10.369996] kjournald2 starting: pid 853, dev sda10:8, commit interval 5 seconds
Feb 11 10:53:59 ryan-laptop kernel: [   10.370462] EXT4-fs (sda10): internal journal on sda10:8
Feb 11 10:53:59 ryan-laptop kernel: [   10.370466] EXT4-fs (sda10): delayed allocation enabled
Feb 11 10:53:59 ryan-laptop kernel: [   10.370469] EXT4-fs: file extents enabled
Feb 11 10:53:59 ryan-laptop kernel: [   10.374518] EXT4-fs: mballoc enabled
Feb 11 10:53:59 ryan-laptop kernel: [   10.374532] EXT4-fs (sda10): mounted filesystem with ordered data mode
Feb 11 10:53:59 ryan-laptop kernel: [   10.895172] EXT4-fs (sda5): barriers enabled
Feb 11 10:53:59 ryan-laptop kernel: [   10.903121] kjournald2 starting: pid 865, dev sda5:8, commit interval 5 seconds
Feb 11 10:53:59 ryan-laptop kernel: [   10.905341] EXT4-fs (sda5): internal journal on sda5:8
Feb 11 10:53:59 ryan-laptop kernel: [   10.905344] EXT4-fs (sda5): delayed allocation enabled
Feb 11 10:53:59 ryan-laptop kernel: [   10.905347] EXT4-fs: file extents enabled
Feb 11 10:53:59 ryan-laptop kernel: [   10.905402] EXT4-fs: mballoc enabled
Feb 11 10:53:59 ryan-laptop kernel: [   10.905416] EXT4-fs (sda5): mounted filesystem with ordered data mode
Feb 11 10:53:59 ryan-laptop kernel: [   11.339071] EXT4-fs (sda6): barriers enabled
Feb 11 10:53:59 ryan-laptop kernel: [   11.341897] kjournald2 starting: pid 875, dev sda6:8, commit interval 5 seconds
Feb 11 10:53:59 ryan-laptop kernel: [   11.342405] EXT4-fs (sda6): internal journal on sda6:8
Feb 11 10:53:59 ryan-laptop kernel: [   11.342408] EXT4-fs (sda6): delayed allocation enabled
Feb 11 10:53:59 ryan-laptop kernel: [   11.342411] EXT4-fs: file extents enabled
Feb 11 10:53:59 ryan-laptop kernel: [   11.342909] EXT4-fs: mballoc enabled
Feb 11 10:53:59 ryan-laptop kernel: [   11.342924] EXT4-fs (sda6): mounted filesystem with ordered data mode
Feb 11 10:53:59 ryan-laptop kernel: [   11.987274] EXT4-fs (sda7): barriers enabled
Feb 11 10:53:59 ryan-laptop kernel: [   11.988310] kjournald2 starting: pid 887, dev sda7:8, commit interval 5 seconds
Feb 11 10:53:59 ryan-laptop kernel: [   11.988806] EXT4-fs (sda7): internal journal on sda7:8
Feb 11 10:53:59 ryan-laptop kernel: [   11.988809] EXT4-fs (sda7): delayed allocation enabled
Feb 11 10:53:59 ryan-laptop kernel: [   11.988812] EXT4-fs: file extents enabled
Feb 11 10:53:59 ryan-laptop kernel: [   11.988887] EXT4-fs: mballoc enabled
Feb 11 10:53:59 ryan-laptop kernel: [   11.988901] EXT4-fs (sda7): mounted filesystem with ordered data mode
Feb 11 10:53:59 ryan-laptop kernel: [   12.995179] EXT4-fs (sda8): barriers enabled
Feb 11 10:53:59 ryan-laptop kernel: [   12.995523] kjournald2 starting: pid 905, dev sda8:8, commit interval 5 seconds
Feb 11 10:53:59 ryan-laptop kernel: [   12.995934] EXT4-fs (sda8): internal journal on sda8:8
Feb 11 10:53:59 ryan-laptop kernel: [   12.995937] EXT4-fs (sda8): delayed allocation enabled
Feb 11 10:53:59 ryan-laptop kernel: [   12.995940] EXT4-fs: file extents enabled
Feb 11 10:53:59 ryan-laptop kernel: [   12.996078] EXT4-fs: mballoc enabled
Feb 11 10:53:59 ryan-laptop kernel: [   12.996092] EXT4-fs (sda8): mounted filesystem with ordered data mode
Feb 11 10:53:59 ryan-laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Feb 11 10:54:00 ryan-laptop init: ureadahead-other main process (957) terminated with status 4
Feb 11 10:54:00 ryan-laptop kernel: [   14.187541] __ratelimit: 3 callbacks suppressed
Feb 11 10:54:00 ryan-laptop kernel: [   14.187544] type=1505 audit(1265914440.489:12): operation="profile_replace" pid=971 name=/usr/share/gdm/guest-session/Xsession
Feb 11 10:54:00 ryan-laptop kernel: [   14.189999] type=1505 audit(1265914440.493:13): operation="profile_replace" pid=972 name=/sbin/dhclient3
Feb 11 10:54:00 ryan-laptop kernel: [   14.190739] type=1505 audit(1265914440.493:14): operation="profile_replace" pid=972 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb 11 10:54:00 ryan-laptop kernel: [   14.191136] type=1505 audit(1265914440.493:15): operation="profile_replace" pid=972 name=/usr/lib/connman/scripts/dhclient-script
Feb 11 10:54:00 ryan-laptop kernel: [   14.195853] type=1505 audit(1265914440.497:16): operation="profile_replace" pid=973 name=/usr/bin/evince
Feb 11 10:54:00 ryan-laptop kernel: [   14.209252] type=1505 audit(1265914440.513:17): operation="profile_replace" pid=973 name=/usr/bin/evince-previewer
Feb 11 10:54:00 ryan-laptop kernel: [   14.217000] type=1505 audit(1265914440.521:18): operation="profile_replace" pid=973 name=/usr/bin/evince-thumbnailer
Feb 11 10:54:00 ryan-laptop kernel: [   14.227368] type=1505 audit(1265914440.529:19): operation="profile_replace" pid=975 name=/usr/lib/cups/backend/cups-pdf
Feb 11 10:54:00 ryan-laptop kernel: [   14.228308] EXT4-fs (sda9): barriers enabled
Feb 11 10:54:00 ryan-laptop kernel: [   14.228789] type=1505 audit(1265914440.533:20): operation="profile_replace" pid=975 name=/usr/sbin/cupsd
Feb 11 10:54:00 ryan-laptop kernel: [   14.231392] type=1505 audit(1265914440.533:21): operation="profile_replace" pid=976 name=/usr/sbin/tcpdump
Feb 11 10:54:00 ryan-laptop kernel: [   14.232604] kjournald2 starting: pid 977, dev sda9:8, commit interval 5 seconds
Feb 11 10:54:00 ryan-laptop kernel: [   14.235624] EXT4-fs (sda9): internal journal on sda9:8
Feb 11 10:54:00 ryan-laptop kernel: [   14.235630] EXT4-fs (sda9): delayed allocation enabled
Feb 11 10:54:00 ryan-laptop kernel: [   14.235634] EXT4-fs: file extents enabled
Feb 11 10:54:00 ryan-laptop kernel: [   14.235817] EXT4-fs: mballoc enabled
Feb 11 10:54:00 ryan-laptop kernel: [   14.235832] EXT4-fs (sda9): mounted filesystem with ordered data mode
Feb 11 10:54:00 ryan-laptop avahi-daemon[1003]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Feb 11 10:54:00 ryan-laptop avahi-daemon[1003]: Successfully dropped root privileges.
Feb 11 10:54:00 ryan-laptop avahi-daemon[1003]: avahi-daemon 0.6.25 starting up.
Feb 11 10:54:00 ryan-laptop avahi-daemon[1003]: Successfully called chroot().
Feb 11 10:54:00 ryan-laptop avahi-daemon[1003]: Successfully dropped remaining capabilities.
Feb 11 10:54:01 ryan-laptop avahi-daemon[1003]: No service file found in /etc/avahi/services.
Feb 11 10:54:01 ryan-laptop avahi-daemon[1003]: Network interface enumeration completed.
Feb 11 10:54:01 ryan-laptop avahi-daemon[1003]: Registering HINFO record with values 'I686'/'LINUX'.
Feb 11 10:54:01 ryan-laptop avahi-daemon[1003]: Server startup complete. Host name is ryan-laptop.local. Local service cookie is 1630146482.
Feb 11 10:54:01 ryan-laptop NetworkManager: <info>  starting...
Feb 11 10:54:01 ryan-laptop NetworkManager: <info>  Trying to start the modem-manager...
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: init!
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0)
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wmaster0, iface: wmaster0)
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wmaster0, iface: wmaster0): no ifupdown configuration found.
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0, iface: eth0)
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: end _init.
Feb 11 10:54:01 ryan-laptop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin Sierra
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin Option
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin Generic
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin Huawei
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin Gobi
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin Novatel
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin ZTE
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin Nokia
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin Ericsson MBM
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin Option High-Speed
Feb 11 10:54:01 ryan-laptop modem-manager: Loaded plugin MotoC
Feb 11 10:54:01 ryan-laptop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 11 10:54:01 ryan-laptop NetworkManager: <info>  Found radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
Feb 11 10:54:01 ryan-laptop NetworkManager: <info>  Found radio killswitch rfkill0 (at /sys/devices/virtual/rfkill/rfkill0) (driver <unknown>)
Feb 11 10:54:01 ryan-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: (158907120) ... get_connections.
Feb 11 10:54:01 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: (158907120) ... get_connections (managed=false): return empty list.
Feb 11 10:54:02 ryan-laptop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945')
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (wlan0): now managed
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (wlan0): bringing up device.
Feb 11 10:54:02 ryan-laptop kernel: [   15.944065] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
Feb 11 10:54:02 ryan-laptop gdm-binary[1010]: WARNING: Unable to find users: no seat-id found
Feb 11 10:54:02 ryan-laptop kernel: [   16.423005] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
Feb 11 10:54:02 ryan-laptop anacron[1191]: Anacron 2.3 started on 2010-02-11
Feb 11 10:54:02 ryan-laptop kernel: [   16.494308] Registered led device: iwl-phy0::radio
Feb 11 10:54:02 ryan-laptop kernel: [   16.494326] Registered led device: iwl-phy0::assoc
Feb 11 10:54:02 ryan-laptop kernel: [   16.494378] Registered led device: iwl-phy0::RX
Feb 11 10:54:02 ryan-laptop kernel: [   16.494392] Registered led device: iwl-phy0::TX
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (wlan0): preparing device.
Feb 11 10:54:02 ryan-laptop kernel: [   16.497798] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 11 10:54:02 ryan-laptop kernel: [   16.499197] tg3 0000:09:00.0: PME# disabled
Feb 11 10:54:02 ryan-laptop kernel: [   16.499307]   alloc irq_desc for 29 on node -1
Feb 11 10:54:02 ryan-laptop kernel: [   16.499309]   alloc kstat_irqs on node -1
Feb 11 10:54:02 ryan-laptop kernel: [   16.499328] tg3 0000:09:00.0: irq 29 for MSI/MSI-X
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Feb 11 10:54:02 ryan-laptop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (eth0): carrier is OFF
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3')
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (eth0): now managed
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (eth0): bringing up device.
Feb 11 10:54:02 ryan-laptop init: apport pre-start process (1148) terminated with status 1
Feb 11 10:54:02 ryan-laptop kernel: [   16.584560] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (eth0): preparing device.
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Feb 11 10:54:02 ryan-laptop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  modem-manager is now available
Feb 11 10:54:02 ryan-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Feb 11 10:54:02 ryan-laptop NetworkManager: <info>  Trying to start the supplicant...
Feb 11 10:54:02 ryan-laptop init: apport post-stop process (1193) terminated with status 1
Feb 11 10:54:02 ryan-laptop cron[1171]: (CRON) INFO (pidfile fd = 3)
Feb 11 10:54:02 ryan-laptop cron[1200]: (CRON) STARTUP (fork ok)
Feb 11 10:54:03 ryan-laptop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Feb 11 10:54:03 ryan-laptop cron[1200]: (CRON) INFO (Running @reboot jobs)
Feb 11 10:54:03 ryan-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Feb 11 10:54:03 ryan-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Feb 11 10:54:03 ryan-laptop anacron[1191]: Will run job `cron.daily' in 5 min.
Feb 11 10:54:03 ryan-laptop anacron[1191]: Will run job `cron.weekly' in 10 min.
Feb 11 10:54:03 ryan-laptop anacron[1191]: Jobs will be executed sequentially
Feb 11 10:54:03 ryan-laptop gdm-binary[1010]: WARNING: GdmDisplay: display lasted 1.102920 seconds
Feb 11 10:54:04 ryan-laptop acpid: client connected from 1243[0:0]
Feb 11 10:54:04 ryan-laptop acpid: client connected from 1273[107:114]
Feb 11 10:54:04 ryan-laptop kernel: [   18.145938] integrated sync not supported
Feb 11 10:54:04 ryan-laptop kernel: [   18.369730] integrated sync not supported
Feb 11 10:54:04 ryan-laptop wpa_supplicant[1196]: CTRL-EVENT-SCAN-RESULTS 
Feb 11 10:54:04 ryan-laptop kernel: [   18.606265] [drm] TV-16: set mode 1024x768 20
Feb 11 10:54:06 ryan-laptop kernel: [   19.792108] ppdev: user-space parallel port driver
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Feb 11 10:54:06 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-0:1.0
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-2
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb6
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb6/6-0:1.0
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb7
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb7/7-0:1.0
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Feb 11 10:54:06 ryan-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Feb 11 10:54:06 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:54:06 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:54:06 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:54:06 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Feb 11 10:54:06 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:54:06 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:54:06 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:54:06 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:54:06 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:54:06 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5/5-2
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Device vendor/product is 413C:3012
Feb 11 10:54:06 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:54:06 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb6
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:54:06 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:54:06 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Feb 11 10:54:06 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Failed to get parent
Feb 11 10:54:06 ryan-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb7
Feb 11 10:54:06 ryan-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Feb 11 10:54:06 ryan-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Feb 11 10:54:07 ryan-laptop console-kit-daemon[1032]: WARNING: Couldn't read /proc/1013/environ: Failed to open file '/proc/1013/environ': No such file or directory
Feb 11 10:54:09 ryan-laptop pulseaudio[1585]: pid.c: Stale PID file, overwriting.
Feb 11 10:54:12 ryan-laptop kernel: [   25.974413] integrated sync not supported
Feb 11 10:54:12 ryan-laptop kernel: [   26.174662] integrated sync not supported
Feb 11 10:54:12 ryan-laptop kernel: [   26.374705] integrated sync not supported
Feb 11 10:54:15 ryan-laptop kernel: [   28.973679] integrated sync not supported
Feb 11 10:54:24 ryan-laptop wpa_supplicant[1196]: CTRL-EVENT-SCAN-RESULTS 
Feb 11 10:55:05 ryan-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Feb 11 10:55:05 ryan-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="879" x-info="http://www.rsyslog.com"] (re)start
Feb 11 10:55:05 ryan-laptop rsyslogd: rsyslogd's groupid changed to 102
Feb 11 10:55:05 ryan-laptop rsyslogd: rsyslogd's useriFeb 11 11:37:17 ryan-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
```

---

