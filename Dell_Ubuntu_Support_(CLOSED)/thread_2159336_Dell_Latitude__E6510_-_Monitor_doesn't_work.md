---
title: "Dell Latitude | E6510 - Monitor doesn't work"
date: 2013-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tiagoarruda on 2013-07-02
Hi everyone,

I'm using ubuntu 12.10 on a Dell LATITUDE E6510. 
Everytime I connect a monitor on my laptop ubuntu freezes after a while. 
I've found in some posts that I could solve this by updating my kernel, so I updated it to kernel 3.10. 
After that ubuntu did stopped to freeze with the monitor connected, but 3.10 is unstable and I had other issues with wireless and vmware that make me give up that version, right know I'm using kernel 3.9 and it has the same issue with the monitor (it is the last stable version).

Here it goes some data about my system:

DELL LATITUDE | E6510

Kernel: 3.9.8-030908-generic


Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal



I'm just joining the Ubuntu Forums community, thanks in advance for the help.

---

### Post by tiagoarruda on 2013-07-02
I've reproduced the freeze and collected [COLOR=#333333][FONT=monospace]dmesg and [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]/var/log/Xorg.0.log.
Here are the results:

[SIZE=5][B]dmesg
[/B][/SIZE]
[/FONT][/COLOR][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.9.8-030908-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201306271518 SMP Thu Jun 27 19:19:16 UTC 2013
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.9.8-030908-generic root=UUID=69eecf32-b1e4-436a-801e-e382a458ebba ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000095bff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000095c00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cf65efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cf65f000-0x00000000cf67efff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cf67f000-0x00000000cf76efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cf76f000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1b000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Dell Inc. Latitude E6510/0N5KHN, BIOS A07 02/15/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x230000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF0000000 write-back
[    0.000000]   3 base 100000000 mask F00000000 write-back
[    0.000000]   4 base 200000000 mask FC0000000 write-back
[    0.000000]   5 base 230000000 mask FF0000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 1GB, type WB
[    0.000000] reg 5, base: 8960MB, range: 256MB, type UC
[    0.000000] total RAM covered: 8192M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64K 	num_reg: 6  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 512MB, type WB
[    0.000000] reg 5, base: 8704MB, range: 256MB, type WB
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcf65f max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f2190-0x000f219f] mapped at [ffff8800000f2190]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff88000008f000] 8f000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01f61000, 0x01f61fff] PGTABLE
[    0.000000] BRK [0x01f62000, 0x01f62fff] PGTABLE
[    0.000000] BRK [0x01f63000, 0x01f63fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22fe00000-0x22fffffff]
[    0.000000]  [mem 0x22fe00000-0x22fffffff] page 2M
[    0.000000] BRK [0x01f64000, 0x01f64fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22c000000-0x22fdfffff]
[    0.000000]  [mem 0x22c000000-0x22fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x22bffffff]
[    0.000000]  [mem 0x200000000-0x22bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcf65efff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xcf5fffff] page 2M
[    0.000000]  [mem 0xcf600000-0xcf65efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] BRK [0x01f65000, 0x01f65fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x363da000-0x371e4fff]
[    0.000000] ACPI: RSDP 00000000000fe300 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000cf67de18 00064 (v01 DELL    E2      06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000cf75fc18 000F4 (v04 DELL    E2      06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20130117/tbfadt-395)
[    0.000000] ACPI BIOS Bug: Warning: 32/64X FACS address mismatch in FADT - 0xCF76BF40/0x00000000CF76ED40, using 32 (20130117/tbfadt-522)
[    0.000000] ACPI: DSDT 00000000cf73e018 0A6C6 (v01 DELL    E2      00001001 INTL 20080729)
[    0.000000] ACPI: FACS 00000000cf76bf40 00040
[    0.000000] ACPI: APIC 00000000cf67cf18 0008C (v02 DELL    E2      06222004 MSFT 00010013)
[    0.000000] ACPI: TCPA 00000000cf76dd18 00032 (v02                 00000000      00000000)
[    0.000000] ACPI: MCFG 00000000cf76dc98 0003C (v01 A M I  GMCH945. 06222004 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cf76dc18 00038 (v01 DELL    E2      00000001 ASL  00000061)
[    0.000000] ACPI: BOOT 00000000cf76db98 00028 (v01 DELL   E2       06222004 AMI  00010013)
[    0.000000] ACPI: SLIC 00000000cf766818 00176 (v03 DELL    E2      06222004 MSFT 00010013)
[    0.000000] ACPI: SSDT 00000000cf74d018 009F1 (v01  PmRef    CpuPm 00003000 INTL 20080729)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22fffffff]
[    0.000000]   NODE_DATA [mem 0x22fff4000-0x22fff8fff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880227600000-ffff88022f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00094fff]
[    0.000000]   node   0: [mem 0x00100000-0xcf65efff]
[    0.000000]   node   0: [mem 0x100000000-0x22fffffff]
[    0.000000] On node 0 totalpages: 2094579
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3988 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13210 pages used for memmap
[    0.000000]   DMA32 zone: 845407 pages, LIFO batch:31
[    0.000000]   Normal zone: 19456 pages used for memmap
[    0.000000]   Normal zone: 1245184 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000095000 - 0000000000096000
[    0.000000] PM: Registered nosave memory: 0000000000096000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cf65f000 - 00000000cf67f000
[    0.000000] PM: Registered nosave memory: 00000000cf67f000 - 00000000cf76f000
[    0.000000] PM: Registered nosave memory: 00000000cf76f000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed1b000
[    0.000000] PM: Registered nosave memory: 00000000fed1b000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff800000
[    0.000000] PM: Registered nosave memory: 00000000ff800000 - 0000000100000000
[    0.000000] e820: [mem 0xd0000000-0xf7ffffff] available for PCI devices
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88022fc00000 s81472 r8192 d20928 u262144
[    0.000000] pcpu-alloc: s81472 r8192 d20928 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2061828
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.9.8-030908-generic root=UUID=69eecf32-b1e4-436a-801e-e382a458ebba ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8149800k/9175040k available (7061k kernel code, 796724k absent, 228516k reserved, 6160k data, 1136k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1728.939 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.87 BogoMIPS (lpj=6915756)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000033] Security Framework initialized
[    0.000046] AppArmor: AppArmor initialized
[    0.000047] Yama: becoming mindful.
[    0.000744] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002817] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003672] Mount-cache hash table entries: 256
[    0.003891] Initializing cgroup subsys cpuacct
[    0.003894] Initializing cgroup subsys memory
[    0.003902] Initializing cgroup subsys devices
[    0.003904] Initializing cgroup subsys freezer
[    0.003905] Initializing cgroup subsys blkio
[    0.003907] Initializing cgroup subsys perf_event
[    0.003910] Initializing cgroup subsys hugetlb
[    0.003934] CPU: Physical Processor ID: 0
[    0.003935] CPU: Processor Core ID: 0
[    0.003939] mce: CPU supports 9 MCE banks
[    0.003949] CPU0: Thermal monitoring handled by SMI
[    0.003959] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.003959] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.003959] tlb_flushall_shift: 6
[    0.004056] Freeing SMP alternatives: 24k freed
[    0.004063] ACPI: Core revision 20130117
[    0.010656] ACPI: All ACPI Tables successfully acquired
[    0.011793] ftrace: allocating 28947 entries in 114 pages
[    0.030369] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.070036] smpboot: CPU0: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz (fam: 06, model: 1e, stepping: 05)
[    0.176716] Performance Events: PEBS fmt1+, 16-deep LBR, Nehalem events, Intel PMU driver.
[    0.176722] perf_event_intel: CPU erratum AAJ80 worked around
[    0.176724] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.176726] ... version:                3
[    0.176727] ... bit width:              48
[    0.176728] ... generic registers:      4
[    0.176730] ... value mask:             0000ffffffffffff
[    0.176731] ... max period:             000000007fffffff
[    0.176732] ... fixed-purpose events:   3
[    0.176733] ... event mask:             000000070000000f
[    0.189155] CPU1: Thermal monitoring handled by SMI
[    0.191347] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.202493] CPU2: Thermal monitoring handled by SMI
[    0.227189] CPU3: Thermal monitoring handled by SMI
[    0.240413] CPU4: Thermal monitoring handled by SMI
[    0.253682] CPU5: Thermal monitoring handled by SMI
[    0.266933] CPU6: Thermal monitoring handled by SMI
[    0.178111] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 OK
[    0.280189] CPU7: Thermal monitoring handled by SMI
[    0.282308] Brought up 8 CPUs
[    0.282312] smpboot: Total of 8 processors activated (27663.02 BogoMIPS)
[    0.287892] devtmpfs: initialized
[    0.289492] EVM: security.selinux
[    0.289494] EVM: security.SMACK64
[    0.289495] EVM: security.capability
[    0.289550] PM: Registering ACPI NVS region [mem 0xcf67f000-0xcf76efff] (983040 bytes)
[    0.290676] regulator-dummy: no parameters
[    0.290736] NET: Registered protocol family 16
[    0.290895] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.290898] ACPI: bus type PCI registered
[    0.290988] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.290991] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.295688] PCI: Using configuration type 1 for base access
[    0.295696] dmi type 0xB1 record - unknown flag
[    0.296899] bio: create slab <bio-0> at 0
[    0.297008] ACPI: Added _OSI(Module Device)
[    0.297010] ACPI: Added _OSI(Processor Device)
[    0.297012] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.297014] ACPI: Added _OSI(Processor Aggregator Device)
[    0.298592] ACPI: EC: Look up EC in DSDT
[    0.304498] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.314174] ACPI: SSDT 00000000cf7eaa98 0032A (v01  PmRef  Cpu0Ist 00003000 INTL 20080729)
[    0.314563] ACPI: Dynamic OEM Table Load:
[    0.314566] ACPI: SSDT           (null) 0032A (v01  PmRef  Cpu0Ist 00003000 INTL 20080729)
[    0.314718] ACPI: SSDT 00000000cf7e9018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20080729)
[    0.315081] ACPI: Dynamic OEM Table Load:
[    0.315084] ACPI: SSDT           (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20080729)
[    0.315413] ACPI: SSDT 00000000cf7ea718 00303 (v01  PmRef    ApIst 00003000 INTL 20080729)
[    0.315854] ACPI: Dynamic OEM Table Load:
[    0.315857] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20080729)
[    0.315990] ACPI: SSDT 00000000cf7e8d98 00119 (v01  PmRef    ApCst 00003000 INTL 20080729)
[    0.316388] ACPI: Dynamic OEM Table Load:
[    0.316391] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20080729)
[    0.319377] ACPI: Interpreter enabled
[    0.319385] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130117/hwxface-568)
[    0.319391] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130117/hwxface-568)
[    0.319406] ACPI: (supports S0 S3 S4 S5)
[    0.319408] ACPI: Using IOAPIC for interrupt routing
[    0.319443] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.355805] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.355849] \_SB_.PCI0:_OSC invalid UUID
[    0.355850] _OSC request data:1 8 0 
[    0.356633] PCI host bridge to bus 0000:00
[    0.356637] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.356640] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.356642] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.356644] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.356647] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xfeafffff]
[    0.356658] pci 0000:00:00.0: [8086:d132] type 00 class 0x060000
[    0.356780] pci 0000:00:03.0: [8086:d138] type 01 class 0x060400
[    0.356837] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.356879] pci 0000:00:03.0: System wakeup disabled by ACPI
[    0.356922] pci 0000:00:08.0: [8086:d155] type 00 class 0x088000
[    0.357029] pci 0000:00:08.1: [8086:d156] type 00 class 0x088000
[    0.357134] pci 0000:00:08.2: [8086:d157] type 00 class 0x088000
[    0.357257] pci 0000:00:08.3: [8086:d158] type 00 class 0x088000
[    0.357380] pci 0000:00:10.0: [8086:d150] type 00 class 0x088000
[    0.357487] pci 0000:00:10.1: [8086:d151] type 00 class 0x088000
[    0.357623] pci 0000:00:19.0: [8086:10ea] type 00 class 0x020000
[    0.357656] pci 0000:00:19.0: reg 10: [mem 0xe9600000-0xe961ffff]
[    0.357670] pci 0000:00:19.0: reg 14: [mem 0xe9680000-0xe9680fff]
[    0.357684] pci 0000:00:19.0: reg 18: [io  0x8040-0x805f]
[    0.357758] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.357799] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.357849] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.357881] pci 0000:00:1a.0: reg 10: [mem 0xe9670000-0xe96703ff]
[    0.357983] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.358040] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.358089] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.358114] pci 0000:00:1b.0: reg 10: [mem 0xe9660000-0xe9663fff 64bit]
[    0.358194] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.358224] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.358275] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.358358] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.358392] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.358436] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.358518] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.358552] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.358598] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400
[    0.358679] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.358714] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.358758] pci 0000:00:1c.3: [8086:3b48] type 01 class 0x060400
[    0.358839] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.358875] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.358925] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.358956] pci 0000:00:1d.0: reg 10: [mem 0xe9650000-0xe96503ff]
[    0.359053] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.359111] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.359155] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.359232] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.359278] pci 0000:00:1f.0: [8086:3b07] type 00 class 0x060100
[    0.359453] pci 0000:00:1f.2: [8086:282a] type 00 class 0x010400
[    0.359482] pci 0000:00:1f.2: reg 10: [io  0x8090-0x8097]
[    0.359496] pci 0000:00:1f.2: reg 14: [io  0x8080-0x8083]
[    0.359509] pci 0000:00:1f.2: reg 18: [io  0x8070-0x8077]
[    0.359522] pci 0000:00:1f.2: reg 1c: [io  0x8060-0x8063]
[    0.359535] pci 0000:00:1f.2: reg 20: [io  0x8020-0x803f]
[    0.359548] pci 0000:00:1f.2: reg 24: [mem 0xe9640000-0xe96407ff]
[    0.359606] pci 0000:00:1f.2: PME# supported from D3hot
[    0.359692] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.359718] pci 0000:00:1f.3: reg 10: [mem 0xe9630000-0xe96300ff 64bit]
[    0.359744] pci 0000:00:1f.3: reg 20: [io  0x8000-0x801f]
[    0.359897] pci 0000:01:00.0: [10de:0a6c] type 00 class 0x030000
[    0.359907] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff]
[    0.359918] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.359928] pci 0000:01:00.0: reg 1c: [mem 0xe0000000-0xe1ffffff 64bit pref]
[    0.359936] pci 0000:01:00.0: reg 24: [io  0x7000-0x707f]
[    0.359943] pci 0000:01:00.0: reg 30: [mem 0xe3000000-0xe307ffff pref]
[    0.360027] pci 0000:01:00.1: [10de:0be3] type 00 class 0x040300
[    0.360038] pci 0000:01:00.1: reg 10: [mem 0xe3080000-0xe3083fff]
[    0.365270] pci 0000:00:03.0: PCI bridge to [bus 01]
[    0.365279] pci 0000:00:03.0:   bridge window [io  0x7000-0x7fff]
[    0.365286] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xe30fffff]
[    0.365384] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.365393] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    0.365402] pci 0000:00:1c.0:   bridge window [mem 0xe8200000-0xe95fffff]
[    0.365594] pci 0000:03:00.0: [14e4:4727] type 00 class 0x028000
[    0.365697] pci 0000:03:00.0: reg 10: [mem 0xe6e00000-0xe6e03fff 64bit]
[    0.366046] pci 0000:03:00.0: supports D1 D2
[    0.366048] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.366175] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.366240] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.366249] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.366258] pci 0000:00:1c.1:   bridge window [mem 0xe6e00000-0xe81fffff]
[    0.366406] pci 0000:04:00.0: [1180:e476] type 02 class 0x060700
[    0.366462] pci 0000:04:00.0: reg 10: [mem 0xe5940000-0xe5940fff]
[    0.366532] pci 0000:04:00.0: supports D1 D2
[    0.366534] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.366568] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.366671] pci 0000:04:00.1: [1180:e822] type 00 class 0x080501
[    0.366731] pci 0000:04:00.1: reg 10: [mem 0xe5930000-0xe59300ff]
[    0.366869] pci 0000:04:00.1: supports D1 D2
[    0.366872] pci 0000:04:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.367002] pci 0000:04:00.4: [1180:e832] type 00 class 0x0c0010
[    0.367026] pci 0000:04:00.4: reg 10: [mem 0xe5900000-0xe59007ff]
[    0.367164] pci 0000:04:00.4: supports D1 D2
[    0.367166] pci 0000:04:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.373327] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    0.373336] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
[    0.373345] pci 0000:00:1c.2:   bridge window [mem 0xe3100000-0xe59fffff]
[    0.373489] pci_bus 0000:05: busn_res: can not insert [bus 05-ff] under [bus 04-05] (conflicts with (null) [bus 04-05])
[    0.373545] pci_bus 0000:05: busn_res: [bus 05-ff] end is updated to 08
[    0.373547] pci_bus 0000:05: busn_res: can not insert [bus 05-08] under [bus 04-05] (conflicts with (null) [bus 04-05])
[    0.373587] pci_bus 0000:05: [bus 05-08] partially hidden behind bridge 0000:04 [bus 04-05]
[    0.373660] pci 0000:00:1c.3: PCI bridge to [bus 06-0b]
[    0.373669] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.373678] pci 0000:00:1c.3:   bridge window [mem 0xe5a00000-0xe6dfffff]
[    0.373771] pci 0000:00:1e.0: PCI bridge to [bus 0c] (subtractive decode)
[    0.373786] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.373788] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.373791] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.373793] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    0.373874] \_SB_.PCI0:_OSC invalid UUID
[    0.373876] _OSC request data:1 1f 0 
[    0.373880] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.373882] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.375662] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.375742] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.375823] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.375900] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.375977] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.376051] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.376128] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.376201] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.379355] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 3f])
[    0.379419] PCI host bridge to bus 0000:3f
[    0.379423] pci_bus 0000:3f: root bus resource [bus 3f]
[    0.379430] pci 0000:3f:00.0: [8086:2c52] type 00 class 0x060000
[    0.379481] pci 0000:3f:00.1: [8086:2c81] type 00 class 0x060000
[    0.379531] pci 0000:3f:02.0: [8086:2c90] type 00 class 0x060000
[    0.379576] pci 0000:3f:02.1: [8086:2c91] type 00 class 0x060000
[    0.379623] pci 0000:3f:03.0: [8086:2c98] type 00 class 0x060000
[    0.379665] pci 0000:3f:03.1: [8086:2c99] type 00 class 0x060000
[    0.379710] pci 0000:3f:03.4: [8086:2c9c] type 00 class 0x060000
[    0.379755] pci 0000:3f:04.0: [8086:2ca0] type 00 class 0x060000
[    0.379804] pci 0000:3f:04.1: [8086:2ca1] type 00 class 0x060000
[    0.379854] pci 0000:3f:04.2: [8086:2ca2] type 00 class 0x060000
[    0.379897] pci 0000:3f:04.3: [8086:2ca3] type 00 class 0x060000
[    0.379943] pci 0000:3f:05.0: [8086:2ca8] type 00 class 0x060000
[    0.379986] pci 0000:3f:05.1: [8086:2ca9] type 00 class 0x060000
[    0.380030] pci 0000:3f:05.2: [8086:2caa] type 00 class 0x060000
[    0.380076] pci 0000:3f:05.3: [8086:2cab] type 00 class 0x060000
[    0.380132] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.380135] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.381719] ACPI: Enabled 3 GPEs in block 00 to 3F
[    0.381728] acpi root: \_SB_.PCI0 notify handler is installed
[    0.381783] acpi root: \_SB_.CPBG notify handler is installed
[    0.381796] Found 2 acpi root devices
[    0.381855] ACPI: EC: GPE = 0x10, I/O: command/status = 0x934, data = 0x930
[    0.385915] ACPI: No dock devices found.
[    0.385994] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.385999] vgaarb: loaded
[    0.386001] vgaarb: bridge control possible 0000:01:00.0
[    0.386189] SCSI subsystem initialized
[    0.386192] ACPI: bus type ATA registered
[    0.386230] libata version 3.00 loaded.
[    0.386251] ACPI: bus type USB registered
[    0.386270] usbcore: registered new interface driver usbfs
[    0.386279] usbcore: registered new interface driver hub
[    0.386301] usbcore: registered new device driver usb
[    0.386394] PCI: Using ACPI for IRQ routing
[    0.387849] PCI: pci_cache_line_size set to 64 bytes
[    0.388085] e820: reserve RAM buffer [mem 0x00095c00-0x0009ffff]
[    0.388087] e820: reserve RAM buffer [mem 0xcf65f000-0xcfffffff]
[    0.388177] NetLabel: Initializing
[    0.388179] NetLabel:  domain hash size = 128
[    0.388180] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.388193] NetLabel:  unlabeled traffic allowed by default
[    0.388291] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.388300] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    0.388307] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.390372] hpet: hpet2 irq 40 for MSI
[    0.390443] hpet: hpet3 irq 41 for MSI
[    0.390513] hpet: hpet4 irq 42 for MSI
[    0.390578] hpet: hpet5 irq 43 for MSI
[    0.390639] hpet: hpet6 irq 44 for MSI
[    0.390741] Switching to clocksource hpet
[    0.396288] AppArmor: AppArmor Filesystem Enabled
[    0.396310] pnp: PnP ACPI init
[    0.396322] ACPI: bus type PNP registered
[    0.396370] pnp 00:00: [dma 4]
[    0.396395] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.396419] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.396547] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.396586] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.396645] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.396648] system 00:04: [io  0x1000-0x1003] has been reserved
[    0.396650] system 00:04: [io  0x1004-0x1013] has been reserved
[    0.396653] system 00:04: [io  0xffff] has been reserved
[    0.396656] system 00:04: [io  0x0400-0x047f] has been reserved
[    0.396658] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.396661] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.396664] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.396699] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.396732] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.398563] pnp 00:07: Plug and Play ACPI device, IDs PNP0401 (disabled)
[    0.398600] pnp 00:08: Plug and Play ACPI device, IDs DLL040b PNP0f13 (active)
[    0.398954] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.398958] system 00:09: [mem 0xfed1b000-0xfed1bfff] has been reserved
[    0.398961] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.398963] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.398966] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.398969] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.398972] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.398974] system 00:09: [mem 0xe96c0000-0xe96c0fff] has been reserved
[    0.398978] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.399087] pnp 00:0a: Plug and Play ACPI device, IDs SMO8800 (active)
[    0.403798] pnp: PnP ACPI: found 11 devices
[    0.403801] ACPI: bus type PNP unregistered
[    0.411171] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.411187] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.411254] pci 0000:04:00.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.411257] pci 0000:00:1c.2: bridge window [mem 0x04000000-0x03ffffff pref] to [bus 04-05] add_size 4000000
[    0.411271] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 06-0b] add_size 200000
[    0.411291] pci 0000:00:1c.2: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.411294] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.411296] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.411299] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.411304] pci 0000:00:1c.2: BAR 15: assigned [mem 0xec000000-0xefffffff pref]
[    0.411308] pci 0000:00:1c.0: BAR 15: assigned [mem 0xe9700000-0xe98fffff 64bit pref]
[    0.411312] pci 0000:00:1c.1: BAR 15: assigned [mem 0xe9900000-0xe9afffff 64bit pref]
[    0.411315] pci 0000:00:1c.3: BAR 15: assigned [mem 0xe9b00000-0xe9cfffff 64bit pref]
[    0.411320] pci 0000:00:03.0: PCI bridge to [bus 01]
[    0.411323] pci 0000:00:03.0:   bridge window [io  0x7000-0x7fff]
[    0.411328] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xe30fffff]
[    0.411334] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.411337] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    0.411347] pci 0000:00:1c.0:   bridge window [mem 0xe8200000-0xe95fffff]
[    0.411356] pci 0000:00:1c.0:   bridge window [mem 0xe9700000-0xe98fffff 64bit pref]
[    0.411366] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.411374] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.411383] pci 0000:00:1c.1:   bridge window [mem 0xe6e00000-0xe81fffff]
[    0.411392] pci 0000:00:1c.1:   bridge window [mem 0xe9900000-0xe9afffff 64bit pref]
[    0.411404] pci 0000:04:00.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.411407] pci 0000:04:00.0: res[16]=[mem 0x04000000-0x03ffffff] get_res_add_size add_size 4000000
[    0.411409] pci 0000:04:00.0: res[13]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.411412] pci 0000:04:00.0: res[14]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.411415] pci 0000:04:00.0: BAR 15: assigned [mem 0xec000000-0xefffffff pref]
[    0.411418] pci 0000:04:00.0: BAR 16: can't assign mem (size 0x4000000)
[    0.411421] pci 0000:04:00.0: BAR 13: assigned [io  0x2000-0x20ff]
[    0.411424] pci 0000:04:00.0: BAR 14: assigned [io  0x2400-0x24ff]
[    0.411427] pci 0000:04:00.0: BAR 16: can't assign mem (size 0x4000000)
[    0.411430] pci 0000:04:00.0: BAR 15: assigned [mem 0xec000000-0xefffffff pref]
[    0.411433] pci 0000:04:00.0: BAR 14: assigned [io  0x2000-0x20ff]
[    0.411436] pci 0000:04:00.0: BAR 13: assigned [io  0x2400-0x24ff]
[    0.411438] pci 0000:04:00.0: CardBus bridge to [bus 05-08]
[    0.411440] pci 0000:04:00.0:   bridge window [io  0x2400-0x24ff]
[    0.411496] pci 0000:04:00.0:   bridge window [io  0x2000-0x20ff]
[    0.411505] pci 0000:04:00.0:   bridge window [mem 0xec000000-0xefffffff pref]
[    0.411515] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    0.411523] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
[    0.411532] pci 0000:00:1c.2:   bridge window [mem 0xe3100000-0xe59fffff]
[    0.411541] pci 0000:00:1c.2:   bridge window [mem 0xec000000-0xefffffff pref]
[    0.411551] pci 0000:00:1c.3: PCI bridge to [bus 06-0b]
[    0.411559] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.411569] pci 0000:00:1c.3:   bridge window [mem 0xe5a00000-0xe6dfffff]
[    0.411577] pci 0000:00:1c.3:   bridge window [mem 0xe9b00000-0xe9cfffff 64bit pref]
[    0.411588] pci 0000:00:1e.0: PCI bridge to [bus 0c]
[    0.424000] pci 0000:00:1e.0: setting latency timer to 64
[    0.424011] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.424013] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.424016] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.424018] pci_bus 0000:00: resource 7 [mem 0xd0000000-0xfeafffff]
[    0.424020] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    0.424023] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xe30fffff]
[    0.424026] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
[    0.424028] pci_bus 0000:02: resource 1 [mem 0xe8200000-0xe95fffff]
[    0.424030] pci_bus 0000:02: resource 2 [mem 0xe9700000-0xe98fffff 64bit pref]
[    0.424033] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.424035] pci_bus 0000:03: resource 1 [mem 0xe6e00000-0xe81fffff]
[    0.424038] pci_bus 0000:03: resource 2 [mem 0xe9900000-0xe9afffff 64bit pref]
[    0.424040] pci_bus 0000:04: resource 0 [io  0x2000-0x3fff]
[    0.424042] pci_bus 0000:04: resource 1 [mem 0xe3100000-0xe59fffff]
[    0.424045] pci_bus 0000:04: resource 2 [mem 0xec000000-0xefffffff pref]
[    0.424047] pci_bus 0000:05: resource 0 [io  0x2400-0x24ff]
[    0.424049] pci_bus 0000:05: resource 1 [io  0x2000-0x20ff]
[    0.424052] pci_bus 0000:05: resource 2 [mem 0xec000000-0xefffffff pref]
[    0.424054] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    0.424056] pci_bus 0000:06: resource 1 [mem 0xe5a00000-0xe6dfffff]
[    0.424059] pci_bus 0000:06: resource 2 [mem 0xe9b00000-0xe9cfffff 64bit pref]
[    0.424061] pci_bus 0000:0c: resource 4 [io  0x0000-0x0cf7]
[    0.424064] pci_bus 0000:0c: resource 5 [io  0x0d00-0xffff]
[    0.424066] pci_bus 0000:0c: resource 6 [mem 0x000a0000-0x000bffff]
[    0.424068] pci_bus 0000:0c: resource 7 [mem 0xd0000000-0xfeafffff]
[    0.424109] NET: Registered protocol family 2
[    0.424343] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.424816] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.425215] TCP: Hash tables configured (established 65536 bind 65536)
[    0.425239] TCP: reno registered
[    0.425253] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.425336] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.425473] NET: Registered protocol family 1
[    0.425954] pci 0000:01:00.0: Boot video device
[    0.426088] PCI: CLS 64 bytes, default 64
[    0.426125] Trying to unpack rootfs image as initramfs...
[    0.766252] Freeing initrd memory: 14380k freed
[    0.768659] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.768665] software IO TLB [mem 0xcb65f000-0xcf65f000] (64MB) mapped at [ffff8800cb65f000-ffff8800cf65efff]
[    0.768722] Simple Boot Flag at 0xf1 set to 0x1
[    0.769055] Scanning for low memory corruption every 60 seconds
[    0.769323] Initialise module verification
[    0.769384] audit: initializing netlink socket (disabled)
[    0.769399] type=2000 audit(1372771192.652:1): initialized
[    0.810642] bounce pool size: 64 pages
[    0.810653] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.812452] VFS: Disk quotas dquot_6.5.2
[    0.812502] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.813081] fuse init (API version 7.21)
[    0.813181] msgmni has been set to 15945
[    0.813863] Key type asymmetric registered
[    0.813866] Asymmetric key parser 'x509' registered
[    0.813911] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.813958] io scheduler noop registered
[    0.813960] io scheduler deadline registered (default)
[    0.813968] io scheduler cfq registered
[    0.814282] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.814296] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.814298] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.814449] acpiphp: Slot [1] registered
[    0.814566] intel_idle: MWAIT substates: 0x1120
[    0.814602] intel_idle: v0.4 model 0x1E
[    0.814604] intel_idle: lapic_timer_reliable_states 0x2
[    0.815411] ACPI: AC Adapter [AC] (on-line)
[    0.815824] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.816380] ACPI: Lid Switch [LID]
[    0.816422] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.816426] ACPI: Power Button [PBTN]
[    0.816460] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.816463] ACPI: Sleep Button [SBTN]
[    0.816497] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.816500] ACPI: Power Button [PWRF]
[    0.816574] ACPI: Requesting acpi_cpufreq
[    0.833557] GHES: HEST is not enabled!
[    0.833640] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.837451] Linux agpgart interface v0.103
[    0.839129] brd: module loaded
[    0.840000] loop: module loaded
[    0.840360] libphy: Fixed MDIO Bus: probed
[    0.840444] tun: Universal TUN/TAP device driver, 1.6
[    0.840446] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.840500] PPP generic driver version 2.4.2
[    0.840584] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.840586] ehci-pci: EHCI PCI platform driver
[    0.841693] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.841699] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.841706] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.841721] ehci-pci 0000:00:1a.0: debug port 2
[    0.845645] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.845667] ehci-pci 0000:00:1a.0: irq 16, io mem 0xe9670000
[    0.848602] ACPI: Battery Slot [BAT0] (battery present)
[    0.850115] ACPI: Battery Slot [BAT1] (battery absent)
[    0.854594] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.854616] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.854619] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.854621] usb usb1: Product: EHCI Host Controller
[    0.854623] usb usb1: Manufacturer: Linux 3.9.8-030908-generic ehci_hcd
[    0.854625] usb usb1: SerialNumber: 0000:00:1a.0
[    0.854741] hub 1-0:1.0: USB hub found
[    0.854746] hub 1-0:1.0: 3 ports detected
[    0.854963] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.854971] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.854979] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.854996] ehci-pci 0000:00:1d.0: debug port 2
[    0.858938] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.858955] ehci-pci 0000:00:1d.0: irq 17, io mem 0xe9650000
[    0.870598] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.870613] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.870615] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.870618] usb usb2: Product: EHCI Host Controller
[    0.870620] usb usb2: Manufacturer: Linux 3.9.8-030908-generic ehci_hcd
[    0.870622] usb usb2: SerialNumber: 0000:00:1d.0
[    0.870726] hub 2-0:1.0: USB hub found
[    0.870731] hub 2-0:1.0: 3 ports detected
[    0.870836] ehci-platform: EHCI generic platform driver
[    0.870847] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.870863] uhci_hcd: USB Universal Host Controller Interface driver
[    0.870925] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.871370] i8042: Warning: Keylock active
[    0.872828] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.872836] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.872963] mousedev: PS/2 mouse device common for all mice
[    0.873186] rtc_cmos 00:05: RTC can wake from S4
[    0.873403] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.873444] rtc_cmos 00:05: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.873526] device-mapper: uevent: version 1.0.3
[    0.873625] device-mapper: ioctl: 4.24.0-ioctl (2013-01-15) initialised: [email]dm-devel@redhat.com[/email]
[    0.873815] cpuidle: using governor ladder
[    0.873963] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.874222] cpuidle: using governor menu
[    0.874235] ledtrig-cpu: registered to indicate activity on CPUs
[    0.874237] EFI Variables Facility v0.08 2004-May-17
[    0.874400] ashmem: initialized
[    0.874576] TCP: cubic registered
[    0.874685] NET: Registered protocol family 10
[    0.874886] NET: Registered protocol family 17
[    0.874898] Key type dns_resolver registered
[    0.875252] Loading module verification certificates
[    0.876459] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 339439d63ac8576d123e458e3d7f5c3e953c9980'
[    0.876469] registered taskstats version 1
[    0.881658] Key type trusted registered
[    0.887708] Key type encrypted registered
[    0.894789] rtc_cmos 00:05: setting system clock to 2013-07-02 13:19:53 UTC (1372771193)
[    0.896540] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.896542] EDD information not available.
[    0.897604] Freeing unused kernel memory: 1136k freed
[    0.897763] Write protecting the kernel read-only data: 12288k
[    0.900318] Freeing unused kernel memory: 1120k freed
[    0.902420] Freeing unused kernel memory: 1004k freed
[    0.921157] udevd[131]: starting version 175
[    0.954047] pps_core: LinuxPPS API ver. 1 registered
[    0.954052] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.957239] PTP clock support registered
[    0.962005] ahci 0000:00:1f.2: version 3.0
[    0.962276] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    0.962386] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x33 impl RAID mode
[    0.962393] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems sxs apst 
[    0.962409] ahci 0000:00:1f.2: setting latency timer to 64
[    0.967567] e1000e: Intel(R) PRO/1000 Network Driver - 2.2.14-k
[    0.967571] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    0.971737] sdhci: Secure Digital Host Controller Interface driver
[    0.971742] sdhci: Copyright(c) Pierre Ossman
[    0.974506] sdhci-pci 0000:04:00.1: SDHCI controller found [1180:e822] (rev 3)
[    0.974908] mmc0: no vqmmc regulator found
[    0.974912] mmc0: no vmmc regulator found
[    0.983923] scsi0 : ahci
[    0.984056] scsi1 : ahci
[    0.984205] scsi2 : ahci
[    0.984505] scsi3 : ahci
[    0.984904] scsi4 : ahci
[    0.985020] scsi5 : ahci
[    0.985102] ata1: SATA max UDMA/133 abar m2048@0xe9640000 port 0xe9640100 irq 45
[    0.985110] ata2: SATA max UDMA/133 abar m2048@0xe9640000 port 0xe9640180 irq 45
[    0.985112] ata3: DUMMY
[    0.985113] ata4: DUMMY
[    0.985116] ata5: SATA max UDMA/133 abar m2048@0xe9640000 port 0xe9640300 irq 45
[    0.985123] ata6: SATA max UDMA/133 abar m2048@0xe9640000 port 0xe9640380 irq 45
[    0.985337] e1000e 0000:00:19.0: setting latency timer to 64
[    0.985413] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.985453] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[    1.010559] mmc0: SDHCI controller on PCI [0000:04:00.1] using DMA
[    1.074779] firewire_ohci 0000:04:00.4: added OHCI v1.0 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.166639] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.223976] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 5c:26:0a:43:71:94
[    1.223979] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.224053] e1000e 0000:00:19.0 eth0: MAC: 9, PHY: 10, PBA No: 2041FF-0FF
[    1.299297] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.299305] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.299755] hub 1-1:1.0: USB hub found
[    1.300094] hub 1-1:1.0: 6 ports detected
[    1.302570] ata6: SATA link down (SStatus 0 SControl 300)
[    1.302594] ata5: SATA link down (SStatus 0 SControl 300)
[    1.302621] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.302645] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.303737] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.306318] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GU40N, A102, max UDMA/133
[    1.310259] ata2.00: configured for UDMA/133
[    1.355490] ata1.00: ATA-8: TOSHIBA MK2556GSY, LH003D, max UDMA/100
[    1.355498] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.356883] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    1.357301] ata1.00: configured for UDMA/100
[    1.357842] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2556GS LH00 PQ: 0 ANSI: 5
[    1.358044] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.358090] sd 0:0:0:0: [sda] Write Protect is off
[    1.358093] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.358124] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.358155] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.360303] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GU40N    A102 PQ: 0 ANSI: 5
[    1.364502] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.364508] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.364856] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.364978] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.410499] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.426931]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.428423] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.543161] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    1.543169] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.543578] hub 2-1:1.0: USB hub found
[    1.543739] hub 2-1:1.0: 8 ports detected
[    1.574388] firewire_core 0000:04:00.4: created device fw0: GUID 01bb8ec1394fc000, S400
[    1.614836] usb 1-1.4: new high-speed USB device number 3 using ehci-pci
[    1.714346] usb 1-1.4: New USB device found, idVendor=05ca, idProduct=1814
[    1.714353] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.714358] usb 1-1.4: Product: Laptop_Integrated_Webcam_3M
[    1.714363] usb 1-1.4: Manufacturer: CN06YWTK7248711Q03X2
[    1.766286] tsc: Refined TSC clocksource calibration: 1728.999 MHz
[    1.766295] Switching to clocksource tsc
[    1.814527] usb 2-1.1: new high-speed USB device number 3 using ehci-pci
[    1.886568] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    1.886571] EXT4-fs (sda6): write access will be enabled during recovery
[    1.907488] usb 2-1.1: New USB device found, idVendor=1a40, idProduct=0101
[    1.907496] usb 2-1.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.907501] usb 2-1.1: Product: USB 2.0 Hub
[    1.907931] hub 2-1.1:1.0: USB hub found
[    1.908056] hub 2-1.1:1.0: 4 ports detected
[    1.978453] usb 2-1.7: new full-speed USB device number 4 using ehci-pci
[    2.074712] usb 2-1.7: New USB device found, idVendor=413c, idProduct=8187
[    2.074715] usb 2-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.074717] usb 2-1.7: Product: DW375 Bluetooth Module
[    2.074719] usb 2-1.7: Manufacturer: Dell Computer Corp
[    2.074720] usb 2-1.7: SerialNumber: 1C659DF698D6
[    2.146235] usb 2-1.8: new full-speed USB device number 5 using ehci-pci
[    2.265350] usb 2-1.8: New USB device found, idVendor=0a5c, idProduct=5800
[    2.265358] usb 2-1.8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.265363] usb 2-1.8: Product: 5880
[    2.265367] usb 2-1.8: Manufacturer: Broadcom Corp
[    2.265375] usb 2-1.8: SerialNumber: 0123456789ABCD
[    2.265447] usb 2-1.8: config 0 descriptor??
[    2.362373] usb 2-1.1.3: new low-speed USB device number 6 using ehci-pci
[    2.475946] usb 2-1.1.3: New USB device found, idVendor=045e, idProduct=078c
[    2.475955] usb 2-1.1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.475960] usb 2-1.1.3: Product: USB Keyboard
[    2.475965] usb 2-1.1.3: Manufacturer: LITEON Technology
[    2.483299] hidraw: raw HID events driver (C) Jiri Kosina
[    2.487732] usbcore: registered new interface driver usbhid
[    2.487734] usbhid: USB HID core driver
[    2.491321] input: LITEON Technology USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.3/2-1.1.3:1.0/input/input5
[    2.491519] hid-generic 0003:045E:078C.0001: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Keyboard] on usb-0000:00:1d.0-1.1.3/input0
[    2.566224] usb 2-1.1.4: new low-speed USB device number 7 using ehci-pci
[    2.679807] usb 2-1.1.4: New USB device found, idVendor=1c4f, idProduct=0003
[    2.679815] usb 2-1.1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.679820] usb 2-1.1.4: Product: Usb Mouse
[    2.679825] usb 2-1.1.4: Manufacturer: SIGMACHIP
[    2.682821] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.4/2-1.1.4:1.0/input/input6
[    2.683017] hid-generic 0003:1C4F:0003.0002: input,hidraw1: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:1d.0-1.1.4/input0
[    3.202855] EXT4-fs (sda6): recovery complete
[    3.210423] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    5.980146] usb 2-1.1.4: USB disconnect, device number 7
[    7.472143] usb 2-1.1.4: new low-speed USB device number 8 using ehci-pci
[    7.585359] usb 2-1.1.4: New USB device found, idVendor=1c4f, idProduct=0003
[    7.585367] usb 2-1.1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    7.585372] usb 2-1.1.4: Product: Usb Mouse
[    7.585377] usb 2-1.1.4: Manufacturer: SIGMACHIP
[    7.588791] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.4/2-1.1.4:1.0/input/input7
[    7.589560] hid-generic 0003:1C4F:0003.0003: input,hidraw1: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:1d.0-1.1.4/input0
[   14.950947] Adding 8376316k swap on /dev/sda5.  Priority:-1 extents:1 across:8376316k 
[   15.083615] udevd[440]: starting version 175
[   15.196179] type=1400 audit(1372782007.803:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=495 comm="apparmor_parser"
[   15.196777] type=1400 audit(1372782007.807:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=495 comm="apparmor_parser"
[   15.197130] type=1400 audit(1372782007.807:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=495 comm="apparmor_parser"
[   15.329957] wmi: Mapper loaded
[   15.340940] microcode: CPU0 sig=0x106e5, pf=0x10, revision=0x3
[   15.380727] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   15.411504] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.428363] microcode: CPU1 sig=0x106e5, pf=0x10, revision=0x3
[   15.430379] microcode: CPU2 sig=0x106e5, pf=0x10, revision=0x3
[   15.431286] acpi device:1f: registered as cooling_device8
[   15.432490] microcode: CPU3 sig=0x106e5, pf=0x10, revision=0x3
[   15.432618] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   15.432675] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/LNXVIDEO:01/input/input9
[   15.434796] microcode: CPU4 sig=0x106e5, pf=0x10, revision=0x3
[   15.438027] microcode: CPU5 sig=0x106e5, pf=0x10, revision=0x3
[   15.439815] microcode: CPU6 sig=0x106e5, pf=0x10, revision=0x3
[   15.441373] microcode: CPU7 sig=0x106e5, pf=0x10, revision=0x3
[   15.442948] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   15.469643] lib80211: common routines for IEEE802.11 drivers
[   15.469646] lib80211_crypt: registered algorithm 'NULL'
[   15.488127] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130117/utaddress-251)
[   15.488136] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.488144] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20130117/utaddress-251)
[   15.488150] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.488153] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130117/utaddress-251)
[   15.488158] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.488160] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20130117/utaddress-251)
[   15.488165] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.488167] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   15.494301] yenta_cardbus 0000:04:00.0: CardBus bridge found [1028:040b]
[   15.494384] yenta_cardbus 0000:04:00.0: CardBus bridge to [bus 05-08]
[   15.494388] yenta_cardbus 0000:04:00.0:   bridge window [io  0x2400-0x24ff]
[   15.494433] yenta_cardbus 0000:04:00.0:   bridge window [io  0x2000-0x20ff]
[   15.494444] yenta_cardbus 0000:04:00.0:   bridge window [mem 0xec000000-0xefffffff pref]
[   15.494456] yenta_cardbus 0000:04:00.0:   bridge window [mem 0xe3400000-0xe37fffff]
[   15.591916] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.591920] Disabling lock debugging due to kernel taint
[   15.592738] wl: module verification failed: signature and/or required key missing - tainting kernel
[   15.621670] yenta_cardbus 0000:04:00.0: ISA IRQ mask 0x0000, PCI irq 18
[   15.621726] yenta_cardbus 0000:04:00.0: Socket status: 30000006
[   15.621729] pci_bus 0000:05: Upper limit for fixing this bridge's parent bridge: #05
[   15.621735] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge window: [io  0x2000-0x3fff]
[   15.621738] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge window: [mem 0xe3100000-0xe59fffff]
[   15.621741] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe3100000-0xe59fffff:
[   15.621745]  excluding 0xe3390000-0xe38affff 0xe5770000-0xe59fffff
[   15.621754] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge window: [mem 0xec000000-0xefffffff pref]
[   15.621757] pcmcia_socket pcmcia_socket0: cs: memory probe 0xec000000-0xefffffff:
[   15.621762]  excluding 0xec000000-0xefffffff
[   15.627062] lib80211_crypt: registered algorithm 'TKIP'
[   15.627392] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112
[   15.680490] Linux video capture interface: v2.00
[   15.687786] EDAC MC: Ver: 3.0.0
[   15.735995] parport_pc 00:07: [io  0x0378-0x037b]
[   15.736190] parport_pc 00:07: [irq 5]
[   15.749120] parport_pc 00:07: activated
[   15.749125] parport_pc 00:07: reported by Plug and Play ACPI
[   15.749332] parport_pc 00:07: disabled
[   15.756032] Bluetooth: Core ver 2.16
[   15.756053] NET: Registered protocol family 31
[   15.756055] Bluetooth: HCI device and connection manager initialized
[   15.756062] Bluetooth: HCI socket layer initialized
[   15.756065] Bluetooth: L2CAP socket layer initialized
[   15.756071] Bluetooth: SCO socket layer initialized
[   15.765497] [drm] Initialized drm 1.1.0 20060810
[   15.843798] EDAC i7core: Device not found: dev 00.0 PCI ID 8086:2c50
[   15.872511] usbcore: registered new interface driver btusb
[   15.887681] ppdev: user-space parallel port driver
[   15.890865] lp: driver loaded but no devices found
[   15.891599] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   15.891607]  excluding 0xc0000-0xfffff
[   15.891625] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   15.891630]  excluding 0xa0000000-0xa0ffffff
[   15.891647] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   15.891652]  excluding 0x60000000-0x60ffffff
[   15.998675] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_3M (05ca:1814)
[   16.000347] input: Laptop_Integrated_Webcam_3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input10
[   16.000567] usbcore: registered new interface driver uvcvideo
[   16.000569] USB Video Class driver (1.1.1)
[   16.041729] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x0a8600b1
[   16.041733] nouveau  [  DEVICE][0000:01:00.0] Chipset: GT218 (NVA8)
[   16.041736] nouveau  [  DEVICE][0000:01:00.0] Family : NV50
[   16.046845] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   16.047888] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[   16.120794] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[   16.120799] nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
[   16.120957] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[   16.120961] nouveau  [   VBIOS][0000:01:00.0] version 70.18.53.00.02
[   16.121363] nouveau  [     PFB][0000:01:00.0] RAM type: DDR3
[   16.121368] nouveau  [     PFB][0000:01:00.0] RAM size: 512 MiB
[   16.121371] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 960 tags
[   16.147968] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[   16.147984] nouveau  [  PTHERM][0000:01:00.0] fan management: disabled
[   16.147991] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[   16.147998] nouveau  [  PTHERM][0000:01:00.0] programmed thresholds [ 90(3), 95(3), 105(5), 135(5) ]
[   16.148181] [TTM] Zone  kernel: Available graphics memory: 4083732 kiB
[   16.148185] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   16.148186] [TTM] Initializing pool allocator
[   16.148193] [TTM] Initializing DMA pool allocator
[   16.152178] nouveau  [     DRM] VRAM: 512 MiB
[   16.152182] nouveau  [     DRM] GART: 512 MiB
[   16.152188] nouveau  [     DRM] TMDS table version 2.0
[   16.152192] nouveau  [     DRM] DCB version 4.0
[   16.152196] nouveau  [     DRM] DCB outp 00: 048003b6 0f220014
[   16.152199] nouveau  [     DRM] DCB outp 01: 02033300 00000000
[   16.152202] nouveau  [     DRM] DCB outp 02: 028113a6 0f220010
[   16.152204] nouveau  [     DRM] DCB outp 03: 02011362 00020010
[   16.152207] nouveau  [     DRM] DCB outp 04: 088223c6 0f220010
[   16.152210] nouveau  [     DRM] DCB outp 05: 08022382 00020010
[   16.152212] nouveau  [     DRM] DCB conn 00: 00002047
[   16.152216] nouveau  [     DRM] DCB conn 01: 00101146
[   16.152219] nouveau  [     DRM] DCB conn 02: 00410246
[   16.152222] nouveau  [     DRM] DCB conn 03: 00000300
[   16.194078] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.194082] [drm] No driver support for vblank timestamp query.
[   16.194085] nouveau  [     DRM] ACPI backlight interface available, not registering our own
[   16.194156] nouveau  [     DRM] 3 available performance level(s)
[   16.194161] nouveau  [     DRM] 0: core 135MHz shader 270MHz memory 135MHz voltage 850mV
[   16.194164] nouveau  [     DRM] 1: core 405MHz shader 810MHz memory 405MHz voltage 850mV
[   16.194168] nouveau  [     DRM] 3: core 606MHz shader 1468MHz memory 790MHz voltage 1000mV
[   16.194171] nouveau  [     DRM] c: core 405MHz shader 810MHz memory 405MHz voltage 1000mV
[   16.229080] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   16.238274] nouveau  [     DRM] MM: using COPY for buffer copies
[   16.281258] autoconfig: line_outs=1 (0xe/0x0/0x0/0x0/0x0) type:line
[   16.281262]    speaker_outs=1 (0xd/0x0/0x0/0x0/0x0)
[   16.281264]    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   16.281266]    mono: mono_out=0x0
[   16.281267]    inputs:
[   16.281269]      Dock Mic=0xf
[   16.281271]      Internal Mic=0x11
[   16.281273]      Mic=0xa
[   16.292163] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.292282] input: HDA Intel MID Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   16.292398] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   16.292547] input: HDA Intel MID Dock Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   16.395165] nouveau  [     DRM] allocated 1366x768 fb: 0x70000, bo ffff88021cc43000
[   16.395232] fbcon: nouveaufb (fb0) is primary device
[   16.514599] dell_wmi: Received unknown WMI event (0x11)
[   16.577020] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   16.692667] Console: switching to colour frame buffer device 170x48
[   16.730440] dell_wmi: Received unknown WMI event (0x11)
[   16.824606] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[   16.824609] nouveau 0000:01:00.0: registered panic notifier
[   16.824614] [drm] Initialized nouveau 1.1.0 20120801 for 0000:01:00.0 on minor 0
[   16.824760] hda_intel: Disabling MSI
[   16.824774] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.828608] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   16.839386] init: failsafe main process (980) killed by TERM signal
[   16.909645] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.909650] Bluetooth: BNEP filters: protocol multicast
[   16.909660] Bluetooth: BNEP socket layer initialized
[   16.917880] type=1400 audit(1372782009.527:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1060 comm="apparmor_parser"
[   16.918468] type=1400 audit(1372782009.527:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1060 comm="apparmor_parser"
[   16.965766] Bluetooth: RFCOMM TTY layer initialized
[   16.965779] Bluetooth: RFCOMM socket layer initialized
[   16.965780] Bluetooth: RFCOMM ver 1.11
[   17.040129] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   17.094833] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input15
[   17.107822] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input16
[   17.143910] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   17.144014] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.340338] type=1400 audit(1372782009.951:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1107 comm="apparmor_parser"
[   17.340825] type=1400 audit(1372782009.951:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1107 comm="apparmor_parser"
[   17.341102] type=1400 audit(1372782009.951:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1107 comm="apparmor_parser"
[   17.342901] type=1400 audit(1372782009.951:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1111 comm="apparmor_parser"
[   17.343703] type=1400 audit(1372782009.955:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1111 comm="apparmor_parser"
[   17.711642] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input17
[   17.711804] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input18
[   17.711942] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input19
[   17.712073] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input20
[   17.836745] /dev/vmmon[1256]: Module vmmon: registered with major=10 minor=165
[   17.836752] /dev/vmmon[1256]: Module vmmon: initialized
[   17.947960] [1288]: VMCI: shared components initialized.
[   17.947999] [1288]: VMCI: host components initialized.
[   17.948053] [1288]: VMCI: Module registered (name=vmci,major=10,minor=54).
[   17.948055] [1288]: VMCI: Using host personality
[   17.948057] [1288]: VMCI: Module (name=vmci) is initialized
[   20.304758] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx
[   20.304795] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.267626] /dev/vmnet: open called by PID 1897 (vmnet-bridge)
[   23.267635] /dev/vmnet: hub 0 does not exist, allocating memory.
[   23.267655] /dev/vmnet: port on hub 0 successfully opened
[   23.267670] bridge-eth0: up
[   23.267673] bridge-eth0: attached
[   23.811808] /dev/vmnet: open called by PID 1904 (vmnet-netifup)
[   23.811815] /dev/vmnet: hub 1 does not exist, allocating memory.
[   23.811828] /dev/vmnet: port on hub 1 successfully opened
[   23.926235] /dev/vmnet: open called by PID 1909 (vmnet-dhcpd)
[   23.926246] /dev/vmnet: port on hub 1 successfully opened
[   24.001177] /dev/vmnet: open called by PID 1913 (vmnet-natd)
[   24.001184] /dev/vmnet: hub 8 does not exist, allocating memory.
[   24.001197] /dev/vmnet: port on hub 8 successfully opened
[   24.002195] userif-3: sent link down event.
[   24.002198] userif-3: sent link up event.<7>[   24.003456] /dev/vmnet: open called by PID 1914 (vmnet-netifup)
[   24.003462] /dev/vmnet: port on hub 8 successfully opened
[   24.044200] /dev/vmnet: open called by PID 1916 (vmnet-dhcpd)
[   24.044210] /dev/vmnet: port on hub 8 successfully opened
[   24.407573] init: plymouth-stop pre-start process (2348) terminated with status 1
[   29.865614] userif-3: sent link down event.
[   29.865618] userif-3: sent link up event.userif-3: sent link down event.
[   30.987415] userif-3: sent link up event.userif-3: sent link down event.
[  861.523132] userif-3: sent link up event.<7>[  950.042877] /dev/vmmon[4708]: PTSC: initialized at 1728999000 Hz using TSC, TSCs are synchronized.
[  950.270415] /dev/vmmon[4708]: Monitor IPI vector: 0
[  953.202002] /dev/vmnet: open called by PID 4721 (vmx-vcpu-0)
[  953.202026] device eth0 entered promiscuous mode
[  953.202045] bridge-eth0: enabled promiscuous mode
[  953.202048] /dev/vmnet: port on hub 0 successfully opened
[ 1596.377874] audit_printk_skb: 54 callbacks suppressed
[ 1596.377878] type=1400 audit(1372783589.353:30): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=6691 comm="apparmor_parser"
[ 1596.378518] type=1400 audit(1372783589.357:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=6691 comm="apparmor_parser"
[ 1911.222671] userif-3: sent link down event.
[ 1911.222681] userif-3: sent link up event.userif-3: sent link down event.
[ 3512.765099] userif-3: sent link up event.userif-3: sent link down event.
[ 4244.994115] userif-3: sent link up event.userif-3: sent link down event.
[ 4407.744461] userif-3: sent link up event.<6>[ 6209.017872] dell_wmi: Received unknown WMI event (0x11)
[ 6874.650328] dell_wmi: Received unknown WMI event (0x11)
[ 7311.260301] userif-3: sent link down event.
[ 7311.260310] userif-3: sent link up event.userif-3: sent link down event.
[ 8105.164097] userif-3: sent link up event.userif-3: sent link down event.
[ 8514.496028] userif-3: sent link up event.<6>[10459.381339] dell_wmi: Received unknown WMI event (0x11)
[12631.045129] dell_wmi: Received unknown WMI event (0x11)
[18295.149052] nouveau E[     DRM] GPU lockup - switching to software fbcon
[18299.103756] nouveau E[Xorg[1243]] failed to idle channel 0xcccc0001 [Xorg[1243]]
[18302.102467] nouveau E[Xorg[1243]] failed to idle channel 0xcccc0001 [Xorg[1243]]
[18304.101922] nouveau E[   PFIFO][0000:01:00.0] channel 3 [Xorg[1243]] unload timeout
[18307.100441] nouveau E[Xorg[1243]] failed to idle channel 0xcccc0000 [Xorg[1243]]
[18310.099112] nouveau E[Xorg[1243]] failed to idle channel 0xcccc0000 [Xorg[1243]]
[18312.098502] nouveau E[   PFIFO][0000:01:00.0] channel 2 [Xorg[1243]] unload timeout
[18315.132955] nouveau E[compiz[2478]] failed to idle channel 0xcccc0000 [compiz[2478]]
[18318.131747] nouveau E[compiz[2478]] failed to idle channel 0xcccc0000 [compiz[2478]]
[18320.131063] nouveau E[   PFIFO][0000:01:00.0] channel 4 [compiz[2478]] unload timeout
[18332.157669] device eth0 left promiscuous mode
[18332.157703] bridge-eth0: disabled promiscuous mode
[18340.968463] unity-greeter[12140]: segfault at 18 ip 00007feba60fe616 sp 00007fff21d23450 error 4 in libxklavier.so.16.2.0[7feba60ee000+19000]


[SIZE=5][B]Xorg.0.log
[/B][/SIZE]
[ 18322.143] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[ 18322.143] X Protocol Version 11, Revision 0
[ 18322.143] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[ 18322.143] Current Operating System: Linux AC-TARRUDA-PC 3.9.8-030908-generic #201306271518 SMP Thu Jun 27 19:19:16 UTC 2013 x86_64
[ 18322.143] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.9.8-030908-generic root=UUID=69eecf32-b1e4-436a-801e-e382a458ebba ro quiet splash vt.handoff=7
[ 18322.143] Build Date: 11 April 2013  12:53:36PM
[ 18322.143] xorg-server 2:1.13.0-0ubuntu6.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[ 18322.143] Current version of pixman: 0.26.0
[ 18322.143] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[ 18322.143] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 18322.143] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  2 18:25:14 2013
[ 18322.520] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 18322.825] (==) No Layout section.  Using the first Screen section.
[ 18322.825] (==) No screen section available. Using defaults.
[ 18322.825] (**) |-->Screen "Default Screen Section" (0)
[ 18322.825] (**) |   |-->Monitor "<default monitor>"
[ 18322.825] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[ 18322.825] (==) Automatically adding devices
[ 18322.825] (==) Automatically enabling devices
[ 18322.825] (==) Automatically adding GPU devices
[ 18322.900] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 18322.900] 	Entry deleted from font path.
[ 18322.900] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 18322.900] 	Entry deleted from font path.
[ 18322.900] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 18322.900] 	Entry deleted from font path.
[ 18322.942] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 18322.942] 	Entry deleted from font path.
[ 18322.942] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 18322.942] 	Entry deleted from font path.
[ 18322.942] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[ 18322.942] 	Entry deleted from font path.
[ 18322.942] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[ 18322.942] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 18322.942] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 18322.942] (II) Loader magic: 0x7f00a2409c40
[ 18322.942] (II) Module ABI versions:
[ 18322.942] 	X.Org ANSI C Emulation: 0.4
[ 18322.942] 	X.Org Video Driver: 13.0
[ 18322.942] 	X.Org XInput driver : 18.0
[ 18322.942] 	X.Org Server Extension : 7.0
[ 18322.943] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 18327.483] (--) PCI:*(0:1:0:0) 10de:0a6c:1028:040b rev 162, Mem @ 0xe2000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00007000/128, BIOS @ 0x????????/524288
[ 18327.484] (II) Open ACPI successful (/var/run/acpid.socket)
[ 18327.484] Initializing built-in extension Generic Event Extension
[ 18327.484] Initializing built-in extension SHAPE
[ 18327.484] Initializing built-in extension MIT-SHM
[ 18327.484] Initializing built-in extension XInputExtension
[ 18327.484] Initializing built-in extension XTEST
[ 18327.484] Initializing built-in extension BIG-REQUESTS
[ 18327.484] Initializing built-in extension SYNC
[ 18327.484] Initializing built-in extension XKEYBOARD
[ 18327.484] Initializing built-in extension XC-MISC
[ 18327.484] Initializing built-in extension SECURITY
[ 18327.484] Initializing built-in extension XINERAMA
[ 18327.484] Initializing built-in extension XFIXES
[ 18327.484] Initializing built-in extension RENDER
[ 18327.484] Initializing built-in extension RANDR
[ 18327.484] Initializing built-in extension COMPOSITE
[ 18327.484] Initializing built-in extension DAMAGE
[ 18327.484] Initializing built-in extension MIT-SCREEN-SAVER
[ 18327.484] Initializing built-in extension DOUBLE-BUFFER
[ 18327.484] Initializing built-in extension RECORD
[ 18327.484] Initializing built-in extension DPMS
[ 18327.484] Initializing built-in extension X-Resource
[ 18327.484] Initializing built-in extension XVideo
[ 18327.484] Initializing built-in extension XVideo-MotionCompensation
[ 18327.484] Initializing built-in extension XFree86-VidModeExtension
[ 18327.484] Initializing built-in extension XFree86-DGA
[ 18327.484] Initializing built-in extension XFree86-DRI
[ 18327.484] Initializing built-in extension DRI2
[ 18327.484] (II) LoadModule: "glx"
[ 18327.584] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 18327.601] (II) Module glx: vendor="X.Org Foundation"
[ 18327.601] 	compiled for 1.13.0, module version = 1.0.0
[ 18327.601] 	ABI class: X.Org Server Extension, version 7.0
[ 18327.601] (==) AIGLX enabled
[ 18327.601] Loading extension GLX
[ 18327.601] (==) Matched nvidia as autoconfigured driver 0
[ 18327.601] (==) Matched nouveau as autoconfigured driver 1
[ 18327.601] (==) Matched nv as autoconfigured driver 2
[ 18327.601] (==) Matched nvidia as autoconfigured driver 3
[ 18327.601] (==) Matched nouveau as autoconfigured driver 4
[ 18327.601] (==) Matched nv as autoconfigured driver 5
[ 18327.601] (==) Matched vesa as autoconfigured driver 6
[ 18327.601] (==) Matched modesetting as autoconfigured driver 7
[ 18327.601] (==) Matched fbdev as autoconfigured driver 8
[ 18327.601] (==) Assigned the driver to the xf86ConfigLayout
[ 18327.601] (II) LoadModule: "nvidia"
[ 18327.624] (WW) Warning, couldn't open module nvidia
[ 18327.624] (II) UnloadModule: "nvidia"
[ 18327.624] (II) Unloading nvidia
[ 18327.624] (EE) Failed to load module "nvidia" (module does not exist, 0)
[ 18327.624] (II) LoadModule: "nouveau"
[ 18327.624] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 18327.625] (II) Module nouveau: vendor="X.Org Foundation"
[ 18327.625] 	compiled for 1.13.0, module version = 1.0.2
[ 18327.625] 	Module class: X.Org Video Driver
[ 18327.625] 	ABI class: X.Org Video Driver, version 13.0
[ 18327.625] (II) LoadModule: "nv"
[ 18327.625] (WW) Warning, couldn't open module nv
[ 18327.625] (II) UnloadModule: "nv"
[ 18327.625] (II) Unloading nv
[ 18327.625] (EE) Failed to load module "nv" (module does not exist, 0)
[ 18327.625] (II) LoadModule: "vesa"
[ 18327.625] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 18327.638] (II) Module vesa: vendor="X.Org Foundation"
[ 18327.638] 	compiled for 1.12.99.902, module version = 2.3.2
[ 18327.638] 	Module class: X.Org Video Driver
[ 18327.638] 	ABI class: X.Org Video Driver, version 13.0
[ 18327.638] (II) LoadModule: "modesetting"
[ 18327.638] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 18327.649] (II) Module modesetting: vendor="X.Org Foundation"
[ 18327.649] 	compiled for 1.13.0, module version = 0.5.0
[ 18327.649] 	Module class: X.Org Video Driver
[ 18327.649] 	ABI class: X.Org Video Driver, version 13.0
[ 18327.649] (II) LoadModule: "fbdev"
[ 18327.649] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 18327.654] (II) Module fbdev: vendor="X.Org Foundation"
[ 18327.654] 	compiled for 1.12.99.902, module version = 0.4.3
[ 18327.654] 	Module class: X.Org Video Driver
[ 18327.654] 	ABI class: X.Org Video Driver, version 13.0
[ 18327.654] (==) Matched nvidia as autoconfigured driver 0
[ 18327.654] (==) Matched nouveau as autoconfigured driver 1
[ 18327.654] (==) Matched nv as autoconfigured driver 2
[ 18327.654] (==) Matched nvidia as autoconfigured driver 3
[ 18327.654] (==) Matched nouveau as autoconfigured driver 4
[ 18327.654] (==) Matched nv as autoconfigured driver 5
[ 18327.654] (==) Matched vesa as autoconfigured driver 6
[ 18327.654] (==) Matched modesetting as autoconfigured driver 7
[ 18327.654] (==) Matched fbdev as autoconfigured driver 8
[ 18327.654] (==) Assigned the driver to the xf86ConfigLayout
[ 18327.654] (II) LoadModule: "nvidia"
[ 18327.655] (WW) Warning, couldn't open module nvidia
[ 18327.655] (II) UnloadModule: "nvidia"
[ 18327.655] (II) Unloading nvidia
[ 18327.655] (EE) Failed to load module "nvidia" (module does not exist, 0)
[ 18327.655] (II) LoadModule: "nouveau"
[ 18327.655] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 18327.655] (II) Module nouveau: vendor="X.Org Foundation"
[ 18327.655] 	compiled for 1.13.0, module version = 1.0.2
[ 18327.655] 	Module class: X.Org Video Driver
[ 18327.655] 	ABI class: X.Org Video Driver, version 13.0
[ 18327.655] (II) UnloadModule: "nouveau"
[ 18327.655] (II) Unloading nouveau
[ 18327.655] (II) Failed to load module "nouveau" (already loaded, 0)
[ 18327.655] (II) LoadModule: "nv"
[ 18327.656] (WW) Warning, couldn't open module nv
[ 18327.656] (II) UnloadModule: "nv"
[ 18327.656] (II) Unloading nv
[ 18327.656] (EE) Failed to load module "nv" (module does not exist, 0)
[ 18327.656] (II) LoadModule: "vesa"
[ 18327.656] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 18327.656] (II) Module vesa: vendor="X.Org Foundation"
[ 18327.656] 	compiled for 1.12.99.902, module version = 2.3.2
[ 18327.656] 	Module class: X.Org Video Driver
[ 18327.656] 	ABI class: X.Org Video Driver, version 13.0
[ 18327.656] (II) UnloadModule: "vesa"
[ 18327.656] (II) Unloading vesa
[ 18327.656] (II) Failed to load module "vesa" (already loaded, 0)
[ 18327.656] (II) LoadModule: "modesetting"
[ 18327.656] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 18327.656] (II) Module modesetting: vendor="X.Org Foundation"
[ 18327.656] 	compiled for 1.13.0, module version = 0.5.0
[ 18327.656] 	Module class: X.Org Video Driver
[ 18327.656] 	ABI class: X.Org Video Driver, version 13.0
[ 18327.656] (II) UnloadModule: "modesetting"
[ 18327.656] (II) Unloading modesetting
[ 18327.656] (II) Failed to load module "modesetting" (already loaded, 0)
[ 18327.656] (II) LoadModule: "fbdev"
[ 18327.657] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 18327.657] (II) Module fbdev: vendor="X.Org Foundation"
[ 18327.657] 	compiled for 1.12.99.902, module version = 0.4.3
[ 18327.657] 	Module class: X.Org Video Driver
[ 18327.657] 	ABI class: X.Org Video Driver, version 13.0
[ 18327.657] (II) UnloadModule: "fbdev"
[ 18327.657] (II) Unloading fbdev
[ 18327.657] (II) Failed to load module "fbdev" (already loaded, 0)
[ 18327.657] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[ 18327.657] (II) NOUVEAU driver for NVIDIA chipset families :
[ 18327.657] 	RIVA TNT        (NV04)
[ 18327.657] 	RIVA TNT2       (NV05)
[ 18327.657] 	GeForce 256     (NV10)
[ 18327.657] 	GeForce 2       (NV11, NV15)
[ 18327.657] 	GeForce 4MX     (NV17, NV18)
[ 18327.657] 	GeForce 3       (NV20)
[ 18327.657] 	GeForce 4Ti     (NV25, NV28)
[ 18327.657] 	GeForce FX      (NV3x)
[ 18327.657] 	GeForce 6       (NV4x)
[ 18327.657] 	GeForce 7       (G7x)
[ 18327.657] 	GeForce 8       (G8x)
[ 18327.657] 	GeForce GTX 200 (NVA0)
[ 18327.657] 	GeForce GTX 400 (NVC0)
[ 18327.657] (II) VESA: driver for VESA chipsets: vesa
[ 18327.657] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[ 18327.657] (II) FBDEV: driver for framebuffer: fbdev
[ 18327.657] (++) using VT number 7


