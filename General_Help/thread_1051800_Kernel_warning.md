---
title: "Kernel warning"
date: 2009-01-27
forum: General Help
---

### Post by nkonstas on 2009-01-27
Hi,

I keep getting the following warning in the Kernel ring buffer:

longhaul: Warning: Timeout while waiting for idle PCI bus.

Any ideas?

Edit: I'm running Kernel 2.6.24-23-generic

Thanks,
Nikos.

---

### Post by Yashiro on 2009-01-27
Running 'lspci' will give you a possible list of culprits.

If could be harmless though, possibly disk related? Do you use PATA/IDE disks?

---

### Post by nkonstas on 2009-01-27
Thanks.

Is there a way to find out which device actually causes the problem?

I'm not sure if I still have any IDE/PATA drives on that machine. How to find out without opening it up...? :)

Here's the complete output from dmesg in case it helps:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Nov 27 18:44:42 UTC 2008 (Ubuntu 2.6.24-23.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001eff0000 (usable)
[    0.000000]  BIOS-e820: 000000001eff0000 - 000000001eff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001eff3000 - 000000001f000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 495MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 126960) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   126960
[    0.000000]   HighMem    126960 ->   126960
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   126960
[    0.000000] On node 0 totalpages: 126960
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 959 pages used for memmap
[    0.000000]   Normal zone: 121905 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6560 checksum 0
[    0.000000] ACPI: RSDP 000F6560, 0014 (r0 VT9174)
[    0.000000] ACPI: RSDT 1EFF3000, 0028 (r1 VT9174 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1EFF3040, 0074 (r1 VT9174 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1EFF30C0, 2FDD (r1 VT9174 AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 1EFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f000000:e0ff0000)
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 125969
[    0.000000] Kernel command line: root=UUID=af008a0c-5e18-4bd2-9f5d-884b266e6094 ro quiet splash
[    0.000000] No local APIC present or hardware disabled
[    0.000000] mapped APIC to ffffb000 (013ed000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 999.874 MHz processor.
[   34.314255] Console: colour VGA+ 80x25
[   34.314265] console [tty0] enabled
[   34.315392] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   34.317273] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   34.391444] Memory: 490528k/507840k available (2178k kernel code, 16752k reserved, 1005k data, 368k init, 0k highmem)
[   34.391478] virtual kernel memory layout:
[   34.391482]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   34.391487]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   34.391492]     vmalloc : 0xdf800000 - 0xff7fe000   ( 511 MB)
[   34.391497]     lowmem  : 0xc0000000 - 0xdeff0000   ( 495 MB)
[   34.391502]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   34.391507]       .data : 0xc0320918 - 0xc041bdc4   (1005 kB)
[   34.391512]       .text : 0xc0100000 - 0xc0320918   (2178 kB)
[   34.391524] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   34.391632] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   34.471659] Calibrating delay using timer specific routine.. 2001.79 BogoMIPS (lpj=4003590)
[   34.471731] Security Framework initialized
[   34.471757] SELinux:  Disabled at boot.
[   34.471813] AppArmor: AppArmor initialized
[   34.471829] Failure registering capabilities with primary security module.
[   34.471856] Mount-cache hash table entries: 512
[   34.472158] Initializing cgroup subsys ns
[   34.472170] Initializing cgroup subsys cpuacct
[   34.472198] CPU: After generic identify, caps: 0380b035 1380b035 00000000 00000000 00000000 00000000 00000000 00000000
[   34.472226] CPU: L1 I Cache: 64K (32 bytes/line), D cache 64K (32 bytes/line)
[   34.472236] CPU: L2 Cache: 64K (32 bytes/line)
[   34.472243] CPU: After all inits, caps: 0380b135 1380b035 00000000 00000000 00000000 00000000 00000000 00000000
[   34.472271] Compat vDSO mapped to ffffe000.
[   34.472310] Checking 'hlt' instruction... OK.
[   34.488287] SMP alternatives: switching to UP code
[   34.490989] Freeing SMP alternatives: 11k freed
[   34.491378] Early unpacking initramfs... done
[   35.838576] ACPI: Core revision 20070126
[   35.838808] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   35.842911] ACPI: setting ELCR to 0200 (from 1e20)
[   35.845908] CPU0: Centaur VIA Nehemiah stepping 01
[   35.845925] SMP motherboard not detected.
[   35.845932] Local APIC not detected. Using dummy APIC emulation.
[   35.846081] Brought up 1 CPUs
[   35.846156] CPU0 attaching sched-domain:
[   35.846166]  domain 0: span 01
[   35.846172]   groups: 01
[   35.846790] net_namespace: 64 bytes
[   35.846814] Booting paravirtualized kernel on bare hardware
[   35.848234] Time:  1:02:45  Date: 01/27/09
[   35.848343] NET: Registered protocol family 16
[   35.849125] EISA bus registered
[   35.849156] ACPI: bus type pci registered
[   35.868123] PCI: PCI BIOS revision 2.10 entry at 0xfb260, last bus=1
[   35.868135] PCI: Using configuration type 1
[   35.868166] Setting up standard PCI resources
[   35.876487] ACPI: EC: Look up EC in DSDT
[   35.885129] ACPI: Interpreter enabled
[   35.885148] ACPI: (supports S0 S1 S4 S5)
[   35.885188] ACPI: Using PIC for interrupt routing
[   35.898152] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   35.898865] PCI quirk: region 0400-047f claimed by vt8235 PM
[   35.898878] PCI quirk: region 0500-050f claimed by vt8235 SMB
[   35.899453] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   35.940037] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   35.940473] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   35.940907] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[   35.941341] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   35.941822] Linux Plug and Play Support v0.97 (c) Adam Belay
[   35.941957] pnp: PnP ACPI init
[   35.941986] ACPI: bus type pnp registered
[   35.951036] pnp: PnP ACPI: found 13 devices
[   35.951051] ACPI: ACPI bus type pnp unregistered
[   35.951064] PnPBIOS: Disabled by ACPI PNP
[   35.952126] PCI: Using ACPI for IRQ routing
[   35.952141] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   35.995505] NET: Registered protocol family 8
[   35.995517] NET: Registered protocol family 20
[   35.995804] AppArmor: AppArmor Filesystem Enabled
[   35.999480] Time: tsc clocksource has been installed.
[   36.007686] system 00:00: iomem range 0xd4800-0xd7fff has been reserved
[   36.007700] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   36.007711] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   36.007721] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   36.007733] system 00:00: iomem range 0x1eff0000-0x1effffff could not be reserved
[   36.007745] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   36.007756] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   36.007767] system 00:00: iomem range 0x100000-0x1efeffff could not be reserved
[   36.007779] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[   36.007790] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[   36.007813] system 00:02: ioport range 0x400-0x47f has been reserved
[   36.007824] system 00:02: ioport range 0x500-0x50f has been reserved
[   36.007848] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   36.039519] PCI: Bridge: 0000:00:01.0
[   36.039529]   IO window: disabled.
[   36.039541]   MEM window: dc000000-ddffffff
[   36.039551]   PREFETCH window: d8000000-dbffffff
[   36.039583] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   36.039627] NET: Registered protocol family 2
[   36.079789] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   36.080542] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   36.081054] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   36.081664] TCP: Hash tables configured (established 16384 bind 16384)
[   36.081675] TCP reno registered
[   36.091919] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   37.305263]  it is
[   38.695628] Freeing initrd memory: 7748k freed
[   38.697242] audit: initializing netlink socket (disabled)
[   38.697284] audit(1233018167.308:1): initialized
[   38.704851] VFS: Disk quotas dquot_6.5.1
[   38.705160] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   38.705665] io scheduler noop registered
[   38.705675] io scheduler anticipatory registered
[   38.705682] io scheduler deadline registered
[   38.705721] io scheduler cfq registered (default)
[   38.705753] PCI: VIA PCI bridge detected. Disabling DAC.
[   38.705854] Boot video device is 0000:01:00.0
[   38.706829] isapnp: Scanning for PnP cards...
[   39.060899] isapnp: No Plug & Play device found
[   39.171909] Real Time Clock Driver v1.12ac
[   39.172238] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   39.172528] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.172915] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   39.174364] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.175158] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   39.177926] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   39.178199] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   39.178731] PNP: No PS/2 controller found. Probing ports directly.
[   39.430899] serio: i8042 KBD port at 0x60,0x64 irq 1
[   39.443092] mice: PS/2 mouse device common for all mice
[   39.443552] EISA: Probing bus 0 at eisa.0
[   39.443616] EISA: Detected 0 cards.
[   39.443626] cpuidle: using governor ladder
[   39.443633] cpuidle: using governor menu
[   39.444177] NET: Registered protocol family 1
[   39.444268] Using IPI No-Shortcut mode
[   39.444386] registered taskstats version 1
[   39.444689]   Magic number: 9:62:4
[   39.444727]   hash matches device ttybf
[   39.445008] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   39.445016] EDD information not available.
[   39.446610] Freeing unused kernel memory: 368k freed
[   39.446701] Write protecting the kernel read-only data: 801k
[   41.314105] fuse init (API version 7.9)
[   41.550633] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   41.550658] ACPI: Processor [CPU0] (supports 2 throttling states)
[   41.630002] md: linear personality registered for level -1
[   41.644586] md: multipath personality registered for level -4
[   41.659908] md: raid0 personality registered for level 0
[   41.676519] md: raid1 personality registered for level 1
[   41.690056] xor: automatically using best checksumming function: pIII_sse
[   41.706386]    pIII_sse  :  2189.000 MB/sec
[   41.706394] xor: using function: pIII_sse (2189.000 MB/sec)
[   41.710530] async_tx: api initialized (async)
[   41.790709] raid6: int32x1    117 MB/s
[   41.858573] raid6: int32x2    160 MB/s
[   41.926448] raid6: int32x4    159 MB/s
[   41.994617] raid6: int32x8    124 MB/s
[   42.062389] raid6: mmxx1      364 MB/s
[   42.130330] raid6: mmxx2      500 MB/s
[   42.198484] raid6: sse1x1     303 MB/s
[   42.266342] raid6: sse1x2     464 MB/s
[   42.266350] raid6: using algorithm sse1x2 (464 MB/s)
[   42.266361] md: raid6 personality registered for level 6
[   42.266368] md: raid5 personality registered for level 5
[   42.266376] md: raid4 personality registered for level 4
[   42.361581] md: raid10 personality registered for level 10
[   43.550344] usbcore: registered new interface driver usbfs
[   43.550407] usbcore: registered new interface driver hub
[   43.591314] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   43.591333] PCI: setting IRQ 10 as level-triggered
[   43.591342] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   43.644422] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[df003000-df0037ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   43.686226] usbcore: registered new device driver usb
[   43.726201] USB Universal Host Controller Interface driver v3.0
[   44.133824] SCSI subsystem initialized
[   44.172585] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   44.172603] PCI: setting IRQ 11 as level-triggered
[   44.172613] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   44.172645] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   44.173395] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   44.173449] uhci_hcd 0000:00:10.0: irq 11, io base 0x00009400
[   44.174003] usb usb1: configuration #1 chosen from 1 choice
[   44.174089] hub 1-0:1.0: USB hub found
[   44.174110] hub 1-0:1.0: 2 ports detected
[   44.242056] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   44.242079] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   44.278288] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   44.278328] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   44.278403] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   44.278450] uhci_hcd 0000:00:10.1: irq 10, io base 0x00009800
[   44.278854] usb usb2: configuration #1 chosen from 1 choice
[   44.278926] hub 2-0:1.0: USB hub found
[   44.278946] hub 2-0:1.0: 2 ports detected
[   44.383303] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
[   44.383320] PCI: setting IRQ 12 as level-triggered
[   44.383330] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
[   44.383361] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   44.383464] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   44.383515] uhci_hcd 0000:00:10.2: irq 12, io base 0x00009c00
[   44.383920] usb usb3: configuration #1 chosen from 1 choice
[   44.383994] hub 3-0:1.0: USB hub found
[   44.384014] hub 3-0:1.0: 2 ports detected
[   44.487411] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[   44.487429] PCI: setting IRQ 5 as level-triggered
[   44.487438] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   44.487475] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   44.487597] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   44.487710] ehci_hcd 0000:00:10.3: irq 5, io mem 0xdf000000
[   44.497939] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   44.498321] usb usb4: configuration #1 chosen from 1 choice
[   44.498411] hub 4-0:1.0: USB hub found
[   44.498433] hub 4-0:1.0: 6 ports detected
[   44.529314] libata version 3.00 loaded.
[   44.602768] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   44.607504] eth0: VIA Rhine II at 0xdf001000, 00:40:63:cc:19:00, IRQ 11.
[   44.608224] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link cde1.
[   44.611022] pata_via 0000:00:11.1: version 0.3.3
[   44.611112] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   44.611132] PCI: VIA VLink IRQ fixup for 0000:00:11.1, from 255 to 11
[   44.650673] scsi0 : pata_via
[   44.690690] scsi1 : pata_via
[   44.696182] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xa000 irq 14
[   44.696197] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xa008 irq 15
[   44.858540] ata1.00: ATA-7: Hitachi HDT725040VLAT80, V5COA4EA, max UDMA/133
[   44.858559] ata1.00: 781422768 sectors, multi 16: LBA48 
[   44.874332] ata1.00: configured for UDMA/133
[   45.039615] ata2.00: ATA-6: WDC WD2000BB-22GUA0, 08.02D08, max UDMA/100
[   45.039633] ata2.00: 390721968 sectors, multi 16: LBA48 
[   45.049654] FDC 0 is a post-1991 82077
[   45.055493] ata2.00: configured for UDMA/100
[   45.055848] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72504 V5CO PQ: 0 ANSI: 5
[   45.056292] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2000BB-22G 08.0 PQ: 0 ANSI: 5
[   45.063782] sata_sil 0000:00:14.0: version 2.3
[   45.063987] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   45.097857] scsi2 : sata_sil
[   45.146863] scsi3 : sata_sil
[   45.165810] scsi4 : sata_sil
[   45.193788] scsi5 : sata_sil
[   45.193960] ata3: SATA max UDMA/100 mmio m1024@0xdf002000 tf 0xdf002080 irq 10
[   45.193972] ata4: SATA max UDMA/100 mmio m1024@0xdf002000 tf 0xdf0020c0 irq 10
[   45.193983] ata5: SATA max UDMA/100 mmio m1024@0xdf002000 tf 0xdf002280 irq 10
[   45.193993] ata6: SATA max UDMA/100 mmio m1024@0xdf002000 tf 0xdf0022c0 irq 10
[   45.442154] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[004063000003ca21]
[   45.505825] ata3: SATA link down (SStatus 0 SControl 310)
[   45.973700] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   46.002551] ata4.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[   46.002570] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (not used)
[   46.018905] ata4.00: configured for UDMA/100
[   46.330415] ata5: SATA link down (SStatus 0 SControl 310)
[   46.797544] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   46.827868] ata6.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[   46.827886] ata6.00: 976773168 sectors, multi 16: LBA48 NCQ (not used)
[   46.842236] ata6.00: configured for UDMA/100
[   46.842625] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   46.843033] scsi 5:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   47.164146] Driver 'sd' needs updating - please use bus_type methods
[   47.164842] sd 0:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
[   47.164892] sd 0:0:0:0: [sda] Write Protect is off
[   47.164902] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   47.164958] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.165133] sd 0:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
[   47.165173] sd 0:0:0:0: [sda] Write Protect is off
[   47.165182] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   47.165233] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.165248]  sda: sda1 sda2 < sda5 >
[   47.196976] sd 0:0:0:0: [sda] Attached SCSI disk
[   47.197193] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[   47.197239] sd 1:0:0:0: [sdb] Write Protect is off
[   47.197249] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   47.197307] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.197521] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[   47.197564] sd 1:0:0:0: [sdb] Write Protect is off
[   47.197573] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   47.197628] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.197645]  sdb: sdb1
[   47.225951] sd 1:0:0:0: [sdb] Attached SCSI disk
[   47.226175] sd 3:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   47.226221] sd 3:0:0:0: [sdc] Write Protect is off
[   47.226231] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   47.226289] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.226446] sd 3:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   47.226487] sd 3:0:0:0: [sdc] Write Protect is off
[   47.226496] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   47.226550] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.226564]  sdc: sdc1
[   47.235285] sd 3:0:0:0: [sdc] Attached SCSI disk
[   47.235489] sd 5:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[   47.235533] sd 5:0:0:0: [sdd] Write Protect is off
[   47.235543] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   47.235601] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.235738] sd 5:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[   47.235778] sd 5:0:0:0: [sdd] Write Protect is off
[   47.235787] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   47.235841] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.235857]  sdd: sdd1
[   47.239155] sd 5:0:0:0: [sdd] Attached SCSI disk
[   47.304972] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   47.305033] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   47.305086] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   47.305141] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   47.838865] md: md0 stopped.
[   47.874799] md: md0 stopped.
[   48.039761] Attempting manual resume
[   48.039775] swsusp: Resume From Partition 8:5
[   48.039782] PM: Checking swsusp image.
[   48.040127] PM: Resume from disk failed.
[   48.131867] kjournald starting.  Commit interval 5 seconds
[   48.131918] EXT3-fs: mounted filesystem with ordered data mode.
[   56.853007] ip_tables: (C) 2000-2006 Netfilter Core Team
[   56.917547] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[   59.022177] md: md0 stopped.
[   59.040901] md: bind<sdd1>
[   59.041901] md: bind<sdc1>
[   61.526607] Linux agpgart interface v0.102
[   61.594956] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   61.672423] agpgart: Detected VIA CLE266 chipset
[   61.686491] agpgart: AGP aperture is 128M @ 0xd0000000
[   61.759415] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   61.838749] raid1: raid set md0 active with 2 out of 2 mirrors
[   62.982594] irda_init()
[   62.982657] NET: Registered protocol family 23
[   64.198860] input: Power Button (FF) as /devices/virtual/input/input1
[   64.210312] ACPI: Power Button (FF) [PWRF]
[   64.210694] input: Power Button (CM) as /devices/virtual/input/input2
[   64.226288] ACPI: Power Button (CM) [PWRB]
[   64.886418] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   65.157990] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   65.158951] vt8623fb 0000:01:00.0: memory size detection failed (10 4), suppose 16 MB
[   66.310320] Console: switching to colour frame buffer device 80x30
[   66.310358] fb0: VIA VT8623 on 0000:01:00.0, 16 MB RAM
[   67.852875] eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[   71.617354] parport_pc 00:0b: reported by Plug and Play ACPI
[   71.617399] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   72.484272] NET: Registered protocol family 10
[   72.485264] lo: Disabled Privacy Extensions
[   73.154037] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
[   73.154208] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   77.756771] lp0: using parport0 (interrupt-driven).
[   77.896839] vt1211: Found VT1211 chip at 0x6000, revision 2
[   78.191155] Adding 2843464k swap on /dev/sda5.  Priority:-1 extents:1 across:2843464k
[   78.981383] EXT3 FS on sda1, internal journal
[   79.935531] kjournald starting.  Commit interval 5 seconds
[   79.935570] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[   79.972766] EXT3 FS on md0, internal journal
[   79.972792] EXT3-fs: mounted filesystem with ordered data mode.
[   80.014156] ReiserFS: sdb1: found reiserfs format "3.6" with standard journal
[   80.014207] ReiserFS: sdb1: using ordered data mode
[   80.038965] ReiserFS: sdb1: journal params: device sdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   80.044226] ReiserFS: sdb1: checking transaction log (sdb1)
[   80.146873] ReiserFS: sdb1: Using r5 hash to sort names
[   81.726051] NET: Registered protocol family 15
[   82.462007] padlock: VIA PadLock Hash Engine not detected.
[   82.630901] eth0: no IPv6 routers present
[   82.770679] padlock: VIA PadLock Hash Engine not detected.
[   83.412228] padlock: VIA PadLock not detected.
[   86.643694] eth0: link down
[   88.608819] No dock devices found.
[   89.453480] longhaul: VIA C3 'Nehemiah A' [C5XLOE] CPU detected.  Powersaver supported.
[   89.453520] longhaul: ACPI I/O at 0x400
[   89.453563] longhaul: Using northbridge support.
[   89.453570] longhaul: Using ACPI support.
[   92.363946] tun: Universal TUN/TAP device driver, 1.6
[   92.363964] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   92.366715] tun0: Disabled Privacy Extensions
[   93.273659] ppdev: user-space parallel port driver
[   93.441802] audit(1233018222.908:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5543 profile="/usr/sbin/cupsd" namespace="default"
[   95.543482] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   95.543501] apm: overridden by ACPI.
[  135.797579] Marking TSC unstable due to: cpufreq changes.
[  135.798877] Time: acpi_pm clocksource has been installed.
[  149.750885] Clocksource tsc unstable (delta = -126151502 ns)
[  159.011183] Bluetooth: Core ver 2.11
[  159.013967] NET: Registered protocol family 31
[  159.013990] Bluetooth: HCI device and connection manager initialized
[  159.014007] Bluetooth: HCI socket layer initialized
[  106.370079] Bluetooth: L2CAP ver 2.9
[  106.370097] Bluetooth: L2CAP socket layer initialized
[  106.580706] Bluetooth: RFCOMM socket layer initialized
[  106.580763] Bluetooth: RFCOMM TTY layer initialized
[  106.580770] Bluetooth: RFCOMM ver 1.8
[  110.462391] [drm] Initialized drm 1.1.0 20060810
[  110.487153] [drm] Initialized via 2.11.1 20070202 on minor 0
[  110.535773] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  110.535823] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  110.535895] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  193.977509] eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[ 2980.485132] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 2562.179821] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 7209.493664] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 7217.015912] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9048.989056] longhaul: Warning: Timeout while waiting for idle PCI bus.
[10860.455293] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8375.667493] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 7262.402624] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9079.646283] longhaul: Warning: Timeout while waiting for idle PCI bus.
[10904.621387] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 7790.969855] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9104.466411] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11008.737243] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11016.031296] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11030.819200] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9197.257817] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 7908.124892] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11090.639201] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11120.373974] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 7945.228048] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11135.112459] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8578.522021] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8595.636307] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11187.090396] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11201.966254] longhaul: Warning: Timeout while waiting for idle PCI bus.
[10201.128521] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11352.235004] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11382.202835] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11389.496801] longhaul: Warning: Timeout while waiting for idle PCI bus.
[10412.290822] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11456.361145] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11471.351454] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8831.142863] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11478.511470] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11485.409799] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11492.495994] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11499.702103] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8215.994260] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11507.179218] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11514.078853] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11521.169747] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11528.259941] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8247.005601] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11557.673514] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8257.391925] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11565.158600] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11572.156888] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11579.648742] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8272.936836] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11586.929988] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8278.132827] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11594.207268] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11601.493315] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11608.487556] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8293.673473] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11615.978271] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11623.260320] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11630.560349] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9696.700882] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11637.806023] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11644.800274] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11651.986407] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9737.837119] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 7815.507524] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11753.396209] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11863.525216] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9891.033049] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12006.375234] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12066.077099] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12073.270831] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12080.564838] longhaul: Warning: Timeout while waiting for idle PCI bus.
[10993.148589] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12102.438942] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12109.633092] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12116.927117] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8656.773967] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9333.897264] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9408.090737] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12235.568891] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9419.356050] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12243.040356] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12249.933992] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9430.401800] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12257.396366] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12264.683899] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12271.885981] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9471.016313] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12331.140542] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12390.767239] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12405.368103] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8287.984091] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12435.483678] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12436.856252] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9572.833523] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11315.813839] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8887.779666] longhaul: Warning: Timeout while waiting for idle PCI bus.
[11325.885071] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9589.657690] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8316.467822] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12466.896044] longhaul: Warning: Timeout while waiting for idle PCI bus.
[10394.544123] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12480.115268] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9610.288435] longhaul: Warning: Timeout while waiting for idle PCI bus.
[10407.967518] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8335.380052] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12495.239906] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12497.122673] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 8341.206297] longhaul: Warning: Timeout while waiting for idle PCI bus.
[12503.978955] longhaul: Warning: Timeout while waiting for idle PCI bus.
[14981.552021] longhaul: Warning: Timeout while waiting for idle PCI bus.
[ 9997.818227] longhaul: Warning: Timeout while waiting for idle PCI bus.
[10015.950373] longhaul: Warning: Timeout while waiting for idle PCI bus.
[13654.839588] longhaul: Warning: Timeout while waiting for idle PCI bus.
[13659.194045] longhaul: Warning: Timeout while waiting for idle PCI bus.
[18599.696696] longhaul: Warning: Timeout while waiting for idle PCI bus.
[20200.375028] longhaul: Warning: Timeout while waiting for idle PCI bus.
[22219.050008] longhaul: Warning: Timeout while waiting for idle PCI bus.
[25830.400352] longhaul: Warning: Timeout while waiting for idle PCI bus.
[25837.694378] longhaul: Warning: Timeout while waiting for idle PCI bus.

---

