---
title: "ubuntu 8.10 keeps freezing"
date: 2008-12-23
forum: General Help
---

### Post by nerktord on 2008-12-23
I've recently be encountering some random freezes(mouse, keyboard, apps, everything)..I've tried to boot out of x using many methods, but failed. I have to hold down the power button to restart(hardboot). These freezes are happening more and more often now, like one every 30 min.

This has only been happening since I freshly installed 8.10, I'm pretty sure I never had anything like this on 8.04, because I probably would of remembered. I use to have a few application crash now and again, but they would never take down the entire system.

Concerning these freezes, I first thought it could possibly be firefox, because it always froze when firefox was open. But I've noticed now, it's quite random regardless of the app I'm using.

Any solutions?

Heres a dmesg log right after it crashed

```

[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f85b0] 000f85b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x00077d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00077d90
[    0.000000] On node 0 totalpages: 490797
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 259221 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: SiS     
[    0.000000] MPTABLE: Product ID: 671MX       
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] I/O APIC #2 Version 20 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:68000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 486482
[    0.000000] Kernel command line: root=UUID=1db1b79e-50b0-4f56-9170-29693780d7f3 ro quiet splash acpi=off noapic nolapic apm=power_off acpi=force
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1466.641 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1931140k/1963584k available (2572k kernel code, 31108k reserved, 1160k data, 424k init, 1046080k highmem)
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
[    0.004023] Calibrating delay loop (skipped), value calculated using timer frequency.. 2933.28 BogoMIPS (lpj=5866564)
[    0.004064] Security Framework initialized
[    0.004080] SELinux:  Disabled at boot.
[    0.004125] AppArmor: AppArmor initialized
[    0.004142] Mount-cache hash table entries: 512
[    0.004515] Initializing cgroup subsys ns
[    0.004524] Initializing cgroup subsys cpuacct
[    0.004531] Initializing cgroup subsys memory
[    0.004563] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004569] CPU: L2 cache: 1024K
[    0.004576] CPU: Physical Processor ID: 0
[    0.004581] CPU: Processor Core ID: 0
[    0.004589] using mwait in idle threads.
[    0.004609] Checking 'hlt' instruction... OK.
[    0.024009] ACPI: Core revision 20080609
[    0.028259] ACPI: Checking initramfs for custom DSDT
[    0.864135] BIOS bug, local APIC #0 not detected!...
[    0.864194] ... forcing use of dummy APIC emulation.(tell your hw vendor)
[    0.864249] SMP disabled
[    0.864383] Brought up 1 CPUs
[    0.864389] Total of 1 processors activated (2933.28 BogoMIPS).
[    0.864411] CPU0 attaching sched-domain:
[    0.864417]  domain 0: span 0 level CPU
[    0.864424]   groups: 0
[    0.864954] net_namespace: 840 bytes
[    0.864994] Booting paravirtualized kernel on bare hardware
[    0.865420] Time:  2:17:06  Date: 12/24/08
[    0.865479] NET: Registered protocol family 16
[    0.868386] EISA bus registered
[    0.868419] ACPI: bus type pci registered
[    0.868683] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 0
[    0.868690] PCI: MCFG area at e0000000 reserved in E820
[    0.868695] PCI: Using MMCONFIG for extended config space
[    0.868701] PCI: Using configuration type 1 for base access
[    0.872705] ACPI: EC: Look up EC in DSDT
[    0.881542] ACPI: Interpreter enabled
[    0.881552] ACPI: (supports S0 S3 S4 S5)
[    0.881584] ACPI: Using PIC for interrupt routing
[    0.882200] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.910226] ACPI: EC: GPE = 0x13, I/O: command/status = 0x66, data = 0x62
[    0.910233] ACPI: EC: driver started in interrupt mode
[    0.910829] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.910919] pnp: PnP ACPI init
[    0.910938] ACPI: bus type pnp registered
[    0.917427] pnp: PnP ACPI: found 10 devices
[    0.917433] ACPI: ACPI bus type pnp unregistered
[    0.917444] PnPBIOS: Disabled by ACPI PNP
[    0.918296] PCI: Probing PCI hardware
[    0.918304] PCI: Probing PCI hardware (bus 00)
[    0.918463] PCI: 0000:00:00.0 reg 10 32bit mmio: [a0000000, afffffff]
[    0.918716] PCI: 0000:00:02.5 reg 10 io port: [1f0, 1f7]
[    0.918730] PCI: 0000:00:02.5 reg 14 io port: [3f4, 3f7]
[    0.918744] PCI: 0000:00:02.5 reg 18 io port: [170, 177]
[    0.918757] PCI: 0000:00:02.5 reg 1c io port: [374, 377]
[    0.918771] PCI: 0000:00:02.5 reg 20 io port: [1080, 108f]
[    0.918817] pci 0000:00:02.5: PME# supported from D3cold
[    0.918826] pci 0000:00:02.5: PME# disabled
[    0.918862] PCI: 0000:00:03.0 reg 10 32bit mmio: [b0104000, b0104fff]
[    0.918950] PCI: 0000:00:03.1 reg 10 32bit mmio: [b0105000, b0105fff]
[    0.919057] PCI: 0000:00:03.3 reg 10 32bit mmio: [b0106000, b0106fff]
[    0.919131] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.919140] pci 0000:00:03.3: PME# disabled
[    0.919197] PCI: 0000:00:04.0 reg 10 32bit mmio: [b0307000, b030707f]
[    0.919211] PCI: 0000:00:04.0 reg 14 io port: [1000, 107f]
[    0.919276] pci 0000:00:04.0: supports D1
[    0.919281] pci 0000:00:04.0: supports D2
[    0.919286] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.919295] pci 0000:00:04.0: PME# disabled
[    0.919348] PCI: 0000:00:05.0 reg 10 io port: [10c8, 10cf]
[    0.919362] PCI: 0000:00:05.0 reg 14 io port: [10bc, 10bf]
[    0.919375] PCI: 0000:00:05.0 reg 18 io port: [10c0, 10c7]
[    0.919389] PCI: 0000:00:05.0 reg 1c io port: [10b8, 10bb]
[    0.919402] PCI: 0000:00:05.0 reg 20 io port: [10a0, 10af]
[    0.919447] pci 0000:00:05.0: PME# supported from D3cold
[    0.919455] pci 0000:00:05.0: PME# disabled
[    0.919524] PCI: 0000:00:0f.0 reg 10 32bit mmio: [b0100000, b0103fff]
[    0.919599] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.919608] pci 0000:00:0f.0: PME# disabled
[    0.919704] PCI: 0000:01:00.0 reg 10 32bit mmio: [c0000000, cfffffff]
[    0.919717] PCI: 0000:01:00.0 reg 14 32bit mmio: [b0000000, b001ffff]
[    0.919729] PCI: 0000:01:00.0 reg 18 io port: [9000, 907f]
[    0.919782] pci 0000:01:00.0: supports D1
[    0.919787] pci 0000:01:00.0: supports D2
[    0.919851] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.919860] PCI: bridge 0000:00:01.0 32bit mmio: [b0000000, b00fffff]
[    0.919869] PCI: bridge 0000:00:01.0 32bit mmio pref: [c0000000, cfffffff]
[    0.921589] NET: Registered protocol family 8
[    0.921589] NET: Registered protocol family 20
[    0.921589] NetLabel: Initializing
[    0.921589] NetLabel:  domain hash size = 128
[    0.921589] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.921589] NetLabel:  unlabeled traffic allowed by default
[    0.921589] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.921589]    actual entries 65620
[    0.921589] AppArmor: AppArmor Filesystem Enabled
[    0.921589] system 00:04: ioport range 0x8000-0x80be has been reserved
[    0.921589] system 00:04: ioport range 0x8100-0x812f has been reserved
[    0.921589] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.921589] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.921589] system 00:04: ioport range 0x200-0x20f has been reserved
[    0.921589] system 00:04: ioport range 0x290-0x297 has been reserved
[    0.921589] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.921589] system 00:04: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.921589] system 00:04: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.921589] system 00:04: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.921589] system 00:04: iomem range 0xffc00000-0xffc00fff has been reserved
[    0.921589] system 00:04: iomem range 0xffe00000-0xffe00fff has been reserved
[    0.921589] system 00:04: iomem range 0xffe80000-0xffefffff has been reserved
[    0.958790] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.958798] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.958809] pci 0000:00:01.0:   MEM window: 0xb0000000-0xb00fffff
[    0.958819] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.958845] pci 0000:00:01.0: setting latency timer to 64
[    0.958854] bus: 00 index 0 io port: [0, ffff]
[    0.958859] bus: 00 index 1 mmio: [0, ffffffff]
[    0.958865] bus: 01 index 0 io port: [9000, 9fff]
[    0.958870] bus: 01 index 1 mmio: [b0000000, b00fffff]
[    0.958875] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    0.958880] bus: 01 index 3 mmio: [0, 0]
[    0.958899] NET: Registered protocol family 2
[    0.959180] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.959729] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.960658] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.961262] TCP: Hash tables configured (established 131072 bind 65536)
[    0.961271] TCP reno registered
[    0.961564] NET: Registered protocol family 1
[    0.961839] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.782152]  it is
[    2.668134] Freeing initrd memory: 8011k freed
[    2.669740] audit: initializing netlink socket (disabled)
[    2.669774] type=2000 audit(1230085026.668:1): initialized
[    2.684457] highmem bounce pool size: 64 pages
[    2.684472] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.690317] VFS: Disk quotas dquot_6.5.1
[    2.690539] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.690773] msgmni has been set to 1746
[    2.691075] io scheduler noop registered
[    2.691082] io scheduler anticipatory registered
[    2.691088] io scheduler deadline registered
[    2.691116] io scheduler cfq registered (default)
[    2.691212] pci 0000:01:00.0: Boot video device
[    2.691838] isapnp: Scanning for PnP cards...
[    3.046059] isapnp: No Plug & Play device found
[    3.129758] hpet_acpi_add: no address or irqs in _CRS
[    3.129903] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.135586] brd: module loaded
[    3.135758] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.136106] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.140982] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.144059] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.144080] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.144086] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.144092] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.144098] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.145176] mice: PS/2 mouse device common for all mice
[    3.145510] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    3.145538] rtc0: alarms up to one year, y3k
[    3.145836] EISA: Probing bus 0 at eisa.0
[    3.145850] Cannot allocate resource for EISA slot 1
[    3.145890] Cannot allocate resource for EISA slot 8
[    3.145895] EISA: Detected 0 cards.
[    3.145902] cpuidle: using governor ladder
[    3.145909] cpuidle: using governor menu
[    3.147163] TCP cubic registered
[    3.147223] Using IPI No-Shortcut mode
[    3.147677] registered taskstats version 1
[    3.147863]   Magic number: 4:768:258
[    3.147914] tty ttyx0: hash matches
[    3.148141] rtc_cmos 00:02: setting system clock to 2008-12-24 02:17:08 UTC (1230085028)
[    3.148149] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.148154] EDD information not available.
[    3.148599] Freeing unused kernel memory: 424k freed
[    3.148686] Write protecting the kernel text: 2576k
[    3.148745] Write protecting the kernel read-only data: 936k
[    3.182381] input: AT Raw Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.508636] fuse init (API version 7.9)
[    3.782420] ACPI: SSDT 77D94062, 0289 (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[    3.784666] ACPI: SSDT 77D93AC5, 0518 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[    3.789959] Monitor-Mwait will be used to enter C-1 state
[    3.789967] Monitor-Mwait will be used to enter C-2 state
[    3.789974] Monitor-Mwait will be used to enter C-3 state
[    3.814378] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.819494] processor ACPI0007:00: registered as cooling_device0
[    3.819506] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.845975] thermal LNXTHERM:01: registered as thermal_zone0
[    3.847566] ACPI: Thermal Zone [TZ01] (55 C)
[    5.370262] No dock devices found.
[    5.595088] SCSI subsystem initialized
[    5.708235] usbcore: registered new interface driver usbfs
[    5.708289] usbcore: registered new interface driver hub
[    5.715215] usbcore: registered new device driver usb
[    5.738892] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    5.738988] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    5.739056] ehci_hcd 0000:00:03.3: irq 7, io mem 0xb0106000
[    5.747100] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.748098] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.748395] usb usb1: configuration #1 chosen from 1 choice
[    5.748462] hub 1-0:1.0: USB hub found
[    5.748480] hub 1-0:1.0: 8 ports detected
[    5.749920] libata version 3.00 loaded.
[    5.956671] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    5.956734] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    5.956763] ohci_hcd 0000:00:03.0: irq 11, io mem 0xb0104000
[    6.012743] usb usb2: configuration #1 chosen from 1 choice
[    6.012821] hub 2-0:1.0: USB hub found
[    6.012842] hub 2-0:1.0: 4 ports detected
[    6.068072] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    6.116495] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    6.116564] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    6.116593] ohci_hcd 0000:00:03.1: irq 10, io mem 0xb0105000
[    6.174338] usb usb3: configuration #1 chosen from 1 choice
[    6.174408] hub 3-0:1.0: USB hub found
[    6.174426] hub 3-0:1.0: 4 ports detected
[    6.286622] pata_sis 0000:00:02.5: version 0.5.2
[    6.291655] scsi0 : pata_sis
[    6.291870] scsi1 : pata_sis
[    6.291965] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    6.291973] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    6.456418] ata1.00: ATAPI: Optiarc DVD RW AD-7530B, NX06, max UDMA/33
[    6.472409] ata1.00: configured for UDMA/33
[    6.472510] ata2: port disabled. ignoring.
[    6.473967] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NX06 PQ: 0 ANSI: 5
[    6.484150] sata_sis 0000:00:05.0: version 1.0
[    6.484176] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    6.485526] scsi2 : sata_sis
[    6.485705] scsi3 : sata_sis
[    6.485795] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 5
[    6.485802] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 5
[    6.648608] ata3.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC7KP, max UDMA/100
[    6.648617] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.664664] ata3.00: configured for UDMA/100
[    6.759604] usb 1-6: configuration #1 chosen from 1 choice
[    6.831436] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[    6.998820] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    6.998906] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    7.046723] Driver 'sr' needs updating - please use bus_type methods
[    7.056789] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.056800] Uniform CD-ROM driver Revision: 3.20
[    7.057020] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    7.126472] usbcore: registered new interface driver libusual
[    7.145454] Driver 'sd' needs updating - please use bus_type methods
[    7.145698] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    7.145742] sd 2:0:0:0: [sda] Write Protect is off
[    7.145748] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.145819] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.145978] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    7.146018] sd 2:0:0:0: [sda] Write Protect is off
[    7.146025] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.146096] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.146107]  sda:<6>Initializing USB Mass Storage driver...
[    7.160467] scsi4 : SCSI emulation for USB Mass Storage devices
[    7.160730] usbcore: registered new interface driver usb-storage
[    7.160738] USB Mass Storage support registered.
[    7.161027] usb-storage: device found at 2
[    7.161032] usb-storage: waiting for device to settle before scanning
[    7.171995]  sda1 sda2 < sda5 >
[    7.191488] sd 2:0:0:0: [sda] Attached SCSI disk
[    7.264199] Marking TSC unstable due to TSC halts in idle
[    7.485533] PM: Starting manual resume from disk
[    7.485543] PM: Resume from partition 8:5
[    7.485547] PM: Checking hibernation image.
[    7.485767] PM: Resume from disk failed.
[    7.534937] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.534946] EXT3-fs: write access will be enabled during recovery.
[    8.301879] kjournald starting.  Commit interval 5 seconds
[    8.301914] EXT3-fs: sda1: orphan cleanup on readonly fs
[    8.301927] ext3_orphan_cleanup: deleting unreferenced inode 5267587
[    8.302001] EXT3-fs: sda1: 1 orphan inode deleted
[    8.302006] EXT3-fs: recovery complete.
[    8.314983] EXT3-fs: mounted filesystem with ordered data mode.
[   12.160460] usb-storage: device scan complete
[   12.167022] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   12.169083] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   12.169297] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   16.246103] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.389381] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.389689] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   16.389696] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   16.389701] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   16.929528] udevd version 124 started
[   18.240657] Linux agpgart interface v0.103
[   18.353007] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.430153] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.498847] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   18.683841] agpgart-sis 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[   19.160479] sis190 Gigabit Ethernet driver 1.2 loaded.
[   19.160523] sis190 0000:00:04.0: setting latency timer to 64
[   19.160542] 0000:00:04.0: Read MAC address from EEPROM
[   19.248074] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[   19.634239] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   19.648115] ACPI: Power Button (FF) [PWRF]
[   19.648503] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   19.664113] ACPI: Power Button (CM) [PWRB]
[   19.664382] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   19.680125] ACPI: Sleep Button (CM) [SLPB]
[   19.680462] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   19.680936] ACPI: Lid Switch [LID0]
[   19.710604] ACPI: AC Adapter [AC0] (on-line)
[   19.744086] 0000:00:04.0: Using transceiver at address 1 as default.
[   19.777017] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f89ce000 (IRQ: 3), 00:03:0d:76:24:a3
[   19.777025] eth0: GMII mode.
[   19.777049] eth0: Enabling Auto-negotiation.
[   19.923574] ACPI: Battery Slot [BAT0] (battery present)
[   20.930643] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   21.971740] acpi device:0f: registered as cooling_device1
[   21.972210] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/device:0d/input/input7
[   21.984085] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   23.589897] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   23.622087] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   23.717982] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   23.758049] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   27.956729] lp: driver loaded but no devices found
[   28.025660] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   28.025669] apm: overridden by ACPI.
[   28.477942] Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k
[   71.390439] atkbd.c: Unknown key pressed (raw set 2, code 0xa2 on isa0060/serio0).
[   71.390449] atkbd.c: Use 'setkeycodes e022 <keycode>' to make it known.
[   71.405407] atkbd.c: Unknown key released (raw set 2, code 0xa2 on isa0060/serio0).
[   71.405414] atkbd.c: Use 'setkeycodes e022 <keycode>' to make it known.
[   71.430364] atkbd.c: Unknown key pressed (raw set 2, code 0x85 on isa0060/serio0).
[   71.430371] atkbd.c: Use 'setkeycodes e005 <keycode>' to make it known.
[   71.445340] atkbd.c: Unknown key released (raw set 2, code 0x85 on isa0060/serio0).
[   71.445346] atkbd.c: Use 'setkeycodes e005 <keycode>' to make it known.
[   71.530220] atkbd.c: Unknown key pressed (raw set 2, code 0x85 on isa0060/serio0).
[   71.530228] atkbd.c: Use 'setkeycodes e005 <keycode>' to make it known.
[   71.545180] atkbd.c: Unknown key released (raw set 2, code 0x85 on isa0060/serio0).
[   71.545186] atkbd.c: Use 'setkeycodes e005 <keycode>' to make it known.
[   71.590110] atkbd.c: Unknown key pressed (raw set 2, code 0xa2 on isa0060/serio0).
[   71.590117] atkbd.c: Use 'setkeycodes e022 <keycode>' to make it known.
[   71.605016] atkbd.c: Unknown key released (raw set 2, code 0xa2 on isa0060/serio0).
[   71.605022] atkbd.c: Use 'setkeycodes e022 <keycode>' to make it known.
[  131.293966] atkbd.c: Unknown key pressed (raw set 2, code 0xa2 on isa0060/serio0).
[  131.293975] atkbd.c: Use 'setkeycodes e022 <keycode>' to make it known.
[  131.308869] atkbd.c: Unknown key released (raw set 2, code 0xa2 on isa0060/serio0).
[  131.308877] atkbd.c: Use 'setkeycodes e022 <keycode>' to make it known.
[  131.333827] atkbd.c: Unknown key pressed (raw set 2, code 0x85 on isa0060/serio0).
[  131.333834] atkbd.c: Use 'setkeycodes e005 <keycode>' to make it known.
[  131.348805] atkbd.c: Unknown key released (raw set 2, code 0x85 on isa0060/serio0).
[  131.348812] atkbd.c: Use 'setkeycodes e005 <keycode>' to make it known.
[  131.433736] atkbd.c: Unknown key pressed (raw set 2, code 0x85 on isa0060/serio0).
[  131.433745] atkbd.c: Use 'setkeycodes e005 <keycode>' to make it known.
[  131.448711] atkbd.c: Unknown key released (raw set 2, code 0x85 on isa0060/serio0).
[  131.448718] atkbd.c: Use 'setkeycodes e005 <keycode>' to make it known.
[  131.493571] atkbd.c: Unknown key pressed (raw set 2, code 0xa2 on isa0060/serio0).
[  131.493580] atkbd.c: Use 'setkeycodes e022 <keycode>' to make it known.
[  131.508546] atkbd.c: Unknown key released (raw set 2, code 0xa2 on isa0060/serio0).
[  131.508553] atkbd.c: Use 'setkeycodes e022 <keycode>' to make it known.
[  207.534018] EXT3 FS on sda1, internal journal
[  208.717311] type=1505 audit(1230085234.042:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=5063
[  209.136406] type=1505 audit(1230085234.462:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5068
[  209.136811] type=1505 audit(1230085234.462:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=5068
[  210.483077] ACPI: WMI: Mapper loaded
[  211.600927] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  211.657368] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  211.657378] apm: disabled on user request.
[  211.778913] ppdev: user-space parallel port driver
[  213.231989] Bluetooth: Core ver 2.13
[  213.236848] NET: Registered protocol family 31
[  213.236875] Bluetooth: HCI device and connection manager initialized
[  213.236883] Bluetooth: HCI socket layer initialized
[  213.289621] Bluetooth: L2CAP ver 2.11
[  213.289636] Bluetooth: L2CAP socket layer initialized
[  213.320113] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  213.320123] Bluetooth: BNEP filters: protocol multicast
[  213.366994] Bridge firewalling registered
[  213.376511] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  213.394200] Bluetooth: RFCOMM socket layer initialized
[  213.398402] Bluetooth: RFCOMM TTY layer initialized
[  213.398410] Bluetooth: RFCOMM ver 1.10
[  213.400455] Bluetooth: SCO (Voice Link) ver 0.6
[  213.400464] Bluetooth: SCO socket layer initialized
[  227.564121] eth0: mii ext = 0000.
[  227.580050] eth0: mii lpa = 45e1 adv = 01e1.
[  227.580063] eth0: link on 100 Mbps Full Duplex mode.
[  227.709421] NET: Registered protocol family 17
[  230.957489] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  239.645499] CPU0 attaching NULL sched-domain.
[  239.656170] CPU0 attaching sched-domain:
[  239.656185]  domain 0: span 0 level CPU
[  239.656193]   groups: 0
[  262.008481] NET: Registered protocol family 10
[  262.012822] lo: Disabled Privacy Extensions

```

