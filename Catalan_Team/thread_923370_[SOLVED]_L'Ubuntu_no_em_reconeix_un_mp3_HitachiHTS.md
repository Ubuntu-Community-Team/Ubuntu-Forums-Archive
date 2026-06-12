---
title: "[SOLVED] L'Ubuntu no em reconeix un mp3 HitachiHTS541616J9SA00"
date: 2008-09-18
forum: Catalan Team
---

### Post by lo gambusí on 2008-09-18
Hola, gent!

Tinc lo reproductor mp3 que vos dic al títol i mentre amb Windows XP no tinc cap problema, l'Ubuntu no me'l reconeix. Per no reconèixer-lo ni tan sols el nota connectat quan faig un lsusb.

He buscat per internet i no he trobat res. Alguna proposta? :?

---

### Post by papapep on 2008-09-18
St. Gúguel em diu, repetides vegades, que la referència aquesta que dónes és un disc dur Hitachi...no un reproductor d'audio...curiós...
Fent un dmesg quan l'has connectat, què es veu?

---

### Post by lo gambusí on 2008-09-18
Em surt un missatge tan llarg que no puc copiar-lo sencer... Te'l copio a trossos.

> [   39.755283] Yenta: CardBus bridge found at 0000:06:04.0 [1025:0090]
[   39.755314] Yenta: Using CSCINT to route CSC interrupts to PCI
[   39.755318] Yenta: Routing CardBus interrupts to PCI
[   39.755326] Yenta TI: socket 0000:06:04.0, mfunc 0x90501212, devctl 0x44
[   39.988957] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   39.988964] Socket status: 30000006
[   39.988968] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   39.988976] pcmcia: parent PCI bridge Memory window: 0xd2000000 - 0xd20fffff
[   40.250257] sdhci: Secure Digital Host Controller Interface driver
[   40.250263] sdhci: Copyright(c) Pierre Ossman
[   40.250330] sdhci: SDHCI controller found at 0000:06:04.2 [1524:0550] (rev 1)
[   40.250356] PCI: Enabling device 0000:06:04.2 (0000 -> 0002)
[   40.250366] ACPI: PCI Interrupt 0000:06:04.2[B] -> GSI 17 (level, low) -> IRQ 17
[   40.250457] mmc0: SDHCI at 0xd2003400 irq 17 PIO
[   40.250472] sdhci: SDHCI controller found at 0000:06:04.4 [1524:0551] (rev 1)
[   40.250494] PCI: Enabling device 0000:06:04.4 (0000 -> 0002)
[   40.250500] ACPI: PCI Interrupt 0000:06:04.4[B] -> GSI 17 (level, low) -> IRQ 17
[   40.250557] mmc1: SDHCI at 0xd2003100 irq 17 PIO
[   40.365686] ACPI: AC Adapter [ACAD] (off-line)
[   40.550105] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input8
[   40.592655] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   40.592976] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   40.640587] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   40.673217] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   40.704035] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   40.987865] nvidia: module license 'NVIDIA' taints kernel.
[   40.992223] ACPI: Battery Slot [BAT1] (battery present)
[   41.558977] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   41.558983] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   41.559117] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   41.559136] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   41.559168] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   42.073741] Linux video capture interface: v2.00
[   42.173280] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0321) 
[   42.401996] usbcore: registered new interface driver gspca
[   42.402005] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[   43.185995] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.186009] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   43.186133] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   43.217393] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   43.217433] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   43.307925] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   43.308548] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   43.311126] cs: IO port probe 0x100-0x3af: clean.
[   43.313269] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   43.314149] cs: IO port probe 0x820-0x8ff: clean.
[   43.314880] cs: IO port probe 0xc00-0xcf7: clean.
[   43.315858] cs: IO port probe 0xa00-0xaff: clean.
[   43.515356] udev: renamed network interface wlan0 to eth1
[   43.868485] lp: driver loaded but no devices found
[   44.053405] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   44.089467] EXT3 FS on sda1, internal journal
[   44.277429] device-mapper: uevent: version 1.0.3
[   44.277471] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]


