---
title: "Why is Ubuntu so unstable"
date: 2009-02-06
forum: General Help
---

### Post by yusuo85 on 2009-02-06
im making alot of posts today.

My computer has a tendency to suddenly reboot itself for no reason other then its working a little too hard, multiple windows etc.
Where as I've never had this problem with windows regardless of what or how much I have open.

Anyone have any suggestions on a different, more stable distro to use, I tried debian but the lack of deluge support in the toolbar made that a no go

---

### Post by donkyhotay on 2009-02-06
I've found ubuntu to be quite stable, what kind of hardware and drivers are you using?

---

### Post by mb_webguy on 2009-02-06
A better question is "Why is Ubuntu so unstable on *your system*", since it is very stable on many other people's systems -- otherwise it wouldn't be nearly as popular.

Switching distributions may not necessarily help, since the Linux kernel will be pretty much the same.

If you can post some details about your system (such as the output of dmesg), someone might be able to help fix your problem.

---

### Post by Yashiro on 2009-02-06
Linux suddenly rebooting? That's none too common.
Crash, sure. Reboot? Not so much.

---

### Post by yusuo85 on 2009-02-06
3.2ghz pent 4, 1.25gb ram, ati x600 256mb graphics, 2 sata drives one 320gb one 250gb

---

### Post by theozzlives on 2009-02-06
Sounds like a heat prob to me. Check your CPU heatsink and fan.

---

