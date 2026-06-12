---
title: "login window setting app not working"
date: 2009-02-01
forum: General Help
---

### Post by kdub on 2009-02-01
Hi,
When I go to my system>prefer>login window app, it asks for admin password,
then starts at the first tab and refuses any further commands.It then has to be force quit in order to close.Any ideas?
thanx,
ken

---

### Post by spiderbatdad on 2009-02-01
Is the user account a member of the admin group? If you type id in your terminal window, you will see the groups the user belongs to. One of the groups should be admin.

---

### Post by kdub on 2009-02-01
yeah,
it's an admin acc. and the proper password was used.I'm at a loss but it's not like I know what I'm doing-give me a year (it took me from win 3.11 to xp sp1 to almost figure out ms then I jump ship up to Linux)
kdub

---

### Post by kdub on 2009-02-04
JUst out of curiousity how do you (or what is ) type in an id in the terminal window?
thanx
kdub

---

### Post by overlord.gaurav on 2009-02-04
By type id in your terminal, he meant:
Click on Applications > Accessories > Terminal
Type "id" over here and press enter.
You'll get an output.
He wanted you to paste that output.

---

### Post by kdub on 2009-02-04
Overlord,
like this?:
uid=1000(kdub) gid=1000(kdub) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(kdub)
kdub@kbw:~$ 
thanx,
kdub

---

### Post by spiderbatdad on 2009-02-05
kdub, not sure what the problem is, but the behavior isn't normal, obviously.
Does your system have at least 512 RAM?
The kernel creates a diagnostic message during boot and some system operations. Try a fresh reboot then immediately open your terminal and enter:
```
dmesg > ~/Desktop/dmesg.txt
```This tells the computer to output the dmesg log and write it to your desktop. The command is case sensitive.
Then right click on the file that gets written to your desktop and select 'create an archive' You can upload the archive here with the manage attachment tool below.

lol. forget the first question. I see system specs in your sig.

---