---

### Post by lo gambusí on 2008-09-18
2a part...
> [   45.143531] NET: Registered protocol family 17
[   45.444364] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.149794] No dock devices found.
[   46.691692] acpi_cpufreq: no version for "struct_module" found: kernel tainted.
[   47.605062] ppdev: user-space parallel port driver
[   47.868309] audit(1221749749.554:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5234 profile="/usr/sbin/cupsd" namespace="default"
[   47.973546] apm: BIOS not found.
[   53.334259] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   53.334267] vboxdrv: Successfully done.
[   53.334270] vboxdrv: Found 2 processor cores.
[   53.334347] vboxdrv: fAsync=0 offMin=0x53e offMax=0x1bac
[   53.334354] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   53.334358] vboxdrv: Successfully loaded version 2.0.2 (interface 0x00090000).
[   53.461753] tun: Universal TUN/TAP device driver, 1.6
[   53.461760] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   55.928608] Bluetooth: Core ver 2.11
[   55.929029] NET: Registered protocol family 31
[   55.929034] Bluetooth: HCI device and connection manager initialized
[   55.929040] Bluetooth: HCI socket layer initialized
[   55.969336] Bluetooth: L2CAP ver 2.9
[   55.969343] Bluetooth: L2CAP socket layer initialized
[   56.058395] Bluetooth: RFCOMM socket layer initialized
[   56.058413] Bluetooth: RFCOMM TTY layer initialized
[   56.058416] Bluetooth: RFCOMM ver 1.8
[   62.787979] eth1: Initial auth_alg=0
[   62.787990] eth1: authenticate with AP 00:1f:c6:f1:d2:61
[   62.789756] eth1: RX authentication from 00:1f:c6:f1:d2:61 (alg=0 transaction=2 status=0)
[   62.789762] eth1: authenticated
[   62.789766] eth1: associate with AP 00:1f:c6:f1:d2:61
[   62.791476] eth1: RX AssocResp from 00:1f:c6:f1:d2:61 (capab=0x401 status=0 aid=1)
[   62.791484] eth1: associated
[   74.106956] NET: Registered protocol family 10
[   74.107368] lo: Disabled Privacy Extensions
[   74.108989] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   84.663757] eth1: no IPv6 routers present
[   88.874866] CPU0 attaching NULL sched-domain.
[   88.874876] CPU1 attaching NULL sched-domain.
[   88.880908] CPU0 attaching sched-domain:
[   88.880916]  domain 0: span 03
[   88.880920]   groups: 01 02
[   88.880925]   domain 1: span 03
[   88.880928]    groups: 03
[   88.880932] CPU1 attaching sched-domain:
[   88.880935]  domain 0: span 03
[   88.880938]   groups: 02 01
[   88.880942]   domain 1: span 03
[   88.880945]    groups: 03
[  167.431365] CPU0 attaching NULL sched-domain.
[  167.431374] CPU1 attaching NULL sched-domain.
[  167.454211] CPU0 attaching sched-domain:
[  167.454222]  domain 0: span 03
[  167.454225]   groups: 01 02
[  167.454231] CPU1 attaching sched-domain:
[  167.454234]  domain 0: span 03
[  167.454237]   groups: 02 01
[  410.245728] usb 5-1: new high speed USB device using ehci_hcd and address 4
[  410.379396] usb 5-1: configuration #1 chosen from 1 choice
[  410.520679] usbcore: registered new interface driver libusual
[  410.554100] Initializing USB Mass Storage driver...
[  410.554347] scsi2 : SCSI emulation for USB Mass Storage devices
[  410.554536] usbcore: registered new interface driver usb-storage
[  410.554541] USB Mass Storage support registered.
[  410.554924] usb-storage: device found at 4
[  410.554927] usb-storage: waiting for device to settle before scanning
[  411.149975] usb-storage: device scan complete
[  411.150470] scsi 2:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[  411.154927] sd 2:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[  411.155413] sd 2:0:0:0: [sdb] Write Protect is off
[  411.155419] sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  411.155423] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  411.156659] sd 2:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[  411.157158] sd 2:0:0:0: [sdb] Write Protect is off
[  411.157163] sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  411.157167] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  411.157172]  sdb: sdb1
[  411.163541] sd 2:0:0:0: [sdb] Attached SCSI disk
[  411.163606] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  429.999358] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  429.999371] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  429.999377] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  429.999385] end_request: I/O error, dev sdb, sector 15885672
[  481.253992] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  481.254004] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  481.254011] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  481.254019] end_request: I/O error, dev sdb, sector 15885720
[  481.254067] FAT: Directory bread(block 15885657) failed
[  532.993421] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  532.993429] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  532.993434] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  532.993438] end_request: I/O error, dev sdb, sector 15885721
[  532.993459] FAT: Directory bread(block 15885658) failed
[  554.113849] usb 5-1: USB disconnect, address 4
[  554.114141] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  554.114150] end_request: I/O error, dev sdb, sector 15885729
[  554.114231] FAT: Directory bread(block 15885666) failed
[  554.114690] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  554.114698] end_request: I/O error, dev sdb, sector 45894823
[  554.115185] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  554.115192] end_request: I/O error, dev sdb, sector 45894823
[  554.115237] FAT: Directory bread(block 45894760) failed
[  554.115744] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  554.115751] end_request: I/O error, dev sdb, sector 45894824
[  554.115816] FAT: Directory bread(block 45894761) failed
[  554.116929] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK


