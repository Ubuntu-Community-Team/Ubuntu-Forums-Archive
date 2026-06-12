---
title: "fails to boot (screen goes black) about 1/6 times"
date: 2009-05-23
forum: General Help
---

### Post by PGScooter on 2009-05-23
Hi,

A desktop computer is failing to boot about 1 out of 6 times. It is running Xubuntu 8.04 32-bit. I do not have many packages installed and the problem has existed since I installed it.

Below I've posted my kern.log file. 15:28:34 is the timestamp where it failed to boot. All of the boots after that in the posted kern.log have worked fine. I compared it to the others and didn't see any problem, but I do not understand most of the kern.log. I would really like to get this computer stable.

Is there any other file or log or output that would be of help? Any ideas? Could this be an xorg problem?

Notes:
-I never put the computer on standby or hibernate, all of these boots are after clean shutdowns, except when there is a failed boot, I must turn off the computer with the power button.
-By "failed boot" I mean that the screen does not come up (it is like there is a permanent screen saver). The computer seems to boot normally besides the screen. This is why I am blindly guessing its an xorg problem.

Thanks!

```

May 22 15:28:34 bettyhost kernel: Inspecting /boot/System.map-2.6.24-24-generic
May 22 15:28:34 bettyhost kernel: Loaded 27917 symbols from /boot/System.map-2.6.24-24-generic.
May 22 15:28:34 bettyhost kernel: Symbols match kernel version 2.6.24.
May 22 15:28:34 bettyhost kernel: Loaded 15166 symbols from 84 modules.
May 22 15:28:34 bettyhost kernel: [    0.000000] Initializing cgroup subsys cpuset
May 22 15:28:34 bettyhost kernel: [    0.000000] Initializing cgroup subsys cpu
May 22 15:28:34 bettyhost kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Wed Apr 15 15:54:25 UTC 2009 (Ubuntu 2.6.24-24.53-generic)
May 22 15:28:34 bettyhost kernel: [    0.000000] BIOS-provided physical RAM map:
May 22 15:28:34 bettyhost kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 22 15:28:34 bettyhost kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 22 15:28:34 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 22 15:28:34 bettyhost kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fef0000 (usable)
May 22 15:28:34 bettyhost kernel: [    0.000000]  BIOS-e820: 000000002fef0000 - 000000002fef3000 (ACPI NVS)
May 22 15:28:34 bettyhost kernel: [    0.000000]  BIOS-e820: 000000002fef3000 - 000000002ff00000 (ACPI data)
May 22 15:28:34 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May 22 15:28:34 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May 22 15:28:34 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
May 22 15:28:34 bettyhost kernel: [    0.000000] 0MB HIGHMEM available.
May 22 15:28:34 bettyhost kernel: [    0.000000] 766MB LOWMEM available.
May 22 15:28:34 bettyhost kernel: [    0.000000] found SMP MP-table at 000f4ba0
May 22 15:28:34 bettyhost kernel: [    0.000000] Entering add_active_range(0, 0, 196336) 0 entries of 256 used
May 22 15:28:34 bettyhost kernel: [    0.000000] Zone PFN ranges:
May 22 15:28:34 bettyhost kernel: [    0.000000]   DMA             0 ->     4096
May 22 15:28:34 bettyhost kernel: [    0.000000]   Normal       4096 ->   196336
May 22 15:28:34 bettyhost kernel: [    0.000000]   HighMem    196336 ->   196336
May 22 15:28:34 bettyhost kernel: [    0.000000] Movable zone start PFN for each node
May 22 15:28:34 bettyhost kernel: [    0.000000] early_node_map[1] active PFN ranges
May 22 15:28:34 bettyhost kernel: [    0.000000]     0:        0 ->   196336
May 22 15:28:34 bettyhost kernel: [    0.000000] On node 0 totalpages: 196336
May 22 15:28:34 bettyhost kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 22 15:28:34 bettyhost kernel: [    0.000000]   DMA zone: 0 pages reserved
May 22 15:28:34 bettyhost kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May 22 15:28:34 bettyhost kernel: [    0.000000]   Normal zone: 1501 pages used for memmap
May 22 15:28:34 bettyhost kernel: [    0.000000]   Normal zone: 190739 pages, LIFO batch:31
May 22 15:28:34 bettyhost kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
May 22 15:28:34 bettyhost kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 22 15:28:34 bettyhost kernel: [    0.000000] DMI 2.3 present.
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6D40 checksum 0
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: RSDP 000F6D40, 0014 (r0 IntelR)
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: RSDT 2FEF3000, 0030 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: FACP 2FEF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: DSDT 2FEF30C0, 3543 (r1 INTELR AWRDACPI     1000 MSFT  100000C)
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: FACS 2FEF0000, 0040
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: BOOT 2FEF6640, 0028 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: APIC 2FEF6680, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May 22 15:28:34 bettyhost kernel: [    0.000000] Processor #0 15:1 APIC version 20
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May 22 15:28:34 bettyhost kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: IRQ0 used by override.
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: IRQ2 used by override.
May 22 15:28:34 bettyhost kernel: [    0.000000] ACPI: IRQ9 used by override.
May 22 15:28:34 bettyhost kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May 22 15:28:34 bettyhost kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 22 15:28:34 bettyhost kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2ff00000:ced00000)
May 22 15:28:34 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May 22 15:28:34 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
May 22 15:28:34 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
May 22 15:28:34 bettyhost kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194803
May 22 15:28:34 bettyhost kernel: [    0.000000] Kernel command line: root=UUID=3bd8db4a-33f3-4f2f-b16e-13aadf7a2cf1 ro quiet splash
May 22 15:28:34 bettyhost kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May 22 15:28:34 bettyhost kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May 22 15:28:34 bettyhost kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 22 15:28:34 bettyhost kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May 22 15:28:34 bettyhost kernel: [    0.000000] Initializing CPU#0
May 22 15:28:34 bettyhost kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May 22 15:28:34 bettyhost kernel: [    0.000000] Detected 1794.309 MHz processor.
May 22 15:28:34 bettyhost kernel: [    9.064868] Console: colour VGA+ 80x25
May 22 15:28:34 bettyhost kernel: [    9.064873] console [tty0] enabled
May 22 15:28:34 bettyhost kernel: [    9.065842] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May 22 15:28:34 bettyhost kernel: [    9.067306] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May 22 15:28:34 bettyhost kernel: [    9.094673] Memory: 766332k/785344k available (2179k kernel code, 18404k reserved, 1008k data, 368k init, 0k highmem)
May 22 15:28:34 bettyhost kernel: [    9.094687] virtual kernel memory layout:
May 22 15:28:34 bettyhost kernel: [    9.094689]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May 22 15:28:34 bettyhost kernel: [    9.094691]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May 22 15:28:34 bettyhost kernel: [    9.094692]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May 22 15:28:34 bettyhost kernel: [    9.094694]     lowmem  : 0xc0000000 - 0xefef0000   ( 766 MB)
May 22 15:28:34 bettyhost kernel: [    9.094696]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
May 22 15:28:34 bettyhost kernel: [    9.094697]       .data : 0xc0320d78 - 0xc041cdc4   (1008 kB)
May 22 15:28:34 bettyhost kernel: [    9.094699]       .text : 0xc0100000 - 0xc0320d78   (2179 kB)
May 22 15:28:34 bettyhost kernel: [    9.094704] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May 22 15:28:34 bettyhost kernel: [    9.094759] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
May 22 15:28:34 bettyhost kernel: [    9.174689] Calibrating delay using timer specific routine.. 3592.43 BogoMIPS (lpj=7184872)
May 22 15:28:34 bettyhost kernel: [    9.174732] Security Framework initialized
May 22 15:28:34 bettyhost kernel: [    9.174743] SELinux:  Disabled at boot.
May 22 15:28:34 bettyhost kernel: [    9.174764] AppArmor: AppArmor initialized
May 22 15:28:34 bettyhost kernel: [    9.174771] Failure registering capabilities with primary security module.
May 22 15:28:34 bettyhost kernel: [    9.174786] Mount-cache hash table entries: 512
May 22 15:28:34 bettyhost kernel: [    9.175015] Initializing cgroup subsys ns
May 22 15:28:34 bettyhost kernel: [    9.175025] Initializing cgroup subsys cpuacct
May 22 15:28:34 bettyhost kernel: [    9.175046] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
May 22 15:28:34 bettyhost kernel: [    9.175066] CPU: Trace cache: 12K uops, L1 D cache: 8K
May 22 15:28:34 bettyhost kernel: [    9.175070] CPU: L2 cache: 128K
May 22 15:28:34 bettyhost kernel: [    9.175074] CPU: Hyper-Threading is disabled
May 22 15:28:34 bettyhost kernel: [    9.175079] CPU: After all inits, caps: 3febfbff 00000000 00000000 00043080 00000000 00000000 00000000 00000000
May 22 15:28:34 bettyhost kernel: [    9.175098] Compat vDSO mapped to ffffe000.
May 22 15:28:34 bettyhost kernel: [    9.175120] Checking 'hlt' instruction... OK.
May 22 15:28:34 bettyhost kernel: [    9.191281] SMP alternatives: switching to UP code
May 22 15:28:34 bettyhost kernel: [    9.193829] Freeing SMP alternatives: 11k freed
May 22 15:28:34 bettyhost kernel: [    9.194060] Early unpacking initramfs... done
May 22 15:28:34 bettyhost kernel: [    9.722307] ACPI: Core revision 20070126
May 22 15:28:34 bettyhost kernel: [    9.722387] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 22 15:28:34 bettyhost kernel: [    9.728084] CPU0: Intel(R) Celeron(R) CPU 1.80GHz stepping 03
May 22 15:28:34 bettyhost kernel: [    9.728143] Total of 1 processors activated (3592.43 BogoMIPS).
May 22 15:28:34 bettyhost kernel: [    9.728291] ENABLING IO-APIC IRQs
May 22 15:28:34 bettyhost kernel: [    9.728493] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May 22 15:28:34 bettyhost kernel: [    9.873954] Brought up 1 CPUs
May 22 15:28:34 bettyhost kernel: [    9.873991] CPU0 attaching sched-domain:
May 22 15:28:34 bettyhost kernel: [    9.873996]  domain 0: span 01
May 22 15:28:34 bettyhost kernel: [    9.873999]   groups: 01
May 22 15:28:34 bettyhost kernel: [    9.874422] net_namespace: 64 bytes
May 22 15:28:34 bettyhost kernel: [    9.874440] Booting paravirtualized kernel on bare hardware
May 22 15:28:34 bettyhost kernel: [    9.875421] Time: 22:27:48  Date: 05/22/09
May 22 15:28:34 bettyhost kernel: [    9.875478] NET: Registered protocol family 16
May 22 15:28:34 bettyhost kernel: [    9.876207] EISA bus registered
May 22 15:28:34 bettyhost kernel: [    9.876252] ACPI: bus type pci registered
May 22 15:28:34 bettyhost kernel: [    9.902955] PCI: PCI BIOS revision 2.10 entry at 0xfaea0, last bus=1
May 22 15:28:34 bettyhost kernel: [    9.902960] PCI: Using configuration type 1
May 22 15:28:34 bettyhost kernel: [    9.902985] Setting up standard PCI resources
May 22 15:28:34 bettyhost kernel: [    9.917814] ACPI: EC: Look up EC in DSDT
May 22 15:28:34 bettyhost kernel: [    9.922470] ACPI: Interpreter enabled
May 22 15:28:34 bettyhost kernel: [    9.922479] ACPI: (supports S0 S1 S3 S4 S5)
May 22 15:28:34 bettyhost kernel: [    9.922509] ACPI: Using IOAPIC for interrupt routing
May 22 15:28:34 bettyhost kernel: [    9.932481] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 22 15:28:34 bettyhost kernel: [    9.933146] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
May 22 15:28:34 bettyhost kernel: [    9.933149] * this clock source is slow. If you are sure your timer does not have
May 22 15:28:34 bettyhost kernel: [    9.933151] * this bug, please use "acpi_pm_good" to disable the workaround
May 22 15:28:34 bettyhost kernel: [    9.933209] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
May 22 15:28:34 bettyhost kernel: [    9.933214] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
May 22 15:28:34 bettyhost kernel: [    9.933890] PCI: Transparent bridge - 0000:00:1e.0
May 22 15:28:34 bettyhost kernel: [    9.933938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 22 15:28:34 bettyhost kernel: [    9.934202] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May 22 15:28:34 bettyhost kernel: [    9.957395] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May 22 15:28:34 bettyhost kernel: [    9.957586] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May 22 15:28:34 bettyhost kernel: [    9.957812] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May 22 15:28:34 bettyhost kernel: [    9.958009] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May 22 15:28:34 bettyhost kernel: [    9.958190] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 22 15:28:34 bettyhost kernel: [    9.958366] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 22 15:28:34 bettyhost kernel: [    9.958543] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 22 15:28:34 bettyhost kernel: [    9.958720] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May 22 15:28:34 bettyhost kernel: [    9.959112] Linux Plug and Play Support v0.97 (c) Adam Belay
May 22 15:28:34 bettyhost kernel: [    9.959231] pnp: PnP ACPI init
May 22 15:28:34 bettyhost kernel: [    9.959252] ACPI: bus type pnp registered
May 22 15:28:34 bettyhost kernel: [    9.964581] pnp: PnP ACPI: found 12 devices
May 22 15:28:34 bettyhost kernel: [    9.964590] ACPI: ACPI bus type pnp unregistered
May 22 15:28:34 bettyhost kernel: [    9.964597] PnPBIOS: Disabled by ACPI PNP
May 22 15:28:34 bettyhost kernel: [    9.965454] PCI: Using ACPI for IRQ routing
May 22 15:28:34 bettyhost kernel: [    9.965462] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 22 15:28:34 bettyhost kernel: [    9.985808] NET: Registered protocol family 8
May 22 15:28:34 bettyhost kernel: [    9.985814] NET: Registered protocol family 20
May 22 15:28:34 bettyhost kernel: [    9.986032] AppArmor: AppArmor Filesystem Enabled
May 22 15:28:34 bettyhost kernel: [    9.989703] Time: tsc clocksource has been installed.
May 22 15:28:34 bettyhost kernel: [    9.997850] system 00:00: iomem range 0xcc000-0xcffff has been reserved
May 22 15:28:34 bettyhost kernel: [    9.997856] system 00:00: iomem range 0xd6800-0xd7fff has been reserved
May 22 15:28:34 bettyhost kernel: [    9.997861] system 00:00: iomem range 0xf0000-0xfbfff could not be reserved
May 22 15:28:34 bettyhost kernel: [    9.997865] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
May 22 15:28:34 bettyhost kernel: [    9.997869] system 00:00: iomem range 0x2fef0000-0x2fefffff could not be reserved
May 22 15:28:34 bettyhost kernel: [    9.997873] system 00:00: iomem range 0x0-0x9ffff could not be reserved
May 22 15:28:34 bettyhost kernel: [    9.997877] system 00:00: iomem range 0x100000-0x2feeffff could not be reserved
May 22 15:28:34 bettyhost kernel: [    9.997882] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
May 22 15:28:34 bettyhost kernel: [    9.997887] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
May 22 15:28:34 bettyhost kernel: [    9.997891] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
May 22 15:28:34 bettyhost kernel: [    9.997896] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
May 22 15:28:34 bettyhost kernel: [    9.997900] system 00:00: iomem range 0xe0000-0xeffff has been reserved
May 22 15:28:34 bettyhost kernel: [    9.997911] system 00:02: ioport range 0x400-0x4bf could not be reserved
May 22 15:28:34 bettyhost kernel: [    9.997921] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May 22 15:28:34 bettyhost kernel: [    9.997925] system 00:03: ioport range 0x800-0x87f has been reserved
May 22 15:28:34 bettyhost kernel: [   10.029424] PCI: Bridge: 0000:00:1e.0
May 22 15:28:34 bettyhost kernel: [   10.029432]   IO window: c000-cfff
May 22 15:28:34 bettyhost kernel: [   10.029439]   MEM window: ec000000-edffffff
May 22 15:28:34 bettyhost kernel: [   10.029444]   PREFETCH window: disabled.
May 22 15:28:34 bettyhost kernel: [   10.029462] PCI: Setting latency timer of device 0000:00:1e.0 to 64
May 22 15:28:34 bettyhost kernel: [   10.029486] NET: Registered protocol family 2
May 22 15:28:34 bettyhost kernel: [   10.065744] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May 22 15:28:34 bettyhost kernel: [   10.066377] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May 22 15:28:34 bettyhost kernel: [   10.068139] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May 22 15:28:34 bettyhost kernel: [   10.069056] TCP: Hash tables configured (established 131072 bind 65536)
May 22 15:28:34 bettyhost kernel: [   10.069063] TCP reno registered
May 22 15:28:34 bettyhost kernel: [   10.077869] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
May 22 15:28:34 bettyhost kernel: [   10.539420]  it is
May 22 15:28:34 bettyhost kernel: [   11.073964] Freeing initrd memory: 7310k freed
May 22 15:28:34 bettyhost kernel: [   11.074301] Simple Boot Flag at 0x59 set to 0x1
May 22 15:28:34 bettyhost kernel: [   11.075601] audit: initializing netlink socket (disabled)
May 22 15:28:34 bettyhost kernel: [   11.075625] audit(1243031268.876:1): initialized
May 22 15:28:34 bettyhost kernel: [   11.081590] VFS: Disk quotas dquot_6.5.1
May 22 15:28:34 bettyhost kernel: [   11.081807] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 22 15:28:34 bettyhost kernel: [   11.082196] io scheduler noop registered
May 22 15:28:34 bettyhost kernel: [   11.082202] io scheduler anticipatory registered
May 22 15:28:34 bettyhost kernel: [   11.082204] io scheduler deadline registered
May 22 15:28:34 bettyhost kernel: [   11.082244] io scheduler cfq registered (default)
May 22 15:28:34 bettyhost kernel: [   11.082263] Boot video device is 0000:00:02.0
May 22 15:28:34 bettyhost kernel: [   11.083262] isapnp: Scanning for PnP cards...
May 22 15:28:34 bettyhost kernel: [   11.437316] isapnp: No Plug & Play device found
May 22 15:28:34 bettyhost kernel: [   11.595977] Real Time Clock Driver v1.12ac
May 22 15:28:34 bettyhost kernel: [   11.596265] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 22 15:28:34 bettyhost kernel: [   11.596513] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 22 15:28:34 bettyhost kernel: [   11.598775] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 22 15:28:34 bettyhost kernel: [   11.599317] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
May 22 15:28:34 bettyhost kernel: [   11.608066] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 22 15:28:34 bettyhost kernel: [   11.608263] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 22 15:28:34 bettyhost kernel: [   11.608582] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May 22 15:28:34 bettyhost kernel: [   11.608589] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May 22 15:28:34 bettyhost kernel: [   11.609310] serio: i8042 KBD port at 0x60,0x64 irq 1
May 22 15:28:34 bettyhost kernel: [   11.612056] mice: PS/2 mouse device common for all mice
May 22 15:28:34 bettyhost kernel: [   11.612464] EISA: Probing bus 0 at eisa.0
May 22 15:28:34 bettyhost kernel: [   11.612509] EISA: Detected 0 cards.
May 22 15:28:34 bettyhost kernel: [   11.612514] cpuidle: using governor ladder
May 22 15:28:34 bettyhost kernel: [   11.612517] cpuidle: using governor menu
May 22 15:28:34 bettyhost kernel: [   11.612690] NET: Registered protocol family 1
May 22 15:28:34 bettyhost kernel: [   11.612749] Using IPI No-Shortcut mode
May 22 15:28:34 bettyhost kernel: [   11.612815] registered taskstats version 1
May 22 15:28:34 bettyhost kernel: [   11.612966]   Magic number: 9:906:502
May 22 15:28:34 bettyhost kernel: [   11.613127] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 22 15:28:34 bettyhost kernel: [   11.613130] EDD information not available.
May 22 15:28:34 bettyhost kernel: [   11.613748] Freeing unused kernel memory: 368k freed
May 22 15:28:34 bettyhost kernel: [   11.613802] Write protecting the kernel read-only data: 806k
May 22 15:28:34 bettyhost kernel: [   11.634150] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May 22 15:28:34 bettyhost kernel: [   13.035289] fuse init (API version 7.9)
May 22 15:28:34 bettyhost kernel: [   13.079502] ACPI: Processor [CPU0] (supports 2 throttling states)
May 22 15:28:34 bettyhost kernel: [   14.036716] usbcore: registered new interface driver usbfs
May 22 15:28:34 bettyhost kernel: [   14.036760] usbcore: registered new interface driver hub
May 22 15:28:34 bettyhost kernel: [   14.052617] usbcore: registered new device driver usb
May 22 15:28:34 bettyhost kernel: [   14.064596] USB Universal Host Controller Interface driver v3.0
May 22 15:28:34 bettyhost kernel: [   14.067845] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
May 22 15:28:34 bettyhost kernel: [   14.067867] PCI: Setting latency timer of device 0000:00:1d.0 to 64
May 22 15:28:34 bettyhost kernel: [   14.067873] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May 22 15:28:34 bettyhost kernel: [   14.068387] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May 22 15:28:34 bettyhost kernel: [   14.068430] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000d800
May 22 15:28:34 bettyhost kernel: [   14.068748] usb usb1: configuration #1 chosen from 1 choice
May 22 15:28:34 bettyhost kernel: [   14.068802] hub 1-0:1.0: USB hub found
May 22 15:28:34 bettyhost kernel: [   14.068817] hub 1-0:1.0: 2 ports detected
May 22 15:28:34 bettyhost kernel: [   14.139929] SCSI subsystem initialized
May 22 15:28:34 bettyhost kernel: [   14.172590] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
May 22 15:28:34 bettyhost kernel: [   14.172609] PCI: Setting latency timer of device 0000:00:1d.1 to 64
May 22 15:28:34 bettyhost kernel: [   14.172615] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May 22 15:28:34 bettyhost kernel: [   14.172673] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May 22 15:28:34 bettyhost kernel: [   14.172712] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000d000
May 22 15:28:34 bettyhost kernel: [   14.172920] usb usb2: configuration #1 chosen from 1 choice
May 22 15:28:34 bettyhost kernel: [   14.172975] hub 2-0:1.0: USB hub found
May 22 15:28:34 bettyhost kernel: [   14.172987] hub 2-0:1.0: 2 ports detected
May 22 15:28:34 bettyhost kernel: [   14.249987] libata version 3.00 loaded.
May 22 15:28:34 bettyhost kernel: [   14.276467] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
May 22 15:28:34 bettyhost kernel: [   14.276490] PCI: Setting latency timer of device 0000:00:1d.2 to 64
May 22 15:28:34 bettyhost kernel: [   14.276496] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May 22 15:28:34 bettyhost kernel: [   14.276558] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May 22 15:28:34 bettyhost kernel: [   14.276596] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000d400
May 22 15:28:34 bettyhost kernel: [   14.276860] usb usb3: configuration #1 chosen from 1 choice
May 22 15:28:34 bettyhost kernel: [   14.276910] hub 3-0:1.0: USB hub found
May 22 15:28:34 bettyhost kernel: [   14.276924] hub 3-0:1.0: 2 ports detected
May 22 15:28:34 bettyhost kernel: [   14.380398] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
May 22 15:28:34 bettyhost kernel: [   14.380426] PCI: Setting latency timer of device 0000:00:1d.7 to 64
May 22 15:28:34 bettyhost kernel: [   14.380432] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May 22 15:28:34 bettyhost kernel: [   14.380499] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
May 22 15:28:34 bettyhost kernel: [   14.384441] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
May 22 15:28:34 bettyhost kernel: [   14.384459] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xee080000
May 22 15:28:34 bettyhost kernel: [   14.410135] Floppy drive(s): fd0 is 1.44M
May 22 15:28:34 bettyhost kernel: [   14.412147] usb 1-1: new full speed USB device using uhci_hcd and address 2
May 22 15:28:34 bettyhost kernel: [   14.424103] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May 22 15:28:34 bettyhost kernel: [   14.424334] usb usb4: configuration #1 chosen from 1 choice
May 22 15:28:34 bettyhost kernel: [   14.424387] hub 4-0:1.0: USB hub found
May 22 15:28:34 bettyhost kernel: [   14.424401] hub 4-0:1.0: 6 ports detected
May 22 15:28:34 bettyhost kernel: [   14.428249] FDC 0 is a post-1991 82077
May 22 15:28:34 bettyhost kernel: [   14.528358] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 17
May 22 15:28:34 bettyhost kernel: [   14.528375] 3c59x: Donald Becker and others.
May 22 15:28:34 bettyhost kernel: [   14.528383] 0000:01:04.0: 3Com PCI 3c905C Tornado at f0820000.
May 22 15:28:34 bettyhost kernel: [   14.555592] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 17 (level, low) -> IRQ 16
May 22 15:28:34 bettyhost kernel: [   14.571941] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
May 22 15:28:34 bettyhost kernel: [   14.571953] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
May 22 15:28:34 bettyhost kernel: [   14.571960] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
May 22 15:28:34 bettyhost kernel: [   14.612014] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
May 22 15:28:34 bettyhost kernel: [   14.612063] b44.c:v2.0
May 22 15:28:34 bettyhost kernel: [   14.612111] ata_piix 0000:00:1f.1: version 2.12
May 22 15:28:34 bettyhost kernel: [   14.612138] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
May 22 15:28:34 bettyhost kernel: [   14.612217] PCI: Setting latency timer of device 0000:00:1f.1 to 64
May 22 15:28:34 bettyhost kernel: [   14.614085] scsi0 : ata_piix
May 22 15:28:34 bettyhost kernel: [   14.616033] scsi1 : ata_piix
May 22 15:28:34 bettyhost kernel: [   14.616979] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May 22 15:28:34 bettyhost kernel: [   14.616986] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May 22 15:28:34 bettyhost kernel: [   14.632407] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0b:db:11:ac:ec
May 22 15:28:34 bettyhost kernel: [   14.787935] ata1.00: HPA unlocked: 58593750 -> 58633344, native 58633344
May 22 15:28:34 bettyhost kernel: [   14.787945] ata1.00: ATA-5: WDC WD300BB-75DEA0, 05.03E05, max UDMA/100
May 22 15:28:34 bettyhost kernel: [   14.787949] ata1.00: 58633344 sectors, multi 16: LBA 
May 22 15:28:34 bettyhost kernel: [   14.804822] ata1.00: configured for UDMA/100
May 22 15:28:34 bettyhost kernel: [   14.959664] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 22 15:28:34 bettyhost kernel: [   14.959670] ata2: failed to recover some devices, retrying in 5 secs
May 22 15:28:34 bettyhost kernel: [   15.275020] usb 1-1: new full speed USB device using uhci_hcd and address 3
May 22 15:28:34 bettyhost kernel: [   15.477629] usb 1-1: configuration #1 chosen from 1 choice
May 22 15:28:34 bettyhost kernel: [   15.718513] usb 1-2: new low speed USB device using uhci_hcd and address 4
May 22 15:28:34 bettyhost kernel: [   15.895008] usb 1-2: configuration #1 chosen from 1 choice
May 22 15:28:34 bettyhost kernel: [   15.924634] usbcore: registered new interface driver hiddev
May 22 15:28:34 bettyhost kernel: [   15.937219] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
May 22 15:28:34 bettyhost kernel: [   15.950220] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
May 22 15:28:34 bettyhost kernel: [   15.950250] usbcore: registered new interface driver usbhid
May 22 15:28:34 bettyhost kernel: [   15.950256] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
May 22 15:28:34 bettyhost kernel: [   20.113037] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 22 15:28:34 bettyhost kernel: [   20.113044] ata2: failed to recover some devices, retrying in 5 secs
May 22 15:28:34 bettyhost kernel: [   25.266485] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 22 15:28:34 bettyhost kernel: [   25.266492] ata2: failed to recover some devices, retrying in 5 secs
May 22 15:28:34 bettyhost kernel: [   30.583891] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-248F, R602, max UDMA/33
May 22 15:28:34 bettyhost kernel: [   30.755641] ata2.00: configured for UDMA/33
May 22 15:28:34 bettyhost kernel: [   30.755864] scsi 0:0:0:0: Direct-Access     ATA      WDC WD300BB-75DE 05.0 PQ: 0 ANSI: 5
May 22 15:28:34 bettyhost kernel: [   30.758411] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-248F  R602 PQ: 0 ANSI: 5
May 22 15:28:34 bettyhost kernel: [   30.788840] Driver 'sd' needs updating - please use bus_type methods
May 22 15:28:34 bettyhost kernel: [   30.789010] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
May 22 15:28:34 bettyhost kernel: [   30.789043] sd 0:0:0:0: [sda] Write Protect is off
May 22 15:28:34 bettyhost kernel: [   30.789048] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 22 15:28:34 bettyhost kernel: [   30.789093] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 22 15:28:34 bettyhost kernel: [   30.789217] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
May 22 15:28:34 bettyhost kernel: [   30.789247] sd 0:0:0:0: [sda] Write Protect is off
May 22 15:28:34 bettyhost kernel: [   30.789252] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 22 15:28:34 bettyhost kernel: [   30.789296] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 22 15:28:34 bettyhost kernel: [   30.789305]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May 22 15:28:34 bettyhost kernel: [   30.817003]  sda1 sda2 < sda5 >
May 22 15:28:34 bettyhost kernel: [   30.849034] sd 0:0:0:0: [sda] Attached SCSI disk
May 22 15:28:34 bettyhost kernel: [   30.863481] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 22 15:28:34 bettyhost kernel: [   30.863565] sr 1:0:0:0: Attached scsi generic sg1 type 5
May 22 15:28:34 bettyhost kernel: [   30.866508] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May 22 15:28:34 bettyhost kernel: [   30.866517] Uniform CD-ROM driver Revision: 3.20
May 22 15:28:34 bettyhost kernel: [   30.866609] sr 1:0:0:0: Attached scsi CD-ROM sr0
May 22 15:28:34 bettyhost kernel: [   31.310427] Attempting manual resume
May 22 15:28:34 bettyhost kernel: [   31.310435] swsusp: Resume From Partition 8:5
May 22 15:28:34 bettyhost kernel: [   31.310438] PM: Checking swsusp image.
May 22 15:28:34 bettyhost kernel: [   31.310695] PM: Resume from disk failed.
May 22 15:28:34 bettyhost kernel: [   31.375728] kjournald starting.  Commit interval 5 seconds
May 22 15:28:34 bettyhost kernel: [   31.375758] EXT3-fs: mounted filesystem with ordered data mode.
May 22 15:28:34 bettyhost kernel: [   44.557763] Linux agpgart interface v0.102
May 22 15:28:34 bettyhost kernel: [   44.658205] agpgart: Detected an Intel 830M Chipset.
May 22 15:28:34 bettyhost kernel: [   44.658410] agpgart: Detected 892K stolen memory.
May 22 15:28:34 bettyhost kernel: [   44.826818] agpgart: AGP aperture is 128M @ 0xe0000000
May 22 15:28:34 bettyhost kernel: [   44.826859] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
May 22 15:28:34 bettyhost kernel: [   45.045187] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 22 15:28:34 bettyhost kernel: [   45.089675] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 22 15:28:34 bettyhost kernel: [   45.182020] intel_rng: FWH not detected
May 22 15:28:34 bettyhost kernel: [   45.388394] iTCO_vendor_support: vendor-support=0
May 22 15:28:34 bettyhost kernel: [   45.421800] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
May 22 15:28:34 bettyhost kernel: [   45.421948] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
May 22 15:28:34 bettyhost kernel: [   45.422004] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
May 22 15:28:34 bettyhost kernel: [   45.453704] input: Power Button (FF) as /devices/virtual/input/input3
May 22 15:28:34 bettyhost kernel: [   45.464582] ACPI: Power Button (FF) [PWRF]
May 22 15:28:34 bettyhost kernel: [   45.464830] input: Power Button (CM) as /devices/virtual/input/input4
May 22 15:28:34 bettyhost kernel: [   45.480568] ACPI: Power Button (CM) [PWRB]
May 22 15:28:34 bettyhost kernel: [   47.319116] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2F11
May 22 15:28:34 bettyhost kernel: [   47.319155] usbcore: registered new interface driver usblp
May 22 15:28:34 bettyhost kernel: [   47.599501] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 16
May 22 15:28:34 bettyhost kernel: [   47.599541] PCI: Setting latency timer of device 0000:00:1f.5 to 64
May 22 15:28:34 bettyhost kernel: [   47.874788] input: PC Speaker as /devices/platform/pcspkr/input/input5
May 22 15:28:34 bettyhost kernel: [   48.017314] intel8x0_measure_ac97_clock: measured 54769 usecs
May 22 15:28:34 bettyhost kernel: [   48.017320] intel8x0: clocking to 48000
May 22 15:28:34 bettyhost kernel: [   48.903340] parport_pc 00:0a: reported by Plug and Play ACPI
May 22 15:28:34 bettyhost kernel: [   48.903374] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
May 22 15:28:34 bettyhost kernel: [   48.908623] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
May 22 15:28:34 bettyhost kernel: [   51.454116] loop: module loaded
May 22 15:28:34 bettyhost kernel: [   51.488020] lp0: using parport0 (interrupt-driven).
May 22 15:28:34 bettyhost kernel: [   51.643367] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
May 22 15:28:34 bettyhost kernel: [   52.258496] EXT3 FS on sda1, internal journal
May 22 15:28:34 bettyhost kernel: [   53.863142] ip_tables: (C) 2000-2006 Netfilter Core Team
May 22 15:28:34 bettyhost kernel: [   54.697748] No dock devices found.
May 22 15:28:35 bettyhost kernel: [   56.927437] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May 22 15:28:35 bettyhost kernel: [   56.927447] apm: overridden by ACPI.
May 22 15:28:35 bettyhost kernel: [   57.121936] ppdev: user-space parallel port driver
May 22 15:28:36 bettyhost kernel: [   57.518701] audit(1243031316.200:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5187 profile="/usr/sbin/cupsd" namespace="default"
May 22 15:28:38 bettyhost kernel: [   60.174743] eth0:  setting full-duplex.
May 22 15:28:39 bettyhost kernel: [   60.412864] Bluetooth: Core ver 2.11
May 22 15:28:39 bettyhost kernel: [   60.414045] NET: Registered protocol family 31
May 22 15:28:39 bettyhost kernel: [   60.414054] Bluetooth: HCI device and connection manager initialized
May 22 15:28:39 bettyhost kernel: [   60.414061] Bluetooth: HCI socket layer initialized
May 22 15:28:39 bettyhost kernel: [   60.552210] Bluetooth: L2CAP ver 2.9
May 22 15:28:39 bettyhost kernel: [   60.552219] Bluetooth: L2CAP socket layer initialized
May 22 15:28:39 bettyhost kernel: [   60.565283] Bluetooth: RFCOMM socket layer initialized
May 22 15:28:39 bettyhost kernel: [   60.565339] Bluetooth: RFCOMM TTY layer initialized
May 22 15:28:39 bettyhost kernel: [   60.565345] Bluetooth: RFCOMM ver 1.8
May 22 15:28:42 bettyhost kernel: [   63.595665] NET: Registered protocol family 17
May 22 15:28:44 bettyhost kernel: [   66.198309] [drm] Initialized drm 1.1.0 20060810
May 22 15:28:44 bettyhost kernel: [   66.210272] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
May 22 15:28:44 bettyhost kernel: [   66.210289] PCI: Setting latency timer of device 0000:00:02.0 to 64
May 22 15:28:44 bettyhost kernel: [   66.211246] [drm] Initialized i915 1.6.0 20060119 on minor 0
May 22 15:28:59 bettyhost kernel: [   80.329591] NET: Registered protocol family 10
May 22 15:28:59 bettyhost kernel: [   80.330602] lo: Disabled Privacy Extensions
May 22 15:28:59 bettyhost kernel: [   80.333317] ADDRCONF(NETDEV_UP): eth1: link is not ready
May 22 15:50:36 bettyhost kernel: Inspecting /boot/System.map-2.6.24-24-generic
May 22 15:50:36 bettyhost kernel: Loaded 27917 symbols from /boot/System.map-2.6.24-24-generic.
May 22 15:50:36 bettyhost kernel: Symbols match kernel version 2.6.24.
May 22 15:50:36 bettyhost kernel: Loaded 15166 symbols from 84 modules.
May 22 15:50:36 bettyhost kernel: [    0.000000] Initializing cgroup subsys cpuset
May 22 15:50:36 bettyhost kernel: [    0.000000] Initializing cgroup subsys cpu
May 22 15:50:36 bettyhost kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Wed Apr 15 15:54:25 UTC 2009 (Ubuntu 2.6.24-24.53-generic)
May 22 15:50:36 bettyhost kernel: [    0.000000] BIOS-provided physical RAM map:
May 22 15:50:36 bettyhost kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 22 15:50:36 bettyhost kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 22 15:50:36 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 22 15:50:36 bettyhost kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fef0000 (usable)
May 22 15:50:36 bettyhost kernel: [    0.000000]  BIOS-e820: 000000002fef0000 - 000000002fef3000 (ACPI NVS)
May 22 15:50:36 bettyhost kernel: [    0.000000]  BIOS-e820: 000000002fef3000 - 000000002ff00000 (ACPI data)
May 22 15:50:36 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May 22 15:50:36 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May 22 15:50:36 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
May 22 15:50:36 bettyhost kernel: [    0.000000] 0MB HIGHMEM available.
May 22 15:50:36 bettyhost kernel: [    0.000000] 766MB LOWMEM available.
May 22 15:50:36 bettyhost kernel: [    0.000000] found SMP MP-table at 000f4ba0
May 22 15:50:36 bettyhost kernel: [    0.000000] Entering add_active_range(0, 0, 196336) 0 entries of 256 used
May 22 15:50:36 bettyhost kernel: [    0.000000] Zone PFN ranges:
May 22 15:50:36 bettyhost kernel: [    0.000000]   DMA             0 ->     4096
May 22 15:50:36 bettyhost kernel: [    0.000000]   Normal       4096 ->   196336
May 22 15:50:36 bettyhost kernel: [    0.000000]   HighMem    196336 ->   196336
May 22 15:50:36 bettyhost kernel: [    0.000000] Movable zone start PFN for each node
May 22 15:50:36 bettyhost kernel: [    0.000000] early_node_map[1] active PFN ranges
May 22 15:50:36 bettyhost kernel: [    0.000000]     0:        0 ->   196336
May 22 15:50:36 bettyhost kernel: [    0.000000] On node 0 totalpages: 196336
May 22 15:50:36 bettyhost kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 22 15:50:36 bettyhost kernel: [    0.000000]   DMA zone: 0 pages reserved
May 22 15:50:36 bettyhost kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May 22 15:50:36 bettyhost kernel: [    0.000000]   Normal zone: 1501 pages used for memmap
May 22 15:50:36 bettyhost kernel: [    0.000000]   Normal zone: 190739 pages, LIFO batch:31
May 22 15:50:36 bettyhost kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
May 22 15:50:36 bettyhost kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 22 15:50:36 bettyhost kernel: [    0.000000] DMI 2.3 present.
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6D40 checksum 0
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: RSDP 000F6D40, 0014 (r0 IntelR)
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: RSDT 2FEF3000, 0030 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: FACP 2FEF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: DSDT 2FEF30C0, 3543 (r1 INTELR AWRDACPI     1000 MSFT  100000C)
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: FACS 2FEF0000, 0040
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: BOOT 2FEF6640, 0028 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: APIC 2FEF6680, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May 22 15:50:36 bettyhost kernel: [    0.000000] Processor #0 15:1 APIC version 20
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May 22 15:50:36 bettyhost kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: IRQ0 used by override.
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: IRQ2 used by override.
May 22 15:50:36 bettyhost kernel: [    0.000000] ACPI: IRQ9 used by override.
May 22 15:50:36 bettyhost kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May 22 15:50:36 bettyhost kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 22 15:50:36 bettyhost kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2ff00000:ced00000)
May 22 15:50:36 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May 22 15:50:36 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
May 22 15:50:36 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
May 22 15:50:36 bettyhost kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194803
May 22 15:50:36 bettyhost kernel: [    0.000000] Kernel command line: root=UUID=3bd8db4a-33f3-4f2f-b16e-13aadf7a2cf1 ro quiet splash
May 22 15:50:36 bettyhost kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May 22 15:50:36 bettyhost kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May 22 15:50:36 bettyhost kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 22 15:50:36 bettyhost kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May 22 15:50:36 bettyhost kernel: [    0.000000] Initializing CPU#0
May 22 15:50:36 bettyhost kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May 22 15:50:36 bettyhost kernel: [    0.000000] Detected 1794.294 MHz processor.
May 22 15:50:36 bettyhost kernel: [    9.368468] Console: colour VGA+ 80x25
May 22 15:50:36 bettyhost kernel: [    9.368474] console [tty0] enabled
May 22 15:50:36 bettyhost kernel: [    9.369445] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May 22 15:50:36 bettyhost kernel: [    9.370916] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May 22 15:50:36 bettyhost kernel: [    9.398293] Memory: 766332k/785344k available (2179k kernel code, 18404k reserved, 1008k data, 368k init, 0k highmem)
May 22 15:50:36 bettyhost kernel: [    9.398306] virtual kernel memory layout:
May 22 15:50:36 bettyhost kernel: [    9.398308]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May 22 15:50:36 bettyhost kernel: [    9.398309]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May 22 15:50:36 bettyhost kernel: [    9.398311]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May 22 15:50:36 bettyhost kernel: [    9.398313]     lowmem  : 0xc0000000 - 0xefef0000   ( 766 MB)
May 22 15:50:36 bettyhost kernel: [    9.398314]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
May 22 15:50:36 bettyhost kernel: [    9.398316]       .data : 0xc0320d78 - 0xc041cdc4   (1008 kB)
May 22 15:50:36 bettyhost kernel: [    9.398318]       .text : 0xc0100000 - 0xc0320d78   (2179 kB)
May 22 15:50:36 bettyhost kernel: [    9.398322] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May 22 15:50:36 bettyhost kernel: [    9.398378] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
May 22 15:50:36 bettyhost kernel: [    9.478309] Calibrating delay using timer specific routine.. 3592.39 BogoMIPS (lpj=7184780)
May 22 15:50:36 bettyhost kernel: [    9.478351] Security Framework initialized
May 22 15:50:36 bettyhost kernel: [    9.478362] SELinux:  Disabled at boot.
May 22 15:50:36 bettyhost kernel: [    9.478383] AppArmor: AppArmor initialized
May 22 15:50:36 bettyhost kernel: [    9.478391] Failure registering capabilities with primary security module.
May 22 15:50:36 bettyhost kernel: [    9.478406] Mount-cache hash table entries: 512
May 22 15:50:36 bettyhost kernel: [    9.478639] Initializing cgroup subsys ns
May 22 15:50:36 bettyhost kernel: [    9.478649] Initializing cgroup subsys cpuacct
May 22 15:50:36 bettyhost kernel: [    9.478671] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
May 22 15:50:36 bettyhost kernel: [    9.478690] CPU: Trace cache: 12K uops, L1 D cache: 8K
May 22 15:50:36 bettyhost kernel: [    9.478694] CPU: L2 cache: 128K
May 22 15:50:36 bettyhost kernel: [    9.478698] CPU: Hyper-Threading is disabled
May 22 15:50:36 bettyhost kernel: [    9.478703] CPU: After all inits, caps: 3febfbff 00000000 00000000 00043080 00000000 00000000 00000000 00000000
May 22 15:50:36 bettyhost kernel: [    9.478722] Compat vDSO mapped to ffffe000.
May 22 15:50:36 bettyhost kernel: [    9.478744] Checking 'hlt' instruction... OK.
May 22 15:50:36 bettyhost kernel: [    9.494900] SMP alternatives: switching to UP code
May 22 15:50:36 bettyhost kernel: [    9.497441] Freeing SMP alternatives: 11k freed
May 22 15:50:36 bettyhost kernel: [    9.497671] Early unpacking initramfs... done
May 22 15:50:36 bettyhost kernel: [   10.025161] ACPI: Core revision 20070126
May 22 15:50:36 bettyhost kernel: [   10.025244] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 22 15:50:36 bettyhost kernel: [   10.030864] CPU0: Intel(R) Celeron(R) CPU 1.80GHz stepping 03
May 22 15:50:36 bettyhost kernel: [   10.030923] Total of 1 processors activated (3592.39 BogoMIPS).
May 22 15:50:36 bettyhost kernel: [   10.031071] ENABLING IO-APIC IRQs
May 22 15:50:36 bettyhost kernel: [   10.031270] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May 22 15:50:36 bettyhost kernel: [   10.177576] Brought up 1 CPUs
May 22 15:50:36 bettyhost kernel: [   10.177613] CPU0 attaching sched-domain:
May 22 15:50:36 bettyhost kernel: [   10.177618]  domain 0: span 01
May 22 15:50:36 bettyhost kernel: [   10.177621]   groups: 01
May 22 15:50:36 bettyhost kernel: [   10.178045] net_namespace: 64 bytes
May 22 15:50:36 bettyhost kernel: [   10.178064] Booting paravirtualized kernel on bare hardware
May 22 15:50:36 bettyhost kernel: [   10.179050] Time: 22:49:49  Date: 05/22/09
May 22 15:50:36 bettyhost kernel: [   10.179108] NET: Registered protocol family 16
May 22 15:50:36 bettyhost kernel: [   10.179836] EISA bus registered
May 22 15:50:36 bettyhost kernel: [   10.179882] ACPI: bus type pci registered
May 22 15:50:36 bettyhost kernel: [   10.206583] PCI: PCI BIOS revision 2.10 entry at 0xfaea0, last bus=1
May 22 15:50:36 bettyhost kernel: [   10.206588] PCI: Using configuration type 1
May 22 15:50:36 bettyhost kernel: [   10.206614] Setting up standard PCI resources
May 22 15:50:36 bettyhost kernel: [   10.221453] ACPI: EC: Look up EC in DSDT
May 22 15:50:36 bettyhost kernel: [   10.226099] ACPI: Interpreter enabled
May 22 15:50:36 bettyhost kernel: [   10.226110] ACPI: (supports S0 S1 S3 S4 S5)
May 22 15:50:36 bettyhost kernel: [   10.226140] ACPI: Using IOAPIC for interrupt routing
May 22 15:50:36 bettyhost kernel: [   10.236079] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 22 15:50:36 bettyhost kernel: [   10.236748] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
May 22 15:50:36 bettyhost kernel: [   10.236751] * this clock source is slow. If you are sure your timer does not have
May 22 15:50:36 bettyhost kernel: [   10.236753] * this bug, please use "acpi_pm_good" to disable the workaround
May 22 15:50:36 bettyhost kernel: [   10.236811] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
May 22 15:50:36 bettyhost kernel: [   10.236816] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
May 22 15:50:36 bettyhost kernel: [   10.237489] PCI: Transparent bridge - 0000:00:1e.0
May 22 15:50:36 bettyhost kernel: [   10.237538] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 22 15:50:36 bettyhost kernel: [   10.237801] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May 22 15:50:36 bettyhost kernel: [   10.261001] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May 22 15:50:36 bettyhost kernel: [   10.261191] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May 22 15:50:36 bettyhost kernel: [   10.261414] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May 22 15:50:36 bettyhost kernel: [   10.261609] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May 22 15:50:36 bettyhost kernel: [   10.261788] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 22 15:50:36 bettyhost kernel: [   10.261968] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 22 15:50:36 bettyhost kernel: [   10.262149] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 22 15:50:36 bettyhost kernel: [   10.262329] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May 22 15:50:36 bettyhost kernel: [   10.262719] Linux Plug and Play Support v0.97 (c) Adam Belay
May 22 15:50:36 bettyhost kernel: [   10.262839] pnp: PnP ACPI init
May 22 15:50:36 bettyhost kernel: [   10.262860] ACPI: bus type pnp registered
May 22 15:50:36 bettyhost kernel: [   10.268181] pnp: PnP ACPI: found 12 devices
May 22 15:50:36 bettyhost kernel: [   10.268189] ACPI: ACPI bus type pnp unregistered
May 22 15:50:36 bettyhost kernel: [   10.268196] PnPBIOS: Disabled by ACPI PNP
May 22 15:50:36 bettyhost kernel: [   10.269053] PCI: Using ACPI for IRQ routing
May 22 15:50:36 bettyhost kernel: [   10.269061] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 22 15:50:36 bettyhost kernel: [   10.289431] NET: Registered protocol family 8
May 22 15:50:36 bettyhost kernel: [   10.289437] NET: Registered protocol family 20
May 22 15:50:36 bettyhost kernel: [   10.289655] AppArmor: AppArmor Filesystem Enabled
May 22 15:50:36 bettyhost kernel: [   10.293324] Time: tsc clocksource has been installed.
May 22 15:50:36 bettyhost kernel: [   10.301472] system 00:00: iomem range 0xcc000-0xcffff has been reserved
May 22 15:50:36 bettyhost kernel: [   10.301479] system 00:00: iomem range 0xd6800-0xd7fff has been reserved
May 22 15:50:36 bettyhost kernel: [   10.301484] system 00:00: iomem range 0xf0000-0xfbfff could not be reserved
May 22 15:50:36 bettyhost kernel: [   10.301488] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
May 22 15:50:36 bettyhost kernel: [   10.301492] system 00:00: iomem range 0x2fef0000-0x2fefffff could not be reserved
May 22 15:50:36 bettyhost kernel: [   10.301496] system 00:00: iomem range 0x0-0x9ffff could not be reserved
May 22 15:50:36 bettyhost kernel: [   10.301500] system 00:00: iomem range 0x100000-0x2feeffff could not be reserved
May 22 15:50:36 bettyhost kernel: [   10.301506] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
May 22 15:50:36 bettyhost kernel: [   10.301510] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
May 22 15:50:36 bettyhost kernel: [   10.301515] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
May 22 15:50:36 bettyhost kernel: [   10.301519] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
May 22 15:50:36 bettyhost kernel: [   10.301523] system 00:00: iomem range 0xe0000-0xeffff has been reserved
May 22 15:50:36 bettyhost kernel: [   10.301535] system 00:02: ioport range 0x400-0x4bf could not be reserved
May 22 15:50:36 bettyhost kernel: [   10.301545] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May 22 15:50:36 bettyhost kernel: [   10.301550] system 00:03: ioport range 0x800-0x87f has been reserved
May 22 15:50:36 bettyhost kernel: [   10.333033] PCI: Bridge: 0000:00:1e.0
May 22 15:50:36 bettyhost kernel: [   10.333040]   IO window: c000-cfff
May 22 15:50:36 bettyhost kernel: [   10.333048]   MEM window: ec000000-edffffff
May 22 15:50:36 bettyhost kernel: [   10.333053]   PREFETCH window: disabled.
May 22 15:50:36 bettyhost kernel: [   10.333071] PCI: Setting latency timer of device 0000:00:1e.0 to 64
May 22 15:50:36 bettyhost kernel: [   10.333096] NET: Registered protocol family 2
May 22 15:50:36 bettyhost kernel: [   10.369366] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May 22 15:50:36 bettyhost kernel: [   10.369997] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May 22 15:50:36 bettyhost kernel: [   10.371769] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May 22 15:50:36 bettyhost kernel: [   10.372681] TCP: Hash tables configured (established 131072 bind 65536)
May 22 15:50:36 bettyhost kernel: [   10.372688] TCP reno registered
May 22 15:50:36 bettyhost kernel: [   10.381489] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
May 22 15:50:36 bettyhost kernel: [   10.843833]  it is
May 22 15:50:36 bettyhost kernel: [   11.378764] Freeing initrd memory: 7310k freed
May 22 15:50:36 bettyhost kernel: [   11.379109] Simple Boot Flag at 0x59 set to 0x1
May 22 15:50:36 bettyhost kernel: [   11.380433] audit: initializing netlink socket (disabled)
May 22 15:50:36 bettyhost kernel: [   11.380457] audit(1243032589.880:1): initialized
May 22 15:50:36 bettyhost kernel: [   11.386418] VFS: Disk quotas dquot_6.5.1
May 22 15:50:36 bettyhost kernel: [   11.386639] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 22 15:50:36 bettyhost kernel: [   11.387025] io scheduler noop registered
May 22 15:50:36 bettyhost kernel: [   11.387031] io scheduler anticipatory registered
May 22 15:50:36 bettyhost kernel: [   11.387034] io scheduler deadline registered
May 22 15:50:36 bettyhost kernel: [   11.387073] io scheduler cfq registered (default)
May 22 15:50:36 bettyhost kernel: [   11.387091] Boot video device is 0000:00:02.0
May 22 15:50:36 bettyhost kernel: [   11.388119] isapnp: Scanning for PnP cards...
May 22 15:50:36 bettyhost kernel: [   11.742177] isapnp: No Plug & Play device found
May 22 15:50:36 bettyhost kernel: [   11.903967] Real Time Clock Driver v1.12ac
May 22 15:50:36 bettyhost kernel: [   11.904260] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 22 15:50:36 bettyhost kernel: [   11.904506] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 22 15:50:36 bettyhost kernel: [   11.906835] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 22 15:50:36 bettyhost kernel: [   11.907511] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
May 22 15:50:36 bettyhost kernel: [   11.916368] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 22 15:50:36 bettyhost kernel: [   11.916557] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 22 15:50:36 bettyhost kernel: [   11.916863] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May 22 15:50:36 bettyhost kernel: [   11.916869] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May 22 15:50:36 bettyhost kernel: [   11.917578] serio: i8042 KBD port at 0x60,0x64 irq 1
May 22 15:50:36 bettyhost kernel: [   11.919626] mice: PS/2 mouse device common for all mice
May 22 15:50:36 bettyhost kernel: [   11.920043] EISA: Probing bus 0 at eisa.0
May 22 15:50:36 bettyhost kernel: [   11.920087] EISA: Detected 0 cards.
May 22 15:50:36 bettyhost kernel: [   11.920093] cpuidle: using governor ladder
May 22 15:50:36 bettyhost kernel: [   11.920096] cpuidle: using governor menu
May 22 15:50:36 bettyhost kernel: [   11.920274] NET: Registered protocol family 1
May 22 15:50:36 bettyhost kernel: [   11.920334] Using IPI No-Shortcut mode
May 22 15:50:36 bettyhost kernel: [   11.920402] registered taskstats version 1
May 22 15:50:36 bettyhost kernel: [   11.920555]   Magic number: 9:768:856
May 22 15:50:36 bettyhost kernel: [   11.920660]   hash matches device ptyv8
May 22 15:50:36 bettyhost kernel: [   11.920672]   hash matches device ptysb
May 22 15:50:36 bettyhost kernel: [   11.920728] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 22 15:50:36 bettyhost kernel: [   11.920731] EDD information not available.
May 22 15:50:36 bettyhost kernel: [   11.921379] Freeing unused kernel memory: 368k freed
May 22 15:50:36 bettyhost kernel: [   11.921431] Write protecting the kernel read-only data: 806k
May 22 15:50:36 bettyhost kernel: [   11.941896] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May 22 15:50:36 bettyhost kernel: [   13.344315] fuse init (API version 7.9)
May 22 15:50:36 bettyhost kernel: [   13.388702] ACPI: Processor [CPU0] (supports 2 throttling states)
May 22 15:50:36 bettyhost kernel: [   14.031839] usbcore: registered new interface driver usbfs
May 22 15:50:36 bettyhost kernel: [   14.031882] usbcore: registered new interface driver hub
May 22 15:50:36 bettyhost kernel: [   14.056599] usbcore: registered new device driver usb
May 22 15:50:36 bettyhost kernel: [   14.072295] USB Universal Host Controller Interface driver v3.0
May 22 15:50:36 bettyhost kernel: [   14.072405] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
May 22 15:50:36 bettyhost kernel: [   14.072424] PCI: Setting latency timer of device 0000:00:1d.0 to 64
May 22 15:50:36 bettyhost kernel: [   14.072429] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May 22 15:50:36 bettyhost kernel: [   14.073000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May 22 15:50:36 bettyhost kernel: [   14.073045] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000d800
May 22 15:50:36 bettyhost kernel: [   14.073315] usb usb1: configuration #1 chosen from 1 choice
May 22 15:50:36 bettyhost kernel: [   14.073366] hub 1-0:1.0: USB hub found
May 22 15:50:36 bettyhost kernel: [   14.073379] hub 1-0:1.0: 2 ports detected
May 22 15:50:36 bettyhost kernel: [   14.176562] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
May 22 15:50:36 bettyhost kernel: [   14.176581] PCI: Setting latency timer of device 0000:00:1d.1 to 64
May 22 15:50:36 bettyhost kernel: [   14.176587] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May 22 15:50:36 bettyhost kernel: [   14.176644] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May 22 15:50:36 bettyhost kernel: [   14.176682] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000d000
May 22 15:50:36 bettyhost kernel: [   14.176904] usb usb2: configuration #1 chosen from 1 choice
May 22 15:50:36 bettyhost kernel: [   14.176953] hub 2-0:1.0: USB hub found
May 22 15:50:36 bettyhost kernel: [   14.176966] hub 2-0:1.0: 2 ports detected
May 22 15:50:36 bettyhost kernel: [   14.280415] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
May 22 15:50:36 bettyhost kernel: [   14.280435] PCI: Setting latency timer of device 0000:00:1d.2 to 64
May 22 15:50:36 bettyhost kernel: [   14.280441] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May 22 15:50:36 bettyhost kernel: [   14.280506] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May 22 15:50:36 bettyhost kernel: [   14.280544] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000d400
May 22 15:50:36 bettyhost kernel: [   14.280753] usb usb3: configuration #1 chosen from 1 choice
May 22 15:50:36 bettyhost kernel: [   14.280803] hub 3-0:1.0: USB hub found
May 22 15:50:36 bettyhost kernel: [   14.280816] hub 3-0:1.0: 2 ports detected
May 22 15:50:36 bettyhost kernel: [   14.384358] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
May 22 15:50:36 bettyhost kernel: [   14.384385] PCI: Setting latency timer of device 0000:00:1d.7 to 64
May 22 15:50:36 bettyhost kernel: [   14.384391] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May 22 15:50:36 bettyhost kernel: [   14.384455] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
May 22 15:50:36 bettyhost kernel: [   14.388366] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
May 22 15:50:36 bettyhost kernel: [   14.388386] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xee080000
May 22 15:50:36 bettyhost kernel: [   14.416105] usb 1-1: new full speed USB device using uhci_hcd and address 2
May 22 15:50:36 bettyhost kernel: [   14.429757] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May 22 15:50:36 bettyhost kernel: [   14.429999] usb usb4: configuration #1 chosen from 1 choice
May 22 15:50:36 bettyhost kernel: [   14.430053] hub 4-0:1.0: USB hub found
May 22 15:50:36 bettyhost kernel: [   14.430068] hub 4-0:1.0: 6 ports detected
May 22 15:50:36 bettyhost kernel: [   14.464279] SCSI subsystem initialized
May 22 15:50:36 bettyhost kernel: [   14.532142] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 17
May 22 15:50:36 bettyhost kernel: [   14.532158] 3c59x: Donald Becker and others.
May 22 15:50:36 bettyhost kernel: [   14.532167] 0000:01:04.0: 3Com PCI 3c905C Tornado at f0840000.
May 22 15:50:36 bettyhost kernel: [   14.601013] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 17 (level, low) -> IRQ 16
May 22 15:50:36 bettyhost kernel: [   14.609931] libata version 3.00 loaded.
May 22 15:50:36 bettyhost kernel: [   14.619838] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
May 22 15:50:36 bettyhost kernel: [   14.619849] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
May 22 15:50:36 bettyhost kernel: [   14.619857] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
May 22 15:50:36 bettyhost kernel: [   14.659918] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
May 22 15:50:36 bettyhost kernel: [   14.659966] b44.c:v2.0
May 22 15:50:36 bettyhost kernel: [   14.680370] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0b:db:11:ac:ec
May 22 15:50:36 bettyhost kernel: [   14.700094] ata_piix 0000:00:1f.1: version 2.12
May 22 15:50:36 bettyhost kernel: [   14.700125] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
May 22 15:50:36 bettyhost kernel: [   14.700196] PCI: Setting latency timer of device 0000:00:1f.1 to 64
May 22 15:50:36 bettyhost kernel: [   14.715756] scsi0 : ata_piix
May 22 15:50:36 bettyhost kernel: [   14.728031] scsi1 : ata_piix
May 22 15:50:36 bettyhost kernel: [   14.728976] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May 22 15:50:36 bettyhost kernel: [   14.728983] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May 22 15:50:36 bettyhost kernel: [   14.767793] Floppy drive(s): fd0 is 1.44M
May 22 15:50:36 bettyhost kernel: [   14.787444] FDC 0 is a post-1991 82077
May 22 15:50:36 bettyhost kernel: [   14.899804] ata1.00: HPA unlocked: 58593750 -> 58633344, native 58633344
May 22 15:50:36 bettyhost kernel: [   14.899814] ata1.00: ATA-5: WDC WD300BB-75DEA0, 05.03E05, max UDMA/100
May 22 15:50:36 bettyhost kernel: [   14.899818] ata1.00: 58633344 sectors, multi 16: LBA 
May 22 15:50:36 bettyhost kernel: [   14.916698] ata1.00: configured for UDMA/100
May 22 15:50:36 bettyhost kernel: [   15.071467] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 22 15:50:36 bettyhost kernel: [   15.071474] ata2: failed to recover some devices, retrying in 5 secs
May 22 15:50:36 bettyhost kernel: [   15.278981] usb 1-1: new full speed USB device using uhci_hcd and address 3
May 22 15:50:36 bettyhost kernel: [   15.481246] usb 1-1: configuration #1 chosen from 1 choice
May 22 15:50:36 bettyhost kernel: [   15.722444] usb 1-2: new low speed USB device using uhci_hcd and address 4
May 22 15:50:36 bettyhost kernel: [   15.898644] usb 1-2: configuration #1 chosen from 1 choice
May 22 15:50:36 bettyhost kernel: [   16.193088] usbcore: registered new interface driver hiddev
May 22 15:50:36 bettyhost kernel: [   16.206445] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
May 22 15:50:36 bettyhost kernel: [   16.221835] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
May 22 15:50:36 bettyhost kernel: [   16.221867] usbcore: registered new interface driver usbhid
May 22 15:50:36 bettyhost kernel: [   16.221873] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
May 22 15:50:36 bettyhost kernel: [   20.224820] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 22 15:50:36 bettyhost kernel: [   20.224828] ata2: failed to recover some devices, retrying in 5 secs
May 22 15:50:36 bettyhost kernel: [   25.378212] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 22 15:50:36 bettyhost kernel: [   25.378219] ata2: failed to recover some devices, retrying in 5 secs
May 22 15:50:36 bettyhost kernel: [   30.695571] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-248F, R602, max UDMA/33
May 22 15:50:36 bettyhost kernel: [   30.867317] ata2.00: configured for UDMA/33
May 22 15:50:36 bettyhost kernel: [   30.867541] scsi 0:0:0:0: Direct-Access     ATA      WDC WD300BB-75DE 05.0 PQ: 0 ANSI: 5
May 22 15:50:36 bettyhost kernel: [   30.870113] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-248F  R602 PQ: 0 ANSI: 5
May 22 15:50:36 bettyhost kernel: [   30.900241] Driver 'sd' needs updating - please use bus_type methods
May 22 15:50:36 bettyhost kernel: [   30.900403] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
May 22 15:50:36 bettyhost kernel: [   30.900433] sd 0:0:0:0: [sda] Write Protect is off
May 22 15:50:36 bettyhost kernel: [   30.900438] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 22 15:50:36 bettyhost kernel: [   30.900480] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 22 15:50:36 bettyhost kernel: [   30.900600] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
May 22 15:50:36 bettyhost kernel: [   30.900625] sd 0:0:0:0: [sda] Write Protect is off
May 22 15:50:36 bettyhost kernel: [   30.900629] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 22 15:50:36 bettyhost kernel: [   30.900668] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 22 15:50:36 bettyhost kernel: [   30.900677]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May 22 15:50:36 bettyhost kernel: [   30.929266]  sda1 sda2 < sda5 >
May 22 15:50:36 bettyhost kernel: [   30.961301] sd 0:0:0:0: [sda] Attached SCSI disk
May 22 15:50:36 bettyhost kernel: [   30.976151] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 22 15:50:36 bettyhost kernel: [   30.976194] sr 1:0:0:0: Attached scsi generic sg1 type 5
May 22 15:50:36 bettyhost kernel: [   30.977723] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May 22 15:50:36 bettyhost kernel: [   30.977732] Uniform CD-ROM driver Revision: 3.20
May 22 15:50:36 bettyhost kernel: [   30.977824] sr 1:0:0:0: Attached scsi CD-ROM sr0
May 22 15:50:36 bettyhost kernel: [   31.422214] Attempting manual resume
May 22 15:50:36 bettyhost kernel: [   31.422223] swsusp: Resume From Partition 8:5
May 22 15:50:36 bettyhost kernel: [   31.422287] PM: Checking swsusp image.
May 22 15:50:36 bettyhost kernel: [   31.422528] PM: Resume from disk failed.
May 22 15:50:36 bettyhost kernel: [   31.453656] EXT3-fs: INFO: recovery required on readonly filesystem.
May 22 15:50:36 bettyhost kernel: [   31.453665] EXT3-fs: write access will be enabled during recovery.
May 22 15:50:36 bettyhost kernel: [   31.675856] kjournald starting.  Commit interval 5 seconds
May 22 15:50:36 bettyhost kernel: [   31.675889] EXT3-fs: sda1: orphan cleanup on readonly fs
May 22 15:50:36 bettyhost kernel: [   31.675900] ext3_orphan_cleanup: deleting unreferenced inode 522425
May 22 15:50:36 bettyhost kernel: [   31.675974] ext3_orphan_cleanup: deleting unreferenced inode 41265
May 22 15:50:36 bettyhost kernel: [   31.675987] EXT3-fs: sda1: 2 orphan inodes deleted
May 22 15:50:36 bettyhost kernel: [   31.675990] EXT3-fs: recovery complete.
May 22 15:50:36 bettyhost kernel: [   31.678148] EXT3-fs: mounted filesystem with ordered data mode.
May 22 15:50:36 bettyhost kernel: [   45.825497] Linux agpgart interface v0.102
May 22 15:50:36 bettyhost kernel: [   45.956071] agpgart: Detected an Intel 830M Chipset.
May 22 15:50:36 bettyhost kernel: [   45.956265] agpgart: Detected 892K stolen memory.
May 22 15:50:36 bettyhost kernel: [   46.131551] agpgart: AGP aperture is 128M @ 0xe0000000
May 22 15:50:36 bettyhost kernel: [   46.131595] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
May 22 15:50:36 bettyhost kernel: [   46.424684] intel_rng: FWH not detected
May 22 15:50:36 bettyhost kernel: [   46.463078] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 22 15:50:36 bettyhost kernel: [   46.491177] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 22 15:50:36 bettyhost kernel: [   46.563259] input: Power Button (FF) as /devices/virtual/input/input3
May 22 15:50:36 bettyhost kernel: [   46.574958] ACPI: Power Button (FF) [PWRF]
May 22 15:50:36 bettyhost kernel: [   46.576051] input: Power Button (CM) as /devices/virtual/input/input4
May 22 15:50:36 bettyhost kernel: [   46.586851] ACPI: Power Button (CM) [PWRB]
May 22 15:50:36 bettyhost kernel: [   46.614846] iTCO_vendor_support: vendor-support=0
May 22 15:50:36 bettyhost kernel: [   46.650798] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
May 22 15:50:36 bettyhost kernel: [   46.651079] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
May 22 15:50:36 bettyhost kernel: [   46.651195] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
May 22 15:50:36 bettyhost kernel: [   47.434263] input: PC Speaker as /devices/platform/pcspkr/input/input5
May 22 15:50:36 bettyhost kernel: [   49.218254] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2F11
May 22 15:50:36 bettyhost kernel: [   49.218294] usbcore: registered new interface driver usblp
May 22 15:50:36 bettyhost kernel: [   49.259567] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 16
May 22 15:50:36 bettyhost kernel: [   49.259607] PCI: Setting latency timer of device 0000:00:1f.5 to 64
May 22 15:50:36 bettyhost kernel: [   49.678874] intel8x0_measure_ac97_clock: measured 54745 usecs
May 22 15:50:36 bettyhost kernel: [   49.678881] intel8x0: clocking to 48000
May 22 15:50:36 bettyhost kernel: [   50.197623] parport_pc 00:0a: reported by Plug and Play ACPI
May 22 15:50:36 bettyhost kernel: [   50.197657] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
May 22 15:50:36 bettyhost kernel: [   50.209286] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
May 22 15:50:36 bettyhost kernel: [   52.756337] loop: module loaded
May 22 15:50:36 bettyhost kernel: [   52.781795] lp0: using parport0 (interrupt-driven).
May 22 15:50:36 bettyhost kernel: [   52.937624] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
May 22 15:50:36 bettyhost kernel: [   53.552297] EXT3 FS on sda1, internal journal
May 22 15:50:36 bettyhost kernel: [   54.973846] ip_tables: (C) 2000-2006 Netfilter Core Team
May 22 15:50:36 bettyhost kernel: [   55.731572] No dock devices found.
May 22 15:50:37 bettyhost kernel: [   57.871566] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May 22 15:50:37 bettyhost kernel: [   57.871577] apm: overridden by ACPI.
May 22 15:50:37 bettyhost kernel: [   58.049414] ppdev: user-space parallel port driver
May 22 15:50:37 bettyhost kernel: [   58.399095] audit(1243032637.779:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5184 profile="/usr/sbin/cupsd" namespace="default"
May 22 15:50:40 bettyhost kernel: [   61.083398] eth0:  setting full-duplex.
May 22 15:50:40 bettyhost kernel: [   61.373793] Bluetooth: Core ver 2.11
May 22 15:50:40 bettyhost kernel: [   61.374945] NET: Registered protocol family 31
May 22 15:50:40 bettyhost kernel: [   61.374954] Bluetooth: HCI device and connection manager initialized
May 22 15:50:40 bettyhost kernel: [   61.374961] Bluetooth: HCI socket layer initialized
May 22 15:50:40 bettyhost kernel: [   61.588007] Bluetooth: L2CAP ver 2.9
May 22 15:50:40 bettyhost kernel: [   61.588015] Bluetooth: L2CAP socket layer initialized
May 22 15:50:40 bettyhost kernel: [   61.601497] Bluetooth: RFCOMM socket layer initialized
May 22 15:50:40 bettyhost kernel: [   61.601527] Bluetooth: RFCOMM TTY layer initialized
May 22 15:50:40 bettyhost kernel: [   61.601530] Bluetooth: RFCOMM ver 1.8
May 22 15:50:44 bettyhost kernel: [   64.864350] NET: Registered protocol family 17
May 22 15:50:46 bettyhost kernel: [   67.240468] [drm] Initialized drm 1.1.0 20060810
May 22 15:50:46 bettyhost kernel: [   67.261339] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
May 22 15:50:46 bettyhost kernel: [   67.261357] PCI: Setting latency timer of device 0000:00:02.0 to 64
May 22 15:50:46 bettyhost kernel: [   67.261505] [drm] Initialized i915 1.6.0 20060119 on minor 0
May 22 15:50:48 bettyhost kernel: [   68.752003] NET: Registered protocol family 10
May 22 15:50:48 bettyhost kernel: [   68.753049] lo: Disabled Privacy Extensions
May 22 15:50:48 bettyhost kernel: [   68.755847] ADDRCONF(NETDEV_UP): eth1: link is not ready
May 22 20:10:57 bettyhost kernel: Inspecting /boot/System.map-2.6.24-24-generic
May 22 20:10:57 bettyhost kernel: Loaded 27917 symbols from /boot/System.map-2.6.24-24-generic.
May 22 20:10:57 bettyhost kernel: Symbols match kernel version 2.6.24.
May 22 20:10:57 bettyhost kernel: Loaded 15166 symbols from 84 modules.
May 22 20:10:57 bettyhost kernel: [    0.000000] Initializing cgroup subsys cpuset
May 22 20:10:57 bettyhost kernel: [    0.000000] Initializing cgroup subsys cpu
May 22 20:10:57 bettyhost kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Wed Apr 15 15:54:25 UTC 2009 (Ubuntu 2.6.24-24.53-generic)
May 22 20:10:57 bettyhost kernel: [    0.000000] BIOS-provided physical RAM map:
May 22 20:10:57 bettyhost kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 22 20:10:57 bettyhost kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 22 20:10:57 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 22 20:10:57 bettyhost kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fef0000 (usable)
May 22 20:10:57 bettyhost kernel: [    0.000000]  BIOS-e820: 000000002fef0000 - 000000002fef3000 (ACPI NVS)
May 22 20:10:57 bettyhost kernel: [    0.000000]  BIOS-e820: 000000002fef3000 - 000000002ff00000 (ACPI data)
May 22 20:10:57 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May 22 20:10:57 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May 22 20:10:57 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
May 22 20:10:57 bettyhost kernel: [    0.000000] 0MB HIGHMEM available.
May 22 20:10:57 bettyhost kernel: [    0.000000] 766MB LOWMEM available.
May 22 20:10:57 bettyhost kernel: [    0.000000] found SMP MP-table at 000f4ba0
May 22 20:10:57 bettyhost kernel: [    0.000000] Entering add_active_range(0, 0, 196336) 0 entries of 256 used
May 22 20:10:57 bettyhost kernel: [    0.000000] Zone PFN ranges:
May 22 20:10:57 bettyhost kernel: [    0.000000]   DMA             0 ->     4096
May 22 20:10:57 bettyhost kernel: [    0.000000]   Normal       4096 ->   196336
May 22 20:10:57 bettyhost kernel: [    0.000000]   HighMem    196336 ->   196336
May 22 20:10:57 bettyhost kernel: [    0.000000] Movable zone start PFN for each node
May 22 20:10:57 bettyhost kernel: [    0.000000] early_node_map[1] active PFN ranges
May 22 20:10:57 bettyhost kernel: [    0.000000]     0:        0 ->   196336
May 22 20:10:57 bettyhost kernel: [    0.000000] On node 0 totalpages: 196336
May 22 20:10:57 bettyhost kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 22 20:10:57 bettyhost kernel: [    0.000000]   DMA zone: 0 pages reserved
May 22 20:10:57 bettyhost kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May 22 20:10:57 bettyhost kernel: [    0.000000]   Normal zone: 1501 pages used for memmap
May 22 20:10:57 bettyhost kernel: [    0.000000]   Normal zone: 190739 pages, LIFO batch:31
May 22 20:10:57 bettyhost kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
May 22 20:10:57 bettyhost kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 22 20:10:57 bettyhost kernel: [    0.000000] DMI 2.3 present.
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6D40 checksum 0
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: RSDP 000F6D40, 0014 (r0 IntelR)
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: RSDT 2FEF3000, 0030 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: FACP 2FEF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: DSDT 2FEF30C0, 3543 (r1 INTELR AWRDACPI     1000 MSFT  100000C)
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: FACS 2FEF0000, 0040
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: BOOT 2FEF6640, 0028 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: APIC 2FEF6680, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May 22 20:10:57 bettyhost kernel: [    0.000000] Processor #0 15:1 APIC version 20
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May 22 20:10:57 bettyhost kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: IRQ0 used by override.
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: IRQ2 used by override.
May 22 20:10:57 bettyhost kernel: [    0.000000] ACPI: IRQ9 used by override.
May 22 20:10:57 bettyhost kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May 22 20:10:57 bettyhost kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 22 20:10:57 bettyhost kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2ff00000:ced00000)
May 22 20:10:57 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May 22 20:10:57 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
May 22 20:10:57 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
May 22 20:10:57 bettyhost kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194803
May 22 20:10:57 bettyhost kernel: [    0.000000] Kernel command line: root=UUID=3bd8db4a-33f3-4f2f-b16e-13aadf7a2cf1 ro quiet splash
May 22 20:10:57 bettyhost kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May 22 20:10:57 bettyhost kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May 22 20:10:57 bettyhost kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 22 20:10:57 bettyhost kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May 22 20:10:57 bettyhost kernel: [    0.000000] Initializing CPU#0
May 22 20:10:57 bettyhost kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May 22 20:10:57 bettyhost kernel: [    0.000000] Detected 1794.284 MHz processor.
May 22 20:10:57 bettyhost kernel: [    8.966071] Console: colour VGA+ 80x25
May 22 20:10:57 bettyhost kernel: [    8.966077] console [tty0] enabled
May 22 20:10:57 bettyhost kernel: [    8.966994] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May 22 20:10:57 bettyhost kernel: [    8.968452] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May 22 20:10:57 bettyhost kernel: [    8.995846] Memory: 766332k/785344k available (2179k kernel code, 18404k reserved, 1008k data, 368k init, 0k highmem)
May 22 20:10:57 bettyhost kernel: [    8.995859] virtual kernel memory layout:
May 22 20:10:57 bettyhost kernel: [    8.995861]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May 22 20:10:57 bettyhost kernel: [    8.995863]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May 22 20:10:57 bettyhost kernel: [    8.995865]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May 22 20:10:57 bettyhost kernel: [    8.995866]     lowmem  : 0xc0000000 - 0xefef0000   ( 766 MB)
May 22 20:10:57 bettyhost kernel: [    8.995868]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
May 22 20:10:57 bettyhost kernel: [    8.995870]       .data : 0xc0320d78 - 0xc041cdc4   (1008 kB)
May 22 20:10:57 bettyhost kernel: [    8.995872]       .text : 0xc0100000 - 0xc0320d78   (2179 kB)
May 22 20:10:57 bettyhost kernel: [    8.995877] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May 22 20:10:57 bettyhost kernel: [    8.995932] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
May 22 20:10:57 bettyhost kernel: [    9.075863] Calibrating delay using timer specific routine.. 3592.44 BogoMIPS (lpj=7184880)
May 22 20:10:57 bettyhost kernel: [    9.075907] Security Framework initialized
May 22 20:10:57 bettyhost kernel: [    9.075918] SELinux:  Disabled at boot.
May 22 20:10:57 bettyhost kernel: [    9.075939] AppArmor: AppArmor initialized
May 22 20:10:57 bettyhost kernel: [    9.075947] Failure registering capabilities with primary security module.
May 22 20:10:57 bettyhost kernel: [    9.075960] Mount-cache hash table entries: 512
May 22 20:10:57 bettyhost kernel: [    9.076190] Initializing cgroup subsys ns
May 22 20:10:57 bettyhost kernel: [    9.076199] Initializing cgroup subsys cpuacct
May 22 20:10:57 bettyhost kernel: [    9.076219] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
May 22 20:10:57 bettyhost kernel: [    9.076239] CPU: Trace cache: 12K uops, L1 D cache: 8K
May 22 20:10:57 bettyhost kernel: [    9.076243] CPU: L2 cache: 128K
May 22 20:10:57 bettyhost kernel: [    9.076246] CPU: Hyper-Threading is disabled
May 22 20:10:57 bettyhost kernel: [    9.076251] CPU: After all inits, caps: 3febfbff 00000000 00000000 00043080 00000000 00000000 00000000 00000000
May 22 20:10:57 bettyhost kernel: [    9.076269] Compat vDSO mapped to ffffe000.
May 22 20:10:57 bettyhost kernel: [    9.076292] Checking 'hlt' instruction... OK.
May 22 20:10:57 bettyhost kernel: [    9.092470] SMP alternatives: switching to UP code
May 22 20:10:57 bettyhost kernel: [    9.095007] Freeing SMP alternatives: 11k freed
May 22 20:10:57 bettyhost kernel: [    9.095231] Early unpacking initramfs... done
May 22 20:10:57 bettyhost kernel: [    9.622970] ACPI: Core revision 20070126
May 22 20:10:57 bettyhost kernel: [    9.623054] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 22 20:10:57 bettyhost kernel: [    9.628686] CPU0: Intel(R) Celeron(R) CPU 1.80GHz stepping 03
May 22 20:10:57 bettyhost kernel: [    9.628745] Total of 1 processors activated (3592.44 BogoMIPS).
May 22 20:10:57 bettyhost kernel: [    9.628893] ENABLING IO-APIC IRQs
May 22 20:10:57 bettyhost kernel: [    9.629095] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May 22 20:10:57 bettyhost kernel: [    9.775128] Brought up 1 CPUs
May 22 20:10:57 bettyhost kernel: [    9.775167] CPU0 attaching sched-domain:
May 22 20:10:57 bettyhost kernel: [    9.775172]  domain 0: span 01
May 22 20:10:57 bettyhost kernel: [    9.775175]   groups: 01
May 22 20:10:57 bettyhost kernel: [    9.775614] net_namespace: 64 bytes
May 22 20:10:57 bettyhost kernel: [    9.775633] Booting paravirtualized kernel on bare hardware
May 22 20:10:57 bettyhost kernel: [    9.776632] Time:  3:10:11  Date: 05/23/09
May 22 20:10:57 bettyhost kernel: [    9.776692] NET: Registered protocol family 16
May 22 20:10:57 bettyhost kernel: [    9.777427] EISA bus registered
May 22 20:10:57 bettyhost kernel: [    9.777473] ACPI: bus type pci registered
May 22 20:10:57 bettyhost kernel: [    9.804175] PCI: PCI BIOS revision 2.10 entry at 0xfaea0, last bus=1
May 22 20:10:57 bettyhost kernel: [    9.804181] PCI: Using configuration type 1
May 22 20:10:57 bettyhost kernel: [    9.804206] Setting up standard PCI resources
May 22 20:10:57 bettyhost kernel: [    9.819055] ACPI: EC: Look up EC in DSDT
May 22 20:10:57 bettyhost kernel: [    9.823726] ACPI: Interpreter enabled
May 22 20:10:57 bettyhost kernel: [    9.823735] ACPI: (supports S0 S1 S3 S4 S5)
May 22 20:10:57 bettyhost kernel: [    9.823765] ACPI: Using IOAPIC for interrupt routing
May 22 20:10:57 bettyhost kernel: [    9.833766] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 22 20:10:57 bettyhost kernel: [    9.834433] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
May 22 20:10:57 bettyhost kernel: [    9.834436] * this clock source is slow. If you are sure your timer does not have
May 22 20:10:57 bettyhost kernel: [    9.834438] * this bug, please use "acpi_pm_good" to disable the workaround
May 22 20:10:57 bettyhost kernel: [    9.834496] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
May 22 20:10:57 bettyhost kernel: [    9.834501] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
May 22 20:10:57 bettyhost kernel: [    9.835168] PCI: Transparent bridge - 0000:00:1e.0
May 22 20:10:57 bettyhost kernel: [    9.835214] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 22 20:10:57 bettyhost kernel: [    9.835472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May 22 20:10:57 bettyhost kernel: [    9.858689] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May 22 20:10:57 bettyhost kernel: [    9.858881] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May 22 20:10:57 bettyhost kernel: [    9.859122] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May 22 20:10:57 bettyhost kernel: [    9.859302] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May 22 20:10:57 bettyhost kernel: [    9.859475] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 22 20:10:57 bettyhost kernel: [    9.859652] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 22 20:10:57 bettyhost kernel: [    9.859829] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 22 20:10:57 bettyhost kernel: [    9.860005] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May 22 20:10:57 bettyhost kernel: [    9.860398] Linux Plug and Play Support v0.97 (c) Adam Belay
May 22 20:10:57 bettyhost kernel: [    9.860518] pnp: PnP ACPI init
May 22 20:10:57 bettyhost kernel: [    9.860539] ACPI: bus type pnp registered
May 22 20:10:57 bettyhost kernel: [    9.865848] pnp: PnP ACPI: found 12 devices
May 22 20:10:57 bettyhost kernel: [    9.865855] ACPI: ACPI bus type pnp unregistered
May 22 20:10:57 bettyhost kernel: [    9.865863] PnPBIOS: Disabled by ACPI PNP
May 22 20:10:57 bettyhost kernel: [    9.866719] PCI: Using ACPI for IRQ routing
May 22 20:10:57 bettyhost kernel: [    9.866728] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 22 20:10:57 bettyhost kernel: [    9.886983] NET: Registered protocol family 8
May 22 20:10:57 bettyhost kernel: [    9.886990] NET: Registered protocol family 20
May 22 20:10:57 bettyhost kernel: [    9.887207] AppArmor: AppArmor Filesystem Enabled
May 22 20:10:57 bettyhost kernel: [    9.890878] Time: tsc clocksource has been installed.
May 22 20:10:57 bettyhost kernel: [    9.899026] system 00:00: iomem range 0xcc000-0xcffff has been reserved
May 22 20:10:57 bettyhost kernel: [    9.899034] system 00:00: iomem range 0xd6800-0xd7fff has been reserved
May 22 20:10:57 bettyhost kernel: [    9.899038] system 00:00: iomem range 0xf0000-0xfbfff could not be reserved
May 22 20:10:57 bettyhost kernel: [    9.899042] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
May 22 20:10:57 bettyhost kernel: [    9.899047] system 00:00: iomem range 0x2fef0000-0x2fefffff could not be reserved
May 22 20:10:57 bettyhost kernel: [    9.899051] system 00:00: iomem range 0x0-0x9ffff could not be reserved
May 22 20:10:57 bettyhost kernel: [    9.899055] system 00:00: iomem range 0x100000-0x2feeffff could not be reserved
May 22 20:10:57 bettyhost kernel: [    9.899061] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
May 22 20:10:57 bettyhost kernel: [    9.899065] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
May 22 20:10:57 bettyhost kernel: [    9.899070] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
May 22 20:10:57 bettyhost kernel: [    9.899074] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
May 22 20:10:57 bettyhost kernel: [    9.899078] system 00:00: iomem range 0xe0000-0xeffff has been reserved
May 22 20:10:57 bettyhost kernel: [    9.899089] system 00:02: ioport range 0x400-0x4bf could not be reserved
May 22 20:10:57 bettyhost kernel: [    9.899100] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May 22 20:10:57 bettyhost kernel: [    9.899104] system 00:03: ioport range 0x800-0x87f has been reserved
May 22 20:10:57 bettyhost kernel: [    9.930588] PCI: Bridge: 0000:00:1e.0
May 22 20:10:57 bettyhost kernel: [    9.930596]   IO window: c000-cfff
May 22 20:10:57 bettyhost kernel: [    9.930603]   MEM window: ec000000-edffffff
May 22 20:10:57 bettyhost kernel: [    9.930609]   PREFETCH window: disabled.
May 22 20:10:57 bettyhost kernel: [    9.930626] PCI: Setting latency timer of device 0000:00:1e.0 to 64
May 22 20:10:57 bettyhost kernel: [    9.930650] NET: Registered protocol family 2
May 22 20:10:57 bettyhost kernel: [    9.966920] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May 22 20:10:57 bettyhost kernel: [    9.967553] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May 22 20:10:57 bettyhost kernel: [    9.969309] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May 22 20:10:57 bettyhost kernel: [    9.970227] TCP: Hash tables configured (established 131072 bind 65536)
May 22 20:10:57 bettyhost kernel: [    9.970233] TCP reno registered
May 22 20:10:57 bettyhost kernel: [    9.979042] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
May 22 20:10:57 bettyhost kernel: [   10.441140]  it is
May 22 20:10:57 bettyhost kernel: [   10.976399] Freeing initrd memory: 7310k freed
May 22 20:10:57 bettyhost kernel: [   10.976743] Simple Boot Flag at 0x59 set to 0x1
May 22 20:10:57 bettyhost kernel: [   10.978058] audit: initializing netlink socket (disabled)
May 22 20:10:57 bettyhost kernel: [   10.978082] audit(1243048211.880:1): initialized
May 22 20:10:57 bettyhost kernel: [   10.983991] VFS: Disk quotas dquot_6.5.1
May 22 20:10:57 bettyhost kernel: [   10.984210] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 22 20:10:57 bettyhost kernel: [   10.984596] io scheduler noop registered
May 22 20:10:57 bettyhost kernel: [   10.984603] io scheduler anticipatory registered
May 22 20:10:57 bettyhost kernel: [   10.984606] io scheduler deadline registered
May 22 20:10:57 bettyhost kernel: [   10.984645] io scheduler cfq registered (default)
May 22 20:10:57 bettyhost kernel: [   10.984665] Boot video device is 0000:00:02.0
May 22 20:10:57 bettyhost kernel: [   10.985696] isapnp: Scanning for PnP cards...
May 22 20:10:57 bettyhost kernel: [   11.339746] isapnp: No Plug & Play device found
May 22 20:10:57 bettyhost kernel: [   11.501502] Real Time Clock Driver v1.12ac
May 22 20:10:57 bettyhost kernel: [   11.501779] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 22 20:10:57 bettyhost kernel: [   11.502019] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 22 20:10:57 bettyhost kernel: [   11.504276] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 22 20:10:57 bettyhost kernel: [   11.504862] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
May 22 20:10:57 bettyhost kernel: [   11.513690] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 22 20:10:57 bettyhost kernel: [   11.513888] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 22 20:10:57 bettyhost kernel: [   11.514201] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May 22 20:10:57 bettyhost kernel: [   11.514207] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May 22 20:10:57 bettyhost kernel: [   11.514928] serio: i8042 KBD port at 0x60,0x64 irq 1
May 22 20:10:57 bettyhost kernel: [   11.517186] mice: PS/2 mouse device common for all mice
May 22 20:10:57 bettyhost kernel: [   11.517593] EISA: Probing bus 0 at eisa.0
May 22 20:10:57 bettyhost kernel: [   11.517637] EISA: Detected 0 cards.
May 22 20:10:57 bettyhost kernel: [   11.517643] cpuidle: using governor ladder
May 22 20:10:57 bettyhost kernel: [   11.517646] cpuidle: using governor menu
May 22 20:10:57 bettyhost kernel: [   11.517829] NET: Registered protocol family 1
May 22 20:10:57 bettyhost kernel: [   11.517890] Using IPI No-Shortcut mode
May 22 20:10:57 bettyhost kernel: [   11.517960] registered taskstats version 1
May 22 20:10:57 bettyhost kernel: [   11.518116]   Magic number: 9:652:159
May 22 20:10:57 bettyhost kernel: [   11.518285] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 22 20:10:57 bettyhost kernel: [   11.518288] EDD information not available.
May 22 20:10:57 bettyhost kernel: [   11.518936] Freeing unused kernel memory: 368k freed
May 22 20:10:57 bettyhost kernel: [   11.518989] Write protecting the kernel read-only data: 806k
May 22 20:10:57 bettyhost kernel: [   11.539514] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May 22 20:10:57 bettyhost kernel: [   12.941579] fuse init (API version 7.9)
May 22 20:10:57 bettyhost kernel: [   12.985978] ACPI: Processor [CPU0] (supports 2 throttling states)
May 22 20:10:57 bettyhost kernel: [   13.628502] usbcore: registered new interface driver usbfs
May 22 20:10:57 bettyhost kernel: [   13.628547] usbcore: registered new interface driver hub
May 22 20:10:57 bettyhost kernel: [   13.642922] usbcore: registered new device driver usb
May 22 20:10:57 bettyhost kernel: [   13.664270] USB Universal Host Controller Interface driver v3.0
May 22 20:10:57 bettyhost kernel: [   13.664384] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
May 22 20:10:57 bettyhost kernel: [   13.664404] PCI: Setting latency timer of device 0000:00:1d.0 to 64
May 22 20:10:57 bettyhost kernel: [   13.664410] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May 22 20:10:57 bettyhost kernel: [   13.664941] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May 22 20:10:57 bettyhost kernel: [   13.664985] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000d800
May 22 20:10:57 bettyhost kernel: [   13.665255] usb usb1: configuration #1 chosen from 1 choice
May 22 20:10:57 bettyhost kernel: [   13.665311] hub 1-0:1.0: USB hub found
May 22 20:10:57 bettyhost kernel: [   13.665325] hub 1-0:1.0: 2 ports detected
May 22 20:10:57 bettyhost kernel: [   13.766136] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
May 22 20:10:57 bettyhost kernel: [   13.766157] PCI: Setting latency timer of device 0000:00:1d.1 to 64
May 22 20:10:57 bettyhost kernel: [   13.766163] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May 22 20:10:57 bettyhost kernel: [   13.766218] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May 22 20:10:57 bettyhost kernel: [   13.766256] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000d000
May 22 20:10:57 bettyhost kernel: [   13.766478] usb usb2: configuration #1 chosen from 1 choice
May 22 20:10:57 bettyhost kernel: [   13.766526] hub 2-0:1.0: USB hub found
May 22 20:10:57 bettyhost kernel: [   13.766540] hub 2-0:1.0: 2 ports detected
May 22 20:10:57 bettyhost kernel: [   13.869964] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
May 22 20:10:57 bettyhost kernel: [   13.869985] PCI: Setting latency timer of device 0000:00:1d.2 to 64
May 22 20:10:57 bettyhost kernel: [   13.869991] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May 22 20:10:57 bettyhost kernel: [   13.870054] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May 22 20:10:57 bettyhost kernel: [   13.870093] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000d400
May 22 20:10:57 bettyhost kernel: [   13.870304] usb usb3: configuration #1 chosen from 1 choice
May 22 20:10:57 bettyhost kernel: [   13.870353] hub 3-0:1.0: USB hub found
May 22 20:10:57 bettyhost kernel: [   13.870367] hub 3-0:1.0: 2 ports detected
May 22 20:10:57 bettyhost kernel: [   13.973900] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
May 22 20:10:57 bettyhost kernel: [   13.973927] PCI: Setting latency timer of device 0000:00:1d.7 to 64
May 22 20:10:57 bettyhost kernel: [   13.973933] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May 22 20:10:57 bettyhost kernel: [   13.974001] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
May 22 20:10:57 bettyhost kernel: [   13.977934] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
May 22 20:10:57 bettyhost kernel: [   13.977953] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xee080000
May 22 20:10:57 bettyhost kernel: [   14.013630] usb 1-1: new full speed USB device using uhci_hcd and address 2
May 22 20:10:57 bettyhost kernel: [   14.025580] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May 22 20:10:57 bettyhost kernel: [   14.025816] usb usb4: configuration #1 chosen from 1 choice
May 22 20:10:57 bettyhost kernel: [   14.025868] hub 4-0:1.0: USB hub found
May 22 20:10:57 bettyhost kernel: [   14.025883] hub 4-0:1.0: 6 ports detected
May 22 20:10:57 bettyhost kernel: [   14.046022] SCSI subsystem initialized
May 22 20:10:57 bettyhost kernel: [   14.132978] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 17
May 22 20:10:57 bettyhost kernel: [   14.132994] 3c59x: Donald Becker and others.
May 22 20:10:57 bettyhost kernel: [   14.133003] 0000:01:04.0: 3Com PCI 3c905C Tornado at f0842000.
May 22 20:10:57 bettyhost kernel: [   14.184068] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 17 (level, low) -> IRQ 16
May 22 20:10:57 bettyhost kernel: [   14.191028] libata version 3.00 loaded.
May 22 20:10:57 bettyhost kernel: [   14.201379] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
May 22 20:10:57 bettyhost kernel: [   14.201390] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
May 22 20:10:57 bettyhost kernel: [   14.201398] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
May 22 20:10:57 bettyhost kernel: [   14.241403] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
May 22 20:10:57 bettyhost kernel: [   14.241452] b44.c:v2.0
May 22 20:10:57 bettyhost kernel: [   14.261928] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0b:db:11:ac:ec
May 22 20:10:57 bettyhost kernel: [   14.278378] ata_piix 0000:00:1f.1: version 2.12
May 22 20:10:57 bettyhost kernel: [   14.278408] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
May 22 20:10:57 bettyhost kernel: [   14.278486] PCI: Setting latency timer of device 0000:00:1f.1 to 64
May 22 20:10:57 bettyhost kernel: [   14.293268] scsi0 : ata_piix
May 22 20:10:57 bettyhost kernel: [   14.308043] scsi1 : ata_piix
May 22 20:10:57 bettyhost kernel: [   14.308991] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May 22 20:10:57 bettyhost kernel: [   14.308999] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May 22 20:10:57 bettyhost kernel: [   14.343468] Floppy drive(s): fd0 is 1.44M
May 22 20:10:57 bettyhost kernel: [   14.364461] FDC 0 is a post-1991 82077
May 22 20:10:57 bettyhost kernel: [   14.477316] ata1.00: HPA unlocked: 58593750 -> 58633344, native 58633344
May 22 20:10:57 bettyhost kernel: [   14.477326] ata1.00: ATA-5: WDC WD300BB-75DEA0, 05.03E05, max UDMA/100
May 22 20:10:57 bettyhost kernel: [   14.477330] ata1.00: 58633344 sectors, multi 16: LBA 
May 22 20:10:57 bettyhost kernel: [   14.494220] ata1.00: configured for UDMA/100
May 22 20:10:57 bettyhost kernel: [   14.649052] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 22 20:10:57 bettyhost kernel: [   14.649058] ata2: failed to recover some devices, retrying in 5 secs
May 22 20:10:57 bettyhost kernel: [   14.880533] usb 1-1: new full speed USB device using uhci_hcd and address 3
May 22 20:10:57 bettyhost kernel: [   15.083181] usb 1-1: configuration #1 chosen from 1 choice
May 22 20:10:57 bettyhost kernel: [   15.323927] usb 1-2: new low speed USB device using uhci_hcd and address 4
May 22 20:10:57 bettyhost kernel: [   15.500572] usb 1-2: configuration #1 chosen from 1 choice
May 22 20:10:57 bettyhost kernel: [   15.771793] usbcore: registered new interface driver hiddev
May 22 20:10:57 bettyhost kernel: [   15.784432] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
May 22 20:10:57 bettyhost kernel: [   15.795394] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
May 22 20:10:57 bettyhost kernel: [   15.795426] usbcore: registered new interface driver usbhid
May 22 20:10:57 bettyhost kernel: [   15.795431] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
May 22 20:10:57 bettyhost kernel: [   19.802339] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 22 20:10:57 bettyhost kernel: [   19.802346] ata2: failed to recover some devices, retrying in 5 secs
May 22 20:10:57 bettyhost kernel: [   24.955711] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 22 20:10:57 bettyhost kernel: [   24.955718] ata2: failed to recover some devices, retrying in 5 secs
May 22 20:10:57 bettyhost kernel: [   30.273037] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-248F, R602, max UDMA/33
May 22 20:10:57 bettyhost kernel: [   30.444772] ata2.00: configured for UDMA/33
May 22 20:10:57 bettyhost kernel: [   30.445002] scsi 0:0:0:0: Direct-Access     ATA      WDC WD300BB-75DE 05.0 PQ: 0 ANSI: 5
May 22 20:10:57 bettyhost kernel: [   30.447609] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-248F  R602 PQ: 0 ANSI: 5
May 22 20:10:57 bettyhost kernel: [   30.476760] Driver 'sd' needs updating - please use bus_type methods
May 22 20:10:57 bettyhost kernel: [   30.476929] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
May 22 20:10:57 bettyhost kernel: [   30.476963] sd 0:0:0:0: [sda] Write Protect is off
May 22 20:10:57 bettyhost kernel: [   30.476968] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 22 20:10:57 bettyhost kernel: [   30.477015] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 22 20:10:57 bettyhost kernel: [   30.477136] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
May 22 20:10:57 bettyhost kernel: [   30.477165] sd 0:0:0:0: [sda] Write Protect is off
May 22 20:10:57 bettyhost kernel: [   30.477170] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 22 20:10:57 bettyhost kernel: [   30.477215] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 22 20:10:57 bettyhost kernel: [   30.477226]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May 22 20:10:57 bettyhost kernel: [   30.505046]  sda1 sda2 < sda5 >
May 22 20:10:57 bettyhost kernel: [   30.537105] sd 0:0:0:0: [sda] Attached SCSI disk
May 22 20:10:57 bettyhost kernel: [   30.550278] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 22 20:10:57 bettyhost kernel: [   30.550319] sr 1:0:0:0: Attached scsi generic sg1 type 5
May 22 20:10:57 bettyhost kernel: [   30.554641] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May 22 20:10:57 bettyhost kernel: [   30.554650] Uniform CD-ROM driver Revision: 3.20
May 22 20:10:57 bettyhost kernel: [   30.554746] sr 1:0:0:0: Attached scsi CD-ROM sr0
May 22 20:10:57 bettyhost kernel: [   31.010599] Attempting manual resume
May 22 20:10:57 bettyhost kernel: [   31.010608] swsusp: Resume From Partition 8:5
May 22 20:10:57 bettyhost kernel: [   31.010610] PM: Checking swsusp image.
May 22 20:10:58 bettyhost kernel: [   31.010852] PM: Resume from disk failed.
May 22 20:10:58 bettyhost kernel: [   31.080291] kjournald starting.  Commit interval 5 seconds
May 22 20:10:58 bettyhost kernel: [   31.080322] EXT3-fs: mounted filesystem with ordered data mode.
May 22 20:10:58 bettyhost kernel: [   44.494420] Linux agpgart interface v0.102
May 22 20:10:58 bettyhost kernel: [   44.830055] agpgart: Detected an Intel 830M Chipset.
May 22 20:10:58 bettyhost kernel: [   44.830202] agpgart: Detected 892K stolen memory.
May 22 20:10:58 bettyhost kernel: [   44.849830] agpgart: AGP aperture is 128M @ 0xe0000000
May 22 20:10:58 bettyhost kernel: [   45.019300] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 22 20:10:58 bettyhost kernel: [   45.063256] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
May 22 20:10:58 bettyhost kernel: [   45.122594] input: Power Button (FF) as /devices/virtual/input/input3
May 22 20:10:58 bettyhost kernel: [   45.133549] ACPI: Power Button (FF) [PWRF]
May 22 20:10:58 bettyhost kernel: [   45.133759] input: Power Button (CM) as /devices/virtual/input/input4
May 22 20:10:58 bettyhost kernel: [   45.148414] ACPI: Power Button (CM) [PWRB]
May 22 20:10:58 bettyhost kernel: [   45.173700] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 22 20:10:58 bettyhost kernel: [   45.489104] intel_rng: FWH not detected
May 22 20:10:58 bettyhost kernel: [   45.698620] iTCO_vendor_support: vendor-support=0
May 22 20:10:58 bettyhost kernel: [   45.748618] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
May 22 20:10:58 bettyhost kernel: [   45.748935] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
May 22 20:10:58 bettyhost kernel: [   45.749050] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
May 22 20:10:58 bettyhost kernel: [   47.011489] input: PC Speaker as /devices/platform/pcspkr/input/input5
May 22 20:10:58 bettyhost kernel: [   47.762635] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2F11
May 22 20:10:58 bettyhost kernel: [   47.762672] usbcore: registered new interface driver usblp
May 22 20:10:58 bettyhost kernel: [   47.818250] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 16
May 22 20:10:58 bettyhost kernel: [   47.818291] PCI: Setting latency timer of device 0000:00:1f.5 to 64
May 22 20:10:58 bettyhost kernel: [   48.237594] intel8x0_measure_ac97_clock: measured 54802 usecs
May 22 20:10:58 bettyhost kernel: [   48.237640] intel8x0: clocking to 48000
May 22 20:10:58 bettyhost kernel: [   48.700135] parport_pc 00:0a: reported by Plug and Play ACPI
May 22 20:10:58 bettyhost kernel: [   48.700168] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
May 22 20:10:58 bettyhost kernel: [   48.708106] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
May 22 20:10:58 bettyhost kernel: [   51.359350] loop: module loaded
May 22 20:10:58 bettyhost kernel: [   51.393911] lp0: using parport0 (interrupt-driven).
May 22 20:10:58 bettyhost kernel: [   51.548689] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
May 22 20:10:58 bettyhost kernel: [   52.164120] EXT3 FS on sda1, internal journal
May 22 20:10:58 bettyhost kernel: [   53.776788] ip_tables: (C) 2000-2006 Netfilter Core Team
May 22 20:10:58 bettyhost kernel: [   54.610766] No dock devices found.
May 22 20:10:58 bettyhost kernel: [   56.791233] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May 22 20:10:58 bettyhost kernel: [   56.791243] apm: overridden by ACPI.
May 22 20:10:58 bettyhost kernel: [   56.985671] ppdev: user-space parallel port driver
May 22 20:10:59 bettyhost kernel: [   57.382495] audit(1243048259.157:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5181 profile="/usr/sbin/cupsd" namespace="default"
May 22 20:11:01 bettyhost kernel: [   60.048902] eth0:  setting full-duplex.
May 22 20:11:02 bettyhost kernel: [   60.253197] Bluetooth: Core ver 2.11
May 22 20:11:02 bettyhost kernel: [   60.254398] NET: Registered protocol family 31
May 22 20:11:02 bettyhost kernel: [   60.254407] Bluetooth: HCI device and connection manager initialized
May 22 20:11:02 bettyhost kernel: [   60.254415] Bluetooth: HCI socket layer initialized
May 22 20:11:02 bettyhost kernel: [   60.391164] Bluetooth: L2CAP ver 2.9
May 22 20:11:02 bettyhost kernel: [   60.391172] Bluetooth: L2CAP socket layer initialized
May 22 20:11:02 bettyhost kernel: [   60.561454] Bluetooth: RFCOMM socket layer initialized
May 22 20:11:02 bettyhost kernel: [   60.561484] Bluetooth: RFCOMM TTY layer initialized
May 22 20:11:02 bettyhost kernel: [   60.561487] Bluetooth: RFCOMM ver 1.8
May 22 20:11:05 bettyhost kernel: [   63.799890] NET: Registered protocol family 17
May 22 20:11:06 bettyhost kernel: [   64.554514] [drm] Initialized drm 1.1.0 20060810
May 22 20:11:06 bettyhost kernel: [   64.664707] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
May 22 20:11:06 bettyhost kernel: [   64.664725] PCI: Setting latency timer of device 0000:00:02.0 to 64
May 22 20:11:06 bettyhost kernel: [   64.664883] [drm] Initialized i915 1.6.0 20060119 on minor 0
May 22 20:11:07 bettyhost kernel: [   65.996329] NET: Registered protocol family 10
May 22 20:11:07 bettyhost kernel: [   65.997380] lo: Disabled Privacy Extensions
May 22 20:11:07 bettyhost kernel: [   66.000190] ADDRCONF(NETDEV_UP): eth1: link is not ready
May 23 09:58:34 bettyhost kernel: Inspecting /boot/System.map-2.6.24-24-generic
May 23 09:58:34 bettyhost kernel: Loaded 27917 symbols from /boot/System.map-2.6.24-24-generic.
May 23 09:58:34 bettyhost kernel: Symbols match kernel version 2.6.24.
May 23 09:58:34 bettyhost kernel: Loaded 15064 symbols from 83 modules.
May 23 09:58:34 bettyhost kernel: [    0.000000] Initializing cgroup subsys cpuset
May 23 09:58:34 bettyhost kernel: [    0.000000] Initializing cgroup subsys cpu
May 23 09:58:34 bettyhost kernel: [    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Wed Apr 15 15:54:25 UTC 2009 (Ubuntu 2.6.24-24.53-generic)
May 23 09:58:34 bettyhost kernel: [    0.000000] BIOS-provided physical RAM map:
May 23 09:58:34 bettyhost kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 23 09:58:34 bettyhost kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 23 09:58:34 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 23 09:58:34 bettyhost kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fef0000 (usable)
May 23 09:58:34 bettyhost kernel: [    0.000000]  BIOS-e820: 000000002fef0000 - 000000002fef3000 (ACPI NVS)
May 23 09:58:34 bettyhost kernel: [    0.000000]  BIOS-e820: 000000002fef3000 - 000000002ff00000 (ACPI data)
May 23 09:58:34 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May 23 09:58:34 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May 23 09:58:34 bettyhost kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
May 23 09:58:34 bettyhost kernel: [    0.000000] 0MB HIGHMEM available.
May 23 09:58:34 bettyhost kernel: [    0.000000] 766MB LOWMEM available.
May 23 09:58:34 bettyhost kernel: [    0.000000] found SMP MP-table at 000f4ba0
May 23 09:58:34 bettyhost kernel: [    0.000000] Entering add_active_range(0, 0, 196336) 0 entries of 256 used
May 23 09:58:34 bettyhost kernel: [    0.000000] Zone PFN ranges:
May 23 09:58:34 bettyhost kernel: [    0.000000]   DMA             0 ->     4096
May 23 09:58:34 bettyhost kernel: [    0.000000]   Normal       4096 ->   196336
May 23 09:58:34 bettyhost kernel: [    0.000000]   HighMem    196336 ->   196336
May 23 09:58:34 bettyhost kernel: [    0.000000] Movable zone start PFN for each node
May 23 09:58:34 bettyhost kernel: [    0.000000] early_node_map[1] active PFN ranges
May 23 09:58:34 bettyhost kernel: [    0.000000]     0:        0 ->   196336
May 23 09:58:34 bettyhost kernel: [    0.000000] On node 0 totalpages: 196336
May 23 09:58:34 bettyhost kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 23 09:58:34 bettyhost kernel: [    0.000000]   DMA zone: 0 pages reserved
May 23 09:58:34 bettyhost kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May 23 09:58:34 bettyhost kernel: [    0.000000]   Normal zone: 1501 pages used for memmap
May 23 09:58:34 bettyhost kernel: [    0.000000]   Normal zone: 190739 pages, LIFO batch:31
May 23 09:58:34 bettyhost kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
May 23 09:58:34 bettyhost kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 23 09:58:34 bettyhost kernel: [    0.000000] DMI 2.3 present.
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6D40 checksum 0
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: RSDP 000F6D40, 0014 (r0 IntelR)
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: RSDT 2FEF3000, 0030 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: FACP 2FEF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: DSDT 2FEF30C0, 3543 (r1 INTELR AWRDACPI     1000 MSFT  100000C)
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: FACS 2FEF0000, 0040
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: BOOT 2FEF6640, 0028 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: APIC 2FEF6680, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May 23 09:58:34 bettyhost kernel: [    0.000000] Processor #0 15:1 APIC version 20
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May 23 09:58:34 bettyhost kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: IRQ0 used by override.
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: IRQ2 used by override.
May 23 09:58:34 bettyhost kernel: [    0.000000] ACPI: IRQ9 used by override.
May 23 09:58:34 bettyhost kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May 23 09:58:34 bettyhost kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 23 09:58:34 bettyhost kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2ff00000:ced00000)
May 23 09:58:34 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May 23 09:58:34 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
May 23 09:58:34 bettyhost kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
May 23 09:58:34 bettyhost kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194803
May 23 09:58:34 bettyhost kernel: [    0.000000] Kernel command line: root=UUID=3bd8db4a-33f3-4f2f-b16e-13aadf7a2cf1 ro quiet splash
May 23 09:58:34 bettyhost kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
May 23 09:58:34 bettyhost kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
May 23 09:58:34 bettyhost kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 23 09:58:34 bettyhost kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May 23 09:58:34 bettyhost kernel: [    0.000000] Initializing CPU#0
May 23 09:58:34 bettyhost kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May 23 09:58:34 bettyhost kernel: [    0.000000] Detected 1794.311 MHz processor.
May 23 09:58:34 bettyhost kernel: [    9.053940] Console: colour VGA+ 80x25
May 23 09:58:34 bettyhost kernel: [    9.053945] console [tty0] enabled
May 23 09:58:34 bettyhost kernel: [    9.054921] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May 23 09:58:34 bettyhost kernel: [    9.056384] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May 23 09:58:34 bettyhost kernel: [    9.083755] Memory: 766332k/785344k available (2179k kernel code, 18404k reserved, 1008k data, 368k init, 0k highmem)
May 23 09:58:34 bettyhost kernel: [    9.083769] virtual kernel memory layout:
May 23 09:58:34 bettyhost kernel: [    9.083770]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
May 23 09:58:34 bettyhost kernel: [    9.083772]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May 23 09:58:34 bettyhost kernel: [    9.083773]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
May 23 09:58:34 bettyhost kernel: [    9.083775]     lowmem  : 0xc0000000 - 0xefef0000   ( 766 MB)
May 23 09:58:34 bettyhost kernel: [    9.083777]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
May 23 09:58:34 bettyhost kernel: [    9.083778]       .data : 0xc0320d78 - 0xc041cdc4   (1008 kB)
May 23 09:58:34 bettyhost kernel: [    9.083780]       .text : 0xc0100000 - 0xc0320d78   (2179 kB)
May 23 09:58:34 bettyhost kernel: [    9.083785] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May 23 09:58:34 bettyhost kernel: [    9.083839] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
May 23 09:58:34 bettyhost kernel: [    9.163770] Calibrating delay using timer specific routine.. 3592.43 BogoMIPS (lpj=7184862)
May 23 09:58:34 bettyhost kernel: [    9.163811] Security Framework initialized
May 23 09:58:34 bettyhost kernel: [    9.163822] SELinux:  Disabled at boot.
May 23 09:58:34 bettyhost kernel: [    9.163843] AppArmor: AppArmor initialized
May 23 09:58:34 bettyhost kernel: [    9.163851] Failure registering capabilities with primary security module.
May 23 09:58:34 bettyhost kernel: [    9.163865] Mount-cache hash table entries: 512
May 23 09:58:34 bettyhost kernel: [    9.164085] Initializing cgroup subsys ns
May 23 09:58:34 bettyhost kernel: [    9.164095] Initializing cgroup subsys cpuacct
May 23 09:58:34 bettyhost kernel: [    9.164115] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
May 23 09:58:34 bettyhost kernel: [    9.164135] CPU: Trace cache: 12K uops, L1 D cache: 8K
May 23 09:58:34 bettyhost kernel: [    9.164139] CPU: L2 cache: 128K
May 23 09:58:34 bettyhost kernel: [    9.164142] CPU: Hyper-Threading is disabled
May 23 09:58:34 bettyhost kernel: [    9.164147] CPU: After all inits, caps: 3febfbff 00000000 00000000 00043080 00000000 00000000 00000000 00000000
May 23 09:58:34 bettyhost kernel: [    9.164165] Compat vDSO mapped to ffffe000.
May 23 09:58:34 bettyhost kernel: [    9.164187] Checking 'hlt' instruction... OK.
May 23 09:58:34 bettyhost kernel: [    9.180375] SMP alternatives: switching to UP code
May 23 09:58:34 bettyhost kernel: [    9.182922] Freeing SMP alternatives: 11k freed
May 23 09:58:34 bettyhost kernel: [    9.183154] Early unpacking initramfs... done
May 23 09:58:34 bettyhost kernel: [    9.710739] ACPI: Core revision 20070126
May 23 09:58:34 bettyhost kernel: [    9.710823] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 23 09:58:34 bettyhost kernel: [    9.716526] CPU0: Intel(R) Celeron(R) CPU 1.80GHz stepping 03
May 23 09:58:34 bettyhost kernel: [    9.716585] Total of 1 processors activated (3592.43 BogoMIPS).
May 23 09:58:34 bettyhost kernel: [    9.716733] ENABLING IO-APIC IRQs
May 23 09:58:34 bettyhost kernel: [    9.716934] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May 23 09:58:34 bettyhost kernel: [    9.863035] Brought up 1 CPUs
May 23 09:58:34 bettyhost kernel: [    9.863072] CPU0 attaching sched-domain:
May 23 09:58:34 bettyhost kernel: [    9.863078]  domain 0: span 01
May 23 09:58:34 bettyhost kernel: [    9.863081]   groups: 01
May 23 09:58:34 bettyhost kernel: [    9.863520] net_namespace: 64 bytes
May 23 09:58:34 bettyhost kernel: [    9.863539] Booting paravirtualized kernel on bare hardware
May 23 09:58:34 bettyhost kernel: [    9.864543] Time: 16:57:48  Date: 05/23/09
May 23 09:58:34 bettyhost kernel: [    9.864604] NET: Registered protocol family 16
May 23 09:58:34 bettyhost kernel: [    9.865326] EISA bus registered
May 23 09:58:34 bettyhost kernel: [    9.865371] ACPI: bus type pci registered
May 23 09:58:34 bettyhost kernel: [    9.892081] PCI: PCI BIOS revision 2.10 entry at 0xfaea0, last bus=1
May 23 09:58:34 bettyhost kernel: [    9.892086] PCI: Using configuration type 1
May 23 09:58:34 bettyhost kernel: [    9.892112] Setting up standard PCI resources
May 23 09:58:34 bettyhost kernel: [    9.906903] ACPI: EC: Look up EC in DSDT
May 23 09:58:34 bettyhost kernel: [    9.911597] ACPI: Interpreter enabled
May 23 09:58:34 bettyhost kernel: [    9.911607] ACPI: (supports S0 S1 S3 S4 S5)
May 23 09:58:34 bettyhost kernel: [    9.911636] ACPI: Using IOAPIC for interrupt routing
May 23 09:58:34 bettyhost kernel: [    9.921546] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 23 09:58:34 bettyhost kernel: [    9.922213] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
May 23 09:58:34 bettyhost kernel: [    9.922216] * this clock source is slow. If you are sure your timer does not have
May 23 09:58:34 bettyhost kernel: [    9.922218] * this bug, please use "acpi_pm_good" to disable the workaround
May 23 09:58:34 bettyhost kernel: [    9.922276] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
May 23 09:58:34 bettyhost kernel: [    9.922281] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
May 23 09:58:34 bettyhost kernel: [    9.922955] PCI: Transparent bridge - 0000:00:1e.0
May 23 09:58:34 bettyhost kernel: [    9.923004] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 23 09:58:34 bettyhost kernel: [    9.923269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
May 23 09:58:34 bettyhost kernel: [    9.946427] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May 23 09:58:34 bettyhost kernel: [    9.946616] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May 23 09:58:34 bettyhost kernel: [    9.946792] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May 23 09:58:34 bettyhost kernel: [    9.947027] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May 23 09:58:34 bettyhost kernel: [    9.947203] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 23 09:58:34 bettyhost kernel: [    9.947377] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 23 09:58:34 bettyhost kernel: [    9.947554] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 23 09:58:34 bettyhost kernel: [    9.947731] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May 23 09:58:34 bettyhost kernel: [    9.948118] Linux Plug and Play Support v0.97 (c) Adam Belay
May 23 09:58:34 bettyhost kernel: [    9.948235] pnp: PnP ACPI init
May 23 09:58:34 bettyhost kernel: [    9.948257] ACPI: bus type pnp registered
May 23 09:58:34 bettyhost kernel: [    9.953623] pnp: PnP ACPI: found 12 devices
May 23 09:58:34 bettyhost kernel: [    9.953630] ACPI: ACPI bus type pnp unregistered
May 23 09:58:34 bettyhost kernel: [    9.953639] PnPBIOS: Disabled by ACPI PNP
May 23 09:58:34 bettyhost kernel: [    9.954499] PCI: Using ACPI for IRQ routing
May 23 09:58:34 bettyhost kernel: [    9.954507] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 23 09:58:34 bettyhost kernel: [    9.974888] NET: Registered protocol family 8
May 23 09:58:34 bettyhost kernel: [    9.974894] NET: Registered protocol family 20
May 23 09:58:34 bettyhost kernel: [    9.975104] AppArmor: AppArmor Filesystem Enabled
May 23 09:58:34 bettyhost kernel: [    9.978784] Time: tsc clocksource has been installed.
May 23 09:58:34 bettyhost kernel: [    9.986932] system 00:00: iomem range 0xcc000-0xcffff has been reserved
May 23 09:58:34 bettyhost kernel: [    9.986938] system 00:00: iomem range 0xd6800-0xd7fff has been reserved
May 23 09:58:34 bettyhost kernel: [    9.986943] system 00:00: iomem range 0xf0000-0xfbfff could not be reserved
May 23 09:58:34 bettyhost kernel: [    9.986947] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
May 23 09:58:34 bettyhost kernel: [    9.986951] system 00:00: iomem range 0x2fef0000-0x2fefffff could not be reserved
May 23 09:58:34 bettyhost kernel: [    9.986955] system 00:00: iomem range 0x0-0x9ffff could not be reserved
May 23 09:58:34 bettyhost kernel: [    9.986960] system 00:00: iomem range 0x100000-0x2feeffff could not be reserved
May 23 09:58:34 bettyhost kernel: [    9.986965] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
May 23 09:58:34 bettyhost kernel: [    9.986970] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
May 23 09:58:34 bettyhost kernel: [    9.986974] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
May 23 09:58:34 bettyhost kernel: [    9.986979] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
May 23 09:58:34 bettyhost kernel: [    9.986983] system 00:00: iomem range 0xe0000-0xeffff has been reserved
May 23 09:58:34 bettyhost kernel: [    9.986995] system 00:02: ioport range 0x400-0x4bf could not be reserved
May 23 09:58:34 bettyhost kernel: [    9.987005] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
May 23 09:58:34 bettyhost kernel: [    9.987009] system 00:03: ioport range 0x800-0x87f has been reserved
May 23 09:58:34 bettyhost kernel: [   10.018506] PCI: Bridge: 0000:00:1e.0
May 23 09:58:34 bettyhost kernel: [   10.018513]   IO window: c000-cfff
May 23 09:58:34 bettyhost kernel: [   10.018521]   MEM window: ec000000-edffffff
May 23 09:58:34 bettyhost kernel: [   10.018526]   PREFETCH window: disabled.
May 23 09:58:34 bettyhost kernel: [   10.018544] PCI: Setting latency timer of device 0000:00:1e.0 to 64
May 23 09:58:34 bettyhost kernel: [   10.018567] NET: Registered protocol family 2
May 23 09:58:34 bettyhost kernel: [   10.054827] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May 23 09:58:34 bettyhost kernel: [   10.055459] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May 23 09:58:34 bettyhost kernel: [   10.057229] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May 23 09:58:34 bettyhost kernel: [   10.058142] TCP: Hash tables configured (established 131072 bind 65536)
May 23 09:58:34 bettyhost kernel: [   10.058149] TCP reno registered
May 23 09:58:34 bettyhost kernel: [   10.066953] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
May 23 09:58:34 bettyhost kernel: [   10.528944]  it is
May 23 09:58:34 bettyhost kernel: [   11.064343] Freeing initrd memory: 7310k freed
May 23 09:58:34 bettyhost kernel: [   11.064685] Simple Boot Flag at 0x59 set to 0x1
May 23 09:58:34 bettyhost kernel: [   11.066002] audit: initializing netlink socket (disabled)
May 23 09:58:34 bettyhost kernel: [   11.066027] audit(1243097868.880:1): initialized
May 23 09:58:34 bettyhost kernel: [   11.071947] VFS: Disk quotas dquot_6.5.1
May 23 09:58:34 bettyhost kernel: [   11.072156] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 23 09:58:34 bettyhost kernel: [   11.072526] io scheduler noop registered
May 23 09:58:34 bettyhost kernel: [   11.072532] io scheduler anticipatory registered
May 23 09:58:34 bettyhost kernel: [   11.072535] io scheduler deadline registered
May 23 09:58:34 bettyhost kernel: [   11.072571] io scheduler cfq registered (default)
May 23 09:58:34 bettyhost kernel: [   11.072590] Boot video device is 0000:00:02.0
May 23 09:58:34 bettyhost kernel: [   11.073588] isapnp: Scanning for PnP cards...
May 23 09:58:34 bettyhost kernel: [   11.427645] isapnp: No Plug & Play device found
May 23 09:58:34 bettyhost kernel: [   11.584594] Real Time Clock Driver v1.12ac
May 23 09:58:34 bettyhost kernel: [   11.584921] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 23 09:58:34 bettyhost kernel: [   11.585164] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 23 09:58:34 bettyhost kernel: [   11.587372] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 23 09:58:34 bettyhost kernel: [   11.587943] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
May 23 09:58:34 bettyhost kernel: [   11.596615] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 23 09:58:34 bettyhost kernel: [   11.597019] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 23 09:58:34 bettyhost kernel: [   11.597334] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May 23 09:58:34 bettyhost kernel: [   11.597340] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May 23 09:58:34 bettyhost kernel: [   11.598062] serio: i8042 KBD port at 0x60,0x64 irq 1
May 23 09:58:34 bettyhost kernel: [   11.608984] mice: PS/2 mouse device common for all mice
May 23 09:58:34 bettyhost kernel: [   11.609406] EISA: Probing bus 0 at eisa.0
May 23 09:58:34 bettyhost kernel: [   11.609450] EISA: Detected 0 cards.
May 23 09:58:34 bettyhost kernel: [   11.609456] cpuidle: using governor ladder
May 23 09:58:34 bettyhost kernel: [   11.609459] cpuidle: using governor menu
May 23 09:58:34 bettyhost kernel: [   11.609640] NET: Registered protocol family 1
May 23 09:58:34 bettyhost kernel: [   11.609703] Using IPI No-Shortcut mode
May 23 09:58:34 bettyhost kernel: [   11.609769] registered taskstats version 1
May 23 09:58:34 bettyhost kernel: [   11.609924]   Magic number: 9:860:995
May 23 09:58:34 bettyhost kernel: [   11.609941]   hash matches device ttyd8
May 23 09:58:34 bettyhost kernel: [   11.609953]   hash matches device ttyab
May 23 09:58:34 bettyhost kernel: [   11.610098] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 23 09:58:34 bettyhost kernel: [   11.610101] EDD information not available.
May 23 09:58:34 bettyhost kernel: [   11.610758] Freeing unused kernel memory: 368k freed
May 23 09:58:34 bettyhost kernel: [   11.610810] Write protecting the kernel read-only data: 806k
May 23 09:58:34 bettyhost kernel: [   11.631307] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May 23 09:58:34 bettyhost kernel: [   13.029906] fuse init (API version 7.9)
May 23 09:58:34 bettyhost kernel: [   13.074172] ACPI: Processor [CPU0] (supports 2 throttling states)
May 23 09:58:34 bettyhost kernel: [   14.017780] usbcore: registered new interface driver usbfs
May 23 09:58:34 bettyhost kernel: [   14.017822] usbcore: registered new interface driver hub
May 23 09:58:34 bettyhost kernel: [   14.029755] usbcore: registered new device driver usb
May 23 09:58:34 bettyhost kernel: [   14.049692] USB Universal Host Controller Interface driver v3.0
May 23 09:58:34 bettyhost kernel: [   14.052942] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
May 23 09:58:34 bettyhost kernel: [   14.052962] PCI: Setting latency timer of device 0000:00:1d.0 to 64
May 23 09:58:34 bettyhost kernel: [   14.052968] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May 23 09:58:34 bettyhost kernel: [   14.053471] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May 23 09:58:34 bettyhost kernel: [   14.053517] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000d800
May 23 09:58:34 bettyhost kernel: [   14.053808] usb usb1: configuration #1 chosen from 1 choice
May 23 09:58:34 bettyhost kernel: [   14.053857] hub 1-0:1.0: USB hub found
May 23 09:58:34 bettyhost kernel: [   14.053869] hub 1-0:1.0: 2 ports detected
May 23 09:58:34 bettyhost kernel: [   14.123005] SCSI subsystem initialized
May 23 09:58:34 bettyhost kernel: [   14.165049] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
May 23 09:58:34 bettyhost kernel: [   14.165068] PCI: Setting latency timer of device 0000:00:1d.1 to 64
May 23 09:58:34 bettyhost kernel: [   14.165074] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May 23 09:58:34 bettyhost kernel: [   14.165131] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May 23 09:58:34 bettyhost kernel: [   14.165168] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000d000
May 23 09:58:34 bettyhost kernel: [   14.165374] usb usb2: configuration #1 chosen from 1 choice
May 23 09:58:34 bettyhost kernel: [   14.165425] hub 2-0:1.0: USB hub found
May 23 09:58:34 bettyhost kernel: [   14.165471] hub 2-0:1.0: 2 ports detected
May 23 09:58:34 bettyhost kernel: [   14.238954] libata version 3.00 loaded.
May 23 09:58:34 bettyhost kernel: [   14.269537] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
May 23 09:58:34 bettyhost kernel: [   14.269557] PCI: Setting latency timer of device 0000:00:1d.2 to 64
May 23 09:58:34 bettyhost kernel: [   14.269564] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May 23 09:58:34 bettyhost kernel: [   14.269622] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May 23 09:58:34 bettyhost kernel: [   14.269660] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000d400
May 23 09:58:34 bettyhost kernel: [   14.269892] usb usb3: configuration #1 chosen from 1 choice
May 23 09:58:34 bettyhost kernel: [   14.269942] hub 3-0:1.0: USB hub found
May 23 09:58:34 bettyhost kernel: [   14.269955] hub 3-0:1.0: 2 ports detected
May 23 09:58:34 bettyhost kernel: [   14.373477] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
May 23 09:58:34 bettyhost kernel: [   14.373505] PCI: Setting latency timer of device 0000:00:1d.7 to 64
May 23 09:58:34 bettyhost kernel: [   14.373510] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May 23 09:58:34 bettyhost kernel: [   14.373577] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
May 23 09:58:34 bettyhost kernel: [   14.377537] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
May 23 09:58:34 bettyhost kernel: [   14.377558] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xee080000
May 23 09:58:34 bettyhost kernel: [   14.400553] Floppy drive(s): fd0 is 1.44M
May 23 09:58:34 bettyhost kernel: [   14.405196] usb 1-2: new low speed USB device using uhci_hcd and address 2
May 23 09:58:34 bettyhost kernel: [   14.417157] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May 23 09:58:34 bettyhost kernel: [   14.417383] usb usb4: configuration #1 chosen from 1 choice
May 23 09:58:34 bettyhost kernel: [   14.417436] hub 4-0:1.0: USB hub found
May 23 09:58:34 bettyhost kernel: [   14.417450] hub 4-0:1.0: 6 ports detected
May 23 09:58:35 bettyhost kernel: [   14.421328] FDC 0 is a post-1991 82077
May 23 09:58:35 bettyhost kernel: [   14.521487] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 17
May 23 09:58:35 bettyhost kernel: [   14.521504] 3c59x: Donald Becker and others.
May 23 09:58:35 bettyhost kernel: [   14.521513] 0000:01:04.0: 3Com PCI 3c905C Tornado at f0820000.
May 23 09:58:35 bettyhost kernel: [   14.549397] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 17 (level, low) -> IRQ 16
May 23 09:58:35 bettyhost kernel: [   14.568992] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
May 23 09:58:35 bettyhost kernel: [   14.569003] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
May 23 09:58:35 bettyhost kernel: [   14.569011] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
May 23 09:58:35 bettyhost kernel: [   14.609022] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
May 23 09:58:35 bettyhost kernel: [   14.609071] b44.c:v2.0
May 23 09:58:35 bettyhost kernel: [   14.609120] ata_piix 0000:00:1f.1: version 2.12
May 23 09:58:35 bettyhost kernel: [   14.609146] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
May 23 09:58:35 bettyhost kernel: [   14.609227] PCI: Setting latency timer of device 0000:00:1f.1 to 64
May 23 09:58:35 bettyhost kernel: [   14.611102] scsi0 : ata_piix
May 23 09:58:35 bettyhost kernel: [   14.613029] scsi1 : ata_piix
May 23 09:58:35 bettyhost kernel: [   14.613975] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May 23 09:58:35 bettyhost kernel: [   14.613982] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May 23 09:58:35 bettyhost kernel: [   14.629476] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0b:db:11:ac:ec
May 23 09:58:35 bettyhost kernel: [   14.785008] ata1.00: HPA unlocked: 58593750 -> 58633344, native 58633344
May 23 09:58:35 bettyhost kernel: [   14.785017] ata1.00: ATA-5: WDC WD300BB-75DEA0, 05.03E05, max UDMA/100
May 23 09:58:35 bettyhost kernel: [   14.785022] ata1.00: 58633344 sectors, multi 16: LBA 
May 23 09:58:35 bettyhost kernel: [   14.801896] ata1.00: configured for UDMA/100
May 23 09:58:35 bettyhost kernel: [   14.956745] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 23 09:58:35 bettyhost kernel: [   14.956752] ata2: failed to recover some devices, retrying in 5 secs
May 23 09:58:35 bettyhost kernel: [   15.028438] usb 1-2: new low speed USB device using uhci_hcd and address 3
May 23 09:58:35 bettyhost kernel: [   15.205094] usb 1-2: configuration #1 chosen from 1 choice
May 23 09:58:35 bettyhost kernel: [   15.794481] usbcore: registered new interface driver hiddev
May 23 09:58:35 bettyhost kernel: [   15.807518] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
May 23 09:58:35 bettyhost kernel: [   15.819463] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
May 23 09:58:35 bettyhost kernel: [   15.819493] usbcore: registered new interface driver usbhid
May 23 09:58:35 bettyhost kernel: [   15.819499] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
May 23 09:58:35 bettyhost kernel: [   20.110119] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 23 09:58:35 bettyhost kernel: [   20.110127] ata2: failed to recover some devices, retrying in 5 secs
May 23 09:58:35 bettyhost kernel: [   25.263571] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
May 23 09:58:35 bettyhost kernel: [   25.263578] ata2: failed to recover some devices, retrying in 5 secs
May 23 09:58:35 bettyhost kernel: [   30.580993] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-248F, R602, max UDMA/33
May 23 09:58:35 bettyhost kernel: [   30.752751] ata2.00: configured for UDMA/33
May 23 09:58:35 bettyhost kernel: [   30.752975] scsi 0:0:0:0: Direct-Access     ATA      WDC WD300BB-75DE 05.0 PQ: 0 ANSI: 5
May 23 09:58:35 bettyhost kernel: [   30.755625] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-248F  R602 PQ: 0 ANSI: 5
May 23 09:58:35 bettyhost kernel: [   30.785707] Driver 'sd' needs updating - please use bus_type methods
May 23 09:58:35 bettyhost kernel: [   30.785879] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
May 23 09:58:35 bettyhost kernel: [   30.785916] sd 0:0:0:0: [sda] Write Protect is off
May 23 09:58:35 bettyhost kernel: [   30.785922] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 23 09:58:35 bettyhost kernel: [   30.785972] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 23 09:58:35 bettyhost kernel: [   30.786095] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
May 23 09:58:35 bettyhost kernel: [   30.786125] sd 0:0:0:0: [sda] Write Protect is off
May 23 09:58:35 bettyhost kernel: [   30.786130] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 23 09:58:35 bettyhost kernel: [   30.786179] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 23 09:58:35 bettyhost kernel: [   30.786189]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May 23 09:58:35 bettyhost kernel: [   30.816147]  sda1 sda2 < sda5 >
May 23 09:58:35 bettyhost kernel: [   30.847738] sd 0:0:0:0: [sda] Attached SCSI disk
May 23 09:58:35 bettyhost kernel: [   30.862532] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 23 09:58:35 bettyhost kernel: [   30.862570] sr 1:0:0:0: Attached scsi generic sg1 type 5
May 23 09:58:35 bettyhost kernel: [   30.865457] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May 23 09:58:35 bettyhost kernel: [   30.865466] Uniform CD-ROM driver Revision: 3.20
May 23 09:58:35 bettyhost kernel: [   30.865561] sr 1:0:0:0: Attached scsi CD-ROM sr0
May 23 09:58:35 bettyhost kernel: [   31.326669] Attempting manual resume
May 23 09:58:35 bettyhost kernel: [   31.326677] swsusp: Resume From Partition 8:5
May 23 09:58:35 bettyhost kernel: [   31.326680] PM: Checking swsusp image.
May 23 09:58:35 bettyhost kernel: [   31.326921] PM: Resume from disk failed.
May 23 09:58:35 bettyhost kernel: [   31.390948] kjournald starting.  Commit interval 5 seconds
May 23 09:58:35 bettyhost kernel: [   31.390977] EXT3-fs: mounted filesystem with ordered data mode.
May 23 09:58:35 bettyhost kernel: [   44.872769] Linux agpgart interface v0.102
May 23 09:58:35 bettyhost kernel: [   44.988027] intel_rng: FWH not detected
May 23 09:58:35 bettyhost kernel: [   45.023352] agpgart: Detected an Intel 830M Chipset.
May 23 09:58:35 bettyhost kernel: [   45.023501] agpgart: Detected 892K stolen memory.
May 23 09:58:35 bettyhost kernel: [   45.044762] agpgart: AGP aperture is 128M @ 0xe0000000
May 23 09:58:35 bettyhost kernel: [   45.078463] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 23 09:58:35 bettyhost kernel: [   45.110645] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 23 09:58:35 bettyhost kernel: [   45.345859] iTCO_vendor_support: vendor-support=0
May 23 09:58:35 bettyhost kernel: [   45.417773] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
May 23 09:58:35 bettyhost kernel: [   45.417930] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
May 23 09:58:35 bettyhost kernel: [   45.417985] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
May 23 09:58:35 bettyhost kernel: [   45.551913] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
May 23 09:58:35 bettyhost kernel: [   45.791918] input: Power Button (FF) as /devices/virtual/input/input3
May 23 09:58:35 bettyhost kernel: [   45.801268] ACPI: Power Button (FF) [PWRF]
May 23 09:58:35 bettyhost kernel: [   45.801491] input: Power Button (CM) as /devices/virtual/input/input4
May 23 09:58:35 bettyhost kernel: [   45.817211] ACPI: Power Button (CM) [PWRB]
May 23 09:58:35 bettyhost kernel: [   45.850574] input: PC Speaker as /devices/platform/pcspkr/input/input5
May 23 09:58:35 bettyhost kernel: [   47.751196] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 16
May 23 09:58:35 bettyhost kernel: [   47.751237] PCI: Setting latency timer of device 0000:00:1f.5 to 64
May 23 09:58:35 bettyhost kernel: [   48.004032] parport_pc 00:0a: reported by Plug and Play ACPI
May 23 09:58:35 bettyhost kernel: [   48.004066] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
May 23 09:58:35 bettyhost kernel: [   48.170218] intel8x0_measure_ac97_clock: measured 54747 usecs
May 23 09:58:35 bettyhost kernel: [   48.170224] intel8x0: clocking to 48000
May 23 09:58:35 bettyhost kernel: [   48.515040] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
May 23 09:58:35 bettyhost kernel: [   51.446149] loop: module loaded
May 23 09:58:35 bettyhost kernel: [   51.480229] lp0: using parport0 (interrupt-driven).
May 23 09:58:35 bettyhost kernel: [   51.635501] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
May 23 09:58:35 bettyhost kernel: [   52.250844] EXT3 FS on sda1, internal journal
May 23 09:58:35 bettyhost kernel: [   53.880221] ip_tables: (C) 2000-2006 Netfilter Core Team
May 23 09:58:35 bettyhost kernel: [   54.726591] No dock devices found.
May 23 09:58:35 bettyhost kernel: [   56.928181] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May 23 09:58:35 bettyhost kernel: [   56.928191] apm: overridden by ACPI.
May 23 09:58:35 bettyhost kernel: [   57.122602] ppdev: user-space parallel port driver
May 23 09:58:36 bettyhost kernel: [   57.586058] audit(1243097916.276:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5151 profile="/usr/sbin/cupsd" namespace="default"
May 23 09:58:38 bettyhost kernel: [   59.885032] eth0:  setting half-duplex.
May 23 09:58:38 bettyhost kernel: [   60.073006] Bluetooth: Core ver 2.11
May 23 09:58:38 bettyhost kernel: [   60.076853] NET: Registered protocol family 31
May 23 09:58:38 bettyhost kernel: [   60.076863] Bluetooth: HCI device and connection manager initialized
May 23 09:58:38 bettyhost kernel: [   60.076870] Bluetooth: HCI socket layer initialized
May 23 09:58:38 bettyhost kernel: [   60.136280] Bluetooth: L2CAP ver 2.9
May 23 09:58:38 bettyhost kernel: [   60.136289] Bluetooth: L2CAP socket layer initialized
May 23 09:58:38 bettyhost kernel: [   60.278295] Bluetooth: RFCOMM socket layer initialized
May 23 09:58:38 bettyhost kernel: [   60.278324] Bluetooth: RFCOMM TTY layer initialized
May 23 09:58:38 bettyhost kernel: [   60.278327] Bluetooth: RFCOMM ver 1.8
May 23 09:58:41 bettyhost kernel: [   62.553457] [drm] Initialized drm 1.1.0 20060810
May 23 09:58:41 bettyhost kernel: [   62.640775] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
May 23 09:58:41 bettyhost kernel: [   62.640793] PCI: Setting latency timer of device 0000:00:02.0 to 64
May 23 09:58:41 bettyhost kernel: [   62.640949] [drm] Initialized i915 1.6.0 20060119 on minor 0
May 23 09:59:03 bettyhost kernel: [   85.267119] NET: Registered protocol family 10
May 23 09:59:06 bettyhost kernel: [   85.268089] lo: Disabled Privacy Extensions
May 23 09:59:06 bettyhost kernel: [   85.269221] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 23 09:59:06 bettyhost kernel: [   85.270784] ADDRCONF(NETDEV_UP): eth1: link is not ready
May 23 09:59:56 bettyhost kernel: [  137.784834] eth0:  setting full-duplex.
May 23 09:59:56 bettyhost kernel: [  137.789218] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 23 09:59:58 bettyhost kernel: [  140.082934] NET: Registered protocol family 17
May 23 10:00:06 bettyhost kernel: [  148.055128] eth0: no IPv6 routers present

```

