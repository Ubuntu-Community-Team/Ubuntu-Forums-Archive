---
title: "Jaunty, nautilus can't open &quot;Computer&quot; or mount drives!"
date: 2009-05-13
forum: General Help
---

### Post by Black_Wolf_92 on 2009-05-13
When I click Places/Computer

I get the error

> Nautilus cannot handle "computer" locations

Also no remove drives (ipods, usbs, other partitions) are not being mounted anymore. From my memory, they were originally, so something has been changed since the clean install (upgraded etc) to make this happen.

Thanks to anyone who can help me!

---

### Post by Peter09 on 2009-05-13
Go to a terminal and enter

```
dmesg | more
```

scroll through and look for errors

---

### Post by Black_Wolf_92 on 2009-05-13
This is the full output to that. I don't think i see many OBVIOUS errors. Hopefully someone can help me out here though!


> 
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.
3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 
2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfff0000 (usable)
[    0.000000]  BIOS-e820: 00000000dfff0000 - 00000000dfff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfff3000 - 00000000e0000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xdfff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000dfff0000 (usable)
[    0.000000]  modified: 00000000dfff0000 - 00000000dfff3000 (ACPI NVS)
[    0.000000]  modified: 00000000dfff3000 - 00000000e0000000 (ACPI data)
[    0.000000]  modified: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bf000 - 37fef05d
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb105d
[    0.000000] Move RAMDISK from 00000000378bf000 - 0000000037fef05c to 00881000
 - 00fb105c
[    0.000000] ACPI: RSDP 000F6250, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT DFFF3000, 0038 (r1 GBT    NVDAACPI 42302E31 NVDA  1010
101)
[    0.000000] ACPI: FACP DFFF3040, 0074 (r1 GBT    NVDAACPI 42302E31 NVDA  1010
101)
[    0.000000] ACPI: DSDT DFFF30C0, 43ED (r1 GBT    NVDAACPI     1000 MSFT  1000
00C)
[    0.000000] ACPI: FACS DFFF0000, 0040
[    0.000000] ACPI: SSDT DFFF7580, 02CC (r1 PTLTD  POWERNOW        1  LTP      
  1)
[    0.000000] ACPI: HPET DFFF7880, 0038 (r1 GBT    NVDAACPI 42302E31 NVDA      
 98)
[    0.000000] ACPI: MCFG DFFF78C0, 003C (r1 GBT    NVDAACPI 42302E31 NVDA  1010
101)
[    0.000000] ACPI: APIC DFFF74C0, 0098 (r1 GBT    NVDAACPI 42302E31 NVDA  1010
101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2699MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 -
 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 -
 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 -
 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 -
 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 -
 0000881000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 -
 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 -
 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb105d]      NEW RAMDISK ==> [0000881000 -
 0000fb105d]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 -
 0000019000]
