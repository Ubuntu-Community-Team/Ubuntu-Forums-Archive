---
title: "Webcam integrada"
date: 2008-01-13
forum: Catalan Team
---

### Post by lluisalguero on 2008-01-13
Hola companys,
tinc al portàtil una webcam integrada, però no la puc fer funcionar, el amsn em diu que no n'hi ha cap d'instalada. He googlejat una mica buscant informació, però tot el que diuen no té res a veure amb pc's clònics, tot (o la gran majoria) parlen de HP, Toshiba, etc.

L'unic que he tret en clar és fer un lsusb per a veure quina càmara és, i aquest és el resultat

lluis@lluis-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0402:5602 ALi Corp. 
Bus 002 Device 001: ID 0000:0000  
lluis@lluis-laptop:~$ 


Si teniu o sabeu algún lloc on expliquen com fer-ho, ja m'ho miraré, tampoc us voldria "emprenyar" amb les meves coses, ja que veig que no es un problema de l'ubuntu si no la meva ineficàcia per a trobar-ho.

Gràcies,

Lluís

---

### Post by patrickfromspain on 2008-01-14
podries enganxar el contingut de dmesg?

---

### Post by lluisalguero on 2008-01-14
La sortida és molt llarga....

[    3.632000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.632000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.632000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.632000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.632000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.632000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
[    3.636000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.636000] USB Universal Host Controller Interface driver v3.0
[    3.636000] usb usb1: configuration #1 chosen from 1 choice
[    3.636000] hub 1-0:1.0: USB hub found
[    3.636000] hub 1-0:1.0: 8 ports detected
[    3.668000] SCSI subsystem initialized
[    3.676000] libata version 2.21 loaded.
[    3.740000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.740000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.740000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.740000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.740000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ec00
[    3.740000] usb usb2: configuration #1 chosen from 1 choice
[    3.740000] hub 2-0:1.0: USB hub found
[    3.740000] hub 2-0:1.0: 2 ports detected
[    3.860000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.860000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.860000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.860000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.860000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000e880
[    3.860000] usb usb3: configuration #1 chosen from 1 choice
[    3.860000] hub 3-0:1.0: USB hub found
[    3.860000] hub 3-0:1.0: 2 ports detected
[    3.964000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.964000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.964000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.964000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.964000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    3.964000] usb usb4: configuration #1 chosen from 1 choice
[    3.964000] hub 4-0:1.0: USB hub found
[    3.964000] hub 4-0:1.0: 2 ports detected
[    3.984000] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    4.068000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    4.068000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.068000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.068000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    4.068000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e480
[    4.068000] usb usb5: configuration #1 chosen from 1 choice
[    4.068000] hub 5-0:1.0: USB hub found
[    4.068000] hub 5-0:1.0: 2 ports detected
[    4.120000] usb 1-2: configuration #1 chosen from 1 choice
[    4.172000] ata_piix 0000:00:1f.2: version 2.11
[    4.172000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.172000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.172000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.172000] scsi0 : ata_piix
[    4.172000] scsi1 : ata_piix
[    4.172000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    4.172000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    4.336000] ata1.00: ATA-7: SAMSUNG HM160JI, AD100-10, max UDMA/100
[    4.336000] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.352000] ata1.00: configured for UDMA/100
[    4.684000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    4.696000] ata2.01: ATAPI: TSSTcorpCD/DVDW SN-S082D, SS03, max UDMA/33
[    4.856000] usb 4-1: configuration #1 chosen from 1 choice
[    4.888000] ata2.01: configured for UDMA/33
[    4.888000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160JI  AD10 PQ: 0 ANSI: 5
[    4.896000] scsi 1:0:1:0: CD-ROM            TSSTcorp CD/DVDW SN-S082D SS03 PQ: 0 ANSI: 5
[    4.896000] ACPI: PCI Interrupt 0000:06:04.4[A] -> GSI 16 (level, low) -> IRQ 16
[    4.948000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[feafd000-feafd7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.952000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    4.952000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    4.952000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[    4.952000] eth0: RTL8168b/8111b at 0xf8854000, 00:16:17:51:6b:4e, XID 38000000 IRQ 17
[    4.960000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.960000] sd 0:0:0:0: [sda] Write Protect is off
[    4.960000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.960000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.960000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.960000] sd 0:0:0:0: [sda] Write Protect is off
[    4.960000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.960000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.960000]  sda:<6>usbcore: registered new interface driver hiddev
[    5.008000] input: Logitech USB RECEIVER as /class/input/input2
[    5.008000] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.2-1
[    5.008000] usbcore: registered new interface driver usbhid
[    5.008000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.716000]  sda1 sda2 sda3 sda4
[    5.732000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.732000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.732000] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    5.772000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.772000] Uniform CD-ROM driver Revision: 3.20
[    5.772000] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    6.068000] Attempting manual resume
[    6.068000] swsusp: Resume From Partition 8:3
[    6.068000] PM: Checking swsusp image.
[    6.068000] PM: Resume from disk failed.
[    6.096000] kjournald starting.  Commit interval 5 seconds
[    6.096000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.224000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dc1000480fef00]
[   13.860000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.864000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.112000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.204000] intel_rng: FWH not detected
[   14.380000] input: PC Speaker as /class/input/input3
[   14.412000] iTCO_vendor_support: vendor-support=0
[   14.416000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.464000] ieee80211_crypt: registered algorithm 'NULL'
[   14.476000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.476000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   14.524000] sdhci: Secure Digital Host Controller Interface driver
[   14.524000] sdhci: Copyright(c) Pierre Ossman
[   14.524000] sdhci: SDHCI controller found at 0000:06:04.2 [1217:7120] (rev 1)
[   14.524000] ACPI: PCI Interrupt 0000:06:04.2[A] -> GSI 16 (level, low) -> IRQ 16
[   14.524000] sdhci:slot0: Unknown controller version (16). You may experience problems.
[   14.524000] mmc0: SDHCI at 0xfeaffc00 irq 16 PIO
[   14.540000] Yenta: CardBus bridge found at 0000:06:04.0 [1462:0531]
[   14.540000] Yenta O2: res at 0x94/0xD4: 00/ea
[   14.540000] Yenta O2: enabling read prefetch/write burst
[   14.616000] usbcore: registered new interface driver lmpcm_usb
[   14.616000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   14.660000] nvidia: module license 'NVIDIA' taints kernel.
[   14.676000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   14.676000] Socket status: 30000006
[   14.676000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   14.676000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   14.676000] cs: IO port probe 0xd000-0xdfff: clean.
[   14.676000] pcmcia: parent PCI bridge Memory window: 0xfe200000 - 0xfeafffff
[   14.676000] pcmcia: parent PCI bridge Memory window: 0xddf00000 - 0xdfefffff
[   14.912000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.912000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   14.912000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   14.912000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp
[   14.912000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.932000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   14.932000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   14.932000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   14.984000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[   14.984000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   14.984000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.140000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.140000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.312000] cs: IO port probe 0x100-0x3af: clean.
[   15.312000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.316000] cs: IO port probe 0x820-0x8ff: clean.
[   15.316000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.316000] cs: IO port probe 0xa00-0xaff: clean.
[   15.348000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   15.904000] lp: driver loaded but no devices found
[   16.008000] Adding 498004k swap on /dev/sda3.  Priority:-1 extents:1 across:498004k
[   16.484000] EXT3 FS on sda4, internal journal
[   16.752000] hda_intel: azx_get_response timeout, switching to polling mode...
[   16.780000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   16.916000] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   17.076000] ieee80211_crypt: registered algorithm 'WEP'
[   17.896000] NET: Registered protocol family 10
[   17.896000] lo: Disabled Privacy Extensions
[   19.352000] ACPI: Battery Slot [BAT1] (battery present)
[   19.456000] input: Power Button (FF) as /class/input/input5
[   19.456000] ACPI: Power Button (FF) [PWRF]
[   19.456000] input: Power Button (CM) as /class/input/input6
[   19.456000] ACPI: Power Button (CM) [PWRB]
[   19.456000] input: Sleep Button (CM) as /class/input/input7
[   19.456000] ACPI: Sleep Button (CM) [SLPB]
[   19.456000] input: Lid Switch as /class/input/input8
[   19.456000] ACPI: Lid Switch [LID0]
[   19.548000] No dock devices found.
[   19.592000] ACPI: AC Adapter [ADP1] (on-line)
[   19.612000] ACPI: Video Device [JVGA] (multi-head: yes  rom: no  post: no)
[   20.636000] Failure registering capabilities with primary security module.
[   20.820000] ppdev: user-space parallel port driver
[   20.988000] r8169: eth0: link down
[   20.992000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.308000] audit(1200300238.991:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5307 profile="/usr/sbin/cupsd"
[   21.548000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   21.548000] apm: disabled - APM is not SMP safe.
[   22.608000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.608000] vboxdrv: Successfully done.
[   23.012000] Bluetooth: Core ver 2.11
[   23.012000] NET: Registered protocol family 31
[   23.012000] Bluetooth: HCI device and connection manager initialized
[   23.012000] Bluetooth: HCI socket layer initialized
[   23.024000] Bluetooth: L2CAP ver 2.8
[   23.024000] Bluetooth: L2CAP socket layer initialized
[   23.128000] Bluetooth: RFCOMM socket layer initialized
[   23.128000] Bluetooth: RFCOMM TTY layer initialized
[   23.128000] Bluetooth: RFCOMM ver 1.8
[   28.116000] eth1: no IPv6 routers present
[   76.152000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   76.152000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.180000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   76.180000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.324000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   76.324000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.356000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   76.356000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.464000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   76.464000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.492000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   76.492000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.620000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   76.620000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.648000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   76.648000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.776000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   76.776000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.804000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   76.804000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.920000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   76.920000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   76.952000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   76.952000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   77.076000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   77.076000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   77.108000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   77.108000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   77.212000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   77.212000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   77.244000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   77.244000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   77.360000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   77.360000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   77.388000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   77.388000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[   77.828000] ata2.01: qc timeout (cmd 0xa0)
[   77.828000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   77.828000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[   77.828000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[   82.868000] ata2: port is slow to respond, please be patient (Status 0xd1)
[   87.856000] ata2: device not ready (errno=-16), forcing hardreset
[   87.856000] ata2: soft resetting port
[   88.392000] ata2.01: configured for UDMA/33
[   88.392000] ata2: EH complete
[  134.524000] ata2.01: qc timeout (cmd 0xa0)
[  134.524000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  134.524000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[  134.524000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  139.568000] ata2: port is slow to respond, please be patient (Status 0xd1)
[  144.556000] ata2: device not ready (errno=-16), forcing hardreset
[  144.556000] ata2: soft resetting port
[  145.096000] ata2.01: configured for UDMA/33
[  145.096000] ata2: EH complete
[  213.224000] ata2.01: qc timeout (cmd 0xa0)
[  213.224000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  213.224000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[  213.224000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  218.272000] ata2: port is slow to respond, please be patient (Status 0xd0)
[  223.264000] ata2: device not ready (errno=-16), forcing hardreset
[  223.264000] ata2: soft resetting port
[  223.804000] ata2.01: configured for UDMA/33
[  223.804000] ata2: EH complete
[  523.968000] ata2.01: qc timeout (cmd 0xa0)
[  523.968000] ata2.01: limiting speed to UDMA/25:PIO4
[  523.968000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  523.968000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[  523.968000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  528.972000] ata2: port is slow to respond, please be patient (Status 0xd0)
[  534.012000] ata2: device not ready (errno=-16), forcing hardreset
[  534.012000] ata2: soft resetting port
[  534.544000] ata2.01: configured for UDMA/25
[  534.544000] ata2: EH complete
[  766.796000] ata2.01: qc timeout (cmd 0xa0)
[  766.796000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  766.796000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[  766.796000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  771.808000] ata2: port is slow to respond, please be patient (Status 0xd0)
[  776.804000] ata2: device not ready (errno=-16), forcing hardreset
[  776.804000] ata2: soft resetting port
[  777.348000] ata2.01: configured for UDMA/25
[  777.348000] ata2: EH complete
[  979.512000] ata2.01: qc timeout (cmd 0xa0)
[  979.512000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  979.512000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[  979.512000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  984.556000] ata2: port is slow to respond, please be patient (Status 0xd0)
[  989.544000] ata2: device not ready (errno=-16), forcing hardreset
[  989.544000] ata2: soft resetting port
[  990.080000] ata2.01: configured for UDMA/25
[  990.080000] ata2: EH complete
[ 1034.180000] ata2.01: qc timeout (cmd 0xa0)
[ 1034.180000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1034.180000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[ 1034.180000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 1039.228000] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 1044.212000] ata2: device not ready (errno=-16), forcing hardreset
[ 1044.212000] ata2: soft resetting port
[ 1044.744000] ata2.01: configured for UDMA/25
[ 1044.744000] ata2: EH complete
[ 1240.928000] ata2.01: qc timeout (cmd 0xa0)
[ 1240.928000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1240.928000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[ 1240.928000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 1245.932000] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 1250.980000] ata2: device not ready (errno=-16), forcing hardreset
[ 1250.980000] ata2: soft resetting port
[ 1251.516000] ata2.01: configured for UDMA/25
[ 1251.516000] ata2: EH complete
[ 1287.648000] ata2.01: qc timeout (cmd 0xa0)
[ 1287.648000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1287.648000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[ 1287.648000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 1292.704000] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 1297.704000] ata2: device not ready (errno=-16), forcing hardreset
[ 1297.704000] ata2: soft resetting port
[ 1298.240000] ata2.01: configured for UDMA/25
[ 1298.240000] ata2: EH complete
[ 1340.324000] ata2.01: qc timeout (cmd 0xa0)
[ 1340.324000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1340.324000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[ 1340.324000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 1345.376000] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 1350.328000] ata2: device not ready (errno=-16), forcing hardreset
[ 1350.328000] ata2: soft resetting port
[ 1350.860000] ata2.01: configured for UDMA/25
[ 1350.860000] ata2: EH complete
[ 1645.052000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1645.052000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[ 1645.052000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 1650.096000] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 1655.088000] ata2: device not ready (errno=-16), forcing hardreset
[ 1655.088000] ata2: soft resetting port
[ 1655.624000] ata2.01: configured for UDMA/25
[ 1655.624000] ata2: EH complete
[ 2529.948000] ata2.01: qc timeout (cmd 0xa0)
[ 2529.948000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2529.948000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[ 2529.948000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 2534.996000] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 2539.984000] ata2: device not ready (errno=-16), forcing hardreset
[ 2539.984000] ata2: soft resetting port
[ 2540.516000] ata2.01: configured for UDMA/25
[ 2540.516000] ata2: EH complete
[ 2636.632000] ata2.01: qc timeout (cmd 0xa0)
[ 2636.632000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2636.632000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[ 2636.632000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 2641.676000] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 2646.664000] ata2: device not ready (errno=-16), forcing hardreset
[ 2646.664000] ata2: soft resetting port
[ 2647.200000] ata2.01: configured for UDMA/25
[ 2647.200000] ata2: EH complete
[ 2923.356000] ata2.01: qc timeout (cmd 0xa0)
[ 2923.356000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2923.356000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[ 2923.356000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 2928.400000] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 2933.392000] ata2: device not ready (errno=-16), forcing hardreset
[ 2933.392000] ata2: soft resetting port
[ 2933.932000] ata2.01: configured for UDMA/25
[ 2933.932000] ata2: EH complete
[ 3018.016000] ata2.01: qc timeout (cmd 0xa0)
[ 3018.016000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3018.016000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[ 3018.016000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 3023.060000] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 3028.044000] ata2: device not ready (errno=-16), forcing hardreset
[ 3028.044000] ata2: soft resetting port
[ 3028.576000] ata2.01: configured for UDMA/25
[ 3028.576000] ata2: EH complete
[ 3158.756000] ata2.01: qc timeout (cmd 0xa0)
[ 3158.756000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3158.756000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[ 3158.756000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 3163.800000] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 3168.792000] ata2: device not ready (errno=-16), forcing hardreset
[ 3168.792000] ata2: soft resetting port
[ 3169.328000] ata2.01: configured for UDMA/25
[ 3169.328000] ata2: EH complete
[ 3245.388000] ata2.01: qc timeout (cmd 0xa0)
[ 3245.388000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3245.388000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[ 3245.388000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 3250.428000] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 3255.412000] ata2: device not ready (errno=-16), forcing hardreset
[ 3255.412000] ata2: soft resetting port
[ 3255.948000] ata2.01: configured for UDMA/25
[ 3255.948000] ata2: EH complete
[ 3610.212000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3610.212000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x1e data 0 
[ 3610.212000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 3615.256000] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 3620.248000] ata2: device not ready (errno=-16), forcing hardreset
[ 3620.248000] ata2: soft resetting port
[ 3620.780000] ata2.01: configured for UDMA/25
[ 3620.780000] ata2: EH complete
[ 3918.956000] ata2.01: qc timeout (cmd 0xa0)
[ 3918.956000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3918.956000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[ 3918.956000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 3924.008000] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 3929.000000] ata2: device not ready (errno=-16), forcing hardreset
[ 3929.000000] ata2: soft resetting port
[ 3929.536000] ata2.01: configured for UDMA/25
[ 3929.536000] ata2: EH complete
[ 4253.744000] ata2.01: qc timeout (cmd 0xa0)
[ 4253.744000] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4253.744000] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[ 4253.744000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 4258.752000] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 4263.800000] ata2: device not ready (errno=-16), forcing hardreset
[ 4263.800000] ata2: soft resetting port
[ 4264.344000] ata2.01: configured for UDMA/25
[ 4264.344000] ata2: EH complete
lluis@lluis-laptop:~$

---

### Post by patrickfromspain on 2008-01-14
san google m'ha ajudat a trobar aixo:

[http://sourceforge.net/projects/m560x-driver](http://sourceforge.net/projects/m560x-driver)

s'ha de baixar i compilar per svn. No es un driver estable i el mes probable es que, si funciona, ho faci malament.

svn co [https://m560x-driver.svn.sourceforge.net/svnroot/m560x-driver/m560x/trunk](https://m560x-driver.svn.sourceforge.net/svnroot/m560x-driver/m560x/trunk) m560x-driver i partir d'alla cd m560x-driver/km_560x i llavors  make i sudo make install. Reinicia el pc i a veure si hi ha mes sort i te l'agafa.

salut!

---

### Post by lluisalguero on 2008-01-14
cd m560x-driver/km_560x

aquí em diu:

lluis@lluis-laptop:~$ cd m560x-driver/km_560x
bash: cd: m560x-driver/km_560x: No such file or directory


:confused:

---

### Post by lluisanunez on 2008-01-15
> **lluisalguero said:**
> cd m560x-driver/km_560x

aquí em diu:

lluis@lluis-laptop:~$ cd m560x-driver/km_560x
bash: cd: m560x-driver/km_560x: No such file or directory


:confused:

T'està dient que aquest directori al qual vols canviar no existeix. Mira bé com es diu...

---

### Post by lluisalguero on 2008-01-18
> **lluisanunez said:**
> T'està dient que aquest directori al qual vols canviar no existeix. Mira bé com es diu...

Perdona la meva tardança...es que he tingut uns dies una mica liats....gracies

---

