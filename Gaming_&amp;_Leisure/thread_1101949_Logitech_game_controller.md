---
title: "Logitech game controller"
date: 2009-03-20
forum: Gaming &amp; Leisure
---

### Post by AndyP79 on 2009-03-20
Hi All,
 I have a Logitech Precision controller that I picked up for $20. But no luck with it. My laptop does not see it. I downloaded an emulator and a few games from days long gone, and really want to use the game controller. Do I have to get a driver or mount it or some other thing to make it work, or certain controller? Please keep in mind I am still fresh to Mint, and Linux, and these are simple games from a LONG time ago, no need fro a crazy controller.

Thanks

---

### Post by AndyP79 on 2009-03-20
By the way, I am looking at the SNES conrollers on amazon, and they have a usb adapter, do these work, or do I have to add a driver or something still?

---

### Post by hikaricore on 2009-03-20
Unplug the controller, plug it back in, then run:

> dmesg

From a terminal and post the output.
I can almost guarantee that Linux sees the device, you may just have to use one of the various joystick cli tools to set it up properly.
Personally I've never had this issue and I bought a generic piece of crap controller.

---

### Post by AndyP79 on 2009-03-20
Okay, I ran what you said, but, uh...okay, here it is, it's REALLY long......


[    0.593652] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    0.593787] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.593922] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.594059] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.594197] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.594339] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.594475] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.594848] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.594890] pnp: PnP ACPI init
[    0.594901] ACPI: bus type pnp registered
[    0.616561] pnp 00:06: io resource (0x2e-0x2f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.616565] pnp 00:06: io resource (0x61-0x61) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.616569] pnp 00:06: io resource (0x63-0x63) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.616573] pnp 00:06: io resource (0x65-0x65) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.616577] pnp 00:06: io resource (0x67-0x67) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.616581] pnp 00:06: io resource (0x70-0x70) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.616585] pnp 00:06: io resource (0x80-0x80) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.616589] pnp 00:06: io resource (0x92-0x92) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.616593] pnp 00:06: io resource (0xb2-0xb3) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.616597] pnp 00:06: io resource (0x800-0x80f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.616602] pnp 00:06: io resource (0x2e-0x2f) overlaps 0000:00:1c.2 BAR 7 (0x0-0xfff), disabling
[    0.616606] pnp 00:06: io resource (0x61-0x61) overlaps 0000:00:1c.2 BAR 7 (0x0-0xfff), disabling
[    0.616610] pnp 00:06: io resource (0x63-0x63) overlaps 0000:00:1c.2 BAR 7 (0x0-0xfff), disabling
[    0.616614] pnp 00:06: io resource (0x65-0x65) overlaps 0000:00:1c.2 BAR 7 (0x0-0xfff), disabling
[    0.616618] pnp 00:06: io resource (0x67-0x67) overlaps 0000:00:1c.2 BAR 7 (0x0-0xfff), disabling
[    0.616622] pnp 00:06: io resource (0x70-0x70) overlaps 0000:00:1c.2 BAR 7 (0x0-0xfff), disabling
[    0.616626] pnp 00:06: io resource (0x80-0x80) overlaps 0000:00:1c.2 BAR 7 (0x0-0xfff), disabling
[    0.616630] pnp 00:06: io resource (0x92-0x92) overlaps 0000:00:1c.2 BAR 7 (0x0-0xfff), disabling
[    0.616634] pnp 00:06: io resource (0xb2-0xb3) overlaps 0000:00:1c.2 BAR 7 (0x0-0xfff), disabling
[    0.616638] pnp 00:06: io resource (0x800-0x80f) overlaps 0000:00:1c.2 BAR 7 (0x0-0xfff), disabling
[    0.616970] pnp: PnP ACPI: found 10 devices
[    0.616973] ACPI: ACPI bus type pnp unregistered
[    0.616977] PnPBIOS: Disabled by ACPI PNP
[    0.617385] PCI: Using ACPI for IRQ routing
[    0.617391] pci 0000:00:1c.0: BAR 7: can't allocate resource
[    0.617394] pci 0000:00:1c.0: BAR 8: can't allocate resource
[    0.617396] pci 0000:00:1c.2: BAR 7: can't allocate resource
[    0.617399] pci 0000:00:1c.2: BAR 8: can't allocate resource
[    0.617444] pci 0000:06:00.0: BAR 0: can't allocate resource
[    0.617548] NET: Registered protocol family 8
[    0.617548] NET: Registered protocol family 20
[    0.617548] NetLabel: Initializing
[    0.617548] NetLabel:  domain hash size = 128
[    0.617548] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.617548] NetLabel:  unlabeled traffic allowed by default
[    0.617548] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.617548] hpet0: 3 64-bit timers, 14318180 Hz
[    0.617710] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.617713]    actual entries 65620
[    0.617828] AppArmor: AppArmor Filesystem Enabled
[    0.617861] ACPI: RTC can wake from S4
[    0.617873] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.617873] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.617873] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.617873] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.617873] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.617873] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    0.617873] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[    0.617873] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    0.617873] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    0.617873] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.617873] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.617873] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.620049] Switched to high resolution mode on CPU 0
[    0.654686] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.654689] pci 0000:00:1c.0:   IO window: disabled
[    0.654697] pci 0000:00:1c.0:   MEM window: disabled
[    0.654702] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.654725] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.654727] pci 0000:00:1c.2:   IO window: disabled
[    0.654734] pci 0000:00:1c.2:   MEM window: 0x68000000-0x680fffff
[    0.654739] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.654748] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.654752] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.654759] pci 0000:00:1e.0:   MEM window: 0xd0100000-0xd01fffff
[    0.654765] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.654787] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.654795] pci 0000:00:1c.0: setting latency timer to 64
[    0.654804] pci 0000:00:1c.2: enabling device (0100 -> 0102)
[    0.654811] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.654819] pci 0000:00:1c.2: setting latency timer to 64
[    0.654828] pci 0000:00:1e.0: setting latency timer to 64
[    0.654832] bus: 00 index 0 io port: [0, ffff]
[    0.654835] bus: 00 index 1 mmio: [0, ffffffff]
[    0.654838] bus: 01 index 0 mmio: [0, fff]
[    0.654840] bus: 01 index 1 mmio: [0, fffff]
[    0.654842] bus: 01 index 2 mmio: [0, 0]
[    0.654844] bus: 01 index 3 mmio: [0, 0]
[    0.654847] bus: 06 index 0 mmio: [0, fff]
[    0.654849] bus: 06 index 1 mmio: [68000000, 680fffff]
[    0.654852] bus: 06 index 2 mmio: [0, 0]
[    0.654854] bus: 06 index 3 mmio: [0, 0]
[    0.654856] bus: 08 index 0 io port: [2000, 2fff]
[    0.654859] bus: 08 index 1 mmio: [d0100000, d01fffff]
[    0.654861] bus: 08 index 2 mmio: [0, 0]
[    0.654864] bus: 08 index 3 io port: [0, ffff]
[    0.654866] bus: 08 index 4 mmio: [0, ffffffff]
[    0.654878] NET: Registered protocol family 2
[    0.655025] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.655306] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.656148] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.656632] TCP: Hash tables configured (established 131072 bind 65536)
[    0.656637] TCP reno registered
[    0.656818] NET: Registered protocol family 1
[    0.656963] checking if image is initramfs... it is
[    1.511698] Freeing initrd memory: 8711k freed
[    1.511926] Simple Boot Flag at 0x36 set to 0x1
[    1.512676] audit: initializing netlink socket (disabled)
[    1.512695] type=2000 audit(1237493697.512:1): initialized
[    1.519888] highmem bounce pool size: 64 pages
[    1.519896] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.522626] VFS: Disk quotas dquot_6.5.1
[    1.522736] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.522855] msgmni has been set to 1753
[    1.523003] io scheduler noop registered
[    1.523007] io scheduler anticipatory registered
[    1.523010] io scheduler deadline registered
[    1.523025] io scheduler cfq registered (default)
[    1.523043] pci 0000:00:02.0: Boot video device
[    9.520009] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    9.520162] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    9.520213] pcieport-driver 0000:00:1c.0: found MSI capability
[    9.520266] pci_express 0000:00:1c.0:pcie00: allocate port service
[    9.520316] pci_express 0000:00:1c.0:pcie02: allocate port service
[    9.520362] pci_express 0000:00:1c.0:pcie03: allocate port service
[    9.520482] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    9.520531] pcieport-driver 0000:00:1c.2: found MSI capability
[    9.520579] pci_express 0000:00:1c.2:pcie00: allocate port service
[    9.520625] pci_express 0000:00:1c.2:pcie02: allocate port service
[    9.520671] pci_express 0000:00:1c.2:pcie03: allocate port service
[    9.521042] isapnp: Scanning for PnP cards...
[    9.874965] isapnp: No Plug & Play device found
[    9.917839] hpet_resources: 0xfed00000 is busy
[    9.917926] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    9.920912] brd: module loaded
[    9.920997] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    9.921137] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.942918] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.942925] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.943311] mice: PS/2 mouse device common for all mice
[    9.944416] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    9.944449] rtc0: alarms up to one month, y3k, hpet irqs
[    9.944584] EISA: Probing bus 0 at eisa.0
[    9.944593] Cannot allocate resource for EISA slot 1
[    9.944596] Cannot allocate resource for EISA slot 2
[    9.944623] EISA: Detected 0 cards.
[    9.944627] cpuidle: using governor ladder
[    9.944629] cpuidle: using governor menu
[    9.945189] TCP cubic registered
[    9.945223] Using IPI No-Shortcut mode
[    9.945465] registered taskstats version 1
[    9.945580]   Magic number: 1:698:245
[    9.945618] tty ttyw1: hash matches
[    9.945772] rtc_cmos 00:09: setting system clock to 2009-03-19 20:15:07 UTC (1237493707)
[    9.945776] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.945779] EDD information not available.
[    9.946035] Freeing unused kernel memory: 424k freed
[    9.946091] Write protecting the kernel text: 2576k
[    9.946129] Write protecting the kernel read-only data: 936k
[    9.961518] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   10.193095] fuse init (API version 7.9)
[   10.476176] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.480214] processor ACPI0007:00: registered as cooling_device0
[   10.480219] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.490626] Marking TSC unstable due to TSC halts in idle
[   10.493883] thermal LNXTHERM:01: registered as thermal_zone0
[   10.510299] ACPI: Thermal Zone [TZ01] (66 C)
[   10.510477] thermal LNXTHERM:02: registered as thermal_zone1
[   10.510588] ACPI: Thermal Zone [TZ02] (27 C)
[   11.151289] b43-pci-bridge 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.151310] b43-pci-bridge 0000:06:00.0: setting latency timer to 64
[   11.216197] ssb: Sonics Silicon Backplane found on PCI device 0000:06:00.0
[   11.243406] usbcore: registered new interface driver usbfs
[   11.243436] usbcore: registered new interface driver hub
[   11.243501] usbcore: registered new device driver usb
[   11.249210] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   11.249227] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   11.249231] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   11.249283] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1