### Post by yusuo85 on 2009-02-06
[   22.144158] Calibrating delay using timer specific routine.. 6783.50 BogoMIPS (lpj=13567010)
[   22.144168] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
[   22.144175] monitor/mwait feature present.
[   22.144180] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   22.144183] CPU: L2 cache: 1024K
[   22.144185] CPU: Physical Processor ID: 0
[   22.144187] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043180 0000441d 00000000 00000000 00000000
[   22.144546] CPU1: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 04
[   22.144584] Total of 2 processors activated (13626.70 BogoMIPS).
[   22.144731] ENABLING IO-APIC IRQs
[   22.144904] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.291848] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   22.311802] Brought up 2 CPUs
[   22.311829] CPU0 attaching sched-domain:
[   22.311833]  domain 0: span 03
[   22.311835]   groups: 01 02
[   22.311838]   domain 1: span 03
[   22.311840]    groups: 03
[   22.311842] CPU1 attaching sched-domain:
[   22.311844]  domain 0: span 03
[   22.311845]   groups: 02 01
[   22.311848]   domain 1: span 03
[   22.311850]    groups: 03
[   22.312102] net_namespace: 64 bytes
[   22.312110] Booting paravirtualized kernel on bare hardware
[   22.312613] Time:  0:02:04  Date: 02/07/09
[   22.312636] NET: Registered protocol family 16
[   22.312882] EISA bus registered
[   22.312889] ACPI: bus type pci registered
[   22.340306] PCI: PCI BIOS revision 3.00 entry at 0xfbaf0, last bus=3
[   22.340308] PCI: Using configuration type 1
[   22.340317] Setting up standard PCI resources
[   22.354446] ACPI: EC: Look up EC in DSDT
[   22.358550] ACPI: Interpreter enabled
[   22.358554] ACPI: (supports S0 S3 S4 S5)
[   22.358568] ACPI: Using IOAPIC for interrupt routing
[   22.363537] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.364087] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   22.364091] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   22.364874] PCI: Transparent bridge - 0000:00:1e.0
[   22.364904] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.365052] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   22.365132] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   22.375095] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.375199] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   22.375302] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.375404] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.375514] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   22.375617] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.375718] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.375819] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.375958] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.375997] pnp: PnP ACPI init
[   22.376007] ACPI: bus type pnp registered
[   22.378668] pnpacpi: exceeded the max number of mem resources: 12
[   22.378737] pnp: PnP ACPI: found 13 devices
[   22.378739] ACPI: ACPI bus type pnp unregistered
[   22.378744] PnPBIOS: Disabled by ACPI PNP
[   22.379022] PCI: Using ACPI for IRQ routing
[   22.379025] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.419343] NET: Registered protocol family 8
[   22.419346] NET: Registered protocol family 20
[   22.419419] AppArmor: AppArmor Filesystem Enabled
[   22.423322] Time: tsc clocksource has been installed.
[   22.435330] system 00:01: ioport range 0xb78-0xb7b has been reserved
[   22.435333] system 00:01: ioport range 0xf78-0xf7b has been reserved
[   22.435335] system 00:01: ioport range 0xa78-0xa7b has been reserved
[   22.435338] system 00:01: ioport range 0xe78-0xe7b has been reserved
[   22.435340] system 00:01: ioport range 0xbbc-0xbbf has been reserved
[   22.435342] system 00:01: ioport range 0xfbc-0xfbf has been reserved
[   22.435344] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   22.435347] system 00:01: ioport range 0x294-0x297 has been reserved
[   22.435357] system 00:09: ioport range 0x400-0x4bf could not be reserved
[   22.435363] system 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   22.435369] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[   22.435372] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   22.435374] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   22.435376] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   22.435379] system 00:0c: iomem range 0x4fff0000-0x4fffffff could not be reserved
[   22.435381] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   22.435384] system 00:0c: iomem range 0x100000-0x4ffeffff could not be reserved
[   22.435387] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   22.435389] system 00:0c: iomem range 0xfed13000-0xfed1dfff could not be reserved
[   22.435392] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved
[   22.435394] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   22.435397] system 00:0c: iomem range 0xffb00000-0xffb7ffff could not be reserved
[   22.465819] PCI: Bridge: 0000:00:01.0
[   22.465822]   IO window: c000-cfff
[   22.465826]   MEM window: d0000000-d00fffff
[   22.465829]   PREFETCH window: c0000000-cfffffff
[   22.465833] PCI: Bridge: 0000:00:1c.0
[   22.465835]   IO window: disabled.
[   22.465839]   MEM window: disabled.
[   22.465842]   PREFETCH window: disabled.
[   22.465847] PCI: Bridge: 0000:00:1e.0
[   22.465850]   IO window: d000-dfff
[   22.465854]   MEM window: d0100000-d01fffff
[   22.465857]   PREFETCH window: disabled.
[   22.465874] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.465880] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.465899] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.465904] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.465914] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.465925] NET: Registered protocol family 2
[   22.503149] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.503451] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.504057] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.504450] TCP: Hash tables configured (established 131072 bind 65536)
[   22.504452] TCP reno registered
[   22.515237] checking if image is initramfs... it is
[   22.961825] Switched to high resolution mode on CPU 1
[   22.965670] Switched to high resolution mode on CPU 0
[   23.028755] Freeing initrd memory: 7319k freed
[   23.029691] audit: initializing netlink socket (disabled)
[   23.029711] audit(1233964924.224:1): initialized
[   23.029923] highmem bounce pool size: 64 pages
[   23.032119] VFS: Disk quotas dquot_6.5.1
[   23.032201] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.032348] io scheduler noop registered
[   23.032351] io scheduler anticipatory registered
[   23.032352] io scheduler deadline registered
[   23.032363] io scheduler cfq registered (default)
[   23.032449] Boot video device is 0000:01:00.0
[   23.032570] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.032608] assign_interrupt_mode Found MSI capability
[   23.032640] Allocate Port Service[0000:00:01.0:pcie00]
[   23.032725] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.032766] assign_interrupt_mode Found MSI capability
[   23.032799] Allocate Port Service[0000:00:1c.0:pcie00]
[   23.032841] Allocate Port Service[0000:00:1c.0:pcie02]
[   23.033131] isapnp: Scanning for PnP cards...
[   23.386766] isapnp: No Plug & Play device found
[   23.420945] Real Time Clock Driver v1.12ac
[   23.421059] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.421181] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.421936] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.422871] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.422944] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.423119] PNP: No PS/2 controller found. Probing ports directly.
[   23.425214] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.425221] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.444360] mice: PS/2 mouse device common for all mice
[   23.444504] EISA: Probing bus 0 at eisa.0
[   23.444534] EISA: Detected 0 cards.
[   23.444537] cpuidle: using governor ladder
[   23.444539] cpuidle: using governor menu
[   23.444621] NET: Registered protocol family 1
[   23.444650] Using IPI No-Shortcut mode
[   23.444679] registered taskstats version 1
[   23.444774]   Magic number: 13:456:0
[   23.444780]   hash matches device ttye8
[   23.444786]   hash matches device ttybb
[   23.444883] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.444884] EDD information not available.
[   23.445108] Freeing unused kernel memory: 368k freed
[   23.445131] Write protecting the kernel read-only data: 806k
[   24.678451] fuse init (API version 7.9)
[   24.724011] ACPI: Fan [FAN] (on)
[   24.735106] ACPI: Thermal Zone [THRM] (71 C)
[   25.185193] usbcore: registered new interface driver usbfs
[   25.185226] usbcore: registered new interface driver hub
[   25.185531] SCSI subsystem initialized
[   25.219835] usbcore: registered new device driver usb
[   25.223498] USB Universal Host Controller Interface driver v3.0
[   25.223578] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   25.223598] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   25.223604] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   25.223946] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   25.223979] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000e300
[   25.224156] usb usb1: configuration #1 chosen from 1 choice
[   25.224188] hub 1-0:1.0: USB hub found
[   25.224196] hub 1-0:1.0: 2 ports detected
[   25.224254] libata version 3.00 loaded.
[   25.327504] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   25.327522] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.327528] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.327558] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   25.327565] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   25.327636] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   25.327670] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e000
[   25.327826] usb usb2: configuration #1 chosen from 1 choice
[   25.327865] hub 2-0:1.0: USB hub found
[   25.327874] hub 2-0:1.0: 2 ports detected
[   25.350990] Floppy drive(s): fd0 is 1.44M
[   25.374288] FDC 0 is a post-1991 82077
[   25.431119] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   25.431132] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   25.431136] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.431163] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   25.431191] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000e100
[   25.431303] usb usb3: configuration #1 chosen from 1 choice
[   25.431328] hub 3-0:1.0: USB hub found
[   25.431334] hub 3-0:1.0: 2 ports detected
[   25.534837] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   25.534855] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   25.534860] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   25.534896] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   25.534929] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e200
[   25.535100] usb usb4: configuration #1 chosen from 1 choice
[   25.535143] hub 4-0:1.0: USB hub found
[   25.535155] hub 4-0:1.0: 2 ports detected
[   25.570356] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   25.641685] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[   25.641702] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   25.641707] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   25.641745] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   25.645679] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   25.645695] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xd0204000
[   25.701180] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.701355] usb usb5: configuration #1 chosen from 1 choice
[   25.701402] hub 5-0:1.0: USB hub found
[   25.701415] hub 5-0:1.0: 8 ports detected
[   25.805296] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 18 (level, low) -> IRQ 19
[   25.810918] eth0: VIA Rhine III at 0xd0105000, 00:11:09:78:00:06, IRQ 19.
[   25.811634] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[   25.813495] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 19 (level, low) -> IRQ 18
[   25.866590] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[d0103000-d01037ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   25.904558] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   25.904613] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.904633] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   25.904671] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[   25.904718] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   25.904733] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   25.909202] ata_piix 0000:00:1f.1: version 2.12
[   25.909224] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   25.909270] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.909350] scsi0 : ata_piix
[   25.909421] scsi1 : ata_piix
[   25.910383] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   25.910388] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   26.099933] usb 1-1: device not accepting address 2, error -71
[   26.279939] ata1.00: ATA-7: MAXTOR STM3320820A, 3.AAE, max UDMA/100
[   26.279943] ata1.00: 625142448 sectors, multi 16: LBA48 
[   26.279967] ata1.01: ATAPI: PIONEER DVD RW  DVR-108, 1.14, max UDMA/66
[   26.279981] ata1.00: limited to UDMA/33 due to 40-wire cable
[   26.279983] ata1.01: limited to UDMA/33 due to 40-wire cable
[   26.346343] ata1.00: configured for UDMA/33
[   26.506946] ata1.01: configured for UDMA/33
[   26.506992] ata2: port disabled. ignoring.
[   26.507140] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM332082 3.AA PQ: 0 ANSI: 5
[   26.512911] scsi 0:0:1:0: CD-ROM            PIONEER  DVD RW  DVR-108  1.14 PQ: 0 ANSI: 5
[   26.512989] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   26.513014] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[   26.513063] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   26.513146] scsi2 : ata_piix
[   26.513208] scsi3 : ata_piix
[   26.513843] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe500 bmdma 0xe800 irq 18
[   26.513846] ata4: SATA max UDMA/133 cmd 0xe600 ctl 0xe700 bmdma 0xe808 irq 18
[   26.843111] ata4.00: ATA-6: WDC WD2500JD-00HBB0, 08.02D08, max UDMA/133
[   26.843116] ata4.00: 488397168 sectors, multi 16: LBA48 
[   26.859081] ata4.00: configured for UDMA/133
[   26.859211] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500JD-00H 08.0 PQ: 0 ANSI: 5
[   26.871353] Driver 'sd' needs updating - please use bus_type methods
[   26.871584] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   26.871603] sd 0:0:0:0: [sda] Write Protect is off
[   26.871607] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.871635] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.871707] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   26.871722] sd 0:0:0:0: [sda] Write Protect is off
[   26.871726] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.871752] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.871758]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   26.892210]  sda1
[   26.892289] sd 0:0:0:0: [sda] Attached SCSI disk
[   26.892389] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   26.892410] sd 3:0:0:0: [sdb] Write Protect is off
[   26.892414] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   26.892445] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.892522] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   26.892538] sd 3:0:0:0: [sdb] Write Protect is off
[   26.892541] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   26.892568] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.892574]  sdb: sdb1 sdb2 sdb3 sdb4
[   26.921842] sd 3:0:0:0: [sdb] Attached SCSI disk
[   26.928271] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.928304] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   26.928333] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   26.928678] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   26.928683] Uniform CD-ROM driver Revision: 3.20
[   26.928750] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   27.025076] usb 5-6: new high speed USB device using ehci_hcd and address 4
[   27.159223] usb 5-6: configuration #1 chosen from 1 choice
[   27.169804] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011066600000001]
[   27.395934] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   27.563976] usb 1-1: configuration #1 chosen from 1 choice
[   27.802665] usb 1-2: new low speed USB device using uhci_hcd and address 5
[   27.978709] usb 1-2: configuration #1 chosen from 1 choice
[   27.981853] usbcore: registered new interface driver libusual
[   27.982289] usbcore: registered new interface driver hiddev
[   28.000979] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[   28.002941] Initializing USB Mass Storage driver...
[   28.004553] scsi4 : SCSI emulation for USB Mass Storage devices
[   28.005325] usb-storage: device found at 4
[   28.005328] usb-storage: waiting for device to settle before scanning
[   28.026033] input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1
[   28.040658] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
[   28.053904] input,hidraw1: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:1d.0-2
[   28.080343] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input3
[   28.089795] input,hidraw2: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:1d.0-2
[   28.089821] usbcore: registered new interface driver usbhid
[   28.089826] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.090220] usbcore: registered new interface driver usb-storage
[   28.090226] USB Mass Storage support registered.
[   28.162712] Attempting manual resume
[   28.162717] swsusp: Resume From Partition 8:19
[   28.162718] PM: Checking swsusp image.
[   28.162871] PM: Resume from disk failed.
[   28.194467] kjournald starting.  Commit interval 5 seconds
[   28.194479] EXT3-fs: mounted filesystem with ordered data mode.
[   32.986783] usb-storage: device scan complete
[   32.988676] scsi 4:0:0:0: Direct-Access     Generic  CF Card       CF 1.4B PQ: 0 ANSI: 0 CCS
[   32.990546] scsi 4:0:0:1: Direct-Access     Generic  MS Card       MS 1.4B PQ: 0 ANSI: 0 CCS
[   32.992405] scsi 4:0:0:2: Direct-Access     Generic  SD Card   MMC/SD 1.4B PQ: 0 ANSI: 0 CCS
[   32.994474] scsi 4:0:0:3: Direct-Access     Generic  SM/XD Card    SM 1.4B PQ: 0 ANSI: 0 CCS
[   33.007664] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   33.007747] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   33.008878] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[   33.008931] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   33.010118] sd 4:0:0:2: [sde] Attached SCSI removable disk
[   33.010169] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   33.011236] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   33.011287] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   33.976611] Linux agpgart interface v0.102
[   34.164025] iTCO_vendor_support: vendor-support=0
[   34.217663] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.265451] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   34.265582] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0460)
[   34.265625] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   34.360947] input: Power Button (FF) as /devices/virtual/input/input4
[   34.379304] ACPI: Power Button (FF) [PWRF]
[   34.379448] input: Power Button (CM) as /devices/virtual/input/input5
[   34.403219] ACPI: Power Button (CM) [PWRB]
[   34.403361] input: Sleep Button (CM) as /devices/virtual/input/input6
[   34.403486] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.435133] ACPI: Sleep Button (CM) [SLPB]
[   34.516749] intel_rng: FWH not detected
[   34.797062] Linux video capture interface: v2.00
[   34.857847] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 18 (level, low) -> IRQ 19
[   35.196273] saa7130/34: v4l2 driver version 0.2.14 loaded
[   35.581663] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   35.682340] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   35.790341] [fglrx] Maximum main memory to use for locked dma buffers: 1172 MBytes.
[   35.790392] [fglrx] ASYNCIO init succeed!
[   35.791043] [fglrx] PAT is enabled successfully!
[   35.792656] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   36.543795] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   36.802329] parport_pc 00:08: reported by Plug and Play ACPI
[   36.802386] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   36.942719] NET: Registered protocol family 10
[   36.943182] lo: Disabled Privacy Extensions
[   37.804787] p54: LM86 firmware
[   37.804792] p54: FW rev 2.7.0.0 - Softmac protocol 4.1
[   38.646768] phy0: Selected rate control algorithm 'simple'
[   38.701970] phy0: hwaddr 00:07:ca:03:c2:88, isl3886
[   38.702044] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 20
[   38.702052] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   38.702058] saa7134[0]: found at 0000:03:01.0, rev: 1, irq: 20, latency: 32, mmio: 0xd0102000
[   38.702068] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
[   38.702077] saa7134[0]: board init: gpio is 0
[   38.702082] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   38.836473] saa7134[0]: i2c eeprom 00: be 16 03 00 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   38.836485] saa7134[0]: i2c eeprom 10: ff ff ff ff 15 00 0e 01 0c c0 08 00 00 00 00 00
[   38.836494] saa7134[0]: i2c eeprom 20: 00 00 00 e3 ff ff ff ff ff ff ff ff ff ff ff ff
[   38.836503] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.836512] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.836520] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.836529] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.836538] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.852422] saa7134[0] Tuner type is 38
[   38.932177] tuner 0-0043: chip found @ 0x86 (saa7134[0])
[   38.932220] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   38.932222] tuner 0-0043: type set to tda9887
[   38.948125] All bytes are equal. It is not a TEA5767
[   38.948128] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   38.948144] tuner-simple 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   38.948147] tuner 0-0060: type set to Philips PAL/SECAM m
[   38.948150] tuner-simple 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   38.948152] tuner 0-0060: type set to Philips PAL/SECAM m
[   38.950796] saa7134[0]: registered device video0 [v4l2]
[   38.950817] saa7134[0]: registered device vbi0
[   38.950838] saa7134[0]: registered device radio0
[   39.036402] saa7134 ALSA driver for DMA sound loaded
[   39.036435] saa7134[0]/alsa: saa7134[0] at 0xd0102000 irq 20 registered as card -2
[   39.060574] saa7134[0]/dvb: frontend initialization failed
[   39.953583] lp0: using parport0 (interrupt-driven).
[   40.027289] Adding 586364k swap on /dev/sdb3.  Priority:-1 extents:1 across:586364k
[   46.999183] eth0: no IPv6 routers present
[   49.559968] EXT3-fs warning: checktime reached, running e2fsck is recommended
[   49.560118] EXT3 FS on sdb2, internal journal
[   51.618565] ip_tables: (C) 2000-2006 Netfilter Core Team
[   51.961271] No dock devices found.
[   53.048788] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   53.048796] apm: disabled - APM is not SMP safe.
[   53.270863] ppdev: user-space parallel port driver
[   53.327326] audit(1233964955.505:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5631 profile="/usr/sbin/cupsd" namespace="default"
[   55.910547] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   55.911159] Bluetooth: Core ver 2.11
[   55.912195] NET: Registered protocol family 31
[   55.912202] Bluetooth: HCI device and connection manager initialized
[   55.912210] Bluetooth: HCI socket layer initialized
[   55.927131] Bluetooth: L2CAP ver 2.9
[   55.927139] Bluetooth: L2CAP socket layer initialized
[   55.982427] Bluetooth: RFCOMM socket layer initialized
[   55.982449] Bluetooth: RFCOMM TTY layer initialized
[   55.982452] Bluetooth: RFCOMM ver 1.8
[   58.046167] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   61.296841] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   61.296849] [fglrx] Reserve Block - 1 offset =  0Xffff000 length = 0X1000
[   61.296853] [fglrx] Reserve Block - 2 offset =  0X7fc0000 length = 0X40000
[   61.443012] [fglrx] interrupt source 20008000 successfully enabled
[   61.443020] [fglrx] enable ID = 0x00000004
[   61.443034] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   61.443118] [fglrx] interrupt source 10000000 successfully enabled
[   61.443123] [fglrx] enable ID = 0x00000005
[   61.443129] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000



