---
title: "Ubuntu Desktop Environment fails after log in"
date: 2011-01-28
forum: Desktop Environments
---

### Post by Nickjpost on 2011-01-28
Good morning all!
Last night I upgraded to Ubuntu 10.10 and ran into some problems. I can only work in the desktop GUI in safe mode, the regular Desktop environment loads up rarely. 
Here is some hardware info:
Toshiba Satellite L25-S1217
Intel Celeron 1.6 GHz
RAM 874 MiB
Available disk space 47.5 GiB
 
Now, here is the dmesg output....notice the errors at the bottom (Idon't know what they mean, but I suspect that xwindows is having trouble mounting)
 
[SIZE=2][FONT=Courier New]#Dmesg output:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ea0000 - 0000000037eb3000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037eb3000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x37ea0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 037F00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000037ea0000 (usable)
[    0.000000]  modified: 0000000037ea0000 - 0000000037eb3000 (ACPI data)
[    0.000000]  modified: 0000000037eb3000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  modified: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f73b0] f73b0
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 294f5000 - 29f38000
[    0.000000] ACPI: RSDP 000f7450 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 37eae1d6 00038 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 37eb2f00 00074 (v01 ATI    Goldfish 06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 37eae62b 048D5 (v01    ATI    SB400 06040000 MSFT 0100000C)
[    0.000000] ACPI: FACS 37eb3fc0 00040
[    0.000000] ACPI: APIC 37eb2f74 00050 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 37eb2fc4 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 37eae410 0021B (v01  PmRef  Cpu0Cst 00003001 INTL 20030224)
[    0.000000] ACPI: SSDT 37eae20e 00202 (v01  PmRef    CpuPm 00003000 INTL 20030224)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00037ea0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00037ea0
[    0.000000] On node 0 totalpages: 228912
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 14 pages used for memmap
[    0.000000]   HighMem zone: 1684 pages, LIFO batch:0
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x82
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 38000000 (gap: 38000000:a8000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227122
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=b75bc744-a956-4199-94df-0559b075880d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4580460 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (49 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [00294f5000 - 0029f38000]         RAMDISK
[    0.000000]   #4 [00009a1000 - 00009a4168]             BRK
[    0.000000]   #5 [00000f73c0 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000f73b0 - 00000f73c0]    MP-table mpf
[    0.000000]   #7 [000009f800 - 000009fd70]   BIOS reserved
[    0.000000]   #8 [000009ff10 - 00000f73b0]   BIOS reserved
[    0.000000]   #9 [000009fd70 - 000009ff10]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001701000]         BOOTMEM
[    0.000000]   #15 [0001701000 - 0001701004]         BOOTMEM
[    0.000000]   #16 [0001701040 - 0001701100]         BOOTMEM
[    0.000000]   #17 [0001701100 - 0001701154]         BOOTMEM
[    0.000000]   #18 [0001701180 - 0001704180]         BOOTMEM
[    0.000000]   #19 [0001704180 - 0001704184]         BOOTMEM
[    0.000000]   #20 [00017041c0 - 0001704220]         BOOTMEM
[    0.000000]   #21 [0001704240 - 0001704267]         BOOTMEM
[    0.000000]   #22 [0001704280 - 0001704408]         BOOTMEM
[    0.000000]   #23 [0001704440 - 0001704480]         BOOTMEM
[    0.000000]   #24 [0001704480 - 00017044c0]         BOOTMEM
[    0.000000]   #25 [00017044c0 - 0001704500]         BOOTMEM
[    0.000000]   #26 [0001704500 - 0001704540]         BOOTMEM
[    0.000000]   #27 [0001704540 - 0001704580]         BOOTMEM
[    0.000000]   #28 [0001704580 - 00017045c0]         BOOTMEM
[    0.000000]   #29 [00017045c0 - 0001704600]         BOOTMEM
[    0.000000]   #30 [0001704600 - 0001704640]         BOOTMEM
[    0.000000]   #31 [0001704640 - 0001704680]         BOOTMEM
[    0.000000]   #32 [0001704680 - 00017046c0]         BOOTMEM
[    0.000000]   #33 [00017046c0 - 0001704700]         BOOTMEM
[    0.000000]   #34 [0001704700 - 0001704710]         BOOTMEM
[    0.000000]   #35 [0001704740 - 0001704750]         BOOTMEM
[    0.000000]   #36 [0001704780 - 00017047ea]         BOOTMEM
[    0.000000]   #37 [0001704800 - 000170486a]         BOOTMEM
[    0.000000]   #38 [0001800000 - 000180e000]         BOOTMEM
[    0.000000]   #39 [0001706880 - 0001706884]         BOOTMEM
[    0.000000]   #40 [00017068c0 - 00017068c4]         BOOTMEM
[    0.000000]   #41 [0001706900 - 0001706904]         BOOTMEM
[    0.000000]   #42 [0001706940 - 0001706944]         BOOTMEM
[    0.000000]   #43 [0001706980 - 0001706a30]         BOOTMEM
[    0.000000]   #44 [0001706a40 - 0001706ae8]         BOOTMEM
[    0.000000]   #45 [0001706b00 - 000170ab00]         BOOTMEM
[    0.000000]   #46 [000170ab00 - 000178ab00]         BOOTMEM
[    0.000000]   #47 [000178ab00 - 00017cab00]         BOOTMEM
[    0.000000]   #48 [000180e000 - 0001c6c46c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:00037ea0)
[    0.000000] Memory: 883752k/916096k available (4928k kernel code, 31896k reserved, 2336k data, 684k init, 6792k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]    RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]    RCU-based detection of stalled CPUs is disabled.
[    0.000000]    Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.765 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.53 BogoMIPS (lpj=6383060)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004045] Security Framework initialized
[    0.004074] AppArmor: AppArmor initialized
[    0.004077] Yama: becoming mindful.
[    0.004156] Mount-cache hash table entries: 512
[    0.004337] Initializing cgroup subsys ns
[    0.004343] Initializing cgroup subsys cpuacct
[    0.004349] Initializing cgroup subsys memory
[    0.004362] Initializing cgroup subsys devices
[    0.004366] Initializing cgroup subsys freezer
[    0.004369] Initializing cgroup subsys net_cls
[    0.004413] mce: CPU supports 5 MCE banks
[    0.004427] CPU0: Thermal monitoring enabled (TM1)
[    0.004440] Performance Events: p6 PMU driver.
[    0.004451] ... version:                0
[    0.004454] ... bit width:              32
[    0.004457] ... generic registers:      2
[    0.004460] ... value mask:             00000000ffffffff
[    0.004463] ... max period:             000000007fffffff
[    0.004465] ... fixed-purpose events:   0
[    0.004468] ... event mask:             0000000000000003
[    0.008629] SMP alternatives: switching to UP code
[    0.017709] Freeing SMP alternatives: 24k freed
[    0.017731] ACPI: Core revision 20100428
[    0.028012] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028022] ftrace: allocating 21758 entries in 43 pages
[    0.032127] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032508] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.072252] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
[    0.076000] Brought up 1 CPUs
[    0.076000] Total of 1 processors activated (3191.53 BogoMIPS).
[    0.076000] devtmpfs: initialized
[    0.076000] regulator: core version 0.5
[    0.076000] Time: 11:04:10  Date: 01/28/11
[    0.076000] NET: Registered protocol family 16
[    0.076000] EISA bus registered
[    0.076000] ACPI: bus type pci registered
[    0.076000] PCI: MMCONFIG for domain 0000 [bus 00-0d] at [mem 0xe0000000-0xe0dfffff] (base 0xe0000000)
[    0.076000] PCI: MMCONFIG at [mem 0xe0000000-0xe0dfffff] reserved in E820
[    0.076000] PCI: Using MMCONFIG for extended config space
[    0.076000] PCI: Using configuration type 1 for base access
[    0.076139] bio: create slab <bio-0> at 0
[    0.077435] ACPI: EC: Look up EC in DSDT
[    0.140119] ACPI: Interpreter enabled
[    0.140125] ACPI: (supports S0 S3 S4 S5)
[    0.144027] ACPI: Using IOAPIC for interrupt routing
[    0.149128] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.149439] ACPI: No dock devices found.
[    0.149447] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.150237] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.151750] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.151754] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.151758] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.151762] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.151766] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    0.151770] pci_root PNP0A03:00: host bridge window [mem 0x38000000-0xfebfffff] (ignored)
[    0.151774] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.151777] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.151956] pci 0000:00:13.0: reg 10: [mem 0xc0004000-0xc0004fff]
[    0.152096] pci 0000:00:13.1: reg 10: [mem 0xc0005000-0xc0005fff]
[    0.152233] pci 0000:00:13.2: reg 10: [mem 0xc0006000-0xc0006fff]
[    0.152322] pci 0000:00:13.2: supports D1 D2
[    0.152325] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.152332] pci 0000:00:13.2: PME# disabled
[    0.152384] pci 0000:00:14.0: reg 10: [io  0x8040-0x804f]
[    0.152395] pci 0000:00:14.0: reg 14: [mem 0xc0007000-0xc00073ff]
[    0.152442] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.152492] pci 0000:00:14.1: reg 10: [io  0x8430-0x8437]
[    0.152503] pci 0000:00:14.1: reg 14: [io  0x8424-0x8427]
[    0.152514] pci 0000:00:14.1: reg 18: [io  0x8428-0x842f]
[    0.152525] pci 0000:00:14.1: reg 1c: [io  0x8420-0x8423]
[    0.152536] pci 0000:00:14.1: reg 20: [io  0x8410-0x841f]
[    0.152770] pci 0000:00:14.5: reg 10: [mem 0xc0007400-0xc00074ff]
[    0.152895] pci 0000:00:14.6: reg 10: [mem 0xc0007800-0xc00078ff]
[    0.153054] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.153061] pci 0000:01:05.0: reg 14: [io  0x9000-0x90ff]
[    0.153068] pci 0000:01:05.0: reg 18: [mem 0xc0100000-0xc010ffff]
[    0.153085] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.153103] pci 0000:01:05.0: supports D1 D2
[    0.153133] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.153140] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.153145] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
[    0.153151] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.153221] pci 0000:09:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.153260] pci 0000:09:01.0: supports D1 D2
[    0.153263] pci 0000:09:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.153270] pci 0000:09:01.0: PME# disabled
[    0.153330] pci 0000:09:02.0: reg 10: [io  0xa000-0xa0ff]
[    0.153343] pci 0000:09:02.0: reg 14: [mem 0xc0210000-0xc02100ff]
[    0.153428] pci 0000:09:02.0: supports D1 D2
[    0.153430] pci 0000:09:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.153438] pci 0000:09:02.0: PME# disabled
[    0.153499] pci 0000:09:04.0: reg 10: [mem 0xc0200000-0xc020ffff]
[    0.153671] pci 0000:00:14.4: PCI bridge to [bus 09-0e] (subtractive decode)
[    0.153682] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.153690] pci 0000:00:14.4:   bridge window [mem 0xc0200000-0xc02fffff]
[    0.153697] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.153701] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.153705] pci 0000:00:14.4:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.153794] pci_bus 0000:00: on NUMA node 0
[    0.153801] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.154062] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.154195] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.157344] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.157481] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.157614] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.157747] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.157879] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.158012] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.158144] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.158277] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.158328] HEST: Table is not found!
[    0.158456] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.158461] vgaarb: loaded
[    0.158697] SCSI subsystem initialized
[    0.158786] libata version 3.00 loaded.
[    0.158878] usbcore: registered new interface driver usbfs
[    0.158896] usbcore: registered new interface driver hub
[    0.158932] usbcore: registered new device driver usb
[    0.159115] ACPI: WMI: Mapper loaded
[    0.159119] PCI: Using ACPI for IRQ routing
[    0.159123] PCI: pci_cache_line_size set to 64 bytes
[    0.159214] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.159218] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.159221] reserve RAM buffer: 0000000037ea0000 - 0000000037ffffff 
[    0.159373] NetLabel: Initializing
[    0.159376] NetLabel:  domain hash size = 128
[    0.159378] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.159400] NetLabel:  unlabeled traffic allowed by default
[    0.159456] Switching to clocksource tsc
[    0.172648] AppArmor: AppArmor Filesystem Enabled
[    0.172693] pnp: PnP ACPI init
[    0.172749] ACPI: bus type pnp registered
[    0.175495] pnp 00:09: disabling [mem 0x00000000-0x00000fff] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.175609] pnp: PnP ACPI: found 10 devices
[    0.175612] ACPI: ACPI bus type pnp unregistered
[    0.175619] PnPBIOS: Disabled by ACPI PNP
[    0.175642] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.175653] system 00:08: [io  0x1080] has been reserved
[    0.175656] system 00:08: [io  0x0200-0x020f] has been reserved
[    0.175660] system 00:08: [io  0x040b] has been reserved
[    0.175664] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.175668] system 00:08: [io  0x04d6] has been reserved
[    0.175671] system 00:08: [io  0x0530-0x0537] has been reserved
[    0.175675] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.175679] system 00:08: [io  0x0c14] has been reserved
[    0.175682] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.175686] system 00:08: [io  0x0c6c] has been reserved
[    0.175689] system 00:08: [io  0x0c6f] has been reserved
[    0.175693] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.175697] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.175701] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.175705] system 00:08: [io  0x8000-0x805f] could not be reserved
[    0.175709] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.175713] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.175717] system 00:08: [io  0x0280-0x0293] has been reserved
[    0.175720] system 00:08: [io  0x087f] has been reserved
[    0.175728] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.175732] system 00:09: [mem 0xfff80000-0xffffffff] has been reserved
[    0.212444] pci 0000:00:14.4: BAR 15: assigned [mem 0x38000000-0x3bffffff pref]
[    0.212451] pci 0000:01:05.0: BAR 6: assigned [mem 0xc0120000-0xc013ffff pref]
[    0.212457] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.212462] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.212469] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
[    0.212474] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.212489] pci 0000:09:01.0: BAR 15: assigned [mem 0x38000000-0x3bffffff pref]
[    0.212494] pci 0000:09:01.0: BAR 16: assigned [mem 0x3c000000-0x3fffffff]
[    0.212498] pci 0000:09:01.0: BAR 0: assigned [mem 0xc0211000-0xc0211fff]
[    0.212507] pci 0000:09:01.0: BAR 0: set to [mem 0xc0211000-0xc0211fff] (PCI address [0xc0211000-0xc0211fff]
[    0.212513] pci 0000:09:01.0: BAR 13: assigned [io  0xa400-0xa4ff]
[    0.212516] pci 0000:09:01.0: BAR 14: assigned [io  0xa800-0xa8ff]
[    0.212521] pci 0000:09:01.0: CardBus bridge to [bus 0a-0d]
[    0.212524] pci 0000:09:01.0:   bridge window [io  0xa400-0xa4ff]
[    0.212540] pci 0000:09:01.0:   bridge window [io  0xa800-0xa8ff]
[    0.212548] pci 0000:09:01.0:   bridge window [mem 0x38000000-0x3bffffff pref]
[    0.212556] pci 0000:09:01.0:   bridge window [mem 0x3c000000-0x3fffffff]
[    0.212564] pci 0000:00:14.4: PCI bridge to [bus 09-0e]
[    0.212569] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.212579] pci 0000:00:14.4:   bridge window [mem 0xc0200000-0xc02fffff]
[    0.212586] pci 0000:00:14.4:   bridge window [mem 0x38000000-0x3bffffff pref]
[    0.212629] pci 0000:09:01.0: enabling device (0000 -> 0003)
[    0.212643]   alloc irq_desc for 20 on node -1
[    0.212647]   alloc kstat_irqs on node -1
[    0.212660] pci 0000:09:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.212672] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.212676] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.212679] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.212682] pci_bus 0000:01: resource 1 [mem 0xc0100000-0xc01fffff]
[    0.212686] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff pref]
[    0.212690] pci_bus 0000:09: resource 0 [io  0xa000-0xafff]
[    0.212693] pci_bus 0000:09: resource 1 [mem 0xc0200000-0xc02fffff]
[    0.212697] pci_bus 0000:09: resource 2 [mem 0x38000000-0x3bffffff pref]
[    0.212700] pci_bus 0000:09: resource 4 [io  0x0000-0xffff]
[    0.212703] pci_bus 0000:09: resource 5 [mem 0x00000000-0xffffffff]
[    0.212707] pci_bus 0000:0a: resource 0 [io  0xa400-0xa4ff]
[    0.212710] pci_bus 0000:0a: resource 1 [io  0xa800-0xa8ff]
[    0.212714] pci_bus 0000:0a: resource 2 [mem 0x38000000-0x3bffffff pref]
[    0.212717] pci_bus 0000:0a: resource 3 [mem 0x3c000000-0x3fffffff]
[    0.212795] NET: Registered protocol family 2
[    0.212902] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.213376] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.215752] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.217277] TCP: Hash tables configured (established 131072 bind 65536)
[    0.217283] TCP reno registered
[    0.217295] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.217345] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.217634] NET: Registered protocol family 1
[    0.217677] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.892698] pci 0000:01:05.0: Boot video device
[    0.892719] PCI: CLS 32 bytes, default 64
[    0.893048] cpufreq-nforce2: No nForce2 chipset.
[    0.893095] Scanning for low memory corruption every 60 seconds
[    0.893398] audit: initializing netlink socket (disabled)
[    0.893423] type=2000 audit(1296212650.891:1): initialized
[    0.907902] Trying to unpack rootfs image as initramfs...
[    0.924949] highmem bounce pool size: 64 pages
[    0.924961] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.931080] VFS: Disk quotas dquot_6.5.2
[    0.931194] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.937379] fuse init (API version 7.14)
[    0.937573] msgmni has been set to 1712
[    0.945468] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.945475] io scheduler noop registered
[    0.945478] io scheduler deadline registered
[    0.945506] io scheduler cfq registered (default)
[    0.945700] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.945731] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.949365] ACPI: AC Adapter [ACAD] (on-line)
[    0.949490] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.955675] ACPI: Lid Switch [LID]
[    0.955787] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.955796] ACPI: Power Button [PWRB]
[    0.955860] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.955864] ACPI: Power Button [PWRF]
[    0.956096] ACPI: acpi_idle registered with cpuidle
[    0.956308] Marking TSC unstable due to TSC halts in idle
[    0.962338] Switching to clocksource acpi_pm
[    0.974531] thermal LNXTHERM:01: registered as thermal_zone0
[    0.974553] ACPI: Thermal Zone [THRM] (30 C)
[    0.974712] ERST: Table is not found!
[    0.975035] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.975562]   alloc irq_desc for 17 on node -1
[    0.975565]   alloc kstat_irqs on node -1
[    0.975579] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.975590] serial 0000:00:14.6: PCI INT B disabled
[    0.977238] brd: module loaded
[    0.977990] loop: module loaded
[    0.978371]   alloc irq_desc for 16 on node -1
[    0.978375]   alloc kstat_irqs on node -1
[    0.978384] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.978463] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.978912] Fixed MDIO Bus: probed
[    0.978959] PPP generic driver version 2.4.2
[    0.979042] tun: Universal TUN/TAP device driver, 1.6
[    0.979044] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.979163] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.979193]   alloc irq_desc for 19 on node -1
[    0.979196]   alloc kstat_irqs on node -1
[    0.979204] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.979235] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.979283] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.979379] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0006000
[    0.984281] ACPI: Battery Slot [BAT1] (battery absent)
[    0.984329] isapnp: Scanning for PnP cards...
[    0.989894] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.990151] hub 1-0:1.0: USB hub found
[    0.990162] hub 1-0:1.0: 8 ports detected
[    0.990292] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.990327] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.990358] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.990421] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.990456] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0004000
[    1.052635] hub 2-0:1.0: USB hub found
[    1.052653] hub 2-0:1.0: 4 ports detected
[    1.052782] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.052819] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.052892] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    1.052934] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0005000
[    1.140589] hub 3-0:1.0: USB hub found
[    1.140606] hub 3-0:1.0: 4 ports detected
[    1.140746] uhci_hcd: USB Universal Host Controller Interface driver
[    1.140940] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.143041] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.143057] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.143261] mice: PS/2 mouse device common for all mice
[    1.143488] rtc_cmos 00:04: RTC can wake from S4
[    1.143553] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.143592] rtc0: alarms up to one month, 114 bytes nvram
[    1.143773] device-mapper: uevent: version 1.0.3
[    1.152674] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.152826] device-mapper: multipath: version 1.1.1 loaded
[    1.152831] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.153059] EISA: Probing bus 0 at eisa.0
[    1.153076] Cannot allocate resource for EISA slot 1
[    1.153110] Cannot allocate resource for EISA slot 8
[    1.153113] EISA: Detected 0 cards.
[    1.158257] cpuidle: using governor ladder
[    1.158333] cpuidle: using governor menu
[    1.158784] TCP cubic registered
[    1.158991] NET: Registered protocol family 10
[    1.159479] lo: Disabled Privacy Extensions
[    1.159752] NET: Registered protocol family 17
[    1.159863] Using IPI No-Shortcut mode
[    1.160069] PM: Resume from disk failed.
[    1.160089] registered taskstats version 1
[    1.160370]   Magic number: 11:750:75
[    1.160551] rtc_cmos 00:04: setting system clock to 2011-01-28 11:04:11 UTC (1296212651)
[    1.160556] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.160559] EDD information not available.
[    1.176449] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.667780] isapnp: No Plug & Play device found
[    1.718029] Freeing initrd memory: 10508k freed
[    1.746760] Freeing unused kernel memory: 684k freed
[    1.748873] Write protecting the kernel text: 4932k
[    1.748923] Write protecting the kernel read-only data: 1976k
[    1.770280] udev[65]: starting version 163
[    2.040210] scsi0 : pata_atiixp
[    2.048173] scsi1 : pata_atiixp
[    2.048742] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    2.048746] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    2.054241] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.054278] 8139cp 0000:09:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.213323] ata2.00: ATAPI: DVD/CDRW UJDA770, 1.50, max UDMA/33
[    2.213632] ata1.00: ATA-6: TOSHIBA MK6034GAX, AC101A, max UDMA/100
[    2.213636] ata1.00: 117210240 sectors, multi 16: LBA48 
[    2.221227] ata2.00: configured for UDMA/33
[    2.221497] ata1.00: configured for UDMA/100
[    2.221727] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6034GA AC10 PQ: 0 ANSI: 5
[    2.221963] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.222340] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.222411] sd 0:0:0:0: [sda] Write Protect is off
[    2.222415] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.222447] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.222654]  sda:
[    2.224225] scsi 1:0:0:0: CD-ROM            MATSHITA DVD/CDRW UJDA770 1.50 PQ: 0 ANSI: 5
[    2.228059] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.228064] Uniform CD-ROM driver Revision: 3.20
[    2.228492] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.228654] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.259091]  sda1 sda2 < sda5 >
[    2.289931] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.306812] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.306886]   alloc irq_desc for 21 on node -1
[    2.306890]   alloc kstat_irqs on node -1
[    2.306903] 8139too 0000:09:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.311955] 8139too 0000:09:02.0: eth0: RealTek RTL8139 at 0xa000, 00:16:36:2f:2e:93, IRQ 21
[    2.644461] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.644469] EXT4-fs (sda1): write access will be enabled during recovery
[    3.334005] EXT4-fs (sda1): orphan cleanup on readonly fs
[    3.334021] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1179692
[    3.334130] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1179691
[    3.334149] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 786686
[    3.334168] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 786681
[    3.334182] EXT4-fs (sda1): 4 orphan inodes deleted
[    3.334187] EXT4-fs (sda1): recovery complete
[    3.682616] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   19.462903] Adding 2437116k swap on /dev/sda5.  Priority:-1 extents:1 across:2437116k 
[   19.493429] udev[284]: starting version 163
[   19.599304] lp: driver loaded but no devices found
[   19.897499] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.151717] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[   20.238372] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.382579] Linux agpgart interface v0.103
[   20.448531] yenta_cardbus 0000:09:01.0: CardBus bridge found [1179:ff31]
[   20.448568] yenta_cardbus 0000:09:01.0: Using CSCINT to route CSC interrupts to PCI
[   20.448571] yenta_cardbus 0000:09:01.0: Routing CardBus interrupts to PCI
[   20.448581] yenta_cardbus 0000:09:01.0: TI: mfunc 0x015c1d22, devctl 0x44
[   20.604148] type=1400 audit(1296212670.940:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=599 comm="apparmor_parser"
[   20.604970] type=1400 audit(1296212670.940:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=599 comm="apparmor_parser"
[   20.605426] type=1400 audit(1296212670.940:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=599 comm="apparmor_parser"
[   20.617755] cfg80211: Calling CRDA to update world regulatory domain
[   20.674275] cfg80211: World regulatory domain updated:
[   20.674281]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.674286]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.674290]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.674293]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.674297]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.674301]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.697303] yenta_cardbus 0000:09:01.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   20.697311] yenta_cardbus 0000:09:01.0: Socket status: 30000007
[   20.697324] yenta_cardbus 0000:09:01.0: pcmcia: parent PCI bridge window: [io  0xa000-0xafff]
[   20.697330] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: excluding 0xa000-0xa0ff 0xa400-0xa4ff 0xa800-0xa8ff
[   20.738315] yenta_cardbus 0000:09:01.0: pcmcia: parent PCI bridge window: [mem 0xc0200000-0xc02fffff]
[   20.738325] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc0200000-0xc02fffff: excluding 0xc0200000-0xc021ffff
[   20.738343] yenta_cardbus 0000:09:01.0: pcmcia: parent PCI bridge window: [mem 0x38000000-0x3bffffff pref]
[   20.738347] pcmcia_socket pcmcia_socket0: cs: memory probe 0x38000000-0x3bffffff: excluding 0x38000000-0x3bffffff
[   20.778628] [drm] Initialized drm 1.1.0 20060810
[   20.912933] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x200-0x20f 0x280-0x297 0x370-0x377
[   20.915850] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x408-0x40f 0x4d0-0x4d7
[   20.933492] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   20.934444] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   20.935355] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   20.935427] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   20.935497] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   20.935576] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   20.970995] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0/0x0
[   20.971003] synaptics: Toshiba Satellite L25                     detected, limiting rate to 40pps.
[   21.011264]   alloc irq_desc for 22 on node -1
[   21.011269]   alloc kstat_irqs on node -1
[   21.011282] ath5k 0000:09:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.011366] ath5k 0000:09:04.0: registered as 'phy0'
[   21.557437] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input4
[   21.585575] eth0: link down
[   21.585966] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.717470] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.741689] type=1400 audit(1296212672.076:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=717 comm="apparmor_parser"
[   21.757935] type=1400 audit(1296212672.092:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=718 comm="apparmor_parser"
[   21.758761] type=1400 audit(1296212672.092:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=718 comm="apparmor_parser"
[   21.759225] type=1400 audit(1296212672.092:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=718 comm="apparmor_parser"
[   21.767069] type=1400 audit(1296212672.100:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=719 comm="apparmor_parser"
[   21.770133] [drm] radeon defaulting to kernel modesetting.
[   21.770141] [drm] radeon kernel modesetting enabled.
[   21.770251] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.784871] [drm] initializing kernel modesetting (RS400 0x1002:0x5A62).
[   21.785019] [drm] register mmio base: 0xC0100000
[   21.785022] [drm] register mmio size: 65536
[   21.785291] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   21.785355] [drm] Generation 2 PCI interface, using max accessible memory
[   21.785362] radeon 0000:01:05.0: VRAM: 128M 0x38000000 - 0x3FFFFFFF (128M used)
[   21.785367] radeon 0000:01:05.0: GTT: 32M 0x40000000 - 0x41FFFFFF
[   21.785409] [drm] radeon: irq initialized.
[   21.786025] [drm] Detected VRAM RAM=128M, BAR=256M
[   21.786032] [drm] RAM width 128bits DDR
[   21.788340] type=1400 audit(1296212672.124:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=719 comm="apparmor_parser"
[   21.789301] [TTM] Zone  kernel: Available graphics memory: 444088 kiB.
[   21.789305] [TTM] Zone highmem: Available graphics memory: 447484 kiB.
[   21.789308] [TTM] Initializing pool allocator.
[   21.789342] [drm] radeon: 128M of VRAM memory ready
[   21.789344] [drm] radeon: 32M of GTT memory ready.
[   21.789386] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   21.791271] [drm] radeon: 4 quad pipes, 1 z pipes initialized.
[   21.793146] [drm] Loading R300 Microcode
[   21.799128] [drm] radeon: ring at 0x0000000040000000
[   21.799158] [drm] ring test succeeded in 1 usecs
[   21.799353] [drm] radeon: ib pool ready.
[   21.799471] [drm] ib test succeeded in 0 usecs
[   21.799528] [drm] Default TV standard: NTSC
[   21.799530] [drm] 14.318180000 MHz TV ref clk
[   21.801591] [drm] Panel ID String: SHP                     
[   21.801595] [drm] Panel Size 1024x768
[   21.802776] [drm] Default TV standard: NTSC
[   21.802779] [drm] 14.318180000 MHz TV ref clk
[   21.802935] [drm] Radeon Display Connectors
[   21.802938] [drm] Connector 0:
[   21.802941] [drm]   VGA
[   21.802945] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   21.802947] [drm]   Encoders:
[   21.802950] [drm]     CRT1: INTERNAL_DAC2
[   21.802952] [drm] Connector 1:
[   21.802954] [drm]   LVDS
[   21.802957] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   21.802960] [drm]   Encoders:
[   21.802962] [drm]     LCD1: INTERNAL_LVDS
[   21.802964] [drm] Connector 2:
[   21.802966] [drm]   S-video
[   21.802968] [drm]   Encoders:
[   21.802970] [drm]     TV1: INTERNAL_DAC2
[   21.822157] type=1400 audit(1296212672.156:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=719 comm="apparmor_parser"
[   21.828082] MC'97 0 converters and GPIO not ready (0x1)
[   21.829555] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   22.095434] [drm] fb mappable at 0xD0040000
[   22.095439] [drm] vram apper at 0xD0000000
[   22.095441] [drm] size 3145728
[   22.095443] [drm] fb depth is 24
[   22.095446] [drm]    pitch is 4096
[   22.149941] Console: switching to colour frame buffer device 128x48
[   22.154337] fb0: radeondrmfb frame buffer device
[   22.154339] drm: registered panic notifier
[   22.157215] Slow work thread pool: Starting up
[   22.165805] Slow work thread pool: Ready
[   22.165826] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[   22.710606] ath: EEPROM regdomain: 0x64
[   22.710610] ath: EEPROM indicates we should expect a direct regpair map
[   22.710617] ath: Country alpha2 being used: 00
[   22.710620] ath: Regpair used: 0x64
[   22.737783] phy0: Selected rate control algorithm 'minstrel'
[   22.738599] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   22.810468] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.881537] ppdev: user-space parallel port driver
[   23.736088] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.639507] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
 [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Again, I don't really understand much of these so any help is welcome. Those last two entries concern me. [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]Thanks in advance to those who take the time to reply!![/FONT][/SIZE]

---

### Post by Nickjpost on 2011-01-29
The issue here, in case the 99 viewers of this thread are curious, was a driver that needed to be configured/changed.
For more info if you have a similar issue and have a radeon/ATI graphics card check out this document and follow the applicable links:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