---

### Post by nerktord on 2008-12-23
bump

---

### Post by Coder543 on 2008-12-23
I'm no kernel developer but, from the theory I've read (The Minix Book, like 2nd edition) I don't think that this is a good thing. This looks like the process switching stops. (aka. no cpu time is being given to any apps). No idea what would cause that though.
[  239.645499] CPU0 attaching NULL sched-domain.

---

### Post by albinootje on 2008-12-23
I'm just a below average Linux-sysadmin, and very far from a kernel-hacker, but what I find interesting in your posted logfile bits, is this :

> **nerktord said:**
> 
[    0.864135] BIOS bug, local APIC #0 not detected!...
[    0.864194] ... forcing use of dummy APIC emulation.(tell your hw vendor)

[    3.129758] hpet_acpi_add: no address or irqs in _CRS
[    3.129903] Serial: 8250/16550 driver4 ports, IRQ sharing enabled

[    7.264199] Marking TSC unstable due to TSC halts in idle

[   23.589897] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   23.622087] hda_codec: Unknown model for ALC662, trying auto-probe from
BIOS...
[  230.957489] hda-intel: IRQ timing workaround is activated for card #0.
Suggest a bigger bdl_pos_adj.


Can you boot with these kernel options :
```

noapic nolapic

```
And are you using screensaver + powermanagement ?

