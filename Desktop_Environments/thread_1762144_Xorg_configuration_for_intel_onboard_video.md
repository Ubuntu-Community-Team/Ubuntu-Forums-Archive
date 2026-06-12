---
title: "Xorg configuration for intel onboard video"
date: 2011-05-18
forum: Desktop Environments
---

### Post by reedk on 2011-05-18
My PCI-E Nvidia card died, and I want to use the onboard video from my H55 chipset, which Windows identifies as "Intel 5 Series/3400 Series". This is on 10.04 LTS.
I did 'apt-get purge nvidia*' followed by adding "intel" as the driver in xorg.conf, but on boot I get the message:
```
intel0: no valid modes found
Screen(s) found but none has a usable configuration

```

Any advice? 


Current xorg.conf:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "intel"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-30-generic-pae (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #59-Ubuntu SMP Tue Mar 1 23:01:33 UTC 2011 (Ubuntu 2.6.32-30.59-generic-pae 2.6.32.29+drm33.13)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d77e0000 (usable)
[    0.000000]  BIOS-e820: 00000000d77e0000 - 00000000d77e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000d77e3000 - 00000000d77f0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d77f0000 - 00000000d7800000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000118000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x118000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CDFFF write-protect
[    0.000000]   CE000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 0D8000000 mask FF8000000 uncachable
[    0.000000]   3 base 100000000 mask FE0000000 write-back
[    0.000000]   4 base 118000000 mask FF8000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d8000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000d77e0000 (usable)
[    0.000000]  modified: 00000000d77e0000 - 00000000d77e3000 (ACPI NVS)
[    0.000000]  modified: 00000000d77e3000 - 00000000d77f0000 (ACPI data)
[    0.000000]  modified: 00000000d77f0000 - 00000000d7800000 (reserved)
[    0.000000]  modified: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000118000000 (usable)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 7000-d000
[    0.000000] RAMDISK: 3733f000 - 37fef81d
[    0.000000] Allocated new RAMDISK: 00943000 - 015f381d
[    0.000000] Move RAMDISK from 000000003733f000 - 0000000037fef81c to 00943000 - 015f381c
[    0.000000] ACPI: RSDP 000f70c0 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT d77e3040 00040 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP d77e30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT d77e3180 055B4 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS d77e0000 00040
[    0.000000] ACPI: HPET d77e8880 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG d77e8900 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: EUDS d77e8940 004D0 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG d77e8e10 00A4A (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC d77e8780 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT d77e9880 014C0 (v01  INTEL PPM RCM  80000001 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3590MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00009000 - 0000ff40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000093a818]    TEXT DATA BSS ==> [0000100000 - 000093a818]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [000093b000 - 00009420f6]              BRK ==> [000093b000 - 00009420f6]
[    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #7 [0000943000 - 00015f381d]      NEW RAMDISK ==> [0000943000 - 00015f381d]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00f5700] f5700
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x00118000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000d77e0
[    0.000000]     0: 0x00100000 -> 0x00118000
[    0.000000] On node 0 totalpages: 980857
[    0.000000] free_area_init_node: node 0, pgdat c07daf40, node_mem_map c15f5000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7181 pages used for memmap
[    0.000000]   HighMem zone: 745941 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d7800000 (gap: d7800000:1c800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c3a00000 s39480 r0 d21960 u262144
[    0.000000] pcpu-alloc: s39480 r0 d21960 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 971896
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic-pae root=UUID=d7bb7d35-7ff4-41b9-975b-a298f8213387 ro vga=795 quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 22937600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:00118000)
[    0.000000] Memory: 3841080k/4587520k available (4842k kernel code, 81072k reserved, 2219k data, 680k init, 3012488k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07e6000 - 0xc0890000   ( 680 kB)
[    0.000000]       .data : 0xc05ba91f - 0xc07e58c8   (2219 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05ba91f   (4842 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:472
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000]   alloc irq_desc for 24 on node -1
[    0.000000]   alloc kstat_irqs on node -1
[    0.000000]   alloc irq_desc for 25 on node -1
[    0.000000]   alloc kstat_irqs on node -1
[    0.000000]   alloc irq_desc for 26 on node -1
[    0.000000]   alloc kstat_irqs on node -1
[    0.000000]   alloc irq_desc for 27 on node -1
[    0.000000]   alloc kstat_irqs on node -1
[    0.000000]   alloc irq_desc for 28 on node -1
[    0.000000]   alloc kstat_irqs on node -1
[    0.000000] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2934.234 MHz processor.
[    0.000029] Calibrating delay loop (skipped), value calculated using timer frequency.. 5868.46 BogoMIPS (lpj=11736936)
[    0.000093] Security Framework initialized
[    0.000166] AppArmor: AppArmor initialized
[    0.000198] Mount-cache hash table entries: 512
[    0.000802] Initializing cgroup subsys ns
[    0.000809] Initializing cgroup subsys cpuacct
[    0.000836] Initializing cgroup subsys memory
[    0.000867] Initializing cgroup subsys devices
[    0.000870] Initializing cgroup subsys freezer
[    0.000874] Initializing cgroup subsys net_cls
[    0.000967] CPU: Physical Processor ID: 0
[    0.000969] CPU: Processor Core ID: 0
[    0.000997] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001001] CPU: L2 cache: 256K
[    0.001003] CPU: L3 cache: 4096K
[    0.001031] mce: CPU supports 9 MCE banks
[    0.001092] CPU0: Thermal monitoring enabled (TM1)
[    0.001098] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6
[    0.001133] using mwait in idle threads.
[    0.001162] Performance Events: Westmere events, Intel PMU driver.
[    0.001192] ... version:                3
[    0.001195] ... bit width:              48
[    0.001197] ... generic registers:      4
[    0.001220] ... value mask:             0000ffffffffffff
[    0.001224] ... max period:             000000007fffffff
[    0.001227] ... fixed-purpose events:   3
[    0.001229] ... event mask:             000000070000000f
[    0.001257] Checking 'hlt' instruction... OK.
[    0.032052] ACPI: Core revision 20090903
[    0.088595] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.088602] ftrace: allocating 22430 entries in 44 pages
[    0.129023] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.129764] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.169674] CPU0: Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz stepping 02
[    0.275996] Booting processor 1 APIC 0x4 ip 0x6000
[    0.286575] Initializing CPU#1
[    0.363150] CPU: Physical Processor ID: 0
[    0.363153] CPU: Processor Core ID: 2
[    0.363179] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.363182] CPU: L2 cache: 256K
[    0.363184] CPU: L3 cache: 4096K
[    0.363248] CPU1: Thermal monitoring enabled (TM1)
[    0.363254] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6
[    0.363410] CPU1: Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz stepping 02
[    0.363442] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.384011] Booting processor 2 APIC 0x1 ip 0x6000
[    0.394376] Initializing CPU#2
[    0.474714] CPU: Physical Processor ID: 0
[    0.474717] CPU: Processor Core ID: 0
[    0.474745] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.474749] CPU: L2 cache: 256K
[    0.474752] CPU: L3 cache: 4096K
[    0.474841] CPU2: Thermal monitoring enabled (TM1)
[    0.474847] CPU 2 MCA banks SHD:2 SHD:3 SHD:5 SHD:6
[    0.474967] CPU2: Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz stepping 02
[    0.475002] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.495601] Booting processor 3 APIC 0x5 ip 0x6000
[    0.505936] Initializing CPU#3
[    0.586281] CPU: Physical Processor ID: 0
[    0.586304] CPU: Processor Core ID: 2
[    0.586309] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.586312] CPU: L2 cache: 256K
[    0.586314] CPU: L3 cache: 4096K
[    0.586378] CPU3: Thermal monitoring enabled (TM1)
[    0.586405] CPU 3 MCA banks SHD:2 SHD:3 SHD:5 SHD:6
[    0.586526] CPU3: Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz stepping 02
[    0.586559] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.606680] Brought up 4 CPUs
[    0.606684] Total of 4 processors activated (23465.59 BogoMIPS).
[    0.614957] CPU0 attaching sched-domain:
[    0.614988]  domain 0: span 0,2 level SIBLING
[    0.614992]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[    0.615021]   domain 1: span 0-3 level MC
[    0.615026]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    0.615081] CPU1 attaching sched-domain:
[    0.615084]  domain 0: span 1,3 level SIBLING
[    0.615088]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[    0.615116]   domain 1: span 0-3 level MC
[    0.615120]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    0.615150] CPU2 attaching sched-domain:
[    0.615153]  domain 0: span 0,2 level SIBLING
[    0.615156]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[    0.615185]   domain 1: span 0-3 level MC
[    0.615188]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    0.615218] CPU3 attaching sched-domain:
[    0.615221]  domain 0: span 1,3 level SIBLING
[    0.615245]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[    0.615252]   domain 1: span 0-3 level MC
[    0.615276]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    0.616823] devtmpfs: initialized
[    0.618568] regulator: core version 0.5
[    0.618659] Time: 20:17:06  Date: 05/18/11
[    0.618887] NET: Registered protocol family 16
[    0.619376] Trying to unpack rootfs image as initramfs...
[    0.619407] EISA bus registered
[    0.619463] ACPI: bus type pci registered
[    0.619783] PCI: MCFG configuration 0: base f4000000 segment 0 buses 0 - 63
[    0.619788] PCI: MCFG area at f4000000 reserved in E820
[    0.619791] PCI: Using MMCONFIG for extended config space
[    0.619815] PCI: Using configuration type 1 for base access
[    0.624064] bio: create slab <bio-0> at 0
[    0.627545] ACPI: EC: Look up EC in DSDT
[    0.657677] ACPI: Interpreter enabled
[    0.657708] ACPI: (supports S0 S3 S4 S5)
[    0.657804] ACPI: Using IOAPIC for interrupt routing
[    0.682686] ACPI Warning: Incorrect checksum in table [TAMG] - 27, should be 26 (20090903/tbutils-314)
[    0.683383] ACPI: No dock devices found.
[    0.683872] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.684221] pci 0000:00:02.0: reg 10 64bit mmio: [0xfb800000-0xfbbfffff]
[    0.684252] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.684259] pci 0000:00:02.0: reg 20 io port: [0xff00-0xff07]
[    0.684518] pci 0000:00:16.0: reg 10 64bit mmio: [0xfbfff000-0xfbfff00f]
[    0.684675] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.684681] pci 0000:00:16.0: PME# disabled
[    0.684868] pci 0000:00:1a.0: reg 20 io port: [0xfe00-0xfe1f]
[    0.685089] pci 0000:00:1a.1: reg 20 io port: [0xfd00-0xfd1f]
[    0.685289] pci 0000:00:1a.2: reg 20 io port: [0xfc00-0xfc1f]
[    0.685512] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfbffe000-0xfbffe3ff]
[    0.685675] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.685702] pci 0000:00:1a.7: PME# disabled
[    0.685830] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfbff4000-0xfbff7fff]
[    0.685961] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.685967] pci 0000:00:1b.0: PME# disabled
[    0.686161] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.686187] pci 0000:00:1c.0: PME# disabled
[    0.686412] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.686418] pci 0000:00:1c.5: PME# disabled
[    0.686580] pci 0000:00:1d.0: reg 20 io port: [0xfb00-0xfb1f]
[    0.686801] pci 0000:00:1d.1: reg 20 io port: [0xfa00-0xfa1f]
[    0.687021] pci 0000:00:1d.2: reg 20 io port: [0xf900-0xf91f]
[    0.687245] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfbffd000-0xfbffd3ff]
[    0.687409] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.687414] pci 0000:00:1d.7: PME# disabled
[    0.687986] pci 0000:00:1f.2: reg 10 io port: [0xf800-0xf807]
[    0.687994] pci 0000:00:1f.2: reg 14 io port: [0xf700-0xf703]
[    0.688022] pci 0000:00:1f.2: reg 18 io port: [0xf600-0xf607]
[    0.688050] pci 0000:00:1f.2: reg 1c io port: [0xf500-0xf503]
[    0.688058] pci 0000:00:1f.2: reg 20 io port: [0xf400-0xf41f]
[    0.688087] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfbffc000-0xfbffc7ff]
[    0.688185] pci 0000:00:1f.2: PME# supported from D3hot
[    0.688190] pci 0000:00:1f.2: PME# disabled
[    0.688285] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfbffb000-0xfbffb0ff]
[    0.688343] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.688669] pci 0000:02:00.0: reg 10 io port: [0xee00-0xeeff]
[    0.688732] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfbeff000-0xfbefffff]
[    0.688769] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfbef8000-0xfbefbfff]
[    0.688801] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.688925] pci 0000:02:00.0: supports D1 D2
[    0.688928] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.688955] pci 0000:02:00.0: PME# disabled
[    0.689121] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
[    0.689146] pci 0000:00:1c.5: bridge 32bit mmio: [0xfbd00000-0xfbdfffff]
[    0.689155] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xfbe00000-0xfbefffff]
[    0.689309] pci 0000:00:1e.0: transparent bridge
[    0.689375] pci_bus 0000:00: on NUMA node 0
[    0.689403] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.690764] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.691086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.691397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.776793] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.777282] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.777793] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.778305] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.778789] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.779272] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.779757] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.780240] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.780820] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.780876] vgaarb: loaded
[    0.781459] SCSI subsystem initialized
[    0.782136] libata version 3.00 loaded.
[    0.782495] usbcore: registered new interface driver usbfs
[    0.782555] usbcore: registered new interface driver hub
[    0.782687] usbcore: registered new device driver usb
[    0.783260] ACPI: WMI: Mapper loaded
[    0.783264] PCI: Using ACPI for IRQ routing
[    0.783906] NetLabel: Initializing
[    0.783909] NetLabel:  domain hash size = 128
[    0.783912] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.783998] NetLabel:  unlabeled traffic allowed by default
[    0.784163] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
[    0.784195] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.789555] hpet: hpet2 irq 24 for MSI
[    0.790027] hpet: hpet3 irq 25 for MSI
[    0.793940] hpet: hpet4 irq 26 for MSI
[    0.798692] hpet: hpet5 irq 27 for MSI
[    0.798783] Switching to clocksource tsc
[    0.810950] AppArmor: AppArmor Filesystem Enabled
[    0.810990] pnp: PnP ACPI init
[    0.811055] ACPI: bus type pnp registered
[    0.821960] pnp: PnP ACPI: found 12 devices
[    0.821963] ACPI: ACPI bus type pnp unregistered
[    0.821992] PnPBIOS: Disabled by ACPI PNP
[    0.822031] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.822056] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.822060] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.822085] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.822089] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.822121] system 00:08: ioport range 0x400-0x47f has been reserved
[    0.822125] system 00:08: ioport range 0x580-0x5ff has been reserved
[    0.822158] system 00:09: iomem range 0xf4000000-0xf7ffffff has been reserved
[    0.822187] system 00:0a: iomem range 0xd1a00-0xd3fff has been reserved
[    0.822192] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
[    0.822217] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.822221] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.822246] system 00:0a: iomem range 0xd77e0000-0xd77effff could not be reserved
[    0.822251] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.822255] system 00:0a: iomem range 0x100000-0xd77dffff could not be reserved
[    0.822280] system 00:0a: iomem range 0xd77f0000-0xd77fffff has been reserved
[    0.822285] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.822310] system 00:0a: iomem range 0xfed10000-0xfed1dfff has been reserved
[    0.822315] system 00:0a: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.822319] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.822345] system 00:0a: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.822349] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[    0.822374] system 00:0a: iomem range 0xe0000-0xeffff has been reserved
[    0.857592] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.857618] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.857625] pci 0000:00:1c.0:   MEM window: 0xd8000000-0xd81fffff
[    0.857656] pci 0000:00:1c.0:   PREFETCH window: 0x000000d8200000-0x000000d83fffff
[    0.857687] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.857692] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
[    0.857719] pci 0000:00:1c.5:   MEM window: 0xfbd00000-0xfbdfffff
[    0.857725] pci 0000:00:1c.5:   PREFETCH window: 0x000000fbe00000-0x000000fbefffff
[    0.857753] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.857756] pci 0000:00:1e.0:   IO window: disabled
[    0.857782] pci 0000:00:1e.0:   MEM window: disabled
[    0.857787] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.857845] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.857877]   alloc irq_desc for 16 on node -1
[    0.857880]   alloc kstat_irqs on node -1
[    0.857911] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.857940] pci 0000:00:1c.0: setting latency timer to 64
[    0.857951]   alloc irq_desc for 17 on node -1
[    0.857974]   alloc kstat_irqs on node -1
[    0.857979] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.858005] pci 0000:00:1c.5: setting latency timer to 64
[    0.858014] pci 0000:00:1e.0: setting latency timer to 64
[    0.858042] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.858046] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.858071] pci_bus 0000:01: resource 0 io:  [0x1000-0x1fff]
[    0.858075] pci_bus 0000:01: resource 1 mem: [0xd8000000-0xd81fffff]
[    0.858079] pci_bus 0000:01: resource 2 pref mem [0xd8200000-0xd83fffff]
[    0.858104] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.858107] pci_bus 0000:02: resource 1 mem: [0xfbd00000-0xfbdfffff]
[    0.858111] pci_bus 0000:02: resource 2 pref mem [0xfbe00000-0xfbefffff]
[    0.858136] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.858140] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.858299] NET: Registered protocol family 2
[    0.858691] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.859844] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.863191] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.864838] TCP: Hash tables configured (established 131072 bind 65536)
[    0.864864] TCP reno registered
[    0.865248] NET: Registered protocol family 1
[    0.865317] pci 0000:00:02.0: Boot video device
[    0.898863] cpufreq-nforce2: No nForce2 chipset.
[    0.898995] Scanning for low memory corruption every 60 seconds
[    0.899448] audit: initializing netlink socket (disabled)
[    0.899507] type=2000 audit(1305749825.704:1): initialized
[    0.948747] highmem bounce pool size: 64 pages
[    0.948758] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.954839] VFS: Disk quotas dquot_6.5.2
[    0.955091] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.957480] fuse init (API version 7.13)
[    0.957832] msgmni has been set to 1620
[    0.958945] alg: No test for stdrng (krng)
[    0.959178] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.959204] io scheduler noop registered
[    0.959208] io scheduler anticipatory registered
[    0.959231] io scheduler deadline registered
[    0.959369] io scheduler cfq registered (default)
[    0.959909]   alloc irq_desc for 29 on node -1
[    0.959913]   alloc kstat_irqs on node -1
[    0.959971] pcieport 0000:00:1c.0: irq 29 for MSI/MSI-X
[    0.960004] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.960360]   alloc irq_desc for 30 on node -1
[    0.960363]   alloc kstat_irqs on node -1
[    0.960392] pcieport 0000:00:1c.5: irq 30 for MSI/MSI-X
[    0.960423] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.960683] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.961075] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.961490] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.961517] ACPI: Power Button [PWRB]
[    0.961742] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.961746] ACPI: Power Button [PWRF]
[    0.966419] Monitor-Mwait will be used to enter C-1 state
[    0.966549] Monitor-Mwait will be used to enter C-2 state
[    0.966644] Monitor-Mwait will be used to enter C-3 state
[    0.966836] processor LNXCPU:00: registered as cooling_device0
[    0.971015] processor LNXCPU:01: registered as cooling_device1
[    0.975458] processor LNXCPU:02: registered as cooling_device2
[    0.990367] processor LNXCPU:03: registered as cooling_device3
[    0.999881] isapnp: Scanning for PnP cards...
[    1.005364] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.005684] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.006935] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.011149] brd: module loaded
[    1.012952] loop: module loaded
[    1.013277] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.014984] Fixed MDIO Bus: probed
[    1.015118] PPP generic driver version 2.4.2
[    1.015304] tun: Universal TUN/TAP device driver, 1.6
[    1.015307] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.015655] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.015753]   alloc irq_desc for 18 on node -1
[    1.015757]   alloc kstat_irqs on node -1
[    1.015787] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.015824] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.015849] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.016011] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.016115] ehci_hcd 0000:00:1a.7: debug port 2
[    1.020049] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.020112] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbffe000
[    1.032551] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.032883] usb usb1: configuration #1 chosen from 1 choice
[    1.033033] hub 1-0:1.0: USB hub found
[    1.033068] hub 1-0:1.0: 6 ports detected
[    1.033269]   alloc irq_desc for 23 on node -1
[    1.033292]   alloc kstat_irqs on node -1
[    1.033323] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.033357] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.033362] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.033488] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.033584] ehci_hcd 0000:00:1d.7: debug port 2
[    1.037498] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.037535] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbffd000
[    1.052497] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.053010] usb usb2: configuration #1 chosen from 1 choice
[    1.053169] hub 2-0:1.0: USB hub found
[    1.053203] hub 2-0:1.0: 6 ports detected
[    1.053488] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.053558] uhci_hcd: USB Universal Host Controller Interface driver
[    1.053686] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.053719] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.053746] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.053940] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.054047] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000fe00
[    1.054526] usb usb3: configuration #1 chosen from 1 choice
[    1.054683] hub 3-0:1.0: USB hub found
[    1.054719] hub 3-0:1.0: 2 ports detected
[    1.054945]   alloc irq_desc for 21 on node -1
[    1.054971]   alloc kstat_irqs on node -1
[    1.055002] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.055034] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.055041] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.055263] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.055366] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fd00
[    1.055846] usb usb4: configuration #1 chosen from 1 choice
[    1.056003] hub 4-0:1.0: USB hub found
[    1.056040] hub 4-0:1.0: 2 ports detected
[    1.056266] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.056298] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.056325] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.056489] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.056580] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fc00
[    1.057065] usb usb5: configuration #1 chosen from 1 choice
[    1.057223] hub 5-0:1.0: USB hub found
[    1.057256] hub 5-0:1.0: 2 ports detected
[    1.057485] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.057517] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.057544] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.057712] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.057801] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fb00
[    1.058257] usb usb6: configuration #1 chosen from 1 choice
[    1.058418] hub 6-0:1.0: USB hub found
[    1.058451] hub 6-0:1.0: 2 ports detected
[    1.058679]   alloc irq_desc for 19 on node -1
[    1.058704]   alloc kstat_irqs on node -1
[    1.058714] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.058746] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.058773] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.058962] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.059066] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fa00
[    1.059549] usb usb7: configuration #1 chosen from 1 choice
[    1.059711] hub 7-0:1.0: USB hub found
[    1.059744] hub 7-0:1.0: 2 ports detected
[    1.059968] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.060000] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.060027] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.060191] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.060280] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f900
[    1.060765] usb usb8: configuration #1 chosen from 1 choice
[    1.060935] hub 8-0:1.0: USB hub found
[    1.060989] hub 8-0:1.0: 2 ports detected
[    1.061506] PNP: No PS/2 controller found. Probing ports directly.
[    1.095790] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.095817] If AUX port is really absent please use the 'i8042.noaux' option.
[    1.347936] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.348741] mice: PS/2 mouse device common for all mice
[    1.349454] rtc_cmos 00:04: RTC can wake from S4
[    1.349708] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.349808] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.350571] device-mapper: uevent: version 1.0.3
[    1.351220] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.351772] device-mapper: multipath: version 1.1.0 loaded
[    1.351800] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.352575] EISA: Probing bus 0 at eisa.0
[    1.352609] Cannot allocate resource for EISA slot 1
[    1.352706] EISA: Detected 0 cards.
[    1.354176] cpuidle: using governor ladder
[    1.355534] cpuidle: using governor menu
[    1.358199] TCP cubic registered
[    1.359138] NET: Registered protocol family 10
[    1.362041] lo: Disabled Privacy Extensions
[    1.364096] NET: Registered protocol family 17
[    1.367921] Using IPI No-Shortcut mode
[    1.368308] PM: Resume from disk failed.
[    1.368408] registered taskstats version 1
[    1.370242]   Magic number: 11:188:296
[    1.370467] tty tty29: hash matches
[    1.370759] rtc_cmos 00:04: setting system clock to 2011-05-18 20:17:07 UTC (1305749827)
[    1.370787] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.370792] EDD information not available.
[    1.385396] isapnp: No Plug & Play device found
[    1.626287] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    1.779013] usb 2-3: configuration #1 chosen from 1 choice
[    2.021438] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.193421] usb 3-1: configuration #1 chosen from 1 choice
[    2.194094] Freeing initrd memory: 12994k freed
[    2.204427] Freeing unused kernel memory: 680k freed
[    2.205573] Write protecting the kernel text: 4844k
[    2.205926] Write protecting the kernel read-only data: 1884k
[    2.281588] udev: starting version 151
[    2.444314] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    2.588759] Linux agpgart interface v0.103
[    2.615380] Initializing USB Mass Storage driver...
[    2.616283] scsi0 : SCSI emulation for USB Mass Storage devices
[    2.617050] usbcore: registered new interface driver usb-storage
[    2.617058] USB Mass Storage support registered.
[    2.622200] usb-storage: device found at 2
[    2.622204] usb-storage: waiting for device to settle before scanning
[    2.637488] usb 3-2: configuration #1 chosen from 1 choice
[    2.647822] ahci 0000:00:1f.2: version 3.0
[    2.647923] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.648121]   alloc irq_desc for 31 on node -1
[    2.648146]   alloc kstat_irqs on node -1
[    2.648186] ahci 0000:00:1f.2: irq 31 for MSI/MSI-X
[    2.648371] ahci: SSS flag set, parallel bus scan disabled
[    2.665951] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.666039] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.666166] r8169 0000:02:00.0: setting latency timer to 64
[    2.666299]   alloc irq_desc for 32 on node -1
[    2.666303]   alloc kstat_irqs on node -1
[    2.666362] r8169 0000:02:00.0: irq 32 for MSI/MSI-X
[    2.667588] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    2.667618] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems apst 
[    2.667626] ahci 0000:00:1f.2: setting latency timer to 64
[    2.670513] eth0: RTL8168d/8111d at 0xf8314000, 6c:f0:49:0b:5b:4d, XID 083000c0 IRQ 32
[    2.711722] scsi1 : ahci
[    2.712164] scsi2 : ahci
[    2.712487] scsi3 : ahci
[    2.712803] scsi4 : ahci
[    2.713098] scsi5 : ahci
[    2.713392] scsi6 : ahci
[    2.714295] ata1: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc100 irq 31
[    2.714322] ata2: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc180 irq 31
[    2.714348] ata3: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc200 irq 31
[    2.714354] ata4: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc280 irq 31
[    2.714381] ata5: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc300 irq 31
[    2.714386] ata6: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc380 irq 31
[    2.808433] [drm] Initialized drm 1.1.0 20060810
[    2.818831] agpgart-intel 0000:00:00.0: Intel IGDNG/D Chipset
[    2.820654] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[    2.847207] usbcore: registered new interface driver hiddev
[    2.865924] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input3
[    2.866525] generic-usb 0003:046D:C50E.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1a.0-2/input0
[    2.866689] usbcore: registered new interface driver usbhid
[    2.866695] usbhid: v2.6:USB HID core driver
[    2.907119] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    2.968189] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    3.091321] usb 5-1: configuration #1 chosen from 1 choice
[    3.098666] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input4
[    3.098988] generic-usb 0003:046D:C52B.0002: input,hidraw1: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.2-1/input0
[    3.103296] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.1/input/input5
[    3.103976] generic-usb 0003:046D:C52B.0003: input,hiddev96,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-1/input1
[    3.111162] generic-usb 0003:046D:C52B.0004: hiddev97,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.2-1/input2
[    3.194054] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.196282] ata1.00: ATA-8: OCZ CORE_SSD, 02.10103, max UDMA/100
[    3.196288] ata1.00: 118128640 sectors, multi 0: LBA 
[    3.197816] ata1.00: configured for UDMA/100
[    3.214458] scsi 1:0:0:0: Direct-Access     ATA      OCZ CORE_SSD     02.1 PQ: 0 ANSI: 5
[    3.215268] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    3.215449] sd 1:0:0:0: [sda] 118128640 512-byte logical blocks: (60.4 GB/56.3 GiB)
[    3.215644] sd 1:0:0:0: [sda] Write Protect is off
[    3.215650] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.215775] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.216349]  sda:
[    4.099245] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.099841] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223L, SB02, max UDMA/100
[    4.100893] ata2.00: configured for UDMA/100
[    4.116273] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223L  SB02 PQ: 0 ANSI: 5
[    4.121698] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.121726] Uniform CD-ROM driver Revision: 3.20
[    4.122117] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.122339] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    4.331193]  sda1 sda2 sda3
[    4.332868] sd 1:0:0:0: [sda] Attached SCSI disk
[    5.004703] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.006830] ata3.00: ATA-8: WDC WD5000AAKS-00UU3A0, 01.03B01, max UDMA/133
[    5.006836] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.008491] ata3.00: configured for UDMA/133
[    5.021120] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 01.0 PQ: 0 ANSI: 5
[    5.021708] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    5.021803] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    5.021895] sd 3:0:0:0: [sdb] Write Protect is off
[    5.021899] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.021992] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.022503]  sdb: sdb1 sdb2
[    5.046803] sd 3:0:0:0: [sdb] Attached SCSI disk
[    5.343751] ata4: SATA link down (SStatus 0 SControl 300)
[    5.679237] ata5: SATA link down (SStatus 0 SControl 300)
[    6.014376] ata6: SATA link down (SStatus 0 SControl 300)
[    6.151282] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.151315] pci 0000:00:02.0: setting latency timer to 64
[    6.171913] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[    6.171940] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    6.172338]   alloc irq_desc for 33 on node -1
[    6.172364]   alloc kstat_irqs on node -1
[    6.172401] pci 0000:00:02.0: irq 33 for MSI/MSI-X
[    6.172498] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    6.326572] uvesafb: Intel Corporation, Intel(R)Ironlake Desktop Graphics Controller, Hardware Version 0.0, OEM: Intel(R)Ironlake Desktop Graphics Chipset Accelerated VGA BIOS, VBE v3.0
[    6.334753] uvesafb: VBIOS/hardware supports DDC2 transfers
[    6.347465] uvesafb: monitor limits: vf = 85 Hz, hf = 82 kHz, clk = 140 MHz
[    6.347764] uvesafb: scrolling: redraw
[    6.349922] mtrr: type mismatch for e0000000,1000000 old: write-back new: write-combining
[    6.349928] mtrr: type mismatch for e0000000,800000 old: write-back new: write-combining
[    6.349953] mtrr: type mismatch for e0000000,400000 old: write-back new: write-combining
[    6.349958] mtrr: type mismatch for e0000000,200000 old: write-back new: write-combining
[    6.349983] mtrr: type mismatch for e0000000,100000 old: write-back new: write-combining
[    6.349988] mtrr: type mismatch for e0000000,80000 old: write-back new: write-combining
[    6.350013] mtrr: type mismatch for e0000000,40000 old: write-back new: write-combining
[    6.350018] mtrr: type mismatch for e0000000,20000 old: write-back new: write-combining
[    6.350023] mtrr: type mismatch for e0000000,10000 old: write-back new: write-combining
[    6.350048] mtrr: type mismatch for e0000000,8000 old: write-back new: write-combining
[    6.350053] mtrr: type mismatch for e0000000,4000 old: write-back new: write-combining
[    6.350078] mtrr: type mismatch for e0000000,2000 old: write-back new: write-combining
[    6.350083] mtrr: type mismatch for e0000000,1000 old: write-back new: write-combining
[    6.350335] uvesafb: framebuffer at 0xe0000000, mapped to 0xf8e00000, using 21600k, total 65472k
[    6.350341] fb0: VESA VGA frame buffer device
[    7.253697] Console: switching to colour frame buffer device 160x64
[    7.606151] usb-storage: device scan complete
[    7.610568] scsi 0:0:0:0: Direct-Access     USB2.0   CF  CardReader        PQ: 0 ANSI: 0
[    7.614618] scsi 0:0:0:1: Direct-Access     USB2.0   CBO CardReader        PQ: 0 ANSI: 0
[    7.617742] sd 0:0:0:0: Attached scsi generic sg3 type 0
[    7.619896] sd 0:0:0:1: Attached scsi generic sg4 type 0
[    7.623016] sd 0:0:0:0: [sdc] Attached SCSI removable disk
[    7.624307] sd 0:0:0:1: [sdd] Attached SCSI removable disk
[    8.091043] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    8.091052] EXT4-fs (sda1): write access will be enabled during recovery
[    8.376374] EXT4-fs (sda1): recovery complete
[    8.380362] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   18.141251] Adding 4033528k swap on /dev/sda3.  Priority:-1 extents:1 across:4033528k 
[   18.229833] udev: starting version 151
[   18.370356] lp: driver loaded but no devices found
[   18.463564] vga16fb: initializing
[   18.463572] vga16fb: mapped to 0xc00a0000
[   18.463604] vga16fb: not registering due to another framebuffer present
[   19.069609] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1093
[   19.069764] usbcore: registered new interface driver usblp
[   19.147368] type=1505 audit(1305764245.324:2):  operation="profile_load" pid=745 name="/sbin/dhclient3"
[   19.186447] type=1505 audit(1305764245.364:3):  operation="profile_load" pid=745 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.188160] type=1505 audit(1305764245.364:4):  operation="profile_load" pid=745 name="/usr/lib/connman/scripts/dhclient-script"
[   19.232179] type=1505 audit(1305764245.408:5):  operation="profile_load" pid=784 name="/usr/sbin/ntpd"
[   19.590802] r8169: eth0: link down
[   19.590864] r8169: eth0: link down
[   19.601337] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.908874]   alloc irq_desc for 22 on node -1
[   19.908903]   alloc kstat_irqs on node -1
[   19.908962] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.909219] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.090375] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   22.566448] r8169: eth0: link up
[   22.567513] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.660882] r8169: eth0: link down
[   26.239444] r8169: eth0: link up
[   27.884328] EXT4-fs (sda2): mounted filesystem with ordered data mode
[   28.852328] EXT4-fs (sdb2): mounted filesystem with ordered data mode
[   29.435590] RPC: Registered udp transport module.
[   29.435617] RPC: Registered tcp transport module.
[   29.435621] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   29.439413] type=1505 audit(1305764255.644:6):  operation="profile_load" pid=1272 name="/usr/share/gdm/guest-session/Xsession"
[   29.455797] type=1505 audit(1305764255.664:7):  operation="profile_replace" pid=1274 name="/sbin/dhclient3"
[   29.472213] type=1505 audit(1305764255.680:8):  operation="profile_load" pid=1282 name="/usr/lib/libvirt/virt-aa-helper"
[   29.478938] type=1505 audit(1305764255.684:9):  operation="profile_load" pid=1281 name="/usr/bin/freshclam"
[   29.482060] type=1505 audit(1305764255.688:10):  operation="profile_replace" pid=1274 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   29.483829] type=1505 audit(1305764255.692:11):  operation="profile_replace" pid=1274 name="/usr/lib/connman/scripts/dhclient-script"
[   29.510774] type=1505 audit(1305764255.716:12):  operation="profile_load" pid=1283 name="/usr/lib/cups/backend/cups-pdf"
[   29.515508] type=1505 audit(1305764255.724:13):  operation="profile_load" pid=1285 name="/usr/sbin/mysqld-akonadi"
[   29.519234] type=1505 audit(1305764255.724:14):  operation="profile_load" pid=1283 name="/usr/sbin/cupsd"
[   29.524844] type=1505 audit(1305764255.732:15):  operation="profile_load" pid=1275 name="/usr/bin/evince"
[   29.659587] svc: failed to register lockdv1 RPC service (errno 97).
[   30.098305] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   30.129316] Bridge firewalling registered
[   30.200391] virbr0: starting userspace STP failed, starting kernel STP
[   30.254656] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.403420] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   30.404646] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   30.404672] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   30.404678] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   30.417142] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   30.418144] NFSD: starting 90-second grace period
[   31.456893] lo: Disabled Privacy Extensions
[   31.672868] vboxdrv: Found 4 processor cores.
[   31.675125] vboxdrv: fAsync=0 offMin=0x71eb offMax=0xcf01
[   31.676891] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   31.676896] vboxdrv: Successfully loaded version 3.2.12 (interface 0x00140001).
[   32.778885] eth0: no IPv6 routers present
[   32.781236] ppdev: user-space parallel port driver
[   33.490145] CPU0 attaching NULL sched-domain.
[   33.490179] CPU1 attaching NULL sched-domain.
[   33.490185] CPU2 attaching NULL sched-domain.
[   33.490211] CPU3 attaching NULL sched-domain.
[   33.516892] CPU0 attaching sched-domain:
[   33.516899]  domain 0: span 0,2 level SIBLING
[   33.516927]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[   33.516961]   domain 1: span 0-3 level MC
[   33.516988]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   33.517023] CPU1 attaching sched-domain:
[   33.517028]  domain 0: span 1,3 level SIBLING
[   33.517054]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[   33.517087]   domain 1: span 0-3 level MC
[   33.517092]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   33.517126] CPU2 attaching sched-domain:
[   33.517151]  domain 0: span 0,2 level SIBLING
[   33.517157]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   33.517189]   domain 1: span 0-3 level MC
[   33.517215]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   33.517249] CPU3 attaching sched-domain:
[   33.517253]  domain 0: span 1,3 level SIBLING
[   33.517279]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   33.517311]   domain 1: span 0-3 level MC
[   33.517316]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   33.524842] CPU0 attaching NULL sched-domain.
[   33.524850] CPU1 attaching NULL sched-domain.
[   33.524876] CPU2 attaching NULL sched-domain.
[   33.524881] CPU3 attaching NULL sched-domain.
[   33.580499] CPU0 attaching sched-domain:
[   33.580527]  domain 0: span 0,2 level SIBLING
[   33.580533]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[   33.580566]   domain 1: span 0-3 level MC
[   33.580591]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   33.580626] CPU1 attaching sched-domain:
[   33.580651]  domain 0: span 1,3 level SIBLING
[   33.580657]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[   33.580689]   domain 1: span 0-3 level MC
[   33.580694]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   33.580749] CPU2 attaching sched-domain:
[   33.580753]  domain 0: span 0,2 level SIBLING
[   33.580759]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   33.580791]   domain 1: span 0-3 level MC
[   33.580818]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   33.580852] CPU3 attaching sched-domain:
[   33.580877]  domain 0: span 1,3 level SIBLING
[   33.580882]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   33.580914]   domain 1: span 0-3 level MC
[   33.580920]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   34.183217] usb 3-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   34.433211] ata1.00: configured for UDMA/100
[   34.433245] ata1: EH complete
[   34.434726] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.615990] virbr0: no IPv6 routers present
[  215.198739] CPU0 attaching NULL sched-domain.
[  215.198796] CPU1 attaching NULL sched-domain.
[  215.198801] CPU2 attaching NULL sched-domain.
[  215.198826] CPU3 attaching NULL sched-domain.
[  215.239407] CPU0 attaching sched-domain:
[  215.239441]  domain 0: span 0,2 level SIBLING
[  215.239467]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[  215.239476]   domain 1: span 0-3 level MC
[  215.239501]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[  215.239536] CPU1 attaching sched-domain:
[  215.239539]  domain 0: span 1,3 level SIBLING
[  215.239563]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[  215.239571]   domain 1: span 0-3 level MC
[  215.239595]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[  215.239605] CPU2 attaching sched-domain:
[  215.239628]  domain 0: span 0,2 level SIBLING
[  215.239632]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[  215.239660]   domain 1: span 0-3 level MC
[  215.239664]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[  215.239694] CPU3 attaching sched-domain:
[  215.239697]  domain 0: span 1,3 level SIBLING
[  215.239700]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[  215.239729]   domain 1: span 0-3 level MC
[  215.239732]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[  215.250741] CPU0 attaching NULL sched-domain.
[  215.250800] CPU1 attaching NULL sched-domain.
[  215.250805] CPU2 attaching NULL sched-domain.
[  215.250830] CPU3 attaching NULL sched-domain.
[  215.279416] CPU0 attaching sched-domain:
[  215.279450]  domain 0: span 0,2 level SIBLING
[  215.279477]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[  215.279509]   domain 1: span 0-3 level MC
[  215.279514]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[  215.279573] CPU1 attaching sched-domain:
[  215.279578]  domain 0: span 1,3 level SIBLING
[  215.279603]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[  215.279633]   domain 1: span 0-3 level MC
[  215.279638]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[  215.279670] CPU2 attaching sched-domain:
[  215.279675]  domain 0: span 0,2 level SIBLING
[  215.279699]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[  215.279709]   domain 1: span 0-3 level MC
[  215.279734]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[  215.279766] CPU3 attaching sched-domain:
[  215.279769]  domain 0: span 1,3 level SIBLING
[  215.279773]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[  215.279804]   domain 1: span 0-3 level MC
[  215.279829]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[  263.251237] lo: Disabled Privacy Extensions
```

---

### Post by varunendra on 2011-05-19
If you are able to boot into 'Recovery' mode with failsafeX graphics option, try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

