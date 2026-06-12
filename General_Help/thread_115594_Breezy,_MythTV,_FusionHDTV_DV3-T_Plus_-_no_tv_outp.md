---
title: "Breezy, MythTV, FusionHDTV DV3-T Plus - no tv output"
date: 2006-01-10
forum: General Help
---

### Post by andrewsawyer on 2006-01-10
I would really appreciate some help with the last step in getting my MythTV box up and running.

I have everything installed from mysql to the extra plugins.  All seems to work and connect, including the tv_grab_au, which seems to all work fine.  However - I can't watch tv.

I just get a black screen for 10-15 seconds, and then it goes back to the menu.

lspci shows the following:
```
andrew@mediacentre:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:00:13.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
0000:00:13.2 Multimedia controller: Conexant: Unknown device 8802 (rev 05)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
andrew@mediacentre:~$

```

And dmesg gives:

```
andrew@mediacentre:~$ dmesg
10 11 12) *5
[4294668.801000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[4294668.802000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[4294668.802000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[4294668.803000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[4294668.803000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[4294668.804000] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[4294668.805000] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[4294668.805000] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[4294668.810000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.810000] pnp: PnP ACPI init
[4294668.816000] pnp: PnP ACPI: found 14 devices
[4294668.816000] PnPBIOS: Disabled by ACPI PNP
[4294668.816000] PCI: Using ACPI for IRQ routing
[4294668.816000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.861000] pnp: 00:01: ioport range 0x400-0x47f could not be reserved
[4294668.861000] pnp: 00:01: ioport range 0x500-0x50f has been reserved
[4294668.862000] audit: initializing netlink socket (disabled)
[4294668.862000] audit: initialized
[4294668.862000] VFS: Disk quotas dquot_6.5.1
[4294668.862000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.862000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.862000] devfs: boot_options: 0x0
[4294668.862000] Initializing Cryptographic API
[4294668.862000] isapnp: Scanning for PnP cards...
[4294669.215000] isapnp: No Plug & Play device found
[4294669.251000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294669.251000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.251000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.251000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.251000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.252000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.255000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.255000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.256000] io scheduler noop registered
[4294669.256000] io scheduler anticipatory registered
[4294669.256000] io scheduler deadline registered
[4294669.256000] io scheduler cfq registered
[4294669.256000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.256000] NET: Registered protocol family 2
[4294669.265000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294669.265000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294669.265000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294669.265000] TCP: Hash tables configured (established 16384 bind 16384)
[4294669.265000] NET: Registered protocol family 8
[4294669.265000] NET: Registered protocol family 20
[4294669.265000] ACPI wakeup devices:
[4294669.265000] SLPB PCI0 USB0 USB1 USB2 USB3 USB4 USB5 USB6 LAN0 AC97 UAR1
[4294669.265000] ACPI: (supports S0 S1 S4 S5)
[4294669.266000] Freeing unused kernel memory: 168k freed
[4294669.290000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294669.295000] vga16fb: initializing
[4294669.295000] vga16fb: mapped to 0xc00a0000
[4294669.421000] Console: switching to colour frame buffer device 80x30
[4294669.421000] fb0: VGA16 VGA frame buffer device
[4294670.550000] Capability LSM initialized
[4294670.567000] NET: Registered protocol family 1
[4294670.587000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.587000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.587000] ACPI: bus type ide registered
[4294670.596000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294670.596000] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug.
[4294670.596000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[4294670.596000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[4294670.596000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
[4294670.596000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 4
[4294670.596000] VP_IDE: chipset revision 6
[4294670.596000] VP_IDE: not 100% native mode: will probe irqs later
[4294670.596000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294670.596000]     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:DMA
[4294670.596000]     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:DMA
[4294670.596000] Probing IDE interface ide0...
[4294670.980000] hda: Maxtor 6L300R0, ATA DISK drive
[4294671.235000] hdb: Maxtor 5A300J0, ATA DISK drive
[4294671.289000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.289000] Probing IDE interface ide1...
[4294671.673000] hdc: ST3300831A, ATA DISK drive
[4294672.081000] hdd: SONY DVD RW DW-U18A, ATAPI CD/DVD-ROM drive
[4294672.132000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.132000] Probing IDE interface ide2...
[4294672.645000] Probing IDE interface ide3...
[4294673.157000] Probing IDE interface ide4...
[4294673.669000] Probing IDE interface ide5...
[4294674.186000] hda: max request size: 1024KiB
[4294674.208000] hda: 586114704 sectors (300090 MB) w/16384KiB Cache, CHS=36483/255/63, UDMA(33)
[4294674.210000] hda: cache flushes supported
[4294674.210000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3 p4
[4294674.232000] hdb: max request size: 1024KiB
[4294674.249000] hdb: 585940320 sectors (300001 MB) w/2048KiB Cache, CHS=36473/255/63, UDMA(33)
[4294674.249000] hdb: cache flushes supported
[4294674.249000]  /dev/ide/host0/bus0/target1/lun0: p1 < p5 >
[4294674.259000] hdc: max request size: 1024KiB
[4294674.259000] hdc: 586072368 sectors (300069 MB) w/8192KiB Cache, CHS=36481/255/63, UDMA(100)
[4294674.259000] hdc: cache flushes supported
[4294674.260000]  /dev/ide/host0/bus1/target0/lun0: p1 < p5 >
[4294674.287000] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache

[4294674.287000] Uniform CD-ROM driver Revision: 3.20
[4294674.875000] Attempting manual resume
[4294674.897000] swsusp: Suspend partition has wrong signature?
[4294674.926000] usbcore: registered new driver usbfs
[4294674.926000] usbcore: registered new driver hub
[4294674.927000] USB Universal Host Controller Interface driver v2.2
[4294674.928000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[4294674.928000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294674.928000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 5
[4294674.928000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294674.990000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294674.990000] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d000
[4294674.990000] hub 1-0:1.0: USB hub found
[4294674.990000] hub 1-0:1.0: 2 ports detected
[4294674.993000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294674.993000] PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 5
[4294674.993000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294675.055000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294675.055000] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d400
[4294675.055000] hub 2-0:1.0: USB hub found
[4294675.055000] hub 2-0:1.0: 2 ports detected
[4294675.058000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.058000] PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 5
[4294675.058000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
[4294675.120000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294675.120000] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[4294675.120000] hub 3-0:1.0: USB hub found
[4294675.120000] hub 3-0:1.0: 2 ports detected
[4294675.150000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.150000] ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
[4294675.150000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294675.150000] ehci_hcd 0000:00:10.3: irq 21, io mem 0xea100000
[4294675.151000] ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.151000] hub 4-0:1.0: USB hub found
[4294675.151000] hub 4-0:1.0: 6 ports detected
[4294675.161000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[4294675.209000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294675.209000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[4294675.209000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 23
[4294675.209000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 7
[4294675.214000] eth0: VIA Rhine II at 0x1e400, 00:01:29:94:31:ec, IRQ 23.
[4294675.214000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[4294676.159000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[4294677.984000] ACPI: Fan [FAN] (on)
[4294677.988000] ACPI: CPU0 (power states: C1[C1])
[4294677.989000] ACPI: Thermal Zone [THRM] (22 C)
[4294678.296000] Attempting manual resume
[4294678.297000] swsusp: Suspend partition has wrong signature?
[4294678.317000] kjournald starting.  Commit interval 5 seconds
[4294678.317000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.984000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294682.967000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1
[4294683.193000] EXT3 FS on hda1, internal journal
[4294688.022000] parport: PnPBIOS parport detected.
[4294688.022000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[4294688.112000] lp0: using parport0 (interrupt-driven).
[4294688.147000] mice: PS/2 mouse device common for all mice
[4294688.251000] Linux video capture interface: v1.00
[4294688.305000] bttv: driver version 0.9.15 loaded
[4294688.305000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294688.309000] bt878: AUDIO driver version 0.0.0 loaded
[4294688.690000] input: PS/2 Generic Mouse on isa0060/serio1
[4294688.963000] ts: Compaq touchscreen protocol output
[4294691.799000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294692.628000] cdrom: open failed.
[4294732.059000] kjournald starting.  Commit interval 5 seconds
[4294732.059000] EXT3 FS on hda4, internal journal
[4294732.059000] EXT3-fs: mounted filesystem with ordered data mode.
[4294732.130000] ReiserFS: hdb5: found reiserfs format "3.6" with standard journal
[4294749.980000] ReiserFS: hdb5: using ordered data mode
[4294750.003000] ReiserFS: hdb5: journal params: device hdb5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294750.005000] ReiserFS: hdb5: checking transaction log (hdb5)
[4294750.051000] ReiserFS: hdb5: Using r5 hash to sort names
[4294750.118000] ReiserFS: hdc5: found reiserfs format "3.6" with standard journal
[4294764.584000] ReiserFS: hdc5: using ordered data mode
[4294764.606000] ReiserFS: hdc5: journal params: device hdc5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294764.608000] ReiserFS: hdc5: checking transaction log (hdc5)
[4294764.646000] ReiserFS: hdc5: Using r5 hash to sort names
[4294764.703000] ReiserFS: hda6: found reiserfs format "3.6" with standard journal
[4294779.000000] ReiserFS: hda6: using ordered data mode
[4294779.016000] ReiserFS: hda6: journal params: device hda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294779.019000] ReiserFS: hda6: checking transaction log (hda6)
[4294779.091000] ReiserFS: hda6: Using r5 hash to sort names
[4294779.148000] kjournald starting.  Commit interval 5 seconds
[4294779.148000] EXT3 FS on hda3, internal journal
[4294779.148000] EXT3-fs: mounted filesystem with ordered data mode.
[4294780.668000] Linux agpgart interface v0.101 (c) Dave Jones
[4294780.681000] agpgart: Detected VIA P4M266x/P4N266 chipset
[4294780.700000] agpgart: AGP aperture is 128M @ 0xd8000000
[4294780.826000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294780.844000] shpchp: shpc_init : shpc_cap_offset == 0
[4294780.844000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294781.254000] irda_init()
[4294781.254000] NET: Registered protocol family 23
[4294781.719000] via82xx: Assuming DXS channels with 48k fixed sample rate.
[4294781.719000]          Please try dxs_support=5 option
[4294781.719000]          and report if it works on your machine.
[4294781.719000]          For more details, read ALSA-Configuration.txt.
[4294781.720000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[4294781.720000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
[4294781.720000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 6
[4294781.720000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294783.145000] cx2388x v4l2 driver version 0.0.4 loaded
[4294783.151000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294783.151000] cx88[0]: subsystem: 18ac:db10, board: DVICO FusionHDTV DVB-T Plus [card=21,autodetected]
[4294783.324000] cx88[0]/0: found at 0000:00:13.0, rev: 5, irq: 18, latency: 32, mmio: 0xe8000000
[4294783.326000] cx88[0]/0: registered device video0 [v4l2]
[4294783.349000] cx88[0]/0: registered device vbi0
[4294783.547000] cx2388x dvb driver version 0.0.4 loaded
[4294783.553000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 18 (level, low) -> IRQ 18
[4294783.553000] cx88[0]/2: found at 0000:00:13.2, rev: 5, irq: 18, latency: 32, mmio: 0xe9000000
[4294783.553000] cx88[0]/2: cx2388x based dvb card
[4294783.555000] DVB: registering new adapter (cx88[0]).
[4294783.555000] DVB: registering frontend 0 (DVICO FusionHDTV DVB-T Plus)...
[4294783.749000] cx2388x blackbird driver version 0.0.4 loaded
[4294785.260000] Real Time Clock Driver v1.12
[4294785.382000] input: PC Speaker
[4294785.544000] FDC 0 is a post-1991 82077
[4294787.290000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294787.304000] NET: Registered protocol family 17
[4294788.923000] NET: Registered protocol family 10
[4294788.923000] Disabled Privacy Extensions on device c031eb40(lo)
[4294788.923000] IPv6 over IPv4 tunneling driver
[4294791.212000] ACPI: Power Button (FF) [PWRF]
[4294791.212000] ACPI: Power Button (CM) [PWRB]
[4294791.212000] ACPI: Sleep Button (CM) [SLPB]
[4294791.365000] ibm_acpi: ec object not found
[4294794.744000] mtrr: type mismatch for e0000000,2000000 old: write-back new: write-combining
[4294796.476000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294796.476000] apm: overridden by ACPI.
[4294799.626000] eth0: no IPv6 routers present
[4294803.968000] Bluetooth: Core ver 2.7
[4294803.968000] NET: Registered protocol family 31
[4294803.968000] Bluetooth: HCI device and connection manager initialized
[4294803.968000] Bluetooth: HCI socket layer initialized
[4294803.991000] Bluetooth: L2CAP ver 2.7
[4294803.991000] Bluetooth: L2CAP socket layer initialized
[4294804.022000] Bluetooth: RFCOMM ver 1.5
[4294804.022000] Bluetooth: RFCOMM socket layer initialized
[4294804.022000] Bluetooth: RFCOMM TTY layer initialized
[4295204.212000] mtrr: type mismatch for e0000000,2000000 old: write-back new: write-combining
[4295213.583000] atkbd.c: Failed to enable keyboard on isa0060/serio0
[4295213.591000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4295222.671000] input: AT Translated Set 2 keyboard on isa0060/serio0
andrew@mediacentre:~$
```

