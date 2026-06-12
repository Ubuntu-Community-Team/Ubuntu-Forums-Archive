---
title: "USB drive no longer detects anything"
date: 2009-04-07
forum: General Help
---

### Post by tegnoto89 on 2009-04-07
Recently my USB drive has seemingly stopped working properly.  I had been trying to get my Creative Zen player to work with it, so I thought it was a compatibility issue.  Then I tried my brother's iPod.  No luck.  SO finally I stuck in a flash drive that definitely used to work with this computer, and lo and behold, even that was not detected.  What's going on??

The odd thing is, when the mp3 players are in, they light up and charge.

---

### Post by dacorr on 2009-04-07
plug them in and from terminal type lsusb to see if the device is detected as it just may not have mounted it

---

### Post by mb_webguy on 2009-04-07
It sounds to me like your USB hub has burned out.

For a desktop, the solution is to get a [USB PCI card]("http://www.amazon.com/s/qid=1239137157/ref=sr_nr_n_0?ie=UTF8&rs=229184&keywords=usb%20card%20pci&bbn=229184&rnid=229184&rh=n%3A172282%2Cn%3A!493964%2Ck%3Ausb%20card%20pci%2Cn%3A541966%2Cn%3A172455%2Cn%3A229184%2Cn%3A229185").  You should be able to wire any front ports to the card fairly easily.

For a laptop... you're pretty much snookered as far as a permanent solution short of replacing your motherboard, since USB hubs in laptops are generally soldered onto it.  You could get a [USB PCMCIA adapter]("http://www.amazon.com/s/qid=1239137426/ref=sr_ex_n_2?ie=UTF8&rs=229185&keywords=usb%20pcmcia%20adapter&bbn=541966&rh=n%3A172282%2Cn%3A!493964%2Ck%3Ausb%20pcmcia%20adapter%2Cn%3A541966"), but then you'd have a bulky thing sticking out of the side of the laptop, which you couldn't use at the same time as a wireless PCMCIA card, if you use one.

---

### Post by tegnoto89 on 2009-04-07
> plug them in and from terminal type lsusb to see if the device is detected as it just may not have mounted it

lsusb (with Creative Zen V Plus plugged in):

```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 004: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  

```

dmesg:

