---
title: "Screen resolution issues  ''load detected on head A'"
date: 2012-06-26
forum: Desktop Environments
---

### Post by mojo risin on 2012-06-26
Hi,
I have got a problem with my computer-- It has lost the right setting for resolution again(it did it previously but I could force it then-  I think it may have to do with that error message 'load detected on head a' that comes up whenever one wants to change something about the resolution.
Atm it is in 1024*768 res. and 60 hz which is quite an annoying setting as the refresh rate is rather headache inducing.
The normal setting is 1152*864 , and it also has normally a couple more higher resolutions.
I put up the dmesg- as well as xrandr aswell as the display stats from the system profiler gui.
the first clear messages about the graphics driver start about 28.
[HTML]xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
TV-1 disconnected (normal left inverted right x axis y axis)
morri@schrabbelkiste:~$ xrandr --output VGA-1 --mode 1152×864 --rate 75
xrandr: cannot find mode 1152×864
[/HTML][http://pastebin.com/LrvxpDCY](http://pastebin.com/LrvxpDCY)
and the long dmesg
[HTML]dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-17-generic (buildd@roseapple) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 (Ubuntu 3.0.0-17.30-generic 3.0.22)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffc000 (usable)
[    0.000000]  BIOS-e820: 000000001fffc000 - 000000001ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: System Manufacturer System Name/MED 2001, BIOS ASUS MED 2001 ACPI BIOS Revision 1007 02/12/2001
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1fffc max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 0FC000000 mask FFE000000 write-combining
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-000000001fffc000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001fffc000 page 4k
[    0.000000] kernel direct mapping tables up to 1fffc000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 1e767000 - 1f46b000
[    0.000000] ACPI: RSDP 000f61b0 00014 (v00 ASUS  )
[    0.000000] ACPI: RSDT 1fffc000 0002C (v01 ASUS   MED_2001 30303031 MSFT 31313031)
[    0.000000] ACPI: FACP 1fffc080 00074 (v01 ASUS   MED_2001 30303031 MSFT 31313031)
[    0.000000] ACPI: DSDT 1fffc100 02649 (v01   ASUS MED_2001 00001000 MSFT 0100000B)
[    0.000000] ACPI: FACS 1ffff000 00040
[    0.000000] ACPI: BOOT 1fffc040 00028 (v01 ASUS   MED_2001 30303031 MSFT 31313031)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fffc000
[    0.000000]   low ram: 0 - 1fffc000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fffc
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fffc
[    0.000000] On node 0 totalpages: 130955
[    0.000000] free_area_init_node: node 0, pgdat c17b54c0, node_mem_map dfbfb200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125980 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dfff0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @de000000 s26240 r0 d22912 u4194304
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129931
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=531fd004-53a1-4644-b083-2358792e0cb6 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2096832 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 494324k/524272k available (5340k kernel code, 29496k reserved, 2595k data, 696k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe07fc000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdfffc000   ( 511 MB)
[    0.000000]       .init : 0xc17c1000 - 0xc186f000   ( 696 kB)
[    0.000000]       .data : 0xc15371c4 - 0xc17c0140   (2595 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15371c4   (5340 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=ddc06000 soft=ddc08000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 997.529 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 1995.05 BogoMIPS (lpj=3990116)
[    0.004021] pid_max: default: 32768 minimum: 301
[    0.004078] Security Framework initialized
[    0.004136] AppArmor: AppArmor initialized
[    0.004142] Yama: becoming mindful.
[    0.004298] Mount-cache hash table entries: 512
[    0.004636] Initializing cgroup subsys cpuacct
[    0.004654] Initializing cgroup subsys memory
[    0.004679] Initializing cgroup subsys devices
[    0.004687] Initializing cgroup subsys freezer
[    0.004694] Initializing cgroup subsys net_cls
[    0.004701] Initializing cgroup subsys blkio
[    0.004719] Initializing cgroup subsys perf_event
[    0.004803] mce: CPU supports 5 MCE banks
[    0.004949] SMP alternatives: switching to UP code
[    0.018788] Freeing SMP alternatives: 24k freed
[    0.018832] ACPI: Core revision 20110413
[    0.022486] ACPI: setting ELCR to 0200 (from 0e20)
[    0.022703] ftrace: allocating 24903 entries in 49 pages
[    0.028321] weird, boot CPU (#0) not listed by the BIOS.
[    0.028336] SMP motherboard not detected.
[    0.028342] Local APIC not detected. Using dummy APIC emulation.
[    0.028347] SMP disabled
[    0.028354] Performance Events: 
[    0.028361] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.028367] no hardware sampling interrupt available.
[    0.028376] p6 PMU driver.
[    0.028392] ... version:                0
[    0.028397] ... bit width:              32
[    0.028401] ... generic registers:      2
[    0.028407] ... value mask:             00000000ffffffff
[    0.028413] ... max period:             000000007fffffff
[    0.028418] ... fixed-purpose events:   0
[    0.028423] ... event mask:             0000000000000003
[    0.033214] Brought up 1 CPUs
[    0.033229] Total of 1 processors activated (1995.05 BogoMIPS).
[    0.033834] devtmpfs: initialized
[    0.034390] PM: Registering ACPI NVS region at 1ffff000 (4096 bytes)
[    0.041824] print_constraints: dummy: 
[    0.041884] Time: 10:01:50  Date: 06/26/12
[    0.042032] NET: Registered protocol family 16
[    0.042359] EISA bus registered
[    0.042394] ACPI: bus type pci registered
[    0.043593] PCI: PCI BIOS revision 2.10 entry at 0xf0900, last bus=1
[    0.043600] PCI: Using configuration type 1 for base access
[    0.046620] bio: create slab <bio-0> at 0
[    0.048046] ACPI: EC: Look up EC in DSDT
[    0.051822] ACPI: Interpreter enabled
[    0.051842] ACPI: (supports S0 S1 S4 S5)
[    0.051906] ACPI: Using PIC for interrupt routing
[    0.066155] ACPI: No dock devices found.
[    0.066165] HEST: Table not found.
[    0.066178] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.066385] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.066792] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.066801] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.066810] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.066819] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000dffff] (ignored)
[    0.066827] pci_root PNP0A03:00: host bridge window [mem 0x20000000-0xffffffff] (ignored)
[    0.066859] pci 0000:00:00.0: [1106:0691] type 0 class 0x000600
[    0.066878] pci 0000:00:00.0: reg 10: [mem 0xfc000000-0xfdffffff pref]
[    0.066958] pci 0000:00:01.0: [1106:8598] type 1 class 0x000604
[    0.067005] pci 0000:00:01.0: supports D1
[    0.067030] pci 0000:00:04.0: [1106:0686] type 0 class 0x000601
[    0.067117] pci 0000:00:04.1: [1106:0571] type 0 class 0x000101
[    0.067164] pci 0000:00:04.1: reg 20: [io  0xd800-0xd80f]
[    0.067233] pci 0000:00:04.2: [1106:3038] type 0 class 0x000c03
[    0.067279] pci 0000:00:04.2: reg 20: [io  0xd400-0xd41f]
[    0.067339] pci 0000:00:04.3: [1106:3038] type 0 class 0x000c03
[    0.067384] pci 0000:00:04.3: reg 20: [io  0xd000-0xd01f]
[    0.067444] pci 0000:00:04.4: [1106:3057] type 0 class 0x000600
[    0.067492] pci 0000:00:04.4: quirk: [io  0xe400-0xe4ff] claimed by vt82c586 ACPI
[    0.067503] pci 0000:00:04.4: quirk: [io  0xe800-0xe80f] claimed by vt82c686 SMB
[    0.067552] pci 0000:00:05.0: [1274:5880] type 0 class 0x000401
[    0.067572] pci 0000:00:05.0: reg 10: [io  0xb800-0xb83f]
[    0.067640] pci 0000:00:05.0: supports D1 D2
[    0.067668] pci 0000:00:09.0: [1317:0985] type 0 class 0x000200
[    0.067689] pci 0000:00:09.0: reg 10: [io  0xb400-0xb4ff]
[    0.067704] pci 0000:00:09.0: reg 14: [mem 0xed800000-0xed8003ff]
[    0.067744] pci 0000:00:09.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.067773] pci 0000:00:09.0: supports D1 D2
[    0.067780] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.067790] pci 0000:00:09.0: PME# disabled
[    0.067815] pci 0000:00:0a.0: [1244:0e00] type 0 class 0x000280
[    0.067836] pci 0000:00:0a.0: reg 10: [mem 0xed000000-0xed00001f]
[    0.067850] pci 0000:00:0a.0: reg 14: [io  0xb000-0xb01f]
[    0.067911] pci 0000:00:0a.0: supports D2
[    0.067918] pci 0000:00:0a.0: PME# supported from D2 D3hot D3cold
[    0.067926] pci 0000:00:0a.0: PME# disabled
[    0.067951] pci 0000:00:0b.0: [1033:0035] type 0 class 0x000c03
[    0.067971] pci 0000:00:0b.0: reg 10: [mem 0xec800000-0xec800fff]
[    0.068073] pci 0000:00:0b.0: supports D1 D2
[    0.068080] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.068088] pci 0000:00:0b.0: PME# disabled
[    0.068113] pci 0000:00:0b.1: [1033:0035] type 0 class 0x000c03
[    0.068134] pci 0000:00:0b.1: reg 10: [mem 0xec000000-0xec000fff]
[    0.068199] pci 0000:00:0b.1: supports D1 D2
[    0.068205] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot
[    0.068214] pci 0000:00:0b.1: PME# disabled
[    0.068242] pci 0000:00:0b.2: [1033:00e0] type 0 class 0x000c03
[    0.068263] pci 0000:00:0b.2: reg 10: [mem 0xeb800000-0xeb8000ff]
[    0.068328] pci 0000:00:0b.2: supports D1 D2
[    0.068335] pci 0000:00:0b.2: PME# supported from D0 D1 D2 D3hot
[    0.068343] pci 0000:00:0b.2: PME# disabled
[    0.068419] pci 0000:01:00.0: [10de:0150] type 0 class 0x000300
[    0.068440] pci 0000:01:00.0: reg 10: [mem 0xee000000-0xeeffffff]
[    0.068455] pci 0000:01:00.0: reg 14: [mem 0xf0000000-0xf7ffffff pref]
[    0.068491] pci 0000:01:00.0: reg 30: [mem 0xefff0000-0xefffffff pref]
[    0.068562] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.068572] pci 0000:00:01.0:   bridge window [io  0xe000-0xd000] (disabled)
[    0.068582] pci 0000:00:01.0:   bridge window [mem 0xee000000-0xefdfffff]
[    0.068592] pci 0000:00:01.0:   bridge window [mem 0xeff00000-0xfbffffff pref]
[    0.068607] pci_bus 0000:00: on NUMA node 0
[    0.068620] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.068967] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.069115]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.124030] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.124184] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.124331] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.124490] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.124803] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.124812] vgaarb: loaded
[    0.124816] vgaarb: bridge control possible 0000:01:00.0
[    0.125510] SCSI subsystem initialized
[    0.125727] libata version 3.00 loaded.
[    0.125882] usbcore: registered new interface driver usbfs
[    0.125919] usbcore: registered new interface driver hub
[    0.126006] usbcore: registered new device driver usb
[    0.126293] PCI: Using ACPI for IRQ routing
[    0.126307] PCI: pci_cache_line_size set to 32 bytes
[    0.126404] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.126411] reserve RAM buffer: 000000001fffc000 - 000000001fffffff 
[    0.126729] NetLabel: Initializing
[    0.126736] NetLabel:  domain hash size = 128
[    0.126740] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.126772] NetLabel:  unlabeled traffic allowed by default
[    0.126946] Switching to clocksource pit
[    0.148501] AppArmor: AppArmor Filesystem Enabled
[    0.148619] pnp: PnP ACPI init
[    0.148678] ACPI: bus type pnp registered
[    0.149124] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.149134] pnp 00:00: [mem 0x000f0000-0x000fffff]
[    0.149142] pnp 00:00: [mem 0x00100000-0x1fffffff]
[    0.149150] pnp 00:00: [mem 0xfffe0000-0xffffffff]
[    0.149321] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.149332] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.149342] system 00:00: [mem 0x00100000-0x1fffffff] could not be reserved
[    0.149352] system 00:00: [mem 0xfffe0000-0xffffffff] could not be reserved
[    0.149364] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.149772] pnp 00:01: [bus 00-ff]
[    0.149782] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.149791] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.149799] pnp 00:01: [io  0x0d00-0xffff window]
[    0.149807] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.149815] pnp 00:01: [mem 0x000c8000-0x000dffff window]
[    0.149823] pnp 00:01: [mem 0x20000000-0xffffffff window]
[    0.149939] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.150058] pnp 00:02: [io  0x0010-0x001f]
[    0.150066] pnp 00:02: [io  0x0022-0x002d]
[    0.150074] pnp 00:02: [io  0x0030-0x003f]
[    0.150081] pnp 00:02: [io  0x0044-0x005f]
[    0.150088] pnp 00:02: [io  0x0062-0x0063]
[    0.150095] pnp 00:02: [io  0x0065-0x006f]
[    0.150102] pnp 00:02: [io  0x0074-0x007f]
[    0.150109] pnp 00:02: [io  0x0091-0x0093]
[    0.150116] pnp 00:02: [io  0x00a2-0x00bf]
[    0.150124] pnp 00:02: [io  0x00e0-0x00ef]
[    0.150131] pnp 00:02: [io  0x03f0-0x03f1]
[    0.150138] pnp 00:02: [io  0x04d0-0x04d1]
[    0.150261] system 00:02: [io  0x03f0-0x03f1] has been reserved
[    0.150270] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.150280] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.150339] pnp 00:03: [io  0xe400-0xe47f]
[    0.150347] pnp 00:03: [io  0xe800-0xe80f]
[    0.150371] pnp 00:03: disabling [io  0xe400-0xe47f] because it overlaps 0000:00:04.4 BAR 13 [io  0xe400-0xe4ff]
[    0.150459] system 00:03: [io  0xe800-0xe80f] has been reserved
[    0.150470] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.150610] pnp 00:04: [dma 4]
[    0.150618] pnp 00:04: [io  0x0000-0x000f]
[    0.150625] pnp 00:04: [io  0x0080-0x0090]
[    0.150632] pnp 00:04: [io  0x0094-0x009f]
[    0.150640] pnp 00:04: [io  0x00c0-0x00df]
[    0.150725] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.150760] pnp 00:05: [io  0x0070-0x0073]
[    0.150773] pnp 00:05: [irq 8]
[    0.150847] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.150875] pnp 00:06: [io  0x0061]
[    0.150950] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.150979] pnp 00:07: [io  0x00f0-0x00ff]
[    0.150988] pnp 00:07: [irq 13]
[    0.151063] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.151411] pnp 00:08: [io  0x03f2-0x03f5]
[    0.151419] pnp 00:08: [io  0x03f7]
[    0.151436] pnp 00:08: [irq 6]
[    0.151444] pnp 00:08: [dma 2]
[    0.151568] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.152282] pnp 00:09: [io  0x0378-0x037f]
[    0.152291] pnp 00:09: [io  0x0778-0x077b]
[    0.152299] pnp 00:09: [irq 7]
[    0.152306] pnp 00:09: [dma 3]
[    0.152464] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.152917] pnp 00:0a: [io  0x03f8-0x03ff]
[    0.152926] pnp 00:0a: [irq 4]
[    0.153168] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.153692] pnp 00:0b: [io  0x02f8-0x02ff]
[    0.153701] pnp 00:0b: [irq 3]
[    0.153865] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.154074] pnp 00:0c: [io  0x0060]
[    0.154082] pnp 00:0c: [io  0x0064]
[    0.154089] pnp 00:0c: [irq 1]
[    0.154172] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.154296] pnp 00:0d: [irq 12]
[    0.154378] pnp 00:0d: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.154494] pnp: PnP ACPI: found 14 devices
[    0.154501] ACPI: ACPI bus type pnp unregistered
[    0.154512] PnPBIOS: Disabled by ACPI PNP
[    0.194189] Switching to clocksource acpi_pm
[    0.194276] PCI: max bus depth: 1 pci_try_num: 2
[    0.194329] pci 0000:00:09.0: BAR 6: assigned [mem 0x20000000-0x2001ffff pref]
[    0.194341] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.194348] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.194360] pci 0000:00:01.0:   bridge window [mem 0xee000000-0xefdfffff]
[    0.194371] pci 0000:00:01.0:   bridge window [mem 0xeff00000-0xfbffffff pref]
[    0.194400] pci 0000:00:01.0: setting latency timer to 64
[    0.194411] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.194419] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.194428] pci_bus 0000:01: resource 1 [mem 0xee000000-0xefdfffff]
[    0.194437] pci_bus 0000:01: resource 2 [mem 0xeff00000-0xfbffffff pref]
[    0.194578] NET: Registered protocol family 2
[    0.194760] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.195325] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.195746] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.196276] TCP: Hash tables configured (established 16384 bind 16384)
[    0.196285] TCP reno registered
[    0.196303] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.196358] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.196787] NET: Registered protocol family 1
[    0.196856] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.196869] pci 0000:00:04.0: Disabling VIA external APIC routing
[    0.197105] Switched to NOHz mode on CPU #0
[    0.197142] pci 0000:01:00.0: Boot video device
[    0.197153] PCI: CLS 32 bytes, default 32
[    0.197355] Simple Boot Flag at 0x3a set to 0x1
[    0.198162] audit: initializing netlink socket (disabled)
[    0.198198] type=2000 audit(1340704910.194:1): initialized
[    0.254253] Trying to unpack rootfs image as initramfs...
[    0.329213] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.341385] VFS: Disk quotas dquot_6.5.2
[    0.341589] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.344268] fuse init (API version 7.16)
[    0.344643] msgmni has been set to 965
[    0.356596] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.356810] io scheduler noop registered
[    0.356817] io scheduler deadline registered
[    0.356901] io scheduler cfq registered (default)
[    0.357326] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.357402] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.357788] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.357806] ACPI: Power Button [PWRB]
[    0.357942] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.357952] ACPI: Power Button [PWRF]
[    0.358010] ACPI: acpi_idle registered with cpuidle
[    0.358095] Marking TSC unstable due to TSC halts in idle
[    0.371496] ERST: Table is not found!
[    0.376886] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.397759] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.397868] isapnp: Scanning for PnP cards...
[    0.489610] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.576732] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.621900] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.689506] Linux agpgart interface v0.103
[    0.689722] agpgart: Detected VIA Apollo Pro 133 chipset
[    0.692001] agpgart-via 0000:00:00.0: AGP aperture is 32M @ 0xfc000000
[    0.699960] brd: module loaded
[    0.706734] loop: module loaded
[    0.708650] Fixed MDIO Bus: probed
[    0.708739] PPP generic driver version 2.4.2
[    0.708941] tun: Universal TUN/TAP device driver, 1.6
[    0.708947] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.709225] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.709895] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    0.709904] PCI: setting IRQ 9 as level-triggered
[    0.709918] ehci_hcd 0000:00:0b.2: PCI INT C -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    0.709957] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[    0.710089] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 1
[    0.772437] ehci_hcd 0000:00:0b.2: irq 9, io mem 0xeb800000
[    0.868225] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 1.00
[    0.868772] hub 1-0:1.0: USB hub found
[    0.868789] hub 1-0:1.0: 3 ports detected
[    0.869034] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.869727] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.869737] PCI: setting IRQ 10 as level-triggered
[    0.869750] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.869789] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.869986] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.870039] ohci_hcd 0000:00:0b.0: irq 10, io mem 0xec800000
[    0.992690] hub 2-0:1.0: USB hub found
[    0.992710] hub 2-0:1.0: 2 ports detected
[    0.993414] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[    0.993424] PCI: setting IRQ 5 as level-triggered
[    0.993437] ohci_hcd 0000:00:0b.1: PCI INT B -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    0.993476] ohci_hcd 0000:00:0b.1: OHCI Host Controller
[    0.993666] ohci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 3
[    0.993722] ohci_hcd 0000:00:0b.1: irq 5, io mem 0xec000000
[    1.044427] isapnp: No Plug & Play device found
[    1.097151] hub 3-0:1.0: USB hub found
[    1.097171] hub 3-0:1.0: 1 port detected
[    1.097374] uhci_hcd: USB Universal Host Controller Interface driver
[    1.097583] uhci_hcd 0000:00:04.2: PCI INT D -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    1.097615] uhci_hcd 0000:00:04.2: UHCI Host Controller
[    1.097782] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 4
[    1.097835] uhci_hcd 0000:00:04.2: irq 5, io base 0x0000d400
[    1.098234] hub 4-0:1.0: USB hub found
[    1.098249] hub 4-0:1.0: 2 ports detected
[    1.098414] uhci_hcd 0000:00:04.3: PCI INT D -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    1.098433] uhci_hcd 0000:00:04.3: UHCI Host Controller
[    1.098555] uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 5
[    1.098597] uhci_hcd 0000:00:04.3: irq 5, io base 0x0000d000
[    1.098978] hub 5-0:1.0: USB hub found
[    1.098992] hub 5-0:1.0: 2 ports detected
[    1.099324] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.104820] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.104860] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.105421] mousedev: PS/2 mouse device common for all mice
[    1.105863] rtc_cmos 00:05: RTC can wake from S4
[    1.106111] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.106158] rtc0: alarms up to one year, 242 bytes nvram
[    1.106603] device-mapper: uevent: version 1.0.3
[    1.106858] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.106961] EISA: Probing bus 0 at eisa.0
[    1.107023] EISA: Detected 0 cards.
[    1.107051] cpufreq-nforce2: No nForce2 chipset.
[    1.107135] cpuidle: using governor ladder
[    1.107236] cpuidle: using governor menu
[    1.107243] EFI Variables Facility v0.08 2004-May-17
[    1.108164] TCP cubic registered
[    1.108694] NET: Registered protocol family 10
[    1.117853] NET: Registered protocol family 17
[    1.117975] Registering the dns_resolver key type
[    1.118043] Using IPI No-Shortcut mode
[    1.118381] PM: Hibernation image not present or could not be loaded.
[    1.118418] registered taskstats version 1
[    1.132423] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.472172] usb 3-1: new full speed USB device number 2 using ohci_hcd
[    1.715692] Freeing initrd memory: 13328k freed
[    1.774858]   Magic number: 0:973:22
[    1.775081] rtc_cmos 00:05: setting system clock to 2012-06-26 10:01:52 UTC (1340704912)
[    1.775134] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.775139] EDD information not available.
[    1.775432] Freeing unused kernel memory: 696k freed
[    1.777235] Write protecting the kernel text: 5344k
[    1.777352] Write protecting the kernel read-only data: 2192k
[    1.808309] usb 5-2: new full speed USB device number 2 using uhci_hcd
[    1.845255] udevd[76]: starting version 173
[    2.201234] Floppy drive(s): fd0 is 1.44M
[    2.220145] FDC 0 is a post-1991 82077
[    2.270251] pata_via 0000:00:04.1: version 0.3.4
[    2.299387] scsi0 : pata_via
[    2.304185] scsi1 : pata_via
[    2.305106] ACPI Exception: AE_AML_PACKAGE_LIMIT, Index (0x0000000000000008) is beyond end of object (20110413/exoparg2-418)
[    2.305131] ACPI Error: Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0._GTM] (Node ddc22a08), AE_AML_PACKAGE_LIMIT (20110413/psparse-536)
[    2.305165] ata1: ACPI get timing mode failed (AE 0x300b)
[    2.305436] ACPI Exception: AE_AML_PACKAGE_LIMIT, Index (0x0000000000000008) is beyond end of object (20110413/exoparg2-418)
[    2.305456] ACPI Error: Method parse/execution failed [\_SB_.PCI0.IDE0.CHN1._GTM] (Node ddc22af8), AE_AML_PACKAGE_LIMIT (20110413/psparse-536)
[    2.305481] ata2: ACPI get timing mode failed (AE 0x300b)
[    2.305491] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xd800 irq 14
[    2.305499] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xd808 irq 15
[    2.309895] tulip: Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    2.310005] tulip 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    2.310044] tulip: tulip_init_one: Enabled WOL support for AN983B
[    2.310356] tulip0:  MII transceiver #1 config 1000 status 7849 advertising 05e1
[    2.358785] net eth0: ADMtek Comet rev 17 at Port 0xb400, 00:0c:f6:04:83:c6, IRQ 9
[    2.468595] ata1.00: native sectors (78165359) is smaller than sectors (78165360)
[    2.468612] ata1.00: ATA-4: ST340823A, 3.39, max UDMA/100
[    2.468621] ata1.00: 78165360 sectors, multi 16: LBA 
[    2.476553] ata1.00: configured for UDMA/66
[    2.476903] scsi 0:0:0:0: Direct-Access     ATA      ST340823A        3.39 PQ: 0 ANSI: 5
[    2.477399] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.477843] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    2.478011] sd 0:0:0:0: [sda] Write Protect is off
[    2.478021] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.478088] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.551778]  sda: sda2 < sda5 sda6 sda7 >
[    2.552995] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.648328] ata2.00: ATAPI: SONY CD-RW CRX0811, MYS2, max MWDMA2
[    2.648347] ata2.01: ATAPI: LITEON  DVD-ROM LTD122, IHN9, max UDMA/33
[    2.664246] ata2.00: configured for MWDMA2
[    2.680242] ata2.01: configured for UDMA/33
[    2.682536] scsi 1:0:0:0: CD-ROM            SONY     CD-RW CRX0811    MYS2 PQ: 0 ANSI: 5
[    2.685017] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    2.685029] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.685420] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.685630] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.687611] scsi 1:0:1:0: CD-ROM            LITEON   DVD-ROM LTD122   IHN9 PQ: 0 ANSI: 5
[    2.691040] sr1: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[    2.691455] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    2.691683] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    3.410910] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    6.808134] uhci_hcd 0000:00:04.3: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   16.920080] usb 5-2: device descriptor read/64, error -110
[   24.723866] udevd[296]: starting version 175
[   24.803885] Adding 514044k swap on /dev/sda7.  Priority:-1 extents:1 across:514044k 
[   25.069197] lp: driver loaded but no devices found
[   25.282587] parport_pc: VIA 686A/8231 detected
[   25.282598] parport_pc: probing current configuration
[   25.282623] parport_pc: Current parallel port base: 0x378
[   25.282722] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   25.380504] lp0: using parport0 (interrupt-driven).
[   25.380518] parport_pc: VIA parallel port: io=0x378, irq=7
[   25.423735] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.609598] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   25.827740] wmi: Mapper loaded
[   26.373342] type=1400 audit(1340704937.096:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=493 comm="apparmor_parser"
[   26.374805] type=1400 audit(1340704937.096:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=493 comm="apparmor_parser"
[   26.375622] type=1400 audit(1340704937.096:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=493 comm="apparmor_parser"
[   26.435929] [drm] Initialized drm 1.1.0 20060810
[   26.531861] via686a 0000:00:04.4: base address not set - upgrade BIOS or use force_addr=0xaddr
[   26.557995] Modular ISDN core version 1.1.21
[   26.574332] NET: Registered protocol family 34
[   26.610234] psmouse serio1: ID: 10 00 64
[   26.641107] mISDNipac module version 2.0
[   26.837501] type=1400 audit(1340704937.560:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=495 comm="apparmor_parser"
[   27.072962] AVM Fritz PCI driver Rev. 2.1
[   27.073067] fcpci 0000:00:0a.0: PCI INT A -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[   27.073076] mISDN: found adapter Fritz!Card PCI v2 at 0000:00:0a.0
[   27.073095] AVM.1: AVM Fritz!CARD PCIv2 config irq:5 base:0xB000
[   27.472198] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   27.475161] ppdev: user-space parallel port driver
...
[   27.476474] NET: Registered protocol family 31
[   27.704797] type=1400 audit(1340704938.428:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=620 comm="apparmor_parser"
[   27.708323] type=1400 audit(1340704938.432:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=620 comm="apparmor_parser"
[   28.034989] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   28.035001] PCI: setting IRQ 11 as level-triggered
[   28.035017] nouveau 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   28.173804] ISDN subsystem Rev: 1.1.2.3/1.1.2.3/1.1.2.2/1.1.2.3/1.1.2.2/1.1.2.2 loaded
[   28.212857] [drm] nouveau 0000:01:00.0: Detected an NV10 generation card (0x015000a3)
[   28.213161] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   28.248339] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   28.248737] [drm] nouveau 0000:01:00.0: BMP BIOS found
[   28.248745] [drm] nouveau 0000:01:00.0: BMP version 5.17
[   28.248753] [drm] nouveau 0000:01:00.0: Bios version 03.15.00.12
[   28.248763] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 1.2
[   28.248771] [drm] nouveau 0000:01:00.0: No useful information in BIOS output table; adding all possible outputs
[   28.541758] [drm] nouveau 0000:01:00.0: Detected TV encoder: ch7006
[   28.542304] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x07F6
[   28.542329] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x0E6C
[   28.542343] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x0811
[   28.542368] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x0E13
[   28.542383] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0x088E
[   28.542392] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 5 at offset 0x0980
[   28.542420] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 6 at offset 0x08B7
[   28.820179] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 7 at offset 0x091B
[   28.930787] init: failsafe main process (654) killed by TERM signal
[   29.316863] HiSax: Linux Driver for passive ISDN cards
[   29.316878] HiSax: Version 3.5 (module)
[   29.316885] HiSax: Layer1 Revision 2.46.2.5
[   29.316891] HiSax: Layer2 Revision 2.30.2.4
[   29.316896] HiSax: TeiMgr Revision 2.20.2.3
[   29.316901] HiSax: Layer3 Revision 2.22.2.3
[   29.316907] HiSax: LinkLayer Revision 2.59.2.4
[   29.380381] hisax_isac: ISAC-S/ISAC-SX ISDN driver v0.1.0
[   29.393029] type=1400 audit(1340704940.116:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=743 comm="apparmor_parser"
[   29.408495] type=1400 audit(1340704940.132:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=746 comm="apparmor_parser"
[   29.412003] type=1400 audit(1340704940.132:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=746 comm="apparmor_parser"
[   29.415906] type=1400 audit(1340704940.136:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=746 comm="apparmor_parser"
[   29.460225] hisax_fcpcipnp: Fritz!Card PCI/PCIv2/PnP ISDN driver v0.0.1
[   29.460256] Error: Driver 'fcpci' is already registered, aborting...
[   30.432651] ENS1371 0000:00:05.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[   30.812088] [drm] nouveau 0000:01:00.0: 0 available performance level(s)
[   30.812115] [drm] nouveau 0000:01:00.0: c: memory 332MHz core 199MHz
[   30.816604] [TTM] Zone  kernel: Available graphics memory: 254186 kiB.
[   30.816612] [TTM] Initializing pool allocator.
[   30.816648] [drm] nouveau 0000:01:00.0: Detected 32MiB VRAM
[   30.817001] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   30.817039] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   30.817112] nouveau 0000:01:00.0: putting AGP V2 device into 4x mode
[   30.817121] [drm] nouveau 0000:01:00.0: 32 MiB GART (aperture)
[   30.821719] [drm] nouveau 0000:01:00.0: Detected TV encoder: ch7006
[   31.017474] i2c-core: driver [ch7006] using legacy suspend method
[   31.017484] i2c-core: driver [ch7006] using legacy resume method
[   31.025040] ch7006 1-0075: Detected version ID: 50
[   31.039211] init: alsa-restore main process (827) terminated with status 19
[   31.151190] vboxdrv: Found 1 processor cores.
[   31.157151] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   31.157162] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   31.384065] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   31.384080] [drm] No driver support for vblank timestamp query.
[   31.388924] vboxpci: IOMMU not found (not registered)
[   31.406030] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   31.406044] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 1)
[   31.563463] [drm] nouveau 0000:01:00.0: Load detected on head A
[   31.760671] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x44000, bo d2c87600
[   31.771892] fbcon: nouveaufb (fb0) is primary device
[   31.775764] Console: switching to colour frame buffer device 128x48
[   31.775891] fb0: nouveaufb frame buffer device
[   31.775897] drm: registered panic notifier
[   31.775925] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   32.336450] init: lxdm main process (936) killed by TERM signal
[   32.352147] usb 5-2: new full speed USB device number 3 using uhci_hcd
[   32.932741] [drm] nouveau 0000:01:00.0: Load detected on head A
[   33.171434] [drm] nouveau 0000:01:00.0: Load detected on head A
[   33.960069] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 1)
[   34.038590] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[   34.038606] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A
[   34.047801] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 1)
[   36.130919] [drm] nouveau 0000:01:00.0: Load detected on head A
[   38.976044] eth0: no IPv6 routers present
[   43.431006] [drm] nouveau 0000:01:00.0: Load detected on head A
[   45.175578] [drm] nouveau 0000:01:00.0: Load detected on head A
[   45.511754] [drm] nouveau 0000:01:00.0: Load detected on head A
[   45.930937] [drm] nouveau 0000:01:00.0: Load detected on head A
[   46.230913] [drm] nouveau 0000:01:00.0: Load detected on head A
...
[  405.439892] [drm] nouveau 0000:01:00.0: Load detected on head A
[ 1083.795047] [drm] nouveau 0000:01:00.0: Load detected on head A
[/HTML][ATTACH]220273[/ATTACH]
[HTML]-Display-
Resolution        : 1024x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.11.3
-Monitors-
Monitor 0        : 1024x768 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : Nouveau
Renderer        : Mesa DRI nv15 x86/MMX/SSE
Version        : 1.2 Mesa 8.0.2
Direct Rendering        : Yes
[/HTML]

---

### Post by mojo risin on 2012-06-26
Okay-- Looks like it was the hardware(my Monitor) that is on the way out. It is a little older but it looks fine with my newer monitor on the computer

---

