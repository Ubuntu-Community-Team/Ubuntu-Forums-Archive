---
title: "[SOLVED] Sick hdd?"
date: 2009-01-06
forum: General Help
---

### Post by archolman on 2009-01-06
```
After  searching forums, I think I have an answer for the symptoms I've been getting, but it's not good. I think I have a sick HDD.:(

I thank the person who gave someone else the code snippet
"dmesg",  which returned (sorry it's so long, but I don't know how to enclose it in a scrollable box) the following;


[    0.876352] bus: 01 index 3 io port: [0, ffff]
[    0.876409] bus: 01 index 4 mmio: [0, ffffffff]
[    0.876498] NET: Registered protocol family 2
[    0.876943] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.877664] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.877937] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.878207] TCP: Hash tables configured (established 8192 bind 8192)
[    0.878272] TCP reno registered
[    0.878682] NET: Registered protocol family 1
[    0.879109] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.600067]  it is
[    2.538578] Freeing initrd memory: 7942k freed
[    2.541193] audit: initializing netlink socket (disabled)
[    2.541300] type=2000 audit(1231245425.540:1): initialized
[    2.555026] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.563663] VFS: Disk quotas dquot_6.5.1
[    2.564132] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.564564] msgmni has been set to 494
[    2.566218] io scheduler noop registered
[    2.566283] io scheduler anticipatory registered
[    2.566340] io scheduler deadline registered
[    2.566441] io scheduler cfq registered (default)
[    2.566536] pci 0000:00:02.0: Boot video device
[    2.566621] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    2.567740] isapnp: Scanning for PnP cards...
[    2.921587] isapnp: No Plug & Play device found
[    3.086535] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.086852] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.087470] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.089903] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.091106] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.097048] brd: module loaded
[    3.097350] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.097805] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.100980] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.101057] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.102683] mice: PS/2 mouse device common for all mice
[    3.103262] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    3.103359] rtc0: alarms up to one month
[    3.103805] EISA: Probing bus 0 at eisa.0
[    3.103910] EISA: Detected 0 cards.
[    3.103968] cpuidle: using governor ladder
[    3.104069] cpuidle: using governor menu
[    3.105678] TCP cubic registered
[    3.105812] Using IPI No-Shortcut mode
[    3.106828] registered taskstats version 1
[    3.107150]   Magic number: 9:271:632
[    3.107385] tty ptycb: hash matches
[    3.107639] rtc_cmos 00:02: setting system clock to 2009-01-06 12:37:06 UTC (1231245426)
[    3.107723] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.107784] EDD information not available.
[    3.109493] Freeing unused kernel memory: 424k freed
[    3.109720] Write protecting the kernel text: 2576k
[    3.109870] Write protecting the kernel read-only data: 936k
[    3.130045] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.527290] fuse init (API version 7.9)
[    3.603931] processor ACPI0007:00: registered as cooling_device0
[    4.972216] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    4.972292] e100: Copyright(c) 1999-2006 Intel Corporation
[    4.972885] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    4.972950] PCI: setting IRQ 11 as level-triggered
[    4.972959] e100 0000:01:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    4.995501] e100 0000:01:08.0: PME# disabled
[    5.074685] e100: eth0: e100_probe: addr 0xff8f7000, irq 11, MAC addr 00:03:47:a4:9b:76
[    5.086896] No dock devices found.
[    5.318173] SCSI subsystem initialized
[    5.365913] usbcore: registered new interface driver usbfs
[    5.366049] usbcore: registered new interface driver hub
[    5.366283] usbcore: registered new device driver usb
[    5.428875] USB Universal Host Controller Interface driver v3.0
[    5.429562] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    5.429629] uhci_hcd 0000:00:1f.2: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    5.429724] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    5.429732] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    5.429922] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    5.430042] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ef40
[    5.430600] usb usb1: configuration #1 chosen from 1 choice
[    5.430732] hub 1-0:1.0: USB hub found
[    5.430809] hub 1-0:1.0: 2 ports detected
[    5.434616] libata version 3.00 loaded.
[    5.533404] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    5.533485] PCI: setting IRQ 10 as level-triggered
[    5.533495] uhci_hcd 0000:00:1f.4: PCI INT C -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    5.533589] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    5.533596] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    5.533737] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    5.533858] uhci_hcd 0000:00:1f.4: irq 10, io base 0x0000ef80
[    5.534301] usb usb2: configuration #1 chosen from 1 choice
[    5.534437] hub 2-0:1.0: USB hub found
[    5.534516] hub 2-0:1.0: 2 ports detected
[    5.636979] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    5.658589] ata_piix 0000:00:1f.1: version 2.12
[    5.658739] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.660799] scsi0 : ata_piix
[    5.661363] scsi1 : ata_piix
[    5.664460] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    5.664529] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    5.828487] ata1.00: ATA-7: Maxtor 2F040L0, VAM51JJ0, max UDMA/133
[    5.828566] ata1.00: 78165360 sectors, multi 16: LBA48 
[    5.844388] ata1.00: configured for UDMA/100
[    6.000715] ata2.00: ATAPI: HL-DT-ST GCE-8527B, 1.01, max UDMA/33
[    6.032462] ata2.00: configured for UDMA/33
[    6.032901] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2F040L0   VAM5 PQ: 0 ANSI: 5
[    6.033636] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8527B  1.01 PQ: 0 ANSI: 5
[    7.215477] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.215659] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    7.292109] Driver 'sd' needs updating - please use bus_type methods
[    7.292546] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[    7.292670] sd 0:0:0:0: [sda] Write Protect is off
[    7.292731] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.292839] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.293116] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[    7.293219] sd 0:0:0:0: [sda] Write Protect is off
[    7.293279] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.293364] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.293453]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.312187]  sda1 sda2 < sda5 >
[    7.342055] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.358905] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    7.358991] Uniform CD-ROM driver Revision: 3.20
[    7.359362] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.735515] PM: Starting manual resume from disk
[    7.735585] PM: Resume from partition 8:5
[    7.735590] PM: Checking hibernation image.
[    7.736106] PM: Resume from disk failed.
[    7.849608] kjournald starting.  Commit interval 5 seconds
[    7.849718] EXT3-fs: mounted filesystem with ordered data mode.
[   16.867070] udevd version 124 started
[   18.666558] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.827559] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.949015] Linux agpgart interface v0.103
[   19.012181] iTCO_vendor_support: vendor-support=0
[   19.077683] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   19.079941] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   19.080107] iTCO_wdt: No card detected
[   19.173581] agpgart-intel 0000:00:00.0: Intel i815 Chipset
[   19.269967] intel_rng: Firmware space is locked read-only. If you can't or
[   19.269973] intel_rng: don't want to disable this in firmware setup, and if
[   19.269977] intel_rng: you are certain that your system has a functional
[   19.269980] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   19.297998] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   19.581758] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   20.110320] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   20.125381] ACPI: Power Button (FF) [PWRF]
[   20.125796] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   20.136137] ACPI: Sleep Button (CM) [SBTN]
[   22.879480] parport_pc 00:0a: reported by Plug and Play ACPI
[   22.879587] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   23.806348] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[   23.806428] Yamaha DS-1 PCI 0000:01:09.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[   23.808112] firmware: requesting yamaha/ds1_dsp.fw
[   24.164603] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   28.793894] firmware: requesting yamaha/ds1_ctrl.fw
[   29.755425] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   29.755507] PCI: setting IRQ 9 as level-triggered
[   29.755516] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[   29.755634] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   30.376045] intel8x0_measure_ac97_clock: measured 55929 usecs
[   30.376124] intel8x0: clocking to 41143
[   30.775195] lp0: using parport0 (interrupt-driven).
[   31.092361] Adding 738948k swap on /dev/sda5.  Priority:-1 extents:1 across:738948k
[   31.660434] EXT3 FS on sda1, internal journal
[   32.573558] type=1505 audit(1231245456.025:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3730
[   33.135161] type=1505 audit(1231245456.585:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3735
[   33.136383] type=1505 audit(1231245456.589:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3735
[   33.358069] ip_tables: (C) 2000-2006 Netfilter Core Team
[   33.496186] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   34.801728] NET: Registered protocol family 17
[   35.968682] NET: Registered protocol family 10
[   35.970010] lo: Disabled Privacy Extensions
[   36.284394] warning: `ntpd' uses 32-bit capabilities (legacy support in use)
[   46.524027] eth0: no IPv6 routers present
[   56.522044] ACPI: WMI: Mapper loaded
[   60.281578] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   60.281676] ata1.00: BMDMA stat 0x24
[   60.281744] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[   60.281747]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[   60.281899] ata1.00: status: { DRDY ERR }
[   60.281956] ata1.00: error: { UNC }
[   60.304259] ata1.00: configured for UDMA/100
[   60.304289] ata1: EH complete
[   62.623964] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   62.624060] ata1.00: BMDMA stat 0x24
[   62.624125] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[   62.624129]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[   62.624280] ata1.00: status: { DRDY ERR }
[   62.624337] ata1.00: error: { UNC }
[   62.648256] ata1.00: configured for UDMA/100
[   62.648280] ata1: EH complete
[   64.944386] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   64.944458] ata1.00: BMDMA stat 0x24
[   64.944522] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[   64.944526]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[   64.944678] ata1.00: status: { DRDY ERR }
[   64.944734] ata1.00: error: { UNC }
[   64.968256] ata1.00: configured for UDMA/100
[   64.968278] ata1: EH complete
[   67.264813] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   67.264887] ata1.00: BMDMA stat 0x24
[   67.264951] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[   67.264955]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[   67.265107] ata1.00: status: { DRDY ERR }
[   67.265163] ata1.00: error: { UNC }
[   67.288256] ata1.00: configured for UDMA/100
[   67.288279] ata1: EH complete
[   69.585231] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   69.585302] ata1.00: BMDMA stat 0x24
[   69.585366] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[   69.585370]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[   69.585521] ata1.00: status: { DRDY ERR }
[   69.585578] ata1.00: error: { UNC }
[   69.608255] ata1.00: configured for UDMA/100
[   69.608279] ata1: EH complete
[   71.905652] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   71.905724] ata1.00: BMDMA stat 0x24
[   71.905789] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[   71.905793]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[   71.905944] ata1.00: status: { DRDY ERR }
[   71.906000] ata1.00: error: { UNC }
[   71.928256] ata1.00: configured for UDMA/100
[   71.928290] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   71.928301] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   71.928313] Descriptor sense data with sense descriptors (in hex):
[   71.928321]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   71.928342]         02 c5 76 67 
[   71.928351] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   71.928366] end_request: I/O error, dev sda, sector 46495335
[   71.928470] ata1: EH complete
[   71.941901] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   71.941976] sd 0:0:0:0: [sda] Write Protect is off
[   71.941983] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   71.943754] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   71.944229] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   71.944284] sd 0:0:0:0: [sda] Write Protect is off
[   71.944291] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   71.944388] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   73.072301] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   73.072317] apm: overridden by ACPI.
[   73.623537] ppdev: user-space parallel port driver
[   78.130156] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   78.130261] ata1.00: BMDMA stat 0x24
[   78.130329] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   78.130333]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   78.130485] ata1.00: status: { DRDY ERR }
[   78.130542] ata1.00: error: { UNC }
[   78.156262] ata1.00: configured for UDMA/100
[   78.156299] ata1: EH complete
[   80.439567] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   80.439655] ata1.00: BMDMA stat 0x24
[   80.439723] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   80.439727]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   80.439879] ata1.00: status: { DRDY ERR }
[   80.439936] ata1.00: error: { UNC }
[   80.464259] ata1.00: configured for UDMA/100
[   80.464303] ata1: EH complete
[   82.748987] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   82.749068] ata1.00: BMDMA stat 0x24
[   82.749135] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   82.749139]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   82.749291] ata1.00: status: { DRDY ERR }
[   82.749348] ata1.00: error: { UNC }
[   82.772261] ata1.00: configured for UDMA/100
[   82.772307] ata1: EH complete
[   85.058411] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   85.058496] ata1.00: BMDMA stat 0x24
[   85.058562] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   85.058566]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   85.058719] ata1.00: status: { DRDY ERR }
[   85.058775] ata1.00: error: { UNC }
[   85.080259] ata1.00: configured for UDMA/100
[   85.080297] ata1: EH complete
[   87.367837] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   87.367919] ata1.00: BMDMA stat 0x24
[   87.367985] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   87.367989]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   87.368170] ata1.00: status: { DRDY ERR }
[   87.368229] ata1.00: error: { UNC }
[   87.392258] ata1.00: configured for UDMA/100
[   87.392297] ata1: EH complete
[   89.677263] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   89.677346] ata1.00: BMDMA stat 0x24
[   89.677411] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   89.677415]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   89.677567] ata1.00: status: { DRDY ERR }
[   89.677624] ata1.00: error: { UNC }
[   89.700258] ata1.00: configured for UDMA/100
[   89.700307] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   89.700317] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   89.700331] Descriptor sense data with sense descriptors (in hex):
[   89.700337]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   89.700359]         00 76 40 47 
[   89.700368] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   89.700382] end_request: I/O error, dev sda, sector 7749703
[   89.700493] ata1: EH complete
[   89.718262] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   89.718348] sd 0:0:0:0: [sda] Write Protect is off
[   89.718355] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   89.718445] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   89.718541] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   89.718589] sd 0:0:0:0: [sda] Write Protect is off
[   89.718595] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   89.718681] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   92.008685] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   92.008767] ata1.00: BMDMA stat 0x24
[   92.008834] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   92.008838]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   92.008989] ata1.00: status: { DRDY ERR }
[   92.009046] ata1.00: error: { UNC }
[   92.096259] ata1.00: configured for UDMA/100
[   92.096294] ata1: EH complete
[   94.395090] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   94.395174] ata1.00: BMDMA stat 0x24
[   94.395241] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   94.395245]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   94.395398] ata1.00: status: { DRDY ERR }
[   94.395455] ata1.00: error: { UNC }
[   94.416268] ata1.00: configured for UDMA/100
[   94.416308] ata1: EH complete
[   96.704538] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   96.704625] ata1.00: BMDMA stat 0x24
[   96.704694] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   96.704698]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   96.704853] ata1.00: status: { DRDY ERR }
[   96.704910] ata1.00: error: { UNC }
[   96.728259] ata1.00: configured for UDMA/100
[   96.728299] ata1: EH complete
[   99.013936] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   99.014019] ata1.00: BMDMA stat 0x24
[   99.014086] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   99.014090]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   99.014242] ata1.00: status: { DRDY ERR }
[   99.014299] ata1.00: error: { UNC }
[   99.036258] ata1.00: configured for UDMA/100
[   99.036295] ata1: EH complete
[  101.323370] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  101.323452] ata1.00: BMDMA stat 0x24
[  101.323519] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[  101.323523]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[  101.323674] ata1.00: status: { DRDY ERR }
[  101.323731] ata1.00: error: { UNC }
[  101.348258] ata1.00: configured for UDMA/100
[  101.348294] ata1: EH complete
[  103.632797] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  103.632879] ata1.00: BMDMA stat 0x24
[  103.632946] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[  103.632950]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[  103.633101] ata1.00: status: { DRDY ERR }
[  103.633158] ata1.00: error: { UNC }
[  103.656258] ata1.00: configured for UDMA/100
[  103.656308] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  103.656318] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  103.656331] Descriptor sense data with sense descriptors (in hex):
[  103.656337]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  103.656358]         00 76 40 47 
[  103.656367] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  103.656382] end_request: I/O error, dev sda, sector 7749703
[  103.656499] ata1: EH complete
[  103.688906] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  103.688992] sd 0:0:0:0: [sda] Write Protect is off
[  103.688999] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  103.690105] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  103.690211] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  103.690263] sd 0:0:0:0: [sda] Write Protect is off
[  103.690270] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  103.690355] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  107.716277] [drm] Initialized drm 1.1.0 20060810
[  107.729146] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[  107.729175] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[  107.729187] pci 0000:00:02.0: setting latency timer to 64
[  107.735987] [drm] Initialized i810 1.4.0 20030605 on minor 0
[  107.739021] mtrr: base(0xf8000000) is not aligned on a size(0x258000) boundary
[  108.264372] [drm] Using v1.4 init.
[  108.268298] mtrr: base(0xf8000000) is not aligned on a size(0x3000000) boundary
[  111.484028] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[  111.484036]     driver to use reclaim_buffers_idlelocked() instead.
[  111.484040]     I will go on reclaiming the buffers anyway.
[  118.589229] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  118.589267] ata1.00: BMDMA stat 0x24
[  118.589286] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  118.589290]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  118.589300] ata1.00: status: { DRDY ERR }
[  118.589306] ata1.00: error: { UNC }
[  118.612477] ata1.00: configured for UDMA/100
[  118.612552] ata1: EH complete
[  120.909498] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  120.909522] ata1.00: BMDMA stat 0x24
[  120.909538] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  120.909542]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  120.909551] ata1.00: status: { DRDY ERR }
[  120.909557] ata1.00: error: { UNC }
[  120.932257] ata1.00: configured for UDMA/100
[  120.932300] ata1: EH complete
[  123.229917] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  123.229940] ata1.00: BMDMA stat 0x24
[  123.229957] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  123.229961]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  123.229970] ata1.00: status: { DRDY ERR }
[  123.229976] ata1.00: error: { UNC }
[  123.252257] ata1.00: configured for UDMA/100
[  123.252296] ata1: EH complete
[  125.550346] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  125.550369] ata1.00: BMDMA stat 0x24
[  125.550385] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  125.550389]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  125.550398] ata1.00: status: { DRDY ERR }
[  125.550404] ata1.00: error: { UNC }
[  125.564281] ata1.00: configured for UDMA/100
[  125.564310] ata1: EH complete
[  127.859774] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  127.859797] ata1.00: BMDMA stat 0x24
[  127.859814] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  127.859818]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  127.859827] ata1.00: status: { DRDY ERR }
[  127.859833] ata1.00: error: { UNC }
[  127.880257] ata1.00: configured for UDMA/100
[  127.880293] ata1: EH complete
[  130.180184] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  130.180205] ata1.00: BMDMA stat 0x24
[  130.180222] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  130.180226]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  130.180235] ata1.00: status: { DRDY ERR }
[  130.180241] ata1.00: error: { UNC }
[  130.204258] ata1.00: configured for UDMA/100
[  130.204298] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  130.204309] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  130.204321] Descriptor sense data with sense descriptors (in hex):
[  130.204327]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  130.204348]         02 c3 eb e7 
[  130.204357] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  130.204372] end_request: I/O error, dev sda, sector 46394343
[  130.204431] ata1: EH complete
[  130.208213] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  130.269492] sd 0:0:0:0: [sda] Write Protect is off
[  130.269514] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  130.272357] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  130.294633] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  130.295885] sd 0:0:0:0: [sda] Write Protect is off
[  130.295907] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  130.328196] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  132.918521] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  132.918544] ata1.00: BMDMA stat 0x24
[  132.918561] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  132.918565]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  132.918574] ata1.00: status: { DRDY ERR }
[  132.918580] ata1.00: error: { UNC }
[  133.028259] ata1.00: configured for UDMA/100
[  133.028295] ata1: EH complete
[  135.348908] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  135.348930] ata1.00: BMDMA stat 0x24
[  135.348947] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  135.348951]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  135.348960] ata1.00: status: { DRDY ERR }
[  135.348966] ata1.00: error: { UNC }
[  135.372286] ata1.00: configured for UDMA/100
[  135.372329] ata1: EH complete
[  137.691309] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  137.691332] ata1.00: BMDMA stat 0x24
[  137.691348] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  137.691352]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  137.691361] ata1.00: status: { DRDY ERR }
[  137.691367] ata1.00: error: { UNC }
[  137.712259] ata1.00: configured for UDMA/100
[  137.712300] ata1: EH complete
[  140.033735] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  140.033756] ata1.00: BMDMA stat 0x24
[  140.033772] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  140.033776]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  140.033785] ata1.00: status: { DRDY ERR }
[  140.033791] ata1.00: error: { UNC }
[  140.056259] ata1.00: configured for UDMA/100
[  140.056303] ata1: EH complete
[  142.376150] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  142.376172] ata1.00: BMDMA stat 0x24
[  142.376189] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  142.376193]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  142.376203] ata1.00: status: { DRDY ERR }
[  142.376208] ata1.00: error: { UNC }
[  142.400259] ata1.00: configured for UDMA/100
[  142.400306] ata1: EH complete
[  144.729570] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  144.729592] ata1.00: BMDMA stat 0x24
[  144.729610] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  144.729614]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  144.729622] ata1.00: status: { DRDY ERR }
[  144.729628] ata1.00: error: { UNC }
[  144.752261] ata1.00: configured for UDMA/100
[  144.752311] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  144.752322] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  144.752335] Descriptor sense data with sense descriptors (in hex):
[  144.752341]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  144.752362]         02 d4 c0 a7 
[  144.752371] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  144.752386] end_request: I/O error, dev sda, sector 47497383
[  144.752438] ata1: EH complete
[  144.786079] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  144.786170] sd 0:0:0:0: [sda] Write Protect is off
[  144.786178] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  144.786275] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  144.786375] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  144.786422] sd 0:0:0:0: [sda] Write Protect is off
[  144.786429] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  144.786514] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  273.856681] ppdev0: registered pardevice
[  273.958742] ppdev0: unregistered pardevice
[  274.842685] ppdev0: registered pardevice
[  274.892207] ppdev0: unregistered pardevice
[  278.284744] ppdev0: registered pardevice
[  278.332490] ppdev0: unregistered pardevice 

