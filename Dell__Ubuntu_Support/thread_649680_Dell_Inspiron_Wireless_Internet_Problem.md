---
title: "Dell Inspiron Wireless Internet Problem"
date: 2007-12-25
forum: Dell  Ubuntu Support
---

### Post by dunningtonc on 2007-12-25
I just received a brand new Dell Inspiron 1420 today for Christmas. It is a Dell with Ubuntu that came with 7.04 (Feisty) already installed. Everything seems to be working except for the internet. 

My computer recognizes the connections around it. However, it will not connect to any of them. I got it to connect twice, although I haven't really got the internet to work yet. I don't know what I did to get it to work the first time, although I think it was related to the little switch to the left of what I think is the wifi light. I think this is how I got it to connect the second time, too. However, it disconnected and now won't connect to anything else.

I don't think the problem is with the network, since my other computers connect to it, or with the wifi card since it recognizes the networks and has connected before. I feel like I must be missing something very obvious, but I have no idea what it is. If anyone can help it would be greatly appreciated,

---

### Post by walkerk on 2007-12-25
please post the output of the following:

```
dmesg | grep bcm43xx
```
```
lspci | grep Network
```
```
lshw -C network
```
```
iwconfig
```
```
iwlist scanning
```

---

### Post by dunningtonc on 2007-12-25
Here are the results:

The first ```
dmesg | grep bcm43xx
``` didn't do anything, it just gave me another line to type in. The only related command that did anything was "dmesg" so here is the output of that.

