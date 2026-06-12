---
title: "Automount USB Mass Storage"
date: 2007-09-15
forum: Desktop Environments
---

### Post by joep on 2007-09-15
Hi I can't auto mount my Maxtor 320 gig  USB  external hhd  Been trying for hours. This is what I get when I run dmesg  ,.   Any help appreciated Joe The hhd is fat 32. 

[   36.124848] usb 1-2.1: new full speed USB device using ohci_hcd and address 5
[   36.243924] usb 1-2.1: configuration #1 chosen from 1 choice
[   36.463628] ide1 at 0x170-0x177,0x376 on irq 15
[   36.472640] usb 1-2.7: new full speed USB device using ohci_hcd and address 6
[   36.486585] hda: max request size: 512KiB
[   36.499488] hda: Host Protected Area detected.
[   36.499493]  current capacity is 488395055 sectors (250058 MB)
[   36.499495]  native  capacity is 488397168 sectors (250059 MB)
[   36.500158] hda: Host Protected Area disabled.
[   36.500165] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(33)
[   36.500637] hda: cache flushes supported
[   36.500713]  hda: hda1 hda2 < hda5 >
[   36.564860] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   36.564876] Uniform CD-ROM driver Revision: 3.20
[   36.677765] usb 1-2.7: configuration #1 chosen from 1 choice
[   36.682542] usbcore: registered new interface driver hiddev
[   36.688904] input: USB Optical Mouse USB Optical Mouse as /class/input/input2
[   36.688940] input: USB HID v1.10 Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:02.0-1
[   36.688976] usbcore: registered new interface driver usbhid
[   36.688982] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   36.786147] Attempting manual resume
[   36.786154] swsusp: Resume From Partition 3:5
[   36.786157] PM: Checking swsusp image.
[   36.786506] PM: Resume from disk failed.
[   36.840863] kjournald starting.  Commit interval 5 seconds
[   36.840883] EXT3-fs: mounted filesystem with ordered data mode.
[   47.954523] Linux agpgart interface v0.102 (c) Dave Jones
[   47.960034] agpgart: Detected NVIDIA nForce2 chipset
[   47.967796] agpgart: AGP aperture is 64M @ 0xd0000000
[   48.655834] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.659070] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   49.374641] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   49.374694] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
[   49.634501] input: PC Speaker as /class/input/input3
[   50.141506] gameport: EMU10K1 is pci0000:01:07.1/gameport0, io 0xd400, speed 59659kHz
[   50.150351] Linux video capture interface: v2.00
[   50.200626] bttv: driver version 0.9.17 loaded
[   50.200634] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   50.200750] bttv: Bt8xx card found (0).
[   50.201097] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   50.201112] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 19
[   50.201132] bttv0: Bt878 (rev 17) at 0000:01:0a.0, irq: 19, latency: 32, mmio: 0xd6000000
[   50.201149] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   50.201155] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[   50.201209] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   50.201611] bttv0: i2c: checking for MSP34xx @ 0x80... <6>parport_pc 00:0b: reported by Plug and Play ACPI
[   50.240908] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   50.776289] not found
[   50.776298] bttv0: pinnacle/mt: id=1 info="PAL / mono" radio=no
[   50.776303] bttv0: using tuner=33
[   50.776310] bttv0: i2c: checking for MSP34xx @ 0x80... <6>Bluetooth: Core ver 2.11
[   50.856640] NET: Registered protocol family 31
[   50.856645] Bluetooth: HCI device and connection manager initialized
[   50.856651] Bluetooth: HCI socket layer initialized
[   50.871883] Bluetooth: HCI USB driver ver 2.9
[   50.897784] not found
[   50.897795] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   50.917440] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   50.944665] pegasus: v0.6.14 (2006/09/27), Pegasus/Pegasus II USB Ethernet driver
[   50.979860] tuner 2-0043: chip found @ 0x86 (bt878 #0 [sw])
[   50.979924] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   51.006086] tuner 2-0060: Chip ID is not zero. It is not a TEA5767
[   51.006095] tuner 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   51.008898] tuner 2-0060: microtune: companycode=3cbf part=42 rev=22
[   51.010044] tuner 2-0060: microtune MT2050 found, OK
[   51.012773] tuner 2-0060: microtune: companycode=3cbf part=42 rev=22
[   51.013917] tuner 2-0060: microtune MT2050 found, OK
[   51.021406] usbcore: registered new interface driver hci_usb
[   51.161046] pegasus 1-2.1:1.0: setup Pegasus II specific registers
[   51.342639] pegasus 1-2.1:1.0: eth0, SMC 2206 USB Ethernet, 26:80:62:5f:65:6e
[   51.342681] usbcore: registered new interface driver pegasus
[   51.366064] bttv0: registered device video0
[   51.366127] bttv0: registered device vbi0
[   51.366163] bttv0: PLL: 28636363 => 35468950 .. ok
[   51.398836] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   51.398851] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 20
[   51.421200] bt878: AUDIO driver version 0.0.0 loaded
[   51.421265] bt878: Bt878 AUDIO function found (0).
[   51.421303] ACPI: PCI Interrupt 0000:01:0a.1[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 19
[   51.421314] bt878_probe: card id=[0x1211bd], Unknown card.
[   51.421316] Exiting..
[   51.421324] ACPI: PCI interrupt for device 0000:01:0a.1 disabled
[   51.421331] bt878: probe of 0000:01:0a.1 failed with error -22
[   51.460425] eth0: set allmulti
[   51.461945] eth0: set allmulti
[   51.719399] eth0: set allmulti
[   51.719425] eth0: set allmulti
[   51.831806] lp0: using parport0 (interrupt-driven).
[   51.912152] Adding 3028212k swap on /dev/hda5.  Priority:-1 extents:1 across:3028212k
[   52.335993] EXT3 FS on hda1, internal journal
[   52.759233] NET: Registered protocol family 17
[   56.717919] eth0: set allmulti
[   56.717952] eth0: set allmulti
[   56.927197] NET: Registered protocol family 10
[   56.927352] lo: Disabled Privacy Extensions
[   56.927440] eth0: set allmulti
[   56.927478] eth0: set allmulti
[   58.824994] No dock devices found.
[   58.983274] input: Power Button (FF) as /class/input/input4
[   58.990207] ACPI: Power Button (FF) [PWRF]
[   59.048902] input: Power Button (CM) as /class/input/input5
[   59.055685] ACPI: Power Button (CM) [PWRB]
[   61.463149] eth0: set allmulti
[   63.333269] ppdev: user-space parallel port driver
[   63.771887] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   63.771897] apm: overridden by ACPI.
[   64.049837] Failure registering capabilities with primary security module.
[   64.118796] eth0: set allmulti
[   64.326779] Bluetooth: L2CAP ver 2.8
[   64.326788] Bluetooth: L2CAP socket layer initialized
[   64.407161] Bluetooth: RFCOMM socket layer initialized
[   64.407313] Bluetooth: RFCOMM TTY layer initialized
[   64.407317] Bluetooth: RFCOMM ver 1.8
[   67.753582] eth0: no IPv6 routers present
[ 5928.069469] usb 1-2.2: new full speed USB device using ohci_hcd and address 7
[ 5928.169404] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 5928.200586] usb 1-2.2: configuration #1 chosen from 1 choice
[ 5928.962480] usbcore: registered new interface driver libusual
[ 5929.049557] Initializing USB Mass Storage driver...
[ 5929.051067] scsi0 : SCSI emulation for USB Mass Storage devices
[ 5929.051854] usb-storage: device found at 7
[ 5929.051859] usb-storage: waiting for device to settle before scanning
[ 5929.052092] usbcore: registered new interface driver usb-storage
[ 5929.052213] USB Mass Storage support registered.
[ 5934.048910] usb-storage: device scan complete
[ 5935.143276] scsi 0:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 5935.187197] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 5935.195184] sd 0:0:0:0: [sda] Write Protect is off
[ 5935.195190] sd 0:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 5935.195195] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 5935.201183] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 5935.209177] sd 0:0:0:0: [sda] Write Protect is off
[ 5935.209183] sd 0:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 5935.209186] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 5935.209192]  sda: sda1
[ 5935.240873] sd 0:0:0:0: [sda] Attached SCSI disk
[ 5935.275906] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 6007.725587] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 6007.725603] end_request: I/O error, dev sda, sector 16507
[ 6007.725614] FAT: FAT read failed (blocknr 16444)
[ 6007.731552] usb 1-2.2: USB disconnect, address 7
[ 6018.097304] usb 1-2.2: new full speed USB device using ohci_hcd and address 8
[ 6018.197240] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 6018.228413] usb 1-2.2: configuration #1 chosen from 1 choice
[ 6018.231581] scsi1 : SCSI emulation for USB Mass Storage devices
[ 6018.231857] usb-storage: device found at 8
[ 6018.231861] usb-storage: waiting for device to settle before scanning
[ 6023.229272] usb-storage: device scan complete
[ 6024.641427] scsi 1:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 6024.666365] sd 1:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 6024.674353] sd 1:0:0:0: [sda] Write Protect is off
[ 6024.674359] sd 1:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 6024.674364] sd 1:0:0:0: [sda] Assuming drive cache: write through
[ 6024.680349] sd 1:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 6024.688347] sd 1:0:0:0: [sda] Write Protect is off
[ 6024.688353] sd 1:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 6024.688357] sd 1:0:0:0: [sda] Assuming drive cache: write through
[ 6024.688362]  sda: sda1
[ 6024.713449] sd 1:0:0:0: [sda] Attached SCSI disk
[ 6024.713525] sd 1:0:0:0: Attached scsi generic sg0 type 0
[ 6235.119834] sd 1:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 6235.119849] end_request: I/O error, dev sda, sector 50774
[ 6235.120129] FAT: FAT read failed (blocknr 50711)
[ 6235.125797] usb 1-2.2: USB disconnect, address 8
[ 6242.761195] usb 1-2.2: new full speed USB device using ohci_hcd and address 9
[ 6242.861133] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 6242.892305] usb 1-2.2: configuration #1 chosen from 1 choice
[ 6242.895441] scsi2 : SCSI emulation for USB Mass Storage devices
[ 6242.895752] usb-storage: device found at 9
[ 6242.895756] usb-storage: waiting for device to settle before scanning
[ 6247.893165] usb-storage: device scan complete
[ 6248.980575] scsi 2:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 6249.006469] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 6249.013479] sd 2:0:0:0: [sda] Write Protect is off
[ 6249.013492] sd 2:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 6249.013496] sd 2:0:0:0: [sda] Assuming drive cache: write through
[ 6249.021071] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 6249.028714] sd 2:0:0:0: [sda] Write Protect is off
[ 6249.028721] sd 2:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 6249.028726] sd 2:0:0:0: [sda] Assuming drive cache: write through
[ 6249.028734]  sda: sda1
[ 6249.060864] sd 2:0:0:0: [sda] Attached SCSI disk
[ 6249.060943] sd 2:0:0:0: Attached scsi generic sg0 type 0
[ 6867.189542] sd 2:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 6867.189557] end_request: I/O error, dev sda, sector 141013
[ 6867.189569] FAT: FAT read failed (blocknr 140950)
[ 6867.195500] usb 1-2.2: USB disconnect, address 9
[ 6867.855249] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855311] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855320] FAT: Directory bread(block 305126) failed
[ 6867.855331] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855339] FAT: Directory bread(block 305127) failed
[ 6867.855350] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855358] FAT: Directory bread(block 305128) failed
[ 6867.855368] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855375] FAT: Directory bread(block 305129) failed
[ 6867.855386] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855393] FAT: Directory bread(block 305130) failed
[ 6867.855403] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855410] FAT: Directory bread(block 305131) failed
[ 6867.855421] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855429] FAT: Directory bread(block 305132) failed
[ 6867.855439] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855446] FAT: Directory bread(block 305133) failed
[ 6867.855457] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855464] FAT: Directory bread(block 305134) failed
[ 6867.855475] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855482] FAT: Directory bread(block 305135) failed
[ 6867.855493] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855500] FAT: Directory bread(block 305136) failed
[ 6867.855510] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855518] FAT: Directory bread(block 305137) failed
[ 6867.855528] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855536] FAT: Directory bread(block 305138) failed
[ 6867.855546] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855553] FAT: Directory bread(block 305139) failed
[ 6867.855564] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855572] FAT: Directory bread(block 305140) failed
[ 6867.855582] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855589] FAT: Directory bread(block 305141) failed
[ 6867.855600] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855607] FAT: Directory bread(block 305142) failed
[ 6867.855617] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855625] FAT: Directory bread(block 305143) failed
[ 6867.855635] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855643] FAT: Directory bread(block 305144) failed
[ 6867.855653] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855660] FAT: Directory bread(block 305145) failed
[ 6867.855671] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855678] FAT: Directory bread(block 305146) failed
[ 6867.855689] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855696] FAT: Directory bread(block 305147) failed
[ 6867.855707] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855714] FAT: Directory bread(block 305148) failed
[ 6867.855724] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855732] FAT: Directory bread(block 305149) failed
[ 6867.855742] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855750] FAT: Directory bread(block 305150) failed
[ 6867.855760] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855767] FAT: Directory bread(block 305151) failed
[ 6867.855778] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855786] FAT: Directory bread(block 305152) failed
[ 6867.855796] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855803] FAT: Directory bread(block 305153) failed
[ 6867.855814] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855821] FAT: Directory bread(block 305154) failed
[ 6867.855831] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855839] FAT: Directory bread(block 305155) failed
[ 6867.855849] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855857] FAT: Directory bread(block 305156) failed
[ 6867.855867] scsi 2:0:0:0: rejecting I/O to dead device
[ 6867.855874] FAT: Directory bread(block 305157) failed
[ 6884.264219] usb 1-2.2: new full speed USB device using ohci_hcd and address 10
[ 6884.364154] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 6884.395326] usb 1-2.2: configuration #1 chosen from 1 choice
[ 6884.398476] scsi3 : SCSI emulation for USB Mass Storage devices
[ 6884.398562] usb-storage: device found at 10
[ 6884.398565] usb-storage: waiting for device to settle before scanning
[ 6887.351362] usb 1-2.2: USB disconnect, address 10
[ 6897.279389] usb 1-2.2: new full speed USB device using ohci_hcd and address 11
[ 6897.379325] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 6897.410505] usb 1-2.2: configuration #1 chosen from 1 choice
[ 6897.413687] scsi4 : SCSI emulation for USB Mass Storage devices
[ 6897.413966] usb-storage: device found at 11
[ 6897.413970] usb-storage: waiting for device to settle before scanning
[ 6902.411342] usb-storage: device scan complete
[ 6903.844504] scsi 4:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 6903.869439] sd 4:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 6903.877424] sd 4:0:0:0: [sda] Write Protect is off
[ 6903.877430] sd 4:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 6903.877434] sd 4:0:0:0: [sda] Assuming drive cache: write through
[ 6903.883419] sd 4:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 6903.891415] sd 4:0:0:0: [sda] Write Protect is off
[ 6903.891421] sd 4:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 6903.891425] sd 4:0:0:0: [sda] Assuming drive cache: write through
[ 6903.891430]  sda: sda1
[ 6903.916519] sd 4:0:0:0: [sda] Attached SCSI disk
[ 6903.916598] sd 4:0:0:0: Attached scsi generic sg0 type 0
[ 7318.543926] sd 4:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 7318.543942] end_request: I/O error, dev sda, sector 100621
[ 7318.544222] FAT: FAT read failed (blocknr 100558)
[ 7318.546952] usb 1-2.2: USB disconnect, address 11
[ 7334.072534] usb 1-2.2: new full speed USB device using ohci_hcd and address 12
[ 7334.172471] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 7334.203655] usb 1-2.2: configuration #1 chosen from 1 choice
[ 7334.206822] scsi5 : SCSI emulation for USB Mass Storage devices
[ 7334.207111] usb-storage: device found at 12
[ 7334.207115] usb-storage: waiting for device to settle before scanning
[ 7339.203488] usb-storage: device scan complete
[ 7340.636649] scsi 5:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 7340.661580] sd 5:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 7340.669571] sd 5:0:0:0: [sda] Write Protect is off
[ 7340.669578] sd 5:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 7340.669582] sd 5:0:0:0: [sda] Assuming drive cache: write through
[ 7340.675570] sd 5:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 7340.683561] sd 5:0:0:0: [sda] Write Protect is off
[ 7340.683568] sd 5:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 7340.683571] sd 5:0:0:0: [sda] Assuming drive cache: write through
[ 7340.683577]  sda: sda1
[ 7340.709669] sd 5:0:0:0: [sda] Attached SCSI disk
[ 7340.709748] sd 5:0:0:0: Attached scsi generic sg0 type 0
[ 7378.032080] usb 1-2.2: USB disconnect, address 12
[ 7395.092810] usb 1-2.2: new full speed USB device using ohci_hcd and address 13
[ 7395.192748] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 7395.223931] usb 1-2.2: configuration #1 chosen from 1 choice
[ 7395.227101] scsi6 : SCSI emulation for USB Mass Storage devices
[ 7395.227189] usb-storage: device found at 13
[ 7395.227193] usb-storage: waiting for device to settle before scanning
[ 7400.224763] usb-storage: device scan complete
[ 7402.040688] scsi 6:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 7402.065624] sd 6:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 7402.073614] sd 6:0:0:0: [sda] Write Protect is off
[ 7402.073621] sd 6:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 7402.073625] sd 6:0:0:0: [sda] Assuming drive cache: write through
[ 7402.079616] sd 6:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 7402.087605] sd 6:0:0:0: [sda] Write Protect is off
[ 7402.087611] sd 6:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 7402.087614] sd 6:0:0:0: [sda] Assuming drive cache: write through
[ 7402.087620]  sda: sda1
[ 7402.112713] sd 6:0:0:0: [sda] Attached SCSI disk
[ 7402.112789] sd 6:0:0:0: Attached scsi generic sg0 type 0
[ 7413.434776] usb 1-2.2: USB disconnect, address 13
[ 7419.878899] usb 1-2.2: new full speed USB device using ohci_hcd and address 14
[ 7419.978836] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 7420.009999] usb 1-2.2: configuration #1 chosen from 1 choice
[ 7420.013142] scsi7 : SCSI emulation for USB Mass Storage devices
[ 7420.013460] usb-storage: device found at 14
[ 7420.013464] usb-storage: waiting for device to settle before scanning
[ 7425.011848] usb-storage: device scan complete
[ 7425.754419] scsi 7:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 7425.761362] sd 7:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 7425.769357] sd 7:0:0:0: [sda] Write Protect is off
[ 7425.769363] sd 7:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 7425.769368] sd 7:0:0:0: [sda] Assuming drive cache: write through
[ 7425.775362] sd 7:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 7425.783345] sd 7:0:0:0: [sda] Write Protect is off
[ 7425.783352] sd 7:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 7425.783355] sd 7:0:0:0: [sda] Assuming drive cache: write through
[ 7425.783361]  sda: sda1
[ 7425.810457] sd 7:0:0:0: [sda] Attached SCSI disk
[ 7425.810536] sd 7:0:0:0: Attached scsi generic sg0 type 0
[ 7436.237051] usb 1-2.2: USB disconnect, address 14
[ 7446.867651] usb 1-2.2: new full speed USB device using ohci_hcd and address 15
[ 7446.967587] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 7446.998760] usb 1-2.2: configuration #1 chosen from 1 choice
[ 7447.001916] scsi8 : SCSI emulation for USB Mass Storage devices
[ 7447.002223] usb-storage: device found at 15
[ 7447.002227] usb-storage: waiting for device to settle before scanning
[ 7452.000604] usb-storage: device scan complete
[ 7453.413774] scsi 8:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 7453.438717] sd 8:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 7453.446698] sd 8:0:0:0: [sda] Write Protect is off
[ 7453.446704] sd 8:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 7453.446709] sd 8:0:0:0: [sda] Assuming drive cache: write through
[ 7453.452694] sd 8:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 7453.460688] sd 8:0:0:0: [sda] Write Protect is off
[ 7453.460695] sd 8:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 7453.460698] sd 8:0:0:0: [sda] Assuming drive cache: write through
[ 7453.460704]  sda: sda1
[ 7453.494784] sd 8:0:0:0: [sda] Attached SCSI disk
[ 7453.494858] sd 8:0:0:0: Attached scsi generic sg0 type 0
[ 7630.616093] usb 1-2.2: USB disconnect, address 15
[ 7635.772986] usb 1-2.2: new full speed USB device using ohci_hcd and address 17
[ 7635.872922] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 7635.904097] usb 1-2.2: configuration #1 chosen from 1 choice
[ 7635.969799] scsi9 : SCSI emulation for USB Mass Storage devices
[ 7635.971365] usb-storage: device found at 17
[ 7635.971371] usb-storage: waiting for device to settle before scanning
[ 7637.396014] usb 1-2.2: USB disconnect, address 17
[ 7914.522320] usb 1-2.2: new full speed USB device using ohci_hcd and address 18
[ 7914.622258] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 7914.653431] usb 1-2.2: configuration #1 chosen from 1 choice
[ 7914.656573] scsi10 : SCSI emulation for USB Mass Storage devices
[ 7914.656863] usb-storage: device found at 18
[ 7914.656867] usb-storage: waiting for device to settle before scanning
[ 7919.651281] usb-storage: device scan complete
[ 7921.103426] scsi 10:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 7921.128357] sd 10:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 7921.136348] sd 10:0:0:0: [sda] Write Protect is off
[ 7921.136354] sd 10:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 7921.136359] sd 10:0:0:0: [sda] Assuming drive cache: write through
[ 7921.142344] sd 10:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 7921.150338] sd 10:0:0:0: [sda] Write Protect is off
[ 7921.150344] sd 10:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 7921.150348] sd 10:0:0:0: [sda] Assuming drive cache: write through
[ 7921.150354]  sda: sda1
[ 7921.175446] sd 10:0:0:0: [sda] Attached SCSI disk
[ 7921.175525] sd 10:0:0:0: Attached scsi generic sg0 type 0
[ 8014.385261] usb 1-2.2: USB disconnect, address 18
[ 8029.557134] usb 1-2.2: new full speed USB device using ohci_hcd and address 19
[ 8029.657070] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 8029.688249] usb 1-2.2: configuration #1 chosen from 1 choice
[ 8029.691420] scsi11 : SCSI emulation for USB Mass Storage devices
[ 8029.691710] usb-storage: device found at 19
[ 8029.691714] usb-storage: waiting for device to settle before scanning
[ 8034.689098] usb-storage: device scan complete
[ 8035.436664] scsi 11:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 8035.443601] sd 11:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 8035.451595] sd 11:0:0:0: [sda] Write Protect is off
[ 8035.451601] sd 11:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 8035.451606] sd 11:0:0:0: [sda] Assuming drive cache: write through
[ 8035.457590] sd 11:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 8035.465585] sd 11:0:0:0: [sda] Write Protect is off
[ 8035.465591] sd 11:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 8035.465594] sd 11:0:0:0: [sda] Assuming drive cache: write through
[ 8035.465600]  sda: sda1
[ 8035.484690] sd 11:0:0:0: [sda] Attached SCSI disk
[ 8035.484764] sd 11:0:0:0: Attached scsi generic sg0 type 0
[ 8148.160815] usb 1-2.2: USB disconnect, address 19
[ 8577.134805] usb 1-2.2: new full speed USB device using ohci_hcd and address 20
[ 8577.234742] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 8577.265925] usb 1-2.2: configuration #1 chosen from 1 choice
[ 8577.269071] scsi12 : SCSI emulation for USB Mass Storage devices
[ 8577.269351] usb-storage: device found at 20
[ 8577.269354] usb-storage: waiting for device to settle before scanning
[ 8582.263760] usb-storage: device scan complete
[ 8583.687925] scsi 12:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 8583.712858] sd 12:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 8583.720851] sd 12:0:0:0: [sda] Write Protect is off
[ 8583.720857] sd 12:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 8583.720862] sd 12:0:0:0: [sda] Assuming drive cache: write through
[ 8583.726845] sd 12:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 8583.734842] sd 12:0:0:0: [sda] Write Protect is off
[ 8583.734849] sd 12:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 8583.734852] sd 12:0:0:0: [sda] Assuming drive cache: write through
[ 8583.734858]  sda: sda1
[ 8583.751947] sd 12:0:0:0: [sda] Attached SCSI disk
[ 8583.752021] sd 12:0:0:0: Attached scsi generic sg0 type 0
[ 9071.541537] usb 1-2.2: USB disconnect, address 20
[ 9600.102661] usb 1-2.2: new full speed USB device using ohci_hcd and address 21
[ 9600.202599] usb 1-2.2: not running at top speed; connect to a high speed hub
[ 9600.233777] usb 1-2.2: configuration #1 chosen from 1 choice
[ 9600.236920] scsi13 : SCSI emulation for USB Mass Storage devices
[ 9600.237246] usb-storage: device found at 21
[ 9600.237250] usb-storage: waiting for device to settle before scanning
[ 9605.234621] usb-storage: device scan complete
[ 9606.721741] scsi 13:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[ 9606.746674] sd 13:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 9606.754666] sd 13:0:0:0: [sda] Write Protect is off
[ 9606.754673] sd 13:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 9606.754677] sd 13:0:0:0: [sda] Assuming drive cache: write through
[ 9606.760663] sd 13:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[ 9606.768657] sd 13:0:0:0: [sda] Write Protect is off
[ 9606.768664] sd 13:0:0:0: [sda] Mode Sense: 17 00 00 00
[ 9606.768667] sd 13:0:0:0: [sda] Assuming drive cache: write through
[ 9606.768672]  sda: sda1
[ 9606.793762] sd 13:0:0:0: [sda] Attached SCSI disk
[ 9606.793841] sd 13:0:0:0: Attached scsi generic sg0 type 0
[10042.189874] usb 1-2.2: USB disconnect, address 21
joe@joe-desktop:~$ 

:(

---

### Post by joep on 2007-09-15
managed to fix it by restarting the computer and moving the USB from the hub to the computer. ](*,)

---

### Post by atentik on 2007-12-10
Does that mean every time you need to use the harddrive you have to restart the computer? I have the same problem.... that is why Windows is a bit better

---

### Post by ktheking on 2007-12-21
Problem lies in USB controller of the external HD ,and also on the USB controller on the pci-card,motherboard or hub.

The problem lies in 2 area's :
 -usb power supply : most of the times usb chips on hub,pci-card or motherboard is not able to give enough power.
 -usb 1.1 , usb 2.0 : Backward compatibility problem : many controllers have issues on getting this sorted ,and are not able to make an agreement on which speed they will work with one another. This problem lies in combination of both HD controller and motherboard/pci-card/hub controller. Here this instability may be caused by a bad driver as well (which doesn't handle speed agreement well).

Certain hardware will work better under Linux. Some better under Windoze.

So the message is : always try you thing with some different controllers (on both sides).

Greetz ,

K.
I work with usb since the early version of Windoze 95 ,hence this knowledge. I am also a reseller of all sorts equipment and have a business in computer repairs.
I'm an electronics's engineer converted to IT. This is why I look at IT problems always a bit differently.

---

