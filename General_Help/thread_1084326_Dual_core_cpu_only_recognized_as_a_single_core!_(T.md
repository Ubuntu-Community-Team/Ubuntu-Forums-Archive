---
title: "Dual core cpu only recognized as a single core! (T1600)"
date: 2009-03-01
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-03-01
SOLVED
My cpu is T1600 Mobile Celeron Dual-core [http://processorfinder.intel.com/details.aspx?sSpec=SLB6J](http://processorfinder.intel.com/details.aspx?sSpec=SLB6J)
But cat /proc/cpuinfo tells me it is a single core
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Genuine Intel(R) CPU           T1600  @ 1.66GHz
stepping	: 13
cpu MHz		: 1666.625
cache size	: 1024 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3333.25
clflush size	: 64
power management:

coppen@coppen-laptop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Genuine Intel(R) CPU           T1600  @ 1.66GHz
stepping	: 13
cpu MHz		: 1666.625
cache size	: 1024 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3333.25
clflush size	: 64
power management:

```

But dmesg says it is a dual-core but then then SMP is disable. Is that because of ACPI problem? In my /boot/grub/menu.lst I added acpi=on and nolapic because if this two options are missed the boot process would hang. **[update: I just find out only nolapic is needed to boot without freezing at the loading bar]**
```
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] found SMP MP-table at [c00f85b0] 000f85b0
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
    0.022266] ACPI: Core revision 20080609
[    0.025121] ACPI: Checking initramfs for custom DSDT
[    0.427585] ACPI: setting ELCR to 0800 (from 0eb8)
[    0.428100] BIOS bug, local APIC #0 not detected!...
[    0.428142] ... forcing use of dummy APIC emulation.(tell your hw vendor)
[    0.428181] SMP disabled
```
The #5 post in this thread ([http://ubuntuforums.org/showthread.php?t=272176](http://ubuntuforums.org/showthread.php?t=272176)) suggest enabling APIC/ACPI/SMP settings enabled in the BIOS. I checked the Bios and it doesn't have any choice for acpi or anything similar. The BIOS is over simplified as this notebook is a cheap machine. [please take a look at the photo of my BIOS ]

[[img]http://www.freeimagehosting.net/uploads/th.c6cdb9be85.jpg[/img]](http://www.freeimagehosting.net/image.php?c6cdb9be85.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.ae131e81c8.jpg[/img]](http://www.freeimagehosting.net/image.php?ae131e81c8.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.8762a54627.jpg[/img]](http://www.freeimagehosting.net/image.php?8762a54627.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.6e9ac46d3f.jpg[/img]](http://www.freeimagehosting.net/image.php?6e9ac46d3f.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.6e9ac46d3f.jpg[/img]](http://www.freeimagehosting.net/image.php?6e9ac46d3f.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.6e9ac46d3f.jpg[/img]](http://www.freeimagehosting.net/image.php?6e9ac46d3f.jpg)

[[img]http://www.freeimagehosting.net/uploads/th.3b56426eb0.jpg[/img]](http://www.freeimagehosting.net/image.php?3b56426eb0.jpg)

 Here's my /boot/grub/menu.lst
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro **acpi=on nolapic**  quiet  
initrd		/initrd.img-2.6.27-11-generic
```



Below is the full context of dmesg

