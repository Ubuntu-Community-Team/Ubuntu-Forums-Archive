---
title: "kernel panic not syncing vfs unable to mount"
date: 2009-02-27
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-02-27
I got this in bootup

```
kernel panic-not syncing VFS Unable to mount root fs on unknown-block (0,0)
```

I boot in to the recovery mode and everything seems ok. I have read these threads but still have no idea.  [http://ubuntuforums.org/showthread.php?t=27709](http://ubuntuforums.org/showthread.php?t=27709) [http://ubuntuforums.org/showthread.php?t=550737&page=2](http://ubuntuforums.org/showthread.php?t=550737&page=2)

please help! thanks!

edit:here's my /boot/grub/menu.lst
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro acpi=on nolapic pnpbios=off quiet  
nitrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro acpi=on nolapic  single
initrd		/initrd.img-2.6.27-11-generic
```

edit: I boot into recovery mode and then choose "resume" and everything seems okay, here's the dmesg.```
 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037d90000 (usable)
[    0.000000]  BIOS-e820: 0000000037d90000 - 0000000037d9b000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037d9b000 - 0000000037d9c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037d9c000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Malformed early option 'acpi'
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x37d90 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 37d90000 @ 7000-d000
[    0.000000] RAMDISK: 375ad000 - 37d7fc43
[    0.000000] ACPI: RSDP 000F8580, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 37D91D00, 0094 (r1  HASEE PARADISE  6040000  LTP        0)
[    0.000000] ACPI: FACP 37D9AB86, 00F4 (r3 SiS    671MX     6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 37D95D1A, 4DF8 (r1 PTLTD       671  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 37D9BFC0, 0040
[    0.000000] ACPI: APIC 37D9AC7A, 005E (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: SLIC 37D9ACD8, 0176 (r1  HASEE PARADISE  6040000  LTP        0)
[    0.000000] ACPI: MCFG 37D9AE4E, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: SLIC 37D9AE8A, 0176 (r1  HASEE PARADISE  6040000  LTP        0)
[    0.000000] ACPI: SSDT 37D9363F, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D93599, 00A6 (r1  PmRef  Cpu7Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D934F3, 00A6 (r1  PmRef  Cpu6Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D9344D, 00A6 (r1  PmRef  Cpu5Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D933A7, 00A6 (r1  PmRef  Cpu4Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D93301, 00A6 (r1  PmRef  Cpu3Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D9325B, 00A6 (r1  PmRef  Cpu2Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D931B5, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D91D94, 1421 (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 893MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37d90000
[    0.000000]   low ram: 00000000 - 37d90000
[    0.000000]   bootmap 00009000 - 0000ffb4
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0037d90000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [00375ad000 - 0037d7fc43]          RAMDISK ==> [00375ad000 - 0037d7fc43]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00f85b0] 000f85b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037d90
[    0.000000]   HighMem  0x00037d90 -> 0x00037d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00037d90
[    0.000000] On node 0 totalpages: 228653
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    0.000000]   Normal zone: 222681 pages, LIFO batch:31
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
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:a8000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 226642
[    0.000000] Kernel command line: root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro acpi=on nolapic  single
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1666.631 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 892596k/915008k available (2576k kernel code, 21892k reserved, 1165k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf7d90000   ( 893 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3333.26 BogoMIPS (lpj=6666524)
[    0.004122] Security Framework initialized
[    0.004171] SELinux:  Disabled at boot.
[    0.004234] AppArmor: AppArmor initialized
[    0.004286] Mount-cache hash table entries: 512
[    0.004500] Initializing cgroup subsys ns
[    0.004549] Initializing cgroup subsys cpuacct
[    0.004595] Initializing cgroup subsys memory
[    0.004655] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004729] CPU: L2 cache: 1024K
[    0.004773] CPU: Physical Processor ID: 0
[    0.004818] CPU: Processor Core ID: 0
[    0.004864] using mwait in idle threads.
[    0.004915] Checking 'hlt' instruction... OK.
[    0.022305] ACPI: Core revision 20080609
[    0.025206] ACPI: Checking initramfs for custom DSDT
[    0.427801] ACPI: setting ELCR to 0800 (from 0eb8)
[    0.428101] BIOS bug, local APIC #0 not detected!...
[    0.428155] ... forcing use of dummy APIC emulation.(tell your hw vendor)
[    0.428204] SMP disabled
[    0.428317] Brought up 1 CPUs
[    0.428362] Total of 1 processors activated (3333.26 BogoMIPS).
[    0.428420] CPU0 attaching NULL sched-domain.
[    0.428690] net_namespace: 840 bytes
[    0.428757] Booting paravirtualized kernel on bare hardware
[    0.429029] Time: 13:00:23  Date: 02/28/09
[    0.432058] NET: Registered protocol family 16
[    0.432449] EISA bus registered
[    0.432512] ACPI: bus type pci registered
[    0.432688] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 0
[    0.432739] PCI: MCFG area at e0000000 reserved in E820
[    0.432786] PCI: Using MMCONFIG for extended config space
[    0.432833] PCI: Using configuration type 1 for base access
[    0.434835] ACPI: EC: Look up EC in DSDT
[    0.439507] ACPI: Interpreter enabled
[    0.439563] ACPI: (supports S0 S3 S4 S5)
[    0.439724] ACPI: Using PIC for interrupt routing
[    0.440196] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.449247] ACPI: EC: GPE = 0x13, I/O: command/status = 0x66, data = 0x62
[    0.449300] ACPI: EC: driver started in interrupt mode
[    0.449423] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.449560] PCI: 0000:00:00.0 reg 10 32bit mmio: [a0000000, afffffff]
[    0.449725] PCI: 0000:00:02.5 reg 10 io port: [1f0, 1f7]
[    0.449733] PCI: 0000:00:02.5 reg 14 io port: [3f4, 3f7]
[    0.449740] PCI: 0000:00:02.5 reg 18 io port: [170, 177]
[    0.449748] PCI: 0000:00:02.5 reg 1c io port: [374, 377]
[    0.449756] PCI: 0000:00:02.5 reg 20 io port: [1080, 108f]
[    0.449786] pci 0000:00:02.5: PME# supported from D3cold
[    0.449837] pci 0000:00:02.5: PME# disabled
[    0.449902] PCI: 0000:00:03.0 reg 10 32bit mmio: [b0104000, b0104fff]
[    0.449958] PCI: 0000:00:03.1 reg 10 32bit mmio: [b0105000, b0105fff]
[    0.450028] PCI: 0000:00:03.3 reg 10 32bit mmio: [b0106000, b0106fff]
[    0.450075] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.450126] pci 0000:00:03.3: PME# disabled
[    0.450205] PCI: 0000:00:04.0 reg 10 32bit mmio: [b0307000, b030707f]
[    0.450213] PCI: 0000:00:04.0 reg 14 io port: [1000, 107f]
[    0.450255] pci 0000:00:04.0: supports D1
[    0.450257] pci 0000:00:04.0: supports D2
[    0.450260] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450311] pci 0000:00:04.0: PME# disabled
[    0.450385] PCI: 0000:00:05.0 reg 10 io port: [10c8, 10cf]
[    0.450393] PCI: 0000:00:05.0 reg 14 io port: [10bc, 10bf]
[    0.450401] PCI: 0000:00:05.0 reg 18 io port: [10c0, 10c7]
[    0.450408] PCI: 0000:00:05.0 reg 1c io port: [10b8, 10bb]
[    0.450416] PCI: 0000:00:05.0 reg 20 io port: [10a0, 10af]
[    0.450444] pci 0000:00:05.0: PME# supported from D3cold
[    0.450493] pci 0000:00:05.0: PME# disabled
[    0.450582] PCI: 0000:00:0f.0 reg 10 32bit mmio: [b0100000, b0103fff]
[    0.450630] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.450681] pci 0000:00:0f.0: PME# disabled
[    0.450784] PCI: 0000:01:00.0 reg 10 32bit mmio: [c0000000, cfffffff]
[    0.450790] PCI: 0000:01:00.0 reg 14 32bit mmio: [b0000000, b001ffff]
[    0.450797] PCI: 0000:01:00.0 reg 18 io port: [9000, 907f]
[    0.450828] pci 0000:01:00.0: supports D1
[    0.450830] pci 0000:01:00.0: supports D2
[    0.450868] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.450873] PCI: bridge 0000:00:01.0 32bit mmio: [b0000000, b00fffff]
[    0.450878] PCI: bridge 0000:00:01.0 32bit mmio pref: [c0000000, cfffffff]
[    0.450888] bus 00 -> node 0
[    0.450896] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.459925] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.460385] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.460808] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 9 10 11)
[    0.461229] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[    0.461679] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.462101] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.462521] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.462942] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.463779] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.463869] pnp: PnP ACPI init
[    0.463924] ACPI: bus type pnp registered
[    0.466169] pnp 00:05: IRQ 13 override to level, low
[    0.466217] PCI: setting IRQ 13 as level-triggered
[    0.466427] pnp 00:07: IRQ 12 override to level, low
[    0.466783] PCI: setting IRQ 12 as level-triggered
[    0.467614] pnp: PnP ACPI: found 10 devices
[    0.467660] ACPI: ACPI bus type pnp unregistered
[    0.468033] PnPBIOS: Disabled by ACPI PNP
[    0.468492] PCI: Using ACPI for IRQ routing
[    0.468664] NET: Registered protocol family 8
[    0.468664] NET: Registered protocol family 20
[    0.468664] NetLabel: Initializing
[    0.468664] NetLabel:  domain hash size = 128
[    0.468664] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.468664] NetLabel:  unlabeled traffic allowed by default
[    0.468682] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.468732]    actual entries 65620
[    0.468904] AppArmor: AppArmor Filesystem Enabled
[    0.468974] system 00:04: ioport range 0x8000-0x80be has been reserved
[    0.468974] system 00:04: ioport range 0x8100-0x812f has been reserved
[    0.468974] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.468974] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.468974] system 00:04: ioport range 0x200-0x20f has been reserved
[    0.468974] system 00:04: ioport range 0x290-0x297 has been reserved
[    0.468974] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.468974] system 00:04: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.468974] system 00:04: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.468974] system 00:04: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.468974] system 00:04: iomem range 0xffc00000-0xffc00fff has been reserved
[    0.468974] system 00:04: iomem range 0xffe00000-0xffe00fff has been reserved
[    0.468974] system 00:04: iomem range 0xffe80000-0xffefffff has been reserved
[    0.505510] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.505560] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.505611] pci 0000:00:01.0:   MEM window: 0xb0000000-0xb00fffff
[    0.505662] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.505738] pci 0000:00:01.0: setting latency timer to 64
[    0.505743] bus: 00 index 0 io port: [0, ffff]
[    0.505788] bus: 00 index 1 mmio: [0, ffffffff]
[    0.505834] bus: 01 index 0 io port: [9000, 9fff]
[    0.505880] bus: 01 index 1 mmio: [b0000000, b00fffff]
[    0.505927] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    0.505973] bus: 01 index 3 mmio: [0, 0]
[    0.506027] NET: Registered protocol family 2
[    0.506224] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.506581] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.507426] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.508077] TCP: Hash tables configured (established 131072 bind 65536)
[    0.508131] TCP reno registered
[    0.508373] NET: Registered protocol family 1
[    0.508593] checking if image is initramfs... it is
[    1.008087] Switched to high resolution mode on CPU 0
[    1.328846] Freeing initrd memory: 8011k freed
[    1.329778] audit: initializing netlink socket (disabled)
[    1.329851] type=2000 audit(1235826023.328:1): initialized
[    1.336973] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.339687] VFS: Disk quotas dquot_6.5.1
[    1.339842] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.340043] msgmni has been set to 1759
[    1.340236] io scheduler noop registered
[    1.340282] io scheduler anticipatory registered
[    1.340328] io scheduler deadline registered
[    1.340386] io scheduler cfq registered (default)
[    1.340486] pci 0000:01:00.0: Boot video device
[    1.340874] isapnp: Scanning for PnP cards...
[    1.694530] isapnp: No Plug & Play device found
[    1.735435] hpet_acpi_add: no address or irqs in _CRS
[    1.735565] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.738250] brd: module loaded
[    1.738388] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.738627] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.743316] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.746801] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.746853] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.746901] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.746948] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.746996] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.747554] mice: PS/2 mouse device common for all mice
[    1.747773] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.747839] rtc0: alarms up to one year, y3k
[    1.748039] EISA: Probing bus 0 at eisa.0
[    1.748090] Cannot allocate resource for EISA slot 1
[    1.748159] Cannot allocate resource for EISA slot 8
[    1.748205] EISA: Detected 0 cards.
[    1.748250] cpuidle: using governor ladder
[    1.748296] cpuidle: using governor menu
[    1.748970] TCP cubic registered
[    1.749050] Using IPI No-Shortcut mode
[    1.749332] registered taskstats version 1
[    1.749473]   Magic number: 13:418:29
[    1.749531] tty ttydc: hash matches
[    1.749740] rtc_cmos 00:02: setting system clock to 2009-02-28 13:00:24 UTC (1235826024)
[    1.749803] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.749851] EDD information not available.
[    1.750162] Freeing unused kernel memory: 424k freed
[    1.750249] Write protecting the kernel text: 2580k
[    1.750324] Write protecting the kernel read-only data: 940k
[    1.784930] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.905578] fuse init (API version 7.9)
[    1.935569] ACPI: SSDT 37D9389E, 0518 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[    1.936475] Monitor-Mwait will be used to enter C-1 state
[    1.936480] Monitor-Mwait will be used to enter C-2 state
[    1.936483] Monitor-Mwait will be used to enter C-3 state
[    1.936752] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.936976] processor ACPI0007:00: registered as cooling_device0
[    1.937028] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.940379] Marking TSC unstable due to TSC halts in idle
[    1.941184] thermal LNXTHERM:01: registered as thermal_zone0
[    1.942986] ACPI: Thermal Zone [TZ01] (54 C)
[    2.488279] No dock devices found.
[    2.535982] SCSI subsystem initialized
[    2.560155] usbcore: registered new interface driver usbfs
[    2.560241] usbcore: registered new interface driver hub
[    2.572090] usbcore: registered new device driver usb
[    2.593390] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 7
[    2.593447] PCI: setting IRQ 7 as level-triggered
[    2.593452] ehci_hcd 0000:00:03.3: PCI INT C -> Link[LNKG] -> GSI 7 (level, low) -> IRQ 7
[    2.593527] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    2.593633] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    2.593732] ehci_hcd 0000:00:03.3: irq 7, io mem 0xb0106000
[    2.604036] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.604302] usb usb1: configuration #1 chosen from 1 choice
[    2.604381] hub 1-0:1.0: USB hub found
[    2.604434] hub 1-0:1.0: 8 ports detected
[    2.624200] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.632548] libata version 3.00 loaded.
[    2.812357] pata_sis 0000:00:02.5: version 0.5.2
[    2.812671] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    2.812725] PCI: setting IRQ 9 as level-triggered
[    2.812730] pata_sis 0000:00:02.5: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    2.813305] scsi0 : pata_sis
[    2.813465] scsi1 : pata_sis
[    2.813901] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    2.813952] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    2.980056] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    2.992297] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632H, CH01, max UDMA/33
[    3.024313] ata1.00: configured for UDMA/33
[    3.024421] ata2: port disabled. ignoring.
[    3.028127] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  CH01 PQ: 0 ANSI: 5
[    3.028625] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    3.028676] PCI: setting IRQ 11 as level-triggered
[    3.028681] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    3.028764] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.028849] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    3.028931] ohci_hcd 0000:00:03.0: irq 11, io mem 0xb0104000
[    3.084279] usb usb2: configuration #1 chosen from 1 choice
[    3.084367] hub 2-0:1.0: USB hub found
[    3.084421] hub 2-0:1.0: 4 ports detected
[    3.292609] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[    3.292665] PCI: setting IRQ 10 as level-triggered
[    3.292670] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    3.292752] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.292833] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    3.292911] ohci_hcd 0000:00:03.1: irq 10, io mem 0xb0105000
[    3.350221] usb usb3: configuration #1 chosen from 1 choice
[    3.350306] hub 3-0:1.0: USB hub found
[    3.350361] hub 3-0:1.0: 4 ports detected
[    3.457332] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    3.457389] PCI: setting IRQ 5 as level-triggered
[    3.457394] pata_acpi 0000:00:05.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    3.457504] pata_acpi 0000:00:05.0: PCI INT A disabled
[    3.462535] sata_sis 0000:00:05.0: version 1.0
[    3.462600] sata_sis 0000:00:05.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    3.462669] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    3.470104] scsi2 : sata_sis
[    3.470253] scsi3 : sata_sis
[    3.470918] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 5
[    3.470970] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 5
[    3.476243] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.504081] Driver 'sr' needs updating - please use bus_type methods
[    3.516268] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.516338] Uniform CD-ROM driver Revision: 3.20
[    3.516506] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.668364] usb 1-6: configuration #1 chosen from 1 choice
[    3.686067] ata3.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    3.686124] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.700852] ata3.00: configured for UDMA/133
[    3.852042] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    3.866961] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    3.867223] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    3.905533] Driver 'sd' needs updating - please use bus_type methods
[    3.905715] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    3.905783] sd 2:0:0:0: [sda] Write Protect is off
[    3.905829] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.905861] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.906001] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    3.906066] sd 2:0:0:0: [sda] Write Protect is off
[    3.906113] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.906143] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.906208]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    3.994389] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.064728] usb 2-3: configuration #1 chosen from 1 choice
[    4.072642] usbcore: registered new interface driver libusual
[    4.086742] Initializing USB Mass Storage driver...
[    4.095901] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.098428] usbcore: registered new interface driver usb-storage
[    4.098484] USB Mass Storage support registered.
[    4.098690] usbcore: registered new interface driver hiddev
[    4.098771] usb-storage: device found at 3
[    4.098774] usb-storage: waiting for device to settle before scanning
[    4.105457] input: USB Optical Mouse as /devices/pci0000:00/0000:00:03.0/usb2/2-3/2-3:1.0/input/input2
[    4.106295] input,hiddev96,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:03.0-3
[    4.106542] usbcore: registered new interface driver usbhid
[    4.106590] usbhid: v2.6:USB HID core driver
[    4.391202] PM: Starting manual resume from disk
[    4.391251] PM: Resume from partition 8:10
[    4.391253] PM: Checking hibernation image.
[    4.391528] PM: Resume from disk failed.
[    4.436249] kjournald starting.  Commit interval 5 seconds
[    4.436318] EXT3-fs: mounted filesystem with ordered data mode.
[    9.096354] usb-storage: device scan complete
[    9.108217] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    9.109539] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    9.109733] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   10.440465] udevd version 124 started
[   11.024788] Linux agpgart interface v0.103
[   11.064241] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   11.128320] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.162020] agpgart-sis 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[   11.176974] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.300226] sis190 Gigabit Ethernet driver 1.2 loaded.
[   11.300561] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[   11.300610] PCI: setting IRQ 3 as level-triggered
[   11.300615] sis190 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 3 (level, low) -> IRQ 3
[   11.300687] sis190 0000:00:04.0: setting latency timer to 64
[   11.300699] 0000:00:04.0: Read MAC address from EEPROM
[   11.388043] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[   11.820342] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.832047] ACPI: Power Button (FF) [PWRF]
[   11.832286] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   11.848045] ACPI: Power Button (CM) [PWRB]
[   11.848241] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   11.860052] ACPI: Sleep Button (CM) [SLPB]
[   11.860244] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input6
[   11.860849] ACPI: Lid Switch [LID0]
[   11.884886] ACPI: AC Adapter [AC0] (on-line)
[   11.900030] 0000:00:04.0: Using transceiver at address 1 as default.
[   11.936379] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f899a000 (IRQ: 3), 00:03:0d:af:c3:b5
[   11.936449] eth0: GMII mode.
[   11.936494] eth0: Enabling Auto-negotiation.
[   11.937408] ACPI: Battery Slot [BAT0] (battery present)
[   12.781449] acpi device:0f: registered as cooling_device1
[   12.781693] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/device:0d/input/input7
[   12.792044] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.877405] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
[   12.877461] PCI: setting IRQ 4 as level-triggered
[   12.877467] HDA Intel 0000:00:0f.0: PCI INT A -> Link[LNKC] -> GSI 4 (level, low) -> IRQ 4
[   12.877554] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   12.909938] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   13.808505] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   14.202141] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000
[   14.241870] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   16.428645] lp: driver loaded but no devices found
[   16.683289] Adding 979924k swap on /dev/sda10.  Priority:-1 extents:1 across:979924k
[   17.178391] EXT3 FS on sda8, internal journal
[   18.282498] kjournald starting.  Commit interval 5 seconds
[   18.282800] EXT3 FS on sda6, internal journal
[   18.282806] EXT3-fs: mounted filesystem with ordered data mode.
[   18.337872] kjournald starting.  Commit interval 5 seconds
[   18.338202] EXT3 FS on sda9, internal journal
[   18.338207] EXT3-fs: mounted filesystem with ordered data mode.
[   18.373700] kjournald starting.  Commit interval 5 seconds
[   18.373970] EXT3 FS on sda7, internal journal
[   18.373975] EXT3-fs: mounted filesystem with ordered data mode.
[   18.615850] type=1505 audit(1235797241.368:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3924
[   18.820801] type=1505 audit(1235797241.576:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3929
[   18.821104] type=1505 audit(1235797241.576:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3929
[   18.974331] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.011502] ACPI: WMI: Mapper loaded
[   26.897230] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   27.002252] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   27.002258] apm: overridden by ACPI.
[   27.183629] ppdev: user-space parallel port driver
[   28.641883] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   28.641892] vboxdrv: Successfully done.
[   28.641895] vboxdrv: Found 1 processor cores.
[   28.643550] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   28.643556] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   28.830128] NET: Registered protocol family 10
[   28.832190] lo: Disabled Privacy Extensions
[   34.060722] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.641485] [drm] Initialized drm 1.1.0 20060810
[   34.647089] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[   34.647100] pci 0000:01:00.0: setting latency timer to 64
[   34.648850] [drm] Initialized sis 1.3.0 20070626 on minor 0
[   34.650124] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
[   34.650151] agpgart-sis 0000:00:00.0: putting AGP V3 device into 4x mode
[   34.650201] pci 0000:01:00.0: putting AGP V3 device into 4x mode
[   38.578333] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   43.652098] usb 1-1: new high speed USB device using ehci_hcd and address 4
[   43.800383] usb 1-1: configuration #1 chosen from 1 choice
[   44.084075] eth0: auto-negotiating...
[   44.633704] phy0: Selected rate control algorithm 'pid'
[   44.900245] phy0: hwaddr 00:22:43:74:7b:05, RTL8187vB (default) V1 + rtl8225
[   44.900622] usbcore: registered new interface driver rtl8187
[   57.678418] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.700033] eth0: auto-negotiating...
[   57.810240] NET: Registered protocol family 17
[   61.840074] CPU0 attaching NULL sched-domain.
[   61.856121] CPU0 attaching NULL sched-domain.
[   67.724073] eth0: auto-negotiating...
[   71.374263] wlan0: authenticate with AP 00:19:5b:df:63:da
[   71.376021] wlan0: authenticated
[   71.376028] wlan0: associate with AP 00:19:5b:df:63:da
[   71.378714] wlan0: RX AssocResp from 00:19:5b:df:63:da (capab=0x431 status=0 aid=1)
[   71.378719] wlan0: associated
[   71.379640] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.656941] padlock: VIA PadLock not detected.
[   76.273286] atkbd.c: Unknown key pressed (translated set 2, code 0xad on isa0060/serio0).
[   76.273293] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[   76.283321] atkbd.c: Unknown key released (translated set 2, code 0xad on isa0060/serio0).
[   76.283327] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[   76.313244] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
[   76.313250] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[   76.323248] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
[   76.323253] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[   76.413047] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
[   76.413053] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[   76.423080] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
[   76.423085] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[   76.472983] atkbd.c: Unknown key pressed (translated set 2, code 0xad on isa0060/serio0).
[   76.472989] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[   76.482981] atkbd.c: Unknown key released (translated set 2, code 0xad on isa0060/serio0).
[   76.482986] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[   77.748081] eth0: auto-negotiating...
[   81.428075] wlan0: no IPv6 routers present
[   87.772070] eth0: auto-negotiating...
[   97.796202] eth0: auto-negotiating...
[  107.820072] eth0: auto-negotiating...
[  117.844034] eth0: auto-negotiating...
[  127.868080] eth0: auto-negotiating...
[  136.317731] atkbd.c: Unknown key pressed (translated set 2, code 0xad on isa0060/serio0).
[  136.317738] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[  136.327695] atkbd.c: Unknown key released (translated set 2, code 0xad on isa0060/serio0).
[  136.327700] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[  136.357678] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
[  136.357683] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[  136.367648] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
[  136.367653] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[  136.457570] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
[  136.457577] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[  136.467531] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
[  136.467536] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[  136.517498] atkbd.c: Unknown key pressed (translated set 2, code 0xad on isa0060/serio0).
[  136.517504] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[  136.527508] atkbd.c: Unknown key released (translated set 2, code 0xad on isa0060/serio0).
[  136.527515] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[  137.892078] eth0: auto-negotiating...
[  147.916075] eth0: auto-negotiating...
[  157.940034] eth0: auto-negotiating...
[  167.964204] eth0: auto-negotiating...
[  177.996051] eth0: auto-negotiating...
[  188.020079] eth0: auto-negotiating...
[  198.044072] eth0: auto-negotiating...
[  208.068037] eth0: auto-negotiating...
[  218.092080] eth0: auto-negotiating...
[  228.116072] eth0: auto-negotiating...
[  238.140073] eth0: auto-negotiating...
[  248.164068] eth0: auto-negotiating...
[  258.188159] eth0: auto-negotiating...
[  268.212070] eth0: auto-negotiating...
[  278.236073] eth0: auto-negotiating...
[  288.260068] eth0: auto-negotiating...
[  298.284072] eth0: auto-negotiating...


