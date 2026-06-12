---
title: "Raid 5 Array not recognized anymore"
date: 2009-02-28
forum: General Help
---

### Post by Pringles on 2009-02-28
Hello Everyone,

I had been running Ubuntu 8.10 great for a long time, 8.04 before that, and 7.04 before that. I had a Raid 5 setup on 4 250 GB hard drives setup as my home directory. The OS and swap were on sda, the raid on sdb-sde.

I decided to try the elive compiz live cd. Well, it failed to boot, then Ubuntu failed to boot. It gave me an fsck error. So I wiped out sda and reinstalled Ubuntu 8.10 hoping it would still recognize the raid.

Well, I go to Computer and there is the "750.2 GB of media", I try to double-click to mount it or open it and I get: "Cannot mount volume" "Unable to mount volume".

I tried going into gparted to see what it sees and they all have the raid flag but they are of unknown filesystems.

Here is my dmesg:

```
[    1.279312] VFS: Disk quotas dquot_6.5.1
[    1.279404] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.279508] msgmni has been set to 15981
[    1.279621] io scheduler noop registered
[    1.279623] io scheduler anticipatory registered
[    1.279625] io scheduler deadline registered
[    1.279751] io scheduler cfq registered (default)
[    1.279893] pci 0000:01:00.0: Boot video device
[    1.280006] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.280046] pcieport-driver 0000:00:01.0: found MSI capability
[    1.280064] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.280116] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.280205] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.280233] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.280262] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.280307] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.280352] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.280437] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.280465] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.280494] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.280553] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.280601] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.312909] Linux agpgart interface v0.103
[    1.312914] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.315308] brd: module loaded
[    1.315395] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.315583] PNP: No PS/2 controller found. Probing ports directly.
[    1.317894] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.317898] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.333644] mice: PS/2 mouse device common for all mice
[    1.333792] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.333822] rtc0: alarms up to one month, hpet irqs
[    1.333864] cpuidle: using governor ladder
[    1.333866] cpuidle: using governor menu
[    1.334218] TCP cubic registered
[    1.334423] registered taskstats version 1
[    1.334541]   Magic number: 13:180:183
[    1.334563] tty ttyr9: hash matches
[    1.334633] rtc_cmos 00:03: setting system clock to 2009-02-28 14:11:38 UTC (1235830298)
[    1.334636] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.334638] EDD information not available.
[    1.334676] Freeing unused kernel memory: 540k freed
[    1.334806] Write protecting the kernel read-only data: 4352k
[    1.425230] fuse init (API version 7.9)
[    1.436678] ACPI: SSDT CFEE7F80, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[    1.436898] processor ACPI0007:00: registered as cooling_device0
[    1.437071] ACPI: SSDT CFEE8440, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[    1.437259] processor ACPI0007:01: registered as cooling_device1
[    1.437435] ACPI: SSDT CFEE85A0, 0152 (r1  PmRef  Cpu2Ist     3000 INTL 20041203)
[    1.437616] processor ACPI0007:02: registered as cooling_device2
[    1.437787] ACPI: SSDT CFEE8700, 0152 (r1  PmRef  Cpu3Ist     3000 INTL 20041203)
[    1.437968] processor ACPI0007:03: registered as cooling_device3
[    1.440872] thermal LNXTHERM:01: registered as thermal_zone0
[    1.441069] ACPI: Thermal Zone [THRM] (20 C)
[    1.449837] md: linear personality registered for level -1
[    1.452221] md: multipath personality registered for level -4
[    1.454334] md: raid0 personality registered for level 0
[    1.457151] md: raid1 personality registered for level 1
[    1.458853] xor: automatically using best checksumming function: generic_sse
[    1.476999]    generic_sse: 10698.000 MB/sec
[    1.477000] xor: using function: generic_sse (10698.000 MB/sec)
[    1.477771] async_tx: api initialized (async)
[    1.545017] raid6: int64x1   2689 MB/s
[    1.613010] raid6: int64x2   3672 MB/s
[    1.681007] raid6: int64x4   3453 MB/s
[    1.749010] raid6: int64x8   2583 MB/s
[    1.817003] raid6: sse2x1    4535 MB/s
[    1.885006] raid6: sse2x2    6751 MB/s
[    1.953001] raid6: sse2x4    8553 MB/s
[    1.953002] raid6: using algorithm sse2x4 (8553 MB/s)
[    1.953004] md: raid6 personality registered for level 6
[    1.953005] md: raid5 personality registered for level 5
[    1.953006] md: raid4 personality registered for level 4
[    1.965705] md: raid10 personality registered for level 10
[    2.063621] usbcore: registered new interface driver usbfs
[    2.063636] usbcore: registered new interface driver hub
[    2.065585] usbcore: registered new device driver usb
[    2.066973] USB Universal Host Controller Interface driver v3.0
[    2.067071] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.067079] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.067082] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.068297] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.068326] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[    2.068420] usb usb1: configuration #1 chosen from 1 choice
[    2.068439] hub 1-0:1.0: USB hub found
[    2.068444] hub 1-0:1.0: 2 ports detected
[    2.072749] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.080638] No dock devices found.
[    2.091011] SCSI subsystem initialized
[    2.103928] libata version 3.00 loaded.
[    2.169893] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.169901] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.169904] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.169922] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.169951] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[    2.170014] usb usb2: configuration #1 chosen from 1 choice
[    2.170032] hub 2-0:1.0: USB hub found
[    2.170036] hub 2-0:1.0: 2 ports detected
[    2.377761] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.377768] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.377771] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.377796] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.377823] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fd00
[    2.377886] usb usb3: configuration #1 chosen from 1 choice
[    2.377902] hub 3-0:1.0: USB hub found
[    2.377907] hub 3-0:1.0: 2 ports detected
[    2.480268] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.480278] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.480280] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.480303] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.484199] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.484207] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
[    2.488082] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    2.501577] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.501644] usb usb4: configuration #1 chosen from 1 choice
[    2.501670] hub 4-0:1.0: USB hub found
[    2.501677] hub 4-0:1.0: 6 ports detected
[    2.556052] hub 2-0:1.0: unable to enumerate USB device on port 1
[    2.709708] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.709714] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.709717] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.709746] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.709770] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[    2.709825] usb usb5: configuration #1 chosen from 1 choice
[    2.709840] hub 5-0:1.0: USB hub found
[    2.709845] hub 5-0:1.0: 2 ports detected
[    2.814276] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.814280] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.814283] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.814300] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.814318] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[    2.814378] usb usb6: configuration #1 chosen from 1 choice
[    2.814394] hub 6-0:1.0: USB hub found
[    2.814398] hub 6-0:1.0: 2 ports detected
[    2.824544] usb 4-3: new high speed USB device using ehci_hcd and address 2
[    2.918295] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.918300] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.918302] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.918318] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.918337] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[    2.918392] usb usb7: configuration #1 chosen from 1 choice
[    2.918409] hub 7-0:1.0: USB hub found
[    2.918413] hub 7-0:1.0: 2 ports detected
[    2.956960] usb 4-3: configuration #1 chosen from 1 choice
[    2.957517] hub 4-3:1.0: USB hub found
[    2.957642] hub 4-3:1.0: 4 ports detected
[    3.022419] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.022428] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.022431] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.022456] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.026356] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.026360] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
[    3.041525] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.041591] usb usb8: configuration #1 chosen from 1 choice
[    3.041616] hub 8-0:1.0: USB hub found
[    3.041624] hub 8-0:1.0: 6 ports detected
[    3.146018] ahci 0000:00:1f.2: version 3.0
[    3.146027] ahci 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.146175] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    3.146177] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ems 
[    3.146181] ahci 0000:00:1f.2: setting latency timer to 64
[    3.146468] scsi0 : ahci
[    3.146551] scsi1 : ahci
[    3.146609] scsi2 : ahci
[    3.146665] scsi3 : ahci
[    3.146724] scsi4 : ahci
[    3.146784] scsi5 : ahci
[    3.146870] ata1: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 2300
[    3.146872] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 2300
[    3.146875] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    3.146877] ata4: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    3.146879] ata5: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    3.146881] ata6: SATA max UDMA/133 irq_stat 0x00000040, connection status changed
[    3.252158] usb 4-3.2: new low speed USB device using ehci_hcd and address 3
[    3.365743] usb 4-3.2: configuration #1 chosen from 1 choice
[    3.464031] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.464596] ata1.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    3.464598] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.465300] ata1.00: configured for UDMA/133
[    4.188032] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.188557] ata2.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    4.188560] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.189235] ata2.00: configured for UDMA/133
[    4.912031] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.912575] ata3.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    4.912578] ata3.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.913258] ata3.00: configured for UDMA/133
[    5.640031] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.640588] ata4.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    5.640590] ata4.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.641286] ata4.00: configured for UDMA/133
[    6.364031] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.364570] ata5.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    6.364573] ata5.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.365248] ata5.00: configured for UDMA/133
[    7.088031] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.088306] ata6.00: ATAPI: ASUS    DRW-2014L1T, 1.00, max UDMA/66, ATAPI AN
[    7.088729] ata6.00: configured for UDMA/66
[    7.088827] scsi 0:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    7.088950] scsi 1:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    7.089066] scsi 2:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    7.089142] scsi 3:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    7.089215] scsi 4:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    7.094095] scsi 5:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.00 PQ: 0 ANSI: 5
[    7.094213] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    7.094231] r8169 0000:04:00.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    7.094361] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.094641] eth0: RTL8169sc/8110sc at 0xffffc20000c3c000, 00:50:8d:b5:b0:e9, XID 18000000 IRQ 23
[    7.095304] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    7.095318] r8169 0000:04:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.095485] eth1: RTL8169sc/8110sc at 0xffffc20000c3e000, 00:50:8d:b5:b0:ea, XID 18000000 IRQ 22
[    7.112348] usbcore: registered new interface driver hiddev
[    7.112701] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    7.112704] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    7.112709] ahci 0000:03:00.0: setting latency timer to 64
[    7.112799] scsi6 : ahci
[    7.112863] scsi7 : ahci
[    7.112919] ata7: SATA max UDMA/133 abar m8192@0xfdafe000 port 0xfdafe100 irq 16
[    7.112922] ata8: SATA max UDMA/133 abar m8192@0xfdafe000 port 0xfdafe180 irq 16
[    7.114841] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.7/usb4/4-3/4-3.2/4-3.2:1.0/input/input1
[    7.140124] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.7-3.2
[    7.146543] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.7/usb4/4-3/4-3.2/4-3.2:1.1/input/input2
[    7.177629] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.7-3.2
[    7.177648] usbcore: registered new interface driver usbhid
[    7.177651] usbhid: v2.6:USB HID core driver
[    7.428091] ata7: SATA link down (SStatus 0 SControl 300)
[    7.764543] ata8: SATA link down (SStatus 0 SControl 300)
[    7.780093] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    7.780105] pata_acpi 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.780139] pata_acpi 0000:03:00.1: setting latency timer to 64
[    7.780153] pata_acpi 0000:03:00.1: PCI INT B disabled
[    7.780173] ohci1394 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    7.829888] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fddfd000-fddfd7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.830022] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.830048] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    7.830072] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    7.830096] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[    7.830121] scsi 4:0:0:0: Attached scsi generic sg4 type 0
[    7.830158] scsi 5:0:0:0: Attached scsi generic sg5 type 5
[    7.831576] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.831600] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    7.831652] scsi8 : pata_jmicron
[    7.831702] scsi9 : pata_jmicron
[    7.831729] ata9: PATA max UDMA/100 cmd 0xbf00 ctl 0xbe00 bmdma 0xbb00 irq 17
[    7.831731] ata10: PATA max UDMA/100 cmd 0xbd00 ctl 0xbc00 bmdma 0xbb08 irq 17
[    7.843956] Driver 'sd' needs updating - please use bus_type methods
[    7.844033] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    7.844043] sd 0:0:0:0: [sda] Write Protect is off
[    7.844045] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.844062] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.844118] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    7.844127] sd 0:0:0:0: [sda] Write Protect is off
[    7.844129] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.844146] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.844148]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.858461]  sda1 sda2 < sda5 >
[    7.884220] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.884310] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    7.884321] sd 1:0:0:0: [sdb] Write Protect is off
[    7.884322] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.884340] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.884383] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    7.884393] sd 1:0:0:0: [sdb] Write Protect is off
[    7.884395] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.884411] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.884414]  sdb: sdb1 < sdb5 >
[    7.901360] sd 1:0:0:0: [sdb] Attached SCSI disk
[    7.901426] sd 2:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    7.901441] sd 2:0:0:0: [sdc] Write Protect is off
[    7.901444] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.901470] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.901523] sd 2:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    7.901537] sd 2:0:0:0: [sdc] Write Protect is off
[    7.901539] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.901565] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.901568]  sdc: sdc1
[    7.917704] sd 2:0:0:0: [sdc] Attached SCSI disk
[    7.917787] sd 3:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
[    7.917798] sd 3:0:0:0: [sdd] Write Protect is off
[    7.917799] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    7.917816] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.917851] sd 3:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
[    7.917861] sd 3:0:0:0: [sdd] Write Protect is off
[    7.917862] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    7.917879] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.917882]  sdd: sdd1
[    7.933315] sd 3:0:0:0: [sdd] Attached SCSI disk
[    7.933379] sd 4:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[    7.933389] sd 4:0:0:0: [sde] Write Protect is off
[    7.933391] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    7.933408] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.933442] sd 4:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[    7.933452] sd 4:0:0:0: [sde] Write Protect is off
[    7.933454] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    7.933470] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.933473]  sde: sde1
[    7.950660] sd 4:0:0:0: [sde] Attached SCSI disk
[    7.953512] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.953516] Uniform CD-ROM driver Revision: 3.20
[    7.953592] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    7.992516] ata9.00: ATAPI: ASUS    DVD-E616A3, 1.10, max UDMA/100
[    8.008555] ata9.00: configured for UDMA/100
[    8.176379] scsi 8:0:0:0: CD-ROM            ASUS     DVD-E616A3       1.10 PQ: 0 ANSI: 5
[    8.176510] scsi 8:0:0:0: Attached scsi generic sg6 type 5
[    8.184049] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    8.184118] sr 8:0:0:0: Attached scsi CD-ROM sr1
[    8.295763] md: md0 stopped.
[    8.350832] md: bind<sdd1>
[    8.350856] md: could not bd_claim sdd1.
[    8.350860] md: md_import_device returned -16
[    8.351006] md: bind<sde1>
[    8.351142] md: bind<sdb5>
[    8.384836] md: md0 stopped.
[    8.384847] md: unbind<sdb5>
[    8.409143] md: export_rdev(sdb5)
[    8.409161] md: unbind<sde1>
[    8.421023] md: export_rdev(sde1)
[    8.421031] md: unbind<sdd1>
[    8.433023] md: export_rdev(sdd1)
[    8.464025] md: bind<sdc1>
[    8.464205] md: bind<sdd1>
[    8.464338] md: bind<sde1>
[    8.464470] md: bind<sdb5>
[    8.468978] raid5: device sdb5 operational as raid disk 0
[    8.468980] raid5: device sde1 operational as raid disk 3
[    8.468981] raid5: device sdd1 operational as raid disk 2
[    8.468983] raid5: device sdc1 operational as raid disk 1
[    8.469356] raid5: allocated 4288kB for md0
[    8.469357] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
[    8.469359] RAID5 conf printout:
[    8.469360]  --- rd:4 wd:4
[    8.469361]  disk 0, o:1, dev:sdb5
[    8.469362]  disk 1, o:1, dev:sdc1
[    8.469363]  disk 2, o:1, dev:sdd1
[    8.469364]  disk 3, o:1, dev:sde1
[    8.548194] PM: Starting manual resume from disk
[    8.548197] PM: Resume from partition 8:5
[    8.548198] PM: Checking hibernation image.
[    8.548306] PM: Resume from disk failed.
[    8.617527] kjournald starting.  Commit interval 5 seconds
[    8.617543] EXT3-fs: mounted filesystem with ordered data mode.

```