---

### Post by AndyP79 on 2009-03-20
Here's the second part.....


[   11.253198] ehci_hcd 0000:00:1d.7: debug port 1
[   11.253206] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   11.253221] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0544000
[   11.267497] USB Universal Host Controller Interface driver v3.0
[   11.273226] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.273445] usb usb1: configuration #1 chosen from 1 choice
[   11.273477] hub 1-0:1.0: USB hub found
[   11.273488] hub 1-0:1.0: 6 ports detected
[   11.273706] No dock devices found.
[   11.334894] SCSI subsystem initialized
[   11.338167] 8139too Fast Ethernet driver 0.9.28
[   11.402055] libata version 3.00 loaded.
[   11.480565] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   11.480578] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   11.480583] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.480613] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   11.480644] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[   11.480759] usb usb2: configuration #1 chosen from 1 choice
[   11.480789] hub 2-0:1.0: USB hub found
[   11.480797] hub 2-0:1.0: 2 ports detected
[   11.592039] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   11.688346] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   11.688359] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   11.688363] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.688393] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   11.688433] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   11.688549] usb usb3: configuration #1 chosen from 1 choice
[   11.688583] hub 3-0:1.0: USB hub found
[   11.688593] hub 3-0:1.0: 2 ports detected
[   11.745573] usb 1-1: configuration #1 chosen from 1 choice
[   11.896371] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   11.896384] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   11.896389] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.896419] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   11.896461] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   11.896584] usb usb4: configuration #1 chosen from 1 choice
[   11.896615] hub 4-0:1.0: USB hub found
[   11.896624] hub 4-0:1.0: 2 ports detected
[   12.008045] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   12.104440] ata_piix 0000:00:1f.1: version 2.12
[   12.104457] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   12.104502] ata_piix 0000:00:1f.1: setting latency timer to 64
[   12.104947] scsi0 : ata_piix
[   12.105354] scsi1 : ata_piix
[   12.106072] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   12.106076] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   12.185855] usb 3-2: configuration #1 chosen from 1 choice
[   12.284566] ata1.00: ATAPI: TSSTcorpCDW/DVD TS-L462D, HS02, max MWDMA2
[   12.300056] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   12.332439] ata1.00: configured for MWDMA2
[   12.332488] ata2: port disabled. ignoring.
[   12.360499] scsi 0:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462D HS02 PQ: 0 ANSI: 5
[   12.360636] ahci 0000:00:1f.2: version 3.0
[   12.360653] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   12.360771] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x1 impl SATA mode
[   12.360775] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   12.360781] ahci 0000:00:1f.2: setting latency timer to 64
[   12.361471] scsi2 : ahci
[   12.361917] scsi3 : ahci
[   12.362366] scsi4 : ahci
[   12.362846] scsi5 : ahci
[   12.362969] ata3: SATA max UDMA/133 abar m1024@0xd0544400 port 0xd0544500 irq 221
[   12.362973] ata4: DUMMY
[   12.362974] ata5: DUMMY
[   12.362976] ata6: DUMMY
[   12.477974] usb 4-2: configuration #1 chosen from 1 choice
[   12.491052] usbcore: registered new interface driver libusual
[   12.499076] Initializing USB Mass Storage driver...
[   12.499720] scsi6 : SCSI emulation for USB Mass Storage devices
[   12.499872] usbcore: registered new interface driver usb-storage
[   12.499876] USB Mass Storage support registered.
[   12.499995] usb-storage: device found at 2
[   12.499998] usb-storage: waiting for device to settle before scanning
[   12.500026] Clocksource tsc unstable (delta = -338192905 ns)
[   12.511433] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[   12.680072] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   12.681110] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
, 3.BHD, max UDMA/1000: ATA-7: ST980812AS
[   12.681121] ata3.00: 156301488 sectors, multi 16: LBA48 
[   12.682305] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   12.682319] ata3.00: configured for UDMA/100
[   12.696226] scsi 2:0:0:0: Direct-Access     ATA      ST980812AS       3.BH PQ: 0 ANSI: 5
[   12.696430] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   12.697326] 8139too 0000:08:08.0: enabling device (0105 -> 0107)
[   12.697340] 8139too 0000:08:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.698397] eth0: RealTek RTL8139 at 0x2000, 00:16:d4:bd:29:87, IRQ 16
[   12.698400] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   12.706079] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   12.825586] usbcore: registered new interface driver hiddev
[   12.836598] Driver 'sr' needs updating - please use bus_type methods
[   12.839987] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input2
[   12.852218] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   12.867378] Driver 'sd' needs updating - please use bus_type methods
[   12.880508] Fixing up Logitech keyboard report descriptor
[   12.881662] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input3
[   12.882160] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   12.896872] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input4
[   12.897232] input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2
[   12.910671] hiddev97hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-2
[   12.910696] usbcore: registered new interface driver usbhid
[   12.910701] usbhid: v2.6:USB HID core driver
[   12.933296] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   12.933303] Uniform CD-ROM driver Revision: 3.20
[   12.933412] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   12.940948] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   12.940988] sd 2:0:0:0: [sda] Write Protect is off
[   12.940992] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.941036] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.941136] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   12.941159] sd 2:0:0:0: [sda] Write Protect is off
[   12.941163] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.941205] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.941211]  sda: sda1 sda2 < sda5 sda6 sda7 >
[   12.999209] sd 2:0:0:0: [sda] Attached SCSI disk
[   13.331841] PM: Starting manual resume from disk
[   13.331846] PM: Resume from partition 8:7
[   13.331848] PM: Checking hibernation image.
[   13.331981] PM: Resume from disk failed.
[   13.386851] kjournald starting.  Commit interval 5 seconds
[   13.386869] EXT3-fs: mounted filesystem with ordered data mode.
[   17.500213] usb-storage: device scan complete
[   17.503558] scsi 6:0:0:0: Direct-Access     TOSHIBA  MK2555GSX             PQ: 0 ANSI: 2
[   17.504790] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   17.507039] sd 6:0:0:0: [sdb] Write Protect is off
[   17.507043] sd 6:0:0:0: [sdb] Mode Sense: 38 00 00 00
[   17.507046] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   17.508040] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   17.510283] sd 6:0:0:0: [sdb] Write Protect is off
[   17.510286] sd 6:0:0:0: [sdb] Mode Sense: 38 00 00 00
[   17.510289] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   17.510293]  sdb: sdb1
[   18.858699] sd 6:0:0:0: [sdb] Attached SCSI disk
[   18.858870] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   21.081719] udevd version 124 started
[   21.826112] Linux agpgart interface v0.103
[   21.905086] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.967618] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.026025] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   22.026231] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   22.058542] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   22.456722] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   22.472073] ACPI: Power Button (FF) [PWRF]
[   22.472118] ACPI Error (evxfevnt-0186): Could not enable SleepButton event [20080609]
[   22.472123] ACPI Warning (evxface-0145): Could not enable fixed event 3 [20080609]
[   22.472280] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input6
[   22.472360] ACPI: Lid Switch [LID]
[   22.472457] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input7
[   22.488036] ACPI: Power Button (CM) [PWRB]
[   22.667473] ACPI: WMI: Mapper loaded
[   22.891159] ieee80211_crypt: registered algorithm 'NULL'
[   22.894756] wl: module license 'MIXED/Proprietary' taints kernel.
[   23.462256] acpi device:03: registered as cooling_device1
[   23.462445] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input8
[   23.472038] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   23.501463] acpi device:07: registered as cooling_device2
[   23.501650] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/input/input9
[   23.518740] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   23.526417] ACPI: AC Adapter [ACAD] (on-line)
[   23.743467] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   23.743502] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.078640] ACPI: Battery Slot [BAT1] (battery present)
[   24.431528] b43-phy0: Broadcom 4311 WLAN found
[   24.523650] phy0: Selected rate control algorithm 'pid'
[   25.021944] iTCO_vendor_support: vendor-support=0
[   25.053194] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   25.053339] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   25.053519] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.139650] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   25.182295] intel_rng: FWH not detected
[   25.753273] input: PC Speaker as /devices/platform/pcspkr/input/input10
[   26.760903] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   26.824186] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   29.099482] lp: driver loaded but no devices found
[   29.371580] Adding 1614492k swap on /dev/sda7.  Priority:-1 extents:1 across:1614492k
[   29.929889] EXT3 FS on sda6, internal journal
[   31.101857] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.915631] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   33.020502] apm: BIOS not found.
[   33.222574] ppdev: user-space parallel port driver
[   36.535812] Bluetooth: Core ver 2.13
[   36.538622] NET: Registered protocol family 31
[   36.538629] Bluetooth: HCI device and connection manager initialized
[   36.538634] Bluetooth: HCI socket layer initialized
[   36.566422] Bluetooth: L2CAP ver 2.11
[   36.566429] Bluetooth: L2CAP socket layer initialized
[   36.581432] Bluetooth: SCO (Voice Link) ver 0.6
[   36.581441] Bluetooth: SCO socket layer initialized
[   36.599304] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.599312] Bluetooth: BNEP filters: protocol multicast
[   36.615924] Bluetooth: RFCOMM socket layer initialized
[   36.616252] Bluetooth: RFCOMM TTY layer initialized
[   36.616262] Bluetooth: RFCOMM ver 1.10
[   36.656664] Bridge firewalling registered
[   36.658207] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   40.724363] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   40.768289] input: b43-phy0 as /devices/virtual/input/input12
[   40.852186] [drm] Initialized drm 1.1.0 20060810
[   40.864128] firmware: requesting b43/ucode5.fw
[   40.873537] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   40.873548] pci 0000:00:02.0: setting latency timer to 64
[   40.876666] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   40.913233] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   40.913248] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   41.038494] input: b43-phy0 as /devices/virtual/input/input13
[   41.096082] firmware: requesting b43/ucode5.fw
[   41.099441] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   41.099453] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   41.228564] NET: Registered protocol family 17
[ 1802.764583] Buffer I/O error on device sr0, logical block 0
[ 1802.764599] Buffer I/O error on device sr0, logical block 1
[ 1802.764602] Buffer I/O error on device sr0, logical block 2
[ 1802.764605] Buffer I/O error on device sr0, logical block 3
[ 1802.764608] Buffer I/O error on device sr0, logical block 4
[ 1802.764611] Buffer I/O error on device sr0, logical block 5
[ 1802.764614] Buffer I/O error on device sr0, logical block 6
[ 1802.764618] Buffer I/O error on device sr0, logical block 7
[ 1802.764621] Buffer I/O error on device sr0, logical block 8
[ 1802.764625] Buffer I/O error on device sr0, logical block 9
[ 4417.256645] __ratelimit: 30 callbacks suppressed
[ 4417.256656] Buffer I/O error on device sr0, logical block 0
[ 4417.256661] Buffer I/O error on device sr0, logical block 1
[ 4417.256665] Buffer I/O error on device sr0, logical block 2
[ 4417.256668] Buffer I/O error on device sr0, logical block 3
[ 4417.256671] Buffer I/O error on device sr0, logical block 4
[ 4417.256674] Buffer I/O error on device sr0, logical block 5
[ 4417.256677] Buffer I/O error on device sr0, logical block 6
[ 4417.256680] Buffer I/O error on device sr0, logical block 7
[ 4417.256684] Buffer I/O error on device sr0, logical block 8
[ 4417.256687] Buffer I/O error on device sr0, logical block 9
[17052.675468] __ratelimit: 30 callbacks suppressed
[17052.675479] npviewer.bin[1516]: segfault at ff9bea2c ip ff9bea2c sp bfd7874c error 4
[17101.512626] npviewer.bin[1534]: segfault at 4046d366 ip 08051544 sp bf8e8128 error 4 in npviewer.bin[8048000+1a000]
[71197.730923] npviewer.bin[25748]: segfault at ff9bea2c ip ff9bea2c sp bfea116c error 4
[71510.448821] npviewer.bin[26084]: segfault at ff9bea2c ip ff9bea2c sp bf9edcbc error 4
[110264.688078] usb 4-2: USB disconnect, address 2
[110268.632055] usb 4-2: new low speed USB device using uhci_hcd and address 3
[110268.838629] usb 4-2: configuration #1 chosen from 1 choice
[110268.859685] input: Logitech Logitech(R) Precision(TM) Gamepad as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input14
[110268.888276] input,hidraw2: USB HID v1.10 Joystick [Logitech Logitech(R) Precision(TM) Gamepad] on usb-0000:00:1d.2-2
[110277.584085] usb 4-2: USB disconnect, address 3
[110283.208047] usb 4-2: new low speed USB device using uhci_hcd and address 4
[110283.412563] usb 4-2: configuration #1 chosen from 1 choice
[110283.450519] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input15
[110283.472278] input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2
[110283.486358] hiddev97hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-2
[111723.672111] usb 4-2: USB disconnect, address 4
[111728.120063] usb 4-2: new low speed USB device using uhci_hcd and address 5
[111728.304428] usb 4-2: configuration #1 chosen from 1 choice
[111728.329324] input: Logitech Logitech(R) Precision(TM) Gamepad as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input16
[111728.356188] input,hidraw2: USB HID v1.10 Joystick [Logitech Logitech(R) Precision(TM) Gamepad] on usb-0000:00:1d.2-2

