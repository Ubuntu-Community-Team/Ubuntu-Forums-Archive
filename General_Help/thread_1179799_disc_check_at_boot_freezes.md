---
title: "disc check at boot freezes"
date: 2009-06-06
forum: General Help
---

### Post by richlyn9 on 2009-06-06
hi,
i have the recent ubuntu 9.04 installed on the secondary HDD with a triple boot of windows xp and ubuntu 8.10 (both win and 8.10 on the primary HDD)yesterday all of a sudden the normal routine disc check hangs and freezes at 40% 
if i skip the check it boots up fine and als well(to the best of my little knowlwedge)still would like to know  why does the disc check freeze (after which there is no option but to restart)

any thing that i should lookout for, any warning bells?
please help
Thanks!

---

### Post by sanemanmad on 2009-06-06
check ```
dmesg 
```for any errors. That is where errors from boot are logged.

---

### Post by richlyn9 on 2009-06-06
just type   "dmesg"  to see the errors at boot?

---

### Post by sanemanmad on 2009-06-06
> **richlyn9 said:**
> just type   "dmesg"  to see the errors at boot?

Yes. In a terminal type ```
dmesg|more
```and this will let you see the errors by scrolling. I would suggest also saving it to txt file and uploading here.

```
dmesg > dmesg.txt
```

---