```
[   23.788905] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   23.788908] Copyright (c) 1999-2006 Intel Corporation.
[   23.788962] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 17
[   23.788978] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   23.790146] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:6b:38:aa:48
[   23.811697] usbcore: registered new interface driver usbfs
[   23.811715] usbcore: registered new interface driver hub
[   23.811738] usbcore: registered new device driver usb
[   23.812566] USB Universal Host Controller Interface driver v3.0
[   23.880553] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   23.880577] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 17
[   23.880588] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   23.880592] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   23.880782] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   23.880820] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001860
[   23.880919] usb usb1: configuration #1 chosen from 1 choice
[   23.880936] hub 1-0:1.0: USB hub found
[   23.880940] hub 1-0:1.0: 2 ports detected
[   23.943770] SCSI subsystem initialized
[   23.949541] libata version 3.00 loaded.
[   23.982289] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[   23.982304] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   23.982310] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   23.982328] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   23.982365] uhci_hcd 0000:00:1a.1: irq 18, io base 0x00001880
[   23.982456] usb usb2: configuration #1 chosen from 1 choice
[   23.982475] hub 2-0:1.0: USB hub found
[   23.982479] hub 2-0:1.0: 2 ports detected
[   24.086162] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.086177] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.086181] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.086199] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   24.086235] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[   24.086328] usb usb3: configuration #1 chosen from 1 choice
[   24.086346] hub 3-0:1.0: USB hub found
[   24.086349] hub 3-0:1.0: 2 ports detected
[   24.189476] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
[   24.189489] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   24.189495] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   24.189512] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   24.189546] uhci_hcd 0000:00:1d.1: irq 21, io base 0x000018c0
[   24.189638] usb usb4: configuration #1 chosen from 1 choice
[   24.189655] hub 4-0:1.0: USB hub found
[   24.189659] hub 4-0:1.0: 2 ports detected
[   24.228333] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   24.296298] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
[   24.296307] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   24.296313] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   24.296330] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   24.296369] uhci_hcd 0000:00:1d.2: irq 22, io base 0x000018e0
[   24.296451] usb usb5: configuration #1 chosen from 1 choice
[   24.296468] hub 5-0:1.0: USB hub found
[   24.296471] hub 5-0:1.0: 2 ports detected
[   24.308033] usb 1-1: configuration #1 chosen from 1 choice
[   24.310777] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
[   24.310810] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.310826] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   24.310335] ahci 0000:00:1f.2: version 3.0
[   24.310367] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[   24.310421] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match, using nr_ports
[   24.310423] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   24.365457] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   24.370466] Clocksource tsc unstable (delta = -341709845 ns)
[   24.375990] usb 1-2: configuration #1 chosen from 1 choice
[   24.409242] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x7 impl SATA mode
[   24.409245] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   24.409252] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.409504] scsi0 : ahci
[   24.409669] scsi1 : ahci
[   24.409796] scsi2 : ahci
[   24.409846] ata1: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 217
[   24.409851] ata2: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226180 irq 217
[   24.409856] ata3: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 217
[   24.465648] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.466598] ata1.00: ATA-8: Hitachi HTS543216L9A300, FB2OC40C, max UDMA/133
[   24.466601] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   24.467257] ata1.00: configured for UDMA/133
[   24.478912] ata2: SATA link down (SStatus 0 SControl 0)
[   24.491278] ata3: SATA link down (SStatus 0 SControl 0)
[   24.492003] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[   24.492385] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 19
[   24.492401] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   24.492405] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   24.492427] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   24.496364] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   24.496372] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfe226c00
[   24.501164] Driver 'sd' needs updating - please use bus_type methods
[   24.502831] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   24.502841] sd 0:0:0:0: [sda] Write Protect is off
[   24.502842] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.502861] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.502896] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   24.502903] sd 0:0:0:0: [sda] Write Protect is off
[   24.502905] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.502916] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.502918]  sda:<6>ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.506319] usb usb6: configuration #1 chosen from 1 choice
[   24.506338] hub 6-0:1.0: USB hub found
[   24.506342] hub 6-0:1.0: 4 ports detected
[   24.522780]  sda1 sda2 < sda5 >
[   24.547557] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.550599] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.551679] usb 1-1: USB disconnect, address 2
[   24.606772] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
[   24.606788] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.606792] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.606816] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   24.610718] ehci_hcd 0000:00:1d.7: debug port 1
[   24.610724] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.610733] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe227000
[   24.626045] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.626140] usb usb7: configuration #1 chosen from 1 choice
[   24.626158] hub 7-0:1.0: USB hub found
[   24.626163] hub 7-0:1.0: 6 ports detected
[   24.668857] usb 1-2: USB disconnect, address 3
[   24.673754] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 21
[   24.673764] PCI: Setting latency timer of device 0000:15:00.1 to 64
[   24.726387] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   24.735006] ata_piix 0000:00:1f.1: version 2.12
[   24.735025] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
[   24.735064] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.735175] scsi3 : ata_piix
[   24.735232] scsi4 : ata_piix
[   24.735852] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1830 irq 14
[   24.735854] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1838 irq 15
[   24.747732] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-U10N, 1.05, max UDMA/33
[   24.753187] ata4.00: configured for UDMA/33
[   24.753310] ata5: port disabled. ignoring.
[   24.755093] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-U10N  1.05 PQ: 0 ANSI: 5
[   24.755157] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   24.762418] Driver 'sr' needs updating - please use bus_type methods
[   24.765060] sr0: scsi3-mmc drive: 47x/47x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.765062] Uniform CD-ROM driver Revision: 3.20
[   24.765098] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   24.811982] Attempting manual resume
[   24.811985] swsusp: Resume From Partition 8:5
[   24.811986] PM: Checking swsusp image.
[   24.811609] PM: Resume from disk failed.
[   24.850573] kjournald starting.  Commit interval 5 seconds
[   24.850581] EXT3-fs: mounted filesystem with ordered data mode.
[   24.967972] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   25.132098] usb 1-1: configuration #1 chosen from 1 choice
[   25.371410] usb 1-2: new full speed USB device using uhci_hcd and address 5
[   25.499614] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b032a118cde]
[   25.544996] usb 1-2: configuration #1 chosen from 1 choice
[   31.676372] Linux agpgart interface v0.102
[   31.770821] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.937540] iTCO_vendor_support: vendor-support=0
[   32.025429] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.106671] input: Power Button (FF) as /devices/virtual/input/input2
[   32.136718] ACPI: Power Button (FF) [PWRF]
[   32.136775] input: Lid Switch as /devices/virtual/input/input3
[   32.136889] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   32.136959] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   32.136995] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   32.137340] ACPI: Lid Switch [LID]
[   32.137382] input: Sleep Button (CM) as /devices/virtual/input/input4
[   32.168635] ACPI: Sleep Button (CM) [SLPB]
[   32.302006] ricoh-mmc: Ricoh MMC Controller disabling driver
[   32.302009] ricoh-mmc: Copyright(c) Philip Langdale
[   32.302045] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   32.302062] ricoh-mmc: Controller is now disabled.
[   32.354134] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   32.457498] ACPI: WMI-Acer: Mapper loaded
[   32.482599] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   32.482605] Socket status: 30000006
[   32.482608] pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
[   32.482610] cs: IO port probe 0x8000-0xbfff: clean.
[   32.483464] pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
[   32.483466] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   32.544530] sdhci: Secure Digital Host Controller Interface driver
[   32.544532] sdhci: Copyright(c) Pierre Ossman
[   32.544565] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 21)
[   32.544620] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 22
[   32.544632] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   32.544641] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   32.544677] mmc0: SDHCI at 0xf8101800 irq 22 DMA
[   32.596712] ACPI: Battery Slot [BAT0] (battery present)
[   32.597718] ACPI: AC Adapter [AC] (on-line)
[   32.617859] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   32.653924] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   32.671925] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   32.673576] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   32.704057] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   32.848461] Non-volatile memory driver v1.2
[   33.110335] Bluetooth: Core ver 2.11
[   33.110588] NET: Registered protocol family 31
[   33.110590] Bluetooth: HCI device and connection manager initialized
[   33.110593] Bluetooth: HCI socket layer initialized
[   33.244049] nvidia: module license 'NVIDIA' taints kernel.
[   33.519377] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.519387] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   33.519483] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   33.561245] Bluetooth: HCI USB driver ver 2.9
[   33.570103] usbcore: registered new interface driver hci_usb
[   33.578251] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   33.578253] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   33.578381] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   33.578413] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   33.578442] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   33.735629] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   33.735634] serio: Synaptics pass-through port at isa0060/serio1/input0
[   33.775965] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   33.830041] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   33.830043] thinkpad_acpi: http://ibm-acpi.sf.net/
[   33.830045] thinkpad_acpi: ThinkPad BIOS 7LET44WW (1.14 ), EC 7KHT22WW-1.06
[   33.830046] thinkpad_acpi: Lenovo ThinkPad T61
[   33.830536] thinkpad_acpi: radio switch found; radios are enabled
[   33.835775] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   33.836025] input: ThinkPad Extra Buttons as /devices/virtual/input/input9
[   33.852861] cs: IO port probe 0x100-0x3af: clean.
[   33.854812] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   33.855589] cs: IO port probe 0x820-0x8ff: clean.
[   33.856223] cs: IO port probe 0xc00-0xcf7: clean.
[   33.856999] cs: IO port probe 0xa00-0xaff: clean.
[   33.922862] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   33.923150] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   33.940051] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   33.940056] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   33.940071] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   34.296424] lp: driver loaded but no devices found
[   34.372926] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k
[   34.807696] EXT3 FS on sda1, internal journal
[   35.461265] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.914319] ACPI: ACPI Dock Station Driver 
[   35.948948] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   35.948953] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   35.948978] ACPI: Error installing bay notify handler
[   35.948981] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   36.871559] apm: BIOS not found.
[   37.011235] ppdev: user-space parallel port driver
[   37.161938] audit(1239116788.623:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5336 profile="/usr/sbin/cupsd" namespace="default"
[   37.284940] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input10
[   38.290800] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   38.514267] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input11
[   39.502024] Bluetooth: L2CAP ver 2.9
[   39.502031] Bluetooth: L2CAP socket layer initialized
[   39.715791] Bluetooth: RFCOMM socket layer initialized
[   39.715812] Bluetooth: RFCOMM TTY layer initialized
[   39.715816] Bluetooth: RFCOMM ver 1.8
[   54.213722] NET: Registered protocol family 10
[   54.214219] lo: Disabled Privacy Extensions
[   54.215124] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.216092] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.958271] CPU0 attaching NULL sched-domain.
[   63.958281] CPU1 attaching NULL sched-domain.
[   63.981714] CPU0 attaching sched-domain:
[   63.981724]  domain 0: span 03
[   63.981728]   groups: 01 02
[   63.981735] CPU1 attaching sched-domain:
[   63.981739]  domain 0: span 03
[   63.981743]   groups: 02 01
[   64.538797] UDF-fs: Partition marked readonly; forcing readonly mount
[   64.599626] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'CREAM_FAREWELL_CONCERT', timestamp 2005/08/09 17:17 (1f10)
[   65.819324] NET: Registered protocol family 17
[   69.458056] wlan0: Initial auth_alg=0
[   69.458062] wlan0: authenticate with AP 00:17:df:2f:be:f0
[   69.460828] wlan0: Initial auth_alg=0
[   69.460831] wlan0: authenticate with AP 00:17:df:2f:be:f1
[   69.462924] wlan0: RX authentication from 00:17:df:2f:be:f1 (alg=0 transaction=2 status=0)
[   69.462928] wlan0: authenticated
[   69.462930] wlan0: associate with AP 00:17:df:2f:be:f1
[   69.466936] wlan0: Initial auth_alg=0
[   69.466940] wlan0: authenticate with AP 00:17:df:2f:be:f1
[   69.466950] wlan0: association frame received from 00:17:df:2f:be:f1, but not in associate state - ignored
[   69.469528] wlan0: RX authentication from 00:17:df:2f:be:f1 (alg=0 transaction=2 status=0)
[   69.469531] wlan0: authenticated
[   69.469534] wlan0: associate with AP 00:17:df:2f:be:f1
[   69.665804] wlan0: associate with AP 00:17:df:2f:be:f1
[   69.673547] wlan0: RX AssocResp from 00:17:df:2f:be:f1 (capab=0x431 status=0 aid=2)
[   69.673550] wlan0: associated
[   69.675191] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   80.191169] wlan0: no IPv6 routers present
[  121.237672] wlan0: no IPv6 routers present
[  648.625134] irq 23: nobody cared (try booting with the "irqpoll" option)
[  648.625142] Pid: 0, comm: swapper Tainted: P        2.6.24-23-generic #1
[  648.625162]  [<c0169234>] __report_bad_irq+0x24/0x80
[  648.625173]  [<c016950b>] note_interrupt+0x27b/0x2c0
[  648.625180]  [<f8893ccb>] usb_hcd_irq+0x2b/0x60 [usbcore]
[  648.625209]  [<c0168730>] handle_IRQ_event+0x30/0x60
[  648.625216]  [<c0169ec6>] handle_fasteoi_irq+0x86/0xe0
[  648.625222]  [<c0106f0b>] do_IRQ+0x3b/0x70
[  648.625226]  [<c014969b>] tick_notify+0x25b/0x390
[  648.625230]  [<c0105403>] common_interrupt+0x23/0x30
[  648.625237]  [<c031cc9d>] _spin_unlock_irqrestore+0xd/0x20
[  648.625243]  [<c024836b>] acpi_get_register+0x2a/0x30
[  648.625251]  [<f8887236>] acpi_idle_enter_bm+0x51/0x2ce [processor]
[  648.625259]  [<c02964d4>] menu_select+0x84/0xa0
[  648.625266]  [<c029585c>] cpuidle_idle_call+0x7c/0xb0
[  648.625270]  [<c0102695>] cpu_idle+0x45/0xd0
[  648.625274]  [<c0423a5f>] start_kernel+0x31f/0x3b0
[  648.625279]  [<c0423130>] unknown_bootoption+0x0/0x1e0
[  648.625285]  =======================
[  648.625286] handlers:
[  648.625288] [<f8893ca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  648.625300] Disabling IRQ #23
[16336.173963] CPU0 attaching NULL sched-domain.
[16336.173967] CPU1 attaching NULL sched-domain.
[16336.196458] CPU0 attaching sched-domain:
[16336.196462]  domain 0: span 03
[16336.196463]   groups: 01 02
[16336.196466]   domain 1: span 03
[16336.196467]    groups: 03
[16336.196469] CPU1 attaching sched-domain:
[16336.196471]  domain 0: span 03
[16336.196472]   groups: 02 01
[16336.196474]   domain 1: span 03
[16336.196475]    groups: 03
[16337.160398] Monitor-Mwait will be used to enter C-3 state
[16824.138315] CPU0 attaching NULL sched-domain.
[16824.138326] CPU1 attaching NULL sched-domain.
[16824.159638] CPU0 attaching sched-domain:
[16824.159647]  domain 0: span 03
[16824.159651]   groups: 01 02
[16824.159658] CPU1 attaching sched-domain:
[16824.159662]  domain 0: span 03
[16824.159666]   groups: 02 01
[19546.472247] wlan0: RX deauthentication from 00:17:df:2f:be:f1 (reason=1)
[19546.472252] wlan0: deauthenticated
[19547.468619] wlan0: authenticate with AP 00:17:df:2f:be:f1
[19547.471014] wlan0: RX authentication from 00:17:df:2f:be:f1 (alg=0 transaction=2 status=0)
[19547.471020] wlan0: authenticated
[19547.471023] wlan0: associate with AP 00:17:df:2f:be:f1
[19547.480306] wlan0: RX ReassocResp from 00:17:df:2f:be:f1 (capab=0x431 status=0 aid=2)
[19547.480312] wlan0: associated
[19557.607830] wlan0: Initial auth_alg=0
[19557.607842] wlan0: authenticate with AP 00:17:df:2f:c0:c1
[19557.610946] wlan0: Initial auth_alg=0
[19557.610952] wlan0: authenticate with AP 00:17:df:2f:c0:c1
[19557.610964] wlan0: RX authentication from 00:17:df:2f:c0:c1 (alg=0 transaction=2 status=0)
[19557.610967] wlan0: authenticated
[19557.610970] wlan0: associate with AP 00:17:df:2f:c0:c1
[19557.610982] wlan0: authentication frame received from 00:17:df:2f:c0:c1, but not in authenticate state - ignored
[19557.613658] wlan0: authentication frame received from 00:17:df:2f:c0:c1, but not in authenticate state - ignored
[19557.614728] wlan0: RX ReassocResp from 00:17:df:2f:c0:c1 (capab=0x431 status=0 aid=3)
[19557.614734] wlan0: associated
[19557.614808] wlan0: No ProbeResp from current AP 00:17:df:2f:c0:c1 - assume out of range
[19560.731324] wlan0: Initial auth_alg=0
[19560.731335] wlan0: authenticate with AP 00:17:df:2f:c0:c1
[19560.735304] wlan0: Initial auth_alg=0
[19560.735310] wlan0: authenticate with AP 00:17:df:2f:c0:c1
[19560.735325] wlan0: RX authentication from 00:17:df:2f:c0:c1 (alg=0 transaction=2 status=0)
[19560.735328] wlan0: authenticated
[19560.735331] wlan0: associate with AP 00:17:df:2f:c0:c1
[19560.735344] wlan0: authentication frame received from 00:17:df:2f:c0:c1, but not in authenticate state - ignored
[19560.736502] wlan0: authentication frame received from 00:17:df:2f:c0:c1, but not in authenticate state - ignored
[19560.739614] wlan0: RX ReassocResp from 00:17:df:2f:c0:c1 (capab=0x431 status=0 aid=3)
[19560.739618] wlan0: associated
[19567.448317] wlan0: deauthenticate(reason=3)
[19572.503164] wlan0: Initial auth_alg=0
[19572.503172] wlan0: authenticate with AP 00:17:df:2f:c0:c1
[19572.505929] wlan0: Initial auth_alg=0
[19572.505934] wlan0: authenticate with AP 00:17:df:2f:c0:c1
[19572.513366] wlan0: Initial auth_alg=0
[19572.513373] wlan0: authenticate with AP 00:17:df:2f:be:fe
[19572.515830] wlan0: Initial auth_alg=0
[19572.515836] wlan0: authenticate with AP 00:17:df:2f:be:fe
[19572.713553] wlan0: authenticate with AP 00:17:df:2f:be:fe
[19572.714249] wlan0: RX authentication from 00:17:df:2f:be:fe (alg=0 transaction=2 status=0)
[19572.714253] wlan0: authenticated
[19572.714254] wlan0: associate with AP 00:17:df:2f:be:fe
[19572.716099] wlan0: RX AssocResp from 00:17:df:2f:be:fe (capab=0x11 status=0 aid=2)
[19572.716103] wlan0: associated
[19572.717855] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[19583.466598] wlan0: no IPv6 routers present
[19621.433806] wlan0: no IPv6 routers present
[32202.466056] wlan0: RX deauthentication from 00:17:df:2f:be:fe (reason=1)
[32202.466066] wlan0: deauthenticated
[32203.462110] wlan0: authenticate with AP 00:17:df:2f:be:fe
[32203.462917] wlan0: RX authentication from 00:17:df:2f:be:fe (alg=0 transaction=2 status=0)
[32203.462926] wlan0: authenticated
[32203.462931] wlan0: associate with AP 00:17:df:2f:be:fe
[32203.468609] wlan0: RX ReassocResp from 00:17:df:2f:be:fe (capab=0x11 status=0 aid=2)
[32203.468617] wlan0: associated
[32213.385760] wlan0: Initial auth_alg=0
[32213.385767] wlan0: authenticate with AP 00:17:df:2f:7b:d1
[32213.388219] wlan0: Initial auth_alg=0
[32213.388222] wlan0: authenticate with AP 00:17:df:2f:7b:d1
[32213.388229] wlan0: RX authentication from 00:17:df:2f:7b:d1 (alg=0 transaction=2 status=0)
[32213.388231] wlan0: authenticated
[32213.388233] wlan0: associate with AP 00:17:df:2f:7b:d1
[32213.388240] wlan0: authentication frame received from 00:17:df:2f:7b:d1, but not in authenticate state - ignored
[32213.390786] wlan0: authentication frame received from 00:17:df:2f:7b:d1, but not in authenticate state - ignored
[32213.398236] wlan0: RX ReassocResp from 00:17:df:2f:7b:d1 (capab=0x431 status=0 aid=19)
[32213.398239] wlan0: associated
[34175.447318] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[34194.980625] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[34266.667806] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[34285.894190] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[34829.944079] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[34837.818491] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[34993.977871] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[35013.714747] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[35632.725996] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[35652.670145] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[35847.584284] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[35867.321994] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[35888.081818] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[35907.205359] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[36015.912683] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[36035.036789] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[36332.832287] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[36352.569449] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[36430.496009] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[36450.336295] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[37010.237208] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[37029.462290] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[37355.586325] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[37374.914401] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[37871.002524] wlan0: CTS protection enabled (BSSID=00:17:df:2f:7b:d1)
[37890.330085] wlan0: CTS protection disabled (BSSID=00:17:df:2f:7b:d1)
[37960.342390] usb 7-2: new high speed USB device using ehci_hcd and address 2
[37965.335443] ehci_hcd 0000:00:1d.7: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[37975.878322] usb 7-2: device not accepting address 2, error -110
[37975.988642] usb 7-2: new high speed USB device using ehci_hcd and address 3
[37991.523074] usb 7-2: device not accepting address 3, error -110
[37991.634890] usb 7-2: new high speed USB device using ehci_hcd and address 4
[38002.052950] usb 7-2: device not accepting address 4, error -110
[38002.165795] usb 7-2: new high speed USB device using ehci_hcd and address 5
[38012.584172] usb 7-2: device not accepting address 5, error -110

```

Do those errors at the bottom mean anything?

> For a laptop... you're pretty much snookered as far as a permanent solution short of replacing your motherboard, since USB hubs in laptops are generally soldered onto it. You could get a USB PCMCIA adapter, but then you'd have a bulky thing sticking out of the side of the laptop, which you couldn't use at the same time as a wireless PCMCIA card, if you use one.

Grrrr.  Is there any possibility it's more to do with the OS than the hardware?

---

### Post by tegnoto89 on 2009-04-10
Bump

---

### Post by tegnoto89 on 2009-04-14
Solved...  USB was disabled in BIOS.  Thanks for the responses.

---

