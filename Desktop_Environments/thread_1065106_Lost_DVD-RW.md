---
title: "Lost DVD-RW"
date: 2009-02-09
forum: Desktop Environments
---

### Post by marcgh on 2009-02-09
Hi,

I'm not sure I am here in the correct forum, please correct me if I am wrong.

I was running Ubuntu 8.10 without problems till yesterday evening.

To try to solve some dongle issues on a specific software I installed VIRTUAL BOX. Installed XP on top of it + the guest additions for the USB dongle.

Since that moment I have lost both in UBUNTU and Virtualbox(XP) my DVD writer. Any CD or DVD I insert result in "**UNABLE TO MOUNT LOCATION**"

I observed also that if I mount one of the other HDD, it will effectively mount and I will be able to open files in that HDD but at the same time I get the following weird error: 
"**UNABLE TO MOUNT LOCATION - INTERNAL ERROR: NO MOUNT OBJECT FOR MOUNTED VOLUME**"

Since I am dual booting I booted in Windows XP and could read as usual on that same drive. So i am pretty sure it's not the drive.

Attached 2 screenshots - if it helps.



All help will be highly appreciated.

Marc

---

### Post by marcgh on 2009-02-10
Anybody ?

---

### Post by marcgh on 2009-02-11
Nobody?
I am Unique in my problems?

---

### Post by marcgh on 2009-02-11
BUMP.....
I need my dvd back!

---

### Post by marcgh on 2009-02-12
Come on, 78 vieuws and nobody has any idea?
Help please...

---

### Post by Neural oD on 2009-02-12
maybe something's gone wrong in the fstab file - post the contents of your fstab file - found in /etc/fstab

---

### Post by Neural oD on 2009-02-12
the line in my fstab looks like this
```
dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

yours should be similar

---

### Post by marcgh on 2009-02-12
Hi Neural oD
Thanks for your reply.
I did as you said and the result looks similar to your fstab.
Anything else I can do?

---

### Post by Neural oD on 2009-02-13
pop in a dvd - then on the command line type in dmesg
Post the relevant info here - all you need to do is highlight the code and then when you post here wrap it in code blocks ```
 your copied data goes here 