[    0.000000] found SMP MP-table at [c00f4880] 000f4880
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000dfff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x000dfff0
[    0.000000] On node 0 totalpages: 917365
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c100000
0
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 5400 pages used for memmap
[    0.000000]   HighMem zone: 685786 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e1000000 (gap: e0000000:1000
0000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pag
es: 910197
[    0.000000] Kernel command line: root=UUID=b2ae26b8-f2d0-428d-ae62-1eddfe281d
a4 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2712.250 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 18349760 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3605848k/3669952k available (4126k kernel code, 62708k re
served, 2208k data, 532k init, 2764744k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor 
mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, N
odes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer fr
equency.. 5424.50 BogoMIPS (lpj=10849000)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.352160] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
[    0.352205] Brought up 2 CPUs
[    0.352207] Total of 2 processors activated (10849.19 BogoMIPS).
[    0.352271] CPU0 attaching sched-domain:
[    0.352273]  domain 0: span 0-1 level CPU
[    0.352275]   groups: 0 1
[    0.352279] CPU1 attaching sched-domain:
[    0.352280]  domain 0: span 0-1 level CPU
[    0.352282]   groups: 1 0
[    0.352331] net_namespace: 776 bytes
[    0.352331] Booting paravirtualized kernel on bare hardware
[    0.352331] Time: 19:39:58  Date: 05/13/09
[    0.352331] regulator: core version 0.5
[    0.352331] NET: Registered protocol family 16
[    0.352331] EISA bus registered
[    0.352331] ACPI: bus type pci registered
[    0.352331] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.352331] PCI: MCFG area at f0000000 reserved in E820
[    0.352331] PCI: Using MMCONFIG for extended config space
[    0.352331] PCI: Using configuration type 1 for base access
[    0.352856] ACPI: EC: Look up EC in DSDT
[    0.359936] ACPI: Interpreter enabled
[    0.359939] ACPI: (supports S0 S1 S4 S5)
[    0.359953] ACPI: Using IOAPIC for interrupt routing
[    0.365765] ACPI: No dock devices found.
[    0.365773] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.365941] pci 0000:00:01.1: reg 10 io port: [0xe000-0xe03f]
[    0.365950] pci 0000:00:01.1: reg 20 io port: [0x1c00-0x1c3f]
[    0.365953] pci 0000:00:01.1: reg 24 io port: [0xc400-0xc43f]
[    0.365963] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.365967] pci 0000:00:01.1: PME# disabled
[    0.366006] pci 0000:00:02.0: reg 10 32bit mmio: [0xfc106000-0xfc106fff]
[    0.366022] pci 0000:00:02.0: supports D1 D2
[    0.366023] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.366026] pci 0000:00:02.0: PME# disabled
[    0.366044] pci 0000:00:02.1: reg 10 32bit mmio: [0xfc107000-0xfc1070ff]
[    0.366061] pci 0000:00:02.1: supports D1 D2
[    0.366062] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.366065] pci 0000:00:02.1: PME# disabled
[    0.366111] pci 0000:00:05.0: reg 10 32bit mmio: [0xfc100000-0xfc103fff]
[    0.366127] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.366129] pci 0000:00:05.0: PME# disabled
[    0.366157] pci 0000:00:06.0: reg 20 io port: [0xf000-0xf00f]
[    0.366183] pci 0000:00:07.0: reg 10 32bit mmio: [0xfc104000-0xfc104fff]
[    0.366186] pci 0000:00:07.0: reg 14 io port: [0xc800-0xc807]
[    0.366198] pci 0000:00:07.0: supports D1 D2
[    0.366199] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.366202] pci 0000:00:07.0: PME# disabled
[    0.366219] pci 0000:00:08.0: reg 10 io port: [0x9f0-0x9f7]
[    0.366222] pci 0000:00:08.0: reg 14 io port: [0xbf0-0xbf3]
[    0.366225] pci 0000:00:08.0: reg 18 io port: [0x970-0x977]
[    0.366228] pci 0000:00:08.0: reg 1c io port: [0xb70-0xb73]
[    0.366231] pci 0000:00:08.0: reg 20 io port: [0xdc00-0xdc0f]
[    0.366234] pci 0000:00:08.0: reg 24 32bit mmio: [0xfc105000-0xfc105fff]
[    0.366262] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.366264] pci 0000:00:09.0: PME# disabled
[    0.366355] pci 0000:01:07.0: reg 10 32bit mmio: [0xfc000000-0xfc00ffff]
[    0.366360] pci 0000:01:07.0: reg 14 32bit mmio: [0xfc010000-0xfc01ffff]
[    0.366408] pci 0000:00:04.0: transparent bridge
[    0.366412] pci 0000:00:04.0: bridge 32bit mmio: [0xfc000000-0xfc0fffff]
[    0.366432] pci 0000:02:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.366439] pci 0000:02:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.366445] pci 0000:02:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.366449] pci 0000:02:00.0: reg 24 io port: [0xb000-0xb07f]
[    0.366453] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.366491] pci 0000:00:09.0: bridge io port: [0xb000-0xbfff]
[    0.366494] pci 0000:00:09.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
[    0.366497] pci 0000:00:09.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.366501] bus 00 -> node 0
[    0.366506] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.366724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.389508] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[    0.389626] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[    0.389742] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.389858] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.389974] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.390091] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.390207] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.390324] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.390440] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.390556] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.390674] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.390791] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.390908] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.391024] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.391142] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.391259] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.391375] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.391493] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.391608] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.391759] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.391902] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.392053] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.392200] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.392343] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.392486] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.392629] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.392772] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.392915] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[    0.393059] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.393202] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.393345] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.393489] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.393633] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.393787] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.393930] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.394074] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.394219] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.394362] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.394470] ACPI: WMI: Mapper loaded
[    0.394518] SCSI subsystem initialized
[    0.394518] libata version 3.00 loaded.
[    0.394518] usbcore: registered new interface driver usbfs
[    0.394518] usbcore: registered new interface driver hub
[    0.394518] usbcore: registered new device driver usb
[    0.394518] PCI: Using ACPI for IRQ routing
[    0.400008] Bluetooth: Core ver 2.13
[    0.400021] NET: Registered protocol family 31
[    0.400021] Bluetooth: HCI device and connection manager initialized
[    0.400021] Bluetooth: HCI socket layer initialized
[    0.400021] NET: Registered protocol family 8
[    0.400021] NET: Registered protocol family 20
[    0.400025] NetLabel: Initializing
[    0.400026] NetLabel:  domain hash size = 128
[    0.400027] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.400038] NetLabel:  unlabeled traffic allowed by default
[    0.400050] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.400054] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.404055] AppArmor: AppArmor Filesystem Enabled
[    0.408012] Switched to high resolution mode on CPU 0
[    0.408216] Switched to high resolution mode on CPU 1
[    0.412013] pnp: PnP ACPI init
[    0.412021] ACPI: bus type pnp registered
[    0.415387] pnp: PnP ACPI: found 15 devices
[    0.415389] ACPI: ACPI bus type pnp unregistered
[    0.415391] PnPBIOS: Disabled by ACPI PNP
[    0.415399] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.415401] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.415403] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.415405] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.415407] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.415408] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.415411] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.415413] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[    0.415417] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.415419] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.415421] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.415423] system 00:02: ioport range 0x290-0x294 has been reserved
[    0.415430] system 00:0d: iomem range 0xf0000000-0xf7ffffff has been reserved
[    0.415434] system 00:0e: iomem range 0xd1800-0xd3fff has been reserved
[    0.415436] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[    0.415438] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[    0.415440] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[    0.415442] system 00:0e: iomem range 0xdfff0000-0xdfffffff could not be reserved
[    0.415444] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
[    0.415446] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.415448] system 00:0e: iomem range 0x100000-0xdffeffff could not be reserved
[    0.415450] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.415452] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.450108] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.450109] pci 0000:00:04.0:   IO window: disabled
[    0.450113] pci 0000:00:04.0:   MEM window: 0xfc000000-0xfc0fffff
[    0.450115] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.450120] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.450122] pci 0000:00:09.0:   IO window: 0xb000-0xbfff
[    0.450124] pci 0000:00:09.0:   MEM window: 0xf8000000-0xfbffffff
[    0.450126] pci 0000:00:09.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.450133] pci 0000:00:04.0: setting latency timer to 64
[    0.450137] pci 0000:00:09.0: setting latency timer to 64
[    0.450139] bus: 00 index 0 io port: [0x00-0xffff]
[    0.450141] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.450142] bus: 01 index 0 mmio: [0x0-0x0]
[    0.450144] bus: 01 index 1 mmio: [0xfc000000-0xfc0fffff]
[    0.450145] bus: 01 index 2 mmio: [0x0-0x0]
[    0.450147] bus: 01 index 3 io port: [0x00-0xffff]
[    0.450148] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.450150] bus: 02 index 0 io port: [0xb000-0xbfff]
[    0.450151] bus: 02 index 1 mmio: [0xf8000000-0xfbffffff]
[    0.450153] bus: 02 index 2 mmio: [0xe0000000-0xefffffff]
[    0.450154] bus: 02 index 3 mmio: [0x0-0x0]
[    0.450162] NET: Registered protocol family 2
[    0.464051] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.464268] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.464774] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.465039] TCP: Hash tables configured (established 131072 bind 65536)
[    0.465041] TCP reno registered
[    0.472080] NET: Registered protocol family 1
[    0.472172] checking if image is initramfs... it is
[    0.898742] Freeing initrd memory: 7360k freed
[    0.898895] cpufreq: No nForce2 chipset.
[    0.898991] audit: initializing netlink socket (disabled)
[    0.899006] type=2000 audit(1242243597.896:1): initialized
[    0.904948] highmem bounce pool size: 64 pages
[    0.904952] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.905852] VFS: Disk quotas dquot_6.5.1
[    0.905891] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.906334] fuse init (API version 7.10)
[    0.906393] msgmni has been set to 1658
[    0.906546] alg: No test for stdrng (krng)
[    0.906556] io scheduler noop registered
[    0.906558] io scheduler anticipatory registered
[    0.906559] io scheduler deadline registered
[    0.906571] io scheduler cfq registered (default)
[    0.906599] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.906690] pci 0000:00:04.0: Enabling HT MSI Mapping
[    0.906704] pci 0000:00:05.0: Enabling HT MSI Mapping
[    0.906729] pci 0000:00:07.0: Enabling HT MSI Mapping
[    0.906742] pci 0000:00:08.0: Enabling HT MSI Mapping
[    0.906755] pci 0000:00:09.0: Enabling HT MSI Mapping
[    0.906776] pci 0000:02:00.0: Boot video device
[    0.910771] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    0.910790] pcieport-driver 0000:00:09.0: found MSI capability
[    0.910803] pcieport-driver 0000:00:09.0: irq 2303 for MSI/MSI-X
[    0.910808] pci_express 0000:00:09.0:pcie00: allocate port service
[    0.910819] pci_express 0000:00:09.0:pcie03: allocate port service
[    0.910853] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.910860] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.910969] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.910971] ACPI: Power Button (FF) [PWRF]
[    0.911002] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.911004] ACPI: Power Button (CM) [PWRB]
[    0.911219] processor ACPI_CPU:00: registered as cooling_device0
[    0.911244] processor ACPI_CPU:01: registered as cooling_device1
[    0.913625] isapnp: Scanning for PnP cards...
[    1.266221] isapnp: No Plug & Play device found
[    1.272674] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.272755] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.272993] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.273581] brd: module loaded
[    1.273828] loop: module loaded
[    1.273878] Fixed MDIO Bus: probed
[    1.273882] PPP generic driver version 2.4.2
[    1.273929] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.273950] Driver 'sd' needs updating - please use bus_type methods
[    1.273957] Driver 'sr' needs updating - please use bus_type methods
[    1.274089] sata_nv 0000:00:08.0: version 3.5
[    1.274362] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.274369] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.274411] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.274467] scsi0 : sata_nv
[    1.274542] scsi1 : sata_nv
[    1.274654] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 23
[    1.274656] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 23
[    1.740033] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.756601] ata1.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    1.756606] ata1.00: ATA-7: ST3250310AS, 4.AAA, max UDMA/133
[    1.756608] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.772208] ata1.00: configured for UDMA/133
[    2.240030] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.248108] ata2.00: ATAPI: PIONEER DVD-RW  DVR-216, 1.08, max UDMA/66
[    2.264119] ata2.00: configured for UDMA/66
[    2.264462] scsi 0:0:0:0: Direct-Access     ATA      ST3250310AS      4.AA PQ: 0 ANSI: 5
[    2.264539] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.264552] sd 0:0:0:0: [sda] Write Protect is off
[    2.264554] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.264572] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.264630] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.264641] sd 0:0:0:0: [sda] Write Protect is off
[    2.264643] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.264660] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.264663]  sda: sda1 sda2 sda3 sda4
[    2.314301] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.314340] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.345712] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-216  1.08 PQ: 0 ANSI: 5
[    2.440067] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.440069] Uniform CD-ROM driver Revision: 3.20
[    2.440133] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.440159] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.440226] pata_amd 0000:00:06.0: version 0.3.10
[    2.440257] pata_amd 0000:00:06.0: setting latency timer to 64
[    2.440324] scsi2 : pata_amd
[    2.440373] scsi3 : pata_amd
[    2.440844] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    2.440846] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    2.606922] ata4: port disabled. ignoring.
[    2.607263] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.607518] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    2.607523] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    2.607538] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.607540] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.607584] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    2.607605] ehci_hcd 0000:00:02.1: debug port 1
[    2.607608] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.607620] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfc107000
[    2.616015] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    2.616069] usb usb1: configuration #1 chosen from 1 choice
[    2.616088] hub 1-0:1.0: USB hub found
[    2.616095] hub 1-0:1.0: 10 ports detected
[    2.616177] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.616420] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    2.616423] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    2.616430] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.616432] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.616466] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    2.616482] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfc106000
[    2.674033] usb usb2: configuration #1 chosen from 1 choice
[    2.674050] hub 2-0:1.0: USB hub found
[    2.674057] hub 2-0:1.0: 10 ports detected
[    2.674131] uhci_hcd: USB Universal Host Controller Interface driver
[    2.674176] usbcore: registered new interface driver libusual
[    2.674201] usbcore: registered new interface driver usbserial
[    2.674209] USB Serial support registered for generic
[    2.674218] usbcore: registered new interface driver usbserial_generic
[    2.674220] usbserial: USB Serial Driver core
[    2.674255] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.674582] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.674586] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.676536] mice: PS/2 mouse device common for all mice
[    2.688562] rtc_cmos 00:05: RTC can wake from S4
[    2.688588] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.688621] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.688668] device-mapper: uevent: version 1.0.3
[    2.688750] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.688866] device-mapper: multipath: version 1.0.5 loaded
[    2.688868] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.688943] EISA: Probing bus 0 at eisa.0
[    2.688948] Cannot allocate resource for EISA slot 1
[    2.688964] EISA: Detected 0 cards.
[    2.689039] cpuidle: using governor ladder
[    2.689041] cpuidle: using governor menu
[    2.689410] TCP cubic registered
[    2.689479] NET: Registered protocol family 10
[    2.689788] lo: Disabled Privacy Extensions
[    2.690012] NET: Registered protocol family 17
[    2.690026] Bluetooth: L2CAP ver 2.11
[    2.690028] Bluetooth: L2CAP socket layer initialized
[    2.690030] Bluetooth: SCO (Voice Link) ver 0.6
[    2.690031] Bluetooth: SCO socket layer initialized
[    2.690065] Bluetooth: RFCOMM socket layer initialized
[    2.690071] Bluetooth: RFCOMM TTY layer initialized
[    2.690073] Bluetooth: RFCOMM ver 1.10
[    2.690114] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ processors (2 cpu cores) (version 2.20.00)
[    2.690164] powernow-k8:    0 : fid 0x13 (2700 MHz), vid 0x9
[    2.690165] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0xa
[    2.690167] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xc
[    2.690169] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0xe
[    2.690170] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0x10
[    2.690172] powernow-k8:    5 : fid 0xa (1800 MHz), vid 0x10
[    2.690173] powernow-k8:    6 : fid 0x2 (1000 MHz), vid 0x12
[    2.690222] Using IPI No-Shortcut mode
[    2.690293] registered taskstats version 1
[    2.690387]   Magic number: 9:119:698
[    2.690394] block sr0: hash matches
[    2.690479] rtc_cmos 00:05: setting system clock to 2009-05-13 19:40:00 UTC (1242243600)
[    2.690482] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.690483] EDD information not available.
[    2.690751] Freeing unused kernel memory: 532k freed
[    2.690863] Write protecting the kernel text: 4128k
[    2.690901] Write protecting the kernel read-only data: 1532k
[    2.706281] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.864436] Floppy drive(s): fd0 is 1.44M
[    2.884068] FDC 0 is a post-1991 82077
[    2.889672] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.889950] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    2.889958] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    2.889962] forcedeth 0000:00:07.0: setting latency timer to 64
[    2.975046] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.105446] usb 1-2: configuration #1 chosen from 1 choice
[    3.408903] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:d0:cc:09:1f
[    3.408907] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    3.471048] PM: Starting manual resume from disk
[    3.471051] PM: Resume from partition 8:4
[    3.471053] PM: Checking hibernation image.
[    3.471155] PM: Resume from disk failed.
[    3.497785] kjournald starting.  Commit interval 5 seconds
[    3.497793] EXT3-fs: mounted filesystem with ordered data mode.
[    7.563648] udev: starting version 141
[    7.818456] parport_pc 00:0a: reported by Plug and Play ACPI
[    7.818500] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.839031] ppdev: user-space parallel port driver
[    8.025042] Linux agpgart interface v0.103
[    8.232537] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    8.238391] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[    8.238405] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xc400
[    8.264380] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[    8.758726] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[    8.758735] nvidia 0000:02:00.0: PCI INT A -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
[    8.758741] nvidia 0000:02:00.0: setting latency timer to 64
[    8.759722] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.37.05  Thu Apr 30 14:10:53 PDT 2009
[    8.772360] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[    8.772857] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    8.772865] ndiswrapper 0000:01:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    8.773694] ndiswrapper: using IRQ 17
[    8.873771] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    8.961876] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[    8.961881] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[    8.961938] HDA Intel 0000:00:05.0: setting latency timer to 64
[    9.032543] wlan0: ethernet device 00:1e:2a:cc:55:a8 using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[    9.032555] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[    9.034077] usbcore: registered new interface driver ndiswrapper
[    9.325193] psmouse serio1: ID: 10 00 64<6>lp0: using parport0 (interrupt-driven).
[    9.736029] Adding 4297376k swap on /dev/sda4.  Priority:-1 extents:1 across:4297376k
[    9.824321] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   10.265289] EXT3 FS on sda2, internal journal
[   11.063210] kjournald starting.  Commit interval 5 seconds
[   11.063383] EXT3 FS on sda3, internal journal
[   11.063387] EXT3-fs: mounted filesystem with ordered data mode.
[   11.280121] type=1505 audit(1242207609.089:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1995
[   11.320160] type=1505 audit(1242207609.129:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1999
[   11.320268] type=1505 audit(1242207609.129:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1999
[   11.320309] type=1505 audit(1242207609.129:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1999
[   11.320343] type=1505 audit(1242207609.129:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1999
[   11.433589] type=1505 audit(1242207609.241:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2004
[   11.433747] type=1505 audit(1242207609.241:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2004
[   11.456725] type=1505 audit(1242207609.265:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2008
[   13.666466] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.666469] Bluetooth: BNEP filters: protocol multicast
[   13.686912] Bridge firewalling registered
[   19.191194] forcedeth 0000:00:07.0: irq 2302 for MSI/MSI-X
[   19.191399] eth0: no link during initialization.
[   19.191822] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.190813] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.200951] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.408012] wlan0: no IPv6 routers present
[   43.488652] type=1503 audit(1242207641.297:10): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/usr/local/lib/libgthread-2.0.so.0.2000.1" pid=3208 profile="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   43.488856] type=1503 audit(1242207641.297:11): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/usr/local/lib/libgobject-2.0.so.0.2000.1" pid=3208 profile="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   43.488934] type=1503 audit(1242207641.297:12): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/usr/local/lib/libglib-2.0.so.0.2000.1" pid=3208 profile="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   47.992837] end_request: I/O error, dev fd0, sector 0
[   60.161073] end_request: I/O error, dev fd0, sector 0
[   60.161080] Buffer I/O error on device fd0, logical block 0
[   64.274383] type=1503 audit(1242207662.082:13): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/usr/local/lib/libgthread-2.0.so.0.2000.1" pid=3240 profile="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   64.274553] type=1503 audit(1242207662.082:14): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/usr/local/lib/libgobject-2.0.so.0.2000.1" pid=3240 profile="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   64.274615] type=1503 audit(1242207662.082:15): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/usr/local/lib/libglib-2.0.so.0.2000.1" pid=3240 profile="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   72.336861] end_request: I/O error, dev fd0, sector 0
[   72.336868] Buffer I/O error on device fd0, logical block 0
[   79.500023] Clocksource tsc unstable (delta = -242149451 ns)
[   84.513614] end_request: I/O error, dev fd0, sector 0
[   96.689491] end_request: I/O error, dev fd0, sector 0
[  108.897860] end_request: I/O error, dev fd0, sector 0
[  108.897875] Buffer I/O error on device fd0, logical block 0
[  121.072878] end_request: I/O error, dev fd0, sector 0
[  121.072893] Buffer I/O error on device fd0, logical block 0
[  133.249599] end_request: I/O error, dev fd0, sector 0
[  145.420684] end_request: I/O error, dev fd0, sector 2
[  145.420717] EXT4-fs: unable to read superblock
[  157.592745] end_request: I/O error, dev fd0, sector 0

