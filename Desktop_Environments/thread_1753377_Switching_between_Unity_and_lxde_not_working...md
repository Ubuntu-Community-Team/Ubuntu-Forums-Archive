---
title: "Switching between Unity and lxde not working.."
date: 2011-05-08
forum: Desktop Environments
---

### Post by eb3ha4el on 2011-05-08
*Post titled changed (same matter, expanded).


Hi

I got several WM/DE installed in my Ubuntu 11.04
Trying to switching them in login menu
some works and some doesn't.
when it doesn't work, it just comes back to login screen
with black screen appearing for short time, almost flashing.
 
Any ideas?
LXDE did not work before, when I only had default DE comes with ubuntu and LXDE additionally installed. But now it seems it works after installing some other WM.


WM doesn't work currently;
IceWM, JWM.

---

### Post by triceratops on 2011-05-09
> **eb3ha4el said:**
> 
when screen turns back to login screen, it shows some messages 
in terminal, if anyone can please tell me how to copy those text from TUI (Not terminal windows in GUI)into GUI, I'll put them on here.

Try this to get bootup information.

Get into superuser however you like to do it.  Go to root.    

Type or cut n paste this: 

```
dmesg /var/log/boot.log > /var/log/bootlog.txt
```dmesg reads the boot.log.  The caret outputs boot.log to a text file in the /var/log directory that you can open with any text editor.  

Use a text editor to cut 'n' paste log info into a forum box.

```
mousepad /var/log/bootlog.txt
``` or

```
gedit /var/log/bootlog.txt
```, whatever you'd prefer.  When done, log back in to user (not so good to be su all the time).

---

### Post by eb3ha4el on 2011-05-09
> **triceratops said:**
> Try this to get bootup information.

Get into superuser however you like to do it.  Go to root.    

Type or cut n paste this: 

```
dmesg /var/log/boot.log > /var/log/bootlog.txt
```dmesg reads the boot.log.  The caret outputs boot.log to a text file in the /var/log directory that you can open with any text editor.  

Use a text editor to cut 'n' paste log info into a forum box.

```
mousepad /var/log/bootlog.txt
``` or

```
gedit /var/log/bootlog.txt
```, whatever you'd prefer.  When done, log back in to user (not so good to be su all the time).




thanks 
here's the log




