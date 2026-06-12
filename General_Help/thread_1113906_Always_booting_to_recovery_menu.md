---
title: "Always booting to recovery menu"
date: 2009-04-02
forum: General Help
---

### Post by infirmus on 2009-04-02
I'm running Ubuntu 8.10 Intrepid server and every time I boot it goes to the "Recovery menu" and I have to press enter to resume normal boot. It is really annoying because I cant remotely reboot the server. Has anyone else experienced this or know a fix?

uname -a:
Linux server 2.6.27-7-server #1 SMP Fri Oct 24 07:20:47 UTC 2008 x86_64 GNU/Linux

dmesg output:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-server (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 07:20:47 UTC 2008 (Ubuntu 2.6.27-7.14-server)
[    0.000000] Command line: root=/dev/mapper/single-rootfs ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007dfb0000 (usable)
[    0.000000]  BIOS-e820: 000000007dfb0000 - 000000007dfc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007dfc0000 - 000000007dff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007dff0000 - 000000007e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7dfb0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 007de00000 page 2M
[    0.000000]  007de00000 - 007dfb0000 page 4k
[    0.000000] kernel direct mapping tables up to 7dfb0000 @ 8000-c000
[    0.000000] last_map_addr: 7dfb0000 end: 7dfb0000
[    0.000000] RAMDISK: 3771b000 - 37fefda0
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000FBA40, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7DFB0000, 003C (r1 100207 RSDT1125 20071002 MSFT       97)
[    0.000000] ACPI: FACP 7DFB0200, 0084 (r2 A M I  OEMFACP  12000601 MSFT       97)
[    0.000000] ACPI: DSDT 7DFB0450, 5B7A (r1  ASR32 ASR32164      164 INTL 20051117)
[    0.000000] ACPI: FACS 7DFC0000, 0040
[    0.000000] ACPI: APIC 7DFB0390, 0080 (r1 100207 APIC1125 20071002 MSFT       97)
[    0.000000] ACPI: MCFG 7DFB0410, 003C (r1 100207 OEMMCFG  20071002 MSFT       97)
[    0.000000] ACPI: OEMB 7DFC0040, 0071 (r1 100207 OEMB1125 20071002 MSFT       97)
[    0.000000] ACPI: NVHD 7DFC00C0, 0554 (r1 100207  NVHDCP  20071002 MSFT       97)
[    0.000000] ACPI: SSDT 7DFB5FD0, 0206 (r1 A M I  POWERNOW        1 AMD         1)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007dfb0000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007dfb0000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000a000 -  0000000000019bf7] pages 10
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007dfb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b6f9c]    TEXT DATA BSS ==> [0000200000 - 00008b6f9c]
[    0.000000]   #3 [003771b000 - 0037fefda0]          RAMDISK ==> [003771b000 - 0037fefda0]
[    0.000000]   #4 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20001ffffff] PMD -> [ffff880001200000-ffff8800031fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007dfb0
[    0.000000] On node 0 totalpages: 515917
[    0.000000]   DMA zone: 2110 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 503921 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7e000000:80c00000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 506031
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=/dev/mapper/single-rootfs ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2094.808 MHz processor.
[    0.010000] spurious 8259A interrupt: IRQ7.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Checking aperture...
[    0.010000] No AGP bridge found
[    0.010000] Node 0: aperture @ 6204000000 size 32 MB
[    0.010000] Aperture beyond 4GB. Ignoring.
[    0.010000] Memory: 2014548k/2064064k available (3110k kernel code, 49120k reserved, 1573k data, 536k init)
[    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.010000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.010009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4189.61 BogoMIPS (lpj=20948080)
[    0.010037] Security Framework initialized
[    0.010044] SELinux:  Disabled at boot.
[    0.010061] AppArmor: AppArmor initialized
[    0.010284] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011575] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.012129] Mount-cache hash table entries: 256
[    0.012328] Initializing cgroup subsys ns
[    0.012331] Initializing cgroup subsys cpuacct
[    0.012334] Initializing cgroup subsys memory
[    0.012350] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.012352] CPU: L2 Cache: 512K (64 bytes/line)
[    0.012355] CPU 0/0 -> Node 0
[    0.012356] tseg: 0000000000
[    0.012370] CPU: Physical Processor ID: 0
[    0.012372] CPU: Processor Core ID: 0
[    0.012381] using C1E aware idle routine
[    0.013741] ACPI: Core revision 20080609
[    0.015701] ACPI: Checking initramfs for custom DSDT
[    0.356178] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.456200] CPU0: AMD Athlon(tm) X2 Dual Core Processor BE-2350 stepping 01
[    0.456205] Using local APIC timer interrupts.
[    0.460001] APIC timer calibration result 12469107
[    0.460003] Detected 12.469 MHz APIC timer.
[    0.460177] Booting processor 1/1 ip 6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 4189.71 BogoMIPS (lpj=20948561)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.620223] CPU1: AMD Athlon(tm) X2 Dual Core Processor BE-2350 stepping 01
[    0.620241] Brought up 2 CPUs
[    0.620243] Total of 2 processors activated (8379.32 BogoMIPS).
[    0.620322] CPU0 attaching sched-domain:
[    0.620325]  domain 0: span 0-1 level CPU
[    0.620327]   groups: 0 1
[    0.620331]   domain 1: span 0-1 level NODE
[    0.620333]    groups: 0-1
[    0.620338] CPU1 attaching sched-domain:
[    0.620339]  domain 0: span 0-1 level CPU
[    0.620341]   groups: 1 0
[    0.620345]   domain 1: span 0-1 level NODE
[    0.620346]    groups: 0-1
[    0.620437] net_namespace: 1552 bytes
[    0.620437] Booting paravirtualized kernel on bare hardware
[    0.620437] Time:  9:45:28  Date: 04/02/09
[    0.620437] NET: Registered protocol family 16
[    0.620437] node 0 link 0: io port [1000, ffffff]
[    0.620437] node 0 link 0: io port [1000, 1fff]
[    0.620437] TOM: 0000000080000000 aka 2048M
[    0.620437] node 0 link 0: mmio [e0000000, efffffff]
[    0.620437] node 0 link 0: mmio [a0000, bffff]
[    0.620437] node 0 link 0: mmio [80000000, fe0bffff]
[    0.620437] bus: [00,07] on node 0 link 0
[    0.620437] bus: 00 index 0 io port: [0, ffff]
[    0.620437] bus: 00 index 1 mmio: [80000000, fcffffffff]
[    0.620437] bus: 00 index 2 mmio: [a0000, bffff]
[    0.620437] ACPI: bus type pci registered
[    0.620437] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.620437] PCI: Not using MMCONFIG.
[    0.620437] PCI: Using configuration type 1 for base access
[    0.620800] ACPI: EC: Look up EC in DSDT
[    0.638862] ACPI: Interpreter enabled
[    0.638865] ACPI: (supports S0 S1 S3 S4 S5)
[    0.638884] ACPI: Using IOAPIC for interrupt routing
[    0.638953] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.645959] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.658306] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.670215] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.670215] PCI: 0000:00:01.0 reg 10 io port: [1f00, 1fff]
[    0.670215] PCI: 0000:00:01.1 reg 10 io port: [cc00, cc3f]
[    0.670215] PCI: 0000:00:01.1 reg 20 io port: [1d00, 1d3f]
[    0.670215] PCI: 0000:00:01.1 reg 24 io port: [1e00, 1e3f]
[    0.670215] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.670215] pci 0000:00:01.1: PME# disabled
[    0.670225] PCI: 0000:00:01.3 reg 10 32bit mmio: [fe980000, fe9fffff]
[    0.670307] PCI: 0000:00:06.0 reg 20 io port: [ffa0, ffaf]
[    0.670353] PCI: 0000:00:09.0 reg 10 io port: [f80, f87]
[    0.670356] PCI: 0000:00:09.0 reg 14 io port: [f00, f03]
[    0.670359] PCI: 0000:00:09.0 reg 18 io port: [e80, e87]
[    0.670362] PCI: 0000:00:09.0 reg 1c io port: [e00, e03]
[    0.670366] PCI: 0000:00:09.0 reg 20 io port: [bc00, bc0f]
[    0.670369] PCI: 0000:00:09.0 reg 24 32bit mmio: [fe97c000, fe97dfff]
[    0.670402] PCI: 0000:00:0a.0 reg 10 32bit mmio: [fe97b000, fe97bfff]
[    0.670406] PCI: 0000:00:0a.0 reg 14 io port: [b880, b887]
[    0.670409] PCI: 0000:00:0a.0 reg 18 32bit mmio: [fe97ac00, fe97acff]
[    0.670413] PCI: 0000:00:0a.0 reg 1c 32bit mmio: [fe97a800, fe97a80f]
[    0.670428] pci 0000:00:0a.0: supports D1
[    0.670430] pci 0000:00:0a.0: supports D2
[    0.670432] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670436] pci 0000:00:0a.0: PME# disabled
[    0.670458] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670461] pci 0000:00:0b.0: PME# disabled
[    0.670483] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670485] pci 0000:00:0c.0: PME# disabled
[    0.670507] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670510] pci 0000:00:0d.0: PME# disabled
[    0.670531] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670534] pci 0000:00:0e.0: PME# disabled
[    0.670556] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670558] pci 0000:00:0f.0: PME# disabled
[    0.670580] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670583] pci 0000:00:10.0: PME# disabled
[    0.670608] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670611] pci 0000:00:11.0: PME# disabled
[    0.670623] PCI: 0000:00:12.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.670626] PCI: 0000:00:12.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.670632] PCI: 0000:00:12.0 reg 1c 64bit mmio: [fc000000, fcffffff]
[    0.670637] PCI: 0000:00:12.0 reg 30 32bit mmio: [fe940000, fe95ffff]
[    0.670733] PCI: 0000:01:08.0 reg 10 32bit mmio: [feaf0000, feafffff]
[    0.670797] PCI: 0000:01:0a.0 reg 10 64bit mmio: [feaefc00, feaefc7f]
[    0.670806] PCI: 0000:01:0a.0 reg 18 64bit mmio: [feae0000, feae7fff]
[    0.670811] PCI: 0000:01:0a.0 reg 20 io port: [dc00, dc0f]
[    0.670821] PCI: 0000:01:0a.0 reg 30 32bit mmio: [fea00000, fea7ffff]
[    0.670835] pci 0000:01:0a.0: supports D1
[    0.670837] pci 0000:01:0a.0: supports D2
[    0.670856] pci 0000:00:08.0: transparent bridge
[    0.670859] PCI: bridge 0000:00:08.0 io port: [d000, dfff]
[    0.670862] PCI: bridge 0000:00:08.0 32bit mmio: [fea00000, feafffff]
[    0.670933] PCI: 0000:03:00.0 reg 10 io port: [e800, e8ff]
[    0.670948] PCI: 0000:03:00.0 reg 18 64bit mmio: [febff000, febfffff]
[    0.670963] PCI: 0000:03:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.670977] pci 0000:03:00.0: supports D1
[    0.670979] pci 0000:03:00.0: supports D2
[    0.670980] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.670984] pci 0000:03:00.0: PME# disabled
[    0.671013] PCI: bridge 0000:00:0c.0 io port: [e000, efff]
[    0.671016] PCI: bridge 0000:00:0c.0 32bit mmio: [feb00000, febfffff]
[    0.671198] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.671749] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.671950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.672091] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.672232] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
[    0.672374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
[    0.672515] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR15._PRT]
[    0.672656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR16._PRT]
[    0.672797] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.690858] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *7 10 11 16 17 18 19)
[    0.690858] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 10 11 16 17 18 19) *0, disabled.
[    0.690977] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 *10 11 16 17 18 19)
[    0.691298] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11 16 17 18 19) *0, disabled.
[    0.691624] ACPI: PCI Interrupt Link [LNEA] (IRQs 5 7 10 *11 16 17 18 19)
[    0.691945] ACPI: PCI Interrupt Link [LNEB] (IRQs 5 7 10 11 16 17 18 19) *0, disabled.
[    0.692267] ACPI: PCI Interrupt Link [LNEC] (IRQs 5 7 10 11 16 17 18 19) *0, disabled.
[    0.692588] ACPI: PCI Interrupt Link [LNED] (IRQs 5 7 10 11 16 17 18 19) *0, disabled.
[    0.692921] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.693240] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *0, disabled.
[    0.693570] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *7
[    0.693890] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.694217] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.694543] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.694868] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *7
[    0.695194] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *15
[    0.695566] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.695893] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.696213] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *0, disabled.
[    0.696278] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.696278] pnp: PnP ACPI init
[    0.696278] ACPI: bus type pnp registered
[    0.702138] pnp: PnP ACPI: found 12 devices
[    0.702138] ACPI: ACPI bus type pnp unregistered
[    0.702138] PCI: Using ACPI for IRQ routing
[    0.770046] NET: Registered protocol family 8
[    0.770048] NET: Registered protocol family 20
[    0.770065] NetLabel: Initializing
[    0.770065] NetLabel:  domain hash size = 128
[    0.770065] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.770065] NetLabel:  unlabeled traffic allowed by default
[    0.772969] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.772972]    actual entries 65586
[    0.773121] AppArmor: AppArmor Filesystem Enabled
[    0.773150] ACPI: RTC can wake from S4
[    0.800036] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.800039] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.800042] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.800045] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.800048] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.800050] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.800053] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.800056] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.800059] system 00:04: ioport range 0x1c00-0x1c7f has been reserved
[    0.800061] system 00:04: ioport range 0x1c80-0x1cff has been reserved
[    0.800066] system 00:04: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.800069] system 00:04: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.800072] system 00:04: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.800081] system 00:06: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.800084] system 00:06: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.800093] system 00:09: ioport range 0x290-0x29f has been reserved
[    0.800104] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.800110] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.800113] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[    0.800116] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.800118] system 00:0b: iomem range 0x100000-0x7fffffff could not be reserved
[    0.800121] system 00:0b: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.804601] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.804605] pci 0000:00:08.0:   IO window: 0xd000-0xdfff
[    0.804609] pci 0000:00:08.0:   MEM window: 0xfea00000-0xfeafffff
[    0.804613] pci 0000:00:08.0:   PREFETCH window: 0x00000080000000-0x000000800fffff
[    0.804618] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.804620] pci 0000:00:0b.0:   IO window: disabled
[    0.804622] pci 0000:00:0b.0:   MEM window: disabled
[    0.804625] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.804629] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.804631] pci 0000:00:0c.0:   IO window: 0xe000-0xefff
[    0.804634] pci 0000:00:0c.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.804637] pci 0000:00:0c.0:   PREFETCH window: 0x00000080100000-0x000000801fffff
[    0.804641] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.804643] pci 0000:00:0d.0:   IO window: disabled
[    0.804645] pci 0000:00:0d.0:   MEM window: disabled
[    0.804648] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.804651] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:05
[    0.804653] pci 0000:00:0e.0:   IO window: disabled
[    0.804656] pci 0000:00:0e.0:   MEM window: disabled
[    0.804658] pci 0000:00:0e.0:   PREFETCH window: disabled
[    0.804662] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:06
[    0.804664] pci 0000:00:0f.0:   IO window: disabled
[    0.804666] pci 0000:00:0f.0:   MEM window: disabled
[    0.804669] pci 0000:00:0f.0:   PREFETCH window: disabled
[    0.804672] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.804674] pci 0000:00:10.0:   IO window: disabled
[    0.804677] pci 0000:00:10.0:   MEM window: disabled
[    0.804679] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.804683] pci 0000:00:11.0: PCI bridge, secondary bus 0000:08
[    0.804684] pci 0000:00:11.0:   IO window: disabled
[    0.804687] pci 0000:00:11.0:   MEM window: disabled
[    0.804689] pci 0000:00:11.0:   PREFETCH window: disabled
[    0.804700] pci 0000:00:08.0: setting latency timer to 64
[    0.804706] pci 0000:00:0b.0: setting latency timer to 64
[    0.804711] pci 0000:00:0c.0: setting latency timer to 64
[    0.804716] pci 0000:00:0d.0: setting latency timer to 64
[    0.804722] pci 0000:00:0e.0: setting latency timer to 64
[    0.804727] pci 0000:00:0f.0: setting latency timer to 64
[    0.804732] pci 0000:00:10.0: setting latency timer to 64
[    0.804737] pci 0000:00:11.0: setting latency timer to 64
[    0.804740] bus: 00 index 0 io port: [0, ffff]
[    0.804742] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.804744] bus: 01 index 0 io port: [d000, dfff]
[    0.804746] bus: 01 index 1 mmio: [fea00000, feafffff]
[    0.804749] bus: 01 index 2 mmio: [80000000, 800fffff]
[    0.804751] bus: 01 index 3 io port: [0, ffff]
[    0.804753] bus: 01 index 4 mmio: [0, ffffffffffffffff]
[    0.804755] bus: 02 index 0 mmio: [0, 0]
[    0.804757] bus: 02 index 1 mmio: [0, 0]
[    0.804759] bus: 02 index 2 mmio: [0, 0]
[    0.804761] bus: 02 index 3 mmio: [0, 0]
[    0.804762] bus: 03 index 0 io port: [e000, efff]
[    0.804764] bus: 03 index 1 mmio: [feb00000, febfffff]
[    0.804766] bus: 03 index 2 mmio: [80100000, 801fffff]
[    0.804768] bus: 03 index 3 mmio: [0, 0]
[    0.804770] bus: 04 index 0 mmio: [0, 0]
[    0.804772] bus: 04 index 1 mmio: [0, 0]
[    0.804773] bus: 04 index 2 mmio: [0, 0]
[    0.804775] bus: 04 index 3 mmio: [0, 0]
[    0.804777] bus: 05 index 0 mmio: [0, 0]
[    0.804779] bus: 05 index 1 mmio: [0, 0]
[    0.804780] bus: 05 index 2 mmio: [0, 0]
[    0.804782] bus: 05 index 3 mmio: [0, 0]
[    0.804784] bus: 06 index 0 mmio: [0, 0]
[    0.804786] bus: 06 index 1 mmio: [0, 0]
[    0.804787] bus: 06 index 2 mmio: [0, 0]
[    0.804789] bus: 06 index 3 mmio: [0, 0]
[    0.804791] bus: 07 index 0 mmio: [0, 0]
[    0.804792] bus: 07 index 1 mmio: [0, 0]
[    0.804794] bus: 07 index 2 mmio: [0, 0]
[    0.804796] bus: 07 index 3 mmio: [0, 0]
[    0.804798] bus: 08 index 0 mmio: [0, 0]
[    0.804799] bus: 08 index 1 mmio: [0, 0]
[    0.804801] bus: 08 index 2 mmio: [0, 0]
[    0.804803] bus: 08 index 3 mmio: [0, 0]
[    0.804817] NET: Registered protocol family 2
[    0.810019] Switched to high resolution mode on CPU 0
[    0.810186] Switched to high resolution mode on CPU 1
[    0.890138] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.891135] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.893216] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.893733] TCP: Hash tables configured (established 262144 bind 65536)
[    0.893736] TCP reno registered
[    0.920132] NET: Registered protocol family 1
[    0.920256] checking if image is initramfs... it is
[    1.651582] Freeing initrd memory: 9043k freed
[    1.658180] audit: initializing netlink socket (disabled)
[    1.658196] type=2000 audit(1238665528.650:1): initialized
[    1.663909] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.667392] VFS: Disk quotas dquot_6.5.1
[    1.667498] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.667625] msgmni has been set to 3952
[    1.667766] io scheduler noop registered
[    1.667768] io scheduler anticipatory registered
[    1.667770] io scheduler deadline registered (default)
[    1.667935] io scheduler cfq registered
[    1.667967] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.668033] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.668062] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.668077] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.668094] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.668110] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.668126] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.668142] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.668158] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.668174] pci 0000:00:11.0: Enabling HT MSI Mapping
[    1.668190] pci 0000:00:12.0: Boot video device
[    1.668329] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.668354] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.668378] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.668443] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.668533] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.668556] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.668575] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.668631] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.668722] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.668745] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.668763] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.668825] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.668917] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[    1.668940] pcieport-driver 0000:00:0e.0: found MSI capability
[    1.668959] pci_express 0000:00:0e.0:pcie00: allocate port service
[    1.669018] pci_express 0000:00:0e.0:pcie03: allocate port service
[    1.669108] pcieport-driver 0000:00:0f.0: setting latency timer to 64
[    1.669132] pcieport-driver 0000:00:0f.0: found MSI capability
[    1.669150] pci_express 0000:00:0f.0:pcie00: allocate port service
[    1.669210] pci_express 0000:00:0f.0:pcie03: allocate port service
[    1.669303] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.669327] pcieport-driver 0000:00:10.0: found MSI capability
[    1.669345] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.669405] pci_express 0000:00:10.0:pcie03: allocate port service
[    1.669494] pcieport-driver 0000:00:11.0: setting latency timer to 64
[    1.669517] pcieport-driver 0000:00:11.0: found MSI capability
[    1.669535] pci_express 0000:00:11.0:pcie00: allocate port service
[    1.669595] pci_express 0000:00:11.0:pcie03: allocate port service
[    1.721047] Linux agpgart interface v0.103
[    1.721053] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.724608] brd: module loaded
[    1.724708] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.724880] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.727335] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.727341] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.770571] mice: PS/2 mouse device common for all mice
[    1.770772] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.770807] rtc0: alarms up to one year, y3k
[    1.770885] cpuidle: using governor ladder
[    1.770887] cpuidle: using governor menu
[    1.771289] TCP cubic registered
[    1.771610] registered taskstats version 1
[    1.771768]   Magic number: 5:325:777
[    1.771939] rtc_cmos 00:05: setting system clock to 2009-04-02 09:45:29 UTC (1238665529)
[    1.771942] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.771944] EDD information not available.
[    1.771991] Freeing unused kernel memory: 536k freed
[    1.772295] Write protecting the kernel read-only data: 4344k
[    1.799497] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.867331] fuse init (API version 7.9)
[    1.887881] processor ACPI0007:00: registered as cooling_device0
[    1.887977] processor ACPI0007:01: registered as cooling_device1
[    1.903915] device-mapper: uevent: version 1.0.3
[    1.904187] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    1.923211] md: linear personality registered for level -1
[    1.927246] md: multipath personality registered for level -4
[    1.930925] md: raid0 personality registered for level 0
[    1.936083] md: raid1 personality registered for level 1
[    1.939454] xor: automatically using best checksumming function: generic_sse
[    1.981255]    generic_sse:  6440.400 MB/sec
[    1.981257] xor: using function: generic_sse (6440.400 MB/sec)
[    1.982651] async_tx: api initialized (async)
[    2.151268] raid6: int64x1   2047 MB/s
[    2.321264] raid6: int64x2   2731 MB/s
[    2.491270] raid6: int64x4   2554 MB/s
[    2.661276] raid6: int64x8   1852 MB/s
[    2.831271] raid6: sse2x1    2883 MB/s
[    3.001263] raid6: sse2x2    3957 MB/s
[    3.171256] raid6: sse2x4    4053 MB/s
[    3.171258] raid6: using algorithm sse2x4 (4053 MB/s)
[    3.171262] md: raid6 personality registered for level 6
[    3.171264] md: raid5 personality registered for level 5
[    3.171266] md: raid4 personality registered for level 4
[    3.191846] md: raid10 personality registered for level 10
[    3.487266] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.487844] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    3.487856] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    3.487861] forcedeth 0000:00:0a.0: setting latency timer to 64
[    3.495975] No dock devices found.
[    3.513888] SCSI subsystem initialized
[    3.538624] libata version 3.00 loaded.
[    4.020919] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:19:66:51:e4:79
[    4.020924] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    4.021142] ahci 0000:00:09.0: version 3.0
[    4.021769] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[    4.021781] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    4.021860] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    4.021864] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    4.021867] ahci 0000:00:09.0: setting latency timer to 64
[    4.022704] scsi0 : ahci
[    4.023092] scsi1 : ahci
[    4.023206] scsi2 : ahci
[    4.023316] scsi3 : ahci
[    4.023440] ata1: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22
[    4.023443] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22
[    4.023446] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22
[    4.023449] ata4: SATA max UDMA/133 abar m8192@0xfe97c000 port 0xfe97c280 irq 22
[    4.951277] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.979955] ata1.00: ATA-8: ST31000333AS, CC1H, max UDMA/133
[    4.979957] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.021884] ata1.00: configured for UDMA/133
[    5.950025] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.951923] ata2.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[    5.951926] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.953889] ata2.00: configured for UDMA/133
[    6.881274] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.901822] ata3.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[    6.901824] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.903798] ata3.00: configured for UDMA/133
[    7.250025] ata4: SATA link down (SStatus 0 SControl 300)
[    7.250146] scsi 0:0:0:0: Direct-Access     ATA      ST31000333AS     CC1H PQ: 0 ANSI: 5
[    7.250295] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    7.250408] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    7.251179] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    7.251815] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 19
[    7.251827] r8169 0000:03:00.0: PCI INT A -> Link[LNEA] -> GSI 19 (level, low) -> IRQ 19
[    7.251844] r8169 0000:03:00.0: setting latency timer to 64
[    7.252219] eth1: RTL8168b/8111b at 0xffffc20000332000, 00:21:27:c9:d2:17, XID 38000000 IRQ 2296
[    7.255932] sata_sil24 0000:01:0a.0: version 1.1
[    7.256549] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 18
[    7.256561] sata_sil24 0000:01:0a.0: PCI INT A -> Link[LNKC] -> GSI 18 (level, low) -> IRQ 18
[    7.257736] scsi4 : sata_sil24
[    7.257950] pata_acpi 0000:00:06.0: setting latency timer to 64
[    7.259317] scsi5 : sata_sil24
[    7.265419] scsi6 : sata_sil24
[    7.265546] scsi7 : sata_sil24
[    7.265589] ata5: SATA max UDMA/100 host m128@0xfeaefc00 port 0xfeae0000 irq 18
[    7.265593] ata6: SATA max UDMA/100 host m128@0xfeaefc00 port 0xfeae2000 irq 18
[    7.265597] ata7: SATA max UDMA/100 host m128@0xfeaefc00 port 0xfeae4000 irq 18
[    7.265600] ata8: SATA max UDMA/100 host m128@0xfeaefc00 port 0xfeae6000 irq 18
[    7.266017] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.266060] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    7.266099] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    7.286718] Driver 'sd' needs updating - please use bus_type methods
[    7.286874] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[    7.286902] sd 0:0:0:0: [sda] Write Protect is off
[    7.286904] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.286953] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.287046] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[    7.287071] sd 0:0:0:0: [sda] Write Protect is off
[    7.287073] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.287119] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.287123]  sda: sda1 sda2
[    7.291818] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.291940] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    7.291968] sd 1:0:0:0: [sdb] Write Protect is off
[    7.291971] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.292018] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.292097] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    7.292121] sd 1:0:0:0: [sdb] Write Protect is off
[    7.292124] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.292170] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.292173]  sdb: sdb1 sdb2 sdb3
[    7.309320] sd 1:0:0:0: [sdb] Attached SCSI disk
[    7.309442] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[    7.309470] sd 2:0:0:0: [sdc] Write Protect is off
[    7.309472] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.309520] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.309598] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[    7.309622] sd 2:0:0:0: [sdc] Write Protect is off
[    7.309624] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.309670] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.309674]  sdc: sdc1 sdc2 sdc3
[    7.344287] sd 2:0:0:0: [sdc] Attached SCSI disk
[    9.500037] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[    9.503100] ata5.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[    9.503105] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    9.505079] ata5.00: configured for UDMA/100
[   11.740037] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   11.746233] ata6.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[   11.746236] ata6.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   11.748243] ata6.00: configured for UDMA/100
[   13.830033] ata7: SATA link down (SStatus 0 SControl 0)
[   15.921279] ata8: SATA link down (SStatus 0 SControl 0)
[   15.921393] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   15.921581] scsi 4:0:0:0: Attached scsi generic sg3 type 0
[   15.924294] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   15.924432] scsi 5:0:0:0: Attached scsi generic sg4 type 0
[   15.927429] pata_amd 0000:00:06.0: version 0.3.10
[   15.927478] pata_amd 0000:00:06.0: setting latency timer to 64
[   15.927543] sd 4:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[   15.927580] sd 4:0:0:0: [sdd] Write Protect is off
[   15.927583] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   15.927600] scsi8 : pata_amd
[   15.927718] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.927799] scsi9 : pata_amd
[   15.930076] ata9: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   15.930079] ata10: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   15.931363] sd 4:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[   15.934196] sd 4:0:0:0: [sdd] Write Protect is off
[   15.934201] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   15.936403] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.936412]  sdd: sdd1 sdd2 sdd3
[   15.971772] sd 4:0:0:0: [sdd] Attached SCSI disk
[   15.971887] sd 5:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
[   15.971921] sd 5:0:0:0: [sde] Write Protect is off
[   15.971923] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[   15.971982] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.972076] sd 5:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
[   15.972107] sd 5:0:0:0: [sde] Write Protect is off
[   15.972110] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[   15.972166] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.972170]  sde: sde1 sde2 sde3
[   16.026905] sd 5:0:0:0: [sde] Attached SCSI disk
[   16.110364] ata9.00: ATAPI: PIONEER DVD-RW  DVR-111, 1.29, max UDMA/66
[   16.110377] ata9: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:900:0x11)
[   16.150272] ata9.00: configured for UDMA/66
[   16.150322] ata10: port disabled. ignoring.
[   16.150373] isa bounce pool size: 16 pages
[   16.156899] scsi 8:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-111  1.29 PQ: 0 ANSI: 5
[   16.157088] scsi 8:0:0:0: Attached scsi generic sg5 type 5
[   16.223128] Driver 'sr' needs updating - please use bus_type methods
[   16.247986] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   16.247992] Uniform CD-ROM driver Revision: 3.20
[   16.248128] sr 8:0:0:0: Attached scsi CD-ROM sr0
[   16.634858] PM: Starting manual resume from disk
[   16.634863] PM: Resume from partition 254:0
[   16.634864] PM: Checking hibernation image.
[   16.635070] PM: Resume from disk failed.
[   16.674022] kjournald starting.  Commit interval 5 seconds
[   16.674050] EXT3-fs: mounted filesystem with ordered data mode.
[   18.907465] udevd version 124 started
[   19.250980] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   19.301334] ACPI: Power Button (FF) [PWRF]
[   19.301477] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   19.381336] ACPI: Power Button (CM) [PWRB]
[   19.744427] ACPI: WMI: Mapper loaded
[   20.224598] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.255749] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.447817] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   21.115525] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   22.387848] loop: module loaded
[   22.456044] lp: driver loaded but no devices found
[   22.726577] Adding 1048568k swap on /dev/mapper/single-swap.  Priority:-1 extents:1 across:1048568k
[   23.062288] EXT3 FS on dm-1, internal journal
[   23.983308] kjournald starting.  Commit interval 5 seconds
[   23.984165] EXT3 FS on sda1, internal journal
[   23.984173] EXT3-fs: mounted filesystem with ordered data mode.
[   24.016012] kjournald starting.  Commit interval 5 seconds
[   24.017594] EXT3 FS on dm-2, internal journal
[   24.017602] EXT3-fs: mounted filesystem with ordered data mode.
[   24.347168] type=1505 audit(1238665552.022:2): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4253
[   24.395274] type=1505 audit(1238665552.072:3): operation="profile_load" name="/usr/sbin/named" name2="default" pid=4257
[   24.524233] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.787656] PPP generic driver version 2.4.2
[   24.811887] NET: Registered protocol family 17
[   24.852020] NET: Registered protocol family 10
[   24.852521] lo: Disabled Privacy Extensions
[   25.138395] NET: Registered protocol family 24
[   25.179101] r8169: eth1: link up
[   25.179121] r8169: eth1: link up
[   25.326632] Bridge firewalling registered
[   25.327699] br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   25.331168] device eth1 entered promiscuous mode
[   25.384357] br0: port 1(eth1) entering learning state
[   35.240016] eth1: no IPv6 routers present
[   35.491265] br0: no IPv6 routers present
[   35.600015] eth0: no IPv6 routers present
[   40.380015] br0: topology change detected, propagating
[   40.380021] br0: port 1(eth1) entering forwarding state
[   40.691517] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   40.691694] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   40.691696] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   40.691698] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   62.377132] type=1503 audit(1238665590.051:4): operation="capable" name="sys_resource" pid=5064 profile="/usr/sbin/named"
[   62.377413] type=1503 audit(1238665590.051:5): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=104 name="/proc/5063/net/if_inet6" pid=5064 profile="/usr/sbin/named"
[   65.280701] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)

```

---

### Post by dcstar on 2009-04-02
> **infirmus said:**
> I'm running Ubuntu 8.10 Intrepid server and every time I boot it goes to the "Recovery menu" and I have to press enter to resume normal boot. It is really annoying because I cant remotely reboot the server. Has anyone else experienced this or know a fix?
.........

Boot off a Live CD and fsck the root partition.

---

