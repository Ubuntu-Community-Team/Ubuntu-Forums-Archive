---
title: "missing devices in /dev"
date: 2009-05-25
forum: General Help
---

### Post by ant2ne on 2009-05-25
```
$ ls /dev/sd*
/dev/sda  /dev/sdb
$ ls /dev/md*
/dev/md0  /dev/md1  /dev/md2  /dev/md3

```
md0 is made from sda0 and sdb0
md1 is made from sda1 and sdb1 and so on

I can not
> $ sudo mdadm /dev/md0 --add /dev/sda0
mdadm: cannot find /dev/sda0: No such file or directory
Because sda0 does not exist, md0 does though. Which would normally mean that the disk sda is missing. But there is no sdb0 either. And they can't both be missing (RAID1).

Where are these devices? How do I add them back into the arry?

---

### Post by regala on 2009-05-25
> **ant2ne said:**
> ```
$ ls /dev/sd*
/dev/sda  /dev/sdb
$ ls /dev/md*
/dev/md0  /dev/md1  /dev/md2  /dev/md3

```
md0 is made from sda0 and sdb0
md1 is made from sda1 and sdb1 and so on

I can not
Because sda0 does not exist, md0 does though. Which would normally mean that the disk sda is missing. But there is no sdb0 either. And they can't both be missing (RAID1).

Where are these devices? How do I add them back into the arry?

post your dmesg (run dmesg in a terminal and post the output here) please

br, mathieu

---