---

### Post by lo gambusí on 2008-09-18
3a part:

> [  554.116938] end_request: I/O error, dev sdb, sector 45894825
[  554.119170] FAT: Directory bread(block 45894762) failed
[  554.119214] FAT: Directory bread(block 45894763) failed
[  554.119225] FAT: Directory bread(block 45894764) failed
[  554.119234] FAT: Directory bread(block 45894765) failed
[  554.119243] FAT: Directory bread(block 45894766) failed
[  554.119252] FAT: Directory bread(block 45894767) failed
[  554.119262] FAT: Directory bread(block 45894768) failed
[  554.119272] FAT: Directory bread(block 45894769) failed
[  554.119281] FAT: Directory bread(block 45894770) failed
[  554.119290] FAT: Directory bread(block 45894771) failed
[  554.119298] FAT: Directory bread(block 45894772) failed
[  554.119307] FAT: Directory bread(block 45894773) failed
[  554.119315] FAT: Directory bread(block 45894774) failed
[  554.119324] FAT: Directory bread(block 45894775) failed
[  554.119333] FAT: Directory bread(block 45894776) failed
[  554.119342] FAT: Directory bread(block 45894777) failed
[  554.119351] FAT: Directory bread(block 45894778) failed
[  554.119359] FAT: Directory bread(block 45894779) failed
[  554.119368] FAT: Directory bread(block 45894780) failed
[  554.119377] FAT: Directory bread(block 45894781) failed
[  554.119385] FAT: Directory bread(block 45894782) failed
[  554.119394] FAT: Directory bread(block 45894783) failed
[  554.119403] FAT: Directory bread(block 45894784) failed
[  554.119412] FAT: Directory bread(block 45894785) failed
[  554.119421] FAT: Directory bread(block 45894786) failed
[  554.119429] FAT: Directory bread(block 45894787) failed
[  554.119438] FAT: Directory bread(block 45894788) failed
[  554.119446] FAT: Directory bread(block 45894789) failed
[  554.119454] FAT: Directory bread(block 45894790) failed
[  554.119462] FAT: Directory bread(block 45894791) failed
[  554.119472] FAT: Directory bread(block 45894792) failed
[  554.119480] FAT: Directory bread(block 45894793) failed
[  554.119489] FAT: Directory bread(block 45894794) failed
[  554.119497] FAT: Directory bread(block 45894795) failed
[  554.119506] FAT: Directory bread(block 45894796) failed
[  554.119514] FAT: Directory bread(block 45894797) failed
[  554.119523] FAT: Directory bread(block 45894798) failed
[  554.119531] FAT: Directory bread(block 45894799) failed
[  554.119540] FAT: Directory bread(block 45894800) failed
[  554.119549] FAT: Directory bread(block 45894801) failed
[  554.119558] FAT: Directory bread(block 45894802) failed
[  554.119566] FAT: Directory bread(block 45894803) failed
[  554.119575] FAT: Directory bread(block 45894804) failed
[  554.119583] FAT: Directory bread(block 45894805) failed
[  554.119592] FAT: Directory bread(block 45894806) failed
[  554.119601] FAT: Directory bread(block 45894807) failed
[  554.119610] FAT: Directory bread(block 45894808) failed
[  554.119619] FAT: Directory bread(block 45894809) failed
[  554.119628] FAT: Directory bread(block 45894810) failed
[  554.119637] FAT: Directory bread(block 45894811) failed
[  554.119646] FAT: Directory bread(block 45894812) failed
[  554.119654] FAT: Directory bread(block 45894813) failed
[  554.119663] FAT: Directory bread(block 45894814) failed
[  554.119672] FAT: Directory bread(block 45894815) failed
[  554.119681] FAT: Directory bread(block 45894816) failed
[  554.119690] FAT: Directory bread(block 45894817) failed
[  554.119699] FAT: Directory bread(block 45894818) failed
[  554.119708] FAT: Directory bread(block 45894819) failed
[  554.119717] FAT: Directory bread(block 45894820) failed
[  554.119725] FAT: Directory bread(block 45894821) failed
[  554.119734] FAT: Directory bread(block 45894822) failed
[  554.119743] FAT: Directory bread(block 45894823) failed
[  554.135815] FAT: FAT read failed (blocknr 159)
[  554.138988] FAT: Directory bread(block 15885667) failed
[  554.139007] FAT: Directory bread(block 15885668) failed
[  554.139018] FAT: Directory bread(block 15885669) failed
[  554.139027] FAT: Directory bread(block 15885670) failed
[  554.139037] FAT: Directory bread(block 15885671) failed
[  554.144934] FAT: FAT read failed (blocknr 3638)
[  554.226509] FAT: FAT read failed (blocknr 5622)
[  554.226529] FAT: bread failed in fat_clusters_flush
[  554.226543] FAT: unable to read inode block for updating (i_pos 681549046)
[  554.227325] Buffer I/O error on device sdb1, logical block 29635690
[  554.227328] lost page write due to I/O error on sdb1
[  555.576995] usb 5-1: new high speed USB device using ehci_hcd and address 5
[  555.711908] usb 5-1: configuration #1 chosen from 1 choice
[  555.712773] scsi3 : SCSI emulation for USB Mass Storage devices
[  555.713146] usb-storage: device found at 5
[  555.713151] usb-storage: waiting for device to settle before scanning
[  556.870416] usb-storage: device scan complete
[  556.871058] scsi 3:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[  556.883619] sd 3:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[  556.884359] sd 3:0:0:0: [sdb] Write Protect is off
[  556.884368] sd 3:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  556.884375] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  556.885863] sd 3:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[  556.886601] sd 3:0:0:0: [sdb] Write Protect is off
[  556.886609] sd 3:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  556.886616] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  556.886622]  sdb:<6>usb 5-1: USB disconnect, address 5
[  558.778716] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.778724] end_request: I/O error, dev sdb, sector 0
[  558.778730] Buffer I/O error on device sdb, logical block 0
[  558.778799] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.778809] end_request: I/O error, dev sdb, sector 0
[  558.778814] Buffer I/O error on device sdb, logical block 0
[  558.778846] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.778854] end_request: I/O error, dev sdb, sector 0
[  558.778859] Buffer I/O error on device sdb, logical block 0
[  558.778882] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.778889] end_request: I/O error, dev sdb, sector 0
[  558.778894] Buffer I/O error on device sdb, logical block 0
[  558.778916] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.778924] end_request: I/O error, dev sdb, sector 0
[  558.778928] Buffer I/O error on device sdb, logical block 0
[  558.778939] ldm_validate_partition_table(): Disk read failed.
[  558.778956] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.778963] end_request: I/O error, dev sdb, sector 0
[  558.778968] Buffer I/O error on device sdb, logical block 0
[  558.778989] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.778997] end_request: I/O error, dev sdb, sector 0
[  558.779002] Buffer I/O error on device sdb, logical block 0
[  558.779023] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.779030] end_request: I/O error, dev sdb, sector 0
[  558.779035] Buffer I/O error on device sdb, logical block 0
[  558.779056] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.779064] end_request: I/O error, dev sdb, sector 0
[  558.779069] Buffer I/O error on device sdb, logical block 0
[  558.779079] Dev sdb: unable to read RDB block 0
[  558.779095] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.779102] end_request: I/O error, dev sdb, sector 0
[  558.779107] Buffer I/O error on device sdb, logical block 0
[  558.779129] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.779137] end_request: I/O error, dev sdb, sector 0
[  558.779179] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.779187] end_request: I/O error, dev sdb, sector 24
[  558.779213] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.779220] end_request: I/O error, dev sdb, sector 24
[  558.779243] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  558.779250] end_request: I/O error, dev sdb, sector 0
[  558.779271] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK


