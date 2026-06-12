---
title: "Finalizing Live Cd"
date: 2009-05-21
forum: General Help
---

### Post by texas.chef94 on 2009-05-21
I have a grandson who I want to introduce Linux, but on my computer, but not my HD.
I understand on some smaller ISO images where there is room to spare that it is possible to load the CD to RAM and save the changes on the CD, but has something to do with finalizing the CD which I do not understand.
Anyone out there able to direct me to a article or resource or is this just a myth. Thanks

Allen

---

### Post by geirha on 2009-05-21
I haven't heard of this myself, and I don't think you can burn on a CD while it is being used. I think your best bet is to put a liveCD image on a >= 1GB USB-stick and make it persistant. [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by texas.chef94 on 2009-05-21
So I passed on the CD option. I know the USB pen is sdc1
[http://s577.photobucket.com/albums/ss219/worthamtx/](http://s577.photobucket.com/albums/ss219/worthamtx/)
Screenschot 4.4 unzipped
What must I do to get this OS to boot for my grandson.
some one said to run this and I did (way over my head)
    0.004230] Initializing cgroup subsys cpuacct
[    0.004233] Initializing cgroup subsys memory
[    0.004238] Initializing cgroup subsys freezer
[    0.004252] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004255] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004257] tseg: 001bf00000
[    0.004276] SMP alternatives: switching to UP code
[    0.135269] ACPI: Core revision 20080926
[    0.136399] ACPI: Checking initramfs for custom DSDT
[    0.460067] Setting APIC routing to flat
[    0.460777] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.500971] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[    0.504002] Brought up 1 CPUs
[    0.504002] Total of 1 processors activated (3581.67 BogoMIPS).
[    0.504002] CPU0 attaching NULL sched-domain.
[    0.504002] net_namespace: 1400 bytes
[    0.504002] Booting paravirtualized kernel on bare hardware
[    0.504002] Time: 11:30:31  Date: 05/21/09
[    0.504002] regulator: core version 0.5
[    0.504002] NET: Registered protocol family 16
[    0.504002] node 0 link 0: io port [b000, ffff]
[    0.504002] TOM: 0000000020000000 aka 512M
[    0.504002] node 0 link 0: mmio [a0000, bffff]
[    0.504002] node 0 link 0: mmio [20000000, fe02ffff]
[    0.504002] node 0 link 0: mmio [e0000000, e03fffff]
[    0.504002] bus: [00,03] on node 0 link 0
[    0.504002] bus: 00 index 0 io port: [0, ffff]
[    0.504002] bus: 00 index 1 mmio: [a0000, bffff]
[    0.504002] bus: 00 index 2 mmio: [20000000, fcffffffff]
[    0.504002] ACPI: bus type pci registered
[    0.504002] PCI: Using configuration type 1 for base access
[    0.504002] ACPI: EC: Look up EC in DSDT
[    0.506423] ACPI: Interpreter enabled
[    0.506427] ACPI: (supports S0 S3 S4 S5)
[    0.506449] ACPI: Using IOAPIC for interrupt routing
[    0.510228] ACPI: No dock devices found.
[    0.510237] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.510280] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.510325] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.510328] pci 0000:00:05.0: PME# disabled
[    0.510397] pci 0000:00:12.0: reg 10 io port: [0xfc00-0xfc07]
[    0.510405] pci 0000:00:12.0: reg 14 io port: [0xf800-0xf803]
[    0.510413] pci 0000:00:12.0: reg 18 io port: [0xf400-0xf407]
[    0.510422] pci 0000:00:12.0: reg 1c io port: [0xf000-0xf003]
[    0.510430] pci 0000:00:12.0: reg 20 io port: [0xec00-0xec0f]
[    0.510438] pci 0000:00:12.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f1ff]
[    0.510446] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.510460] pci 0000:00:12.0: supports D1 D2
[    0.510505] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02e000-0xfe02efff]
[    0.510595] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.510695] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.510744] pci 0000:00:13.2: supports D1 D2
[    0.510746] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.510750] pci 0000:00:13.2: PME# disabled
[    0.510801] pci 0000:00:14.0: reg 10 io port: [0x500-0x50f]
[    0.510809] pci 0000:00:14.0: reg 14 32bit mmio: [0xfe02b000-0xfe02b3ff]
[    0.510844] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.510892] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.510900] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.510908] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.510916] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.510925] pci 0000:00:14.1: reg 20 io port: [0xe400-0xe40f]
[    0.511087] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe02a000-0xfe02a0ff]
[    0.511220] pci 0000:01:05.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.511224] pci 0000:01:05.0: reg 14 io port: [0xcc00-0xccff]
[    0.511228] pci 0000:01:05.0: reg 18 32bit mmio: [0xfdaf0000-0xfdafffff]
[    0.511237] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.511242] pci 0000:01:05.0: supports D1 D2
[    0.511254] pci 0000:01:05.1: reg 10 32bit mmio: [0xc8000000-0xcfffffff]
[    0.511258] pci 0000:01:05.1: reg 14 32bit mmio: [0xfdae0000-0xfdaeffff]
[    0.511270] pci 0000:01:05.1: supports D1 D2
[    0.511285] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.511288] pci 0000:00:01.0: bridge 32bit mmio: [0xfda00000-0xfdafffff]
[    0.511292] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc8000000-0xd7ffffff]
[    0.511344] pci 0000:02:00.0: reg 10 64bit mmio: [0xfdef0000-0xfdefffff]
[    0.511382] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.511386] pci 0000:02:00.0: PME# disabled
[    0.511444] pci 0000:00:05.0: bridge io port: [0xd000-0xdfff]
[    0.511446] pci 0000:00:05.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.511450] pci 0000:00:05.0: bridge 32bit mmio pref: [0xfdb00000-0xfdbfffff]
[    0.511519] pci 0000:00:14.4: transparent bridge
[    0.511527] pci 0000:00:14.4: bridge io port: [0xb000-0xbfff]
[    0.511532] pci 0000:00:14.4: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.511537] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfdc00000-0xfdcfffff]
[    0.511551] bus 00 -> node 0
[    0.511557] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.511803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.511935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.525681] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.525796] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.525912] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.526025] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.526136] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.526249] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.526359] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.526473] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 10 11)
[    0.526588] ACPI: WMI: Mapper loaded
[    0.526788] SCSI subsystem initialized
[    0.526824] libata version 3.00 loaded.
[    0.526871] usbcore: registered new interface driver usbfs
[    0.526886] usbcore: registered new interface driver hub
[    0.526915] usbcore: registered new device driver usb
[    0.527011] PCI: Using ACPI for IRQ routing
[    0.527021] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.536009] Bluetooth: Core ver 2.13
[    0.536051] NET: Registered protocol family 31
[    0.536052] Bluetooth: HCI device and connection manager initialized
[    0.536056] Bluetooth: HCI socket layer initialized
[    0.536058] NET: Registered protocol family 8
[    0.536060] NET: Registered protocol family 20
[    0.536070] NetLabel: Initializing
[    0.536071] NetLabel:  domain hash size = 128
[    0.536073] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.536088] NetLabel:  unlabeled traffic allowed by default
[    0.536282] AppArmor: AppArmor Filesystem Enabled
[    0.548007] pnp: PnP ACPI init
[    0.548019] ACPI: bus type pnp registered
[    0.550882] pnp 00:0d: mem resource (0xd1800-0xd3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.550886] pnp 00:0d: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.550889] pnp 00:0d: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.550892] pnp 00:0d: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.550895] pnp 00:0d: mem resource (0x1bf00000-0x1bffffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.550899] pnp 00:0d: mem resource (0x1bef0000-0x1befffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.550902] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.550905] pnp 00:0d: mem resource (0x100000-0x1beeffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.550908] pnp 00:0d: mem resource (0x1c000000-0x1fffffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.550966] pnp: PnP ACPI: found 14 devices
[    0.550968] ACPI: ACPI bus type pnp unregistered
[    0.550977] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.550980] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.550982] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.550985] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.550987] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.550989] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.550992] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.550994] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.550997] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.550999] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.551002] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.551008] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.551011] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.551013] system 00:06: ioport range 0x900-0x90f has been reserved
[    0.551020] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.551025] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[    0.551031] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.551034] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.551037] system 00:0d: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.555728] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.555730] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.555734] pci 0000:00:01.0:   MEM window: 0xfda00000-0xfdafffff
[    0.555737] pci 0000:00:01.0:   PREFETCH window: 0x000000c8000000-0x000000d7ffffff
[    0.555741] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
[    0.555743] pci 0000:00:05.0:   IO window: 0xd000-0xdfff
[    0.555746] pci 0000:00:05.0:   MEM window: 0xfde00000-0xfdefffff
[    0.555749] pci 0000:00:05.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.555753] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.555757] pci 0000:00:14.4:   IO window: 0xb000-0xbfff
[    0.555763] pci 0000:00:14.4:   MEM window: 0xfdd00000-0xfddfffff
[    0.555768] pci 0000:00:14.4:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.555783] pci 0000:00:05.0: setting latency timer to 64
[    0.555792] bus: 00 index 0 io port: [0x00-0xffff]
[    0.555794] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.555796] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.555798] bus: 01 index 1 mmio: [0xfda00000-0xfdafffff]
[    0.555800] bus: 01 index 2 mmio: [0xc8000000-0xd7ffffff]
[    0.555802] bus: 01 index 3 mmio: [0x0-0x0]
[    0.555804] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.555806] bus: 02 index 1 mmio: [0xfde00000-0xfdefffff]
[    0.555808] bus: 02 index 2 mmio: [0xfdb00000-0xfdbfffff]
[    0.555810] bus: 02 index 3 mmio: [0x0-0x0]
[    0.555811] bus: 03 index 0 io port: [0xb000-0xbfff]
[    0.555813] bus: 03 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.555815] bus: 03 index 2 mmio: [0xfdc00000-0xfdcfffff]
[    0.555817] bus: 03 index 3 io port: [0x00-0xffff]
[    0.555819] bus: 03 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.555830] NET: Registered protocol family 2
[    0.556024] Switched to high resolution mode on CPU 0
[    0.588064] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.588289] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    0.588435] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.588581] TCP: Hash tables configured (established 16384 bind 16384)
[    0.588583] TCP reno registered
[    0.600104] NET: Registered protocol family 1
[    0.600243] checking if image is initramfs... it is
[    1.258423] Freeing initrd memory: 7765k freed
[    1.264084] audit: initializing netlink socket (disabled)
[    1.264101] type=2000 audit(1242905431.264:1): initialized
[    1.272988] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.274168] VFS: Disk quotas dquot_6.5.1
[    1.274221] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.274781] fuse init (API version 7.10)
[    1.274858] msgmni has been set to 846
[    1.275030] alg: No test for stdrng (krng)
[    1.275042] io scheduler noop registered
[    1.275044] io scheduler anticipatory registered
[    1.275045] io scheduler deadline registered
[    1.275083] io scheduler cfq registered (default)
[    1.275092] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    1.316047] pci 0000:01:05.0: Boot video device
[    1.316126] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.316144] pcieport-driver 0000:00:05.0: found MSI capability
[    1.316147] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.316195] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.316204] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.316332] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.316334] ACPI: Power Button (FF) [PWRF]
[    1.316379] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.316381] ACPI: Power Button (CM) [PWRB]
[    1.316634] processor ACPI_CPU:00: registered as cooling_device0
[    1.318364] thermal LNXTHERM:01: registered as thermal_zone0
[    1.318512] ACPI: Thermal Zone [THRM] (27 C)
[    1.340164] Linux agpgart interface v0.103
[    1.340174] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.340302] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.340609] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.341302] brd: module loaded
[    1.341585] loop: module loaded
[    1.341654] Fixed MDIO Bus: probed
[    1.341660] PPP generic driver version 2.4.2
[    1.341718] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.341746] Driver 'sd' needs updating - please use bus_type methods
[    1.341755] Driver 'sr' needs updating - please use bus_type methods
[    1.341865] sata_sil 0000:00:12.0: version 2.3
[    1.341915] sata_sil 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.342063] scsi0 : sata_sil
[    1.342161] scsi1 : sata_sil
[    1.342276] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 23
[    1.342280] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 23
[    1.660059] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.668505] ata1.00: ATA-7: SAMSUNG SP0411C/R, UU100-05, max UDMA/100
[    1.668508] ata1.00: 78165360 sectors, multi 16: LBA48 
[    1.676513] ata1.00: configured for UDMA/100
[    1.996040] ata2: SATA link down (SStatus 0 SControl 300)
[    1.996077] isa bounce pool size: 16 pages
[    1.996160] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0411C/ UU10 PQ: 0 ANSI: 5
[    1.996254] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    1.996271] sd 0:0:0:0: [sda] Write Protect is off
[    1.996274] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.996299] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.996362] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    1.996376] sd 0:0:0:0: [sda] Write Protect is off
[    1.996379] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.996404] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.996407]  sda: sda1 sda2 < sda5 >
[    2.020839] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.020888] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.021056] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.021194] scsi2 : pata_atiixp
[    2.021250] scsi3 : pata_atiixp
[    2.022114] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[    2.022116] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[    2.200580] ata3.00: ATAPI: HL-DT-ST RW/DVD GCC-4482B, 1.05, max UDMA/44
[    2.200602] ata3.00: limited to UDMA/33 due to 40-wire cable
[    2.232534] ata3.00: configured for UDMA/33
[    2.388718] scsi 2:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4482B 1.05 PQ: 0 ANSI: 5
[    2.390970] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.390973] Uniform CD-ROM driver Revision: 3.20
[    2.391073] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.391117] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.391462] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.391490] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.391511] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.391564] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    2.391646] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02c000
[    2.400029] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.400111] usb usb1: configuration #1 chosen from 1 choice
[    2.400137] hub 1-0:1.0: USB hub found
[    2.400147] hub 1-0:1.0: 8 ports detected
[    2.400274] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.400287] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.400299] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.400342] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.400360] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02e000
[    2.460056] usb usb2: configuration #1 chosen from 1 choice
[    2.460085] hub 2-0:1.0: USB hub found
[    2.460096] hub 2-0:1.0: 4 ports detected
[    2.460182] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.460192] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.460227] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.460243] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02d000
[    2.520056] usb usb3: configuration #1 chosen from 1 choice
[    2.520079] hub 3-0:1.0: USB hub found
[    2.520089] hub 3-0:1.0: 4 ports detected
[    2.520177] uhci_hcd: USB Universal Host Controller Interface driver
[    2.520234] usbcore: registered new interface driver libusual
[    2.520267] usbcore: registered new interface driver usbserial
[    2.520276] USB Serial support registered for generic
[    2.520287] usbcore: registered new interface driver usbserial_generic
[    2.520289] usbserial: USB Serial Driver core
[    2.520331] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.522937] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.522942] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.532044] mice: PS/2 mouse device common for all mice
[    2.568066] rtc_cmos 00:03: RTC can wake from S4
[    2.568104] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.568142] rtc0: alarms up to one month, 242 bytes nvram
[    2.568203] device-mapper: uevent: version 1.0.3
[    2.568315] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.568364] device-mapper: multipath: version 1.0.5 loaded
[    2.568367] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.568442] cpuidle: using governor ladder
[    2.568443] cpuidle: using governor menu
[    2.568877] TCP cubic registered
[    2.568946] NET: Registered protocol family 10
[    2.569332] lo: Disabled Privacy Extensions
[    2.569617] NET: Registered protocol family 17
[    2.569640] Bluetooth: L2CAP ver 2.11
[    2.569641] Bluetooth: L2CAP socket layer initialized
[    2.569644] Bluetooth: SCO (Voice Link) ver 0.6
[    2.569645] Bluetooth: SCO socket layer initialized
[    2.569674] Bluetooth: RFCOMM socket layer initialized
[    2.569680] Bluetooth: RFCOMM TTY layer initialized
[    2.569682] Bluetooth: RFCOMM ver 1.10
[    2.569701] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[    2.569744] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[    2.569746] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[    2.569856] registered taskstats version 1
[    2.569981]   Magic number: 9:215:530
[    2.570071] rtc_cmos 00:03: setting system clock to 2009-05-21 11:30:33 UTC (1242905433)
[    2.570074] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.570076] EDD information not available.
[    2.570108] Freeing unused kernel memory: 536k freed
[    2.570409] Write protecting the kernel read-only data: 6708k
[    2.603023] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.892031] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    3.011760] Floppy drive(s): fd0 is 1.44M
[    3.025730] usb 1-8: configuration #1 chosen from 1 choice
[    3.031668] Initializing USB Mass Storage driver...
[    3.032607] FDC 0 is a post-1991 82077
[    3.037733] scsi4 : SCSI emulation for USB Mass Storage devices
[    3.039809] usbcore: registered new interface driver usb-storage
[    3.039813] USB Mass Storage support registered.
[    3.039918] usb-storage: device found at 4
[    3.039921] usb-storage: waiting for device to settle before scanning
[    3.064616] tg3.c:v3.94 (August 14, 2008)
[    3.064643] tg3 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.064653] tg3 0000:02:00.0: setting latency timer to 64
[    3.085125] eth0: Tigon3 [partno(BCM95751) rev 4200 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:13:d3:b5:24:eb
[    3.085130] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    3.085133] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.320043] usb 3-1: new full speed USB device using ohci_hcd and address 2
[    3.503180] PM: Starting manual resume from disk
[    3.503184] PM: Resume from partition 8:5
[    3.503186] PM: Checking hibernation image.
[    3.503384] PM: Resume from disk failed.
[    3.535998] usb 3-1: configuration #1 chosen from 1 choice
[    3.549355] kjournald starting.  Commit interval 5 seconds
[    3.549375] EXT3-fs: mounted filesystem with ordered data mode.
[    3.840032] usb 3-3: new low speed USB device using ohci_hcd and address 3
[    4.042145] usb 3-3: configuration #1 chosen from 1 choice
[    8.036254] usb-storage: device scan complete
[    8.036721] scsi 4:0:0:0: Direct-Access     WD       1600BEV External 1.04 PQ: 0 ANSI: 4
[    8.037703] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    8.038575] sd 4:0:0:0: [sdb] Write Protect is off
[    8.038578] sd 4:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    8.038580] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    8.039202] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    8.039945] sd 4:0:0:0: [sdb] Write Protect is off
[    8.039947] sd 4:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    8.039949] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    8.039952]  sdb: sdb1 sdb2
[    8.040703] sd 4:0:0:0: [sdb] Attached SCSI disk
[    8.040767] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   10.136930] udev: starting version 141
[   10.480543] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.547374] parport_pc 00:09: reported by Plug and Play ACPI
[   10.547457] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   10.593325] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x500, revision 0
[   10.680686] usbcore: registered new interface driver hiddev
[   10.685510] input: HID 04b3:3108 as /devices/pci0000:00/0000:00:13.1/usb3/3-3/3-3:1.0/input/input4
[   10.705694] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   10.720260] generic-usb 0003:04B3:3108.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:3108] on usb-0000:00:13.1-3/input0
[   10.720285] usbcore: registered new interface driver usbhid
[   10.720307] usbhid: v2.6:USB HID core driver
[   11.092308] ppdev: user-space parallel port driver
[   11.141209] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2F11
[   11.141236] usbcore: registered new interface driver usblp
[   11.681219] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.888258] lp0: using parport0 (interrupt-driven).
[   11.987222] Adding 1261060k swap on /dev/sda5.  Priority:-1 extents:1 across:1261060k
[   12.537886] EXT3 FS on sda1, internal journal
[   13.692070] type=1505 audit(1242905444.621:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1951
[   13.745915] type=1505 audit(1242905444.673:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1955
[   13.746084] type=1505 audit(1242905444.673:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1955
[   13.746135] type=1505 audit(1242905444.673:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1955
[   13.746180] type=1505 audit(1242905444.673:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1955
[   13.894998] type=1505 audit(1242905444.821:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1960
[   13.895210] type=1505 audit(1242905444.821:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1960
[   13.929477] type=1505 audit(1242905444.857:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1964
[   17.866503] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.866508] Bluetooth: BNEP filters: protocol multicast
[   18.662036] Bridge firewalling registered
[   20.145732] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.334580] [drm] Initialized drm 1.1.0 20060810
[   21.099227] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   21.580972] [drm] Setting GART location based on new memory map
[   21.581658] [drm] Loading R300 Microcode
[   21.581715] [drm] Num pipes: 3
[   21.581721] [drm] writeback test succeeded in 1 usecs
[   23.929423] ppdev0: registered pardevice
[   23.976220] ppdev0: unregistered pardevice
[   25.134660] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.710294] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   26.710298] tg3: eth0: Flow control is off for TX and off for RX.
[   26.710349] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   37.428019] eth0: no IPv6 routers present
[   44.058038] EXT4-fs: barriers enabled
[   44.078396] kjournald2 starting.  Commit interval 5 seconds
[   44.078414] EXT4-fs warning: maximal mount count reached, running e2fsck is recommended
[   44.081481] EXT4 FS on sdb1, internal journal on sdb1:8
[   44.081485] EXT4-fs: delayed allocation enabled
[   44.081486] EXT4-fs: file extents enabled
[   44.097581] EXT4-fs: mballoc enabled
[   44.097591] EXT4-fs: mounted filesystem with ordered data mode.
[   44.151423] EXT4-fs: barriers enabled
[   44.180160] kjournald2 starting.  Commit interval 5 seconds
[   44.180792] EXT4 FS on sdb2, internal journal on sdb2:8
[   44.180794] EXT4-fs: delayed allocation enabled
[   44.180796] EXT4-fs: file extents enabled
[   44.197638] EXT4-fs: mballoc enabled
[   44.197718] EXT4-fs: mounted filesystem with ordered data mode.
[   83.052043] Clocksource tsc unstable (delta = -104884824 ns)
[39353.456051] usb 1-7: new high speed USB device using ehci_hcd and address 5
[39353.592703] usb 1-7: configuration #1 chosen from 1 choice
[39353.593380] scsi5 : SCSI emulation for USB Mass Storage devices
[39353.593710] usb-storage: device found at 5
[39353.593713] usb-storage: waiting for device to settle before scanning
[39358.593037] usb-storage: device scan complete
[39358.594666] scsi 5:0:0:0: Direct-Access     Lexar    JD Secure II +   1100 PQ: 0 ANSI: 0 CCS
[39358.740801] sd 5:0:0:0: [sdc] 1966080 512-byte hardware sectors: (1.00 GB/960 MiB)
[39358.741634] sd 5:0:0:0: [sdc] Write Protect is off
[39358.741639] sd 5:0:0:0: [sdc] Mode Sense: 43 00 00 00
[39358.741643] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[39358.749036] sd 5:0:0:0: [sdc] 1966080 512-byte hardware sectors: (1.00 GB/960 MiB)
[39358.749882] sd 5:0:0:0: [sdc] Write Protect is off
[39358.749887] sd 5:0:0:0: [sdc] Mode Sense: 43 00 00 00
[39358.749891] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[39358.749901]  sdc: sdc1
[39358.750868] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[39358.751195] sd 5:0:0:0: Attached scsi generic sg3 type 0
[43431.122182] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[43431.122190] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[43431.122194] EXT4-fs: mballoc: 0 generated and it took 0
[43431.122198] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[43436.363255] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[43436.363261] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[43436.363266] EXT4-fs: mballoc: 0 generated and it took 0
[43436.363269] EXT4-fs: mballoc: 0 preallocated, 0 discarded
allen@allen-desktop:~$

---

### Post by geirha on 2009-05-21
Did you try any of the programs listed in my previous link? Try this for instance. [http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

---

