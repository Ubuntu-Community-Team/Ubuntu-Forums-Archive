---
title: "Ubuntu &quot;rots&quot;"
date: 2008-12-27
forum: General Help
---

### Post by inxygnuu on 2008-12-27
Hello, I have had my current Ubuntu installation for 1 month now, and I have had 2 installations, and they have both "rotted" as in things just stop working. First my usb drive, and before that, the startup screen freezes until I press a key. Why does this happen?

---

### Post by ushimitsudoki on 2008-12-27
The first thing I would do is to examine logs and see if the reveal anything.
The two most informative are usually /var/log/dmesg and /var/log/Xorg.0.log

---

### Post by inxygnuu on 2008-12-28
dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7f50000 (usable)
[    0.000000]  BIOS-e820: 00000000b7f50000 - 00000000b7f65000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7f65000 - 00000000b7f66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7f66000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xb7f50 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37831000 - 37fefa35
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F8250, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT B7F5C0CE, 006C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP B7F649BA, 00F4 (r3 NVIDIA MCP67-M   6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT B7F5C13A, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS B7F65FC0, 0040
[    0.000000] ACPI: TCPA B7F64AAE, 0032 (r1 Phoeni  x        6040000  TL         0)
[    0.000000] ACPI: SRAT B7F64AE0, 00A0 (r1 AMD    HAMMER    6040000 AMD         1)
[    0.000000] ACPI: SSDT B7F64B80, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG B7F64D86, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET B7F64DC2, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC B7F64DFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT B7F64E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC B7F64E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] 2047MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037831000 - 0037fefa35]          RAMDISK ==> [0037831000 - 0037fefa35]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f8220] 000f8220
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000b7f50
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000b7f50
[    0.000000] On node 0 totalpages: 753390
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3962 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 519505 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 746767
[    0.000000] Kernel command line: root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2000.131 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2972336k/3013952k available (2572k kernel code, 40256k reserved, 1160k data, 424k init, 2096448k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.26 BogoMIPS (lpj=8000524)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(2) -> Core 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017561] ACPI: Core revision 20080609
[    0.020481] ACPI: Checking initramfs for custom DSDT
[    0.360317] ENABLING IO-APIC IRQs
[    0.360547] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.400842] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.404025] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4000.42 BogoMIPS (lpj=8000859)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.488179] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.488207] Brought up 2 CPUs
[    0.488210] Total of 2 processors activated (8000.69 BogoMIPS).
[    0.488055] System has AMD C1E enabled
[    0.488249] CPU0 attaching sched-domain:
[    0.488071] Switch to broadcast mode on CPU1
[    0.488257]  domain 0: span 0-1 level CPU
[    0.488260]   groups: 0 1
[    0.488266] CPU1 attaching sched-domain:
[    0.488268]  domain 0: span 0-1 level CPU
[    0.488271]   groups: 1 0
[    0.488340] Switch to broadcast mode on CPU0
[    0.488340] net_namespace: 840 bytes
[    0.488340] Booting paravirtualized kernel on bare hardware
[    0.488340] Time: 11:11:09  Date: 12/28/08
[    0.488340] NET: Registered protocol family 16
[    0.488340] EISA bus registered
[    0.488340] ACPI: bus type pci registered
[    0.488340] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.488340] PCI: MCFG area at e0000000 reserved in E820
[    0.488340] PCI: Using MMCONFIG for extended config space
[    0.488340] PCI: Using configuration type 1 for base access
[    0.488804] ACPI: EC: Look up EC in DSDT
[    0.494185] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.495076] ACPI: Interpreter enabled
[    0.495079] ACPI: (supports S0 S3 S4 S5)
[    0.495095] ACPI: Using IOAPIC for interrupt routing
[    0.495160] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.516216] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.516216] ACPI: EC: driver started in interrupt mode
[    0.516216] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.516216] PCI: 0000:00:01.1 reg 10 io port: [3080, 30bf]
[    0.516216] PCI: 0000:00:01.1 reg 20 io port: [3040, 307f]
[    0.516218] PCI: 0000:00:01.1 reg 24 io port: [3000, 303f]
[    0.516233] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.516239] pci 0000:00:01.1: PME# disabled
[    0.516287] PCI: 0000:00:01.3 reg 10 32bit mmio: [f6200000, f627ffff]
[    0.516362] PCI: 0000:00:02.0 reg 10 32bit mmio: [f6486000, f6486fff]
[    0.516383] pci 0000:00:02.0: supports D1
[    0.516385] pci 0000:00:02.0: supports D2
[    0.516387] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516391] pci 0000:00:02.0: PME# disabled
[    0.516410] PCI: 0000:00:02.1 reg 10 32bit mmio: [f6489000, f64890ff]
[    0.516435] pci 0000:00:02.1: supports D1
[    0.516436] pci 0000:00:02.1: supports D2
[    0.516438] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516442] pci 0000:00:02.1: PME# disabled
[    0.516463] PCI: 0000:00:04.0 reg 10 32bit mmio: [f6487000, f6487fff]
[    0.516484] pci 0000:00:04.0: supports D1
[    0.516486] pci 0000:00:04.0: supports D2
[    0.516488] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516492] pci 0000:00:04.0: PME# disabled
[    0.516511] PCI: 0000:00:04.1 reg 10 32bit mmio: [f6489400, f64894ff]
[    0.516535] pci 0000:00:04.1: supports D1
[    0.516537] pci 0000:00:04.1: supports D2
[    0.516539] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516543] pci 0000:00:04.1: PME# disabled
[    0.516575] PCI: 0000:00:06.0 reg 20 io port: [30c0, 30cf]
[    0.516610] PCI: 0000:00:07.0 reg 10 32bit mmio: [f6480000, f6483fff]
[    0.516634] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.516638] pci 0000:00:07.0: PME# disabled
[    0.516690] PCI: 0000:00:09.0 reg 10 io port: [30f0, 30f7]
[    0.516694] PCI: 0000:00:09.0 reg 14 io port: [30e4, 30e7]
[    0.516698] PCI: 0000:00:09.0 reg 18 io port: [30e8, 30ef]
[    0.516702] PCI: 0000:00:09.0 reg 1c io port: [30e0, 30e3]
[    0.516706] PCI: 0000:00:09.0 reg 20 io port: [30d0, 30df]
[    0.516710] PCI: 0000:00:09.0 reg 24 32bit mmio: [f6484000, f6485fff]
[    0.516750] PCI: 0000:00:0a.0 reg 10 32bit mmio: [f6488000, f6488fff]
[    0.516755] PCI: 0000:00:0a.0 reg 14 io port: [30f8, 30ff]
[    0.516759] PCI: 0000:00:0a.0 reg 18 32bit mmio: [f6489c00, f6489cff]
[    0.516763] PCI: 0000:00:0a.0 reg 1c 32bit mmio: [f6489800, f648980f]
[    0.516781] pci 0000:00:0a.0: supports D1
[    0.516783] pci 0000:00:0a.0: supports D2
[    0.516785] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516789] pci 0000:00:0a.0: PME# disabled
[    0.516818] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516821] pci 0000:00:0c.0: PME# disabled
[    0.516847] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516850] pci 0000:00:0d.0: PME# disabled
[    0.516868] PCI: 0000:00:12.0 reg 10 32bit mmio: [f5000000, f5ffffff]
[    0.516872] PCI: 0000:00:12.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.516879] PCI: 0000:00:12.0 reg 1c 64bit mmio: [f4000000, f4ffffff]
[    0.516885] PCI: 0000:00:12.0 reg 30 32bit mmio: [0, 1ffff]
[    0.516989] PCI: 0000:02:05.0 reg 10 32bit mmio: [0, 7ff]
[    0.517019] pci 0000:02:05.0: supports D1
[    0.517021] pci 0000:02:05.0: supports D2
[    0.517024] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.517027] pci 0000:02:05.0: PME# disabled
[    0.517048] PCI: 0000:02:05.1 reg 10 32bit mmio: [f6100800, f61008ff]
[    0.517079] pci 0000:02:05.1: supports D1
[    0.517081] pci 0000:02:05.1: supports D2
[    0.517083] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.517087] pci 0000:02:05.1: PME# disabled
[    0.517108] PCI: 0000:02:05.2 reg 10 32bit mmio: [f6100c00, f6100cff]
[    0.517138] pci 0000:02:05.2: supports D1
[    0.517140] pci 0000:02:05.2: supports D2
[    0.517142] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.517146] pci 0000:02:05.2: PME# disabled
[    0.517167] PCI: 0000:02:05.3 reg 10 32bit mmio: [f6101000, f61010ff]
[    0.517197] pci 0000:02:05.3: supports D1
[    0.517199] pci 0000:02:05.3: supports D2
[    0.517201] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.517205] pci 0000:02:05.3: PME# disabled
[    0.517227] PCI: 0000:02:05.4 reg 10 32bit mmio: [f6101400, f61014ff]
[    0.517258] pci 0000:02:05.4: supports D1
[    0.517260] pci 0000:02:05.4: supports D2
[    0.517262] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.517266] pci 0000:02:05.4: PME# disabled
[    0.517295] pci 0000:00:08.0: transparent bridge
[    0.517300] PCI: bridge 0000:00:08.0 32bit mmio: [f6100000, f61fffff]
[    0.517339] PCI: bridge 0000:00:0c.0 io port: [4000, 4fff]
[    0.517342] PCI: bridge 0000:00:0c.0 32bit mmio: [f2000000, f3ffffff]
[    0.517346] PCI: bridge 0000:00:0c.0 64bit mmio pref: [f0000000, f1ffffff]
[    0.517381] PCI: 0000:03:00.0 reg 10 64bit mmio: [f6000000, f600ffff]
[    0.517451] PCI: bridge 0000:00:0d.0 32bit mmio: [f6000000, f60fffff]
[    0.517461] bus 00 -> node 0
[    0.517468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.517576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.517601] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.517640] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.557903] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.557903] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.557903] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.557903] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.557903] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.557903] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.557903] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.557903] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.557903] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.558135] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.558389] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.558649] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.558903] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.559157] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.559416] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.559672] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.559927] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.560198] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.560458] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.564162] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.564185] pnp: PnP ACPI init
[    0.564185] ACPI: bus type pnp registered
[    0.568390] pnp: PnP ACPI: found 12 devices
[    0.568393] ACPI: ACPI bus type pnp unregistered
[    0.568396] PnPBIOS: Disabled by ACPI PNP
[    0.568427] PCI: Using ACPI for IRQ routing
[    0.572044] NET: Registered protocol family 8
[    0.572047] NET: Registered protocol family 20
[    0.576040] NetLabel: Initializing
[    0.576040] NetLabel:  domain hash size = 128
[    0.576040] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.576055] NetLabel:  unlabeled traffic allowed by default
[    0.576063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.576068] hpet0: 3 32-bit timers, 25000000 Hz
[    0.577674] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.577677]    actual entries 65620
[    0.577825] AppArmor: AppArmor Filesystem Enabled
[    0.577853] ACPI: RTC can wake from S4
[    0.580051] Switched to high resolution mode on CPU 0
[    0.580065] Switched to high resolution mode on CPU 1
[    0.580097] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.580104] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.580107] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.580110] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.580113] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.580116] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.580119] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.580126] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.580129] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.580140] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.580143] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.580147] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.580150] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.580154] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.615473] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.615476] pci 0000:00:08.0:   IO window: disabled
[    0.615480] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.615483] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.615488] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.615491] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.615494] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.615498] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.615502] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.615504] pci 0000:00:0d.0:   IO window: disabled
[    0.615508] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.615511] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.615520] pci 0000:00:08.0: setting latency timer to 64
[    0.615526] pci 0000:00:0c.0: setting latency timer to 64
[    0.615531] pci 0000:00:0d.0: setting latency timer to 64
[    0.615534] bus: 00 index 0 io port: [0, ffff]
[    0.615537] bus: 00 index 1 mmio: [0, ffffffff]
[    0.615539] bus: 02 index 0 mmio: [0, 0]
[    0.615541] bus: 02 index 1 mmio: [f6100000, f61fffff]
[    0.615543] bus: 02 index 2 mmio: [0, 0]
[    0.615545] bus: 02 index 3 io port: [0, ffff]
[    0.615548] bus: 02 index 4 mmio: [0, ffffffff]
[    0.615550] bus: 04 index 0 io port: [4000, 4fff]
[    0.615552] bus: 04 index 1 mmio: [f2000000, f3ffffff]
[    0.615555] bus: 04 index 2 mmio: [f0000000, f1ffffff]
[    0.615558] bus: 04 index 3 mmio: [0, 0]
[    0.615560] bus: 03 index 0 mmio: [0, 0]
[    0.615562] bus: 03 index 1 mmio: [f6000000, f60fffff]
[    0.615564] bus: 03 index 2 mmio: [0, 0]
[    0.615566] bus: 03 index 3 mmio: [0, 0]
[    0.615579] NET: Registered protocol family 2
[    0.625082] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.625388] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.626191] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.626641] TCP: Hash tables configured (established 131072 bind 65536)
[    0.626644] TCP reno registered
[    0.629114] NET: Registered protocol family 1
[    0.629244] checking if image is initramfs... it is
[    1.323274] Freeing initrd memory: 7930k freed
[    1.323444] Simple Boot Flag at 0x36 set to 0x1
[    1.324630] audit: initializing netlink socket (disabled)
[    1.324648] type=2000 audit(1230462669.324:1): initialized
[    1.330751] highmem bounce pool size: 64 pages
[    1.330758] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.333544] VFS: Disk quotas dquot_6.5.1
[    1.333656] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.333769] msgmni has been set to 1728
[    1.333902] io scheduler noop registered
[    1.333904] io scheduler anticipatory registered
[    1.333907] io scheduler deadline registered
[    1.333919] io scheduler cfq registered (default)
[    1.333953] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.334113] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.334128] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.334144] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.334161] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.334177] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.334192] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.334208] pci 0000:00:12.0: Boot video device
[    1.334348] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.334376] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.334399] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.334463] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.334552] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.334578] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.334596] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.334651] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.335060] isapnp: Scanning for PnP cards...
[    1.687659] isapnp: No Plug & Play device found
[    1.730604] hpet_resources: 0xfed00000 is busy
[    1.730709] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.733419] brd: module loaded
[    1.733503] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.733648] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.761242] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.761249] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.761597] mice: PS/2 mouse device common for all mice
[    1.761761] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.761796] rtc0: alarms up to one year, y3k, hpet irqs
[    1.761937] EISA: Probing bus 0 at eisa.0
[    1.761943] Cannot allocate resource for EISA slot 1
[    1.761949] Cannot allocate resource for EISA slot 3
[    1.761952] Cannot allocate resource for EISA slot 4
[    1.761964] EISA: Detected 0 cards.
[    1.761968] cpuidle: using governor ladder
[    1.761970] cpuidle: using governor menu
[    1.762467] TCP cubic registered
[    1.762494] Using IPI No-Shortcut mode
[    1.762720] registered taskstats version 1
[    1.762868]   Magic number: 4:922:176
[    1.762928] tty ttyr2: hash matches
[    1.763031] acpi device:0c: hash matches
[    1.763080] rtc_cmos 00:07: setting system clock to 2008-12-28 11:11:11 UTC (1230462671)
[    1.763083] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.763085] EDD information not available.
[    1.763390] Freeing unused kernel memory: 424k freed
[    1.763455] Write protecting the kernel text: 2576k
[    1.763495] Write protecting the kernel read-only data: 936k
[    1.781734] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.941956] fuse init (API version 7.9)
[    2.020874] ACPI: processor limited to max C-state 1
[    2.029063] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.029144] processor ACPI0007:00: registered as cooling_device0
[    2.029149] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.029364] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.029431] processor ACPI0007:01: registered as cooling_device1
[    2.029437] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.032299] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080609]
[    2.541745] usbcore: registered new interface driver usbfs
[    2.541770] usbcore: registered new interface driver hub
[    2.541831] usbcore: registered new device driver usb
[    2.542025] No dock devices found.
[    2.576592] SCSI subsystem initialized
[    2.666882] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    2.666896] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    2.666909] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.666913] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.666973] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    2.667004] ehci_hcd 0000:00:02.1: debug port 1
[    2.667009] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.667027] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    2.667085] libata version 3.00 loaded.
[    2.669118] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.677772] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.677949] usb usb1: configuration #1 chosen from 1 choice
[    2.677977] hub 1-0:1.0: USB hub found
[    2.677989] hub 1-0:1.0: 7 ports detected
[    2.885803] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    2.885810] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    2.885825] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    2.885829] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    2.885855] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    2.885885] ehci_hcd 0000:00:04.1: debug port 1
[    2.885890] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    2.885898] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    2.897033] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.897217] usb usb2: configuration #1 chosen from 1 choice
[    2.897246] hub 2-0:1.0: USB hub found
[    2.897256] hub 2-0:1.0: 2 ports detected
[    8.922150] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    8.922163] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    8.922178] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    8.922182] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    8.922211] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    8.922235] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    9.170806] usb usb3: configuration #1 chosen from 1 choice
[    9.170836] hub 3-0:1.0: USB hub found
[    9.170846] hub 3-0:1.0: 7 ports detected
[    9.357114] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    9.419492] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    9.419497] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    9.419512] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    9.419515] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    9.419541] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    9.419555] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    9.483635] usb usb4: configuration #1 chosen from 1 choice
[    9.483664] hub 4-0:1.0: USB hub found
[    9.483674] hub 4-0:1.0: 2 ports detected
[    9.553889] usb 2-2: configuration #1 chosen from 1 choice
[    9.732862] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    9.733319] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    9.733329] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    9.733335] forcedeth 0000:00:0a.0: setting latency timer to 64
[    9.733412] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    9.971083] usb 3-1: configuration #1 chosen from 1 choice
[   10.170316] usb 4-1: new full speed USB device using ohci_hcd and address 2
[   10.295371] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:95:10:70
[   10.295375] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   10.297042] ohci1394 0000:02:05.0: enabling device (0100 -> 0102)
[   10.297474] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   10.297488] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[   10.349235] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   10.356378] pata_acpi 0000:00:06.0: setting latency timer to 64
[   10.356835] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[   10.356847] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[   10.356865] pata_acpi 0000:00:09.0: setting latency timer to 64
[   10.356873] pata_acpi 0000:00:09.0: PCI INT A disabled
[   10.359727] pata_amd 0000:00:06.0: version 0.3.10
[   10.359773] pata_amd 0000:00:06.0: setting latency timer to 64
[   10.363775] scsi0 : pata_amd
[   10.363911] scsi1 : pata_amd
[   10.364324] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[   10.364328] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[   10.486723] usb 4-1: configuration #1 chosen from 1 choice
[   10.490099] usbcore: registered new interface driver hiddev
[   10.496067] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.0/input/input2
[   10.521188] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:02.0-1
[   10.539338] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.1/input/input3
[   10.545017] ata1.00: ATAPI: PIONEER DVDRW  DR-KD08HB, 1K09, max MWDMA2
[   10.545031] ata1: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[   10.554014] input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:02.0-1
[   10.554041] usbcore: registered new interface driver usbhid
[   10.554045] usbhid: v2.6:USB HID core driver
[   10.576523] ata1.00: configured for MWDMA2
[   10.576570] ata2: port disabled. ignoring.
[   10.615658] scsi 0:0:0:0: CD-ROM            PIONEER  DVDRW  DR-KD08HB 1K09 PQ: 0 ANSI: 5
[   10.615904] ahci 0000:00:09.0: version 3.0
[   10.615918] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[   10.616012] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   10.616016] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[   10.616020] ahci 0000:00:09.0: setting latency timer to 64
[   10.616394] scsi2 : ahci
[   10.616500] scsi3 : ahci
[   10.616590] scsi4 : ahci
[   10.616683] scsi5 : ahci
[   10.616795] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 221
[   10.616799] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 221
[   10.616802] ata5: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 221
[   10.616805] ata6: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 221
[   10.623850] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[   10.637222] Driver 'sr' needs updating - please use bus_type methods
[   10.764715] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   10.764721] Uniform CD-ROM driver Revision: 3.20
[   10.764822] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   11.139044] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   11.139757] ata3.00: ATA-8: ST9200827AS, 3.BHA, max UDMA/100
[   11.139761] ata3.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   11.140199] ata3.00: configured for UDMA/100
[   11.514316] ata4: SATA link down (SStatus 0 SControl 300)
[   11.687102] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[   11.889685] ata5: SATA link down (SStatus 0 SControl 300)
[   12.139749] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0090a91d40668db4]
[   12.139904] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[00241b00145a1201]
[   12.178951] scsi6 : SBP-2 IEEE-1394
[   12.233644] ata6: SATA link down (SStatus 0 SControl 300)
[   12.233774] scsi 2:0:0:0: Direct-Access     ATA      ST9200827AS      3.BH PQ: 0 ANSI: 5
[   12.233954] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   12.256444] Driver 'sd' needs updating - please use bus_type methods
[   16.919600] ieee1394: sbp2: Logged into SBP-2 device
[   16.933268] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   17.053673] scsi 6:0:0:0: Direct-Access     WD       My Book          1025 PQ: 0 ANSI: 4
[   17.053885] scsi 6:0:0:0: Attached scsi generic sg2 type 0
[   17.054108] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   17.057058] sd 2:0:0:0: [sda] Write Protect is off
[   17.057063] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.058093] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.058205] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   17.058225] sd 2:0:0:0: [sda] Write Protect is off
[   17.058228] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.058261] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.058265]  sda:<6>scsi7 : SBP-2 IEEE-1394
[   17.202200]  sda1 sda3 < sda5 sda6 sda7 sda8 >
[   17.258133] sd 2:0:0:0: [sda] Attached SCSI disk
[   17.306684] sd 6:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   17.338546] sd 6:0:0:0: [sdb] Write Protect is off
[   17.338549] sd 6:0:0:0: [sdb] Mode Sense: 10 00 00 00
[   17.364260] sd 6:0:0:0: [sdb] Cache data unavailable
[   17.364264] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   17.413800] sd 6:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   17.445517] sd 6:0:0:0: [sdb] Write Protect is off
[   17.445520] sd 6:0:0:0: [sdb] Mode Sense: 10 00 00 00
[   17.471654] sd 6:0:0:0: [sdb] Cache data unavailable
[   17.471657] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   17.471662]  sdb: sdb1 sdb2 sdb3 sdb4
[   17.898510] sd 6:0:0:0: [sdb] Attached SCSI disk
[   22.010321] ieee1394: sbp2: Logged into SBP-2 device
[   22.023712] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   22.143295] scsi 7:0:1:0: Enclosure         WD       My Book Device        PQ: 0 ANSI: 4
[   22.143493] scsi 7:0:1:0: Attached scsi generic sg3 type 13
[   22.146885] ------------[ cut here ]------------
[   22.146889] WARNING: at /build/buildd/linux-2.6.27/fs/sysfs/dir.c:463 sysfs_add_one+0x4e/0x50()
[   22.146892] sysfs: duplicate filename '0090a91d40668db4-1' can not be created
[   22.146894] Modules linked in: sd_mod crc_t10dif sbp2(+) sr_mod cdrom sg usbhid hid ahci pata_amd pata_acpi ata_generic ohci1394 ieee1394 ohci_hcd forcedeth ehci_hcd libata scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   22.146916] Pid: 2075, comm: knodemgrd_0 Not tainted 2.6.27-7-generic #1
[   22.146920]  [<c0131d65>] warn_slowpath+0x65/0x90
[   22.146927]  [<c0381fef>] ? kprobe_flush_task+0x5f/0x80
[   22.146933]  [<c0128550>] ? finish_task_switch+0xb0/0xe0
[   22.146937]  [<c024d9ca>] ? idr_get_empty_slot+0xda/0x250
[   22.146942]  [<c024dbc4>] ? ida_get_new_above+0x84/0x1c0
[   22.146946]  [<c01c724e>] ? find_inode+0xe/0x70
[   22.146950]  [<c01ffc30>] ? sysfs_ilookup_test+0x0/0x20
[   22.146954]  [<c01ffc30>] ? sysfs_ilookup_test+0x0/0x20
[   22.146958]  [<c02541f2>] ? strcmp+0x12/0x40
[   22.146962]  [<c01fff59>] ? sysfs_find_dirent+0x29/0x40
[   22.146966]  [<c0200018>] ? __sysfs_add_one+0x18/0x90
[   22.146969]  [<c02001ee>] sysfs_add_one+0x4e/0x50
[   22.146972]  [<c0201079>] sysfs_do_create_link+0xd9/0x130
[   22.146976]  [<c0201107>] sysfs_create_link+0x17/0x20
[   22.146979]  [<c02c3b9e>] driver_sysfs_add+0x2e/0x80
[   22.146984]  [<c02c3ef9>] device_bind_driver+0x19/0x40
[   22.146987]  [<c02c3f59>] device_attach+0x39/0x80
[   22.146991]  [<c02c2ba8>] bus_rescan_devices_helper+0x48/0x80
[   22.146994]  [<c02c3593>] bus_for_each_dev+0x53/0x80
[   22.146998]  [<c02c35db>] bus_rescan_devices+0x1b/0x20
[   22.147001]  [<c02c2b60>] ? bus_rescan_devices_helper+0x0/0x80
[   22.147005]  [<f890522a>] nodemgr_host_thread+0x29a/0x2d0 [ieee1394]
[   22.147021]  [<f8905b50>] ? node_probe+0x0/0x60 [ieee1394]
[   22.147032]  [<f8904f90>] ? nodemgr_host_thread+0x0/0x2d0 [ieee1394]
[   22.147042]  [<c0147141>] kthread+0x41/0x80
[   22.147046]  [<c0147100>] ? kthread+0x0/0x80
[   22.147050]  [<c0105297>] kernel_thread_helper+0x7/0x10
[   22.147055]  =======================
[   22.147057] ---[ end trace 5ad7f7930c9449e4 ]---
[   22.175670] Driver 'ses' needs updating - please use bus_type methods
[   22.175693] ses 7:0:1:0: Attached Enclosure device
[   27.064334] PM: Starting manual resume from disk
[   27.064338] PM: Resume from partition 8:7
[   27.064340] PM: Checking hibernation image.
[   27.064456] PM: Resume from disk failed.
[   27.109915] kjournald starting.  Commit interval 5 seconds
[   27.109927] EXT3-fs: mounted filesystem with ordered data mode.
[   33.695573] udevd version 124 started
[   34.424196] ACPI: AC Adapter [ACAD] (on-line)
[   34.892549] ACPI: Battery Slot [BAT0] (battery present)
[   34.892830] ACPI: WMI: Mapper loaded
[   35.373189] acpi device:25: registered as cooling_device2
[   35.373374] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input4
[   35.397062] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   35.409049] ricoh-mmc: Ricoh MMC Controller disabling driver
[   35.409053] ricoh-mmc: Copyright(c) Philip Langdale
[   35.409882] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   35.409898] ricoh-mmc: Controller is now disabled.
[   35.510330] sdhci: Secure Digital Host Controller Interface driver
[   35.510335] sdhci: Copyright(c) Pierre Ossman
[   35.558622] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[   35.559081] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   35.559094] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   35.562153] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
[   35.731838] Bluetooth: Core ver 2.13
[   35.741112] NET: Registered protocol family 31
[   35.741116] Bluetooth: HCI device and connection manager initialized
[   35.741121] Bluetooth: HCI socket layer initialized
[   35.856908] Linux video capture interface: v2.00
[   36.003359] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.027942] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.101260] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   36.101875] usbcore: registered new interface driver btusb
[   36.145416] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   36.145430] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   36.145461] HDA Intel 0000:00:07.0: setting latency timer to 64
[   36.154545] Linux agpgart interface v0.103
[   36.186618] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
[   36.188385] input: HP Webcam as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input5
[   36.224208] usbcore: registered new interface driver uvcvideo
[   36.224213] USB Video Class driver (v0.1.0)
[   36.444014] nvidia: module license 'NVIDIA' taints kernel.
[   36.700214] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   36.811261] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   36.811301] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   36.811310] nvidia 0000:00:12.0: setting latency timer to 64
[   37.074743] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
[   37.152978] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   37.303802] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'RtlIsServicePackVersionInstalled'
[   37.303820] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   37.303828] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   37.303835] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   37.303893] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   37.303902] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   37.303914] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   37.303922] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   37.303934] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   37.303954] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   37.303965] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   37.303974] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   37.303982] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   37.303995] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   37.304008] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   37.304020] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   37.304029] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   37.304038] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   37.304048] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   37.304057] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   37.304072] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   37.304081] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   37.304109] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   37.304118] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   37.304126] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   37.304135] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   37.304147] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   37.304164] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   37.304173] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   37.304181] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   37.304189] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   37.304201] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   37.304209] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   37.304220] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   37.304228] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   37.304237] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   37.304245] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   37.304254] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   37.304263] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   37.304272] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   37.304276] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathr'
[   37.304954] ndiswrapper (load_wrap_driver:108): couldn't load driver netathr; check system log for messages from 'loadndisdriver'
[   37.305070] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   37.308357] usbcore: registered new interface driver ndiswrapper
[   38.720929] lp: driver loaded but no devices found
[   38.811123] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)
[   38.877661] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   38.877674] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   38.877684] ath_pci 0000:03:00.0: setting latency timer to 64
[   39.367548] MadWifi: ath_attach: Switching rfkill capability off.
[   39.372986] wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)
[   39.414238] ath_pci: wifi0: Atheros 5424/2424: mem=0xf6000000, irq=19
[   39.557405] Adding 3076376k swap on /dev/sda7.  Priority:-1 extents:1 across:3076376k
[   40.102240] EXT3 FS on sda8, internal journal
[   41.217813] type=1505 audit(1230462710.701:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4524
[   41.422032] type=1505 audit(1230462710.906:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4529
[   41.422296] type=1505 audit(1230462710.906:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4529
[   41.589214] ip_tables: (C) 2000-2006 Netfilter Core Team

Xorg.0.log:


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux evan-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 28 06:12:00 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI: (0@0:1:3) nVidia Corporation MCP67 Co-processor rev 162, Mem @ 0xf6200000/0
(--) PCI:*(0@0:18:0) nVidia Corporation GeForce 7150M rev 162, Mem @ 0xf5000000/0, 0xd0000000/0, 0xf4000000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.80  Wed Oct  1 15:06:06 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  177.80  Wed Oct  1 14:45:01 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:12:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7150M / nForce 630M (C67) at PCI:0:18:0
(II) NVIDIA(0):     (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.67.32.16.17
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7150M / nForce 630M at
(--) NVIDIA(0):     PCI:0:18:0:
(--) NVIDIA(0):     GATEWAY EV700 (CRT-0)
(--) NVIDIA(0):     LPL LP154WX4-TLC8 (DFP-0)
(--) NVIDIA(0): GATEWAY EV700 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): LPL LP154WX4-TLC8 (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): LPL LP154WX4-TLC8 (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event6"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Desktop? 2.10
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: always reports core events
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: Device: "/dev/input/event3"
(II) Microsoft Microsoft Wireless Optical Desktop? 2.10: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Desktop? 2.10: Found x and y absolute axes
(II) Microsoft Microsoft Wireless Optical Desktop? 2.10: Found 6 mouse buttons
(II) Microsoft Microsoft Wireless Optical Desktop? 2.10: Found keys
(II) Microsoft Microsoft Wireless Optical Desktop? 2.10: Configuring as mouse
(II) Microsoft Microsoft Wireless Optical Desktop? 2.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop? 2.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: xkb_layout: "us"
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Desktop? 2.10
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: always reports core events
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: Device: "/dev/input/event2"
(II) Microsoft Microsoft Wireless Optical Desktop? 2.10: Found keys
(II) Microsoft Microsoft Wireless Optical Desktop? 2.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop? 2.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Microsoft Wireless Optical Desktop? 2.10: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event4"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
AUDIT: Sun Dec 28 06:12:11 2008: 5859 X: client 4 rejected from local host ( uid=0 gid=0 pid=6849 )
AUDIT: Sun Dec 28 06:12:41 2008: 5859 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6854 )
AUDIT: Sun Dec 28 06:12:41 2008: 5859 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6855 )
AUDIT: Sun Dec 28 06:12:41 2008: 5859 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6856 )

---

### Post by noerrorsfound on 2008-12-28
Code tags...

---

### Post by inxygnuu on 2008-12-28
> **noerrorsfound said:**
> Code tags...

what? i'm sorry...

---

