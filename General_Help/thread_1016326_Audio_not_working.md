---
title: "Audio not working"
date: 2008-12-19
forum: General Help
---

### Post by miked860 on 2008-12-19
My audio will not work. It worked fine before my last reboot. I haven't changed anything at all. Any ideas?

---

### Post by linux_tech on 2008-12-19
Try installing gnome-alsamixer if you have not yet installed it.  Run it and adjusting settings
In terminal (Applications>Accessories>Terminal) type:

```
sudo apt-get install gnome-alsamixer 
```
Make sure nothing is muted and try unchecking the option for Audigy Analog/ digital output jack.

---

### Post by miked860 on 2008-12-19
Did what you said and nothing changed.

---

### Post by linux_tech on 2008-12-19
ok try restarting alsa
```

sudo /etc/init.d/alsa-utils stop
sudo alsa force-reload
sudo /etc/init.d/alsa-utils start

```

---

### Post by miked860 on 2008-12-19
Nothing changed.

---

### Post by linux_tech on 2008-12-19
Are you getting any system sounds?  Try the sound tests in System>Preferences>Sound

---

### Post by miked860 on 2008-12-19
Nope.

---

### Post by linux_tech on 2008-12-19
What is output of:
```

aplay -l
lspci | grep audio
amixer info
dmesg

```

reference for troubleshooting sound-
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by miked860 on 2008-12-19
```
miked860@miked860-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
miked860@miked860-desktop:~$ lspci | grep audio
miked860@miked860-desktop:~$ amixer info
Card default 'Intel'/'HDA Intel at 0x50200000 irq 16'
  Mixer name	: 'Realtek ALC880'
  Components	: 'HDA:10ec0880'
  Controls      : 14
  Simple ctrls  : 9
miked860@miked860-desktop:~$ 
```