```

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
[    0.000000] Kernel command line: root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro acpi=on nolapic  quiet  
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1666.625 MHz processor.
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
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3333.25 BogoMIPS (lpj=6666500)
[    0.004030] Security Framework initialized
[    0.004036] SELinux:  Disabled at boot.
[    0.004057] AppArmor: AppArmor initialized
[    0.004065] Mount-cache hash table entries: 512
[    0.004236] Initializing cgroup subsys ns
[    0.004240] Initializing cgroup subsys cpuacct
[    0.004244] Initializing cgroup subsys memory
[    0.004260] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004264] CPU: L2 cache: 1024K
[    0.004267] CPU: Physical Processor ID: 0
[    0.004269] CPU: Processor Core ID: 0
[    0.004272] using mwait in idle threads.
[    0.004280] Checking 'hlt' instruction... OK.
[    0.022266] ACPI: Core revision 20080609
[    0.025121] ACPI: Checking initramfs for custom DSDT
[    0.427585] ACPI: setting ELCR to 0800 (from 0eb8)
[    0.428100] BIOS bug, local APIC #0 not detected!...
[    0.428142] ... forcing use of dummy APIC emulation.(tell your hw vendor)
[    0.428181] SMP disabled
[    0.428254] Brought up 1 CPUs
[    0.428257] Total of 1 processors activated (3333.25 BogoMIPS).
[    0.428270] CPU0 attaching NULL sched-domain.
[    0.428538] net_namespace: 840 bytes
[    0.428562] Booting paravirtualized kernel on bare hardware
[    0.428789] Time: 11:40:36  Date: 03/02/09
[    0.428824] NET: Registered protocol family 16
[    0.429170] EISA bus registered
[    0.429192] ACPI: bus type pci registered
[    0.429324] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 0
[    0.429328] PCI: MCFG area at e0000000 reserved in E820
[    0.429331] PCI: Using MMCONFIG for extended config space
[    0.429334] PCI: Using configuration type 1 for base access
[    0.433329] ACPI: EC: Look up EC in DSDT
[    0.437983] ACPI: Interpreter enabled
[    0.437994] ACPI: (supports S0 S3 S4 S5)
[    0.438009] ACPI: Using PIC for interrupt routing
[    0.438402] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.447872] ACPI: EC: GPE = 0x13, I/O: command/status = 0x66, data = 0x62
[    0.447876] ACPI: EC: driver started in interrupt mode
[    0.447954] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.448059] PCI: 0000:00:00.0 reg 10 32bit mmio: [a0000000, afffffff]
[    0.448224] PCI: 0000:00:02.5 reg 10 io port: [1f0, 1f7]
[    0.448232] PCI: 0000:00:02.5 reg 14 io port: [3f4, 3f7]
[    0.448240] PCI: 0000:00:02.5 reg 18 io port: [170, 177]
[    0.448248] PCI: 0000:00:02.5 reg 1c io port: [374, 377]
[    0.448256] PCI: 0000:00:02.5 reg 20 io port: [1080, 108f]
[    0.448286] pci 0000:00:02.5: PME# supported from D3cold
[    0.448291] pci 0000:00:02.5: PME# disabled
[    0.448314] PCI: 0000:00:03.0 reg 10 32bit mmio: [b0104000, b0104fff]
[    0.448370] PCI: 0000:00:03.1 reg 10 32bit mmio: [b0105000, b0105fff]
[    0.448439] PCI: 0000:00:03.3 reg 10 32bit mmio: [b0106000, b0106fff]
[    0.448487] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.448492] pci 0000:00:03.3: PME# disabled
[    0.448529] PCI: 0000:00:04.0 reg 10 32bit mmio: [b0307000, b030707f]
[    0.448537] PCI: 0000:00:04.0 reg 14 io port: [1000, 107f]
[    0.448579] pci 0000:00:04.0: supports D1
[    0.448581] pci 0000:00:04.0: supports D2
[    0.448584] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448589] pci 0000:00:04.0: PME# disabled
[    0.448620] PCI: 0000:00:05.0 reg 10 io port: [10c8, 10cf]
[    0.448629] PCI: 0000:00:05.0 reg 14 io port: [10bc, 10bf]
[    0.448636] PCI: 0000:00:05.0 reg 18 io port: [10c0, 10c7]
[    0.448644] PCI: 0000:00:05.0 reg 1c io port: [10b8, 10bb]
[    0.448652] PCI: 0000:00:05.0 reg 20 io port: [10a0, 10af]
[    0.448680] pci 0000:00:05.0: PME# supported from D3cold
[    0.448685] pci 0000:00:05.0: PME# disabled
[    0.448732] PCI: 0000:00:0f.0 reg 10 32bit mmio: [b0100000, b0103fff]
[    0.448780] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.448785] pci 0000:00:0f.0: PME# disabled
[    0.448846] PCI: 0000:01:00.0 reg 10 32bit mmio: [c0000000, cfffffff]
[    0.448853] PCI: 0000:01:00.0 reg 14 32bit mmio: [b0000000, b001ffff]
[    0.448859] PCI: 0000:01:00.0 reg 18 io port: [9000, 907f]
[    0.448890] pci 0000:01:00.0: supports D1
[    0.448892] pci 0000:01:00.0: supports D2
[    0.448930] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.448935] PCI: bridge 0000:00:01.0 32bit mmio: [b0000000, b00fffff]
[    0.448940] PCI: bridge 0000:00:01.0 32bit mmio pref: [c0000000, cfffffff]
[    0.448950] bus 00 -> node 0
[    0.448958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.457975] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.458121] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.458263] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 9 10 11)
[    0.458404] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[    0.458574] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.458715] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.458857] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.458998] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.459443] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.459487] pnp: PnP ACPI init
[    0.459501] ACPI: bus type pnp registered
[    0.462169] pnp 00:05: IRQ 13 override to level, low
[    0.462173] PCI: setting IRQ 13 as level-triggered
[    0.462379] pnp 00:07: IRQ 12 override to level, low
[    0.462382] PCI: setting IRQ 12 as level-triggered
[    0.463211] pnp: PnP ACPI: found 10 devices
[    0.463213] ACPI: ACPI bus type pnp unregistered
[    0.463219] PnPBIOS: Disabled by ACPI PNP
[    0.464388] PCI: Using ACPI for IRQ routing
[    0.464518] NET: Registered protocol family 8
[    0.464518] NET: Registered protocol family 20
[    0.464518] NetLabel: Initializing
[    0.464518] NetLabel:  domain hash size = 128
[    0.464518] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.464518] NetLabel:  unlabeled traffic allowed by default
[    0.464518] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.464518]    actual entries 65620
[    0.464551] AppArmor: AppArmor Filesystem Enabled
[    0.464577] system 00:04: ioport range 0x8000-0x80be has been reserved
[    0.464577] system 00:04: ioport range 0x8100-0x812f has been reserved
[    0.464577] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.464577] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.464577] system 00:04: ioport range 0x200-0x20f has been reserved
[    0.464577] system 00:04: ioport range 0x290-0x297 has been reserved
[    0.464577] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.464577] system 00:04: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.464577] system 00:04: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.464577] system 00:04: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.464577] system 00:04: iomem range 0xffc00000-0xffc00fff has been reserved
[    0.464577] system 00:04: iomem range 0xffe00000-0xffe00fff has been reserved
[    0.464577] system 00:04: iomem range 0xffe80000-0xffefffff has been reserved
[    0.500329] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.500334] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.500341] pci 0000:00:01.0:   MEM window: 0xb0000000-0xb00fffff
[    0.500346] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.500364] pci 0000:00:01.0: setting latency timer to 64
[    0.500369] bus: 00 index 0 io port: [0, ffff]
[    0.500371] bus: 00 index 1 mmio: [0, ffffffff]
[    0.500374] bus: 01 index 0 io port: [9000, 9fff]
[    0.500377] bus: 01 index 1 mmio: [b0000000, b00fffff]
[    0.500379] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    0.500382] bus: 01 index 3 mmio: [0, 0]
[    0.500393] NET: Registered protocol family 2
[    0.500548] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.500855] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.501638] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.502189] TCP: Hash tables configured (established 131072 bind 65536)
[    0.502194] TCP reno registered
[    0.502410] NET: Registered protocol family 1
[    0.502584] checking if image is initramfs... it is
[    1.004087] Switched to high resolution mode on CPU 0
[    1.323021] Freeing initrd memory: 8011k freed
[    1.323906] audit: initializing netlink socket (disabled)
[    1.323933] type=2000 audit(1235994036.320:1): initialized
[    1.331013] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.333698] VFS: Disk quotas dquot_6.5.1
[    1.333809] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.333940] msgmni has been set to 1759
[    1.334089] io scheduler noop registered
[    1.334092] io scheduler anticipatory registered
[    1.334096] io scheduler deadline registered
[    1.334110] io scheduler cfq registered (default)
[    1.334167] pci 0000:01:00.0: Boot video device
[    1.334550] isapnp: Scanning for PnP cards...
[    1.688271] isapnp: No Plug & Play device found
[    1.729185] hpet_acpi_add: no address or irqs in _CRS
[    1.729260] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.731828] brd: module loaded
[    1.731916] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.732114] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.735423] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.738760] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.738766] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.738770] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.738773] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.738775] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.739277] mice: PS/2 mouse device common for all mice
[    1.739446] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.739466] rtc0: alarms up to one year, y3k
[    1.739602] EISA: Probing bus 0 at eisa.0
[    1.739612] Cannot allocate resource for EISA slot 1
[    1.739638] Cannot allocate resource for EISA slot 8
[    1.739640] EISA: Detected 0 cards.
[    1.739644] cpuidle: using governor ladder
[    1.739648] cpuidle: using governor menu
[    1.740293] TCP cubic registered
[    1.740329] Using IPI No-Shortcut mode
[    1.740557] registered taskstats version 1
[    1.740658]   Magic number: 1:428:680
[    1.740848] rtc_cmos 00:02: setting system clock to 2009-03-02 11:40:37 UTC (1235994037)
[    1.740852] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.740855] EDD information not available.
[    1.741128] Freeing unused kernel memory: 424k freed
[    1.741171] Write protecting the kernel text: 2580k
[    1.741202] Write protecting the kernel read-only data: 940k
[    1.776426] input: AT Raw Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.888636] fuse init (API version 7.9)
[    1.917996] ACPI: SSDT 37D9389E, 0518 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[    1.918728] Monitor-Mwait will be used to enter C-1 state
[    1.918732] Monitor-Mwait will be used to enter C-2 state
[    1.918736] Monitor-Mwait will be used to enter C-3 state
[    1.919007] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.919081] processor ACPI0007:00: registered as cooling_device0
[    1.919088] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.928113] Marking TSC unstable due to TSC halts in idle
[    1.930911] thermal LNXTHERM:01: registered as thermal_zone0
[    1.933321] ACPI: Thermal Zone [TZ01] (26 C)
[    2.468241] No dock devices found.
[    2.539028] SCSI subsystem initialized
[    2.579534] usbcore: registered new interface driver usbfs
[    2.579569] usbcore: registered new interface driver hub
[    2.579630] usbcore: registered new device driver usb
[    2.625897] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 7
[    2.625903] PCI: setting IRQ 7 as level-triggered
[    2.625908] ehci_hcd 0000:00:03.3: PCI INT C -> Link[LNKG] -> GSI 7 (level, low) -> IRQ 7
[    2.625926] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    2.625987] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    2.626029] ehci_hcd 0000:00:03.3: irq 7, io mem 0xb0106000
[    2.636054] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.636257] usb usb1: configuration #1 chosen from 1 choice
[    2.636290] hub 1-0:1.0: USB hub found
[    2.636301] hub 1-0:1.0: 8 ports detected
[    2.649492] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.661142] libata version 3.00 loaded.
[    2.844365] pata_sis 0000:00:02.5: version 0.5.2
[    2.844679] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    2.844683] PCI: setting IRQ 9 as level-triggered
[    2.844688] pata_sis 0000:00:02.5: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    2.845196] scsi0 : pata_sis
[    2.845311] scsi1 : pata_sis
[    2.845704] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    2.845707] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    3.012064] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    3.024415] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632H, CH01, max UDMA/33
[    3.056343] ata1.00: configured for UDMA/33
[    3.056401] ata2: port disabled. ignoring.
[    3.060235] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  CH01 PQ: 0 ANSI: 5
[    3.060665] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    3.060669] PCI: setting IRQ 11 as level-triggered
[    3.060674] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    3.060696] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.060736] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    3.060756] ohci_hcd 0000:00:03.0: irq 11, io mem 0xb0104000
[    3.118257] usb usb2: configuration #1 chosen from 1 choice
[    3.118292] hub 2-0:1.0: USB hub found
[    3.118304] hub 2-0:1.0: 4 ports detected
[    3.324557] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[    3.324562] PCI: setting IRQ 10 as level-triggered
[    3.324568] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    3.324589] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.324624] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    3.324643] ohci_hcd 0000:00:03.1: irq 10, io mem 0xb0105000
[    3.382360] usb usb3: configuration #1 chosen from 1 choice
[    3.382538] hub 3-0:1.0: USB hub found
[    3.382549] hub 3-0:1.0: 4 ports detected
[    3.488211] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    3.488216] PCI: setting IRQ 5 as level-triggered
[    3.488221] pata_acpi 0000:00:05.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    3.488267] pata_acpi 0000:00:05.0: PCI INT A disabled
[    3.497863] sata_sis 0000:00:05.0: version 1.0
[    3.497885] sata_sis 0000:00:05.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    3.497893] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    3.505219] scsi2 : sata_sis
[    3.507124] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.508690] scsi3 : sata_sis
[    3.509345] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 5
[    3.509348] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 5
[    3.536334] Driver 'sr' needs updating - please use bus_type methods
[    3.550813] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.550819] Uniform CD-ROM driver Revision: 3.20
[    3.550946] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.699481] usb 1-6: configuration #1 chosen from 1 choice
[    3.719570] ata3.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    3.719575] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.733267] ata3.00: configured for UDMA/133
[    3.884075] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    3.898991] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    3.899188] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    3.938780] Driver 'sd' needs updating - please use bus_type methods
[    3.938910] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    3.938929] sd 2:0:0:0: [sda] Write Protect is off
[    3.938932] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.938962] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.939043] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    3.939061] sd 2:0:0:0: [sda] Write Protect is off
[    3.939063] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.939093] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.939098]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    4.027806] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.096244] usb 2-3: configuration #1 chosen from 1 choice
[    4.098841] usbcore: registered new interface driver libusual
[    4.112653] Initializing USB Mass Storage driver...
[    4.121445] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.121579] usbcore: registered new interface driver usb-storage
[    4.121584] USB Mass Storage support registered.
[    4.121589] usb-storage: device found at 3
[    4.121591] usb-storage: waiting for device to settle before scanning
[    4.128441] usbcore: registered new interface driver hiddev
[    4.135471] input: USB Optical Mouse as /devices/pci0000:00/0000:00:03.0/usb2/2-3/2-3:1.0/input/input2
[    4.138137] input,hiddev96,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:03.0-3
[    4.138165] usbcore: registered new interface driver usbhid
[    4.138170] usbhid: v2.6:USB HID core driver
[    4.456351] PM: Starting manual resume from disk
[    4.456356] PM: Resume from partition 8:10
[    4.456358] PM: Checking hibernation image.
[    4.456594] PM: Resume from disk failed.
[    4.503119] kjournald starting.  Commit interval 5 seconds
[    4.503137] EXT3-fs: mounted filesystem with ordered data mode.
[    9.120379] usb-storage: device scan complete
[    9.126721] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    9.128077] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    9.128242] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   10.251589] udevd version 124 started
[   10.800233] Linux agpgart interface v0.103
[   10.832774] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   10.920214] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.968055] agpgart-sis 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[   10.983803] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.072226] sis190 Gigabit Ethernet driver 1.2 loaded.
[   11.072509] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[   11.072513] PCI: setting IRQ 3 as level-triggered
[   11.072518] sis190 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 3 (level, low) -> IRQ 3
[   11.072531] sis190 0000:00:04.0: setting latency timer to 64
[   11.072543] 0000:00:04.0: Read MAC address from EEPROM
[   11.160031] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[   11.616316] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.628064] ACPI: Power Button (FF) [PWRF]
[   11.628269] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   11.644032] ACPI: Power Button (CM) [PWRB]
[   11.644149] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   11.660064] ACPI: Sleep Button (CM) [SLPB]
[   11.660212] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input6
[   11.660643] ACPI: Lid Switch [LID0]
[   11.661158] ACPI: AC Adapter [AC0] (on-line)
[   11.672032] 0000:00:04.0: Using transceiver at address 1 as default.
[   11.704436] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f899a000 (IRQ: 3), 00:03:0d:af:c3:b5
[   11.704440] eth0: GMII mode.
[   11.704447] eth0: Enabling Auto-negotiation.
[   11.723036] ACPI: Battery Slot [BAT0] (battery absent)
[   12.704546] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
[   12.704551] PCI: setting IRQ 4 as level-triggered
[   12.704556] HDA Intel 0000:00:0f.0: PCI INT A -> Link[LNKC] -> GSI 4 (level, low) -> IRQ 4
[   12.704584] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   12.732807] acpi device:0f: registered as cooling_device1
[   12.732976] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/device:0d/input/input7
[   12.737934] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   12.748044] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   13.604132] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   13.946656] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000
[   13.984742] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   16.239773] lp: driver loaded but no devices found
[   16.333370] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   16.437522] usbcore: registered new interface driver ndiswrapper
[   16.541083] Adding 979924k swap on /dev/sda10.  Priority:-1 extents:1 across:979924k
[   16.570909] EXT3 FS on sda8, internal journal
[   16.815022] kjournald starting.  Commit interval 5 seconds
[   16.815283] EXT3 FS on sda6, internal journal
[   16.815290] EXT3-fs: mounted filesystem with ordered data mode.
[   16.870365] kjournald starting.  Commit interval 5 seconds
[   16.870711] EXT3 FS on sda9, internal journal
[   16.870717] EXT3-fs: mounted filesystem with ordered data mode.
[   16.906187] kjournald starting.  Commit interval 5 seconds
[   16.906526] EXT3 FS on sda7, internal journal
[   16.906532] EXT3-fs: mounted filesystem with ordered data mode.
[   17.171583] type=1505 audit(1235965253.101:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3897
[   17.375977] type=1505 audit(1235965253.305:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3902
[   17.376344] type=1505 audit(1235965253.309:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3902
[   17.551374] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.023541] NET: Registered protocol family 17
[   19.985367] ACPI: WMI: Mapper loaded
[   20.794315] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   20.865013] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   20.865020] apm: overridden by ACPI.
[   21.046505] ppdev: user-space parallel port driver
[   22.524614] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.524621] vboxdrv: Successfully done.
[   22.524624] vboxdrv: Found 1 processor cores.
[   22.526429] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.526437] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   22.715212] NET: Registered protocol family 10
[   22.717264] lo: Disabled Privacy Extensions
[   24.986493] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.127606] [drm] Initialized drm 1.1.0 20060810
[   30.133224] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[   30.133235] pci 0000:01:00.0: setting latency timer to 64
[   30.134945] [drm] Initialized sis 1.3.0 20070626 on minor 0
[   30.136249] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
[   30.136277] agpgart-sis 0000:00:00.0: putting AGP V3 device into 4x mode
[   30.136328] pci 0000:01:00.0: putting AGP V3 device into 4x mode
[   34.066890] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   35.008031] eth0: auto-negotiating...
[   45.032827] eth0: auto-negotiating...
[   50.173022] scim-bridge[5574]: segfault at 53454741 ip b7f2d9ad sp bf9ccea0 error 4 in libscim-1.0.so.8.2.3[b7ecc000+c6000]
[   55.056075] eth0: auto-negotiating...
[   55.708960] CPU0 attaching NULL sched-domain.
[   55.716382] CPU0 attaching NULL sched-domain.
[   65.080079] eth0: auto-negotiating...
[   74.440074] usb 1-1: new high speed USB device using ehci_hcd and address 4
[   74.588929] usb 1-1: configuration #1 chosen from 1 choice
[   74.708044] usb 1-1: reset high speed USB device using ehci_hcd and address 4

```


Why my poor celeron dual-core is discriminated as a single core :confused:
Any help will be very appreciated!

Edit: top and system monitor also say it's a single core
Edit 2: I have 8.10 ubuntu on it and I think the kernel supports dual core
```
 uname -a
Linux coppen-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux 
```

Edit 3:  lshw seems able to recognize it as dual core.

```
coppen-laptop
    description: Notebook
    product: @A
    vendor: OEM

    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled 
  *-core
       description: Motherboard
       product: N/A
       vendor: OEM
       physical id: 0
       version: N/A

     *-firmware
          description: BIOS
          vendor: OEM
          physical id: 0
          version: 1.13 (07/05/2008)
          size: 107KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T1600  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13

          slot: uPGA 479M
          size: 1600MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 1MiB
          capabilities: burst internal write-back
     
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13

          size: 1700MHz
          capabilities: ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
```

edit: Am I posting on a wrong board?

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