[ 18327.657] (WW) Falling back to old probe method for vesa
[ 18327.657] (WW) Falling back to old probe method for modesetting
[ 18327.657] (WW) Falling back to old probe method for fbdev
[ 18327.657] (II) Loading sub module "fbdevhw"
[ 18327.657] (II) LoadModule: "fbdevhw"
[ 18327.657] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 18327.670] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 18327.670] 	compiled for 1.13.0, module version = 0.0.2
[ 18327.670] 	ABI class: X.Org Video Driver, version 13.0
[ 18327.670] (II) Loading sub module "dri"
[ 18327.670] (II) LoadModule: "dri"
[ 18327.670] (II) Module "dri" already built-in
[ 18327.670] (II) NOUVEAU(0): Loaded DRI module
[ 18327.670] (II) [drm] DRM interface version 1.4
[ 18327.670] (II) [drm] DRM open master succeeded.
[ 18327.670] (--) NOUVEAU(0): Chipset: "NVIDIA NVa8"
[ 18327.670] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[ 18327.670] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[ 18327.670] (==) NOUVEAU(0): RGB weight 888
[ 18327.670] (==) NOUVEAU(0): Default visual is TrueColor
[ 18327.670] (==) NOUVEAU(0): Using HW cursor
[ 18327.670] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[ 18327.670] (==) NOUVEAU(0): Page flipping enabled
[ 18327.670] (==) NOUVEAU(0): Swap limit set to 2 [Max allowed 2]
[ 18327.716] (II) NOUVEAU(0): Output eDP-1 has no monitor section
[ 18327.748] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[ 18327.876] (II) NOUVEAU(0): Output DP-1 has no monitor section
[ 18328.004] (II) NOUVEAU(0): Output DP-2 has no monitor section
[ 18328.010] (II) NOUVEAU(0): EDID for output eDP-1
[ 18328.010] (II) NOUVEAU(0): Manufacturer: LGD  Model: 24b  Serial#: 0
[ 18328.011] (II) NOUVEAU(0): Year: 2010  Week: 0
[ 18328.011] (II) NOUVEAU(0): EDID Version: 1.4
[ 18328.011] (II) NOUVEAU(0): Digital Display Input
[ 18328.011] (II) NOUVEAU(0): 6 bits per channel
[ 18328.011] (II) NOUVEAU(0): Digital interface is DisplayPort
[ 18328.011] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[ 18328.011] (II) NOUVEAU(0): Gamma: 2.20
[ 18328.011] (II) NOUVEAU(0): No DPMS capabilities specified
[ 18328.011] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 
[ 18328.011] (II) NOUVEAU(0): First detailed timing is preferred mode
[ 18328.011] (II) NOUVEAU(0): Preferred mode is native pixel format and refresh rate
[ 18328.011] (II) NOUVEAU(0): redX: 0.622 redY: 0.365   greenX: 0.340 greenY: 0.607
[ 18328.011] (II) NOUVEAU(0): blueX: 0.145 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[ 18328.011] (II) NOUVEAU(0): Manufacturer's mask: 0
[ 18328.011] (II) NOUVEAU(0): Supported detailed timing:
[ 18328.011] (II) NOUVEAU(0): clock: 72.0 MHz   Image Size:  344 x 194 mm
[ 18328.011] (II) NOUVEAU(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1520 h_border: 0
[ 18328.011] (II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[ 18328.011] (II) NOUVEAU(0): Supported detailed timing:
[ 18328.011] (II) NOUVEAU(0): clock: 48.0 MHz   Image Size:  344 x 194 mm
[ 18328.011] (II) NOUVEAU(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1520 h_border: 0
[ 18328.011] (II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[ 18328.011] (II) NOUVEAU(0):  G7W62\81156WH2
[ 18328.011] (II) NOUVEAU(0): Unknown vendor-specific block 0
[ 18328.011] (II) NOUVEAU(0): EDID (in hex):
[ 18328.011] (II) NOUVEAU(0): 	00ffffffffffff0030e44b0200000000
[ 18328.011] (II) NOUVEAU(0): 	00140104952213780262259f5d579b25
[ 18328.011] (II) NOUVEAU(0): 	19505400000001010101010101010101
[ 18328.011] (II) NOUVEAU(0): 	010101010101201c569a500016303020
[ 18328.011] (II) NOUVEAU(0): 	350058c21000001ac012569a50001630
[ 18328.011] (II) NOUVEAU(0): 	3020350058c21000001a000000fe0047
[ 18328.011] (II) NOUVEAU(0): 	37573632813135365748320a00000000
[ 18328.011] (II) NOUVEAU(0): 	00004101160000000009010a20200056
[ 18328.011] (II) NOUVEAU(0): Printing probed modes for output eDP-1
[ 18328.011] (II) NOUVEAU(0): Modeline "1366x768"x60.0   72.00  1366 1414 1446 1520  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[ 18328.011] (II) NOUVEAU(0): Modeline "1366x768"x40.0   48.00  1366 1414 1446 1520  768 771 776 790 +hsync -vsync (31.6 kHz e)
[ 18328.011] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz e)
[ 18328.011] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz e)
[ 18328.011] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz e)
[ 18328.011] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz e)
[ 18328.011] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz e)
[ 18328.011] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz e)
[ 18328.043] (II) NOUVEAU(0): EDID for output VGA-1
[ 18328.043] (II) NOUVEAU(0): Manufacturer: SAM  Model: 8ab  Serial#: 1496531512
[ 18328.043] (II) NOUVEAU(0): Year: 2012  Week: 48
[ 18328.043] (II) NOUVEAU(0): EDID Version: 1.3
[ 18328.043] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[ 18328.043] (II) NOUVEAU(0): Sync:  Separate  Composite  SyncOnGreen
[ 18328.043] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[ 18328.043] (II) NOUVEAU(0): Gamma: 2.20
[ 18328.043] (II) NOUVEAU(0): DPMS capabilities: Off; RGB/Color Display
[ 18328.043] (II) NOUVEAU(0): First detailed timing is preferred mode
[ 18328.043] (II) NOUVEAU(0): redX: 0.635 redY: 0.349   greenX: 0.332 greenY: 0.609
[ 18328.043] (II) NOUVEAU(0): blueX: 0.155 blueY: 0.055   whiteX: 0.312 whiteY: 0.329
[ 18328.043] (II) NOUVEAU(0): Supported established timings:
[ 18328.043] (II) NOUVEAU(0): 720x400@70Hz
[ 18328.043] (II) NOUVEAU(0): 640x480@60Hz
[ 18328.043] (II) NOUVEAU(0): 640x480@67Hz
[ 18328.043] (II) NOUVEAU(0): 640x480@72Hz
[ 18328.043] (II) NOUVEAU(0): 640x480@75Hz
[ 18328.043] (II) NOUVEAU(0): 800x600@56Hz
[ 18328.043] (II) NOUVEAU(0): 800x600@60Hz
[ 18328.043] (II) NOUVEAU(0): 800x600@72Hz
[ 18328.043] (II) NOUVEAU(0): 800x600@75Hz
[ 18328.043] (II) NOUVEAU(0): 832x624@75Hz
[ 18328.043] (II) NOUVEAU(0): 1024x768@60Hz
[ 18328.043] (II) NOUVEAU(0): 1024x768@70Hz
[ 18328.043] (II) NOUVEAU(0): 1024x768@75Hz
[ 18328.043] (II) NOUVEAU(0): 1280x1024@75Hz
[ 18328.043] (II) NOUVEAU(0): 1152x864@75Hz
[ 18328.043] (II) NOUVEAU(0): Manufacturer's mask: 0
[ 18328.043] (II) NOUVEAU(0): Supported standard timings:
[ 18328.043] (II) NOUVEAU(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[ 18328.043] (II) NOUVEAU(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[ 18328.043] (II) NOUVEAU(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[ 18328.043] (II) NOUVEAU(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[ 18328.043] (II) NOUVEAU(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[ 18328.043] (II) NOUVEAU(0): #5: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[ 18328.043] (II) NOUVEAU(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[ 18328.043] (II) NOUVEAU(0): Supported detailed timing:
[ 18328.043] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[ 18328.043] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[ 18328.043] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[ 18328.043] (II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[ 18328.043] (II) NOUVEAU(0): Monitor name: S22B300
[ 18328.043] (II) NOUVEAU(0): Serial No: HXFCB02562
[ 18328.043] (II) NOUVEAU(0): EDID (in hex):
[ 18328.043] (II) NOUVEAU(0): 	00ffffffffffff004c2dab0838423359
[ 18328.043] (II) NOUVEAU(0): 	301601030e301b782a90c1a259559c27
[ 18328.043] (II) NOUVEAU(0): 	0e5054bfef80714f81c0810081809500
[ 18328.043] (II) NOUVEAU(0): 	a9c0b3000101023a801871382d40582c
[ 18328.043] (II) NOUVEAU(0): 	4500dd0c1100001e000000fd00384b1e
[ 18328.043] (II) NOUVEAU(0): 	5111000a202020202020000000fc0053
[ 18328.043] (II) NOUVEAU(0): 	3232423330300a2020202020000000ff
[ 18328.043] (II) NOUVEAU(0): 	00485846434230323536320a2020009b
[ 18328.043] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[ 18328.043] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 18328.043] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1600x900"x60.0  118.96  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[ 18328.043] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[ 18328.043] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 18328.168] (II) NOUVEAU(0): EDID for output DP-1
[ 18328.296] (II) NOUVEAU(0): EDID for output DP-2
[ 18328.296] (II) NOUVEAU(0): Output eDP-1 connected
[ 18328.296] (II) NOUVEAU(0): Output VGA-1 connected
[ 18328.296] (II) NOUVEAU(0): Output DP-1 disconnected
[ 18328.296] (II) NOUVEAU(0): Output DP-2 disconnected
[ 18328.296] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[ 18328.296] (II) NOUVEAU(0): Output eDP-1 using initial mode 1024x768
[ 18328.296] (II) NOUVEAU(0): Output VGA-1 using initial mode 1024x768
[ 18328.296] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 18328.296] (--) NOUVEAU(0): Virtual size is 1024x768 (pitch 0)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "1366x768": 72.0 MHz (scaled from 0.0 MHz), 47.4 kHz, 60.0 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "1366x768"x60.0   72.00  1366 1414 1446 1520  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "1366x768": 48.0 MHz (scaled from 0.0 MHz), 31.6 kHz, 40.0 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "1366x768"x40.0   48.00  1366 1414 1446 1520  768 771 776 790 +hsync -vsync (31.6 kHz e)
[ 18328.296] (==) NOUVEAU(0): DPI set to (96, 96)
[ 18328.296] (II) Loading sub module "fb"
[ 18328.296] (II) LoadModule: "fb"
[ 18328.296] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 18328.335] (II) Module fb: vendor="X.Org Foundation"
[ 18328.335] 	compiled for 1.13.0, module version = 1.0.0
[ 18328.335] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 18328.335] (II) Loading sub module "exa"
[ 18328.335] (II) LoadModule: "exa"
[ 18328.335] (II) Loading /usr/lib/xorg/modules/libexa.so
[ 18328.335] (II) Module exa: vendor="X.Org Foundation"
[ 18328.335] 	compiled for 1.13.0, module version = 2.6.0
[ 18328.335] 	ABI class: X.Org Video Driver, version 13.0
[ 18328.335] (II) Loading sub module "shadowfb"
[ 18328.335] (II) LoadModule: "shadowfb"
[ 18328.336] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[ 18328.336] (II) Module shadowfb: vendor="X.Org Foundation"
[ 18328.336] 	compiled for 1.13.0, module version = 1.0.0
[ 18328.336] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 18328.336] (II) UnloadModule: "vesa"
[ 18328.336] (II) Unloading vesa
[ 18328.336] (II) UnloadModule: "modesetting"
[ 18328.336] (II) Unloading modesetting
[ 18328.336] (II) UnloadModule: "fbdev"
[ 18328.336] (II) Unloading fbdev
[ 18328.336] (II) UnloadSubModule: "fbdevhw"
[ 18328.336] (II) Unloading fbdevhw
[ 18328.336] (--) Depth 24 pixmap format is 32 bpp
[ 18328.338] (II) NOUVEAU(0): Opened GPU channel 0
[ 18328.351] (II) NOUVEAU(0): [DRI2] Setup complete
[ 18328.351] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[ 18328.351] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[ 18328.353] (II) EXA(0): Driver allocated offscreen pixmaps
[ 18328.353] (II) EXA(0): Driver registered support for the following operations:
[ 18328.353] (II)         Solid
[ 18328.353] (II)         Copy
[ 18328.353] (II)         Composite (RENDER acceleration)
[ 18328.353] (II)         UploadToScreen
[ 18328.353] (II)         DownloadFromScreen
[ 18328.353] (==) NOUVEAU(0): Backing store disabled
[ 18328.353] (==) NOUVEAU(0): Silken mouse enabled
[ 18328.363] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[ 18328.363] (II) NOUVEAU(0): [XvMC] Extension initialized.
[ 18328.363] (==) NOUVEAU(0): DPMS enabled
[ 18328.363] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 18328.364] (--) RandR disabled
[ 18328.392] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 18328.392] (II) AIGLX: enabled GLX_INTEL_swap_event
[ 18328.392] (II) AIGLX: enabled GLX_ARB_create_context
[ 18328.392] (II) AIGLX: enabled GLX_ARB_create_context_profile
[ 18328.392] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[ 18328.392] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[ 18328.392] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[ 18328.392] (II) AIGLX: Loaded and initialized nouveau
[ 18328.392] (II) GLX: Initialized DRI2 GL provider for screen 0
[ 18328.394] (II) NOUVEAU(0): NVEnterVT is called.
[ 18340.410] (II) NOUVEAU(0): Setting screen physical size to 270 x 203
[ 18340.410] resize called 1024 768
[ 18340.502] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 18340.511] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[ 18340.511] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 18340.511] (II) LoadModule: "evdev"
[ 18340.512] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 18340.523] (II) Module evdev: vendor="X.Org Foundation"
[ 18340.523] 	compiled for 1.13.0, module version = 2.7.3
[ 18340.523] 	Module class: X.Org XInput Driver
[ 18340.523] 	ABI class: X.Org XInput driver, version 18.0
[ 18340.523] (II) Using input driver 'evdev' for 'Power Button'
[ 18340.523] (**) Power Button: always reports core events
[ 18340.523] (**) evdev: Power Button: Device: "/dev/input/event3"
[ 18340.523] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 18340.523] (--) evdev: Power Button: Found keys
[ 18340.523] (II) evdev: Power Button: Configuring as keyboard
[ 18340.523] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[ 18340.523] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 18340.523] (**) Option "xkb_rules" "evdev"
[ 18340.523] (**) Option "xkb_model" "pc105"
[ 18340.523] (**) Option "xkb_layout" "br"
[ 18340.525] (II) XKB: reuse xkmfile /var/lib/xkb/server-A37B2EFB8B2398771EA3BE2A51A1034B516E3F38.xkm
[ 18340.525] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[ 18340.525] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 18340.525] (II) Using input driver 'evdev' for 'Video Bus'
[ 18340.525] (**) Video Bus: always reports core events
[ 18340.525] (**) evdev: Video Bus: Device: "/dev/input/event8"
[ 18340.525] (--) evdev: Video Bus: Vendor 0 Product 0x6
[ 18340.525] (--) evdev: Video Bus: Found keys
[ 18340.525] (II) evdev: Video Bus: Configuring as keyboard
[ 18340.525] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/LNXVIDEO:01/input/input9/event8"
[ 18340.525] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[ 18340.525] (**) Option "xkb_rules" "evdev"
[ 18340.525] (**) Option "xkb_model" "pc105"
[ 18340.525] (**) Option "xkb_layout" "br"
[ 18340.526] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 18340.526] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 18340.526] (II) Using input driver 'evdev' for 'Power Button'
[ 18340.526] (**) Power Button: always reports core events
[ 18340.526] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 18340.526] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 18340.526] (--) evdev: Power Button: Found keys
[ 18340.526] (II) evdev: Power Button: Configuring as keyboard
[ 18340.526] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[ 18340.526] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[ 18340.526] (**) Option "xkb_rules" "evdev"
[ 18340.526] (**) Option "xkb_model" "pc105"
[ 18340.526] (**) Option "xkb_layout" "br"
[ 18340.526] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[ 18340.526] (II) No input driver specified, ignoring this device.
[ 18340.526] (II) This device may have been added with another device file.
[ 18340.526] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[ 18340.526] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 18340.527] (II) Using input driver 'evdev' for 'Sleep Button'
[ 18340.527] (**) Sleep Button: always reports core events
[ 18340.527] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[ 18340.527] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[ 18340.527] (--) evdev: Sleep Button: Found keys
[ 18340.527] (II) evdev: Sleep Button: Configuring as keyboard
[ 18340.527] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[ 18340.527] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[ 18340.527] (**) Option "xkb_rules" "evdev"
[ 18340.527] (**) Option "xkb_model" "pc105"
[ 18340.527] (**) Option "xkb_layout" "br"
[ 18340.527] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 18340.527] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event16)
[ 18340.527] (II) No input driver specified, ignoring this device.
[ 18340.527] (II) This device may have been added with another device file.
[ 18340.527] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event17)
[ 18340.527] (II) No input driver specified, ignoring this device.
[ 18340.527] (II) This device may have been added with another device file.
[ 18340.528] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event18)
[ 18340.528] (II) No input driver specified, ignoring this device.
[ 18340.528] (II) This device may have been added with another device file.
[ 18340.528] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event19)
[ 18340.528] (II) No input driver specified, ignoring this device.
[ 18340.528] (II) This device may have been added with another device file.
[ 18340.528] (II) config/udev: Adding input device Laptop_Integrated_Webcam_3M (/dev/input/event9)
[ 18340.528] (**) Laptop_Integrated_Webcam_3M: Applying InputClass "evdev keyboard catchall"
[ 18340.528] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_3M'
[ 18340.528] (**) Laptop_Integrated_Webcam_3M: always reports core events
[ 18340.528] (**) evdev: Laptop_Integrated_Webcam_3M: Device: "/dev/input/event9"
[ 18340.528] (--) evdev: Laptop_Integrated_Webcam_3M: Vendor 0x5ca Product 0x1814
[ 18340.528] (--) evdev: Laptop_Integrated_Webcam_3M: Found keys
[ 18340.528] (II) evdev: Laptop_Integrated_Webcam_3M: Configuring as keyboard
[ 18340.528] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input10/event9"
[ 18340.528] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_3M" (type: KEYBOARD, id 10)
[ 18340.528] (**) Option "xkb_rules" "evdev"
[ 18340.528] (**) Option "xkb_model" "pc105"
[ 18340.528] (**) Option "xkb_layout" "br"
[ 18340.529] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event10)
[ 18340.529] (II) No input driver specified, ignoring this device.
[ 18340.529] (II) This device may have been added with another device file.
[ 18340.529] (II) config/udev: Adding input device HDA Intel MID Dock Mic (/dev/input/event11)
[ 18340.529] (II) No input driver specified, ignoring this device.
[ 18340.529] (II) This device may have been added with another device file.
[ 18340.529] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event12)
[ 18340.529] (II) No input driver specified, ignoring this device.
[ 18340.529] (II) This device may have been added with another device file.
[ 18340.529] (II) config/udev: Adding input device HDA Intel MID Dock Line Out (/dev/input/event13)
[ 18340.529] (II) No input driver specified, ignoring this device.
[ 18340.529] (II) This device may have been added with another device file.
[ 18340.530] (II) config/udev: Adding input device LITEON Technology USB Keyboard (/dev/input/event5)
[ 18340.530] (**) LITEON Technology USB Keyboard: Applying InputClass "evdev keyboard catchall"
[ 18340.530] (II) Using input driver 'evdev' for 'LITEON Technology USB Keyboard'
[ 18340.530] (**) LITEON Technology USB Keyboard: always reports core events
[ 18340.530] (**) evdev: LITEON Technology USB Keyboard: Device: "/dev/input/event5"
[ 18340.530] (--) evdev: LITEON Technology USB Keyboard: Vendor 0x45e Product 0x78c
[ 18340.530] (--) evdev: LITEON Technology USB Keyboard: Found keys
[ 18340.530] (II) evdev: LITEON Technology USB Keyboard: Configuring as keyboard
[ 18340.530] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.3/2-1.1.3:1.0/input/input5/event5"
[ 18340.530] (II) XINPUT: Adding extended input device "LITEON Technology USB Keyboard" (type: KEYBOARD, id 11)
[ 18340.530] (**) Option "xkb_rules" "evdev"
[ 18340.530] (**) Option "xkb_model" "pc105"
[ 18340.530] (**) Option "xkb_layout" "br"
[ 18340.530] (II) config/udev: Adding input device SIGMACHIP Usb Mouse (/dev/input/event6)
[ 18340.530] (**) SIGMACHIP Usb Mouse: Applying InputClass "evdev pointer catchall"
[ 18340.530] (II) Using input driver 'evdev' for 'SIGMACHIP Usb Mouse'
[ 18340.530] (**) SIGMACHIP Usb Mouse: always reports core events
[ 18340.530] (**) evdev: SIGMACHIP Usb Mouse: Device: "/dev/input/event6"
[ 18340.530] (--) evdev: SIGMACHIP Usb Mouse: Vendor 0x1c4f Product 0x3
[ 18340.530] (--) evdev: SIGMACHIP Usb Mouse: Found 9 mouse buttons
[ 18340.530] (--) evdev: SIGMACHIP Usb Mouse: Found scroll wheel(s)
[ 18340.530] (--) evdev: SIGMACHIP Usb Mouse: Found relative axes
[ 18340.530] (--) evdev: SIGMACHIP Usb Mouse: Found x and y relative axes
[ 18340.530] (II) evdev: SIGMACHIP Usb Mouse: Configuring as mouse
[ 18340.530] (II) evdev: SIGMACHIP Usb Mouse: Adding scrollwheel support
[ 18340.530] (**) evdev: SIGMACHIP Usb Mouse: YAxisMapping: buttons 4 and 5
[ 18340.530] (**) evdev: SIGMACHIP Usb Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 18340.530] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.4/2-1.1.4:1.0/input/input7/event6"
[ 18340.530] (II) XINPUT: Adding extended input device "SIGMACHIP Usb Mouse" (type: MOUSE, id 12)
[ 18340.530] (II) evdev: SIGMACHIP Usb Mouse: initialized for relative axes.
[ 18340.531] (**) SIGMACHIP Usb Mouse: (accel) keeping acceleration scheme 1
[ 18340.531] (**) SIGMACHIP Usb Mouse: (accel) acceleration profile 0
[ 18340.531] (**) SIGMACHIP Usb Mouse: (accel) acceleration factor: 2.000
[ 18340.531] (**) SIGMACHIP Usb Mouse: (accel) acceleration threshold: 4
[ 18340.531] (II) config/udev: Adding input device SIGMACHIP Usb Mouse (/dev/input/mouse0)
[ 18340.531] (II) No input driver specified, ignoring this device.
[ 18340.531] (II) This device may have been added with another device file.
[ 18340.531] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[ 18340.531] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 18340.531] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 18340.531] (**) AT Translated Set 2 keyboard: always reports core events
[ 18340.531] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[ 18340.531] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[ 18340.531] (--) evdev: AT Translated Set 2 keyboard: Found keys
[ 18340.531] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[ 18340.531] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[ 18340.531] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[ 18340.531] (**) Option "xkb_rules" "evdev"
[ 18340.531] (**) Option "xkb_model" "pc105"
[ 18340.531] (**) Option "xkb_layout" "br"
[ 18340.532] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event14)
[ 18340.532] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[ 18340.532] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[ 18340.532] (II) Using input driver 'evdev' for 'DualPoint Stick'
[ 18340.532] (**) DualPoint Stick: always reports core events
[ 18340.532] (**) evdev: DualPoint Stick: Device: "/dev/input/event14"
[ 18340.532] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[ 18340.532] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[ 18340.532] (--) evdev: DualPoint Stick: Found relative axes
[ 18340.532] (--) evdev: DualPoint Stick: Found x and y relative axes
[ 18340.532] (II) evdev: DualPoint Stick: Configuring as mouse
[ 18340.532] (**) Option "Emulate3Buttons" "true"
[ 18340.532] (**) Option "EmulateWheel" "true"
[ 18340.532] (**) Option "EmulateWheelButton" "2"
[ 18340.532] (**) Option "YAxisMapping" "4 5"
[ 18340.532] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[ 18340.532] (**) Option "XAxisMapping" "6 7"
[ 18340.532] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[ 18340.532] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 18340.532] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input15/event14"
[ 18340.532] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 14)
[ 18340.532] (II) evdev: DualPoint Stick: initialized for relative axes.
[ 18340.532] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[ 18340.532] (**) DualPoint Stick: (accel) acceleration profile 0
[ 18340.532] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[ 18340.532] (**) DualPoint Stick: (accel) acceleration threshold: 4
[ 18340.532] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse1)
[ 18340.532] (II) No input driver specified, ignoring this device.
[ 18340.532] (II) This device may have been added with another device file.
[ 18340.533] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event15)
[ 18340.533] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[ 18340.533] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[ 18340.533] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[ 18340.533] (II) LoadModule: "synaptics"
[ 18340.533] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 18340.533] (II) Module synaptics: vendor="X.Org Foundation"
[ 18340.533] 	compiled for 1.12.99.905, module version = 1.6.2
[ 18340.533] 	Module class: X.Org XInput Driver
[ 18340.533] 	ABI class: X.Org XInput driver, version 18.0
[ 18340.533] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[ 18340.533] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[ 18340.533] (**) Option "Device" "/dev/input/event15"
[ 18340.540] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: ignoring touch events for semi-multitouch device
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 2000
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 1400
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[ 18340.540] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle double triple
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[ 18340.540] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[ 18340.572] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input16/event15"
[ 18340.572] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 15)
[ 18340.572] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[ 18340.572] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: MaxSpeed is now 1.75
[ 18340.572] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: AccelFactor is now 0.082
[ 18340.573] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[ 18340.573] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[ 18340.573] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[ 18340.573] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[ 18340.573] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[ 18340.573] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[ 18340.573] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[ 18340.578] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[ 18340.578] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[ 18340.578] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[ 18340.578] (**) Dell WMI hotkeys: always reports core events
[ 18340.578] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event7"
[ 18340.578] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[ 18340.578] (--) evdev: Dell WMI hotkeys: Found keys
[ 18340.578] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[ 18340.578] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event7"
[ 18340.579] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 16)
[ 18340.579] (**) Option "xkb_rules" "evdev"
[ 18340.579] (**) Option "xkb_model" "pc105"
[ 18340.579] (**) Option "xkb_layout" "br"
[ 18348.284] (EE) 
[ 18348.284] (EE) Backtrace:
[ 18348.304] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f00a2194b76]
[ 18348.304] (EE) 1: /usr/bin/X (0x7f00a1fec000+0x1ac9a9) [0x7f00a21989a9]
[ 18348.304] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f00a1312000+0xfcb0) [0x7f00a1321cb0]
[ 18348.304] (EE) 3: /lib/x86_64-linux-gnu/libc.so.6 (0x7f009ff76000+0x14a3b4) [0x7f00a00c03b4]
[ 18348.304] (EE) 4: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0x584e) [0x7f009df9b84e]
[ 18348.304] (EE) 5: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0x5d03) [0x7f009df9bd03]
[ 18348.304] (EE) 6: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0x851a) [0x7f009df9e51a]
[ 18348.304] (EE) 7: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0x106bf) [0x7f009dfa66bf]
[ 18348.304] (EE) 8: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0x12098) [0x7f009dfa8098]
[ 18348.304] (EE) 9: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0xb56c) [0x7f009dfa156c]
[ 18348.305] (EE) 10: /usr/bin/X (0x7f00a1fec000+0x198ea3) [0x7f00a2184ea3]
[ 18348.305] (EE) 11: /usr/bin/X (0x7f00a1fec000+0xe2830) [0x7f00a20ce830]
[ 18348.305] (EE) 12: /usr/bin/X (0x7f00a1fec000+0x12adb8) [0x7f00a2116db8]
[ 18348.305] (EE) 13: /usr/bin/X (0x7f00a1fec000+0x55a91) [0x7f00a2041a91]
[ 18348.305] (EE) 14: /usr/bin/X (0x7f00a1fec000+0x4456a) [0x7f00a203056a]
[ 18348.305] (EE) 15: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f009ff9776d]
[ 18348.305] (EE) 16: /usr/bin/X (0x7f00a1fec000+0x448ad) [0x7f00a20308ad]
[ 18348.305] (EE) 
[ 18348.305] (EE) Segmentation fault at address 0x50
[ 18348.306] 
Fatal server error:
[ 18348.306] Caught signal 11 (Segmentation fault). Server aborting
[ 18348.306] 
[ 18348.306] (EE) 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[ 18348.306] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 18348.306] (EE) 
[ 18348.328] (II) evdev: Power Button: Close
[ 18348.328] (II) UnloadModule: "evdev"
[ 18348.332] (II) evdev: Video Bus: Close
[ 18348.332] (II) UnloadModule: "evdev"
[ 18348.351] (II) evdev: Power Button: Close
[ 18348.351] (II) UnloadModule: "evdev"
[ 18348.364] (II) evdev: Sleep Button: Close
[ 18348.364] (II) UnloadModule: "evdev"
[ 18348.368] (II) evdev: Laptop_Integrated_Webcam_3M: Close
[ 18348.368] (II) UnloadModule: "evdev"
[ 18348.376] (II) evdev: LITEON Technology USB Keyboard: Close
[ 18348.376] (II) UnloadModule: "evdev"
[ 18348.396] (II) evdev: SIGMACHIP Usb Mouse: Close
[ 18348.396] (II) UnloadModule: "evdev"
[ 18348.412] (II) evdev: AT Translated Set 2 keyboard: Close
[ 18348.412] (II) UnloadModule: "evdev"
[ 18348.412] (II) evdev: DualPoint Stick: Close
[ 18348.412] (II) UnloadModule: "evdev"
[ 18348.416] (II) UnloadModule: "synaptics"
[ 18348.420] (II) evdev: Dell WMI hotkeys: Close
[ 18348.420] (II) UnloadModule: "evdev"
[ 18348.420] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 18348.420] (II) NOUVEAU(0): NVLeaveVT is called.

---

### Post by Hexxus on 2013-07-13
Hello there, I've got a lot of Dell equipment running Ubuntu, just out of curiousity, does it work with 12.04LTS? Try booting it up from a flashdrive on that and see if you can re-produce the problem. I had a few "Weird" things happen with 12.10 and 13.04 but 12.04LTS seemed to have none of them.

---