---

### Post by Peter09 on 2009-05-13
At the bottom dev/fd0 is showing errors.

What output from

```
df -h
```
and
```
fdisk -l
```

---

### Post by Black_Wolf_92 on 2009-05-13
df -h

> Filesystem            Size Used Avail Use% Mounted on
/dev/sda2              19G  3.1G   15G  18% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  104K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  144K  1.8G   1% /dev
tmpfs                 1.8G   76K  1.8G   1% /dev/shm
lrm                   1.8G  2.4M  1.8G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda3             150G   22G  120G  16% /home



and fdisk -l

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1aa04a5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2           27435       29866    19535040   83  Linux
/dev/sda3            7650       27434   158923012+  83  Linux
/dev/sda4           29867       30401     4297387+  82  Linux swap / Solaris

Partition table entries are not in disk order



Worth saying my partitions are like this.
Windows partition
Linux Ubuntu partition
Share/Home partition
Swap Partition


Also, my HOME partition is mounting fine, i can access all those files, however, i'm positive that the windows partition (72.2gb MEDIA for example can't remember exact size) used to show up as well. No usbs mount as well as i mentioned, and i can't access Network, Computer, Cd Roms from places menu

---

### Post by Peter09 on 2009-05-13
Did you upgrade or was it a complete install?

