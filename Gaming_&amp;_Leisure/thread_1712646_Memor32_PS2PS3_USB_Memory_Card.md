---
title: "Memor32 PS2/PS3 USB Memory Card"
date: 2011-03-23
forum: Gaming &amp; Leisure
---

### Post by dogeatery on 2011-03-23
Not sure where else to file this, so I put it in gaming and leisure.

I bought a [Memor32 card]("http://www.memor32.com/") , which is supposed to connect to my computer and allow me to transfer game data between a PC and game console.  When I plug it into my computer, nothing happened, so I installed drivers as directed in the README file.  Still, it doesn't work.  Is anyone familiar with this card?  Is there a way to get it going?  I also put out messages on their message board but so far have no received a reply.

---

### Post by dogeatery on 2011-03-23
Here is the printout of ```
lsusb
```
The Memor32 is listed as Future Technology Devices.

```
babo-bap@babo-bap ~ $ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 003: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 002: ID 10f1:1a08  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by sakuramboo on 2011-03-23
What is the output given from dmesg when you plug it in?

---

### Post by dogeatery on 2011-03-23
Thanks for taking on my issue, sakuramboo.  Get ready for a lot of information to sift through:

```
babo-bap@babo-bap ~ $ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-30-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 (Ubuntu 2.6.32-30.59-generic 2.6.32.29+drm33.13)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7b0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7b0000 - 000000003f7be000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7be000 - 000000003f7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x3f7b0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f7b0000 (usable)
[    0.000000]  modified: 000000003f7b0000 - 000000003f7be000 (ACPI data)
[    0.000000]  modified: 000000003f7be000 - 000000003f7f0000 (ACPI NVS)
[    0.000000]  modified: 000000003f7f0000 - 000000003f800000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 8e6000-9c7000
[    0.000000] RAMDISK: 2ed3a000 - 2fa03b60
[    0.000000] ACPI: RSDP 000f9c30 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3f7b0000 0003C (v01 110708 RSDT1432 20081107 MSFT 00000097)
[    0.000000] ACPI: FACP 3f7b0200 00084 (v02 110708 FACP1432 20081107 MSFT 00000097)
[    0.000000] ACPI: DSDT 3f7b0430 07ECA (v01  361A0 361A0F05 00000F05 INTL 20051117)
[    0.000000] ACPI: FACS 3f7be000 00040
[    0.000000] ACPI: APIC 3f7b0390 0005C (v01 110708 APIC1432 20081107 MSFT 00000097)
[    0.000000] ACPI: MCFG 3f7b03f0 0003C (v01 110708 OEMMCFG  20081107 MSFT 00000097)
[    0.000000] ACPI: OEMB 3f7be040 00224 (v01 110708 OEMB1432 20081107 MSFT 00000097)
[    0.000000] ACPI: ASF! 3f7b8300 00075 (v32 LEGEND I865PASF 00000001 INTL 20051117)
[    0.000000] ACPI: SSDT 3f7bebe0 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00007000 - 0000df00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e1ed8]    TEXT DATA BSS ==> [0000100000 - 00008e1ed8]
[    0.000000]   #4 [002ed3a000 - 002fa03b60]          RAMDISK ==> [002ed3a000 - 002fa03b60]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008e2000 - 00008e5170]              BRK ==> [00008e2000 - 00008e5170]
[    0.000000]   #7 [00008e6000 - 00009c1000]          PGTABLE ==> [00008e6000 - 00009c1000]
[    0.000000]   #8 [0000007000 - 000000e000]          BOOTMAP ==> [0000007000 - 000000e000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f7b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f7b0
[    0.000000] On node 0 totalpages: 259915
[    0.000000] free_area_init_node: node 0, pgdat c079c940, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 256 pages used for memmap
[    0.000000]   HighMem zone: 32434 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c17f7000 s36056 r0 d21288 u65536
[    0.000000] pcpu-alloc: s36056 r0 d21288 u65536 alloc=16*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257883
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=53387546-0b9c-4d3e-94f3-db2b8833f1e7 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5200320 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f7b0)
[    0.000000] Memory: 1002888k/1040064k available (4689k kernel code, 36220k reserved, 2122k data, 664k init, 130760k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a7000 - 0xc084d000   ( 664 kB)
[    0.000000]       .data : 0xc0594467 - 0xc07a6f08   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0594467   (4689 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.256 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.51 BogoMIPS (lpj=6385024)
[    0.004046] Security Framework initialized
[    0.004092] AppArmor: AppArmor initialized
[    0.004108] Mount-cache hash table entries: 512
[    0.004353] Initializing cgroup subsys ns
[    0.004364] Initializing cgroup subsys cpuacct
[    0.004374] Initializing cgroup subsys memory
[    0.004387] Initializing cgroup subsys devices
[    0.004393] Initializing cgroup subsys freezer
[    0.004400] Initializing cgroup subsys net_cls
[    0.004437] Atom PSE erratum detected, BIOS microcode update recommended
[    0.004446] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004453] CPU: L2 cache: 512K
[    0.004459] CPU: Physical Processor ID: 0
[    0.004463] CPU: Processor Core ID: 0
[    0.004470] mce: CPU supports 5 MCE banks
[    0.004490] CPU0: Thermal monitoring enabled (TM2)
[    0.004499] using mwait in idle threads.
[    0.004511] Performance Events: Atom events, Intel PMU driver.
[    0.004529] ... version:                3
[    0.004533] ... bit width:              40
[    0.004538] ... generic registers:      2
[    0.004543] ... value mask:             000000ffffffffff
[    0.004548] ... max period:             000000007fffffff
[    0.004553] ... fixed-purpose events:   3
[    0.004558] ... event mask:             0000000700000003
[    0.004568] Checking 'hlt' instruction... OK.
[    0.020009] Disabling 4MB page tables to avoid TLB bug
[    0.024402] ACPI: Core revision 20090903
[    0.044027] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044039] ftrace: allocating 21799 entries in 43 pages
[    0.048118] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048491] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.089053] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.092001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.176099] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.176116] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.180041] Brought up 2 CPUs
[    0.180049] Total of 2 processors activated (6384.64 BogoMIPS).
[    0.180332] CPU0 attaching sched-domain:
[    0.180342]  domain 0: span 0-1 level SIBLING
[    0.180347]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.180360]   domain 1: span 0-1 level MC
[    0.180365]    groups: 0-1 (cpu_power = 1178)
[    0.180377] CPU1 attaching sched-domain:
[    0.180381]  domain 0: span 0-1 level SIBLING
[    0.180387]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.180398]   domain 1: span 0-1 level MC
[    0.180403]    groups: 0-1 (cpu_power = 1178)
[    0.180581] devtmpfs: initialized
[    0.180581] regulator: core version 0.5
[    0.180581] Time: 23:56:09  Date: 03/23/11
[    0.180581] NET: Registered protocol family 16
[    0.180581] Trying to unpack rootfs image as initramfs...
[    0.180581] EISA bus registered
[    0.180607] ACPI: bus type pci registered
[    0.180787] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.180797] PCI: Not using MMCONFIG.
[    0.181110] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.181118] PCI: Using configuration type 1 for base access
[    0.186645] bio: create slab <bio-0> at 0
[    0.189005] ACPI: EC: Look up EC in DSDT
[    0.191802] ACPI: BIOS _OSI(Linux) query ignored
[    0.193991] ACPI: Executed 1 blocks of module-level executable AML code
[    0.810676] Freeing initrd memory: 13094k freed
[    0.912585] ACPI: Interpreter enabled
[    0.912597] ACPI: (supports S0 S3 S4 S5)
[    0.912649] ACPI: Using IOAPIC for interrupt routing
[    0.912748] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.928341] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.928341] PCI: updated MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.928341] PCI: Using MMCONFIG for extended config space
[    0.941950] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.942384] ACPI: No dock devices found.
[    0.942703] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.942861] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe980000-0xfe9fffff]
[    0.942871] pci 0000:00:02.0: reg 14 io port: [0xdc80-0xdc87]
[    0.942881] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.942890] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfe940000-0xfe97ffff]
[    0.942944] pci 0000:00:02.1: reg 10 32bit mmio: [0xfe880000-0xfe8fffff]
[    0.943071] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe938000-0xfe93bfff]
[    0.943138] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.943146] pci 0000:00:1b.0: PME# disabled
[    0.943245] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.943253] pci 0000:00:1c.0: PME# disabled
[    0.943354] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.943362] pci 0000:00:1c.1: PME# disabled
[    0.943438] pci 0000:00:1d.0: reg 20 io port: [0xdc00-0xdc1f]
[    0.943513] pci 0000:00:1d.1: reg 20 io port: [0xd880-0xd89f]
[    0.943587] pci 0000:00:1d.2: reg 20 io port: [0xd800-0xd81f]
[    0.943662] pci 0000:00:1d.3: reg 20 io port: [0xd480-0xd49f]
[    0.943742] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe937c00-0xfe937fff]
[    0.943816] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.943824] pci 0000:00:1d.7: PME# disabled
[    0.944031] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.944045] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.944053] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.944061] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0500 (mask 0003)
[    0.944069] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    0.944143] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.944159] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.944171] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.944183] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.944195] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.944283] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.944526] pci 0000:01:00.0: reg 10 64bit mmio: [0xfeafc000-0xfeafffff]
[    0.944743] pci 0000:01:00.0: supports D1 D2
[    0.944882] pci 0000:00:1c.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.945313] pci 0000:02:00.0: reg 10 64bit mmio: [0xfebfc000-0xfebfffff]
[    0.945366] pci 0000:02:00.0: reg 18 io port: [0xec00-0xecff]
[    0.945850] pci 0000:02:00.0: supports D1 D2
[    0.945855] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.945883] pci 0000:02:00.0: PME# disabled
[    0.946085] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
[    0.946094] pci 0000:00:1c.1: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.946171] pci 0000:00:1e.0: transparent bridge
[    0.946206] pci_bus 0000:00: on NUMA node 0
[    0.946219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.946491] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.946875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.966072] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.966294] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.966512] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.966729] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.966947] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.967165] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.967384] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.967603] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.967855] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.967876] vgaarb: loaded
[    0.968169] SCSI subsystem initialized
[    0.968203] libata version 3.00 loaded.
[    0.968203] usbcore: registered new interface driver usbfs
[    0.968203] usbcore: registered new interface driver hub
[    0.968203] usbcore: registered new device driver usb
[    0.968203] ACPI: WMI: Mapper loaded
[    0.968210] PCI: Using ACPI for IRQ routing
[    0.968663] NetLabel: Initializing
[    0.968668] NetLabel:  domain hash size = 128
[    0.968672] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.968698] NetLabel:  unlabeled traffic allowed by default
[    0.968942] hpet clockevent registered
[    0.968950] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.968961] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.968972] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.972038] Switching to clocksource tsc
[    0.975676] AppArmor: AppArmor Filesystem Enabled
[    0.975723] pnp: PnP ACPI init
[    0.975760] ACPI: bus type pnp registered
[    0.980749] pnp: PnP ACPI: found 12 devices
[    0.980756] ACPI: ACPI bus type pnp unregistered
[    0.980764] PnPBIOS: Disabled by ACPI PNP
[    0.980794] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.980833] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.980840] system 00:08: ioport range 0x500-0x501 has been reserved
[    0.980847] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.980854] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.980862] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.980870] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.980877] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
[    0.980892] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.980899] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.980913] system 00:0a: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.980927] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.980935] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.980942] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.980949] system 00:0b: iomem range 0x100000-0x3f7fffff could not be reserved
[    0.980957] system 00:0b: iomem range 0xfed90000-0xffffffff could not be reserved
[    1.015953] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    1.015961] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    1.015971] pci 0000:00:1c.0:   MEM window: 0xfea00000-0xfeafffff
[    1.015980] pci 0000:00:1c.0:   PREFETCH window: 0x00000040000000-0x000000401fffff
[    1.015992] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    1.015999] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    1.016008] pci 0000:00:1c.1:   MEM window: 0xfeb00000-0xfebfffff
[    1.016017] pci 0000:00:1c.1:   PREFETCH window: 0x00000040200000-0x000000403fffff
[    1.016028] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    1.016033] pci 0000:00:1e.0:   IO window: disabled
[    1.016041] pci 0000:00:1e.0:   MEM window: disabled
[    1.016048] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.016070] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    1.016084]   alloc irq_desc for 16 on node -1
[    1.016088]   alloc kstat_irqs on node -1
[    1.016101] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.016111] pci 0000:00:1c.0: setting latency timer to 64
[    1.016127]   alloc irq_desc for 17 on node -1
[    1.016131]   alloc kstat_irqs on node -1
[    1.016140] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.016148] pci 0000:00:1c.1: setting latency timer to 64
[    1.016161] pci 0000:00:1e.0: setting latency timer to 64
[    1.016170] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.016176] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    1.016183] pci_bus 0000:01: resource 0 io:  [0x1000-0x1fff]
[    1.016189] pci_bus 0000:01: resource 1 mem: [0xfea00000-0xfeafffff]
[    1.016195] pci_bus 0000:01: resource 2 pref mem [0x40000000-0x401fffff]
[    1.016202] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    1.016207] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    1.016214] pci_bus 0000:02: resource 2 pref mem [0x40200000-0x403fffff]
[    1.016220] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    1.016226] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    1.016302] NET: Registered protocol family 2
[    1.016512] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.017187] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.018163] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.018600] TCP: Hash tables configured (established 131072 bind 65536)
[    1.018607] TCP reno registered
[    1.018848] NET: Registered protocol family 1
[    1.018899] pci 0000:00:02.0: Boot video device
[    1.019472] cpufreq-nforce2: No nForce2 chipset.
[    1.019535] Scanning for low memory corruption every 60 seconds
[    1.019845] audit: initializing netlink socket (disabled)
[    1.019869] type=2000 audit(1300924570.019:1): initialized
[    1.037129] highmem bounce pool size: 64 pages
[    1.037141] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.040819] VFS: Disk quotas dquot_6.5.2
[    1.040956] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.042426] fuse init (API version 7.13)
[    1.042641] msgmni has been set to 1730
[    1.043140] alg: No test for stdrng (krng)
[    1.043290] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.043297] io scheduler noop registered
[    1.043302] io scheduler anticipatory registered
[    1.043306] io scheduler deadline registered
[    1.043412] io scheduler cfq registered (default)
[    1.043676]   alloc irq_desc for 24 on node -1
[    1.043682]   alloc kstat_irqs on node -1
[    1.043700] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    1.043716] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.043943]   alloc irq_desc for 25 on node -1
[    1.043948]   alloc kstat_irqs on node -1
[    1.043962] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    1.043976] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.044155] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.044340] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.045842] ACPI: AC Adapter [AC0] (on-line)
[    1.046054] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0D:00/input/input0
[    1.046526] ACPI: Lid Switch [LID]
[    1.046636] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.046643] ACPI: Sleep Button [SLPB]
[    1.046746] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    1.046753] ACPI: Power Button [PWRB]
[    1.046859] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.046866] ACPI: Power Button [PWRF]
[    1.048218] ACPI: SSDT 3f7be340 0023C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.049095] ACPI: SSDT 3f7be610 005D0 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.049785] Monitor-Mwait will be used to enter C-1 state
[    1.049856] Monitor-Mwait will be used to enter C-2 state
[    1.049920] Monitor-Mwait will be used to enter C-3 state
[    1.049937] Marking TSC unstable due to TSC halts in idle
[    1.050044] Switching to clocksource hpet
[    1.050110] processor LNXCPU:00: registered as cooling_device0
[    1.050961] ACPI: SSDT 3f7be270 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    1.051555] ACPI: SSDT 3f7be580 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    1.052572] processor LNXCPU:01: registered as cooling_device1
[    1.059011] thermal LNXTHERM:01: registered as thermal_zone0
[    1.059030] ACPI: Thermal Zone [THRM] (28 C)
[    1.059346] isapnp: Scanning for PnP cards...
[    1.063843] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.065074] ACPI: Battery Slot [BAT1] (battery absent)
[    1.067715] brd: module loaded
[    1.069260] loop: module loaded
[    1.069522] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.069775] ata_piix 0000:00:1f.1: version 2.13
[    1.069806]   alloc irq_desc for 18 on node -1
[    1.069813]   alloc kstat_irqs on node -1
[    1.069829] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.069910] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.070114] scsi0 : ata_piix
[    1.070360] scsi1 : ata_piix
[    1.074211] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.074221] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.075293] Fixed MDIO Bus: probed
[    1.075403] PPP generic driver version 2.4.2
[    1.075531] tun: Universal TUN/TAP device driver, 1.6
[    1.075537] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.075800] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.075850]   alloc irq_desc for 23 on node -1
[    1.075856]   alloc kstat_irqs on node -1
[    1.075871] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.075906] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.075915] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.076060] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.076114] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.076135] ehci_hcd 0000:00:1d.7: debug port 1
[    1.080036] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.080080] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe937c00
[    1.084284] ata2: port disabled. ignoring.
[    1.096030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.096303] usb usb1: configuration #1 chosen from 1 choice
[    1.096393] hub 1-0:1.0: USB hub found
[    1.096416] hub 1-0:1.0: 8 ports detected
[    1.096580] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.096627] uhci_hcd: USB Universal Host Controller Interface driver
[    1.096707] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.096727] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.096735] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.096845] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.096891] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000dc00
[    1.097151] usb usb2: configuration #1 chosen from 1 choice
[    1.097233] hub 2-0:1.0: USB hub found
[    1.097253] hub 2-0:1.0: 2 ports detected
[    1.097375]   alloc irq_desc for 19 on node -1
[    1.097382]   alloc kstat_irqs on node -1
[    1.097397] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.097411] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.097419] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.097528] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.097584] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d880
[    1.097854] usb usb3: configuration #1 chosen from 1 choice
[    1.097933] hub 3-0:1.0: USB hub found
[    1.097953] hub 3-0:1.0: 2 ports detected
[    1.098068] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.098083] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.098091] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.098181] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.098235] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    1.098479] usb usb4: configuration #1 chosen from 1 choice
[    1.098558] hub 4-0:1.0: USB hub found
[    1.098576] hub 4-0:1.0: 2 ports detected
[    1.098690] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.098704] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.098712] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.098808] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.098862] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d480
[    1.099116] usb usb5: configuration #1 chosen from 1 choice
[    1.099197] hub 5-0:1.0: USB hub found
[    1.099216] hub 5-0:1.0: 2 ports detected
[    1.099472] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.104691] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.107342] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.107364] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.107373] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.107382] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.107391] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.107625] mice: PS/2 mouse device common for all mice
[    1.108066] rtc_cmos 00:03: RTC can wake from S4
[    1.108172] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.108217] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.108569] device-mapper: uevent: version 1.0.3
[    1.108888] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.109124] device-mapper: multipath: version 1.1.0 loaded
[    1.109133] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.109503] EISA: Probing bus 0 at eisa.0
[    1.109516] Cannot allocate resource for EISA slot 1
[    1.109554] EISA: Detected 0 cards.
[    1.110001] cpuidle: using governor ladder
[    1.110344] cpuidle: using governor menu
[    1.111526] TCP cubic registered
[    1.112107] NET: Registered protocol family 10
[    1.113400] lo: Disabled Privacy Extensions
[    1.114328] NET: Registered protocol family 17
[    1.115436] Using IPI No-Shortcut mode
[    1.115685] PM: Resume from disk failed.
[    1.115716] registered taskstats version 1
[    1.116615]   Magic number: 3:43:960
[    1.116753] rtc_cmos 00:03: setting system clock to 2011-03-23 23:56:10 UTC (1300924570)
[    1.116763] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.116769] EDD information not available.
[    1.146114] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.236604] ata1.00: CFA: SanDisk pSSD 8GB, SSD 4.47, max UDMA/66
[    1.236614] ata1.00: 16007040 sectors, multi 0: LBA 
[    1.237257] ata1.00: configured for UDMA/66
[    1.408045] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.413566] isapnp: No Plug & Play device found
[    1.413850] scsi 0:0:0:0: Direct-Access     ATA      SanDisk pSSD 8GB SSD  PQ: 0 ANSI: 5
[    1.414207] sd 0:0:0:0: [sda] 16007040 512-byte logical blocks: (8.19 GB/7.63 GiB)
[    1.414267] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.414397] sd 0:0:0:0: [sda] Write Protect is off
[    1.414406] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.414502] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.414883]  sda: sda1 sda2 < sda5 sda6 >
[    1.417564] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.417653] Freeing unused kernel memory: 664k freed
[    1.418217] Write protecting the kernel text: 4692k
[    1.418297] Write protecting the kernel read-only data: 1844k
[    1.461410] udev: starting version 151
[    1.557648] usb 1-2: configuration #1 chosen from 1 choice
[    1.668134] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.789091] Initializing USB Mass Storage driver...
[    1.793382] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.793699] usbcore: registered new interface driver usb-storage
[    1.793711] USB Mass Storage support registered.
[    1.793732] usb-storage: device found at 2
[    1.793738] usb-storage: waiting for device to settle before scanning
[    1.816416] Linux agpgart interface v0.103
[    1.818950] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    1.819090] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[    1.821818] sky2 driver version 1.25
[    1.822005] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.822065] sky2 0000:02:00.0: setting latency timer to 64
[    1.822173] sky2 0000:02:00.0: Yukon-2 FE+ chip revision 0
[    1.822743]   alloc irq_desc for 26 on node -1
[    1.822750]   alloc kstat_irqs on node -1
[    1.822837] sky2 0000:02:00.0: irq 26 for MSI/MSI-X
[    1.825130] sky2 eth0: addr 00:22:64:71:96:ce
[    1.845365] usb 1-4: configuration #1 chosen from 1 choice
[    1.878145] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.878169] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[    1.913125] [drm] Initialized drm 1.1.0 20060810
[    1.930773] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.931652] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.937687] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.956142] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    1.960270] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
[    2.013201] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.013218] i915 0000:00:02.0: setting latency timer to 64
[    2.023665] [drm] set up 7M of stolen space
[    2.090745] usb 1-5: configuration #1 chosen from 1 choice
[    2.094954] scsi3 : SCSI emulation for USB Mass Storage devices
[    2.095784] usb-storage: device found at 4
[    2.095791] usb-storage: waiting for device to settle before scanning
[    2.127058] [drm] initialized overlay support
[    2.567268] fb0: inteldrmfb frame buffer device
[    2.567276] registered panic notifier
[    2.567295] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.572193] vga16fb: initializing
[    2.572205] vga16fb: mapped to 0xc00a0000
[    2.572215] vga16fb: not registering due to another framebuffer present
[    2.833803] Console: switching to colour frame buffer device 128x37
[    3.487075] xor: automatically using best checksumming function: pIII_sse
[    3.505022]    pIII_sse  :  4847.000 MB/sec
[    3.505028] xor: using function: pIII_sse (4847.000 MB/sec)
[    3.515262] device-mapper: dm-raid45: initialized v0.2594b
[    3.582786] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.792435] usb-storage: device scan complete
[    6.834911] scsi 2:0:0:0: Direct-Access     StoreJet  Transcend            PQ: 0 ANSI: 2 CCS
[    6.836235] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.836977] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    6.837839] sd 2:0:0:0: [sdb] Write Protect is off
[    6.837854] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[    6.837865] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.839835] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.839852]  sdb: sdb1
[    6.863095] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.863112] sd 2:0:0:0: [sdb] Attached SCSI disk
[    7.093542] usb-storage: device scan complete
[    7.094269] scsi 3:0:0:0: Direct-Access     Single   Flash Reader     1.00 PQ: 0 ANSI: 0
[    7.095488] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    7.456670] Adding 192740k swap on /dev/sda6.  Priority:-1 extents:1 across:192740k 
[    7.510373] udev: starting version 151
[    7.534317] sd 3:0:0:0: [sdc] 15564800 512-byte logical blocks: (7.96 GB/7.42 GiB)
[    7.535836] sd 3:0:0:0: [sdc] Write Protect is off
[    7.535850] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[    7.535859] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[    7.538830] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[    7.538847]  sdc: sdc1
[    7.542087] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[    7.542103] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[    7.603905] lp: driver loaded but no devices found
[    8.084144] intel_rng: FWH not detected
[    8.411662] cfg80211: Calling CRDA to update world regulatory domain
[    8.484581] cfg80211: World regulatory domain updated:
[    8.484593]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.484603]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.484611]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.484619]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.484627]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.484636]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.689771] Linux video capture interface: v2.00
[    8.785361] uvcvideo: Found UVC 1.00 device Webcam-101 (10f1:1a08)
[    8.801196] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    8.802024] input: Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input7
[    8.802217] usbcore: registered new interface driver uvcvideo
[    8.802228] USB Video Class driver (v0.1.0)
[    8.813113] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.069849] phy0: Selected rate control algorithm 'minstrel'
[    9.072066] Registered led device: b43-phy0::tx
[    9.072141] Registered led device: b43-phy0::rx
[    9.072207] Registered led device: b43-phy0::radio
[    9.072396] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[    9.172457] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04711/0xa00000
[    9.205492] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[    9.375789] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.375864] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.564646] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[    9.589372] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    9.590231] input: HDA Intel Mic at Sep Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    9.591070] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    9.591941] input: HDA Intel HP Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   10.684183] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   10.723167] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[   10.731219] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[   10.872352] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   16.401190] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.429764] sky2 eth0: enabling interface
[   16.434821] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.550787] ppdev: user-space parallel port driver
[   17.948035] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   17.948473] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.432044] eth0: no IPv6 routers present
[   29.686526] CPU0 attaching NULL sched-domain.
[   29.686543] CPU1 attaching NULL sched-domain.
[   29.709159] CPU0 attaching sched-domain:
[   29.709171]  domain 0: span 0-1 level SIBLING
[   29.709180]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   29.709200]   domain 1: span 0-1 level MC
[   29.709208]    groups: 0-1 (cpu_power = 1178)
[   29.709226] CPU1 attaching sched-domain:
[   29.709234]  domain 0: span 0-1 level SIBLING
[   29.709242]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   29.709259]   domain 1: span 0-1 level MC
[   29.709267]    groups: 0-1 (cpu_power = 1178)
[   41.816314] b43-phy0: Radio hardware status changed to DISABLED

```

---

### Post by sakuramboo on 2011-03-23
I looked around on some sites and I don't think that there is a pre-made program that can interface with that in Linux natively.

In order to use it (even in Windows), you need to use their Memor32 management software. There does not seem to be a native Linux application for it.

That is not to say it can't be accessed. `lsusb` reports the correct device. It has a means of communication to the kernel, so, in theory, you should be able to access it if you were able to interface with the usb port it is using.

I think that this is going to require some hacking on your part. The crappy thing is, the documentation from D2XX is dated and VERY Windows centric. But, the perl example they provided can be ported and they mentioned PyUSB might be ported (doubtful, but would be nice to hop onto their mailing list).

Sorry I couldn't help any further. I don't own one of them and so I can't really start hacking away at it to get it working.

---

