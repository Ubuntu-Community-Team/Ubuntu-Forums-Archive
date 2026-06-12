---
title: "Only two cores of Quad Core active"
date: 2009-03-19
forum: General Help
---

### Post by CabbageCake on 2009-03-19
Having trouble getting Ubuntu to ativate all the cores of my Intel Core 2 Quad Q8200. The problem only started occurring yesterday; I only have two active CPUs on my system at present.

dmesg shows the following:

```

[    0.440037] Total of 2 processors activated (9333.14 BogoMIPS).

```

I'm running kernel 2.6.27-11:

```

Linux bunty 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

```

Would be really grateful for any help!

Here is my dmesg:


```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
[    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cbfb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cbfb0000 - 00000000cbfc0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cbfc0000 - 00000000cbff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cbff0000 - 00000000cc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xcbfb0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3782b000 - 37fef17b
[    0.000000] ACPI: RSDP 000FA150, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CBFB0000, 003C (r1 062608 RSDT2004 20080626 MSFT       97)
[    0.000000] ACPI: FACP CBFB0200, 0084 (r1 A M I  OEMFACP  12000601 MSFT       97)
[    0.000000] ACPI: DSDT CBFB0440, 57CC (r1  ASR74 ASR74132      132 INTL 20051117)
[    0.000000] ACPI: FACS CBFC0000, 0040
[    0.000000] ACPI: APIC CBFB0390, 006C (r1 062608 APIC2004 20080626 MSFT       97)
[    0.000000] ACPI: MCFG CBFB0400, 003C (r1 062608 OEMMCFG  20080626 MSFT       97)
[    0.000000] ACPI: OEMB CBFC0040, 0071 (r1 062608 OEMB2004 20080626 MSFT       97)
[    0.000000] ACPI: HPET CBFB5C10, 0038 (r1 062608 OEMHPET  20080626 MSFT       97)
[    0.000000] ACPI: SSDT CBFC09E0, 0A7C (r1 DpgPmm    CpuPm       12 INTL 20051117)
[    0.000000] 2367MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003782b000 - 0037fef17b]          RAMDISK ==> [003782b000 - 0037fef17b]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009ac00 - 0000100000]    BIOS reserved ==> [000009ac00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000cbfb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x000cbfb0
[    0.000000] On node 0 totalpages: 835386
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3942 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 600800 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 3, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cc000000:32e00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 828042
[    0.000000] Kernel command line: root=UUID=c3e2b2f8-21ea-4eb2-9d2b-c1f3f01c5cf6 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2333.289 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 3297420k/3342016k available (2576k kernel code, 43272k reserved, 1165k data, 424k init, 2424512k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4666.57 BogoMIPS (lpj=9333156)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017683] ACPI: Core revision 20080609
[    0.019506] ACPI: Checking initramfs for custom DSDT
[    0.308192] ENABLING IO-APIC IRQs
[    0.308358] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.349470] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.352022] Booting processor 1/2 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4666.56 BogoMIPS (lpj=9333126)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.436450] CPU1: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.436462] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.440035] Brought up 2 CPUs
[    0.440037] Total of 2 processors activated (9333.14 BogoMIPS).
[    0.440056] CPU0 attaching sched-domain:
[    0.440058]  domain 0: span 0-1 level CPU
[    0.440060]   groups: 0 1
[    0.440065] CPU1 attaching sched-domain:
[    0.440066]  domain 0: span 0-1 level CPU
[    0.440068]   groups: 1 0
[    0.440116] net_namespace: 840 bytes
[    0.440116] Booting paravirtualized kernel on bare hardware
[    0.440238] Time:  9:33:21  Date: 03/19/09
[    0.440261] NET: Registered protocol family 16
[    0.440277] EISA bus registered
[    0.440277] ACPI: bus type pci registered
[    0.440277] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.440277] PCI: Not using MMCONFIG.
[    0.440277] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.440277] PCI: Using configuration type 1 for base access
[    0.440794] ACPI: EC: Look up EC in DSDT
[    0.452012] ACPI: Interpreter enabled
[    0.452017] ACPI: (supports S0 S1 S3 S4 S5)
[    0.452042] ACPI: Using IOAPIC for interrupt routing
[    0.452095] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.456539] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.456541] PCI: Using MMCONFIG for extended config space
[    0.465470] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.465470] PCI: 0000:00:1a.0 reg 20 io port: [c800, c81f]
[    0.465470] PCI: 0000:00:1a.1 reg 20 io port: [c880, c89f]
[    0.465470] PCI: 0000:00:1a.2 reg 20 io port: [cc00, cc1f]
[    0.465470] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fbdffc00, fbdfffff]
[    0.465470] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.465470] pci 0000:00:1a.7: PME# disabled
[    0.465470] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fbdf8000, fbdfbfff]
[    0.465470] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.465470] pci 0000:00:1b.0: PME# disabled
[    0.465470] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.465470] pci 0000:00:1c.0: PME# disabled
[    0.465470] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.465470] pci 0000:00:1c.4: PME# disabled
[    0.465470] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.465470] pci 0000:00:1c.5: PME# disabled
[    0.465470] PCI: 0000:00:1d.0 reg 20 io port: [c080, c09f]
[    0.465470] PCI: 0000:00:1d.1 reg 20 io port: [c400, c41f]
[    0.465470] PCI: 0000:00:1d.2 reg 20 io port: [c480, c49f]
[    0.465470] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fbdff800, fbdffbff]
[    0.465470] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.465470] pci 0000:00:1d.7: PME# disabled
[    0.465470] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.465470] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.465470] PCI: 0000:00:1f.2 reg 10 io port: [b000, b007]
[    0.465470] PCI: 0000:00:1f.2 reg 14 io port: [ac00, ac03]
[    0.465470] PCI: 0000:00:1f.2 reg 18 io port: [a880, a887]
[    0.465470] PCI: 0000:00:1f.2 reg 1c io port: [a800, a803]
[    0.465470] PCI: 0000:00:1f.2 reg 20 io port: [a480, a48f]
[    0.465470] PCI: 0000:00:1f.2 reg 24 io port: [a400, a40f]
[    0.465470] PCI: 0000:00:1f.3 reg 10 64bit mmio: [fbdff400, fbdff4ff]
[    0.465470] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.465470] PCI: 0000:00:1f.5 reg 10 io port: [c000, c007]
[    0.465470] PCI: 0000:00:1f.5 reg 14 io port: [bc00, bc03]
[    0.465470] PCI: 0000:00:1f.5 reg 18 io port: [b880, b887]
[    0.465470] PCI: 0000:00:1f.5 reg 1c io port: [b800, b803]
[    0.465470] PCI: 0000:00:1f.5 reg 20 io port: [b480, b48f]
[    0.465470] PCI: 0000:00:1f.5 reg 24 io port: [b400, b40f]
[    0.465470] PCI: 0000:03:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.465470] PCI: 0000:03:00.0 reg 14 64bit mmio: [d0000000, dfffffff]
[    0.465470] PCI: 0000:03:00.0 reg 1c 64bit mmio: [fc000000, fcffffff]
[    0.465470] PCI: 0000:03:00.0 reg 30 32bit mmio: [febe0000, febfffff]
[    0.465470] PCI: bridge 0000:00:1c.0 32bit mmio: [fc000000, febfffff]
[    0.465470] PCI: bridge 0000:00:1c.0 64bit mmio pref: [d0000000, dfffffff]
[    0.468031] PCI: 0000:02:00.0 reg 10 io port: [ec00, ec07]
[    0.468039] PCI: 0000:02:00.0 reg 14 io port: [e880, e883]
[    0.468047] PCI: 0000:02:00.0 reg 18 io port: [e800, e807]
[    0.468056] PCI: 0000:02:00.0 reg 1c io port: [e480, e483]
[    0.468064] PCI: 0000:02:00.0 reg 20 io port: [e400, e40f]
[    0.468078] PCI: 0000:02:00.0 reg 30 32bit mmio: [fbff0000, fbffffff]
[    0.468132] PCI: bridge 0000:00:1c.4 io port: [e000, efff]
[    0.468135] PCI: bridge 0000:00:1c.4 32bit mmio: [fbf00000, fbffffff]
[    0.468179] PCI: 0000:01:00.0 reg 10 io port: [d800, d8ff]
[    0.468197] PCI: 0000:01:00.0 reg 18 64bit mmio: [cffff000, cfffffff]
[    0.468210] PCI: 0000:01:00.0 reg 20 64bit mmio: [cffe0000, cffeffff]
[    0.468217] PCI: 0000:01:00.0 reg 30 32bit mmio: [fbef0000, fbefffff]
[    0.468243] pci 0000:01:00.0: supports D1
[    0.468244] pci 0000:01:00.0: supports D2
[    0.468246] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.468250] pci 0000:01:00.0: PME# disabled
[    0.468278] PCI: bridge 0000:00:1c.5 io port: [d000, dfff]
[    0.468281] PCI: bridge 0000:00:1c.5 32bit mmio: [fbe00000, fbefffff]
[    0.468286] PCI: bridge 0000:00:1c.5 64bit mmio pref: [cff00000, cfffffff]
[    0.468327] pci 0000:00:1e.0: transparent bridge
[    0.468349] bus 00 -> node 0
[    0.468355] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.468590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.468784] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.468896] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.469003] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.484945] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.484945] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.484945] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.484945] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.484945] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.484945] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.484945] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.485022] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.485080] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 93, should be 84 [20080609]
[    0.485080] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.485080] pnp: PnP ACPI init
[    0.485080] ACPI: bus type pnp registered
[    0.492412] pnp: PnP ACPI: found 18 devices
[    0.492412] ACPI: ACPI bus type pnp unregistered
[    0.492412] PnPBIOS: Disabled by ACPI PNP
[    0.492412] PCI: Using ACPI for IRQ routing
[    0.500042] NET: Registered protocol family 8
[    0.500044] NET: Registered protocol family 20
[    0.500059] NetLabel: Initializing
[    0.500060] NetLabel:  domain hash size = 128
[    0.500062] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.500072] NetLabel:  unlabeled traffic allowed by default
[    0.500078] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.500082] hpet0: 4 64-bit timers, 14318180 Hz
[    0.501847] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.501849]    actual entries 65620
[    0.501914] AppArmor: AppArmor Filesystem Enabled
[    0.501930] ACPI: RTC can wake from S4
[    0.504037] Switched to high resolution mode on CPU 0
[    0.504486] Switched to high resolution mode on CPU 1
[    0.508020] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.508023] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved
[    0.508032] system 00:09: ioport range 0x280-0x28f has been reserved
[    0.508034] system 00:09: ioport range 0x290-0x29f has been reserved
[    0.508039] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.508042] system 00:0a: ioport range 0x800-0x87f has been reserved
[    0.508044] system 00:0a: ioport range 0x480-0x4bf has been reserved
[    0.508046] system 00:0a: ioport range 0x900-0x90f has been reserved
[    0.508049] system 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.508052] system 00:0a: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.508058] system 00:0d: iomem range 0xffc00000-0xfff7ffff could not be reserved
[    0.508063] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.508065] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.508070] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[    0.508075] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.508078] system 00:11: iomem range 0xc0000-0xcffff could not be reserved
[    0.508080] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[    0.508083] system 00:11: iomem range 0x100000-0xcbffffff could not be reserved
[    0.543087] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    0.543089] pci 0000:00:1c.0:   IO window: disabled
[    0.543094] pci 0000:00:1c.0:   MEM window: 0xfc000000-0xfebfffff
[    0.543097] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.543103] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:02
[    0.543105] pci 0000:00:1c.4:   IO window: 0xe000-0xefff
[    0.543109] pci 0000:00:1c.4:   MEM window: 0xfbf00000-0xfbffffff
[    0.543113] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.543118] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:01
[    0.543120] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
[    0.543124] pci 0000:00:1c.5:   MEM window: 0xfbe00000-0xfbefffff
[    0.543128] pci 0000:00:1c.5:   PREFETCH window: 0x000000cff00000-0x000000cfffffff
[    0.543133] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.543135] pci 0000:00:1e.0:   IO window: disabled
[    0.543139] pci 0000:00:1e.0:   MEM window: disabled
[    0.543142] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.543154] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.543158] pci 0000:00:1c.0: setting latency timer to 64
[    0.543164] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.543167] pci 0000:00:1c.4: setting latency timer to 64
[    0.543174] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.543177] pci 0000:00:1c.5: setting latency timer to 64
[    0.543183] pci 0000:00:1e.0: setting latency timer to 64
[    0.543186] bus: 00 index 0 io port: [0, ffff]
[    0.543188] bus: 00 index 1 mmio: [0, ffffffff]
[    0.543190] bus: 03 index 0 mmio: [0, 0]
[    0.543191] bus: 03 index 1 mmio: [fc000000, febfffff]
[    0.543193] bus: 03 index 2 mmio: [d0000000, dfffffff]
[    0.543195] bus: 03 index 3 mmio: [0, 0]
[    0.543196] bus: 02 index 0 io port: [e000, efff]
[    0.543198] bus: 02 index 1 mmio: [fbf00000, fbffffff]
[    0.543200] bus: 02 index 2 mmio: [0, 0]
[    0.543201] bus: 02 index 3 mmio: [0, 0]
[    0.543203] bus: 01 index 0 io port: [d000, dfff]
[    0.543205] bus: 01 index 1 mmio: [fbe00000, fbefffff]
[    0.543206] bus: 01 index 2 mmio: [cff00000, cfffffff]
[    0.543208] bus: 01 index 3 mmio: [0, 0]
[    0.543210] bus: 04 index 0 mmio: [0, 0]
[    0.543211] bus: 04 index 1 mmio: [0, 0]
[    0.543213] bus: 04 index 2 mmio: [0, 0]
[    0.543214] bus: 04 index 3 io port: [0, ffff]
[    0.543216] bus: 04 index 4 mmio: [0, ffffffff]
[    0.543223] NET: Registered protocol family 2
[    0.555986] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.556172] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.556450] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.556610] TCP: Hash tables configured (established 131072 bind 65536)
[    0.556613] TCP reno registered
[    0.564060] NET: Registered protocol family 1
[    0.564156] checking if image is initramfs... it is
[    1.147823] Freeing initrd memory: 7952k freed
[    1.148708] audit: initializing netlink socket (disabled)
[    1.148722] type=2000 audit(1237455201.148:1): initialized
[    1.153928] highmem bounce pool size: 64 pages
[    1.153933] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.156058] VFS: Disk quotas dquot_6.5.1
[    1.156130] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.156210] msgmni has been set to 1722
[    1.156306] io scheduler noop registered
[    1.156308] io scheduler anticipatory registered
[    1.156310] io scheduler deadline registered
[    1.156320] io scheduler cfq registered (default)
[    1.156446] pci 0000:03:00.0: Boot video device
[    1.156541] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.156569] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.156598] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.156632] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.156665] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.156738] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.156765] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.156792] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.156824] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.156854] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.156925] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.156952] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.156979] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.157010] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.157041] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.157294] isapnp: Scanning for PnP cards...
[    1.510889] isapnp: No Plug & Play device found
[    1.539771] hpet_resources: 0xfed00000 is busy
[    1.539845] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.539958] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.540088] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.540692] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.542234] brd: module loaded
[    1.542296] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.542464] PNP: No PS/2 controller found. Probing ports directly.
[    1.544783] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.544789] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.548100] mice: PS/2 mouse device common for all mice
[    1.548226] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.548245] rtc0: alarms up to one month, y3k, hpet irqs
[    1.548378] EISA: Probing bus 0 at eisa.0
[    1.548402] EISA: Detected 0 cards.
[    1.548405] cpuidle: using governor ladder
[    1.548407] cpuidle: using governor menu
[    1.548838] TCP cubic registered
[    1.548862] Using IPI No-Shortcut mode
[    1.549012] registered taskstats version 1
[    1.549123]   Magic number: 1:391:576
[    1.549162] tty ptyb8: hash matches
[    1.549227] rtc_cmos 00:03: setting system clock to 2009-03-19 09:33:22 UTC (1237455202)
[    1.549230] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.549232] EDD information not available.
[    1.549373] Freeing unused kernel memory: 424k freed
[    1.549406] Write protecting the kernel text: 2580k
[    1.549429] Write protecting the kernel read-only data: 940k
[    1.724125] fuse init (API version 7.9)
[    1.872206] ACPI: SSDT CBFC00C0, 01F3 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    1.872553] processor ACPI0007:00: registered as cooling_device0
[    1.872859] ACPI: SSDT CBFC0550, 01F3 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    1.873170] processor ACPI0007:01: registered as cooling_device1
[    2.037853] usbcore: registered new interface driver usbfs
[    2.037872] usbcore: registered new interface driver hub
[    2.044633] usbcore: registered new device driver usb
[    2.046838] USB Universal Host Controller Interface driver v3.0
[    2.046877] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.046885] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.046888] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.046925] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.046952] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c800
[    2.047057] usb usb1: configuration #1 chosen from 1 choice
[    2.047078] hub 1-0:1.0: USB hub found
[    2.047084] hub 1-0:1.0: 2 ports detected
[    2.148770] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.148783] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.148789] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.148809] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.148859] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c880
[    2.148937] usb usb2: configuration #1 chosen from 1 choice
[    2.148961] hub 2-0:1.0: USB hub found
[    2.148968] hub 2-0:1.0: 2 ports detected
[    2.152077] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.168855] No dock devices found.
[    2.181462] SCSI subsystem initialized
[    2.196046] libata version 3.00 loaded.
[    2.252768] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.252777] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.252781] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.252802] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.252830] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000cc00
[    2.252906] usb usb3: configuration #1 chosen from 1 choice
[    2.252927] hub 3-0:1.0: USB hub found
[    2.252932] hub 3-0:1.0: 2 ports detected
[    2.356722] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.356734] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.356737] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.356770] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.360658] ehci_hcd 0000:00:1a.7: debug port 1
[    2.360663] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.360675] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbdffc00
[    2.376009] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.376111] usb usb4: configuration #1 chosen from 1 choice
[    2.376133] hub 4-0:1.0: USB hub found
[    2.376139] hub 4-0:1.0: 6 ports detected
[    2.505208] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.505214] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.505217] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.505244] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.505270] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c080
[    2.505343] usb usb5: configuration #1 chosen from 1 choice
[    2.505363] hub 5-0:1.0: USB hub found
[    2.505368] hub 5-0:1.0: 2 ports detected
[    2.608180] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.608188] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.608191] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.608215] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.608237] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c400
[    2.608308] usb usb6: configuration #1 chosen from 1 choice
[    2.608330] hub 6-0:1.0: USB hub found
[    2.608335] hub 6-0:1.0: 2 ports detected
[    2.816183] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.816192] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.816195] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.816220] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.816242] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c480
[    2.816316] usb usb7: configuration #1 chosen from 1 choice
[    2.816338] hub 7-0:1.0: USB hub found
[    2.816343] hub 7-0:1.0: 2 ports detected
[    2.920134] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.920146] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.920149] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.920167] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    2.924053] ehci_hcd 0000:00:1d.7: debug port 1
[    2.924058] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.924063] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbdff800
[    2.928512] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    2.940008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.940074] usb usb8: configuration #1 chosen from 1 choice
[    2.940097] hub 8-0:1.0: USB hub found
[    2.940102] hub 8-0:1.0: 6 ports detected
[    2.996032] hub 6-0:1.0: unable to enumerate USB device on port 2
[    3.149655] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.149677] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    3.149687] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    3.149714] pata_acpi 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.149728] pata_acpi 0000:00:1f.5: setting latency timer to 64
[    3.149735] pata_acpi 0000:00:1f.5: PCI INT B disabled
[    3.149751] pata_acpi 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.149768] pata_acpi 0000:02:00.0: setting latency timer to 64
[    3.149778] pata_acpi 0000:02:00.0: PCI INT A disabled
[    3.152086] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.152097] r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.152109] r8169 0000:01:00.0: setting latency timer to 64
[    3.152410] eth0: RTL8168c/8111c at 0xf8868000, 00:19:66:83:21:c7, XID 3c2000c0 IRQ 220
[    3.159266] ata_piix 0000:00:1f.2: version 2.12
[    3.159278] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.159281] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    3.159317] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.160390] scsi0 : ata_piix
[    3.160470] scsi1 : ata_piix
[    3.161570] ata1: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 19
[    3.161573] ata2: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 19
[    3.490564] ata1: SATA link down (SStatus 0 SControl 300)
[    3.616010] usb 6-2: new low speed USB device using uhci_hcd and address 3
[    3.801527] usb 6-2: configuration #1 chosen from 1 choice
[    3.819079] ata2: SATA link down (SStatus 0 SControl 300)
[    3.819126] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.819130] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    3.819165] ata_piix 0000:00:1f.5: setting latency timer to 64
[    3.819330] scsi2 : ata_piix
[    3.822251] scsi3 : ata_piix
[    3.823471] ata3: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb480 irq 19
[    3.823474] ata4: SATA max UDMA/133 cmd 0xb880 ctl 0xb800 bmdma 0xb488 irq 19
[    3.825430] usbcore: registered new interface driver hiddev
[    3.839493] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input1
[    3.839672] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:1d.1-2
[    3.925362] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.1/input/input2
[    3.925561] input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:1d.1-2
[    3.925578] usbcore: registered new interface driver usbhid
[    3.925581] usbhid: v2.6:USB HID core driver
[    4.154544] ata3: SATA link down (SStatus 0 SControl 300)
[    4.628039] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.637121] ata4.00: ATA-8: WDC WD5000AACS-00G8B0, 05.04C05, max UDMA/133
[    4.637124] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.653150] ata4.00: configured for UDMA/133
[    4.653237] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 05.0 PQ: 0 ANSI: 5
[    4.653339] pata_jmicron 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.653366] pata_jmicron 0000:02:00.0: setting latency timer to 64
[    4.653810] scsi4 : pata_jmicron
[    4.653861] scsi5 : pata_jmicron
[    4.654047] ata5: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
[    4.654050] ata6: PATA max UDMA/100 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 16
[    4.661744] scsi 3:0:0:0: Attached scsi generic sg0 type 0
[    4.673311] Driver 'sd' needs updating - please use bus_type methods
[    4.673832] sd 3:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    4.673845] sd 3:0:0:0: [sda] Write Protect is off
[    4.673847] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.673867] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.673920] sd 3:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    4.673932] sd 3:0:0:0: [sda] Write Protect is off
[    4.673934] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.673954] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.673956]  sda: sda1 sda2 < sda5 >
[    4.715524] sd 3:0:0:0: [sda] Attached SCSI disk
[    4.816493] ata5.00: ATAPI: HL-DT-STDVD-ROM GDR8163B, 0L23, max UDMA/33
[    4.832503] ata5.00: configured for UDMA/33
[    4.996684] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8163B 0L23 PQ: 0 ANSI: 5
[    4.996800] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    5.010704] Driver 'sr' needs updating - please use bus_type methods
[    5.018614] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    5.018618] Uniform CD-ROM driver Revision: 3.20
[    5.018698] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    5.238199] PM: Starting manual resume from disk
[    5.238202] PM: Resume from partition 8:5
[    5.238204] PM: Checking hibernation image.
[    5.238359] PM: Resume from disk failed.
[    5.280813] kjournald starting.  Commit interval 5 seconds
[    5.280829] EXT3-fs: mounted filesystem with ordered data mode.
[   10.972014] udevd version 124 started
[   11.404586] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.447781] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.465576] iTCO_vendor_support: vendor-support=0
[   11.472905] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   11.473554] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0860)
[   11.473629] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.560895] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.570584] Linux agpgart interface v0.103
[   11.588531] ACPI: Power Button (FF) [PWRF]
[   11.588629] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   11.620524] ACPI: Power Button (CM) [PWRB]
[   11.928532] parport_pc 00:08: reported by Plug and Play ACPI
[   11.928582] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   12.254975] nvidia: module license 'NVIDIA' taints kernel.
[   12.266832] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.517654] udev: renamed network interface eth0 to eth1
[   12.581719] nvidia 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.581728] nvidia 0000:03:00.0: setting latency timer to 64
[   12.581875] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.581894] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.582152] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
[   12.626404] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.931304] lp0: using parport0 (interrupt-driven).
[   14.024570] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   14.563850] EXT3 FS on sda1, internal journal
[   15.495604] type=1505 audit(1237455216.673:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4099
[   15.627879] type=1505 audit(1237455216.805:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4104
[   15.628058] type=1505 audit(1237455216.809:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4104
[   15.671917] type=1505 audit(1237455216.849:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4108
[   15.697809] type=1505 audit(1237455216.877:6): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=4112
[   15.862225] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.461623] ACPI: WMI: Mapper loaded
[   17.449710] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   17.680334] NET: Registered protocol family 10
[   17.680942] lo: Disabled Privacy Extensions
[   19.727584] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   19.727589] apm: disabled - APM is not SMP safe.
[   19.915927] ppdev: user-space parallel port driver
[   22.703816] Bluetooth: Core ver 2.13
[   22.704690] NET: Registered protocol family 31
[   22.704694] Bluetooth: HCI device and connection manager initialized
[   22.704697] Bluetooth: HCI socket layer initialized
[   22.733409] Bluetooth: L2CAP ver 2.11
[   22.733414] Bluetooth: L2CAP socket layer initialized
[   22.771637] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.771642] Bluetooth: BNEP filters: protocol multicast
[   22.806735] Bridge firewalling registered
[   22.821009] Bluetooth: SCO (Voice Link) ver 0.6
[   22.821015] Bluetooth: SCO socket layer initialized
[   22.958924] Bluetooth: RFCOMM socket layer initialized
[   22.958937] Bluetooth: RFCOMM TTY layer initialized
[   22.958946] Bluetooth: RFCOMM ver 1.10
[   27.064438] r8169: eth1: link up
[   27.064448] r8169: eth1: link up
[   27.207059] NET: Registered protocol family 17
[   37.436010] eth1: no IPv6 routers present
[  146.716260] ppdev0: registered pardevice
[  146.764225] ppdev0: unregistered pardevice
[  148.060071] ppdev0: registered pardevice
[  148.108015] ppdev0: unregistered pardevice
[  149.944261] ppdev0: registered pardevice
[  149.992137] ppdev0: unregistered pardevice


```

---

### Post by hikaricore on 2009-03-19
Check the output of:

> cat /proc/cpuinfo

And see how many cores it shows.  You may also want to check bios to see if it's registering your cpu properly.
If you've applied any bios level cpu clock setting changes I suggest resetting them, powering completely down then starting your system up again.

---

### Post by CabbageCake on 2009-03-19
> **hikaricore said:**
> Check the output of:



And see how many cores it shows.  You may also want to check bios to see if it's registering your cpu properly.
If you've applied any bios level cpu clock setting changes I suggest resetting them, powering completely down then starting your system up again.

/proc/cpuinfo is showing two cores only. I haven't changed any BIOS settings recently.

---

### Post by CabbageCake on 2009-03-19
Here's cpuinfo:
```

matt@bunty:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
stepping	: 7
cpu MHz		: 2003.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 4666.57
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
stepping	: 7
cpu MHz		: 2003.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 2
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 4666.56
clflush size	: 64
power management:

```

---