Could you also try booting with your soundcard disabled in the BIOS ?
Do you need your serial ports and parallel port ? 
If not, you can turn them of in the BIOS so they don't need an irq.

---

### Post by imtheguido on 2008-12-23
I was having this same problem when I first installed 8.10. When it freezes does your Caps Lock light on your keyboard flash? If so you are having a Kernal Panic. It is usually caused by a hardware incompatability of some sort. I had a really old wireless card in my tower. As soon as I took it out, the computer has not frozen since. I know that it has been having issues with various wireless cards from other issues I have read like this. Are you perhaps using a wireless card of some sort?

---

### Post by Coder543 on 2008-12-23
> **albinootje said:**
> I'm just a below average Linux-sysadmin, and very far from a kernel-hacker, but what I find interesting in your posted logfile bits, is this :



Can you boot with these kernel options :
```

noapic nolapic

```And are you using screensaver + powermanagement ?

Could you also try booting with your soundcard disabled in the BIOS ?
Do you need your serial ports and parallel port ? 
If not, you can turn them of in the BIOS so they don't need an irq.

Wow, I missed that. Albinootje is correct, boot with noapic nolapic and your problems *should* go away, if they disable IRQ. Anyways, as we see here...
[  230.957489] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Right before the system process scheduling is nullified, an IRQ timing 'workaround' is used
this 'workaround' must be the NULL schedule.