---

### Post by AndyP79 on 2009-03-21
Hi All,
 Okay, I am on my second controller now. First I used a Logitech Precision, didn't work, no response. Now I got a brand new Logitech Dual Action Controller. Still nothing. 

I saw a forum,  where the guy was having problems, then it seemed it turned out to be a problem with the game, could it be the ZSNES emulator that i am using? the game works fine with keypad, but that is a sure way to die quickly, right! 

I posted on here earlier for the last controller, but I lost who ever it was that responded.....maybe Saturday more people are around??

Thanks

---

### Post by hikaricore on 2009-03-21
Please do not make duplicate threads.

> 111728.329324] input: Logitech Logitech(R) Precision(TM) Gamepad as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input16
[111728.356188] input,hidraw2: USB HID v1.10 Joystick [Logitech Logitech(R) Precision(TM) Gamepad] on usb-0000:00:1d.2-2

Your controller is obviously being detected so the problem likely lies within whatever game/emu you're trying to configure it in.
Perhaps if you provide info about the program your controller doesn't work with someone can help you.

---

### Post by AndyP79 on 2009-03-21
> **hikaricore said:**
> Please do not make duplicate threads.



Your controller is obviously being detected so the problem likely lies within whatever game/emu you're trying to configure it in.
Perhaps if you provide info about the program your controller doesn't work with someone can help you.



Sorry, still new to this. Okay, I have been using ZSNES emulator. I am trying to run Super Mario World on it.

---

### Post by hikaricore on 2009-03-21
And when you go into configure the controls for a gamepad in zsnes, click on the button you wish to set, and press said button, nothing happens?

You should also run zsnes from a terminal if i recall it shows info about connected controllers at startup in the terminal output.

---

### Post by AndyP79 on 2009-03-21
AHHHH!!! Okay, I did not know I had to configure buttons in ZSNES! HAHA!! I feel like a dork. Let me try that then I will post what I get out of it.

---

### Post by AndyP79 on 2009-03-21
> **hikaricore said:**
> And when you go into configure the controls for a gamepad in zsnes, click on the button you wish to set, and press said button, nothing happens?

You should also run zsnes from a terminal if i recall it shows info about connected controllers at startup in the terminal output.



Bada Bing Bada Boom!! Thank You. This worked, and I am playing my games now.

---

### Post by hikaricore on 2009-03-21
Rock on, glad to help.  ^_^

---

