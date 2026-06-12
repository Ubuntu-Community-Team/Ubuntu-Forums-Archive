---
title: "start-up delayed for 70 seconds"
date: 2009-05-20
forum: General Help
---

### Post by caole261188 on 2009-05-20
Hi everyone,

Yesterday, everything is normal. However after I have my voip service installed today (it's an analog phone with a router, so my desktop is behind 2 routers now),the start-up is painfully slow. I don't know if it's the cause of this problem.

From the dmesg command, I found out that there is a 70 seconds delay after vboxdrv and before BlueTooth is loaded. Please take a look and tell me if you can find any problem. Thanks in advance!

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-14-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Wed Apr 15 18:59:16 UTC 2009 (Ubuntu 2.6.27-14.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099c00 (usable)
[    0.000000]  BIOS-e820: 0000000000099c00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe90000 (usable)
[    0.000000]  BIOS-e820: 000000007fe90000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] last_pfn = 0x7fe90 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3782b000 - 37fefe83
[    0.000000] ACPI: RSDP 000F97A0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7FEE3080, 005C (r1 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEE7200, 00F4 (r3 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEE3200, 3FFC (r1 DELL   AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FE90000, 0040
[    0.000000] ACPI: HPET 7FEE73C0, 0038 (r1 DELL    FX09    42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 7FEE7400, 003C (r1 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: SLIC 7FEE7440, 0176 (r1 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: DMY2 7FEE75C0, 0080 (r1 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEE7300, 0084 (r1 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 7FEE7CA0, 0380 (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c39e0]    TEXT DATA BSS ==> [0000100000 - 00005c39e0]
[    0.000000]   #4 [003782b000 - 0037fefe83]          RAMDISK ==> [003782b000 - 0037fefe83]
[    0.000000]   #5 [00005c4000 - 00005c7000]    INIT_PG_TABLE ==> [00005c4000 - 00005c7000]
[    0.000000]   #6 [0000099c00 - 0000100000]    BIOS reserved ==> [0000099c00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f3f00] 000f3f00
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fe90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000099
[    0.000000]     0: 0x00000100 -> 0x0007fe90
[    0.000000] On node 0 totalpages: 523817
[    0.000000] free_area_init_node: node 0, pgdat c048c700, node_mem_map c1000000
[    0.000000]   DMA zone: 3957 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 291955 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
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
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 0000000000099000 - 000000000009a000
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519212
[    0.000000] Kernel command line: root=UUID=b8af9730-fab6-4585-be23-c9362e5ce8bf ro quiet splash vga=795 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2992.473 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2062148k/2095680k available (2578k kernel code, 32316k reserved, 1162k data, 428k init, 1178176k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0518000   ( 428 kB)
[    0.004000]       .data : 0xc0384a8a - 0xc04a7680   (1162 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0384a8a   (2578 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5984.94 BogoMIPS (lpj=11969892)
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
[    0.017348] ACPI: Core revision 20080609
[    0.018574] ACPI: Checking initramfs for custom DSDT
[    0.240185] ENABLING IO-APIC IRQs
[    0.240350] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.283425] CPU0: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
[    0.284017] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5984.98 BogoMIPS (lpj=11969974)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.368521] CPU1: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz stepping 0b
[    0.368532] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.372039] Brought up 2 CPUs
[    0.372041] Total of 2 processors activated (11969.93 BogoMIPS).
[    0.372058] CPU0 attaching sched-domain:
[    0.372060]  domain 0: span 0-1 level MC
[    0.372062]   groups: 0 1
[    0.372067] CPU1 attaching sched-domain:
[    0.372068]  domain 0: span 0-1 level MC
[    0.372069]   groups: 1 0
[    0.372125] net_namespace: 840 bytes
[    0.372125] Booting paravirtualized kernel on bare hardware
[    0.372199] Time: 23:26:07  Date: 05/20/09
[    0.372218] NET: Registered protocol family 16
[    0.372231] EISA bus registered
[    0.372231] ACPI: bus type pci registered
[    0.372231] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.372231] PCI: MCFG area at e0000000 reserved in E820
[    0.372231] PCI: Using MMCONFIG for extended config space
[    0.372231] PCI: Using configuration type 1 for base access
[    0.372231] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.372231] mtrr: probably your BIOS does not setup all CPUs.
[    0.372231] mtrr: corrected configuration.
[    0.372552] ACPI: EC: Look up EC in DSDT
[    0.378380] ACPI: Interpreter enabled
[    0.378384] ACPI: (supports S0 S3 S4 S5)
[    0.378394] ACPI: Using IOAPIC for interrupt routing
[    0.380779] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.380779] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.380779] pci 0000:00:01.0: PME# disabled
[    0.380779] PCI: 0000:00:19.0 reg 10 32bit mmio: [fdfc0000, fdfdffff]
[    0.380779] PCI: 0000:00:19.0 reg 14 32bit mmio: [fdfff000, fdffffff]
[    0.380779] PCI: 0000:00:19.0 reg 18 io port: [ff00, ff1f]
[    0.380779] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.380779] pci 0000:00:19.0: PME# disabled
[    0.380779] PCI: 0000:00:1a.0 reg 20 io port: [fe00, fe1f]
[    0.380779] PCI: 0000:00:1a.1 reg 20 io port: [fd00, fd1f]
[    0.380779] PCI: 0000:00:1a.2 reg 20 io port: [fc00, fc1f]
[    0.380779] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fdffe000, fdffe3ff]
[    0.380779] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.380779] pci 0000:00:1a.7: PME# disabled
[    0.380779] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fdff4000, fdff7fff]
[    0.380779] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.380779] pci 0000:00:1b.0: PME# disabled
[    0.380779] PCI: 0000:00:1d.0 reg 20 io port: [fb00, fb1f]
[    0.380779] PCI: 0000:00:1d.1 reg 20 io port: [fa00, fa1f]
[    0.380779] PCI: 0000:00:1d.2 reg 20 io port: [f900, f91f]
[    0.380779] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fdffd000, fdffd3ff]
[    0.380779] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.380779] pci 0000:00:1d.7: PME# disabled
[    0.380831] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.380834] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.380879] PCI: 0000:00:1f.2 reg 10 io port: [f800, f807]
[    0.380884] PCI: 0000:00:1f.2 reg 14 io port: [f700, f703]
[    0.380888] PCI: 0000:00:1f.2 reg 18 io port: [f600, f607]
[    0.380893] PCI: 0000:00:1f.2 reg 1c io port: [f500, f503]
[    0.380897] PCI: 0000:00:1f.2 reg 20 io port: [f400, f41f]
[    0.380901] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fdffc000, fdffc7ff]
[    0.380934] pci 0000:00:1f.2: PME# supported from D3hot
[    0.380937] pci 0000:00:1f.2: PME# disabled
[    0.380951] PCI: 0000:00:1f.3 reg 10 64bit mmio: [fdffb000, fdffb0ff]
[    0.380962] PCI: 0000:00:1f.3 reg 20 io port: [500, 51f]
[    0.380997] PCI: 0000:01:00.0 reg 10 64bit mmio: [d0000000, dfffffff]
[    0.381004] PCI: 0000:01:00.0 reg 18 64bit mmio: [fdef0000, fdefffff]
[    0.381008] PCI: 0000:01:00.0 reg 20 io port: [de00, deff]
[    0.381015] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.381034] pci 0000:01:00.0: supports D1
[    0.381035] pci 0000:01:00.0: supports D2
[    0.381053] PCI: 0000:01:00.1 reg 10 64bit mmio: [fdee0000, fdeeffff]
[    0.381083] pci 0000:01:00.1: supports D1
[    0.381084] pci 0000:01:00.1: supports D2
[    0.381113] PCI: bridge 0000:00:01.0 io port: [d000, dfff]
[    0.381115] PCI: bridge 0000:00:01.0 32bit mmio: [fde00000, fdefffff]
[    0.381118] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.381157] pci 0000:00:1e.0: transparent bridge
[    0.381160] PCI: bridge 0000:00:1e.0 io port: [c000, cfff]
[    0.381163] PCI: bridge 0000:00:1e.0 32bit mmio: [fdd00000, fddfffff]
[    0.381167] PCI: bridge 0000:00:1e.0 64bit mmio pref: [fdc00000, fdcfffff]
[    0.381175] bus 00 -> node 0
[    0.381180] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.381384] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.392710] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.392710] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.392710] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.392710] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.392710] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.392710] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.392710] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.392744] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[    0.392788] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.392788] pnp: PnP ACPI init
[    0.392788] ACPI: bus type pnp registered
[    0.396365] pnp: PnP ACPI: found 12 devices
[    0.396365] ACPI: ACPI bus type pnp unregistered
[    0.396365] PnPBIOS: Disabled by ACPI PNP
[    0.396365] PCI: Using ACPI for IRQ routing
[    0.404033] NET: Registered protocol family 8
[    0.404036] NET: Registered protocol family 20
[    0.404053] NetLabel: Initializing
[    0.404053] NetLabel:  domain hash size = 128
[    0.404053] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.404056] NetLabel:  unlabeled traffic allowed by default
[    0.404062] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.404067] hpet0: 4 64-bit timers, 14318180 Hz
[    0.405655] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.405657]    actual entries 65620
[    0.405709] AppArmor: AppArmor Filesystem Enabled
[    0.405725] ACPI: RTC can wake from S4
[    0.412063] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.412066] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.412069] system 00:01: ioport range 0x290-0x297 has been reserved
[    0.412072] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.412082] system 00:08: ioport range 0x400-0x4bf could not be reserved
[    0.412088] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.412094] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    0.412097] system 00:0b: iomem range 0x7ff00000-0x7fffffff has been reserved
[    0.412101] system 00:0b: iomem range 0xfed00000-0xfed000ff could not be reserved
[    0.412104] system 00:0b: iomem range 0x7fe90000-0x7fefffff could not be reserved
[    0.412106] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.412109] system 00:0b: iomem range 0x100000-0x7fe8ffff could not be reserved
[    0.412113] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.412116] system 00:0b: iomem range 0xfed14000-0xfed1dfff could not be reserved
[    0.412119] system 00:0b: iomem range 0xfed20000-0xfed9ffff could not be reserved
[    0.412122] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.412125] system 00:0b: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.412128] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.412131] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[    0.447019] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.447021] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.447024] pci 0000:00:01.0:   MEM window: 0xfde00000-0xfdefffff
[    0.447027] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.447030] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.447032] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.447036] pci 0000:00:1e.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.447039] pci 0000:00:1e.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.447048] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.447051] pci 0000:00:01.0: setting latency timer to 64
[    0.447055] pci 0000:00:1e.0: setting latency timer to 64
[    0.447058] bus: 00 index 0 io port: [0, ffff]
[    0.447059] bus: 00 index 1 mmio: [0, ffffffff]
[    0.447060] bus: 01 index 0 io port: [d000, dfff]
[    0.447062] bus: 01 index 1 mmio: [fde00000, fdefffff]
[    0.447063] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.447065] bus: 01 index 3 mmio: [0, 0]
[    0.447066] bus: 02 index 0 io port: [c000, cfff]
[    0.447067] bus: 02 index 1 mmio: [fdd00000, fddfffff]
[    0.447069] bus: 02 index 2 mmio: [fdc00000, fdcfffff]
[    0.447070] bus: 02 index 3 io port: [0, ffff]
[    0.447071] bus: 02 index 4 mmio: [0, ffffffff]
[    0.447077] NET: Registered protocol family 2
[    0.460165] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.460366] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.460597] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.460723] TCP: Hash tables configured (established 131072 bind 65536)
[    0.460726] TCP reno registered
[    0.468210] NET: Registered protocol family 1
[    0.468310] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[    0.504155] Switched to high resolution mode on CPU 0
[    0.991492]  it is
[    1.226295] Freeing initrd memory: 7955k freed
[    1.227033] audit: initializing netlink socket (disabled)
[    1.227051] type=2000 audit(1242861967.224:1): initialized
[    1.230426] highmem bounce pool size: 64 pages
[    1.230430] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.231895] VFS: Disk quotas dquot_6.5.1
[    1.231949] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.232017] msgmni has been set to 1743
[    1.232097] io scheduler noop registered
[    1.232099] io scheduler anticipatory registered
[    1.232101] io scheduler deadline registered
[    1.232108] io scheduler cfq registered (default)
[    1.232216] pci 0000:01:00.0: Boot video device
[    1.232283] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.232306] pcieport-driver 0000:00:01.0: found MSI capability
[    1.232328] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.232353] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.232549] isapnp: Scanning for PnP cards...
[    1.585297] isapnp: No Plug & Play device found
[    1.605518] hpet_resources: 0xfed00000 is busy
[    1.605569] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.606903] brd: module loaded
[    1.606945] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.607051] PNP: No PS/2 controller found. Probing ports directly.
[    1.607334] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.607337] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.608614] mice: PS/2 mouse device common for all mice
[    1.608725] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.608752] rtc0: alarms up to one month, hpet irqs
[    1.608825] EISA: Probing bus 0 at eisa.0
[    1.608846] EISA: Detected 0 cards.
[    1.608848] cpuidle: using governor ladder
[    1.608850] cpuidle: using governor menu
[    1.609174] TCP cubic registered
[    1.609192] Using IPI No-Shortcut mode
[    1.609297] registered taskstats version 1
[    1.609365]   Magic number: 9:312:454
[    1.609426] rtc_cmos 00:04: setting system clock to 2009-05-20 23:26:08 UTC (1242861968)
[    1.609428] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.609429] EDD information not available.
[    1.609562] Freeing unused kernel memory: 428k freed
[    1.609586] Write protecting the kernel text: 2580k
[    1.609603] Write protecting the kernel read-only data: 940k
[    1.665299] vesafb: framebuffer at 0xd0000000, mapped to 0xf8880000, using 10240k, total 16384k
[    1.665302] vesafb: mode is 1280x1024x32, linelength=5120, pages=2
[    1.665303] vesafb: protected mode interface info at c000:a104
[    1.665305] vesafb: pmi: set display start = c00ca192, set palette = c00ca254
[    1.665306] vesafb: scrolling: redraw
[    1.665308] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.665422] Console: switching to colour frame buffer device 160x64
[    1.697217] fb0: VESA VGA frame buffer device
[    1.806518] fuse init (API version 7.9)
[    1.814463] fan PNP0C0B:00: registered as cooling_device0
[    1.814468] ACPI: Fan [FAN] (on)
[    1.819605] ACPI: SSDT 7FEE7680, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[    1.819790] processor ACPI0007:00: registered as cooling_device1
[    1.819923] ACPI: SSDT 7FEE7B40, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[    1.820099] processor ACPI0007:01: registered as cooling_device2
[    1.821857] thermal LNXTHERM:01: registered as thermal_zone0
[    1.822066] ACPI: Thermal Zone [THRM] (40 C)
[    1.946275] usbcore: registered new interface driver usbfs
[    1.946294] usbcore: registered new interface driver hub
[    1.949346] usbcore: registered new device driver usb
[    1.949402] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    1.949404] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.949434] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.949441] e1000e 0000:00:19.0: setting latency timer to 64
[    1.970493] USB Universal Host Controller Interface driver v3.0
[    2.013610] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.028127] FDC 0 is a post-1991 82077
[    2.032163] No dock devices found.
[    2.043396] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1d:09:76:dc:58
[    2.043398] 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
[    2.043419] 0000:00:19.0: eth0: MAC: 5, PHY: 7, PBA No: ffffff-0ff
[    2.043452] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.043458] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.043461] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.043487] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.043513] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000fe00
[    2.043616] usb usb1: configuration #1 chosen from 1 choice
[    2.043634] hub 1-0:1.0: USB hub found
[    2.043638] hub 1-0:1.0: 2 ports detected
[    2.049113] SCSI subsystem initialized
[    2.060032] libata version 3.00 loaded.
[    2.144738] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.144746] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.144749] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.144765] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.144791] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fd00
[    2.144852] usb usb2: configuration #1 chosen from 1 choice
[    2.144870] hub 2-0:1.0: USB hub found
[    2.144874] hub 2-0:1.0: 2 ports detected
[    2.248716] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.248725] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.248728] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.248754] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.248781] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fc00
[    2.248841] usb usb3: configuration #1 chosen from 1 choice
[    2.248858] hub 3-0:1.0: USB hub found
[    2.248862] hub 3-0:1.0: 2 ports detected
[    2.456144] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.456156] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.456160] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.456186] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.460084] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.460091] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdffe000
[    2.472018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.472092] usb usb4: configuration #1 chosen from 1 choice
[    2.472119] hub 4-0:1.0: USB hub found
[    2.472125] hub 4-0:1.0: 6 ports detected
[    2.680131] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.680137] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.680140] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.680164] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.680189] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fb00
[    2.680262] usb usb5: configuration #1 chosen from 1 choice
[    2.680278] hub 5-0:1.0: USB hub found
[    2.680282] hub 5-0:1.0: 2 ports detected
[    2.784650] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.784656] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.784659] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.784680] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.784701] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fa00
[    2.784778] usb usb6: configuration #1 chosen from 1 choice
[    2.784796] hub 6-0:1.0: USB hub found
[    2.784799] hub 6-0:1.0: 2 ports detected
[    2.888643] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.888649] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.888653] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.888674] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.888694] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f900
[    2.888770] usb usb7: configuration #1 chosen from 1 choice
[    2.888786] hub 7-0:1.0: USB hub found
[    2.888790] hub 7-0:1.0: 2 ports detected
[    3.096133] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.096140] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.096144] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.096167] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.100070] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.100073] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffd000
[    3.124031] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    3.136019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.136085] usb usb8: configuration #1 chosen from 1 choice
[    3.136110] hub 8-0:1.0: USB hub found
[    3.136116] hub 8-0:1.0: 6 ports detected
[    3.310077] usb 3-1: configuration #1 chosen from 1 choice
[    3.345041] ahci 0000:00:1f.2: version 3.0
[    3.345050] ahci 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.345133] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    3.345136] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part ems 
[    3.345139] ahci 0000:00:1f.2: setting latency timer to 64
[    3.345457] scsi0 : ahci
[    3.345655] scsi1 : ahci
[    3.345701] scsi2 : ahci
[    3.345745] scsi3 : ahci
[    3.345969] scsi4 : ahci
[    3.346072] scsi5 : ahci
[    3.346157] ata1: SATA max UDMA/133 abar m2048@0xfdffc000 port 0xfdffc100 irq 222
[    3.346159] ata2: SATA max UDMA/133 abar m2048@0xfdffc000 port 0xfdffc180 irq 222
[    3.346161] ata3: SATA max UDMA/133 abar m2048@0xfdffc000 port 0xfdffc200 irq 222
[    3.346163] ata4: SATA max UDMA/133 abar m2048@0xfdffc000 port 0xfdffc280 irq 222
[    3.346165] ata5: SATA max UDMA/133 abar m2048@0xfdffc000 port 0xfdffc300 irq 222
[    3.346167] ata6: SATA max UDMA/133 abar m2048@0xfdffc000 port 0xfdffc380 irq 222
[    3.552020] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    3.720089] usb 3-2: configuration #1 chosen from 1 choice
[    3.828049] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.868692] ata1.00: ATA-7: ST3500630AS, 3.ADG, max UDMA/133
[    3.868695] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.927007] ata1.00: configured for UDMA/133
[    4.088533] usb 8-5: new high speed USB device using ehci_hcd and address 2
[    4.298490] usb 8-5: configuration #1 chosen from 1 choice
[    4.408041] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.408575] usbcore: registered new interface driver hiddev
[    4.408780] usbcore: registered new interface driver libusual
[    4.409746] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GSA-H73N, B103, max UDMA/100
[    4.411829] ata2.00: configured for UDMA/100
[    4.412831] Initializing USB Mass Storage driver...
[    4.648519] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    4.728033] ata3: SATA link down (SStatus 0 SControl 300)
[    4.827820] usb 7-2: configuration #1 chosen from 1 choice
[    4.830767] hub 7-2:1.0: USB hub found
[    4.832739] hub 7-2:1.0: 3 ports detected
[    5.048034] ata4: SATA link down (SStatus 0 SControl 300)
[    5.064072] input: Darfon USB Combo Keyboard as /devices/pci0000:00/0000:00:1a.2/usb3/3-1/3-1:1.0/input/input1
[    5.064198] input,hidraw0: USB HID v1.00 Keyboard [Darfon USB Combo Keyboard] on usb-0000:00:1a.2-1
[    5.099883] input: Darfon USB Combo Keyboard as /devices/pci0000:00/0000:00:1a.2/usb3/3-1/3-1:1.1/input/input2
[    5.100092] input,hiddev96,hidraw1: USB HID v1.00 Device [Darfon USB Combo Keyboard] on usb-0000:00:1a.2-1
[    5.100151] scsi6 : SCSI emulation for USB Mass Storage devices
[    5.100196] usb-storage: device found at 2
[    5.100197] usb-storage: waiting for device to settle before scanning
[    5.121747] usb 7-2.1: new full speed USB device using uhci_hcd and address 3
[    5.259812] usb 7-2.1: configuration #1 chosen from 1 choice
[    5.337750] usb 7-2.2: new full speed USB device using uhci_hcd and address 4
[    5.368526] ata5: SATA link down (SStatus 0 SControl 300)
[    5.489005] usb 7-2.2: configuration #1 chosen from 1 choice
[    5.569750] usb 7-2.3: new full speed USB device using uhci_hcd and address 5
[    5.688014] ata6: SATA link down (SStatus 0 SControl 300)
[    5.688112] scsi 0:0:0:0: Direct-Access     ATA      ST3500630AS      3.AD PQ: 0 ANSI: 5
[    5.688216] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.689647] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-H73N B103 PQ: 0 ANSI: 5
[    5.689737] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.703626] Driver 'sd' needs updating - please use bus_type methods
[    5.703688] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.703699] sd 0:0:0:0: [sda] Write Protect is off
[    5.703701] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.703718] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.703765] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.703774] sd 0:0:0:0: [sda] Write Protect is off
[    5.703776] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.703792] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.703795]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.721848] usb 7-2.3: configuration #1 chosen from 1 choice
[    5.724245]  sda1 sda2 sda3 sda4
[    5.733801] input: Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input3
[    5.735807] input,hidraw2: USB HID v1.11 Keyboard [Logitech BT Mini-Receiver] on usb-0000:00:1d.2-2.2
[    5.740140] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.744819] input: Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input4
[    5.745085] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    5.745087] Uniform CD-ROM driver Revision: 3.20
[    5.745136] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.757817] input,hiddev97,hidraw3: USB HID v1.11 Mouse [Logitech BT Mini-Receiver] on usb-0000:00:1d.2-2.3
[    5.757852] usbcore: registered new interface driver usbhid
[    5.757856] usbcore: registered new interface driver usb-storage
[    5.757859] usbhid: v2.6:USB HID core driver
[    5.757862] USB Mass Storage support registered.
[    5.990455] PM: Starting manual resume from disk
[    5.990458] PM: Resume from partition 8:3
[    5.990459] PM: Checking hibernation image.
[    5.990587] PM: Resume from disk failed.
[    6.017683] kjournald starting.  Commit interval 5 seconds
[    6.017689] EXT3-fs: mounted filesystem with ordered data mode.
[   10.105825] usb-storage: device scan complete
[   10.109941] scsi 6:0:0:0: Direct-Access     DELL     USB   HS-CF Card 7.00 PQ: 0 ANSI: 0
[   10.113939] scsi 6:0:0:1: Direct-Access     DELL     USB   HS-xD/SM   7.00 PQ: 0 ANSI: 0
[   10.117690] scsi 6:0:0:2: Direct-Access     DELL     USB   HS-MS Card 7.00 PQ: 0 ANSI: 0
[   10.120939] scsi 6:0:0:3: Direct-Access     DELL     USB   HS-SD Card 7.00 PQ: 0 ANSI: 0
[   10.125495] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   10.125594] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   10.130105] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[   10.130152] sd 6:0:0:1: Attached scsi generic sg3 type 0
[   10.134976] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[   10.135023] sd 6:0:0:2: Attached scsi generic sg4 type 0
[   10.183979] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   10.184036] sd 6:0:0:3: Attached scsi generic sg5 type 0
[   13.130135] udevd version 124 started
[   13.407594] Linux agpgart interface v0.103
[   13.422795] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.456831] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.497942] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   13.524027] ACPI: Power Button (FF) [PWRF]
[   13.524093] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   13.536573] iTCO_vendor_support: vendor-support=0
[   13.552017] ACPI: Power Button (CM) [PWRB]
[   13.565701] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.573221] iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0460)
[   13.573309] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.001650] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.001669] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.017227] Bluetooth: Core ver 2.13
[   14.029299] NET: Registered protocol family 31
[   14.029301] Bluetooth: HCI device and connection manager initialized
[   14.029304] Bluetooth: HCI socket layer initialized
[   14.063590] input: Wacom Bamboo as /devices/pci0000:00/0000:00:1a.2/usb3/3-2/3-2:1.0/input/input7
[   14.084376] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   14.092942] usbcore: registered new interface driver wacom
[   14.092955] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
[   14.093228] usbcore: registered new interface driver btusb
[   14.312233] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   14.468312] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.970158] lp: driver loaded but no devices found
[   15.071152] Adding 6827616k swap on /dev/sda3.  Priority:-1 extents:1 across:6827616k
[   15.598967] EXT3 FS on sda2, internal journal
[   16.341157] kjournald starting.  Commit interval 5 seconds
[   16.341354] EXT3 FS on sda1, internal journal
[   16.341357] EXT3-fs: mounted filesystem with ordered data mode.
[   16.547625] type=1505 audit(1242861983.671:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4348
[   16.654664] type=1505 audit(1242861983.779:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4353
[   16.654780] type=1505 audit(1242861983.779:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4353
[   16.698938] type=1505 audit(1242861983.822:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4357
[   16.789483] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.205233] ACPI: WMI: Mapper loaded
[   17.932868] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.695028] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   19.695032] apm: disabled - APM is not SMP safe.
[   20.072235] ppdev: user-space parallel port driver
[   27.419059] NET: Registered protocol family 10
[   27.419937] lo: Disabled Privacy Extensions
[   35.872287] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   35.872292] vboxdrv: Successfully done.
[   35.872294] vboxdrv: Found 2 processor cores.
[   35.873697] vboxdrv: fAsync=0 offMin=0x318 offMax=0x1935
[   35.874176] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   35.874180] vboxdrv: Successfully loaded version 2.2.0 (interface 0x000a0009).
[  100.533272] Bluetooth: L2CAP ver 2.11
[  100.533278] Bluetooth: L2CAP socket layer initialized
[  100.546789] Bluetooth: SCO (Voice Link) ver 0.6
[  100.546794] Bluetooth: SCO socket layer initialized
[  100.562402] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  100.562406] Bluetooth: BNEP filters: protocol multicast
[  100.585070] Bridge firewalling registered
[  100.719046] Bluetooth: RFCOMM socket layer initialized
[  100.719243] Bluetooth: RFCOMM TTY layer initialized
[  100.719247] Bluetooth: RFCOMM ver 1.10
[  102.132783] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  102.160864] [fglrx] Maximum main memory to use for locked dma buffers: 1895 MBytes.
[  102.161177] [fglrx]   vendor: 1002 device: 7183 count: 1
[  102.161917] [fglrx] ioport: bar 4, base 0xde00, size: 0x100
[  102.161929] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  102.161934] pci 0000:01:00.0: setting latency timer to 64
[  102.164076] [fglrx] Driver built-in PAT support is enabled successfully
[  102.164107] [fglrx] module loaded - fglrx 8.59.2 [Mar 13 2009] with 1 minors
[  104.936260] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  105.240015] [fglrx] Firegl kernel thread PID: 7025
[  105.240834] [fglrx] Gart USWC size:947 M.
[  105.240836] [fglrx] Gart cacheable size:60 M.
[  105.240841] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  105.240843] [fglrx] Reserved FB block: Unshared offset:fefa000, size:101000 
[  105.240845] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[  106.616760] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  106.616766] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  106.618090] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  106.848582] NET: Registered protocol family 17
[  117.428011] eth0: no IPv6 routers present
```

---

### Post by kerry_s on 2009-05-20
try disabling apparmor, see if thats causing it.

---

