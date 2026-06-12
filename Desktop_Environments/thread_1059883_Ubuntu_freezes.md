---
title: "Ubuntu freezes"
date: 2009-02-04
forum: Desktop Environments
---

### Post by chetankharche on 2009-02-04
Hi,
I have installed Ubuntu 8.04 desktop edition on my toshiba laptop. But ubuntu seems to freeze on many occassions. I am using gnome. I am not able to do anything when this happens. I can only keep moving the mouse but am not able to do anything else. Can any one tell me if this happens to everyone or is there any solutions for this..

Thanks

---

### Post by ncubede on 2009-02-04
I'd assume your problem is hardware related, or you have a serious shortage of OS resources. You did not give a lot of information about what your platform is, whether you have any strange output in ```
dmesg
``` or elsewhere, whether your system is swapping, e.g. check ```
top
```.

And, no, this is not normal if the system's base hardware is working correctly. it can happen of course, but is not normal.

---

### Post by chetankharche on 2009-02-04
Ok, about my system i have core duo 2 processor 1.8ghz, 2gb ram, 120 gb hard drive. Also am attaching the output of dmesg and top below.

**output of dmesg**
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:13:11 UTC 2009 (Ubuntu 2.6.24-23.48-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f670000 (usable)
[    0.000000]  BIOS-e820: 000000007f670000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f65c0
[    0.000000] Entering add_active_range(0, 0, 521840) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521840
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521840
[    0.000000] On node 0 totalpages: 521840
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2284 pages used for memmap
[    0.000000]   HighMem zone: 290180 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6510 checksum 0
[    0.000000] ACPI: RSDP 000F6510, 0014 (r0 TOSINV)
[    0.000000] ACPI: RSDT 7F67E1F8, 0048 (r1 TOSINV Capell00  6040000  LTP        0)
[    0.000000] ACPI: FACP 7F685DEE, 0074 (r1 TOSINV CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: DSDT 7F67F8EF, 64FF (r1 TOSINV CALISTGA  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 7F686FC0, 0040
[    0.000000] ACPI: APIC 7F685E62, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7F685ECA, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7F685F02, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: BOOT 7F685FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: APIC 7F685F70, 0068 (r1 TOSINV   APIC    6040000  LTP        0)
[    0.000000] ACPI: SSDT 7F67F29C, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F67EC0A, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F67E240, 04F6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517764
[    0.000000] Kernel command line: root=UUID=f8ed13dd-3ee9-448d-8552-45315395efbf ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.058 MHz processor.
[   29.482604] Console: colour VGA+ 80x25
[   29.482610] console [tty0] enabled
[   29.482952] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   29.483615] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.743341] Memory: 2057512k/2087360k available (2179k kernel code, 28644k reserved, 1008k data, 368k init, 1169856k highmem)
[   29.743359] virtual kernel memory layout:
[   29.743361]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   29.743364]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   29.743367]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   29.743370]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   29.743372]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   29.743375]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   29.743378]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[   29.743385] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.743451] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   29.743619] hpet clockevent registered
[   29.823552] Calibrating delay using timer specific routine.. 3196.78 BogoMIPS (lpj=6393570)
[   29.823590] Security Framework initialized
[   29.823602] SELinux:  Disabled at boot.
[   29.823629] AppArmor: AppArmor initialized
[   29.823637] Failure registering capabilities with primary security module.
[   29.823653] Mount-cache hash table entries: 512
[   29.823872] Initializing cgroup subsys ns
[   29.823881] Initializing cgroup subsys cpuacct
[   29.823901] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
[   29.823916] monitor/mwait feature present.
[   29.823920] using mwait in idle threads.
[   29.823928] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.823933] CPU: L2 cache: 2048K
[   29.823938] CPU: Physical Processor ID: 0
[   29.823942] CPU: Processor Core ID: 0
[   29.823946] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00042940 0000c189 00000000 00000000 00000000
[   29.823965] Compat vDSO mapped to ffffe000.
[   29.823989] Checking 'hlt' instruction... OK.
[   29.840283] SMP alternatives: switching to UP code
[   29.844586] Early unpacking initramfs... done
[   30.603023] ACPI: Core revision 20070126
[   30.603144] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   30.674402] CPU0: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[   30.674434] SMP alternatives: switching to SMP code
[   30.675726] Booting processor 1/1 eip 3000
[   30.686228] Initializing CPU#1
[   30.762651] Calibrating delay using timer specific routine.. 3192.18 BogoMIPS (lpj=6384363)
[   30.762665] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
[   30.762676] monitor/mwait feature present.
[   30.762682] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.762686] CPU: L2 cache: 2048K
[   30.762690] CPU: Physical Processor ID: 0
[   30.762694] CPU: Processor Core ID: 1
[   30.762697] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00042940 0000c189 00000000 00000000 00000000
[   30.763662] CPU1: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[   30.763704] Total of 2 processors activated (6388.96 BogoMIPS).
[   30.763913] ENABLING IO-APIC IRQs
[   30.764144] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   30.910715] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   30.930723] Brought up 2 CPUs
[   30.930766] CPU0 attaching sched-domain:
[   30.930772]  domain 0: span 03
[   30.930776]   groups: 01 02
[   30.930783] CPU1 attaching sched-domain:
[   30.930787]  domain 0: span 03
[   30.930790]   groups: 02 01
[   30.931257] net_namespace: 64 bytes
[   30.931274] Booting paravirtualized kernel on bare hardware
[   30.932214] Time: 15:10:25  Date: 02/04/09
[   30.932268] NET: Registered protocol family 16
[   30.932693] EISA bus registered
[   30.932702] ACPI: bus type pci registered
[   30.933046] PCI: PCI BIOS revision 2.10 entry at 0xfd875, last bus=7
[   30.933051] PCI: Using configuration type 1
[   30.933069] Setting up standard PCI resources
[   30.940733] ACPI: EC: Look up EC in DSDT
[   30.967852] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   30.968968] ACPI: Interpreter enabled
[   30.968974] ACPI: (supports S0 S3 S4 S5)
[   30.969004] ACPI: Using IOAPIC for interrupt routing
[   31.047624] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[   31.047631] ACPI: EC: driver started in poll mode
[   31.047726] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.048870] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   31.048878] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   31.050442] PCI: Transparent bridge - 0000:00:1e.0
[   31.050590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.051323] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   31.051627] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   31.051929] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   31.052255] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   31.175153] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   31.175395] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   31.175624] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   31.175852] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   31.176080] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   31.176308] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   31.176538] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   31.176769] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   31.177098] ACPI: Power Resource [FN00] (off)
[   31.177205] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.177269] pnp: PnP ACPI init
[   31.177284] ACPI: bus type pnp registered
[   31.250788] pnp: PnP ACPI: found 10 devices
[   31.250793] ACPI: ACPI bus type pnp unregistered
[   31.250802] PnPBIOS: Disabled by ACPI PNP
[   31.251295] PCI: Using ACPI for IRQ routing
[   31.251301] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.310147] NET: Registered protocol family 8
[   31.310151] NET: Registered protocol family 20
[   31.310219] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   31.310229] hpet0: 3 64-bit timers, 14318180 Hz
[   31.311294] AppArmor: AppArmor Filesystem Enabled
[   31.314130] Time: tsc clocksource has been installed.
[   31.314155] Switched to high resolution mode on CPU 0
[   31.314347] Switched to high resolution mode on CPU 1
[   31.326118] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   31.326126] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   31.326133] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   31.326140] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   31.326147] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   31.326154] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   31.326161] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   31.326177] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   31.326192] system 00:06: ioport range 0x400-0x401 has been reserved
[   31.326198] system 00:06: ioport range 0x680-0x69f has been reserved
[   31.326204] system 00:06: ioport range 0x800-0x80f has been reserved
[   31.326211] system 00:06: ioport range 0x1000-0x107f has been reserved
[   31.326217] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   31.326223] system 00:06: ioport range 0x1640-0x164f has been reserved
[   31.357097] PCI: Bridge: 0000:00:1c.0
[   31.357101]   IO window: disabled.
[   31.357110]   MEM window: disabled.
[   31.357117]   PREFETCH window: disabled.
[   31.357126] PCI: Bridge: 0000:00:1c.1
[   31.357132]   IO window: 2000-2fff
[   31.357141]   MEM window: d8000000-d9ffffff
[   31.357149]   PREFETCH window: d2000000-d3ffffff
[   31.357158] PCI: Bridge: 0000:00:1c.2
[   31.357164]   IO window: 3000-3fff
[   31.357173]   MEM window: da000000-dbffffff
[   31.357180]   PREFETCH window: d4000000-d5ffffff
[   31.357203] PCI: Bus 8, cardbus bridge: 0000:07:06.0
[   31.357208]   IO window: 00004400-000044ff
[   31.357216]   IO window: 00004800-000048ff
[   31.357224]   PREFETCH window: 88000000-8bffffff
[   31.357232]   MEM window: 8c000000-8fffffff
[   31.357240] PCI: Bridge: 0000:00:1e.0
[   31.357246]   IO window: 4000-4fff
[   31.357255]   MEM window: dc000000-dc0fffff
[   31.357262]   PREFETCH window: disabled.
[   31.357308] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   31.357320] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.357354] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   31.357365] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   31.357399] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   31.357410] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   31.357430] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   31.357454] PCI: Enabling device 0000:07:06.0 (0000 -> 0003)
[   31.357461] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   31.357489] NET: Registered protocol family 2
[   31.394089] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.394532] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   31.396070] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.396837] TCP: Hash tables configured (established 131072 bind 65536)
[   31.396843] TCP reno registered
[   31.406242] checking if image is initramfs... it is
[   32.906934] Freeing initrd memory: 7319k freed
[   32.907176] Simple Boot Flag at 0x36 set to 0x1
[   32.908508] audit: initializing netlink socket (disabled)
[   32.908528] audit(1233760225.980:1): initialized
[   32.908932] highmem bounce pool size: 64 pages
[   32.913159] VFS: Disk quotas dquot_6.5.1
[   32.913319] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.913579] io scheduler noop registered
[   32.913584] io scheduler anticipatory registered
[   32.913588] io scheduler deadline registered
[   32.913612] io scheduler cfq registered (default)
[   32.913629] Boot video device is 0000:00:02.0
[   32.913767] PCI: Firmware left 0000:07:08.0 e100 interrupts enabled, disabling
[   32.913983] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   32.914061] assign_interrupt_mode Found MSI capability
[   32.914128] Allocate Port Service[0000:00:1c.0:pcie00]
[   32.914203] Allocate Port Service[0000:00:1c.0:pcie02]
[   32.914363] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   32.914440] assign_interrupt_mode Found MSI capability
[   32.914502] Allocate Port Service[0000:00:1c.1:pcie00]
[   32.914572] Allocate Port Service[0000:00:1c.1:pcie02]
[   32.914732] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   32.914808] assign_interrupt_mode Found MSI capability
[   32.914870] Allocate Port Service[0000:00:1c.2:pcie00]
[   32.914940] Allocate Port Service[0000:00:1c.2:pcie02]
[   32.915436] isapnp: Scanning for PnP cards...
[   33.270037] isapnp: No Plug & Play device found
[   33.328444] Real Time Clock Driver v1.12ac
[   33.328872] hpet_resources: 0xfed00000 is busy
[   33.328932] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.331411] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.331551] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   33.331755] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   33.334553] i8042.c: Detected active multiplexing controller, rev 1.1.
[   33.336051] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.336060] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   33.336066] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   33.336072] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   33.336077] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   33.364279] mice: PS/2 mouse device common for all mice
[   33.364516] EISA: Probing bus 0 at eisa.0
[   33.364528] Cannot allocate resource for EISA slot 1
[   33.364534] Cannot allocate resource for EISA slot 2
[   33.364538] Cannot allocate resource for EISA slot 3
[   33.364543] Cannot allocate resource for EISA slot 4
[   33.364571] EISA: Detected 0 cards.
[   33.364577] cpuidle: using governor ladder
[   33.364581] cpuidle: using governor menu
[   33.364744] NET: Registered protocol family 1
[   33.364796] Using IPI No-Shortcut mode
[   33.364845] registered taskstats version 1
[   33.365047]   Magic number: 13:480:183
[   33.365084]   hash matches device ttyr9
[   33.365176] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   33.365181] EDD information not available.
[   33.365455] Freeing unused kernel memory: 368k freed
[   33.365514] Write protecting the kernel read-only data: 806k
[   33.398038] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   34.824284] fuse init (API version 7.9)
[   34.852237] ACPI: Transitioning device [FAN0] to D3
[   34.852244] ACPI: Transitioning device [FAN0] to D3
[   34.852251] ACPI: Fan [FAN0] (off)
[   34.865490] ACPI: SSDT 7F67E997, 01EA (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   34.865974] ACPI: SSDT 7F67E736, 01DC (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   34.866948] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   34.866959] ACPI: Processor [CPU0] (supports 8 throttling states)
[   34.867498] ACPI: SSDT 7F67EB81, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   34.867955] ACPI: SSDT 7F67E912, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   34.869105] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   34.869117] ACPI: Processor [CPU1] (supports 8 throttling states)
[   34.871687] ACPI: Thermal Zone [TZ00] (38 C)
[   34.873759] ACPI: Invalid passive threshold
[   34.878663] ACPI: Transitioning device [FAN0] to D0
[   34.878668] ACPI: Transitioning device [FAN0] to D0
[   34.878673] ACPI: Unable to turn cooling device [f7c47450] 'on'
[   34.878680] ACPI: Thermal Zone [TZ01] (33 C)
[   35.745255] usbcore: registered new interface driver usbfs
[   35.745301] usbcore: registered new interface driver hub
[   35.746463] SCSI subsystem initialized
[   35.763752] usbcore: registered new device driver usb
[   35.768390] USB Universal Host Controller Interface driver v3.0
[   35.768480] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   35.768500] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   35.768508] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   35.768840] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   35.768888] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   35.769155] usb usb1: configuration #1 chosen from 1 choice
[   35.769206] hub 1-0:1.0: USB hub found
[   35.769218] hub 1-0:1.0: 2 ports detected
[   35.814621] libata version 3.00 loaded.
[   35.869871] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   35.869892] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   35.869900] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   35.869949] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   35.869994] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   35.870227] usb usb2: configuration #1 chosen from 1 choice
[   35.870275] hub 2-0:1.0: USB hub found
[   35.870286] hub 2-0:1.0: 2 ports detected
[   35.910797] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   35.910804] e100: Copyright(c) 1999-2006 Intel Corporation
[   35.973788] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   35.973810] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   35.973818] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   35.973864] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   35.973910] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   35.974134] usb usb3: configuration #1 chosen from 1 choice
[   35.974188] hub 3-0:1.0: USB hub found
[   35.974200] hub 3-0:1.0: 2 ports detected
[   36.077687] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   36.077709] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   36.077717] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   36.077763] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   36.077810] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   36.078047] usb usb4: configuration #1 chosen from 1 choice
[   36.078097] hub 4-0:1.0: USB hub found
[   36.078108] hub 4-0:1.0: 2 ports detected
[   36.181618] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   36.181642] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   36.181650] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   36.181701] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   36.185632] ehci_hcd 0000:00:1d.7: debug port 1
[   36.185643] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   36.185656] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xdc444000
[   36.202415] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.202623] usb usb5: configuration #1 chosen from 1 choice
[   36.202675] hub 5-0:1.0: USB hub found
[   36.202687] hub 5-0:1.0: 8 ports detected
[   36.306707] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   36.336935] e100: eth0: e100_probe: addr 0xdc005000, irq 21, MAC addr 00:a0:d1:4c:b7:0b
[   36.337000] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 16
[   36.386902] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[dc006000-dc0067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   36.387510] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   36.387577] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   36.387601] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   36.393057] ata_piix 0000:00:1f.2: version 2.12
[   36.393067] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   36.546096] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   36.546157] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   36.547919] scsi0 : ata_piix
[   36.549024] scsi1 : ata_piix
[   36.550985] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[   36.550992] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[   36.713423] ata1.00: ATA-7: TOSHIBA MK1234GSX, AH001A, max UDMA/100
[   36.713433] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   36.721434] ata1.00: configured for UDMA/100
[   36.920721] Clocksource tsc unstable (delta = -349027007 ns)
[   36.924862] Time: hpet clocksource has been installed.
[   36.950593] ata2.00: ATAPI: PIONEER DVD-RW  DVR-K16A, 1.63, max UDMA/33
[   36.980050] ata2.00: configured for UDMA/33
[   36.980363] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1234GS AH00 PQ: 0 ANSI: 5
[   36.987386] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-K16A 1.63 PQ: 0 ANSI: 5
[   37.006529] Driver 'sd' needs updating - please use bus_type methods
[   37.006674] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   37.006701] sd 0:0:0:0: [sda] Write Protect is off
[   37.006706] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.006744] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.006832] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   37.006860] sd 0:0:0:0: [sda] Write Protect is off
[   37.006865] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.006903] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.006911]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   37.038207]  sda1 sda2 < sda5 >
[   37.066672] sd 0:0:0:0: [sda] Attached SCSI disk
[   37.078063] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   37.078104] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   37.081287] sr0: scsi3-mmc drive: 31x/31x writer dvd-ram cd/rw xa/form2 cdda tray
[   37.081295] Uniform CD-ROM driver Revision: 3.20
[   37.081385] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   37.815153] kjournald starting.  Commit interval 5 seconds
[   37.815191] EXT3-fs: mounted filesystem with ordered data mode.
[   46.867130] Linux agpgart interface v0.102
[   46.943091] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.101774] agpgart: Detected an Intel 945GM Chipset.
[   47.104026] agpgart: Detected 7932K stolen memory.
[   47.124749] agpgart: AGP aperture is 256M @ 0xc0000000
[   47.178567] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.438525] intel_rng: FWH not detected
[   47.774117] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   47.775288] ACPI: AC Adapter [ADP0] (on-line)
[   47.801284] iTCO_vendor_support: vendor-support=0
[   47.826144] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   47.826287] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   47.826351] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   47.846287] input: Power Button (FF) as /devices/virtual/input/input2
[   47.870039] ACPI: Power Button (FF) [PWRF]
[   47.870152] input: Lid Switch as /devices/virtual/input/input3
[   47.870287] ACPI: Lid Switch [LID]
[   47.870384] input: Power Button (CM) as /devices/virtual/input/input4
[   47.886026] ACPI: Power Button (CM) [PWRB]
[   47.921311] ACPI: Battery Slot [BAT0] (battery present)
[   48.093976] Yenta: CardBus bridge found at 0000:07:06.0 [1179:ff10]
[   48.094007] Yenta: Enabling burst memory read transactions
[   48.094016] Yenta: Using CSCINT to route CSC interrupts to PCI
[   48.094021] Yenta: Routing CardBus interrupts to PCI
[   48.094031] Yenta TI: socket 0000:07:06.0, mfunc 0x01a01b22, devctl 0x66
[   48.326465] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   48.326474] Socket status: 30000006
[   48.326479] Yenta: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[   48.326488] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   48.326494] cs: IO port probe 0x4000-0x4fff: clean.
[   48.327115] pcmcia: parent PCI bridge Memory window: 0xdc000000 - 0xdc0fffff
[   48.354696] sdhci: Secure Digital Host Controller Interface driver
[   48.354703] sdhci: Copyright(c) Pierre Ossman
[   48.405835] ACPI: PCI Interrupt 0000:07:06.2[A] -> GSI 18 (level, low) -> IRQ 18
[   48.405958] sdhci: SDHCI controller found at 0000:07:06.3 [104c:803c] (rev 0)
[   48.405983] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 18
[   48.406077] mmc0: SDHCI at 0xdc006800 irq 18 DMA
[   48.711417] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   48.711425] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   48.711666] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   48.711687] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   48.711724] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   48.938084] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5
[   48.956963] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   48.957674] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
[   48.972935] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   50.152953] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   50.152998] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   50.178442] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[   50.685213] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   51.018142] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   51.018156] synaptics: Toshiba Satellite A105 detected, limiting rate to 40pps.
[   51.049991] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   52.633238] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   52.637948] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   52.798504] cs: IO port probe 0x100-0x3af: clean.
[   52.800726] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   52.801690] cs: IO port probe 0x820-0x8ff: clean.
[   52.802491] cs: IO port probe 0xc00-0xcf7: clean.
[   52.803592] cs: IO port probe 0xa00-0xaff: clean.
[   53.385708] lp: driver loaded but no devices found
[   54.002385] EXT3 FS on sda1, internal journal
[   55.209393] ip_tables: (C) 2000-2006 Netfilter Core Team
[   55.804589] ACPI: Error installing notify handler
[   55.804720] No dock devices found.
[   57.286376] apm: BIOS not found.
[   57.420092] ppdev: user-space parallel port driver
[   57.569172] audit(1233760256.473:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5347 profile="/usr/sbin/cupsd" namespace="default"
[   62.982301] Bluetooth: Core ver 2.11
[   62.982463] NET: Registered protocol family 31
[   62.982467] Bluetooth: HCI device and connection manager initialized
[   62.982475] Bluetooth: HCI socket layer initialized
[   63.021250] Bluetooth: L2CAP ver 2.9
[   63.021262] Bluetooth: L2CAP socket layer initialized
[   63.071623] Bluetooth: RFCOMM socket layer initialized
[   63.071639] Bluetooth: RFCOMM TTY layer initialized
[   63.071641] Bluetooth: RFCOMM ver 1.8
[   64.547732] /dev/vmmon[5731]: Module vmmon: registered with major=10 minor=165
[   64.547751] /dev/vmmon[5731]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
[   64.547754] /dev/vmmon[5731]: Module vmmon: initialized
[   64.591757] /dev/vmci[5742]: VMCI: Driver initialized.
[   64.591806] /dev/vmci[5742]: Module vmci: registered with major=10 minor=63
[   64.591809] /dev/vmci[5742]: Module vmci: initialized
[   64.621642] vsock: no version for "VMCIDatagram_Send" found: kernel tainted.
[   65.506192] [drm] Initialized drm 1.1.0 20060810
[   65.522433] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   65.522452] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   65.522587] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   66.634714] /dev/vmnet: open called by PID 5835 (vmnet-netifup)
[   66.634733] /dev/vmnet: hub 1 does not exist, allocating memory.
[   66.634759] /dev/vmnet: port on hub 1 successfully opened
[   66.999059] /dev/vmnet: open called by PID 5834 (vmnet-dhcpd)
[   66.999083] /dev/vmnet: port on hub 1 successfully opened
[   67.023390] /dev/vmnet: open called by PID 5868 (vmnet-netifup)
[   67.023681] /dev/vmnet: hub 8 does not exist, allocating memory.
[   67.023946] /dev/vmnet: port on hub 8 successfully opened
[   67.195246] /dev/vmnet: open called by PID 5872 (vmnet-dhcpd)
[   67.195273] /dev/vmnet: port on hub 8 successfully opened
[   67.398132] /dev/vmnet: open called by PID 5887 (vmnet-natd)
[   67.398165] /dev/vmnet: port on hub 8 successfully opened
[   74.202729] NET: Registered protocol family 10
[   74.203295] lo: Disabled Privacy Extensions
[   74.204286] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   74.206230] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   84.175431] vmnet1: no IPv6 routers present
[   84.283577] vmnet8: no IPv6 routers present
[  102.029568] CPU0 attaching NULL sched-domain.
[  102.029581] CPU1 attaching NULL sched-domain.
[  102.048289] CPU0 attaching sched-domain:
[  102.048300]  domain 0: span 03
[  102.048305]   groups: 01 02
[  102.048312]   domain 1: span 03
[  102.048316]    groups: 03
[  102.048323] CPU1 attaching sched-domain:
[  102.048327]  domain 0: span 03
[  102.048331]   groups: 02 01
[  102.048337]   domain 1: span 03
[  102.048343]    groups: 03
[  106.156006] NET: Registered protocol family 17
[  106.356537] UDF-fs: No VRS found
[  106.381752] ISO 9660 Extensions: Microsoft Joliet Level 3
[  106.461472] ISO 9660 Extensions: RRIP_1991A
[  110.337587] wlan0: Initial auth_alg=0
[  110.337598] wlan0: authenticate with AP 00:1e:58:23:91:af
[  110.341903] wlan0: Initial auth_alg=0
[  110.341911] wlan0: authenticate with AP 00:23:69:22:dc:37
[  110.342751] wlan0: Initial auth_alg=0
[  110.342760] wlan0: authenticate with AP 00:23:69:22:dc:37
[  110.345156] wlan0: RX authentication from 00:23:69:22:dc:37 (alg=0 transaction=2 status=0)
[  110.345169] wlan0: authenticated
[  110.345174] wlan0: associate with AP 00:23:69:22:dc:37
[  110.346672] wlan0: authentication frame received from 00:23:69:22:dc:37, but not in authenticate state - ignored
[  110.348056] wlan0: RX AssocResp from 00:23:69:22:dc:37 (capab=0x411 status=0 aid=2)
[  110.348066] wlan0: associated
[  110.348188] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  110.348196] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  110.348203] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  110.348210] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  110.352264] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  111.534427] padlock: VIA PadLock not detected.
[  111.861880] /dev/vmnet: open called by PID 5855 (vmnet-bridge)
[  111.861894] /dev/vmnet: hub 2 does not exist, allocating memory.
[  111.861907] /dev/vmnet: port on hub 2 successfully opened
[  111.861928] bridge-wlan0: is a Wireless Adapter
[  111.861933] bridge-wlan0: up
[  111.861938] bridge-wlan0: attached
[  115.041468] wlan0: no IPv6 routers present
[ 1690.760578] CPU0 attaching NULL sched-domain.
[ 1690.760585] CPU1 attaching NULL sched-domain.
[ 1690.799779] CPU0 attaching sched-domain:
[ 1690.799793]  domain 0: span 03
[ 1690.799797]   groups: 01 02
[ 1690.799805] CPU1 attaching sched-domain:
[ 1690.799809]  domain 0: span 03
[ 1690.799813]   groups: 02 01

**output of top**
top - 11:10:47 up  1:00,  2 users,  load average: 0.18, 0.16, 0.22
Tasks: 131 total,   2 running, 129 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  0.5%sy,  0.0%ni, 97.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2066016k total,  1136944k used,   929072k free,    23224k buffers
Swap:        0k total,        0k used,        0k free,   708768k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5676 root      20   0  396m  48m 8424 S    1  2.4   2:17.94 Xorg                                                                                            
 5241 messageb  20   0  2904 1376  800 S    1  0.1   0:02.90 dbus-daemon                                                                                     
 6610 assasin   20   0 23044 6804 4880 S    1  0.3   0:00.36 seahorse-agent                                                                                  
 6724 assasin   20   0 21644  14m 5844 S    1  0.7   0:14.24 compiz.real                                                                                     
 9541 assasin   20   0 65760  19m  10m S    1  0.9   0:01.34 gnome-terminal                                                                                  
 9826 assasin   20   0  2308 1132  852 R    1  0.1   0:00.10 top                                                                                             
    1 root      20   0  2844 1688  544 S    0  0.1   0:02.22 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.12 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0                                                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   46 root      15  -5     0    0    0 S    0  0.0   0:00.20 kblockd/0                                                                                       
   47 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/1                                                                                       
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   51 root      15  -5     0    0    0 S    0  0.0   0:00.04 kacpi_notify                                                                                    
  139 root      15  -5     0    0    0 S    0  0.0   0:00.02 kseriod                                                                                         
  181 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  182 root      20   0     0    0    0 S    0  0.0   0:00.24 pdflush                                                                                         
  183 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                         
  224 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
  225 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
 1548 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1555 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
 1566 root      15  -5     0    0    0 S    0  0.0   0:00.14 ata/0                                                                                           
 1567 root      15  -5     0    0    0 S    0  0.0   0:00.02 ata/1                                                                                           
 1573 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
 1597 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                        
 1969 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                                                     
assasin@assassin:~$ 

Please let me know if i need to give information about anything else.

---

### Post by Ramptu on 2009-02-04
I had that same problem with 8.04 and never was really able to resolve the issue but after upgrading to 8.10 Intrepid that problem and a few other glitches I had and since been eliminated. I find 8.10 just to be overall more stable and smoother at least on my system configuration.

Not saying your issue can't be resolved but if your able to upgrade to Intrepid you may find some of those issues go away.

---

### Post by reahjw6 on 2009-02-04
I was ok in 8.04 But in 8.10 my screen froze as well i found for some reason AWN was causing this.
I removed AWN and all is ok.
So i installed AWN again a few weeks later and my system froze again.
After removing Awn completly i have had no problems since.

---

### Post by dnvikram on 2009-02-04
Sounds like you are also having the same issue I am having.What machine are you running 8.10 on?Below is my thread.

[http://ubuntuforums.org/showthread.php?t=1058188](http://ubuntuforums.org/showthread.php?t=1058188)

Even I uninstalled AWN thinking it was the culprint.But,it turns its not.I suffer from these freezes even after uninstalling it.But,this time the freeze coincides with the launching of firefox especially when the visual effects are enabled.No idea,who is the real culprit.I never faced such issue in 8.04..

---

### Post by chetankharche on 2009-02-06
Hi,
I have upgraded my ubuntu 8.04 to ubuntu 8.10 and for last 2 days it seems that the problem of ubuntu freezing has gone. I hope this has solved my problem.

---

