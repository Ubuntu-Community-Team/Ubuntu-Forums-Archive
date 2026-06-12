---
title: "constant freezing"
date: 2008-12-10
forum: General Help
---

### Post by blackvd on 2008-12-10
I have a fresh install of Ubuntu 8.10 which keeps freezing on me. It happens when I'm at work so I can't figure out what is causing it. Whenever I leave it for long periods of time the monitor quits responding and I have to hard reboot.

dmesg gives this output which is weird

```
[ 2421.151744] rix 514 (0) bad ratekbps 0 mode 6
[ 2421.199352] rix 514 (0) bad ratekbps 0 mode 6
[ 2422.387567] rix 514 (0) bad ratekbps 0 mode 6
[ 2433.050286] wifi0: rx FIFO overrun; resetting
[ 2580.897537] rix 514 (0) bad ratekbps 0 mode 6
[ 2660.252026] rix 514 (0) bad ratekbps 0 mode 6
[ 2660.256856] rix 514 (0) bad ratekbps 0 mode 6
[ 2661.844619] rix 514 (0) bad ratekbps 0 mode 6
[ 2662.164528] rix 514 (0) bad ratekbps 0 mode 6
```

Goes on forever so I just posted a section of it. 

Guessing it has to do with my wi-fi and or deluge as I have both going all the time. My wireless pci card is a Netgear RangeMax WPN311. My computer is brand new self built so I'm worried it might be my hardware. My HDD is a Super Talent Solid State Drive(32GB) which actually came with Hardy =D>

Computer just froze as I was typing this line luckily firefox saved it.

So here is the end of dmesg output after rebooting