Thats what dmesg shows me

---

### Post by yusuo85 on 2009-02-06
i dont think its the heatsink and fan as I thought it may of been that to begin with so replaced them both

---

### Post by mb_webguy on 2009-02-06
If you can remember the specific date and approximate time when your system spontaneously rebooted, you might be able to find something in /var/log/syslog about it.

---

### Post by yusuo85 on 2009-02-06
i know it happened within the last hour but specific time cant do, next time it happens i'll keep an eye out though. thanks mb_webguy

---

### Post by mb_webguy on 2009-02-06
Yeah... I've been looking through your dmesg listing, and nothing is jumping out at me as being unusual...  But then again dmesg is really only about the kernel as it's loaded at startup.  I wasn't necessarily expecting to find anything, but it's always a good place to start.

Runtime problems would more likely show up in /var/log/syslog.

---

### Post by cariboo on 2009-02-06
Do you get any errors showing up if you run in a terminal:

```
cat /var/log/syslog | error
```

Jim

---

### Post by nikgare on 2009-02-07
Is the whole system crashing, or just X ?

---

### Post by dasunst3r on 2009-02-07
Also, the next time it crashes, open your machine up and feel the heatsink.  If it's "OH, ****!!!" hot, then that means your computer's overheated.

---

### Post by mb_webguy on 2009-02-07
> **dasunst3r said:**
> Also, the next time it crashes, open your machine up and feel the heatsink.  If it's "OH, ****!!!" hot, then that means your computer's overheated.