### Post by kdub on 2009-02-05
Spider,
I did the command and got this:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005ff70000 (usable)
[    0.000000]  BIOS-e820: 000000005ff70000 - 000000005ff7c000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005ff7c000 - 000000005ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005ff80000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffff000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x5ff70 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781d000 - 37fefc95
[    0.000000] ACPI: RSDP 000F6500, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 5FF77A1D, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 5FF7BED2, 0074 (r1 HP     08B0      6040000 PTL        50)
[    0.000000] ACPI: DSDT 5FF77E73, 405F (r1 HP     08B0      6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 5FF7CFC0, 0040
[    0.000000] ACPI: BOOT 5FF7BFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 5FF77A4D, 018A (r1  INTEL  EISTRef     2000 INTL 20021002)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781d000 - 0037fefc95]          RAMDISK ==> [003781d000 - 0037fefc95]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0005ff70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005ff70
[    0.000000] On node 0 totalpages: 392975
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 162257 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01d87000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9f800000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389520
[    0.000000] Kernel command line: root=UUID=d527a13f-5f02-460b-8d26-dfb5e3f7b555 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1096.435 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1543380k/1572288k available (2576k kernel code, 27624k reserved, 1165k data, 424k init, 654784k highmem)
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
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004020] Calibrating delay loop (skipped), value calculated using timer frequency.. 2192.87 BogoMIPS (lpj=4385740)
[    0.004056] Security Framework initialized
[    0.004075] SELinux:  Disabled at boot.
[    0.004115] AppArmor: AppArmor initialized
[    0.004130] Mount-cache hash table entries: 512
[    0.004428] Initializing cgroup subsys ns
[    0.004439] Initializing cgroup subsys cpuacct
[    0.004443] Initializing cgroup subsys memory
[    0.004471] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004476] CPU: L2 cache: 2048K
[    0.004499] Checking 'hlt' instruction... OK.
[    0.020754] SMP alternatives: switching to UP code
[    0.028015] Freeing SMP alternatives: 11k freed
[    0.028020] ACPI: Core revision 20080609
[    0.032198] ACPI: Checking initramfs for custom DSDT
[    0.642529] ACPI: setting ELCR to 0200 (from 0c00)
[    0.644072] weird, boot CPU (#0) not listedby the BIOS.
[    0.644076] SMP motherboard not detected.
[    0.644081] Local APIC not detected. Using dummy APIC emulation.
[    0.644085] SMP disabled
[    0.644179] Brought up 1 CPUs
[    0.644183] Total of 1 processors activated (2192.87 BogoMIPS).
[    0.644202] CPU0 attaching NULL sched-domain.
[    0.644539] net_namespace: 840 bytes
[    0.644558] Booting paravirtualized kernel on bare hardware
[    0.644872] Time:  9:11:22  Date: 02/05/09
[    0.644912] NET: Registered protocol family 16
[    0.645383] EISA bus registered
[    0.645406] ACPI: bus type pci registered
[    0.646013] PCI: PCI BIOS revision 2.10 entry at 0xfd9c3, last bus=2
[    0.646018] PCI: Using configuration type 1 for base access
[    0.648506] ACPI: EC: Look up EC in DSDT
[    0.653279] ACPI: Interpreter enabled
[    0.653287] ACPI: (supports S0 S3 S4 S5)
[    0.653312] ACPI: Using PIC for interrupt routing
[    0.653787] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.666767] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.666772] ACPI: EC: driver started in interrupt mode
[    0.666865] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.666968] PCI: 0000:00:00.0 reg 10 32bit mmio: [e2000000, e3ffffff]
[    0.667090] PCI: 0000:00:1d.0 reg 20 io port: [1800, 181f]
[    0.667148] PCI: 0000:00:1d.1 reg 20 io port: [1820, 183f]
[    0.667207] PCI: 0000:00:1d.2 reg 20 io port: [1840, 185f]
[    0.667272] PCI: 0000:00:1d.7 reg 10 32bit mmio: [d0000000, d00003ff]
[    0.667330] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.667337] pci 0000:00:1d.7: PME# disabled
[    0.667420] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.667429] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.667435] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.667458] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.667467] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.667476] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.667485] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.667494] PCI: 0000:00:1f.1 reg 20 io port: [1860, 186f]
[    0.667503] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.667558] PCI: 0000:00:1f.3 reg 20 io port: [1880, 189f]
[    0.667605] PCI: 0000:00:1f.5 reg 10 io port: [1c00, 1cff]
[    0.667614] PCI: 0000:00:1f.5 reg 14 io port: [18c0, 18ff]
[    0.667623] PCI: 0000:00:1f.5 reg 18 32bit mmio: [d0000c00, d0000dff]
[    0.667632] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [d0000800, d00008ff]
[    0.667662] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.667669] pci 0000:00:1f.5: PME# disabled
[    0.667698] PCI: 0000:00:1f.6 reg 10 io port: [2400, 24ff]
[    0.667707] PCI: 0000:00:1f.6 reg 14 io port: [2000, 207f]
[    0.667746] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.667752] pci 0000:00:1f.6: PME# disabled
[    0.667790] PCI: 0000:01:00.0 reg 10 32bit mmio: [d8000000, d8ffffff]
[    0.667798] PCI: 0000:01:00.0 reg 14 32bit mmio: [f0000000, f3ffffff]
[    0.667806] PCI: 0000:01:00.0 reg 18 32bit mmio: [e8000000, e807ffff]
[    0.667825] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.667875] PCI: bridge 0000:00:01.0 32bit mmio: [d8000000, dfffffff]
[    0.667881] PCI: bridge 0000:00:01.0 32bit mmio pref: [e8000000, f7ffffff]
[    0.667926] PCI: 0000:02:05.0 reg 10 32bit mmio: [e0000000, e000ffff]
[    0.668001] PCI: 0000:02:06.0 reg 10 32bit mmio: [e0012000, e0012fff]
[    0.668019] pci 0000:02:06.0: supports D1
[    0.668043] pci 0000:02:06.0: supports D2
[    0.668047] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.668054] pci 0000:02:06.0: PME# disabled
[    0.668086] PCI: 0000:02:06.1 reg 10 32bit mmio: [e0013000, e0013fff]
[    0.668104] pci 0000:02:06.1: supports D1
[    0.668107] pci 0000:02:06.1: supports D2
[    0.668111] pci 0000:02:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.668117] pci 0000:02:06.1: PME# disabled
[    0.668146] PCI: 0000:02:06.2 reg 10 io port: [4000, 403f]
[    0.668223] PCI: 0000:02:07.0 reg 10 32bit mmio: [e0010000, e0011fff]
[    0.668254] PCI: 0000:02:07.0 reg 30 32bit mmio: [0, 3fff]
[    0.668270] pci 0000:02:07.0: supports D1
[    0.668273] pci 0000:02:07.0: supports D2
[    0.668277] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.668283] pci 0000:02:07.0: PME# disabled
[    0.668317] pci 0000:00:1e.0: transparent bridge
[    0.668323] PCI: bridge 0000:00:1e.0 io port: [3000, 4fff]
[    0.668330] PCI: bridge 0000:00:1e.0 32bit mmio: [e0000000, e05fffff]
[    0.668379] bus 00 -> node 0
[    0.668390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.668838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.668999] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.676723] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[    0.676902] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.677078] ACPI: PCI Interrupt Link [LNKC] (IRQs 12) *11
[    0.677254] ACPI: PCI Interrupt Link [LNKD] (IRQs 15) *10
[    0.677429] ACPI: PCI Interrupt Link [LNKE] (IRQs 9 10 11 12 15) *0, disabled.
[    0.677610] ACPI: PCI Interrupt Link [LNKF] (IRQs 9 10 11 12 15) *0, disabled.
[    0.677790] ACPI: PCI Interrupt Link [LNKG] (IRQs 9 10 11 12 15) *0, disabled.
[    0.677976] ACPI: PCI Interrupt Link [LNKH] (IRQs 9 *10 11 12 15)
[    0.678240] ACPI: Power Resource [LRP0] (off)
[    0.678316] ACPI: Power Resource [LRP1] (off)
[    0.678390] ACPI: Power Resource [LRP2] (off)
[    0.678492] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.678550] pnp: PnP ACPI init
[    0.678561] ACPI: bus type pnp registered
[    0.682941] pnp: PnP ACPI: found 8 devices
[    0.682946] ACPI: ACPI bus type pnp unregistered
[    0.682951] PnPBIOS: Disabled by ACPI PNP
[    0.683487] PCI: Using ACPI for IRQ routing
[    0.683649] NET: Registered protocol family 8
[    0.683649] NET: Registered protocol family 20
[    0.683649] NetLabel: Initializing
[    0.683649] NetLabel:  domain hash size = 128
[    0.683649] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.683649] NetLabel:  unlabeled traffic allowed by default
[    0.684287] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.684292]    actual entries 65620
[    0.684428] AppArmor: AppArmor Filesystem Enabled
[    0.684447] ACPI: RTC can wake from S4
[    0.684502] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.684508] system 00:04: ioport range 0x700-0x70f has been reserved
[    0.684513] system 00:04: ioport range 0x800-0x807 has been reserved
[    0.684518] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.684524] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.684529] system 00:04: ioport range 0xfe00-0xfe7f has been reserved
[    0.684534] system 00:04: ioport range 0xfe80-0xfeff has been reserved
[    0.684541] system 00:04: iomem range 0xfebfe000-0xfebfefff has been reserved
[    0.684546] system 00:04: iomem range 0xfebff000-0xfebfffff has been reserved
[    0.684552] system 00:04: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.719934] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.719939] pci 0000:00:01.0:   IO window: disabled
[    0.719946] pci 0000:00:01.0:   MEM window: 0xd8000000-0xdfffffff
[    0.719952] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000f7ffffff
[    0.719967] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.719972] pci 0000:02:06.0:   IO window: 0x003000-0x0030ff
[    0.719978] pci 0000:02:06.0:   IO window: 0x003400-0x0034ff
[    0.719985] pci 0000:02:06.0:   PREFETCH window: 0x70000000-0x73ffffff
[    0.719992] pci 0000:02:06.0:   MEM window: 0x7c000000-0x7fffffff
[    0.719998] pci 0000:02:06.1: CardBus bridge, secondary bus 0000:07
[    0.720002] pci 0000:02:06.1:   IO window: 0x003800-0x0038ff
[    0.720009] pci 0000:02:06.1:   IO window: 0x003c00-0x003cff
[    0.720015] pci 0000:02:06.1:   PREFETCH window: 0x74000000-0x77ffffff
[    0.720022] pci 0000:02:06.1:   MEM window: 0x80000000-0x83ffffff
[    0.720040] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.720045] pci 0000:00:1e.0:   IO window: 0x3000-0x4fff
[    0.720053] pci 0000:00:1e.0:   MEM window: 0xe0000000-0xe05fffff
[    0.720060] pci 0000:00:1e.0:   PREFETCH window: 0x00000070000000-0x00000079ffffff
[    0.720081] pci 0000:00:1e.0: setting latency timer to 64
[    0.720092] pci 0000:02:06.0: enabling device (0006 -> 0007)
[    0.720382] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.720387] PCI: setting IRQ 11 as level-triggered
[    0.720394] pci 0000:02:06.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.720407] pci 0000:02:06.1: enabling device (0006 -> 0007)
[    0.720675] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.720679] PCI: setting IRQ 10 as level-triggered
[    0.720686] pci 0000:02:06.1: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.720695] bus: 00 index 0 io port: [0, ffff]
[    0.720699] bus: 00 index 1 mmio: [0, ffffffff]
[    0.720703] bus: 01 index 0 mmio: [0, 0]
[    0.720706] bus: 01 index 1 mmio: [d8000000, dfffffff]
[    0.720710] bus: 01 index 2 mmio: [e8000000, f7ffffff]
[    0.720714] bus: 01 index 3 mmio: [0, 0]
[    0.720718] bus: 02 index 0 io port: [3000, 4fff]
[    0.720722] bus: 02 index 1 mmio: [e0000000, e05fffff]
[    0.720726] bus: 02 index 2 mmio: [70000000, 79ffffff]
[    0.720730] bus: 02 index 3 io port: [0, ffff]
[    0.720734] bus: 02 index 4 mmio: [0, ffffffff]
[    0.720737] bus: 03 index 0 io port: [3000, 30ff]
[    0.720741] bus: 03 index 1 io port: [3400, 34ff]
[    0.720745] bus: 03 index 2 mmio: [70000000, 73ffffff]
[    0.720749] bus: 03 index 3 mmio: [7c000000, 7fffffff]
[    0.720753] bus: 07 index 0 io port: [3800, 38ff]
[    0.720757] bus: 07 index 1 io port: [3c00, 3cff]
[    0.720761] bus: 07 index 2 mmio: [74000000, 77ffffff]
[    0.720765] bus: 07 index 3 mmio: [80000000, 83ffffff]
[    0.720778] NET: Registered protocol family 2
[    0.720971] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.721362] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.722340] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.722970] TCP: Hash tables configured (established 131072 bind 65536)
[    0.722976] TCP reno registered
[    0.723157] NET: Registered protocol family 1
[    0.723357] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.565032]  it is
[    2.218321] Freeing initrd memory: 8011k freed
[    2.218615] Simple Boot Flag at 0x36 set to 0x1
[    2.219248] audit: initializing netlink socket (disabled)
[    2.219275] type=2000 audit(1233825083.216:1): initialized
[    2.230481] highmem bounce pool size: 64 pages
[    2.230492] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.234385] VFS: Disk quotas dquot_6.5.1
[    2.234528] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.234700] msgmni has been set to 1752
[    2.234905] io scheduler noop registered
[    2.234910] io scheduler anticipatory registered
[    2.234914] io scheduler deadline registered
[    2.234935] io scheduler cfq registered (default)
[    2.235046] pci 0000:01:00.0: Boot video device
[    2.235582] isapnp: Scanning for PnP cards...
[    2.589358] isapnp: No Plug & Play device found
[    2.645665] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.645940] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    2.648395] serial 00:06: activated
[    2.648705] 00:06: ttyS0 at I/O 0x300 (irq = 4) is a 16550A
[    2.648963] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    2.648974] serial 0000:00:1f.6: PCI INT B disabled
[    2.651406] brd: module loaded
[    2.651520] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.651788] PNP: No PS/2 controller found. Probing ports directly.
[    2.654764] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.656264] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.656272] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.656277] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.656281] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.656286] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.656921] mice: PS/2 mouse device common for all mice
[    2.657124] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.657145] rtc0: alarms up to one month, y3k
[    2.657340] EISA: Probing bus 0 at eisa.0
[    2.657350] Cannot allocate resource for EISA slot 1
[    2.657355] Cannot allocate resource for EISA slot 2
[    2.657359] Cannot allocate resource for EISA slot 3
[    2.657363] Cannot allocate resource for EISA slot 4
[    2.657385] EISA: Detected 0 cards.
[    2.657391] cpuidle: using governor ladder
[    2.657395] cpuidle: using governor menu
[    2.658238] TCP cubic registered
[    2.658282] Using IPI No-Shortcut mode
[    2.658575] registered taskstats version 1
[    2.658754]   Magic number: 13:916:170
[    2.658913] rtc_cmos 00:01: setting system clock to 2009-02-05 09:11:24 UTC (1233825084)
[    2.658918] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.658922] EDD information not available.
[    2.659299] Freeing unused kernel memory: 424k freed
[    2.659381] Write protecting the kernel text: 2580k
[    2.659430] Write protecting the kernel read-only data: 940k
[    2.665495] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.004067] fuse init (API version 7.9)
[    3.220307] ACPI: Transitioning device [FAN0] to D3
[    3.228048] fan PNP0C0B:00: registered as cooling_device0
[    3.228059] ACPI: Fan [FAN0] (off)
[    3.228198] ACPI: Transitioning device [FAN1] to D3
[    3.234917] fan PNP0C0B:01: registered as cooling_device1
[    3.234927] ACPI: Fan [FAN1] (off)
[    3.235065] ACPI: Transitioning device [FAN2] to D3
[    3.235132] fan PNP0C0B:02: registered as cooling_device2
[    3.235142] ACPI: Fan [FAN2] (off)
[    3.250051] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.250127] processor ACPI0007:00: registered as cooling_device3
[    3.250134] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.254297] Marking TSC unstable due to TSC halts in idle
[    3.255591] thermal LNXTHERM:01: registered as thermal_zone0
[    3.256748] ACPI: Thermal Zone [THRM] (50 C)
[    4.436126] usbcore: registered new interface driver usbfs
[    4.436167] usbcore: registered new interface driver hub
[    4.456260] No dock devices found.
[    4.496398] usbcore: registered new device driver usb
[    4.569703] SCSI subsystem initialized
[    4.570155] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    4.570163] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    4.570182] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.570188] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.570258] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.574169] ehci_hcd 0000:00:1d.7: debug port 1
[    4.574179] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.574191] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xd0000000
[    4.588032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.588283] usb usb1: configuration #1 chosen from 1 choice
[    4.588329] hub 1-0:1.0: USB hub found
[    4.588341] hub 1-0:1.0: 6 ports detected
[    4.600146] USB Universal Host Controller Interface driver v3.0
[    4.744071] libata version 3.00 loaded.
[    4.796412] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.796427] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.796434] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.796485] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.796518] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    4.796672] usb usb2: configuration #1 chosen from 1 choice
[    4.796719] hub 2-0:1.0: USB hub found
[    4.796731] hub 2-0:1.0: 2 ports detected
[    5.004701] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 15
[    5.004708] PCI: setting IRQ 15 as level-triggered
[    5.004715] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 15 (level, low) -> IRQ 15
[    5.004728] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.004733] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.004782] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    5.004814] uhci_hcd 0000:00:1d.1: irq 15, io base 0x00001820
[    5.004971] usb usb3: configuration #1 chosen from 1 choice
[    5.005016] hub 3-0:1.0: USB hub found
[    5.005028] hub 3-0:1.0: 2 ports detected
[    5.108661] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
[    5.108667] PCI: setting IRQ 12 as level-triggered
[    5.108674] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[    5.108686] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.108692] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.108737] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    5.108766] uhci_hcd 0000:00:1d.2: irq 12, io base 0x00001840
[    5.108915] usb usb4: configuration #1 chosen from 1 choice
[    5.108960] hub 4-0:1.0: USB hub found
[    5.108972] hub 4-0:1.0: 2 ports detected
[    5.116040] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    5.293690] usb 2-2: configuration #1 chosen from 1 choice
[    5.316655] ata_piix 0000:00:1f.1: version 2.12
[    5.316671] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    5.316684] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[    5.316742] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.316850] scsi0 : ata_piix
[    5.316996] scsi1 : ata_piix
[    5.317955] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    5.317960] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    5.428047] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    5.480513] ata1.00: ATA-6: TOSHIBA MK4025GAS, KA101A, max UDMA/100
[    5.480519] ata1.00: 78140160 sectors, multi 16: LBA 
[    5.488414] ata1.00: configured for UDMA/100
[    5.488465] ata2: port disabled. ignoring.
[    5.488623] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4025GA KA10 PQ: 0 ANSI: 5
[    5.495516] b44 0000:02:07.0: PCI INT A -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[    5.552112] ssb: Sonics Silicon Backplane found on PCI device 0000:02:07.0
[    5.552151] b44.c:v2.0
[    5.572546] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:11:85:5e:36:cd
[    5.658280] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.660859] usb 4-2: configuration #1 chosen from 1 choice
[    5.665315] usbcore: registered new interface driver hiddev
[    5.680627] input: Jing-Mold USB K/B+Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input2
[    5.681515] Driver 'sd' needs updating - please use bus_type methods
[    5.681655] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    5.681683] sd 0:0:0:0: [sda] Write Protect is off
[    5.681688] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.681730] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.681830] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    5.681855] sd 0:0:0:0: [sda] Write Protect is off
[    5.681860] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.681903] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.681909]  sda:<6>input,hidraw0: USB HID v1.10 Keyboard [Jing-Mold USB K/B+Mouse] on usb-0000:00:1d.0-2
[    5.696683]  sda1 sda2 <<6>input: Jing-Mold USB K/B+Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input3
[    5.721826]  sda5<6>input,hidraw1: USB HID v1.10 Mouse [Jing-Mold USB K/B+Mouse] on usb-0000:00:1d.0-2
[    5.740309] usbcore: registered new interface driver usbhid
[    5.740316] usbhid: v2.6:USB HID core driver
[    5.751159]  sda6 >
[    5.751414] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.246322] PM: Starting manual resume from disk
[    6.246329] PM: Resume from partition 8:6
[    6.246332] PM: Checking hibernation image.
[    6.246593] PM: Resume from disk failed.
[    6.332126] kjournald starting.  Commit interval 5 seconds
[    6.332144] EXT3-fs: mounted filesystem with ordered data mode.
[   15.280421] udevd version 124 started
[   16.707023] Linux agpgart interface v0.103
[   16.796260] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.861868] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.917686] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   16.921342] agpgart-intel 0000:00:00.0: AGP aperture is 32M @ 0xe2000000
[   16.980189] iTCO_vendor_support: vendor-support=0
[   17.040175] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   17.040321] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   17.040505] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.184270] intel_rng: FWH not detected
[   17.766424] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   17.776040] ACPI: Power Button (FF) [PWRF]
[   17.776166] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   17.788040] ACPI: Power Button (CM) [PWRB]
[   17.803249] ACPI: AC Adapter [AC] (on-line)
[   17.940553] ACPI: Battery Slot [CMB0] (battery present)
[   17.984671] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   17.996853] ACPI: WMI: Mapper loaded
[   18.886258] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/input/input7
[   18.896036] ACPI: Video Device [AGPB] (multi-head: yes  rom: no  post: no)
[   19.276207] irda_init()
[   19.276230] NET: Registered protocol family 23
[   19.484250] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   19.484290] nsc-ircc, chip->init
[   19.484301] nsc-ircc, Found chip at base=0x04e
[   19.484329] nsc-ircc, driver loaded (Dag Brattli)
[   19.484338] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.484369] nsc-ircc, Found chip at base=0x04e
[   19.484396] nsc-ircc, driver loaded (Dag Brattli)
[   19.484401] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.484698] nsc-ircc 00:07: disabled
[   20.628567] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   20.628597] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   21.066917] nvidia: module license 'NVIDIA' taints kernel.
[   21.445810] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   21.520746] wlan: 0.9.4
[   21.547003] ath_pci: 0.9.4
[   21.552034] intel8x0_measure_ac97_clock: measured 55372 usecs
[   21.552039] intel8x0: clocking to 48000
[   21.553816] nvidia 0000:01:00.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   21.554064] Yenta: CardBus bridge found at 0000:02:06.0 [103c:08b0]
[   21.554085] Yenta: Using CSCINT to route CSC interrupts to PCI
[   21.554089] Yenta: Routing CardBus interrupts to PCI
[   21.554096] Yenta TI: socket 0000:02:06.0, mfunc 0x00001022, devctl 0x64
[   21.554131] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.09  Mon Oct 27 14:23:30 PST 2008
[   21.784610] Yenta: ISA IRQ mask 0x00f8, PCI irq 11
[   21.784617] Socket status: 30000086
[   21.784622] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   21.784632] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x4fff
[   21.784637] cs: IO port probe 0x3000-0x4fff: clean.
[   21.785424] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe05fffff
[   21.785430] pcmcia: parent PCI bridge Memory window: 0x70000000 - 0x79ffffff
[   21.820292] ath_pci 0000:02:05.0: PCI INT A -> Link[LNKD] -> GSI 15 (level, low) -> IRQ 15
[   23.064195] Bluetooth: Core ver 2.13
[   23.064571] NET: Registered protocol family 31
[   23.064575] Bluetooth: HCI device and connection manager initialized
[   23.064581] Bluetooth: HCI socket layer initialized
[   23.103466] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   23.103622] usbcore: registered new interface driver btusb
[   23.559116] ath_rate_sample: 1.2 (0.9.4)
[   23.559867] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   23.559882] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   23.559891] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   23.559909] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   23.559923] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   23.559931] wifi0: mac 5.6 phy 4.1 5 GHz radio 1.7 2 GHz radio 2.3
[   23.559940] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   23.559944] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   23.559947] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   23.559951] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   23.559955] wifi0: Use hw queue 8 for CAB traffic
[   23.559958] wifi0: Use hw queue 9 for beacons
[   23.600172] wifi0: Atheros 5212: mem=0xe0000000, irq=15
[   23.600209] Yenta: CardBus bridge found at 0000:02:06.1 [103c:08b0]
[   23.600230] Yenta: Using CSCINT to route CSC interrupts to PCI
[   23.600234] Yenta: Routing CardBus interrupts to PCI
[   23.600242] Yenta TI: socket 0000:02:06.1, mfunc 0x00001022, devctl 0x64
[   23.832676] Yenta: ISA IRQ mask 0x00f8, PCI irq 10
[   23.832683] Socket status: 30000084
[   23.832688] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   23.832698] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x4fff
[   23.832703] cs: IO port probe 0x3000-0x4fff: clean.
[   23.833490] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe05fffff
[   23.833495] pcmcia: parent PCI bridge Memory window: 0x70000000 - 0x79ffffff
[   25.796130] cs: IO port probe 0x100-0x3af: clean.
[   25.797975] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.798789] cs: IO port probe 0x820-0x8ff: clean.
[   25.799467] cs: IO port probe 0xc00-0xcf7: clean.
[   25.800403] cs: IO port probe 0xa00-0xaff: clean.
[   25.834773] cs: IO port probe 0x100-0x3af: clean.
[   25.836646] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.837459] cs: IO port probe 0x820-0x8ff: clean.
[   25.838137] cs: IO port probe 0xc00-0xcf7: clean.
[   25.839044] cs: IO port probe 0xa00-0xaff: clean.
[   26.369269] lp: driver loaded but no devices found
[   26.758032] Adding 1220900k swap on /dev/sda6.  Priority:-1 extents:1 across:1220900k
[   27.424687] EXT3 FS on sda5, internal journal
[   28.710277] type=1505 audit(1233843110.573:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3983
[   29.053590] type=1505 audit(1233843110.917:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3988
[   29.053992] type=1505 audit(1233843110.917:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3988
[   29.256955] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.784984] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   31.866548] apm: BIOS not found.
[   32.107408] ppdev: user-space parallel port driver
[   34.716027] Clocksource tsc unstable (delta = -199680952 ns)
[   35.282791] ttyS1: LSR safety check engaged!
[   35.506672] Bluetooth: L2CAP ver 2.11
[   35.506680] Bluetooth: L2CAP socket layer initialized
[   35.560647] Bluetooth: SCO (Voice Link) ver 0.6
[   35.560660] Bluetooth: SCO socket layer initialized
[   35.604222] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.604235] Bluetooth: BNEP filters: protocol multicast
[   35.652726] Bluetooth: RFCOMM socket layer initialized
[   35.653055] Bluetooth: RFCOMM TTY layer initialized
[   35.653061] Bluetooth: RFCOMM ver 1.10
[   35.676374] Bridge firewalling registered
[   40.613733] NET: Registered protocol family 17
[   75.124994] spurious 8259A interrupt: IRQ7.
[  109.660759] NET: Registered protocol family 10
[  109.663379] lo: Disabled Privacy Extensions
[  109.665810] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  120.244045] ath0: no IPv6 routers present
[  164.082223] ttyS1: LSR safety check engaged!
[  164.082256] type=1503 audit(1233843245.945:5): operation="capable" name="sys_admin" pid=5912 profile="/usr/sbin/cupsd"
ken

