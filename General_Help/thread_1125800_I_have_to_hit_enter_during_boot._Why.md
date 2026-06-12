---
title: "I have to hit enter during boot. Why?"
date: 2009-04-14
forum: General Help
---

### Post by dphirschler on 2009-04-14
My Ubuntu 8.10 machine stalls during boot.  It's right after "starting network" and I think it's hanging on the fstab mounting of network drives.  The thing is, if I just hit 'enter', then it continues to boot as normal.  And the drives are mounted too.  What's the deal?


Darryl

---

### Post by spiderbatdad on 2009-04-14
not sure but maybe copy/paste dmesg to pastebin and post a link to it in your next post.
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

```
dmesg > ~/Desktop/dmesg.txt
```

---

### Post by juancarlospaco on 2009-04-14
ACPI/APM/IOAPIC or VBOX not properly installed.

---

### Post by _Purple_ on 2009-04-15
Try to edit Grub and add acpi=noirq to the end of the first kernel statement. 

```
gksudo gedit /boot/grub/menu.lst 
```

Then save and reboot. I am not sure if this will fix your problem.

---

### Post by dphirschler on 2009-04-15
> **spiderbatdad said:**
> not sure but maybe copy/paste dmesg to pastebin and post a link to it in your next post.
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

```
dmesg > ~/Desktop/dmesg.txt
```