```
[    0.446719] AppArmor: AppArmor Filesystem Enabled
[    0.446734] ACPI: RTC can wake from S4
[    0.460019] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.460022] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.460024] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.460026] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.460028] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.460038] system 00:0a: ioport range 0x400-0x4bf could not be reserved
[    0.460043] system 00:0b: iomem range 0xe0000000-0xe3ffffff could not be reserved
[    0.460048] system 00:0c: iomem range 0xcd000-0xcffff has been reserved
[    0.460050] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.460052] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.460054] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.460057] system 00:0c: iomem range 0xcfee0000-0xcfefffff could not be reserved
[    0.460059] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.460061] system 00:0c: iomem range 0x100000-0xcfedffff could not be reserved
[    0.460064] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.460066] system 00:0c: iomem range 0xfed13000-0xfed1dfff could not be reserved
[    0.460069] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.460071] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.460073] system 00:0c: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.460076] system 00:0c: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.460078] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
[    0.464919] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.464921] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.464924] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe7ffffff
[    0.464926] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.464928] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.464930] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
[    0.464933] pci 0000:00:1c.0:   MEM window: disabled
[    0.464936] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.464940] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.464942] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.464945] pci 0000:00:1c.1:   MEM window: 0xe8000000-0xe8ffffff
[    0.464947] pci 0000:00:1c.1:   PREFETCH window: 0x000000e9000000-0x000000e90fffff
[    0.464952] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.464953] pci 0000:00:1e.0:   IO window: disabled
[    0.464956] pci 0000:00:1e.0:   MEM window: 0xe9100000-0xe91fffff
[    0.464958] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.464966] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.464969] pci 0000:00:01.0: setting latency timer to 64
[    0.464973] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.464976] pci 0000:00:1c.0: setting latency timer to 64
[    0.464981] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.464984] pci 0000:00:1c.1: setting latency timer to 64
[    0.464988] pci 0000:00:1e.0: setting latency timer to 64
[    0.464990] bus: 00 index 0 io port: [0, ffff]
[    0.464991] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.464992] bus: 01 index 0 io port: [c000, cfff]
[    0.464993] bus: 01 index 1 mmio: [e4000000, e7ffffff]
[    0.464995] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.464996] bus: 01 index 3 mmio: [0, 0]
[    0.464997] bus: 02 index 0 io port: [b000, bfff]
[    0.464998] bus: 02 index 1 mmio: [0, 0]
[    0.464999] bus: 02 index 2 mmio: [0, 0]
[    0.465000] bus: 02 index 3 mmio: [0, 0]
[    0.465001] bus: 03 index 0 io port: [d000, dfff]
[    0.465002] bus: 03 index 1 mmio: [e8000000, e8ffffff]
[    0.465003] bus: 03 index 2 mmio: [e9000000, e90fffff]
[    0.465004] bus: 03 index 3 mmio: [0, 0]
[    0.465005] bus: 04 index 0 mmio: [0, 0]
[    0.465006] bus: 04 index 1 mmio: [e9100000, e91fffff]
[    0.465007] bus: 04 index 2 mmio: [0, 0]
[    0.465008] bus: 04 index 3 io port: [0, ffff]
[    0.465009] bus: 04 index 4 mmio: [0, ffffffffffffffff]
[    0.465015] NET: Registered protocol family 2
[    0.500666] Switched to high resolution mode on CPU 1
[    0.503910] Switched to high resolution mode on CPU 0
[    0.504062] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.504834] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.507127] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.507509] TCP: Hash tables configured (established 524288 bind 65536)
[    0.507511] TCP reno registered
[    0.516102] NET: Registered protocol family 1
[    0.516204] checking if image is initramfs... it is
[    1.031373] Freeing initrd memory: 8463k freed
[    1.033828] audit: initializing netlink socket (disabled)
[    1.033847] type=2000 audit(1228887421.032:1): initialized
[    1.037939] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.039474] VFS: Disk quotas dquot_6.5.1
[    1.039524] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.039591] msgmni has been set to 7917
[    1.039664] io scheduler noop registered
[    1.039665] io scheduler anticipatory registered
[    1.039666] io scheduler deadline registered
[    1.039744] io scheduler cfq registered (default)
[    1.039827] pci 0000:01:00.0: Boot video device
[    1.039890] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.039909] pcieport-driver 0000:00:01.0: found MSI capability
[    1.039928] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.039953] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.040002] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.040025] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.040048] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.040072] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.040098] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.040155] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.040178] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.040201] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.040225] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.040252] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.059409] hpet_resources: 0xfed00000 is busy
[    1.059456] Linux agpgart interface v0.103
[    1.059459] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.059566] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.059981] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.061108] brd: module loaded
[    1.061152] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.061253] PNP: No PS/2 controller found. Probing ports directly.
[    1.095174] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.095175] If AUX port is really absent please use the 'i8042.noaux' option.
[    1.344084] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.352589] mice: PS/2 mouse device common for all mice
[    1.352690] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.352710] rtc0: alarms up to one month, hpet irqs
[    1.352732] cpuidle: using governor ladder
[    1.352734] cpuidle: using governor menu
[    1.352971] TCP cubic registered
[    1.353083] registered taskstats version 1
[    1.353155]   Magic number: 4:895:617
[    1.353170] tty ptye7: hash matches
[    1.353173] tty ptyba: hash matches
[    1.353221] rtc_cmos 00:04: setting system clock to 2008-12-10 05:37:02 UTC (1228887422)
[    1.353223] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.353224] EDD information not available.
[    1.353248] Freeing unused kernel memory: 536k freed
[    1.353386] Write protecting the kernel read-only data: 4348k
[    1.468372] fuse init (API version 7.9)
[    1.486750] ACPI: SSDT CFEE6D40, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    1.526521] processor ACPI0007:00: registered as cooling_device0
[    1.526524] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.526662] ACPI: SSDT CFEE7200, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[    1.526806] processor ACPI0007:01: registered as cooling_device1
[    1.526808] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.687698] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.687713] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.687730] r8169 0000:03:00.0: setting latency timer to 64
[    1.687968] eth0: RTL8168c/8111c at 0xffffc20000630000, 00:1f:d0:68:cd:60, XID 3c4000c0 IRQ 2300
[    1.744044] usbcore: registered new interface driver usbfs
[    1.744060] usbcore: registered new interface driver hub
[    1.746305] No dock devices found.
[    1.751806] usbcore: registered new device driver usb
[    1.753524] SCSI subsystem initialized
[    1.754361] USB Universal Host Controller Interface driver v3.0
[    1.754386] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.754392] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.754395] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.754424] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.754450] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e000
[    1.754572] usb usb1: configuration #1 chosen from 1 choice
[    1.754591] hub 1-0:1.0: USB hub found
[    1.754597] hub 1-0:1.0: 2 ports detected
[    1.763834] libata version 3.00 loaded.
[    1.860179] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.860185] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.860188] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.860204] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    1.860229] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e100
[    1.860283] usb usb2: configuration #1 chosen from 1 choice
[    1.860299] hub 2-0:1.0: USB hub found
[    1.860304] hub 2-0:1.0: 2 ports detected
[    1.964162] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.964169] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.964171] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.964188] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    1.964213] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e200
[    1.964267] usb usb3: configuration #1 chosen from 1 choice
[    1.964284] hub 3-0:1.0: USB hub found
[    1.964289] hub 3-0:1.0: 2 ports detected
[    2.168184] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.168191] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.168194] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.168210] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.168237] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e300
[    2.168294] usb usb4: configuration #1 chosen from 1 choice
[    2.168311] hub 4-0:1.0: USB hub found
[    2.168316] hub 4-0:1.0: 2 ports detected
[    2.280507] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.376749] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.376761] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.376764] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.376791] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.380702] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.380707] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe9204000
[    2.408508] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.408591] usb usb5: configuration #1 chosen from 1 choice
[    2.408618] hub 5-0:1.0: USB hub found
[    2.408625] hub 5-0:1.0: 8 ports detected
[    2.616119] ata_piix 0000:00:1f.2: version 2.12
[    2.616129] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.616133] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.616164] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.616217] scsi0 : ata_piix
[    2.616276] scsi1 : ata_piix
[    2.616764] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    2.616765] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    2.780180] ata1.00: ATA-8: STT_FTM32GL25H, 080826, max UDMA/100
[    2.780182] ata1.00: 62586880 sectors, multi 0: LBA 
[    2.788180] ata1.00: configured for UDMA/100
[    2.804007] usb 3-1: device not accepting address 2, error -71
[    2.860030] hub 3-0:1.0: unable to enumerate USB device on port 1
[    2.944124] ata2.01: NODEV after polling detection
[    2.952179] ata2.00: ATAPI: HL-DT-ST DVDRAM GH20NS15, IL00, max UDMA/100
[    2.968180] ata2.00: configured for UDMA/100
[    2.968249] scsi 0:0:0:0: Direct-Access     ATA      STT_FTM32GL25H   0808 PQ: 0 ANSI: 5
[    2.971718] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH20NS15  IL00 PQ: 0 ANSI: 5
[    2.982417] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    2.982439] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    2.990393] Driver 'sd' needs updating - please use bus_type methods
[    2.990447] sd 0:0:0:0: [sda] 62586880 512-byte hardware sectors (32044 MB)
[    2.990459] sd 0:0:0:0: [sda] Write Protect is off
[    2.990461] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.990479] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.990528] sd 0:0:0:0: [sda] 62586880 512-byte hardware sectors (32044 MB)
[    2.990539] sd 0:0:0:0: [sda] Write Protect is off
[    2.990540] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.990559] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.990562]  sda: sda1 sda2 < sda5 >
[    2.991403] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.998306] Driver 'sr' needs updating - please use bus_type methods
[    3.009824] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.009826] Uniform CD-ROM driver Revision: 3.20
[    3.009878] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.086348] PM: Starting manual resume from disk
[    3.086350] PM: Resume from partition 8:5
[    3.086351] PM: Checking hibernation image.
[    3.086495] PM: Resume from disk failed.
[    3.098299] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.098302] EXT3-fs: write access will be enabled during recovery.
[    3.156519] usb 5-7: new high speed USB device using ehci_hcd and address 3
[    3.290317] usb 5-7: configuration #1 chosen from 1 choice
[    3.532013] usb 3-1: new low speed USB device using uhci_hcd and address 4
[    3.709351] usb 3-1: configuration #1 chosen from 1 choice
[    3.712487] usbcore: registered new interface driver libusual
[    3.719513] Initializing USB Mass Storage driver...
[    3.720881] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.723813] usbcore: registered new interface driver usb-storage
[    3.723815] USB Mass Storage support registered.
[    3.723818] usb-storage: device found at 3
[    3.723819] usb-storage: waiting for device to settle before scanning
[    3.724345] usbcore: registered new interface driver hiddev
[    3.738484] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input1
[    3.760071] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-1
[    3.788257] Fixing up Logitech keyboard report descriptor
[    3.788844] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/input/input2
[    3.812652] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-1
[    3.812668] usbcore: registered new interface driver usbhid
[    3.812670] usbhid: v2.6:USB HID core driver
[    8.720087] usb-storage: device scan complete
[    8.720573] scsi 2:0:0:0: Direct-Access     WD       5000AVV External 1.05 PQ: 0 ANSI: 4
[    8.722058] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    8.722806] sd 2:0:0:0: [sdb] Write Protect is off
[    8.722808] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    8.722810] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.723682] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    8.724430] sd 2:0:0:0: [sdb] Write Protect is off
[    8.724432] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    8.724433] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.724435]  sdb: sdb1
[    8.724869] sd 2:0:0:0: [sdb] Attached SCSI disk
[    8.724934] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   18.415828] kjournald starting.  Commit interval 5 seconds
[   18.415836] EXT3-fs: sda1: orphan cleanup on readonly fs
[   18.415842] ext3_orphan_cleanup: deleting unreferenced inode 1753243
[   18.416418] ext3_orphan_cleanup: deleting unreferenced inode 1657764
[   18.416437] ext3_orphan_cleanup: deleting unreferenced inode 91244
[   18.416452] ext3_orphan_cleanup: deleting unreferenced inode 91252
[   18.416462] ext3_orphan_cleanup: deleting unreferenced inode 1654914
[   18.416842] ext3_orphan_cleanup: deleting unreferenced inode 311338
[   18.416862] EXT3-fs: sda1: 6 orphan inodes deleted
[   18.416864] EXT3-fs: recovery complete.
[   19.584642] EXT3-fs: mounted filesystem with ordered data mode.
[   21.148467] udevd version 124 started
[   21.276049] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.277345] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   21.304527] ACPI: Power Button (FF) [PWRF]
[   21.304575] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   21.304677] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.332510] ACPI: Power Button (CM) [PWRB]
[   21.548218] nvidia: module license 'NVIDIA' taints kernel.
[   21.549192] Symbol init_mm is marked as UNUSED, however this module is using it.
[   21.549193] This symbol will go away in the future.
[   21.549194] Please evalute if this is the right api to use and if it really is, submit a report the linux kernel mailinglist together with submitting your code for inclusion.
[   21.819652] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.819657] nvidia 0000:01:00.0: setting latency timer to 64
[   21.819734] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.12  Thu Jul 17 18:10:24 PDT 2008
[   21.899341] parport_pc 00:09: reported by Plug and Play ACPI
[   21.899385] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   21.932490] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   21.938290] wlan: 0.9.4
[   21.941258] ath_pci: 0.9.4
[   21.941289] ath_pci 0000:04:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   22.552066] intel_rng: FWH not detected
[   22.574940] ath_rate_sample: 1.2 (0.9.4)
[   22.575233] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   22.575237] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   22.575243] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   22.575247] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   22.575249] wifi0: mac 7.9 phy 4.5 radio 5.6
[   22.575251] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   22.575253] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   22.575254] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   22.575255] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   22.575256] wifi0: Use hw queue 8 for CAB traffic
[   22.575257] wifi0: Use hw queue 9 for beacons
[   22.589971] wifi0: Atheros 5212: mem=0xe9100000, irq=20
[   22.593196] iTCO_vendor_support: vendor-support=0
[   22.615406] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   22.622492] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   22.636578] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   22.636646] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   22.747514] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.747528] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.142341] lp0: using parport0 (interrupt-driven).
[   24.205971] Adding 1325320k swap on /dev/sda5.  Priority:-1 extents:1 across:1325320k
[   24.259131] EXT3 FS on sda1, internal journal
[   24.384227] type=1505 audit(1228887445.273:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3905
[   24.465622] type=1505 audit(1228887445.357:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3910
[   24.465730] type=1505 audit(1228887445.357:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3910
[   24.492132] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.667467] ACPI: WMI: Mapper loaded
[   25.025975] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   25.052007] ppdev: user-space parallel port driver
[   29.616412] r8169: eth0: link down
[   29.787566] NET: Registered protocol family 17
[   68.088132] NET: Registered protocol family 10
[   68.088968] lo: Disabled Privacy Extensions
[   68.089777] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.472505] ath0: no IPv6 routers present
```


If anyone can help please let me know what other information is needed. 

Thanks.

---

### Post by blackvd on 2008-12-10
So absolutely no one has experienced freezing in 8.10? Not looking forward to testing all my hardware :(

---

### Post by blackvd on 2008-12-12
Installed Linux Mint 5 and my computer hasn't froze yet. So it might be a Ibex issue have to wait and see.

---

### Post by 2hot6ft2 on 2008-12-12
Just answered this so this is the same reply

Believe it or not the freezes seem to tie into the sound Pulse Audio (when not configured properly) can send the cpu to 100% causing the freeze. This has been reported by several people and the solution is here for that.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I was having freezes too and since completing the how to have not had a freeze at all.

This may or may not be your particular issue but it's where I would start after reading everything I have.

---

### Post by Steve Meynell on 2009-10-12
I too am experiencing constant freezing.  I am using Hardy Version however.  But my freezing seems to be related to the use of Deluge.  I can sometimes run my system for hours without a freeze up but as soon as I start Deluge it will freeze after a little while.  I have been able to run Deluge for a long period of time but not very often.

It's very confusing and also quite frustrating.

---

