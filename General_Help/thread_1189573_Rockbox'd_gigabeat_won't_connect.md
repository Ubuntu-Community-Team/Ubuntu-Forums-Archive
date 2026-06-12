---
title: "Rockbox'd gigabeat won't connect"
date: 2009-06-16
forum: General Help
---

### Post by Huzudra on 2009-06-16
Alright, this gigabeat F40 with rockbox 3.2 on it SHOULD just connect like any USB hard drive when i plug it into any mass storage compliant computer, it always has in the past.

i'm on a fresh 9.04 wubi install here and when i plug it in, nothing happens.  works fine in windows 7 on the same computer and fine in xp on the laptop here (parents computers).  i just wanted to listen to some music through the computers surround, using the player like an external drive, but it won't come up when i plug it in.  the usb kingston memory stick comes up correct though.

heres the dmesq i ran, it looks like its waiting for the device to settle?

```

[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10485680 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2052988k/2097136k available (4126k kernel code, 42840k reserved, 2208k data, 532k init, 1191928k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004027] Calibrating delay loop (skipped), value calculated using timer frequency.. 4799.57 BogoMIPS (lpj=9599148)
[    0.004065] Security Framework initialized
[    0.004090] SELinux:  Disabled at boot.
[    0.004136] AppArmor: AppArmor initialized
[    0.004163] Mount-cache hash table entries: 512
[    0.004472] Initializing cgroup subsys ns
[    0.004482] Initializing cgroup subsys cpuacct
[    0.004487] Initializing cgroup subsys memory
[    0.004498] Initializing cgroup subsys freezer
[    0.004532] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004537] CPU: L2 cache: 512K
[    0.004545] CPU: Hyper-Threading is disabled
[    0.004578] Checking 'hlt' instruction... OK.
[    0.020945] SMP alternatives: switching to UP code
[    0.144863] Freeing SMP alternatives: 18k freed
[    0.144871] ACPI: Core revision 20080926
[    0.146836] ACPI: Checking initramfs for custom DSDT
[    0.508415] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.548112] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[    0.552002] Brought up 1 CPUs
[    0.552002] Total of 1 processors activated (4799.57 BogoMIPS).
[    0.552002] CPU0 attaching NULL sched-domain.
[    0.552002] net_namespace: 776 bytes
[    0.552002] Booting paravirtualized kernel on bare hardware
[    0.552002] Time: 13:07:07  Date: 06/16/09
[    0.552002] regulator: core version 0.5
[    0.552002] NET: Registered protocol family 16
[    0.552002] EISA bus registered
[    0.552002] ACPI: bus type pci registered
[    0.552002] PCI: PCI BIOS revision 2.10 entry at 0xf11b0, last bus=1
[    0.552002] PCI: Using configuration type 1 for base access
[    0.553876] ACPI: EC: Look up EC in DSDT
[    0.564116] ACPI: Interpreter enabled
[    0.564126] ACPI: (supports S0 S1 S4 S5)
[    0.564151] ACPI: Using IOAPIC for interrupt routing
[    0.572682] ACPI: No dock devices found.
[    0.572696] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.572774] pci 0000:00:00.0: reg 10 32bit mmio: [0xd8000000-0xdbffffff]
[    0.572963] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.573024] pci 0000:00:02.1: reg 20 io port: [0xe600-0xe61f]
[    0.573092] pci 0000:00:02.3: reg 10 32bit mmio: [0xd5800000-0xd5800fff]
[    0.573140] pci 0000:00:02.3: reg 30 32bit mmio: [0xdfee0000-0xdfefffff]
[    0.573155] pci 0000:00:02.3: supports D1 D2
[    0.573158] pci 0000:00:02.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.573165] pci 0000:00:02.3: PME# disabled
[    0.573202] pci 0000:00:02.5: reg 10 io port: [0xd800-0xd807]
[    0.573213] pci 0000:00:02.5: reg 14 io port: [0xd400-0xd403]
[    0.573222] pci 0000:00:02.5: reg 18 io port: [0xd000-0xd007]
[    0.573233] pci 0000:00:02.5: reg 1c io port: [0xb800-0xb803]
[    0.573242] pci 0000:00:02.5: reg 20 io port: [0xb400-0xb40f]
[    0.573311] pci 0000:00:02.7: reg 10 io port: [0xa400-0xa4ff]
[    0.573321] pci 0000:00:02.7: reg 14 io port: [0xa000-0xa07f]
[    0.573372] pci 0000:00:02.7: supports D1 D2
[    0.573374] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.573380] pci 0000:00:02.7: PME# disabled
[    0.573414] pci 0000:00:03.0: reg 10 32bit mmio: [0xd5000000-0xd5000fff]
[    0.573492] pci 0000:00:03.1: reg 10 32bit mmio: [0xd4800000-0xd4800fff]
[    0.573570] pci 0000:00:03.2: reg 10 32bit mmio: [0xd4000000-0xd4000fff]
[    0.573662] pci 0000:00:03.3: reg 10 32bit mmio: [0xd3800000-0xd3800fff]
[    0.573718] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.573724] pci 0000:00:03.3: PME# disabled
[    0.573782] pci 0000:00:04.0: reg 10 io port: [0x9800-0x98ff]
[    0.573793] pci 0000:00:04.0: reg 14 32bit mmio: [0xd3000000-0xd3000fff]
[    0.573833] pci 0000:00:04.0: reg 30 32bit mmio: [0xdfec0000-0xdfedffff]
[    0.573847] pci 0000:00:04.0: supports D1 D2
[    0.573850] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.573856] pci 0000:00:04.0: PME# disabled
[    0.573919] pci 0000:00:0c.0: reg 10 io port: [0x9400-0x94ff]
[    0.573930] pci 0000:00:0c.0: reg 14 32bit mmio: [0xd2800000-0xd28000ff]
[    0.573969] pci 0000:00:0c.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.573983] pci 0000:00:0c.0: supports D1 D2
[    0.573985] pci 0000:00:0c.0: PME# supported from D1 D2 D3hot
[    0.573991] pci 0000:00:0c.0: PME# disabled
[    0.574043] pci 0000:00:0d.0: reg 10 io port: [0x9000-0x903f]
[    0.574100] pci 0000:00:0d.0: supports D1 D2
[    0.574148] pci 0000:00:0d.1: reg 10 io port: [0x8800-0x8807]
[    0.574204] pci 0000:00:0d.1: supports D1 D2
[    0.574254] pci 0000:00:0d.2: reg 10 32bit mmio: [0xd2000000-0xd20007ff]
[    0.574265] pci 0000:00:0d.2: reg 14 32bit mmio: [0xd1800000-0xd1803fff]
[    0.574316] pci 0000:00:0d.2: supports D1 D2
[    0.574318] pci 0000:00:0d.2: PME# supported from D0 D1 D2 D3hot
[    0.574324] pci 0000:00:0d.2: PME# disabled
[    0.574384] pci 0000:00:0e.0: reg 10 io port: [0x8400-0x843f]
[    0.574394] pci 0000:00:0e.0: reg 14 io port: [0x8000-0x800f]
[    0.574404] pci 0000:00:0e.0: reg 18 io port: [0x7800-0x787f]
[    0.574415] pci 0000:00:0e.0: reg 1c 32bit mmio: [0xd1000000-0xd1000fff]
[    0.574425] pci 0000:00:0e.0: reg 20 32bit mmio: [0xd0800000-0xd081ffff]
[    0.574454] pci 0000:00:0e.0: supports D1
[    0.574544] pci 0000:01:00.0: reg 10 32bit mmio: [0xd7000000-0xd7ffffff]
[    0.574552] pci 0000:01:00.0: reg 14 32bit mmio: [0xe0000000-0xefffffff]
[    0.574561] pci 0000:01:00.0: reg 18 32bit mmio: [0xd6000000-0xd6ffffff]
[    0.574585] pci 0000:01:00.0: reg 30 32bit mmio: [0xdffe0000-0xdfffffff]
[    0.574655] pci 0000:00:01.0: bridge 32bit mmio: [0xd6000000-0xd7ffffff]
[    0.574662] pci 0000:00:01.0: bridge 32bit mmio pref: [0xdff00000-0xfebfffff]
[    0.574675] bus 00 -> node 0
[    0.574683] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.575164] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.577030] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.577193] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.577349] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.577505] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[    0.577657] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[    0.577810] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[    0.577963] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[    0.578116] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[    0.578295] ACPI: WMI: Mapper loaded
[    0.578652] SCSI subsystem initialized
[    0.578716] libata version 3.00 loaded.
[    0.578794] usbcore: registered new interface driver usbfs
[    0.578822] usbcore: registered new interface driver hub
[    0.578862] usbcore: registered new device driver usb
[    0.579037] PCI: Using ACPI for IRQ routing
[    0.579205] Bluetooth: Core ver 2.13
[    0.579205] NET: Registered protocol family 31
[    0.579205] Bluetooth: HCI device and connection manager initialized
[    0.579205] Bluetooth: HCI socket layer initialized
[    0.579205] NET: Registered protocol family 8
[    0.579205] NET: Registered protocol family 20
[    0.579205] NetLabel: Initializing
[    0.579205] NetLabel:  domain hash size = 128
[    0.579205] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.579205] NetLabel:  unlabeled traffic allowed by default
[    0.579205] AppArmor: AppArmor Filesystem Enabled
[    0.579205] pnp: PnP ACPI init
[    0.579205] ACPI: bus type pnp registered
[    0.586577] pnp: PnP ACPI: found 17 devices
[    0.586580] ACPI: ACPI bus type pnp unregistered
[    0.586587] PnPBIOS: Disabled by ACPI PNP
[    0.586602] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.586607] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.586610] system 00:00: iomem range 0x100000-0x7fffffff could not be reserved
[    0.586614] system 00:00: iomem range 0xfec00000-0xfec000ff has been reserved
[    0.586618] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.586626] system 00:02: ioport range 0xe400-0xe47f has been reserved
[    0.586630] system 00:02: ioport range 0xe480-0xe4ff has been reserved
[    0.586633] system 00:02: ioport range 0xe600-0xe61f has been reserved
[    0.586636] system 00:02: ioport range 0x480-0x48f has been reserved
[    0.586640] system 00:02: iomem range 0xffee0000-0xffefffff has been reserved
[    0.586648] system 00:03: iomem range 0xfffe0000-0xffffffff could not be reserved
[    0.586655] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.586667] system 00:10: ioport range 0x295-0x296 has been reserved
[    0.621463] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.621466] pci 0000:00:01.0:   IO window: disabled
[    0.621474] pci 0000:00:01.0:   MEM window: 0xd6000000-0xd7ffffff
[    0.621481] pci 0000:00:01.0:   PREFETCH window: 0x000000dff00000-0x000000febfffff
[    0.621504] pci 0000:00:01.0: setting latency timer to 64
[    0.621510] bus: 00 index 0 io port: [0x00-0xffff]
[    0.621513] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.621515] bus: 01 index 0 mmio: [0x0-0x0]
[    0.621518] bus: 01 index 1 mmio: [0xd6000000-0xd7ffffff]
[    0.621521] bus: 01 index 2 mmio: [0xdff00000-0xfebfffff]
[    0.621523] bus: 01 index 3 mmio: [0x0-0x0]
[    0.621539] NET: Registered protocol family 2
[    0.621717] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.622234] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.623998] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.625082] TCP: Hash tables configured (established 131072 bind 65536)
[    0.625092] TCP reno registered
[    0.625439] NET: Registered protocol family 1
[    0.625680] checking if image is initramfs... it is
[    1.124028] Switched to high resolution mode on CPU 0
[    1.390280] Freeing initrd memory: 7616k freed
[    1.390372] Simple Boot Flag at 0x3a set to 0x1
[    1.390430] cpufreq: No nForce2 chipset.
[    1.390727] audit: initializing netlink socket (disabled)
[    1.390769] type=2000 audit(1245157627.388:1): initialized
[    1.399120] highmem bounce pool size: 64 pages
[    1.399129] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.400681] VFS: Disk quotas dquot_6.5.1
[    1.400759] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.401566] fuse init (API version 7.10)
[    1.401687] msgmni has been set to 1698
[    1.401947] alg: No test for stdrng (krng)
[    1.401965] io scheduler noop registered
[    1.401968] io scheduler anticipatory registered
[    1.401971] io scheduler deadline registered
[    1.401997] io scheduler cfq registered (default)
[    1.448060] pci 0000:01:00.0: Boot video device
[    1.456195] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.456210] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.456394] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.456398] ACPI: Power Button (FF) [PWRF]
[    1.456460] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.456464] ACPI: Power Button (CM) [PWRB]
[    1.456618] ACPI: Invalid PBLK length [5]
[    1.456719] processor ACPI_CPU:00: registered as cooling_device0
[    1.461138] isapnp: Scanning for PnP cards...
[    1.814922] isapnp: No Plug & Play device found
[    1.816556] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.816675] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.816789] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.817237] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.817398] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.818479] brd: module loaded
[    1.818937] loop: module loaded
[    1.819065] Fixed MDIO Bus: probed
[    1.819075] PPP generic driver version 2.4.2
[    1.819161] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.819212] Driver 'sd' needs updating - please use bus_type methods
[    1.819226] Driver 'sr' needs updating - please use bus_type methods
[    1.819361] sata_promise 0000:00:0e.0: version 2.12
[    1.819401] sata_promise 0000:00:0e.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.832216] scsi0 : sata_promise
[    1.832382] scsi1 : sata_promise
[    1.832458] scsi2 : sata_promise
[    1.832505] ata1: SATA max UDMA/133 mmio m4096@0xd1000000 ata 0xd1000200 irq 16
[    1.832510] ata2: SATA max UDMA/133 mmio m4096@0xd1000000 ata 0xd1000280 irq 16
[    1.832513] ata3: PATA max UDMA/133 mmio m4096@0xd1000000 ata 0xd1000300 irq 16
[    2.152044] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.161415] ata1.00: ATA-7: Maxtor 6L300S0, BACE1G20, max UDMA/133
[    2.161419] ata1.00: 586114704 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.177413] ata1.00: configured for UDMA/133
[    2.496040] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.504742] ata2.00: ATA-8: WDC WD6401AALS-00L3B2, 01.03B01, max UDMA/133
[    2.504746] ata2.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.520789] ata2.00: configured for UDMA/133
[    2.676223] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L300S0   BACE PQ: 0 ANSI: 5
[    2.676374] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors: (300 GB/279 GiB)
[    2.676397] sd 0:0:0:0: [sda] Write Protect is off
[    2.676401] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.676436] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.676542] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors: (300 GB/279 GiB)
[    2.676561] sd 0:0:0:0: [sda] Write Protect is off
[    2.676565] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.676597] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.676603]  sda: sda1
[    2.694994] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.695081] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.695195] scsi 1:0:0:0: Direct-Access     ATA      WDC WD6401AALS-0 01.0 PQ: 0 ANSI: 5
[    2.695312] sd 1:0:0:0: [sdb] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    2.695333] sd 1:0:0:0: [sdb] Write Protect is off
[    2.695337] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.695370] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.695444] sd 1:0:0:0: [sdb] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    2.695462] sd 1:0:0:0: [sdb] Write Protect is off
[    2.695466] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.695498] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.695503]  sdb: sdb1 sdb2
[    2.705708] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.705771] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.706469] pata_sis 0000:00:02.5: version 0.5.2
[    2.706491] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.706751] scsi3 : pata_sis
[    2.706844] scsi4 : pata_sis
[    2.707578] ata4: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xb400 irq 14
[    2.707582] ata5: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xb408 irq 15
[    2.868371] ata4.00: ATAPI: HP      DVD Writer 740b, HJ24, max UDMA/33
[    2.884385] ata4.00: configured for UDMA/33
[    3.052961] scsi 3:0:0:0: CD-ROM            HP       DVD Writer 740b  HJ24 PQ: 0 ANSI: 5
[    3.058180] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    3.058186] Uniform CD-ROM driver Revision: 3.20
[    3.058346] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.058428] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    3.058616] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.058658] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.058693] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    3.058786] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    3.058843] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
[    3.058863] ehci_hcd 0000:00:03.3: irq 23, io mem 0xd3800000
[    3.068024] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    3.068134] usb usb1: configuration #1 chosen from 1 choice
[    3.068171] hub 1-0:1.0: USB hub found
[    3.068188] hub 1-0:1.0: 6 ports detected
[    3.068339] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.068369] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.068391] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.068452] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    3.068472] ohci_hcd 0000:00:03.0: irq 20, io mem 0xd5000000
[    3.126069] usb usb2: configuration #1 chosen from 1 choice
[    3.126103] hub 2-0:1.0: USB hub found
[    3.126120] hub 2-0:1.0: 2 ports detected
[    3.126248] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.126266] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.126324] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    3.126353] ohci_hcd 0000:00:03.1: irq 21, io mem 0xd4800000
[    3.182072] usb usb3: configuration #1 chosen from 1 choice
[    3.182106] hub 3-0:1.0: USB hub found
[    3.182120] hub 3-0:1.0: 2 ports detected
[    3.182227] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.182245] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    3.182304] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[    3.182329] ohci_hcd 0000:00:03.2: irq 22, io mem 0xd4000000
[    3.238067] usb usb4: configuration #1 chosen from 1 choice
[    3.238099] hub 4-0:1.0: USB hub found
[    3.238112] hub 4-0:1.0: 2 ports detected
[    3.238231] uhci_hcd: USB Universal Host Controller Interface driver
[    3.238356] usbcore: registered new interface driver libusual
[    3.238419] usbcore: registered new interface driver usbserial
[    3.238435] USB Serial support registered for generic
[    3.238455] usbcore: registered new interface driver usbserial_generic
[    3.238458] usbserial: USB Serial Driver core
[    3.238535] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.238861] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.238871] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.239042] mice: PS/2 mouse device common for all mice
[    3.239208] rtc_cmos 00:06: RTC can wake from S4
[    3.239264] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.239293] rtc0: alarms up to one month, 242 bytes nvram
[    3.239385] device-mapper: uevent: version 1.0.3
[    3.239560] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.239626] device-mapper: multipath: version 1.0.5 loaded
[    3.239631] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.239762] EISA: Probing bus 0 at eisa.0
[    3.239798] Cannot allocate resource for EISA slot 7
[    3.239801] Cannot allocate resource for EISA slot 8
[    3.239803] EISA: Detected 0 cards.
[    3.239847] cpuidle: using governor ladder
[    3.239851] cpuidle: using governor menu
[    3.240534] TCP cubic registered
[    3.240637] NET: Registered protocol family 10
[    3.241186] lo: Disabled Privacy Extensions
[    3.241581] NET: Registered protocol family 17
[    3.241609] Bluetooth: L2CAP ver 2.11
[    3.241612] Bluetooth: L2CAP socket layer initialized
[    3.241616] Bluetooth: SCO (Voice Link) ver 0.6
[    3.241619] Bluetooth: SCO socket layer initialized
[    3.241672] Bluetooth: RFCOMM socket layer initialized
[    3.241689] Bluetooth: RFCOMM TTY layer initialized
[    3.241691] Bluetooth: RFCOMM ver 1.10
[    3.241766] Using IPI No-Shortcut mode
[    3.241933] registered taskstats version 1
[    3.242096]   Magic number: 13:643:129
[    3.242170] acpi PNP0C02:01: hash matches
[    3.242175] acpi device:04: hash matches
[    3.242220] rtc_cmos 00:06: setting system clock to 2009-06-16 13:07:10 UTC (1245157630)
[    3.242225] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.242227] EDD information not available.
[    3.243261] Freeing unused kernel memory: 532k freed
[    3.243394] Write protecting the kernel text: 4128k
[    3.243439] Write protecting the kernel read-only data: 1532k
[    3.277936] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.385512] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.518615] usb 1-2: configuration #1 chosen from 1 choice
[    3.557156] Initializing USB Mass Storage driver...
[    3.567904] scsi5 : SCSI emulation for USB Mass Storage devices
[    3.584095] usbcore: registered new interface driver usb-storage
[    3.584104] USB Mass Storage support registered.
[    3.584282] usb-storage: device found at 2
[    3.584285] usb-storage: waiting for device to settle before scanning
[    3.746356] Floppy drive(s): fd0 is 1.44M
[    3.764796] FDC 0 is a post-1991 82077
[    3.917433] ohci1394 0000:00:02.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.969366] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[d5800000-d58007ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
[    3.989122] ohci1394 0000:00:0d.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    4.039024] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[d2000000-d20007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.159064] sis900.c: v1.08.10 Apr. 2 2006
[    4.159141] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.161179] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    4.177259] 0000:00:04.0: Using transceiver found at address 1 as default
[    4.193560] eth0: SiS 900 PCI Fast Ethernet at 0x9800, IRQ 19, 00:e0:18:ea:2b:51
[    4.193598] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.193624] r8169 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.193717] r8169 0000:00:0c.0: no PCI Express capability
[    4.194501] eth1: RTL8169sb/8110sb at 0xf7d42000, 00:e0:4c:09:70:28, XID 10000000 IRQ 16
[    5.109023] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.109031] EXT3-fs: write access will be enabled during recovery.
[    5.325563] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00023c0151127c8b]
[    5.460706] kjournald starting.  Commit interval 5 seconds
[    5.460745] EXT3-fs: recovery complete.
[    5.460990] EXT3-fs: mounted filesystem with ordered data mode.
[    8.584350] usb-storage: device scan complete
[    8.585105] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[    8.586522] sd 5:0:0:0: [sdc] 1952768 512-byte hardware sectors: (999 MB/953 MiB)
[    8.587024] sd 5:0:0:0: [sdc] Write Protect is off
[    8.587029] sd 5:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    8.587033] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    8.588899] sd 5:0:0:0: [sdc] 1952768 512-byte hardware sectors: (999 MB/953 MiB)
[    8.589522] sd 5:0:0:0: [sdc] Write Protect is off
[    8.589527] sd 5:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    8.589531] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    8.589542]  sdc: sdc1
[    8.590569] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    8.590674] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    8.948937] udev: starting version 141
[    9.151539] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.175911] Linux agpgart interface v0.103
[    9.178392] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
[    9.203266] parport_pc 00:0a: reported by Plug and Play ACPI
[    9.203401] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    9.212262] agpgart-sis 0000:00:00.0: SiS chipset [1039/0648]
[    9.217053] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd8000000
[    9.516765] nvidia: module license 'NVIDIA' taints kernel.
[   10.067053] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   10.069073] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.070262] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   10.388064] intel8x0_measure_ac97_clock: measured 54411 usecs
[   10.388070] intel8x0: clocking to 48000
[   10.456965] gameport: EMU10K1 is pci0000:00:0d.1/gameport0, io 0x8800, speed 932kHz
[   10.493672] EMU10K1_Audigy 0000:00:0d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.498759] Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[   10.542059] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   10.657955] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.005958] ppdev: user-space parallel port driver
[   11.127776] psmouse serio1: ID: 10 00 64<4>logips2pp: Detected unknown logitech mouse model 105
[   11.358833] lp0: using parport0 (interrupt-driven).
[   11.676327] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   12.048153] EXT3 FS on loop0, internal journal
[   16.313093] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k
[   16.507823] type=1505 audit(1245179243.761:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2056
[   16.576105] type=1505 audit(1245179243.833:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2060
[   16.576512] type=1505 audit(1245179243.833:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2060
[   16.576604] type=1505 audit(1245179243.833:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2060
[   16.576673] type=1505 audit(1245179243.833:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2060
[   16.767999] type=1505 audit(1245179244.021:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2065
[   16.768563] type=1505 audit(1245179244.025:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2065
[   16.813975] type=1505 audit(1245179244.069:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2069
[   19.897848] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.897854] Bluetooth: BNEP filters: protocol multicast
[   19.919102] Bridge firewalling registered
[   22.255119] agpgart-sis 0000:00:00.0: AGP 3.0 bridge
[   22.255149] agpgart-sis 0000:00:00.0: putting AGP V3 device at 0000:00:00.0 into 4x mode
[   22.255155] agpgart-sis 0000:00:00.0: SiS delay workaround: giving bridge time to recover
[   22.268137] agpgart-sis 0000:00:00.0: putting AGP V3 device at 0000:01:00.0 into 4x mode
[   24.744589] r8169: eth1: link down
[   24.744812] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   26.745579] eth0: Media Link On 100mbps full-duplex 
[   34.820029] eth0: no IPv6 routers present
[B][   60.464043] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   60.625211] usb 1-4: configuration #1 chosen from 1 choice
[   60.658309] scsi6 : SCSI emulation for USB Mass Storage devices
[   60.658721] usb-storage: device found at 3
[   60.658725] usb-storage: waiting for device to settle before scanning
[22239.396743] usb 1-2: USB disconnect, address 2
[22254.538514] usb 1-4: USB disconnect, address 3
[22263.000032] usb 1-4: new high speed USB device using ehci_hcd and address 4
[22263.135339] usb 1-4: configuration #1 chosen from 1 choice
[22263.136667] scsi7 : SCSI emulation for USB Mass Storage devices
[22263.136969] usb-storage: device found at 4
[22263.136972] usb-storage: waiting for device to settle before scanning[/B]
bob@ubuntu:~$ 

```

thoughts?  i've been googling like a mad man, and all i can find are references to some sansa players, but none of it looks like the issue with the gigabeat.  ignore that its a music player with rockbox, treat it as a USB external hard drive.

---

### Post by Chronon on 2009-06-16
Yes.  It's the same problem with Jaunty trying to mount the device in MTP mode without due diligence.  (I also have this problem with my Rockboxed Gigabeat F40.)  In my experience, UMS support has been a bit broken in Jaunty because of this.  Strangely, my Rockboxed DAPs seem to connect properly (as UMS devices) on my Eee PC running Jaunty (NBR).  

Here's the relevant bug report that I think you're alluding to: [https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998)

---

### Post by Huzudra on 2009-06-17
so how do i get it to work? i use ubuntu 9.04 at home as well, 9.04 seems more broken that 8.1 was :(

---

### Post by roebeet on 2009-08-29
Found this while googling something else, so sorry for the late reply.

I have this same problem with my Rockboxed Gigabeat plus Jaunty x64.   Since I use Virtualbox constantly, my workaround is to mount it in one of my VM's, then unmount it - after that, the drive will show up in my Jaunty host.   Not the best workaround, but it works for me.

---