---

### Post by sedawk on 2009-05-23
Do you have a second PC connected to the same network?
You can activate sshd on the Ubuntu machine (if it is not actived by
default) and when the screen stays blank you can login via ssh
and check the log files.

If you do not have a second PC things get more tricky:

* Write a script that collects important data and run it
  via /etc/rc.local or as a cronjob.
  Check what is different when the system fails to start
  properly

* Learn how to do basic things blindly: Rebooting the machine
  (Ctrl+Alt+Del ?). Shutting the machine down.
  Restarting X (Ctrl+Alt+Backspace ?).
  Switching to a text console ( (Ctrl+) Alt+F1 ?)
  to login and restart gdm (sudo /etc/init.d/gdm restart).

Do you have any external USB drives? I sometimes have a similar
problem and I think this happens when I turned on the USB drives
before booting the Ubuntu machine.

---

### Post by PGScooter on 2009-05-25
sedawk, thanks for the reply. I do not have any external usb drives. I do, however, have a printer attached to the computer. I have tested (thanks to your suggestion) whether it makes a difference if it is turned on or not at boot and it does not seem to matter.

I am not sure what "important data" you suggest I collect. Aren't most important logs archived anyway?

Thanks

---

### Post by PGScooter on 2009-06-11
I had a usb printer connected to the desktop. Ensuring that it is turned off before turning the computer on seems to have solved the problem. If someone thinks its worthwhile, I will file a bug report.

---