```
[    0.496079] NetLabel: Initializing
[    0.496079] NetLabel:  domain hash size = 128
[    0.496079] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.496089] NetLabel:  unlabeled traffic allowed by default
[    0.496165] hpet clockevent registered
[    0.496170] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.496176] hpet0: 3 64-bit timers, 14318180 Hz
[    0.497858] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.497861]    actual entries 65620
[    0.497970] AppArmor: AppArmor Filesystem Enabled
[    0.497992] ACPI: RTC can wake from S4
[    0.504067] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.504072] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.504075] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.504079] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.504083] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.504086] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.504090] system 00:01: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.504105] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.504108] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.504116] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.539618] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.539623] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.539628] pci 0000:00:01.0:   MEM window: 0x50100000-0x501fffff
[    0.539632] pci 0000:00:01.0:   PREFETCH window: 0x00000040000000-0x0000004fffffff
[    0.539638] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.539641] pci 0000:00:1c.0:   IO window: disabled
[    0.539647] pci 0000:00:1c.0:   MEM window: 0x50300000-0x503fffff
[    0.539651] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.539658] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.539660] pci 0000:00:1c.1:   IO window: disabled
[    0.539666] pci 0000:00:1c.1:   MEM window: 0x50400000-0x504fffff
[    0.539671] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.539677] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.539680] pci 0000:00:1c.2:   IO window: disabled
[    0.539685] pci 0000:00:1c.2:   MEM window: 0x50500000-0x505fffff
[    0.539690] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.539697] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.539699] pci 0000:00:1c.3:   IO window: disabled
[    0.539705] pci 0000:00:1c.3:   MEM window: 0x50600000-0x506fffff
[    0.539709] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.539717] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.539720] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.539726] pci 0000:00:1e.0:   MEM window: 0x50000000-0x500fffff
[    0.539731] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.539747] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.539752] pci 0000:00:01.0: setting latency timer to 64
[    0.539763] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.539768] pci 0000:00:1c.0: setting latency timer to 64
[    0.539776] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.539781] pci 0000:00:1c.1: setting latency timer to 64
[    0.539790] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.539795] pci 0000:00:1c.2: setting latency timer to 64
[    0.539804] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.539809] pci 0000:00:1c.3: setting latency timer to 64
[    0.539817] pci 0000:00:1e.0: setting latency timer to 64
[    0.539822] bus: 00 index 0 io port: [0, ffff]
[    0.539825] bus: 00 index 1 mmio: [0, ffffffff]
[    0.539827] bus: 01 index 0 io port: [2000, 2fff]
[    0.539830] bus: 01 index 1 mmio: [50100000, 501fffff]
[    0.539832] bus: 01 index 2 mmio: [40000000, 4fffffff]
[    0.539834] bus: 01 index 3 mmio: [0, 0]
[    0.539837] bus: 02 index 0 mmio: [0, 0]
[    0.539839] bus: 02 index 1 mmio: [50300000, 503fffff]
[    0.539841] bus: 02 index 2 mmio: [0, 0]
[    0.539843] bus: 02 index 3 mmio: [0, 0]
[    0.539845] bus: 03 index 0 mmio: [0, 0]
[    0.539848] bus: 03 index 1 mmio: [50400000, 504fffff]
[    0.539850] bus: 03 index 2 mmio: [0, 0]
[    0.539852] bus: 03 index 3 mmio: [0, 0]
[    0.539854] bus: 04 index 0 mmio: [0, 0]
[    0.539856] bus: 04 index 1 mmio: [50500000, 505fffff]
[    0.539858] bus: 04 index 2 mmio: [0, 0]
[    0.539860] bus: 04 index 3 mmio: [0, 0]
[    0.539863] bus: 05 index 0 mmio: [0, 0]
[    0.539865] bus: 05 index 1 mmio: [50600000, 506fffff]
[    0.539867] bus: 05 index 2 mmio: [0, 0]
[    0.539869] bus: 05 index 3 mmio: [0, 0]
[    0.539872] bus: 06 index 0 io port: [1000, 1fff]
[    0.539874] bus: 06 index 1 mmio: [50000000, 500fffff]
[    0.539876] bus: 06 index 2 mmio: [0, 0]
[    0.539878] bus: 06 index 3 io port: [0, ffff]
[    0.539880] bus: 06 index 4 mmio: [0, ffffffff]
[    0.539891] NET: Registered protocol family 2
[    0.552128] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.552475] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.552782] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.552956] TCP: Hash tables configured (established 131072 bind 65536)
[    0.552960] TCP reno registered
[    0.560148] NET: Registered protocol family 1
[    0.560293] checking if image is initramfs... it is
[    0.996675] Switched to high resolution mode on CPU 1
[    1.000094] Switched to high resolution mode on CPU 0
[    1.191890] Freeing initrd memory: 7990k freed
[    1.193626] audit: initializing netlink socket (disabled)
[    1.193644] type=2000 audit(1229716976.192:1): initialized
[    1.198733] highmem bounce pool size: 64 pages
[    1.198741] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.202539] VFS: Disk quotas dquot_6.5.1
[    1.202674] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.202830] msgmni has been set to 1762
[    1.203011] io scheduler noop registered
[    1.203015] io scheduler anticipatory registered
[    1.203018] io scheduler deadline registered
[    1.203034] io scheduler cfq registered (default)
[    1.203240] pci 0000:01:00.0: Boot video device
[    1.203258] pci 0000:06:08.0: Firmware left e100 interrupts enabled; disabling
[    1.203423] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.203466] pcieport-driver 0000:00:01.0: found MSI capability
[    1.203504] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.203578] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.203712] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.203750] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.203788] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.203858] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.203937] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.204077] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.204115] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.204153] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.204226] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.204308] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.204435] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.204473] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.204511] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.204581] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.204661] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.204796] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.204834] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.204872] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.204945] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.205034] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.205660] isapnp: Scanning for PnP cards...
[    1.557326] isapnp: No Plug & Play device found
[    1.617978] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.618148] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.619115] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.622343] brd: module loaded
[    1.622458] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.622642] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.622646] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.623324] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.623759] mice: PS/2 mouse device common for all mice
[    1.623985] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.624020] rtc0: alarms up to one month, hpet irqs
[    1.624254] EISA: Probing bus 0 at eisa.0
[    1.624261] Cannot allocate resource for EISA slot 1
[    1.624264] Cannot allocate resource for EISA slot 2
[    1.624266] Cannot allocate resource for EISA slot 3
[    1.624284] EISA: Detected 0 cards.
[    1.624289] cpuidle: using governor ladder
[    1.624292] cpuidle: using governor menu
[    1.624964] TCP cubic registered
[    1.624995] Using IPI No-Shortcut mode
[    1.625292] registered taskstats version 1
[    1.625430]   Magic number: 4:548:43
[    1.625437] tty ttyec: hash matches
[    1.625511] rtc_cmos 00:03: setting system clock to 2008-12-19 20:02:57 UTC (1229716977)
[    1.625515] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.625518] EDD information not available.
[    1.625770] Freeing unused kernel memory: 424k freed
[    1.625829] Write protecting the kernel text: 2576k
[    1.625865] Write protecting the kernel read-only data: 936k
[    1.645050] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.761147] fuse init (API version 7.9)
[    2.367617] processor ACPI0007:00: registered as cooling_device0
[    2.367624] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.367849] processor ACPI0007:01: registered as cooling_device1
[    2.367859] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.925637] usbcore: registered new interface driver usbfs
[    2.925683] usbcore: registered new interface driver hub
[    2.925786] usbcore: registered new device driver usb
[    2.937587] USB Universal Host Controller Interface driver v3.0
[    2.937658] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.937671] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.937677] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.937746] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.937785] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    2.938020] usb usb1: configuration #1 chosen from 1 choice
[    2.938071] hub 1-0:1.0: USB hub found
[    2.938085] hub 1-0:1.0: 2 ports detected
[    2.973091] No dock devices found.
[    3.041442] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.041457] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.041464] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.041512] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.041553] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    3.041792] usb usb2: configuration #1 chosen from 1 choice
[    3.041875] hub 2-0:1.0: USB hub found
[    3.041891] hub 2-0:1.0: 2 ports detected
[    3.049307] SCSI subsystem initialized
[    3.049435] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    3.049440] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.108177] libata version 3.00 loaded.
[    3.108250] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.252379] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.252392] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.252398] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.252441] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.252490] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    3.252639] usb usb3: configuration #1 chosen from 1 choice
[    3.252684] hub 3-0:1.0: USB hub found
[    3.252696] hub 3-0:1.0: 2 ports detected
[    3.369034] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.460566] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.460583] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.460593] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.460677] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.460733] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    3.460985] usb usb4: configuration #1 chosen from 1 choice
[    3.461064] hub 4-0:1.0: USB hub found
[    3.461092] hub 4-0:1.0: 2 ports detected
[    3.538657] usb 2-1: configuration #1 chosen from 1 choice
[    3.545889] hub 2-1:1.0: USB hub found
[    3.553062] hub 2-1:1.0: 4 ports detected
[    3.568735] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.568755] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.568762] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.568807] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.572739] ehci_hcd 0000:00:1d.7: debug port 1
[    3.572748] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.572760] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x50204000
[    3.588056] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.588471] usb usb5: configuration #1 chosen from 1 choice
[    3.588599] hub 5-0:1.0: USB hub found
[    3.588634] hub 5-0:1.0: 8 ports detected
[    3.666676] hub 2-1:1.0: hub_port_status failed (err = -71)
[    3.667669] hub 2-1:1.0: hub_port_status failed (err = -71)
[    3.668672] hub 2-1:1.0: hub_port_status failed (err = -71)
[    3.669670] hub 2-1:1.0: hub_port_status failed (err = -71)
[    3.670001] usb 2-1: USB disconnect, address 2
[    3.796451] e100 0000:06:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.817595] e100 0000:06:08.0: PME# disabled
[    3.817970] e100: eth0: e100_probe: addr 0x50000000, irq 20, MAC addr 00:13:20:5b:91:34
[    3.818339] via-rhine 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.824245] eth1: VIA Rhine III at 0x50002000, 00:19:5b:69:c3:58, IRQ 22.
[    3.824961] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
[    3.825013] ohci1394 0000:06:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.876779] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[50001000-500017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    3.892709] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.892771] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.892803] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.892882] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.892931] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    3.892956] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    3.897767] ata_piix 0000:00:1f.1: version 2.12
[    3.897782] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.897832] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.898144] scsi0 : ata_piix
[    3.899606] scsi1 : ata_piix
[    3.900949] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[    3.900956] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[    4.036029] usb 5-3: new high speed USB device using ehci_hcd and address 2
[    4.072398] ata1.00: ATAPI: _NEC DVD_RW ND-3540A, 1.01, max UDMA/33
[    4.072423] ata1.01: ATAPI: SAMSUNG CD-ROM  SC-148A, B400, max UDMA/33
[    4.088333] ata1.00: configured for UDMA/33
[    4.108297] ata1.01: configured for UDMA/33
[    4.108348] ata2: port disabled. ignoring.
[    4.109487] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-3540A  1.01 PQ: 0 ANSI: 5
[    4.110063] scsi 0:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148A   B400 PQ: 0 ANSI: 5
[    4.110209] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.110217] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    4.110281] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.110374] scsi2 : ata_piix
[    4.110500] scsi3 : ata_piix
[    4.110578] ata3: SATA max UDMA/133 cmd 0x30c8 ctl 0x30e4 bmdma 0x30a0 irq 19
[    4.110584] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e0 bmdma 0x30a8 irq 19
[    4.170115] usb 5-3: configuration #1 chosen from 1 choice
[    4.170639] hub 5-3:1.0: USB hub found
[    4.170945] hub 5-3:1.0: 4 ports detected
[    4.273496] ata3.00: ATA-6: WDC WD2000JD-22HBB0, 08.02D08, max UDMA/133
[    4.273502] ata3.00: 390721968 sectors, multi 16: LBA48 
[    4.289508] ata3.00: configured for UDMA/133
[    4.454941] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2000JD-22H 08.0 PQ: 0 ANSI: 5
[    4.473952] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.474027] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.474101] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    4.496719] Driver 'sd' needs updating - please use bus_type methods
[    4.496912] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    4.496951] sd 2:0:0:0: [sda] Write Protect is off
[    4.496958] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.497058] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.497196] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    4.497230] sd 2:0:0:0: [sda] Write Protect is off
[    4.497235] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.497296] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.497304]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    4.512340] usb 5-3.2: new high speed USB device using ehci_hcd and address 4
[    4.515587] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.515593] Uniform CD-ROM driver Revision: 3.20
[    4.515714] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.517698]  sda5sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    4.519201] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    4.527477]  sda6 sda7 >
[    4.539035] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.606830] usb 5-3.2: configuration #1 chosen from 1 choice
[    4.856040] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.029045] usb 3-1: configuration #1 chosen from 1 choice
[    5.031930] usbcore: registered new interface driver libusual
[    5.046292] Initializing USB Mass Storage driver...
[    5.046464] scsi4 : SCSI emulation for USB Mass Storage devices
[    5.046635] usbcore: registered new interface driver usb-storage
[    5.046642] USB Mass Storage support registered.
[    5.055849] usb-storage: device found at 4
[    5.055855] usb-storage: waiting for device to settle before scanning
[    5.062163] usbcore: registered new interface driver hiddev
[    5.074850] input: CHESEN USB MOUSE as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input2
[    5.075193] input,hidraw0: USB HID v1.10 Mouse [CHESEN USB MOUSE] on usb-0000:00:1d.2-1
[    5.075217] usbcore: registered new interface driver usbhid
[    5.075222] usbhid: v2.6:USB HID core driver
[    5.154296] PM: Starting manual resume from disk
[    5.154300] PM: Resume from partition 8:5
[    5.154302] PM: Checking hibernation image.
[    5.154450] PM: Resume from disk failed.
[    5.157837] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00132000005b9134]
[    5.204059] kjournald starting.  Commit interval 5 seconds
[    5.204070] EXT3-fs: mounted filesystem with ordered data mode.
[    9.878503] udevd version 124 started
[   10.053183] usb-storage: device scan complete
[   10.077960] scsi 4:0:0:0: Direct-Access     Creative NOMAD MuVo TX    0100 PQ: 0 ANSI: 4
[   10.079261] sd 4:0:0:0: [sdb] 1005824 512-byte hardware sectors (515 MB)
[   10.079760] sd 4:0:0:0: [sdb] Write Protect is off
[   10.079767] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.079772] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   10.081389] sd 4:0:0:0: [sdb] 1005824 512-byte hardware sectors (515 MB)
[   10.081885] sd 4:0:0:0: [sdb] Write Protect is off
[   10.081891] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.081895] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   10.081902]  sdb: sdb1
[   10.083686] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   10.083861] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   10.339087] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.371562] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.525611] Linux agpgart interface v0.103
[   10.740692] intel_rng: Firmware space is locked read-only. If you can't or
[   10.740696] intel_rng: don't want to disable this in firmware setup, and if
[   10.740699] intel_rng: you are certain that your system has a functional
[   10.740702] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   10.881515] iTCO_vendor_support: vendor-support=0
[   10.914592] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   10.914793] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0460)
[   10.914985] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.106820] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.203434] [fglrx] Maximum main memory to use for locked dma buffers: 910 MBytes.
[   11.204024] [fglrx]   vendor: 1002 device: 5b63 count: 1
[   11.205775] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   11.205796] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.205804] pci 0000:01:00.0: setting latency timer to 64
[   11.208348] [fglrx] PAT is enabled successfully!
[   11.208392] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   11.211258] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.233039] ACPI: Power Button (FF) [PWRF]
[   11.233170] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   11.265056] ACPI: Sleep Button (CM) [SLPB]
[   12.007079] parport_pc 00:07: reported by Plug and Play ACPI
[   12.007109] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   12.871784] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.871819] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.888436] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.901710] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   14.873961] lp0: using parport0 (interrupt-driven).
[   15.072786] Adding 995956k swap on /dev/sda5.  Priority:-1 extents:1 across:995956k
[   15.641758] EXT3 FS on sda6, internal journal
[   16.706458] type=1505 audit(1229734992.961:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4087
[   16.875082] type=1505 audit(1229734993.129:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4092
[   16.875272] type=1505 audit(1229734993.129:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4092
[   17.038183] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.095074] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   17.095248] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   17.095251] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   17.095254] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   17.225941] NET: Registered protocol family 10
[   17.226718] lo: Disabled Privacy Extensions
[   17.245030] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   18.234221] ACPI: WMI: Mapper loaded
[   19.108231] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.182178] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   19.182186] apm: disabled - APM is not SMP safe.
[   19.428201] ppdev: user-space parallel port driver
[   20.695065] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.695073] vboxdrv: Successfully done.
[   20.695078] vboxdrv: Found 2 processor cores.
[   20.695254] vboxdrv: fAsync=0 offMin=0x400 offMax=0x2c70
[   20.695287] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.695292] vboxdrv: Successfully loaded version 2.0.6 (interface 0x00090000).
[   22.446279] Bluetooth: Core ver 2.13
[   22.446870] NET: Registered protocol family 31
[   22.446875] Bluetooth: HCI device and connection manager initialized
[   22.446882] Bluetooth: HCI socket layer initialized
[   22.466417] Bluetooth: L2CAP ver 2.11
[   22.466424] Bluetooth: L2CAP socket layer initialized
[   22.482234] Bluetooth: SCO (Voice Link) ver 0.6
[   22.482241] Bluetooth: SCO socket layer initialized
[   22.499548] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.499555] Bluetooth: BNEP filters: protocol multicast
[   22.528540] Bridge firewalling registered
[   22.528769] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   22.559030] Bluetooth: RFCOMM socket layer initialized
[   22.559053] Bluetooth: RFCOMM TTY layer initialized
[   22.559058] Bluetooth: RFCOMM ver 1.10
[   26.683022] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.694784] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
[   26.834195] NET: Registered protocol family 17
[   30.861167] [fglrx] CMM init INV FB MC:0xc8000000, length:0x8000000
[   30.861183] [fglrx] Reserved FB block: Shared offset:0, size:40000 
[   30.861186] [fglrx] Reserved FB block: Unshared offset:7fbc000, size:44000 
[   36.928012] eth1: no IPv6 routers present
[   44.570247] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:19:5b:69:c3:58:00:19:e4:17:52:c1:08:00 SRC=24.41.21.22 DST=192.168.1.73 LEN=31 TOS=0x00 PREC=0x20 TTL=46 ID=1533 PROTO=UDP SPT=3291 DPT=56460 LEN=11 
[   64.671896] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:19:5b:69:c3:58:00:19:e4:17:52:c1:08:00 SRC=24.41.21.22 DST=192.168.1.73 LEN=31 TOS=0x00 PREC=0x20 TTL=46 ID=56252 PROTO=UDP SPT=3291 DPT=56460 LEN=11 
[  115.087727] ppdev0: registered pardevice
[  115.136025] ppdev0: unregistered pardevice
[  115.356305] ppdev0: registered pardevice
[  115.404311] ppdev0: unregistered pardevice
[  116.482464] type=1503 audit(1229735092.737:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5946/net/" pid=5946 profile="/usr/sbin/cupsd"
[  117.513472] type=1503 audit(1229735093.770:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5950/net/" pid=5950 profile="/usr/sbin/cupsd"
[  117.513522] type=1503 audit(1229735093.770:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5950 profile="/usr/sbin/cupsd"
[  117.513539] type=1503 audit(1229735093.770:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5950 profile="/usr/sbin/cupsd"
[  117.513554] type=1503 audit(1229735093.770:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5950 profile="/usr/sbin/cupsd"
[  117.513570] type=1503 audit(1229735093.770:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5950 profile="/usr/sbin/cupsd"
[  117.513585] type=1503 audit(1229735093.770:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5950 profile="/usr/sbin/cupsd"
[  117.513603] type=1503 audit(1229735093.770:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5950 profile="/usr/sbin/cupsd"
[  117.513618] type=1503 audit(1229735093.770:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5950 profile="/usr/sbin/cupsd"
[  117.513633] type=1503 audit(1229735093.770:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5950 profile="/usr/sbin/cupsd"
[  118.068319] ppdev0: registered pardevice
[  118.116183] ppdev0: unregistered pardevice
[ 1080.526339] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:19:5b:69:c3:58:00:19:5b:44:71:10:08:00 SRC=192.168.1.69 DST=192.168.1.73 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=44842 DF PROTO=TCP SPT=4588 DPT=49315 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 1140.563223] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:19:5b:69:c3:58:00:19:5b:44:71:10:08:00 SRC=192.168.1.69 DST=192.168.1.73 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=44919 DF PROTO=TCP SPT=4593 DPT=56460 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 1142.666320] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:19:5b:69:c3:58:00:19:5b:44:71:10:08:00 SRC=192.168.1.69 DST=192.168.1.73 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=44922 DF PROTO=TCP SPT=4594 DPT=56460 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 1203.384716] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1204.080547] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1204.080581] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1204.113713] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[ 2880.965026] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:19:5b:69:c3:58:00:19:5b:44:71:10:08:00 SRC=192.168.1.69 DST=192.168.1.73 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=55150 DF PROTO=TCP SPT=4655 DPT=49315 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 2883.072851] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:19:5b:69:c3:58:00:19:5b:44:71:10:08:00 SRC=192.168.1.69 DST=192.168.1.73 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=55155 DF PROTO=TCP SPT=4656 DPT=49315 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 2940.973585] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:19:5b:69:c3:58:00:19:5b:44:71:10:08:00 SRC=192.168.1.69 DST=192.168.1.73 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=55302 DF PROTO=TCP SPT=4665 DPT=56460 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 2943.078771] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:19:5b:69:c3:58:00:19:5b:44:71:10:08:00 SRC=192.168.1.69 DST=192.168.1.73 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=55310 DF PROTO=TCP SPT=4666 DPT=56460 WINDOW=16384 RES=0x00 SYN URGP=0 
miked860@miked860-desktop:~$ 
```

