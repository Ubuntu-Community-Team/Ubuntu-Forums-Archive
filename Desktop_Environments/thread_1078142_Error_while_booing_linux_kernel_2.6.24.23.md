---
title: "Error while booing linux kernel 2.6.24.23"
date: 2009-02-23
forum: Desktop Environments
---

### Post by ambdeep on 2009-02-23
When I boot linux kernel 2.6.24.23 the ubuntu sign load for a while and then I get a black screen with loads of stuff on it..... bout I also get one error saying that there is no suitable modulator for kernel....it doesn't affect my software...I can still do every thing but it takes a lot longer to boot.
I do not experience this when I boot using kernel version 2.6.24.19.
Please help....thanks in advance

---

### Post by yoyoned on 2009-02-23
A bit more information would be helpful.  After booting kernel 2.6.24.23, open a terminal and type dmesg.  Post the output

---

### Post by ambdeep on 2009-02-23
> **yoyoned said:**
> A bit more information would be helpful.  After booting kernel 2.6.24.23, open a terminal and type dmesg.  Post the output
Heres the output.........
```
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114608
[    0.000000] On node 0 totalpages: 114608
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 863 pages used for memmap
[    0.000000]   Normal zone: 109649 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB1A0 checksum 0
[    0.000000] ACPI: RSDP 000FB1A0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1BFB0000, 0034 (r1 A M I  OEMRSDT  11000511 MSFT       97)
[    0.000000] ACPI: FACP 1BFB0200, 0084 (r2 A M I  OEMFACP  11000511 MSFT       97)
[    0.000000] ACPI: DSDT 1BFB0440, 5448 (r1  A0313 A0313001        1 INTL  2002026)
[    0.000000] ACPI: FACS 1BFBE000, 0040
[    0.000000] ACPI: APIC 1BFB0390, 006C (r1 A M I  OEMAPIC  11000511 MSFT       97)
[    0.000000] ACPI: MCFG 1BFB0400, 003C (r1 A M I  OEMMCFG  11000511 MSFT       97)
[    0.000000] ACPI: OEMB 1BFBE040, 004B (r1 A M I  AMI_OEM  11000511 MSFT       97)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3780000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113713
[    0.000000] Kernel command line: root=UUID=d3919821-0ea8-47cc-a3db-4a90f9039f70 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2999.292 MHz processor.
[   21.329590] Console: colour VGA+ 80x25
[   21.329595] console [tty0] enabled
[   21.329999] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.330327] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.340092] Memory: 442360k/458432k available (2179k kernel code, 15500k reserved, 1008k data, 368k init, 0k highmem)
[   21.340099] virtual kernel memory layout:
[   21.340100]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   21.340101]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.340102]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   21.340103]     lowmem  : 0xc0000000 - 0xdbfb0000   ( 447 MB)
[   21.340104]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   21.340105]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   21.340106]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[   21.340109] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.340150] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   21.420080] Calibrating delay using timer specific routine.. 6005.55 BogoMIPS (lpj=12011101)
[   21.420107] Security Framework initialized
[   21.420113] SELinux:  Disabled at boot.
[   21.420128] AppArmor: AppArmor initialized
[   21.420132] Failure registering capabilities with primary security module.
[   21.420141] Mount-cache hash table entries: 512
[   21.420268] Initializing cgroup subsys ns
[   21.420273] Initializing cgroup subsys cpuacct
[   21.420286] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000 00000000
[   21.420295] monitor/mwait feature present.
[   21.420297] using mwait in idle threads.
[   21.420303] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   21.420306] CPU: L2 cache: 2048K
[   21.420308] CPU: Physical Processor ID: 0
[   21.420311] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043180 0000649d 00000000 00000000 00000000
[   21.420322] Compat vDSO mapped to ffffe000.
[   21.420338] Checking 'hlt' instruction... OK.
[   21.436533] SMP alternatives: switching to UP code
[   21.438471] Early unpacking initramfs... done
[   21.741939] ACPI: Core revision 20070126
[   21.742016] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.745089] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   21.745112] SMP alternatives: switching to SMP code
[   21.746002] Booting processor 1/1 eip 3000
[   21.756652] Initializing CPU#1
[   21.835577] Calibrating delay using timer specific routine.. 5998.82 BogoMIPS (lpj=11997652)
[   21.835589] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000 00000000
[   21.835597] monitor/mwait feature present.
[   21.835605] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   21.835607] CPU: L2 cache: 2048K
[   21.835610] CPU: Physical Processor ID: 0
[   21.835613] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043180 0000649d 00000000 00000000 00000000
[   21.836159] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   21.836206] Total of 2 processors activated (12004.37 BogoMIPS).
[   21.836769] ENABLING IO-APIC IRQs
[   21.837037] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.983565] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   22.003558] Brought up 2 CPUs
[   22.003586] CPU0 attaching sched-domain:
[   22.003589]  domain 0: span 03
[   22.003591]   groups: 01 02
[   22.003595]   domain 1: span 03
[   22.003597]    groups: 03
[   22.003600] CPU1 attaching sched-domain:
[   22.003602]  domain 0: span 03
[   22.003603]   groups: 02 01
[   22.003606]   domain 1: span 03
[   22.003608]    groups: 03
[   22.003899] net_namespace: 64 bytes
[   22.003911] Booting paravirtualized kernel on bare hardware
[   22.004615] Time:  9:08:21  Date: 02/24/09
[   22.004643] NET: Registered protocol family 16
[   22.004921] EISA bus registered
[   22.004928] ACPI: bus type pci registered
[   22.005174] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[   22.005177] PCI: Using configuration type 1
[   22.005195] Setting up standard PCI resources
[   22.027408] ACPI: EC: Look up EC in DSDT
[   22.033474] ACPI: Interpreter enabled
[   22.033478] ACPI: (supports S0 S1 S3 S4 S5)
[   22.033496] ACPI: Using IOAPIC for interrupt routing
[   22.043135] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.043917] PCI quirk: region 4000-403f claimed by ali7101 ACPI
[   22.044440] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.044556] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   22.044653] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE2P._PRT]
[   22.047266] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15), disabled.
[   22.047444] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   22.047620] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   22.047788] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   22.047961] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   22.048130] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   22.048300] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   22.048464] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15), disabled.
[   22.048635] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   22.048787] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  8A, should be 7D [20070126]
[   22.048794] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.048841] pnp: PnP ACPI init
[   22.048852] ACPI: bus type pnp registered
[   22.055191] pnp: PnP ACPI: found 13 devices
[   22.055194] ACPI: ACPI bus type pnp unregistered
[   22.055198] PnPBIOS: Disabled by ACPI PNP
[   22.055516] PCI: Using ACPI for IRQ routing
[   22.055520] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.055527] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   22.079332] NET: Registered protocol family 8
[   22.079335] NET: Registered protocol family 20
[   22.079428] AppArmor: AppArmor Filesystem Enabled
[   22.083318] Time: tsc clocksource has been installed.
[   22.095379] system 00:07: ioport range 0x28d-0x28e has been reserved
[   22.095382] system 00:07: ioport range 0x480-0x48f has been reserved
[   22.095385] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   22.095388] system 00:07: ioport range 0x4000-0x40bf could not be reserved
[   22.095391] system 00:07: ioport range 0x40c0-0x40df has been reserved
[   22.095394] system 00:07: ioport range 0x900-0x91f has been reserved
[   22.095397] system 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
[   22.095400] system 00:07: iomem range 0xffb00000-0xffbfffff could not be reserved
[   22.095403] system 00:07: iomem range 0xc0000000-0xc0000fff has been reserved
[   22.095406] system 00:07: iomem range 0xff6fe000-0xff6fefff has been reserved
[   22.095409] system 00:07: iomem range 0xff6ff000-0xff6fffff has been reserved
[   22.095412] system 00:07: iomem range 0xff780000-0xff7fffff could not be reserved
[   22.095419] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[   22.095422] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[   22.095429] system 00:0a: ioport range 0xc00-0xc0f has been reserved
[   22.095432] system 00:0a: ioport range 0xd00-0xd0f has been reserved
[   22.095434] system 00:0a: ioport range 0xa20-0xa2f has been reserved
[   22.095437] system 00:0a: ioport range 0xa30-0xa3f has been reserved
[   22.095448] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[   22.095454] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   22.095457] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   22.095460] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   22.095463] system 00:0c: iomem range 0x100000-0x1bffffff could not be reserved
[   22.095466] system 00:0c: iomem range 0xfff80000-0xffffffff could not be reserved
[   22.125997] PCI: Bridge: 0000:00:01.0
[   22.126000]   IO window: a000-cfff
[   22.126005]   MEM window: bfd00000-dfdfffff
[   22.126008]   PREFETCH window: 9fc00000-bfbfffff
[   22.126012] PCI: Bridge: 0000:00:19.0
[   22.126016]   IO window: d000-dfff
[   22.126021]   MEM window: dfe00000-dfefffff
[   22.126026]   PREFETCH window: disabled.
[   22.126052] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   22.126066] NET: Registered protocol family 2
[   22.163357] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   22.163628] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   22.163708] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   22.163789] TCP: Hash tables configured (established 16384 bind 16384)
[   22.163792] TCP reno registered
[   22.175419] checking if image is initramfs... it is
[   22.622892] Switched to high resolution mode on CPU 1
[   22.626721] Switched to high resolution mode on CPU 0
[   22.780083] Freeing initrd memory: 7324k freed
[   22.781215] audit: initializing netlink socket (disabled)
[   22.781243] audit(1235466501.320:1): initialized
[   22.784066] VFS: Disk quotas dquot_6.5.1
[   22.784170] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.784345] io scheduler noop registered
[   22.784348] io scheduler anticipatory registered
[   22.784350] io scheduler deadline registered
[   22.784363] io scheduler cfq registered (default)
[   22.784374] PCI: MSI quirk detected. MSI deactivated.
[   23.273841] Boot video device is 0000:01:05.0
[   23.274234] isapnp: Scanning for PnP cards...
[   23.625501] isapnp: No Plug & Play device found
[   23.664062] Real Time Clock Driver v1.12ac
[   23.664204] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.664374] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.665240] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.666283] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.666378] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.666574] PNP: No PS/2 controller found. Probing ports directly.
[   23.668698] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.668705] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.677505] mice: PS/2 mouse device common for all mice
[   23.677662] EISA: Probing bus 0 at eisa.0
[   23.677688] Cannot allocate resource for EISA slot 4
[   23.677711] EISA: Detected 0 cards.
[   23.677715] cpuidle: using governor ladder
[   23.677718] cpuidle: using governor menu
[   23.677824] NET: Registered protocol family 1
[   23.677856] Using IPI No-Shortcut mode
[   23.677893] registered taskstats version 1
[   23.678001]   Magic number: 13:794:121
[   23.678070] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.678072] EDD information not available.
[   23.678520] Freeing unused kernel memory: 368k freed
[   23.678547] Write protecting the kernel read-only data: 806k
[   24.893959] fuse init (API version 7.9)
[   24.915402] ACPI: SSDT 1BFB5890, 02FC (r1    AMI   CPU1PM        1 INTL  2002026)
[   24.915653] ACPI: Processor [CPU1] (supports 8 throttling states)
[   24.915740] ACPI: SSDT 1BFB5B90, 02FC (r1    AMI   CPU2PM        1 INTL  2002026)
[   24.915963] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.915978] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.096958] usbcore: registered new interface driver usbfs
[   25.097001] usbcore: registered new interface driver hub
[   25.097689] usbcore: registered new device driver usb
[   25.099630] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.099684] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   25.099702] ohci_hcd 0000:00:1c.0: OHCI Host Controller
[   25.100111] ohci_hcd 0000:00:1c.0: new USB bus registered, assigned bus number 1
[   25.100138] ohci_hcd 0000:00:1c.0: irq 16, io mem 0xdfffc000
[   25.158618] usb usb1: configuration #1 chosen from 1 choice
[   25.158660] hub 1-0:1.0: USB hub found
[   25.158674] hub 1-0:1.0: 3 ports detected
[   25.260476] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 18 (level, low) -> IRQ 17
[   25.260501] ohci_hcd 0000:00:1c.1: OHCI Host Controller
[   25.260540] ohci_hcd 0000:00:1c.1: new USB bus registered, assigned bus number 2
[   25.260571] ohci_hcd 0000:00:1c.1: irq 17, io mem 0xdfffd000
[   25.318433] usb usb2: configuration #1 chosen from 1 choice
[   25.318477] hub 2-0:1.0: USB hub found
[   25.318490] hub 2-0:1.0: 3 ports detected
[   25.400164] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.400175] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.420239] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 19 (level, low) -> IRQ 18
[   25.420258] ohci_hcd 0000:00:1c.2: OHCI Host Controller
[   25.420294] ohci_hcd 0000:00:1c.2: new USB bus registered, assigned bus number 3
[   25.420324] ohci_hcd 0000:00:1c.2: irq 18, io mem 0xdfffe000
[   25.464681] SCSI subsystem initialized
[   25.478251] usb usb3: configuration #1 chosen from 1 choice
[   25.478313] hub 3-0:1.0: USB hub found
[   25.478330] hub 3-0:1.0: 3 ports detected
[   25.495508] Floppy drive(s): fd0 is 1.44M
[   25.497239] libata version 3.00 loaded.
[   25.515796] FDC 0 is a post-1991 82077
[   25.563913] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   25.580294] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 19
[   25.580317] ehci_hcd 0000:00:1c.3: EHCI Host Controller
[   25.580360] ehci_hcd 0000:00:1c.3: new USB bus registered, assigned bus number 4
[   25.580408] ehci_hcd 0000:00:1c.3: debug port 1
[   25.580418] PCI: cache line size of 128 is not supported by device 0000:00:1c.3
[   25.580435] ehci_hcd 0000:00:1c.3: irq 19, io mem 0xdffff800
[   25.751757] ehci_hcd 0000:00:1c.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.751963] usb usb4: configuration #1 chosen from 1 choice
[   25.752016] hub 4-0:1.0: USB hub found
[   25.752027] hub 4-0:1.0: 8 ports detected
[   25.855738] sata_uli 0000:00:1f.1: version 1.3
[   25.855790] PCI: Enabling device 0000:00:1f.1 (0105 -> 0107)
[   25.855812] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 21 (level, low) -> IRQ 20
[   25.856058] scsi0 : sata_uli
[   25.856148] scsi1 : sata_uli
[   25.856215] scsi2 : sata_uli
[   25.856285] scsi3 : sata_uli
[   25.856338] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe480 bmdma 0xe000 irq 20
[   25.856345] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xe008 irq 20
[   25.856351] ata3: SATA max UDMA/133 cmd 0xec08 ctl 0xe486 bmdma 0xe010 cmd 0xe409 ctl 0xe086 bmdma 0xe018 irq 20
[   25.856357] ata4: SATA max UDMA/133 irq 20
[   26.146158] usb 1-2: device not accepting address 2, error -62
[   26.322963] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   26.368653] ata1.00: ATA-7: ST3160212AS, 3.AAE, max UDMA/133
[   26.368658] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   26.435215] ata1.00: configured for UDMA/133
[   26.745408] ata2: SATA link down (SStatus 0 SControl 300)
[   27.057027] ata3: SATA link down (SStatus 0 SControl 300)
[   27.241766] usb 1-2: new full speed USB device using ohci_hcd and address 4
[   27.368617] ata4: SATA link down (SStatus 0 SControl 300)
[   27.368819] scsi 0:0:0:0: Direct-Access     ATA      ST3160212AS      3.AA PQ: 0 ANSI: 5
[   27.369365] ALI15X3: IDE controller (0x10b9:0x5229 rev 0xc7) at  PCI slot 0000:00:1f.0
[   27.369410] ACPI: PCI Interrupt 0000:00:1f.0[A] -> GSI 21 (level, low) -> IRQ 20
[   27.369427] ALI15X3: not 100% native mode: will probe irqs later
[   27.369455]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[   27.369478]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:pio, hdd:pio
[   27.369493] Probing IDE interface ide0...
[   27.378927] Driver 'sd' needs updating - please use bus_type methods
[   27.379017] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   27.379034] sd 0:0:0:0: [sda] Write Protect is off
[   27.379037] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.379062] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.379125] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   27.379139] sd 0:0:0:0: [sda] Write Protect is off
[   27.379142] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.379166] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.379170]  sda: sda1 sda2 sda3 sda4
[   27.416947] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.422036] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.453695] usb 1-2: configuration #1 chosen from 1 choice
[   27.757119] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   27.825343] hdb: SONY DVD RW DW-Q120A, ATAPI CD/DVD-ROM drive
[   27.968040] usb 3-2: configuration #1 chosen from 1 choice
[   27.993452] usbcore: registered new interface driver hiddev
[   27.998129] input: HID Keyboard HID Mouse as /devices/pci0000:00/0000:00:1c.2/usb3/3-2/3-2:1.0/input/input1
[   28.019828] input,hidraw0: USB HID v1.10 Keyboard [HID Keyboard HID Mouse] on usb-0000:00:1c.2-2
[   28.026103] input: HID Keyboard HID Mouse as /devices/pci0000:00/0000:00:1c.2/usb3/3-2/3-2:1.1/input/input2
[   28.059772] input,hidraw1: USB HID v1.10 Mouse [HID Keyboard HID Mouse] on usb-0000:00:1c.2-2
[   28.059794] usbcore: registered new interface driver usbhid
[   28.059800] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.159920] hda: ST3160212A, ATA DISK drive
[   28.159938] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[   28.160088] hda: UDMA/100 mode selected
[   28.160303] hdb: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[   28.160572] hdb: UDMA/66 mode selected
[   28.160895] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   28.175057] Probing IDE interface ide1...
[   28.759874] hda: max request size: 512KiB
[   28.811121] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63
[   28.835506] hda: cache flushes supported
[   28.835553]  hda: hda1
[   28.861038] hdb: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   28.861049] Uniform CD-ROM driver Revision: 3.20
[   29.187861] Attempting manual resume
[   29.187866] swsusp: Resume From Partition 8:4
[   29.187868] PM: Checking swsusp image.
[   29.188055] PM: Resume from disk failed.
[   29.235764] kjournald starting.  Commit interval 5 seconds
[   29.235774] EXT3-fs: mounted filesystem with ordered data mode.
[   36.206606] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
[   36.206745] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 21
[   36.266468] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.281796] eth0: ULi M5263 at pci0000:00:1b.0, 00:15:f2:da:de:24, irq 21.
[   36.311289] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.376312] Linux agpgart interface v0.102
[   36.696117] ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
[   36.696124] ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not inserted.
[   36.843795] ali15x3_smbus 0000:00:1e.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   36.843808] ali15x3_smbus 0000:00:1e.1: ALI15X3 not detected, module not inserted.
[   36.988616] input: Power Button (FF) as /devices/virtual/input/input3
[   37.008368] ACPI: Power Button (FF) [PWRF]
[   37.008520] input: Power Button (CM) as /devices/virtual/input/input4
[   37.040323] ACPI: Power Button (CM) [PWRB]
[   37.601194] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   37.769072] [fglrx] Maximum main memory to use for locked dma buffers: 372 MBytes.
[   37.769132] [fglrx] ASYNCIO init succeed!
[   37.770511] [fglrx] PAT is enabled successfully!
[   37.772617] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   38.108286] ACPI: PCI Interrupt 0000:00:1d.0[C] -> GSI 22 (level, low) -> IRQ 22
[   38.210963] Linux video capture interface: v2.00
[   38.239414] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   38.339759] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. SONIX JPEG (sn9c1xx) 
[   38.341879] usbcore: registered new interface driver gspca
[   38.341887] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[   38.422629] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
[   38.422688] usbcore: registered new interface driver sn9c102
[   38.522888] parport_pc 00:06: reported by Plug and Play ACPI
[   38.522966] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   39.491672] NET: Registered protocol family 17
[   39.838156] NET: Registered protocol family 10
[   39.838614] lo: Disabled Privacy Extensions
[   39.839371] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   40.528179] lp0: using parport0 (interrupt-driven).
[   40.581278] Adding 2096472k swap on /dev/sda4.  Priority:-1 extents:1 across:2096472k
[   41.139880] EXT3 FS on sda3, internal journal
[   42.285534] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.410815] uli526x: eth0 NIC Link is Up 100 Mbps Full duplex
[   42.411144] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   42.564564] PPP generic driver version 2.4.2
[   42.609388] NET: Registered protocol family 24
[   43.058466] No dock devices found.
[   44.160016] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   44.160026] apm: disabled - APM is not SMP safe.
[   44.378955] ppdev: user-space parallel port driver
[   44.586191] audit(1235446724.145:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5164 profile="/usr/sbin/cupsd" namespace="default"
[   52.656473] eth0: no IPv6 routers present
[   53.871503] Bluetooth: Core ver 2.11
[   53.872033] NET: Registered protocol family 31
[   53.872041] Bluetooth: HCI device and connection manager initialized
[   53.872050] Bluetooth: HCI socket layer initialized
[   53.893597] Bluetooth: L2CAP ver 2.9
[   53.893605] Bluetooth: L2CAP socket layer initialized
[   53.954179] Bluetooth: RFCOMM socket layer initialized
[   53.954208] Bluetooth: RFCOMM TTY layer initialized
[   53.954212] Bluetooth: RFCOMM ver 1.8
[   55.736419] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[   56.260482] [fglrx] GART Table is not in FRAME_BUFFER range 
[   56.260496] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   56.260501] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   56.523950] [fglrx] interrupt source 10000000 successfully enabled
[   56.523959] [fglrx] enable ID = 0x00000004
[   56.523976] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   80.523672] UDF-fs: No VRS found
[   80.680267] ISO 9660 Extensions: Microsoft Joliet Level 3
[   80.681917] ISO 9660 Extensions: RRIP_1991A

```

---

### Post by yoyoned on 2009-02-26
It appears to be a known issue.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/65529](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/65529)

But it doesn't sound like it's causing any issues.  You could try adding force_addr=0xaddr to the kernel line of the applicable entry in /boot/grub/menu.lst, but if it's not causing any trouble, I'd just ignore it.

---

### Post by ambdeep on 2009-02-28
Thanks

---

