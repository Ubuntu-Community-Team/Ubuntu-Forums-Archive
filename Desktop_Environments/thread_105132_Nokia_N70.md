---
title: "Nokia N70"
date: 2005-12-17
forum: Desktop Environments
---

### Post by rado_london on 2005-12-17
Hi
I just bought the new Nokia N70. It has USB cable and software which is available only for linux. I tried to connect it via USB while in Linux. This is the output of my lsusb:
```
rado@linux:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0421:043a Nokia Mobile Phones
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 001 Device 001: ID 0000:0000

```

But the problem is that I can't edit my files, add mp3s etc.
Can you please help me finding the right way of doing it.

Thanks in advance

---

### Post by vtec on 2005-12-17
Doesn't that work like a usb drive. Did you try to mount /dev/sda1 or sda. I don't have one but i thought i read that somewhere. By the way what do you think of it, what are you using it for? I'm very interested in that device.

---

### Post by rado_london on 2005-12-17
First of all it is really nice. There is much externel software (Acroread, Opera etc.). It is a bit slow but after removing the useless stuff it becomes the dream. Andd this 2.0 mepgapixel camera is just more than perfect. 
Can you also give me a bit help about mounting it. Do I need to add anything in /etc/fstab, what is the exact command etc.

Best Regards

---

### Post by vtec on 2005-12-18
Is the N70 the same as the 770 internet tablet?? Well im not sure if this will work, but i thought that i read that it works like a usb drive. If this is true then the following should work. When you plug the device in it will be given a device name. This is normaly /dev/sda. To check for sure plug it in and from a terminal run: ```
 dmesg 
``` That will display a bunch of kernel messages. At the very end it should same some stuff like this:

```

[4298759.316000] USB Mass Storage support registered.
[4298764.320000]   Vendor: SanDisk   Model: Cruzer Mini       Rev: 0.1
[4298764.320000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4298764.333000] usb-storage: device scan complete
[4298765.400000] SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
[4298765.401000] sda: Write Protect is off
[4298765.401000] sda: Mode Sense: 03 00 00 00
[4298765.401000] sda: assuming drive cache: write through
[4298765.406000] SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
[4298765.407000] sda: Write Protect is off
[4298765.407000] sda: Mode Sense: 03 00 00 00
[4298765.407000] sda: assuming drive cache: write through
[4298765.407000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4298765.411000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4298767.834000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

See where it is saying sda, that is the device name my usb drive is given. Now that you know what it is call you need to mount it. To mount it you need to know the device name and where you want to mount it. I sugguest you mount it somewhere in /mnt. if you would like to mount it there run the following command to create a place in /mnt to mount the drive

```

sudo mkdir /mnt/nokia

```

then to mount:

```

sudo mount /dev/sda1 /mnt/nokia