:lolflag: Not the most scientific of methods, but it works for me...

---

### Post by txcrackers on 2009-02-07
Actually, I'd put my hand *near* the heatsink. If the CPU is overheating, that heatsink can literally burn you.

---

### Post by hikaricore on 2009-02-07
> **Bonsanto said:**
> I am windows user, I installed ubuntu in my other HDD and it crashes too much, how can I give you more info? I am totally new in this.

Your best bet is to make your own thread and post as much information about what happens as possible.

---

### Post by DigiTan on 2009-02-07
I had the exact same problem you described until yesterday.  This is what worked for me...

[LIST=1]
[*]At the boot menu, press [F6] or whichever key gives you boot options.
[*]In the command line that appears press [Home]
[*]Type in "acpi=off" without the quotes and make sure there's a space between that and the next command.
[/LIST]

...apparently a lot of users were having some kind of acpi problem related to CPU temp management.  Even with fresh Live CD copies.  It was happening with all Ubuntu versions from 6.06 to 8.10, and hit hardest those with *any* Debian base and an nForce chipset.

---

### Post by rbmorse on 2009-02-07
Another common cause of spontaneous reboots is a marginal power supply  or one that is starting to fail.

---

### Post by DigiTan on 2009-02-07
> **Bonsanto said:**
> Yeah I suposted that was my processor thanks I will try that!