---

### Post by nerktord on 2008-12-24
> **albinootje said:**
> Can you boot with these kernel options :
```

noapic nolapic

```
And are you using screensaver + powermanagement ?

Could you also try booting with your soundcard disabled in the BIOS ?
Do you need your serial ports and parallel port ? 
If not, you can turn them of in the BIOS so they don't need an irq.


Yes, I need those two options(noapic, nolapic) to be set before I boot, otherwise the ubuntu loading bar fails to load and lags indefinitely. I first noticed this problem when I first decided to install ubuntu on this laptop, but ubuntu's boot menu options allows you to set those options to proceed with the install, but from there on, I had to make the changes to the boot menu.lst, rather than adding the options to the boot sequence every time.

I'm not really sure why this is though? I think I remembered the issue being about power saving features or the graphics card, not too sure.

Do you think this could have something to do with the random freezes? To be more specific, the freezes occur when I'm using the computer normally, not during boot time or shutdown, but between those.

Also, this laptop came with window vista pre-installed, it worked for a couple of weeks, but then I kept continuously getting the blue screen of death and automatic restarts every 30 min - 1 hour. This was the very reason why I chose to install ubuntu :D

So could it possibly be some kind of hardware issue?, but the thing is, on 8.04 I'm sure this never happened, it would hardly ever crash, the only thing that crashed was firefox now and again, which was probably due to an inconsistency within the flash plugin. 

I really want to keep on using ubuntu and not have to deal with this type of problem.

Ill also try some of the other options you recommended. But until then I'm still clueless to what to do.

---

### Post by nerktord on 2008-12-24
> **imtheguido said:**
> I was having this same problem when I first installed 8.10. When it freezes does your Caps Lock light on your keyboard flash? If so you are having a Kernal Panic. It is usually caused by a hardware incompatability of some sort. I had a really old wireless card in my tower. As soon as I took it out, the computer has not frozen since. I know that it has been having issues with various wireless cards from other issues I have read like this. Are you perhaps using a wireless card of some sort?

I'm not too sure if it is a kernel panic because this is a laptop keyboard and lacks a cap-lock light. However, when it does freeze up, I can hear the processor speed up really fast.

This laptop does have a built-in wireless card, but it's not really supported by ubuntu, so I really haven't found much use for it. But it does exist though.

---

### Post by Yoeri on 2008-12-24
I had frequent crashes on a Desktop, there it was an "unsupported" video card. The card worked but after a while, the system freezed when compositing was on.

Similar crashes on a laptop. On the laptop, it was the wireless adapter. After installing the windows drivers in NDiswrapper, my problems were solved.

Maybe look into that direction ... ndiswrapper/valid wireless drivers

Good luck!
Y

---

### Post by nerktord on 2008-12-24
Hmm it may be related to wireless drivers, I'll be sure to check it out further.

I recently did a disk check on boot up and I've only had one crash today, I normally have one every 30min. Still baffled to what it could be.

---

### Post by albinootje on 2008-12-24
> **nerktord said:**
> Hmm it may be related to wireless drivers, I'll be sure to check it out further.

I recently did a disk check on boot up and I've only had one crash today, I normally have one every 30min. Still baffled to what it could be.

Do you have any other partitions which didn't get a fsck recently ? 
You could search your logfiles for file-system or related errors.
Better find out sooner than later.

That reminds me, I had freezes with my IDE disk before, it would either freeze completely or freeze for a few seconds, I could hear the hard disk make the same sound as it would do when I would turn off the computer (Both in ArchLinux and Ubuntu Hardy).
First I thought there was a problem with the power-supply cables, but now I've switched from an IDE to a SATA disk (with Ubuntu Intrepid), and those problems are completely gone.

---