---

### Post by lo gambusí on 2008-09-18
I darrera:

> [  558.779279] end_request: I/O error, dev sdb, sector 0
[  558.779289]  unable to read partition table
[  558.779366] sd 3:0:0:0: [sdb] Attached SCSI disk
[  558.779434] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  559.288447] usb 5-1: new high speed USB device using ehci_hcd and address 6
[  559.421134] usb 5-1: configuration #1 chosen from 1 choice
[  559.421712] scsi4 : SCSI emulation for USB Mass Storage devices
[  559.421994] usb-storage: device found at 6
[  559.421997] usb-storage: waiting for device to settle before scanning
[  560.408707] usb-storage: device scan complete
[  560.409205] scsi 4:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[  560.414172] sd 4:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[  560.414662] sd 4:0:0:0: [sdb] Write Protect is off
[  560.414668] sd 4:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  560.414672] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  560.415908] sd 4:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[  560.416406] sd 4:0:0:0: [sdb] Write Protect is off
[  560.416411] sd 4:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  560.416415] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  560.416420]  sdb: sdb1
[  560.428282] sd 4:0:0:0: [sdb] Attached SCSI disk
[  560.428352] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  572.823006] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  572.823021] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  572.823028] sd 4:0:0:0: [sdb] Add. Sense: Data phase error
[  572.823036] end_request: I/O error, dev sdb, sector 15885672
[  624.434154] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  624.434168] sd 4:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  624.434175] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[  624.434183] end_request: I/O error, dev sdb, sector 15885720
[  624.434245] FAT: Directory bread(block 15885657) failed
[  676.419692] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  676.419705] end_request: I/O error, dev sdb, sector 15885721
[  676.419710] usb 5-1: USB disconnect, address 6
[  676.419740] FAT: Directory bread(block 15885658) failed
[  676.420251] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  676.420261] end_request: I/O error, dev sdb, sector 15885722
[  676.420286] FAT: Directory bread(block 15885659) failed
[  676.420312] FAT: Directory bread(block 15885660) failed
[  676.420323] FAT: Directory bread(block 15885661) failed
[  676.420333] FAT: Directory bread(block 15885662) failed
[  676.420342] FAT: Directory bread(block 15885663) failed
[  676.420353] FAT: Directory bread(block 15885664) failed
[  676.420363] FAT: Directory bread(block 15885665) failed
[  676.420373] FAT: Directory bread(block 15885666) failed
[  676.420382] FAT: Directory bread(block 15885667) failed
[  676.420391] FAT: Directory bread(block 15885668) failed
[  676.420400] FAT: Directory bread(block 15885669) failed
[  676.420410] FAT: Directory bread(block 15885670) failed
[  676.420419] FAT: Directory bread(block 15885671) failed
[  676.427863] printk: 5 messages suppressed.
[  676.427875] Buffer I/O error on device sdb1, logical block 1
[  676.427880] lost page write due to I/O error on sdb1
[  676.442276] Buffer I/O error on device sdb1, logical block 29635690
[  676.442286] lost page write due to I/O error on sdb1
[  676.452212] FAT: Directory bread(block 29635690) failed
[  676.452822] FAT: Directory bread(block 29635690) failed
[  676.453145] FAT: Directory bread(block 29635690) failed
[  677.082493] usb 5-1: new high speed USB device using ehci_hcd and address 7
[  677.216413] usb 5-1: configuration #1 chosen from 1 choice
[  677.217239] scsi5 : SCSI emulation for USB Mass Storage devices
[  677.217616] usb-storage: device found at 7
[  677.217621] usb-storage: waiting for device to settle before scanning
[  679.098176] usb-storage: device scan complete
[  679.098734] scsi 5:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[  679.106413] sd 5:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[  679.107155] sd 5:0:0:0: [sdb] Write Protect is off
[  679.107160] sd 5:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  679.107162] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  679.108402] sd 5:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[  679.108893] sd 5:0:0:0: [sdb] Write Protect is off
[  679.108898] sd 5:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  679.108900] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  679.108903]  sdb: sdb1
[  679.483838] sd 5:0:0:0: [sdb] Attached SCSI disk
[  679.483919] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  681.506985] usb 5-1: USB disconnect, address 7
[  682.695602] usb 5-1: new high speed USB device using ehci_hcd and address 8
[  682.829564] usb 5-1: configuration #1 chosen from 1 choice
[  682.830392] scsi6 : SCSI emulation for USB Mass Storage devices
[  682.830765] usb-storage: device found at 8
[  682.830770] usb-storage: waiting for device to settle before scanning
[  686.145299] usb-storage: device scan complete
[  686.145947] scsi 6:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[  686.154252] sd 6:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[  686.154745] sd 6:0:0:0: [sdb] Write Protect is off
[  686.154751] sd 6:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  686.154755] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  686.155993] sd 6:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[  686.156491] sd 6:0:0:0: [sdb] Write Protect is off
[  686.156496] sd 6:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  686.156500] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  686.156505]  sdb: sdb1
[  686.164857] sd 6:0:0:0: [sdb] Attached SCSI disk
[  686.164925] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  759.002188] usb 5-1: USB disconnect, address 8
[  768.745912] usb 5-1: new high speed USB device using ehci_hcd and address 9
[  768.880617] usb 5-1: configuration #1 chosen from 1 choice
[  768.894310] scsi7 : SCSI emulation for USB Mass Storage devices
[  768.894839] usb-storage: device found at 9
[  768.894844] usb-storage: waiting for device to settle before scanning
[  770.466622] usb-storage: device scan complete
[  770.467380] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[  771.356189] sd 7:0:0:0: [sdb] 2015232 512-byte hardware sectors (1032 MB)
[  771.356812] sd 7:0:0:0: [sdb] Write Protect is off
[  771.356819] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  771.356823] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  771.359803] sd 7:0:0:0: [sdb] 2015232 512-byte hardware sectors (1032 MB)
[  771.360429] sd 7:0:0:0: [sdb] Write Protect is off
[  771.360436] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  771.360440] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  771.360449]  sdb: sdb1
[  771.361696] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  771.361769] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 1172.490828] usb 5-1: USB disconnect, address 9
[ 1173.852454] usb 5-1: new high speed USB device using ehci_hcd and address 10
[ 1173.987205] usb 5-1: configuration #1 chosen from 1 choice
[ 1173.987691] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1173.987892] usb-storage: device found at 10
[ 1173.987896] usb-storage: waiting for device to settle before scanning
[ 1174.329322] usb 5-1: USB disconnect, address 10
[ 1194.702379] usb 5-1: new high speed USB device using ehci_hcd and address 11
[ 1194.836053] usb 5-1: configuration #1 chosen from 1 choice
[ 1194.836516] scsi9 : SCSI emulation for USB Mass Storage devices
[ 1194.836853] usb-storage: device found at 11
[ 1194.836859] usb-storage: waiting for device to settle before scanning
[ 1194.938234] usb 5-1: USB disconnect, address 11
[ 1195.405793] usb 5-1: new high speed USB device using ehci_hcd and address 12
[ 1195.541477] usb 5-1: configuration #1 chosen from 1 choice
[ 1195.544565] scsi10 : SCSI emulation for USB Mass Storage devices
[ 1195.546309] usb-storage: device found at 12
[ 1195.546316] usb-storage: waiting for device to settle before scanning
[ 1198.552861] usb-storage: device scan complete
[ 1198.553540] scsi 10:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 1199.027077] sd 10:0:0:0: [sdb] 2015232 512-byte hardware sectors (1032 MB)
[ 1199.027699] sd 10:0:0:0: [sdb] Write Protect is off
[ 1199.027703] sd 10:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1199.027706] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1199.030319] sd 10:0:0:0: [sdb] 2015232 512-byte hardware sectors (1032 MB)
[ 1199.030949] sd 10:0:0:0: [sdb] Write Protect is off
[ 1199.030952] sd 10:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1199.030954] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1199.030961]  sdb: sdb1
[ 1199.031773] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 1199.031821] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 1208.685509] usb 5-1: USB disconnect, address 12
[ 1208.958141] usb 5-1: new high speed USB device using ehci_hcd and address 13
[ 1209.091976] usb 5-1: configuration #1 chosen from 1 choice
[ 1209.092256] scsi11 : SCSI emulation for USB Mass Storage devices
[ 1209.092476] usb-storage: device found at 13
[ 1209.092479] usb-storage: waiting for device to settle before scanning
[ 1209.144986] usb 5-1: USB disconnect, address 13
oriol@oriol-laptop:~$ 



---

### Post by papapep on 2008-09-18
Ostres Gambusí, que només feien falta les últimes línies i, en tot cas, hauries d'adjuntar un fitxer tan gran i no enganxar-lo...:-/
Fixa't que les últimes 20-30 línies només parlen d'USB, o sigui que alguna cosa fa.
Seria interessant saber el model exacte de l'aparell. Té rotulat el que has posat el títol???

---

### Post by lo gambusí on 2008-09-18
A vore, rotulat no surt res, i a la capseta tampoc. Lo nom que he dit és lo que surt quan lo lliges amb windows xp.

És [este]("http://cgi.ebay.es/ws/eBayISAPI.dll?ViewItem&item=260284935022&ssPageName=MERC_VIC_RCRX_Pr4_PcY_BIN_IT&refitem=260280883066&itemcount=4&refwidgetloc=closed_view_item&usedrule1=CrossSell_LogicX&refwidgettype=cross_promot_widget&_trksid=p284.m183&_trkparms=algo%3DCRX%26its%3DS%252BI%26itu%3DUCI%252BSI%26otn%3D4") model. Sento no tenir més dades... :(

---

### Post by lo gambusí on 2008-10-07
Bé. l'intrepid ibex **sí** me'l reconeix! :D

---

