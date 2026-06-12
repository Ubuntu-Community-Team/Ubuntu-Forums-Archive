---
title: "Strange one this! I have to hold down a key for Ubuntu to boot...."
date: 2008-12-16
forum: General Help
---

### Post by SteveGodfrey on 2008-12-16
I have a Pavilion laptop which worked fine with 8.04. I upgraded to 8.10 when it was released, the upgrade went fine however when I rebooted the PC the 'throbber' stopped and won't progress until I pressed a button. In order for Ubuntu to load up fully I have to hold down a key, it doesn't matter which one!

I assumed this was a funny from performing an upgrade so today did a fresh install of 8.10 but still have the same problem.

Any suggestions where I can look to find the cause of this?

I've attached DMESG following a reboot.

[    0.545012] PCI: 0000:02:05.0 reg 10 32bit mmio: [0, 7ff]
[    0.545043] pci 0000:02:05.0: supports D1
[    0.545045] pci 0000:02:05.0: supports D2
[    0.545048] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545052] pci 0000:02:05.0: PME# disabled
[    0.545073] PCI: 0000:02:05.1 reg 10 32bit mmio: [f6100800, f61008ff]
[    0.545104] pci 0000:02:05.1: supports D1
[    0.545106] pci 0000:02:05.1: supports D2
[    0.545108] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545112] pci 0000:02:05.1: PME# disabled
[    0.545133] PCI: 0000:02:05.2 reg 10 32bit mmio: [f6100c00, f6100cff]
[    0.545164] pci 0000:02:05.2: supports D1
[    0.545166] pci 0000:02:05.2: supports D2
[    0.545169] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545173] pci 0000:02:05.2: PME# disabled
[    0.545194] PCI: 0000:02:05.3 reg 10 32bit mmio: [f6101000, f61010ff]
[    0.545225] pci 0000:02:05.3: supports D1
[    0.545227] pci 0000:02:05.3: supports D2
[    0.545230] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545234] pci 0000:02:05.3: PME# disabled
[    0.545255] PCI: 0000:02:05.4 reg 10 32bit mmio: [f6101400, f61014ff]
[    0.545286] pci 0000:02:05.4: supports D1
[    0.545288] pci 0000:02:05.4: supports D2
[    0.545290] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545294] pci 0000:02:05.4: PME# disabled
[    0.545323] pci 0000:00:08.0: transparent bridge
[    0.545328] PCI: bridge 0000:00:08.0 32bit mmio: [f6100000, f61fffff]
[    0.545365] PCI: bridge 0000:00:0c.0 io port: [4000, 4fff]
[    0.545368] PCI: bridge 0000:00:0c.0 32bit mmio: [f2000000, f3ffffff]
[    0.545373] PCI: bridge 0000:00:0c.0 64bit mmio pref: [f0000000, f1ffffff]
[    0.545412] PCI: 0000:03:00.0 reg 10 64bit mmio: [f6000000, f6003fff]
[    0.545451] pci 0000:03:00.0: supports D1
[    0.545453] pci 0000:03:00.0: supports D2
[    0.545486] PCI: bridge 0000:00:0d.0 32bit mmio: [f6000000, f60fffff]
[    0.545496] bus 00 -> node 0
[    0.545504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.545621] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.545650] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.545692] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.590007] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.590007] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.590007] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.590007] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.590007] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.592260] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.592540] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.592819] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.593098] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.593377] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.593656] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.593936] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.594215] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.594494] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.594773] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.595054] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.595333] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.595612] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.595891] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.596156] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.596171] pnp: PnP ACPI init
[    0.596171] ACPI: bus type pnp registered
[    0.600437] pnp: PnP ACPI: found 12 devices
[    0.600441] ACPI: ACPI bus type pnp unregistered
[    0.600446] PnPBIOS: Disabled by ACPI PNP
[    0.600480] PCI: Using ACPI for IRQ routing
[    0.604046] NET: Registered protocol family 8
[    0.604049] NET: Registered protocol family 20
[    0.608041] NetLabel: Initializing
[    0.608041] NetLabel:  domain hash size = 128
[    0.608041] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.608056] NetLabel:  unlabeled traffic allowed by default
[    0.608064] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.608070] hpet0: 3 32-bit timers, 25000000 Hz
[    0.609654] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.609656]    actual entries 65620
[    0.609792] AppArmor: AppArmor Filesystem Enabled
[    0.609822] ACPI: RTC can wake from S4
[    0.612051] Switched to high resolution mode on CPU 0
[    0.612065] Switched to high resolution mode on CPU 1
[    0.612100] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.612109] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.612113] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.612116] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.612119] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.612123] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.612126] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.612134] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.612137] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.612150] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.612154] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.612158] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.612161] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.612165] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.647523] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.647526] pci 0000:00:08.0:   IO window: disabled
[    0.647531] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.647535] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.647540] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.647543] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.647547] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.647550] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.647555] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.647558] pci 0000:00:0d.0:   IO window: disabled
[    0.647562] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.647565] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.647575] pci 0000:00:08.0: setting latency timer to 64
[    0.647582] pci 0000:00:0c.0: setting latency timer to 64
[    0.647588] pci 0000:00:0d.0: setting latency timer to 64
[    0.647592] bus: 00 index 0 io port: [0, ffff]
[    0.647595] bus: 00 index 1 mmio: [0, ffffffff]
[    0.647597] bus: 02 index 0 mmio: [0, 0]
[    0.647600] bus: 02 index 1 mmio: [f6100000, f61fffff]
[    0.647602] bus: 02 index 2 mmio: [0, 0]
[    0.647605] bus: 02 index 3 io port: [0, ffff]
[    0.647607] bus: 02 index 4 mmio: [0, ffffffff]
[    0.647610] bus: 04 index 0 io port: [4000, 4fff]
[    0.647612] bus: 04 index 1 mmio: [f2000000, f3ffffff]
[    0.647615] bus: 04 index 2 mmio: [f0000000, f1ffffff]
[    0.647617] bus: 04 index 3 mmio: [0, 0]
[    0.647620] bus: 03 index 0 mmio: [0, 0]
[    0.647623] bus: 03 index 1 mmio: [f6000000, f60fffff]
[    0.647625] bus: 03 index 2 mmio: [0, 0]
[    0.647627] bus: 03 index 3 mmio: [0, 0]
[    0.647639] NET: Registered protocol family 2
[    0.657078] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.657383] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.658025] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.658347] TCP: Hash tables configured (established 131072 bind 65536)
[    0.658351] TCP reno registered
[    0.661104] NET: Registered protocol family 1
[    0.661232] checking if image is initramfs... it is
[    1.436387] Freeing initrd memory: 7990k freed
[    1.436535] Simple Boot Flag at 0x36 set to 0x1
[    1.437807] audit: initializing netlink socket (disabled)
[    1.437822] type=2000 audit(1229429782.436:1): initialized
[    1.444531] highmem bounce pool size: 64 pages
[    1.444538] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.447740] VFS: Disk quotas dquot_6.5.1
[    1.447850] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.447986] msgmni has been set to 1744
[    1.448142] io scheduler noop registered
[    1.448145] io scheduler anticipatory registered
[    1.448148] io scheduler deadline registered
[    1.448162] io scheduler cfq registered (default)
[    1.448196] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.448365] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.448381] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.448399] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.448416] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.448433] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.448449] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.448465] pci 0000:00:12.0: Boot video device
[    1.448620] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.448647] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.448670] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.448735] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.448829] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.448855] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.448875] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.448935] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.449385] isapnp: Scanning for PnP cards...
[    1.801976] isapnp: No Plug & Play device found
[    1.846711] hpet_resources: 0xfed00000 is busy
[    1.846820] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.849652] brd: module loaded
[    1.849741] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.849886] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.876974] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.876984] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.877372] mice: PS/2 mouse device common for all mice
[    1.877525] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.877564] rtc0: alarms up to one year, y3k, hpet irqs
[    1.877703] EISA: Probing bus 0 at eisa.0
[    1.877709] Cannot allocate resource for EISA slot 1
[    1.877715] Cannot allocate resource for EISA slot 3
[    1.877717] Cannot allocate resource for EISA slot 4
[    1.877730] EISA: Detected 0 cards.
[    1.877734] cpuidle: using governor ladder
[    1.877736] cpuidle: using governor menu
[    1.878302] TCP cubic registered
[    1.878332] Using IPI No-Shortcut mode
[    1.878582] registered taskstats version 1
[    1.878738]   Magic number: 4:231:279
[    1.878764] tty ttyy7: hash matches
[    1.878773] tty ttyva: hash matches
[    1.878836] tty tty16: hash matches
[    1.878910] rtc_cmos 00:07: setting system clock to 2008-12-16 12:16:23 UTC (1229429783)
[    1.878914] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.878916] EDD information not available.
[    1.879215] Freeing unused kernel memory: 424k freed
[    1.879287] Write protecting the kernel text: 2576k
[    1.879332] Write protecting the kernel read-only data: 936k
[    1.898222] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.121201] fuse init (API version 7.9)
[    2.174159] ACPI: processor limited to max C-state 1
[    2.174365] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.174447] processor ACPI0007:00: registered as cooling_device0
[    2.174453] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.174670] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.174735] processor ACPI0007:01: registered as cooling_device1
[    2.174740] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.178148] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080609]
[    2.665919] usbcore: registered new interface driver usbfs
[    2.665946] usbcore: registered new interface driver hub
[    2.665985] usbcore: registered new device driver usb
[    2.668319] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.668807] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    2.668818] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    2.668832] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.668836] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.668889] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.668916] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    2.670806] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.708450] No dock devices found.
[    2.726191] usb usb1: configuration #1 chosen from 1 choice
[    2.726222] hub 1-0:1.0: USB hub found
[    2.726234] hub 1-0:1.0: 7 ports detected
[    2.744729] SCSI subsystem initialized
[    2.775988] libata version 3.00 loaded.
[    2.828808] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    2.828816] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    2.828830] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    2.828834] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    2.828862] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    2.828878] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    2.886176] usb usb2: configuration #1 chosen from 1 choice
[    2.886209] hub 2-0:1.0: USB hub found
[    2.886220] hub 2-0:1.0: 2 ports detected
[    3.092885] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    3.092899] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    3.092915] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.092919] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.092968] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    3.092996] ehci_hcd 0000:00:02.1: debug port 1
[    3.093016] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    3.093039] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    3.269054] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    7.907789] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.907967] usb usb3: configuration #1 chosen from 1 choice
[    7.907998] hub 3-0:1.0: USB hub found
[    7.908009] hub 3-0:1.0: 7 ports detected
[    8.148013] Clocksource tsc unstable (delta = 4398045842885 ns)
[    8.149040] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    8.149047] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    8.149060] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    8.149064] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    8.149110] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[    8.149142] ehci_hcd 0000:00:04.1: debug port 1
[    8.149147] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    8.149155] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    8.304894] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    8.305080] usb usb4: configuration #1 chosen from 1 choice
[    8.305112] hub 4-0:1.0: USB hub found
[    8.305123] hub 4-0:1.0: 2 ports detected
[    8.554780] pata_amd 0000:00:06.0: version 0.3.10
[    8.554828] pata_amd 0000:00:06.0: setting latency timer to 64
[    8.554928] scsi0 : pata_amd
[    8.555432] scsi1 : pata_amd
[    8.555884] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    8.555888] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    8.710175] usb 2-2: device not accepting address 2, error -62
[    8.741952] ata1.00: ATAPI: MATSHITADVD-RAM UJ-861H, 1.50, max MWDMA2
[    8.741969] ata1: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc700) ACPI=0x39f (120:600:0x12)
[    8.772960] hub 2-0:1.0: unable to enumerate USB device on port 2
[    8.805140] ata1.00: configured for MWDMA2
[    8.805208] ata2: port disabled. ignoring.
[    8.807345] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-861H  1.50 PQ: 0 ANSI: 5
[    8.808163] ahci 0000:00:09.0: version 3.0
[    8.808632] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    8.808643] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    8.808739] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    8.808743] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[    8.808747] ahci 0000:00:09.0: setting latency timer to 64
[    8.809144] scsi2 : ahci
[    8.809753] scsi3 : ahci
[    8.810256] scsi4 : ahci
[    8.810774] scsi5 : ahci
[    8.810895] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 221
[    8.810899] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 221
[    8.810902] ata5: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 221
[    8.810906] ata6: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 221
[    9.054354] usb 4-2: new high speed USB device using ehci_hcd and address 2
[    9.252559] usb 4-2: configuration #1 chosen from 1 choice
[    9.366870] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.367642] ata3.00: ATA-8: Hitachi HTS542512K9SA00, BB2OC32P, max UDMA/100
[    9.367647] ata3.00: 234441648 sectors, multi 16: LBA48 
[    9.368627] ata3.00: configured for UDMA/100
[   10.336371] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   10.337310] ata4.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC31P, max UDMA/133
[   10.337314] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   10.338456] ata4.00: configured for UDMA/133
[   10.712062] ata5: SATA link down (SStatus 0 SControl 300)
[   11.087050] ata6: SATA link down (SStatus 0 SControl 300)
[   11.087167] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BB2O PQ: 0 ANSI: 5
[   11.088291] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[   11.089329] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   11.089796] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   11.089808] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[   11.089813] forcedeth 0000:00:0a.0: setting latency timer to 64
[   11.650808] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:eb:53:87
[   11.650813] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   11.651411] ohci1394 0000:02:05.0: enabling device (0100 -> 0102)
[   11.651864] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   11.651878] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[   11.703616] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   11.742559] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[   11.742610] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   11.742655] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[   11.770183] Driver 'sd' needs updating - please use bus_type methods
[   11.770317] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   11.770336] sd 2:0:0:0: [sda] Write Protect is off
[   11.770339] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.770368] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.770441] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   11.770457] sd 2:0:0:0: [sda] Write Protect is off
[   11.770460] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.770487] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.770492]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   11.778213] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   11.778219] Uniform CD-ROM driver Revision: 3.20
[   11.778322] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   11.787247]  sda1 sda2 sda3 < sda5 sda6 >
[   11.826779] sd 2:0:0:0: [sda] Attached SCSI disk
[   11.826865] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   11.826884] sd 3:0:0:0: [sdb] Write Protect is off
[   11.826887] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   11.826915] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.826978] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   11.826995] sd 3:0:0:0: [sdb] Write Protect is off
[   11.826998] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   11.827025] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.827030]  sdb: sdb1
[   12.201538] sd 3:0:0:0: [sdb] Attached SCSI disk
[   12.736915] PM: Starting manual resume from disk
[   12.736920] PM: Resume from partition 8:6
[   12.736922] PM: Checking hibernation image.
[   12.737105] PM: Resume from disk failed.
[   12.788747] kjournald starting.  Commit interval 5 seconds
[   12.788761] EXT3-fs: mounted filesystem with ordered data mode.
[   12.998889] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0002509800]
[   19.200043] udevd version 124 started
[   19.799792] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.811431] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.101170] Linux agpgart interface v0.103
[   20.133271] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   20.149026] ACPI: Power Button (FF) [PWRF]
[   20.149149] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[   20.165026] ACPI: Sleep Button (CM) [SLPB]
[   20.166881] ACPI: AC Adapter [ACAD] (on-line)
[   20.166955] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   20.168793] ACPI: Lid Switch [LID]
[   20.168933] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   20.201046] ACPI: Power Button (CM) [PWRB]
[   20.458904] nvidia: module license 'NVIDIA' taints kernel.
[   20.716551] ACPI: Battery Slot [BAT0] (battery present)
[   20.889260] ACPI: WMI: Mapper loaded
[   20.968446] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   20.968459] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   20.968467] nvidia 0000:00:12.0: setting latency timer to 64
[   20.968793] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
[   21.242561] acpi device:25: registered as cooling_device2
[   21.242784] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input6
[   21.277021] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   21.344018] ricoh-mmc: Ricoh MMC Controller disabling driver
[   21.344023] ricoh-mmc: Copyright(c) Philip Langdale
[   21.344058] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   21.344074] ricoh-mmc: Controller is now disabled.
[   21.414921] ieee80211_crypt: registered algorithm 'NULL'
[   21.433699] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   21.433712] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   21.433718] wl 0000:03:00.0: setting latency timer to 64
[   21.453846] sdhci: Secure Digital Host Controller Interface driver
[   21.453850] sdhci: Copyright(c) Pierre Ossman
[   21.502476] ieee80211_crypt: registered algorithm 'TKIP'
[   21.502816] eth1: Broadcom BCM4312 802.11 Wireless Controller 5.10.27.6
[   21.617175] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[   21.617641] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   21.617654] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   21.620708] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
[   21.827564] Linux video capture interface: v2.00
[   21.841355] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   21.841370] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   21.841403] HDA Intel 0000:00:07.0: setting latency timer to 64
[   21.844959] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   22.101629] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
[   22.103381] input: HP Webcam as /devices/pci0000:00/0000:00:04.1/usb4/4-2/4-2:1.0/input/input8
[   22.128352] usbcore: registered new interface driver uvcvideo
[   22.128358] USB Video Class driver (v0.1.0)
[   22.834495] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   22.917524] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   24.225174] loop: module loaded
[   24.277315] lp: driver loaded but no devices found
[   24.491668] Adding 1228932k swap on /dev/sda6.  Priority:-1 extents:1 across:1228932k
[   25.045347] EXT3 FS on sda5, internal journal
[   25.996562] type=1505 audit(1229429807.917:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4336
[   26.224504] type=1505 audit(1229429808.145:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4341
[   26.224753] type=1505 audit(1229429808.145:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4341
[   26.377416] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.347903] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 processors (2 cpu cores) (version 2.20.00)
[   27.348553] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[   27.348558] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   27.348561] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a
[   28.142024] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   28.196668] apm: BIOS not found.
[   28.399331] ppdev: user-space parallel port driver
[   31.505921] Bluetooth: Core ver 2.13
[   31.506163] NET: Registered protocol family 31
[   31.506172] Bluetooth: HCI device and connection manager initialized
[   31.506189] Bluetooth: HCI socket layer initialized
[   31.528628] Bluetooth: L2CAP ver 2.11
[   31.528643] Bluetooth: L2CAP socket layer initialized
[   31.545479] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.545495] Bluetooth: BNEP filters: protocol multicast
[   31.579435] Bridge firewalling registered
[   31.579823] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   31.599552] Bluetooth: SCO (Voice Link) ver 0.6
[   31.599568] Bluetooth: SCO socket layer initialized
[   31.653253] Bluetooth: RFCOMM socket layer initialized
[   31.653291] Bluetooth: RFCOMM TTY layer initialized
[   31.653296] Bluetooth: RFCOMM ver 1.10
[   35.849148] eth0: no link during initialization.
[   36.497568] NET: Registered protocol family 17
[   41.852612] NET: Registered protocol family 10
[   41.853811] lo: Disabled Privacy Extensions
[   41.855059] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.592020] eth1: no IPv6 routers present
[   82.319331] CPU0 attaching NULL sched-domain.
[   82.319367] CPU1 attaching NULL sched-domain.
[   82.322816] CPU0 attaching sched-domain:
[   82.322830]  domain 0: span 0-1 level MC
[   82.322841]   groups: 0 1
[   82.322852]   domain 1: span 0-1 level CPU
[   82.322859]    groups: 0-1
[   82.322874] CPU1 attaching sched-domain:
[   82.322879]  domain 0: span 0-1 level MC
[   82.322887]   groups: 1 0
[   82.322896]   domain 1: span 0-1 level CPU
[   82.322901]    groups: 0-1

---

### Post by drs305 on 2008-12-16
This bug has been reported by many people. One of the bug reports is:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247")

The thread is quite long, and most of the solutions involve adding something to the boot line in your menu.lst. Suggested remedies include adding " noapic ", " nolapic " , and/or " hpet=disable " to your menu.lst boot line. They all have side effects so I won't suggest one over the other. These 'solutions' start pretty near the end of the thread (search within the thread for 'worb' ).

Personally, the only suggestion I would try was the simplest - several people had success by just quickly hitting the power button once during boot.

---

### Post by geirha on 2008-12-16
Also, in the future, please put terminal output and file contents (like the dmesg output above) inside code tags. You put text into code tags that by marking the text and clicking the # icon. Makes the output easier to read, and shortens the height of the post.

---

