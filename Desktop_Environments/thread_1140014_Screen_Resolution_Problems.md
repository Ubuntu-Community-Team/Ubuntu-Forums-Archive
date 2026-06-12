---
title: "Screen Resolution Problems"
date: 2009-04-27
forum: Desktop Environments
---

### Post by RossImlach on 2009-04-27
I recently installed Ubuntu 9.04 on one of my PCs. The installation went fine etc, and it is running great, apart from one thing: the screen resolution is stuck on 800x600. I have looked in System>preferences>display, but the setting only goes upto 800x600... Can anyone help me to increase this?

Thanks in advance.

---

### Post by Jimbley on 2009-04-27
Hi mate,

We need quite a bit more info off you with regards to your setup. Can you paste the results of dmesg and lspci -v in this thread and let us know what your graphics card is?

Cheers

Jim

---

### Post by RossImlach on 2009-04-27
lspci -v

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8157
    Flags: bus master, fast devsel, latency 0
    Memory at fac00000 (32-bit, prefetchable) [size=4M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a5
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Memory at fbe80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at d800 [size=8]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at c400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fbe7bc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbf00000-fbffffff
    Prefetchable memory behind bridge: 20000000-200fffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at fc00 [size=16]
    Memory at 20100000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8227
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at c000 [size=256]
    I/O ports at b800 [size=64]
    Memory at fbe7b800 (32-bit, non-prefetchable) [size=512]
    Memory at fbe7b400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:0a.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
    Subsystem: Smart Link Ltd. Device 5459
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at e800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: serial

01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at e400 [size=256]
    Memory at fbffec00 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at 20000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

01:0d.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
    Subsystem: ASUSTeK Computer Inc. Device 811a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
    Memory at fbff8000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at e000 [size=256]
    Expansion ROM at 20020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: skge
    Kernel modules: skge

dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  modified: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  modified: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 1fff0000 @ 10000-16000
[    0.000000] RAMDISK: 1f8ad000 - 1ffdfdbe
[    0.000000] ACPI: RSDP 000FA760, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1FFF0000, 0028 (r1 AMIINT                10 MSFT       97)
[    0.000000] ACPI: FACP 1FFF0030, 0074 (r1 AMIINT                10 MSFT       97)
[    0.000000] ACPI: DSDT 1FFF00B0, 1E3A (r1 AMD75X IRONGATE     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1FFF8000, 0040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fff0000
[    0.000000]   low ram: 00000000 - 1fff0000
[    0.000000]   bootmap 00012000 - 00016000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [001f8ad000 - 001ffdfdbe]          RAMDISK ==> [001f8ad000 - 001ffdfdbe]
[    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
[    0.000000]   HighMem  0x0001fff0 -> 0x0001fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fff0
[    0.000000] On node 0 totalpages: 130943
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125968 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x5008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129919
[    0.000000] Kernel command line: root=UUID=0b916dee-edcd-4164-9216-396c88242964 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 997.952 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2620800 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 501404k/524224k available (4126k kernel code, 22200k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xe07f0000 - 0xff3fe000   ( 492 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004023] Calibrating delay loop (skipped), value calculated using timer frequency.. 1995.90 BogoMIPS (lpj=3991808)
[    0.004072] Security Framework initialized
[    0.004090] SELinux:  Disabled at boot.
[    0.004171] AppArmor: AppArmor initialized
[    0.004192] Mount-cache hash table entries: 512
[    0.004525] Initializing cgroup subsys ns
[    0.004534] Initializing cgroup subsys cpuacct
[    0.004540] Initializing cgroup subsys memory
[    0.004550] Initializing cgroup subsys freezer
[    0.004578] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004584] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004620] Checking 'hlt' instruction... OK.
[    0.020160] SMP alternatives: switching to UP code
[    0.325527] Freeing SMP alternatives: 18k freed
[    0.325539] ACPI: Core revision 20080926
[    0.327528] ACPI: Checking initramfs for custom DSDT
[    0.931975] ACPI: setting ELCR to 0200 (from 0c00)
[    0.932164] weird, boot CPU (#0) not listedby the BIOS.
[    0.932170] SMP motherboard not detected.
[    0.932176] Local APIC not detected. Using dummy APIC emulation.
[    0.932181] SMP disabled
[    0.932977] Brought up 1 CPUs
[    0.932984] Total of 1 processors activated (1995.90 BogoMIPS).
[    0.933020] CPU0 attaching NULL sched-domain.
[    0.933821] net_namespace: 776 bytes
[    0.933853] Booting paravirtualized kernel on bare hardware
[    0.934374] Time: 16:10:33  Date: 04/27/09
[    0.934387] regulator: core version 0.5
[    0.934492] NET: Registered protocol family 16
[    0.934820] EISA bus registered
[    0.934852] ACPI: bus type pci registered
[    0.964874] PCI: PCI BIOS revision 2.10 entry at 0xfdb71, last bus=1
[    0.964880] PCI: Using configuration type 1 for base access
[    0.967668] ACPI: EC: Look up EC in DSDT
[    0.975012] ACPI: Interpreter enabled
[    0.975025] ACPI: (supports S0 S1 S4 S5)
[    0.975062] ACPI: Using PIC for interrupt routing
[    0.981393] ACPI: No dock devices found.
[    0.981416] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.981507] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.981518] pci 0000:00:00.0: reg 14 32bit mmio: [0xeddff000-0xeddfffff]
[    0.981528] pci 0000:00:00.0: reg 18 io port: [0xdc00-0xdc03]
[    0.981681] pci 0000:00:07.1: reg 20 io port: [0xf000-0xf00f]
[    0.981762] pci 0000:00:07.4: reg 10 32bit mmio: [0xeffff000-0xefffffff]
[    0.981829] pci 0000:00:09.0: reg 10 io port: [0xd800-0xd8ff]
[    0.981839] pci 0000:00:09.0: reg 14 32bit mmio: [0xefffef00-0xefffefff]
[    0.981871] pci 0000:00:09.0: supports D1 D2
[    0.981877] pci 0000:00:09.0: PME# supported from D1 D2 D3hot
[    0.981884] pci 0000:00:09.0: PME# disabled
[    0.981919] pci 0000:00:0c.0: reg 10 io port: [0xd400-0xd43f]
[    0.981954] pci 0000:00:0c.0: supports D1 D2
[    0.982023] pci 0000:01:05.0: reg 10 32bit mmio: [0xee000000-0xeeffffff]
[    0.982032] pci 0000:01:05.0: reg 14 32bit mmio: [0xda000000-0xdbffffff]
[    0.982055] pci 0000:01:05.0: reg 30 32bit mmio: [0xefef0000-0xefefffff]
[    0.982100] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.982107] pci 0000:00:01.0: bridge 32bit mmio: [0xede00000-0xefefffff]
[    0.982115] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd9c00000-0xddcfffff]
[    0.982127] bus 00 -> node 0
[    0.982140] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.983425] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.983652] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.983873] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.984113] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.984268] ACPI: Power Resource [URP1] (off)
[    0.984330] ACPI: Power Resource [URP2] (off)
[    0.984395] ACPI: Power Resource [FDDP] (off)
[    0.984468] ACPI: Power Resource [LPTP] (off)
[    0.984569] ACPI: WMI: Mapper loaded
[    0.985107] SCSI subsystem initialized
[    0.985220] libata version 3.00 loaded.
[    0.985360] usbcore: registered new interface driver usbfs
[    0.985400] usbcore: registered new interface driver hub
[    0.985469] usbcore: registered new device driver usb
[    0.985737] PCI: Using ACPI for IRQ routing
[    0.985895] Bluetooth: Core ver 2.13
[    0.985895] NET: Registered protocol family 31
[    0.985895] Bluetooth: HCI device and connection manager initialized
[    0.985895] Bluetooth: HCI socket layer initialized
[    0.985895] NET: Registered protocol family 8
[    0.985895] NET: Registered protocol family 20
[    0.985895] NetLabel: Initializing
[    0.985895] NetLabel:  domain hash size = 128
[    0.985895] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.985895] NetLabel:  unlabeled traffic allowed by default
[    0.985895] AppArmor: AppArmor Filesystem Enabled
[    0.985895] pnp: PnP ACPI init
[    0.985895] ACPI: bus type pnp registered
[    0.992788] pnp: PnP ACPI: found 11 devices
[    0.992793] ACPI: ACPI bus type pnp unregistered
[    0.992803] PnPBIOS: Disabled by ACPI PNP
[    1.027784] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.027791] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    1.027800] pci 0000:00:01.0:   MEM window: 0xede00000-0xefefffff
[    1.027808] pci 0000:00:01.0:   PREFETCH window: 0x000000d9c00000-0x000000ddcfffff
[    1.027833] bus: 00 index 0 io port: [0x00-0xffff]
[    1.027838] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.027843] bus: 01 index 0 io port: [0xb000-0xbfff]
[    1.027848] bus: 01 index 1 mmio: [0xede00000-0xefefffff]
[    1.027853] bus: 01 index 2 mmio: [0xd9c00000-0xddcfffff]
[    1.027857] bus: 01 index 3 mmio: [0x0-0x0]
[    1.027888] NET: Registered protocol family 2
[    1.028172] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    1.028767] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    1.029145] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    1.029532] TCP: Hash tables configured (established 16384 bind 16384)
[    1.029539] TCP reno registered
[    1.029805] NET: Registered protocol family 1
[    1.030167] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.631253]  it is
[    2.373072] Freeing initrd memory: 7371k freed
[    2.373314] cpufreq: No nForce2 chipset.
[    2.373683] audit: initializing netlink socket (disabled)
[    2.373735] type=2000 audit(1240848634.372:1): initialized
[    2.391215] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.394153] VFS: Disk quotas dquot_6.5.1
[    2.394276] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.395640] fuse init (API version 7.10)
[    2.395821] msgmni has been set to 994
[    2.396332] alg: No test for stdrng (krng)
[    2.396363] io scheduler noop registered
[    2.396369] io scheduler anticipatory registered
[    2.396373] io scheduler deadline registered
[    2.396407] io scheduler cfq registered (default)
[    2.412089] pci 0000:01:05.0: Boot video device
[    2.417621] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.417642] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.417932] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.417940] ACPI: Power Button (FF) [PWRF]
[    2.418036] input: Sleep Button (FF) as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input1
[    2.418042] ACPI: Sleep Button (FF) [SLPF]
[    2.418150] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    2.418156] ACPI: Power Button (CM) [PWRB]
[    2.418418] processor ACPI_CPU:00: registered as cooling_device0
[    2.421528] isapnp: Scanning for PnP cards...
[    2.775319] isapnp: No Plug & Play device found
[    2.778015] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.778155] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.778294] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.778828] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.779020] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.780726] brd: module loaded
[    2.781456] loop: module loaded
[    2.781671] Fixed MDIO Bus: probed
[    2.781687] PPP generic driver version 2.4.2
[    2.781846] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.781921] Driver 'sd' needs updating - please use bus_type methods
[    2.781942] Driver 'sr' needs updating - please use bus_type methods
[    2.782424] pata_amd 0000:00:07.1: version 0.3.10
[    2.782887] scsi0 : pata_amd
[    2.783177] scsi1 : pata_amd
[    2.783270] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    2.783276] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    2.944505] ata1.00: ATA-5: ST360021A, 3.75, max UDMA/100
[    2.944512] ata1.00: 117231408 sectors, multi 16: LBA 
[    2.952437] ata1.00: configured for UDMA/66
[    3.124301] ata2.00: ATAPI: LITE-ON LTR-52327S, QS53, max UDMA/33
[    3.124359] ata2.01: ATAPI: PIONEER DVD-RW  DVR-109, 1.57, max UDMA/33
[    3.140269] ata2.00: configured for UDMA/33
[    3.156312] ata2.01: configured for UDMA/33
[    3.163768] scsi 0:0:0:0: Direct-Access     ATA      ST360021A        3.75 PQ: 0 ANSI: 5
[    3.164031] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    3.164081] sd 0:0:0:0: [sda] Write Protect is off
[    3.164088] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.164154] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.164331] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    3.164368] sd 0:0:0:0: [sda] Write Protect is off
[    3.164373] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.164436] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.164446]  sda: sda1 sda2 < sda5 >
[    3.198042] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.198166] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.199126] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-52327S       QS53 PQ: 0 ANSI: 5
[    3.202632] sr0: scsi3-mmc drive: 67x/52x writer cd/rw xa/form2 cdda tray
[    3.202641] Uniform CD-ROM driver Revision: 3.20
[    3.202872] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.202975] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.209387] scsi 1:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-109  1.57 PQ: 0 ANSI: 5
[    3.227742] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    3.227879] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    3.227952] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    3.228939] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.228976] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.229463] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[    3.229471] PCI: setting IRQ 10 as level-triggered
[    3.229481] ohci_hcd 0000:00:07.4: PCI INT D -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[    3.229545] ohci_hcd 0000:00:07.4: OHCI Host Controller
[    3.229688] ohci_hcd 0000:00:07.4: new USB bus registered, assigned bus number 1
[    3.229739] ohci_hcd 0000:00:07.4: irq 10, io mem 0xeffff000
[    3.284224] usb usb1: configuration #1 chosen from 1 choice
[    3.284288] hub 1-0:1.0: USB hub found
[    3.284320] hub 1-0:1.0: 4 ports detected
[    3.284540] uhci_hcd: USB Universal Host Controller Interface driver
[    3.284717] usbcore: registered new interface driver libusual
[    3.284790] usbcore: registered new interface driver usbserial
[    3.284814] USB Serial support registered for generic
[    3.284840] usbcore: registered new interface driver usbserial_generic
[    3.284845] usbserial: USB Serial Driver core
[    3.284943] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.285296] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.285313] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.285584] mice: PS/2 mouse device common for all mice
[    3.285995] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    3.286026] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    3.286155] device-mapper: uevent: version 1.0.3
[    3.286432] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.286564] device-mapper: multipath: version 1.0.5 loaded
[    3.286571] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.286756] EISA: Probing bus 0 at eisa.0
[    3.286791] Cannot allocate resource for EISA slot 5
[    3.286809] EISA: Detected 0 cards.
[    3.286880] cpuidle: using governor ladder
[    3.286885] cpuidle: using governor menu
[    3.288060] TCP cubic registered
[    3.288274] NET: Registered protocol family 10
[    3.289162] lo: Disabled Privacy Extensions
[    3.289866] NET: Registered protocol family 17
[    3.289919] Bluetooth: L2CAP ver 2.11
[    3.289923] Bluetooth: L2CAP socket layer initialized
[    3.289930] Bluetooth: SCO (Voice Link) ver 0.6
[    3.289934] Bluetooth: SCO socket layer initialized
[    3.290018] Bluetooth: RFCOMM socket layer initialized
[    3.290044] Bluetooth: RFCOMM TTY layer initialized
[    3.290049] Bluetooth: RFCOMM ver 1.10
[    3.290107] powernow-k8: Processor cpuid 642 not supported
[    3.290161] IO APIC resources could be not be allocated.
[    3.290224] Using IPI No-Shortcut mode
[    3.290463] registered taskstats version 1
[    3.290686]   Magic number: 5:330:187
[    3.290884] rtc_cmos 00:02: setting system clock to 2009-04-27 16:10:36 UTC (1240848636)
[    3.290891] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.290896] EDD information not available.
[    3.292774] Freeing unused kernel memory: 532k freed
[    3.293073] Write protecting the kernel text: 4128k
[    3.293157] Write protecting the kernel read-only data: 1532k
[    3.333565] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.902890] Floppy drive(s): fd0 is 1.44M
[    3.920510] FDC 0 is a post-1991 82077
[    4.100995] 8139too Fast Ethernet driver 0.9.28
[    4.102887] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    4.102902] PCI: setting IRQ 11 as level-triggered
[    4.102915] 8139too 0000:00:09.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    4.104627] eth0: RealTek RTL8139 at 0xd800, 00:00:b5:50:f0:f6, IRQ 11
[    4.104633] eth0:  Identified 8139 chip type 'RTL-8139A'
[    4.959743] PM: Starting manual resume from disk
[    4.959755] PM: Resume from partition 8:5
[    4.959759] PM: Checking hibernation image.
[    4.960213] PM: Resume from disk failed.
[    4.967260] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.967271] EXT3-fs: write access will be enabled during recovery.
[    5.080425] kjournald starting.  Commit interval 5 seconds
[    5.080471] EXT3-fs: recovery complete.
[    5.081270] EXT3-fs: mounted filesystem with ordered data mode.
[   10.889873] udev: starting version 141
[   11.084735] Linux agpgart interface v0.103
[   11.094446] agpgart-amdk7 0000:00:00.0: AMD Irongate chipset
[   11.094473] agpgart-amdk7 0000:00:00.0: AMD 751 chipset with NVidia GeForce; forcing 1X due to errata
[   11.135968] agpgart-amdk7 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   11.190175] parport_pc 00:0a: reported by Plug and Play ACPI
[   11.190221] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   11.271387] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 7007 ss_vid 0 ss_did 0
[   11.271401] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   11.271516] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.115751] nvidia: module license 'NVIDIA' taints kernel.
[   12.228469] NVRM: The NVIDIA RIVA TNT2 Model 64/Model 64 Pro GPU installed in this system is
[   12.228475] NVRM:  supported through the NVIDIA 71.86.xx Legacy drivers. Please
[   12.228478] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[   12.228482] NVRM:  information.  The 173.14.16 NVIDIA driver will ignore
[   12.228485] NVRM:  this GPU.  Continuing probe...
[   12.228597] NVRM: No NVIDIA graphics adapter found!
[   12.297182] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.490779] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.826364] ENS1371 0000:00:0c.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   13.115364] ppdev: user-space parallel port driver
[   14.064565] lp0: using parport0 (interrupt-driven).
[   14.067235] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   14.335409] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k
[   14.947695] EXT3 FS on sda1, internal journal
[   16.356761] type=1505 audit(1240848649.565:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1789
[   16.499022] type=1505 audit(1240848649.705:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1793
[   16.499681] type=1505 audit(1240848649.705:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1793
[   16.499902] type=1505 audit(1240848649.705:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1793
[   16.500156] type=1505 audit(1240848649.709:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1793
[   16.903817] type=1505 audit(1240848650.109:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1798
[   16.904787] type=1505 audit(1240848650.113:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1798
[   16.992151] type=1505 audit(1240848650.201:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1802
[   21.674439] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.674448] Bluetooth: BNEP filters: protocol multicast
[   21.723510] Bridge firewalling registered
[   26.792168] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   37.676078] eth0: no IPv6 routers present
[  101.487860] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.


Thats everything that was thrown up. I can't really remember what graphics card it has, because its quite an old PC that I've just decided to put ubuntu on. All that I can tell you currently is that its an old NVidia one. Sorry I don't have much more info on that.

Thanks again

---

### Post by Jimbley on 2009-04-27
Cheers for the info.

Support for old Nvidia cards is a bit tricky at times. I suggest that you try installing the legacy drivers for your card from [http://www.nvidia.com/object/linux_display_x86_71.86.09.html](http://www.nvidia.com/object/linux_display_x86_71.86.09.html)

Let me know how you fare.

Take it easy

Jim

---