OK, here goes...

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:57:48 UTC 2009 (Ubuntu 2.6.27-11.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3781d000 - 37fefc03
[    0.000000] ACPI: RSDP 000F6C50, 0014 (r0 KT600 )
[    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 KT600  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 KT600  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF30C0, 4998 (r1 KT600  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: APIC 3FFF7A80, 005A (r1 KT600  AWRDACPI 42302E31 AWRD        0)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781d000 - 0037fefc03]          RAMDISK ==> [003781d000 - 0037fefc03]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f5290] 000f5290
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262013
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3945 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 32464 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259709
[    0.000000] Kernel command line: root=UUID=e7da5971-2261-42d0-bce5-ea6f129d0e42 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1498.521 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1024672k/1048512k available (2576k kernel code, 22988k reserved, 1164k data, 424k init, 131008k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03843ea - 0xc04a7680   (1164 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03843ea   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004023] Calibrating delay loop (skipped), value calculated using timer frequency.. 2997.04 BogoMIPS (lpj=5994084)
[    0.004064] Security Framework initialized
[    0.004080] SELinux:  Disabled at boot.
[    0.004131] AppArmor: AppArmor initialized
[    0.004147] Mount-cache hash table entries: 512
[    0.004465] Initializing cgroup subsys ns
[    0.004473] Initializing cgroup subsys cpuacct
[    0.004477] Initializing cgroup subsys memory
[    0.004504] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004509] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004536] Checking 'hlt' instruction... OK.
[    0.020496] SMP alternatives: switching to UP code
[    0.028052] Freeing SMP alternatives: 11k freed
[    0.028059] ACPI: Core revision 20080609
[    0.032093] ACPI: Checking initramfs for custom DSDT
[    0.480449] ENABLING IO-APIC IRQs
[    0.480768] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.520481] CPU0: AMD Athlon(tm) XP 1800+ stepping 01
[    0.524031] Brought up 1 CPUs
[    0.524031] Total of 1 processors activated (2997.04 BogoMIPS).
[    0.524031] CPU0 attaching NULL sched-domain.
[    0.524031] net_namespace: 840 bytes
[    0.524031] Booting paravirtualized kernel on bare hardware
[    0.524031] Time: 11:24:25  Date: 04/14/09
[    0.524031] NET: Registered protocol family 16
[    0.524031] EISA bus registered
[    0.524031] ACPI: bus type pci registered
[    0.527484] PCI: PCI BIOS revision 2.10 entry at 0xfb360, last bus=1
[    0.527489] PCI: Using configuration type 1 for base access
[    0.530065] ACPI: EC: Look up EC in DSDT
[    0.540790] ACPI: Interpreter enabled
[    0.540804] ACPI: (supports S0 S1 S4 S5)
[    0.540833] ACPI: Using IOAPIC for interrupt routing
[    0.552854] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.552991] PCI: 0000:00:00.0 reg 10 32bit mmio: [d0000000, d7ffffff]
[    0.553072] pci 0000:00:01.0: supports D1
[    0.553114] PCI: 0000:00:09.0 reg 10 32bit mmio: [d8000000, dbffffff]
[    0.553181] PCI: 0000:00:0b.0 reg 10 32bit mmio: [e0000000, e00003ff]
[    0.553222] pci 0000:00:0b.0: supports D1
[    0.553225] pci 0000:00:0b.0: supports D2
[    0.553258] PCI: 0000:00:0f.0 reg 10 io port: [9000, 9007]
[    0.553266] PCI: 0000:00:0f.0 reg 14 io port: [9400, 9403]
[    0.553274] PCI: 0000:00:0f.0 reg 18 io port: [9800, 9807]
[    0.553281] PCI: 0000:00:0f.0 reg 1c io port: [9c00, 9c03]
[    0.553289] PCI: 0000:00:0f.0 reg 20 io port: [a000, a00f]
[    0.553297] PCI: 0000:00:0f.0 reg 24 io port: [a400, a4ff]
[    0.553360] PCI: 0000:00:0f.1 reg 20 io port: [a800, a80f]
[    0.553434] PCI: 0000:00:10.0 reg 20 io port: [ac00, ac1f]
[    0.553456] pci 0000:00:10.0: supports D1
[    0.553459] pci 0000:00:10.0: supports D2
[    0.553463] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.553469] pci 0000:00:10.0: PME# disabled
[    0.553516] PCI: 0000:00:10.1 reg 20 io port: [b000, b01f]
[    0.553539] pci 0000:00:10.1: supports D1
[    0.553542] pci 0000:00:10.1: supports D2
[    0.553545] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.553550] pci 0000:00:10.1: PME# disabled
[    0.553595] PCI: 0000:00:10.2 reg 20 io port: [b400, b41f]
[    0.553618] pci 0000:00:10.2: supports D1
[    0.553620] pci 0000:00:10.2: supports D2
[    0.553623] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.553629] pci 0000:00:10.2: PME# disabled
[    0.553673] PCI: 0000:00:10.3 reg 20 io port: [b800, b81f]
[    0.553695] pci 0000:00:10.3: supports D1
[    0.553698] pci 0000:00:10.3: supports D2
[    0.553701] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.553706] pci 0000:00:10.3: PME# disabled
[    0.553734] PCI: 0000:00:10.4 reg 10 32bit mmio: [e0001000, e00010ff]
[    0.553774] pci 0000:00:10.4: supports D1
[    0.553776] pci 0000:00:10.4: supports D2
[    0.553779] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.553785] pci 0000:00:10.4: PME# disabled
[    0.553850] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.553892] PCI: 0000:00:11.5 reg 10 io port: [bc00, bcff]
[    0.553933] pci 0000:00:11.5: supports D1
[    0.553936] pci 0000:00:11.5: supports D2
[    0.553966] PCI: 0000:00:12.0 reg 10 io port: [c400, c4ff]
[    0.553974] PCI: 0000:00:12.0 reg 14 32bit mmio: [e0002000, e00020ff]
[    0.554010] pci 0000:00:12.0: supports D1
[    0.554013] pci 0000:00:12.0: supports D2
[    0.554016] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.554021] pci 0000:00:12.0: PME# disabled
[    0.554072] PCI: 0000:01:00.0 reg 10 32bit mmio: [de000000, deffffff]
[    0.554079] PCI: 0000:01:00.0 reg 14 32bit mmio: [dc000000, ddffffff]
[    0.554100] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, ffff]
[    0.554149] PCI: bridge 0000:00:01.0 32bit mmio: [de000000, dfffffff]
[    0.554155] PCI: bridge 0000:00:01.0 32bit mmio pref: [dc000000, ddffffff]
[    0.554164] bus 00 -> node 0
[    0.554175] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.605415] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.605747] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.606080] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.606409] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12)
[    0.606696] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.606971] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.607246] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.607522] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.607835] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.608165] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.608518] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.608833] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.609134] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.609201] pnp: PnP ACPI init
[    0.609217] ACPI: bus type pnp registered
[    0.616627] pnp: PnP ACPI: found 13 devices
[    0.616633] ACPI: ACPI bus type pnp unregistered
[    0.616640] PnPBIOS: Disabled by ACPI PNP
[    0.617339] PCI: Using ACPI for IRQ routing
[    0.617543] NET: Registered protocol family 8
[    0.617543] NET: Registered protocol family 20
[    0.617543] NetLabel: Initializing
[    0.617543] NetLabel:  domain hash size = 128
[    0.617543] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.617543] NetLabel:  unlabeled traffic allowed by default
[    0.617543] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.617543]    actual entries 65620
[    0.617543] AppArmor: AppArmor Filesystem Enabled
[    0.617543] ACPI: RTC can wake from S4
[    0.617543] system 00:00: iomem range 0xd0400-0xd3fff has been reserved
[    0.617543] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.617543] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.617543] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.617543] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.617543] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.617543] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.617543] system 00:00: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.617543] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.617543] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.617543] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.617543] system 00:02: ioport range 0x4000-0x407f has been reserved
[    0.617543] system 00:02: ioport range 0x5000-0x500f has been reserved
[    0.617543] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.617543] system 00:03: ioport range 0x800-0x805 has been reserved
[    0.617543] system 00:03: ioport range 0x290-0x297 has been reserved
[    0.654414] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.654419] pci 0000:00:01.0:   IO window: disabled
[    0.654427] pci 0000:00:01.0:   MEM window: 0xde000000-0xdfffffff
[    0.654433] pci 0000:00:01.0:   PREFETCH window: 0x000000dc000000-0x000000ddffffff
[    0.654455] pci 0000:00:01.0: setting latency timer to 64
[    0.654461] bus: 00 index 0 io port: [0, ffff]
[    0.654464] bus: 00 index 1 mmio: [0, ffffffff]
[    0.654467] bus: 01 index 0 mmio: [0, 0]
[    0.654470] bus: 01 index 1 mmio: [de000000, dfffffff]
[    0.654473] bus: 01 index 2 mmio: [dc000000, ddffffff]
[    0.654477] bus: 01 index 3 mmio: [0, 0]
[    0.654500] NET: Registered protocol family 2
[    0.654709] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.655308] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.657868] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.659238] TCP: Hash tables configured (established 131072 bind 65536)
[    0.659245] TCP reno registered
[    0.659452] NET: Registered protocol family 1
[    0.659709] checking if image is initramfs... it is
[    1.156080] Switched to high resolution mode on CPU 0
[    1.644353] Freeing initrd memory: 8011k freed
[    1.645945] audit: initializing netlink socket (disabled)
[    1.645977] type=2000 audit(1239708265.644:1): initialized
[    1.653596] highmem bounce pool size: 64 pages
[    1.653609] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.657609] VFS: Disk quotas dquot_6.5.1
[    1.657773] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.657987] msgmni has been set to 1761
[    1.658219] io scheduler noop registered
[    1.658223] io scheduler anticipatory registered
[    1.658226] io scheduler deadline registered
[    1.658245] io scheduler cfq registered (default)
[    1.658267] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.658363] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    1.658390] pci 0000:01:00.0: Boot video device
[    1.658968] isapnp: Scanning for PnP cards...
[    2.012465] isapnp: No Plug & Play device found
[    2.083229] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.083399] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.083654] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.084820] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.085465] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.088585] brd: module loaded
[    2.088726] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.088947] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.088953] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.089170] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.090026] mice: PS/2 mouse device common for all mice
[    2.090289] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.090329] rtc0: alarms up to one year, y3k
[    2.090547] EISA: Probing bus 0 at eisa.0
[    2.090570] Cannot allocate resource for EISA slot 4
[    2.090574] Cannot allocate resource for EISA slot 5
[    2.090588] EISA: Detected 0 cards.
[    2.090594] cpuidle: using governor ladder
[    2.090598] cpuidle: using governor menu
[    2.091422] TCP cubic registered
[    2.091473] Using IPI No-Shortcut mode
[    2.091912] registered taskstats version 1
[    2.092142]   Magic number: 5:578:428
[    2.092484] rtc_cmos 00:05: setting system clock to 2009-04-14 11:24:27 UTC (1239708267)
[    2.092490] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.092493] EDD information not available.
[    2.093378] Freeing unused kernel memory: 424k freed
[    2.093463] Write protecting the kernel text: 2580k
[    2.093520] Write protecting the kernel read-only data: 940k
[    2.113391] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.440064] fuse init (API version 7.9)
[    2.477449] fan PNP0C0B:00: registered as cooling_device0
[    2.477463] ACPI: Fan [FAN] (on)
[    2.490594] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.490689] processor ACPI0007:00: registered as cooling_device1
[    2.495427] thermal LNXTHERM:01: registered as thermal_zone0
[    2.495959] ACPI: Thermal Zone [THRM] (40 C)
[    3.537267] No dock devices found.
[    3.687783] SCSI subsystem initialized
[    3.732313] usbcore: registered new interface driver usbfs
[    3.732363] usbcore: registered new interface driver hub
[    3.739935] usbcore: registered new device driver usb
[    3.810518] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    3.810526] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    3.810541] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    3.810564] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    3.810660] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    3.810751] ehci_hcd 0000:00:10.4: irq 21, io mem 0xe0001000
[    3.820045] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.820380] usb usb1: configuration #1 chosen from 1 choice
[    3.820439] hub 1-0:1.0: USB hub found
[    3.820460] hub 1-0:1.0: 8 ports detected
[    3.827602] USB Universal Host Controller Interface driver v3.0
[    3.830291] libata version 3.00 loaded.
[    3.849179] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.849190] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    4.028579] sata_via 0000:00:0f.0: version 2.3
[    4.029168] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    4.029173] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    4.029188] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    4.029284] sata_via 0000:00:0f.0: routed to hard irq line 11
[    4.030105] scsi0 : sata_via
[    4.030364] scsi1 : sata_via
[    4.030448] ata1: SATA max UDMA/133 cmd 0x9000 ctl 0x9400 bmdma 0xa000 irq 20
[    4.030453] ata2: SATA max UDMA/133 cmd 0x9800 ctl 0x9c00 bmdma 0xa008 irq 20
[    4.232112] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.396332] ata1.00: ATA-7: WDC WD2000JS-60NCB1, 10.02E02, max UDMA/100
[    4.396341] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.404293] ata1.00: configured for UDMA/100
[    4.608105] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    4.608353] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JS-60N 10.0 PQ: 0 ANSI: 5
[    4.608531] pata_via 0000:00:0f.1: version 0.3.3
[    4.608568] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    4.608838] scsi2 : pata_via
[    4.608937] scsi3 : pata_via
[    4.611594] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xa800 irq 14
[    4.611599] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xa808 irq 15
[    4.772443] ata3.00: ATA-4: ST310211A, 3.54, max UDMA/100
[    4.772451] ata3.00: 19541088 sectors, multi 16: LBA 
[    4.780309] ata3.00: configured for UDMA/100
[    4.944501] ata4.00: ATAPI: SONY    DVD RW DW-D22A, BYS2, max UDMA/66
[    4.960372] ata4.00: configured for UDMA/66
[    4.960594] scsi 2:0:0:0: Direct-Access     ATA      ST310211A        3.54 PQ: 0 ANSI: 5
[    4.961563] scsi 3:0:0:0: CD-ROM            SONY     DVD RW DW-D22A   BYS2 PQ: 0 ANSI: 5
[    4.961780] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    4.961801] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    4.961855] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    4.961889] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000ac00
[    4.962231] usb usb2: configuration #1 chosen from 1 choice
[    4.962276] hub 2-0:1.0: USB hub found
[    4.962295] hub 2-0:1.0: 2 ports detected
[    5.028478] Marking TSC unstable due to TSC halts in idle
[    5.168522] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    5.168543] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    5.168588] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    5.168623] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b000
[    5.168829] usb usb3: configuration #1 chosen from 1 choice
[    5.168882] hub 3-0:1.0: USB hub found
[    5.168898] hub 3-0:1.0: 2 ports detected
[    5.377495] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    5.377515] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    5.377851] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    5.377884] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b400
[    5.378615] usb usb4: configuration #1 chosen from 1 choice
[    5.378942] hub 4-0:1.0: USB hub found
[    5.378964] hub 4-0:1.0: 2 ports detected
[    5.488043] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    5.585825] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    5.585846] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    5.585896] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    5.585932] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000b800
[    5.586137] usb usb5: configuration #1 chosen from 1 choice
[    5.586182] hub 5-0:1.0: USB hub found
[    5.586200] hub 5-0:1.0: 2 ports detected
[    5.673529] usb 3-2: configuration #1 chosen from 1 choice
[    5.794300] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[    5.794307] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    5.794322] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    5.799275] eth0: VIA Rhine II at 0xe0002000, 00:11:5b:a6:e4:c0, IRQ 23.
[    5.799988] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[    5.836548] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.836620] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    5.836688] scsi 3:0:0:0: Attached scsi generic sg2 type 5
[    5.980349] Driver 'sd' needs updating - please use bus_type methods
[    5.980554] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    5.980584] sd 0:0:0:0: [sda] Write Protect is off
[    5.980589] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.980629] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.980745] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    5.980768] sd 0:0:0:0: [sda] Write Protect is off
[    5.980772] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.980810] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.980818]  sda: sda1
[    5.990316] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.990482] sd 2:0:0:0: [sdb] 19541088 512-byte hardware sectors (10005 MB)
[    5.990512] sd 2:0:0:0: [sdb] Write Protect is off
[    5.990517] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.990558] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.990657] sd 2:0:0:0: [sdb] 19541088 512-byte hardware sectors (10005 MB)
[    5.990680] sd 2:0:0:0: [sdb] Write Protect is off
[    5.990684] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.990723] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.990731]  sdb: sdb1 sdb2 < sdb5 >
[    6.043803] sd 2:0:0:0: [sdb] Attached SCSI disk
[    6.064350] usbcore: registered new interface driver hiddev
[    6.078243] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input2
[    6.080379] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:10.1-2
[    6.132768] Driver 'sr' needs updating - please use bus_type methods
[    6.134652] sr0: scsi3-mmc drive: 125x/125x writer cd/rw xa/form2 cdda tray
[    6.134663] Uniform CD-ROM driver Revision: 3.20
[    6.134888] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    6.168308] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.1/input/input3
[    6.192459] input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:10.1-2
[    6.192506] usbcore: registered new interface driver usbhid
[    6.192512] usbhid: v2.6:USB HID core driver
[    6.890725] PM: Starting manual resume from disk
[    6.890735] PM: Resume from partition 8:21
[    6.890738] PM: Checking hibernation image.
[    6.891074] PM: Resume from disk failed.
[    6.955141] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.955151] EXT3-fs: write access will be enabled during recovery.
[    9.876452] kjournald starting.  Commit interval 5 seconds
[    9.876490] EXT3-fs: sdb1: orphan cleanup on readonly fs
[    9.927078] ext3_orphan_cleanup: deleting unreferenced inode 16521
[    9.950955] ext3_orphan_cleanup: deleting unreferenced inode 450815
[    9.954331] ext3_orphan_cleanup: deleting unreferenced inode 450817
[    9.962078] ext3_orphan_cleanup: deleting unreferenced inode 450816
[    9.973034] ext3_orphan_cleanup: deleting unreferenced inode 450800
[    9.973055] ext3_orphan_cleanup: deleting unreferenced inode 450799
[    9.973071] ext3_orphan_cleanup: deleting unreferenced inode 450761
[    9.973276] ext3_orphan_cleanup: deleting unreferenced inode 450742
[    9.973291] ext3_orphan_cleanup: deleting unreferenced inode 450741
[    9.973302] ext3_orphan_cleanup: deleting unreferenced inode 450739
[    9.973312] ext3_orphan_cleanup: deleting unreferenced inode 450738
[    9.973322] ext3_orphan_cleanup: deleting unreferenced inode 450737
[    9.973331] EXT3-fs: sdb1: 12 orphan inodes deleted
[    9.973334] EXT3-fs: recovery complete.
[   10.010288] EXT3-fs: mounted filesystem with ordered data mode.
[   23.183324] udevd version 124 started
[   24.197768] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.305577] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.504826] Linux agpgart interface v0.103
[   24.764330] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   24.781588] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[   24.892466] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   24.908073] ACPI: Power Button (FF) [PWRF]
[   24.908266] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   24.924059] ACPI: Power Button (CM) [PWRB]
[   24.924314] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   24.940056] ACPI: Sleep Button (CM) [SLPB]
[   26.160358] Linux video capture interface: v2.00
[   26.546128] parport_pc 00:0b: reported by Plug and Play ACPI
[   26.546200] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   27.126791] cx18:  Start initialization, version 1.0.0
[   27.126900] cx18-0: Initializing card #0
[   27.126907] cx18-0: Autodetected Hauppauge card
[   27.126938] cx18 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.126953] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   27.130411] cx18-0: cx23418 revision 01010000 (B)
[   27.416432] saa7130/34: v4l2 driver version 0.2.14 loaded
[   27.605608] tveeprom 1-0050: Hauppauge model 74021, rev C1B2, serial# 884873
[   27.605616] tveeprom 1-0050: MAC address is 00-0D-FE-0D-80-89
[   27.605621] tveeprom 1-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   27.605626] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   27.605630] tveeprom 1-0050: audio processor is CX23418 (idx 38)
[   27.605634] tveeprom 1-0050: decoder processor is CX23418 (idx 31)
[   27.605638] tveeprom 1-0050: has no radio, has IR receiver, has IR transmitter
[   27.605643] cx18-0: Autodetected Hauppauge HVR-1600
[   27.605646] cx18-0: VBI is not yet supported
[   27.927588] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   28.212220] tuner 2-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   28.212259] cs5345 1-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   28.437107] tuner-simple 2-0061: creating new instance
[   28.437116] tuner-simple 2-0061: type set to 50 (TCL 2002N)
[   28.438164] cx18-0: Disabled encoder IDX device
[   28.438452] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   28.438459] DVB: registering new adapter (cx18)
[   29.298399] MXL5005S: Attached at address 0x63
[   29.298413] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   29.298755] cx18-0: DVB Frontend registered
[   29.298819] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   29.298872] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   29.298879] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   29.298971] saa7134 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   29.298982] saa7130[0]: found at 0000:00:0b.0, rev: 1, irq: 19, latency: 32, mmio: 0xe0000000
[   29.298992] saa7130[0]: subsystem: 1131:2041, board: UNKNOWN/GENERIC [card=0,autodetected]
[   29.299013] saa7130[0]: board init: gpio is 131ff
[   29.576059] All bytes are equal. It is not a TEA5767
[   29.576283] tuner' 3-0060: chip found @ 0xc0 (saa7130[0])
[   29.584083] tuner' 3-0061: chip found @ 0xc2 (saa7130[0])
[   29.632299] saa7130[0]: i2c eeprom 00: 31 11 41 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   29.632317] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[   29.632328] saa7130[0]: i2c eeprom 20: 41 41 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632340] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632351] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632361] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632372] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632383] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632394] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632405] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632416] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632427] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632438] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632449] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632460] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.632471] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.636370] saa7130[0]: registered device video1 [v4l2]
[   29.636462] saa7130[0]: registered device vbi0
[   29.636570] cx18:  End initialization
[   29.747778] saa7134 ALSA driver for DMA sound loaded
[   29.748927] saa7130[0]/alsa: saa7130[0] at 0xe0000000 irq 19 registered as card -2
[   29.934365] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   29.934373] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   29.934388] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   29.934556] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   36.148430] lp0: using parport0 (interrupt-driven).
[   36.461526] Adding 465844k swap on /dev/sdb5.  Priority:-1 extents:1 across:465844k
[   37.086038] EXT3 FS on sdb1, internal journal
[   38.287309] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   38.291190] SGI XFS Quota Management subsystem
[   38.304552] XFS mounting filesystem sda1
[   38.475308] Starting XFS recovery on filesystem: sda1 (logdev: internal)
[   38.538863] Ending XFS recovery on filesystem: sda1 (logdev: internal)
[   39.130103] type=1505 audit(1239708304.241:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4089
[   39.478652] type=1505 audit(1239708304.589:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4094
[   39.479234] type=1505 audit(1239708304.589:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4094
[   39.587655] type=1505 audit(1239708304.697:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4098
[   39.986209] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.086813] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2868.808069]  CIFS VFS: Error connecting to socket. Aborting operation
[ 2868.808144]  CIFS VFS: cifs_mount failed w/return code = -113
[ 2869.750689] NET: Registered protocol family 10
[ 2869.751409] lo: Disabled Privacy Extensions
[ 2870.242987] ACPI: WMI: Mapper loaded
[ 2870.813106] warning: `ntpd' uses 32-bit capabilities (legacy support in use)
[ 2876.336868] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[ 2876.336880] apm: overridden by ACPI.
[ 2876.677411] ppdev: user-space parallel port driver
[ 2880.472049] eth0: no IPv6 routers present
[ 2882.228059] firmware: requesting v4l-cx23418-apu.fw
[ 2882.430404] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[ 2882.928040] firmware: requesting v4l-cx23418-cpu.fw
[ 2883.001019] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[ 2883.007206] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[ 2883.204032] firmware: requesting v4l-cx23418-apu.fw
[ 2883.756052] firmware: requesting v4l-cx23418-cpu.fw
[ 2884.016047] firmware: requesting v4l-cx23418-dig.fw
[ 2884.201128] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[ 2889.334282] Bluetooth: Core ver 2.13
[ 2889.338734] NET: Registered protocol family 31
[ 2889.338743] Bluetooth: HCI device and connection manager initialized
[ 2889.338750] Bluetooth: HCI socket layer initialized
[ 2889.441019] Bluetooth: L2CAP ver 2.11
[ 2889.441029] Bluetooth: L2CAP socket layer initialized
[ 2889.509550] Bluetooth: SCO (Voice Link) ver 0.6
[ 2889.509560] Bluetooth: SCO socket layer initialized
[ 2889.652211] Bluetooth: RFCOMM socket layer initialized
[ 2889.653237] Bluetooth: RFCOMM TTY layer initialized
[ 2889.653245] Bluetooth: RFCOMM ver 1.10
[ 2889.681171] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 2889.681181] Bluetooth: BNEP filters: protocol multicast
[ 2890.150822] Bridge firewalling registered
[ 2928.861703] UDF-fs: Partition marked readonly; forcing readonly mount
[ 2928.974274] UDF-fs INFO UDF: Mounting volume 'Cartoon Classics 3', timestamp 2003/09/16 03:37 (1f10)
[ 3006.448274] ppdev0: registered pardevice
[ 3006.496136] ppdev0: unregistered pardevice
[ 3006.823419] ppdev0: registered pardevice
[ 3006.920663] ppdev0: unregistered pardevice
[ 3011.548565] ppdev0: registered pardevice
[ 3011.596295] ppdev0: unregistered pardevice

```

Darryl

---

### Post by dphirschler on 2009-04-15
OK, I noticed this:

> [ 2868.808069]  CIFS VFS: Error connecting to socket. Aborting operation
[ 2868.808144]  CIFS VFS: cifs_mount failed w/return code = -113

I remember seeing error code -113.  But my mounts work.  Woops, I just checked /mnt/thurgood and it is not there.  So it is my Windows machine not being mounted.  Perhaps it was turned off at the time.  Is there a way to make it mount only if it is available?  Why make it wait for a keypress when it is not?


Darryl

---

