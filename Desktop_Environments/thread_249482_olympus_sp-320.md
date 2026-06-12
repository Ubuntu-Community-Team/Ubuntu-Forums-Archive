---
title: "olympus sp-320"
date: 2006-09-02
forum: Desktop Environments
---

### Post by kepos on 2006-09-02
hy! i have digital camera mentioned in title, and i don't know how to transfer images from her. is there any program for that? any idea?

i was thinking about buying card reader but it's expensive.

---

### Post by Crooksey on 2006-09-02
Plug it in, then type "dmesg", is your camera mounted, or given a location?

Say the location is /dev/sda4

mkdir /mnt/camera
mount /dev/sda4/ /mnt/camera

---

### Post by kepos on 2006-09-03
> **Crooksey said:**
> Plug it in, then type "dmesg", is your camera mounted, or given a location?

when i plug in my camera i have to chose which mode do i want to use. i have 'pc','easy print' and 'custom print'. for last two when i plug it in, it says camera detected(camera1.png) and after that it displays error message(easyprint.png).
when i chose 'pc' mode, sometimes it displays camera1.png message, sometime nothing. but in any case i'm unable to transfer images form camera, and there is no any dev/sda so i can mount it as removable drive :(

output of dmesg is too large, but here is it:

```
[   30.955491] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   30.955720] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   30.955968] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   30.956279] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   30.956464] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   30.956635] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   30.956817] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   30.956872] PCI: Probing PCI hardware
[   30.956890] PCI: Probing PCI hardware (bus 00)
[   30.957277] Uncovering SIS18 that hid as a SIS503 (compatible=0)
[   30.957288] Enabling SiS 96x SMBus.
[   30.958335] Boot video device is 0000:01:00.0
[   30.960499] PCI: Using IRQ router SIS [1039/0018] at 0000:00:02.0
[   30.960543] PCI: IRQ 0 for device 0000:00:02.1 doesn't match PIRQ mask - try pci=usepirqmask
[   30.960555] PCI: Found IRQ 11 for device 0000:00:02.1
[   30.960576] PCI: Sharing IRQ 11 with 0000:00:09.0
[   30.960590] PCI: Sharing IRQ 11 with 0000:00:0b.0
[   30.965090] PCI: Bridge: 0000:00:01.0
[   30.965103]   IO window: disabled.
[   30.965117]   MEM window: fdc00000-ffcfffff
[   30.965127]   PREFETCH window: eda00000-fdafffff
[   30.966907] audit: initializing netlink socket (disabled)
[   30.966948] audit(1157281400.444:1): initialized
[   30.967381] VFS: Disk quotas dquot_6.5.1
[   30.967469] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.967663] Initializing Cryptographic API
[   30.967681] io scheduler noop registered
[   30.967704] io scheduler anticipatory registered
[   30.967718] io scheduler deadline registered
[   30.967750] io scheduler cfq registered
[   30.968629] isapnp: Scanning for PnP cards...
[   31.325302] isapnp: No Plug & Play device found
[   31.406347] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   31.410540] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[   31.410554] If AUX port is really absent please use the 'i8042.noaux' option.[   31.417068] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.418333] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.418475] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   31.418803] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.419218] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.431367] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.432169] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.434329] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.434527] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.434544] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.435149] mice: PS/2 mouse device common for all mice
[   31.439402] EISA: Probing bus 0 at eisa.0
[   31.439466] EISA: Detected 0 cards.
[   31.439614] NET: Registered protocol family 2
[   31.452912] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   31.455799] TCP established hash table entries: 16384 (order: 4, 65536 bytes)[   31.456133] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   31.456649] TCP: Hash tables configured (established 16384 bind 16384)
[   31.459731] TCP reno registered
[   31.460120] TCP bic registered
[   31.460177] NET: Registered protocol family 1
[   31.460206] NET: Registered protocol family 8
[   31.460213] NET: Registered protocol family 20
[   31.460285] Using IPI Shortcut mode
[   31.460411] Freeing unused kernel memory: 288k freed
[   31.469293] input: AT Translated Set 2 keyboard as /class/input/input0
[   31.677494] vga16fb: initializing
[   31.677518] vga16fb: mapped to 0xc00a0000
[   31.812975] Console: switching to colour frame buffer device 80x25
[   31.813011] fb0: VGA16 VGA frame buffer device
[   32.973245] Capability LSM initialized
[   35.439188] SIS5513: IDE controller at PCI slot 0000:00:02.5
[   35.439243] SIS5513: chipset revision 208
[   35.439251] SIS5513: not 100% native mode: will probe irqs later
[   35.439270] SIS5513: SiS635 ATA 100 (2nd gen) controller
[   35.439346]     ide0: BM-DMA at 0x45e0-0x45e7, BIOS settings: hda:DMA, hdb:DMA
[   35.439383]     ide1: BM-DMA at 0x45e8-0x45ef, BIOS settings: hdc:DMA, hdd:DMA
[   35.439420] Probing IDE interface ide0...
[   35.702841] hda: Maxtor 6E030L0, ATA DISK drive
[   35.957647] hdb: Maxtor 6E040L0, ATA DISK drive
[   36.008921] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   36.009949] Probing IDE interface ide1...
[   36.681190] hdc: TSSTcorpCD/DVDW TS-H552B, ATAPI CD/DVD-ROM drive
[   37.394687] hdd: HL-DT-ST GCE-8525B, ATAPI CD/DVD-ROM drive
[   37.445883] ide1 at 0x170-0x177,0x376 on irq 15
[   37.473953] hda: max request size: 128KiB
[   37.530687] hda: 60058656 sectors (30750 MB) w/2048KiB Cache, CHS=59582/16/63, UDMA(100)
[   37.531034] hda: cache flushes supported
[   37.531682]  hda: hda1
[   37.534596] hdb: max request size: 128KiB
[   37.544618] hdb: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   37.544786] hdb: cache flushes supported
[   37.545380]  hdb: hdb1 hdb2 < hdb5 >
[   37.594643] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   37.594680] Uniform CD-ROM driver Revision: 3.20
[   37.598336] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   38.299294] usbcore: registered new driver usbfs
[   38.300843] usbcore: registered new driver hub
[   38.308035] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   38.309461] PCI: Found IRQ 5 for device 0000:00:02.2
[   38.309492] PCI: Sharing IRQ 5 with 0000:00:02.3
[   38.309507] PCI: Sharing IRQ 5 with 0000:00:09.2
[   38.309567] ohci_hcd 0000:00:02.2: OHCI Host Controller
[   38.902431] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[   38.902497] ohci_hcd 0000:00:02.2: irq 5, io mem 0xffdfe000
[   38.956861] hub 1-0:1.0: USB hub found
[   38.956917] hub 1-0:1.0: 3 ports detected
[   39.058117] PCI: Found IRQ 5 for device 0000:00:02.3
[   39.058145] PCI: Sharing IRQ 5 with 0000:00:02.2
[   39.058158] PCI: Sharing IRQ 5 with 0000:00:09.2
[   39.058214] ohci_hcd 0000:00:02.3: OHCI Host Controller
[   39.574493] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[   39.574527] ohci_hcd 0000:00:02.3: irq 5, io mem 0xffdff000
[   39.628142] hub 2-0:1.0: USB hub found
[   39.628198] hub 2-0:1.0: 3 ports detected
[   39.729516] PCI: Found IRQ 11 for device 0000:00:09.0
[   39.729540] PCI: Sharing IRQ 11 with 0000:00:02.1
[   39.729564] PCI: Sharing IRQ 11 with 0000:00:0b.0
[   39.729609] ohci_hcd 0000:00:09.0: OHCI Host Controller
[   39.730175] ohci_hcd 0000:00:09.0: new USB bus registered, assigned bus number 3
[   39.730211] ohci_hcd 0000:00:09.0: irq 11, io mem 0xffdfa000
[   39.783940] hub 3-0:1.0: USB hub found
[   39.783996] hub 3-0:1.0: 2 ports detected
[   39.885456] PCI: Found IRQ 11 for device 0000:00:09.1
[   39.885489] PCI: Sharing IRQ 11 with 0000:00:02.7
[   39.885508] PCI: Sharing IRQ 11 with 0000:00:0d.0
[   39.885551] ohci_hcd 0000:00:09.1: OHCI Host Controller
[   39.886106] ohci_hcd 0000:00:09.1: new USB bus registered, assigned bus number 4
[   39.886139] ohci_hcd 0000:00:09.1: irq 11, io mem 0xffdfb000
[   39.939919] hub 4-0:1.0: USB hub found
[   39.939975] hub 4-0:1.0: 2 ports detected
[   40.041376] PCI: Found IRQ 5 for device 0000:00:09.2
[   40.041402] PCI: Sharing IRQ 5 with 0000:00:02.3
[   40.041411] PCI: Sharing IRQ 5 with 0000:00:02.2
[   40.041472] ohci_hcd 0000:00:09.2: OHCI Host Controller
[   40.042030] ohci_hcd 0000:00:09.2: new USB bus registered, assigned bus number 5
[   40.042063] ohci_hcd 0000:00:09.2: irq 5, io mem 0xffdfc000
[   40.095779] hub 5-0:1.0: USB hub found
[   40.095839] hub 5-0:1.0: 2 ports detected
[   40.211453] PCI: Found IRQ 11 for device 0000:00:09.3
[   40.211600] ehci_hcd 0000:00:09.3: EHCI Host Controller
[   40.211716] ehci_hcd 0000:00:09.3: debug port 1
[   40.232767] ehci_hcd 0000:00:09.3: new USB bus registered, assigned bus number 6
[   40.232805] ehci_hcd 0000:00:09.3: irq 11, io mem 0xffdfdf00
[   40.232829] ehci_hcd 0000:00:09.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   40.233099] hub 6-0:1.0: USB hub found
[   40.233143] hub 6-0:1.0: 6 ports detected
[   40.257578] usb 4-1: new low speed USB device using ohci_hcd and address 2
[   40.620409] Attempting manual resume
[   40.678374] EXT3-fs: mounted filesystem with ordered data mode.
[   40.708190] kjournald starting.  Commit interval 5 seconds
[   41.057005] usb 4-1: new low speed USB device using ohci_hcd and address 3
[   41.460723] usb 5-1: new full speed USB device using ohci_hcd and address 2
[   59.059177] Linux agpgart interface v0.101 (c) Dave Jones
[   59.065039] agpgart: Detected SiS 635 chipset
[   59.072036] agpgart: AGP aperture is 64M @ 0xe0000000
[   59.445834] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   59.464217] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   59.475747] i2c-sis96x version 1.0.0
[   59.475865] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   59.482344] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[   60.618671] nvidia: module license 'NVIDIA' taints kernel.
[   60.644725] PCI: No IRQ known for interrupt pin A of device 0000:01:00.0. Please try using pci=biosirq.
[   60.644750] NVRM: Can't find an IRQ for your NVIDIA card!
[   60.644757] NVRM: Please check your BIOS settings.
[   60.644764] NVRM: [Plug & Play OS] should be set to NO
[   60.644771] NVRM: [Assign IRQ to VGA] should be set to YES
[   60.644781] nvidia: probe of 0000:01:00.0 failed with error -1
[   60.644804] NVRM: The NVIDIA probe routine failed for 1 device(s).
[   60.644945] NVRM: None of the NVIDIA graphics adapters were initialized!
[   60.840560] PCI: No IRQ known for interrupt pin A of device 0000:01:00.0. Please try using pci=biosirq.
[   60.840582] NVRM: Can't find an IRQ for your NVIDIA card!
[   60.840589] NVRM: Please check your BIOS settings.
[   60.840596] NVRM: [Plug & Play OS] should be set to NO
[   60.840603] NVRM: [Assign IRQ to VGA] should be set to YES
[   60.840618] nvidia: probe of 0000:01:00.0 failed with error -1
[   60.840642] NVRM: The NVIDIA probe routine failed for 1 device(s).
[   60.840780] NVRM: None of the NVIDIA graphics adapters were initialized!
[   60.921260] PCI: Found IRQ 11 for device 0000:00:02.7
[   60.921298] PCI: Sharing IRQ 11 with 0000:00:09.1
[   60.921314] PCI: Sharing IRQ 11 with 0000:00:0d.0
[   60.939263] 8139too Fast Ethernet driver 0.9.27
[   61.229765] intel8x0_measure_ac97_clock: measured 50422 usecs
[   61.229782] intel8x0: clocking to 48000
[   61.233376] PCI: Found IRQ 11 for device 0000:00:0b.0
[   61.233403] PCI: Sharing IRQ 11 with 0000:00:02.1
[   61.233425] PCI: Sharing IRQ 11 with 0000:00:09.0
[   61.234027] eth0: RealTek RTL8139 at 0xd0880e00, 4c:00:10:51:de:66, IRQ 11
[   61.234039] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   61.234093] PCI: Found IRQ 11 for device 0000:00:0d.0
[   61.234115] PCI: Sharing IRQ 11 with 0000:00:02.7
[   61.234125] PCI: Sharing IRQ 11 with 0000:00:09.1
[   61.234588] eth1: RealTek RTL8139 at 0xd0940d00, 4c:00:10:51:da:ab, IRQ 11
[   61.234599] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[   61.289810] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   61.576701] input: ImPS/2 Generic Wheel Mouse as /class/input/input1
[   62.762735] Real Time Clock Driver v1.12
[   62.780481] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7204
[   62.784942] usbcore: registered new driver usblp
[   62.784960] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver[   62.977770] Floppy drive(s): fd0 is 1.44M
[   62.993473] FDC 0 is a post-1991 82077
[   63.225835] usbcore: registered new driver hiddev
[   63.248668] input: A4Tech USB Optical Mouse as /class/input/input2
[   63.248877] input: USB HID v1.10 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:09.1-1
[   63.248921] usbcore: registered new driver usbhid
[   63.248930] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   63.792861] input: PC Speaker as /class/input/input3
[   63.813410] parport: PnPBIOS parport detected.
[   63.813488] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   64.510929] ts: Compaq touchscreen protocol output
[   64.869494] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   66.155136] NET: Registered protocol family 17
[   67.825778] lp0: using parport0 (interrupt-driven).
[   68.043047] Adding 746980k swap on /dev/hdb5.  Priority:-1 extents:1 across:746980k
[   68.268733] EXT3 FS on hdb1, internal journal
[   68.753997] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   68.754015] md: bitmap version 4.39
[   70.181632] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   70.722689] cdrom: open failed.
[   71.262733] cdrom: open failed.
[   71.264845] cdrom: open failed.
[   72.070752] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   88.377306] ppdev: user-space parallel port driver
[   88.875618] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   98.581005] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[   98.581033] hdc: drive_cmd: error=0x04 { AbortedCommand }
[   98.581042] ide: failed opcode was: 0xec
[   98.696997] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[   98.697023] hdd: drive_cmd: error=0x04 { AbortedCommand }
[   98.697032] ide: failed opcode was: 0xec
[  104.481950] Bluetooth: Core ver 2.8
[  104.481978] NET: Registered protocol family 31
[  104.481985] Bluetooth: HCI device and connection manager initialized
[  104.482022] Bluetooth: HCI socket layer initialized
[  104.530287] Bluetooth: L2CAP ver 2.8
[  104.530314] Bluetooth: L2CAP socket layer initialized
[  104.604870] Bluetooth: RFCOMM socket layer initialized
[  104.604945] Bluetooth: RFCOMM TTY layer initialized
[  104.604952] Bluetooth: RFCOMM ver 1.7
[  110.945549] NET: Registered protocol family 10
[  110.946055] lo: Disabled Privacy Extensions
[  110.946534] IPv6 over IPv4 tunneling driver
[  121.863039] eth0: no IPv6 routers present
[  163.952415] usb 6-4: new high speed USB device using ehci_hcd and address 4
[  164.075166] usb 6-4: unable to read config index 0 descriptor/all
[  164.075189] usb 6-4: can't read configurations, error -71
[  164.178256] usb 6-4: new high speed USB device using ehci_hcd and address 5
[  164.296965] usb 6-4: unable to read config index 0 descriptor/start
[  164.296989] usb 6-4: can't read configurations, error -71
[  164.400099] usb 6-4: new high speed USB device using ehci_hcd and address 6
[  164.838134] SCSI subsystem initialized
[  164.866670] Initializing USB Mass Storage driver...
[  164.869096] scsi0 : SCSI emulation for USB Mass Storage devices
[  164.870373] usb-storage: device found at 6
[  164.870390] usb-storage: waiting for device to settle before scanning
[  164.870832] usbcore: registered new driver usb-storage
[  164.870844] USB Mass Storage support registered.
[  169.869349]   Vendor: OLYMPUS   Model: SP320             Rev: 1.00
[  169.869385]   Type:   Direct-Access                      ANSI SCSI revision: 02
[  169.876894] usb-storage: device scan complete
[  169.999287] Driver 'sd' needs updating - please use bus_type methods
[  170.007219] SCSI device sda: 1023120 512-byte hdwr sectors (524 MB)
[  170.012179] sda: Write Protect is off
[  170.012367] sda: Mode Sense: 18 00 00 08
[  170.012377] sda: assuming drive cache: write through
[  170.023227] SCSI device sda: 1023120 512-byte hdwr sectors (524 MB)
[  170.028175] sda: Write Protect is off
[  170.028372] sda: Mode Sense: 18 00 00 08
[  170.028383] sda: assuming drive cache: write through
[  170.028397]  sda:<6>usb 6-4: reset high speed USB device using ehci_hcd and address 6
[  170.283957] usb 6-4: device descriptor read/64, error -71
[  170.495807] usb 6-4: device descriptor read/64, error -71
[  170.698669] usb 6-4: reset high speed USB device using ehci_hcd and address 6[  170.815581] usb 6-4: device descriptor read/64, error -71
[  171.029423] usb 6-4: device descriptor read/64, error -71
[  171.232317] usb 6-4: reset high speed USB device using ehci_hcd and address 6[  171.244847] usb 6-4: device descriptor read/8, error -71
[  171.356799] usb 6-4: device descriptor read/8, error -71
[  171.559106] usb 6-4: reset high speed USB device using ehci_hcd and address 6[  171.573585] usb 6-4: device descriptor read/8, error -71
[  171.689523] usb 6-4: device descriptor read/8, error -71
[  171.789978] usb 6-4: USB disconnect, address 6
[  171.790938] sd 0:0:0:0: SCSI error: return code = 0x10000
[  171.790952] end_request: I/O error, dev sda, sector 0
[  171.790966] Buffer I/O error on device sda, logical block 0
[  171.791676] sd 0:0:0:0: rejecting I/O to device being removed
[  171.791690] Buffer I/O error on device sda, logical block 0
[  171.791704]  unable to read partition table
[  171.792375] sd 0:0:0:0: Attached scsi removable disk sda
[  171.894837] usb 6-4: new high speed USB device using ehci_hcd and address 7
[  172.026768] usb 6-4: device descriptor read/64, error -71
[  172.257592] usb 6-4: device descriptor read/64, error -71
[  172.460470] usb 6-4: new high speed USB device using ehci_hcd and address 8
[  172.580344] usb 6-4: device descriptor read/64, error -71
[  172.813191] usb 6-4: device descriptor read/64, error -71
[  173.016085] usb 6-4: new high speed USB device using ehci_hcd and address 9
[  173.034155] usb 6-4: device descriptor read/8, error -71
[  173.163279] usb 6-4: device descriptor read/8, error -71
[  173.365832] usb 6-4: new high speed USB device using ehci_hcd and address 10
[  173.384519] usb 6-4: device descriptor read/8, error -71
[  173.500082] usb 6-4: device descriptor read/8, error -71
[  441.007231] usb 6-4: new high speed USB device using ehci_hcd and address 11
[  441.130347] usb 6-4: unable to read config index 0 descriptor/all
[  441.130373] usb 6-4: can't read configurations, error -71
[  441.233059] usb 6-4: new high speed USB device using ehci_hcd and address 12
[  441.360742] usb 6-4: unable to read config index 0 descriptor/all
[  441.360766] usb 6-4: can't read configurations, error -71
[  441.463904] usb 6-4: new high speed USB device using ehci_hcd and address 13
[  441.508231] usb 6-4: can't set config #1, error -71
[  441.609842] usb 6-4: new high speed USB device using ehci_hcd and address 14
[  645.407245] usb 6-4: USB disconnect, address 14
[  663.600398] usb 6-4: new high speed USB device using ehci_hcd and address 15
[  663.725771] usb 6-4: unable to read config index 0 descriptor/all
[  663.725795] usb 6-4: can't read configurations, error -71
[  663.828231] usb 6-4: new high speed USB device using ehci_hcd and address 16
[  663.955294] usb 6-4: unable to read config index 0 descriptor/all
[  663.955318] usb 6-4: can't read configurations, error -71
[  664.058071] usb 6-4: new high speed USB device using ehci_hcd and address 17
[  664.076242] usb 6-4: device descriptor read/all, error -71
[  664.178982] usb 6-4: new high speed USB device using ehci_hcd and address 18
[  664.194090] usb 6-4: device descriptor read/8, error -71
[  664.340649] scsi1 : SCSI emulation for USB Mass Storage devices
[  664.340995] usb-storage: device found at 18
[  664.341004] usb-storage: waiting for device to settle before scanning
[  669.339710]   Vendor: OLYMPUS   Model: SP320             Rev: 1.00
[  669.339752]   Type:   Direct-Access                      ANSI SCSI revision: 02
[  669.442273] usb 6-4: reset high speed USB device using ehci_hcd and address 18
[  669.561179] usb 6-4: device descriptor read/64, error -71
[  669.797053] usb 6-4: device descriptor read/64, error -71
[  669.999883] usb 6-4: reset high speed USB device using ehci_hcd and address 18
[  670.130786] usb 6-4: device descriptor read/64, error -71
[  670.364619] usb 6-4: device descriptor read/64, error -71
[  670.567473] usb 6-4: reset high speed USB device using ehci_hcd and address 18
[  670.590829] usb 6-4: device descriptor read/8, error -71
[  670.706543] usb 6-4: device descriptor read/8, error -71
[  670.909240] usb 6-4: reset high speed USB device using ehci_hcd and address 18
[  670.940286] usb 6-4: device descriptor read/8, error -71
[  671.060601] usb 6-4: device descriptor read/8, error -71
[  671.161117] usb 6-4: USB disconnect, address 18
[  671.162399] sda : READ CAPACITY failed.
[  671.162406] sda : status=0, message=00, host=1, driver=00
[  671.162418] sda : sense not available.
[  671.163061] sda: Write Protect is off
[  671.163075] sda: Mode Sense: 00 00 00 00
[  671.163082] sda: assuming drive cache: write through
[  671.165656] sda : READ CAPACITY failed.
[  671.165662] sda : status=0, message=00, host=1, driver=00
[  671.165676] sda : sense not available.
[  671.166047] sda: Write Protect is off
[  671.166058] sda: Mode Sense: 00 00 00 00
[  671.166065] sda: assuming drive cache: write through
[  671.168249] sda : READ CAPACITY failed.
[  671.168255] sda : status=0, message=00, host=1, driver=00
[  671.168269] sda : sense not available.
[  671.169069] sda: Write Protect is off
[  671.169087] sda: Mode Sense: 00 00 00 00
[  671.169095] sda: assuming drive cache: write through
[  671.169109]  sda:<3>Buffer I/O error on device sda, logical block 0
[  671.169255] Buffer I/O error on device sda, logical block 0
[  671.169270]  unable to read partition table
[  671.170113] sd 1:0:0:0: Attached scsi removable disk sda
[  671.170273] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  671.175628] usb-storage: device scan complete
[  671.277985] usb 6-4: new high speed USB device using ehci_hcd and address 19
[  671.396893] usb 6-4: device descriptor read/64, error -71
[  671.621735] usb 6-4: device descriptor read/64, error -71
[  671.824591] usb 6-4: new high speed USB device using ehci_hcd and address 20
[  671.935511] usb 6-4: device descriptor read/64, error -71
[  672.156389] usb 6-4: device descriptor read/64, error -71
[  672.359215] usb 6-4: new high speed USB device using ehci_hcd and address 21
[  672.377877] usb 6-4: device descriptor read/8, error -71
[  672.496702] usb 6-4: device descriptor read/8, error -71
[  672.699033] usb 6-4: new high speed USB device using ehci_hcd and address 22
[  672.732100] usb 6-4: device descriptor read/8, error -71
[  672.846542] usb 6-4: device descriptor read/8, error -71
[  692.080307] usb 6-4: new high speed USB device using ehci_hcd and address 23
[  692.221922] usb 6-4: can't set config #1, error -71
[  692.324152] usb 6-4: new high speed USB device using ehci_hcd and address 24
[  692.434072] usb 6-4: device descriptor read/64, error -71
[  692.654515] scsi2 : SCSI emulation for USB Mass Storage devices
[  692.655014] usb-storage: device found at 24
[  692.655025] usb-storage: waiting for device to settle before scanning
[  697.754327] usb 6-4: reset high speed USB device using ehci_hcd and address 24
[  697.870244] usb 6-4: device descriptor read/64, error -71
[  698.093077] usb 6-4: device descriptor read/64, error -71
[  698.295940] usb 6-4: reset high speed USB device using ehci_hcd and address 24
[  698.407864] usb 6-4: device descriptor read/64, error -71
[  698.616716] usb 6-4: device descriptor read/64, error -71
[  698.819574] usb 6-4: reset high speed USB device using ehci_hcd and address 24
[  698.834558] usb 6-4: device descriptor read/8, error -71
[  698.947503] usb 6-4: device descriptor read/8, error -71
[  699.150345] usb 6-4: reset high speed USB device using ehci_hcd and address 24
[  699.167022] usb 6-4: device descriptor read/8, error -71
[  699.279237] usb 6-4: device descriptor read/8, error -71
[  699.380235] usb 6-4: USB disconnect, address 24
[  699.382182] usb-storage: device scan complete
[  699.484094] usb 6-4: new high speed USB device using ehci_hcd and address 25
[  699.600017] usb 6-4: device descriptor read/64, error -71
[  699.817867] usb 6-4: device descriptor read/64, error -71
[  700.020729] usb 6-4: new high speed USB device using ehci_hcd and address 26
[  700.140638] usb 6-4: device descriptor read/64, error -71
[  700.352490] usb 6-4: device descriptor read/64, error -71
[  700.555353] usb 6-4: new high speed USB device using ehci_hcd and address 27
[  700.774424] usb 6-4: device descriptor read/8, error -71
[  700.888995] usb 6-4: device descriptor read/8, error -71
[  701.090972] usb 6-4: new high speed USB device using ehci_hcd and address 28
[  701.105520] usb 6-4: device descriptor read/8, error -71
[  701.217972] usb 6-4: device descriptor read/8, error -71
[  710.817121] usb 6-4: new high speed USB device using ehci_hcd and address 29
[  762.075044] usb 6-4: USB disconnect, address 29
[  769.275923] usb 6-4: new high speed USB device using ehci_hcd and address 30
[  769.396873] scsi3 : SCSI emulation for USB Mass Storage devices
[  769.397902] usb-storage: device found at 30
[  769.397916] usb-storage: waiting for device to settle before scanning
[  774.397118]   Vendor: OLYMPUS   Model: SP320             Rev: 1.00
[  774.397159]   Type:   Direct-Access                      ANSI SCSI revision: 02
[  774.503253] usb 6-4: reset high speed USB device using ehci_hcd and address 30
[  774.624555] SCSI device sda: 1023120 512-byte hdwr sectors (524 MB)
[  774.629960] sda: Write Protect is off
[  774.629982] sda: Mode Sense: 18 00 00 08
[  774.629990] sda: assuming drive cache: write through
[  774.635550] SCSI device sda: 1023120 512-byte hdwr sectors (524 MB)
[  774.639694] sda: Write Protect is off
[  774.639716] sda: Mode Sense: 18 00 00 08
[  774.639724] sda: assuming drive cache: write through
[  774.639738]  sda:<6>usb 6-4: reset high speed USB device using ehci_hcd and address 30
[  774.862994] usb 6-4: device descriptor read/64, error -71
[  775.080839] usb 6-4: device descriptor read/64, error -71
[  775.283695] usb 6-4: reset high speed USB device using ehci_hcd and address 30
[  775.404616] usb 6-4: device descriptor read/64, error -71
[  775.614469] usb 6-4: device descriptor read/64, error -71
[  775.817327] usb 6-4: reset high speed USB device using ehci_hcd and address 30
[  775.832901] usb 6-4: device descriptor read/8, error -71
[  775.946086] usb 6-4: device descriptor read/8, error -71
[  776.148098] usb 6-4: reset high speed USB device using ehci_hcd and address 30
[  776.160619] usb 6-4: device descriptor read/8, error -71
[  776.278562] usb 6-4: device descriptor read/8, error -71
[  776.378982] usb 6-4: USB disconnect, address 30
[  776.379950] sd 3:0:0:0: SCSI error: return code = 0x10000
[  776.379969] end_request: I/O error, dev sda, sector 0
[  776.379983] Buffer I/O error on device sda, logical block 0
[  776.380917] sd 3:0:0:0: SCSI error: return code = 0x10000
[  776.380933] end_request: I/O error, dev sda, sector 0
[  776.380945] Buffer I/O error on device sda, logical block 0
[  776.380988]  unable to read partition table
[  776.381995] sd 3:0:0:0: Attached scsi removable disk sda
[  776.382153] sd 3:0:0:0: Attached scsi generic sg0 type 0
[  776.386909] usb-storage: device scan complete
[  776.488854] usb 6-4: new high speed USB device using ehci_hcd and address 31
[  776.607763] usb 6-4: device descriptor read/64, error -71
[  776.821617] usb 6-4: device descriptor read/64, error -71
[  777.024480] usb 6-4: new high speed USB device using ehci_hcd and address 32
[  777.140391] usb 6-4: device descriptor read/64, error -71
[  777.369227] usb 6-4: device descriptor read/64, error -71
[  777.572088] usb 6-4: new high speed USB device using ehci_hcd and address 33
[  777.586714] usb 6-4: device descriptor read/8, error -71
[  777.698947] usb 6-4: device descriptor read/8, error -71
[  777.901842] usb 6-4: new high speed USB device using ehci_hcd and address 34
[  777.917197] usb 6-4: device descriptor read/8, error -71
[  778.036279] usb 6-4: device descriptor read/8, error -71
kepos@assimilator:~$

```

---

