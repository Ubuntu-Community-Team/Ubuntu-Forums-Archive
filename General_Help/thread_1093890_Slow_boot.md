---
title: "Slow boot"
date: 2009-03-12
forum: General Help
---

### Post by Nullomore on 2009-03-12
When I boot up, the progress bar stops at a certain point and stays there for a good minute or two. I am not sure what is wrong. Here is the output from dmesg. I think the longest pause occurs at [23.581857], and during the boot, it said [FAILED]. Please ignore the part at [82.736115] usb 1-2: USB disconnect, address 2. This is my cat yoinking out the usb mouse by accident.

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-8-eeepc (root@adamm-laptop) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Sun Nov 16 12:02:12 MST 2008 (Ubuntu 2.6.27-8.17eeepc1-eeepc)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f780000 (usable)
[    0.000000]  BIOS-e820: 000000001f780000 - 000000001f790000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f790000 - 000000001f7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f7d0000 - 000000001f7de000 (reserved)
[    0.000000]  BIOS-e820: 000000001f7e0000 - 000000001f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1f780 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 1f780000 @ 10000-16000
[    0.000000] RAMDISK: 1effe000 - 1f76f474
[    0.000000] ACPI: RSDP 000FBE60, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1F780000, 0034 (r1 A M I  OEMRSDT  10000717 MSFT       97)
[    0.000000] ACPI: FACP 1F780200, 0081 (r1 A M I  OEMFACP  10000717 MSFT       97)
[    0.000000] ACPI: DSDT 1F780400, 5F17 (r1  A0797 A0797000        0 INTL 20051117)
[    0.000000] ACPI: FACS 1F790000, 0040
[    0.000000] ACPI: APIC 1F780390, 0068 (r1 A M I  OEMAPIC  10000717 MSFT       97)
[    0.000000] ACPI: OEMB 1F790040, 0046 (r1 A M I  AMI_OEM  10000717 MSFT       97)
[    0.000000] ACPI: MCFG 1F786320, 003C (r1 A M I  OEMMCFG  10000717 MSFT       97)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1f780000
[    0.000000]   low ram: 00000000 - 1f780000
[    0.000000]   bootmap 00012000 - 00015ef0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f780000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 0000597120]    TEXT DATA BSS ==> [0000100000 - 0000597120]
[    0.000000]   #4 [001effe000 - 001f76f474]          RAMDISK ==> [001effe000 - 001f76f474]
[    0.000000]   #5 [0000598000 - 000059b000]    INIT_PG_TABLE ==> [0000598000 - 000059b000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001f780
[    0.000000]   HighMem  0x0001f780 -> 0x0001f780
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001f780
[    0.000000] On node 0 totalpages: 128783
[    0.000000] free_area_init_node: node 0, pgdat c0481b80, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 123703 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:df600000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 2, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127650
[    0.000000] Kernel command line: root=UUID=a5cfc97c-02df-42c6-9182-ab7a129c4381 ro clocksource=hpet 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 630.058 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Memory: 497588k/515584k available (2548k kernel code, 17356k reserved, 1115k data, 332k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xfff9e000 - 0xfffff000   ( 388 kB)
[    0.004000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.004000]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdf780000   ( 503 MB)
[    0.004000]       .init : 0xc049b000 - 0xc04ee000   ( 332 kB)
[    0.004000]       .data : 0xc037d274 - 0xc0494180   (1115 kB)
[    0.004000]       .text : 0xc0100000 - 0xc037d274   (2548 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004024] Calibrating delay loop (skipped), value calculated using timer frequency.. 1260.11 BogoMIPS (lpj=2520232)
[    0.004236] Security Framework initialized
[    0.004329] SELinux:  Disabled at boot.
[    0.004460] AppArmor: AppArmor initialized
[    0.004558] Mount-cache hash table entries: 512
[    0.005060] Initializing cgroup subsys ns
[    0.005157] Initializing cgroup subsys cpuacct
[    0.005241] Initializing cgroup subsys memory
[    0.005358] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.005476] CPU: L2 cache: 512K
[    0.005575] Checking 'hlt' instruction... OK.
[    0.021200] SMP alternatives: switching to UP code
[    0.032041] Freeing SMP alternatives: 11k freed
[    0.032137] ACPI: Core revision 20080609
[    0.038236] ACPI: Checking initramfs for custom DSDT
[    1.040327] ENABLING IO-APIC IRQs
[    1.040657] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.081956] CPU0: Intel(R) Celeron(R) M processor          900MHz stepping 06
[    1.084031] Brought up 1 CPUs
[    1.084031] Total of 1 processors activated (1260.11 BogoMIPS).
[    1.084031] CPU0 attaching sched-domain:
[    1.084031]  domain 0: span 0 level CPU
[    1.084031]   groups: 0
[    1.084031] net_namespace: 840 bytes
[    1.084031] Booting paravirtualized kernel on bare hardware
[    1.084031] Time:  5:49:05  Date: 03/12/09
[    1.084031] NET: Registered protocol family 16
[    1.084031] ACPI: bus type pci registered
[    1.084031] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    1.084031] PCI: Not using MMCONFIG.
[    1.084031] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    1.084031] PCI: Using configuration type 1 for base access
[    1.089235] ACPI: EC: Look up EC in DSDT
[    1.111221] ACPI: Interpreter enabled
[    1.111321] ACPI: (supports S0 S1 S3 S4 S5)
[    1.111616] ACPI: Using IOAPIC for interrupt routing
[    1.111898] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    1.119590] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    1.119688] PCI: Using MMCONFIG for extended config space
[    1.141237] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    1.141344] ACPI: EC: driver started in poll mode
[    1.141890] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.142278] PCI: 0000:00:02.0 reg 10 32bit mmio: [f7f00000, f7f7ffff]
[    1.142294] PCI: 0000:00:02.0 reg 14 io port: [ec00, ec07]
[    1.142307] PCI: 0000:00:02.0 reg 18 32bit mmio: [d0000000, dfffffff]
[    1.142321] PCI: 0000:00:02.0 reg 1c 32bit mmio: [f7ec0000, f7efffff]
[    1.142386] PCI: 0000:00:02.1 reg 10 32bit mmio: [f7f80000, f7ffffff]
[    1.142540] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f7eb8000, f7ebbfff]
[    1.142607] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.142703] pci 0000:00:1b.0: PME# disabled
[    1.142864] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.142957] pci 0000:00:1c.0: PME# disabled
[    1.143113] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.143207] pci 0000:00:1c.1: PME# disabled
[    1.143364] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.143457] pci 0000:00:1c.2: PME# disabled
[    1.143601] PCI: 0000:00:1d.0 reg 20 io port: [e400, e41f]
[    1.143681] PCI: 0000:00:1d.1 reg 20 io port: [e480, e49f]
[    1.143760] PCI: 0000:00:1d.2 reg 20 io port: [e800, e81f]
[    1.143840] PCI: 0000:00:1d.3 reg 20 io port: [e880, e89f]
[    1.144056] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    1.144073] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    1.144201] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    1.144335] PCI: 0000:00:1f.2 reg 10 io port: [0, 7]
[    1.144349] PCI: 0000:00:1f.2 reg 14 io port: [0, 3]
[    1.144363] PCI: 0000:00:1f.2 reg 18 io port: [0, 7]
[    1.144376] PCI: 0000:00:1f.2 reg 1c io port: [0, 3]
[    1.144390] PCI: 0000:00:1f.2 reg 20 io port: [ffa0, ffaf]
[    1.144430] pci 0000:00:1f.2: PME# supported from D3hot
[    1.144521] pci 0000:00:1f.2: PME# disabled
[    1.144660] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    1.144853] PCI: 0000:03:00.0 reg 10 64bit mmio: [fbfc0000, fbffffff]
[    1.144904] PCI: 0000:03:00.0 reg 30 32bit mmio: [fbfa0000, fbfbffff]
[    1.144945] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    1.145038] pci 0000:03:00.0: PME# disabled
[    1.145178] PCI: bridge 0000:00:1c.1 32bit mmio: [fbf00000, fbffffff]
[    1.145267] PCI: 0000:01:00.0 reg 10 64bit mmio: [fbef0000, fbefffff]
[    1.145407] PCI: bridge 0000:00:1c.2 32bit mmio: [f8000000, fbefffff]
[    1.145421] PCI: bridge 0000:00:1c.2 64bit mmio pref: [f0000000, f6ffffff]
[    1.145499] pci 0000:00:1e.0: transparent bridge
[    1.145622] bus 00 -> node 0
[    1.145649] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.146498] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    1.146842] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    1.147169] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    1.162087] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    1.163048] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.164005] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.164983] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    1.165927] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.166972] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.168073] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.169118] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    1.170218] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.170424] pnp: PnP ACPI init
[    1.170521] ACPI: bus type pnp registered
[    1.178555] pnp: PnP ACPI: found 13 devices
[    1.178648] ACPI: ACPI bus type pnp unregistered
[    1.179963] PCI: Using ACPI for IRQ routing
[    1.180361] NET: Registered protocol family 8
[    1.180361] NET: Registered protocol family 20
[    1.180396] NetLabel: Initializing
[    1.180480] NetLabel:  domain hash size = 128
[    1.180561] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.180686] NetLabel:  unlabeled traffic allowed by default
[    1.181118] hpet clockevent registered
[    1.181129] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.181348] hpet0: 3 64-bit timers, 14318180 Hz
[    1.183241] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.183332]    actual entries 65620
[    1.184067] Switched to high resolution mode on CPU 0
[    1.184201] AppArmor: AppArmor Filesystem Enabled
[    1.184329] ACPI: RTC can wake from S4
[    1.184586] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    1.184716] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.184809] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.184902] system 00:08: ioport range 0x480-0x4bf has been reserved
[    1.184996] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.186833] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[    1.186938] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.187035] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.187169] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    1.187272] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    1.187377] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    1.187471] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    1.187566] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    1.187661] system 00:0c: iomem range 0x100000-0x1f7fffff could not be reserved
[    1.224247] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    1.224345] pci 0000:00:1c.0:   IO window: disabled
[    1.224436] pci 0000:00:1c.0:   MEM window: disabled
[    1.224525] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.224619] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    1.224707] pci 0000:00:1c.1:   IO window: disabled
[    1.224798] pci 0000:00:1c.1:   MEM window: 0xfbf00000-0xfbffffff
[    1.224890] pci 0000:00:1c.1:   PREFETCH window: disabled
[    1.224984] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:01
[    1.225072] pci 0000:00:1c.2:   IO window: disabled
[    1.225162] pci 0000:00:1c.2:   MEM window: 0xf8000000-0xfbefffff
[    1.225255] pci 0000:00:1c.2:   PREFETCH window: 0x000000f0000000-0x000000f6ffffff
[    1.225387] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    1.225475] pci 0000:00:1e.0:   IO window: disabled
[    1.225563] pci 0000:00:1e.0:   MEM window: disabled
[    1.225651] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.225774] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.225872] pci 0000:00:1c.0: setting latency timer to 64
[    1.225893] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.225989] pci 0000:00:1c.1: setting latency timer to 64
[    1.226007] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.226104] pci 0000:00:1c.2: setting latency timer to 64
[    1.226119] pci 0000:00:1e.0: setting latency timer to 64
[    1.226130] bus: 00 index 0 io port: [0, ffff]
[    1.226213] bus: 00 index 1 mmio: [0, ffffffff]
[    1.226296] bus: 04 index 0 mmio: [0, 0]
[    1.226376] bus: 04 index 1 mmio: [0, 0]
[    1.226457] bus: 04 index 2 mmio: [0, 0]
[    1.226538] bus: 04 index 3 mmio: [0, 0]
[    1.226618] bus: 03 index 0 mmio: [0, 0]
[    1.226700] bus: 03 index 1 mmio: [fbf00000, fbffffff]
[    1.226785] bus: 03 index 2 mmio: [0, 0]
[    1.226865] bus: 03 index 3 mmio: [0, 0]
[    1.226945] bus: 01 index 0 mmio: [0, 0]
[    1.227026] bus: 01 index 1 mmio: [f8000000, fbefffff]
[    1.227112] bus: 01 index 2 mmio: [f0000000, f6ffffff]
[    1.227198] bus: 01 index 3 mmio: [0, 0]
[    1.227278] bus: 05 index 0 mmio: [0, 0]
[    1.227359] bus: 05 index 1 mmio: [0, 0]
[    1.227439] bus: 05 index 2 mmio: [0, 0]
[    1.227519] bus: 05 index 3 io port: [0, ffff]
[    1.227602] bus: 05 index 4 mmio: [0, ffffffff]
[    1.227712] NET: Registered protocol family 2
[    1.228236] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    1.228914] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    1.229253] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    1.229545] TCP: Hash tables configured (established 16384 bind 16384)
[    1.229641] TCP reno registered
[    1.229985] NET: Registered protocol family 1
[    1.230404] checking if image is initramfs... it is
[    3.267097] Freeing initrd memory: 7621k freed
[    3.269248] audit: initializing netlink socket (disabled)
[    3.269376] type=2000 audit(1236836946.268:1): initialized
[    3.288545] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.296224] VFS: Disk quotas dquot_6.5.1
[    3.296621] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.297593] msgmni has been set to 987
[    3.298121] io scheduler noop registered
[    3.298210] io scheduler anticipatory registered
[    3.298293] io scheduler deadline registered
[    3.298411] io scheduler cfq registered (default)
[    3.298530] pci 0000:00:02.0: Boot video device
[    3.298942] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    3.299006] pcieport-driver 0000:00:1c.0: found MSI capability
[    3.299165] pci_express 0000:00:1c.0:pcie00: allocate port service
[    3.299310] pci_express 0000:00:1c.0:pcie02: allocate port service
[    3.299452] pci_express 0000:00:1c.0:pcie03: allocate port service
[    3.299665] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    3.299726] pcieport-driver 0000:00:1c.1: found MSI capability
[    3.299869] pci_express 0000:00:1c.1:pcie00: allocate port service
[    3.300000] pci_express 0000:00:1c.1:pcie02: allocate port service
[    3.300166] pci_express 0000:00:1c.1:pcie03: allocate port service
[    3.300380] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    3.300438] pcieport-driver 0000:00:1c.2: found MSI capability
[    3.300582] pci_express 0000:00:1c.2:pcie00: allocate port service
[    3.300720] pci_express 0000:00:1c.2:pcie02: allocate port service
[    3.300846] pci_express 0000:00:1c.2:pcie03: allocate port service
[    3.456472] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.464105] brd: module loaded
[    3.464437] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.464954] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.497621] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.497721] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.499031] mice: PS/2 mouse device common for all mice
[    3.499900] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.500063] rtc0: alarms up to one month, hpet irqs
[    3.500286] cpuidle: using governor ladder
[    3.500370] cpuidle: using governor menu
[    3.501940] TCP cubic registered
[    3.502103] Using IPI No-Shortcut mode
[    3.503034] registered taskstats version 1
[    3.503399]   Magic number: 1:198:820
[    3.503672] tty ptyt0: hash matches
[    3.503892] rtc_cmos 00:03: setting system clock to 2009-03-12 05:49:07 UTC (1236836947)
[    3.504057] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.504148] EDD information not available.
[    3.504659] Freeing unused kernel memory: 332k freed
[    3.504933] Write protecting the kernel text: 2552k
[    3.505123] Write protecting the kernel read-only data: 928k
[    3.526422] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.891702] fuse init (API version 7.9)
[    3.960681] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.961088] processor ACPI0007:00: registered as cooling_device0
[    3.961187] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.969993] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    3.970188] Marking TSC unstable due to TSC halts in idle
[    3.988640] thermal LNXTHERM:01: registered as thermal_zone0
[    4.004778] ACPI: Thermal Zone [TZ00] (56 C)
[    5.697300] usbcore: registered new interface driver usbfs
[    5.697489] usbcore: registered new interface driver hub
[    5.697698] usbcore: registered new device driver usb
[    5.704672] USB Universal Host Controller Interface driver v3.0
[    5.704885] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.704994] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.705004] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.705211] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    5.705394] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e400
[    5.705941] usb usb1: configuration #1 chosen from 1 choice
[    5.706115] hub 1-0:1.0: USB hub found
[    5.706214] hub 1-0:1.0: 2 ports detected
[    5.907414] No dock devices found.
[    5.954270] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.954397] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.954407] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.954572] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    5.954755] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e480
[    5.955181] usb usb2: configuration #1 chosen from 1 choice
[    5.955349] hub 2-0:1.0: USB hub found
[    5.955447] hub 2-0:1.0: 2 ports detected
[    6.056711] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.056836] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    6.056847] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    6.057003] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    6.057184] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    6.057620] usb usb3: configuration #1 chosen from 1 choice
[    6.057792] hub 3-0:1.0: USB hub found
[    6.057893] hub 3-0:1.0: 2 ports detected
[    6.064093] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    6.064907] SCSI subsystem initialized
[    6.159549] libata version 3.00 loaded.
[    6.244965] usb 1-2: configuration #1 chosen from 1 choice
[    6.264728] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    6.264847] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    6.264857] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    6.265043] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    6.265227] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e880
[    6.265669] usb usb4: configuration #1 chosen from 1 choice
[    6.265841] hub 4-0:1.0: USB hub found
[    6.265941] hub 4-0:1.0: 2 ports detected
[    6.376166] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    6.472882] ata_piix 0000:00:1f.2: version 2.12
[    6.472923] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    6.473032] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    6.473339] ata_piix 0000:00:1f.2: setting latency timer to 64
[    6.476528] scsi0 : ata_piix
[    6.476947] scsi1 : ata_piix
[    6.482330] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    6.482432] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    6.539781] usb 3-1: configuration #1 chosen from 1 choice
[    6.652190] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    6.800821] usb 4-2: configuration #1 chosen from 1 choice
[    6.808490] ata2.00: ATA-4: SILICONMOTION SM223AC, , max UDMA/66
[    6.808593] ata2.00: 7815024 sectors, multi 0: LBA 
[    6.824460] ata2.00: configured for UDMA/66
[    6.824872] scsi 1:0:0:0: Direct-Access     ATA      SILICONMOTION SM n/a  PQ: 0 ANSI: 5
[    7.684411] usbcore: registered new interface driver hiddev
[    7.699892] input: B16_b_02 USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
[    7.720557] input,hidraw0: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
[    7.720899] usbcore: registered new interface driver usbhid
[    7.720993] usbhid: v2.6:USB HID core driver
[    7.740596] scsi 1:0:0:0: Attached scsi generic sg0 type 0
[    7.820234] usbcore: registered new interface driver libusual
[    7.875480] Initializing USB Mass Storage driver...
[    7.880629] scsi2 : SCSI emulation for USB Mass Storage devices
[    7.882161] usbcore: registered new interface driver usb-storage
[    7.882266] USB Mass Storage support registered.
[    7.882657] usb-storage: device found at 2
[    7.882665] usb-storage: waiting for device to settle before scanning
[    7.907835] Driver 'sd' needs updating - please use bus_type methods
[    7.908294] sd 1:0:0:0: [sda] 7815024 512-byte hardware sectors (4001 MB)
[    7.908438] sd 1:0:0:0: [sda] Write Protect is off
[    7.908525] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.908614] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    7.908954] sd 1:0:0:0: [sda] 7815024 512-byte hardware sectors (4001 MB)
[    7.909094] sd 1:0:0:0: [sda] Write Protect is off
[    7.909180] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.909266] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    7.909402]  sda: sda1 sda2 < sda5 >
[    7.911721] sd 1:0:0:0: [sda] Attached SCSI disk
[    8.199838] PM: Starting manual resume from disk
[    8.199937] PM: Resume from partition 8:5
[    8.199943] PM: Checking hibernation image.
[    8.200497] PM: Resume from disk failed.
[    8.261312] kjournald starting.  Commit interval 5 seconds
[    8.261448] EXT3-fs: mounted filesystem with ordered data mode.
[    8.680049] Clocksource tsc unstable (delta = -120794149 ns)
[   11.184505] udevd version 124 started
[   12.952074] usb-storage: device scan complete
[   12.955461] scsi 2:0:0:0: Direct-Access     USB2.0   CardReader SD0   0100 PQ: 0 ANSI: 0
[   13.355406] sd 2:0:0:0: [sdb] 3862528 512-byte hardware sectors (1978 MB)
[   13.358397] sd 2:0:0:0: [sdb] Write Protect is off
[   13.358494] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   13.358502] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   13.370402] sd 2:0:0:0: [sdb] 3862528 512-byte hardware sectors (1978 MB)
[   13.373442] sd 2:0:0:0: [sdb] Write Protect is off
[   13.373546] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   13.373555] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   13.373659]  sdb: sdb1
[   13.385033] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   13.385707] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   13.400363] Linux agpgart interface v0.103
[   13.660440] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.736436] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   13.736870] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   14.120045] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   14.120507] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.638534] intel_rng: FWH not detected
[   15.468404] iTCO_vendor_support: vendor-support=0
[   15.524384] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   15.524771] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
[   15.525219] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.597669] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   15.612088] ACPI: Power Button (FF) [PWRF]
[   15.612587] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   15.618603] ACPI: Lid Switch [LID]
[   15.618956] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   15.628039] ACPI: Sleep Button (CM) [SLPB]
[   15.628376] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   15.640036] ACPI: Power Button (CM) [PWRB]
[   15.836468] eeepc: Eee PC Hotkey Driver
[   15.836805] eeepc: Hotkey init flags 0x41
[   15.838283] eeepc: Get control methods supported: 0x101711
[   15.838609] input: Asus EeePC extra buttons as /devices/virtual/input/input7
[   17.876846] ACPI: AC Adapter [AC0] (on-line)
[   19.581285] Atheros(R) L2 Ethernet Driver - version 2.2.3
[   19.581387] Copyright (c) 2007 Atheros Corporation.
[   19.602204] atl2 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.602331] atl2 0000:03:00.0: setting latency timer to 64
[   19.865015] ACPI: Battery Slot [BAT0] (battery present)
[   19.866467] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16/input/input8
[   19.880091] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.094392] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.094575] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.100705] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   20.156126] ath5k_pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.156280] ath5k_pci 0000:01:00.0: setting latency timer to 64
[   20.156349] ath5k_pci 0000:01:00.0: registered as 'phy0'
[   20.160813] ath5k phy0: Support for RF2425 is under development.
[   20.209343] phy0: Selected rate control algorithm 'pid'
[   22.341755] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   22.644719] Linux video capture interface: v2.00
[   22.757339] uvcvideo: Found UVC 1.00 device <unnamed> (eb1a:2761)
[   22.767028] input: UVC Camera (eb1a:2761) as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2:1.0/input/input10
[   22.767263] usbcore: registered new interface driver uvcvideo
[   22.767423] USB Video Class driver (v0.1.0)
[   23.491801] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04753/0x200000
[   23.581857] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   82.736115] usb 1-2: USB disconnect, address 2
[  192.284793] lp: driver loaded but no devices found
[  192.420420] pciehp: HPC vendor_id 8086 device_id 2660 ss_vid 0 ss_did 0
[  192.420634] hpdriver 0000:00:1c.0:pcie02: service driver hpdriver loaded
[  192.423919] pciehp: HPC vendor_id 8086 device_id 2662 ss_vid 0 ss_did 0
[  193.428056] pciehp: Device 0000:03:00.0 already exists at 3:0, cannot hot-add
[  193.428169] pciehp: Cannot add device 0x3:0
[  194.432053] hpdriver 0000:00:1c.1:pcie02: service driver hpdriver loaded
[  194.432119] pciehp: HPC vendor_id 8086 device_id 2664 ss_vid 0 ss_did 0
[  195.436051] pciehp: Device 0000:01:00.0 already exists at 1:0, cannot hot-add
[  195.436167] pciehp: Cannot add device 0x1:0
[  196.440048] hpdriver 0000:00:1c.2:pcie02: service driver hpdriver loaded
[  196.440124] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[  196.658858] i801_smbus 0000:00:1f.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  196.659009] ACPI: I/O resource 0000:00:1f.3 [0x400-0x41f] conflicts with ACPI region SMRG [0x400-0x40f]
[  196.659145] ACPI: Device needs an ACPI driver
[  196.719537] i2c /dev entries driver
[  196.952145] Adding 224868k swap on /dev/sda5.  Priority:-1 extents:1 across:224868k
[  197.119876] EXT3 FS on sda1, internal journal
[  197.823606] type=1505 audit(1236837141.817:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3937
[  198.474732] type=1505 audit(1236837142.469:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3942
[  198.475590] type=1505 audit(1236837142.469:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3942
[  198.609258] ip_tables: (C) 2000-2006 Netfilter Core Team
[  200.322982] ACPI: WMI: Mapper loaded
[  202.146027] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  203.123151] ppdev: user-space parallel port driver
[  206.111439] sd 2:0:0:0: timing out command, waited 180s
[  206.111596] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  206.111609] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  206.111621] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  206.111637] end_request: I/O error, dev sdb, sector 3862512
[  206.111735] Buffer I/O error on device sdb, logical block 482814
[  209.196552] [drm] Initialized drm 1.1.0 20060810
[  209.213472] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  209.213503] pci 0000:00:02.0: setting latency timer to 64
[  209.217506] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  210.081934] NET: Registered protocol family 17
[  242.310523] wlan0: authenticate with AP 00:18:01:f3:ea:9c
[  242.312534] wlan0: authenticated
[  242.312555] wlan0: associate with AP 00:18:01:f3:ea:9c
[  242.315311] wlan0: RX AssocResp from 00:18:01:f3:ea:9c (capab=0x431 status=0 aid=1)
[  242.315328] wlan0: associated
[  247.759918] NET: Registered protocol family 10
[  247.764553] lo: Disabled Privacy Extensions
[  247.770614] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  258.148026] wlan0: no IPv6 routers present
[  268.284049] usb 1-2: new low speed USB device using uhci_hcd and address 3
[  268.490134] usb 1-2: configuration #1 chosen from 1 choice
[  268.516967] input: B16_b_02 USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input12
[  268.545082] input,hidraw0: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
[  386.119929] sd 2:0:0:0: timing out command, waited 180s
[  386.119962] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  386.119976] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  386.119988] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  386.120017] end_request: I/O error, dev sdb, sector 3862512
[  386.120032] Buffer I/O error on device sdb, logical block 482814
[  566.210865] sd 2:0:0:0: timing out command, waited 180s
[  566.210899] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  566.210912] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  566.210925] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  566.210940] end_request: I/O error, dev sdb, sector 3862512
[  566.210954] Buffer I/O error on device sdb, logical block 482814
[  746.215833] sd 2:0:0:0: timing out command, waited 180s
[  746.215866] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  746.215880] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  746.215892] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  746.215907] end_request: I/O error, dev sdb, sector 3862512
[  746.215921] Buffer I/O error on device sdb, logical block 482814
[  926.371932] sd 2:0:0:0: timing out command, waited 180s
[  926.371965] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  926.371978] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  926.371991] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  926.372020] end_request: I/O error, dev sdb, sector 3862512
[  926.372034] Buffer I/O error on device sdb, logical block 482814