Can you type the exact command please?

Sure thing.  Keep in mind I'm using Ubuntu 7.10 Live CD, so mine might be a little different.  But when I'm done changing the boot opitions, it looks like this:

Boot option **acpi=off file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --**

...The only thing typed in by me was the acpi part, everything else was already there.  If this doesn't work, one guy got his working by adding "pci=nomsi" to what I already suggested.  Two other members got theirs working by removing "quiet" and "splash" from that line, but I never had to do any of that myself.

---

### Post by DigiTan on 2009-02-07
> **Bonsanto said:**
> I open 4 firefox + a game And system crashes :)

Has this ever happened in other OS's?

---

### Post by Bonsanto on 2009-02-08
When I use Windows it doesn't happen :)

---

### Post by dargaud on 2009-02-08
Some people in this thread have mentioned CPU speed management. I'm running a low-bandwidth server 24/7. What tools are used to keep the CPU low and cool unless needed ? I'm running kubuntu 64 on AMD 64.

---

### Post by Bonsanto on 2009-02-08
How I see, I will need to return to WIndows, becouse No one knows the solution of my problem. 48 hours waiting for solution.

---

### Post by dargaud on 2009-02-08
Well, Bonsanto, I'm an ubuntu beginner myself too, but their suggestions make a lot of sense. When a system keeps rebooting, it's usually either a hardware problem (overheating) or a driver problem although the second case is rarely an issue under Linux. Have you been running Windows on that machine before ? Without trouble ?