I note that there is a mention in a few places of "MEDIA ERROR", as well as " UNRECOVERED ERROR" as well as other error reports.
Am I right in thinking that means my  HDD is sick?

Yours in low expectations:(
Dick,


```

---

### Post by Tim Sharitt on 2009-01-06
First, What exactly are the symptoms you are experiencing? You may want to try running fsck to try to fix any errors on the file system.

For future reference use the CODE tags around your output
ex. [php]```
place your text here
```[/php]

---

### Post by caljohnsmith on 2009-01-06
If you want to check your HDD's health, you could run a "SMART" test on the HDD from Ubuntu. If you want to give it a shot, how about doing the following:
```
sudo apt-get install smartmontools
```
Note all the following commands assume the HDD in question is "sda", so change them if necessary. First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please post the contents of the two files on your desktop so we can see the results.

---

### Post by archolman on 2009-01-06
[SIZE=4][FONT=Arial Black]When I boot, ( & I was getting this in 8.04.1) the startup txt page was giving too much info to keep up with, but there seemed to be a lot of error reports. In  recovery mode, it recomended running "fsck". This, with a lot of inputting yes & no, seemed to reduce the errors, but it still hangs, FireFox is slow, slow, qiuckquick slow (It may well be a FF fault). Some of the dropdown menus are empty, others take 30+ seconds to appear, some come up instantly. I can't find a network connection, although I have tried manual & auto configs, & sometimes the system does a complete stop. Won't do anything, but Shift-Alt-Backspace sometimes works.[/FONT][/SIZE][FONT=Arial Black][SIZE=4] Otherwise, hot re-boot[/SIZE][/FONT] [FONT=Arial Black][SIZE=4]does it every time.
(And how do I keep the font selection in this post box? I use this setting so that I can see it.
Cheers,
Dick)[/SIZE][/FONT]

---

### Post by archolman on 2009-01-06
[SIZE=4][FONT=Arial Black]Hmmm. 
I got this from the tool req;
```
office@dick-office:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx
Suggested packages:
  eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl swaks
The following NEW packages will be installed
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx smartmontools
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 2225kB of archives.
After this operation, 4887kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  exim4-config exim4-base exim4-daemon-light exim4 bsd-mailx mailx smartmontools
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated
office@dick-office:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx
Suggested packages:
  eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl swaks
The following NEW packages will be installed
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx smartmontools
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 2225kB of archives.
After this operation, 4887kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  exim4-config exim4-base exim4-daemon-light exim4 bsd-mailx mailx smartmontools
Install these packages without verification [y/N]? y
Err http://gb.archive.ubuntu.com intrepid/main exim4-config 4.69-5ubuntu2
  400 Bad Request
Err http://gb.archive.ubuntu.com intrepid/main exim4-base 4.69-5ubuntu2
  400 Bad Request
Err http://gb.archive.ubuntu.com intrepid/main exim4-daemon-light 4.69-5ubuntu2
  400 Bad Request
Err http://gb.archive.ubuntu.com intrepid/main exim4 4.69-5ubuntu2
  400 Bad Request
Err http://gb.archive.ubuntu.com intrepid/main bsd-mailx 8.1.2-0.20071201cvs-3
  400 Bad Request
Err http://gb.archive.ubuntu.com intrepid/main mailx 1:20071201-3
  400 Bad Request
Err http://gb.archive.ubuntu.com intrepid/main smartmontools 5.38-1ubuntu2
  400 Bad Request
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/exim4/exim4-config_4.69-5ubuntu2_all.deb  400 Bad Request
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/exim4/exim4-base_4.69-5ubuntu2_i386.deb  400 Bad Request
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/exim4/exim4-daemon-light_4.69-5ubuntu2_i386.deb  400 Bad Request
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/exim4/exim4_4.69-5ubuntu2_all.deb  400 Bad Request
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/bsd-mailx/bsd-mailx_8.1.2-0.20071201cvs-3_i386.deb  400 Bad Request
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/bsd-mailx/mailx_20071201-3_all.deb  400 Bad Request
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/smartmontools/smartmontools_5.38-1ubuntu2_i386.deb  400 Bad Request
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
office@dick-office:~$ 

```Here's the dmesg output again;
```
 error)