```


I am very much a beginner, so I would greatly appreciate any and all simple explanations!

---

### Post by JohnnysR on 2009-06-12
Hello everyone!! I have exactly the same problem.. (9.04)

On boot it hangs after 'Synaptics..' and after about 2-3 minutes it shows the same "lp: driver loaded but...'

Everything works just fine (except some minor things) but it takes ages to boot.. 

Could someone please help us with this situation...

Thanks..

---

### Post by JohnnysR on 2009-06-15
Anyone to suggest something?

---

### Post by markDubai2009 on 2009-06-16
I seem to be suffering the same problem as the other people here.  I have a Dell XPS 1330M 2.0Ghz Intel 7100 with 2GB of memory with an NVIDIA graphics card.  I originally 8.04 working for a fair few months without issue on booting so had upgraded to 9.04.  Everything else seems ok.  If anybody has any question, please do not hesitate asking.

Tx in advance for the efforts.


Mark


Jun 15 22:10:12 ubuntu kernel: [   17.605839] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Jun 15 22:10:12 ubuntu kernel: [   17.610298] usbcore: registered new interface driver uvcvideo
Jun 15 22:10:12 ubuntu kernel: [   17.610302] USB Video Class driver (v0.1.0)
Jun 15 22:10:12 ubuntu kernel: [   17.723924] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jun 15 22:10:12 ubuntu kernel: [   17.724038] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun 15 22:10:12 ubuntu kernel: [   17.761108] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
Jun 15 22:10:12 ubuntu kernel: [   18.315872] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04753/0x200000
Jun 15 22:10:12 ubuntu kernel: [   18.352028] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
Jun 15 22:10:12 ubuntu kernel: [   18.773018] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x013f1c00
Jun 15 22:10:12 ubuntu kernel: [  108.468255] lp: driver loaded but no devices found
Jun 15 22:10:12 ubuntu kernel: [  108.596103] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
Jun 15 22:10:12 ubuntu kernel: [  109.127714] EXT3 FS on sda1, internal journal
Jun 15 22:10:12 ubuntu kernel: [  110.421339] type=1505 audit(1245089410.362:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2295
Jun 15 22:10:12 ubuntu kernel: [  110.830109] type=1505 audit(1245089410.770:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2299
Jun 15 22:10:12 ubuntu kernel: [  110.830183] type=1505 audit(1245089410.770:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2299
Jun 15 22:10:12 ubuntu kernel: [  110.830213] type=1505 audit(1245089410.770:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2299

---

### Post by markDubai2009 on 2009-06-18
poke poke

---

