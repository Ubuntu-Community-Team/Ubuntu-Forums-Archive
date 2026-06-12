---
title: "[SOLVED] USB/Card Reader PROBLEM!!!!!!!!"
date: 2008-07-02
forum: Desktop Environments
---

### Post by RMD94 on 2008-07-02
Hello,

When i insert a USB it doesn't recognize it, even when i insert a Memory Stck etc it doesn't recognize it but when i am in Windows Vista it recognizes the USB etc.etc. This problem started when i installed Ubuntu Hardy Heron. I had no problems with Gutsy.

Can someone help me??

---

### Post by pytheas22 on 2008-07-02
Please try inserting your disk and then immediately open a terminal (from Applications>Accessories) and type:
```

dmesg
```

Then please copy and paste the output from that command here.  Hopefully that will pinpoint what's wrong and we can figure out a solution.

Also, please post the output of:
```

cat /etc/fstab
```

---

### Post by RMD94 on 2008-07-03
the results for dmesg:

[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190993 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8370 checksum 0
[    0.000000] ACPI: RSDP 000F8370, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 2FFF3040, 0038 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 2FFF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 2FFF3180, 630C (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 2FFF0000, 0040
[    0.000000] ACPI: SSDT 2FFF95C0, 01C4 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 2FFF9800, 0038 (r1 Nvidia AWRDACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 2FFF9880, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 2FFF9500, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 195057
[    0.000000] Kernel command line: root=UUID=08fca082-3898-44fd-ad8d-83630eef8a09 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2009.000 MHz processor.
[   29.333576] spurious 8259A interrupt: IRQ7.
[   29.336852] Console: colour VGA+ 80x25
[   29.336855] console [tty0] enabled
[   29.337183] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   29.337544] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.349925] Memory: 767364k/786368k available (2177k kernel code, 18424k reserved, 1006k data, 368k init, 0k highmem)
[   29.349932] virtual kernel memory layout:
[   29.349933]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   29.349934]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   29.349936]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   29.349937]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[   29.349938]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   29.349939]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   29.349940]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   29.349943] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.349971] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   29.350101] hpet clockevent registered
[   29.429994] Calibrating delay using timer specific routine.. 4022.03 BogoMIPS (lpj=8044062)
[   29.430012] Security Framework initialized
[   29.430016] SELinux:  Disabled at boot.
[   29.430028] AppArmor: AppArmor initialized
[   29.430031] Failure registering capabilities with primary security module.
[   29.430038] Mount-cache hash table entries: 512
[   29.430127] Initializing cgroup subsys ns
[   29.430130] Initializing cgroup subsys cpuacct
[   29.430138] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   29.430146] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   29.430148] CPU: L2 Cache: 512K (64 bytes/line)
[   29.430150] CPU 0(2) -> Core 0
[   29.430152] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f 00000000
[   29.430160] Compat vDSO mapped to ffffe000.
[   29.430168] Checking 'hlt' instruction... OK.
[   29.446200] SMP alternatives: switching to UP code
[   29.447248] Early unpacking initramfs... done
[   29.744525] ACPI: Core revision 20070126
[   29.744586] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.748692] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   29.748708] SMP alternatives: switching to SMP code
[   29.749208] Booting processor 1/1 eip 3000
[   29.758933] Initializing CPU#1
[   29.837167] Calibrating delay using timer specific routine.. 4018.02 BogoMIPS (lpj=8036040)
[   29.837174] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   29.837181] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   29.837183] CPU: L2 Cache: 512K (64 bytes/line)
[   29.837185] CPU 1(2) -> Core 1
[   29.837187] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f 00000000
[   29.837620] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   29.837636] Total of 2 processors activated (8040.05 BogoMIPS).
[   29.837870] ENABLING IO-APIC IRQs
[   29.838105] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   29.985329] Brought up 2 CPUs
[   29.985377] CPU0 attaching sched-domain:
[   29.985380]  domain 0: span 03
[   29.985382]   groups: 01 02
[   29.985385] CPU1 attaching sched-domain:
[   29.985387]  domain 0: span 03
[   29.985388]   groups: 02 01
[   29.985583] net_namespace: 64 bytes
[   29.985589] Booting paravirtualized kernel on bare hardware
[   29.986021] Time: 18:53:49  Date: 07/03/08
[   29.986047] NET: Registered protocol family 16
[   29.986219] EISA bus registered
[   29.986223] ACPI: bus type pci registered
[   29.991945] PCI: PCI BIOS revision 3.00 entry at 0xfade0, last bus=4
[   29.991948] PCI: Using configuration type 1
[   29.991952] Setting up standard PCI resources
[   29.996950] ACPI: EC: Look up EC in DSDT
[   30.003070] ACPI: Interpreter enabled
[   30.003072] ACPI: (supports S0 S3 S4 S5)
[   30.003085] ACPI: Using IOAPIC for interrupt routing
[   30.012895] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.013535] PCI: Transparent bridge - 0000:00:04.0
[   30.013765] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.014010] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   30.085944] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.086124] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
[   30.086301] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.086478] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[   30.086654] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.086832] ACPI: PCI Interrupt Link [LNK6] (IRQs *5 7 9 10 11 14 15)
[   30.087007] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.087184] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.087361] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 *11 14 15)
[   30.087537] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.087715] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[   30.087891] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.088069] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[   30.088245] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.088423] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   30.088601] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[   30.088778] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   30.088956] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[   30.089141] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[   30.089351] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   30.089554] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   30.089755] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   30.089955] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   30.090155] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   30.090356] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
[   30.090556] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   30.090756] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   30.090957] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[   30.091159] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   30.091360] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   30.091562] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   30.091764] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   30.091966] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   30.092167] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   30.092371] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   30.092573] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   30.092776] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   30.092977] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   30.093113] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.093139] pnp: PnP ACPI init
[   30.093146] ACPI: bus type pnp registered
[   30.098813] pnpacpi: exceeded the max number of mem resources: 12
[   30.098917] pnp: PnP ACPI: found 13 devices
[   30.098919] ACPI: ACPI bus type pnp unregistered
[   30.098922] PnPBIOS: Disabled by ACPI PNP
[   30.099117] PCI: Using ACPI for IRQ routing
[   30.099121] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.168970] NET: Registered protocol family 8
[   30.168972] NET: Registered protocol family 20
[   30.169001] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   30.169005] hpet0: 3 32-bit timers, 25000000 Hz
[   30.170049] AppArmor: AppArmor Filesystem Enabled
[   30.172959] Time: hpet clocksource has been installed.
[   30.172972] Switched to high resolution mode on CPU 0
[   30.172814] Switched to high resolution mode on CPU 1
[   30.180944] system 00:01: ioport range 0x1000-0x107f has been reserved
[   30.180947] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   30.180950] system 00:01: ioport range 0x1400-0x147f has been reserved
[   30.180952] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   30.180955] system 00:01: ioport range 0x1800-0x187f has been reserved
[   30.180957] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   30.180961] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[   30.180963] system 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
[   30.180966] system 00:01: iomem range 0x30000000-0x3fffffff could not be reserved
[   30.180972] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   30.180975] system 00:02: ioport range 0x800-0x87f has been reserved
[   30.180977] system 00:02: ioport range 0x290-0x297 has been reserved
[   30.180985] system 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   30.180990] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[   30.180993] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   30.180996] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   30.180998] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   30.181001] system 00:0c: iomem range 0xfeff0000-0xfeff00ff could not be reserved
[   30.181004] system 00:0c: iomem range 0x2fff0000-0x2fffffff could not be reserved
[   30.181006] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[   30.181009] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   30.181012] system 00:0c: iomem range 0x100000-0x2ffeffff could not be reserved
[   30.181014] system 00:0c: iomem range 0x30000000-0x3fffffff could not be reserved
[   30.181017] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   30.181020] system 00:0c: iomem range 0xfee00000-0xfeefffff could not be reserved
[   30.211363] PCI: Bridge: 0000:00:04.0
[   30.211365]   IO window: b000-bfff
[   30.211369]   MEM window: fdf00000-fdffffff
[   30.211372]   PREFETCH window: fd800000-fd8fffff
[   30.211375] PCI: Bridge: 0000:00:09.0
[   30.211376]   IO window: a000-afff
[   30.211379]   MEM window: fde00000-fdefffff
[   30.211381]   PREFETCH window: fdd00000-fddfffff
[   30.211384] PCI: Bridge: 0000:00:0b.0
[   30.211385]   IO window: 9000-9fff
[   30.211388]   MEM window: fdc00000-fdcfffff
[   30.211390]   PREFETCH window: fdb00000-fdbfffff
[   30.211392] PCI: Bridge: 0000:00:0c.0
[   30.211394]   IO window: 8000-8fff
[   30.211397]   MEM window: fda00000-fdafffff
[   30.211399]   PREFETCH window: fd900000-fd9fffff
[   30.211410] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   30.211418] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   30.211425] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   30.211431] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   30.211443] NET: Registered protocol family 2
[   30.248883] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   30.249150] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   30.249949] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   30.250368] TCP: Hash tables configured (established 131072 bind 65536)
[   30.250371] TCP reno registered
[   30.260938] checking if image is initramfs... it is
[   30.843314] Freeing initrd memory: 7305k freed
[   30.843833] audit: initializing netlink socket (disabled)
[   30.843846] audit(1215111229.388:1): initialized
[   30.845795] VFS: Disk quotas dquot_6.5.1
[   30.845861] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.845973] io scheduler noop registered
[   30.845975] io scheduler anticipatory registered
[   30.845977] io scheduler deadline registered
[   30.845986] io scheduler cfq registered (default)
[   30.846014] pci 0000:00:00.0: Enabling HT MSI Mapping
[   30.860706] pci 0000:00:04.0: Enabling HT MSI Mapping
[   30.860721] pci 0000:00:05.0: Enabling HT MSI Mapping
[   30.860744] pci 0000:00:08.0: Enabling HT MSI Mapping
[   30.860757] pci 0000:00:08.1: Enabling HT MSI Mapping
[   30.860770] pci 0000:00:09.0: Enabling HT MSI Mapping
[   30.860784] pci 0000:00:0b.0: Enabling HT MSI Mapping
[   30.860798] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   30.860811] Boot video device is 0000:00:0d.0
[   30.860911] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   30.860933] assign_interrupt_mode Found MSI capability
[   30.860950] Allocate Port Service[0000:00:09.0:pcie00]
[   30.861011] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   30.861031] assign_interrupt_mode Found MSI capability
[   30.861045] Allocate Port Service[0000:00:0b.0:pcie00]
[   30.861100] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   30.861119] assign_interrupt_mode Found MSI capability
[   30.861133] Allocate Port Service[0000:00:0c.0:pcie00]
[   30.861338] isapnp: Scanning for PnP cards...
[   31.213483] isapnp: No Plug & Play device found
[   31.240162] Real Time Clock Driver v1.12ac
[   31.240384] hpet_resources: 0xfeff0000 is busy
[   31.240407] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.240526] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.240649] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.241140] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.241383] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.241831] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   31.241841] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 16
[   31.242163] 0000:01:06.0: ttyS2 at I/O 0xbc08 (irq = 16) is a 16450
[   31.242352] 0000:01:06.0: ttyS3 at I/O 0xbc10 (irq = 16) is a 8250
[   31.242404] Couldn't register serial port 0000:01:06.0: -28
[   31.243050] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.243365] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   31.243511] PNP: No PS/2 controller found. Probing ports directly.
[   31.243874] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.243879] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.260159] mice: PS/2 mouse device common for all mice
[   31.260282] EISA: Probing bus 0 at eisa.0
[   31.260287] Cannot allocate resource for EISA slot 1
[   31.260304] Cannot allocate resource for EISA slot 8
[   31.260306] EISA: Detected 0 cards.
[   31.260308] cpuidle: using governor ladder
[   31.260310] cpuidle: using governor menu
[   31.260390] NET: Registered protocol family 1
[   31.260414] Using IPI No-Shortcut mode
[   31.260447] registered taskstats version 1
[   31.260553]   Magic number: 0:479:897
[   31.260630]   hash matches device ptyy7
[   31.260641]   hash matches device ptyva
[   31.260715] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   31.260717] EDD information not available.
[   31.260955] Freeing unused kernel memory: 368k freed
[   32.473922] fuse init (API version 7.9)
[   32.488907] ACPI: Fan [FAN] (on)
[   32.495540] ACPI: Thermal Zone [THRM] (40 C)
[   32.981813] usbcore: registered new interface driver usbfs
[   32.981837] usbcore: registered new interface driver hub
[   32.981862] usbcore: registered new device driver usb
[   32.992560] SCSI subsystem initialized
[   32.993546] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   32.993978] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   32.993990] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 17
[   32.994006] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   32.994009] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   32.994361] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   32.994379] ohci_hcd 0000:00:02.0: irq 17, io mem 0xfe02f000
[   33.017302] libata version 3.00 loaded.
[   33.051617] usb usb1: configuration #1 chosen from 1 choice
[   33.051641] hub 1-0:1.0: USB hub found
[   33.051649] hub 1-0:1.0: 10 ports detected
[   33.153742] pata_amd 0000:00:06.0: version 0.3.10
[   33.153804] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   33.154634] scsi0 : pata_amd
[   33.155246] scsi1 : pata_amd
[   33.155804] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   33.155807] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   33.456926] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   33.488421] ata1.00: ATAPI: LITE-ON DVDRW SHW-160P6S, PRS2, max UDMA/66
[   33.488434] ata1.00: limited to UDMA/33 due to 40-wire cable
[   33.668737] usb 1-2: configuration #1 chosen from 1 choice
[   33.676064] ata1.00: configured for UDMA/33
[   33.676096] ata2: port disabled. ignoring.
[   33.676698] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-160P6S PRS2 PQ: 0 ANSI: 5
[   33.677554] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   33.677564] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 18
[   33.677577] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   33.677579] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   33.677612] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   33.677641] ehci_hcd 0000:00:02.1: debug port 1
[   33.677645] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   33.677656] ehci_hcd 0000:00:02.1: irq 18, io mem 0xfe02e000
[   33.687835] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.687926] usb usb2: configuration #1 chosen from 1 choice
[   33.687947] hub 2-0:1.0: USB hub found
[   33.687952] hub 2-0:1.0: 10 ports detected
[   33.793651] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   33.793662] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   33.793669] PCI: Setting latency timer of device 0000:01:09.0 to 64
[   33.843393] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fdffe000-fdffe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   33.846958] sata_nv 0000:00:08.0: version 3.5
[   33.847332] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   33.847342] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 20
[   33.847387] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   33.848238] scsi2 : sata_nv
[   33.848294] scsi3 : sata_nv
[   33.848472] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 20
[   33.848475] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 20
[   33.972169] usb 1-2: USB disconnect, address 2
[   33.972451] usbcore: registered new interface driver hiddev
[   34.314667] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   34.322888] ata3.00: ATA-7: HDT722525DLA380, V44OA96A, max UDMA/133
[   34.322891] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   34.338864] ata3.00: configured for UDMA/133
[   34.522347] usb 2-9: new high speed USB device using ehci_hcd and address 3
[   34.650161] ata4: SATA link down (SStatus 0 SControl 300)
[   34.660458] scsi 2:0:0:0: Direct-Access     ATA      HDT722525DLA380  V44O PQ: 0 ANSI: 5
[   34.660883] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   34.660892] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 21
[   34.660935] PCI: Setting latency timer of device 0000:00:08.1 to 64
[   34.661192] scsi4 : sata_nv
[   34.661253] scsi5 : sata_nv
[   34.661397] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc800 irq 21
[   34.661400] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc808 irq 21
[   34.746453] usb 2-9: configuration #1 chosen from 1 choice
[   34.930064] usbcore: registered new interface driver usbhid
[   34.930071] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   34.929822] usbcore: registered new interface driver libusual
[   34.935493] Initializing USB Mass Storage driver...
[   34.970686] ata5: SATA link down (SStatus 0 SControl 300)
[   35.113615] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff5e6da4]
[   35.234300] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   35.290218] ata6: SATA link down (SStatus 0 SControl 300)
[   35.311864] Driver 'sd' needs updating - please use bus_type methods
[   35.313159] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   35.313171] sd 2:0:0:0: [sda] Write Protect is off
[   35.313174] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.313189] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.313242] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   35.313251] sd 2:0:0:0: [sda] Write Protect is off
[   35.313253] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.313266] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.313270]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   35.315868] sr0: scsi3-mmc drive: 125x/125x writer cd/rw xa/form2 cdda tray
[   35.315871] Uniform CD-ROM driver Revision: 3.20
[   35.315904] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   35.329803]  sda1 sda2 sda3 sda4 < sda5 >
[   35.350209] sd 2:0:0:0: [sda] Attached SCSI disk
[   35.353986] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   35.354006] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   35.447249] usb 1-2: configuration #1 chosen from 1 choice
[   35.457323] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input1
[   35.478006] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-2
[   35.486103] Fixing up Logitech keyboard report descriptor
[   35.486603] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.1/input/input2
[   35.538000] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-2
[   35.628621] kjournald starting.  Commit interval 5 seconds
[   35.628638] EXT3-fs: mounted filesystem with ordered data mode.
[   35.840427] usb 1-10: new low speed USB device using ohci_hcd and address 4
[   36.055399] usb 1-10: configuration #1 chosen from 1 choice
[   36.074396] input: Acer IR  Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-10/1-10:1.0/input/input3
[   36.085106] input,hiddev97,hidraw2: USB HID v1.10 Keyboard [Acer IR  Receiver] on usb-0000:00:02.0-10
[   36.085235] scsi6 : SCSI emulation for USB Mass Storage devices
[   36.085291] usbcore: registered new interface driver usb-storage
[   36.085294] USB Mass Storage support registered.
[   36.085422] usb-storage: device found at 3
[   36.085424] usb-storage: waiting for device to settle before scanning
[   41.077925] usb-storage: device scan complete
[   41.109506] scsi 6:0:0:0: Direct-Access     Generic  2.0 Reader-CF    1.00 PQ: 0 ANSI: 0 CCS
[   41.140456] scsi 6:0:0:1: Direct-Access     Generic  2.0 Reader-SM/xD 1.00 PQ: 0 ANSI: 0 CCS
[   41.171295] scsi 6:0:0:2: Direct-Access     Generic  2.0 Reader-SD    1.00 PQ: 0 ANSI: 0 CCS
[   41.202246] scsi 6:0:0:3: Direct-Access     Generic  2.0 Reader-MS    1.00 PQ: 0 ANSI: 0 CCS
[   41.206143] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   41.206173] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   41.210111] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[   41.210137] sd 6:0:0:1: Attached scsi generic sg3 type 0
[   41.214102] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[   41.214131] sd 6:0:0:2: Attached scsi generic sg4 type 0
[   41.218093] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   41.218119] sd 6:0:0:3: Attached scsi generic sg5 type 0
[   42.236228] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.312155] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.432076] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   42.432102] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
[   42.506555] input: Power Button (FF) as /devices/virtual/input/input4
[   42.531679] ACPI: Power Button (FF) [PWRF]
[   42.531769] input: Power Button (CM) as /devices/virtual/input/input5
[   42.555620] ACPI: Power Button (CM) [PWRB]
[   42.838305] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   42.883262] Linux agpgart interface v0.102
[   42.975526] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   42.975538] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 22
[   42.975549] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   42.975577] sky2 0000:03:00.0: v1.20 addr 0xfdcfc000 irq 22 Yukon-EC Ultra (0xb4) rev 2
[   42.975894] sky2 eth0: addr 00:16:ec:c3:a7:39
[   43.280369] nvidia: module license 'NVIDIA' taints kernel.
[   44.071918] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 23
[   44.071924] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [AIGP] -> GSI 23 (level, low) -> IRQ 17
[   44.071932] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   44.072179] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   44.220993] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   44.220999] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 18
[   44.221021] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   44.251919] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   44.592941] parport_pc 00:0a: reported by Plug and Play ACPI
[   44.592988] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   44.607689] ACPI: WMI-Acer: Mapper loaded
[   44.613477] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   44.613489] acer_acpi: No or unsupported WMI interface, unable to load.
[   45.775472] lp0: using parport0 (interrupt-driven).
[   46.385361] EXT3 FS on sda3, internal journal
[   47.424125] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.794867] No dock devices found.
[   48.071157] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[   48.071449] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xc
[   48.071454] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xe
[   48.071456] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   48.750356] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   48.750363] apm: disabled - APM is not SMP safe.
[   48.852240] ppdev: user-space parallel port driver
[   48.956117] audit(1215125648.259:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5234 profile="/usr/sbin/cupsd" namespace="default"
[   51.052069] Clocksource tsc unstable (delta = -250007305 ns)
[   51.697023] sky2 eth0: enabling interface
[   51.739324] Bluetooth: Core ver 2.11
[   51.739608] NET: Registered protocol family 31
[   51.739611] Bluetooth: HCI device and connection manager initialized
[   51.739615] Bluetooth: HCI socket layer initialized
[   51.783558] Bluetooth: L2CAP ver 2.9
[   51.783563] Bluetooth: L2CAP socket layer initialized
[   51.792373] Bluetooth: RFCOMM socket layer initialized
[   51.792385] Bluetooth: RFCOMM TTY layer initialized
[   51.792387] Bluetooth: RFCOMM ver 1.8
[   52.693394] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   53.775599] NET: Registered protocol family 17
[   55.451112] NET: Registered protocol family 10
[   55.451462] lo: Disabled Privacy Extensions
[   60.598235] eth0: no IPv6 routers present
[   67.772492] UDF-fs: No VRS found
[   67.803696] ISO 9660 Extensions: Microsoft Joliet Level 3
[   67.839564] ISO 9660 Extensions: RRIP_1991A
[  269.089579] usb 2-8: new high speed USB device using ehci_hcd and address 5
[  269.147990] usb 2-8: device descriptor read/64, error -71
[  269.257333] usb 2-8: device descriptor read/64, error -71
[  269.365177] usb 2-8: new high speed USB device using ehci_hcd and address 6
[  269.423566] usb 2-8: device descriptor read/64, error -71
[  269.532935] usb 2-8: device descriptor read/64, error -71
[  269.640778] usb 2-8: new high speed USB device using ehci_hcd and address 7
[  269.844483] usb 2-8: device not accepting address 7, error -71
[  269.900402] usb 2-8: new high speed USB device using ehci_hcd and address 8
[  270.104105] usb 2-8: device not accepting address 8, error -71
[  309.644447] usb 2-8: new high speed USB device using ehci_hcd and address 9
[  309.702860] usb 2-8: device descriptor read/64, error -71
[  309.812205] usb 2-8: device descriptor read/64, error -71
[  309.920545] usb 2-8: new high speed USB device using ehci_hcd and address 10
[  309.977963] usb 2-8: device descriptor read/64, error -71