```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6d0000 - 000000003f6e2000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6e2000 - 000000003f6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6e3000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: TOSHIBA TOSHIBA NB200/KAVAA, BIOS V1.70 09/30/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f6d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   2 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f7a70] f7a70
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36782000 - 373b9000
[    0.000000] ACPI: RSDP 000f79f0 00024 (v02 TOSCPL)
[    0.000000] ACPI: XSDT 3f6d50b0 0008C (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3f6e1bd2 000F4 (v03 INTEL  CALISTGA 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 3f6d645c 0B702 (v01 TOSCPL CALISTGA 06040000 INTL 20050624)
[    0.000000] ACPI: FACS 3f6e2fc0 00040
[    0.000000] ACPI: APIC 3f6e1cc6 00068 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 3f6e1d2e 00038 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 3f6e1d66 0003C (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 3f6e1da2 00032 (v01 PTLTD  CALISTGA 06040000  PTL 00000001)
[    0.000000] ACPI: TMOR 3f6e1dd4 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: SLIC 3f6e1dfa 00176 (v01 TOSCPL TOSCPL00 06040000 LOHR 00000000)
[    0.000000] ACPI: APIC 3f6e1f70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 3f6e1fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 3f6d6252 0020A (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d5698 0021F (v02  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d5632 00066 (v02  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d513c 004F6 (v02  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f6d0
[    0.000000] On node 0 totalpages: 259679
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f5f92200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32212 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5800000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257649
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=e0a29338-e926-41dd-946a-cfb95d860865 ro quiet splash nohz=off vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5195520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f6d0)
[    0.000000] Memory: 1002708k/1039168k available (5188k kernel code, 36008k reserved, 2540k data, 700k init, 129864k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5408000 soft=f540a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.678 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.35 BogoMIPS (lpj=6650712)
[    0.004018] pid_max: default: 32768 minimum: 301
[    0.004073] Security Framework initialized
[    0.004109] AppArmor: AppArmor initialized
[    0.004114] Yama: becoming mindful.
[    0.004238] Mount-cache hash table entries: 512
[    0.004505] Initializing cgroup subsys ns
[    0.004514] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004522] Initializing cgroup subsys cpuacct
[    0.004533] Initializing cgroup subsys memory
[    0.004552] Initializing cgroup subsys devices
[    0.004558] Initializing cgroup subsys freezer
[    0.004564] Initializing cgroup subsys net_cls
[    0.004570] Initializing cgroup subsys blkio
[    0.004637] CPU: Physical Processor ID: 0
[    0.004642] CPU: Processor Core ID: 0
[    0.004648] mce: CPU supports 5 MCE banks
[    0.004664] CPU0: Thermal monitoring enabled (TM2)
[    0.004673] using mwait in idle threads.
[    0.011044] ACPI: Core revision 20110112
[    0.024055] ftrace: allocating 23640 entries in 47 pages
[    0.028105] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032318] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072027] CPU0: Intel(R) Atom(TM) CPU N280   @ 1.66GHz stepping 02
[    0.076004] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.076004] ... version:                3
[    0.076004] ... bit width:              40
[    0.076004] ... generic registers:      2
[    0.076004] ... value mask:             000000ffffffffff
[    0.076004] ... max period:             000000007fffffff
[    0.076004] ... fixed-purpose events:   3
[    0.076004] ... event mask:             0000000700000003
[    0.076004] CPU 1 irqstacks, hard=f54ca000 soft=f54cc000
[    0.076004] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.168048] Brought up 2 CPUs
[    0.168059] Total of 2 processors activated (6650.11 BogoMIPS).
[    0.168418] devtmpfs: initialized
[    0.172155] print_constraints: dummy: 
[    0.172201] Time: 21:42:04  Date: 05/23/11
[    0.172291] NET: Registered protocol family 16
[    0.172316] Trying to unpack rootfs image as initramfs...
[    0.172701] EISA bus registered
[    0.172726] ACPI: bus type pci registered
[    0.172954] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.172966] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.172972] PCI: Using MMCONFIG for extended config space
[    0.172979] PCI: Using configuration type 1 for base access
[    0.177244] bio: create slab <bio-0> at 0
[    0.181782] ACPI: EC: Look up EC in DSDT
[    0.190313] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.191767] ACPI: SSDT 3f6d5f7b 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.192823] ACPI: Dynamic OEM Table Load:
[    0.192834] ACPI: SSDT   (null) 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.193433] ACPI: SSDT 3f6d58b7 0063F (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.194418] ACPI: Dynamic OEM Table Load:
[    0.194429] ACPI: SSDT   (null) 0063F (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.195350] ACPI: SSDT 3f6d617e 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.196382] ACPI: Dynamic OEM Table Load:
[    0.196395] ACPI: SSDT   (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.196756] ACPI: SSDT 3f6d5ef6 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.197744] ACPI: Dynamic OEM Table Load:
[    0.197756] ACPI: SSDT   (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.200404] ACPI: Interpreter enabled
[    0.200419] ACPI: (supports S0 S3 S4 S5)
[    0.200485] ACPI: Using IOAPIC for interrupt routing
[    0.254921] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.255434] ACPI: No dock devices found.
[    0.255443] HEST: Table not found.
[    0.255453] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.256579] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.258735] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.258747] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.258757] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.258767] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.258776] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.258785] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.258795] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff]
[    0.258834] pci 0000:00:00.0: [8086:27ac] type 0 class 0x000600
[    0.258920] pci 0000:00:02.0: [8086:27ae] type 0 class 0x000300
[    0.258944] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf007ffff]
[    0.258958] pci 0000:00:02.0: reg 14: [io  0x1800-0x1807]
[    0.258973] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.258987] pci 0000:00:02.0: reg 1c: [mem 0xf0200000-0xf023ffff]
[    0.259052] pci 0000:00:02.1: [8086:27a6] type 0 class 0x000380
[    0.259072] pci 0000:00:02.1: reg 10: [mem 0xf0080000-0xf00fffff]
[    0.259216] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.259252] pci 0000:00:1b.0: reg 10: [mem 0xf0440000-0xf0443fff 64bit]
[    0.259362] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.259374] pci 0000:00:1b.0: PME# disabled
[    0.259422] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.259535] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.259546] pci 0000:00:1c.0: PME# disabled
[    0.259596] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.259709] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.259720] pci 0000:00:1c.1: PME# disabled
[    0.259774] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.259893] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.259905] pci 0000:00:1c.2: PME# disabled
[    0.259959] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.260091] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.260103] pci 0000:00:1c.3: PME# disabled
[    0.260157] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.260234] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.260298] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.260375] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.260439] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.260515] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.260578] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.260655] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.260741] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.260779] pci 0000:00:1d.7: reg 10: [mem 0xf0444000-0xf04443ff]
[    0.260897] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.260908] pci 0000:00:1d.7: PME# disabled
[    0.260956] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.261075] pci 0000:00:1f.0: [8086:27b9] type 0 class 0x000601
[    0.261203] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.261217] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.261229] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.261240] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 007f)
[    0.261253] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0068 (mask 0007)
[    0.261313] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.261340] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.261360] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.261381] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.261401] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.261422] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.261496] pci 0000:00:1f.2: [8086:27c5] type 0 class 0x000106
[    0.261531] pci 0000:00:1f.2: reg 10: [io  0x18c8-0x18cf]
[    0.261553] pci 0000:00:1f.2: reg 14: [io  0x18c0-0x18c3]
[    0.261575] pci 0000:00:1f.2: reg 18: [io  0x18a8-0x18af]
[    0.261598] pci 0000:00:1f.2: reg 1c: [io  0x180c-0x180f]
[    0.261618] pci 0000:00:1f.2: reg 20: [io  0x18b0-0x18bf]
[    0.261639] pci 0000:00:1f.2: reg 24: [mem 0xf0444400-0xf04447ff]
[    0.261698] pci 0000:00:1f.2: PME# supported from D3hot
[    0.261708] pci 0000:00:1f.2: PME# disabled
[    0.261745] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.261830] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
[    0.261968] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.261980] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.261993] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.262009] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.262141] pci 0000:03:00.0: [168c:002b] type 0 class 0x000280
[    0.262199] pci 0000:03:00.0: reg 10: [mem 0xf0100000-0xf010ffff 64bit]
[    0.262399] pci 0000:03:00.0: supports D1
[    0.262406] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.262420] pci 0000:03:00.0: PME# disabled
[    0.268084] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.268099] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.268114] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.268130] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.268304] pci 0000:04:00.0: [10ec:8136] type 0 class 0x000200
[    0.268383] pci 0000:04:00.0: reg 10: [io  0x2000-0x20ff]
[    0.268506] pci 0000:04:00.0: reg 18: [mem 0xf0510000-0xf0510fff 64bit pref]
[    0.268588] pci 0000:04:00.0: reg 20: [mem 0xf0500000-0xf050ffff 64bit pref]
[    0.268644] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.268826] pci 0000:04:00.0: supports D1 D2
[    0.268835] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.268858] pci 0000:04:00.0: PME# disabled
[    0.269054] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.269067] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.269080] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.269097] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.269186] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.269197] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.269210] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.269226] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.269342] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.269355] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.269368] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.269384] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.269394] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.269404] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.269413] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.269423] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.269433] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.269443] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.269453] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
[    0.269503] pci_bus 0000:00: on NUMA node 0
[    0.269519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.270046] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.270220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.270396] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.270572] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.270839] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.271454]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.288759] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.288951] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.289127] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.289303] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.289478] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.289654] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.289852] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.290029] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.290376] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.290410] vgaarb: loaded
[    0.291239] SCSI subsystem initialized
[    0.291427] libata version 3.00 loaded.
[    0.291634] usbcore: registered new interface driver usbfs
[    0.291685] usbcore: registered new interface driver hub
[    0.291805] usbcore: registered new device driver usb
[    0.292255] wmi: Mapper loaded
[    0.292262] PCI: Using ACPI for IRQ routing
[    0.292272] PCI: pci_cache_line_size set to 64 bytes
[    0.292452] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.292462] reserve RAM buffer: 000000003f6d0000 - 000000003fffffff 
[    0.292813] NetLabel: Initializing
[    0.292821] NetLabel:  domain hash size = 128
[    0.292826] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.292859] NetLabel:  unlabeled traffic allowed by default
[    0.293000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.293014] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.293029] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.296175] Switching to clocksource hpet
[    0.318613] AppArmor: AppArmor Filesystem Enabled
[    0.318698] pnp: PnP ACPI init
[    0.318752] ACPI: bus type pnp registered
[    0.319942] pnp 00:00: [bus 00-ff]
[    0.319954] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.319962] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.319971] pnp 00:00: [io  0x0d00-0xffff window]
[    0.319979] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.319988] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.319996] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.320053] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.320062] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.320070] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.320079] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.320087] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.320096] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.320104] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.320113] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.320121] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.320130] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.320138] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.320147] pnp 00:00: [mem 0x40000000-0xfebfffff window]
[    0.320156] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.320360] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.320465] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.320474] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.320482] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.320490] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.320498] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.320506] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.320514] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.320522] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.320679] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.320690] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.320701] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.320711] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.320721] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.320731] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.320753] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.320764] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.320775] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.321508] pnp 00:02: [io  0x0000-0x001f]
[    0.321518] pnp 00:02: [io  0x0081-0x0091]
[    0.321525] pnp 00:02: [io  0x0093-0x009f]
[    0.321533] pnp 00:02: [io  0x00c0-0x00df]
[    0.321541] pnp 00:02: [dma 4]
[    0.321688] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.321943] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.322154] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.322167] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.322212] pnp 00:04: [io  0x00f0]
[    0.322237] pnp 00:04: [irq 13]
[    0.322374] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.322419] pnp 00:05: [io  0x0061]
[    0.322427] pnp 00:05: [io  0x0063]
[    0.322434] pnp 00:05: [io  0x0065]
[    0.322441] pnp 00:05: [io  0x0067]
[    0.322448] pnp 00:05: [io  0x0068]
[    0.322454] pnp 00:05: [io  0x006c]
[    0.322461] pnp 00:05: [io  0x0070]
[    0.322468] pnp 00:05: [io  0x0080]
[    0.322475] pnp 00:05: [io  0x0092]
[    0.322482] pnp 00:05: [io  0x00b2-0x00b3]
[    0.322489] pnp 00:05: [io  0x0800-0x080f]
[    0.322497] pnp 00:05: [io  0x1000-0x107f]
[    0.322504] pnp 00:05: [io  0x1180-0x11bf]
[    0.322511] pnp 00:05: [io  0xfe00]
[    0.322518] pnp 00:05: [io  0xff2c-0xff7f]
[    0.322753] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.322764] system 00:05: [io  0x1000-0x107f] has been reserved
[    0.322774] system 00:05: [io  0x1180-0x11bf] has been reserved
[    0.322783] system 00:05: [io  0xfe00] has been reserved
[    0.322793] system 00:05: [io  0xff2c-0xff7f] has been reserved
[    0.322804] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.322842] pnp 00:06: [io  0x0070-0x0077]
[    0.322860] pnp 00:06: [irq 8]
[    0.323001] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.340159] pnp 00:07: [io  0x0060]
[    0.340170] pnp 00:07: [io  0x0064]
[    0.340196] pnp 00:07: [irq 1]
[    0.340402] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.340450] pnp 00:08: [irq 12]
[    0.340603] pnp 00:08: Plug and Play ACPI device, IDs AUI0311 SYN0700 SYN0002 PNP0f13 (active)
[    0.340715] pnp: PnP ACPI: found 9 devices
[    0.340722] ACPI: ACPI bus type pnp unregistered
[    0.340731] PnPBIOS: Disabled by ACPI PNP
[    0.382598] pci 0000:00:1c.0: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.382618] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.382633] pci 0000:00:1c.1: BAR 15: assigned [mem 0x40400000-0x405fffff 64bit pref]
[    0.382647] pci 0000:00:1c.2: BAR 14: assigned [mem 0x40600000-0x409fffff]
[    0.382660] pci 0000:00:1c.3: BAR 14: assigned [mem 0x40a00000-0x40bfffff]
[    0.382675] pci 0000:00:1c.3: BAR 15: assigned [mem 0x40c00000-0x40dfffff 64bit pref]
[    0.382689] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.382701] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.382713] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.382722] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.382732] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.382746] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff]
[    0.382759] pci 0000:00:1c.0:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.382775] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.382785] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.382799] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.382811] pci 0000:00:1c.1:   bridge window [mem 0x40400000-0x405fffff 64bit pref]
[    0.382830] pci 0000:04:00.0: BAR 6: assigned [mem 0xf0520000-0xf053ffff pref]
[    0.382840] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.382850] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.382863] pci 0000:00:1c.2:   bridge window [mem 0x40600000-0x409fffff]
[    0.382875] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.382891] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.382900] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.382914] pci 0000:00:1c.3:   bridge window [mem 0x40a00000-0x40bfffff]
[    0.382926] pci 0000:00:1c.3:   bridge window [mem 0x40c00000-0x40dfffff 64bit pref]
[    0.382942] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.382949] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.382961] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.382972] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.383029] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.383043] pci 0000:00:1c.0: setting latency timer to 64
[    0.383073] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.383085] pci 0000:00:1c.1: setting latency timer to 64
[    0.383113] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.383125] pci 0000:00:1c.2: setting latency timer to 64
[    0.383153] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.383165] pci 0000:00:1c.3: setting latency timer to 64
[    0.383183] pci 0000:00:1e.0: setting latency timer to 64
[    0.383194] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.383203] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.383212] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.383221] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.383230] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.383239] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.383248] pci_bus 0000:00: resource 10 [mem 0x40000000-0xfebfffff]
[    0.383257] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.383266] pci_bus 0000:02: resource 1 [mem 0x40000000-0x401fffff]
[    0.383276] pci_bus 0000:02: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.383286] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    0.383294] pci_bus 0000:03: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.383303] pci_bus 0000:03: resource 2 [mem 0x40400000-0x405fffff 64bit pref]
[    0.383313] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.383322] pci_bus 0000:04: resource 1 [mem 0x40600000-0x409fffff]
[    0.383332] pci_bus 0000:04: resource 2 [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.383342] pci_bus 0000:05: resource 0 [io  0x5000-0x5fff]
[    0.383352] pci_bus 0000:05: resource 1 [mem 0x40a00000-0x40bfffff]
[    0.383362] pci_bus 0000:05: resource 2 [mem 0x40c00000-0x40dfffff 64bit pref]
[    0.383372] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.383380] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.383389] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.383398] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.383407] pci_bus 0000:06: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.383415] pci_bus 0000:06: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.383424] pci_bus 0000:06: resource 10 [mem 0x40000000-0xfebfffff]
[    0.383539] NET: Registered protocol family 2
[    0.383733] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.384630] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.385734] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.386258] TCP: Hash tables configured (established 131072 bind 65536)
[    0.386266] TCP reno registered
[    0.386279] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.386303] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.386607] NET: Registered protocol family 1
[    0.386660] pci 0000:00:02.0: Boot video device
[    0.386890] PCI: CLS 64 bytes, default 64
[    0.386965] Simple Boot Flag at 0x36 set to 0x1
[    0.387613] cpufreq-nforce2: No nForce2 chipset.
[    0.388115] audit: initializing netlink socket (disabled)
[    0.388144] type=2000 audit(1306186924.384:1): initialized
[    0.412103] highmem bounce pool size: 64 pages
[    0.412120] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.418933] VFS: Disk quotas dquot_6.5.2
[    0.419144] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.421784] fuse init (API version 7.16)
[    0.422166] msgmni has been set to 1704
[    0.423017] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.423128] io scheduler noop registered
[    0.423135] io scheduler deadline registered
[    0.423202] io scheduler cfq registered (default)
[    0.423561] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.423657] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.423834] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.423921] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.424124] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.424206] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.424359] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.424441] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.424732] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.424838] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.425020] intel_idle: MWAIT substates: 0x20220
[    0.425037] intel_idle: v0.4 model 0x1C
[    0.425043] intel_idle: lapic_timer_reliable_states 0x2
[    0.425061] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.425495] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.425880] ACPI: AC Adapter [ACAD] (on-line)
[    0.426184] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.426353] ACPI: Lid Switch [LID0]
[    0.426558] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.426572] ACPI: Power Button [PWRB]
[    0.426767] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.426779] ACPI: Power Button [PWRF]
[    0.427350] ACPI: acpi_idle yielding to intel_idle
[    0.456767] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.457025] ERST: Table is not found!
[    0.457242] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.457790] isapnp: Scanning for PnP cards...
[    0.632985] ACPI: Battery Slot [BAT1] (battery present)
[    0.812038] isapnp: No Plug & Play device found
[    0.853458] Freeing initrd memory: 12508k freed
[    1.784889] Linux agpgart interface v0.103
[    1.785060] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.785229] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.785410] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.785654] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.788912] brd: module loaded
[    1.790424] loop: module loaded
[    1.790680] i2c-core: driver [adp5520] using legacy suspend method
[    1.790685] i2c-core: driver [adp5520] using legacy resume method
[    1.790915] ata_piix 0000:00:1f.1: version 2.13
[    1.790944] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.791009] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.791817] scsi0 : ata_piix
[    1.792111] scsi1 : ata_piix
[    1.792925] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.792933] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.793183] ata2: port disabled. ignoring.
[    1.794030] Fixed MDIO Bus: probed
[    1.794138] PPP generic driver version 2.4.2
[    1.794282] tun: Universal TUN/TAP device driver, 1.6
[    1.794287] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.794527] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.794593] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.794626] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.794635] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.794731] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.816125] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.816159] ehci_hcd 0000:00:1d.7: debug port 1
[    1.820046] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.820079] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0444000
[    1.832066] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.832402] hub 1-0:1.0: USB hub found
[    1.832414] hub 1-0:1.0: 8 ports detected
[    1.832600] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.832639] uhci_hcd: USB Universal Host Controller Interface driver
[    1.832717] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.832732] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.832740] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.832850] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.844102] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.844440] hub 2-0:1.0: USB hub found
[    1.844452] hub 2-0:1.0: 2 ports detected
[    1.844607] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.844621] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.844628] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.844726] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.856123] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.856443] hub 3-0:1.0: USB hub found
[    1.856455] hub 3-0:1.0: 2 ports detected
[    1.856601] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.856614] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.856622] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.856722] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.868122] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.868449] hub 4-0:1.0: USB hub found
[    1.868460] hub 4-0:1.0: 2 ports detected
[    1.868622] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.868637] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.868644] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.868740] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.880122] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.880443] hub 5-0:1.0: USB hub found
[    1.880454] hub 5-0:1.0: 2 ports detected
[    1.880724] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.937339] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.937395] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.937745] mousedev: PS/2 mouse device common for all mice
[    1.940916] rtc_cmos 00:06: RTC can wake from S4
[    1.956234] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.956281] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.956529] device-mapper: uevent: version 1.0.3
[    1.956754] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.956923] device-mapper: multipath: version 1.2.0 loaded
[    1.956932] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.957145] EISA: Probing bus 0 at eisa.0
[    1.957151] EISA: Cannot allocate resource for mainboard
[    1.957158] Cannot allocate resource for EISA slot 1
[    1.957163] Cannot allocate resource for EISA slot 2
[    1.957169] Cannot allocate resource for EISA slot 3
[    1.957174] Cannot allocate resource for EISA slot 4
[    1.957180] Cannot allocate resource for EISA slot 5
[    1.957185] Cannot allocate resource for EISA slot 6
[    1.957190] Cannot allocate resource for EISA slot 7
[    1.957196] Cannot allocate resource for EISA slot 8
[    1.957200] EISA: Detected 0 cards.
[    1.957497] cpuidle: using governor ladder
[    1.957765] cpuidle: using governor menu
[    1.958507] TCP cubic registered
[    1.958944] NET: Registered protocol family 10
[    1.960559] NET: Registered protocol family 17
[    1.960614] Registering the dns_resolver key type
[    1.961699] Using IPI No-Shortcut mode
[    1.962064] PM: Hibernation image not present or could not be loaded.
[    1.962092] registered taskstats version 1
[    1.962712]   Magic number: 11:634:753
[    1.962753] tty ttyS4: hash matches
[    1.962868] rtc_cmos 00:06: setting system clock to 2011-05-23 21:42:06 UTC (1306186926)
[    1.962877] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.962882] EDD information not available.
[    1.963159] Freeing unused kernel memory: 700k freed
[    1.963716] Write protecting the kernel text: 5192k
[    1.963827] Write protecting the kernel read-only data: 2148k
[    1.995522] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.035538] <30>udev[69]: starting version 167
[    2.148081] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    2.357765] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.357856] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.357929] r8169 0000:04:00.0: setting latency timer to 64
[    2.358036] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    2.359632] r8169 0000:04:00.0: eth0: RTL8102e at 0xf8022000, 00:26:22:3c:73:da, XID 04c00000 IRQ 44
[    2.397236] ahci 0000:00:1f.2: version 3.0
[    2.397275] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.397385] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    2.397525] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    2.397539] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    2.397553] ahci 0000:00:1f.2: setting latency timer to 64
[    2.399834] scsi2 : ahci
[    2.400207] scsi3 : ahci
[    2.400519] scsi4 : ahci
[    2.400848] scsi5 : ahci
[    2.401328] ata3: SATA max UDMA/133 abar m1024@0xf0444400 port 0xf0444500 irq 45
[    2.401339] ata4: DUMMY
[    2.401348] ata5: SATA max UDMA/133 abar m1024@0xf0444400 port 0xf0444600 irq 45
[    2.401356] ata6: DUMMY
[    2.720063] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.720108] ata5: SATA link down (SStatus 0 SControl 300)
[    2.720721] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.775217] ata3.00: ATA-8: TOSHIBA MK2555GSX, FG001M, max UDMA/100
[    2.775226] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.776157] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.776338] ata3.00: configured for UDMA/100
[    2.776631] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5
[    2.777221] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.777239] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.777498] sd 2:0:0:0: [sda] Write Protect is off
[    2.777509] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.777621] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.828908]  sda: sda1 sda2 sda3 sda4
[    2.830003] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.491544] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   13.076345] <30>udev[258]: starting version 167
[   13.139581] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[   13.167543] lp: driver loaded but no devices found
[   13.743342] type=1400 audit(1306183338.276:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=438 comm="apparmor_parser"
[   13.757513] type=1400 audit(1306183338.292:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=438 comm="apparmor_parser"
[   13.764477] type=1400 audit(1306183338.300:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=438 comm="apparmor_parser"
[   13.978361] acpi device:01: registered as cooling_device2
[   13.978638] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[   13.978841] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   14.156444] Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[   14.158273] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[   14.295628] intel_rng: FWH not detected
[   14.426583] r8169 0000:04:00.0: eth0: link down
[   14.427301] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.476671] leds_ss4200: no LED devices found
[   14.836211] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   15.031395] type=1400 audit(1306183339.564:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=616 comm="apparmor_parser"
[   15.050750] type=1400 audit(1306183339.584:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=617 comm="apparmor_parser"
[   15.061129] type=1400 audit(1306183339.596:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=617 comm="apparmor_parser"
[   15.077473] type=1400 audit(1306183339.612:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=617 comm="apparmor_parser"
[   15.114778] type=1400 audit(1306183339.648:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=623 comm="apparmor_parser"
[   15.125423] type=1400 audit(1306183339.660:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=623 comm="apparmor_parser"
[   15.157891] type=1400 audit(1306183339.692:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=618 comm="apparmor_parser"
[   15.381405] cfg80211: Calling CRDA to update world regulatory domain
[   15.429626] [drm] Initialized drm 1.1.0 20060810
[   15.579078] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input5
[   15.632867] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[   16.033101] vboxdrv: Found 2 processor cores.
[   16.035686] vboxdrv: fAsync=0 offMin=0x1b8 offMax=0x23c8
[   16.037831] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   16.037841] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
[   16.184692] Linux video capture interface: v2.00
[   16.194074] cfg80211: World regulatory domain updated:
[   16.194085] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.194096] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.194106] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.194115] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.194125] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.194134] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.318010] uvcvideo: Found UVC 1.00 device USB2.0 UVC WebCam (04f2:b128)
[   16.324373] input: USB2.0 UVC WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
[   16.327324] usbcore: registered new interface driver uvcvideo
[   16.327334] USB Video Class driver (v1.0.0)
[   16.479783] Bluetooth: Core ver 2.15
[   16.481405] NET: Registered protocol family 31
[   16.481414] Bluetooth: HCI device and connection manager initialized
[   16.481422] Bluetooth: HCI socket layer initialized
[   16.566133] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   16.614885] usbcore: registered new interface driver btusb
[   16.705115] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.705131] i915 0000:00:02.0: setting latency timer to 64
[   16.781605] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.781615] [drm] Driver supports precise vblank timestamp query.
[   16.884283] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.884855] [drm] initialized overlay support
[   16.911696] Bluetooth: L2CAP ver 2.15
[   16.911704] Bluetooth: L2CAP socket layer initialized
[   16.940699] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.940709] Bluetooth: BNEP filters: protocol multicast
[   16.964274] Bluetooth: SCO (Voice Link) ver 0.6
[   16.964282] Bluetooth: SCO socket layer initialized
[   17.016753] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.016782] ath9k 0000:03:00.0: setting latency timer to 64
[   17.068681] ath: EEPROM regdomain: 0x65
[   17.068688] ath: EEPROM indicates we should expect a direct regpair map
[   17.068698] ath: Country alpha2 being used: 00
[   17.068703] ath: Regpair used: 0x65
[   17.068712] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.068721] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068728] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.068737] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068744] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.068753] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068760] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.068768] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068775] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.068784] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068791] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.068800] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068807] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.068815] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068822] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.068831] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068838] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.068846] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068853] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.068862] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068869] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.068878] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068885] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   17.068893] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068900] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   17.068909] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.068916] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   17.071100] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   17.089883] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   17.093345] Registered led device: ath9k-phy0::radio
[   17.093682] Registered led device: ath9k-phy0::assoc
[   17.093995] Registered led device: ath9k-phy0::tx
[   17.094288] Registered led device: ath9k-phy0::rx
[   17.094314] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8480000, irq=17
[   17.189614] Console: switching to colour frame buffer device 128x37
[   17.189695] fb0: inteldrmfb frame buffer device
[   17.189701] drm: registered panic notifier
[   17.190135] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.194241] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.200419] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   17.200491] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.206512] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.508466] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   17.509079] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.121692] ppdev: user-space parallel port driver
[   18.334134] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[   26.518642] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[   38.420366] wlan0: authenticate with 00:26:5a:92:c1:8e (try 1)
[   38.422407] wlan0: authenticated
[   38.444060] wlan0: associate with 00:26:5a:92:c1:8e (try 1)
[   38.453323] wlan0: RX AssocResp from 00:26:5a:92:c1:8e (capab=0x411 status=0 aid=1)
[   38.453335] wlan0: associated
[   38.463141] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.464059] cfg80211: Calling CRDA for country: TW
[   38.478094] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   38.478108] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478117] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   38.478126] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478134] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   38.478143] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478152] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   38.478161] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478169] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   38.478180] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478189] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   38.478199] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478207] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   38.478216] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478225] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   38.478235] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478243] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   38.478253] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478261] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   38.478270] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478279] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   38.478289] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   38.478296] cfg80211: Disabling freq 2467 MHz
[   38.478303] cfg80211: Disabling freq 2472 MHz
[   38.478309] cfg80211: Disabling freq 2484 MHz
[   38.478320] cfg80211: Regulatory domain changed to country: TW
[   38.478326] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   38.478335] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   38.478344] cfg80211:     (5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   38.478353] cfg80211:     (5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   38.795638] Intel AES-NI instructions are not detected.
[   38.829983] padlock_aes: VIA PadLock not detected.
[   47.410928] wlan0: deauthenticating from 00:26:5a:92:c1:8e by local choice (reason=3)
[   47.466907] cfg80211: All devices are disconnected, going to restore regulatory settings
[   47.466918] cfg80211: Restoring regulatory settings
[   47.466950] cfg80211: Calling CRDA to update world regulatory domain
[   47.478409] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   47.478423] cfg80211: World regulatory domain updated:
[   47.478428] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.478436] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.478444] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   47.478451] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   47.478459] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.478466] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.168040] wlan0: no IPv6 routers present
[   89.149944] wlan0: authenticate with 00:26:5a:92:c1:8e (try 1)
[   89.336351] wlan0: authenticated
[   89.353880] wlan0: associate with 00:26:5a:92:c1:8e (try 1)
[   89.363278] wlan0: RX AssocResp from 00:26:5a:92:c1:8e (capab=0x411 status=0 aid=1)
[   89.363296] wlan0: associated
[   89.371916] cfg80211: Calling CRDA for country: TW
[   89.391081] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   89.391100] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391114] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   89.391129] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391141] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   89.391156] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391169] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   89.391183] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391196] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   89.391210] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391223] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   89.391237] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391250] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   89.391264] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391277] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   89.391292] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391304] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   89.391319] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391331] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   89.391346] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391358] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   89.391373] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   89.391383] cfg80211: Disabling freq 2467 MHz
[   89.391392] cfg80211: Disabling freq 2472 MHz
[   89.391401] cfg80211: Disabling freq 2484 MHz
[   89.391416] cfg80211: Regulatory domain changed to country: TW
[   89.391425] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   89.391440] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   89.391454] cfg80211:     (5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   89.391468] cfg80211:     (5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  110.798728] exe (1957): /proc/1957/oom_adj is deprecated, please use /proc/1957/oom_score_adj instead.

```

---

### Post by eb3ha4el on 2011-05-23
Bump

---