---

### Post by kdub on 2009-02-05
Spider,
I did the command and got this:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005ff70000 (usable)
[    0.000000]  BIOS-e820: 000000005ff70000 - 000000005ff7c000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005ff7c000 - 000000005ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005ff80000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffff000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x5ff70 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781d000 - 37fefc95
[    0.000000] ACPI: RSDP 000F6500, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 5FF77A1D, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 5FF7BED2, 0074 (r1 HP     08B0      6040000 PTL        50)
[    0.000000] ACPI: DSDT 5FF77E73, 405F (r1 HP     08B0      6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 5FF7CFC0, 0040
[    0.000000] ACPI: BOOT 5FF7BFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 5FF77A4D, 018A (r1  INTEL  EISTRef     2000 INTL 20021002)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781d000 - 0037fefc95]          RAMDISK ==> [003781d000 - 0037fefc95]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0005ff70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005ff70
[    0.000000] On node 0 totalpages: 392975
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 162257 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01d87000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9f800000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389520
[    0.000000] Kernel command line: root=UUID=d527a13f-5f02-460b-8d26-dfb5e3f7b555 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1096.435 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1543380k/1572288k available (2576k kernel code, 27624k reserved, 1165k data, 424k init, 654784k highmem)
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
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004020] Calibrating delay loop (skipped), value calculated using timer frequency.. 2192.87 BogoMIPS (lpj=4385740)
[    0.004056] Security Framework initialized
[    0.004075] SELinux:  Disabled at boot.
[    0.004115] AppArmor: AppArmor initialized
[    0.004130] Mount-cache hash table entries: 512
[    0.004428] Initializing cgroup subsys ns
[    0.004439] Initializing cgroup subsys cpuacct
[    0.004443] Initializing cgroup subsys memory
[    0.004471] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004476] CPU: L2 cache: 2048K
[    0.004499] Checking 'hlt' instruction... OK.
[    0.020754] SMP alternatives: switching to UP code
[    0.028015] Freeing SMP alternatives: 11k freed
[    0.028020] ACPI: Core revision 20080609
[    0.032198] ACPI: Checking initramfs for custom DSDT
[    0.642529] ACPI: setting ELCR to 0200 (from 0c00)
[    0.644072] weird, boot CPU (#0) not listedby the BIOS.
[    0.644076] SMP motherboard not detected.
[    0.644081] Local APIC not detected. Using dummy APIC emulation.
[    0.644085] SMP disabled
[    0.644179] Brought up 1 CPUs
[    0.644183] Total of 1 processors activated (2192.87 BogoMIPS).
[    0.644202] CPU0 attaching NULL sched-domain.
[    0.644539] net_namespace: 840 bytes
[    0.644558] Booting paravirtualized kernel on bare hardware
[    0.644872] Time:  9:11:22  Date: 02/05/09
[    0.644912] NET: Registered protocol family 16
[    0.645383] EISA bus registered
[    0.645406] ACPI: bus type pci registered
[    0.646013] PCI: PCI BIOS revision 2.10 entry at 0xfd9c3, last bus=2
[    0.646018] PCI: Using configuration type 1 for base access
[    0.648506] ACPI: EC: Look up EC in DSDT
[    0.653279] ACPI: Interpreter enabled
[    0.653287] ACPI: (supports S0 S3 S4 S5)
[    0.653312] ACPI: Using PIC for interrupt routing
[    0.653787] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.666767] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.666772] ACPI: EC: driver started in interrupt mode
[    0.666865] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.666968] PCI: 0000:00:00.0 reg 10 32bit mmio: [e2000000, e3ffffff]
[    0.667090] PCI: 0000:00:1d.0 reg 20 io port: [1800, 181f]
[    0.667148] PCI: 0000:00:1d.1 reg 20 io port: [1820, 183f]
[    0.667207] PCI: 0000:00:1d.2 reg 20 io port: [1840, 185f]
[    0.667272] PCI: 0000:00:1d.7 reg 10 32bit mmio: [d0000000, d00003ff]
[    0.667330] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.667337] pci 0000:00:1d.7: PME# disabled
[    0.667420] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.667429] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.667435] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.667458] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.667467] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.667476] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.667485] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.667494] PCI: 0000:00:1f.1 reg 20 io port: [1860, 186f]
[    0.667503] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.667558] PCI: 0000:00:1f.3 reg 20 io port: [1880, 189f]
[    0.667605] PCI: 0000:00:1f.5 reg 10 io port: [1c00, 1cff]
[    0.667614] PCI: 0000:00:1f.5 reg 14 io port: [18c0, 18ff]
[    0.667623] PCI: 0000:00:1f.5 reg 18 32bit mmio: [d0000c00, d0000dff]
[    0.667632] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [d0000800, d00008ff]
[    0.667662] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.667669] pci 0000:00:1f.5: PME# disabled
[    0.667698] PCI: 0000:00:1f.6 reg 10 io port: [2400, 24ff]
[    0.667707] PCI: 0000:00:1f.6 reg 14 io port: [2000, 207f]
[    0.667746] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.667752] pci 0000:00:1f.6: PME# disabled
[    0.667790] PCI: 0000:01:00.0 reg 10 32bit mmio: [d8000000, d8ffffff]
[    0.667798] PCI: 0000:01:00.0 reg 14 32bit mmio: [f0000000, f3ffffff]
[    0.667806] PCI: 0000:01:00.0 reg 18 32bit mmio: [e8000000, e807ffff]
[    0.667825] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.667875] PCI: bridge 0000:00:01.0 32bit mmio: [d8000000, dfffffff]
[    0.667881] PCI: bridge 0000:00:01.0 32bit mmio pref: [e8000000, f7ffffff]
[    0.667926] PCI: 0000:02:05.0 reg 10 32bit mmio: [e0000000, e000ffff]
[    0.668001] PCI: 0000:02:06.0 reg 10 32bit mmio: [e0012000, e0012fff]
[    0.668019] pci 0000:02:06.0: supports D1
[    0.668043] pci 0000:02:06.0: supports D2
[    0.668047] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.668054] pci 0000:02:06.0: PME# disabled
[    0.668086] PCI: 0000:02:06.1 reg 10 32bit mmio: [e0013000, e0013fff]
[    0.668104] pci 0000:02:06.1: supports D1
[    0.668107] pci 0000:02:06.1: supports D2
[    0.668111] pci 0000:02:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.668117] pci 0000:02:06.1: PME# disabled
[    0.668146] PCI: 0000:02:06.2 reg 10 io port: [4000, 403f]
[    0.668223] PCI: 0000:02:07.0 reg 10 32bit mmio: [e0010000, e0011fff]
[    0.668254] PCI: 0000:02:07.0 reg 30 32bit mmio: [0, 3fff]
[    0.668270] pci 0000:02:07.0: supports D1
[    0.668273] pci 0000:02:07.0: supports D2
[    0.668277] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.668283] pci 0000:02:07.0: PME# disabled
[    0.668317] pci 0000:00:1e.0: transparent bridge
[    0.668323] PCI: bridge 0000:00:1e.0 io port: [3000, 4fff]
[    0.668330] PCI: bridge 0000:00:1e.0 32bit mmio: [e0000000, e05fffff]
[    0.668379] bus 00 -> node 0
[    0.668390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.668838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.668999] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.676723] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[    0.676902] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.677078] ACPI: PCI Interrupt Link [LNKC] (IRQs 12) *11
[    0.677254] ACPI: PCI Interrupt Link [LNKD] (IRQs 15) *10
[    0.677429] ACPI: PCI Interrupt Link [LNKE] (IRQs 9 10 11 12 15) *0, disabled.
[    0.677610] ACPI: PCI Interrupt Link [LNKF] (IRQs 9 10 11 12 15) *0, disabled.
[    0.677790] ACPI: PCI Interrupt Link [LNKG] (IRQs 9 10 11 12 15) *0, disabled.
[    0.677976] ACPI: PCI Interrupt Link [LNKH] (IRQs 9 *10 11 12 15)
[    0.678240] ACPI: Power Resource [LRP0] (off)
[    0.678316] ACPI: Power Resource [LRP1] (off)
[    0.678390] ACPI: Power Resource [LRP2] (off)
[    0.678492] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.678550] pnp: PnP ACPI init
[    0.678561] ACPI: bus type pnp registered
[    0.682941] pnp: PnP ACPI: found 8 devices
[    0.682946] ACPI: ACPI bus type pnp unregistered
[    0.682951] PnPBIOS: Disabled by ACPI PNP
[    0.683487] PCI: Using ACPI for IRQ routing
[    0.683649] NET: Registered protocol family 8
[    0.683649] NET: Registered protocol family 20
[    0.683649] NetLabel: Initializing
[    0.683649] NetLabel:  domain hash size = 128
[    0.683649] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.683649] NetLabel:  unlabeled traffic allowed by default
[    0.684287] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.684292]    actual entries 65620
[    0.684428] AppArmor: AppArmor Filesystem Enabled
[    0.684447] ACPI: RTC can wake from S4
[    0.684502] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.684508] system 00:04: ioport range 0x700-0x70f has been reserved
[    0.684513] system 00:04: ioport range 0x800-0x807 has been reserved
[    0.684518] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.684524] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.684529] system 00:04: ioport range 0xfe00-0xfe7f has been reserved
[    0.684534] system 00:04: ioport range 0xfe80-0xfeff has been reserved
[    0.684541] system 00:04: iomem range 0xfebfe000-0xfebfefff has been reserved
[    0.684546] system 00:04: iomem range 0xfebff000-0xfebfffff has been reserved
[    0.684552] system 00:04: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.719934] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.719939] pci 0000:00:01.0:   IO window: disabled
[    0.719946] pci 0000:00:01.0:   MEM window: 0xd8000000-0xdfffffff
[    0.719952] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000f7ffffff
[    0.719967] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.719972] pci 0000:02:06.0:   IO window: 0x003000-0x0030ff
[    0.719978] pci 0000:02:06.0:   IO window: 0x003400-0x0034ff
[    0.719985] pci 0000:02:06.0:   PREFETCH window: 0x70000000-0x73ffffff
[    0.719992] pci 0000:02:06.0:   MEM window: 0x7c000000-0x7fffffff
[    0.719998] pci 0000:02:06.1: CardBus bridge, secondary bus 0000:07
[    0.720002] pci 0000:02:06.1:   IO window: 0x003800-0x0038ff
[    0.720009] pci 0000:02:06.1:   IO window: 0x003c00-0x003cff
[    0.720015] pci 0000:02:06.1:   PREFETCH window: 0x74000000-0x77ffffff
[    0.720022] pci 0000:02:06.1:   MEM window: 0x80000000-0x83ffffff
[    0.720040] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.720045] pci 0000:00:1e.0:   IO window: 0x3000-0x4fff
[    0.720053] pci 0000:00:1e.0:   MEM window: 0xe0000000-0xe05fffff
[    0.720060] pci 0000:00:1e.0:   PREFETCH window: 0x00000070000000-0x00000079ffffff
[    0.720081] pci 0000:00:1e.0: setting latency timer to 64
[    0.720092] pci 0000:02:06.0: enabling device (0006 -> 0007)
[    0.720382] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.720387] PCI: setting IRQ 11 as level-triggered
[    0.720394] pci 0000:02:06.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.720407] pci 0000:02:06.1: enabling device (0006 -> 0007)
[    0.720675] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.720679] PCI: setting IRQ 10 as level-triggered
[    0.720686] pci 0000:02:06.1: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.720695] bus: 00 index 0 io port: [0, ffff]
[    0.720699] bus: 00 index 1 mmio: [0, ffffffff]
[    0.720703] bus: 01 index 0 mmio: [0, 0]
[    0.720706] bus: 01 index 1 mmio: [d8000000, dfffffff]
[    0.720710] bus: 01 index 2 mmio: [e8000000, f7ffffff]
[    0.720714] bus: 01 index 3 mmio: [0, 0]
[    0.720718] bus: 02 index 0 io port: [3000, 4fff]
[    0.720722] bus: 02 index 1 mmio: [e0000000, e05fffff]
[    0.720726] bus: 02 index 2 mmio: [70000000, 79ffffff]
[    0.720730] bus: 02 index 3 io port: [0, ffff]
[    0.720734] bus: 02 index 4 mmio: [0, ffffffff]
[    0.720737] bus: 03 index 0 io port: [3000, 30ff]
[    0.720741] bus: 03 index 1 io port: [3400, 34ff]
[    0.720745] bus: 03 index 2 mmio: [70000000, 73ffffff]
[    0.720749] bus: 03 index 3 mmio: [7c000000, 7fffffff]
[    0.720753] bus: 07 index 0 io port: [3800, 38ff]
[    0.720757] bus: 07 index 1 io port: [3c00, 3cff]
[    0.720761] bus: 07 index 2 mmio: [74000000, 77ffffff]
[    0.720765] bus: 07 index 3 mmio: [80000000, 83ffffff]
[    0.720778] NET: Registered protocol family 2
[    0.720971] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.721362] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.722340] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.722970] TCP: Hash tables configured (established 131072 bind 65536)
[    0.722976] TCP reno registered
[    0.723157] NET: Registered protocol family 1
[    0.723357] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.565032]  it is
[    2.218321] Freeing initrd memory: 8011k freed
[    2.218615] Simple Boot Flag at 0x36 set to 0x1
[    2.219248] audit: initializing netlink socket (disabled)
[    2.219275] type=2000 audit(1233825083.216:1): initialized
[    2.230481] highmem bounce pool size: 64 pages
[    2.230492] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.234385] VFS: Disk quotas dquot_6.5.1
[    2.234528] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.234700] msgmni has been set to 1752
[    2.234905] io scheduler noop registered
[    2.234910] io scheduler anticipatory registered
[    2.234914] io scheduler deadline registered
[    2.234935] io scheduler cfq registered (default)
[    2.235046] pci 0000:01:00.0: Boot video device
[    2.235582] isapnp: Scanning for PnP cards...
[    2.589358] isapnp: No Plug & Play device found
[    2.645665] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.645940] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    2.648395] serial 00:06: activated
[    2.648705] 00:06: ttyS0 at I/O 0x300 (irq = 4) is a 16550A
[    2.648963] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    2.648974] serial 0000:00:1f.6: PCI INT B disabled
[    2.651406] brd: module loaded
[    2.651520] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.651788] PNP: No PS/2 controller found. Probing ports directly.
[    2.654764] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.656264] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.656272] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.656277] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.656281] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.656286] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.656921] mice: PS/2 mouse device common for all mice
[    2.657124] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.657145] rtc0: alarms up to one month, y3k
[    2.657340] EISA: Probing bus 0 at eisa.0
[    2.657350] Cannot allocate resource for EISA slot 1
[    2.657355] Cannot allocate resource for EISA slot 2
[    2.657359] Cannot allocate resource for EISA slot 3
[    2.657363] Cannot allocate resource for EISA slot 4
[    2.657385] EISA: Detected 0 cards.
[    2.657391] cpuidle: using governor ladder
[    2.657395] cpuidle: using governor menu
[    2.658238] TCP cubic registered
[    2.658282] Using IPI No-Shortcut mode
[    2.658575] registered taskstats version 1
[    2.658754]   Magic number: 13:916:170
[    2.658913] rtc_cmos 00:01: setting system clock to 2009-02-05 09:11:24 UTC (1233825084)
[    2.658918] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.658922] EDD information not available.
[    2.659299] Freeing unused kernel memory: 424k freed
[    2.659381] Write protecting the kernel text: 2580k
[    2.659430] Write protecting the kernel read-only data: 940k
[    2.665495] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.004067] fuse init (API version 7.9)
[    3.220307] ACPI: Transitioning device [FAN0] to D3
[    3.228048] fan PNP0C0B:00: registered as cooling_device0
[    3.228059] ACPI: Fan [FAN0] (off)
[    3.228198] ACPI: Transitioning device [FAN1] to D3
[    3.234917] fan PNP0C0B:01: registered as cooling_device1
[    3.234927] ACPI: Fan [FAN1] (off)
[    3.235065] ACPI: Transitioning device [FAN2] to D3
[    3.235132] fan PNP0C0B:02: registered as cooling_device2
[    3.235142] ACPI: Fan [FAN2] (off)
[    3.250051] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.250127] processor ACPI0007:00: registered as cooling_device3
[    3.250134] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.254297] Marking TSC unstable due to TSC halts in idle
[    3.255591] thermal LNXTHERM:01: registered as thermal_zone0
[    3.256748] ACPI: Thermal Zone [THRM] (50 C)
[    4.436126] usbcore: registered new interface driver usbfs
[    4.436167] usbcore: registered new interface driver hub
[    4.456260] No dock devices found.
[    4.496398] usbcore: registered new device driver usb
[    4.569703] SCSI subsystem initialized
[    4.570155] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    4.570163] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    4.570182] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.570188] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.570258] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.574169] ehci_hcd 0000:00:1d.7: debug port 1
[    4.574179] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.574191] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xd0000000
[    4.588032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.588283] usb usb1: configuration #1 chosen from 1 choice
[    4.588329] hub 1-0:1.0: USB hub found
[    4.588341] hub 1-0:1.0: 6 ports detected
[    4.600146] USB Universal Host Controller Interface driver v3.0
[    4.744071] libata version 3.00 loaded.
[    4.796412] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.796427] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.796434] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.796485] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.796518] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    4.796672] usb usb2: configuration #1 chosen from 1 choice
[    4.796719] hub 2-0:1.0: USB hub found
[    4.796731] hub 2-0:1.0: 2 ports detected
[    5.004701] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 15
[    5.004708] PCI: setting IRQ 15 as level-triggered
[    5.004715] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 15 (level, low) -> IRQ 15
[    5.004728] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.004733] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.004782] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    5.004814] uhci_hcd 0000:00:1d.1: irq 15, io base 0x00001820
[    5.004971] usb usb3: configuration #1 chosen from 1 choice
[    5.005016] hub 3-0:1.0: USB hub found
[    5.005028] hub 3-0:1.0: 2 ports detected
[    5.108661] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
[    5.108667] PCI: setting IRQ 12 as level-triggered
[    5.108674] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[    5.108686] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.108692] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.108737] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    5.108766] uhci_hcd 0000:00:1d.2: irq 12, io base 0x00001840
[    5.108915] usb usb4: configuration #1 chosen from 1 choice
[    5.108960] hub 4-0:1.0: USB hub found
[    5.108972] hub 4-0:1.0: 2 ports detected
[    5.116040] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    5.293690] usb 2-2: configuration #1 chosen from 1 choice
[    5.316655] ata_piix 0000:00:1f.1: version 2.12
[    5.316671] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    5.316684] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[    5.316742] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.316850] scsi0 : ata_piix
[    5.316996] scsi1 : ata_piix
[    5.317955] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    5.317960] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    5.428047] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    5.480513] ata1.00: ATA-6: TOSHIBA MK4025GAS, KA101A, max UDMA/100
[    5.480519] ata1.00: 78140160 sectors, multi 16: LBA 
[    5.488414] ata1.00: configured for UDMA/100
[    5.488465] ata2: port disabled. ignoring.
[    5.488623] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4025GA KA10 PQ: 0 ANSI: 5
[    5.495516] b44 0000:02:07.0: PCI INT A -> Link[LNKC] -> GSI 12 (level, low) -> IRQ 12
[    5.552112] ssb: Sonics Silicon Backplane found on PCI device 0000:02:07.0
[    5.552151] b44.c:v2.0
[    5.572546] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:11:85:5e:36:cd
[    5.658280] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.660859] usb 4-2: configuration #1 chosen from 1 choice
[    5.665315] usbcore: registered new interface driver hiddev
[    5.680627] input: Jing-Mold USB K/B+Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input2
[    5.681515] Driver 'sd' needs updating - please use bus_type methods
[    5.681655] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    5.681683] sd 0:0:0:0: [sda] Write Protect is off
[    5.681688] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.681730] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.681830] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    5.681855] sd 0:0:0:0: [sda] Write Protect is off
[    5.681860] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.681903] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.681909]  sda:<6>input,hidraw0: USB HID v1.10 Keyboard [Jing-Mold USB K/B+Mouse] on usb-0000:00:1d.0-2
[    5.696683]  sda1 sda2 <<6>input: Jing-Mold USB K/B+Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input3
[    5.721826]  sda5<6>input,hidraw1: USB HID v1.10 Mouse [Jing-Mold USB K/B+Mouse] on usb-0000:00:1d.0-2
[    5.740309] usbcore: registered new interface driver usbhid
[    5.740316] usbhid: v2.6:USB HID core driver
[    5.751159]  sda6 >
[    5.751414] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.246322] PM: Starting manual resume from disk
[    6.246329] PM: Resume from partition 8:6
[    6.246332] PM: Checking hibernation image.
[    6.246593] PM: Resume from disk failed.
[    6.332126] kjournald starting.  Commit interval 5 seconds
[    6.332144] EXT3-fs: mounted filesystem with ordered data mode.
[   15.280421] udevd version 124 started
[   16.707023] Linux agpgart interface v0.103
[   16.796260] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.861868] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.917686] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   16.921342] agpgart-intel 0000:00:00.0: AGP aperture is 32M @ 0xe2000000
[   16.980189] iTCO_vendor_support: vendor-support=0
[   17.040175] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   17.040321] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   17.040505] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.184270] intel_rng: FWH not detected
[   17.766424] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   17.776040] ACPI: Power Button (FF) [PWRF]
[   17.776166] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   17.788040] ACPI: Power Button (CM) [PWRB]
[   17.803249] ACPI: AC Adapter [AC] (on-line)
[   17.940553] ACPI: Battery Slot [CMB0] (battery present)
[   17.984671] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   17.996853] ACPI: WMI: Mapper loaded
[   18.886258] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/input/input7
[   18.896036] ACPI: Video Device [AGPB] (multi-head: yes  rom: no  post: no)
[   19.276207] irda_init()
[   19.276230] NET: Registered protocol family 23
[   19.484250] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   19.484290] nsc-ircc, chip->init
[   19.484301] nsc-ircc, Found chip at base=0x04e
[   19.484329] nsc-ircc, driver loaded (Dag Brattli)
[   19.484338] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.484369] nsc-ircc, Found chip at base=0x04e
[   19.484396] nsc-ircc, driver loaded (Dag Brattli)
[   19.484401] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.484698] nsc-ircc 00:07: disabled
[   20.628567] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   20.628597] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   21.066917] nvidia: module license 'NVIDIA' taints kernel.
[   21.445810] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   21.520746] wlan: 0.9.4
[   21.547003] ath_pci: 0.9.4
[   21.552034] intel8x0_measure_ac97_clock: measured 55372 usecs
[   21.552039] intel8x0: clocking to 48000
[   21.553816] nvidia 0000:01:00.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   21.554064] Yenta: CardBus bridge found at 0000:02:06.0 [103c:08b0]
[   21.554085] Yenta: Using CSCINT to route CSC interrupts to PCI
[   21.554089] Yenta: Routing CardBus interrupts to PCI
[   21.554096] Yenta TI: socket 0000:02:06.0, mfunc 0x00001022, devctl 0x64
[   21.554131] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.09  Mon Oct 27 14:23:30 PST 2008
[   21.784610] Yenta: ISA IRQ mask 0x00f8, PCI irq 11
[   21.784617] Socket status: 30000086
[   21.784622] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   21.784632] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x4fff
[   21.784637] cs: IO port probe 0x3000-0x4fff: clean.
[   21.785424] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe05fffff
[   21.785430] pcmcia: parent PCI bridge Memory window: 0x70000000 - 0x79ffffff
[   21.820292] ath_pci 0000:02:05.0: PCI INT A -> Link[LNKD] -> GSI 15 (level, low) -> IRQ 15
[   23.064195] Bluetooth: Core ver 2.13
[   23.064571] NET: Registered protocol family 31
[   23.064575] Bluetooth: HCI device and connection manager initialized
[   23.064581] Bluetooth: HCI socket layer initialized
[   23.103466] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   23.103622] usbcore: registered new interface driver btusb
[   23.559116] ath_rate_sample: 1.2 (0.9.4)
[   23.559867] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   23.559882] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   23.559891] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   23.559909] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   23.559923] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   23.559931] wifi0: mac 5.6 phy 4.1 5 GHz radio 1.7 2 GHz radio 2.3
[   23.559940] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   23.559944] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   23.559947] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   23.559951] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   23.559955] wifi0: Use hw queue 8 for CAB traffic
[   23.559958] wifi0: Use hw queue 9 for beacons
[   23.600172] wifi0: Atheros 5212: mem=0xe0000000, irq=15
[   23.600209] Yenta: CardBus bridge found at 0000:02:06.1 [103c:08b0]
[   23.600230] Yenta: Using CSCINT to route CSC interrupts to PCI
[   23.600234] Yenta: Routing CardBus interrupts to PCI
[   23.600242] Yenta TI: socket 0000:02:06.1, mfunc 0x00001022, devctl 0x64
[   23.832676] Yenta: ISA IRQ mask 0x00f8, PCI irq 10
[   23.832683] Socket status: 30000084
[   23.832688] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   23.832698] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x4fff
[   23.832703] cs: IO port probe 0x3000-0x4fff: clean.
[   23.833490] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe05fffff
[   23.833495] pcmcia: parent PCI bridge Memory window: 0x70000000 - 0x79ffffff
[   25.796130] cs: IO port probe 0x100-0x3af: clean.
[   25.797975] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.798789] cs: IO port probe 0x820-0x8ff: clean.
[   25.799467] cs: IO port probe 0xc00-0xcf7: clean.
[   25.800403] cs: IO port probe 0xa00-0xaff: clean.
[   25.834773] cs: IO port probe 0x100-0x3af: clean.
[   25.836646] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.837459] cs: IO port probe 0x820-0x8ff: clean.
[   25.838137] cs: IO port probe 0xc00-0xcf7: clean.
[   25.839044] cs: IO port probe 0xa00-0xaff: clean.
[   26.369269] lp: driver loaded but no devices found
[   26.758032] Adding 1220900k swap on /dev/sda6.  Priority:-1 extents:1 across:1220900k
[   27.424687] EXT3 FS on sda5, internal journal
[   28.710277] type=1505 audit(1233843110.573:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3983
[   29.053590] type=1505 audit(1233843110.917:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3988
[   29.053992] type=1505 audit(1233843110.917:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3988
[   29.256955] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.784984] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   31.866548] apm: BIOS not found.
[   32.107408] ppdev: user-space parallel port driver
[   34.716027] Clocksource tsc unstable (delta = -199680952 ns)
[   35.282791] ttyS1: LSR safety check engaged!
[   35.506672] Bluetooth: L2CAP ver 2.11
[   35.506680] Bluetooth: L2CAP socket layer initialized
[   35.560647] Bluetooth: SCO (Voice Link) ver 0.6
[   35.560660] Bluetooth: SCO socket layer initialized
[   35.604222] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.604235] Bluetooth: BNEP filters: protocol multicast
[   35.652726] Bluetooth: RFCOMM socket layer initialized
[   35.653055] Bluetooth: RFCOMM TTY layer initialized
[   35.653061] Bluetooth: RFCOMM ver 1.10
[   35.676374] Bridge firewalling registered
[   40.613733] NET: Registered protocol family 17
[   75.124994] spurious 8259A interrupt: IRQ7.
[  109.660759] NET: Registered protocol family 10
[  109.663379] lo: Disabled Privacy Extensions
[  109.665810] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  120.244045] ath0: no IPv6 routers present
[  164.082223] ttyS1: LSR safety check engaged!
[  164.082256] type=1503 audit(1233843245.945:5): operation="capable" name="sys_admin" pid=5912 profile="/usr/sbin/cupsd"
ken

---

### Post by spiderbatdad on 2009-02-05
spank yourself for posting all that text. You were supposed to make an archive of the file and upload the archive with the manage attachment tool...or use "code" tags or the little # symbols at the top of this window and post large blocks of text between the code tags. :)

Ok. Edit the file /boot/grub/menu.lst with the following command:
```
gksu gedit /boot/grub/menu.lst
```
Go to the section that looks like this:
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=xxxxx ro **lapic hpet=force **
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```Delete "quiet splash" from the end of the line that starts with the word kernel in the section directly beneath ## ## End Default Options ## ##, and replace as above what I have shown in bold.

Next scroll up to the section that looks like this:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```Do the same here...delete quiet splash and replace with the above...normally I do not do this step.

Save the file, and reboot. You will not see the fancy loading bar, but a verbose output from the kernel instead. See if your system's behavior changes.

---

### Post by kdub on 2009-02-06
That didn't work.
Guess I'll wait for 9.04 and start over.Thats the good thing about the release schedual-you only have to wait six months or less when you mess up till all is good again!
thanx,
later,
kdub

---