### Post by ant2ne on 2009-05-25
here is dmesg> [    0.000000] BIOS EBDA/lowmem at: 0009b800/0009b800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=/dev/md1 ro quiet splash pci=noacpi 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009fef0000 (usable)
[    0.000000]  BIOS-e820: 000000009fef0000 - 000000009fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fef3000 - 000000009ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000260000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x260000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0x9fef0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009b800 (usable)
[    0.000000]  modified: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000009fef0000 (usable)
[    0.000000]  modified: 000000009fef0000 - 000000009fef3000 (ACPI NVS)
[    0.000000]  modified: 000000009fef3000 - 000000009ff00000 (ACPI data)
[    0.000000]  modified: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000260000000 (usable)
[    0.000000] init_memory_mapping: 0000000000000000-000000009fef0000
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000]  009fe00000 - 009fef0000 page 4k
[    0.000000] kernel direct mapping tables up to 9fef0000 @ 10000-15000
[    0.000000] last_map_addr: 9fef0000 end: 9fef0000
[    0.000000] init_memory_mapping: 0000000100000000-0000000260000000
[    0.000000]  0100000000 - 0260000000 page 2M
[    0.000000] kernel direct mapping tables up to 260000000 @ 13000-1e000
[    0.000000] last_map_addr: 260000000 end: 260000000
[    0.000000] RAMDISK: 377f1000 - 37fef600
[    0.000000] ACPI: RSDP 000F7F20, 0014 (r0 XFX68L)
[    0.000000] ACPI: RSDT 9FEF3040, 0038 (r1 XFX68L NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP 9FEF30C0, 0074 (r1 XFX68L NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: DSDT 9FEF3180, 5271 (r1 XFX68L NVDAACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 9FEF0000, 0040
[    0.000000] ACPI: HPET 9FEF8540, 0038 (r1 XFX68L NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: WDRT 9FEF85C0, 0047 (r1 XFX68L NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: MCFG 9FEF8680, 003C (r1 XFX68L NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC 9FEF8440, 0098 (r1 XFX68L NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0260000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [00377f1000 - 0037fef600]          RAMDISK ==> [00377f1000 - 0037fef600]
[    0.000000]   #4 [000009b800 - 0000100000]    BIOS reserved ==> [000009b800 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #6 [0000013000 - 0000019000]          PGTABLE ==> [0000013000 - 0000019000]
[    0.000000] found SMP MP-table at [ffff8800000f3f50] 000f3f50
[    0.000000]  [ffffe20000000000-ffffe200085fffff] PMD -> [ffff880028200000-ffff8800307fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00260000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x0009fef0
[    0.000000]     0: 0x00100000 -> 0x00260000
[    0.000000] On node 0 totalpages: 2096763
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2551 pages reserved
[    0.000000]   DMA zone: 1372 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 636712 pages, LIFO batch:31
[    0.000000]   Normal zone: 19712 pages used for memmap
[    0.000000]   Normal zone: 1422080 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: OEM00000
[    0.000000] MPTABLE: Product ID: PROD00000000
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] I/O APIC #4 Version 17 at 0xFEC00000.
[    0.000000] Processors: 4
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009fef0000 - 000000009fef3000
[    0.000000] PM: Registered nosave memory: 000000009fef3000 - 000000009ff00000
[    0.000000] PM: Registered nosave memory: 000000009ff00000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: 9ff00000:30100000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2060164
[    0.000000] Kernel command line: root=/dev/md1 ro quiet splash pci=noacpi 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2399.982 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.004000] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] allocated 99614720 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 8054868k/9961472k available (4760k kernel code, 1574420k absent, 331268k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4799.96 BogoMIPS (lpj=9599928)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20080926
[    0.004000] ACPI: Checking initramfs for custom DSDT
[    0.291104] ACPI: setting ELCR to 0e20 (from 0c20)
[    0.292041] Setting APIC routing to flat
[    0.292123] ExtINT not setup in hardware but reported by MP table
[    0.292494] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.333330] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.336001] Booting processor 1 APIC 0x2 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4800.01 BogoMIPS (lpj=9600032)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.420545] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.420565] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.424081] Booting processor 2 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4799.94 BogoMIPS (lpj=9599898)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.512515] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.512537] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.516107] Booting processor 3 APIC 0x3 ip 0x6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 4799.96 BogoMIPS (lpj=9599923)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.604507] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.604527] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.608023] Brought up 4 CPUs
[    0.608026] Total of 4 processors activated (19199.89 BogoMIPS).
[    0.608103] CPU0 attaching sched-domain:
[    0.608105]  domain 0: span 0,2 level MC
[    0.608107]   groups: 0 2
[    0.608110]   domain 1: span 0-3 level CPU
[    0.608111]    groups: 0,2 1,3
[    0.608115] CPU1 attaching sched-domain:
[    0.608117]  domain 0: span 1,3 level MC
[    0.608118]   groups: 1 3
[    0.608120]   domain 1: span 0-3 level CPU
[    0.608122]    groups: 1,3 0,2
[    0.608125] CPU2 attaching sched-domain:
[    0.608126]  domain 0: span 0,2 level MC
[    0.608128]   groups: 2 0
[    0.608130]   domain 1: span 0-3 level CPU
[    0.608131]    groups: 0,2 1,3
[    0.608134] CPU3 attaching sched-domain:
[    0.608135]  domain 0: span 1,3 level MC
[    0.608136]   groups: 3 1
[    0.608139]   domain 1: span 0-3 level CPU
[    0.608140]    groups: 1,3 0,2
[    0.608239] net_namespace: 1400 bytes
[    0.608239] Booting paravirtualized kernel on bare hardware
[    0.608247] Time: 16:45:50  Date: 05/25/09
[    0.608247] regulator: core version 0.5
[    0.608247] NET: Registered protocol family 16
[    0.608247] ACPI: bus type pci registered
[    0.608247] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.608247] PCI: MCFG area at e0000000 reserved in E820
[    0.617750] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.617752] PCI: Using configuration type 1 for base access
[    0.618299] ACPI: EC: Look up EC in DSDT
[    0.626086] ACPI: Interpreter enabled
[    0.626088] ACPI: (supports S0 S1 S3 S4 S5)
[    0.626108] ACPI: Using PIC for interrupt routing
[    0.632883] ACPI: No dock devices found.
[    0.632951] ACPI: WMI: Mapper loaded
[    0.632981] SCSI subsystem initialized
[    0.632981] libata version 3.00 loaded.
[    0.632981] usbcore: registered new interface driver usbfs
[    0.632981] usbcore: registered new interface driver hub
[    0.632981] usbcore: registered new device driver usb
[    0.632981] PCI: Probing PCI hardware
[    0.632981] PCI: Probing PCI hardware (bus 00)
[    0.632981] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.632981] pci 0000:00:03.0: PME# disabled
[    0.632981] pci 0000:00:0a.0: reg 10 io port: [0xfc00-0xfc7f]
[    0.633004] pci 0000:00:0a.1: reg 10 io port: [0xf800-0xf83f]
[    0.633018] pci 0000:00:0a.1: reg 20 io port: [0xf400-0xf43f]
[    0.633023] pci 0000:00:0a.1: reg 24 io port: [0xf000-0xf03f]
[    0.633035] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.633040] pci 0000:00:0a.1: PME# disabled
[    0.633070] pci 0000:00:0b.0: reg 10 32bit mmio: [0xcffff000-0xcfffffff]
[    0.633093] pci 0000:00:0b.0: supports D1 D2
[    0.633095] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.633098] pci 0000:00:0b.0: PME# disabled
[    0.633122] pci 0000:00:0b.1: reg 10 32bit mmio: [0xcfffe000-0xcfffe0ff]
[    0.633146] pci 0000:00:0b.1: supports D1 D2
[    0.633147] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.633150] pci 0000:00:0b.1: PME# disabled
[    0.633187] pci 0000:00:0d.0: reg 20 io port: [0xec00-0xec0f]
[    0.633224] pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]
[    0.633228] pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]
[    0.633232] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
[    0.633236] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
[    0.633240] pci 0000:00:0e.0: reg 20 io port: [0xd800-0xd80f]
[    0.633244] pci 0000:00:0e.0: reg 24 32bit mmio: [0xcfffd000-0xcfffdfff]
[    0.633281] pci 0000:00:0e.1: reg 10 io port: [0x9e0-0x9e7]
[    0.633285] pci 0000:00:0e.1: reg 14 io port: [0xbe0-0xbe3]
[    0.633289] pci 0000:00:0e.1: reg 18 io port: [0x960-0x967]
[    0.633293] pci 0000:00:0e.1: reg 1c io port: [0xb60-0xb63]
[    0.633297] pci 0000:00:0e.1: reg 20 io port: [0xc400-0xc40f]
[    0.633301] pci 0000:00:0e.1: reg 24 32bit mmio: [0xcfffc000-0xcfffcfff]
[    0.633338] pci 0000:00:0e.2: reg 10 io port: [0xc000-0xc007]
[    0.633342] pci 0000:00:0e.2: reg 14 io port: [0xbc00-0xbc03]
[    0.633346] pci 0000:00:0e.2: reg 18 io port: [0xb800-0xb807]
[    0.633350] pci 0000:00:0e.2: reg 1c io port: [0xb400-0xb403]
[    0.633354] pci 0000:00:0e.2: reg 20 io port: [0xb000-0xb00f]
[    0.633358] pci 0000:00:0e.2: reg 24 32bit mmio: [0xcfffb000-0xcfffbfff]
[    0.633433] pci 0000:00:0f.1: reg 10 32bit mmio: [0xcfff4000-0xcfff7fff]
[    0.633456] pci 0000:00:0f.1: PME# supported from D3hot D3cold
[    0.633459] pci 0000:00:0f.1: PME# disabled
[    0.633506] pci 0000:00:12.0: reg 10 32bit mmio: [0xcfffa000-0xcfffafff]
[    0.633510] pci 0000:00:12.0: reg 14 io port: [0xac00-0xac07]
[    0.633514] pci 0000:00:12.0: reg 18 32bit mmio: [0xcfff9000-0xcfff90ff]
[    0.633518] pci 0000:00:12.0: reg 1c 32bit mmio: [0xcfff8000-0xcfff800f]
[    0.633533] pci 0000:00:12.0: supports D1 D2
[    0.633534] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.633538] pci 0000:00:12.0: PME# disabled
[    0.633582] pci 0000:01:00.0: reg 10 32bit mmio: [0xcc000000-0xccffffff]
[    0.633589] pci 0000:01:00.0: reg 14 64bit mmio: [0xa0000000-0xbfffffff]
[    0.633596] pci 0000:01:00.0: reg 1c 64bit mmio: [0xcd000000-0xcdffffff]
[    0.633604] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.633651] pci 0000:00:03.0: bridge 32bit mmio: [0xcc000000-0xceffffff]
[    0.633655] pci 0000:00:03.0: bridge 64bit mmio pref: [0xa0000000-0xbfffffff]
[    0.633688] pci 0000:02:07.0: reg 10 32bit mmio: [0xcfeff000-0xcfeff7ff]
[    0.633694] pci 0000:02:07.0: reg 14 32bit mmio: [0xcfef8000-0xcfefbfff]
[    0.633721] pci 0000:02:07.0: supports D1 D2
[    0.633722] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot
[    0.633725] pci 0000:02:07.0: PME# disabled
[    0.633758] pci 0000:02:0a.0: reg 10 32bit mmio: [0xcfdff000-0xcfdfffff]
[    0.633818] pci 0000:02:0a.1: reg 10 32bit mmio: [0xcfdfe000-0xcfdfefff]
[    0.633879] pci 0000:00:0f.0: transparent bridge
[    0.633882] pci 0000:00:0f.0: bridge 32bit mmio: [0xcfe00000-0xcfefffff]
[    0.633885] pci 0000:00:0f.0: bridge 32bit mmio pref: [0xcfd00000-0xcfdfffff]
[    0.636098] pci 0000:00:0b.0: PCI->APIC IRQ transform: INT A -> IRQ 10
[    0.636101] pci 0000:00:0b.1: PCI->APIC IRQ transform: INT B -> IRQ 11
[    0.636105] pci 0000:00:0e.0: PCI->APIC IRQ transform: INT A -> IRQ 10
[    0.636107] pci 0000:00:0e.1: PCI->APIC IRQ transform: INT B -> IRQ 11
[    0.636110] pci 0000:00:0e.2: PCI->APIC IRQ transform: INT C -> IRQ 11
[    0.636114] pci 0000:00:0f.1: PCI->APIC IRQ transform: INT B -> IRQ 10
[    0.636116] pci 0000:00:12.0: PCI->APIC IRQ transform: INT A -> IRQ 5
[    0.636119] pci 0000:01:00.0: PCI->APIC IRQ transform: INT A -> IRQ 10
[    0.636122] pci 0000:02:07.0: PCI->APIC IRQ transform: INT A -> IRQ 10
[    0.636124] pci 0000:02:0a.0: PCI->APIC IRQ transform: INT A -> IRQ 11
[    0.636127] pci 0000:02:0a.1: PCI->APIC IRQ transform: INT A -> IRQ 11
[    0.648013] Bluetooth: Core ver 2.13
[    0.648029] NET: Registered protocol family 31
[    0.648029] Bluetooth: HCI device and connection manager initialized
[    0.648029] Bluetooth: HCI socket layer initialized
[    0.648029] NET: Registered protocol family 8
[    0.648029] NET: Registered protocol family 20
[    0.648038] NetLabel: Initializing
[    0.648040] NetLabel:  domain hash size = 128
[    0.648041] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.648056] NetLabel:  unlabeled traffic allowed by default
[    0.648101] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.648106] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.656062] AppArmor: AppArmor Filesystem Enabled
[    0.660009] Switched to high resolution mode on CPU 0
[    0.660577] Switched to high resolution mode on CPU 2
[    0.660777] Switched to high resolution mode on CPU 3
[    0.661104] Switched to high resolution mode on CPU 1
[    0.668022] pnp: PnP ACPI init
[    0.668031] ACPI: bus type pnp registered
[    0.671125] pnp: PnP ACPI: found 11 devices
[    0.671127] ACPI: ACPI bus type pnp unregistered
[    0.671133] system 00:00: ioport range 0x1000-0x107f has been reserved
[    0.671135] system 00:00: ioport range 0x1080-0x10ff has been reserved
[    0.671137] system 00:00: ioport range 0x1400-0x147f has been reserved
[    0.671139] system 00:00: ioport range 0x1480-0x14ff has been reserved
[    0.671142] system 00:00: ioport range 0x1800-0x187f has been reserved
[    0.671144] system 00:00: ioport range 0x1880-0x18ff has been reserved
[    0.671149] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.671151] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.671152] system 00:02: ioport range 0x880-0x88f has been reserved
[    0.671158] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.671162] system 00:0a: iomem range 0xd0000-0xd3fff has been reserved
[    0.671164] system 00:0a: iomem range 0xd5800-0xd7fff has been reserved
[    0.671166] system 00:0a: iomem range 0xf0000-0xfbfff could not be reserved
[    0.671168] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.671170] system 00:0a: iomem range 0x9fef0000-0x9fefffff could not be reserved
[    0.671171] system 00:0a: iomem range 0xffff0000-0xffffffff has been reserved
[    0.671173] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.671175] system 00:0a: iomem range 0x100000-0x9feeffff could not be reserved
[    0.671177] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.671179] system 00:0a: iomem range 0xd0000000-0xdfffffff has been reserved
[    0.671181] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.671182] system 00:0a: iomem range 0xfeff0000-0xfeff0000 has been reserved
[    0.675831] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.675832] pci 0000:00:03.0:   IO window: disabled
[    0.675835] pci 0000:00:03.0:   MEM window: 0xcc000000-0xceffffff
[    0.675838] pci 0000:00:03.0:   PREFETCH window: 0x000000a0000000-0x000000bfffffff
[    0.675842] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:02
[    0.675843] pci 0000:00:0f.0:   IO window: disabled
[    0.675846] pci 0000:00:0f.0:   MEM window: 0xcfe00000-0xcfefffff
[    0.675848] pci 0000:00:0f.0:   PREFETCH window: 0x000000cfd00000-0x000000cfdfffff
[    0.675857] pci 0000:00:03.0: setting latency timer to 64
[    0.675861] pci 0000:00:0f.0: setting latency timer to 64
[    0.675864] bus: 00 index 0 io port: [0x00-0xffff]
[    0.675865] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.675867] bus: 01 index 0 mmio: [0x0-0x0]
[    0.675868] bus: 01 index 1 mmio: [0xcc000000-0xceffffff]
[    0.675870] bus: 01 index 2 mmio: [0xa0000000-0xbfffffff]
[    0.675871] bus: 01 index 3 mmio: [0x0-0x0]
[    0.675872] bus: 02 index 0 mmio: [0x0-0x0]
[    0.675873] bus: 02 index 1 mmio: [0xcfe00000-0xcfefffff]
[    0.675875] bus: 02 index 2 mmio: [0xcfd00000-0xcfdfffff]
[    0.675876] bus: 02 index 3 io port: [0x00-0xffff]
[    0.675877] bus: 02 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.675884] NET: Registered protocol family 2
[    0.708087] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.708771] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.710273] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.710722] TCP: Hash tables configured (established 262144 bind 65536)
[    0.710724] TCP reno registered
[    0.720148] NET: Registered protocol family 1
[    0.720269] checking if image is initramfs... it is
[    1.304013] Freeing initrd memory: 8185k freed
[    1.307442] audit: initializing netlink socket (disabled)
[    1.307456] type=2000 audit(1243269950.304:1): initialized
[    1.314654] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.315706] VFS: Disk quotas dquot_6.5.1
[    1.315762] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.316217] fuse init (API version 7.10)
[    1.316304] msgmni has been set to 15749
[    1.316507] alg: No test for stdrng (krng)
[    1.316524] io scheduler noop registered
[    1.316527] io scheduler anticipatory registered
[    1.316529] io scheduler deadline registered
[    1.316572] io scheduler cfq registered (default)
[    1.316735] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0e.1: Disabling HT MSI mapping<6>pci 0000:00:0e.2: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:0f.1: Disabling HT MSI mapping<6>pci 0000:00:12.0: Disabling HT MSI mapping<7>pci 0000:01:00.0: Boot video device
[    1.333780] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.333811] pcieport-driver 0000:00:03.0: found MSI capability
[    1.333829] pcieport-driver 0000:00:03.0: irq 2303 for MSI/MSI-X
[    1.333837] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.333847] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.333890] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.333898] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.334019] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.334021] ACPI: Power Button (FF) [PWRF]
[    1.334053] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.334055] ACPI: Power Button (CM) [PWRB]
[    1.334191] processor ACPI_CPU:00: registered as cooling_device0
[    1.334195] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.334251] processor ACPI_CPU:01: registered as cooling_device1
[    1.334280] processor ACPI_CPU:02: registered as cooling_device2
[    1.334309] processor ACPI_CPU:03: registered as cooling_device3
[    1.368266] Linux agpgart interface v0.103
[    1.368274] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.369042] brd: module loaded
[    1.369292] loop: module loaded
[    1.369344] Fixed MDIO Bus: probed
[    1.369348] PPP generic driver version 2.4.2
[    1.369392] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.369411] Driver 'sd' needs updating - please use bus_type methods
[    1.369418] Driver 'sr' needs updating - please use bus_type methods
[    1.369578] sata_nv 0000:00:0e.0: version 3.5
[    1.369586] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.369825] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.369973] scsi0 : sata_nv
[    1.370088] scsi1 : sata_nv
[    1.370130] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 10
[    1.370133] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 10
[    2.248034] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.256356] ata1.00: ATA-7: Hitachi HDS721075KLA330, GK8OA70M, max UDMA/133
[    2.256359] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.272343] ata1.00: configured for UDMA/133
[    3.006423] ata2: SATA link down (SStatus 0 SControl 300)
[    3.006521] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72107 GK8O PQ: 0 ANSI: 5
[    3.006589] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    3.006602] sd 0:0:0:0: [sda] Write Protect is off
[    3.006603] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.006622] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.006672] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    3.006683] sd 0:0:0:0: [sda] Write Protect is off
[    3.006685] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.006703] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.006705]  sda: sda1 sda2 sda4 < sda5 sda6 >
[    3.030754] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.030784] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.030797] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    3.030824] sata_nv 0000:00:0e.1: setting latency timer to 64
[    3.030916] scsi2 : sata_nv
[    3.030958] scsi3 : sata_nv
[    3.030982] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 11
[    3.030984] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 11
[    3.908033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.932150] ata3.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L05, max UDMA/100
[    3.964165] ata3.00: configured for UDMA/100
[    4.698407] ata4: SATA link down (SStatus 0 SControl 300)
[    4.699560] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L05 PQ: 0 ANSI: 5
[    4.704980] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.704983] Uniform CD-ROM driver Revision: 3.20
[    4.705072] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.705110] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    4.705127] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    4.705163] sata_nv 0000:00:0e.2: setting latency timer to 64
[    4.705274] scsi4 : sata_nv
[    4.705342] scsi5 : sata_nv
[    4.705367] ata5: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 11
[    4.705374] ata6: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 11
[    5.438412] ata5: SATA link down (SStatus 0 SControl 300)
[    6.170412] ata6: SATA link down (SStatus 0 SControl 300)
[    6.170495] pata_amd 0000:00:0d.0: version 0.3.10
[    6.170521] pata_amd 0000:00:0d.0: setting latency timer to 64
[    6.170573] scsi6 : pata_amd
[    6.170613] scsi7 : pata_amd
[    6.170640] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    6.170641] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    6.334985] ata8: port disabled. ignoring.
[    6.335338] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    6.335357] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    6.335360] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    6.335401] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    6.335424] ehci_hcd 0000:00:0b.1: debug port 1
[    6.335427] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    6.335431] ehci_hcd 0000:00:0b.1: irq 11, io mem 0xcfffe000
[    6.344015] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    6.344090] usb usb1: configuration #1 chosen from 1 choice
[    6.344119] hub 1-0:1.0: USB hub found
[    6.344126] hub 1-0:1.0: 10 ports detected
[    6.344225] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.344245] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    6.344248] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    6.344277] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    6.344286] ohci_hcd 0000:00:0b.0: irq 10, io mem 0xcffff000
[    6.402035] usb usb2: configuration #1 chosen from 1 choice
[    6.402053] hub 2-0:1.0: USB hub found
[    6.402059] hub 2-0:1.0: 10 ports detected
[    6.402137] uhci_hcd: USB Universal Host Controller Interface driver
[    6.402175] usbcore: registered new interface driver libusual
[    6.402198] usbcore: registered new interface driver usbserial
[    6.402207] USB Serial support registered for generic
[    6.402216] usbcore: registered new interface driver usbserial_generic
[    6.402217] usbserial: USB Serial Driver core
[    6.402251] PNP: No PS/2 controller found. Probing ports directly.
[    6.405052] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.405057] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.416052] mice: PS/2 mouse device common for all mice
[    6.452087] rtc_cmos 00:05: RTC can wake from S4
[    6.452125] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    6.452156] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    6.452217] device-mapper: uevent: version 1.0.3
[    6.452273] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    6.452369] device-mapper: multipath: version 1.0.5 loaded
[    6.452371] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.452467] cpuidle: using governor ladder
[    6.452469] cpuidle: using governor menu
[    6.452783] TCP cubic registered
[    6.452832] NET: Registered protocol family 10
[    6.453134] lo: Disabled Privacy Extensions
[    6.453343] NET: Registered protocol family 17
[    6.453357] Bluetooth: L2CAP ver 2.11
[    6.453358] Bluetooth: L2CAP socket layer initialized
[    6.453360] Bluetooth: SCO (Voice Link) ver 0.6
[    6.453361] Bluetooth: SCO socket layer initialized
[    6.453386] Bluetooth: RFCOMM socket layer initialized
[    6.453390] Bluetooth: RFCOMM TTY layer initialized
[    6.453392] Bluetooth: RFCOMM ver 1.10
[    6.453559] registered taskstats version 1
[    6.453738]   Magic number: 9:804:793
[    6.453829] rtc_cmos 00:05: setting system clock to 2009-05-25 16:45:56 UTC (1243269956)
[    6.453832] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.453834] EDD information not available.
[    6.453868] Freeing unused kernel memory: 536k freed
[    6.454010] Write protecting the kernel read-only data: 6708k
[    6.561087] md: linear personality registered for level -1
[    6.562629] md: multipath personality registered for level -4
[    6.564004] md: raid0 personality registered for level 0
[    6.566186] md: raid1 personality registered for level 1
[    6.567442] xor: automatically using best checksumming function: generic_sse
[    6.584003]    generic_sse:  8877.000 MB/sec
[    6.584004] xor: using function: generic_sse (8877.000 MB/sec)
[    6.584826] async_tx: api initialized (async)
[    6.652023] raid6: int64x1   1909 MB/s
[    6.657511] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    6.720016] raid6: int64x2   2618 MB/s
[    6.788028] raid6: int64x4   2015 MB/s
[    6.790885] usb 1-3: configuration #1 chosen from 1 choice
[    6.790975] hub 1-3:1.0: USB hub found
[    6.791083] hub 1-3:1.0: 4 ports detected
[    6.856009] raid6: int64x8   1786 MB/s
[    6.924004] raid6: sse2x1    3859 MB/s
[    6.992009] raid6: sse2x2    4341 MB/s
[    7.060007] raid6: sse2x4    7130 MB/s
[    7.060009] raid6: using algorithm sse2x4 (7130 MB/s)
[    7.060011] md: raid6 personality registered for level 6
[    7.060012] md: raid5 personality registered for level 5
[    7.060014] md: raid4 personality registered for level 4
[    7.064743] md: raid10 personality registered for level 10
[    7.144068] FDC 0 is a post-1991 82077
[    7.169803] ohci1394 0000:02:07.0: setting latency timer to 64
[    7.188579] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    7.188597] forcedeth 0000:00:12.0: setting latency timer to 64
[    7.188638] nv_probe: set workaround bit for reversed mac addr
[    7.219541] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[cfeff000-cfeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.317528] usb 2-4: new full speed USB device using ohci_hcd and address 2
[    7.397945] md: bind<sda1>
[    7.398608] md: bind<sda2>
[    7.400063] raid1: raid set md0 active with 1 out of 2 mirrors
[    7.400778] md: bind<sda5>
[    7.400993] md: bind<sda6>
[    7.401219] raid1: raid set md1 active with 1 out of 2 mirrors
[    7.401732]  md0: unknown partition table
[    7.402628] raid1: raid set md2 active with 1 out of 2 mirrors
[    7.402999] raid1: raid set md3 active with 1 out of 2 mirrors
[    7.404025]  md2:<6> md3:<6> md1: unknown partition table
[    7.419423]  unknown partition table
[    7.421383]  unknown partition table
[    7.529112] usb 2-4: configuration #1 chosen from 1 choice
[    7.535068] hub 2-4:1.0: USB hub found
[    7.538039] hub 2-4:1.0: 3 ports detected
[    7.708674] forcedeth 0000:00:12.0: ifname eth0, PHY OUI 0x5043 @ 2, addr 00:04:4b:03:de:f6
[    7.708677] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[    7.765687] PM: Starting manual resume from disk
[    7.765689] PM: Resume from partition 9:0
[    7.765690] PM: Checking hibernation image.
[    7.765828] PM: Resume from disk failed.
[    7.789400] kjournald starting.  Commit interval 5 seconds
[    7.789410] EXT3-fs: mounted filesystem with ordered data mode.
[    7.864114] usb 2-5: new full speed USB device using ohci_hcd and address 3
[    8.088126] usb 2-5: configuration #1 chosen from 1 choice
[    8.160599] usb 1-3.4: new full speed USB device using ehci_hcd and address 5
[    8.282156] usb 1-3.4: configuration #1 chosen from 1 choice
[    8.366049] usb 2-4.1: new low speed USB device using ohci_hcd and address 4
[    8.479117] usb 2-4.1: configuration #1 chosen from 1 choice
[    8.492147] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0d60cee600044b03]
[    8.569047] usb 2-4.3: new low speed USB device using ohci_hcd and address 5
[    8.682108] usb 2-4.3: configuration #1 chosen from 1 choice
[   11.065565] udev: starting version 141
[   11.970240] nvidia: module license 'NVIDIA' taints kernel.
[   12.222234] nvidia 0000:01:00.0: setting latency timer to 64
[   12.222637] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   12.244447] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   12.244549] usbcore: registered new interface driver btusb
[   12.281422] usbcore: registered new interface driver hiddev
[   12.287420] input: Dell Dell Multimedia Pro Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4.1/2-4.1:1.0/input/input3
[   12.316187] generic-usb 0003:413C:2011.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell Multimedia Pro Keyboard] on usb-0000:00:0b.0-4.1/input0
[   12.329177] input: Dell Dell Multimedia Pro Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4.1/2-4.1:1.1/input/input4
[   12.356202] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3112
[   12.356232] usbcore: registered new interface driver usblp
[   12.359570] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400
[   12.359600] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000
[   12.360135] generic-usb 0003:413C:2011.0002: input,hidraw1: USB HID v1.10 Device [Dell Dell Multimedia Pro Keyboard] on usb-0000:00:0b.0-4.1/input1
[   12.366409] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4.3/2-4.3:1.0/input/input5
[   12.396165] generic-usb 0003:045E:0053.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-4.3/input0
[   12.396187] usbcore: registered new interface driver usbhid
[   12.396211] usbhid: v2.6:USB HID core driver
[   12.409193] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   12.625779] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.646906] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
[   12.646917] resource map sanity check conflict: 0xff000000 0xffffffff 0xffff0000 0xffffffff pnp 00:0a
[   12.646925] ------------[ cut here ]------------
[   12.646927] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390()
[   12.646929] Modules linked in: ck804xrom(+) mtd ip_tables btcx_risc snd chipreg x_tables joydev psmouse serio_raw tveeprom pcspkr soundcore snd_page_alloc map_funcs i2c_nforce2 usblp usbhid btusb nvidia(P) forcedeth ohci1394 ieee1394 floppy raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor
[   12.646949] Pid: 1141, comm: modprobe Tainted: P           2.6.28-11-generic #42-Ubuntu
[   12.646950] Call Trace:
[   12.646956]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90
[   12.646959]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
[   12.646961]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
[   12.646964]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390
[   12.646968]  [<ffffffffa096b2db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
[   12.646970]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
[   12.646973]  [<ffffffffa096b2db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
[   12.646977]  [<ffffffffa0971041>] init_ck804xrom+0x41/0x59 [ck804xrom]
[   12.646979]  [<ffffffffa0971000>] ? init_ck804xrom+0x0/0x59 [ck804xrom]
[   12.646982]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
[   12.646985]  [<ffffffff80416ffa>] ? __next_cpu+0x1a/0x30
[   12.646989]  [<ffffffff802424b2>] ? enqueue_entity+0x122/0x2b0
[   12.646991]  [<ffffffff8024870b>] ? enqueue_task_fair+0x7b/0x80
[   12.646993]  [<ffffffff8023e2a9>] ? wakeup_preempt_entity+0x59/0x60
[   12.646995]  [<ffffffff80249330>] ? check_preempt_wakeup+0x210/0x230
[   12.646998]  [<ffffffff8024a3cc>] ? try_to_wake_up+0x12c/0x2e0
[   12.647002]  [<ffffffff8027ef9d>] sys_init_module+0xad/0x1e0
[   12.647004]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[   12.647006] ---[ end trace 8efa73119d51d0cf ]---
[   12.792227] Found: SST 49LF040B
[   12.792230] ck804xrom @fff80000: Found 1 x8 devices at 0x0 in 8-bit bank
[   12.800818] using fwh lock/unlock method
[   12.800821] number of JEDEC chips: 1
[   12.800823] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
[   12.837062] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   12.837279] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   12.837280] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   12.837282] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   12.854199] Linux video capture interface: v2.00
[   12.914313] bttv: driver version 0.9.17 loaded
[   12.914316] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   12.914386] bttv: Bt8xx card found (0).
[   12.914404] bttv0: Bt878 (rev 17) at 0000:02:0a.0, irq: 11, latency: 16, mmio: 0xcfdff000
[   12.914474] bttv0: detected: ATI TV Wonder/VE [card=64], PCI subsystem ID is 1002:0003
[   12.914476] bttv0: using: ATI TV-Wonder VE [card=64,autodetected]
[   12.914504] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   12.914577] bttv0: tuner type=19
[   12.914578] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   12.915189] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   12.972199] HDA Intel 0000:00:0f.1: setting latency timer to 64
[   12.998351] All bytes are equal. It is not a TEA5767
[   12.998405] tuner' 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   13.004996] tuner-simple 2-0060: creating new instance
[   13.004999] tuner-simple 2-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[   13.014766] bttv0: registered device video0
[   13.014794] bttv0: registered device vbi0
[   13.014826] bttv0: PLL: 28636363 => 35468950 .. ok
[   13.364019] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.990393] lp: driver loaded but no devices found
[   14.093670] Adding 7815480k swap on /dev/md0.  Priority:-1 extents:1 across:7815480k
[   14.644529] EXT3 FS on md1, internal journal
[   15.719975] kjournald starting.  Commit interval 5 seconds
[   15.735670] EXT3 FS on md2, internal journal
[   15.735675] EXT3-fs: mounted filesystem with ordered data mode.
[   15.754745] kjournald starting.  Commit interval 5 seconds
[   15.771833] EXT3 FS on md3, internal journal
[   15.771836] EXT3-fs: mounted filesystem with ordered data mode.
[   15.956605] type=1505 audit(1243269966.002:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2688
[   15.987763] type=1505 audit(1243269966.030:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2692
[   15.987837] type=1505 audit(1243269966.030:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2692
[   15.987865] type=1505 audit(1243269966.030:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2692
[   15.987893] type=1505 audit(1243269966.030:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2692
[   16.073266] type=1505 audit(1243269966.118:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2697
[   16.073394] type=1505 audit(1243269966.118:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2697
[   16.093338] type=1505 audit(1243269966.138:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2701
[   19.662597] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.662599] Bluetooth: BNEP filters: protocol multicast
[   19.764753] Bridge firewalling registered
[   20.856705] ppdev: user-space parallel port driver
[   22.468645] /dev/vmmon[3756]: Module vmmon: registered with major=10 minor=165
[   22.468659] /dev/vmmon[3756]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   22.468669] /dev/vmmon[3756]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   22.468671] /dev/vmmon[3756]: Module vmmon: initialized
[   22.546824] /dev/vmci[3766]: VMCI: Driver initialized.
[   22.547045] /dev/vmci[3766]: Module vmci: registered with major=10 minor=57
[   22.547047] /dev/vmci[3766]: Module vmci: initialized
[   23.015051] /dev/vmnet: open called by PID 3843 (vmnet-netifup)
[   23.015059] /dev/vmnet: hub 1 does not exist, allocating memory.
[   23.015067] /dev/vmnet: port on hub 1 successfully opened
[   23.113977] /dev/vmnet: open called by PID 3842 (vmnet-dhcpd)
[   23.113987] /dev/vmnet: port on hub 1 successfully opened
[   23.119578] /dev/vmnet: open called by PID 3872 (vmnet-netifup)
[   23.119588] /dev/vmnet: hub 8 does not exist, allocating memory.
[   23.119596] /dev/vmnet: port on hub 8 successfully opened
[   23.185917] /dev/vmnet: open called by PID 3875 (vmnet-dhcpd)
[   23.185931] /dev/vmnet: port on hub 8 successfully opened
[   23.312423] /dev/vmnet: open called by PID 3893 (vmnet-natd)
[   23.312435] /dev/vmnet: port on hub 8 successfully opened
[   24.953704] forcedeth 0000:00:12.0: irq 2302 for MSI/MSI-X
[   24.954378] /dev/vmnet: open called by PID 3831 (vmnet-bridge)
[   24.954391] /dev/vmnet: hub 0 does not exist, allocating memory.
[   24.954399] /dev/vmnet: port on hub 0 successfully opened
[   24.954414] bridge-eth0: up
[   24.955832] bridge-eth0: attached
[   32.065140] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   32.065276] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   32.065345] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   32.065625] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   32.065695] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   32.065763] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[   32.066009] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   32.066076] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   32.066141] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   32.066393] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   32.066459] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   32.066524] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[   33.067909] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   33.068195] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   33.560007] vmnet1: no IPv6 routers present
[   33.640005] vmnet8: no IPv6 routers present
[   35.070841] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=200 
[   35.070947] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=200 
[   35.332017] eth0: no IPv6 routers present
[   37.072749] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=200 
[   37.072829] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=200 
[   39.074644] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=200 
[   39.074724] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=200 
[   41.076595] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=200 
[   41.076671] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=200 
[   43.078714] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=200 
[   43.078802] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   43.078928] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=220 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=200 
[   43.078972] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
[   83.960477] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=212 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=192 
[   83.960497] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=213 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=193 
[  103.139458] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=246 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=226 
[  103.153016] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=246 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=226 
[  114.960090] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=212 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=192 
[  114.960116] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=213 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=193 
[  145.960418] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=212 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=192 
[  145.960437] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=213 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=193 
[  157.467405] attempt to access beyond end of device
[  157.467411] md2: rw=0, want=7542522264, limit=234371968
[  157.467415] attempt to access beyond end of device
[  157.467417] md2: rw=0, want=13179650848, limit=234371968
[  157.467420] attempt to access beyond end of device
[  157.467422] md2: rw=0, want=7542522264, limit=234371968
[  157.467426] attempt to access beyond end of device
[  157.467428] md2: rw=0, want=7542522264, limit=234371968
[  157.467431] attempt to access beyond end of device
[  157.467433] md2: rw=0, want=7542522264, limit=234371968
[  157.467436] attempt to access beyond end of device
[  157.467438] md2: rw=0, want=6467723656, limit=234371968
[  157.467441] attempt to access beyond end of device
[  157.467443] md2: rw=0, want=6467715464, limit=234371968
[  157.467448] attempt to access beyond end of device
[  157.467450] md2: rw=0, want=6736783768, limit=234371968
[  157.467453] attempt to access beyond end of device
[  157.467455] md2: rw=0, want=7008780728, limit=234371968
[  157.467458] attempt to access beyond end of device
[  157.467460] md2: rw=0, want=6467717512, limit=234371968
[  157.467463] attempt to access beyond end of device
[  157.467465] md2: rw=0, want=6467715464, limit=234371968
[  157.467468] attempt to access beyond end of device
[  157.467470] md2: rw=0, want=6467731880, limit=234371968
[  157.467473] attempt to access beyond end of device
[  157.467475] md2: rw=0, want=6467715464, limit=234371968
[  157.467478] attempt to access beyond end of device
[  157.467480] md2: rw=0, want=6467717512, limit=234371968
[  157.467483] attempt to access beyond end of device
[  157.467485] md2: rw=0, want=6467715464, limit=234371968
[  157.467488] attempt to access beyond end of device
[  157.467490] md2: rw=0, want=6467719560, limit=234371968
[  157.467493] attempt to access beyond end of device
[  157.467495] md2: rw=0, want=6467715464, limit=234371968
[  157.467498] attempt to access beyond end of device
[  157.467500] md2: rw=0, want=6467725704, limit=234371968
[  157.467504] attempt to access beyond end of device
[  157.467506] md2: rw=0, want=6467715464, limit=234371968
[  157.467508] attempt to access beyond end of device
[  157.467510] md2: rw=0, want=6467819920, limit=234371968
[  177.860106] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=212 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=192 
[  177.860134] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=213 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=193 
[  208.372449] Unknown OutputIN= OUT=vmnet1 SRC=172.16.195.1 DST=172.16.195.255 LEN=212 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=192 
[  208.372470] Unknown OutputIN= OUT=vmnet8 SRC=192.168.164.1 DST=192.168.164.255 LEN=213 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=193 

---

### Post by fjgaude on 2009-05-27
You might show us what mdadm shows for things like this:

```
sudo mdadm -D /dev/md0
```

and so on.

---