Please let me know if you need anything else. I just want the Raid setup as my home directory again!! :D

Oh, 64-bit Ubuntu if that makes a difference...

Thanks!!

---

### Post by fjgaude on 2009-02-28
When you re-installed did you make a mountpoint for the raid array?

Did you add a line in your **/etc/fstab** file to auto load the array?

Show what your fstab looks like, please.

BTW, **Gparted** doesn't understand arrays, thinks the partition table or something like that is missing. Nothing to worry about.

Here's what many do when they re-install. After installing mdadm they run:

```
sudo mdadm --assemble --scan
```

That creates automatically the **/etc/mdadm/mdadm.conf** file and you can now see if the array is there by running the -D command:

```
sudo mdadm -D /dev/md0
```

Or whatever the array name is.

Let us know how you are doing.

---

### Post by Pringles on 2009-02-28
Ok, mdadm recognizes it, I tried adding it to the fstab but it gave me the same error that I got before...

Here is part of the output from mdadm:
```
UUID : 600fe7cb:985c9a3c:bfe7d7cd:c3e84b05
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8       21        0      active sync   /dev/sdb5
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

```

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1761fe2c-0841-40cb-b347-a758f454a368 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=08d69f97-dd62-49e6-a64d-c425ddeb8b4a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/md0
#UUID=600fe7cb-985c-9a3c-bfe7-d7cdc3e84b05 /home               ext3    relatime,errors=remount-ro 0       2


