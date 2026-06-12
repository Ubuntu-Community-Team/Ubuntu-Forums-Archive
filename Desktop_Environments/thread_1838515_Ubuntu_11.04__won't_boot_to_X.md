---
title: "Ubuntu 11.04  won't boot to X"
date: 2011-09-03
forum: Desktop Environments
---

### Post by CyberNerdz on 2011-09-03
I have been running 11.04 with Gnome3 smoothly for months then suddenly until a few weeks ago after an update it won't boot directly to my UI. I have to CTL-ALT-F2, login, then "startx". This is the only way I can get to start X. During boot I see 2 lines where it hangs; can't remember the exact message but it's the battery  check... [OK], then just hangs after the CUP printer... [OK}. I dont know what comes after that but it just stops there. Here is my dmesg:

```

[    0.390483] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.390508] pnp 00:02: [mem 0xe0000000-0xefffffff]
[    0.390600] system 00:02: [mem 0xe0000000-0xefffffff] has been reserved
[    0.390605] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.390783] pnp 00:03: [io  0x1000-0x107f]
[    0.390786] pnp 00:03: [io  0x1080-0x10ff]
[    0.390788] pnp 00:03: [io  0x1400-0x147f]
[    0.390791] pnp 00:03: [io  0x1480-0x14ff]
[    0.390793] pnp 00:03: [io  0x1800-0x187f]
[    0.390796] pnp 00:03: [io  0x1880-0x18ff]
[    0.390872] system 00:03: [io  0x1000-0x107f] has been reserved
[    0.390875] system 00:03: [io  0x1080-0x10ff] has been reserved
[    0.390878] system 00:03: [io  0x1400-0x147f] has been reserved
[    0.390882] system 00:03: [io  0x1480-0x14ff] has been reserved
[    0.390885] system 00:03: [io  0x1800-0x187f] has been reserved
[    0.390888] system 00:03: [io  0x1880-0x18ff] has been reserved
[    0.390892] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.390907] pnp 00:04: [io  0x0010-0x001f]
[    0.390909] pnp 00:04: [io  0x0022-0x003f]
[    0.390912] pnp 00:04: [io  0x0044-0x005f]
[    0.390914] pnp 00:04: [io  0x0063]
[    0.390916] pnp 00:04: [io  0x0065]
[    0.390919] pnp 00:04: [io  0x0067-0x006f]
[    0.390921] pnp 00:04: [io  0x0072-0x0073]
[    0.390924] pnp 00:04: [io  0x0074-0x007f]
[    0.390926] pnp 00:04: [io  0x0080]
[    0.390929] pnp 00:04: [io  0x0084]
[    0.390931] pnp 00:04: [io  0x0091-0x0093]
[    0.390933] pnp 00:04: [io  0x0097-0x009f]
[    0.390936] pnp 00:04: [io  0x00a2-0x00bf]
[    0.390938] pnp 00:04: [io  0x00e0-0x00ef]
[    0.390941] pnp 00:04: [io  0x0360-0x0361]
[    0.390943] pnp 00:04: [io  0x04d0-0x04d1]
[    0.391033] system 00:04: [io  0x0360-0x0361] has been reserved
[    0.391036] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.391040] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.391058] pnp 00:05: [io  0x0000-0x0008]
[    0.391060] pnp 00:05: [io  0x000a-0x000f]
[    0.391063] pnp 00:05: [io  0x0081-0x0083]
[    0.391067] pnp 00:05: [io  0x0087]
[    0.391070] pnp 00:05: [io  0x0089-0x008b]
[    0.391072] pnp 00:05: [io  0x008f]
[    0.391075] pnp 00:05: [io  0x00c0-0x00d1]
[    0.391077] pnp 00:05: [io  0x00d4-0x00df]
[    0.391080] pnp 00:05: [dma 4]
[    0.391123] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.391138] pnp 00:06: [io  0x0061]
[    0.391185] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.391213] pnp 00:07: [io  0x0070-0x0071]
[    0.391256] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.391267] pnp 00:08: [io  0x00f0-0x00f1]
[    0.391277] pnp 00:08: [irq 13]
[    0.391325] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.391346] pnp 00:09: [io  0x0060]
[    0.391349] pnp 00:09: [io  0x0064]
[    0.391358] pnp 00:09: [irq 1]
[    0.391405] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.391423] pnp 00:0a: [irq 12]
[    0.391477] pnp 00:0a: Plug and Play ACPI device, IDs SYN013b SYN0100 SYN0002 PNP0f13 (active)
[    0.391851] pnp 00:0b: [mem 0xffc00000-0xffffffff]
[    0.391854] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.391856] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    0.391859] pnp 00:0b: [mem 0xfed00000-0xfed00fff]
[    0.391862] pnp 00:0b: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.391865] pnp 00:0b: [mem 0xfef00000-0xfef00fff]
[    0.391957] system 00:0b: [mem 0xffc00000-0xffffffff] could not be reserved
[    0.391961] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.391965] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.391969] system 00:0b: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.391972] system 00:0b: [mem 0xfef00000-0xfef00fff] has been reserved
[    0.391976] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.392080] pnp: PnP ACPI: found 12 devices
[    0.392082] ACPI: ACPI bus type pnp unregistered
[    0.398905] pci 0000:00:12.0: BAR 6: assigned [mem 0xf6280000-0xf629ffff pref]
[    0.398911] pci 0000:02:05.0: BAR 0: assigned [mem 0xf6100000-0xf61007ff]
[    0.398917] pci 0000:02:05.0: BAR 0: set to [mem 0xf6100000-0xf61007ff] (PCI address [0xf6100000-0xf61007ff])
[    0.398921] pci 0000:00:08.0: PCI bridge to [bus 02-02]
[    0.398924] pci 0000:00:08.0:   bridge window [io  disabled]
[    0.398928] pci 0000:00:08.0:   bridge window [mem 0xf6100000-0xf61fffff]
[    0.398932] pci 0000:00:08.0:   bridge window [mem pref disabled]
[    0.398936] pci 0000:00:0c.0: PCI bridge to [bus 04-05]
[    0.398939] pci 0000:00:0c.0:   bridge window [io  0x4000-0x4fff]
[    0.398943] pci 0000:00:0c.0:   bridge window [mem 0xf2000000-0xf3ffffff]
[    0.398947] pci 0000:00:0c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.398952] pci 0000:00:0d.0: PCI bridge to [bus 03-03]
[    0.398954] pci 0000:00:0d.0:   bridge window [io  disabled]
[    0.398957] pci 0000:00:0d.0:   bridge window [mem 0xf6000000-0xf60fffff]
[    0.398960] pci 0000:00:0d.0:   bridge window [mem pref disabled]
[    0.398971] pci 0000:00:08.0: setting latency timer to 64
[    0.398977] pci 0000:00:0c.0: setting latency timer to 64
[    0.398982] pci 0000:00:0d.0: setting latency timer to 64
[    0.398986] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.398989] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.398992] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.398995] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.398997] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.399000] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.399003] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.399006] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.399009] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.399012] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.399015] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.399018] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.399021] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.399024] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.399026] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff]
[    0.399029] pci_bus 0000:00: resource 19 [mem 0xfed40000-0xfed44fff]
[    0.399032] pci_bus 0000:00: resource 20 [mem 0xd0000000-0xfebfffff]
[    0.399036] pci_bus 0000:02: resource 1 [mem 0xf6100000-0xf61fffff]
[    0.399039] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    0.399042] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    0.399044] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    0.399047] pci_bus 0000:02: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.399050] pci_bus 0000:02: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.399053] pci_bus 0000:02: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.399056] pci_bus 0000:02: resource 10 [mem 0x000cc000-0x000cffff]
[    0.399059] pci_bus 0000:02: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.399062] pci_bus 0000:02: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.399065] pci_bus 0000:02: resource 13 [mem 0x000dc000-0x000dffff]
[    0.399067] pci_bus 0000:02: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.399070] pci_bus 0000:02: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.399073] pci_bus 0000:02: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.399076] pci_bus 0000:02: resource 17 [mem 0x000ec000-0x000effff]
[    0.399079] pci_bus 0000:02: resource 18 [mem 0x000f0000-0x000fffff]
[    0.399082] pci_bus 0000:02: resource 19 [mem 0xfed40000-0xfed44fff]
[    0.399085] pci_bus 0000:02: resource 20 [mem 0xd0000000-0xfebfffff]
[    0.399088] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.399091] pci_bus 0000:04: resource 1 [mem 0xf2000000-0xf3ffffff]
[    0.399094] pci_bus 0000:04: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.399098] pci_bus 0000:03: resource 1 [mem 0xf6000000-0xf60fffff]
[    0.399145] NET: Registered protocol family 2
[    0.399369] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.401312] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.406132] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.406720] TCP: Hash tables configured (established 524288 bind 65536)
[    0.406723] TCP reno registered
[    0.406742] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.406797] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.406951] NET: Registered protocol family 1
[    0.407145] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.407200] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.407259] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.407324] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.407394] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.407468] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.407475] pci 0000:00:12.0: Boot video device
[    0.407500] PCI: CLS 64 bytes, default 64
[    0.408573] PCI-DMA: Disabling AGP.
[    0.408695] PCI-DMA: aperture base @ b4000000 size 65536 KB
[    0.408697] PCI-DMA: using GART IOMMU.
[    0.408702] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.412481] Simple Boot Flag at 0x36 set to 0x1
[    0.412901] audit: initializing netlink socket (disabled)
[    0.412915] type=2000 audit(1315064635.410:1): initialized
[    0.430417] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.432719] VFS: Disk quotas dquot_6.5.2
[    0.432790] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.433632] fuse init (API version 7.16)
[    0.433742] msgmni has been set to 7394
[    0.434044] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.434080] io scheduler noop registered
[    0.434082] io scheduler deadline registered
[    0.434135] io scheduler cfq registered (default)
[    0.434308] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.434344] pcieport 0000:00:0c.0: irq 40 for MSI/MSI-X
[    0.434421] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.434444] pcieport 0000:00:0d.0: irq 41 for MSI/MSI-X
[    0.434521] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.434554] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.435082] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.435366] ACPI: AC Adapter [ACAD] (off-line)
[    0.435464] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.435471] ACPI: Sleep Button [SLPB]
[    0.435523] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.435769] ACPI: Lid Switch [LID]
[    0.435838] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.435843] ACPI: Power Button [PWRB]
[    0.435895] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.435899] ACPI: Power Button [PWRF]
[    0.436159] ACPI: acpi_idle registered with cpuidle
[    0.436187] ACPI: processor limited to max C-state 1
[    0.438810] [Firmware Bug]: Invalid critical threshold (0)
[    0.439218] thermal LNXTHERM:00: registered as thermal_zone0
[    0.439221] ACPI: Thermal Zone [THRM] (38 C)
[    0.439241] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.439344] ERST: Table is not found!
[    0.439453] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.596439] Freeing initrd memory: 11108k freed
[    0.700405] ACPI: Battery Slot [BAT0] (battery present)
[    1.270479] Linux agpgart interface v0.103
[    1.271975] brd: module loaded
[    1.272694] loop: module loaded
[    1.272824] i2c-core: driver [adp5520] using legacy suspend method
[    1.272827] i2c-core: driver [adp5520] using legacy resume method
[    1.273117] pata_acpi 0000:00:06.0: setting latency timer to 64
[    1.273402] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    1.273425] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    1.273454] pata_acpi 0000:00:09.0: setting latency timer to 64
[    1.273463] pata_acpi 0000:00:09.0: PCI INT A disabled
[    1.273993] Fixed MDIO Bus: probed
[    1.274030] PPP generic driver version 2.4.2
[    1.274085] tun: Universal TUN/TAP device driver, 1.6
[    1.274087] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.274192] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.274419] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    1.274431] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    1.274463] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.274467] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.274550] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.300075] ehci_hcd 0000:00:02.1: debug port 1
[    1.300083] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.300109] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    1.320035] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.320193] hub 1-0:1.0: USB hub found
[    1.320199] hub 1-0:1.0: 7 ports detected
[    1.320546] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    1.320551] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    1.320568] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    1.320572] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    1.320627] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    1.320685] ehci_hcd 0000:00:04.1: debug port 1
[    1.320693] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    1.320701] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    1.340034] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.340168] hub 2-0:1.0: USB hub found
[    1.340174] hub 2-0:1.0: 2 ports detected
[    1.340277] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.340523] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    1.340541] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    1.340557] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.340560] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.340617] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    1.340677] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    1.402170] hub 3-0:1.0: USB hub found
[    1.402176] hub 3-0:1.0: 7 ports detected
[    1.402520] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    1.402525] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    1.402541] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.402544] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.402598] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.402642] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    1.462156] hub 4-0:1.0: USB hub found
[    1.462162] hub 4-0:1.0: 2 ports detected
[    1.462269] uhci_hcd: USB Universal Host Controller Interface driver
[    1.490050] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.511559] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.511566] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.511736] mousedev: PS/2 mouse device common for all mice
[    1.513489] rtc_cmos 00:07: RTC can wake from S4
[    1.532351] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.540079] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.540119] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.540249] device-mapper: uevent: version 1.0.3
[    1.540363] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.540463] device-mapper: multipath: version 1.2.0 loaded
[    1.540467] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.540699] cpuidle: using governor ladder
[    1.540702] cpuidle: using governor menu
[    1.541020] TCP cubic registered
[    1.541180] NET: Registered protocol family 10
[    1.541766] NET: Registered protocol family 17
[    1.541791] Registering the dns_resolver key type
[    1.542297] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 (2 cpu cores) (version 2.20.00)
[    1.542350] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x12
[    1.542353] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[    1.542356] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[    1.542358] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    1.542547] PM: Hibernation image not present or could not be loaded.
[    1.542560] registered taskstats version 1
[    1.542863]   Magic number: 11:517:739
[    1.545401] rtc_cmos 00:07: setting system clock to 2011-09-03 15:43:57 UTC (1315064637)
[    1.545404] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.545406] EDD information not available.
[    1.547660] Freeing unused kernel memory: 956k freed
[    1.548183] Write protecting the kernel read-only data: 10240k
[    1.549136] Freeing unused kernel memory: 184k freed
[    1.555469] Freeing unused kernel memory: 1444k freed
[    1.584581] <30>udev[100]: starting version 167
[    1.660120] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    1.740722] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.740964] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.740986] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.740992] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.769333] sdhci: Secure Digital Host Controller Interface driver
[    1.769337] sdhci: Copyright(c) Pierre Ossman
[    1.779509] firewire_ohci 0000:02:05.0: enabling device (0100 -> 0102)
[    1.779716] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    1.779734] firewire_ohci 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    1.830131] firewire_ohci: Added fw-ohci device 0000:02:05.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    1.830552] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[    1.830766] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[    1.830782] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[    1.831838] sdhci-pci 0000:02:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.831862] mmc0: no vmmc regulator found
[    1.832909] Registered led device: mmc0::
[    1.833956] mmc0: SDHCI controller on PCI [0000:02:05.1] using DMA
[    2.271034] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:af:96:cf
[    2.271040] forcedeth 0000:00:0a.0: highdma pwrctl mgmt lnktim msi desc-v3
[    2.271140] pata_amd 0000:00:06.0: version 0.4.1
[    2.271194] pata_amd 0000:00:06.0: setting latency timer to 64
[    2.271817] scsi0 : pata_amd
[    2.271968] scsi1 : pata_amd
[    2.272302] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    2.272305] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    2.272383] ahci 0000:00:09.0: version 3.0
[    2.272396] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    2.272441] ahci 0000:00:09.0: controller can do NCQ, turning on CAP_NCQ
[    2.272444] ahci 0000:00:09.0: controller can't do PMP, turning off CAP_PMP
[    2.272502] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    2.272507] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pio slum part 
[    2.272512] ahci 0000:00:09.0: setting latency timer to 64
[    2.273476] scsi2 : ahci
[    2.273592] scsi3 : ahci
[    2.273699] scsi4 : ahci
[    2.273800] scsi5 : ahci
[    2.273962] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 23
[    2.273966] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 23
[    2.273969] ata5: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 23
[    2.273972] ata6: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 23
[    2.330143] firewire_core: created device fw0: GUID 00241b00a4f86700, S400
[    2.450313] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[    2.450323] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc700) ACPI=0x39f (120:600:0x12)
[    2.490239] ata1.00: configured for MWDMA2
[    2.495603] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[    2.500434] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.500438] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.500590] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.500692] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.500861] ata2: port disabled. ignoring.
[    2.620035] ata6: SATA link down (SStatus 0 SControl 300)
[    2.620054] ata4: SATA link down (SStatus 0 SControl 300)
[    2.620083] ata5: SATA link down (SStatus 0 SControl 300)
[    3.020036] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.021004] ata3.00: ATA-8: Hitachi HTS547575A9E384, JE4OA40J, max UDMA/133
[    3.021008] ata3.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.022047] ata3.00: configured for UDMA/133
[    3.022185] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54757 JE4O PQ: 0 ANSI: 5
[    3.022407] sd 2:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    3.022411] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.022415] sd 2:0:0:0: [sda] 4096-byte physical blocks
[    3.022494] sd 2:0:0:0: [sda] Write Protect is off
[    3.022498] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.022526] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.351398]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    3.351907] sd 2:0:0:0: [sda] Attached SCSI disk
[    9.254441] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   20.187087] <30>udev[425]: starting version 167
[   20.208522] Adding 3070972k swap on /dev/sda6.  Priority:-1 extents:1 across:3070972k 
[   20.236697] lp: driver loaded but no devices found
[   20.499812] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   20.718345] type=1400 audit(1315089856.664:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=676 comm="apparmor_parser"
[   20.718775] type=1400 audit(1315089856.664:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=676 comm="apparmor_parser"
[   20.719058] type=1400 audit(1315089856.664:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=676 comm="apparmor_parser"
[   20.766294] lib80211: common routines for IEEE802.11 drivers
[   20.766301] lib80211_crypt: registered algorithm 'NULL'
[   20.766585] MCE: In-kernel MCE decoding enabled.
[   20.783748] EDAC MC: Ver: 2.1.0 Apr 11 2011
[   20.796352] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   20.796389] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   20.828221] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   20.843105] EDAC amd64_edac: v3.3.0
[   20.846545] acpi device:24: registered as cooling_device2
[   20.847967] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   20.848053] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   20.848136] EDAC amd64: DRAM ECC disabled.
[   20.848148] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   20.848150]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   20.848152]  (Note that use of the override may cause unknown side effects.)
[   20.912855] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.912861] Disabling lock debugging due to kernel taint
[   20.992998] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   20.993025] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   20.993033] wl 0000:03:00.0: setting latency timer to 64
[   20.999462] malloc in abgphy done
[   21.075301] lib80211_crypt: registered algorithm 'TKIP'
[   21.076904] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[   21.077111] forcedeth 0000:00:0a.0: eth0: no link during initialization
[   21.078552] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.284248] type=1400 audit(1315089857.234:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=825 comm="apparmor_parser"
[   21.284739] type=1400 audit(1315089857.234:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=826 comm="apparmor_parser"
[   21.285412] type=1400 audit(1315089857.234:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=826 comm="apparmor_parser"
[   21.285700] type=1400 audit(1315089857.234:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=826 comm="apparmor_parser"
[   21.291539] type=1400 audit(1315089857.244:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=829 comm="apparmor_parser"
[   21.317671] type=1400 audit(1315089857.264:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=831 comm="apparmor_parser"
[   21.324327] type=1400 audit(1315089857.274:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=831 comm="apparmor_parser"
[   21.490891] eth1: Broadcom BCM4311 802.11 Hybrid Wireless Controller 5.100.82.38
[   21.535512] r852 0000:02:05.3: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   21.539668] r852: Non dma capable device detected, dma disabled
[   21.539684] r852: driver loaded succesfully
[   21.717948] input: HP WMI hotkeys as /devices/virtual/input/input6
[   21.737520] Linux video capture interface: v2.00
[   21.754648] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a101)
[   21.758990] input: HP Webcam as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input7
[   21.760101] usbcore: registered new interface driver uvcvideo
[   21.760106] USB Video Class driver (v1.0.0)
[   21.846600] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   21.846625] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   21.846630] hda_intel: Disable MSI for Nvidia chipset
[   21.846685] HDA Intel 0000:00:07.0: setting latency timer to 64
[   22.659444] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000/0x0
[   22.755070] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   22.893972] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   22.893998] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   22.894008] nvidia 0000:00:12.0: setting latency timer to 64
[   22.894014] vgaarb: device changed decodes: PCI:0000:00:12.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.894384] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
[   22.951302] vboxdrv: Found 2 processor cores.
[   22.952305] vboxdrv: fAsync=1 offMin=0x897db offMax=0x897db
[   22.953259] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   22.953264] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
[   23.914645] ppdev: user-space parallel port driver
[   26.770960] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   27.358974] show_signal_msg: 18 callbacks suppressed
[   27.358981] gdm-simple-slav[1309]: segfault at 0 ip 00007f00df880f15 sp 00007fff73594fb0 error 4 in libnss_compat-2.13.so[7f00df87d000+8000]
[   31.910023] eth1: no IPv6 routers present
[   41.986512] forcedeth 0000:00:0a.0: eth0: link up
[   41.987424] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   52.550018] eth0: no IPv6 routers present
[   78.113275] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   78.355167] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   78.545720] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[  244.536061] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 4 bytes away.
[  245.665173] psmouse.c: resync failed, issuing reconnect request
[  423.822508] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[  458.220028] CE: hpet increased min_delta_ns to 11520 nsec
[  463.162317] exe (2523): /proc/2523/oom_adj is deprecated, please use /proc/2523/oom_score_adj instead.

```

Any assistance will be appreciated.

---

