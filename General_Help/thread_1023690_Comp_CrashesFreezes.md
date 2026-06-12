---
title: "Comp Crashes/Freezes"
date: 2008-12-28
forum: General Help
---

### Post by phonixor on 2008-12-28
Ok it doesn't really matter what i do... or howlong my comp is on...
sometimes for no apperent reason my comp freezes completly (even after 5 min of use... sometimes after days...)... keyboards lights are flickering... and screen is frozen... cant move mouse... or press alt + f10... or anything... and sometimes its just a black screen and then auto reboots...

first i thought it was flash... (which causes my CPU to get to 100% and crashes firefox a lot... (i tried gnash... but it doesnt support all my streaming sites yet ... so thats no good...), anyone know a solution for this aswell?? (downloadhelper plugig is a nice workaround for some sites :P))
but i also had crashes while watching a movie...
or installing Warcraft III...

i thought it might be my ram... so i did the ram test thingy on boottime...
... and it crashed there to... (does this mean its not ubuntu but just my hardware?, and if so is there a way to test this???) i have 2 512mb ram ... and the comp still crashes when i use either one... so i doubt thats it...

so now i wonder what it is... 
thanks in advanche for any help!

---

### Post by linux_tech on 2008-12-28
Sounds like hardware failure.
Give the memtest another try. [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
has alot of good diagnostics on it as well to check memory, hard drive,
cpu, etc.

what is output of ```
dmesg
```?

---

### Post by phonixor on 2008-12-28
will try next time it crashes :P

mmmh i tried adding it as a .txt attachement... but its to big for that :@

and:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3782e000 - 37feff5b
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP 000F7410, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF30C0, 3CFE (r1 INTELR AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: APIC 3FFF6DC0, 0068 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [003782e000 - 0037feff5b]          RAMDISK ==> [003782e000 - 0037feff5b]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f55f0] 000f55f0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262031
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 32464 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259727
[    0.000000] Kernel command line: root=UUID=a11173ab-3b7c-4f1e-84fd-e0b9b389a0e5 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 3000.480 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1024868k/1048512k available (2572k kernel code, 22964k reserved, 1160k data, 424k init, 131008k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 6000.96 BogoMIPS (lpj=12001920)
[    0.004035] Security Framework initialized
[    0.004046] SELinux:  Disabled at boot.
[    0.004073] AppArmor: AppArmor initialized
[    0.004086] Mount-cache hash table entries: 512
[    0.004307] Initializing cgroup subsys ns
[    0.004313] Initializing cgroup subsys cpuacct
[    0.004316] Initializing cgroup subsys memory
[    0.004335] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004339] CPU: L2 cache: 512K
[    0.004342] CPU: Physical Processor ID: 0
[    0.004358] Checking 'hlt' instruction... OK.
[    0.022118] ACPI: Core revision 20080609
[    0.024338] ACPI: Checking initramfs for custom DSDT
[    0.344063] ENABLING IO-APIC IRQs
[    0.344245] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.383934] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[    0.384024] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6001.43 BogoMIPS (lpj=12002865)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.468202] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[    0.468226] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.472065] Brought up 2 CPUs
[    0.472071] Total of 2 processors activated (12002.39 BogoMIPS).
[    0.472094] CPU0 attaching sched-domain:
[    0.472098]  domain 0: span 0-1 level SIBLING
[    0.472101]   groups: 0 1
[    0.472108]   domain 1: span 0-1 level CPU
[    0.472111]    groups: 0-1
[    0.472118] CPU1 attaching sched-domain:
[    0.472121]  domain 0: span 0-1 level SIBLING
[    0.472124]   groups: 1 0
[    0.472129]   domain 1: span 0-1 level CPU
[    0.472133]    groups: 0-1
[    0.472259] net_namespace: 840 bytes
[    0.472259] Booting paravirtualized kernel on bare hardware
[    0.472402] Time: 13:37:53  Date: 12/28/08
[    0.472440] NET: Registered protocol family 16
[    0.472474] EISA bus registered
[    0.472474] ACPI: bus type pci registered
[    0.497835] PCI: PCI BIOS revision 2.10 entry at 0xfbc10, last bus=2
[    0.497839] PCI: Using configuration type 1 for base access
[    0.500675] ACPI: EC: Look up EC in DSDT
[    0.507322] ACPI: Interpreter enabled
[    0.507328] ACPI: (supports S0 S1 S4 S5)
[    0.507349] ACPI: Using IOAPIC for interrupt routing
[    0.512775] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.512775] PCI: 0000:00:00.0 reg 10 32bit mmio: [f0000000, f3ffffff]
[    0.512775] PCI: 0000:00:1d.0 reg 20 io port: [ac00, ac1f]
[    0.512775] PCI: 0000:00:1d.1 reg 20 io port: [a000, a01f]
[    0.512775] PCI: 0000:00:1d.2 reg 20 io port: [a400, a41f]
[    0.512775] PCI: 0000:00:1d.3 reg 20 io port: [a800, a81f]
[    0.512775] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f7100000, f71003ff]
[    0.512775] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.512775] pci 0000:00:1d.7: PME# disabled
[    0.512775] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.512775] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.512775] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.512775] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.512775] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.512775] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.512775] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.512775] PCI: 0000:00:1f.1 reg 20 io port: [f000, f00f]
[    0.512775] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.512775] PCI: 0000:00:1f.3 reg 20 io port: [500, 51f]
[    0.512775] PCI: 0000:00:1f.5 reg 10 io port: [b400, b4ff]
[    0.512775] PCI: 0000:00:1f.5 reg 14 io port: [b800, b83f]
[    0.512775] PCI: 0000:00:1f.5 reg 18 32bit mmio: [f7101000, f71011ff]
[    0.512775] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [f7102000, f71020ff]
[    0.512775] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.512775] pci 0000:00:1f.5: PME# disabled
[    0.512812] PCI: 0000:01:00.0 reg 10 32bit mmio: [f4000000, f4ffffff]
[    0.512819] PCI: 0000:01:00.0 reg 14 32bit mmio: [e0000000, efffffff]
[    0.512825] PCI: 0000:01:00.0 reg 18 32bit mmio: [f5000000, f5ffffff]
[    0.512842] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.512890] PCI: bridge 0000:00:01.0 32bit mmio: [f4000000, f6ffffff]
[    0.512894] PCI: bridge 0000:00:01.0 32bit mmio pref: [e0000000, efffffff]
[    0.512937] PCI: 0000:02:08.0 reg 10 32bit mmio: [f7000000, f7000fff]
[    0.512945] PCI: 0000:02:08.0 reg 14 io port: [9000, 903f]
[    0.512980] pci 0000:02:08.0: supports D1
[    0.512982] pci 0000:02:08.0: supports D2
[    0.512985] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.512990] pci 0000:02:08.0: PME# disabled
[    0.516044] PCI: 0000:02:09.0 reg 10 32bit mmio: [f7001000, f70010ff]
[    0.516052] PCI: 0000:02:09.0 reg 14 io port: [9400, 9407]
[    0.516059] PCI: 0000:02:09.0 reg 18 io port: [9800, 98ff]
[    0.516091] pci 0000:02:09.0: supports D2
[    0.516094] pci 0000:02:09.0: PME# supported from D2 D3hot
[    0.516099] pci 0000:02:09.0: PME# disabled
[    0.516130] PCI: 0000:02:0d.0 reg 10 32bit mmio: [f7002000, f7002fff]
[    0.516170] pci 0000:02:0d.0: supports D1
[    0.516172] pci 0000:02:0d.0: supports D2
[    0.516175] pci 0000:02:0d.0: PME# supported from D0 D1 D2 D3hot
[    0.516179] pci 0000:02:0d.0: PME# disabled
[    0.516203] pci 0000:00:1e.0: transparent bridge
[    0.516208] PCI: bridge 0000:00:1e.0 io port: [9000, 9fff]
[    0.516213] PCI: bridge 0000:00:1e.0 32bit mmio: [f7000000, f70fffff]
[    0.516228] bus 00 -> node 0
[    0.516239] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.516497] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.524681] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.524681] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.524681] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.524681] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.524833] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.524991] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.525148] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.525308] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.525393] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.525393] pnp: PnP ACPI init
[    0.525393] ACPI: bus type pnp registered
[    0.532120] pnp: PnP ACPI: found 13 devices
[    0.532120] ACPI: ACPI bus type pnp unregistered
[    0.532120] PnPBIOS: Disabled by ACPI PNP
[    0.532120] PCI: Using ACPI for IRQ routing
[    0.536051] NET: Registered protocol family 8
[    0.536054] NET: Registered protocol family 20
[    0.536080] NetLabel: Initializing
[    0.536080] NetLabel:  domain hash size = 128
[    0.536080] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.536084] NetLabel:  unlabeled traffic allowed by default
[    0.536172] hpet clockevent registered
[    0.536178] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.536185] hpet0: 3 64-bit timers, 14318180 Hz
[    0.537929] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.537932]    actual entries 65620
[    0.538123] AppArmor: AppArmor Filesystem Enabled
[    0.538145] ACPI: RTC can wake from S4
[    0.540284] system 00:01: ioport range 0xb78-0xb7b has been reserved
[    0.540289] system 00:01: ioport range 0xf78-0xf7b has been reserved
[    0.540292] system 00:01: ioport range 0xa78-0xa7b has been reserved
[    0.540295] system 00:01: ioport range 0xe78-0xe7b has been reserved
[    0.540299] system 00:01: ioport range 0xbbc-0xbbf has been reserved
[    0.540302] system 00:01: ioport range 0xfbc-0xfbf has been reserved
[    0.540306] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.540309] system 00:01: ioport range 0x294-0x297 has been reserved
[    0.540331] system 00:0b: ioport range 0x400-0x4bf could not be reserved
[    0.540341] system 00:0c: iomem range 0xd1800-0xd3fff has been reserved
[    0.540345] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.540349] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.540352] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.540356] system 00:0c: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.540360] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.540364] system 00:0c: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.540368] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.540372] system 00:0c: iomem range 0xfec01000-0xfed8ffff could not be reserved
[    0.540375] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.540379] system 00:0c: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.540383] system 00:0c: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.540387] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
[    0.575964] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.575968] pci 0000:00:01.0:   IO window: disabled
[    0.575974] pci 0000:00:01.0:   MEM window: 0xf4000000-0xf6ffffff
[    0.575980] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.575987] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.575992] pci 0000:00:1e.0:   IO window: 0x9000-0x9fff
[    0.575998] pci 0000:00:1e.0:   MEM window: 0xf7000000-0xf70fffff
[    0.576003] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.576023] pci 0000:00:1e.0: setting latency timer to 64
[    0.576028] bus: 00 index 0 io port: [0, ffff]
[    0.576032] bus: 00 index 1 mmio: [0, ffffffff]
[    0.576037] bus: 01 index 0 mmio: [0, 0]
[    0.576040] bus: 01 index 1 mmio: [f4000000, f6ffffff]
[    0.576043] bus: 01 index 2 mmio: [e0000000, efffffff]
[    0.576046] bus: 01 index 3 mmio: [0, 0]
[    0.576048] bus: 02 index 0 io port: [9000, 9fff]
[    0.576052] bus: 02 index 1 mmio: [f7000000, f70fffff]
[    0.576055] bus: 02 index 2 mmio: [0, 0]
[    0.576057] bus: 02 index 3 io port: [0, ffff]
[    0.576060] bus: 02 index 4 mmio: [0, ffffffff]
[    0.576075] NET: Registered protocol family 2
[    0.588326] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.588738] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.589461] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.589905] TCP: Hash tables configured (established 131072 bind 65536)
[    0.589910] TCP reno registered
[    0.592387] NET: Registered protocol family 1
[    0.592551] checking if image is initramfs... it is
[    1.036289] Switched to high resolution mode on CPU 1
[    1.040072] Switched to high resolution mode on CPU 0
[    1.249064] Freeing initrd memory: 7943k freed
[    1.250461] audit: initializing netlink socket (disabled)
[    1.250480] type=2000 audit(1230471474.249:1): initialized
[    1.255607] highmem bounce pool size: 64 pages
[    1.255617] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.259637] VFS: Disk quotas dquot_6.5.1
[    1.259785] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.259952] msgmni has been set to 1761
[    1.260175] io scheduler noop registered
[    1.260179] io scheduler anticipatory registered
[    1.260182] io scheduler deadline registered
[    1.260202] io scheduler cfq registered (default)
[    1.260316] pci 0000:01:00.0: Boot video device
[    1.260328] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    1.261003] isapnp: Scanning for PnP cards...
[    1.614515] isapnp: No Plug & Play device found
[    1.681386] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.681548] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.681783] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.682770] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.683274] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.686732] brd: module loaded
[    1.686848] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.687080] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.687084] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.687551] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.689259] mice: PS/2 mouse device common for all mice
[    1.689517] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.689545] rtc0: alarms up to one month, hpet irqs
[    1.689803] EISA: Probing bus 0 at eisa.0
[    1.689848] EISA: Detected 0 cards.
[    1.689853] cpuidle: using governor ladder
[    1.689856] cpuidle: using governor menu
[    1.690613] TCP cubic registered
[    1.690651] Using IPI No-Shortcut mode
[    1.691036] registered taskstats version 1
[    1.691182]   Magic number: 4:102:636
[    1.691240] tty ptycf: hash matches
[    1.691335] rtc_cmos 00:03: setting system clock to 2008-12-28 13:37:55 UTC (1230471475)
[    1.691339] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.691342] EDD information not available.
[    1.691747] Freeing unused kernel memory: 424k freed
[    1.691803] Write protecting the kernel text: 2576k
[    1.691838] Write protecting the kernel read-only data: 936k
[    1.713100] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.908136] fuse init (API version 7.9)
[    2.032109] fan PNP0C0B:00: registered as cooling_device0
[    2.032124] ACPI: Fan [FAN] (on)
[    2.064119] processor ACPI0007:00: registered as cooling_device1
[    2.068069] processor ACPI0007:01: registered as cooling_device2
[    2.079923] thermal LNXTHERM:01: registered as thermal_zone0
[    2.080696] ACPI: Thermal Zone [THRM] (71 C)
[    2.366740] usbcore: registered new interface driver usbfs
[    2.366792] usbcore: registered new interface driver hub
[    2.380180] usbcore: registered new device driver usb
[    2.404449] USB Universal Host Controller Interface driver v3.0
[    2.404522] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.404537] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.404543] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.404633] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.404672] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ac00
[    2.404915] usb usb1: configuration #1 chosen from 1 choice
[    2.404966] hub 1-0:1.0: USB hub found
[    2.404980] hub 1-0:1.0: 2 ports detected
[    2.612524] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.612539] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.612546] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.612593] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.612641] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a000
[    2.612818] usb usb2: configuration #1 chosen from 1 choice
[    2.612875] hub 2-0:1.0: USB hub found
[    2.612889] hub 2-0:1.0: 2 ports detected
[    2.724070] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    2.741214] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    2.741220] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.820398] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.820414] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.820420] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.820474] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.820514] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a400
[    2.820700] usb usb3: configuration #1 chosen from 1 choice
[    2.820752] hub 3-0:1.0: USB hub found
[    2.820766] hub 3-0:1.0: 2 ports detected
[    2.870201] No dock devices found.
[    2.908935] usb 1-2: configuration #1 chosen from 1 choice
[    2.909705] SCSI subsystem initialized
[    2.946532] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.946549] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.946557] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.946647] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.946687] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000a800
[    2.947007] usb usb4: configuration #1 chosen from 1 choice
[    2.947073] hub 4-0:1.0: USB hub found
[    2.947093] hub 4-0:1.0: 2 ports detected
[    2.947977] libata version 3.00 loaded.
[    3.024067] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    3.153815] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.153840] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.153848] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.153926] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.157873] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.157898] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7100000
[    3.175632] usb 2-2: device descriptor read/all, error -71
[    3.176039] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.176359] usb usb5: configuration #1 chosen from 1 choice
[    3.176431] hub 5-0:1.0: USB hub found
[    3.176670] hub 5-0:1.0: 8 ports detected
[    3.233092] hub 2-0:1.0: unable to enumerate USB device on port 2
[    3.380098] usb 1-2: USB disconnect, address 2
[    3.383817] ata_piix 0000:00:1f.1: version 2.12
[    3.383823] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.383847] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.383906] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.389054] scsi0 : ata_piix
[    3.389235] scsi1 : ata_piix
[    3.390577] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    3.390582] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    3.406923] e100 0000:02:08.0: PME# disabled
[    3.407542] e100: eth0: e100_probe: addr 0xf7000000, irq 20, MAC addr 00:0c:76:29:7a:20
[    3.561390] ata1.00: ATAPI: Optiarc DVD RW AD-7173A, 1-01, max UDMA/66
[    3.561421] ata1.01: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
[    3.577353] ata1.00: configured for UDMA/66
[    3.593315] ata1.01: configured for UDMA/33
[    3.672028] usb 5-4: new high speed USB device using ehci_hcd and address 3
[    3.757509] ata2.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[    3.757514] ata2.00: 320173056 sectors, multi 16: LBA48 
[    3.772409] ata2.00: configured for UDMA/100
[    3.773525] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7173A  1-01 PQ: 0 ANSI: 5
[    3.784069] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
[    3.784299] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
[    3.784434] ohci1394 0000:02:0d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.805042] usb 5-4: configuration #1 chosen from 1 choice
[    3.836282] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[f7002000-f70027ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.868700] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.868831] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    3.868922] scsi 1:0:0:0: Attached scsi generic sg2 type 0
[    3.901960] Driver 'sd' needs updating - please use bus_type methods
[    3.904258] sd 1:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[    3.904296] sd 1:0:0:0: [sda] Write Protect is off
[    3.904301] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.904357] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.904493] sd 1:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[    3.904527] sd 1:0:0:0: [sda] Write Protect is off
[    3.904532] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.904591] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.904600]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    3.911995] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.912015] Uniform CD-ROM driver Revision: 3.20
[    3.912147] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.916001]  sda1 sda2 sda3
[    3.916042] usb 5-7: new high speed USB device using ehci_hcd and address 4
[    3.919688] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    3.919826] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    3.926793] sd 1:0:0:0: [sda] Attached SCSI disk
[    4.115247] usb 5-7: configuration #1 chosen from 1 choice
[    4.115847] usbcore: registered new interface driver hiddev
[    4.352019] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    4.528565] usb 1-2: configuration #1 chosen from 1 choice
[    4.544715] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
[    4.545194] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
[    4.545789] usbcore: registered new interface driver usbhid
[    4.545794] usbcore: registered new interface driver libusual
[    4.545801] usbhid: v2.6:USB HID core driver
[    4.558537] Initializing USB Mass Storage driver...
[    4.559197] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.561216] usbcore: registered new interface driver usb-storage
[    4.561226] USB Mass Storage support registered.
[    4.562269] usb-storage: device found at 4
[    4.562276] usb-storage: waiting for device to settle before scanning
[    4.641307] PM: Starting manual resume from disk
[    4.641313] PM: Resume from partition 8:2
[    4.641316] PM: Checking hibernation image.
[    4.641558] PM: Resume from disk failed.
[    4.686282] kjournald starting.  Commit interval 5 seconds
[    4.686306] EXT3-fs: mounted filesystem with ordered data mode.
[    5.112223] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000010dc002b34f9]
[    9.565633] usb-storage: device scan complete
[    9.569216] scsi 2:0:0:0: Direct-Access     IN-WIN   iAPP  HS-CF      1.95 PQ: 0 ANSI: 0
[    9.572342] scsi 2:0:0:1: Direct-Access     IN-WIN   iAPP  HS-MS      1.95 PQ: 0 ANSI: 0
[    9.575580] scsi 2:0:0:2: Direct-Access     IN-WIN   iAPP  HS-SM      1.95 PQ: 0 ANSI: 0
[    9.578457] scsi 2:0:0:3: Direct-Access     IN-WIN   iAPP  HS-SD/MMC  1.95 PQ: 0 ANSI: 0
[    9.582799] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    9.582956] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    9.586807] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[    9.586940] sd 2:0:0:1: Attached scsi generic sg4 type 0
[    9.590790] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[    9.590891] sd 2:0:0:2: Attached scsi generic sg5 type 0
[    9.704030] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[    9.930532] sd 2:0:0:3: [sde] Attached SCSI removable disk
[    9.930694] sd 2:0:0:3: Attached scsi generic sg6 type 0
[   10.721106] udevd version 124 started
[   11.533522] Linux agpgart interface v0.103
[   11.563607] intel_rng: FWH not detected
[   11.574487] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.595406] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.626101] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   11.628737] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf0000000
[   11.713024] iTCO_vendor_support: vendor-support=0
[   11.740574] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   11.740751] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   11.740945] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.065672] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   12.130553] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   12.145096] ACPI: Power Button (FF) [PWRF]
[   12.145318] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   12.177075] ACPI: Power Button (CM) [PWRB]
[   12.286393] nvidia: module license 'NVIDIA' taints kernel.
[   12.654506] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.655757] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   12.718003] parport_pc 00:09: reported by Plug and Play ACPI
[   12.718060] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   14.000057] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[   14.134707] phy0: Selected rate control algorithm 'pid'
[   14.209865] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.209896] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.533047] intel8x0_measure_ac97_clock: measured 54596 usecs
[   14.533054] intel8x0: clocking to 48000
[   14.594853] zd1211rw 5-4:1.0: phy0
[   14.594898] usbcore: registered new interface driver zd1211rw
[   17.653149] lp0: using parport0 (interrupt-driven).
[   17.877802] Adding 1951888k swap on /dev/sda2.  Priority:-1 extents:1 across:1951888k
[   18.454276] EXT3 FS on sda1, internal journal
[   19.306892] kjournald starting.  Commit interval 5 seconds
[   19.307184] EXT3 FS on sda3, internal journal
[   19.307192] EXT3-fs: mounted filesystem with ordered data mode.
[   19.604378] type=1505 audit(1230471493.085:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4178
[   19.789597] type=1505 audit(1230471493.269:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4183
[   19.789879] type=1505 audit(1230471493.269:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4183
[   19.944133] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.628911] ACPI: WMI: Mapper loaded
[   22.065650] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   22.139121] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   22.139129] apm: disabled - APM is not SMP safe.
[   22.309248] ppdev: user-space parallel port driver
[   25.987358] Bluetooth: Core ver 2.13
[   25.988454] NET: Registered protocol family 31
[   25.988466] Bluetooth: HCI device and connection manager initialized
[   25.988474] Bluetooth: HCI socket layer initialized
[   26.008335] Bluetooth: L2CAP ver 2.11
[   26.008343] Bluetooth: L2CAP socket layer initialized
[   26.021956] Bluetooth: SCO (Voice Link) ver 0.6
[   26.021963] Bluetooth: SCO socket layer initialized
[   26.036160] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.036168] Bluetooth: BNEP filters: protocol multicast
[   26.064274] Bridge firewalling registered
[   26.064617] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   26.090762] Bluetooth: RFCOMM socket layer initialized
[   26.090790] Bluetooth: RFCOMM TTY layer initialized
[   26.090795] Bluetooth: RFCOMM ver 1.10
[   27.599894] NET: Registered protocol family 10
[   27.602907] lo: Disabled Privacy Extensions
[   29.612591] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   29.612622] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   29.612681] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   30.239362] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.251656] firmware: requesting zd1211/zd1211b_ub
[   30.289198] firmware: requesting zd1211/zd1211b_uphr
[   30.416476] zd1211rw 5-4:1.0: firmware version 4725
[   30.456470] zd1211rw 5-4:1.0: zd1211b chip 079b:0062 v4810 high 00-60-b3 AL2230_RF pa0 g--NS
[   30.514199] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.656390] NET: Registered protocol family 17
[  133.380426] UDF-fs: No VRS found
[  133.391893] ISO 9660 Extensions: Microsoft Joliet Level 1
[  133.392211] ISOFS: changing to secondary root
[  142.365120] wlan0: authenticate with AP 00:1a:6b:1b:7a:30
[  142.366852] wlan0: authenticated
[  142.366865] wlan0: associate with AP 00:1a:6b:1b:7a:30
[  142.369107] wlan0: RX AssocResp from 00:1a:6b:1b:7a:30 (capab=0x411 status=0 aid=1)
[  142.369118] wlan0: associated
[  142.370045] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  152.872011] wlan0: no IPv6 routers present
[  209.771505] ppdev0: registered pardevice
[  209.821037] ppdev0: unregistered pardevice
[  210.392464] ppdev0: registered pardevice
[  210.440207] ppdev0: unregistered pardevice
[  210.524514] ppdev0: registered pardevice
[  210.572367] ppdev0: unregistered pardevice
[  435.681038] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  852.910471] type=1505 audit(1230472326.389:5): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=10599
[  852.970340] type=1505 audit(1230472326.450:6): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=10604
[  853.167221] type=1505 audit(1230472326.646:7): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=10608
[  853.167928] type=1505 audit(1230472326.646:8): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=10608
[  915.692030] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  921.701131] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  997.744104] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[ 1179.680039] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[ 1273.660073] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[ 1387.673035] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[ 1425.690985] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[ 1439.673049] usb 5-7: reset high speed USB device using ehci_hcd and address 4
```

---

### Post by linux_tech on 2008-12-28
Try running a memtest again on it, let it run for at least 30min-1hr
to if there are any errors.

---

### Post by Ivorydawn on 2008-12-28
Hi,

Try adding acpi=ht to your kernel parameters at boot time, alternative is to turn it off completely by acpi=off you can edit the kernel parameters at the GRUB boot prompt.

It worked for me, I was having random total freezes and now it's all fine.

HTH

Regards

Andrew

---

### Post by phonixor on 2008-12-29
thanks i don't know if i did the change correctly... but it did have some effect... instead of the usual freeze or ... partly reboot...
i got a complete instant shutdown...

:popcorn:

i changed the file 
/boot/grub/menu.lst
to:

```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a11173ab-3b7c-4f1e-84fd-e0b9b389a0e5 ro quiet splash acpi=ht
## GJSEDIT ##kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a11173ab-3b7c-4f1e-84fd-e0b9b389a0e5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```