the results for cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=08fca082-3898-44fd-ad8d-83630eef8a09 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I am sorry for the late reply...

---

### Post by pytheas22 on 2008-07-03
Try this:
```

sudo rmmod usbcore
sudo modprobe usbcore autosuspend=-1
```

Now see if you can plug in USB devices properly, and please report back.

---

### Post by RMD94 on 2008-07-03
after typing in "sudo rmmod usbcore" i get an error:

ERROR: Module usbcore is in use by usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd

---

### Post by pytheas22 on 2008-07-03
Sorry, I didn't realize it had dependencies.  First, unplug all USB devices from your computer.  Then do this:
```

sudo -s
rmmod usb_storage
rmmod libusual
rmmod usbhid
rmmod ehci_hcd
rmmod ohci_hcd
rmmod usbcore
modprobe usbcore autosuspend=-1
modprobe ohci_hcd
modprobe ehci_hcd
modprobe usbhid
modprobe libusual
modprobe usb_storage
```

Then plug your USB device back in and please report back.

---

### Post by RMD94 on 2008-07-03
I have to go step bu step right??? but if i remove all USB connection how am i gonna copy paste the commands?????

---

### Post by pytheas22 on 2008-07-03
> I have to go step bu step right??? but if i remove all USB connection how am i gonna copy paste the commands????? 