[   78.130485] ata1.00: status: { DRDY ERR }
[   78.130542] ata1.00: error: { UNC }
[   78.156262] ata1.00: configured for UDMA/100
[   78.156299] ata1: EH complete
[   80.439567] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   80.439655] ata1.00: BMDMA stat 0x24
[   80.439723] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   80.439727]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   80.439879] ata1.00: status: { DRDY ERR }
[   80.439936] ata1.00: error: { UNC }
[   80.464259] ata1.00: configured for UDMA/100
[   80.464303] ata1: EH complete
[   82.748987] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   82.749068] ata1.00: BMDMA stat 0x24
[   82.749135] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   82.749139]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   82.749291] ata1.00: status: { DRDY ERR }
[   82.749348] ata1.00: error: { UNC }
[   82.772261] ata1.00: configured for UDMA/100
[   82.772307] ata1: EH complete
[   85.058411] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   85.058496] ata1.00: BMDMA stat 0x24
[   85.058562] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   85.058566]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   85.058719] ata1.00: status: { DRDY ERR }
[   85.058775] ata1.00: error: { UNC }
[   85.080259] ata1.00: configured for UDMA/100
[   85.080297] ata1: EH complete
[   87.367837] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   87.367919] ata1.00: BMDMA stat 0x24
[   87.367985] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   87.367989]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   87.368170] ata1.00: status: { DRDY ERR }
[   87.368229] ata1.00: error: { UNC }
[   87.392258] ata1.00: configured for UDMA/100
[   87.392297] ata1: EH complete
[   89.677263] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   89.677346] ata1.00: BMDMA stat 0x24
[   89.677411] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   89.677415]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   89.677567] ata1.00: status: { DRDY ERR }
[   89.677624] ata1.00: error: { UNC }
[   89.700258] ata1.00: configured for UDMA/100
[   89.700307] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   89.700317] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   89.700331] Descriptor sense data with sense descriptors (in hex):
[   89.700337]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   89.700359]         00 76 40 47 
[   89.700368] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   89.700382] end_request: I/O error, dev sda, sector 7749703
[   89.700493] ata1: EH complete
[   89.718262] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   89.718348] sd 0:0:0:0: [sda] Write Protect is off
[   89.718355] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   89.718445] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   89.718541] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   89.718589] sd 0:0:0:0: [sda] Write Protect is off
[   89.718595] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   89.718681] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   92.008685] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   92.008767] ata1.00: BMDMA stat 0x24
[   92.008834] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   92.008838]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   92.008989] ata1.00: status: { DRDY ERR }
[   92.009046] ata1.00: error: { UNC }
[   92.096259] ata1.00: configured for UDMA/100
[   92.096294] ata1: EH complete
[   94.395090] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   94.395174] ata1.00: BMDMA stat 0x24
[   94.395241] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   94.395245]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   94.395398] ata1.00: status: { DRDY ERR }
[   94.395455] ata1.00: error: { UNC }
[   94.416268] ata1.00: configured for UDMA/100
[   94.416308] ata1: EH complete
[   96.704538] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   96.704625] ata1.00: BMDMA stat 0x24
[   96.704694] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   96.704698]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   96.704853] ata1.00: status: { DRDY ERR }
[   96.704910] ata1.00: error: { UNC }
[   96.728259] ata1.00: configured for UDMA/100
[   96.728299] ata1: EH complete
[   99.013936] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   99.014019] ata1.00: BMDMA stat 0x24
[   99.014086] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[   99.014090]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[   99.014242] ata1.00: status: { DRDY ERR }
[   99.014299] ata1.00: error: { UNC }
[   99.036258] ata1.00: configured for UDMA/100
[   99.036295] ata1: EH complete
[  101.323370] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  101.323452] ata1.00: BMDMA stat 0x24
[  101.323519] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[  101.323523]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[  101.323674] ata1.00: status: { DRDY ERR }
[  101.323731] ata1.00: error: { UNC }
[  101.348258] ata1.00: configured for UDMA/100
[  101.348294] ata1: EH complete
[  103.632797] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  103.632879] ata1.00: BMDMA stat 0x24
[  103.632946] ata1.00: cmd c8/00:08:47:40:76/00:00:00:00:00/e0 tag 0 dma 4096 in
[  103.632950]          res 51/40:00:47:40:76/00:00:00:00:00/e0 Emask 0x9 (media error)
[  103.633101] ata1.00: status: { DRDY ERR }
[  103.633158] ata1.00: error: { UNC }
[  103.656258] ata1.00: configured for UDMA/100
[  103.656308] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  103.656318] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  103.656331] Descriptor sense data with sense descriptors (in hex):
[  103.656337]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  103.656358]         00 76 40 47 
[  103.656367] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  103.656382] end_request: I/O error, dev sda, sector 7749703
[  103.656499] ata1: EH complete
[  103.688906] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  103.688992] sd 0:0:0:0: [sda] Write Protect is off
[  103.688999] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  103.690105] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  103.690211] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  103.690263] sd 0:0:0:0: [sda] Write Protect is off
[  103.690270] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  103.690355] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  107.716277] [drm] Initialized drm 1.1.0 20060810
[  107.729146] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[  107.729175] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[  107.729187] pci 0000:00:02.0: setting latency timer to 64
[  107.735987] [drm] Initialized i810 1.4.0 20030605 on minor 0
[  107.739021] mtrr: base(0xf8000000) is not aligned on a size(0x258000) boundary
[  108.264372] [drm] Using v1.4 init.
[  108.268298] mtrr: base(0xf8000000) is not aligned on a size(0x3000000) boundary
[  111.484028] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[  111.484036]     driver to use reclaim_buffers_idlelocked() instead.
[  111.484040]     I will go on reclaiming the buffers anyway.
[  118.589229] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  118.589267] ata1.00: BMDMA stat 0x24
[  118.589286] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  118.589290]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  118.589300] ata1.00: status: { DRDY ERR }
[  118.589306] ata1.00: error: { UNC }
[  118.612477] ata1.00: configured for UDMA/100
[  118.612552] ata1: EH complete
[  120.909498] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  120.909522] ata1.00: BMDMA stat 0x24
[  120.909538] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  120.909542]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  120.909551] ata1.00: status: { DRDY ERR }
[  120.909557] ata1.00: error: { UNC }
[  120.932257] ata1.00: configured for UDMA/100
[  120.932300] ata1: EH complete
[  123.229917] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  123.229940] ata1.00: BMDMA stat 0x24
[  123.229957] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  123.229961]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  123.229970] ata1.00: status: { DRDY ERR }
[  123.229976] ata1.00: error: { UNC }
[  123.252257] ata1.00: configured for UDMA/100
[  123.252296] ata1: EH complete
[  125.550346] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  125.550369] ata1.00: BMDMA stat 0x24
[  125.550385] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  125.550389]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  125.550398] ata1.00: status: { DRDY ERR }
[  125.550404] ata1.00: error: { UNC }
[  125.564281] ata1.00: configured for UDMA/100
[  125.564310] ata1: EH complete
[  127.859774] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  127.859797] ata1.00: BMDMA stat 0x24
[  127.859814] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  127.859818]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  127.859827] ata1.00: status: { DRDY ERR }
[  127.859833] ata1.00: error: { UNC }
[  127.880257] ata1.00: configured for UDMA/100
[  127.880293] ata1: EH complete
[  130.180184] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  130.180205] ata1.00: BMDMA stat 0x24
[  130.180222] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[  130.180226]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[  130.180235] ata1.00: status: { DRDY ERR }
[  130.180241] ata1.00: error: { UNC }
[  130.204258] ata1.00: configured for UDMA/100
[  130.204298] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  130.204309] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  130.204321] Descriptor sense data with sense descriptors (in hex):
[  130.204327]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  130.204348]         02 c3 eb e7 
[  130.204357] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  130.204372] end_request: I/O error, dev sda, sector 46394343
[  130.204431] ata1: EH complete
[  130.208213] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  130.269492] sd 0:0:0:0: [sda] Write Protect is off
[  130.269514] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  130.272357] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  130.294633] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  130.295885] sd 0:0:0:0: [sda] Write Protect is off
[  130.295907] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  130.328196] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  132.918521] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  132.918544] ata1.00: BMDMA stat 0x24
[  132.918561] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  132.918565]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  132.918574] ata1.00: status: { DRDY ERR }
[  132.918580] ata1.00: error: { UNC }
[  133.028259] ata1.00: configured for UDMA/100
[  133.028295] ata1: EH complete
[  135.348908] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  135.348930] ata1.00: BMDMA stat 0x24
[  135.348947] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  135.348951]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  135.348960] ata1.00: status: { DRDY ERR }
[  135.348966] ata1.00: error: { UNC }
[  135.372286] ata1.00: configured for UDMA/100
[  135.372329] ata1: EH complete
[  137.691309] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  137.691332] ata1.00: BMDMA stat 0x24
[  137.691348] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  137.691352]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  137.691361] ata1.00: status: { DRDY ERR }
[  137.691367] ata1.00: error: { UNC }
[  137.712259] ata1.00: configured for UDMA/100
[  137.712300] ata1: EH complete
[  140.033735] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  140.033756] ata1.00: BMDMA stat 0x24
[  140.033772] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  140.033776]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  140.033785] ata1.00: status: { DRDY ERR }
[  140.033791] ata1.00: error: { UNC }
[  140.056259] ata1.00: configured for UDMA/100
[  140.056303] ata1: EH complete
[  142.376150] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  142.376172] ata1.00: BMDMA stat 0x24
[  142.376189] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  142.376193]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  142.376203] ata1.00: status: { DRDY ERR }
[  142.376208] ata1.00: error: { UNC }
[  142.400259] ata1.00: configured for UDMA/100
[  142.400306] ata1: EH complete
[  144.729570] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  144.729592] ata1.00: BMDMA stat 0x24
[  144.729610] ata1.00: cmd c8/00:08:a7:c0:d4/00:00:00:00:00/e2 tag 0 dma 4096 in
[  144.729614]          res 51/40:00:a7:c0:d4/00:00:00:00:00/e2 Emask 0x9 (media error)
[  144.729622] ata1.00: status: { DRDY ERR }
[  144.729628] ata1.00: error: { UNC }
[  144.752261] ata1.00: configured for UDMA/100
[  144.752311] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  144.752322] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  144.752335] Descriptor sense data with sense descriptors (in hex):
[  144.752341]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  144.752362]         02 d4 c0 a7 
[  144.752371] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  144.752386] end_request: I/O error, dev sda, sector 47497383
[  144.752438] ata1: EH complete
[  144.786079] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  144.786170] sd 0:0:0:0: [sda] Write Protect is off
[  144.786178] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  144.786275] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  144.786375] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  144.786422] sd 0:0:0:0: [sda] Write Protect is off
[  144.786429] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  144.786514] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  273.856681] ppdev0: registered pardevice
[  273.958742] ppdev0: unregistered pardevice
[  274.842685] ppdev0: registered pardevice
[  274.892207] ppdev0: unregistered pardevice
[  278.284744] ppdev0: registered pardevice
[  278.332490] ppdev0: unregistered pardevice
[ 8553.296032] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 8553.296039]     driver to use reclaim_buffers_idlelocked() instead.
[ 8553.296042]     I will go on reclaiming the buffers anyway.
[ 8553.485895] [drm] DMA Cleanup
[ 8555.774111] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8555.774134] ata1.00: BMDMA stat 0x24
[ 8555.774152] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8555.774155]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8555.774164] ata1.00: status: { DRDY ERR }
[ 8555.774170] ata1.00: error: { UNC }
[ 8555.796264] ata1.00: configured for UDMA/100
[ 8555.796303] ata1: EH complete
[ 8558.094504] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8558.094525] ata1.00: BMDMA stat 0x24
[ 8558.094541] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8558.094545]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8558.094554] ata1.00: status: { DRDY ERR }
[ 8558.094560] ata1.00: error: { UNC }
[ 8558.116258] ata1.00: configured for UDMA/100
[ 8558.116299] ata1: EH complete
[ 8560.414900] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8560.414921] ata1.00: BMDMA stat 0x24
[ 8560.414937] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8560.414941]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8560.414950] ata1.00: status: { DRDY ERR }
[ 8560.414956] ata1.00: error: { UNC }
[ 8560.436255] ata1.00: configured for UDMA/100
[ 8560.436293] ata1: EH complete
[ 8562.735379] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8562.735406] ata1.00: BMDMA stat 0x24
[ 8562.735424] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8562.735428]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8562.735437] ata1.00: status: { DRDY ERR }
[ 8562.735443] ata1.00: error: { UNC }
[ 8562.756422] ata1.00: configured for UDMA/100
[ 8562.756490] ata1: EH complete
[ 8565.055675] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8565.055697] ata1.00: BMDMA stat 0x24
[ 8565.055714] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8565.055718]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8565.055727] ata1.00: status: { DRDY ERR }
[ 8565.055732] ata1.00: error: { UNC }
[ 8565.076267] ata1.00: configured for UDMA/100
[ 8565.076312] ata1: EH complete
[ 8567.376100] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8567.376121] ata1.00: BMDMA stat 0x24
[ 8567.376138] ata1.00: cmd c8/00:08:67:76:c5/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8567.376142]          res 51/40:00:67:76:c5/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8567.376151] ata1.00: status: { DRDY ERR }
[ 8567.376156] ata1.00: error: { UNC }
[ 8567.400257] ata1.00: configured for UDMA/100
[ 8567.400306] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 8567.400317] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 8567.400329] Descriptor sense data with sense descriptors (in hex):
[ 8567.400335]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 8567.400356]         02 c5 76 67 
[ 8567.400365] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 8567.400380] end_request: I/O error, dev sda, sector 46495335
[ 8567.400431] ata1: EH complete
[ 8567.431272] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[ 8567.447546] sd 0:0:0:0: [sda] Write Protect is off
[ 8567.447569] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 8567.451139] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 8567.451652] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[ 8567.452044] sd 0:0:0:0: [sda] Write Protect is off
[ 8567.452057] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 8567.452860] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 8567.647274] mtrr: no MTRR for f8000000,3000000 found
[ 8571.738908] mtrr: base(0xf8000000) is not aligned on a size(0x258000) boundary
[ 8572.250394] [drm] Using v1.4 init.
[ 8572.254678] mtrr: base(0xf8000000) is not aligned on a size(0x3000000) boundary
[ 8575.440030] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 8575.440039]     driver to use reclaim_buffers_idlelocked() instead.
[ 8575.440043]     I will go on reclaiming the buffers anyway.
[ 8601.807994] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8601.808038] ata1.00: BMDMA stat 0x24
[ 8601.808055] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8601.808059]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8601.808068] ata1.00: status: { DRDY ERR }
[ 8601.808074] ata1.00: error: { UNC }
[ 8601.832268] ata1.00: configured for UDMA/100
[ 8601.832309] ata1: EH complete
[ 8604.128376] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8604.128398] ata1.00: BMDMA stat 0x24
[ 8604.128415] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8604.128419]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8604.128428] ata1.00: status: { DRDY ERR }
[ 8604.128434] ata1.00: error: { UNC }
[ 8604.152270] ata1.00: configured for UDMA/100
[ 8604.152316] ata1: EH complete
[ 8606.448787] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8606.448810] ata1.00: BMDMA stat 0x24
[ 8606.448827] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8606.448831]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8606.448840] ata1.00: status: { DRDY ERR }
[ 8606.448846] ata1.00: error: { UNC }
[ 8606.472267] ata1.00: configured for UDMA/100
[ 8606.472311] ata1: EH complete
[ 8608.769169] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8608.769192] ata1.00: BMDMA stat 0x24
[ 8608.769210] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8608.769214]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8608.769222] ata1.00: status: { DRDY ERR }
[ 8608.769229] ata1.00: error: { UNC }
[ 8608.792268] ata1.00: configured for UDMA/100
[ 8608.792315] ata1: EH complete
[ 8611.089558] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8611.089579] ata1.00: BMDMA stat 0x24
[ 8611.089596] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8611.089600]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8611.089609] ata1.00: status: { DRDY ERR }
[ 8611.089615] ata1.00: error: { UNC }
[ 8611.112270] ata1.00: configured for UDMA/100
[ 8611.112318] ata1: EH complete
[ 8613.409950] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8613.409973] ata1.00: BMDMA stat 0x24
[ 8613.409990] ata1.00: cmd c8/00:08:e7:eb:c3/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 8613.409993]          res 51/40:00:e7:eb:c3/00:00:00:00:00/e2 Emask 0x9 (media error)
[ 8613.410003] ata1.00: status: { DRDY ERR }
[ 8613.410008] ata1.00: error: { UNC }
[ 8613.432263] ata1.00: configured for UDMA/100
[ 8613.432315] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 8613.432326] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 8613.432339] Descriptor sense data with sense descriptors (in hex):
[ 8613.432344]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 8613.432366]         02 c3 eb e7 
[ 8613.432375] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 8613.432390] end_request: I/O error, dev sda, sector 46394343
[ 8613.432445] ata1: EH complete
[ 8613.448775] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[ 8613.448870] sd 0:0:0:0: [sda] Write Protect is off
[ 8613.448877] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 8613.448966] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 8613.449066] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[ 8613.449113] sd 0:0:0:0: [sda] Write Protect is off
[ 8613.449120] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 8613.449206] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 8758.796597] ppdev0: registered pardevice
[ 8759.033896] ppdev0: unregistered pardevice
[ 8760.047813] ppdev0: registered pardevice
[ 8760.096158] ppdev0: unregistered pardevice
[ 8763.600509] ppdev0: registered pardevice
[ 8763.648288] ppdev0: unregistered pardevice