I have placed dvb-bt8xx into /etc/modules like I 'think' I'm supposed to, and I'm running kernel 2.6.12.


Also, running mythtv from within my own userarea (rather than the mythtv one) gives the follwoing output in the terminal:

```
 andrew@mediacentre:~$ mythtv
2006-01-11 13:16:33.220 Unable to read configuration file mysql.txt
2006-01-11 13:16:33.224 Writing settings file
/home/andrew/.mythtv/mysql.txt
2006-01-11 13:16:33.257 New DB connection, total: 1
Total desktop width=1280, height=768, numscreens=1
2006-01-11 13:16:33.276 Using screen 0, 1280x768 at 0,0
2006-01-11 13:16:33.291 Switching to square mode (blue)
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-01-11 13:16:33.953 Joystick disabled.
2006-01-11 13:16:34.504 New DB connection, total: 2
2006-01-11 13:16:34.565 Connecting to backend server: 192.168.0.101:6543
(try 1 of 5)
2006-01-11 13:16:34.573 Using protocol version 15
2006-01-11 13:16:34.605 Using protocol version 15
2006-01-11 13:16:34.700 Disable DPMS
2006-01-11 13:16:39.751 taking too long to be allowed to read..
2006-01-11 13:16:44.753 taking too long to be allowed to read..
2006-01-11 13:16:49.754 taking too long to be allowed to read..
2006-01-11 13:16:49.754 Took more than 10 seconds to be allowed to read,
aborting.
Couldn't read file: rbuf://192.168.0.101:6543/myth/tvbuf/ringbuf1.nuv
2006-01-11 13:16:49.785 Changing from None to WatchingLiveTV
2006-01-11 13:16:49.785 Decoder not alive, and trying to play..
2006-01-11 13:16:50.759 RemoteFile::Read() failed in
RingBuffer::safe_read().
2006-01-11 13:16:50.988 RemoteFile::Read() failed in
RingBuffer::safe_read().
2006-01-11 13:16:51.221 RemoteFile::Read() failed in
RingBuffer::safe_read().
2006-01-11 13:16:51.454 RemoteFile::Read() failed in
RingBuffer::safe_read().
2006-01-11 13:16:51.689 RemoteFile::Read() failed in
RingBuffer::safe_read().
2006-01-11 13:16:51.726 Changing from None to None
2006-01-11 13:16:51.915 RemoteFile::Read() failed in
RingBuffer::safe_read().
andrew@mediacentre:~$

```