```

once u've highlighted you can past by using the middle mouse button.

So to sumarize - put your dmesg in here once you've put in a dvd

---

### Post by marcgh on 2009-02-13
Hi,
Thanks for helping me.
This is the result of **dmesg** with a DVD (video) inserted :


[HTML][    0.456282] PCI: bridge 0000:00:03.0 io port: [e000, efff]
[    0.456285] PCI: bridge 0000:00:03.0 32bit mmio: [feb00000, febfffff]
[    0.456288] PCI: bridge 0000:00:03.0 64bit mmio pref: [d0000000, dfffffff]
[    0.456473] pci 0000:00:10.0: transparent bridge
[    0.456548] bus 00 -> node 0
[    0.456553] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.456832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.456963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.457061] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PB._PRT]
[    0.457158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.468361] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.468852] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.469483] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.470114] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.470744] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10
[    0.472171] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *15
[    0.472754] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.473384] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.474015] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.474597] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15
[    0.475180] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.475767] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.476325] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.476959] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.478549] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.479135] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.479765] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *7
[    0.480375] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *10
[    0.480998] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.481480] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 35, should be 34 [20080609]
[    0.481480] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.481480] pnp: PnP ACPI init
[    0.481480] ACPI: bus type pnp registered
[    0.485146] pnp: PnP ACPI: found 14 devices
[    0.485200] ACPI: ACPI bus type pnp unregistered
[    0.485255] PnPBIOS: Disabled by ACPI PNP
[    0.485320] PCI: Using ACPI for IRQ routing
[    0.492045] NET: Registered protocol family 8
[    0.492108] NET: Registered protocol family 20
[    0.492180] NetLabel: Initializing
[    0.492180] NetLabel:  domain hash size = 128
[    0.492180] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.492214] NetLabel:  unlabeled traffic allowed by default
[    0.492277] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.492522] hpet0: 3 32-bit timers, 25000000 Hz
[    0.494292] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.494347]    actual entries 65620
[    0.494481] AppArmor: AppArmor Filesystem Enabled
[    0.494566] ACPI: RTC can wake from S4
[    0.500070] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.500139] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.500195] system 00:06: ioport range 0x4000-0x407f has been reserved
[    0.500250] system 00:06: ioport range 0x4080-0x40ff has been reserved
[    0.500306] system 00:06: ioport range 0x4400-0x447f has been reserved
[    0.500362] system 00:06: ioport range 0x4480-0x44ff has been reserved
[    0.500417] system 00:06: ioport range 0x4800-0x487f has been reserved
[    0.500472] system 00:06: ioport range 0x4880-0x48ff has been reserved
[    0.500528] system 00:06: ioport range 0x2000-0x207f has been reserved
[    0.500584] system 00:06: ioport range 0x2080-0x20ff has been reserved
[    0.500640] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.500699] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.500759] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.500822] system 00:0b: ioport range 0xa00-0xadf has been reserved
[    0.500877] system 00:0b: ioport range 0xae0-0xaef has been reserved
[    0.500935] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.500993] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.501049] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.501071] Switched to high resolution mode on CPU 1
[    0.501107] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.501163] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[    0.501223] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.504033] Switched to high resolution mode on CPU 0
[    0.536236] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.536292] pci 0000:00:03.0:   IO window: 0xe000-0xefff
[    0.536348] pci 0000:00:03.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.536405] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.536466] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.536521] pci 0000:00:06.0:   IO window: disabled
[    0.536577] pci 0000:00:06.0:   MEM window: disabled
[    0.536632] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.536689] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.536744] pci 0000:00:07.0:   IO window: disabled
[    0.536800] pci 0000:00:07.0:   MEM window: disabled
[    0.536855] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.536912] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.536966] pci 0000:00:10.0:   IO window: disabled
[    0.537024] pci 0000:00:10.0:   MEM window: disabled
[    0.537081] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.537146] pci 0000:00:03.0: setting latency timer to 64
[    0.537152] pci 0000:00:06.0: setting latency timer to 64
[    0.537157] pci 0000:00:07.0: setting latency timer to 64
[    0.537163] pci 0000:00:10.0: setting latency timer to 64
[    0.537167] bus: 00 index 0 io port: [0, ffff]
[    0.537221] bus: 00 index 1 mmio: [0, ffffffff]
[    0.537275] bus: 01 index 0 io port: [e000, efff]
[    0.537329] bus: 01 index 1 mmio: [feb00000, febfffff]
[    0.537384] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.537438] bus: 01 index 3 mmio: [0, 0]
[    0.537492] bus: 02 index 0 mmio: [0, 0]
[    0.537546] bus: 02 index 1 mmio: [0, 0]
[    0.537599] bus: 02 index 2 mmio: [0, 0]
[    0.537653] bus: 02 index 3 mmio: [0, 0]
[    0.537706] bus: 03 index 0 mmio: [0, 0]
[    0.537760] bus: 03 index 1 mmio: [0, 0]
[    0.537813] bus: 03 index 2 mmio: [0, 0]
[    0.537867] bus: 03 index 3 mmio: [0, 0]
[    0.537921] bus: 04 index 0 mmio: [0, 0]
[    0.537974] bus: 04 index 1 mmio: [0, 0]
[    0.538028] bus: 04 index 2 mmio: [0, 0]
[    0.538082] bus: 04 index 3 io port: [0, ffff]
[    0.538135] bus: 04 index 4 mmio: [0, ffffffff]
[    0.538194] NET: Registered protocol family 2
[    0.552079] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.552333] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.552708] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.552956] TCP: Hash tables configured (established 131072 bind 65536)
[    0.553012] TCP reno registered
[    0.560104] NET: Registered protocol family 1
[    0.560247] checking if image is initramfs... it is
[    1.133670] Freeing initrd memory: 8813k freed
[    1.134620] audit: initializing netlink socket (disabled)
[    1.134696] type=2000 audit(1234550474.132:1): initialized
[    1.139553] highmem bounce pool size: 64 pages
[    1.139610] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.141431] VFS: Disk quotas dquot_6.5.1
[    1.141546] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.141678] msgmni has been set to 1743
[    1.141823] io scheduler noop registered
[    1.141877] io scheduler anticipatory registered
[    1.141932] io scheduler deadline registered
[    1.141993] io scheduler cfq registered (default)
[    1.142198] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:06.0: Disabling HT MSI mapping<6>pci 0000:00:07.0: Disabling HT MSI mapping<6>pci 0000:00:09.0: Disabling HT MSI mapping<6>pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:10.0: Disabling HT MSI mapping<6>pci 0000:00:10.1: Disabling HT MSI mapping<7>pci 0000:01:00.0: Boot video device
[    1.164947] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.164982] pcieport-driver 0000:00:03.0: found MSI capability
[    1.165063] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.165094] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.165163] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.165197] pcieport-driver 0000:00:06.0: found MSI capability
[    1.165274] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.165306] pci_express 0000:00:06.0:pcie03: allocate port service
[    1.165375] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.165408] pcieport-driver 0000:00:07.0: found MSI capability
[    1.165485] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.165513] pci_express 0000:00:07.0:pcie03: allocate port service
[    1.165759] isapnp: Scanning for PnP cards...
[    1.519552] isapnp: No Plug & Play device found
[    1.544234] hpet_resources: 0xfed00000 is busy
[    1.544301] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.544561] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.545193] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.546552] brd: module loaded
[    1.546655] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.546802] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.548854] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.548912] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.552137] mice: PS/2 mouse device common for all mice
[    1.552287] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.552373] rtc0: alarms up to one year, y3k, hpet irqs
[    1.552528] EISA: Probing bus 0 at eisa.0
[    1.552590] Cannot allocate resource for EISA slot 2
[    1.552648] Cannot allocate resource for EISA slot 4
[    1.552703] Cannot allocate resource for EISA slot 5
[    1.552757] Cannot allocate resource for EISA slot 6
[    1.552819] EISA: Detected 0 cards.
[    1.552873] cpuidle: using governor ladder
[    1.552928] cpuidle: using governor menu
[    1.553380] TCP cubic registered
[    1.553455] Using IPI No-Shortcut mode
[    1.553639] registered taskstats version 1
[    1.553806]   Magic number: 13:991:695
[    1.553909] pci 0000:00:00.0: hash matches
[    1.554001] rtc_cmos 00:02: setting system clock to 2009-02-13 18:41:15 UTC (1234550475)
[    1.554062] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.554116] EDD information not available.
[    1.554384] Freeing unused kernel memory: 424k freed
[    1.554466] Write protecting the kernel text: 2580k
[    1.554539] Write protecting the kernel read-only data: 940k
[    1.586720] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.668538] fuse init (API version 7.9)
[    1.692906] ACPI: SSDT 7FFCE0B0, 0277 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    1.693362] processor ACPI0007:00: registered as cooling_device0
[    1.693678] ACPI: SSDT 7FFCE330, 0277 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    1.694110] processor ACPI0007:01: registered as cooling_device1
[    2.213476] usbcore: registered new interface driver usbfs
[    2.213496] usbcore: registered new interface driver hub
[    2.213532] usbcore: registered new device driver usb
[    2.213648] No dock devices found.
[    2.255027] SCSI subsystem initialized
[    2.268060] libata version 3.00 loaded.
[    2.269978] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.270291] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    2.270300] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    2.270306] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.270328] nv_probe: set workaround bit for reversed mac addr
[    2.272487] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.280107] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.789474] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x1c1 @ 1, addr 00:19:db:f7:47:9f
[    2.789479] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[    2.790331] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22
[    2.790339] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUB0] -> GSI 22 (level, low) -> IRQ 22
[    2.790352] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.790355] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.790393] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.790412] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xfeaff000
[    2.846122] usb usb1: configuration #1 chosen from 1 choice
[    2.846148] hub 1-0:1.0: USB hub found
[    2.846157] hub 1-0:1.0: 8 ports detected
[    2.948481] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    2.948486] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    2.948495] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.948498] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.948517] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    2.948545] ehci_hcd 0000:00:0b.1: debug port 1
[    2.948551] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    2.948561] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfeafec00
[    2.960014] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.960118] usb usb2: configuration #1 chosen from 1 choice
[    2.960139] hub 2-0:1.0: USB hub found
[    2.960145] hub 2-0:1.0: 8 ports detected
[    3.064155] pata_amd 0000:00:0d.0: version 0.3.10
[    3.064196] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.064257] scsi0 : pata_amd
[    3.064326] scsi1 : pata_amd
[    3.065334] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.065336] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.228595] ata1.00: ATA-7: ST3250823A, 3.06, max UDMA/100
[    3.228601] ata1.00: 488397168 sectors, multi 16: LBA48 
[    3.228626] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:900:0x11)
[    3.244527] ata1.00: configured for UDMA/100
[    3.244571] ata2: port disabled. ignoring.
[    3.244670] scsi 0:0:0:0: Direct-Access     ATA      ST3250823A       3.06 PQ: 0 ANSI: 5
[    3.244744] sata_nv 0000:00:0e.0: version 3.5
[    3.245027] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
[    3.245032] sata_nv 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[    3.245035] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.245072] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.245175] scsi2 : sata_nv
[    3.245234] scsi3 : sata_nv
[    3.245352] ata3: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 20
[    3.245355] ata4: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 20
[    3.712057] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.720513] ata3.00: ATA-7: Hitachi HDS721616PLA380, P22OABEA, max UDMA/133
[    3.720518] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.736881] ata3.00: configured for UDMA/133
[    4.204057] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.228486] ata4.00: ATA-7: Hitachi HDS721616PLA380, P22OABEA, max UDMA/133
[    4.228491] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.244501] ata4.00: configured for UDMA/133
[    4.244592] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[    4.244695] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[    4.245657] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 23
[    4.245661] sata_nv 0000:00:0f.0: PCI INT A -> Link[LSA1] -> GSI 23 (level, low) -> IRQ 23
[    4.245663] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    4.245700] sata_nv 0000:00:0f.0: setting latency timer to 64
[    4.245803] scsi4 : sata_nv
[    4.246075] scsi5 : sata_nv
[    4.246200] ata5: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 23
[    4.246203] ata6: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 23
[    4.712056] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.754390] ata5.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[    4.754395] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.821045] ata5.00: configured for UDMA/133
[    5.288056] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.312301] ata6.00: ATAPI: ATAPI   DVD A  DH16A1L, KH1A, max UDMA/33
[    5.344311] ata6.00: configured for UDMA/33
[    5.344380] scsi 4:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    5.345579] scsi 5:0:0:0: CD-ROM            ATAPI    DVD A  DH16A1L   KH1A PQ: 0 ANSI: 5
[    5.361030] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.361062] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    5.361089] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[    5.361116] scsi 4:0:0:0: Attached scsi generic sg3 type 0
[    5.361143] scsi 5:0:0:0: Attached scsi generic sg4 type 5
[    5.380100] Driver 'sd' needs updating - please use bus_type methods
[    5.380183] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.380196] sd 0:0:0:0: [sda] Write Protect is off
[    5.380198] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.380217] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.380270] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.380281] sd 0:0:0:0: [sda] Write Protect is off
[    5.380283] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.380302] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.380305]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.400383]  sda1
[    5.400485] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.400558] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[    5.400571] sd 2:0:0:0: [sdb] Write Protect is off
[    5.400573] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.400594] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.400640] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[    5.400651] sd 2:0:0:0: [sdb] Write Protect is off
[    5.400653] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.400674] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.400676]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    5.449961] sd 2:0:0:0: [sdb] Attached SCSI disk
[    5.450010] sd 3:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[    5.450023] sd 3:0:0:0: [sdc] Write Protect is off
[    5.450025] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.450045] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.450091] sd 3:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[    5.450103] sd 3:0:0:0: [sdc] Write Protect is off
[    5.450105] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.450125] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.450128]  sdc: sdc1
[    5.465054] sd 3:0:0:0: [sdc] Attached SCSI disk
[    5.465107] sd 4:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[    5.465120] sd 4:0:0:0: [sdd] Write Protect is off
[    5.465122] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    5.465142] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.465182] sd 4:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[    5.465194] sd 4:0:0:0: [sdd] Write Protect is off
[    5.465196] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    5.465216] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.465218]  sdd: sdd1
[    5.485514] sd 4:0:0:0: [sdd] Attached SCSI disk
[    5.498473] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.498478] Uniform CD-ROM driver Revision: 3.20
[    5.498556] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    5.757056] PM: Starting manual resume from disk
[    5.757060] PM: Resume from partition 8:22
[    5.757061] PM: Checking hibernation image.
[    5.757228] PM: Resume from disk failed.
[    5.806704] kjournald starting.  Commit interval 5 seconds
[    5.806720] EXT3-fs: mounted filesystem with ordered data mode.
[   11.245845] udevd version 124 started
[   11.600614] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.632930] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.732670] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   11.732697] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x6000
[   11.791108] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   11.816027] ACPI: Power Button (FF) [PWRF]
[   11.816124] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   11.848027] ACPI: Power Button (CM) [PWRB]
[   12.172614] Linux agpgart interface v0.103
[   12.242398] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   12.269921] [fglrx] Maximum main memory to use for locked dma buffers: 1896 MBytes.
[   12.270616] [fglrx]   vendor: 1002 device: 9442 count: 1
[   12.271725] [fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   12.272042] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 19
[   12.272049] pci 0000:01:00.0: PCI INT A -> Link[LNEA] -> GSI 19 (level, low) -> IRQ 19
[   12.272054] pci 0000:01:00.0: setting latency timer to 64
[   12.273410] [fglrx] Driver built-in PAT support is enabled successfully
[   12.274060] [fglrx] module loaded - fglrx 8.57.2 [Jan 14 2009] with 1 minors
[   12.407901] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   13.160328] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   13.183357] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   13.183363] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   13.183383] HDA Intel 0000:00:10.1: setting latency timer to 64
[   13.214854] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.252046] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 18
[   13.252054] HDA Intel 0000:01:00.1: PCI INT B -> Link[LNEB] -> GSI 18 (level, low) -> IRQ 18
[   13.252082] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.172162] lp: driver loaded but no devices found
[   14.202002] f71882fg: Not a Fintek device
[   14.202053] f71882fg: Found F71882FG chip at 0xa00, revision 32
[   14.208556] coretemp coretemp.0: Using relative temperature scale!
[   14.208590] coretemp coretemp.1: Using relative temperature scale!
[   14.429927] Adding 2618552k swap on /dev/sdb6.  Priority:-1 extents:1 across:2618552k
[   14.986519] EXT3 FS on sdb5, internal journal
[   15.133263] device-mapper: uevent: version 1.0.3
[   15.133396] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   16.034854] type=1505 audit(1234550489.975:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4344
[   16.082417] type=1505 audit(1234550490.023:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4349
[   16.208339] type=1505 audit(1234550490.151:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4353
[   16.208536] type=1505 audit(1234550490.151:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4353
[   16.352081] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.918242] ACPI: WMI: Mapper loaded
[   17.658368] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   17.713641] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   17.713645] apm: disabled - APM is not SMP safe.
[   18.637067] ppdev: user-space parallel port driver
[   22.817860] NET: Registered protocol family 10
[   22.819225] lo: Disabled Privacy Extensions
[   24.625659] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   24.625669] vboxdrv: Successfully done.
[   24.625672] vboxdrv: Found 2 processor cores.
[   24.628284] vboxdrv: fAsync=0 offMin=0x3cf offMax=0x1900
[   24.630229] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   24.630237] vboxdrv: Successfully loaded version 2.1.2 (interface 0x000a0009).
[   26.347674] Bluetooth: Core ver 2.13
[   26.348251] NET: Registered protocol family 31
[   26.348257] Bluetooth: HCI device and connection manager initialized
[   26.348263] Bluetooth: HCI socket layer initialized
[   26.377654] Bluetooth: L2CAP ver 2.11
[   26.377663] Bluetooth: L2CAP socket layer initialized
[   26.403116] Bluetooth: SCO (Voice Link) ver 0.6
[   26.403126] Bluetooth: SCO socket layer initialized
[   26.432646] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.432654] Bluetooth: BNEP filters: protocol multicast
[   26.454295] Bluetooth: RFCOMM socket layer initialized
[   26.454312] Bluetooth: RFCOMM TTY layer initialized
[   26.454315] Bluetooth: RFCOMM ver 1.10
[   26.481139] Bridge firewalling registered
[   29.927234] [fglrx] Firegl kernel thread PID: 6068
[   29.952325] [fglrx] Gart USWC size:947 M.
[   29.952333] [fglrx] Gart cacheable size:60 M.
[   29.952342] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   29.952345] [fglrx] Reserved FB block: Unshared offset:fdfb000, size:205000 
[   29.952349] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   30.830788] NET: Registered protocol family 17
[   41.184008] eth0: no IPv6 routers present
[ 8744.347716] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 8744.347727] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 8744.347735] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 8744.347743] end_request: I/O error, dev sr0, sector 64
[ 8744.347751] Buffer I/O error on device sr0, logical block 8
[ 8744.353664] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 8744.353673] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 8744.353680] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 8744.353687] end_request: I/O error, dev sr0, sector 64
[ 8744.353694] Buffer I/O error on device sr0, logical block 8
[ 8744.382605] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 8744.382616] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 8744.382624] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 8744.382632] end_request: I/O error, dev sr0, sector 0
[ 8744.382638] Buffer I/O error on device sr0, logical block 0
[ 8744.386611] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 8744.386619] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 8744.386626] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 8744.386635] end_request: I/O error, dev sr0, sector 8
[ 8744.386641] Buffer I/O error on device sr0, logical block 1
[ 8744.390645] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 8744.390654] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 8744.390661] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 8744.390669] end_request: I/O error, dev sr0, sector 0
[ 8744.390674] Buffer I/O error on device sr0, logical block 0
[ 8744.416454] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 8744.416465] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 8744.416472] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 8744.416480] end_request: I/O error, dev sr0, sector 0
[ 8744.416487] Buffer I/O error on device sr0, logical block 0
[ 8744.421454] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 8744.421464] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 8744.421471] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 8744.421479] end_request: I/O error, dev sr0, sector 0
[ 8744.421485] Buffer I/O error on device sr0, logical block 0
[ 8744.464619] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 8744.464629] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 8744.464636] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 8744.464643] end_request: I/O error, dev sr0, sector 0
[ 8744.464657] Buffer I/O error on device sr0, logical block 0
user@user-ubuntu:~$ 
[/HTML]



Hope I did it the wright way.

regards,
Marc

---

### Post by marcgh on 2009-02-15
Hi Neural oD,

I am really embarassed for what is happening.
Yesterday evening I just wanted to give my DVD reader another go.
I inserted a DVD and.....the dvd mounted and started playing as if nothing ever happens.
This morning, another try...still working.
I burned a dvd with a lightscribe cover and all went well.

I am praying that it will go on like that.

I am sorry for your time and thank you very much for the assistance.

Marc

---

### Post by Neural oD on 2009-02-15
hi marcgh - sorry - been away from the forums for a while - glad to hear that you came right!

---