I didn't know that your wireless card was also USB, but that's ok.  Please just run each of those commands (one line at a time) and see if you can mount a USB drive after that.  If not, reboot your computer and the wireless card should work again.  The commands shouldn't produce output at all.  If any of them does, please try just to remember which one it was and let me know.  I don't need to know the exact output.

The reason I'm asking you to do this is that I think that running those commands is going to solve the problem.  If it does, then we know exactly what the problem is and can apply a more permanent, automatic solution, which won't require running those commands.

---

### Post by RMD94 on 2008-07-03
actually i had rebboted my computer cuz after putting this command "rmmod ohci_hcd
" my mouse and my keyboard stopped working and now when i am tring to insert those commands again i get an error on the first command "rmmod usb_storage
" 

ERROR: Module usb_storage is in use

---

### Post by pytheas22 on 2008-07-03
Sorry, I didn't realize that your keyboard and mouse also are USB.  I'm just going to tell you the permanent solution, as it seems too difficult to test it first, and hopefully it will work.

1. first, backup your grub menu with:

cp /boot/grub/menu.lst ~/menu.backup

1. type:
```

sudo gedit /boot/grub/menu.lst
```

A file will open.  Scroll down towards the bottom and you will see, directly below the line "## ## End Default Options ##," an entry that looks like:
```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Change that entry so that it looks like:
```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash **usbcore.autosuspend=-1**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Then save the file and reboot.  Does the USB work properly now?