---

### Post by DigiTan on 2009-02-08
Hey, you're lucky.  I waited almost 400 hours and no one even replied to my stuff.

Did you try my acpi=off advice?  I read all your posts and the video, and I think your Ubuntu is having CPU temperature or speed management problems.  (Like you said: WinXP works just fine).  In your BIOS, tell us if you have an option to hear an alarm when the CPU temperature is too high.  And enable it if you can.  I would also watch your CPU fan if possible to see if it's going slower than normal.  I've browsed forums for Ubuntu, Debian, and openSUSE and almost everyone who fixed their random crashes said it was because the CPU was too hot.

I've only been using Ubuntu for 2 weeks, and this strikes me as a really user-hostile OS so far.  If the CPU temp is causing failures or Linux can't manage it as well as WinXP, Ubuntu at least needs better way of alerting the user.  It's repelling a lot of prospective users.

---

### Post by DigiTan on 2009-02-08
One more thing.  A friend suggested to me you should open your pc case and disconnect everything that Linux doesn't need.  Extra video cards, extra CD drives, extra USB stuff.  Even unplug your ethernet cable.  Try it out like that for an hour, then hook and ethernet back up and tell us if it's stable.

---

### Post by Bonsanto on 2009-02-10
I reinstalled Ubuntu An watch this.

