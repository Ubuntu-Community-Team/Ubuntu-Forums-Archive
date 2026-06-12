---
title: "Starting Ubuntu Extremely Slow"
date: 2009-01-23
forum: General Help
---

### Post by flylehe on 2009-01-23
Hi,
Today Ubuntu 8.10 boots extremely slow on my laptop. It has been stuck at where the mouse is like a rotating circle for hours and when leaving it alone long enough the screen saver is flashing irregularly. Restart doesn't help.
My Ubuntu was just installed last week. Last time when I was using it, I installed some packages for videos playing, programmed with some C++ code and read some documents and webpages. It gradually became slower and slower. Eventually it didn't respond to my clicking to open a text file before I decided to shut it down and restart it over again. Now I am stuck at the middle of booting. Could someone give me some advice?
Thanks in advance!

---

### Post by hwttdz on 2009-01-23
Can you run the command dmesg at the terminal, and post the output here.

---

### Post by flylehe on 2009-01-23
Ok, I manually typed here what I got on the screen under recovery mode, though some information at the beginning was popped out of the screen. [...] are some serial numbers I guess might be trivial. Thanks!

......
[...]ACPI: WMI: Mapper loaded
[...]acer-wmi: Acer Laptop ACPI-WMI Extras
[...]acer-wmi: No or unsupported WMI interface, unable to load
[...]Broadcom 43xx driver loaded [Features: PLR, Firmware-ID: FW13]
[...]Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04712/0x4000
[...]input: Synps/2 Synaptics TouchhPad as /devices/platform/i8042/serio1/input/input8
[...]cs: IO port probe 0x100-0x3af: clean.
[...]cs: IO port probe ox3e0-ox4ff: excluding 0x480-0x48f
[...]cs: IO port probe 0x820-0x8ff: clean.
[...]cs: IO port probe 0xc00-0xcf7: clean.
[...]cs: IO port probe 0xa00-0xaff: clean.
[...]lp: driver loaded but no devices found
[...]Adding 971892k swap on /dev/sda7. Priority:-1 extents:1 across:971892k
[...]EXT3 FS on sda6, internal journal
[...]type=1505 audit(1232742879.964:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3876
[...]type=1505 audit(1232742880.208:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3881
[...]type=1505 audit(1232742880.208:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3876
[...]ip_tables: (C) 2000-2006 Netfilter Core Team

---

### Post by hwttdz on 2009-01-23
try doing
dmesg > temp.txt, then you can post the contents of temp.txt here.  The serial numbers are times, and they're helpful because it allows one to determine how much time the system is spending on each step.

---

### Post by flylehe on 2009-01-23
To get the text file out of my laptop, I tried to have network connection by switching the runlevel using "telinit" but always ended up with the graphical mode and endless stucking again. Which level is it? Thanks!

---

### Post by flylehe on 2009-01-23
I managed to get the output of dmesg as here:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003befa000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003befa000 - 000000003bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3bef0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781f000 - 37fef9bb
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7F60, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3BEF61BE, 0034 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3BEF9E5F, 0074 (r1 SiS    755F      6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 3BEF61F2, 3C6D (r1 PTLTD       755  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BEFAFC0, 0040
[    0.000000] ACPI: SSDT 3BEF9ED3, 00B5 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 3BEF9F88, 0050 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3BEF9FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [003781f000 - 0037fef9bb]          RAMDISK ==> [003781f000 - 0037fef9bb]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f7fd0] 000f7fd0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003bef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bef0
[    0.000000] On node 0 totalpages: 245391
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 15970 pages, LIFO batch:3
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bff00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243233
[    0.000000] Kernel command line: root=UUID=90d4e706-7a53-4c67-b6af-aac7aecef8e3 ro  single
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1600.048 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 958788k/981952k available (2572k kernel code, 22404k reserved, 1160k data, 424k init, 64448k highmem)
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
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.09 BogoMIPS (lpj=6400192)
[    0.004091] Security Framework initialized
[    0.004126] SELinux:  Disabled at boot.
[    0.004179] AppArmor: AppArmor initialized
[    0.004216] Mount-cache hash table entries: 512
[    0.004411] Initializing cgroup subsys ns
[    0.004444] Initializing cgroup subsys cpuacct
[    0.004475] Initializing cgroup subsys memory
[    0.004519] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004552] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.004592] Checking 'hlt' instruction... OK.
[    0.020487] SMP alternatives: switching to UP code
[    0.027029] Freeing SMP alternatives: 11k freed
[    0.027063] ACPI: Core revision 20080609
[    0.028711] ACPI: Checking initramfs for custom DSDT
[    0.448236] ENABLING IO-APIC IRQs
[    0.448458] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.489102] CPU0: AMD Turion(tm) 64 Mobile Technology ML-30 stepping 02
[    0.492030] Brought up 1 CPUs
[    0.492030] Total of 1 processors activated (3200.09 BogoMIPS).
[    0.492030] CPU0 attaching sched-domain:
[    0.492030]  domain 0: span 0 level CPU
[    0.492030]   groups: 0
[    0.492030] net_namespace: 840 bytes
[    0.492030] Booting paravirtualized kernel on bare hardware
[    0.492030] Time: 17:26:12  Date: 01/23/09
[    0.492030] NET: Registered protocol family 16
[    0.492030] EISA bus registered
[    0.492030] ACPI: bus type pci registered
[    0.492030] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
[    0.492030] PCI: Using configuration type 1 for base access
[    0.492030] ACPI: EC: Look up EC in DSDT
[    0.493895] ACPI: Interpreter enabled
[    0.493927] ACPI: (supports S0 S3 S4 S5)
[    0.494064] ACPI: Using IOAPIC for interrupt routing
[    0.494394] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.534878] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.534911] ACPI: EC: driver started in interrupt mode
[    0.534993] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.535104] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e1ffffff]
[    0.535189] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.535245] PCI: 0000:00:02.1 reg 20 io port: [8100, 811f]
[    0.535270] PCI: 0000:00:02.5 reg 10 io port: [1f0, 1f7]
[    0.535276] PCI: 0000:00:02.5 reg 14 io port: [3f4, 3f7]
[    0.535282] PCI: 0000:00:02.5 reg 18 io port: [170, 177]
[    0.535287] PCI: 0000:00:02.5 reg 1c io port: [374, 377]
[    0.535293] PCI: 0000:00:02.5 reg 20 io port: [2000, 200f]
[    0.535323] PCI: 0000:00:02.6 reg 10 io port: [1000, 10ff]
[    0.535329] PCI: 0000:00:02.6 reg 14 io port: [1c00, 1c7f]
[    0.535356] pci 0000:00:02.6: supports D1
[    0.535358] pci 0000:00:02.6: supports D2
[    0.535361] pci 0000:00:02.6: PME# supported from D3hot D3cold
[    0.535394] pci 0000:00:02.6: PME# disabled
[    0.535442] PCI: 0000:00:02.7 reg 10 io port: [1400, 14ff]
[    0.535449] PCI: 0000:00:02.7 reg 14 io port: [1c80, 1cff]
[    0.535474] pci 0000:00:02.7: supports D1
[    0.535477] pci 0000:00:02.7: supports D2
[    0.535479] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.535512] pci 0000:00:02.7: PME# disabled
[    0.535555] PCI: 0000:00:03.0 reg 10 32bit mmio: [e2002000, e2002fff]
[    0.535590] PCI: 0000:00:03.1 reg 10 32bit mmio: [e2003000, e2003fff]
[    0.535631] PCI: 0000:00:03.2 reg 10 32bit mmio: [e2004000, e2004fff]
[    0.535659] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    0.535693] pci 0000:00:03.2: PME# disabled
[    0.535745] PCI: 0000:00:04.0 reg 10 io port: [1800, 18ff]
[    0.535751] PCI: 0000:00:04.0 reg 14 32bit mmio: [e2005000, e2005fff]
[    0.535769] PCI: 0000:00:04.0 reg 30 32bit mmio: [0, 1ffff]
[    0.535780] pci 0000:00:04.0: supports D1
[    0.535782] pci 0000:00:04.0: supports D2
[    0.535785] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.535819] pci 0000:00:04.0: PME# disabled
[    0.535869] PCI: 0000:00:06.0 reg 10 32bit mmio: [0, fff]
[    0.535880] pci 0000:00:06.0: supports D1
[    0.535882] pci 0000:00:06.0: supports D2
[    0.535885] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.535919] pci 0000:00:06.0: PME# disabled
[    0.535963] PCI: 0000:00:0b.0 reg 10 32bit mmio: [e2000000, e2001fff]
[    0.536099] PCI: 0000:01:00.0 reg 10 32bit mmio: [e8000000, efffffff]
[    0.536104] PCI: 0000:01:00.0 reg 14 32bit mmio: [e2100000, e211ffff]
[    0.536109] PCI: 0000:01:00.0 reg 18 io port: [a000, a07f]
[    0.536125] pci 0000:01:00.0: supports D1
[    0.536127] pci 0000:01:00.0: supports D2
[    0.536149] PCI: bridge 0000:00:01.0 io port: [a000, afff]
[    0.536153] PCI: bridge 0000:00:01.0 32bit mmio: [e2100000, e21fffff]
[    0.536158] PCI: bridge 0000:00:01.0 32bit mmio pref: [e8000000, efffffff]
[    0.536177] bus 00 -> node 0
[    0.536184] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.545971] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[    0.546344] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
[    0.546726] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
[    0.547094] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[    0.547489] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[    0.547857] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[    0.548252] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.548668] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[    0.549123] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.549203] pnp: PnP ACPI init
[    0.549240] ACPI: bus type pnp registered
[    0.551827] pnp: PnP ACPI: found 8 devices
[    0.551858] ACPI: ACPI bus type pnp unregistered
[    0.551890] PnPBIOS: Disabled by ACPI PNP
[    0.552296] PCI: Using ACPI for IRQ routing
[    0.552436] NET: Registered protocol family 8
[    0.552436] NET: Registered protocol family 20
[    0.552436] NetLabel: Initializing
[    0.552436] NetLabel:  domain hash size = 128
[    0.552436] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.552436] NetLabel:  unlabeled traffic allowed by default
[    0.552658] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.552690]    actual entries 65620
[    0.552907] AppArmor: AppArmor Filesystem Enabled
[    0.552950] ACPI: RTC can wake from S4
[    0.552986] system 00:04: ioport range 0x8000-0x807f has been reserved
[    0.552986] system 00:04: ioport range 0x8080-0x80ff has been reserved
[    0.552986] system 00:04: ioport range 0x8100-0x811f has been reserved
[    0.552986] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.552986] system 00:04: ioport range 0x3f0-0x3f1 has been reserved
[    0.552986] system 00:04: iomem range 0xfec00000-0xfecfffff has been reserved
[    0.552986] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.552986] system 00:04: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.552986] system 00:04: iomem range 0xffc00000-0xffc00fff has been reserved
[    0.552986] system 00:04: iomem range 0xffe00000-0xffe00fff has been reserved
[    0.552986] system 00:04: iomem range 0xffe80000-0xffefffff has been reserved
[    0.552986] system 00:04: iomem range 0xfffe0000-0xfffeffff could not be reserved
[    0.552986] system 00:04: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.588953] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.588987] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.589021] pci 0000:00:01.0:   MEM window: 0xe2100000-0xe21fffff
[    0.589055] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
[    0.589371] pci 0000:00:06.0: CardBus bridge, secondary bus 0000:02
[    0.589403] pci 0000:00:06.0:   IO window: 0x002400-0x0024ff
[    0.589437] pci 0000:00:06.0:   IO window: 0x002800-0x0028ff
[    0.589470] pci 0000:00:06.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.589504] pci 0000:00:06.0:   MEM window: 0x54000000-0x57ffffff
[    0.589547] pci 0000:00:06.0: enabling device (0000 -> 0003)
[    0.589585] pci 0000:00:06.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.589620] bus: 00 index 0 io port: [0, ffff]
[    0.589651] bus: 00 index 1 mmio: [0, ffffffff]
[    0.589682] bus: 01 index 0 io port: [a000, afff]
[    0.589713] bus: 01 index 1 mmio: [e2100000, e21fffff]
[    0.589744] bus: 01 index 2 mmio: [e8000000, efffffff]
[    0.589776] bus: 01 index 3 mmio: [0, 0]
[    0.589806] bus: 02 index 0 io port: [2400, 24ff]
[    0.589837] bus: 02 index 1 io port: [2800, 28ff]
[    0.589868] bus: 02 index 2 mmio: [50000000, 53ffffff]
[    0.589899] bus: 02 index 3 mmio: [54000000, 57ffffff]
[    0.589940] NET: Registered protocol family 2
[    0.590110] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.590510] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.591755] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.592454] TCP: Hash tables configured (established 131072 bind 65536)
[    0.592487] TCP reno registered
[    0.592656] NET: Registered protocol family 1
[    0.592853] checking if image is initramfs... it is
[    1.092074] Switched to high resolution mode on CPU 0
[    1.467556] Freeing initrd memory: 8002k freed
[    1.467810] Simple Boot Flag at 0x38 set to 0x1
[    1.468598] audit: initializing netlink socket (disabled)
[    1.468647] type=2000 audit(1232731572.468:1): initialized
[    1.476126] highmem bounce pool size: 64 pages
[    1.476162] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.478921] VFS: Disk quotas dquot_6.5.1
[    1.479059] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.479210] msgmni has been set to 1763
[    1.479375] io scheduler noop registered
[    1.479407] io scheduler anticipatory registered
[    1.479438] io scheduler deadline registered
[    1.479479] io scheduler cfq registered (default)
[    1.898304] pci 0000:01:00.0: Boot video device
[    1.898663] isapnp: Scanning for PnP cards...
[    2.251946] isapnp: No Plug & Play device found
[    2.294378] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.295092] serial 0000:00:02.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.295129] serial 0000:00:02.6: PCI INT C disabled
[    2.297109] brd: module loaded
[    2.297226] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.297393] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.299872] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.299908] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.300429] mice: PS/2 mouse device common for all mice
[    2.300614] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.300667] rtc0: alarms up to one year, y3k
[    2.300836] EISA: Probing bus 0 at eisa.0
[    2.300872] Cannot allocate resource for EISA slot 1
[    2.300904] Cannot allocate resource for EISA slot 2
[    2.300952] Cannot allocate resource for EISA slot 8
[    2.300983] EISA: Detected 0 cards.
[    2.301015] cpuidle: using governor ladder
[    2.301046] cpuidle: using governor menu
[    2.301654] TCP cubic registered
[    2.301712] Using IPI No-Shortcut mode
[    2.301952] registered taskstats version 1
[    2.302091]   Magic number: 9:873:441
[    2.302381] rtc_cmos 00:02: setting system clock to 2009-01-23 17:26:14 UTC (1232731574)
[    2.302417] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.302449] EDD information not available.
[    2.303012] Freeing unused kernel memory: 424k freed
[    2.303114] Write protecting the kernel text: 2576k
[    2.303187] Write protecting the kernel read-only data: 936k
[    2.332463] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.453382] fuse init (API version 7.9)
[    2.483317] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.483515] processor ACPI0007:00: registered as cooling_device0
[    2.483550] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.486781] Marking TSC unstable due to TSC halts in idle
[    2.487810] thermal LNXTHERM:01: registered as thermal_zone0
[    2.493444] ACPI: Thermal Zone [THRM] (65 C)
[    3.034997] No dock devices found.
[    3.115632] SCSI subsystem initialized
[    3.231545] libata version 3.00 loaded.
[    3.242517] usbcore: registered new interface driver usbfs
[    3.242582] usbcore: registered new interface driver hub
[    3.265423] usbcore: registered new device driver usb
[    3.277319] sis900.c: v1.08.10 Apr. 2 2006
[    3.277390] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.282275] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[    3.288137] 0000:00:04.0: Using transceiver found at address 13 as default
[    3.291297] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 19, 00:c0:9f:9d:46:47
[    3.291430] pata_acpi 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.291518] pata_acpi 0000:00:02.5: PCI INT A disabled
[    3.294194] pata_sis 0000:00:02.5: version 0.5.2
[    3.294202] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.297214] scsi0 : pata_sis
[    3.315671] scsi1 : pata_sis
[    3.315953] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2000 irq 14
[    3.315987] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2008 irq 15
[    3.336098] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.480421] ata1.00: ATA-6: ST9100822A, 3.01, max UDMA/100
[    3.480460] ata1.00: 195371568 sectors, multi 16: LBA48 
[    3.496382] ata1.00: configured for UDMA/100
[    3.660296] ata2.00: ATAPI: Slimtype DVDRW SOSW-833S, VRS2, max UDMA/33
[    3.676237] ata2.00: configured for UDMA/33
[    3.676411] scsi 0:0:0:0: Direct-Access     ATA      ST9100822A       3.01 PQ: 0 ANSI: 5
[    3.677107] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SOSW-833S  VRS2 PQ: 0 ANSI: 5
[    3.677394] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.677442] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.677520] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    3.677580] ohci_hcd 0000:00:03.0: irq 20, io mem 0xe2002000
[    3.732223] usb usb1: configuration #1 chosen from 1 choice
[    3.732291] hub 1-0:1.0: USB hub found
[    3.732332] hub 1-0:1.0: 3 ports detected
[    3.940317] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.940370] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.940427] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[    3.940485] ohci_hcd 0000:00:03.1: irq 21, io mem 0xe2003000
[    3.996135] usb usb2: configuration #1 chosen from 1 choice
[    3.996197] hub 2-0:1.0: USB hub found
[    3.996236] hub 2-0:1.0: 3 ports detected
[    4.100193] ehci_hcd 0000:00:03.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    4.100237] ehci_hcd 0000:00:03.2: EHCI Host Controller
[    4.100293] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[    4.100366] ehci_hcd 0000:00:03.2: cache line size of 64 is not supported
[    4.100382] ehci_hcd 0000:00:03.2: irq 23, io mem 0xe2004000
[    4.116032] usb 1-2: new low speed USB device using ohci_hcd and address 2
[    4.128025] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.128325] usb usb3: configuration #1 chosen from 1 choice
[    4.128556] hub 3-0:1.0: USB hub found
[    4.128594] hub 3-0:1.0: 6 ports detected
[    4.184031] hub 1-0:1.0: unable to enumerate USB device on port 2
[    4.340244] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.400062] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0b.0
[    4.414890] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.414972] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.500885] Driver 'sd' needs updating - please use bus_type methods
[    4.501051] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    4.501105] sd 0:0:0:0: [sda] Write Protect is off
[    4.501137] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.501172] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.501285] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    4.501335] sd 0:0:0:0: [sda] Write Protect is off
[    4.501367] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.501401] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.501439]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.523172]  sda1 sda2 sda3 < sda5 sda6 sda7 >
[    4.576823] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.586321] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.586361] Uniform CD-ROM driver Revision: 3.20
[    4.586494] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.696028] usb 1-2: new low speed USB device using ohci_hcd and address 3
[    4.910020] usb 1-2: configuration #1 chosen from 1 choice
[    4.936729] usbcore: registered new interface driver hiddev
[    4.942211] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:03.0/usb1/1-2/1-2:1.0/input/input2
[    4.943732] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:03.0-2
[    4.943885] usbcore: registered new interface driver usbhid
[    4.943919] usbhid: v2.6:USB HID core driver
[    5.046797] PM: Starting manual resume from disk
[    5.046831] PM: Resume from partition 8:7
[    5.046833] PM: Checking hibernation image.
[    5.046978] PM: Resume from disk failed.
[    5.101680] kjournald starting.  Commit interval 5 seconds
[    5.101731] EXT3-fs: mounted filesystem with ordered data mode.
[   14.204156] udevd version 124 started
[   15.024882] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.125692] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.199684] Linux agpgart interface v0.103
[   15.249774] agpgart-amd64 0000:00:00.0: AGP bridge [1039/0760]
[   15.251879] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xe0000000
[   15.649561] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[   15.768631] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
[   15.768683] Yenta: Using CSCINT to route CSC interrupts to PCI
[   15.768715] Yenta: Routing CardBus interrupts to PCI
[   15.768749] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
[   15.820492] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   15.832022] ACPI: Power Button (FF) [PWRF]
[   15.832214] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   15.834317] ACPI: Lid Switch [LID]
[   15.834428] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   15.854112] ACPI: Power Button (CM) [PWRB]
[   15.854274] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   15.868016] ACPI: Sleep Button (CM) [SLPB]
[   15.907044] ACPI: AC Adapter [ACAD] (on-line)
[   15.995509] ACPI: Battery Slot [BAT1] (battery present)
[   16.000776] Yenta: ISA IRQ mask 0x06f8, PCI irq 19
[   16.000810] Socket status: 30000006
[   16.887003] b43-phy0: Broadcom 4318 WLAN found
[   16.977322] phy0: Selected rate control algorithm 'pid'
[   17.333919] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   17.610416] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   17.715405] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   17.952260] ACPI: WMI: Mapper loaded
[   18.114504] acer-wmi: Acer Laptop ACPI-WMI Extras
[   18.114554] acer-wmi: No or unsupported WMI interface, unable to load
[   18.274441] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   18.309872] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   18.540182] intel8x0_measure_ac97_clock: measured 55459 usecs
[   18.540221] intel8x0: clocking to 48000
[   19.609044] cs: IO port probe 0x100-0x3af: clean.
[   19.610739] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[   19.611533] cs: IO port probe 0x820-0x8ff: clean.
[   19.612182] cs: IO port probe 0xc00-0xcf7: clean.
[   19.612986] cs: IO port probe 0xa00-0xaff: clean.
[   20.259001] lp: driver loaded but no devices found
[   20.499196] Adding 971892k swap on /dev/sda7.  Priority:-1 extents:1 across:971892k
[   21.060157] EXT3 FS on sda6, internal journal
[  101.049886] type=1505 audit(1232749672.955:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3877
[  101.294929] type=1505 audit(1232749673.199:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3882
[  101.295258] type=1505 audit(1232749673.199:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3882
[  101.475272] ip_tables: (C) 2000-2006 Netfilter Core Team

---