```

I had to comment out the last uuid because the computer didn't boot...

I know I am doing something wrong but I don't remember what I did a year ago to get the array mounted.

Thanks for your help, I really appreciate it!

---

### Post by fjgaude on 2009-02-28
From where did you get the UUID for the array:

```
# /dev/md0
#UUID=600fe7cb-985c-9a3c-bfe7-d7cdc3e84b05 /home   ext3    relatime,errors=remount-ro 0     2
```

If it comes from the **mdadm.conf** file such is not the UUID to mount, but the UUID from which the array assembles.

Another point, by mounting the array at /home you have all your old hidden "." files that go with the old installed OS... I've never done that before but it might be okay.

Let us know how things go.

---

### Post by Pringles on 2009-02-28
> **fjgaude said:**
> From where did you get the UUID for the array

If it comes from the **mdadm.conf** file such is not the UUID to mount, but the UUID from which the array assembles.

Yes, I got it from the mdadm output... I didn't know how else to get it. How would I go about getting the UUID for the /dev/md0 array?

> **fjgaude said:**
> Another point, by mounting the array at /home you have all your old hidden "." files that go with the old installed OS... I've never done that before but it might be okay.


Yes, I thought of that too. I was hoping it would recover some of my old settings. If it causes problems I will just delete the old ".folders"

Thanks!

---

### Post by fjgaude on 2009-02-28
One way to get the mount UUID of arrays and drives is:

```
blkid
```

It shows all the device UUIDs that can be used as names.

To get **blkid**, you have to install:

```
sudo apt-get install e2fsprogs
```

blkid is part of the **e2fsprogs**... use their **man** pages to learn all about them.

Having an old /home may be an issue. When you installed the new OS it created a new /home, if memory serves me. Let's see what happens. At worth as you mount the raid at /home its data will overwrite what is there. I've never done that before.

---

### Post by Pringles on 2009-02-28
Ok, I got the UUID of the md0 array and I put that into my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1761fe2c-0841-40cb-b347-a758f454a368 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=08d69f97-dd62-49e6-a64d-c425ddeb8b4a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/md0
UUID=09aee066-19a0-47a7-b372-a4ba5e9b7784        /home               ext3    relatime,errors=remount-ro 0       2

```

Then I got this on bootup:

```
Log of fsck -C3 -R -A -a
Sat Feb 28 17:35:58 2009

fsck 1.41.3 (12-Oct-2008)
/dev/md0: Resize inode not valid.

/dev/md0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
fsck died with exit status 4

Sat Feb 28 17:35:59 2009

```

Any ideas? I hate to go through all this trouble but it would kinda suck to lose all 500 GB of this data... Nothing important, but it would still be nice, ya know?

Thanks a lot!

Edit: I am currently running fsck manually on md0... I don't know how long it will take.

---

### Post by fjgaude on 2009-02-28
Strange, and perhaps unlucky that fsck on boot wanted to checked the array so early, usually takes 30 boots for the "2" to take effect.

Let us know how it goes.

---

### Post by Pringles on 2009-02-28
Frank... You are awesome!!!

Thank you so much!

Most of my settings are back, my files are back, I just have to reinstall some programs and my theme.

Thank you!!!!!!

---

### Post by fjgaude on 2009-02-28
I guess things have worked out... the fsck fixed whatever was off in the array?

---

### Post by Pringles on 2009-03-01
Yeah, it said it fixed a few things and changed the files system. I rebooted and it mounted fine as home. I got everything back except my theme and apps.

Thanks!

---