```

---

### Post by Crafty Kisses on 2009-02-28
It looks like you don't have the proper filesystem support. You obviously need to have your filesystem support (ext3 or LVM or whatever you use). Now it could also be me, but it also looks like you don't have /boot before initrid, so for example this is how my initrid line looks in my GRUB configuration file:
```
/boot/initrd.img-2.6.27-7-generic
```
So try putting /boot before initrid and see if that makes a difference, I guess it couldn't hurt. As stated above I'd also try checking to see if your kernel supports your filesystem, I'm not sure if you were compiling your own kernel and didn't add your filesystem support, but I'd check. I'm pretty sure you can check for FS support by running the following:
```
mkinitrd -c -k 2.6.27-7 (your filesystem type)
```
So for the above command, I'm using kernel 2.6.27-7, and I'm using ext3, so you would want to run the following:
```
mkinitrd -c -k 2.6.27-7 ext3
```
Try that and see if that works.

---

### Post by lyjx0228 on 2009-02-28
&#12288;[**&#29983;&#27542;&#22120;&#30129;&#30137;&#27835;&#30103;**](http://www.xbsos.com/szqpzzz.html)-&#29983;&#27542;&#22120;[**&#30129;&#30137;&#30151;&#29366;**](http://www.xbsos.com/dcpzbd.html) [&#20020;&#24202;&#34920;&#29616;] &#12288;[**&#20160;&#20040;&#26159;&#30129;&#30137;**](http://www.xbsos.com/smspz.html)&#12288;&#24863;&#26579;&#21518;&#24179;&#22343;&#32422;4&#65374;5&#26085;&#65292;&#22806;&#38452;&#24739;&#37096;&#20808;&#26377;&#28796;&#28909;&#24863;&#65292;&#26059;&#21363;&#21457;&#29983;&#25104;&#32676;&#19992;&#30137;&#65292;&#21487;&#20026;&#19968;&#31751;&#25110;&#22810;&#31751;&#65292;&#32487;&#20043;&#24418;&#25104;&#27700;&#30129;&#65288;&#22270;&#65289;&#12290;&#25968;&#26085;&#21518;&#28436;&#21464;&#20026;&#33043;&#30129;&#65292;&#30772;&#28291;&#21518;&#24418;&#25104;&#31964;&#28866;&#25110;&#27973;&#28291;&#30113;&#65292;&#33258;&#35273;&#30140;&#30171;&#65292;&#26368;&#21518;&#32467;&#30146;&#33258;&#24840;&#65292;&#30149;&#31243;&#32422;2&#65374;3&#21608;&#12290;&#30382;&#25439;&#22810;&#21457;&#20110;&#30007;&#24615;&#30340;&#21253;&#30382;&#12289;&#40863;&#22836;&#12289;&#20896;&#29366;&#27807;&#21644;&#38452;&#33550;&#31561;&#22788;&#65292;&#20598;&#35265;&#20110;&#23615;&#36947;&#21475;&#65307;[**&#30129;&#30137;&#30340;&#30151;&#29366;**](http://www.xbsos.com/smsszqpz.html)&#22899;&#24615;&#21017;&#22810;&#35265;&#20110;&#22823;&#23567;&#38452;&#21767;&#12289;&#38452;&#33922;&#12289;&#38452;&#38428;&#12289;&#23376;&#23467;&#39048;&#31561;&#22788;&#65292;&#20134;&#35265;&#20110;&#23615;&#36947;&#21475;&#12290;&#21407;&#21457;&#24615;&#29983;&#27542;&#22120;&#30129;&#30137;&#65292;&#24448;&#24448;&#20276;&#26377;&#20840;&#36523;&#19981;&#36866;&#65292;&#20302;&#28909;&#12289;&#22836;&#30171;&#31561;&#20840;&#36523;&#30151;&#29366;&#65292;&#23616;&#37096;&#28107;&#24050;&#32467;&#32959;&#22823;&#12290;&#26412;&#30149;&#24120;&#22797;&#21457;&#65292;[**&#22797;&#21457;&#24615;&#29983;&#27542;&#22120;&#30129;&#30137;**](http://www.xbsos.com/szqpzzz.html)&#36739;&#21407;&#21457;&#32773;&#36731;&#65292;&#25439;&#23475;&#23567;&#65292;&#24448;&#24448;&#26080;&#20840;&#36523;&#30151;&#29366;&#12290;&#30007;&#24615;&#21516;&#24615;&#24651;&#21487;&#20986;&#29616;&#32923;&#38376;&#30452;&#32928;HSV-2&#24863;&#26579;&#65292;&#20854;&#21457;&#30149;&#29575;&#20165;&#27425;&#20110;&#28107;&#29699;&#33740;&#25152;&#33268;&#30340;&#32923;&#38376;&#30452;&#32928;&#28814;&#65292;&#20020;&#24202;&#34920;&#29616;&#20026;&#32923;&#38376;&#30452;&#32928;&#30140;&#30171;&#12289;&#20415;&#31192;&#12289;&#20998;&#27852;&#29289;&#22686;&#21152;&#21644;&#37324;&#24613;&#21518;&#37325;&#65292;&#32923;&#21608;&#21487;&#26377;&#30129;&#30137;&#24615;&#28291;&#30113;&#65292;&#20057;&#29366;&#32467;&#32928;&#38236;&#26816;&#24120;&#35265;&#30452;&#32928;&#19979;&#27573;&#31896;&#33180;&#20805;&#34880;&#12289;&#20986;&#34880;&#21644;&#23567;&#28291;&#30113;&#12290;

---

### Post by Yashiro on 2009-02-28
If recovery mode works then if you just fix your series of typos then normal mode will work too.

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro acpi=on noapic pnpbios=off quiet splash 
initrd		/initrd.img-2.6.27-11-generic


title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro acpi=on noapic  single
initrd		/initrd.img-2.6.27-11-generic
```

If you've made a total hash of it all then here is that section of my menu.lst. It may help you reconstruct yours.
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ba636202-3275-45ed-b485-da35aa659c61  ro splash vga=794 usbhid.mousepoll=1
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ba636202-3275-45ed-b485-da35aa659c61  ro single vga=794
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (profile boot)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ba636202-3275-45ed-b485-da35aa659c61  ro splash vga=794 usbhid.mousepoll=1 profile
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		-----------------------
root

title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
chainloader	+1
```

---

### Post by afeasfaerw23231233 on 2009-02-28
Thanks every one for help!
It was a typo:

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro acpi=on nolapic pnpbios=off quiet  
[COLOR="Red"]**nitrd**[/COLOR]		/initrd.img-2.6.27-11-generic



Now it works again.  

What a fool I am. Thanks!

---