```
dmesg
```
[    7.864000] tg3.c:v3.72.1 (June 5, 2007)
[    7.864000] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    7.864000] PCI: Setting latency timer of device 0000:09:00.0 to 64
[    7.868000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    7.868000] sda: Write Protect is off
[    7.868000] sda: Mode Sense: 00 3a 00 00
[    7.868000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.872000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    7.872000] sda: Write Protect is off
[    7.872000] sda: Mode Sense: 00 3a 00 00
[    7.872000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.872000]  sda:<6>eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1c:23:fc:38:5f
[    8.140000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[0] TSOcap[0] 
[    8.140000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    8.140000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[    8.192000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fe4ff800-fe4fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    8.200000]  sda1 sda2 sda3 sda4 < sda5<6>hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[    8.208000] Uniform CD-ROM driver Revision: 3.20
[    8.216000]  sda6 >
[    8.216000] sd 0:0:0:0: Attached scsi disk sda
[    8.220000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.484000] Attempting manual resume
[    8.484000] swsusp: Resume From Partition 8:5
[    8.484000] PM: Checking swsusp image.
[    8.484000] PM: Resume from disk failed.
[    8.572000] kjournald starting.  Commit interval 5 seconds
[    8.572000] EXT3-fs: mounted filesystem with ordered data mode.
[    9.468000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[334fc0002184a9a1]
[   17.852000] PM: Writing back config space on device 0000:09:00.0 at offset c (was f7df0000, writing 0)
[   18.984000] input: PC Speaker as /class/input/input2
[   19.016000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.016000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.028000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.028000] agpgart: Detected an Intel 965GM Chipset.
[   19.032000] agpgart: Detected 7676K stolen memory.
[   19.044000] agpgart: AGP aperture is 256M @ 0xe0000000
[   19.364000] NET: Registered protocol family 17
[   19.400000] ieee80211_crypt: registered algorithm 'NULL'
[   19.400000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.400000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.476000] sdhci: Secure Digital Host Controller Interface driver
[   19.476000] sdhci: Copyright(c) Pierre Ossman
[   19.476000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
[   19.476000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
[   19.476000] mmc0: SDHCI at 0xfe4ff400 irq 22 DMA
[   19.508000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   19.508000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.508000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   19.508000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   19.508000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.620000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   19.620000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.864000] input: PS/2 Generic Mouse as /class/input/input3
[   20.352000] lp: driver loaded but no devices found
[   20.448000] Adding 1293192k swap on /dev/disk/by-uuid/a1c24a1c-3663-4dcc-a7ae-f7549f393e00.  Priority:-1 extents:1 across:1293192k
[   20.604000] EXT3 FS on sda6, internal journal
[   20.804000] kjournald starting.  Commit interval 5 seconds
[   20.804000] EXT3 FS on sda3, internal journal
[   20.804000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.412000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   57.516000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[   59.736000] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
[   59.784000] usbcore: registered new interface driver hsfusbcd2
[   59.796000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   59.796000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   60.220000] hsfhda: no version for "cnxthsf_OsHdaCodecClearEventCallback" found: kernel tainted.
[   61.056000] ttySHSF0 at MMIO 0x0 (irq = 1) is a Conexant HSF softmodem (HDA-14f12c06:14f1000f-1)
[   61.264000] ACPI: AC Adapter [AC] (on-line)
[   61.332000] ACPI: Battery Slot [BAT0] (battery present)
[   61.352000] input: Lid Switch as /class/input/input4
[   61.352000] ACPI: Lid Switch [LID]
[   61.352000] input: Power Button (CM) as /class/input/input5
[   61.352000] ACPI: Power Button (CM) [PBTN]
[   61.352000] input: Sleep Button (CM) as /class/input/input6
[   61.352000] ACPI: Sleep Button (CM) [SBTN]
[   61.420000] Using specific hotkey driver
[   61.464000] No dock devices found.
[   61.508000] ibm_acpi: ec object not found
[   61.636000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   61.640000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   61.640000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   61.664000] pcc_acpi: loading...
[   62.528000] NET: Registered protocol family 10
[   62.528000] lo: Disabled Privacy Extensions
[   62.528000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   63.320000] usbcore: deregistering interface driver hsfusbcd2
[   63.444000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[   66.100000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   69.832000] [drm] Initialized drm 1.1.0 20060810
[   69.836000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   69.836000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  210.824000] ppdev: user-space parallel port driver
[  211.504000] apm: BIOS not found.
[  212.088000] Bluetooth: Core ver 2.11
[  212.088000] NET: Registered protocol family 31
[  212.088000] Bluetooth: HCI device and connection manager initialized
[  212.088000] Bluetooth: HCI socket layer initialized
[  212.112000] Bluetooth: L2CAP ver 2.8
[  212.112000] Bluetooth: L2CAP socket layer initialized
[  212.344000] Bluetooth: RFCOMM socket layer initialized
[  212.344000] Bluetooth: RFCOMM TTY layer initialized
[  212.344000] Bluetooth: RFCOMM ver 1.8
[  212.960000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[  212.960000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  214.172000] ttySHSF0 at MMIO 0x0 (irq = 1) is a Conexant HSF softmodem (HDA-14f12c06:14f1000f-1)
[  283.800000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  294.692000] eth1: no IPv6 routers present
[  326.408000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  452.672000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  482.372000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  498.732000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  523.028000] ata1.00: exception Emask 0x2 SAct 0x2 SErr 0x0 action 0x2 frozen
[  523.028000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x2 FIS=005040a1:00000001)
[  523.028000] ata1.00: cmd 60/06:08:c3:89:97/00:00:0d:00:00/40 tag 1 cdb 0x0 data 3072 in
[  523.028000]          res 50/00:06:c3:89:97/00:00:0d:00:00/40 Emask 0x2 (HSM violation)
[  523.340000] ata1: soft resetting port
[  523.512000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  523.512000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  523.512000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  523.512000] ata1.00: configured for UDMA/133
[  523.512000] ata1: EH complete
[  523.512000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  523.512000] sda: Write Protect is off
[  523.512000] sda: Mode Sense: 00 3a 00 00
[  523.512000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  524.652000] ata1.00: exception Emask 0x2 SAct 0x4 SErr 0x0 action 0x2 frozen
[  524.652000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x4 FIS=005040a1:00000002)
[  524.652000] ata1.00: cmd 60/06:10:e3:4b:9a/00:00:0d:00:00/40 tag 2 cdb 0x0 data 3072 in
[  524.652000]          res 50/00:06:e3:4b:9a/00:00:0d:00:00/40 Emask 0x2 (HSM violation)
[  524.964000] ata1: soft resetting port
[  525.136000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  525.136000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  525.136000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  525.136000] ata1.00: configured for UDMA/133
[  525.136000] ata1: EH complete
[  525.136000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  525.136000] sda: Write Protect is off
[  525.136000] sda: Mode Sense: 00 3a 00 00
[  525.136000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  525.784000] ata1.00: exception Emask 0x2 SAct 0x4 SErr 0x0 action 0x2 frozen
[  525.784000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x4 FIS=005040a1:00000001)
[  525.784000] ata1.00: cmd 60/06:10:73:15:9c/00:00:0d:00:00/40 tag 2 cdb 0x0 data 3072 in
[  525.784000]          res 50/00:06:73:15:9c/00:00:0d:00:00/40 Emask 0x2 (HSM violation)
[  526.096000] ata1: soft resetting port
[  526.268000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  526.268000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  526.268000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  526.268000] ata1.00: configured for UDMA/133
[  526.268000] ata1: EH complete
[  526.268000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  526.268000] sda: Write Protect is off
[  526.268000] sda: Mode Sense: 00 3a 00 00
[  526.268000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  527.528000] ata1.00: NCQ disabled due to excessive errors
[  527.528000] ata1.00: exception Emask 0x2 SAct 0x4 SErr 0x0 action 0x2 frozen
[  527.528000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x4 FIS=005040a1:00000002)
[  527.528000] ata1.00: cmd 60/06:10:93:0a:a0/00:00:0d:00:00/40 tag 2 cdb 0x0 data 3072 in
[  527.528000]          res 50/00:06:93:0a:a0/00:00:0d:00:00/40 Emask 0x2 (HSM violation)
[  527.840000] ata1: soft resetting port
[  528.012000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  528.012000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  528.012000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[  528.012000] ata1.00: configured for UDMA/133
[  528.012000] ata1: EH complete
[  528.012000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[  528.012000] sda: Write Protect is off
[  528.012000] sda: Mode Sense: 00 3a 00 00
[  528.012000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  619.880000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  802.924000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1549.772000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3856.324000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3868.416000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3888.384000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3889.320000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3889.444000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4014.588000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4743.496000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 4743.496000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4743.788000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 4743.788000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4745.104000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 4745.104000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 4745.108000] ipw3945: Radio Frequency Kill Switch is On:
[ 4745.108000] Kill switch must be turned off for wireless networking to work.
[ 4753.420000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 4753.420000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 4753.584000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 4753.584000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4753.704000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[ 4754.296000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 4754.296000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4755.224000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 4755.224000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4756.612000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 4756.612000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4768.420000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 4768.420000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4768.868000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 4768.868000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4770.588000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 4770.588000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4770.916000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 4770.916000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4812.180000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 4812.180000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 4812.592000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 4812.592000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 5028.764000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5032.144000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 5035.216000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 5035.288000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5036.800000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 5053.468000] eth1: no IPv6 routers present
[ 6359.248000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6394.792000] usb 2-2: new high speed USB device using ehci_hcd and address 2
[ 6394.924000] usb 2-2: configuration #1 chosen from 2 choices
[ 6395.000000] usbcore: registered new interface driver libusual
[ 6395.012000] Initializing USB Mass Storage driver...
[ 6395.012000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 6395.012000] usbcore: registered new interface driver usb-storage
[ 6395.012000] USB Mass Storage support registered.
[ 6395.012000] usb-storage: device found at 2
[ 6395.012000] usb-storage: waiting for device to settle before scanning
[ 6400.012000] usb-storage: device scan complete
[ 6400.012000] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 6400.012000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[ 6400.016000] sdb: Write Protect is off
[ 6400.016000] sdb: Mode Sense: 68 00 00 08
[ 6400.016000] sdb: assuming drive cache: write through
[ 6400.016000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[ 6400.016000] sdb: Write Protect is off
[ 6400.016000] sdb: Mode Sense: 68 00 00 08
[ 6400.016000] sdb: assuming drive cache: write through
[ 6400.016000]  sdb: sdb1 sdb2
[ 6400.032000] sd 3:0:0:0: Attached scsi removable disk sdb
[ 6400.036000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 6487.320000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6636.632000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6757.592000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6783.136000] usb 2-2: USB disconnect, address 2
[ 7369.964000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 7440.492000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 7440.492000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 7441.196000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 7441.196000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 7442.248000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 7442.248000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 7442.804000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 7442.804000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 7445.484000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 7445.484000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 7445.484000] ipw3945: Radio Frequency Kill Switch is On:
[ 7445.484000] Kill switch must be turned off for wireless networking to work.
[ 7458.124000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 7458.124000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 7458.140000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 7458.140000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 7458.404000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[ 7458.676000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 7458.676000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 7460.272000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 7470.408000] eth1: no IPv6 routers present
[ 7550.728000] eth1: no IPv6 routers present
[ 7829.088000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 7950.388000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 7971.784000] usb 2-2: new high speed USB device using ehci_hcd and address 3
[ 7971.916000] usb 2-2: configuration #1 chosen from 2 choices
[ 7971.916000] scsi4 : SCSI emulation for USB Mass Storage devices
[ 7971.916000] usb-storage: device found at 3
[ 7971.916000] usb-storage: waiting for device to settle before scanning
[ 7976.916000] usb-storage: device scan complete
[ 7976.916000] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 7976.916000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[ 7976.920000] sdb: Write Protect is off
[ 7976.920000] sdb: Mode Sense: 68 00 00 08
[ 7976.920000] sdb: assuming drive cache: write through
[ 7976.920000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[ 7976.920000] sdb: Write Protect is off
[ 7976.920000] sdb: Mode Sense: 68 00 00 08
[ 7976.920000] sdb: assuming drive cache: write through
[ 7976.920000]  sdb: sdb1 sdb2
[ 7976.940000] sd 4:0:0:0: Attached scsi removable disk sdb
[ 7976.940000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 8901.332000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 8905.316000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 8905.316000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 8906.056000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 8906.056000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 8932.060000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 8932.060000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 8932.060000] ipw3945: Radio Frequency Kill Switch is On:
[ 8932.060000] Kill switch must be turned off for wireless networking to work.
[ 8941.532000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 9031.048000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 9031.048000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 9031.256000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 9031.256000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9031.336000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[ 9032.028000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 9032.028000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9033.336000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 9036.088000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 9037.652000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 9048.008000] eth1: no IPv6 routers present
[ 9127.660000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 9138.060000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 9138.060000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9139.468000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 9139.468000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9146.988000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 9157.432000] eth1: no IPv6 routers present
[ 9165.768000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[ 9200.800000] usb 2-2: USB disconnect, address 3
[ 9247.824000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 9337.952000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 9337.952000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9338.656000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 9338.656000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9346.592000] ipw3945: Radio Frequency Kill Switch is On:
[ 9346.592000] Kill switch must be turned off for wireless networking to work.
[ 9346.592000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 9346.592000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 9355.952000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 9355.952000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 9356.232000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[10176.480000] usb 2-2: new high speed USB device using ehci_hcd and address 4
[10176.612000] usb 2-2: configuration #1 chosen from 2 choices
[10176.612000] scsi5 : SCSI emulation for USB Mass Storage devices
[10176.612000] usb-storage: device found at 4
[10176.612000] usb-storage: waiting for device to settle before scanning
[10181.612000] usb-storage: device scan complete
[10181.612000] scsi 5:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[10181.612000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[10181.616000] sdb: Write Protect is off
[10181.616000] sdb: Mode Sense: 68 00 00 08
[10181.616000] sdb: assuming drive cache: write through
[10181.616000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[10181.616000] sdb: Write Protect is off
[10181.616000] sdb: Mode Sense: 68 00 00 08
[10181.616000] sdb: assuming drive cache: write through
[10181.616000]  sdb: sdb1 sdb2
[10181.636000] sd 5:0:0:0: Attached scsi removable disk sdb
[10181.636000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[11024.724000] usb 2-2: USB disconnect, address 4
[11137.572000] usb 2-1: new high speed USB device using ehci_hcd and address 5
[11137.704000] usb 2-1: configuration #1 chosen from 2 choices
[11137.704000] scsi6 : SCSI emulation for USB Mass Storage devices
[11137.704000] usb-storage: device found at 5
[11137.704000] usb-storage: waiting for device to settle before scanning
[11142.704000] usb-storage: device scan complete
[11142.704000] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[11142.704000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[11142.708000] sdb: Write Protect is off
[11142.708000] sdb: Mode Sense: 68 00 00 08
[11142.708000] sdb: assuming drive cache: write through
[11142.708000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[11142.708000] sdb: Write Protect is off
[11142.708000] sdb: Mode Sense: 68 00 00 08
[11142.708000] sdb: assuming drive cache: write through
[11142.708000]  sdb: sdb1 sdb2
[11142.728000] sd 6:0:0:0: Attached scsi removable disk sdb
[11142.728000] sd 6:0:0:0: Attached scsi generic sg1 type 0
[11516.340000] usb 2-1: USB disconnect, address 5
[11637.544000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[11637.544000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[11637.840000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[11637.840000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[11666.744000] usb 2-4: new high speed USB device using ehci_hcd and address 6
[11666.876000] usb 2-4: configuration #1 chosen from 2 choices
[11666.876000] scsi7 : SCSI emulation for USB Mass Storage devices
[11666.876000] usb-storage: device found at 6
[11666.876000] usb-storage: waiting for device to settle before scanning
[11671.876000] usb-storage: device scan complete
[11671.876000] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[11671.876000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[11671.880000] sdb: Write Protect is off
[11671.880000] sdb: Mode Sense: 68 00 00 08
[11671.880000] sdb: assuming drive cache: write through
[11671.880000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[11671.880000] sdb: Write Protect is off
[11671.880000] sdb: Mode Sense: 68 00 00 08
[11671.880000] sdb: assuming drive cache: write through
[11671.880000]  sdb: sdb1 sdb2
[11671.892000] sd 7:0:0:0: Attached scsi removable disk sdb
[11671.892000] sd 7:0:0:0: Attached scsi generic sg1 type 0
[11707.100000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[11717.196000] eth1: no IPv6 routers present
[11763.236000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[11766.044000] usb 2-4: USB disconnect, address 6
[13340.224000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[13340.224000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[13342.576000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[13342.576000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[13410.564000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[13420.880000] eth1: no IPv6 routers present
[13438.044000] eth1: no IPv6 routers present
[14799.840000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[14926.916000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[16021.804000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[16021.804000] tg3: eth0: Flow control is off for TX and off for RX.
[16021.808000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[16038.120000] eth0: no IPv6 routers present

```
lspci | grep Network
```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```
lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:bf:23:41:32
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=unassociated
       resources: iomemory:fe8ff000-fe8fffff irq:17
  *-network
       description: Ethernet interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:fc:38:5f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.72.1 ip=192.168.1.104 latency=0 multicast=yes
       resources: iomemory:fe5f0000-fe5fffff irq:17


```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"SSCS03"  
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:0C:41:B0:C6:68   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1669   Missed beacon:0


```
iwlistscanning
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0C:41:B0:C6:68
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:10
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=84/100  Signal level=-49 dBm  Noise level=-49 dBm
                    Extra: Last beacon: 12ms ago


SSCS03 is the name of my wireless network, which is not broadcast. I have to type in its name. It is unencrypted because one of my family's windows laptops won't support wep or anything else. I have connected to it briefly and don't know how I did so. I can see other wireless networks and can't connect to any of them either. 

I'm currently using an ethernet cable connection (i'm pretty sure that's what it's called-I'm plugged in to use the internet right now. I don't know if that affects any of those outputs or not.)

Thanks to anyone who can help-I think I'm probably just missing something, but any help is much appreciated.

---

### Post by walkerk on 2007-12-25
It looks like your card is working properly already...

Click on the WICD link in my signature and follow the steps to download and install it.

After installing it you can add a hidden network using the network drop down...

Just run:
```
/opt/wicd/gui.py
```

Also, be sure to set WICD to use eth1 as your wireless interface (under preferences)

---

### Post by dunningtonc on 2007-12-25
Okay....I installed it, and it's working much better than the Network Manager was. I got it to connect to one of my neighbor's unsecured networks, but it won't connect to the "hidden" ones, so far as I can tell. However, it's definitely an improvement.

It stops connecting to the "Hidden" network (which I'm pretty sure is my SSCS03 network) at the "Obtaining IP address" section. This is the same thing it does if I try to connect to a secure network with a WEP key. If you have any idea how to make the  hidden networks work that I've missed, any tips are appreciated. Thanks for all the help so far, by the way-and your guide on wicd was great, although I just went through Synaptic to install it and didn't use the terminal at all. (I did use the command you gave me, though-but I still can't get the hidden networks to work. I don't think it's the network that's having problems since my other computers have connected to it fine.)

---

### Post by walkerk on 2007-12-26
> **dunningtonc said:**
> Okay....I installed it, and it's working much better than the Network Manager was. I got it to connect to one of my neighbor's unsecured networks, but it won't connect to the "hidden" ones, so far as I can tell. However, it's definitely an improvement.

It stops connecting to the "Hidden" network (which I'm pretty sure is my SSCS03 network) at the "Obtaining IP address" section. This is the same thing it does if I try to connect to a secure network with a WEP key. If you have any idea how to make the  hidden networks work that I've missed, any tips are appreciated. Thanks for all the help so far, by the way-and your guide on wicd was great, although I just went through Synaptic to install it and didn't use the terminal at all. (I did use the command you gave me, though-but I still can't get the hidden networks to work. I don't think it's the network that's having problems since my other computers have connected to it fine.)

You might try to add the Hidden Network with WICD and set a static IP. This way we can tell whether its a problem with DHCP or not. I'd have to test a Hidden network out at home after work today. But I will try this afternoon...

---