```

notice the sda1 instead of sda. The 1 means the first partition of sda. If that does not work try just sda with out the 1.

If the device does work like a usb drive the above should work. good luck with it.

---

### Post by rado_london on 2005-12-18
Unfortunatelly it gives me completely different thing.
This is the output of my dmsg:
```
rado@linux:~$  dmesg
errupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[4294670.304000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)[4294670.305000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)[4294670.305000] burst-mode-ec-10-Aug
[4294670.305000] ACPI: Embedded Controller [EC0] (gpe 27)
[4294670.308000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.308000] pnp: PnP ACPI init
[4294670.309000] pnp: PnP ACPI: found 8 devices
[4294670.309000] PnPBIOS: Disabled by ACPI PNP
[4294670.309000] PCI: Using ACPI for IRQ routing
[4294670.309000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.330000] Simple Boot Flag at 0x36 set to 0x1
[4294670.331000] audit: initializing netlink socket (disabled)
[4294670.331000] audit: initialized
[4294670.331000] VFS: Disk quotas dquot_6.5.1
[4294670.331000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.331000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294670.331000] devfs: boot_options: 0x0
[4294670.331000] Initializing Cryptographic API
[4294670.331000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294670.331000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294670.331000] assign_interrupt_mode Found MSI capability
[4294670.331000] Allocate Port Service[pcie00]
[4294670.331000] Allocate Port Service[pcie02]
[4294670.331000] Allocate Port Service[pcie03]
[4294670.331000] isapnp: Scanning for PnP cards...
[4294670.684000] isapnp: No Plug & Play device found
[4294670.699000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294670.704000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294670.707000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294670.708000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294670.708000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294670.709000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294670.709000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.709000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294670.711000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 20
[4294670.711000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[4294670.711000] io scheduler noop registered
[4294670.711000] io scheduler anticipatory registered
[4294670.711000] io scheduler deadline registered
[4294670.711000] io scheduler cfq registered
[4294670.711000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.712000] EISA: Probing bus 0 at eisa.0
[4294670.712000] Cannot allocate resource for EISA slot 1
[4294670.712000] Cannot allocate resource for EISA slot 2
[4294670.712000] Cannot allocate resource for EISA slot 3
[4294670.712000] EISA: Detected 0 cards.
[4294670.712000] NET: Registered protocol family 2
[4294670.721000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294670.721000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294670.721000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.721000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.721000] NET: Registered protocol family 8
[4294670.721000] NET: Registered protocol family 20
[4294670.721000] ACPI wakeup devices:
[4294670.721000] LID0 RP01 LANC PS2K PS2M
[4294670.721000] ACPI: (supports S0 S3 S4 S5)
[4294670.721000] Freeing unused kernel memory: 224k freed
[4294670.751000] Capability LSM initialized
[4294670.754000] vesafb: framebuffer at 0xc0000000, mapped to 0xe0080000, using 6144k, total 7872k
[4294670.754000] vesafb: mode is 1024x768x32, linelength=4096, pages=1
[4294670.754000] vesafb: protected mode interface info at 00ff:44f0
[4294670.754000] vesafb: scrolling: redraw
[4294670.754000] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[4294670.755000] fb0: VESA VGA frame buffer device
[4294670.764000] Console: switching to colour frame buffer device 128x48
[4294670.767000] NET: Registered protocol family 1
[4294670.779000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.779000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.779000] ACPI: bus type ide registered
[4294670.783000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294670.783000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294670.783000] ICH6: chipset revision 4
[4294670.783000] ICH6: not 100% native mode: will probe irqs later
[4294670.783000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
[4294670.783000] Probing IDE interface ide0...
[4294671.047000] hda: FUJITSU MHT2080AT PL, ATA DISK drive
[4294671.761000] hdb: TSSTcorpCD/DVDW TS-L532R, ATAPI CD/DVD-ROM drive
[4294671.814000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.814000] Probing IDE interface ide1...
[4294671.937000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.327000] Probing IDE interface ide2...
[4294672.839000] Probing IDE interface ide3...
[4294673.351000] Probing IDE interface ide4...
[4294673.863000] Probing IDE interface ide5...
[4294674.377000] hda: max request size: 128KiB
[4294674.440000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[4294674.443000] hda: cache flushes supported
[4294674.443000]  /dev/ide/host0/bus0/target0/lun0: p1 p3 < p5 p6 p7 >
[4294674.496000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294674.496000] Uniform CD-ROM driver Revision: 3.20
[4294674.675000] Attempting manual resume
[4294674.710000] swsusp: Suspend partition has wrong signature?
[4294674.743000] usbcore: registered new driver usbfs
[4294674.743000] usbcore: registered new driver hub
[4294674.744000] USB Universal Host Controller Interface driver v2.2
[4294674.744000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294674.744000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294674.744000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294674.806000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294674.806000] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[4294674.806000] hub 1-0:1.0: USB hub found
[4294674.806000] hub 1-0:1.0: 2 ports detected
[4294674.809000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294674.809000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294674.809000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294674.871000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294674.871000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[4294674.871000] hub 2-0:1.0: USB hub found
[4294674.871000] hub 2-0:1.0: 2 ports detected
[4294674.874000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294674.874000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294674.874000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294674.936000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294674.936000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[4294674.936000] hub 3-0:1.0: USB hub found
[4294674.936000] hub 3-0:1.0: 2 ports detected
[4294674.939000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[4294674.939000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294674.939000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294674.975000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[4294675.001000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294675.001000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[4294675.001000] hub 4-0:1.0: USB hub found
[4294675.001000] hub 4-0:1.0: 2 ports detected
[4294675.029000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[4294675.029000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.029000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294675.029000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.029000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294675.029000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0040000
[4294675.033000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294675.033000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.033000] hub 5-0:1.0: USB hub found
[4294675.033000] hub 5-0:1.0: 8 ports detected
[4294675.128000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294675.128000] 8139cp: pci dev 0000:06:07.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294675.128000] 8139cp: Try the "8139too" driver instead.
[4294675.129000] 8139too Fast Ethernet driver 0.9.27
[4294675.129000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294675.130000] eth0: RealTek RTL8139 at 0x3000, 00:0a:e4:d6:a6:9d, IRQ 20
[4294675.130000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294675.475000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[4294677.144000] usbcore: registered new driver hiddev
[4294677.162000] input: USB HID v1.10 Mouse [Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0] on usb-0000:00:1d.0-1
[4294677.162000] usbcore: registered new driver usbhid
[4294677.162000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294677.372000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[4294677.380000] ACPI: Thermal Zone [THR0] (56 C)
[4294677.387000] ACPI: Thermal Zone [THR1] (41 C)
[4294677.508000] Attempting manual resume
[4294677.509000] swsusp: Suspend partition has wrong signature?
[4294677.535000] kjournald starting.  Commit interval 5 seconds
[4294677.535000] EXT3-fs: mounted filesystem with ordered data mode.
[4294679.243000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294681.761000] Adding 1485972k swap on /dev/hda5.  Priority:-1 extents:1
[4294681.922000] EXT3 FS on hda6, internal journal
[4294688.445000] lp: driver loaded but no devices found
[4294688.466000] mice: PS/2 mouse device common for all mice
[4294688.498000] ieee1394: Initialized config rom entry `ip1394'
[4294688.504000] SCSI subsystem initialized
[4294688.507000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294689.325000] alps.c: Enabling hardware tapping
[4294689.385000] input: PS/2 Mouse on isa0060/serio4
[4294689.387000] input: AlpsPS/2 ALPS GlidePoint on isa0060/serio4
[4294689.807000] ts: Compaq touchscreen protocol output
[4294692.632000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294693.318000] cdrom: open failed.
[4294693.959000] kjournald starting.  Commit interval 5 seconds
[4294693.959000] EXT3 FS on hda7, internal journal
[4294693.959000] EXT3-fs: mounted filesystem with ordered data mode.
[4294693.966000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294694.009000] NTFS volume version 3.1.
[4294695.329000] Linux agpgart interface v0.101 (c) Dave Jones
[4294695.334000] agpgart: Detected an Intel 915GM Chipset.
[4294695.335000] agpgart: Detected 7932K stolen memory.
[4294695.363000] agpgart: AGP aperture is 256M @ 0xc0000000
[4294695.602000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294695.610000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294695.839000] hw_random: RNG not detected
[4294695.976000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
[4294695.976000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294696.787000] intel8x0_measure_ac97_clock: measured 49521 usecs
[4294696.787000] intel8x0: clocking to 48000
[4294697.438000] ieee80211_crypt: registered algorithm 'NULL'
[4294697.441000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294697.441000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294697.448000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294697.448000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294697.451000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294697.451000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294698.281000] Linux Kernel Card Services
[4294698.281000]   options:  [pci] [cardbus] [pm]
[4294698.284000] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294698.284000] Yenta: CardBus bridge found at 0000:06:06.0 [103c:3081]
[4294698.284000] Yenta: Enabling burst memory read transactions
[4294698.284000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294698.284000] Yenta: Routing CardBus interrupts to PCI
[4294698.284000] Yenta TI: socket 0000:06:06.0, mfunc 0x01aa1b02, devctl 0x64
[4294698.505000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 22
[4294698.505000] Socket status: 30000006
[4294698.575000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294698.575000] ACPI: PCI Interrupt 0000:06:06.2[C] -> GSI 21 (level, low) -> IRQ 21
[4294698.626000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[b0108000-b01087ff]  Max Packet=[2048]
[4294699.883000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[05e40a006f455033][4294700.105000] Real Time Clock Driver v1.12
[4294700.706000] NET: Registered protocol family 17
[4294708.911000] NET: Registered protocol family 10
[4294708.911000] Disabled Privacy Extensions on device c02eb280(lo)
[4294708.911000] IPv6 over IPv4 tunneling driver
[4294709.621000] ACPI: AC Adapter [AC] (off-line)
[4294709.668000] ACPI: Battery Slot [BAT0] (battery present)
[4294709.684000] ACPI: Power Button (FF) [PWRF]
[4294709.684000] ACPI: Lid Switch [LID0]
[4294709.684000] ACPI: Sleep Button (CM) [SLPB]
[4294709.684000] ACPI: Power Button (CM) [PWB]
[4294709.769000] ibm_acpi: ec object not found
[4294709.823000] wmi_add device=df654c00
[4294709.823000] calling WQBA
[4294709.863000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[4294712.853000] [drm] Initialized drm 1.0.0 20040925
[4294712.857000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294712.857000] mtrr: 0xc0000000,0x10000000 overlaps existing 0xc0000000,0x400000
[4294712.859000] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
[4294712.860000] mtrr: base(0xc0020000) is not aligned on a size(0x640000) boundary
[4294714.835000] mtrr: 0xc0000000,0x10000000 overlaps existing 0xc0000000,0x400000
[4294715.201000] apm: BIOS not found.
[4294716.086000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x20f 0x4d0-0x4d7
[4294716.089000] cs: IO port probe 0xc00-0xcf7: clean.
[4294716.089000] cs: IO port probe 0xa00-0xaff: clean.
[4294716.401000] Bluetooth: Core ver 2.7
[4294716.401000] NET: Registered protocol family 31
[4294716.401000] Bluetooth: HCI device and connection manager initialized
[4294716.401000] Bluetooth: HCI socket layer initialized
[4294716.412000] Bluetooth: L2CAP ver 2.7
[4294716.412000] Bluetooth: L2CAP socket layer initialized
[4294716.423000] Bluetooth: RFCOMM ver 1.5
[4294716.423000] Bluetooth: RFCOMM socket layer initialized
[4294716.423000] Bluetooth: RFCOMM TTY layer initialized
[4294719.850000] eth0: no IPv6 routers present
[4294757.091000] usb 2-2: new full speed USB device using uhci_hcd and address 2[4294758.435000] cdc_acm 2-2:1.8: ttyACM0: USB ACM device
[4294758.538000] usbcore: registered new driver cdc_acm
[4294758.538000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters

```
Then I tried to mount /dev/sda1 to /media/nokia but it says:
```
rado@linux:~$ sudo mount /dev/sda1 /media/nokia
mount: you must specify the filesystem type
```

Hope you can give me another advace when you see the dmsg because I don't know what is says.

Thanks in advance

---

### Post by vtec on 2005-12-18
Was that 'dmesg' ran right after you pluged in the device and powered it on? It doesn't seem that it see the N70 (770) as a usb device. Is there somthing that maybe you have to turn on, on the device for it to act as a usb drive?

---

### Post by rado_london on 2005-12-18
I plugged it in and run dmsg. I think it is set up to act as usb because in windows i just plug it in and then just browse it as normal removable media.

Another strange fact is that there is no sda1 or sda in /dev/ . The only place I found it was /dev/.static/ . Do you have any ideas in this really impossible mission?

Best regards

---

### Post by vtec on 2005-12-19
Thats odd. If it shows up in windows as a usb drive then linux should have no problem with it. I'm not really sure what else to try since i my self do not have a device to try things with. I would suggesting googleing around and seeing what kinda of device the system should see it as.

---

### Post by rado_london on 2005-12-19
vtec are you planning to get one of these Nokia N70?

---

### Post by vtec on 2005-12-19
I am very interested in one. However i have been holding off in order to see what kind of PIM abilty it would have, and what kind of community formed around it. I probley will be getting eaither a palm tx or the nokia very soon though.

---

### Post by nbcthreat on 2005-12-29
Just to clarify here folks, The Nokia [N70]("http://www.nokia.com/nseries/") and [770]("http://www.nokia.com/770") are completely different items.

---

### Post by theh0g on 2005-12-30
I tried with Gnokii but couldn't get it to work. Maybe someone will have more luck? Either that or we'll have to wait till new version?
I also tried installing Nokia Suite via Wine, but it hangs during install. I have no more ideas, but it'd be great if I could access my phone on Linux, now I have to reboot to Windows every time.

---

