---
title: "Configuració Avermedia AverTV Hybrid+fm PCI"
date: 2008-09-02
forum: Catalan Team
---

### Post by bolidoone on 2008-09-02
Estic intentant configurar aquesta tarja capturadora/sintonitzadora de tdt i no m'ensurtu.

Avermedia Avertv hybrid+fm 16d/c PCI amb xip Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

Hi es instal.lada a Un Amd Athlon 64 3800+ i amb una placa base Gigabyte,estic utilitzant Ubuntu 8.04 i,per ara no em reconeix la tarja el sistema.

Em podeu donar un cop de má.

Gracies.

---

### Post by patrickfromspain on 2008-09-02
enganxans el que et dona al fer dmesg i lspci

salut

---

### Post by bolidoone on 2008-09-02
Hola Patrickfromspain,bona nit.
El resultat de dmesg es:

[   28.548955] ACPI: Interpreter enabled
[   28.548957] ACPI: (supports S0 S1 S4 S5)
[   28.548972] ACPI: Using IOAPIC for interrupt routing
[   28.558059] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.559137] PCI: Transparent bridge - 0000:00:10.0
[   28.559155] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.559424] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   28.642649] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.642806] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
[   28.642959] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   28.643111] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.643263] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.643416] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.643569] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[   28.643720] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.643876] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   28.644028] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.644181] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[   28.644332] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.644485] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[   28.644643] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.644795] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.644948] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   28.645105] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[   28.645257] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.645411] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   28.645564] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[   28.645754] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   28.645937] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   28.646117] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   28.646297] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   28.646477] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   28.646658] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   28.646839] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[   28.647020] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   28.647202] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   28.647383] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   28.647565] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   28.647748] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   28.647930] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   28.648112] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   28.648298] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   28.648480] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   28.648665] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   28.648847] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   28.649029] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   28.649211] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   28.649394] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   28.649521] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.649548] pnp: PnP ACPI init
[   28.649557] ACPI: bus type pnp registered
[   28.654334] pnp: PnP ACPI: found 14 devices
[   28.654337] ACPI: ACPI bus type pnp unregistered
[   28.654563] PCI: Using ACPI for IRQ routing
[   28.654568] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.664563] NET: Registered protocol family 8
[   28.664564] NET: Registered protocol family 20
[   28.664690] AppArmor: AppArmor Filesystem Enabled
[   28.676537] system 00:01: ioport range 0x1000-0x107f has been reserved
[   28.676540] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   28.676542] system 00:01: ioport range 0x1400-0x147f has been reserved
[   28.676545] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   28.676547] system 00:01: ioport range 0x1800-0x187f has been reserved
[   28.676549] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   28.676552] system 00:01: ioport range 0x2000-0x207f has been reserved
[   28.676554] system 00:01: ioport range 0x2080-0x20ff has been reserved
[   28.676558] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   28.676560] system 00:01: iomem range 0x3c000000-0x3fffffff could not be reserved
[   28.676563] system 00:01: iomem range 0xf0000000-0xf1ffffff could not be reserved
[   28.676569] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   28.676571] system 00:02: ioport range 0x800-0x87f has been reserved
[   28.676574] system 00:02: ioport range 0x295-0x314 has been reserved
[   28.676576] system 00:02: ioport range 0x290-0x294 has been reserved
[   28.676587] system 00:0d: iomem range 0xf0000-0xf3fff could not be reserved
[   28.676590] system 00:0d: iomem range 0xf4000-0xf7fff could not be reserved
[   28.676592] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   28.676595] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   28.676597] system 00:0d: iomem range 0x3bff0000-0x3bffffff could not be reserved
[   28.676600] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[   28.676602] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   28.676604] system 00:0d: iomem range 0x100000-0x3bfeffff could not be reserved
[   28.676607] system 00:0d: iomem range 0x3c000000-0x3fffffff could not be reserved
[   28.676609] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[   28.676612] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   28.677001] PCI: Bridge: 0000:00:02.0
[   28.677004]   IO window: 8000-8fff
[   28.677007]   MEM window: disabled.
[   28.677008]   PREFETCH window: disabled.
[   28.677011] PCI: Bridge: 0000:00:03.0
[   28.677012]   IO window: 9000-9fff
[   28.677014]   MEM window: disabled.
[   28.677016]   PREFETCH window: disabled.
[   28.677018] PCI: Bridge: 0000:00:04.0
[   28.677019]   IO window: a000-afff
[   28.677021]   MEM window: disabled.
[   28.677023]   PREFETCH window: disabled.
[   28.677026] PCI: Bridge: 0000:00:10.0
[   28.677027]   IO window: disabled.
[   28.677029]   MEM window: f5000000-f50fffff
[   28.677031]   PREFETCH window: disabled.
[   28.677046] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   28.677052] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   28.677058] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   28.677065] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   28.677116] NET: Registered protocol family 2
[   28.680498] Time: acpi_pm clocksource has been installed.
[   28.680515] Switched to high resolution mode on CPU 0
[   28.679606] Switched to high resolution mode on CPU 1
[   28.712517] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   28.713001] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   28.714366] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   28.715036] TCP: Hash tables configured (established 131072 bind 65536)
[   28.715040] TCP reno registered
[   28.724566] checking if image is initramfs... it is
[   29.325188] Freeing initrd memory: 7536k freed
[   29.331305] audit: initializing netlink socket (disabled)
[   29.331319] audit(1220318133.336:1): initialized
[   29.333268] VFS: Disk quotas dquot_6.5.1
[   29.333345] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   29.333480] io scheduler noop registered
[   29.333482] io scheduler anticipatory registered
[   29.333484] io scheduler deadline registered
[   29.333580] io scheduler cfq registered (default)
[   29.333594] pci 0000:00:00.0: Enabling HT MSI Mapping
[   29.333623] pci 0000:00:02.0: Enabling HT MSI Mapping
[   29.333631] pci 0000:00:03.0: Enabling HT MSI Mapping
[   29.333639] pci 0000:00:04.0: Enabling HT MSI Mapping
[   29.333647] Boot video device is 0000:00:05.0
[   29.333667] pci 0000:00:09.0: Enabling HT MSI Mapping
[   29.347942] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   29.347956] pci 0000:00:0f.0: Enabling HT MSI Mapping
[   29.347964] pci 0000:00:10.0: Enabling HT MSI Mapping
[   29.347974] pci 0000:00:10.1: Enabling HT MSI Mapping
[   29.348152] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.348171] assign_interrupt_mode Found MSI capability
[   29.348189] Allocate Port Service[0000:00:02.0:pcie00]
[   29.348248] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   29.348267] assign_interrupt_mode Found MSI capability
[   29.348280] Allocate Port Service[0000:00:03.0:pcie00]
[   29.348331] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   29.348350] assign_interrupt_mode Found MSI capability
[   29.348363] Allocate Port Service[0000:00:04.0:pcie00]
[   29.375285] Real Time Clock Driver v1.12ac
[   29.375392] Linux agpgart interface v0.102
[   29.375394] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.375526] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.375683] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.376196] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.376474] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.377192] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.377255] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   29.377346] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   29.376684] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.376692] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.395578] mice: PS/2 mouse device common for all mice
[   29.395625] cpuidle: using governor ladder
[   29.395627] cpuidle: using governor menu
[   29.395760] NET: Registered protocol family 1
[   29.395869] registered taskstats version 1
[   29.396003]   Magic number: 8:987:254
[   29.396034]   hash matches device ttytd
[   29.396135] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   29.396138] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   29.396139] EDD information not available.
[   29.396150] Freeing unused kernel memory: 320k freed
[   29.417445] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   30.602591] fuse init (API version 7.9)
[   31.139794] usbcore: registered new interface driver usbfs
[   31.139822] usbcore: registered new interface driver hub
[   31.141621] SCSI subsystem initialized
[   31.148536] usbcore: registered new device driver usb
[   31.158958] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   31.159325] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   31.159334] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   31.159340] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   31.160921] libata version 3.00 loaded.
[   31.166065] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   31.217729] Floppy drive(s): fd0 is 1.44M
[   31.236861] FDC 0 is a post-1991 82077
[   31.676809] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:16:e6:1d:27:0f
[   31.676815] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   31.677048] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   31.677417] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[   31.677425] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 22
[   31.677443] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   31.677450] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[   31.677739] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[   31.677742] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 21 (level, low) -> IRQ 21
[   31.677759] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   31.677765] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[   31.677184] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   31.677195] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 20
[   31.677425] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   31.677433] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   31.677684] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   31.677720] ehci_hcd 0000:00:0b.1: debug port 1
[   31.677724] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   31.677735] ehci_hcd 0000:00:0b.1: irq 20, io mem 0xf5104000
[   31.688339] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.688469] usb usb1: configuration #1 chosen from 1 choice
[   31.688493] hub 1-0:1.0: USB hub found
[   31.688498] hub 1-0:1.0: 8 ports detected
[   31.793012] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   31.793017] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   31.793204] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   31.793212] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   31.793272] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   31.793292] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xf5108000
[   31.849251] usb usb2: configuration #1 chosen from 1 choice
[   31.849278] hub 2-0:1.0: USB hub found
[   31.849288] hub 2-0:1.0: 8 ports detected
[   31.952565] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   31.952575] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   32.002640] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f5004000-f50047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   32.008001] pata_amd 0000:00:0d.0: version 0.3.10
[   32.008054] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   32.020348] scsi0 : pata_amd
[   32.022869] scsi1 : pata_amd
[   32.023586] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   32.023589] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   32.514483] ata1.00: HPA unlocked: 117229295 -> 117231408, native 117231408
[   32.514489] ata1.00: ATA-6: ST360015A, 3.33, max UDMA/100
[   32.514492] ata1.00: 117231408 sectors, multi 16: LBA 
[   32.514508] ata1.01: ATAPI: CDRW5224, P1.4, max UDMA/33
[   32.530583] ata1.00: configured for UDMA/100
[   32.539166] usb 1-7: new high speed USB device using ehci_hcd and address 4
[   32.673774] usb 1-7: configuration #1 chosen from 1 choice
[   32.695294] ata1.01: configured for UDMA/33
[   32.913649] usb 1-8: new high speed USB device using ehci_hcd and address 5
[   33.178575] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4082B, A201, max UDMA/33
[   33.178593] ata2.01: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A103, max UDMA/33
[   33.274240] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0016e60000c385ec]
[   33.350272] ata2.00: configured for UDMA/33
[   33.521041] ata2.01: configured for UDMA/33
[   33.522170] scsi 0:0:0:0: Direct-Access     ATA      ST360015A        3.33 PQ: 0 ANSI: 5
[   33.522461] scsi 0:0:1:0: CD-ROM            PHILIPS  CDRW5224         P1.4 PQ: 0 ANSI: 5
[   33.526738] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4082B A201 PQ: 0 ANSI: 5
[   33.530560] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A103 PQ: 0 ANSI: 5
[   33.530747] sata_nv 0000:00:0e.0: version 3.5
[   33.530761] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 22
[   33.530993] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   33.532014] scsi2 : sata_nv
[   33.532478] scsi3 : sata_nv
[   33.532656] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 22
[   33.532659] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 22
[   33.538000] Driver 'sd' needs updating - please use bus_type methods
[   33.538091] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   33.538103] sd 0:0:0:0: [sda] Write Protect is off
[   33.538106] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.538121] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.538165] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   33.538173] sd 0:0:0:0: [sda] Write Protect is off
[   33.538175] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.538188] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.538191]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   33.555263]  sda1 sda2 < sda5 >
[   33.579409] sd 0:0:0:0: [sda] Attached SCSI disk
[   33.583390] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   33.583412] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   33.583428] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   33.583445] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   33.585545] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   33.585551] Uniform CD-ROM driver Revision: 3.20
[   33.585616] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   33.607521] sr1: scsi3-mmc drive: 32x/32x writer dvd-ram cd/rw xa/form2 cdda tray
[   33.607585] sr 1:0:0:0: Attached scsi CD-ROM sr1
[   33.626846] sr2: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   33.626883] sr 1:0:1:0: Attached scsi CD-ROM sr2
[   33.632521] usb 1-8: configuration #1 chosen from 1 choice
[   33.841375] ata3: SATA link down (SStatus 0 SControl 300)
[   33.932246] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   34.160917] ata4: SATA link down (SStatus 0 SControl 300)
[   34.172480] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 21 (level, low) -> IRQ 21
[   34.171695] usb 2-1: configuration #1 chosen from 1 choice
[   34.172734] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   34.172850] scsi4 : sata_nv
[   34.172942] scsi5 : sata_nv
[   34.173109] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 21
[   34.173112] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 21
[   34.475491] usb 2-5: new full speed USB device using ohci_hcd and address 3
[   34.480494] ata5: SATA link down (SStatus 0 SControl 300)
[   34.678487] usb 2-5: configuration #1 chosen from 1 choice
[   34.681606] usbcore: registered new interface driver libusual
[   34.686509] Initializing USB Mass Storage driver...
[   34.686590] scsi6 : SCSI emulation for USB Mass Storage devices
[   34.686656] usb-storage: device found at 4
[   34.686658] usb-storage: waiting for device to settle before scanning
[   34.686690] scsi7 : SCSI emulation for USB Mass Storage devices
[   34.686750] usbcore: registered new interface driver usb-storage
[   34.686753] USB Mass Storage support registered.
[   34.686887] usb-storage: device found at 5
[   34.686889] usb-storage: waiting for device to settle before scanning
[   34.955857] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   34.963946] ata6.00: ATA-7: Maxtor 6L300S0, BANC1G10, max UDMA/133
[   34.963950] ata6.00: 586114704 sectors, multi 16: LBA48 NCQ (not used)
[   34.979908] ata6.00: configured for UDMA/133
[   34.981041] scsi 5:0:0:0: Direct-Access     ATA      Maxtor 6L300S0   BANC PQ: 0 ANSI: 5
[   34.981114] sd 5:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
[   34.981125] sd 5:0:0:0: [sdb] Write Protect is off
[   34.981127] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   34.981143] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.981190] sd 5:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
[   34.981199] sd 5:0:0:0: [sdb] Write Protect is off
[   34.981201] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   34.981215] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.981220]  sdb: sdb1
[   35.002311] sd 5:0:0:0: [sdb] Attached SCSI disk
[   35.002358] sd 5:0:0:0: Attached scsi generic sg4 type 0
[   35.116196] Attempting manual resume
[   35.116200] swsusp: Resume From Partition 8:5
[   35.116202] PM: Checking swsusp image.
[   35.115387] PM: Resume from disk failed.
[   35.163088] kjournald starting.  Commit interval 5 seconds
[   35.162092] EXT3-fs: mounted filesystem with ordered data mode.
[   39.676380] usb-storage: device scan complete
[   39.679364] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   39.678404] usb-storage: device scan complete
[   39.680607] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   39.682350] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   39.684346] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   39.688367] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   39.688397] sd 6:0:0:0: Attached scsi generic sg5 type 0
[   39.691357] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[   39.691384] sd 6:0:0:1: Attached scsi generic sg6 type 0
[   39.691441] scsi 7:0:0:0: Direct-Access     JetFlash TS8GJFV10        8.07 PQ: 0 ANSI: 2
[   39.695348] sd 6:0:0:2: [sde] Attached SCSI removable disk
[   39.695374] sd 6:0:0:2: Attached scsi generic sg7 type 0
[   39.699344] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[   39.699365] sd 6:0:0:3: Attached scsi generic sg8 type 0
[   39.706311] sd 7:0:0:0: [sdg] 15974400 512-byte hardware sectors (8179 MB)
[   39.709185] sd 7:0:0:0: [sdg] Write Protect is off
[   39.709187] sd 7:0:0:0: [sdg] Mode Sense: 03 00 00 00
[   39.709189] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[   39.719292] sd 7:0:0:0: [sdg] 15974400 512-byte hardware sectors (8179 MB)
[   39.722168] sd 7:0:0:0: [sdg] Write Protect is off
[   39.722170] sd 7:0:0:0: [sdg] Mode Sense: 03 00 00 00
[   39.722172] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[   39.722175]  sdg: sdg1
[   39.724347] sd 7:0:0:0: [sdg] Attached SCSI removable disk
[   39.724372] sd 7:0:0:0: Attached scsi generic sg9 type 0
[   43.449178] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.490012] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.572031] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   43.604281] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   43.604299] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   43.639763] nvidia: module license 'NVIDIA' taints kernel.
[   44.101138] input: Power Button (FF) as /devices/virtual/input/input3
[   44.123194] ACPI: Power Button (FF) [PWRF]
[   44.123267] input: Power Button (CM) as /devices/virtual/input/input4
[   44.147230] parport_pc 00:0a: reported by Plug and Play ACPI
[   44.147285] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   44.155204] ACPI: Power Button (CM) [PWRB]
[   44.188153] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   44.188164] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 16
[   44.188170] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   44.188342] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   44.215866] Linux video capture interface: v2.00
[   44.742302] saa7130/34: v4l2 driver version 0.2.14 loaded
[   44.742747] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   44.742757] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   44.742765] saa7133[0]: found at 0000:01:07.0, rev: 209, irq: 17, latency: 32, mmio: 0xf5005000
[   44.742772] saa7133[0]: subsystem: 1461:f936, board: UNKNOWN/GENERIC [card=0,autodetected]
[   44.742783] saa7133[0]: board init: gpio is 2fe00
[   44.877997] saa7133[0]: i2c eeprom 00: 61 14 36 f9 00 00 00 00 00 00 00 00 00 00 00 00
[   44.878007] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   44.878013] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 00 08 ff 00 0e ff ff ff ff
[   44.878018] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   44.878024] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
[   44.878029] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   44.878034] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   44.878039] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   44.898769] saa7133[0]: registered device video0 [v4l2]
[   44.898795] saa7133[0]: registered device vbi0
[   44.985972] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   45.231402] saa7134 ALSA driver for DMA sound loaded
[   45.231434] saa7133[0]/alsa: saa7133[0] at 0xf5005000 irq 17 registered as card -2
[   45.349019] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   45.349025] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 22
[   45.349214] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   45.425951] Bluetooth: Core ver 2.11
[   45.435268] NET: Registered protocol family 31
[   45.435272] Bluetooth: HCI device and connection manager initialized
[   45.435278] Bluetooth: HCI socket layer initialized
[   45.443964] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/ov511/ov511.c: USB OV511+ video device found
[   45.445074] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/ov511/ov511.c: model: Generic Camera (no ID)
[   45.472055] Bluetooth: HCI USB driver ver 2.9
[   45.986286] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/ov511/ov511.c: Sensor is an OV7620
[   47.340543] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/ov511/ov511.c: Device at usb-0000:00:0b.0-5 registered to minor 1
[   47.340577] usbcore: registered new interface driver ov511
[   47.340581] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver
[   47.340756] usbcore: registered new interface driver hci_usb
[   48.392378] lp0: using parport0 (interrupt-driven).
[   48.806632] Adding 2433808k swap on /dev/sda5.  Priority:-1 extents:1 across:2433808k
[   49.362074] EXT3 FS on sda1, internal journal
[   50.674472] ip_tables: (C) 2000-2006 Netfilter Core Team
[   51.063594] No dock devices found.
[   51.424620] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[   51.425748] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xa
[   51.425753] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xc
[   51.425755] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   52.524468] ppdev: user-space parallel port driver
[   52.739088] audit(1220318157.465:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5568 profile="/usr/sbin/cupsd" namespace="default"
[   54.444308] Clocksource tsc unstable (delta = -123610159 ns)
[   54.605037] Bluetooth: L2CAP ver 2.9
[   54.605041] Bluetooth: L2CAP socket layer initialized
[   54.646981] Bluetooth: RFCOMM socket layer initialized
[   54.646998] Bluetooth: RFCOMM TTY layer initialized
[   54.646999] Bluetooth: RFCOMM ver 1.8
[   56.330123] NET: Registered protocol family 17
[   57.507105] NET: Registered protocol family 10
[   57.507306] lo: Disabled Privacy Extensions
[   62.544582] eth0: no IPv6 routers present
[16222.408154] usb 2-6: new full speed USB device using ohci_hcd and address 4
[16222.518027] usb 2-6: configuration #1 chosen from 1 choice
[16222.601871] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[16222.602104] usbcore: registered new interface driver usblp

i el resultat de fer lspci es:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Es una mica extens,ho sento.

---

### Post by papapep on 2008-09-02
Quan és tan llarg, adjunteu-ho amb un fitxer de text, si us plau.

---

### Post by bolidoone on 2008-09-02
Perdona papapep,no ho savia,hara ja se com ho feu,el proper cop,amb fitxer de text

---

### Post by patrickfromspain on 2008-09-03
be, sembla que la cosa no pinta molt malament, no?

Instal·la el kaffeine: sudo apt-get install kaffeine

quan l'obres, tens una opcio per veure la tele?

---

### Post by bolidoone on 2008-09-03
Ja tenia instal.lat Kaffeine,no tinc la opcio de veure la tele.

---

### Post by bolidoone on 2008-09-03
Us explico els passos que he seguit a traves d'un forum que en va dir en papapep,el forum es:

[http://zonabuologica.wordpress.com/2007/12/04/configurar-avermedia-avertv-hybrid-fm-pci-chip-saa7134/](http://zonabuologica.wordpress.com/2007/12/04/configurar-avermedia-avertv-hybrid-fm-pci-chip-saa7134/)

He fet:

dmesg | grep saa7134ç

i el resultat es aquet:

[   45.231402] saa7134 ALSA driver for DMA sound loaded
[38561.296470] saa7134 ALSA driver for DMA sound unloaded

No em surt res de lo que em diuem,de totes maneres,vaig intentar carregar els moduls que em deien al mateix forum fent aixó:

sudo rmmod saa7134_alsa saa7134-dvb saa7134

i el resultat va ser aquet:

ERROR: Module saa7134_alsa does not exist in /proc/modules
ERROR: Module saa7134_dvb does not exist in /proc/modules
ERROR: Module saa7134 does not exist in /proc/modules

Despres d'aixo no he fet res mes,no se com continuar.

Espero que serveixi d'ajut.

---

### Post by papapep on 2008-09-03
És que l'rmmod no carrega els mòduls, precisament els _descarrega_ (**rm**mod->remove module (elimina mòdul)) :-)

Seguint amb la pàgina d'on has mirat les instruccions, fixa't que ara hauries de provar a carregar els mòduls de nou, a veure si funciona. Fes-ho d'un en un, a veure què tal respon.

```
sudo modprobe saa7134 card=99
sudo modprobe saa7134_alsa
sudo modprobe saa7134-dvb
```

---

### Post by bolidoone on 2008-09-05
He provat a carregar els moduls,quan he fet:

sudo modprobe saa7134 card=99

M'ha demanat contrasnya d'usuari,per a:

sudo modprobe saa7134_alsa
sudo modprobe saa7134-dvb

no ha demanat res,tampoc he vist linies que indiquessin la carrega dels moduls,segueix igual,Kaffeine no em dona opcio de veure tv i tvtime tampoc.

Saluts.

---

### Post by papapep on 2008-09-05
Fes:

```
lsmod |grep saa7134
```

a veure si els ha carregat correctament (si has aturat i tornat a engegar l'ordinador entre els modprobe i ara, els hauràs de tornar a fer). En teoria si no t'ha donat cap missatge d'error el modprobe, vol dir que sí.

---

### Post by bolidoone on 2008-09-05
Crec que si els ha copiat,el resultat es aquet:

saa7134_dvb            19596  0 
videobuf_dvb            8708  1 saa7134_dvb
tda1004x               18820  1 saa7134_dvb
saa7134_alsa           17248  0 
snd_pcm                92168  3 snd_hda_intel,saa7134_alsa,snd_pcm_oss
saa7134               152280  2 saa7134_dvb,saa7134_alsa
compat_ioctl32         11136  1 saa7134
videobuf_dma_sg        17028  4 saa7134_dvb,videobuf_dvb,saa7134_alsa,saa7134
videobuf_core          22020  3 videobuf_dvb,saa7134,videobuf_dma_sg
ir_kbd_i2c             12560  1 saa7134
ir_common              39812  2 saa7134,ir_kbd_i2c
snd                    70856  18 snd_hda_intel,snd_hwdep,snd_seq_dummy,saa7134_alsa,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               30720  2 ov511,saa7134
v4l2_common            21888  3 saa7134,compat_ioctl32,videodev
v4l1_compat            15492  2 saa7134,videodev
i2c_core               28544  6 saa7134_dvb,tda1004x,saa7134,ir_kbd_i2c,i2c_nforce2,nvidia

---

### Post by papapep on 2008-09-05
Bé, i si ara engegues el Kaffeine, no tens aquest botó?

---

### Post by bolidoone on 2008-09-06
No el tinc,em surten cinc botons.

---

### Post by papapep on 2008-09-06
Seria interessant que identifiquessis la teva targeta entre les que surten aquí:

[http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#AVerMedia](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#AVerMedia)

---

### Post by bolidoone on 2008-09-07
La meva tarja es aquesta:

AVerTV Hybrid+FM PCI (A16D)

---

### Post by patrickfromspain on 2008-09-07
Sembla que no pinta massa bé.

La part analogica esta implementada al kernel 2.6.26, i per tant no deu ser al kernel d'ubuntu. 

La part digital sembla que seguint aquestes indicacions es pot fer funcionar: [http://mcentral.de/wiki/index.php5/AVerMedia_AverTV_Hybrid_FM_PCI_A16D](http://mcentral.de/wiki/index.php5/AVerMedia_AverTV_Hybrid_FM_PCI_A16D)

salut

---

