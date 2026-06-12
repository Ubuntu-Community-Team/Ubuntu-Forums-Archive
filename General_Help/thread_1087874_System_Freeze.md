---
title: "System Freeze"
date: 2009-03-05
forum: General Help
---

### Post by Depressed Man on 2009-03-05
```

Mar  5 11:58:31 vendetta-laptop kernel: [    1.525986] type=2000 audit(1236254282.525:1): initialized
Mar  5 11:58:31 vendetta-laptop kernel: [    1.533123] highmem bounce pool size: 64 pages
Mar  5 11:58:31 vendetta-laptop kernel: [    1.533130] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar  5 11:58:31 vendetta-laptop kernel: [    1.536088] VFS: Disk quotas dquot_6.5.1
Mar  5 11:58:31 vendetta-laptop kernel: [    1.536192] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar  5 11:58:31 vendetta-laptop kernel: [    1.536313] msgmni has been set to 1743
Mar  5 11:58:31 vendetta-laptop kernel: [    1.536451] io scheduler noop registered
Mar  5 11:58:31 vendetta-laptop kernel: [    1.536455] io scheduler anticipatory registered
Mar  5 11:58:31 vendetta-laptop kernel: [    1.536458] io scheduler deadline registered
Mar  5 11:58:31 vendetta-laptop kernel: [    1.536472] io scheduler cfq registered (default)
Mar  5 11:58:31 vendetta-laptop kernel: [    1.536794] pcieport-driver 0000:00:1c.0: found MSI capability
Mar  5 11:58:31 vendetta-laptop kernel: [    1.537130] pcieport-driver 0000:00:1c.1: found MSI capability
Mar  5 11:58:31 vendetta-laptop kernel: [    1.537448] pcieport-driver 0000:00:1c.2: found MSI capability
Mar  5 11:58:31 vendetta-laptop kernel: [    1.537771] pcieport-driver 0000:00:1c.3: found MSI capability
Mar  5 11:58:31 vendetta-laptop kernel: [    1.538322] isapnp: Scanning for PnP cards...
Mar  5 11:58:31 vendetta-laptop kernel: [    1.892212] isapnp: No Plug & Play device found
Mar  5 11:58:31 vendetta-laptop kernel: [    1.932584] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Mar  5 11:58:31 vendetta-laptop kernel: [    1.935350] brd: module loaded
Mar  5 11:58:31 vendetta-laptop kernel: [    1.935437] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Mar  5 11:58:31 vendetta-laptop kernel: [    1.935588] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar  5 11:58:31 vendetta-laptop kernel: [    1.939343] i8042.c: Detected active multiplexing controller, rev 1.1.
Mar  5 11:58:31 vendetta-laptop kernel: [    1.943560] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar  5 11:58:31 vendetta-laptop kernel: [    1.943567] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Mar  5 11:58:31 vendetta-laptop kernel: [    1.943572] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Mar  5 11:58:31 vendetta-laptop kernel: [    1.943575] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Mar  5 11:58:31 vendetta-laptop kernel: [    1.943578] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Mar  5 11:58:31 vendetta-laptop kernel: [    1.944136] mice: PS/2 mouse device common for all mice
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945255] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945287] rtc0: alarms up to one month, y3k, hpet irqs
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945442] EISA: Probing bus 0 at eisa.0
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945450] Cannot allocate resource for EISA slot 1
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945454] Cannot allocate resource for EISA slot 2
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945456] Cannot allocate resource for EISA slot 3
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945459] Cannot allocate resource for EISA slot 4
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945462] Cannot allocate resource for EISA slot 5
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945464] Cannot allocate resource for EISA slot 6
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945476] EISA: Detected 0 cards.
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945479] cpuidle: using governor ladder
Mar  5 11:58:31 vendetta-laptop kernel: [    1.945483] cpuidle: using governor menu
Mar  5 11:58:31 vendetta-laptop kernel: [    1.946084] TCP cubic registered
Mar  5 11:58:31 vendetta-laptop kernel: [    1.946114] Using IPI No-Shortcut mode
Mar  5 11:58:31 vendetta-laptop kernel: [    1.946325] registered taskstats version 1
Mar  5 11:58:31 vendetta-laptop kernel: [    1.946468]   Magic number: 1:962:983
Mar  5 11:58:31 vendetta-laptop kernel: [    1.946584] rtc_cmos 00:07: setting system clock to 2009-03-05 11:58:03 UTC (1236254283)
Mar  5 11:58:31 vendetta-laptop kernel: [    1.946588] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar  5 11:58:31 vendetta-laptop kernel: [    1.946590] EDD information not available.
Mar  5 11:58:31 vendetta-laptop kernel: [    1.946848] Freeing unused kernel memory: 424k freed
Mar  5 11:58:31 vendetta-laptop kernel: [    1.946892] Write protecting the kernel text: 2580k
Mar  5 11:58:31 vendetta-laptop kernel: [    1.946924] Write protecting the kernel read-only data: 940k
Mar  5 11:58:31 vendetta-laptop kernel: [    2.147715] fuse init (API version 7.9)
Mar  5 11:58:31 vendetta-laptop kernel: [    2.153144] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Mar  5 11:58:31 vendetta-laptop kernel: [    2.269561] ACPI: SSDT 7F693082, 01FB (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 11:58:31 vendetta-laptop kernel: [    2.270284] ACPI: SSDT 7F692B41, 04BC (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 11:58:31 vendetta-laptop kernel: [    2.328359] ACPI: CPU0 (power states: C1[C1] C2[C2])
Mar  5 11:58:31 vendetta-laptop kernel: [    2.328426] processor ACPI0007:00: registered as cooling_device0
Mar  5 11:58:31 vendetta-laptop kernel: [    2.328431] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar  5 11:58:31 vendetta-laptop kernel: [    2.328844] ACPI: SSDT 7F69327D, 00C8 (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 11:58:31 vendetta-laptop kernel: [    2.329274] ACPI: SSDT 7F692FFD, 0085 (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 11:58:31 vendetta-laptop kernel: [    2.330361] ACPI: CPU1 (power states: C1[C1] C2[C2])
Mar  5 11:58:31 vendetta-laptop kernel: [    2.330414] processor ACPI0007:01: registered as cooling_device1
Mar  5 11:58:31 vendetta-laptop kernel: [    2.330422] ACPI: Processor [CPU1] (supports 8 throttling states)
Mar  5 11:58:31 vendetta-laptop kernel: [    2.334189] Marking TSC unstable due to TSC halts in idle
Mar  5 11:58:31 vendetta-laptop kernel: [    2.337130] thermal LNXTHERM:01: registered as thermal_zone0
Mar  5 11:58:31 vendetta-laptop kernel: [    2.340095] ACPI: Thermal Zone [TZ00] (55 C)
Mar  5 11:58:31 vendetta-laptop kernel: [    2.342163] thermal LNXTHERM:02: registered as thermal_zone1
Mar  5 11:58:31 vendetta-laptop kernel: [    2.345085] ACPI: Thermal Zone [TZ01] (55 C)
Mar  5 11:58:31 vendetta-laptop kernel: [    2.673059] usbcore: registered new interface driver usbfs
Mar  5 11:58:31 vendetta-laptop kernel: [    2.673084] usbcore: registered new interface driver hub
Mar  5 11:58:31 vendetta-laptop kernel: [    2.673144] usbcore: registered new device driver usb
Mar  5 11:58:31 vendetta-laptop kernel: [    2.675700] USB Universal Host Controller Interface driver v3.0
Mar  5 11:58:31 vendetta-laptop kernel: [    2.675755] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar  5 11:58:31 vendetta-laptop kernel: [    2.675769] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar  5 11:58:31 vendetta-laptop kernel: [    2.675814] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Mar  5 11:58:31 vendetta-laptop kernel: [    2.675851] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
Mar  5 11:58:31 vendetta-laptop kernel: [    2.676006] usb usb1: configuration #1 chosen from 1 choice
Mar  5 11:58:31 vendetta-laptop kernel: [    2.676039] hub 1-0:1.0: USB hub found
Mar  5 11:58:31 vendetta-laptop kernel: [    2.676049] hub 1-0:1.0: 2 ports detected
Mar  5 11:58:31 vendetta-laptop kernel: [    2.720145] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
Mar  5 11:58:31 vendetta-laptop kernel: [    2.777279] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar  5 11:58:31 vendetta-laptop kernel: [    2.777295] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar  5 11:58:31 vendetta-laptop kernel: [    2.777325] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Mar  5 11:58:31 vendetta-laptop kernel: [    2.777364] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001840
Mar  5 11:58:31 vendetta-laptop kernel: [    2.777479] usb usb2: configuration #1 chosen from 1 choice
Mar  5 11:58:31 vendetta-laptop kernel: [    2.777519] hub 2-0:1.0: USB hub found
Mar  5 11:58:31 vendetta-laptop kernel: [    2.777526] hub 2-0:1.0: 2 ports detected
Mar  5 11:58:31 vendetta-laptop kernel: [    2.786979] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
Mar  5 11:58:31 vendetta-laptop kernel: [    2.786983] e100: Copyright(c) 1999-2006 Intel Corporation
Mar  5 11:58:31 vendetta-laptop kernel: [    2.798124] ACPI: ACPI Dock Station Driver
Mar  5 11:58:31 vendetta-laptop kernel: [    2.829071] SCSI subsystem initialized
Mar  5 11:58:31 vendetta-laptop kernel: [    2.881322] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar  5 11:58:31 vendetta-laptop kernel: [    2.881339] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar  5 11:58:31 vendetta-laptop kernel: [    2.881370] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Mar  5 11:58:31 vendetta-laptop kernel: [    2.881411] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
Mar  5 11:58:31 vendetta-laptop kernel: [    2.881516] usb usb3: configuration #1 chosen from 1 choice
Mar  5 11:58:31 vendetta-laptop kernel: [    2.881547] hub 3-0:1.0: USB hub found
Mar  5 11:58:31 vendetta-laptop kernel: [    2.881555] hub 3-0:1.0: 2 ports detected
Mar  5 11:58:31 vendetta-laptop kernel: [    3.089324] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Mar  5 11:58:31 vendetta-laptop kernel: [    3.089341] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Mar  5 11:58:31 vendetta-laptop kernel: [    3.089375] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Mar  5 11:58:31 vendetta-laptop kernel: [    3.089416] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
Mar  5 11:58:31 vendetta-laptop kernel: [    3.089527] usb usb4: configuration #1 chosen from 1 choice
Mar  5 11:58:31 vendetta-laptop kernel: [    3.089559] hub 4-0:1.0: USB hub found
Mar  5 11:58:31 vendetta-laptop kernel: [    3.089567] hub 4-0:1.0: 2 ports detected
Mar  5 11:58:31 vendetta-laptop kernel: [    3.200055] usb 3-2: new full speed USB device using uhci_hcd and address 2
Mar  5 11:58:31 vendetta-laptop kernel: [    3.297526] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar  5 11:58:31 vendetta-laptop kernel: [    3.297548] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar  5 11:58:31 vendetta-laptop kernel: [    3.297583] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Mar  5 11:58:31 vendetta-laptop kernel: [    3.301491] ehci_hcd 0000:00:1d.7: debug port 1
Mar  5 11:58:31 vendetta-laptop kernel: [    3.301508] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd03c4000
Mar  5 11:58:31 vendetta-laptop kernel: [    3.332050] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar  5 11:58:31 vendetta-laptop kernel: [    3.332288] usb usb5: configuration #1 chosen from 1 choice
Mar  5 11:58:31 vendetta-laptop kernel: [    3.332347] hub 5-0:1.0: USB hub found
Mar  5 11:58:31 vendetta-laptop kernel: [    3.332361] hub 5-0:1.0: 8 ports detected
Mar  5 11:58:31 vendetta-laptop kernel: [    3.540384] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar  5 11:58:31 vendetta-laptop kernel: [    3.540749] scsi0 : ata_piix
Mar  5 11:58:31 vendetta-laptop kernel: [    3.541080] scsi1 : ata_piix
Mar  5 11:58:31 vendetta-laptop kernel: [    3.541810] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Mar  5 11:58:31 vendetta-laptop kernel: [    3.541814] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Mar  5 11:58:31 vendetta-laptop kernel: [    3.704583] ata1.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.60, max UDMA/33
Mar  5 11:58:31 vendetta-laptop kernel: [    3.720563] ata1.00: configured for UDMA/33
Mar  5 11:58:31 vendetta-laptop kernel: [    3.722546] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.60 PQ: 0 ANSI: 5
Mar  5 11:58:31 vendetta-laptop kernel: [    3.722730] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar  5 11:58:31 vendetta-laptop kernel: [    3.722738] ata_piix 0000:00:1f.2: MAP [ P0 P2 -- -- ]
Mar  5 11:58:31 vendetta-laptop kernel: [    3.876199] scsi2 : ata_piix
Mar  5 11:58:31 vendetta-laptop kernel: [    3.876610] scsi3 : ata_piix
Mar  5 11:58:31 vendetta-laptop kernel: [    3.877873] ata3: SATA max UDMA/133 cmd 0x18d0 ctl 0x18c4 bmdma 0x18b0 irq 19
Mar  5 11:58:31 vendetta-laptop kernel: [    3.877877] ata4: SATA max UDMA/133 cmd 0x18c8 ctl 0x18c0 bmdma 0x18b8 irq 19
Mar  5 11:58:31 vendetta-laptop kernel: [    4.028054] usb 5-6: new high speed USB device using ehci_hcd and address 2
Mar  5 11:58:31 vendetta-laptop kernel: [    4.040631] ata3.00: ATA-7: FUJITSU MHV2160BT PL, 0000004F, max UDMA/100
Mar  5 11:58:31 vendetta-laptop kernel: [    4.040635] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar  5 11:58:31 vendetta-laptop kernel: [    4.056669] ata3.00: configured for UDMA/100
Mar  5 11:58:31 vendetta-laptop kernel: [    4.223322] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHV2160B 0000 PQ: 0 ANSI: 5
Mar  5 11:58:31 vendetta-laptop kernel: [    4.223429] e100 0000:0a:08.0: enabling device (0000 -> 0003)
Mar  5 11:58:31 vendetta-laptop kernel: [    4.223441] e100 0000:0a:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar  5 11:58:31 vendetta-laptop kernel: [    4.250464] e100 0000:0a:08.0: PME# disabled
Mar  5 11:58:31 vendetta-laptop kernel: [    4.250595] usb 5-6: configuration #1 chosen from 1 choice
Mar  5 11:58:31 vendetta-laptop kernel: [    4.252813] e100: eth0: e100_probe: addr 0xd0005000, irq 20, MAC addr 00:13:a9:84:ca:c3
Mar  5 11:58:31 vendetta-laptop kernel: [    4.252852] ohci1394 0000:0a:03.1: enabling device (0000 -> 0002)
Mar  5 11:58:31 vendetta-laptop kernel: [    4.252861] ohci1394 0000:0a:03.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 11:58:31 vendetta-laptop kernel: [    4.302613] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d0006000-d00067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Mar  5 11:58:31 vendetta-laptop kernel: [    4.321139] scsi 0:0:0:0: Attached scsi generic sg0 type 5
Mar  5 11:58:31 vendetta-laptop kernel: [    4.321199] scsi 2:0:0:0: Attached scsi generic sg1 type 0
Mar  5 11:58:31 vendetta-laptop kernel: [    4.342572] Driver 'sr' needs updating - please use bus_type methods
Mar  5 11:58:31 vendetta-laptop kernel: [    4.347027] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Mar  5 11:58:31 vendetta-laptop kernel: [    4.347032] Uniform CD-ROM driver Revision: 3.20
Mar  5 11:58:31 vendetta-laptop kernel: [    4.348215] Driver 'sd' needs updating - please use bus_type methods
Mar  5 11:58:31 vendetta-laptop kernel: [    4.349686] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Mar  5 11:58:31 vendetta-laptop kernel: [    4.349706] sd 2:0:0:0: [sda] Write Protect is off
Mar  5 11:58:31 vendetta-laptop kernel: [    4.349739] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  5 11:58:31 vendetta-laptop kernel: [    4.349820] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Mar  5 11:58:31 vendetta-laptop kernel: [    4.349837] sd 2:0:0:0: [sda] Write Protect is off
Mar  5 11:58:31 vendetta-laptop kernel: [    4.349870] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  5 11:58:31 vendetta-laptop kernel: [    4.349874]  sda: sda1 sda2 sda3 sda4
Mar  5 11:58:31 vendetta-laptop kernel: [    4.364039] usb 5-8: new high speed USB device using ehci_hcd and address 3
Mar  5 11:58:31 vendetta-laptop kernel: [    4.423949] sd 2:0:0:0: [sda] Attached SCSI disk
Mar  5 11:58:31 vendetta-laptop kernel: [    4.495762] usb 5-8: configuration #1 chosen from 1 choice
Mar  5 11:58:31 vendetta-laptop kernel: [    4.496228] usbcore: registered new interface driver libusual
Mar  5 11:58:31 vendetta-laptop kernel: [    4.513031] Initializing USB Mass Storage driver...
Mar  5 11:58:31 vendetta-laptop kernel: [    4.513345] scsi4 : SCSI emulation for USB Mass Storage devices
Mar  5 11:58:31 vendetta-laptop kernel: [    4.513828] usbcore: registered new interface driver usb-storage
Mar  5 11:58:31 vendetta-laptop kernel: [    4.513832] USB Mass Storage support registered.
Mar  5 11:58:31 vendetta-laptop kernel: [    4.740602] PM: Starting manual resume from disk
Mar  5 11:58:31 vendetta-laptop kernel: [    4.764356] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar  5 11:58:31 vendetta-laptop kernel: [    4.764360] EXT3-fs: write access will be enabled during recovery.
Mar  5 11:58:31 vendetta-laptop kernel: [    9.521996] scsi 4:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.52 PQ: 0 ANSI: 0
Mar  5 11:58:31 vendetta-laptop kernel: [    9.572385] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Mar  5 11:58:31 vendetta-laptop kernel: [    9.572562] sd 4:0:0:0: Attached scsi generic sg2 type 0
Mar  5 11:58:31 vendetta-laptop kernel: [   11.676492] kjournald starting.  Commit interval 5 seconds
Mar  5 11:58:31 vendetta-laptop kernel: [   11.676516] EXT3-fs: sda3: orphan cleanup on readonly fs
Mar  5 11:58:31 vendetta-laptop kernel: [   11.676594] EXT3-fs: sda3: 1 orphan inode deleted
Mar  5 11:58:31 vendetta-laptop kernel: [   11.676598] EXT3-fs: recovery complete.
Mar  5 11:58:31 vendetta-laptop kernel: [   11.694901] EXT3-fs: mounted filesystem with ordered data mode.
Mar  5 11:58:31 vendetta-laptop kernel: [   21.510596] udevd version 124 started
Mar  5 11:58:31 vendetta-laptop kernel: [   22.152497] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  5 11:58:31 vendetta-laptop kernel: [   22.200548] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar  5 11:58:31 vendetta-laptop kernel: [   22.280418] iTCO_vendor_support: vendor-support=0
Mar  5 11:58:31 vendetta-laptop kernel: [   22.581129] Linux agpgart interface v0.103
Mar  5 11:58:31 vendetta-laptop kernel: [   22.640468] input: PC Speaker as /devices/platform/pcspkr/input/input2
Mar  5 11:58:31 vendetta-laptop kernel: [   22.690665] ACPI: AC Adapter [ADP1] (on-line)
Mar  5 11:58:31 vendetta-laptop kernel: [   22.838454] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
Mar  5 11:58:31 vendetta-laptop kernel: [   22.852857] ACPI: Lid Switch [LID0]
Mar  5 11:58:31 vendetta-laptop kernel: [   22.852948] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Mar  5 11:58:31 vendetta-laptop kernel: [   22.873042] ACPI: Power Button (CM) [PWRB]
Mar  5 11:58:31 vendetta-laptop kernel: [   22.873252] sony-laptop: Sony Notebook Control Driver v0.6.
Mar  5 11:58:31 vendetta-laptop kernel: [   22.874018] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2b/SNY5001:00/input/input5
Mar  5 11:58:31 vendetta-laptop kernel: [   22.896002] Yenta: CardBus bridge found at 0000:0a:03.0 [104d:81ef]
Mar  5 11:58:31 vendetta-laptop kernel: [   22.896028] Yenta: Enabling burst memory read transactions
Mar  5 11:58:31 vendetta-laptop kernel: [   22.896035] Yenta: Using CSCINT to route CSC interrupts to PCI
Mar  5 11:58:31 vendetta-laptop kernel: [   22.896037] Yenta: Routing CardBus interrupts to PCI
Mar  5 11:58:31 vendetta-laptop kernel: [   22.896044] Yenta TI: socket 0000:0a:03.0, mfunc 0x01131b22, devctl 0x64
Mar  5 11:58:31 vendetta-laptop kernel: [   22.901092] input: Sony Vaio Jogdial as /devices/virtual/input/input6
Mar  5 11:58:31 vendetta-laptop kernel: [   22.934097] sony-laptop: detected Sony Vaio FE Series
Mar  5 11:58:31 vendetta-laptop kernel: [   22.949913] ACPI: Battery Slot [BAT0] (battery present)
Mar  5 11:58:31 vendetta-laptop kernel: [   22.964895] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
Mar  5 11:58:31 vendetta-laptop kernel: [   22.965482] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Mar  5 11:58:31 vendetta-laptop kernel: [   22.983849] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
Mar  5 11:58:31 vendetta-laptop kernel: [   23.003295] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Mar  5 11:58:31 vendetta-laptop kernel: [   23.004653] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Mar  5 11:58:31 vendetta-laptop kernel: [   23.004801] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Mar  5 11:58:31 vendetta-laptop kernel: [   23.125844] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
Mar  5 11:58:31 vendetta-laptop kernel: [   23.125850] Socket status: 30000006
Mar  5 11:58:31 vendetta-laptop kernel: [   23.125854] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
Mar  5 11:58:31 vendetta-laptop kernel: [   23.125862] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x6fff
Mar  5 11:58:31 vendetta-laptop kernel: [   23.125865] cs: IO port probe 0x6000-0x6fff: clean.
Mar  5 11:58:31 vendetta-laptop kernel: [   23.126174] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
Mar  5 11:58:31 vendetta-laptop kernel: [   23.126177] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
Mar  5 11:58:31 vendetta-laptop kernel: [   23.150673] tifm_7xx1 0000:0a:03.2: enabling device (0000 -> 0002)
Mar  5 11:58:31 vendetta-laptop kernel: [   23.150683] tifm_7xx1 0000:0a:03.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar  5 11:58:31 vendetta-laptop kernel: [   23.201243] acpi device:07: registered as cooling_device2
Mar  5 11:58:31 vendetta-laptop kernel: [   23.201486] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/input/input7
Mar  5 11:58:31 vendetta-laptop kernel: [   23.221032] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Mar  5 11:58:31 vendetta-laptop kernel: [   23.269139] intel_rng: FWH not detected
Mar  5 11:58:31 vendetta-laptop kernel: [   23.355347] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
Mar  5 11:58:31 vendetta-laptop kernel: [   23.445945] Linux video capture interface: v2.00
Mar  5 11:58:31 vendetta-laptop kernel: [   23.568094] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
Mar  5 11:58:31 vendetta-laptop kernel: [   24.128246] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1836)
Mar  5 11:58:31 vendetta-laptop kernel: [   24.129081] usbcore: registered new interface driver uvcvideo
Mar  5 11:58:31 vendetta-laptop kernel: [   24.129102] USB Video Class driver (v0.1.0)
Mar  5 11:58:31 vendetta-laptop kernel: [   24.170661] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Mar  5 11:58:31 vendetta-laptop kernel: [   24.170665] iwl3945: Copyright(c) 2003-2008 Intel Corporation
Mar  5 11:58:31 vendetta-laptop kernel: [   24.170740] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar  5 11:58:31 vendetta-laptop kernel: [   24.170777] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Mar  5 11:58:31 vendetta-laptop kernel: [   24.271850] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Mar  5 11:58:31 vendetta-laptop kernel: [   24.488906] iwl3945 0000:06:00.0: PCI INT A disabled
Mar  5 11:58:31 vendetta-laptop kernel: [   24.562233] cs: IO port probe 0x100-0x3af: clean.
Mar  5 11:58:31 vendetta-laptop kernel: [   24.564307] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Mar  5 11:58:31 vendetta-laptop kernel: [   24.565185] cs: IO port probe 0x820-0x8ff: clean.
Mar  5 11:58:31 vendetta-laptop kernel: [   24.565897] cs: IO port probe 0xc00-0xcf7: clean.
Mar  5 11:58:31 vendetta-laptop kernel: [   24.566807] cs: IO port probe 0xa00-0xaff: clean.
Mar  5 11:58:31 vendetta-laptop kernel: [   24.646948] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar  5 11:58:31 vendetta-laptop kernel: [   25.533733] lp: driver loaded but no devices found
Mar  5 11:58:31 vendetta-laptop kernel: [   25.725533] Adding 2939884k swap on /dev/sda4.  Priority:-1 extents:1 across:2939884k
Mar  5 11:58:31 vendetta-laptop kernel: [   26.275494] EXT3 FS on sda3, internal journal
Mar  5 11:58:31 vendetta-laptop kernel: [   27.960236] type=1505 audit(1236272309.609:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4310
Mar  5 11:58:31 vendetta-laptop kernel: [   28.027561] type=1505 audit(1236272309.674:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4315
Mar  5 11:58:31 vendetta-laptop kernel: [   28.220436] type=1505 audit(1236272309.866:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4319
Mar  5 11:58:31 vendetta-laptop kernel: [   28.220657] type=1505 audit(1236272309.866:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4319
Mar  5 11:58:31 vendetta-laptop kernel: [   28.386026] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar  5 11:58:31 vendetta-laptop kernel: [   29.116578] ACPI: WMI: Mapper loaded
Mar  5 11:58:31 vendetta-laptop kernel: [   30.207584] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar  5 11:58:31 vendetta-laptop kernel: [   30.280044] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Mar  5 11:58:31 vendetta-laptop kernel: [   30.280051] apm: disabled - APM is not SMP safe.
Mar  5 11:58:33 vendetta-laptop kernel: [   31.425718] ppdev: user-space parallel port driver
Mar  5 11:58:34 vendetta-laptop kernel: [   32.761484] sonypi: Sony Programmable I/O Controller Driver v1.26.
Mar  5 11:58:34 vendetta-laptop kernel: [   32.762663] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
Mar  5 11:58:34 vendetta-laptop kernel: [   32.765353] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
Mar  5 11:58:34 vendetta-laptop kernel: [   32.765361] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
Mar  5 11:58:34 vendetta-laptop kernel: [   32.765364] sonypi: device allocated minor is 60
Mar  5 11:58:34 vendetta-laptop kernel: [   32.766020] input: Sony Vaio Jogdial as /devices/platform/sonypi/input/input10
Mar  5 11:58:34 vendetta-laptop kernel: [   32.797440] input: Sony Vaio Keys as /devices/platform/sonypi/input/input11
Mar  5 11:58:34 vendetta-laptop kernel: [   32.895370] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
Mar  5 11:58:34 vendetta-laptop kernel: [   32.935647] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 664)
Mar  5 11:58:34 vendetta-laptop kernel: [   32.975851] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 666)
Mar  5 11:58:34 vendetta-laptop kernel: [   33.016098] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
Mar  5 11:58:36 vendetta-laptop kernel: [   34.912956] NET: Registered protocol family 10
Mar  5 11:58:36 vendetta-laptop kernel: [   34.917567] lo: Disabled Privacy Extensions
Mar  5 11:58:38 vendetta-laptop kernel: [   36.400744] Bluetooth: Core ver 2.13
Mar  5 11:58:38 vendetta-laptop kernel: [   36.401587] NET: Registered protocol family 31
Mar  5 11:58:38 vendetta-laptop kernel: [   36.401594] Bluetooth: HCI device and connection manager initialized
Mar  5 11:58:38 vendetta-laptop kernel: [   36.401600] Bluetooth: HCI socket layer initialized
Mar  5 11:58:38 vendetta-laptop kernel: [   36.438532] Bluetooth: L2CAP ver 2.11
Mar  5 11:58:38 vendetta-laptop kernel: [   36.438543] Bluetooth: L2CAP socket layer initialized
Mar  5 11:58:38 vendetta-laptop kernel: [   36.469888] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar  5 11:58:38 vendetta-laptop kernel: [   36.469900] Bluetooth: BNEP filters: protocol multicast
Mar  5 11:58:38 vendetta-laptop kernel: [   36.520692] Bridge firewalling registered
Mar  5 11:58:38 vendetta-laptop kernel: [   36.533293] Bluetooth: RFCOMM socket layer initialized
Mar  5 11:58:38 vendetta-laptop kernel: [   36.534214] Bluetooth: RFCOMM TTY layer initialized
Mar  5 11:58:38 vendetta-laptop kernel: [   36.534223] Bluetooth: RFCOMM ver 1.10
Mar  5 11:58:38 vendetta-laptop kernel: [   36.572296] Bluetooth: SCO (Voice Link) ver 0.6
Mar  5 11:58:38 vendetta-laptop kernel: [   36.572306] Bluetooth: SCO socket layer initialized
Mar  5 11:58:41 vendetta-laptop kernel: [   40.255083] [drm] Initialized drm 1.1.0 20060810
Mar  5 11:58:41 vendetta-laptop kernel: [   40.261587] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 11:58:41 vendetta-laptop kernel: [   40.263298] [drm] Initialized i915 1.6.0 20060119 on minor 0
Mar  5 11:58:42 vendetta-laptop kernel: [   40.689991] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar  5 11:58:42 vendetta-laptop kernel: [   40.691118] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar  5 11:58:42 vendetta-laptop kernel: [   40.691546] firmware: requesting iwlwifi-3945-1.ucode
Mar  5 11:58:42 vendetta-laptop kernel: [   40.844852] Registered led device: iwl-phy0:radio
Mar  5 11:58:42 vendetta-laptop kernel: [   40.844894] Registered led device: iwl-phy0:assoc
Mar  5 11:58:42 vendetta-laptop kernel: [   40.844933] Registered led device: iwl-phy0:RX
Mar  5 11:58:42 vendetta-laptop kernel: [   40.844966] Registered led device: iwl-phy0:TX
Mar  5 11:58:42 vendetta-laptop kernel: [   40.873720] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  5 11:58:42 vendetta-laptop kernel: [   40.960201] NET: Registered protocol family 17
Mar  5 11:58:56 vendetta-laptop pulseaudio[5907]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar  5 11:58:56 vendetta-laptop pulseaudio[5909]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar  5 11:58:56 vendetta-laptop pulseaudio[5909]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar  5 11:59:29 vendetta-laptop kernel: [   88.200290] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar  5 12:00:42 vendetta-laptop syslogd 1.5.0#2ubuntu6: restart.
Mar  5 12:00:43 vendetta-laptop kernel: Inspecting /boot/System.map-2.6.27-11-generic
Mar  5 12:00:43 vendetta-laptop kernel: Cannot find map file.
Mar  5 12:00:43 vendetta-laptop kernel: Loaded 52907 symbols from 102 modules.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f690000 (usable)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 000000007f690000 - 000000007f69a000 (ACPI data)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 000000007f69a000 - 000000007f700000 (ACPI NVS)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] DMI present.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] last_pfn = 0x7f690 max_arch_pfn = 0x100000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] RAMDISK: 37820000 - 37fef2e0
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: RSDP 000F7250, 0014 (r0 PTLTD )
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: RSDT 7F6922F8, 0054 (r1   Sony     VAIO 20070205 PTL         0)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: FACP 7F699C9A, 0084 (r2   Sony     VAIO 20070205 PTL        5A)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: DSDT 7F69416D, 5B2D (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: FACS 7F69AFC0, 0040
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: APIC 7F699D1E, 0068 (r1   Sony     VAIO 20070205 PTL        5A)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: HPET 7F699D86, 0038 (r1   Sony     VAIO 20070205 PTL        5A)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: MCFG 7F699DBE, 003C (r1   Sony     VAIO 20070205 PTL        5A)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: SLIC 7F699DFA, 0176 (r1   Sony     VAIO 20070205 PTL   1000000)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: APIC 7F699F70, 0068 (r1   Sony     VAIO 20070205 PTL         0)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: BOOT 7F699FD8, 0028 (r1   Sony     VAIO 20070205 PTL         1)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: SSDT 7F6939E1, 078C (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: SSDT 7F693345, 069C (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: SSDT 7F6928E2, 025F (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: SSDT 7F69283C, 00A6 (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: SSDT 7F69234C, 04F0 (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: DMI detected: Sony
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] 1142MB HIGHMEM available.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] 896MB LOWMEM available.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   mapped low ram: 0 - 38000000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   low ram: 00000000 - 38000000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   bootmap 00011000 - 00018000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   #4 [0037820000 - 0037fef2e0]          RAMDISK ==> [0037820000 - 0037fef2e0]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   #6 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] found SMP MP-table at [c00f7320] 000f7320
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Zone PFN ranges:
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]   HighMem  0x00038000 -> 0x0007f690
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Movable zone start PFN for each node
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0007f690
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517172
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Kernel command line: root=UUID=22a9f34b-1f50-470f-bf8c-fa688d2ab18c ro quiet splash 
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Initializing CPU#0
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] TSC: using PIT calibration value
Mar  5 12:00:43 vendetta-laptop kernel: [    0.000000] Detected 1662.469 MHz processor.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Console: colour VGA+ 80x25
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] console [tty0] enabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Memory: 2054068k/2087488k available (2576k kernel code, 32188k reserved, 1165k data, 424k init, 1169984k highmem)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] virtual kernel memory layout:
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.93 BogoMIPS (lpj=6649876)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Security Framework initialized
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] SELinux:  Disabled at boot.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] AppArmor: AppArmor initialized
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Mount-cache hash table entries: 512
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Initializing cgroup subsys ns
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Initializing cgroup subsys memory
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] CPU: Processor Core ID: 0
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] using mwait in idle threads.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.018224] ACPI: Core revision 20080609
Mar  5 12:00:43 vendetta-laptop kernel: [    0.020804] ACPI: Checking initramfs for custom DSDT
Mar  5 12:00:43 vendetta-laptop kernel: [    0.428285] ENABLING IO-APIC IRQs
Mar  5 12:00:43 vendetta-laptop kernel: [    0.428480] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar  5 12:00:43 vendetta-laptop kernel: [    0.470972] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Mar  5 12:00:43 vendetta-laptop kernel: [    0.472029] Booting processor 1/1 ip 6000
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Initializing CPU#1
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3325.03 BogoMIPS (lpj=6650070)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar  5 12:00:43 vendetta-laptop kernel: [    0.004000] CPU: Processor Core ID: 1
Mar  5 12:00:43 vendetta-laptop kernel: [    0.556535] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Mar  5 12:00:43 vendetta-laptop kernel: [    0.556555] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560054] Brought up 2 CPUs
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560057] Total of 2 processors activated (6649.97 BogoMIPS).
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560222] net_namespace: 840 bytes
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560222] Booting paravirtualized kernel on bare hardware
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560347] Time: 12:00:21  Date: 03/05/09
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560377] NET: Registered protocol family 16
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560401] EISA bus registered
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560401] ACPI: bus type pci registered
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560401] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560401] PCI: MCFG area at e0000000 reserved in E820
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560401] PCI: Using MMCONFIG for extended config space
Mar  5 12:00:43 vendetta-laptop kernel: [    0.560401] PCI: Using configuration type 1 for base access
Mar  5 12:00:43 vendetta-laptop kernel: [    0.576719] ACPI: Interpreter enabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.576726] ACPI: (supports S0 S3 S4 S5)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.576745] ACPI: Using IOAPIC for interrupt routing
Mar  5 12:00:43 vendetta-laptop kernel: [    0.576813] ACPI: EC: non-query interrupt received, switching to interrupt mode
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608473] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608473] ACPI: EC: driver started in interrupt mode
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608473] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608473] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608473] pci 0000:00:1b.0: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608473] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608473] pci 0000:00:1c.0: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608518] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608525] pci 0000:00:1c.1: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608601] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608607] pci 0000:00:1c.2: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608682] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Mar  5 12:00:43 vendetta-laptop kernel: [    0.608688] pci 0000:00:1c.3: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.609077] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Mar  5 12:00:43 vendetta-laptop kernel: [    0.609083] pci 0000:00:1d.7: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.609251] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Mar  5 12:00:43 vendetta-laptop kernel: [    0.609256] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Mar  5 12:00:43 vendetta-laptop kernel: [    0.609452] pci 0000:00:1f.2: PME# supported from D3hot
Mar  5 12:00:43 vendetta-laptop kernel: [    0.609458] pci 0000:00:1f.2: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.610070] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
Mar  5 12:00:43 vendetta-laptop kernel: [    0.610084] pci 0000:06:00.0: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.610326] pci 0000:0a:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 12:00:43 vendetta-laptop kernel: [    0.610332] pci 0000:0a:03.0: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.610453] pci 0000:0a:03.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 12:00:43 vendetta-laptop kernel: [    0.610459] pci 0000:0a:03.1: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.610573] pci 0000:0a:03.2: PME# supported from D0 D1 D2 D3hot
Mar  5 12:00:43 vendetta-laptop kernel: [    0.610579] pci 0000:0a:03.2: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.612047] pci 0000:0a:08.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 12:00:43 vendetta-laptop kernel: [    0.612053] pci 0000:0a:08.0: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.612099] pci 0000:00:1e.0: transparent bridge
Mar  5 12:00:43 vendetta-laptop kernel: [    0.624167] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.624318] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.624465] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Mar  5 12:00:43 vendetta-laptop kernel: [    0.624612] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Mar  5 12:00:43 vendetta-laptop kernel: [    0.624759] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Mar  5 12:00:43 vendetta-laptop kernel: [    0.624905] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *7 11 12 14 15)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.625052] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 *4 5 6 7 10 12 14 15)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.625197] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 11 12 14 15)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.625288] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar  5 12:00:43 vendetta-laptop kernel: [    0.625288] pnp: PnP ACPI init
Mar  5 12:00:43 vendetta-laptop kernel: [    0.625288] ACPI: bus type pnp registered
Mar  5 12:00:43 vendetta-laptop kernel: [    0.636506] pnp: PnP ACPI: found 10 devices
Mar  5 12:00:43 vendetta-laptop kernel: [    0.636506] ACPI: ACPI bus type pnp unregistered
Mar  5 12:00:43 vendetta-laptop kernel: [    0.636506] PnPBIOS: Disabled by ACPI PNP
Mar  5 12:00:43 vendetta-laptop kernel: [    0.636506] PCI: Using ACPI for IRQ routing
Mar  5 12:00:43 vendetta-laptop kernel: [    0.644042] NET: Registered protocol family 8
Mar  5 12:00:43 vendetta-laptop kernel: [    0.644045] NET: Registered protocol family 20
Mar  5 12:00:43 vendetta-laptop kernel: [    0.644066] NetLabel: Initializing
Mar  5 12:00:43 vendetta-laptop kernel: [    0.644066] NetLabel:  domain hash size = 128
Mar  5 12:00:43 vendetta-laptop kernel: [    0.644066] NetLabel:  protocols = UNLABELED CIPSOv4
Mar  5 12:00:43 vendetta-laptop kernel: [    0.644076] NetLabel:  unlabeled traffic allowed by default
Mar  5 12:00:43 vendetta-laptop kernel: [    0.644085] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Mar  5 12:00:43 vendetta-laptop kernel: [    0.644091] hpet0: 3 64-bit timers, 14318180 Hz
Mar  5 12:00:43 vendetta-laptop kernel: [    0.645658] tracer: 772 pages allocated for 65536 entries of 48 bytes
Mar  5 12:00:43 vendetta-laptop kernel: [    0.645661]    actual entries 65620
Mar  5 12:00:43 vendetta-laptop kernel: [    0.645759] AppArmor: AppArmor Filesystem Enabled
Mar  5 12:00:43 vendetta-laptop kernel: [    0.645788] ACPI: RTC can wake from S4
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652027] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652031] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652035] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652039] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652042] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652046] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652050] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652061] system 00:06: ioport range 0x680-0x6ff has been reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652065] system 00:06: ioport range 0x800-0x80f has been reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652069] system 00:06: ioport range 0x1000-0x107f has been reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652072] system 00:06: ioport range 0x1180-0x11bf has been reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652075] system 00:06: ioport range 0x1640-0x164f has been reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652079] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.652083] system 00:06: ioport range 0xfe80-0xfeff has been reserved
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687387] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687392] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687400] pci 0000:00:1c.0:   MEM window: 0xc8000000-0xc9ffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687406] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0000000-0x000000c1ffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687415] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687420] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687427] pci 0000:00:1c.1:   MEM window: 0xca000000-0xcbffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687433] pci 0000:00:1c.1:   PREFETCH window: 0x000000c2000000-0x000000c3ffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687442] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687446] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687454] pci 0000:00:1c.2:   MEM window: 0xcc000000-0xcdffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687459] pci 0000:00:1c.2:   PREFETCH window: 0x000000c4000000-0x000000c5ffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687468] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:08
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687472] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687480] pci 0000:00:1c.3:   MEM window: 0xce000000-0xcfffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687485] pci 0000:00:1c.3:   PREFETCH window: 0x000000c6000000-0x000000c7ffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687501] pci 0000:0a:03.0: CardBus bridge, secondary bus 0000:0b
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687504] pci 0000:0a:03.0:   IO window: 0x006400-0x0064ff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687510] pci 0000:0a:03.0:   IO window: 0x006800-0x0068ff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687517] pci 0000:0a:03.0:   PREFETCH window: 0x88000000-0x8bffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687523] pci 0000:0a:03.0:   MEM window: 0x90000000-0x93ffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687530] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687534] pci 0000:00:1e.0:   IO window: 0x6000-0x6fff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687541] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd00fffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687547] pci 0000:00:1e.0:   PREFETCH window: 0x00000088000000-0x0000008bffffff
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687567] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687585] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687602] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687618] pci 0000:00:1c.3: PCI INT D -> GSI 21 (level, low) -> IRQ 21
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687631] pci 0000:00:1e.0: enabling device (0004 -> 0007)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687649] pci 0000:0a:03.0: enabling device (0000 -> 0003)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687655] pci 0000:0a:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687664] bus: 00 index 0 io port: [0, ffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687667] bus: 00 index 1 mmio: [0, ffffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687669] bus: 02 index 0 io port: [2000, 2fff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687672] bus: 02 index 1 mmio: [c8000000, c9ffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687675] bus: 02 index 2 mmio: [c0000000, c1ffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687677] bus: 02 index 3 mmio: [0, 0]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687680] bus: 04 index 0 io port: [3000, 3fff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687682] bus: 04 index 1 mmio: [ca000000, cbffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687685] bus: 04 index 2 mmio: [c2000000, c3ffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687687] bus: 04 index 3 mmio: [0, 0]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687690] bus: 06 index 0 io port: [4000, 4fff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687692] bus: 06 index 1 mmio: [cc000000, cdffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687695] bus: 06 index 2 mmio: [c4000000, c5ffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687697] bus: 06 index 3 mmio: [0, 0]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687700] bus: 08 index 0 io port: [5000, 5fff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687702] bus: 08 index 1 mmio: [ce000000, cfffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687705] bus: 08 index 2 mmio: [c6000000, c7ffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687707] bus: 08 index 3 mmio: [0, 0]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687710] bus: 0a index 0 io port: [6000, 6fff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687712] bus: 0a index 1 mmio: [d0000000, d00fffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687715] bus: 0a index 2 mmio: [88000000, 8bffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687718] bus: 0a index 3 io port: [0, ffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687720] bus: 0a index 4 mmio: [0, ffffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687722] bus: 0b index 0 io port: [6400, 64ff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687725] bus: 0b index 1 io port: [6800, 68ff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687727] bus: 0b index 2 mmio: [88000000, 8bffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687730] bus: 0b index 3 mmio: [90000000, 93ffffff]
Mar  5 12:00:43 vendetta-laptop kernel: [    0.687739] NET: Registered protocol family 2
Mar  5 12:00:43 vendetta-laptop kernel: [    0.700061] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.700327] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.700739] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.700967] TCP: Hash tables configured (established 131072 bind 65536)
Mar  5 12:00:43 vendetta-laptop kernel: [    0.700971] TCP reno registered
Mar  5 12:00:43 vendetta-laptop kernel: [    0.704083] NET: Registered protocol family 1
Mar  5 12:00:43 vendetta-laptop kernel: [    0.704223] checking if image is initramfs... it is
Mar  5 12:00:43 vendetta-laptop kernel: [    1.524679] Freeing initrd memory: 7996k freed
Mar  5 12:00:43 vendetta-laptop kernel: [    1.524877] Simple Boot Flag at 0x36 set to 0x1
Mar  5 12:00:43 vendetta-laptop kernel: [    1.526018] audit: initializing netlink socket (disabled)
Mar  5 12:00:43 vendetta-laptop kernel: [    1.526045] type=2000 audit(1236254421.525:1): initialized
Mar  5 12:00:43 vendetta-laptop kernel: [    1.533164] highmem bounce pool size: 64 pages
Mar  5 12:00:43 vendetta-laptop kernel: [    1.533172] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar  5 12:00:43 vendetta-laptop kernel: [    1.536122] VFS: Disk quotas dquot_6.5.1
Mar  5 12:00:43 vendetta-laptop kernel: [    1.536228] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar  5 12:00:43 vendetta-laptop kernel: [    1.536354] msgmni has been set to 1743
Mar  5 12:00:43 vendetta-laptop kernel: [    1.536498] io scheduler noop registered
Mar  5 12:00:43 vendetta-laptop kernel: [    1.536502] io scheduler anticipatory registered
Mar  5 12:00:43 vendetta-laptop kernel: [    1.536505] io scheduler deadline registered
Mar  5 12:00:43 vendetta-laptop kernel: [    1.536519] io scheduler cfq registered (default)
Mar  5 12:00:43 vendetta-laptop kernel: [    1.536849] pcieport-driver 0000:00:1c.0: found MSI capability
Mar  5 12:00:43 vendetta-laptop kernel: [    1.537201] pcieport-driver 0000:00:1c.1: found MSI capability
Mar  5 12:00:43 vendetta-laptop kernel: [    1.537535] pcieport-driver 0000:00:1c.2: found MSI capability
Mar  5 12:00:43 vendetta-laptop kernel: [    1.537871] pcieport-driver 0000:00:1c.3: found MSI capability
Mar  5 12:00:43 vendetta-laptop kernel: [    1.538456] isapnp: Scanning for PnP cards...
Mar  5 12:00:43 vendetta-laptop kernel: [    1.892348] isapnp: No Plug & Play device found
Mar  5 12:00:43 vendetta-laptop kernel: [    1.932677] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Mar  5 12:00:43 vendetta-laptop kernel: [    1.935454] brd: module loaded
Mar  5 12:00:43 vendetta-laptop kernel: [    1.935540] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Mar  5 12:00:43 vendetta-laptop kernel: [    1.935689] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar  5 12:00:43 vendetta-laptop kernel: [    1.940844] i8042.c: Detected active multiplexing controller, rev 1.1.
Mar  5 12:00:43 vendetta-laptop kernel: [    1.945011] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar  5 12:00:43 vendetta-laptop kernel: [    1.945018] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Mar  5 12:00:43 vendetta-laptop kernel: [    1.945021] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Mar  5 12:00:43 vendetta-laptop kernel: [    1.945025] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Mar  5 12:00:43 vendetta-laptop kernel: [    1.945028] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948137] mice: PS/2 mouse device common for all mice
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948299] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948331] rtc0: alarms up to one month, y3k, hpet irqs
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948484] EISA: Probing bus 0 at eisa.0
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948491] Cannot allocate resource for EISA slot 1
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948495] Cannot allocate resource for EISA slot 2
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948498] Cannot allocate resource for EISA slot 3
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948501] Cannot allocate resource for EISA slot 4
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948504] Cannot allocate resource for EISA slot 5
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948507] Cannot allocate resource for EISA slot 6
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948519] EISA: Detected 0 cards.
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948522] cpuidle: using governor ladder
Mar  5 12:00:43 vendetta-laptop kernel: [    1.948526] cpuidle: using governor menu
Mar  5 12:00:43 vendetta-laptop kernel: [    1.949127] TCP cubic registered
Mar  5 12:00:43 vendetta-laptop kernel: [    1.949159] Using IPI No-Shortcut mode
Mar  5 12:00:43 vendetta-laptop kernel: [    1.949371] registered taskstats version 1
Mar  5 12:00:43 vendetta-laptop kernel: [    1.949516]   Magic number: 1:588:25
Mar  5 12:00:43 vendetta-laptop kernel: [    1.949631] rtc_cmos 00:07: setting system clock to 2009-03-05 12:00:22 UTC (1236254422)
Mar  5 12:00:43 vendetta-laptop kernel: [    1.949635] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar  5 12:00:43 vendetta-laptop kernel: [    1.949638] EDD information not available.
Mar  5 12:00:43 vendetta-laptop kernel: [    1.949898] Freeing unused kernel memory: 424k freed
Mar  5 12:00:43 vendetta-laptop kernel: [    1.949943] Write protecting the kernel text: 2580k
Mar  5 12:00:43 vendetta-laptop kernel: [    1.949973] Write protecting the kernel read-only data: 940k
Mar  5 12:00:43 vendetta-laptop kernel: [    2.141047] fuse init (API version 7.9)
Mar  5 12:00:43 vendetta-laptop kernel: [    2.169016] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Mar  5 12:00:43 vendetta-laptop kernel: [    2.209548] ACPI: SSDT 7F693082, 01FB (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:00:43 vendetta-laptop kernel: [    2.210274] ACPI: SSDT 7F692B41, 04BC (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:00:43 vendetta-laptop kernel: [    2.213136] ACPI: CPU0 (power states: C1[C1] C2[C2])
Mar  5 12:00:43 vendetta-laptop kernel: [    2.213213] processor ACPI0007:00: registered as cooling_device0
Mar  5 12:00:43 vendetta-laptop kernel: [    2.213218] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar  5 12:00:43 vendetta-laptop kernel: [    2.213632] ACPI: SSDT 7F69327D, 00C8 (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:00:43 vendetta-laptop kernel: [    2.214061] ACPI: SSDT 7F692FFD, 0085 (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:00:43 vendetta-laptop kernel: [    2.215016] Marking TSC unstable due to TSC halts in idle
Mar  5 12:00:43 vendetta-laptop kernel: [    2.215190] ACPI: CPU1 (power states: C1[C1] C2[C2])
Mar  5 12:00:43 vendetta-laptop kernel: [    2.215252] processor ACPI0007:01: registered as cooling_device1
Mar  5 12:00:43 vendetta-laptop kernel: [    2.215257] ACPI: Processor [CPU1] (supports 8 throttling states)
Mar  5 12:00:43 vendetta-laptop kernel: [    2.220167] thermal LNXTHERM:01: registered as thermal_zone0
Mar  5 12:00:43 vendetta-laptop kernel: [    2.224521] ACPI: Thermal Zone [TZ00] (56 C)
Mar  5 12:00:43 vendetta-laptop kernel: [    2.226527] thermal LNXTHERM:02: registered as thermal_zone1
Mar  5 12:00:43 vendetta-laptop kernel: [    2.229375] ACPI: Thermal Zone [TZ01] (56 C)
Mar  5 12:00:43 vendetta-laptop kernel: [    2.594880] usbcore: registered new interface driver usbfs
Mar  5 12:00:43 vendetta-laptop kernel: [    2.594907] usbcore: registered new interface driver hub
Mar  5 12:00:43 vendetta-laptop kernel: [    2.594955] usbcore: registered new device driver usb
Mar  5 12:00:43 vendetta-laptop kernel: [    2.598353] USB Universal Host Controller Interface driver v3.0
Mar  5 12:00:43 vendetta-laptop kernel: [    2.598410] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar  5 12:00:43 vendetta-laptop kernel: [    2.598426] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar  5 12:00:43 vendetta-laptop kernel: [    2.598471] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Mar  5 12:00:43 vendetta-laptop kernel: [    2.598511] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
Mar  5 12:00:43 vendetta-laptop kernel: [    2.598676] usb usb1: configuration #1 chosen from 1 choice
Mar  5 12:00:43 vendetta-laptop kernel: [    2.598708] hub 1-0:1.0: USB hub found
Mar  5 12:00:43 vendetta-laptop kernel: [    2.598716] hub 1-0:1.0: 2 ports detected
Mar  5 12:00:43 vendetta-laptop kernel: [    2.689648] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
Mar  5 12:00:43 vendetta-laptop kernel: [    2.693920] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
Mar  5 12:00:43 vendetta-laptop kernel: [    2.693924] e100: Copyright(c) 1999-2006 Intel Corporation
Mar  5 12:00:43 vendetta-laptop kernel: [    2.703845] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar  5 12:00:43 vendetta-laptop kernel: [    2.703861] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar  5 12:00:43 vendetta-laptop kernel: [    2.703905] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Mar  5 12:00:43 vendetta-laptop kernel: [    2.703947] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001840
Mar  5 12:00:43 vendetta-laptop kernel: [    2.704092] usb usb2: configuration #1 chosen from 1 choice
Mar  5 12:00:43 vendetta-laptop kernel: [    2.704127] hub 2-0:1.0: USB hub found
Mar  5 12:00:43 vendetta-laptop kernel: [    2.704136] hub 2-0:1.0: 2 ports detected
Mar  5 12:00:43 vendetta-laptop kernel: [    2.714935] ACPI: ACPI Dock Station Driver
Mar  5 12:00:43 vendetta-laptop kernel: [    2.736909] SCSI subsystem initialized
Mar  5 12:00:43 vendetta-laptop kernel: [    2.808317] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar  5 12:00:43 vendetta-laptop kernel: [    2.808334] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar  5 12:00:43 vendetta-laptop kernel: [    2.808366] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Mar  5 12:00:43 vendetta-laptop kernel: [    2.808408] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
Mar  5 12:00:43 vendetta-laptop kernel: [    2.808517] usb usb3: configuration #1 chosen from 1 choice
Mar  5 12:00:43 vendetta-laptop kernel: [    2.808550] hub 3-0:1.0: USB hub found
Mar  5 12:00:43 vendetta-laptop kernel: [    2.808558] hub 3-0:1.0: 2 ports detected
Mar  5 12:00:43 vendetta-laptop kernel: [    3.016384] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Mar  5 12:00:43 vendetta-laptop kernel: [    3.016402] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Mar  5 12:00:43 vendetta-laptop kernel: [    3.016433] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Mar  5 12:00:43 vendetta-laptop kernel: [    3.016474] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
Mar  5 12:00:43 vendetta-laptop kernel: [    3.016581] usb usb4: configuration #1 chosen from 1 choice
Mar  5 12:00:43 vendetta-laptop kernel: [    3.016616] hub 4-0:1.0: USB hub found
Mar  5 12:00:43 vendetta-laptop kernel: [    3.016624] hub 4-0:1.0: 2 ports detected
Mar  5 12:00:43 vendetta-laptop kernel: [    3.128078] usb 3-2: new full speed USB device using uhci_hcd and address 2
Mar  5 12:00:43 vendetta-laptop kernel: [    3.224660] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar  5 12:00:43 vendetta-laptop kernel: [    3.224684] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar  5 12:00:43 vendetta-laptop kernel: [    3.224719] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Mar  5 12:00:43 vendetta-laptop kernel: [    3.228615] ehci_hcd 0000:00:1d.7: debug port 1
Mar  5 12:00:43 vendetta-laptop kernel: [    3.228634] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd03c4000
Mar  5 12:00:43 vendetta-laptop kernel: [    3.261067] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar  5 12:00:43 vendetta-laptop kernel: [    3.261302] usb usb5: configuration #1 chosen from 1 choice
Mar  5 12:00:43 vendetta-laptop kernel: [    3.261357] hub 5-0:1.0: USB hub found
Mar  5 12:00:43 vendetta-laptop kernel: [    3.261380] hub 5-0:1.0: 8 ports detected
Mar  5 12:00:43 vendetta-laptop kernel: [    3.468699] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar  5 12:00:43 vendetta-laptop kernel: [    3.468853] scsi0 : ata_piix
Mar  5 12:00:43 vendetta-laptop kernel: [    3.469196] scsi1 : ata_piix
Mar  5 12:00:43 vendetta-laptop kernel: [    3.469920] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Mar  5 12:00:43 vendetta-laptop kernel: [    3.469924] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Mar  5 12:00:43 vendetta-laptop kernel: [    3.632584] ata1.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.60, max UDMA/33
Mar  5 12:00:43 vendetta-laptop kernel: [    3.648550] ata1.00: configured for UDMA/33
Mar  5 12:00:43 vendetta-laptop kernel: [    3.650577] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.60 PQ: 0 ANSI: 5
Mar  5 12:00:43 vendetta-laptop kernel: [    3.650787] e100 0000:0a:08.0: enabling device (0000 -> 0003)
Mar  5 12:00:43 vendetta-laptop kernel: [    3.650801] e100 0000:0a:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar  5 12:00:43 vendetta-laptop kernel: [    3.651178] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar  5 12:00:43 vendetta-laptop kernel: [    3.651184] ata_piix 0000:00:1f.2: MAP [ P0 P2 -- -- ]
Mar  5 12:00:43 vendetta-laptop kernel: [    3.677756] e100 0000:0a:08.0: PME# disabled
Mar  5 12:00:43 vendetta-laptop kernel: [    3.678770] e100: eth0: e100_probe: addr 0xd0005000, irq 20, MAC addr 00:13:a9:84:ca:c3
Mar  5 12:00:43 vendetta-laptop kernel: [    3.804193] scsi2 : ata_piix
Mar  5 12:00:43 vendetta-laptop kernel: [    3.804598] scsi3 : ata_piix
Mar  5 12:00:43 vendetta-laptop kernel: [    3.805851] ata3: SATA max UDMA/133 cmd 0x18d0 ctl 0x18c4 bmdma 0x18b0 irq 19
Mar  5 12:00:43 vendetta-laptop kernel: [    3.805855] ata4: SATA max UDMA/133 cmd 0x18c8 ctl 0x18c0 bmdma 0x18b8 irq 19
Mar  5 12:00:43 vendetta-laptop kernel: [    3.952050] usb 5-6: new high speed USB device using ehci_hcd and address 2
Mar  5 12:00:43 vendetta-laptop kernel: [    3.968620] ata3.00: ATA-7: FUJITSU MHV2160BT PL, 0000004F, max UDMA/100
Mar  5 12:00:43 vendetta-laptop kernel: [    3.968626] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar  5 12:00:43 vendetta-laptop kernel: [    3.984654] ata3.00: configured for UDMA/100
Mar  5 12:00:43 vendetta-laptop kernel: [    4.148565] usb 5-6: configuration #1 chosen from 1 choice
Mar  5 12:00:43 vendetta-laptop kernel: [    4.151339] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHV2160B 0000 PQ: 0 ANSI: 5
Mar  5 12:00:43 vendetta-laptop kernel: [    4.151454] ohci1394 0000:0a:03.1: enabling device (0000 -> 0002)
Mar  5 12:00:43 vendetta-laptop kernel: [    4.151463] ohci1394 0000:0a:03.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 12:00:43 vendetta-laptop kernel: [    4.201213] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d0006000-d00067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Mar  5 12:00:43 vendetta-laptop kernel: [    4.221259] scsi 0:0:0:0: Attached scsi generic sg0 type 5
Mar  5 12:00:43 vendetta-laptop kernel: [    4.221401] scsi 2:0:0:0: Attached scsi generic sg1 type 0
Mar  5 12:00:43 vendetta-laptop kernel: [    4.237530] Driver 'sd' needs updating - please use bus_type methods
Mar  5 12:00:43 vendetta-laptop kernel: [    4.237772] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Mar  5 12:00:43 vendetta-laptop kernel: [    4.237793] sd 2:0:0:0: [sda] Write Protect is off
Mar  5 12:00:43 vendetta-laptop kernel: [    4.237828] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  5 12:00:43 vendetta-laptop kernel: [    4.237911] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Mar  5 12:00:43 vendetta-laptop kernel: [    4.237929] sd 2:0:0:0: [sda] Write Protect is off
Mar  5 12:00:43 vendetta-laptop kernel: [    4.237965] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  5 12:00:43 vendetta-laptop kernel: [    4.237969]  sda: sda1 sda2 sda3 sda4
Mar  5 12:00:43 vendetta-laptop kernel: [    4.247543] Driver 'sr' needs updating - please use bus_type methods
Mar  5 12:00:43 vendetta-laptop kernel: [    4.252007] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Mar  5 12:00:43 vendetta-laptop kernel: [    4.252012] Uniform CD-ROM driver Revision: 3.20
Mar  5 12:00:43 vendetta-laptop kernel: [    4.256057] usb 5-8: new high speed USB device using ehci_hcd and address 3
Mar  5 12:00:43 vendetta-laptop kernel: [    4.305638] sd 2:0:0:0: [sda] Attached SCSI disk
Mar  5 12:00:43 vendetta-laptop kernel: [    4.391763] usb 5-8: configuration #1 chosen from 1 choice
Mar  5 12:00:43 vendetta-laptop kernel: [    4.392810] usbcore: registered new interface driver libusual
Mar  5 12:00:43 vendetta-laptop kernel: [    4.411504] Initializing USB Mass Storage driver...
Mar  5 12:00:43 vendetta-laptop kernel: [    4.412024] scsi4 : SCSI emulation for USB Mass Storage devices
Mar  5 12:00:43 vendetta-laptop kernel: [    4.412174] usbcore: registered new interface driver usb-storage
Mar  5 12:00:43 vendetta-laptop kernel: [    4.412179] USB Mass Storage support registered.
Mar  5 12:00:43 vendetta-laptop kernel: [    4.651804] PM: Starting manual resume from disk
Mar  5 12:00:43 vendetta-laptop kernel: [    4.674807] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar  5 12:00:43 vendetta-laptop kernel: [    4.674812] EXT3-fs: write access will be enabled during recovery.
Mar  5 12:00:43 vendetta-laptop kernel: [    5.156088] kjournald starting.  Commit interval 5 seconds
Mar  5 12:00:43 vendetta-laptop kernel: [    5.156117] EXT3-fs: recovery complete.
Mar  5 12:00:43 vendetta-laptop kernel: [    5.163562] EXT3-fs: mounted filesystem with ordered data mode.
Mar  5 12:00:43 vendetta-laptop kernel: [    9.421999] scsi 4:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.52 PQ: 0 ANSI: 0
Mar  5 12:00:43 vendetta-laptop kernel: [    9.472485] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Mar  5 12:00:43 vendetta-laptop kernel: [    9.472645] sd 4:0:0:0: Attached scsi generic sg2 type 0
Mar  5 12:00:43 vendetta-laptop kernel: [   14.391562] udevd version 124 started
Mar  5 12:00:43 vendetta-laptop kernel: [   15.055345] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  5 12:00:43 vendetta-laptop kernel: [   15.121186] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar  5 12:00:43 vendetta-laptop kernel: [   15.153201] iTCO_vendor_support: vendor-support=0
Mar  5 12:00:43 vendetta-laptop kernel: [   15.265019] Linux agpgart interface v0.103
Mar  5 12:00:43 vendetta-laptop kernel: [   15.392177] ACPI: AC Adapter [ADP1] (on-line)
Mar  5 12:00:43 vendetta-laptop kernel: [   15.471249] ACPI: Battery Slot [BAT0] (battery present)
Mar  5 12:00:43 vendetta-laptop kernel: [   15.471471] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
Mar  5 12:00:43 vendetta-laptop kernel: [   15.472916] ACPI: Lid Switch [LID0]
Mar  5 12:00:43 vendetta-laptop kernel: [   15.472976] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Mar  5 12:00:43 vendetta-laptop kernel: [   15.489045] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Mar  5 12:00:43 vendetta-laptop kernel: [   15.490706] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Mar  5 12:00:43 vendetta-laptop kernel: [   15.490813] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Mar  5 12:00:43 vendetta-laptop kernel: [   15.500027] ACPI: Power Button (CM) [PWRB]
Mar  5 12:00:43 vendetta-laptop kernel: [   15.562136] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
Mar  5 12:00:43 vendetta-laptop kernel: [   15.562697] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Mar  5 12:00:43 vendetta-laptop kernel: [   15.583003] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
Mar  5 12:00:43 vendetta-laptop kernel: [   15.654692] sony-laptop: Sony Notebook Control Driver v0.6.
Mar  5 12:00:43 vendetta-laptop kernel: [   15.661655] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2b/SNY5001:00/input/input4
Mar  5 12:00:43 vendetta-laptop kernel: [   15.689114] input: Sony Vaio Jogdial as /devices/virtual/input/input5
Mar  5 12:00:43 vendetta-laptop kernel: [   15.718127] sony-laptop: detected Sony Vaio FE Series
Mar  5 12:00:43 vendetta-laptop kernel: [   15.892165] Yenta: CardBus bridge found at 0000:0a:03.0 [104d:81ef]
Mar  5 12:00:43 vendetta-laptop kernel: [   15.892191] Yenta: Enabling burst memory read transactions
Mar  5 12:00:43 vendetta-laptop kernel: [   15.892197] Yenta: Using CSCINT to route CSC interrupts to PCI
Mar  5 12:00:43 vendetta-laptop kernel: [   15.892200] Yenta: Routing CardBus interrupts to PCI
Mar  5 12:00:43 vendetta-laptop kernel: [   15.892207] Yenta TI: socket 0000:0a:03.0, mfunc 0x01131b22, devctl 0x64
Mar  5 12:00:43 vendetta-laptop kernel: [   16.121832] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
Mar  5 12:00:43 vendetta-laptop kernel: [   16.121838] Socket status: 30000006
Mar  5 12:00:43 vendetta-laptop kernel: [   16.121842] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
Mar  5 12:00:43 vendetta-laptop kernel: [   16.121850] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x6fff
Mar  5 12:00:43 vendetta-laptop kernel: [   16.121853] cs: IO port probe 0x6000-0x6fff: clean.
Mar  5 12:00:43 vendetta-laptop kernel: [   16.122160] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
Mar  5 12:00:43 vendetta-laptop kernel: [   16.122163] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
Mar  5 12:00:43 vendetta-laptop kernel: [   16.131854] tifm_7xx1 0000:0a:03.2: enabling device (0000 -> 0002)
Mar  5 12:00:43 vendetta-laptop kernel: [   16.131864] tifm_7xx1 0000:0a:03.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar  5 12:00:43 vendetta-laptop kernel: [   16.132232] intel_rng: FWH not detected
Mar  5 12:00:43 vendetta-laptop kernel: [   16.195579] acpi device:07: registered as cooling_device2
Mar  5 12:00:43 vendetta-laptop kernel: [   16.195832] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/input/input6
Mar  5 12:00:43 vendetta-laptop kernel: [   16.214477] input: PC Speaker as /devices/platform/pcspkr/input/input7
Mar  5 12:00:43 vendetta-laptop kernel: [   16.307777] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Mar  5 12:00:43 vendetta-laptop kernel: [   16.333111] Linux video capture interface: v2.00
Mar  5 12:00:43 vendetta-laptop kernel: [   16.501089] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1836)
Mar  5 12:00:43 vendetta-laptop kernel: [   16.501909] usbcore: registered new interface driver uvcvideo
Mar  5 12:00:43 vendetta-laptop kernel: [   16.501946] USB Video Class driver (v0.1.0)
Mar  5 12:00:43 vendetta-laptop kernel: [   16.535326] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
Mar  5 12:00:43 vendetta-laptop kernel: [   16.582713] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
Mar  5 12:00:43 vendetta-laptop kernel: [   16.609130] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Mar  5 12:00:43 vendetta-laptop kernel: [   16.609135] iwl3945: Copyright(c) 2003-2008 Intel Corporation
Mar  5 12:00:43 vendetta-laptop kernel: [   16.609211] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar  5 12:00:43 vendetta-laptop kernel: [   16.609249] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Mar  5 12:00:43 vendetta-laptop kernel: [   16.666228] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Mar  5 12:00:43 vendetta-laptop kernel: [   17.165951] iwl3945 0000:06:00.0: PCI INT A disabled
Mar  5 12:00:43 vendetta-laptop kernel: [   17.285240] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar  5 12:00:43 vendetta-laptop kernel: [   17.586073] cs: IO port probe 0x100-0x3af: clean.
Mar  5 12:00:43 vendetta-laptop kernel: [   17.588135] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Mar  5 12:00:43 vendetta-laptop kernel: [   17.588994] cs: IO port probe 0x820-0x8ff: clean.
Mar  5 12:00:43 vendetta-laptop kernel: [   17.589722] cs: IO port probe 0xc00-0xcf7: clean.
Mar  5 12:00:43 vendetta-laptop kernel: [   17.590626] cs: IO port probe 0xa00-0xaff: clean.
Mar  5 12:00:43 vendetta-laptop kernel: [   18.427242] lp: driver loaded but no devices found
Mar  5 12:00:43 vendetta-laptop kernel: [   18.635063] Adding 2939884k swap on /dev/sda4.  Priority:-1 extents:1 across:2939884k
Mar  5 12:00:43 vendetta-laptop kernel: [   19.186712] EXT3 FS on sda3, internal journal
Mar  5 12:00:43 vendetta-laptop kernel: [   20.655397] type=1505 audit(1236272441.397:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4293
Mar  5 12:00:43 vendetta-laptop kernel: [   20.722616] type=1505 audit(1236272441.465:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4298
Mar  5 12:00:43 vendetta-laptop kernel: [   20.914897] type=1505 audit(1236272441.657:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4302
Mar  5 12:00:43 vendetta-laptop kernel: [   20.915117] type=1505 audit(1236272441.657:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4302
Mar  5 12:00:43 vendetta-laptop kernel: [   21.052687] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar  5 12:00:43 vendetta-laptop kernel: [   21.753335] ACPI: WMI: Mapper loaded
Mar  5 12:00:43 vendetta-laptop kernel: [   22.917255] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar  5 12:00:43 vendetta-laptop kernel: [   22.989821] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Mar  5 12:00:43 vendetta-laptop kernel: [   22.989829] apm: disabled - APM is not SMP safe.
Mar  5 12:00:45 vendetta-laptop kernel: [   24.263890] ppdev: user-space parallel port driver
Mar  5 12:00:46 vendetta-laptop kernel: [   25.770810] sonypi: Sony Programmable I/O Controller Driver v1.26.
Mar  5 12:00:46 vendetta-laptop kernel: [   25.770879] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
Mar  5 12:00:46 vendetta-laptop kernel: [   25.771012] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
Mar  5 12:00:46 vendetta-laptop kernel: [   25.771023] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
Mar  5 12:00:46 vendetta-laptop kernel: [   25.771025] sonypi: device allocated minor is 60
Mar  5 12:00:46 vendetta-laptop kernel: [   25.771079] input: Sony Vaio Jogdial as /devices/platform/sonypi/input/input10
Mar  5 12:00:46 vendetta-laptop kernel: [   25.816170] input: Sony Vaio Keys as /devices/platform/sonypi/input/input11
Mar  5 12:00:46 vendetta-laptop kernel: [   25.916452] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
Mar  5 12:00:46 vendetta-laptop kernel: [   25.956719] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 664)
Mar  5 12:00:46 vendetta-laptop kernel: [   25.996973] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 666)
Mar  5 12:00:46 vendetta-laptop kernel: [   26.037231] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
Mar  5 12:00:48 vendetta-laptop kernel: [   28.010750] NET: Registered protocol family 10
Mar  5 12:00:48 vendetta-laptop kernel: [   28.011724] lo: Disabled Privacy Extensions
Mar  5 12:00:50 vendetta-laptop kernel: [   29.424785] Bluetooth: Core ver 2.13
Mar  5 12:00:50 vendetta-laptop kernel: [   29.426444] NET: Registered protocol family 31
Mar  5 12:00:50 vendetta-laptop kernel: [   29.426452] Bluetooth: HCI device and connection manager initialized
Mar  5 12:00:50 vendetta-laptop kernel: [   29.426458] Bluetooth: HCI socket layer initialized
Mar  5 12:00:50 vendetta-laptop kernel: [   29.460247] Bluetooth: L2CAP ver 2.11
Mar  5 12:00:50 vendetta-laptop kernel: [   29.460256] Bluetooth: L2CAP socket layer initialized
Mar  5 12:00:50 vendetta-laptop kernel: [   29.491133] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar  5 12:00:50 vendetta-laptop kernel: [   29.491142] Bluetooth: BNEP filters: protocol multicast
Mar  5 12:00:50 vendetta-laptop kernel: [   29.540421] Bridge firewalling registered
Mar  5 12:00:50 vendetta-laptop kernel: [   29.563192] Bluetooth: SCO (Voice Link) ver 0.6
Mar  5 12:00:50 vendetta-laptop kernel: [   29.563199] Bluetooth: SCO socket layer initialized
Mar  5 12:00:50 vendetta-laptop kernel: [   29.584031] Bluetooth: RFCOMM socket layer initialized
Mar  5 12:00:50 vendetta-laptop kernel: [   29.584046] Bluetooth: RFCOMM TTY layer initialized
Mar  5 12:00:50 vendetta-laptop kernel: [   29.584048] Bluetooth: RFCOMM ver 1.10
Mar  5 12:00:53 vendetta-laptop kernel: [   33.240349] [drm] Initialized drm 1.1.0 20060810
Mar  5 12:00:53 vendetta-laptop kernel: [   33.248030] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 12:00:53 vendetta-laptop kernel: [   33.248265] [drm] Initialized i915 1.6.0 20060119 on minor 0
Mar  5 12:00:54 vendetta-laptop kernel: [   33.747763] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar  5 12:00:54 vendetta-laptop kernel: [   33.759294] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar  5 12:00:54 vendetta-laptop kernel: [   33.761759] firmware: requesting iwlwifi-3945-1.ucode
Mar  5 12:00:54 vendetta-laptop kernel: [   33.902027] Registered led device: iwl-phy0:radio
Mar  5 12:00:54 vendetta-laptop kernel: [   33.902054] Registered led device: iwl-phy0:assoc
Mar  5 12:00:54 vendetta-laptop kernel: [   33.902117] Registered led device: iwl-phy0:RX
Mar  5 12:00:54 vendetta-laptop kernel: [   33.902137] Registered led device: iwl-phy0:TX
Mar  5 12:00:54 vendetta-laptop kernel: [   33.977674] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  5 12:00:54 vendetta-laptop kernel: [   34.041360] NET: Registered protocol family 17
Mar  5 12:00:57 vendetta-laptop kernel: [   36.832271] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar  5 12:01:05 vendetta-laptop pulseaudio[5888]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar  5 12:01:05 vendetta-laptop pulseaudio[5890]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar  5 12:01:05 vendetta-laptop pulseaudio[5890]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar  5 12:07:24 vendetta-laptop kernel: [  423.258796] CE: hpet increasing min_delta_ns to 15000 nsec
Mar  5 12:20:42 vendetta-laptop -- MARK --
Mar  5 12:40:42 vendetta-laptop -- MARK --
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238312] Modules linked in: af_packet i915 drm binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ipv6 sonypi ppdev acpi_cpufreq cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table container wmi sbs sbshc pci_slot iptable_filter ip_tables x_tables sbp2 parport_pc lp parport joydev snd_hda_intel pcmcia snd_pcm_oss snd_mixer_oss arc4 snd_pcm ecb crypto_blkcipher snd_seq_dummy iwl3945 snd_seq_oss snd_seq_midi rfkill uvcvideo compat_ioctl32 snd_rawmidi mac80211 videodev snd_seq_midi_event snd_seq led_class v4l1_compat psmouse pcspkr video evdev serio_raw cfg80211 snd_timer snd_seq_device tifm_7xx1 yenta_socket rsrc_nonstatic snd soundcore pcmcia_core sony_laptop output tifm_core intel_agp iTCO_wdt button battery ac agpgart iTCO_vendor_support shpchp pci_hotplug snd_page_alloc ext3 jbd mbcache usb_storage sr_mod cdrom sd_mod crc_t10dif sg ata_generic pata_acpi libusual ata_piix libata scsi_mod ohci1394 dock ieee1394 e100 mii ehci
Mar  5 12:49:09 vendetta-laptop kernel: hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238522] 
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238527] Pid: 24235, comm: ps Not tainted (2.6.27-11-generic #1)
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238532] EIP: 0060:[<c0253d70>] EFLAGS: 00200246 CPU: 0
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238558] EIP is at vsnprintf+0x3f0/0x7b0
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238563] EAX: 00004c15 EBX: c043249f ECX: 0000000a EDX: 00000000
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238567] ESI: ffffffff EDI: 00000000 EBP: e6337e40 ESP: e6337d1c
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238572]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238576] CR0: 8005003b CR2: b7d900c0 CR3: 2630f000 CR4: 00000690
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238581] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238586] DR6: ffff0ff0 DR7: 00000400
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238591]  [<c037f45d>] ? _spin_lock+0xd/0x10
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238602]  [<c01c5c51>] ? __d_lookup+0xf1/0x120
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238610]  [<c037f45d>] ? _spin_lock+0xd/0x10
Mar  5 12:49:09 vendetta-laptop kernel: [ 2929.238618]  [<c01f03a6>] ? task_dumpable+0x46/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238626]  [<c0214f78>] ? cap_task_to_inode+0x8/0x10
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238635]  [<c0214184>] ? security_task_to_inode+0x14/0x20
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238643]  [<c01badbb>] ? __follow_mount+0xb/0x90
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238651]  [<c025418d>] ? scnprintf+0x1d/0x30
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238659]  [<c0257225>] ? bitmap_scnlistprintf+0xf5/0x100
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238667]  [<c01cfd2f>] ? seq_printf+0x2f/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238676]  [<c01cfd2f>] seq_printf+0x2f/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238683]  [<c01f5b58>] proc_pid_status+0x478/0x520
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238691]  [<c01f2027>] proc_single_show+0x57/0x90
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238698]  [<c01cffae>] seq_read+0x12e/0x2d0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238705]  [<c01b296d>] vfs_read+0x9d/0x110
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238713]  [<c01cfe80>] ? seq_read+0x0/0x2d0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238721]  [<c01b2ab2>] sys_read+0x42/0x70
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238727]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238734]  [<c0370000>] ? enable_nonboot_cpus+0x60/0xc0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.238742]  =======================
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245061] Modules linked in: af_packet i915 drm binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ipv6 sonypi ppdev acpi_cpufreq cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table container wmi sbs sbshc pci_slot iptable_filter ip_tables x_tables sbp2 parport_pc lp parport joydev snd_hda_intel pcmcia snd_pcm_oss snd_mixer_oss arc4 snd_pcm ecb crypto_blkcipher snd_seq_dummy iwl3945 snd_seq_oss snd_seq_midi rfkill uvcvideo compat_ioctl32 snd_rawmidi mac80211 videodev snd_seq_midi_event snd_seq led_class v4l1_compat psmouse pcspkr video evdev serio_raw cfg80211 snd_timer snd_seq_device tifm_7xx1 yenta_socket rsrc_nonstatic snd soundcore pcmcia_core sony_laptop output tifm_core intel_agp iTCO_wdt button battery ac agpgart iTCO_vendor_support shpchp pci_hotplug snd_page_alloc ext3 jbd mbcache usb_storage sr_mod cdrom sd_mod crc_t10dif sg ata_generic pata_acpi libusual ata_piix libata scsi_mod ohci1394 dock ieee1394 e100 mii ehci
Mar  5 12:49:10 vendetta-laptop kernel: hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245252] 
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245256] Pid: 24235, comm: ps Not tainted (2.6.27-11-generic #1)
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245261] EIP: 0060:[<c0253d70>] EFLAGS: 00200246 CPU: 0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245267] EIP is at vsnprintf+0x3f0/0x7b0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245271] EAX: 00004c15 EBX: c043249f ECX: 0000000a EDX: 00000000
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245276] ESI: ffffffff EDI: 00000000 EBP: e6337e40 ESP: e6337d1c
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245280]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245285] CR0: 8005003b CR2: b7d900c0 CR3: 2630f000 CR4: 00000690
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245290] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245294] DR6: ffff0ff0 DR7: 00000400
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245299]  [<c037f45d>] ? _spin_lock+0xd/0x10
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245307]  [<c01c5c51>] ? __d_lookup+0xf1/0x120
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245315]  [<c037f45d>] ? _spin_lock+0xd/0x10
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245323]  [<c01f03a6>] ? task_dumpable+0x46/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245330]  [<c0214f78>] ? cap_task_to_inode+0x8/0x10
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245339]  [<c0214184>] ? security_task_to_inode+0x14/0x20
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245346]  [<c01badbb>] ? __follow_mount+0xb/0x90
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245354]  [<c025418d>] ? scnprintf+0x1d/0x30
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245362]  [<c0257225>] ? bitmap_scnlistprintf+0xf5/0x100
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245370]  [<c01cfd2f>] ? seq_printf+0x2f/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245378]  [<c01cfd2f>] seq_printf+0x2f/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245385]  [<c01f5b58>] proc_pid_status+0x478/0x520
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245394]  [<c01f2027>] proc_single_show+0x57/0x90
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245400]  [<c01cffae>] seq_read+0x12e/0x2d0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245408]  [<c01b296d>] vfs_read+0x9d/0x110
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245414]  [<c01cfe80>] ? seq_read+0x0/0x2d0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245422]  [<c01b2ab2>] sys_read+0x42/0x70
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245428]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245435]  [<c0370000>] ? enable_nonboot_cpus+0x60/0xc0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.245443]  =======================
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248064] Modules linked in: af_packet i915 drm binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ipv6 sonypi ppdev acpi_cpufreq cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table container wmi sbs sbshc pci_slot iptable_filter ip_tables x_tables sbp2 parport_pc lp parport joydev snd_hda_intel pcmcia snd_pcm_oss snd_mixer_oss arc4 snd_pcm ecb crypto_blkcipher snd_seq_dummy iwl3945 snd_seq_oss snd_seq_midi rfkill uvcvideo compat_ioctl32 snd_rawmidi mac80211 videodev snd_seq_midi_event snd_seq led_class v4l1_compat psmouse pcspkr video evdev serio_raw cfg80211 snd_timer snd_seq_device tifm_7xx1 yenta_socket rsrc_nonstatic snd soundcore pcmcia_core sony_laptop output tifm_core intel_agp iTCO_wdt button battery ac agpgart iTCO_vendor_support shpchp pci_hotplug snd_page_alloc ext3 jbd mbcache usb_storage sr_mod cdrom sd_mod crc_t10dif sg ata_generic pata_acpi libusual ata_piix libata scsi_mod ohci1394 dock ieee1394 e100 mii ehci
Mar  5 12:49:10 vendetta-laptop kernel: hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248305] 
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248311] Pid: 24235, comm: ps Not tainted (2.6.27-11-generic #1)
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248319] EIP: 0060:[<c0253d70>] EFLAGS: 00200246 CPU: 0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248330] EIP is at vsnprintf+0x3f0/0x7b0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248337] EAX: 00004c15 EBX: c043249f ECX: 0000000a EDX: 00000000
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248345] ESI: ffffffff EDI: 00000000 EBP: e6337e40 ESP: e6337d1c
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248353]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248360] CR0: 8005003b CR2: b7ffe000 CR3: 2630f000 CR4: 00000690
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248369] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248377] DR6: ffff0ff0 DR7: 00000400
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248384]  [<c037f45d>] ? _spin_lock+0xd/0x10
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248394]  [<c01c5c51>] ? __d_lookup+0xf1/0x120
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248405]  [<c037f45d>] ? _spin_lock+0xd/0x10
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248415]  [<c01f03a6>] ? task_dumpable+0x46/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248424]  [<c0214f78>] ? cap_task_to_inode+0x8/0x10
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248435]  [<c0214184>] ? security_task_to_inode+0x14/0x20
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248445]  [<c01badbb>] ? __follow_mount+0xb/0x90
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248455]  [<c025418d>] ? scnprintf+0x1d/0x30
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248464]  [<c0257225>] ? bitmap_scnlistprintf+0xf5/0x100
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248474]  [<c01cfd2f>] ? seq_printf+0x2f/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248484]  [<c01cfd2f>] seq_printf+0x2f/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248494]  [<c01f5b58>] proc_pid_status+0x478/0x520
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248505]  [<c01f2027>] proc_single_show+0x57/0x90
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248515]  [<c01cffae>] seq_read+0x12e/0x2d0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248525]  [<c01b296d>] vfs_read+0x9d/0x110
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248533]  [<c01cfe80>] ? seq_read+0x0/0x2d0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248542]  [<c01b2ab2>] sys_read+0x42/0x70
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248550]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248558]  [<c0370000>] ? enable_nonboot_cpus+0x60/0xc0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.248567]  =======================
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252076] Modules linked in: af_packet i915 drm binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ipv6 sonypi ppdev acpi_cpufreq cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table container wmi sbs sbshc pci_slot iptable_filter ip_tables x_tables sbp2 parport_pc lp parport joydev snd_hda_intel pcmcia snd_pcm_oss snd_mixer_oss arc4 snd_pcm ecb crypto_blkcipher snd_seq_dummy iwl3945 snd_seq_oss snd_seq_midi rfkill uvcvideo compat_ioctl32 snd_rawmidi mac80211 videodev snd_seq_midi_event snd_seq led_class v4l1_compat psmouse pcspkr video evdev serio_raw cfg80211 snd_timer snd_seq_device tifm_7xx1 yenta_socket rsrc_nonstatic snd soundcore pcmcia_core sony_laptop output tifm_core intel_agp iTCO_wdt button battery ac agpgart iTCO_vendor_support shpchp pci_hotplug snd_page_alloc ext3 jbd mbcache usb_storage sr_mod cdrom sd_mod crc_t10dif sg ata_generic pata_acpi libusual ata_piix libata scsi_mod ohci1394 dock ieee1394 e100 mii ehci
Mar  5 12:49:10 vendetta-laptop kernel: hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252320] 
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252324] Pid: 24235, comm: ps Not tainted (2.6.27-11-generic #1)
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252332] EIP: 0060:[<c0253d70>] EFLAGS: 00200246 CPU: 0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252343] EIP is at vsnprintf+0x3f0/0x7b0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252350] EAX: 00004c15 EBX: c043249f ECX: 0000000a EDX: 00000000
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252358] ESI: ffffffff EDI: 00000000 EBP: e6337e40 ESP: e6337d1c
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252365]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252372] CR0: 8005003b CR2: b80c8a71 CR3: 2630f000 CR4: 00000690
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252380] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252388] DR6: ffff0ff0 DR7: 00000400
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252395]  [<c037f45d>] ? _spin_lock+0xd/0x10
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252406]  [<c01c5c51>] ? __d_lookup+0xf1/0x120
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252415]  [<c037f45d>] ? _spin_lock+0xd/0x10
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252425]  [<c01f03a6>] ? task_dumpable+0x46/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252434]  [<c0214f78>] ? cap_task_to_inode+0x8/0x10
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252446]  [<c0214184>] ? security_task_to_inode+0x14/0x20
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252456]  [<c01badbb>] ? __follow_mount+0xb/0x90
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252466]  [<c025418d>] ? scnprintf+0x1d/0x30
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252475]  [<c0257225>] ? bitmap_scnlistprintf+0xf5/0x100
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252486]  [<c01cfd2f>] ? seq_printf+0x2f/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252497]  [<c01cfd2f>] seq_printf+0x2f/0x60
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252504]  [<c01f5b58>] proc_pid_status+0x478/0x520
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252514]  [<c01f2027>] proc_single_show+0x57/0x90
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252524]  [<c01cffae>] seq_read+0x12e/0x2d0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252534]  [<c01b296d>] vfs_read+0x9d/0x110
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252543]  [<c01cfe80>] ? seq_read+0x0/0x2d0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252551]  [<c01b2ab2>] sys_read+0x42/0x70
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252560]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252570]  [<c0370000>] ? enable_nonboot_cpus+0x60/0xc0
Mar  5 12:49:10 vendetta-laptop kernel: [ 2929.252580]  =======================
Mar  5 12:57:02 vendetta-laptop syslogd 1.5.0#2ubuntu6: restart.
Mar  5 12:57:03 vendetta-laptop kernel: Inspecting /boot/System.map-2.6.27-11-generic
Mar  5 12:57:03 vendetta-laptop kernel: Cannot find map file.
Mar  5 12:57:03 vendetta-laptop kernel: Loaded 52907 symbols from 102 modules.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f690000 (usable)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 000000007f690000 - 000000007f69a000 (ACPI data)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 000000007f69a000 - 000000007f700000 (ACPI NVS)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] DMI present.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] last_pfn = 0x7f690 max_arch_pfn = 0x100000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] RAMDISK: 37820000 - 37fef2e0
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: RSDP 000F7250, 0014 (r0 PTLTD )
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: RSDT 7F6922F8, 0054 (r1   Sony     VAIO 20070205 PTL         0)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: FACP 7F699C9A, 0084 (r2   Sony     VAIO 20070205 PTL        5A)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: DSDT 7F69416D, 5B2D (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: FACS 7F69AFC0, 0040
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: APIC 7F699D1E, 0068 (r1   Sony     VAIO 20070205 PTL        5A)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: HPET 7F699D86, 0038 (r1   Sony     VAIO 20070205 PTL        5A)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: MCFG 7F699DBE, 003C (r1   Sony     VAIO 20070205 PTL        5A)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: SLIC 7F699DFA, 0176 (r1   Sony     VAIO 20070205 PTL   1000000)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: APIC 7F699F70, 0068 (r1   Sony     VAIO 20070205 PTL         0)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: BOOT 7F699FD8, 0028 (r1   Sony     VAIO 20070205 PTL         1)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: SSDT 7F6939E1, 078C (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: SSDT 7F693345, 069C (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: SSDT 7F6928E2, 025F (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: SSDT 7F69283C, 00A6 (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: SSDT 7F69234C, 04F0 (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: DMI detected: Sony
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] 1142MB HIGHMEM available.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] 896MB LOWMEM available.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   mapped low ram: 0 - 38000000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   low ram: 00000000 - 38000000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   bootmap 00011000 - 00018000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   #4 [0037820000 - 0037fef2e0]          RAMDISK ==> [0037820000 - 0037fef2e0]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   #6 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] found SMP MP-table at [c00f7320] 000f7320
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Zone PFN ranges:
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]   HighMem  0x00038000 -> 0x0007f690
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Movable zone start PFN for each node
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0007f690
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517172
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Kernel command line: root=UUID=22a9f34b-1f50-470f-bf8c-fa688d2ab18c ro quiet splash 
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Initializing CPU#0
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] TSC: using PIT calibration value
Mar  5 12:57:03 vendetta-laptop kernel: [    0.000000] Detected 1662.467 MHz processor.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Console: colour VGA+ 80x25
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] console [tty0] enabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Memory: 2054068k/2087488k available (2576k kernel code, 32188k reserved, 1165k data, 424k init, 1169984k highmem)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] virtual kernel memory layout:
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.93 BogoMIPS (lpj=6649868)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Security Framework initialized
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] SELinux:  Disabled at boot.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] AppArmor: AppArmor initialized
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Mount-cache hash table entries: 512
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Initializing cgroup subsys ns
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Initializing cgroup subsys memory
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] CPU: Processor Core ID: 0
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] using mwait in idle threads.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.018224] ACPI: Core revision 20080609
Mar  5 12:57:03 vendetta-laptop kernel: [    0.020811] ACPI: Checking initramfs for custom DSDT
Mar  5 12:57:03 vendetta-laptop kernel: [    0.428286] ENABLING IO-APIC IRQs
Mar  5 12:57:03 vendetta-laptop kernel: [    0.428482] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar  5 12:57:03 vendetta-laptop kernel: [    0.469346] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Mar  5 12:57:03 vendetta-laptop kernel: [    0.472029] Booting processor 1/1 ip 6000
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Initializing CPU#1
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3325.04 BogoMIPS (lpj=6650098)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar  5 12:57:03 vendetta-laptop kernel: [    0.004000] CPU: Processor Core ID: 1
Mar  5 12:57:03 vendetta-laptop kernel: [    0.556536] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Mar  5 12:57:03 vendetta-laptop kernel: [    0.556556] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560055] Brought up 2 CPUs
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560058] Total of 2 processors activated (6649.98 BogoMIPS).
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560197] net_namespace: 840 bytes
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560197] Booting paravirtualized kernel on bare hardware
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560344] Time: 12:56:37  Date: 03/05/09
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560374] NET: Registered protocol family 16
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560397] EISA bus registered
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560397] ACPI: bus type pci registered
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560397] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560397] PCI: MCFG area at e0000000 reserved in E820
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560397] PCI: Using MMCONFIG for extended config space
Mar  5 12:57:03 vendetta-laptop kernel: [    0.560397] PCI: Using configuration type 1 for base access
Mar  5 12:57:03 vendetta-laptop kernel: [    0.576720] ACPI: Interpreter enabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.576726] ACPI: (supports S0 S3 S4 S5)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.576744] ACPI: Using IOAPIC for interrupt routing
Mar  5 12:57:03 vendetta-laptop kernel: [    0.576813] ACPI: EC: non-query interrupt received, switching to interrupt mode
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608473] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608473] ACPI: EC: driver started in interrupt mode
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608473] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608473] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608473] pci 0000:00:1b.0: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608473] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608473] pci 0000:00:1c.0: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608520] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608525] pci 0000:00:1c.1: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608602] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608607] pci 0000:00:1c.2: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608683] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Mar  5 12:57:03 vendetta-laptop kernel: [    0.608689] pci 0000:00:1c.3: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.609078] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Mar  5 12:57:03 vendetta-laptop kernel: [    0.609085] pci 0000:00:1d.7: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.609254] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Mar  5 12:57:03 vendetta-laptop kernel: [    0.609259] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Mar  5 12:57:03 vendetta-laptop kernel: [    0.609455] pci 0000:00:1f.2: PME# supported from D3hot
Mar  5 12:57:03 vendetta-laptop kernel: [    0.609461] pci 0000:00:1f.2: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.610075] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
Mar  5 12:57:03 vendetta-laptop kernel: [    0.610088] pci 0000:06:00.0: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.612120] pci 0000:0a:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 12:57:03 vendetta-laptop kernel: [    0.612126] pci 0000:0a:03.0: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.612248] pci 0000:0a:03.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 12:57:03 vendetta-laptop kernel: [    0.612254] pci 0000:0a:03.1: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.612368] pci 0000:0a:03.2: PME# supported from D0 D1 D2 D3hot
Mar  5 12:57:03 vendetta-laptop kernel: [    0.612374] pci 0000:0a:03.2: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.612494] pci 0000:0a:08.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar  5 12:57:03 vendetta-laptop kernel: [    0.612500] pci 0000:0a:08.0: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.612546] pci 0000:00:1e.0: transparent bridge
Mar  5 12:57:03 vendetta-laptop kernel: [    0.624167] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.624318] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.624466] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Mar  5 12:57:03 vendetta-laptop kernel: [    0.624612] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Mar  5 12:57:03 vendetta-laptop kernel: [    0.624759] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Mar  5 12:57:03 vendetta-laptop kernel: [    0.624905] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *7 11 12 14 15)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.625052] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 *4 5 6 7 10 12 14 15)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.625198] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 11 12 14 15)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.625287] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar  5 12:57:03 vendetta-laptop kernel: [    0.625287] pnp: PnP ACPI init
Mar  5 12:57:03 vendetta-laptop kernel: [    0.625287] ACPI: bus type pnp registered
Mar  5 12:57:03 vendetta-laptop kernel: [    0.636305] pnp: PnP ACPI: found 10 devices
Mar  5 12:57:03 vendetta-laptop kernel: [    0.636305] ACPI: ACPI bus type pnp unregistered
Mar  5 12:57:03 vendetta-laptop kernel: [    0.636305] PnPBIOS: Disabled by ACPI PNP
Mar  5 12:57:03 vendetta-laptop kernel: [    0.636305] PCI: Using ACPI for IRQ routing
Mar  5 12:57:03 vendetta-laptop kernel: [    0.644042] NET: Registered protocol family 8
Mar  5 12:57:03 vendetta-laptop kernel: [    0.644045] NET: Registered protocol family 20
Mar  5 12:57:03 vendetta-laptop kernel: [    0.644066] NetLabel: Initializing
Mar  5 12:57:03 vendetta-laptop kernel: [    0.644066] NetLabel:  domain hash size = 128
Mar  5 12:57:03 vendetta-laptop kernel: [    0.644066] NetLabel:  protocols = UNLABELED CIPSOv4
Mar  5 12:57:03 vendetta-laptop kernel: [    0.644077] NetLabel:  unlabeled traffic allowed by default
Mar  5 12:57:03 vendetta-laptop kernel: [    0.644086] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Mar  5 12:57:03 vendetta-laptop kernel: [    0.644092] hpet0: 3 64-bit timers, 14318180 Hz
Mar  5 12:57:03 vendetta-laptop kernel: [    0.645657] tracer: 772 pages allocated for 65536 entries of 48 bytes
Mar  5 12:57:03 vendetta-laptop kernel: [    0.645661]    actual entries 65620
Mar  5 12:57:03 vendetta-laptop kernel: [    0.645758] AppArmor: AppArmor Filesystem Enabled
Mar  5 12:57:03 vendetta-laptop kernel: [    0.645789] ACPI: RTC can wake from S4
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652027] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652031] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652035] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652039] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652042] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652046] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652050] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652062] system 00:06: ioport range 0x680-0x6ff has been reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652065] system 00:06: ioport range 0x800-0x80f has been reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652069] system 00:06: ioport range 0x1000-0x107f has been reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652072] system 00:06: ioport range 0x1180-0x11bf has been reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652076] system 00:06: ioport range 0x1640-0x164f has been reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652079] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.652083] system 00:06: ioport range 0xfe80-0xfeff has been reserved
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687381] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687386] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687393] pci 0000:00:1c.0:   MEM window: 0xc8000000-0xc9ffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687399] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0000000-0x000000c1ffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687409] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687413] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687420] pci 0000:00:1c.1:   MEM window: 0xca000000-0xcbffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687426] pci 0000:00:1c.1:   PREFETCH window: 0x000000c2000000-0x000000c3ffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687436] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687440] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687447] pci 0000:00:1c.2:   MEM window: 0xcc000000-0xcdffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687453] pci 0000:00:1c.2:   PREFETCH window: 0x000000c4000000-0x000000c5ffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687462] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:08
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687466] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687473] pci 0000:00:1c.3:   MEM window: 0xce000000-0xcfffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687479] pci 0000:00:1c.3:   PREFETCH window: 0x000000c6000000-0x000000c7ffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687495] pci 0000:0a:03.0: CardBus bridge, secondary bus 0000:0b
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687498] pci 0000:0a:03.0:   IO window: 0x006400-0x0064ff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687504] pci 0000:0a:03.0:   IO window: 0x006800-0x0068ff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687511] pci 0000:0a:03.0:   PREFETCH window: 0x88000000-0x8bffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687517] pci 0000:0a:03.0:   MEM window: 0x90000000-0x93ffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687523] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687527] pci 0000:00:1e.0:   IO window: 0x6000-0x6fff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687535] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd00fffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687540] pci 0000:00:1e.0:   PREFETCH window: 0x00000088000000-0x0000008bffffff
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687562] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687579] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687596] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687613] pci 0000:00:1c.3: PCI INT D -> GSI 21 (level, low) -> IRQ 21
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687626] pci 0000:00:1e.0: enabling device (0004 -> 0007)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687644] pci 0000:0a:03.0: enabling device (0000 -> 0003)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687649] pci 0000:0a:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687659] bus: 00 index 0 io port: [0, ffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687661] bus: 00 index 1 mmio: [0, ffffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687664] bus: 02 index 0 io port: [2000, 2fff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687667] bus: 02 index 1 mmio: [c8000000, c9ffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687670] bus: 02 index 2 mmio: [c0000000, c1ffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687672] bus: 02 index 3 mmio: [0, 0]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687674] bus: 04 index 0 io port: [3000, 3fff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687677] bus: 04 index 1 mmio: [ca000000, cbffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687679] bus: 04 index 2 mmio: [c2000000, c3ffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687682] bus: 04 index 3 mmio: [0, 0]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687684] bus: 06 index 0 io port: [4000, 4fff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687687] bus: 06 index 1 mmio: [cc000000, cdffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687689] bus: 06 index 2 mmio: [c4000000, c5ffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687692] bus: 06 index 3 mmio: [0, 0]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687694] bus: 08 index 0 io port: [5000, 5fff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687697] bus: 08 index 1 mmio: [ce000000, cfffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687699] bus: 08 index 2 mmio: [c6000000, c7ffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687702] bus: 08 index 3 mmio: [0, 0]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687704] bus: 0a index 0 io port: [6000, 6fff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687707] bus: 0a index 1 mmio: [d0000000, d00fffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687709] bus: 0a index 2 mmio: [88000000, 8bffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687712] bus: 0a index 3 io port: [0, ffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687714] bus: 0a index 4 mmio: [0, ffffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687717] bus: 0b index 0 io port: [6400, 64ff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687719] bus: 0b index 1 io port: [6800, 68ff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687722] bus: 0b index 2 mmio: [88000000, 8bffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687724] bus: 0b index 3 mmio: [90000000, 93ffffff]
Mar  5 12:57:03 vendetta-laptop kernel: [    0.687733] NET: Registered protocol family 2
Mar  5 12:57:03 vendetta-laptop kernel: [    0.700061] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.700329] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.700742] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.700970] TCP: Hash tables configured (established 131072 bind 65536)
Mar  5 12:57:03 vendetta-laptop kernel: [    0.700974] TCP reno registered
Mar  5 12:57:03 vendetta-laptop kernel: [    0.704086] NET: Registered protocol family 1
Mar  5 12:57:03 vendetta-laptop kernel: [    0.704227] checking if image is initramfs... it is
Mar  5 12:57:03 vendetta-laptop kernel: [    1.524747] Freeing initrd memory: 7996k freed
Mar  5 12:57:03 vendetta-laptop kernel: [    1.524946] Simple Boot Flag at 0x36 set to 0x1
Mar  5 12:57:03 vendetta-laptop kernel: [    1.526090] audit: initializing netlink socket (disabled)
Mar  5 12:57:03 vendetta-laptop kernel: [    1.526119] type=2000 audit(1236257797.525:1): initialized
Mar  5 12:57:03 vendetta-laptop kernel: [    1.533241] highmem bounce pool size: 64 pages
Mar  5 12:57:03 vendetta-laptop kernel: [    1.533248] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar  5 12:57:03 vendetta-laptop kernel: [    1.536205] VFS: Disk quotas dquot_6.5.1
Mar  5 12:57:03 vendetta-laptop kernel: [    1.536309] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar  5 12:57:03 vendetta-laptop kernel: [    1.536436] msgmni has been set to 1743
Mar  5 12:57:03 vendetta-laptop kernel: [    1.536580] io scheduler noop registered
Mar  5 12:57:03 vendetta-laptop kernel: [    1.536583] io scheduler anticipatory registered
Mar  5 12:57:03 vendetta-laptop kernel: [    1.536587] io scheduler deadline registered
Mar  5 12:57:03 vendetta-laptop kernel: [    1.536600] io scheduler cfq registered (default)
Mar  5 12:57:03 vendetta-laptop kernel: [    1.536931] pcieport-driver 0000:00:1c.0: found MSI capability
Mar  5 12:57:03 vendetta-laptop kernel: [    1.537278] pcieport-driver 0000:00:1c.1: found MSI capability
Mar  5 12:57:03 vendetta-laptop kernel: [    1.537612] pcieport-driver 0000:00:1c.2: found MSI capability
Mar  5 12:57:03 vendetta-laptop kernel: [    1.537947] pcieport-driver 0000:00:1c.3: found MSI capability
Mar  5 12:57:03 vendetta-laptop kernel: [    1.538531] isapnp: Scanning for PnP cards...
Mar  5 12:57:03 vendetta-laptop kernel: [    1.892445] isapnp: No Plug & Play device found
Mar  5 12:57:03 vendetta-laptop kernel: [    1.932483] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Mar  5 12:57:03 vendetta-laptop kernel: [    1.935309] brd: module loaded
Mar  5 12:57:03 vendetta-laptop kernel: [    1.935397] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Mar  5 12:57:03 vendetta-laptop kernel: [    1.935551] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar  5 12:57:03 vendetta-laptop kernel: [    1.939256] i8042.c: Detected active multiplexing controller, rev 1.1.
Mar  5 12:57:03 vendetta-laptop kernel: [    1.944828] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar  5 12:57:03 vendetta-laptop kernel: [    1.944835] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Mar  5 12:57:03 vendetta-laptop kernel: [    1.944839] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Mar  5 12:57:03 vendetta-laptop kernel: [    1.944842] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Mar  5 12:57:03 vendetta-laptop kernel: [    1.944845] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945224] mice: PS/2 mouse device common for all mice
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945410] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945443] rtc0: alarms up to one month, y3k, hpet irqs
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945600] EISA: Probing bus 0 at eisa.0
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945607] Cannot allocate resource for EISA slot 1
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945612] Cannot allocate resource for EISA slot 2
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945614] Cannot allocate resource for EISA slot 3
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945617] Cannot allocate resource for EISA slot 4
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945620] Cannot allocate resource for EISA slot 5
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945624] Cannot allocate resource for EISA slot 6
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945635] EISA: Detected 0 cards.
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945638] cpuidle: using governor ladder
Mar  5 12:57:03 vendetta-laptop kernel: [    1.945642] cpuidle: using governor menu
Mar  5 12:57:03 vendetta-laptop kernel: [    1.946244] TCP cubic registered
Mar  5 12:57:03 vendetta-laptop kernel: [    1.946275] Using IPI No-Shortcut mode
Mar  5 12:57:03 vendetta-laptop kernel: [    1.946492] registered taskstats version 1
Mar  5 12:57:03 vendetta-laptop kernel: [    1.946636]   Magic number: 1:518:935
Mar  5 12:57:03 vendetta-laptop kernel: [    1.946710] pci_express 0000:00:1c.3:pcie03: hash matches
Mar  5 12:57:03 vendetta-laptop kernel: [    1.946764] rtc_cmos 00:07: setting system clock to 2009-03-05 12:56:38 UTC (1236257798)
Mar  5 12:57:03 vendetta-laptop kernel: [    1.946768] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar  5 12:57:03 vendetta-laptop kernel: [    1.946771] EDD information not available.
Mar  5 12:57:03 vendetta-laptop kernel: [    1.947032] Freeing unused kernel memory: 424k freed
Mar  5 12:57:03 vendetta-laptop kernel: [    1.947077] Write protecting the kernel text: 2580k
Mar  5 12:57:03 vendetta-laptop kernel: [    1.947107] Write protecting the kernel read-only data: 940k
Mar  5 12:57:03 vendetta-laptop kernel: [    2.137049] fuse init (API version 7.9)
Mar  5 12:57:03 vendetta-laptop kernel: [    2.154824] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Mar  5 12:57:03 vendetta-laptop kernel: [    2.180614] ACPI: SSDT 7F693082, 01FB (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:57:03 vendetta-laptop kernel: [    2.181339] ACPI: SSDT 7F692B41, 04BC (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:57:03 vendetta-laptop kernel: [    2.184155] ACPI: CPU0 (power states: C1[C1] C2[C2])
Mar  5 12:57:03 vendetta-laptop kernel: [    2.184219] processor ACPI0007:00: registered as cooling_device0
Mar  5 12:57:03 vendetta-laptop kernel: [    2.184224] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar  5 12:57:03 vendetta-laptop kernel: [    2.184644] ACPI: SSDT 7F69327D, 00C8 (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:57:03 vendetta-laptop kernel: [    2.185088] ACPI: SSDT 7F692FFD, 0085 (r1   Sony     VAIO 20070205 PTL  20050228)
Mar  5 12:57:03 vendetta-laptop kernel: [    2.185940] Marking TSC unstable due to TSC halts in idle
Mar  5 12:57:03 vendetta-laptop kernel: [    2.186213] ACPI: CPU1 (power states: C1[C1] C2[C2])
Mar  5 12:57:03 vendetta-laptop kernel: [    2.186273] processor ACPI0007:01: registered as cooling_device1
Mar  5 12:57:03 vendetta-laptop kernel: [    2.186278] ACPI: Processor [CPU1] (supports 8 throttling states)
Mar  5 12:57:03 vendetta-laptop kernel: [    2.191008] thermal LNXTHERM:01: registered as thermal_zone0
Mar  5 12:57:03 vendetta-laptop kernel: [    2.195301] ACPI: Thermal Zone [TZ00] (55 C)
Mar  5 12:57:03 vendetta-laptop kernel: [    2.197153] thermal LNXTHERM:02: registered as thermal_zone1
Mar  5 12:57:03 vendetta-laptop kernel: [    2.200111] ACPI: Thermal Zone [TZ01] (55 C)
Mar  5 12:57:03 vendetta-laptop kernel: [    2.610309] usbcore: registered new interface driver usbfs
Mar  5 12:57:03 vendetta-laptop kernel: [    2.610337] usbcore: registered new interface driver hub
Mar  5 12:57:03 vendetta-laptop kernel: [    2.610399] usbcore: registered new device driver usb
Mar  5 12:57:03 vendetta-laptop kernel: [    2.624076] USB Universal Host Controller Interface driver v3.0
Mar  5 12:57:03 vendetta-laptop kernel: [    2.624148] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar  5 12:57:03 vendetta-laptop kernel: [    2.624163] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar  5 12:57:03 vendetta-laptop kernel: [    2.624226] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Mar  5 12:57:03 vendetta-laptop kernel: [    2.624267] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
Mar  5 12:57:03 vendetta-laptop kernel: [    2.624439] usb usb1: configuration #1 chosen from 1 choice
Mar  5 12:57:03 vendetta-laptop kernel: [    2.624471] hub 1-0:1.0: USB hub found
Mar  5 12:57:03 vendetta-laptop kernel: [    2.624481] hub 1-0:1.0: 2 ports detected
Mar  5 12:57:03 vendetta-laptop kernel: [    2.645159] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
Mar  5 12:57:03 vendetta-laptop kernel: [    2.649499] ACPI: ACPI Dock Station Driver
Mar  5 12:57:03 vendetta-laptop kernel: [    2.667139] SCSI subsystem initialized
Mar  5 12:57:03 vendetta-laptop kernel: [    2.735073] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar  5 12:57:03 vendetta-laptop kernel: [    2.735090] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar  5 12:57:03 vendetta-laptop kernel: [    2.735120] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Mar  5 12:57:03 vendetta-laptop kernel: [    2.735161] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001840
Mar  5 12:57:03 vendetta-laptop kernel: [    2.735268] usb usb2: configuration #1 chosen from 1 choice
Mar  5 12:57:03 vendetta-laptop kernel: [    2.735300] hub 2-0:1.0: USB hub found
Mar  5 12:57:03 vendetta-laptop kernel: [    2.735308] hub 2-0:1.0: 2 ports detected
Mar  5 12:57:03 vendetta-laptop kernel: [    2.738636] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
Mar  5 12:57:03 vendetta-laptop kernel: [    2.738639] e100: Copyright(c) 1999-2006 Intel Corporation
Mar  5 12:57:03 vendetta-laptop kernel: [    2.837297] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar  5 12:57:03 vendetta-laptop kernel: [    2.837315] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar  5 12:57:03 vendetta-laptop kernel: [    2.837357] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Mar  5 12:57:03 vendetta-laptop kernel: [    2.837400] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
Mar  5 12:57:03 vendetta-laptop kernel: [    2.837512] usb usb3: configuration #1 chosen from 1 choice
Mar  5 12:57:03 vendetta-laptop kernel: [    2.837543] hub 3-0:1.0: USB hub found
Mar  5 12:57:03 vendetta-laptop kernel: [    2.837552] hub 3-0:1.0: 2 ports detected
Mar  5 12:57:03 vendetta-laptop kernel: [    3.045307] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Mar  5 12:57:03 vendetta-laptop kernel: [    3.045325] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Mar  5 12:57:03 vendetta-laptop kernel: [    3.045359] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Mar  5 12:57:03 vendetta-laptop kernel: [    3.045401] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
Mar  5 12:57:03 vendetta-laptop kernel: [    3.045512] usb usb4: configuration #1 chosen from 1 choice
Mar  5 12:57:03 vendetta-laptop kernel: [    3.045544] hub 4-0:1.0: USB hub found
Mar  5 12:57:03 vendetta-laptop kernel: [    3.045552] hub 4-0:1.0: 2 ports detected
Mar  5 12:57:03 vendetta-laptop kernel: [    3.156059] usb 3-2: new full speed USB device using uhci_hcd and address 2
Mar  5 12:57:03 vendetta-laptop kernel: [    3.252512] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar  5 12:57:03 vendetta-laptop kernel: [    3.252536] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar  5 12:57:03 vendetta-laptop kernel: [    3.252568] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Mar  5 12:57:03 vendetta-laptop kernel: [    3.256464] ehci_hcd 0000:00:1d.7: debug port 1
Mar  5 12:57:03 vendetta-laptop kernel: [    3.256481] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd03c4000
Mar  5 12:57:03 vendetta-laptop kernel: [    3.289073] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar  5 12:57:03 vendetta-laptop kernel: [    3.289231] usb usb5: configuration #1 chosen from 1 choice
Mar  5 12:57:03 vendetta-laptop kernel: [    3.289265] hub 5-0:1.0: USB hub found
Mar  5 12:57:03 vendetta-laptop kernel: [    3.289274] hub 5-0:1.0: 8 ports detected
Mar  5 12:57:03 vendetta-laptop kernel: [    3.496380] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar  5 12:57:03 vendetta-laptop kernel: [    3.496527] scsi0 : ata_piix
Mar  5 12:57:03 vendetta-laptop kernel: [    3.496640] scsi1 : ata_piix
Mar  5 12:57:03 vendetta-laptop kernel: [    3.497379] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Mar  5 12:57:03 vendetta-laptop kernel: [    3.497382] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Mar  5 12:57:03 vendetta-laptop kernel: [    3.660573] ata1.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.60, max UDMA/33
Mar  5 12:57:03 vendetta-laptop kernel: [    3.676497] ata1.00: configured for UDMA/33
Mar  5 12:57:03 vendetta-laptop kernel: [    3.678560] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.60 PQ: 0 ANSI: 5
Mar  5 12:57:03 vendetta-laptop kernel: [    3.678768] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar  5 12:57:03 vendetta-laptop kernel: [    3.678776] ata_piix 0000:00:1f.2: MAP [ P0 P2 -- -- ]
Mar  5 12:57:03 vendetta-laptop kernel: [    3.832214] scsi2 : ata_piix
Mar  5 12:57:03 vendetta-laptop kernel: [    3.832647] scsi3 : ata_piix
Mar  5 12:57:03 vendetta-laptop kernel: [    3.833872] ata3: SATA max UDMA/133 cmd 0x18d0 ctl 0x18c4 bmdma 0x18b0 irq 19
Mar  5 12:57:03 vendetta-laptop kernel: [    3.833875] ata4: SATA max UDMA/133 cmd 0x18c8 ctl 0x18c0 bmdma 0x18b8 irq 19
Mar  5 12:57:03 vendetta-laptop kernel: [    3.988248] usb 5-6: new high speed USB device using ehci_hcd and address 2
Mar  5 12:57:03 vendetta-laptop kernel: [    3.996630] ata3.00: ATA-7: FUJITSU MHV2160BT PL, 0000004F, max UDMA/100
Mar  5 12:57:03 vendetta-laptop kernel: [    3.996636] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar  5 12:57:03 vendetta-laptop kernel: [    4.012655] ata3.00: configured for UDMA/100
Mar  5 12:57:03 vendetta-laptop kernel: [    4.180306] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHV2160B 0000 PQ: 0 ANSI: 5
Mar  5 12:57:03 vendetta-laptop kernel: [    4.181339] e100 0000:0a:08.0: enabling device (0000 -> 0003)
Mar  5 12:57:03 vendetta-laptop kernel: [    4.181351] e100 0000:0a:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar  5 12:57:03 vendetta-laptop kernel: [    4.184896] usb 5-6: configuration #1 chosen from 1 choice
Mar  5 12:57:03 vendetta-laptop kernel: [    4.208428] e100 0000:0a:08.0: PME# disabled
Mar  5 12:57:03 vendetta-laptop kernel: [    4.209871] e100: eth0: e100_probe: addr 0xd0005000, irq 20, MAC addr 00:13:a9:84:ca:c3
Mar  5 12:57:03 vendetta-laptop kernel: [    4.209903] ohci1394 0000:0a:03.1: enabling device (0000 -> 0002)
Mar  5 12:57:03 vendetta-laptop kernel: [    4.209911] ohci1394 0000:0a:03.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 12:57:03 vendetta-laptop kernel: [    4.259672] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d0006000-d00067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Mar  5 12:57:03 vendetta-laptop kernel: [    4.277401] scsi 0:0:0:0: Attached scsi generic sg0 type 5
Mar  5 12:57:03 vendetta-laptop kernel: [    4.277457] scsi 2:0:0:0: Attached scsi generic sg1 type 0
Mar  5 12:57:03 vendetta-laptop kernel: [    4.297593] Driver 'sr' needs updating - please use bus_type methods
Mar  5 12:57:03 vendetta-laptop kernel: [    4.302949] usb 5-8: new high speed USB device using ehci_hcd and address 3
Mar  5 12:57:03 vendetta-laptop kernel: [    4.303773] Driver 'sd' needs updating - please use bus_type methods
Mar  5 12:57:03 vendetta-laptop kernel: [    4.303862] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Mar  5 12:57:03 vendetta-laptop kernel: [    4.303867] Uniform CD-ROM driver Revision: 3.20
Mar  5 12:57:03 vendetta-laptop kernel: [    4.304738] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Mar  5 12:57:03 vendetta-laptop kernel: [    4.304758] sd 2:0:0:0: [sda] Write Protect is off
Mar  5 12:57:03 vendetta-laptop kernel: [    4.304791] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  5 12:57:03 vendetta-laptop kernel: [    4.304867] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Mar  5 12:57:03 vendetta-laptop kernel: [    4.304885] sd 2:0:0:0: [sda] Write Protect is off
Mar  5 12:57:03 vendetta-laptop kernel: [    4.304918] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  5 12:57:03 vendetta-laptop kernel: [    4.304922]  sda: sda1 sda2 sda3 sda4
Mar  5 12:57:03 vendetta-laptop kernel: [    4.370521] sd 2:0:0:0: [sda] Attached SCSI disk
Mar  5 12:57:03 vendetta-laptop kernel: [    4.436073] usb 5-8: configuration #1 chosen from 1 choice
Mar  5 12:57:03 vendetta-laptop kernel: [    4.446563] usbcore: registered new interface driver libusual
Mar  5 12:57:03 vendetta-laptop kernel: [    4.453386] Initializing USB Mass Storage driver...
Mar  5 12:57:03 vendetta-laptop kernel: [    4.454242] scsi4 : SCSI emulation for USB Mass Storage devices
Mar  5 12:57:03 vendetta-laptop kernel: [    4.454525] usbcore: registered new interface driver usb-storage
Mar  5 12:57:03 vendetta-laptop kernel: [    4.454529] USB Mass Storage support registered.
Mar  5 12:57:03 vendetta-laptop kernel: [    4.773791] PM: Starting manual resume from disk
Mar  5 12:57:03 vendetta-laptop kernel: [    4.797577] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar  5 12:57:03 vendetta-laptop kernel: [    4.797583] EXT3-fs: write access will be enabled during recovery.
Mar  5 12:57:03 vendetta-laptop kernel: [    8.595177] kjournald starting.  Commit interval 5 seconds
Mar  5 12:57:03 vendetta-laptop kernel: [    8.595201] EXT3-fs: sda3: orphan cleanup on readonly fs
Mar  5 12:57:03 vendetta-laptop kernel: [    8.595290] EXT3-fs: sda3: 1 orphan inode deleted
Mar  5 12:57:03 vendetta-laptop kernel: [    8.595294] EXT3-fs: recovery complete.
Mar  5 12:57:03 vendetta-laptop kernel: [    8.615917] EXT3-fs: mounted filesystem with ordered data mode.
Mar  5 12:57:03 vendetta-laptop kernel: [    9.461976] scsi 4:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.52 PQ: 0 ANSI: 0
Mar  5 12:57:03 vendetta-laptop kernel: [    9.512838] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Mar  5 12:57:03 vendetta-laptop kernel: [    9.513009] sd 4:0:0:0: Attached scsi generic sg2 type 0
Mar  5 12:57:03 vendetta-laptop kernel: [   18.414027] udevd version 124 started
Mar  5 12:57:03 vendetta-laptop kernel: [   18.947448] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  5 12:57:03 vendetta-laptop kernel: [   19.077234] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar  5 12:57:03 vendetta-laptop kernel: [   19.169213] iTCO_vendor_support: vendor-support=0
Mar  5 12:57:03 vendetta-laptop kernel: [   19.231130] ACPI: AC Adapter [ADP1] (on-line)
Mar  5 12:57:03 vendetta-laptop kernel: [   19.321180] Linux agpgart interface v0.103
Mar  5 12:57:03 vendetta-laptop kernel: [   19.341454] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Mar  5 12:57:03 vendetta-laptop kernel: [   19.341551] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Mar  5 12:57:03 vendetta-laptop kernel: [   19.341655] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Mar  5 12:57:03 vendetta-laptop kernel: [   19.506087] ACPI: Battery Slot [BAT0] (battery present)
Mar  5 12:57:03 vendetta-laptop kernel: [   19.570762] tifm_7xx1 0000:0a:03.2: enabling device (0000 -> 0002)
Mar  5 12:57:03 vendetta-laptop kernel: [   19.570772] tifm_7xx1 0000:0a:03.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar  5 12:57:03 vendetta-laptop kernel: [   19.706077] acpi device:07: registered as cooling_device2
Mar  5 12:57:03 vendetta-laptop kernel: [   19.706310] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/input/input2
Mar  5 12:57:03 vendetta-laptop kernel: [   19.736037] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Mar  5 12:57:03 vendetta-laptop kernel: [   19.796322] sony-laptop: Sony Notebook Control Driver v0.6.
Mar  5 12:57:03 vendetta-laptop kernel: [   19.797238] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2b/SNY5001:00/input/input3
Mar  5 12:57:03 vendetta-laptop kernel: [   19.816090] input: Sony Vaio Jogdial as /devices/virtual/input/input4
Mar  5 12:57:03 vendetta-laptop kernel: [   19.816276] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
Mar  5 12:57:03 vendetta-laptop kernel: [   19.823736] Yenta: CardBus bridge found at 0000:0a:03.0 [104d:81ef]
Mar  5 12:57:03 vendetta-laptop kernel: [   19.823761] Yenta: Enabling burst memory read transactions
Mar  5 12:57:03 vendetta-laptop kernel: [   19.823768] Yenta: Using CSCINT to route CSC interrupts to PCI
Mar  5 12:57:03 vendetta-laptop kernel: [   19.823770] Yenta: Routing CardBus interrupts to PCI
Mar  5 12:57:03 vendetta-laptop kernel: [   19.823777] Yenta TI: socket 0000:0a:03.0, mfunc 0x01131b22, devctl 0x64
Mar  5 12:57:03 vendetta-laptop kernel: [   19.849050] sony-laptop: detected Sony Vaio FE Series
Mar  5 12:57:03 vendetta-laptop kernel: [   19.854902] ACPI: Lid Switch [LID0]
Mar  5 12:57:03 vendetta-laptop kernel: [   19.854975] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
Mar  5 12:57:03 vendetta-laptop kernel: [   19.864862] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
Mar  5 12:57:03 vendetta-laptop kernel: [   19.865474] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Mar  5 12:57:03 vendetta-laptop kernel: [   19.904910] ACPI: Power Button (CM) [PWRB]
Mar  5 12:57:03 vendetta-laptop kernel: [   19.906929] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
Mar  5 12:57:03 vendetta-laptop kernel: [   19.940052] intel_rng: FWH not detected
Mar  5 12:57:03 vendetta-laptop kernel: [   20.056834] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
Mar  5 12:57:03 vendetta-laptop kernel: [   20.056839] Socket status: 30000006
Mar  5 12:57:03 vendetta-laptop kernel: [   20.056843] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
Mar  5 12:57:03 vendetta-laptop kernel: [   20.056852] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x6fff
Mar  5 12:57:03 vendetta-laptop kernel: [   20.056855] cs: IO port probe 0x6000-0x6fff: clean.
Mar  5 12:57:03 vendetta-laptop kernel: [   20.057163] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
Mar  5 12:57:03 vendetta-laptop kernel: [   20.057166] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
Mar  5 12:57:03 vendetta-laptop kernel: [   20.319530] Linux video capture interface: v2.00
Mar  5 12:57:03 vendetta-laptop kernel: [   20.337050] input: PC Speaker as /devices/platform/pcspkr/input/input7
Mar  5 12:57:03 vendetta-laptop kernel: [   20.458746] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1836)
Mar  5 12:57:03 vendetta-laptop kernel: [   20.459686] usbcore: registered new interface driver uvcvideo
Mar  5 12:57:03 vendetta-laptop kernel: [   20.459690] USB Video Class driver (v0.1.0)
Mar  5 12:57:03 vendetta-laptop kernel: [   20.468338] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Mar  5 12:57:03 vendetta-laptop kernel: [   20.468343] iwl3945: Copyright(c) 2003-2008 Intel Corporation
Mar  5 12:57:03 vendetta-laptop kernel: [   20.468419] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar  5 12:57:03 vendetta-laptop kernel: [   20.468457] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Mar  5 12:57:03 vendetta-laptop kernel: [   20.521053] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Mar  5 12:57:03 vendetta-laptop kernel: [   20.661120] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
Mar  5 12:57:03 vendetta-laptop kernel: [   20.716798] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
Mar  5 12:57:03 vendetta-laptop kernel: [   21.031654] iwl3945 0000:06:00.0: PCI INT A disabled
Mar  5 12:57:03 vendetta-laptop kernel: [   21.278774] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar  5 12:57:03 vendetta-laptop kernel: [   21.522765] cs: IO port probe 0x100-0x3af: clean.
Mar  5 12:57:03 vendetta-laptop kernel: [   21.524850] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Mar  5 12:57:03 vendetta-laptop kernel: [   21.525738] cs: IO port probe 0x820-0x8ff: clean.
Mar  5 12:57:03 vendetta-laptop kernel: [   21.526456] cs: IO port probe 0xc00-0xcf7: clean.
Mar  5 12:57:03 vendetta-laptop kernel: [   21.527370] cs: IO port probe 0xa00-0xaff: clean.
Mar  5 12:57:03 vendetta-laptop kernel: [   22.406769] lp: driver loaded but no devices found
Mar  5 12:57:03 vendetta-laptop kernel: [   22.614612] Adding 2939884k swap on /dev/sda4.  Priority:-1 extents:1 across:2939884k
Mar  5 12:57:03 vendetta-laptop kernel: [   23.164983] EXT3 FS on sda3, internal journal
Mar  5 12:57:03 vendetta-laptop kernel: [   24.634780] type=1505 audit(1236275821.397:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4298
Mar  5 12:57:03 vendetta-laptop kernel: [   24.702434] type=1505 audit(1236275821.465:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4303
Mar  5 12:57:03 vendetta-laptop kernel: [   24.894463] type=1505 audit(1236275821.657:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4307
Mar  5 12:57:03 vendetta-laptop kernel: [   24.894684] type=1505 audit(1236275821.657:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4307
Mar  5 12:57:03 vendetta-laptop kernel: [   25.032526] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar  5 12:57:03 vendetta-laptop kernel: [   25.747234] ACPI: WMI: Mapper loaded
Mar  5 12:57:03 vendetta-laptop kernel: [   26.824585] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar  5 12:57:03 vendetta-laptop kernel: [   26.883506] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Mar  5 12:57:03 vendetta-laptop kernel: [   26.883513] apm: disabled - APM is not SMP safe.
Mar  5 12:57:05 vendetta-laptop kernel: [   28.016114] ppdev: user-space parallel port driver
Mar  5 12:57:06 vendetta-laptop kernel: [   29.421994] sonypi: Sony Programmable I/O Controller Driver v1.26.
Mar  5 12:57:06 vendetta-laptop kernel: [   29.422972] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
Mar  5 12:57:06 vendetta-laptop kernel: [   29.423117] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
Mar  5 12:57:06 vendetta-laptop kernel: [   29.423128] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
Mar  5 12:57:06 vendetta-laptop kernel: [   29.423130] sonypi: device allocated minor is 60
Mar  5 12:57:06 vendetta-laptop kernel: [   29.423188] input: Sony Vaio Jogdial as /devices/platform/sonypi/input/input10
Mar  5 12:57:06 vendetta-laptop kernel: [   29.472166] input: Sony Vaio Keys as /devices/platform/sonypi/input/input11
Mar  5 12:57:06 vendetta-laptop kernel: [   29.543468] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
Mar  5 12:57:06 vendetta-laptop kernel: [   29.583748] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 664)
Mar  5 12:57:06 vendetta-laptop kernel: [   29.624028] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 666)
Mar  5 12:57:06 vendetta-laptop kernel: [   29.664289] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
Mar  5 12:57:08 vendetta-laptop kernel: [   31.870453] NET: Registered protocol family 10
Mar  5 12:57:08 vendetta-laptop kernel: [   31.871434] lo: Disabled Privacy Extensions
Mar  5 12:57:09 vendetta-laptop kernel: [   32.732691] Bluetooth: Core ver 2.13
Mar  5 12:57:09 vendetta-laptop kernel: [   32.734662] NET: Registered protocol family 31
Mar  5 12:57:09 vendetta-laptop kernel: [   32.734671] Bluetooth: HCI device and connection manager initialized
Mar  5 12:57:09 vendetta-laptop kernel: [   32.734677] Bluetooth: HCI socket layer initialized
Mar  5 12:57:09 vendetta-laptop kernel: [   32.769535] Bluetooth: L2CAP ver 2.11
Mar  5 12:57:09 vendetta-laptop kernel: [   32.769544] Bluetooth: L2CAP socket layer initialized
Mar  5 12:57:09 vendetta-laptop kernel: [   32.799910] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar  5 12:57:09 vendetta-laptop kernel: [   32.799920] Bluetooth: BNEP filters: protocol multicast
Mar  5 12:57:09 vendetta-laptop kernel: [   32.852604] Bridge firewalling registered
Mar  5 12:57:09 vendetta-laptop kernel: [   32.871194] Bluetooth: RFCOMM socket layer initialized
Mar  5 12:57:09 vendetta-laptop kernel: [   32.871216] Bluetooth: RFCOMM TTY layer initialized
Mar  5 12:57:09 vendetta-laptop kernel: [   32.871221] Bluetooth: RFCOMM ver 1.10
Mar  5 12:57:09 vendetta-laptop kernel: [   32.899349] Bluetooth: SCO (Voice Link) ver 0.6
Mar  5 12:57:09 vendetta-laptop kernel: [   32.899355] Bluetooth: SCO socket layer initialized
Mar  5 12:57:12 vendetta-laptop kernel: [   35.746540] [drm] Initialized drm 1.1.0 20060810
Mar  5 12:57:12 vendetta-laptop kernel: [   35.754408] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  5 12:57:12 vendetta-laptop kernel: [   35.754639] [drm] Initialized i915 1.6.0 20060119 on minor 0
Mar  5 12:57:13 vendetta-laptop kernel: [   37.051181] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar  5 12:57:13 vendetta-laptop kernel: [   37.064017] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar  5 12:57:13 vendetta-laptop kernel: [   37.067042] firmware: requesting iwlwifi-3945-1.ucode
Mar  5 12:57:13 vendetta-laptop kernel: [   37.210084] Registered led device: iwl-phy0:radio
Mar  5 12:57:13 vendetta-laptop kernel: [   37.210111] Registered led device: iwl-phy0:assoc
Mar  5 12:57:13 vendetta-laptop kernel: [   37.210134] Registered led device: iwl-phy0:RX
Mar  5 12:57:13 vendetta-laptop kernel: [   37.210153] Registered led device: iwl-phy0:TX
Mar  5 12:57:14 vendetta-laptop kernel: [   37.254023] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  5 12:57:14 vendetta-laptop kernel: [   37.320760] NET: Registered protocol family 17
Mar  5 12:57:25 vendetta-laptop pulseaudio[5894]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar  5 12:57:25 vendetta-laptop pulseaudio[5896]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar  5 12:57:25 vendetta-laptop pulseaudio[5896]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar  5 12:58:02 vendetta-laptop kernel: [   85.376342] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

It's happened twice now today. Last time was around 12:55 PM on March 5th.. Any idea what's going on? System will freeze and lights will flash on my laptop but I can't do anything but a hard reboot. Not even ALT + Sys RQ + O works..

---

### Post by Chandler258 on 2009-03-07
Maybe (re)configuring pulse audio may help.
[http://ubuntuforums.org/showthread.php?p=4928900]("http://ubuntuforums.org/showthread.php?p=4928900")

---

