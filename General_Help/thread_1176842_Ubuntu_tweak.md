---
title: "Ubuntu tweak"
date: 2009-06-02
forum: General Help
---

### Post by noelc on 2009-06-02
Hi,

When first loaded Ubunto 8.1 (Its the only operating system on my PC) a few months ago it operatred quite quickly. Now it can take upto a minute and a half to boot up while opening programs such as as firfox can also take upto a minute to load.

I dont thinks its a hardward problem as I have 1g ram and an intel duo processor and besides orginally Ubuntu loaded quickly includeing the programs,

Is there any tweaks etc I can make which may speed this up.

Thx

---

### Post by albinootje on 2009-06-02
> **noelc said:**
> Now it can take upto a minute and a half to boot up while opening programs such as as firfox can also take upto a minute to load.


Weird, can you check the logfiles ? And post the output of :
```

dmesg

```

Firefox is a little slower for me when I have a lot of bookmarks, and some files in the Firefox profile directories sometimes grow quite big.
Can you try closing down Firefox, and then start it with a new profile :
```

firefox -P

```
And if I were you, I would test-drive a Jaunty/9.04 usb-stick or cdrom and see how slow or fast that is.

---

### Post by jerrrys on 2009-06-02
maybe time to clean your start up menu?

[http://www.ubuntugeek.com/howto-tweak-ubuntu.html](http://www.ubuntugeek.com/howto-tweak-ubuntu.html)

---

### Post by noelc on 2009-06-03
> **albinootje said:**
> Weird, can you check the logfiles ? And post the output of :
```

dmesg

```

Firefox is a little slower for me when I have a lot of bookmarks, and some files in the Firefox profile directories sometimes grow quite big.
Can you try closing down Firefox, and then start it with a new profile :
```

firefox -P

```
And if I were you, I would test-drive a Jaunty/9.04 usb-stick or cdrom and see how slow or fast that is.


Heres the out put of the log file.
[    0.480401] Time:  8:55:59  Date: 06/03/09
[    0.480440] NET: Registered protocol family 16
[    0.480472] EISA bus registered
[    0.480472] ACPI: bus type pci registered
[    0.480472] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.480472] PCI: Using configuration type 1 for base access
[    0.484659] ACPI: EC: Look up EC in DSDT
[    0.494520] ACPI: Interpreter enabled
[    0.494525] ACPI: (supports S0 S1 S3 S4 S5)
[    0.494551] ACPI: Using IOAPIC for interrupt routing
[    0.504245] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.504245] PCI: 0000:00:00.0 reg 10 32bit mmio: [f8000000, fbffffff]
[    0.504245] PCI: 0000:00:1d.0 reg 20 io port: [e000, e01f]
[    0.504292] PCI: 0000:00:1d.1 reg 20 io port: [e400, e41f]
[    0.504349] PCI: 0000:00:1d.2 reg 20 io port: [e800, e81f]
[    0.504406] PCI: 0000:00:1d.3 reg 20 io port: [ec00, ec1f]
[    0.504472] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ff27fc00, ff27ffff]
[    0.504546] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.504552] pci 0000:00:1d.7: PME# disabled
[    0.504639] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.504646] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.504651] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.504675] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.504682] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.504690] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.504697] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.504705] PCI: 0000:00:1f.1 reg 20 io port: [fc00, fc0f]
[    0.504713] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.504767] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.504815] PCI: 0000:00:1f.5 reg 10 io port: [d800, d8ff]
[    0.504822] PCI: 0000:00:1f.5 reg 14 io port: [dc00, dc3f]
[    0.504830] PCI: 0000:00:1f.5 reg 18 32bit mmio: [ff27f800, ff27f9ff]
[    0.504837] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [ff27f400, ff27f4ff]
[    0.504875] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.504880] pci 0000:00:1f.5: PME# disabled
[    0.504922] PCI: 0000:01:00.0 reg 10 32bit mmio: [e0000000, efffffff]
[    0.504929] PCI: 0000:01:00.0 reg 14 io port: [a800, a8ff]
[    0.504936] PCI: 0000:01:00.0 reg 18 32bit mmio: [ff0f0000, ff0fffff]
[    0.504954] PCI: 0000:01:00.0 reg 30 32bit mmio: [ff0c0000, ff0dffff]
[    0.504984] pci 0000:01:00.0: supports D1
[    0.504986] pci 0000:01:00.0: supports D2
[    0.505010] PCI: 0000:01:00.1 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.505017] PCI: 0000:01:00.1 reg 14 32bit mmio: [ff0e0000, ff0effff]
[    0.505058] pci 0000:01:00.1: supports D1
[    0.505060] pci 0000:01:00.1: supports D2
[    0.505102] PCI: bridge 0000:00:01.0 io port: [a000, afff]
[    0.505107] PCI: bridge 0000:00:01.0 32bit mmio: [ff000000, ff0fffff]
[    0.505112] PCI: bridge 0000:00:01.0 32bit mmio pref: [b7f00000, f7efffff]
[    0.505154] PCI: 0000:02:05.0 reg 10 io port: [b800, b8ff]
[    0.505162] PCI: 0000:02:05.0 reg 14 32bit mmio: [ff1ffc00, ff1ffcff]
[    0.505211] pci 0000:02:05.0: supports D1
[    0.505213] pci 0000:02:05.0: supports D2
[    0.505216] pci 0000:02:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.505221] pci 0000:02:05.0: PME# disabled
[    0.505255] pci 0000:00:1e.0: transparent bridge
[    0.505260] PCI: bridge 0000:00:1e.0 io port: [b000, bfff]
[    0.505266] PCI: bridge 0000:00:1e.0 32bit mmio: [ff100000, ff1fffff]
[    0.505282] bus 00 -> node 0
[    0.505292] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.505511] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.508206] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.508376] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.508547] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.508718] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.508895] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.509067] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.509236] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.509413] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.512122] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - E5, should be D8 [20080609]
[    0.512135] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.512155] pnp: PnP ACPI init
[    0.512155] ACPI: bus type pnp registered
[    0.520092] pnp: PnP ACPI: found 13 devices
[    0.520096] ACPI: ACPI bus type pnp unregistered
[    0.520101] PnPBIOS: Disabled by ACPI PNP
[    0.520128] PCI: Using ACPI for IRQ routing
[    0.524051] NET: Registered protocol family 8
[    0.524055] NET: Registered protocol family 20
[    0.524080] NetLabel: Initializing
[    0.524080] NetLabel:  domain hash size = 128
[    0.524080] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.524087] NetLabel:  unlabeled traffic allowed by default
[    0.524171] hpet clockevent registered
[    0.524177] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.524184] hpet0: 3 64-bit timers, 14318180 Hz
[    0.526498] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.526501]    actual entries 65620
[    0.526658] AppArmor: AppArmor Filesystem Enabled
[    0.526679] ACPI: RTC can wake from S4
[    0.528521] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.528525] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.528529] system 00:07: ioport range 0x480-0x4bf has been reserved
[    0.528533] system 00:07: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.528537] system 00:07: iomem range 0xff380000-0xffefffff could not be reserved
[    0.528547] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.528551] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.528563] system 00:0b: ioport range 0x680-0x6ff has been reserved
[    0.528566] system 00:0b: ioport range 0x295-0x296 has been reserved
[    0.528575] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.528578] system 00:0c: iomem range 0xc0000-0xdffff could not be reserved
[    0.528582] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.528585] system 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[    0.528589] system 00:0c: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.564134] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.564139] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.564145] pci 0000:00:01.0:   MEM window: 0xff000000-0xff0fffff
[    0.564151] pci 0000:00:01.0:   PREFETCH window: 0x000000b7f00000-0x000000f7efffff
[    0.564158] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.564162] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.564169] pci 0000:00:1e.0:   MEM window: 0xff100000-0xff1fffff
[    0.564174] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.564195] pci 0000:00:1e.0: setting latency timer to 64
[    0.564200] bus: 00 index 0 io port: [0, ffff]
[    0.564203] bus: 00 index 1 mmio: [0, ffffffff]
[    0.564206] bus: 01 index 0 io port: [a000, afff]
[    0.564209] bus: 01 index 1 mmio: [ff000000, ff0fffff]
[    0.564212] bus: 01 index 2 mmio: [b7f00000, f7efffff]
[    0.564214] bus: 01 index 3 mmio: [0, 0]
[    0.564217] bus: 02 index 0 io port: [b000, bfff]
[    0.564219] bus: 02 index 1 mmio: [ff100000, ff1fffff]
[    0.564222] bus: 02 index 2 mmio: [0, 0]
[    0.564224] bus: 02 index 3 io port: [0, ffff]
[    0.564227] bus: 02 index 4 mmio: [0, ffffffff]
[    0.564240] NET: Registered protocol family 2
[    0.576573] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.576945] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.577442] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.577753] TCP: Hash tables configured (established 131072 bind 65536)
[    0.577757] TCP reno registered
[    0.580637] NET: Registered protocol family 1
[    0.580809] checking if image is initramfs... it is
[    1.024528] Switched to high resolution mode on CPU 1
[    1.028074] Switched to high resolution mode on CPU 0
[    1.257897] Freeing initrd memory: 8017k freed
[    1.259739] audit: initializing netlink socket (disabled)
[    1.259761] type=2000 audit(1244019359.256:1): initialized
[    1.265551] highmem bounce pool size: 64 pages
[    1.265562] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.269548] VFS: Disk quotas dquot_6.5.1
[    1.269687] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.269852] msgmni has been set to 1743
[    1.270053] io scheduler noop registered
[    1.270057] io scheduler anticipatory registered
[    1.270060] io scheduler deadline registered
[    1.270076] io scheduler cfq registered (default)
[    1.270191] pci 0000:01:00.0: Boot video device
[    1.270856] isapnp: Scanning for PnP cards...
[    1.622552] isapnp: No Plug & Play device found
[    1.684291] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.684453] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.685538] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.688824] brd: module loaded
[    1.688933] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.689135] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.689140] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.689634] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.696708] mice: PS/2 mouse device common for all mice
[    1.696926] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.696951] rtc0: alarms up to one month, hpet irqs
[    1.697173] EISA: Probing bus 0 at eisa.0
[    1.697213] EISA: Detected 0 cards.
[    1.697219] cpuidle: using governor ladder
[    1.697222] cpuidle: using governor menu
[    1.697982] TCP cubic registered
[    1.698022] Using IPI No-Shortcut mode
[    1.698352] registered taskstats version 1
[    1.698504]   Magic number: 13:959:926
[    1.698573] tty ptyxb: hash matches
[    1.698655] rtc_cmos 00:02: setting system clock to 2009-06-03 08:56:01 UTC (1244019361)
[    1.698659] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.698662] EDD information not available.
[    1.698994] Freeing unused kernel memory: 428k freed
[    1.699058] Write protecting the kernel text: 2580k
[    1.699097] Write protecting the kernel read-only data: 940k
[    1.720076] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.892152] fuse init (API version 7.9)
[    2.044045] processor ACPI0007:00: registered as cooling_device0
[    2.044054] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.048042] processor ACPI0007:01: registered as cooling_device1
[    2.376139] usbcore: registered new interface driver usbfs
[    2.376180] usbcore: registered new interface driver hub
[    2.376269] usbcore: registered new device driver usb
[    2.404732] USB Universal Host Controller Interface driver v3.0
[    2.404806] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.404819] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.404825] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.404892] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.404934] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000
[    2.405185] usb usb1: configuration #1 chosen from 1 choice
[    2.405233] hub 1-0:1.0: USB hub found
[    2.405246] hub 1-0:1.0: 2 ports detected
[    2.612453] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.612470] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.612477] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.612529] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.612570] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[    2.612754] usb usb2: configuration #1 chosen from 1 choice
[    2.612810] hub 2-0:1.0: USB hub found
[    2.612824] hub 2-0:1.0: 2 ports detected
[    2.716406] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.716424] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.716431] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.716479] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.716523] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    2.716701] usb usb3: configuration #1 chosen from 1 choice
[    2.716757] hub 3-0:1.0: USB hub found
[    2.716771] hub 3-0:1.0: 2 ports detected
[    2.724049] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    2.754975] Floppy drive(s): fd0 is 1.44M
[    2.758989] No dock devices found.
[    2.817612] FDC 0 is a post-1991 82077
[    2.829182] SCSI subsystem initialized
[    2.835842] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.868684] 8139too Fast Ethernet driver 0.9.28
[    2.916221] usb 1-2: configuration #1 chosen from 1 choice
[    2.924390] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.924406] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.924413] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.924463] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.924500] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[    2.924682] usb usb4: configuration #1 chosen from 1 choice
[    2.924738] hub 4-0:1.0: USB hub found
[    2.924752] hub 4-0:1.0: 2 ports detected
[    2.925304] libata version 3.00 loaded.
[    3.036060] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    3.132591] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.132620] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.132629] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.132701] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.136615] ehci_hcd 0000:00:1d.7: debug port 1
[    3.136629] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.136661] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff27fc00
[    3.164535] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.164853] usb usb5: configuration #1 chosen from 1 choice
[    3.164918] hub 5-0:1.0: USB hub found
[    3.164937] hub 5-0:1.0: 8 ports detected
[    3.375349] 8139too 0000:02:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.376367] eth0: RealTek RTL8139 at 0xb800, 00:19:66:2c:88:07, IRQ 22
[    3.376373] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.383248] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.406921] ata_piix 0000:00:1f.1: version 2.12
[    3.406943] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.407008] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.407157] scsi0 : ata_piix
[    3.407364] scsi1 : ata_piix
[    3.411628] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    3.411637] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    3.560529] usb 3-1: device not accepting address 2, error -71
[    3.574179] ata1.00: ATA-6: WDC WD1600BB-00GUA0, 08.02D08, max UDMA/100
[    3.574189] ata1.00: 312581808 sectors, multi 16: LBA48 
[    3.598661] ata1.00: configured for UDMA/100
[    3.616586] hub 3-0:1.0: unable to enumerate USB device on port 1
[    3.768315] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A102, max UDMA/33
[    3.768350] ata2.01: ATAPI: ATAPI 16X DVDROM, OM   VA1, max UDMA/33
[    3.784242] ata2.00: configured for UDMA/33
[    3.800245] ata2.01: configured for UDMA/33
[    3.800415] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BB-00G 08.0 PQ: 0 ANSI: 5
[    3.804305] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A102 PQ: 0 ANSI: 5
[    3.805193] scsi 1:0:1:0: CD-ROM            ATAPI 16 X DVDROM   VA100 A100 PQ: 0 ANSI: 5
[    3.822240] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.822331] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    3.822408] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    3.853044] Driver 'sd' needs updating - please use bus_type methods
[    3.853266] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    3.853305] sd 0:0:0:0: [sda] Write Protect is off
[    3.853311] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.853371] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.853508] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    3.853549] sd 0:0:0:0: [sda] Write Protect is off
[    3.853557] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.853618] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.853629]  sda:<6>usb 5-2: new high speed USB device using ehci_hcd and address 2
[    3.858575] Driver 'sr' needs updating - please use bus_type methods
[    3.873137]  sda1 sda2 < sda5 >
[    3.891624] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.905554] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.905563] Uniform CD-ROM driver Revision: 3.20
[    3.905746] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.908132] sr1: scsi3-mmc drive: 12x/48x cd/rw xa/form2 cdda tray
[    3.908299] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    3.989647] usb 5-2: configuration #1 chosen from 1 choice
[    4.156030] usb 5-7: new high speed USB device using ehci_hcd and address 4
[    4.291115] usb 5-7: configuration #1 chosen from 1 choice
[    4.294010] usbcore: registered new interface driver libusual
[    4.304961] usb 1-2: USB disconnect, address 2
[    4.311839] Initializing USB Mass Storage driver...
[    4.382893] PM: Starting manual resume from disk
[    4.382899] PM: Resume from partition 8:5
[    4.382902] PM: Checking hibernation image.
[    4.383073] PM: Resume from disk failed.
[    4.443329] kjournald starting.  Commit interval 5 seconds
[    4.443341] EXT3-fs: mounted filesystem with ordered data mode.
[    4.672023] usb 3-1: new low speed USB device using uhci_hcd and address 4
[    4.848456] usb 3-1: configuration #1 chosen from 1 choice
[    4.851625] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.851742] usb-storage: device found at 2
[    4.851748] usb-storage: waiting for device to settle before scanning
[    4.851856] scsi3 : SCSI emulation for USB Mass Storage devices
[    4.851956] usb-storage: device found at 4
[    4.851961] usb-storage: waiting for device to settle before scanning
[    4.851990] usbcore: registered new interface driver usb-storage
[    4.851996] USB Mass Storage support registered.
[    9.848259] usb-storage: device scan complete
[    9.848327] usb-storage: device scan complete
[    9.848869] scsi 2:0:0:0: Direct-Access     HP       Photosmart C3180 1.00 PQ: 0 ANSI: 2
[   10.018708] scsi 3:0:0:0: Direct-Access     USB2.0   CF Card       CF 1.6E PQ: 0 ANSI: 0 CCS
[   10.020453] scsi 3:0:0:1: Direct-Access     USB2.0   MULTI Card    MS 1.6E PQ: 0 ANSI: 0 CCS
[   10.021810] sd 3:0:0:0: [sdb] 2030112 512-byte hardware sectors (1039 MB)
[   10.022933] sd 3:0:0:0: [sdb] Write Protect is off
[   10.022938] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 08
[   10.022941] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   10.025061] sd 3:0:0:0: [sdb] 2030112 512-byte hardware sectors (1039 MB)
[   10.026185] sd 3:0:0:0: [sdb] Write Protect is off
[   10.026190] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 08
[   10.026193] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   10.026197]  sdb: sdb1
[   10.027697] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   10.027866] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   10.028894] sd 3:0:0:1: [sdc] Attached SCSI removable disk
[   10.028969] sd 3:0:0:1: Attached scsi generic sg4 type 0
[   10.029770] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[   10.029852] sd 2:0:0:0: Attached scsi generic sg5 type 0
[   10.870740] udevd version 124 started
[   11.410446] Linux agpgart interface v0.103
[   11.536775] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   11.540774] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   11.680726] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.702232] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.165445] intel_rng: FWH not detected
[   12.232906] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.252718] ACPI: Power Button (FF) [PWRF]
[   12.252930] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.272704] iTCO_vendor_support: vendor-support=0
[   12.284551] ACPI: Power Button (CM) [PWRB]
[   12.291057] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   12.292024] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   12.292217] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.434801] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   12.712529] [fglrx] Maximum main memory to use for locked dma buffers: 1896 MBytes.
[   12.712983] [fglrx]   vendor: 1002 device: 4153 count: 1
[   12.714425] [fglrx] ioport: bar 1, base 0xa800, size: 0x100
[   12.714448] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.716196] [fglrx] PAT is enabled successfully!
[   12.716259] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   13.167601] parport_pc 00:06: reported by Plug and Play ACPI
[   13.167703] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   13.836477] usbcore: registered new interface driver hiddev
[   13.858463] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input4
[   13.884818] input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.2-1
[   13.884866] usbcore: registered new interface driver usbhid
[   13.884874] usbhid: v2.6:USB HID core driver
[   13.909390] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5611
[   13.909439] usbcore: registered new interface driver usblp
[   13.971231] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.813597] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.813629] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   15.136558] intel8x0_measure_ac97_clock: measured 55569 usecs
[   15.136565] intel8x0: clocking to 48000
[   20.739693] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.739700] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   20.739706] sr 1:0:1:0: [sr1] Add. Sense: L-EC uncorrectable error
[   20.739714] end_request: I/O error, dev sr1, sector 1321472
[   20.739720] Buffer I/O error on device sr1, logical block 165184
[   26.783274] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   26.783279] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   26.783285] sr 1:0:1:0: [sr1] Add. Sense: L-EC uncorrectable error
[   26.783290] end_request: I/O error, dev sr1, sector 1321472
[   26.783295] Buffer I/O error on device sr1, logical block 165184
[   32.826793] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   32.826799] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   32.826804] sr 1:0:1:0: [sr1] Add. Sense: L-EC uncorrectable error
[   32.826810] end_request: I/O error, dev sr1, sector 1321688
[   32.826814] Buffer I/O error on device sr1, logical block 165211
[   38.870265] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   38.870270] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   38.870275] sr 1:0:1:0: [sr1] Add. Sense: L-EC uncorrectable error
[   38.870281] end_request: I/O error, dev sr1, sector 1321688
[   38.870285] Buffer I/O error on device sr1, logical block 165211
[   45.256107] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   45.256112] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   45.256118] sr 1:0:1:0: [sr1] Add. Sense: L-EC uncorrectable error
[   45.256123] end_request: I/O error, dev sr1, sector 1321696
[   45.256127] Buffer I/O error on device sr1, logical block 165212
[   51.299364] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   51.299369] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   51.299374] sr 1:0:1:0: [sr1] Add. Sense: L-EC uncorrectable error
[   51.299380] end_request: I/O error, dev sr1, sector 1321696
[   51.299384] Buffer I/O error on device sr1, logical block 165212
[   57.342600] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   57.342605] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   57.342610] sr 1:0:1:0: [sr1] Add. Sense: L-EC uncorrectable error
[   57.342616] end_request: I/O error, dev sr1, sector 1321696
[   57.342620] Buffer I/O error on device sr1, logical block 165212
[   63.385675] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   63.385680] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   63.385686] sr 1:0:1:0: [sr1] Add. Sense: L-EC uncorrectable error
[   63.385691] end_request: I/O error, dev sr1, sector 1321696
[   63.385695] Buffer I/O error on device sr1, logical block 165212
[   68.883694] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   68.883700] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   68.883705] sr 1:0:1:0: [sr1] Add. Sense: L-EC uncorrectable error
[   68.883710] end_request: I/O error, dev sr1, sector 1321696
[   68.883715] Buffer I/O error on device sr1, logical block 165212
[   71.973313] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   71.973319] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   71.973324] sr 1:0:1:0: [sr1] Add. Sense: L-EC uncorrectable error
[   71.973330] end_request: I/O error, dev sr1, sector 1321640
[   71.973334] Buffer I/O error on device sr1, logical block 165205
[   72.810536] lp0: using parport0 (interrupt-driven).
[   73.005329] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
[   73.580231] EXT3 FS on sda1, internal journal
[   74.780680] type=1505 audit(1244019434.112:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4135
[   74.975345] type=1505 audit(1244019434.304:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4140
[   74.975611] type=1505 audit(1244019434.304:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4140
[   75.190125] ip_tables: (C) 2000-2006 Netfilter Core Team
[   75.248374] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   75.248573] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   75.248577] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   75.248580] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   75.408880] NET: Registered protocol family 10
[   75.409772] lo: Disabled Privacy Extensions
[   75.429304] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   76.976968] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   77.289961] ppdev: user-space parallel port driver
[   81.540034] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   81.540039] vboxdrv: Successfully done.
[   81.540041] vboxdrv: Found 2 processor cores.
[   81.540236] vboxdrv: fAsync=0 offMin=0x689 offMax=0x252d
[   81.540305] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   81.540308] vboxdrv: Successfully loaded version 2.2.2 (interface 0x000a0009).
[   87.048751] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[   88.440904] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   88.578664] NET: Registered protocol family 17
[   90.490565] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   90.490592] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   90.490645] fglrx_pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   90.490671] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   90.490757] [fglrx] Setup AGP aperture
[   90.491393] [fglrx] GART Table is not in FRAME_BUFFER range 
[   90.496873] [fglrx] CMM init INV FB MC:0xe8000000, length:0x8000000
[   90.496885] [fglrx] Reserved FB block: Shared offset:0, size:40000 
[   99.024035] eth0: no IPv6 routers present
[  110.142361] ISO 9660 Extensions: Microsoft Joliet Level 3
[  110.256009] ISOFS: changing to secondary root
[  187.393376] ppdev0: registered pardevice
[  187.440657] ppdev0: unregistered pardevice
[  189.783217] ppdev0: registered pardevice
[  189.832762] ppdev0: unregistered pardevice
[  189.900211] ppdev0: registered pardevice
[  189.948047] ppdev0: unregistered pardevice

---