[IMG]http://i529.photobucket.com/albums/dd332/xBonsantox/08-02-09_0846.jpg[/IMG]
[IMG]http://i529.photobucket.com/albums/dd332/xBonsantox/08-02-09_0845.jpg[/IMG]

After crash read what they say:
[IMG]http://i529.photobucket.com/albums/dd332/xBonsantox/10-02-09_0848.jpg[/IMG]
[IMG]http://i529.photobucket.com/albums/dd332/xBonsantox/10-02-09_0849.jpg[/IMG]

Can someone tell me step by step how to set acpi=off?

---

### Post by mb_webguy on 2009-02-10
> **Bonsanto said:**
> I reinstalled Ubuntu An watch this.

Um... Watch what, exactly?

EDIT: Ok, *now* I see it.

---

### Post by Bonsanto on 2009-02-10
My windows XP works good :) But Ubuntu crashes

---

### Post by TheLions on 2009-02-10
can you translate it to English?

---

### Post by LowSky on 2009-02-10
Does this only happen while playing games?
As for the Evolution-alarm, that can be turned off if your not using it.

My Spanish is horrible so I making guess at what the warning says
> one has not settled correctly configured the predetermined energy settings 

> An error has occured while loading evolution alarm notify, please check configuration

Looks like you computer is over heating form using the wrong fan settings  and evolution alarm is incorrectly set up

---

### Post by JK3mp on 2009-02-10
I agree it does appear to be energy settings or something overheating..probably as stated above..cooling fans not set properly. Make sure all the BIOS settings are set to the recommended standard...

---

### Post by DigiTan on 2009-02-11
Yeah, it's saying there's been an error loading or saving the default energy setting.  Bonsanto, did you try my acpi=off steps?

---

### Post by Bonsanto on 2009-02-11
Well I reinstalled Ubuntu again. Problems detected:

1.- It always crash, snot so often than before but still crashing.
2.- When I restart I have to run Chdsrk in Windows. (soemtimes yes sometimes not)

How I st acpi =off? I don't know I am idiot I don't udnerstand when to put that. When I run the system I can't put that :(

---