### Post by richlyn9 on 2009-06-06
[    0.420096]  domain 0: span 0-1 level MC 
[    0.420098]   groups: 0 1 
[    0.420103] CPU1 attaching sched-domain: 
[    0.420105]  domain 0: span 0-1 level MC 
[    0.420107]   groups: 1 0 
[    0.420175] net_namespace: 776 bytes 
[    0.420175] Booting paravirtualized kernel on bare hardware 
[    0.420307] Time: 17:40:59  Date: 06/06/09 
[    0.420307] regulator: core version 0.5 
[    0.420307] NET: Registered protocol family 16 
[    0.420307] EISA bus registered 
[    0.420307] ACPI: bus type pci registered 
[    0.420307] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support. 
[    0.422053] PCI: Using configuration type 1 for base access 
[    0.424551] ACPI: EC: Look up EC in DSDT 
[    0.427956] ACPI: Interpreter enabled 
[    0.427960] ACPI: (supports S0 S1 S3 S4 S5) 
[    0.427979] ACPI: Using IOAPIC for interrupt routing 
[    0.431633] ACPI: No dock devices found. 
[    0.431642] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[    0.431718] pci 0000:00:02.0: reg 10 32bit mmio: [0x90100000-0x9017ffff] 
[    0.431722] pci 0000:00:02.0: reg 14 io port: [0x20e0-0x20e7] 
[    0.431727] pci 0000:00:02.0: reg 18 32bit mmio: [0x80000000-0x8fffffff] 
[    0.431731] pci 0000:00:02.0: reg 1c 32bit mmio: [0x90180000-0x901bffff] 
[    0.431801] pci 0000:00:1b.0: reg 10 64bit mmio: [0x901c0000-0x901c3fff] 
[    0.431830] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold 
[    0.431834] pci 0000:00:1b.0: PME# disabled 
[    0.431878] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold 
[    0.431881] pci 0000:00:1c.0: PME# disabled 
[    0.431927] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold 
[    0.431931] pci 0000:00:1c.1: PME# disabled 
[    0.431976] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold 
[    0.431980] pci 0000:00:1c.2: PME# disabled 
[    0.432033] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold 
[    0.432037] pci 0000:00:1c.3: PME# disabled 
[    0.432083] pci 0000:00:1d.0: reg 20 io port: [0x2080-0x209f] 
[    0.432129] pci 0000:00:1d.1: reg 20 io port: [0x2060-0x207f] 
[    0.432174] pci 0000:00:1d.2: reg 20 io port: [0x2040-0x205f] 
[    0.432220] pci 0000:00:1d.3: reg 20 io port: [0x2020-0x203f] 
[    0.432271] pci 0000:00:1d.7: reg 10 32bit mmio: [0x901c4000-0x901c43ff] 
[    0.432308] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold 
[    0.432312] pci 0000:00:1d.7: PME# disabled 
[    0.432423] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO 
[    0.432427] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO 
[    0.432454] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07] 
[    0.432460] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03] 
[    0.432467] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07] 
[    0.432473] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03] 
[    0.432479] pci 0000:00:1f.1: reg 20 io port: [0x20b0-0x20bf] 
[    0.432518] pci 0000:00:1f.2: reg 10 io port: [0x20c8-0x20cf] 
[    0.432524] pci 0000:00:1f.2: reg 14 io port: [0x20ec-0x20ef] 
[    0.432529] pci 0000:00:1f.2: reg 18 io port: [0x20c0-0x20c7] 
[    0.432535] pci 0000:00:1f.2: reg 1c io port: [0x20e8-0x20eb] 
[    0.432541] pci 0000:00:1f.2: reg 20 io port: [0x20a0-0x20af] 
[    0.432557] pci 0000:00:1f.2: PME# supported from D3hot 
[    0.432561] pci 0000:00:1f.2: PME# disabled 
[    0.432605] pci 0000:00:1f.3: reg 20 io port: [0x2000-0x201f] 
[    0.432724] pci 0000:02:00.0: reg 10 io port: [0x1000-0x10ff] 
[    0.432746] pci 0000:02:00.0: reg 18 64bit mmio: [0x90000000-0x90000fff] 
[    0.432769] pci 0000:02:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff] 
[    0.432782] pci 0000:02:00.0: supports D1 D2 
[    0.432783] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold 
[    0.432789] pci 0000:02:00.0: PME# disabled 
[    0.432831] pci 0000:00:1c.1: bridge io port: [0x1000-0x1fff] 
[    0.432835] pci 0000:00:1c.1: bridge 32bit mmio: [0x90000000-0x900fffff] 
[    0.432972] pci 0000:00:1e.0: transparent bridge 
[    0.433002] bus 00 -> node 0 
[    0.433007] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.433305] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT] 
[    0.433470] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT] 
[    0.433580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT] 
[    0.433691] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT] 
[    0.433800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT] 
[    0.437285] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12) 
[    0.437391] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12) 
[    0.437495] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12) 
[    0.437596] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12) 
[    0.437698] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled. 
[    0.437803] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled. 
[    0.437905] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12) 
[    0.438006] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12) 
[    0.438223] ACPI: WMI: Mapper loaded 
[    0.438259] SCSI subsystem initialized 
[    0.438259] libata version 3.00 loaded. 
[    0.438259] usbcore: registered new interface driver usbfs 
[    0.438259] usbcore: registered new interface driver hub 
[    0.438259] usbcore: registered new device driver usb 
[    0.438259] PCI: Using ACPI for IRQ routing 
[    0.444013] Bluetooth: Core ver 2.13 
[    0.444037] NET: Registered protocol family 31 
[    0.444037] Bluetooth: HCI device and connection manager initialized 
[    0.444037] Bluetooth: HCI socket layer initialized 
[    0.444037] NET: Registered protocol family 8 
[    0.444037] NET: Registered protocol family 20 
[    0.444052] NetLabel: Initializing 
[    0.444054] NetLabel:  domain hash size = 128 
[    0.444057] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.444076] NetLabel:  unlabeled traffic allowed by default 
[    0.444094] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
[    0.444102] hpet0: 3 comparators, 64-bit 14.318180 MHz counter 
[    0.448086] AppArmor: AppArmor Filesystem Enabled 
[    0.456053] pnp: PnP ACPI init 
[    0.456082] ACPI: bus type pnp registered 
[    0.458616] pnp: PnP ACPI: found 13 devices 
[    0.458619] ACPI: ACPI bus type pnp unregistered 
[    0.458622] PnPBIOS: Disabled by ACPI PNP 
[    0.458630] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved 
[    0.458633] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved 
[    0.458635] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved 
[    0.458638] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved 
[    0.458640] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved 
[    0.458642] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved 
[    0.458645] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved 
[    0.458647] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved 
[    0.458650] system 00:01: iomem range 0xc0000-0xdffff could not be reserved 
[    0.458652] system 00:01: iomem range 0xe0000-0xfffff could not be reserved 
[    0.458659] system 00:06: ioport range 0x500-0x53f has been reserved 
[    0.458661] system 00:06: ioport range 0x400-0x47f has been reserved 
[    0.458664] system 00:06: ioport range 0x680-0x6ff has been reserved 
[    0.458666] system 00:06: ioport range 0x770-0x77f has been reserved 
[    0.493342] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01 
[    0.493344] pci 0000:00:1c.0:   IO window: disabled 
[    0.493349] pci 0000:00:1c.0:   MEM window: disabled 
[    0.493353] pci 0000:00:1c.0:   PREFETCH window: disabled 
[    0.493359] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02 
[    0.493362] pci 0000:00:1c.1:   IO window: 0x1000-0x1fff 
[    0.493366] pci 0000:00:1c.1:   MEM window: 0x90000000-0x900fffff 
[    0.493370] pci 0000:00:1c.1:   PREFETCH window: 0x00000090200000-0x000000902fffff 
[    0.493376] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03 
[    0.493378] pci 0000:00:1c.2:   IO window: disabled 
[    0.493383] pci 0000:00:1c.2:   MEM window: disabled 
[    0.493386] pci 0000:00:1c.2:   PREFETCH window: disabled 
[    0.493392] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04 
[    0.493394] pci 0000:00:1c.3:   IO window: disabled 
[    0.493398] pci 0000:00:1c.3:   MEM window: disabled 
[    0.493402] pci 0000:00:1c.3:   PREFETCH window: disabled 
[    0.493407] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05 
[    0.493409] pci 0000:00:1e.0:   IO window: disabled 
[    0.493413] pci 0000:00:1e.0:   MEM window: disabled 
[    0.493417] pci 0000:00:1e.0:   PREFETCH window: disabled 
[    0.493430] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    0.493434] pci 0000:00:1c.0: setting latency timer to 64 
[    0.493442] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16 
[    0.493445] pci 0000:00:1c.1: setting latency timer to 64 
[    0.493453] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    0.493456] pci 0000:00:1c.2: setting latency timer to 64 
[    0.493463] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19 
[    0.493467] pci 0000:00:1c.3: setting latency timer to 64 
[    0.493473] pci 0000:00:1e.0: setting latency timer to 64 
[    0.493477] bus: 00 index 0 io port: [0x00-0xffff] 
[    0.493479] bus: 00 index 1 mmio: [0x000000-0xffffffff] 
[    0.493481] bus: 01 index 0 mmio: [0x0-0x0] 
[    0.493483] bus: 01 index 1 mmio: [0x0-0x0] 
[    0.493484] bus: 01 index 2 mmio: [0x0-0x0] 
[    0.493486] bus: 01 index 3 mmio: [0x0-0x0] 
[    0.493488] bus: 02 index 0 io port: [0x1000-0x1fff] 
[    0.493490] bus: 02 index 1 mmio: [0x90000000-0x900fffff] 
[    0.493491] bus: 02 index 2 mmio: [0x90200000-0x902fffff] 
[    0.493493] bus: 02 index 3 mmio: [0x0-0x0] 
[    0.493495] bus: 03 index 0 mmio: [0x0-0x0] 
[    0.493496] bus: 03 index 1 mmio: [0x0-0x0] 
[    0.493498] bus: 03 index 2 mmio: [0x0-0x0] 
[    0.493499] bus: 03 index 3 mmio: [0x0-0x0] 
[    0.493501] bus: 04 index 0 mmio: [0x0-0x0] 
[    0.493502] bus: 04 index 1 mmio: [0x0-0x0] 
[    0.493504] bus: 04 index 2 mmio: [0x0-0x0] 
[    0.493505] bus: 04 index 3 mmio: [0x0-0x0] 
[    0.493507] bus: 05 index 0 mmio: [0x0-0x0] 
[    0.493508] bus: 05 index 1 mmio: [0x0-0x0] 
[    0.493510] bus: 05 index 2 mmio: [0x0-0x0] 
[    0.493511] bus: 05 index 3 io port: [0x00-0xffff] 
[    0.493513] bus: 05 index 4 mmio: [0x000000-0xffffffff] 
[    0.493521] NET: Registered protocol family 2 
[    0.500598] Switched to high resolution mode on CPU 1 
[    0.504148] Switched to high resolution mode on CPU 0 
[    0.508104] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.508371] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.508764] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.508973] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.508975] TCP reno registered 
[    0.516152] NET: Registered protocol family 1 
[    0.516311] checking if image is initramfs... it is 
[    1.066735] Freeing initrd memory: 7373k freed 
[    1.066947] cpufreq: No nForce2 chipset. 
[    1.067087] audit: initializing netlink socket (disabled) 
[    1.067112] type=2000 audit(1244310059.064:1): initialized 
[    1.073539] highmem bounce pool size: 64 pages 
[    1.073543] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    1.074745] VFS: Disk quotas dquot_6.5.1 
[    1.074799] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    1.075334] fuse init (API version 7.10) 
[    1.075408] msgmni has been set to 1698 
[    1.075575] alg: No test for stdrng (krng) 
[    1.075584] io scheduler noop registered 
[    1.075586] io scheduler anticipatory registered 
[    1.075588] io scheduler deadline registered 
[    1.075599] io scheduler cfq registered (default) 
[    1.075612] pci 0000:00:02.0: Boot video device 
[    1.077419] pcieport-driver 0000:00:1c.0: setting latency timer to 64 
[    1.077450] pcieport-driver 0000:00:1c.0: found MSI capability 
[    1.077478] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X 
[    1.077490] pci_express 0000:00:1c.0:pcie00: allocate port service 
[    1.077502] pci_express 0000:00:1c.0:pcie02: allocate port service 
[    1.077554] pcieport-driver 0000:00:1c.1: setting latency timer to 64 
[    1.077584] pcieport-driver 0000:00:1c.1: found MSI capability 
[    1.077606] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X 
[    1.077617] pci_express 0000:00:1c.1:pcie00: allocate port service 
[    1.077628] pci_express 0000:00:1c.1:pcie02: allocate port service 
[    1.077680] pcieport-driver 0000:00:1c.2: setting latency timer to 64 
[    1.077709] pcieport-driver 0000:00:1c.2: found MSI capability 
[    1.077732] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X 
[    1.077743] pci_express 0000:00:1c.2:pcie00: allocate port service 
[    1.077754] pci_express 0000:00:1c.2:pcie02: allocate port service 
[    1.077805] pcieport-driver 0000:00:1c.3: setting latency timer to 64 
[    1.077835] pcieport-driver 0000:00:1c.3: found MSI capability 
[    1.077857] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X 
[    1.077868] pci_express 0000:00:1c.3:pcie00: allocate port service 
[    1.077881] pci_express 0000:00:1c.3:pcie02: allocate port service 
[    1.077941] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    1.078028] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    1.078155] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0 
[    1.078157] ACPI: Power Button (FF) [PWRF] 
[    1.078198] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1 
[    1.078206] ACPI: Sleep Button (CM) [SLPB] 
[    1.078443] processor ACPI_CPU:00: registered as cooling_device0 
[    1.078518] processor ACPI_CPU:01: registered as cooling_device1 
[    1.079635] isapnp: Scanning for PnP cards... 
[    1.432589] isapnp: No Plug & Play device found 
[    1.440767] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[    1.440858] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    1.441249] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    1.441909] brd: module loaded 
[    1.442185] loop: module loaded 
[    1.442243] Fixed MDIO Bus: probed 
[    1.442247] PPP generic driver version 2.4.2 
[    1.442297] input: Macintosh mouse button emulation as /devices/virtual/input/input2 
[    1.442323] Driver 'sd' needs updating - please use bus_type methods 
[    1.442331] Driver 'sr' needs updating - please use bus_type methods 
[    1.442396] ata_piix 0000:00:1f.1: version 2.12 
[    1.442405] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    1.442437] ata_piix 0000:00:1f.1: setting latency timer to 64 
[    1.442502] scsi0 : ata_piix 
[    1.442573] scsi1 : ata_piix 
[    1.442908] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20b0 irq 14 
[    1.442911] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20b8 irq 15 
[    1.604450] ata1.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.03, max UDMA/66 
[    1.620375] ata1.00: configured for UDMA/66 
[    1.621560] ata2: port disabled. ignoring. 
[    1.622999] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.03 PQ: 0 ANSI: 5 
[    1.627271] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray 
[    1.627276] Uniform CD-ROM driver Revision: 3.20 
[    1.627417] sr 0:0:0:0: Attached scsi CD-ROM sr0 
[    1.627485] sr 0:0:0:0: Attached scsi generic sg0 type 5 
[    1.627500] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    1.627503] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ] 
[    1.627534] ata_piix 0000:00:1f.2: setting latency timer to 64 
[    1.627582] scsi2 : ata_piix 
[    1.627630] scsi3 : ata_piix 
[    1.628173] ata3: SATA max UDMA/133 cmd 0x20c8 ctl 0x20ec bmdma 0x20a0 irq 19 
[    1.628176] ata4: SATA max UDMA/133 cmd 0x20c0 ctl 0x20e8 bmdma 0x20a8 irq 19 
[    1.826787] ata3.00: ATA-7: ST3160215AS, 4.AAB, max UDMA/133 
[    1.826791] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[    1.893451] ata3.00: configured for UDMA/133