### Post by airencracken on 2009-01-15
I'm having a very similar problem on my tower.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 15 11:03:58 UTC 2009 (Ubuntu 2.6.27-11.24-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e5000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7ffc0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3782a000 - 37fef22a
[    0.000000] ACPI: RSDP 000FB870, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 7FFC0100, 0044 (r1 A M I  OEMXSDT   4000619 MSFT       97)
[    0.000000] ACPI: FACP 7FFC0290, 00F4 (r3 A M I  OEMFACP   4000619 MSFT       97)
[    0.000000] ACPI: DSDT 7FFC0440, 5683 (r1  A0368 A0368001        1 INTL  2002026)
[    0.000000] ACPI: FACS 7FFCE000, 0040
[    0.000000] ACPI: APIC 7FFC0390, 0070 (r1 A M I  OEMAPIC   4000619 MSFT       97)
[    0.000000] ACPI: MCFG 7FFC0400, 003C (r1 A M I  OEMMCFG   4000619 MSFT       97)
[    0.000000] ACPI: OEMB 7FFCE040, 005B (r1 A M I  AMI_OEM   4000619 MSFT       97)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003782a000 - 0037fef22a]          RAMDISK ==> [003782a000 - 0037fef22a]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007ffc0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffc0
[    0.000000] On node 0 totalpages: 524111
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292256 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e5000
[    0.000000] PM: Registered nosave memory: 00000000000e5000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519503
[    0.000000] Kernel command line: root=UUID=68d77398-d6a4-4f8e-b81b-81c5d1aad5b8 ro quiet splash vga=788 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2210.048 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2063364k/2096896k available (2576k kernel code, 32220k reserved, 1165k data, 424k init, 1179392k highmem)
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
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 4420.09 BogoMIPS (lpj=8840192)
[    0.004034] Security Framework initialized
[    0.004042] SELinux:  Disabled at boot.
[    0.004072] AppArmor: AppArmor initialized
[    0.004080] Mount-cache hash table entries: 512
[    0.004270] Initializing cgroup subsys ns
[    0.004274] Initializing cgroup subsys cpuacct
[    0.004277] Initializing cgroup subsys memory
[    0.004291] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004294] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.004296] CPU 0(2) -> Core 0
[    0.004311] Checking 'hlt' instruction... OK.
[    0.021560] ACPI: Core revision 20080609
[    0.023742] ACPI: Checking initramfs for custom DSDT
[    0.329809] ENABLING IO-APIC IRQs
[    0.330064] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.369767] CPU0: AMD Athlon(tm)64 X2 Dual Core Processor  4400+ stepping 02
[    0.372023] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4420.40 BogoMIPS (lpj=8840816)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.456266] CPU1: AMD Athlon(tm)64 X2 Dual Core Processor  4400+ stepping 02
[    0.456294] Brought up 2 CPUs
[    0.456297] Total of 2 processors activated (8840.50 BogoMIPS).
[    0.456351] CPU0 attaching sched-domain:
[    0.456354]  domain 0: span 0-1 level CPU
[    0.456356]   groups: 0 1
[    0.456362] CPU1 attaching sched-domain:
[    0.456364]  domain 0: span 0-1 level CPU
[    0.456366]   groups: 1 0
[    0.456428] net_namespace: 840 bytes
[    0.456428] Booting paravirtualized kernel on bare hardware
[    0.456428] Time: 16:15:33  Date: 01/15/09
[    0.456428] NET: Registered protocol family 16
[    0.456428] EISA bus registered
[    0.456428] ACPI: bus type pci registered
[    0.456428] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.456428] PCI: Not using MMCONFIG.
[    0.456907] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.456909] PCI: Using configuration type 1 for base access
[    0.456928] ACPI: EC: Look up EC in DSDT
[    0.468801] ACPI: Interpreter enabled
[    0.468805] ACPI: (supports S0 S1 S3 S4 S5)
[    0.468821] ACPI: Using IOAPIC for interrupt routing
[    0.468880] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.474841] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.474844] PCI: Using MMCONFIG for extended config space
[    0.484211] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.484251] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.484255] pci 0000:00:02.0: PME# disabled
[    0.484279] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.484282] pci 0000:00:03.0: PME# disabled
[    0.484306] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.484308] pci 0000:00:04.0: PME# disabled
[    0.484497] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.484547] PCI: 0000:00:0a.1 reg 20 io port: [600, 63f]
[    0.484553] PCI: 0000:00:0a.1 reg 24 io port: [700, 73f]
[    0.484575] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.484581] pci 0000:00:0a.1: PME# disabled
[    0.484612] PCI: 0000:00:0b.0 reg 10 32bit mmio: [febde000, febdefff]
[    0.484646] pci 0000:00:0b.0: supports D1
[    0.484648] pci 0000:00:0b.0: supports D2
[    0.484650] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.484654] pci 0000:00:0b.0: PME# disabled
[    0.484682] PCI: 0000:00:0b.1 reg 10 32bit mmio: [febdfc00, febdfcff]
[    0.484717] pci 0000:00:0b.1: supports D1
[    0.484719] pci 0000:00:0b.1: supports D2
[    0.484721] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.484725] pci 0000:00:0b.1: PME# disabled
[    0.484767] PCI: 0000:00:0d.0 reg 20 io port: [ffa0, ffaf]
[    0.484816] PCI: 0000:00:0e.0 reg 10 io port: [e800, e807]
[    0.484821] PCI: 0000:00:0e.0 reg 14 io port: [e480, e483]
[    0.484827] PCI: 0000:00:0e.0 reg 18 io port: [e400, e407]
[    0.484832] PCI: 0000:00:0e.0 reg 1c io port: [e080, e083]
[    0.484838] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]
[    0.484844] PCI: 0000:00:0e.0 reg 24 32bit mmio: [febff000, febfffff]
[    0.484892] PCI: 0000:00:0f.0 reg 10 io port: [dc00, dc07]
[    0.484898] PCI: 0000:00:0f.0 reg 14 io port: [d880, d883]
[    0.484904] PCI: 0000:00:0f.0 reg 18 io port: [d800, d807]
[    0.484909] PCI: 0000:00:0f.0 reg 1c io port: [d480, d483]
[    0.484915] PCI: 0000:00:0f.0 reg 20 io port: [d400, d40f]
[    0.484920] PCI: 0000:00:0f.0 reg 24 32bit mmio: [febfe000, febfefff]
[    0.485011] PCI: 0000:00:10.1 reg 10 32bit mmio: [febd8000, febdbfff]
[    0.485049] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.485054] pci 0000:00:10.1: PME# disabled
[    0.485086] PCI: 0000:00:14.0 reg 10 32bit mmio: [febd7000, febd7fff]
[    0.485092] PCI: 0000:00:14.0 reg 14 io port: [d080, d087]
[    0.485121] pci 0000:00:14.0: supports D1
[    0.485122] pci 0000:00:14.0: supports D2
[    0.485124] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.485128] pci 0000:00:14.0: PME# disabled
[    0.485298] PCI: 0000:03:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.485305] PCI: 0000:03:00.0 reg 14 64bit mmio: [c0000000, cfffffff]
[    0.485313] PCI: 0000:03:00.0 reg 1c 64bit mmio: [fc000000, fcffffff]
[    0.485317] PCI: 0000:03:00.0 reg 24 io port: [bc00, bc7f]
[    0.485322] PCI: 0000:03:00.0 reg 30 32bit mmio: [fe9e0000, fe9fffff]
[    0.485372] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
[    0.485375] PCI: bridge 0000:00:04.0 32bit mmio: [fa900000, fe9fffff]
[    0.485379] PCI: bridge 0000:00:04.0 64bit mmio pref: [bff00000, dfefffff]
[    0.485417] PCI: 0000:04:05.0 reg 10 32bit mmio: [feaff800, feafffff]
[    0.485424] PCI: 0000:04:05.0 reg 14 io port: [cc00, cc7f]
[    0.485463] pci 0000:04:05.0: supports D2
[    0.485465] pci 0000:04:05.0: PME# supported from D2 D3hot D3cold
[    0.485469] pci 0000:04:05.0: PME# disabled
[    0.485502] pci 0000:00:10.0: transparent bridge
[    0.485506] PCI: bridge 0000:00:10.0 io port: [c000, cfff]
[    0.485510] PCI: bridge 0000:00:10.0 32bit mmio: [fea00000, feafffff]
[    0.485522] bus 00 -> node 0
[    0.485528] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.486155] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE0._PRT]
[    0.486274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE1._PRT]
[    0.486392] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.486529] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.496490] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.500180] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.500434] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.500687] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *5
[    0.500940] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *11
[    0.501193] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.501446] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.501700] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.501953] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.502207] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *7
[    0.502460] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *7
[    0.502713] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *5
[    0.502966] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.503221] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.503475] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
[    0.503728] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *10
[    0.503981] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[    0.504240] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *10
[    0.504541] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.504598] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - FA, should be F2 [20080609]
[    0.504598] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.504598] pnp: PnP ACPI init
[    0.504598] ACPI: bus type pnp registered
[    0.509446] pnp: PnP ACPI: found 11 devices
[    0.509449] ACPI: ACPI bus type pnp unregistered
[    0.509452] PnPBIOS: Disabled by ACPI PNP
[    0.509466] PCI: Using ACPI for IRQ routing
[    0.516040] NET: Registered protocol family 8
[    0.516042] NET: Registered protocol family 20
[    0.516070] NetLabel: Initializing
[    0.516072] NetLabel:  domain hash size = 128
[    0.516074] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.516088] NetLabel:  unlabeled traffic allowed by default
[    0.516674] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.516676]    actual entries 65620
[    0.516838] AppArmor: AppArmor Filesystem Enabled
[    0.516868] ACPI: RTC can wake from S4
[    0.524053] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.524055] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.524058] system 00:06: ioport range 0x500-0x57f has been reserved
[    0.524061] system 00:06: ioport range 0x580-0x5ff has been reserved
[    0.524064] system 00:06: ioport range 0x800-0x87f could not be reserved
[    0.524067] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.524070] system 00:06: ioport range 0x900-0x97f has been reserved
[    0.524073] system 00:06: ioport range 0x980-0x9ff has been reserved
[    0.524076] system 00:06: ioport range 0x2000-0x207f has been reserved
[    0.524078] system 00:06: ioport range 0x2080-0x20ff has been reserved
[    0.524082] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.524085] system 00:06: iomem range 0xfeb80000-0xfebbffff has been reserved
[    0.524088] system 00:06: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.524093] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.524097] system 00:07: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.524102] system 00:08: ioport range 0x290-0x297 has been reserved
[    0.524107] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.524112] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.524115] system 00:0a: iomem range 0xc0000-0xcffff could not be reserved
[    0.524118] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[    0.524121] system 00:0a: iomem range 0x100000-0x7fffffff could not be reserved
[    0.524124] system 00:0a: iomem range 0xff780000-0xffffffff could not be reserved
[    0.559271] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.559273] pci 0000:00:02.0:   IO window: disabled
[    0.559276] pci 0000:00:02.0:   MEM window: disabled
[    0.559279] pci 0000:00:02.0:   PREFETCH window: disabled
[    0.559283] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    0.559285] pci 0000:00:03.0:   IO window: disabled
[    0.559287] pci 0000:00:03.0:   MEM window: disabled
[    0.559290] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.559294] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
[    0.559296] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    0.559300] pci 0000:00:04.0:   MEM window: 0xfa900000-0xfe9fffff
[    0.559303] pci 0000:00:04.0:   PREFETCH window: 0x000000bff00000-0x000000dfefffff
[    0.559307] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.559310] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.559315] pci 0000:00:10.0:   MEM window: 0xfea00000-0xfeafffff
[    0.559318] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.559330] pci 0000:00:02.0: setting latency timer to 64
[    0.559335] pci 0000:00:03.0: setting latency timer to 64
[    0.559340] pci 0000:00:04.0: setting latency timer to 64
[    0.559345] pci 0000:00:10.0: setting latency timer to 64
[    0.559349] bus: 00 index 0 io port: [0, ffff]
[    0.559351] bus: 00 index 1 mmio: [0, ffffffff]
[    0.559353] bus: 01 index 0 mmio: [0, 0]
[    0.559355] bus: 01 index 1 mmio: [0, 0]
[    0.559357] bus: 01 index 2 mmio: [0, 0]
[    0.559359] bus: 01 index 3 mmio: [0, 0]
[    0.559361] bus: 02 index 0 mmio: [0, 0]
[    0.559363] bus: 02 index 1 mmio: [0, 0]
[    0.559364] bus: 02 index 2 mmio: [0, 0]
[    0.559366] bus: 02 index 3 mmio: [0, 0]
[    0.559368] bus: 03 index 0 io port: [b000, bfff]
[    0.559370] bus: 03 index 1 mmio: [fa900000, fe9fffff]
[    0.559372] bus: 03 index 2 mmio: [bff00000, dfefffff]
[    0.559374] bus: 03 index 3 mmio: [0, 0]
[    0.559376] bus: 04 index 0 io port: [c000, cfff]
[    0.559379] bus: 04 index 1 mmio: [fea00000, feafffff]
[    0.559381] bus: 04 index 2 mmio: [0, 0]
[    0.559383] bus: 04 index 3 io port: [0, ffff]
[    0.559385] bus: 04 index 4 mmio: [0, ffffffff]
[    0.559395] NET: Registered protocol family 2
[    0.560052] Switched to high resolution mode on CPU 0
[    0.560319] Switched to high resolution mode on CPU 1
[    0.572071] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.572398] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.573419] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.573999] TCP: Hash tables configured (established 131072 bind 65536)
[    0.574002] TCP reno registered
[    0.580120] NET: Registered protocol family 1
[    0.580254] checking if image is initramfs... it is
[    1.221192] Freeing initrd memory: 7956k freed
[    1.222325] audit: initializing netlink socket (disabled)
[    1.222349] type=2000 audit(1232036133.220:1): initialized
[    1.227910] highmem bounce pool size: 64 pages
[    1.227916] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.230028] VFS: Disk quotas dquot_6.5.1
[    1.230106] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.230199] msgmni has been set to 1743
[    1.230304] io scheduler noop registered
[    1.230307] io scheduler anticipatory registered
[    1.230309] io scheduler deadline registered
[    1.230319] io scheduler cfq registered (default)
[    1.230337] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.230376] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.230387] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.230397] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.230422] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.256089] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.256105] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.256118] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.256133] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.256158] pci 0000:03:00.0: Boot video device
[    1.256317] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.256345] pcieport-driver 0000:00:02.0: found MSI capability
[    1.256368] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.256422] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.256493] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.256518] pcieport-driver 0000:00:03.0: found MSI capability
[    1.256536] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.256588] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.256683] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.256707] pcieport-driver 0000:00:04.0: found MSI capability
[    1.256726] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.256779] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.257159] isapnp: Scanning for PnP cards...
[    1.610435] isapnp: No Plug & Play device found
[    1.647622] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.650236] brd: module loaded
[    1.650317] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.650530] PNP: No PS/2 controller found. Probing ports directly.
[    1.653153] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.653159] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.657164] mice: PS/2 mouse device common for all mice
[    1.657307] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.657339] rtc0: alarms up to one year, y3k
[    1.657503] EISA: Probing bus 0 at eisa.0
[    1.657513] Cannot allocate resource for EISA slot 2
[    1.657534] EISA: Detected 0 cards.
[    1.657537] cpuidle: using governor ladder
[    1.657540] cpuidle: using governor menu
[    1.658046] TCP cubic registered
[    1.658073] Using IPI No-Shortcut mode
[    1.658288] registered taskstats version 1
[    1.658431]   Magic number: 9:511:287
[    1.658450] tty ttyz1: hash matches
[    1.658585] tty tty20: hash matches
[    1.658665] rtc_cmos 00:02: setting system clock to 2009-01-15 16:15:34 UTC (1232036134)
[    1.658668] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.658670] EDD information not available.
[    1.659137] Freeing unused kernel memory: 424k freed
[    1.659199] Write protecting the kernel text: 2580k
[    1.659239] Write protecting the kernel read-only data: 940k
[    1.723698] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 1875k, total 262144k
[    1.723703] vesafb: mode is 800x600x16, linelength=1600, pages=2
[    1.723705] vesafb: protected mode interface info at c000:c2e0
[    1.723708] vesafb: pmi: set display start = c00cc316, set palette = c00cc380
[    1.723710] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    1.723724] vesafb: scrolling: redraw
[    1.723727] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    1.723998] Console: switching to colour frame buffer device 100x37
[    1.728937] fb0: VESA VGA frame buffer device
[    1.817114] fuse init (API version 7.9)
[    1.836169] processor ACPI0007:00: registered as cooling_device0
[    1.836482] processor ACPI0007:01: registered as cooling_device1
[    2.205238] No dock devices found.
[    2.239345] SCSI subsystem initialized
[    2.268514] usbcore: registered new interface driver usbfs
[    2.268541] usbcore: registered new interface driver hub
[    2.268573] usbcore: registered new device driver usb
[    2.270552] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.270986] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    2.270999] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    2.271006] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.273072] nv_probe: set workaround bit for reversed mac addr
[    2.314661] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.318781] libata version 3.00 loaded.
[    2.321100] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.792542] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:15:f2:02:ef:e5
[    2.792548] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[    2.793103] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22
[    2.793118] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUB0] -> GSI 22 (level, low) -> IRQ 22
[    2.793135] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.793139] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.793187] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.793219] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xfebde000
[    2.850192] usb usb1: configuration #1 chosen from 1 choice
[    2.850219] hub 1-0:1.0: USB hub found
[    2.850230] hub 1-0:1.0: 8 ports detected
[    3.056555] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    3.056566] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    3.056576] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    3.056579] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    3.056601] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    3.056631] ehci_hcd 0000:00:0b.1: debug port 1
[    3.056636] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    3.056652] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfebdfc00
[    3.068030] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.068116] usb usb2: configuration #1 chosen from 1 choice
[    3.068140] hub 2-0:1.0: USB hub found
[    3.068147] hub 2-0:1.0: 8 ports detected
[    3.277162] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    3.277530] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
[    3.277540] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[    3.277557] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    3.277566] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    3.277916] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 23
[    3.277919] pata_acpi 0000:00:0f.0: PCI INT A -> Link[LSA1] -> GSI 23 (level, low) -> IRQ 23
[    3.277936] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    3.277943] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    3.278350] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[    3.278359] ohci1394 0000:04:05.0: PCI INT A -> Link[LNKD] -> GSI 19 (level, low) -> IRQ 19
[    3.328126] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.331787] pata_amd 0000:00:0d.0: version 0.3.10
[    3.331836] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.336879] scsi0 : pata_amd
[    3.337098] scsi1 : pata_amd
[    3.378637] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.378640] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.596605] ata1.00: ATA-6: ST3200822A, 3.01, max UDMA/100
[    3.596609] ata1.00: 390721968 sectors, multi 16: LBA48 
[    3.596626] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc600c000) ACPI=0x3f01f (20:900:0x11)
[    3.612513] ata1.00: configured for UDMA/100
[    3.768190] ata2.01: NODEV after polling detection
[    3.780619] ata2.00: ATAPI: ATAPI   DVD DD 8X16X8X16, GSOB, max UDMA/33
[    3.780635] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc600c000) ACPI=0x701f (60:900:0x11)
[    3.792541] ata2.00: configured for UDMA/33
[    3.792667] scsi 0:0:0:0: Direct-Access     ATA      ST3200822A       3.01 PQ: 0 ANSI: 5
[    3.794813] scsi 1:0:0:0: CD-ROM            ATAPI    DVD DD 8X16X8X16 GSOB PQ: 0 ANSI: 5
[    3.798037] sata_nv 0000:00:0e.0: version 3.5
[    3.798053] sata_nv 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[    3.798056] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.798111] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.798303] scsi2 : sata_nv
[    3.798415] scsi3 : sata_nv
[    3.798602] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe000 irq 20
[    3.798605] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xe008 irq 20
[    3.920032] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    4.142425] usb 1-1: configuration #1 chosen from 1 choice
[    4.264074] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.299236] ata3.00: ATA-7: ST3160811AS, 3.AAE, max UDMA/133
[    4.299240] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.365874] ata3.00: configured for UDMA/133
[    4.448032] usb 1-2: new low speed USB device using ohci_hcd and address 3
[    4.597505] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000067ff7d]
[    4.669177] usb 1-2: configuration #1 chosen from 1 choice
[    4.832068] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.840385] ata4.00: ATA-7: ST3250310AS, 3.AAC, max UDMA/133
[    4.840388] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.856391] ata4.00: configured for UDMA/133
[    4.856528] scsi 2:0:0:0: Direct-Access     ATA      ST3160811AS      3.AA PQ: 0 ANSI: 5
[    4.856668] scsi 3:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[    4.856755] sata_nv 0000:00:0f.0: PCI INT A -> Link[LSA1] -> GSI 23 (level, low) -> IRQ 23
[    4.856759] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    4.856819] sata_nv 0000:00:0f.0: setting latency timer to 64
[    4.857725] scsi4 : sata_nv
[    4.857793] scsi5 : sata_nv
[    4.857973] ata5: SATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 23
[    4.857976] ata6: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 23
[    4.976030] usb 1-4: new low speed USB device using ohci_hcd and address 4
[    5.191442] usb 1-4: configuration #1 chosen from 1 choice
[    5.201989] usbcore: registered new interface driver hiddev
[    5.217704] input: Microsoft Microsoft Wireless Optical Mouse® 1.0A as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/input/input1
[    5.217994] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.0A] on usb-0000:00:0b.0-1
[    5.270144] hiddev96hidraw1: USB HID v1.10 Device [CPS UPS AE485] on usb-0000:00:0b.0-2
[    5.276319] input: Unicomp  Endura Keyboard  as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input2
[    5.276568] input,hidraw2: USB HID v1.10 Keyboard [Unicomp  Endura Keyboard ] on usb-0000:00:0b.0-4
[    5.276585] usbcore: registered new interface driver usbhid
[    5.276589] usbhid: v2.6:USB HID core driver
[    5.491403] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.491443] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.491479] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    5.491520] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[    5.517434] Driver 'sd' needs updating - please use bus_type methods
[    5.517580] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    5.517595] sd 0:0:0:0: [sda] Write Protect is off
[    5.517598] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.517621] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.517693] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    5.517705] sd 0:0:0:0: [sda] Write Protect is off
[    5.517707] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.517728] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.517731]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    5.535554]  sda5 sda6 sda7 sda8 >
[    5.584707] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.586299] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[    5.586316] sd 2:0:0:0: [sdb] Write Protect is off
[    5.586318] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.586340] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.586398] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[    5.586410] sd 2:0:0:0: [sdb] Write Protect is off
[    5.586413] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.586432] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.586436]  sdb:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    5.594327] Uniform CD-ROM driver Revision: 3.20
[    5.594385] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.613379]  sdb1 sdb2 < sdb5 >
[    5.637713] sd 2:0:0:0: [sdb] Attached SCSI disk
[    5.637772] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    5.637786] sd 3:0:0:0: [sdc] Write Protect is off
[    5.637788] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.637809] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.637852] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    5.637864] sd 3:0:0:0: [sdc] Write Protect is off
[    5.637866] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.637886] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.637889]  sdc: sdc1
[    5.656430] sd 3:0:0:0: [sdc] Attached SCSI disk
[    6.003135] PM: Starting manual resume from disk
[    6.003139] PM: Resume from partition 8:21
[    6.003141] PM: Checking hibernation image.
[    6.003349] PM: Resume from disk failed.
[    6.062725] kjournald starting.  Commit interval 5 seconds
[    6.062737] EXT3-fs: mounted filesystem with ordered data mode.
[   13.924605] udevd version 124 started
[   14.433179] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.498702] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.604338] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   14.625046] ACPI: Power Button (FF) [PWRF]
[   14.625187] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   14.657043] ACPI: Power Button (CM) [PWRB]
[   14.676071] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[   14.676089] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[   15.091633] Linux agpgart interface v0.103
[   15.736629] nvidia: module license 'NVIDIA' taints kernel.
[   16.008159] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 18
[   16.008175] nvidia 0000:03:00.0: PCI INT A -> Link[LNEA] -> GSI 18 (level, low) -> IRQ 18
[   16.008183] nvidia 0000:03:00.0: setting latency timer to 64
[   16.021903] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
[   16.035384] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   17.041988] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   17.041996] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   17.042021] HDA Intel 0000:00:10.1: setting latency timer to 64
[   17.882571] lp: driver loaded but no devices found
[   17.962586] w83627ehf: Found W83627EHG chip at 0x290
[   18.322986] Adding 6080560k swap on /dev/sdb5.  Priority:-1 extents:1 across:6080560k
[  453.502085] EXT3 FS on sdb1, internal journal
[  454.422764] type=1505 audit(1232065387.722:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=9961
[  454.611901] type=1505 audit(1232065387.910:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=9966
[  454.612196] type=1505 audit(1232065387.910:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=9966
[  454.713907] ip_tables: (C) 2000-2006 Netfilter Core Team
```

Here's my dmesg log.

Hmm, now that I'm taking a better look at it I think it may be my motherboard. Maybe not though. I guess that BIOS message isn't exactly fatal, but it does explain why suspend and resume have never worked.

[http://fixunix.com/kernel/557785-patch-03-49-x86-reserve-low-64k-ami-phoenix-bios-boxen.html](http://fixunix.com/kernel/557785-patch-03-49-x86-reserve-low-64k-ami-phoenix-bios-boxen.html)

[http://www.gossamer-threads.com/lists/linux/kernel/999474](http://www.gossamer-threads.com/lists/linux/kernel/999474)

---

### Post by albinootje on 2009-01-16
> **airencracken said:**
> I'm having a very similar problem on my tower.


Can you boot with the different boot options, and see whether that makes a difference ?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by airencracken on 2009-01-16
> **albinootje said:**
> Can you boot with the different boot options, and see whether that makes a difference ?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Will do.

I'll add "noapic nolapic" to my boot options next time I boot up Ubuntu. Currently I'm running *gasp* WinXP to isolate the OS and make sure it isn't any hardware causing the problem. My ram passed a memtest, my disks don't have any smart errors, and I keep my proc pretty cool though, so I doubt it is the hardware, but I'm just trying to eliminate that as a potential problem.

---

### Post by airencracken on 2009-01-22
> **airencracken said:**
> Will do.

I'll add "noapic nolapic" to my boot options next time I boot up Ubuntu. Currently I'm running *gasp* WinXP to isolate the OS and make sure it isn't any hardware causing the problem. My ram passed a memtest, my disks don't have any smart errors, and I keep my proc pretty cool though, so I doubt it is the hardware, but I'm just trying to eliminate that as a potential problem.

No problems with the hardware as far as I can test. The boot options seem to have cleared up the crashing problem as well. With that knowledge, can you give me an idea as to why that works and what the initial problem was in the first place?

---

### Post by albinootje on 2009-01-22
> **airencracken said:**
> No problems with the hardware as far as I can test. The boot options seem to have cleared up the crashing problem as well. With that knowledge, can you give me an idea as to why that works and what the initial problem was in the first place?

Good.
If you use "noapic nolapic" then you've disable apic, see here :
[http://wiki.osdev.org/APIC](http://wiki.osdev.org/APIC)

It could be a BIOS bug which was causing problems.

Hopefully more hardware vendors will start working more closely together with Linux kernel developers, and hopefully more hardware vendors will become more Linux friendly.

---

### Post by airencracken on 2009-01-23
> **albinootje said:**
> Good.
If you use "noapic nolapic" then you've disable apic, see here :
[http://wiki.osdev.org/APIC](http://wiki.osdev.org/APIC)

It could be a BIOS bug which was causing problems.

Hopefully more hardware vendors will start working more closely together with Linux kernel developers, and hopefully more hardware vendors will become more Linux friendly.

Hopefully so indeed. My system ran stable for about two days then had the same sort of crash as before, but it would have had around eight without those boot options. I'm hoping it was an isolated incident, but I've never had these crashes before. My system was rock solid before, so I don't know what could have changed. I may try flashing my BIOS.

Thanks again for all the help.

---

### Post by airencracken on 2009-01-28
> **airencracken said:**
> Hopefully so indeed. My system ran stable for about two days then had the same sort of crash as before, but it would have had around eight without those boot options. I'm hoping it was an isolated incident, but I've never had these crashes before. My system was rock solid before, so I don't know what could have changed. I may try flashing my BIOS.

Thanks again for all the help.

I've had to remove those options from my boot since they disable the second core on my dual core processor. I'm hoping for the best still since it was a fairly new problem in the first place and there have been significant updates between then and now.

---

### Post by airencracken on 2009-01-29
> **airencracken said:**
> I've had to remove those options from my boot since they disable the second core on my dual core processor. I'm hoping for the best still since it was a fairly new problem in the first place and there have been significant updates between then and now.

Unfortunately it just crashed again. I'm starting to wonder what else I can do. The acpi options really aren't viable since they make the OS see my dual core as a single core.

I'm wondering if there is a bug filed for this...

---

### Post by albinootje on 2009-01-29
> **airencracken said:**
> Unfortunately it just crashed again. I'm starting to wonder what else I can do. The acpi options really aren't viable since they make the OS see my dual core as a single core.

I'm wondering if there is a bug filed for this...

You can search for already filed bugs on [http://launchpad.net](http://launchpad.net)

See also :
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by hammondb3 on 2009-01-31
Im having the same problem when screen saver comes on completely
frozen, have to power it down manually. 
There are some pulse audio messsage in log, whatever that is.
This started after I upgraded from 8.04. to 8.10
anyone have a fix

---

### Post by hammondb3 on 2009-01-31
Im having the same freezing issue, once screen saver comes up
Hvae to power i tdown manually, there are pulse audi messges in log
This  happend after I upgradedfrom 8.04 tro 8.10
Anyone have a fix?

---

### Post by suicidepills on 2009-02-18
> **Coder543 said:**
> Wow, I missed that. Albinootje is correct, boot with noapic nolapic and your problems *should* go away, if they disable IRQ. Anyways, as we see here...
[  230.957489] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Right before the system process scheduling is nullified, an IRQ timing 'workaround' is used
this 'workaround' must be the NULL schedule.

I also find this line in my dmesg after rebooting from a crash:
```

[   42.124292] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

```

I seem to get crashes randomly but not very often.  I'd say about once or twice every 1-2 weeks.  Also, it seems to happen when I'm not using my computer.  For example, I'll be using my computer and walk away for a few minutes.  When I come back, it is completely unresponsive.  No Ctrl-alt-del, no ctrl-alt-backspace.

---

### Post by airencracken on 2009-02-18
> **albinootje said:**
> You can search for already filed bugs on [http://launchpad.net](http://launchpad.net)

See also :
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

Yep. Can't find one. Don't know what to do about this, I'm looking at maybe doing a fresh install. I was considering waiting until 9.04 for a fix, but I can't take this much longer.

Any other log files I could look through or anything? It's starting to drive me bonkers.

---

### Post by afeasfaerw23231233 on 2009-03-02
My system can only boot with and nolapic, otherwise it will hang at the loading bar. But it only recognizes 1 core instead of 2. My chipset is the extractly same as the OP, SiS 671MX, and my cpu is celeron dual-core t1600. Would it be the problem of SiS 671MX or the BIOS?

Here's the extract of my dmesg, this few lines are exactly the same as OP's 
```
[    0.000000] MPTABLE: OEM ID: SiS     
[    0.000000] MPTABLE: Product ID: 671MX       
[    0.000000] MPTABLE: APIC at: 0xFEE00000

[    0.022266] ACPI: Core revision 20080609
[    0.025121] ACPI: Checking initramfs for custom DSDT
[    0.427585] ACPI: setting ELCR to 0800 (from 0eb8)
[    0.428100] BIOS bug, local APIC #0 not detected!...
[    0.428142] ... forcing use of dummy APIC emulation.(tell your hw vendor)
[    0.428181] SMP disabled
[    0.428254] Brought up 1 CPUs
[    0.428257] Total of 1 processors activated (3333.25 BogoMIPS).
```

I searched the net and in fedora forum I found this thread
[http://fedoraforum.org/forum/showthread.php?t=63969](http://fedoraforum.org/forum/showthread.php?t=63969)
The second post said "kernel-patches" may fix the problem. 

Sorry if I am off topic, my system doesn't freeze. But this few line of my dmesg is exactly the same as OP's, and I need to boot with acpi-on and nolapic or the progress bar would freeze. And the annoying problem is my dual core cpu only have one core activated! Thanks for any suggestion! 

Here's my thread about my dual core problem: 
[http://ubuntuforums.org/showthread.php?t=1084383](http://ubuntuforums.org/showthread.php?t=1084383)
[http://ubuntuforums.org/showthread.php?t=1084326](http://ubuntuforums.org/showthread.php?t=1084326)

**Update:** I finally get both core working. I added these options to the kernel line in /boot/grub/menu.lst 
**noapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard** 
And two cores were brought up. 

Hope it may help anyone who has an SiS 671MX with a dual-core cpu. 

Here's the extract of my /boot/grub/menu.lst
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro quiet noapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard
initrd		/initrd.img-2.6.27-11-generic

```

---

### Post by Tur Third on 2009-03-04
I have recently started getting problems with system freezes. I think this might be to do with the graphics card and driver for nvidia in my case. (I have a GeForce 6200 card). Also am on 8.04.

I think my problems started when 'nvidia-glx-new' package was updated.

E.g. In your case freezing when you leave the pc for 10 mins - could be connected with the graphics card trying to start the screensaver.

What graphics card are you using? Are you happy that it works ok?

---

### Post by afeasfaerw23231233 on 2009-03-04
Hello, are you asking the OP or me?

---

### Post by Tur Third on 2009-03-04
That depends. do you think it might be a graphic driver problem? I think that is my problems, but I cannot be sure...

---

### Post by afeasfaerw23231233 on 2009-03-04
I don't know, I am just a newb. But I have three other computers running Ubuntu without big problem. The first has a didicated Nvidia 8400gs graphic card, the second has a integrated intel 845G, the third has an SiS 630 IGP. They both work well. 
But this time my notebook with a SiS 671MX has big problem, the resolution was only 800x600 in 8.10 64-bit, then I searched around the forum and knew that no SiS 671MX driver was available in 64-bit. So I reinstalled a 32-bit ubuntu and installed the driver, which was for 2D acceleration only, SiS didn't release 3D driver for us. Then it came the dual core problem, finally I found a solution from this forum and add the above parameter in the menu.lst. 
Now I encounter another big problem about WLAN. I still cannot find any solution from my thread. What a pain! 
Though I am not supporting Windoze I must admit that my notebook really didn't have a tiny problem druing installing and finding drivers for Windows XP pro 32-bit(I didn't install vista). Now it's almost a week and I am still struggling with problems in Ubuntu.

---