Any help getting this up and running would be very much appreciated.

---

### Post by andrewsawyer on 2006-01-13
Sorted - I did a channel scan on the correct frequency from within MythTV itself rather than just entering them manually.  If anyone else is having problems with MythTV, I can't guarantee that I'll be able to help, but stick up a query on the forum and PM me to let me know - if I can help, I will.

Andy

P.S. Not sure if anyone else might need it, however I've also attached the tv_grab_au file that I've made for Cairns, QLD, Australia.  It's in the form au_cairns.txt, however the .txt has just been added to allow upload to this server.

---

### Post by kosmic on 2006-01-13
Are you running Mytth as the User Mythtv ??

---

### Post by andrewsawyer on 2006-01-13
Yes I am - I followed a couple of guides - one at [www.abarbaccia.com](www.abarbaccia.com) and the other at [www.users.on.net/~jani/dvico-mythtv.html](www.users.on.net/~jani/dvico-mythtv.html)

I also had to do a fair bit of searching through forums etc.  So far, everything is working other than the remote and LED display (iMON Soundgraph) and also I am having a problem with my music database, but I think that might be because some of my music titles have { or other non standard symbols in them.  Could anyone confirm this?  I have 50Gb of mp3's, so I'd rather know for certain before I go through searching for them.

---