---

### Post by richlyn9 on 2009-06-06
this is the continution of the boot logs errors when i typed "dmesg" in terminal

[    2.056688] ata4.00: ATA-8: WDC WD5000AACS-00G8B1, 05.04C05, max UDMA/133 
[    2.056692] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[    2.064683] ata4.00: configured for UDMA/133 
[    2.064805] scsi 2:0:0:0: Direct-Access     ATA      ST3160215AS      4.AA PQ: 0 ANSI: 5 
[    2.064910] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB) 
[    2.064924] sd 2:0:0:0: [sda] Write Protect is off 
[    2.064926] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    2.064949] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    2.064997] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB) 
[    2.065010] sd 2:0:0:0: [sda] Write Protect is off 
[    2.065012] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    2.065034] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    2.065037]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 > 
[    2.143199] sd 2:0:0:0: [sda] Attached SCSI disk 
[    2.143232] sd 2:0:0:0: Attached scsi generic sg1 type 0 
[    2.143296] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 05.0 PQ: 0 ANSI: 5 
[    2.143369] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB) 
[    2.143382] sd 3:0:0:0: [sdb] Write Protect is off 
[    2.143384] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00 
[    2.143406] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    2.143450] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB) 
[    2.143463] sd 3:0:0:0: [sdb] Write Protect is off 
[    2.143465] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00 
[    2.143487] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    2.143490]  sdb: sdb1 sdb2 < sdb5 > 
[    2.174703] sd 3:0:0:0: [sdb] Attached SCSI disk 
[    2.174752] sd 3:0:0:0: Attached scsi generic sg2 type 0 
[    2.175304] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    2.175322] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    2.175338] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[    2.175341] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    2.175399] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1 
[    2.179300] ehci_hcd 0000:00:1d.7: debug port 1 
[    2.179306] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
[    2.179319] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x901c4000 
[    2.192043] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
[    2.192136] usb usb1: configuration #1 chosen from 1 choice 
[    2.192182] hub 1-0:1.0: USB hub found 
[    2.192194] hub 1-0:1.0: 8 ports detected 
[    2.192314] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    2.192327] uhci_hcd: USB Universal Host Controller Interface driver 
[    2.192350] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    2.192355] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[    2.192358] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    2.192396] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
[    2.192417] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002080 
[    2.192482] usb usb2: configuration #1 chosen from 1 choice 
[    2.192503] hub 2-0:1.0: USB hub found 
[    2.192509] hub 2-0:1.0: 2 ports detected 
[    2.192579] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    2.192584] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[    2.192587] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    2.192621] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3 
[    2.192641] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002060 
[    2.192701] usb usb3: configuration #1 chosen from 1 choice 
[    2.192722] hub 3-0:1.0: USB hub found 
[    2.192730] hub 3-0:1.0: 2 ports detected 
[    2.192799] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    2.192805] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[    2.192807] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[    2.192847] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4 
[    2.192874] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040 
[    2.192938] usb usb4: configuration #1 chosen from 1 choice 
[    2.192959] hub 4-0:1.0: USB hub found 
[    2.192964] hub 4-0:1.0: 2 ports detected 
[    2.193035] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16 
[    2.193041] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
[    2.193043] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[    2.193080] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5 
[    2.193107] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00002020 
[    2.193168] usb usb5: configuration #1 chosen from 1 choice 
[    2.193189] hub 5-0:1.0: USB hub found 
[    2.193196] hub 5-0:1.0: 2 ports detected 
[    2.193301] usbcore: registered new interface driver libusual 
[    2.193327] usbcore: registered new interface driver usbserial 
[    2.193336] USB Serial support registered for generic 
[    2.193349] usbcore: registered new interface driver usbserial_generic 
[    2.193351] usbserial: USB Serial Driver core 
[    2.193398] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12 
[    2.196086] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    2.196092] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    2.200088] mice: PS/2 mouse device common for all mice 
[    2.212125] rtc_cmos 00:03: RTC can wake from S4 
[    2.212172] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
[    2.212200] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs 
[    2.212294] device-mapper: uevent: version 1.0.3 
[    2.212371] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email] 
[    2.212431] device-mapper: multipath: version 1.0.5 loaded 
[    2.212433] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    2.212498] EISA: Probing bus 0 at eisa.0 
[    2.212503] Cannot allocate resource for EISA slot 1 
[    2.212505] Cannot allocate resource for EISA slot 2 
[    2.212524] EISA: Detected 0 cards. 
[    2.212565] cpuidle: using governor ladder 
[    2.212567] cpuidle: using governor menu 
[    2.213018] TCP cubic registered 
[    2.213102] NET: Registered protocol family 10 
[    2.213491] lo: Disabled Privacy Extensions 
[    2.213789] NET: Registered protocol family 17 
[    2.213804] Bluetooth: L2CAP ver 2.11 
[    2.213805] Bluetooth: L2CAP socket layer initialized 
[    2.213808] Bluetooth: SCO (Voice Link) ver 0.6 
[    2.213809] Bluetooth: SCO socket layer initialized 
[    2.213833] Bluetooth: RFCOMM socket layer initialized 
[    2.213840] Bluetooth: RFCOMM TTY layer initialized 
[    2.213842] Bluetooth: RFCOMM ver 1.10 
[    2.214176] Using IPI No-Shortcut mode 
[    2.214238] registered taskstats version 1 
[    2.214337]   Magic number: 13:385:693 
[    2.214399] rtc_cmos 00:03: setting system clock to 2009-06-06 17:41:01 UTC (1244310061) 
[    2.214401] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    2.214403] EDD information not available. 
[    2.214640] Freeing unused kernel memory: 532k freed 
[    2.214750] Write protecting the kernel text: 4128k 
[    2.214789] Write protecting the kernel read-only data: 1532k 
[    2.243980] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3 
[    2.391376] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[    2.391399] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    2.391427] r8169 0000:02:00.0: setting latency timer to 64 
[    2.391615] r8169 0000:02:00.0: irq 2299 for MSI/MSI-X 
[    2.392332] eth0: RTL8168b/8111b at 0xf7c64000, 00:19:d1:88:55:82, XID 38500000 IRQ 2299 
[    3.780552] PM: Starting manual resume from disk 
[    3.780555] PM: Resume from partition 8:7 
[    3.780557] PM: Checking hibernation image. 
[    3.780706] PM: Resume from disk failed. 
[    3.782895] EXT3-fs: INFO: recovery required on readonly filesystem. 
[    3.782899] EXT3-fs: write access will be enabled during recovery. 
[    3.833802] kjournald starting.  Commit interval 5 seconds 
[    3.833806] EXT3-fs: recovery complete. 
[    3.834138] EXT3-fs: mounted filesystem with ordered data mode. 
[    7.306907] udev: starting version 141 
[    7.430713] Linux agpgart interface v0.103 
[    7.440925] intel_rng: FWH not detected 
[    7.466663] parport_pc 00:07: reported by Plug and Play ACPI 
[    7.466688] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP] 
[    7.470608] agpgart-intel 0000:00:00.0: Intel 945G Chipset 
[    7.471105] agpgart-intel 0000:00:00.0: detected 7932K stolen memory 
[    7.473632] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000 
[    7.599947] input: PC Speaker as /devices/platform/pcspkr/input/input4 
[    7.612356] ppdev: user-space parallel port driver 
[    7.678502] iTCO_vendor_support: vendor-support=0 
[    7.679775] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05 
[    7.679884] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460) 
[    7.679931] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[    7.837198] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume 
[    7.880785] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
[    7.880858] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[    7.914003] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS... 
[    8.323235] psmouse serio1: ID: 10 00 64<6>input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5 
[    8.909713] lp0: using parport0 (interrupt-driven). 
[    8.971533] Adding 1951856k swap on /dev/sda7.  Priority:-1 extents:1 across:1951856k 
[    9.503006] EXT3 FS on sdb1, internal journal 
[   11.582303] kjournald starting.  Commit interval 5 seconds 
[   11.582315] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended 
[   11.582712] EXT3 FS on sdb5, internal journal 
[   11.582719] EXT3-fs: mounted filesystem with ordered data mode. 
[   11.810210] type=1505 audit(1244290271.094:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1998 
[   11.850907] type=1505 audit(1244290271.134:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2002 
[   11.850997] type=1505 audit(1244290271.134:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2002 
[   11.851037] type=1505 audit(1244290271.134:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2002 
[   11.851070] type=1505 audit(1244290271.134:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2002 
[   11.964443] type=1505 audit(1244290271.246:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2007 
[   11.964643] type=1505 audit(1244290271.250:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2007 
[   11.988993] type=1505 audit(1244290271.274:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2011 
[   13.443524] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   13.443527] Bluetooth: BNEP filters: protocol multicast 
[   13.451452] Bridge firewalling registered 
[   14.670061] [drm] Initialized drm 1.1.0 20060810 
[   14.675367] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   14.675373] pci 0000:00:02.0: setting latency timer to 64 
[   14.675538] [drm] Initialized i915 1.6.0 20080730 on minor 0 
[   14.677703] [drm:i915_setparam] *ERROR* unknown parameter 4 
[   14.677725] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[   15.210801] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[   18.715104] r8169: eth0: link down 
[   18.715291] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   30.364514] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[   51.852085] usb 1-6: new high speed USB device using ehci_hcd and address 2 
[   51.986670] usb 1-6: configuration #1 chosen from 1 choice 
[   52.029532] Initializing USB Mass Storage driver... 
[   52.030363] scsi4 : SCSI emulation for USB Mass Storage devices 
[   52.031449] usbcore: registered new interface driver usb-storage 
[   52.031453] USB Mass Storage support registered. 
[   52.032019] usb-storage: device found at 2 
[   52.032021] usb-storage: waiting for device to settle before scanning 
[   57.032275] usb-storage: device scan complete 
[   57.032881] scsi 4:0:0:0: Direct-Access     JetFlash Transcend 4GB    8.07 PQ: 0 ANSI: 2 
[   57.034351] sd 4:0:0:0: [sdc] 7843840 512-byte hardware sectors: (4.01 GB/3.74 GiB) 
[   57.040805] sd 4:0:0:0: [sdc] Write Protect is off 
[   57.040809] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00 
[   57.040811] sd 4:0:0:0: [sdc] Assuming drive cache: write through 
[   57.043007] sd 4:0:0:0: [sdc] 7843840 512-byte hardware sectors: (4.01 GB/3.74 GiB) 
[   57.043469] sd 4:0:0:0: [sdc] Write Protect is off 
[   57.043472] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00 
[   57.043474] sd 4:0:0:0: [sdc] Assuming drive cache: write through 
[   57.043479]  sdc: sdc1 
[   58.588439] sd 4:0:0:0: [sdc] Attached SCSI removable disk 
[   58.588506] sd 4:0:0:0: Attached scsi generic sg3 type 0 
richlyn@richlyn:~$

---

### Post by richlyn9 on 2009-06-09
i have posted the  boot logs errors when i typed "dmesg" in terminal can someone tell me why  does the disc check freeze at 40% while booting to ubuntu 9.04

---

### Post by dcstar on 2009-06-09
> **richlyn9 said:**
> i have posted the  boot logs errors when i typed "dmesg" in terminal can someone tell me why  does the disc check freeze at 40% while booting to ubuntu 9.04

Boot off a Live CD and do a manual fsck on that drive.

---