---

### Post by RMD94 on 2008-07-03
It has become worst!!!! now i can't boot into Ubuntu. I get an error..... while booting in Ubuntu....

---

### Post by pytheas22 on 2008-07-04
Sorry it made it worse.  To fix the booting problem you can do a few things.  First, you might have multiple entries at the boot menu.  If so, only the top one should cause problems.  Try booting into the other one.  After it boots, run:
```

sudo cp ~/menu.backup /boot/grub/menu.lst
```

That should fix the booting problem.  Please let me know, and then we can get back to solving the USB issue.  I'm sorry for the problems.

---

### Post by pac-man on 2008-07-04
I had the same problem with my external USB card reader, and also with an external hard drive. I "kind of" solved the problem by only doing this:

sudo modprobe ehci_hcd

and that's it. I said "kind of" because now it refuses to use ehci and uses ohci instead, thus, it uses the USB 1.1 speed instead of USB 2.0. It works fine on windows. It's really a pain in the *** because I rely a lot on my external HDD and the transfer rate is waaaay too slow. 

This was working properly on 7.10, I updated the distro to 8.04 and it was still working fine. The problem started when I did a clean installation of 8.04

I think this is the buggiest BUGbuntu release ever! Whenever I use it feels like if I were using a beta: besides that, I have problems shutting it down (takes ages to do it), and I have to reconfigure the xserver settings at least twice a week because the xorg.conf file for some unknown reason changes the resolution itself. Plus, shipping a "stable" release with a beta version of firefox, WTF!

Those canonical guys are making big efforts to force loyal users switch to some other distro... and I think they're getting there.

---

### Post by pytheas22 on 2008-08-12
RMD94: are you still unable to boot into Ubuntu?  Let me know and we'll go from there.

If you can boot into Ubuntu, try running:
```

sudo modprobe -r ehci_hcd
```

and see if it helps.

If you can't boot the system and want to fix it quickly, just reinstall.  Otherwise we can make it boot again, but it may take longer than it would to do a reinstallation.

---

### Post by RMD94 on 2008-08-12
I can boot in Ubuntu..

---

### Post by RMD94 on 2008-08-13
thank u very very much..... 
it worked!!

thx

---