---

### Post by linux_tech on 2008-12-19
Give a reboot a try.

---

### Post by miked860 on 2008-12-19
Doesn't change anything. I beginning to get the feeling I'm screwed.

---

### Post by mosimea on 2008-12-19
Have you recently installed/upgraded your flash plugin?  I know that sometimes screws up the sound.  If so, you can try:

```
 sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
 sudo rm -r ~/.pulse ~/.asound* 
 sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio flashplugin-nonfree
sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
sudo /etc/init.d/alsa-utils restart
```

---

### Post by miked860 on 2008-12-19
No change.

---

### Post by linux_tech on 2008-12-19
Are any other sound devices plugged in such as mp3 player?

Also check for shared irq's- ```
cat /proc/interrupts
```

check to make sure sound modules are loaded
```
lsmod | grep snd
```

---

### Post by miked860 on 2008-12-19
```
miked860@miked860-desktop:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        124          0   IO-APIC-edge      timer
  1:        478          0   IO-APIC-edge      i8042
  4:          2          0   IO-APIC-edge    
  7:          0          0   IO-APIC-edge      parport0
  8:         55          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 14:      28203          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:      74630          0   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel
 17:          3          0   IO-APIC-fasteoi   ohci1394
 18:      16410          0   IO-APIC-fasteoi   uhci_hcd:usb3
 19:      19753          0   IO-APIC-fasteoi   uhci_hcd:usb2, ata_piix
 20:        801          0   IO-APIC-fasteoi   eth0
 22:      33258          0   IO-APIC-fasteoi   eth1
 23:       3616          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
NMI:          0          0   Non-maskable interrupts
LOC:     137736     178769   Local timer interrupts
RES:       4732       5789   Rescheduling interrupts
CAL:       7157       7791   function call interrupts
TLB:       1558       2042   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
miked860@miked860-desktop:~$ lsmod | grep snd
snd_hda_intel         381488  4 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
```

---

### Post by RJARRRPCGP on 2008-12-19
Reseat your sound card, especially if you have a SoundBlaster!

---

### Post by miked860 on 2008-12-19
The soundcard in integrated. I also don't think there is a connection error because it works perfectly fine in Windows.

---

### Post by linux_tech on 2008-12-19
Are there any irq conflicts?  Any change yet? If not
try installing alsa-oss & libasound-
 ```
sudo apt-get install libasound2
```
 ```
sudo apt-get install libasound2-plugins
 sudo apt-get install alsa-oss
```
then test again

---

### Post by miked860 on 2008-12-19
irq conflicts? Still no change.

---

### Post by miked860 on 2008-12-19
Well something finally worked. Audio is magically back now. Thanks for all your help and time guys.

---

### Post by linux_tech on 2008-12-19
glad to hear that sound is working!

---