What is the content of

/etc/fstab?

---

### Post by Black_Wolf_92 on 2009-05-13
it was a complete new install. I've done a lot of work mounting different disks etc with fstab, and i don't think thats the problem. I THINK if anything it happened while i was installing gtk and gt4 toolkits. I was compiling from source a lot etc, and thats the last thing i remember doing before i couldn't access it.

It might be easier to just do a re-install though, i havn't done much on Jaunty, i'll just have to re-install a few packages, but its all working on the live CD, so i know that it'll work again on a clean install, I just wish i knew what went wrong.

Anyway here is the other content if it helps

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=b2ae26b8-f2d0-428d-ae62-1eddfe281da4 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=5effd05a-2827-4ab7-adfb-19ddebd77dea /home           ext3    relatime        0       2
# swap was on /dev/sda4 during installation
UUID=757fb532-6706-4811-a1a3-e715480e9dd9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Peter09 on 2009-05-13
Yes - I donot think its your drives but your config. I bet if you created a new user it would work ok.

You could try deleting .gconf  - it should then setup from scratch again when you login.

---

### Post by Black_Wolf_92 on 2009-05-13
wow thanks a lot peter, that did the trick. Must have messed up a config file somewhere, or got corrupted.

Thanks a lot, its people like you that keep the ubuntu community above everyone else. Cheers ;)

---