i restored it now... guess the memtests are up next!!

---

### Post by Ivorydawn on 2008-12-29
Hi, 

I changed mine at the GRUB menu, I'm not sure if you have to do anything else when you amend the file directly such as update GRUB in some way after the amendment so as not to corrupt the file.  

what do the Kernel parameters look like when you view them at the GRUB menu? instructions are at the bottom of the screen. If you don't get a menu then maybe the file has been corrupted.

Regards

Andrew

---

### Post by Ivorydawn on 2008-12-29
HI again,

Definitely try the Memtest, I did mine when I was having the random freezes, it's something else to cross off the list.

Regards

Andrew

---

### Post by phonixor on 2009-01-02
thanks for the help so far...

i did an memtest for a couple of hours... 6 passes and no errors.
i tried it a couple of times... but sometimes my comp crashed during startup or during memtest... so thats no good... 

i recently fixed my other comp (XP) by cleaning the fan for the cpu.. (which got to 110C :P... (before shutting down the pc))... but i ran 

```
watch acpi -V
``` 

which i found on the forums... and it didn't get all that warm (on my ubuntu pc)..  still i cleaned the fan for this comp aswell... but that didn't fix it either...
(cant remember how hot it went though... but now its 42C... but its not doing much...:P )

...

guess i ruled out:
- CPU heating
- Ubuntu (unless memtest has similar issues :P)
- Corrupt ram?

wonder what else could be wrong or what i could test...
any ideas suggestions... thanks in advance!

:confused:

---