```[/FONT][/SIZE]

---

### Post by archolman on 2009-01-06
[SIZE=3][B][FONT=Arial Black]I have tried a couple of times to down-load the smarttools set, with Synaptic & updater, keep getting the 'error 400' msg. :confused:
* just used it as URL, got a response, but no permission to open file
[/FONT][/B][/SIZE]

---

### Post by caljohnsmith on 2009-01-06
Do you have internet connectivity when you run the Live CD? If so, you could try running those commands from the Live CD. Another option is to download the [Ultimate Boot CD]("http://www.ultimatebootcd.com") and use that, because it has a bunch of HDD diagnostic tests from different HDD manufacturers. Or you could go to the manufacturer'ss website of your HDD, and often they have HDD diagnostic programs you can download and use. Let me know how that goes.

---

### Post by archolman on 2009-01-06
[SIZE=3][B][FONT=Arial Black](OK, I'll give that a try, however, my HDD is 'sda1' but terminal gives 'unrecognised command' ? :confused:)
[/FONT][/B][/SIZE]

---

### Post by caljohnsmith on 2009-01-06
When running the HDD test, you should use "sda" rather than "sda1", because sda refers to the HDD, whereas sda1 refers to the first partition on the sda drive. :)

---

### Post by archolman on 2009-01-06
[B]I'm  logging-out while stuff downloads
[/B]

---

### Post by archolman on 2009-01-06
[SIZE=3][FONT=Arial Black]Boo-Hoo. I have a sick HDD. Thanks for the all help, until I get a new 1, I can't sort anything else out.
At least Ubuntu is robust enough to keep going.[/FONT][B][FONT=Arial Black] :guitar:
Where is the tool to put "SOLVED" on the thread header?
[/FONT][/B][FONT=Arial Black]*found it[/FONT][B][FONT=Arial Black]
[/FONT][/B][FONT=Arial Black]Cheers,
Dick[/FONT][/SIZE]

---

