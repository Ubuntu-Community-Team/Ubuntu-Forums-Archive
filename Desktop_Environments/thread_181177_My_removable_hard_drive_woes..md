---
title: "My removable hard drive woes."
date: 2006-05-23
forum: Desktop Environments
---

### Post by Waste on 2006-05-23
Ok, so I got me a removable hard drive and got it up and running on Ubuntu just fine, can read and manually mount it just fine.
I reformatted it to ext3. (Came as ntfs. Bleh.)
My problem here is, that I wish it to automatically mount to "/media/Maxtor" each time I plug it in.  (It's device path is "/dev/sdb1" as of right now. It changes each time I plug it in.)

I have tried searching the forums, went through some answers from that search and nothing gave me the desired results.

Any help is much appreciated.

---

### Post by ispmarin on 2006-05-23
I supose is a usb removable drive, right? It should mount automaticaly after you plug in. Just in case, check the /etc/group and sees if your user is in the plugdev group. This was giving me some headaches because if your user is not in the plugdev group, pmount cannot mount it automatically. Also, give us the output of dmesg just after you plug the removable drive.

Ivan

---

### Post by Waste on 2006-05-23
plugdev as it is in my /etc/group:

```
plugdev:x:46:waste,tally
```

Output of dmesg:

```
g enabled
[4294668.617000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.618000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.619000] io scheduler noop registered
[4294668.619000] io scheduler anticipatory registered
[4294668.619000] io scheduler deadline registered
[4294668.619000] io scheduler cfq registered
[4294668.619000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.619000] EISA: Probing bus 0 at eisa.0
[4294668.619000] Cannot allocate resource for EISA slot 4
[4294668.619000] EISA: Detected 0 cards.
[4294668.619000] NET: Registered protocol family 2
[4294668.629000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294668.629000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[4294668.630000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.630000] TCP: Hash tables configured (established 262144 bind 65536)
[4294668.630000] NET: Registered protocol family 8
[4294668.630000] NET: Registered protocol family 20
[4294668.630000] ACPI wakeup devices:
[4294668.630000] HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1
[4294668.630000] ACPI: (supports S0 S1 S3 S4 S5)
[4294668.630000] Freeing unused kernel memory: 224k freed
[4294668.641000] vga16fb: initializing
[4294668.641000] vga16fb: mapped to 0xc00a0000
[4294668.847000] Console: switching to colour frame buffer device 80x30
[4294668.847000] fb0: VGA16 VGA frame buffer device
[4294669.015000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294669.994000] Capability LSM initialized
[4294670.003000] NET: Registered protocol family 1
[4294670.013000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.013000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.013000] ACPI: bus type ide registered
[4294670.015000] SCSI subsystem initialized
[4294670.016000] libata version 1.11 loaded.
[4294670.024000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[4294670.024000] NFORCE-CK804: chipset revision 162
[4294670.024000] NFORCE-CK804: not 100% native mode: will probe irqs later
[4294670.024000] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[4294670.024000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294670.024000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[4294670.024000] Probing IDE interface ide0...
[4294670.288000] hda: Maxtor 6Y120P0, ATA DISK drive
[4294670.543000] hdb: Maxtor 6L200P0, ATA DISK drive
[4294670.597000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294670.597000] Probing IDE interface ide1...
[4294671.269000] hdc: TSSTcorpCD/DVDW TS-H552U, ATAPI CD/DVD-ROM drive
[4294671.983000] hdd: SAMSUNG CDRW/DVD SM-352B, ATAPI CD/DVD-ROM drive
[4294672.034000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.034000] Probing IDE interface ide2...
[4294672.547000] Probing IDE interface ide3...
[4294673.059000] Probing IDE interface ide4...
[4294673.571000] Probing IDE interface ide5...
[4294674.085000] hda: max request size: 128KiB
[4294674.100000] hda: 240121728 sectors (122942 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(133)
[4294674.100000] hda: cache flushes supported
[4294674.100000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
[4294674.127000] hdb: max request size: 1024KiB
[4294674.149000] hdb: 398297088 sectors (203928 MB) w/8192KiB Cache, CHS=24792/255/63, UDMA(133)
[4294674.151000] hdb: cache flushes supported
[4294674.151000]  /dev/ide/host0/bus0/target1/lun0: p1
[4294674.163000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294674.163000] Uniform CD-ROM driver Revision: 3.20
[4294674.165000] hdd: ATAPI 52X DVD-ROM CD-R/RW drive, 8192kB Cache
[4294674.418000] Attempting manual resume
[4294674.418000] swsusp: Suspend partition has wrong signature?
[4294674.446000] usbcore: registered new driver usbfs
[4294674.446000] usbcore: registered new driver hub
[4294674.447000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294674.447000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[4294674.447000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[4294674.447000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294674.447000] ohci_hcd 0000:00:02.0: nVidia Corporation CK804 USB Controller
[4294674.458000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[4294674.458000] ohci_hcd 0000:00:02.0: irq 23, io mem 0xd4002000
[4294674.511000] hub 1-0:1.0: USB hub found
[4294674.511000] hub 1-0:1.0: 10 ports detected
[4294674.521000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[4294674.521000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[4294674.521000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[4294674.521000] ehci_hcd 0000:00:02.1: nVidia Corporation CK804 USB Controller
[4294674.521000] ehci_hcd 0000:00:02.1: debug port 1
[4294674.521000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[4294674.521000] ehci_hcd 0000:00:02.1: irq 22, io mem 0xd4003000
[4294674.521000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[4294674.521000] ehci_hcd 0000:00:02.1: park 0
[4294674.521000] ehci_hcd 0000:00:02.1: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294674.522000] hub 2-0:1.0: USB hub found
[4294674.522000] hub 2-0:1.0: 10 ports detected
[4294674.572000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[4294674.572000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[4294674.572000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
[4294674.572000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[4294675.084000] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:0a.0
[4294675.173000] usb 2-4: new high speed USB device using ehci_hcd and address 3[4294675.187000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[4294675.187000] ACPI: PCI Interrupt 0000:05:0c.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[4294675.187000] skge addr 0xd3000000 irq 17 chip Yukon-Lite rev 9
[4294675.187000] skge eth1: addr 00:11:d8:a0:ab:cb
[4294675.247000] usb 2-4: unable to read config index 0 descriptor/start
[4294675.247000] usb 2-4: can't read configurations, error -71
[4294675.310000] usb 2-4: new high speed USB device using ehci_hcd and address 4[4294675.553000] usb 2-10: new high speed USB device using ehci_hcd and address 5
[4294675.823000] usb 1-3: new low speed USB device using ohci_hcd and address 2
[4294677.203000] usbcore: registered new driver hiddev
[4294677.214000] input: USB HID v1.11 Mouse [Microsoft Corporation Microsoft \uffff Laser Mouse 6000] on usb-0000:00:02.0-3
[4294677.214000] usbcore: registered new driver usbhid
[4294677.214000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294677.229000] Initializing USB Mass Storage driver...
[4294677.229000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294677.229000] usb-storage: device found at 4
[4294677.229000] usb-storage: waiting for device to settle before scanning
[4294677.230000] scsi1 : SCSI emulation for USB Mass Storage devices
[4294677.230000] usb-storage: device found at 5
[4294677.230000] usb-storage: waiting for device to settle before scanning
[4294677.230000] usbcore: registered new driver usb-storage
[4294677.230000] USB Mass Storage support registered.
[4294677.615000] ACPI: Fan [FAN] (on)
[4294677.617000] ACPI: CPU0 (power states: C1[C1])
[4294677.617000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294677.618000] ACPI: Thermal Zone [THRM] (40 C)
[4294677.824000] Attempting manual resume
[4294677.824000] swsusp: Suspend partition has wrong signature?
[4294677.836000] kjournald starting.  Commit interval 5 seconds
[4294677.836000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.776000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294681.366000] Adding 3871656k swap on /dev/hda3.  Priority:-1 extents:1
[4294681.622000] EXT3 FS on hda2, internal journal
[4294682.230000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
[4294682.230000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294682.232000]   Vendor: Maxtor    Model: 3200              Rev: 0341
[4294682.232000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4294682.233000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
[4294682.233000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294682.234000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
[4294682.234000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294682.235000] usb-storage: device scan complete
[4294682.237000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
[4294682.237000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294682.243000] usb-storage: device scan complete
[4294686.805000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4294686.807000] SCSI device sdb: 195371568 512-byte hdwr sectors (100030 MB)
[4294686.807000] sdb: assuming drive cache: write through
[4294686.809000] SCSI device sdb: 195371568 512-byte hdwr sectors (100030 MB)
[4294686.809000] sdb: assuming drive cache: write through
[4294686.809000]  /dev/scsi/host1/bus0/target0/lun0: p1
[4294686.839000] Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
[4294686.846000] Attached scsi removable disk sdc at scsi0, channel 0, id 0, lun 1
[4294686.853000] Attached scsi removable disk sdd at scsi0, channel 0, id 0, lun 2
[4294686.861000] Attached scsi removable disk sde at scsi0, channel 0, id 0, lun 3
[4294687.786000] parport: PnPBIOS parport detected.
[4294687.786000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294687.870000] lp0: using parport0 (interrupt-driven).
[4294687.917000] mice: PS/2 mouse device common for all mice
[4294687.954000] ieee1394: Initialized config rom entry `ip1394'
[4294687.957000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294690.654000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294691.413000] cdrom: open failed.
[4294691.415000] cdrom: open failed.
[4294691.965000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294692.013000] NTFS volume version 3.1.
[4294692.053000] NTFS volume version 3.1.
[4294693.379000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[4294693.388000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[4294693.555000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[4294693.555000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 20 (level, low) -> IRQ 20
[4294693.555000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[4294693.865000] intel8x0_measure_ac97_clock: measured 49690 usecs
[4294693.865000] intel8x0: clocking to 46767
[4294694.242000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.251000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294694.508000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[4294694.508000] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[4294695.055000] gameport: EMU10K1 is pci0000:05:06.1/gameport0, io 0xc400, speed 1193kHz
[4294695.119000] Linux video capture interface: v1.00
[4294695.147000] cx2388x v4l2 driver version 0.0.4 loaded
[4294695.150000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[4294695.150000] ACPI: PCI Interrupt 0000:05:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[4294695.150000] cx88[0]: subsystem: 1462:8606, board: MSI TV-@nywhere Master [card=7,autodetected]
[4294695.309000] cx88[0]/0: found at 0000:05:08.0, rev: 5, irq: 18, latency: 32, mmio: 0xd0000000
[4294695.322000] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[4294695.331000] tuner 2-0061: microtune: companycode=3cbf part=42 rev=2f
[4294695.336000] tuner 2-0061: microtune MT2050 found, OK
[4294695.394000] tda9885/6/7: chip found @ 0x86
[4294695.414000] cx88[0]/0: registered device video0 [v4l2]
[4294695.414000] cx88[0]/0: registered device vbi0
[4294695.415000] cx88[0]/0: registered device radio0
[4294695.531000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294695.531000] ACPI: PCI Interrupt 0000:05:0b.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[4294695.584000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d3008000-d30087ff]  Max Packet=[2048]
[4294696.843000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000017cbac][4294697.566000] Real Time Clock Driver v1.12
[4294697.624000] input: PC Speaker
[4294697.683000] Floppy drive(s): fd0 is 1.44M
[4294697.697000] FDC 0 is a post-1991 82077
[4294698.178000] ts: Compaq touchscreen protocol output
[4294702.052000] NET: Registered protocol family 10
[4294702.052000] Disabled Privacy Extensions on device c02eb280(lo)
[4294702.052000] IPv6 over IPv4 tunneling driver
[4294703.519000] ACPI: Power Button (FF) [PWRF]
[4294703.519000] ACPI: Power Button (CM) [PWRB]
[4294703.583000] ibm_acpi: ec object not found
[4294707.381000] Linux agpgart interface v0.101 (c) Dave Jones
[4294707.392000] nvidia: module license 'NVIDIA' taints kernel.
[4294707.398000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[4294707.398000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[4294707.399000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667 Fri Jun 17 07:01:04 PDT 2005
[4294709.947000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294709.948000] apm: overridden by ACPI.
[4294710.081000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[4294711.726000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[4294711.726000] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x2 (1500 mV)
[4294711.726000] powernow-k8:    1 : fid 0x4 (1200 MHz), vid 0x12 (1100 mV)
[4294711.726000] cpu_init done, current fid 0x12, vid 0x2
[4294713.002000] Bluetooth: Core ver 2.7
[4294713.002000] NET: Registered protocol family 31
[4294713.002000] Bluetooth: HCI device and connection manager initialized
[4294713.002000] Bluetooth: HCI socket layer initialized
[4294713.010000] eth0: no IPv6 routers present
[4294713.017000] Bluetooth: L2CAP ver 2.7
[4294713.017000] Bluetooth: L2CAP socket layer initialized
[4294713.052000] Bluetooth: RFCOMM ver 1.5
[4294713.052000] Bluetooth: RFCOMM socket layer initialized
[4294713.052000] Bluetooth: RFCOMM TTY layer initialized
[4294750.304000] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[4294750.372000] cdrom: open failed.
[4294750.374000] cdrom: open failed.
[4294750.375000] cdrom: open failed.
[4294750.376000] cdrom: open failed.
[4295423.043000] usb 2-10: USB disconnect, address 5
[4295425.989000] usb 2-10: new high speed USB device using ehci_hcd and address 6
[4295426.085000] scsi2 : SCSI emulation for USB Mass Storage devices
[4295426.086000] usb-storage: device found at 6
[4295426.086000] usb-storage: waiting for device to settle before scanning
[4295431.929000]   Vendor: Maxtor    Model: 3200              Rev: 0341
[4295431.929000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4295431.933000] SCSI device sdf: 195371568 512-byte hdwr sectors (100030 MB)
[4295431.933000] sdf: assuming drive cache: write through
[4295431.935000] SCSI device sdf: 195371568 512-byte hdwr sectors (100030 MB)
[4295431.935000] sdf: assuming drive cache: write through
[4295431.935000]  /dev/scsi/host2/bus0/target0/lun0: p1
[4295431.971000] Attached scsi disk sdf at scsi2, channel 0, id 0, lun 0
[4295431.974000] usb-storage: device scan complete

```

Thanks,
Waste


[edit]
Yes, it is USB.

---

### Post by ispmarin on 2006-05-23
It seems allright, maybe a energy saver from the hd or the system? Do you have permissions on the driver and the mount point? The mount should not need to be in /etc/fstab...

---

### Post by Waste on 2006-05-23
I haven't added anything to the fstab, well, I did, but I got rid of it after it did not work.

Permissions on the driver?

As for an energy saver, I don't think this drive has any functions of the sort.
It responds immediatly to any request it gets and never powers off.

Where could I enter the info for it to automount to this location?
Currently, I can go to "System >> Administration >> Disks" and manually mount it to the location I choose, but it has root permissions and does not do this automatically.
Nor does it mount at all. (i.e.: Showing up on the desktop upon plugging it in.)

---

### Post by ispmarin on 2006-05-23
Sorry, permissions on the DRIVE. Typo. But the pmount should create the mount point and mount it there when the usb is plugged. I solved all my problems like yours just putting my user (from nis) in the plugdev group. Sorry of not to be of more help... :(

---

### Post by Waste on 2006-05-23
It's ok, man.
I thank you for the help you have already given me. :)

---

### Post by xero1 on 2007-03-30
need help .. ubuntu does not let me copy or write any thing in a usb  devices an it saids that i dont have permision ..? how can y give me  permission? please help i am new in ubuntu   i need the removable  devises for classes  thanks

---

