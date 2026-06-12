---
title: "comp wont see sd card"
date: 2009-01-09
forum: General Help
---

### Post by lilbluegremlin on 2009-01-09
hey,
so i got a new micro sd card for the holidays and my comp does not see it. its never had a problem with sd cards and the other micro sd card i have works just fine. 
im using a mirco sd card to sd card adapter and then a usb sd card reader. 
my cell and my work cell both see the micro sd card and let me put stuff on it but my comp will not see it.

i went to the kern.log file and found this:
> 
Jan  9 14:48:58 ABONY kernel: [60562.865400] sd 4:0:0:0: [sdc] 1985024 1024-byte hardware sectors (2033 MB)
Jan  9 14:48:58 ABONY kernel: [60562.878227] sd 4:0:0:0: [sdc] Write Protect is off
Jan  9 14:48:58 ABONY kernel: [60562.878241] sd 4:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Jan  9 14:48:58 ABONY kernel: [60562.878247] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Jan  9 14:48:58 ABONY kernel: [60562.889240] sd 4:0:0:0: [sdc] 1985024 1024-byte hardware sectors (2033 MB)
Jan  9 14:48:58 ABONY kernel: [60562.902229] sd 4:0:0:0: [sdc] Write Protect is off
Jan  9 14:48:58 ABONY kernel: [60562.902240] sd 4:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Jan  9 14:48:58 ABONY kernel: [60562.902246] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Jan  9 14:48:58 ABONY kernel: [60562.903177]  sdc:<4>__ratelimit: 5 callbacks suppressed
Jan  9 14:48:58 ABONY kernel: [60562.903730] Buffer I/O error on device sdc, logical block 0
...
Jan  9 14:48:58 ABONY kernel: [60562.906808] Buffer I/O error on device sdc, logical block 0
Jan  9 14:48:58 ABONY kernel: [60562.906828] ldm_validate_partition_table(): Disk read failed.
Jan  9 14:48:58 ABONY kernel: [60562.909911] Buffer I/O error on device sdc, logical block 0
...
Jan  9 14:48:58 ABONY kernel: [60562.914420] Buffer I/O error on device sdc, logical block 0
Jan  9 14:48:58 ABONY kernel: [60562.914439] Dev sdc: unable to read RDB block 0
Jan  9 14:48:58 ABONY kernel: [60562.917157] Buffer I/O error on device sdc, logical block 0
Jan  9 14:48:58 ABONY kernel: [60562.918698]  unable to read partition table
Jan  9 14:48:58 ABONY kernel: [60562.957283] sd 4:0:0:0: [sdc] 1985024 1024-byte hardware sectors (2033 MB)
Jan  9 14:48:58 ABONY kernel: [60562.971291] sd 4:0:0:0: [sdc] Write Protect is off
Jan  9 14:48:58 ABONY kernel: [60562.971309] sd 4:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Jan  9 14:48:58 ABONY kernel: [60562.971316] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Jan  9 14:48:58 ABONY kernel: [60562.985633] sd 4:0:0:0: [sdc] 1985024 1024-byte hardware sectors (2033 MB)
Jan  9 14:48:58 ABONY kernel: [60563.002286] sd 4:0:0:0: [sdc] Write Protect is off
Jan  9 14:48:58 ABONY kernel: [60563.002304] sd 4:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Jan  9 14:48:58 ABONY kernel: [60563.002310] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Jan  9 14:48:58 ABONY kernel: [60563.002331]  sdc: sdc1
Jan  9 14:48:58 ABONY kernel: [60563.025828] sdc: p1 exceeds device capacity
Jan  9 14:48:59 ABONY kernel: [60563.730366] attempt to access beyond end of device
Jan  9 14:48:59 ABONY kernel: [60563.730389] sdc: rw=0, want=7934842, limit=3970048
Jan  9 14:48:59 ABONY kernel: [60563.733206] attempt to access beyond end of device
Jan  9 14:48:59 ABONY kernel: [60563.733219] sdc: rw=0, want=7934842, limit=3970048
...
Jan  9 14:48:59 ABONY kernel: [60564.003615] attempt to access beyond end of device
Jan  9 14:48:59 ABONY kernel: [60564.003619] sdc: rw=0, want=7934962, limit=3970048

sorry if thats long i tried to shorten it.
any help here or bumps in the right detection? 
i could not find anything in the forums like this problem.

---

### Post by catalina on 2009-01-10
Hi lilbluegremlin,

I experienced a similar problem.  After I had tried to mount a Memory Stick card in my internal card reader (hp dv4000) my internal card reader stopped mounting my sd cards.  Here is the printout from dmesg with sd card in slot:

2/1-2:1.0/input/input3
[   12.870915] input,hidraw1: USB HID v1.00 Keyboard [USB tenkeypad ] on usb-0000:00:1d.0-2
[   12.870927] usbcore: registered new interface driver usbhid
[   12.870931] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   12.915496] Attempting manual resume
[   12.915500] swsusp: Resume From Partition 8:5
[   12.915502] PM: Checking swsusp image.
[   12.915650] PM: Resume from disk failed.
[   12.932267] kjournald starting.  Commit interval 5 seconds
[   12.932276] EXT3-fs: mounted filesystem with ordered data mode.
[   14.535187] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.569170] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   15.480544] Linux agpgart interface v0.102
[   15.603456] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.744526] agpgart: Detected an Intel 915GM Chipset.
[   15.744993] agpgart: Detected 7932K stolen memory.
[   15.762687] agpgart: AGP aperture is 256M @ 0xc0000000
[   15.821645] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.876602] input: Power Button (FF) as /devices/virtual/input/input4
[   15.896441] ACPI: Power Button (FF) [PWRF]
[   15.896538] input: Lid Switch as /devices/virtual/input/input5
[   15.916491] ACPI: Lid Switch [LID0]
[   15.916572] input: Sleep Button (CM) as /devices/virtual/input/input6
[   15.928425] ACPI: Sleep Button (CM) [SLPB]
[   15.928513] input: Power Button (CM) as /devices/virtual/input/input7
[   15.944425] ACPI: Power Button (CM) [PWB]
[   16.052542] ACPI: WMI-Acer: Mapper loaded
[   16.551060] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   16.564331] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   17.192224] iTCO_vendor_support: vendor-support=0
[   17.223792] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   17.223921] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   17.223969] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.429130] ACPI: AC Adapter [AC] (on-line)
[   17.492159] intel_rng: FWH not detected
[   17.593496] ACPI: Battery Slot [BAT0] (battery present)
[   17.800950] ieee80211_crypt: registered algorithm 'NULL'
[   17.845621] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.845625] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.904144] Yenta: CardBus bridge found at 0000:06:06.0 [103c:3081]
[   17.904168] Yenta: Enabling burst memory read transactions
[   17.904174] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.904176] Yenta: Routing CardBus interrupts to PCI
[   17.904182] Yenta TI: socket 0000:06:06.0, mfunc 0x01aa1b02, devctl 0x64
[   18.000071] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   18.000075] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.136835] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   18.136841] Socket status: 30000006
[   18.136843] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   18.136849] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   18.136852] cs: IO port probe 0x3000-0x3fff: clean.
[   18.137089] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   18.224310] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 20 (level, low) -> IRQ 18
[   18.280643] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.308491] sdhci: Secure Digital Host Controller Interface driver
[   18.308495] sdhci: Copyright(c) Pierre Ossman
[   18.600063] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   19.476271] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   19.676238] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   20.158690] input: PS/2 Mouse as /devices/virtual/input/input10
[   20.200501] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input11
[   20.594714] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   20.594758] ACPI: PCI Interrupt 0000:06:06.3[A] -> GSI 22 (level, low) -> IRQ 17
[   20.594837] sdhci: SDHCI controller found at 0000:06:06.4 [104c:8034] (rev 0)
[   20.594854] ACPI: PCI Interrupt 0000:06:06.4[A] -> GSI 22 (level, low) -> IRQ 17
[   20.594868] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   20.594908] mmc0: SDHCI at 0xb0109000 irq 17 DMA
[   20.594919] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it.
[   20.594945] mmc1: SDHCI at 0xb0108c00 irq 17 DMA
[   20.594955] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it.
[   20.594980] mmc2: SDHCI at 0xb0108800 irq 17 DMA
[   20.595024] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 16
[   20.595038] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   20.597701] cs: IO port probe 0x100-0x3af: clean.
[   20.599375] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.600097] cs: IO port probe 0x820-0x8ff: clean.
[   20.600716] cs: IO port probe 0xc00-0xcf7: clean.
[   20.601464] cs: IO port probe 0xa00-0xaff: clean.
[   20.612555] tifm_core: MMC/SD card detected in socket 0:3
[   20.738232] mmc3: new SDHC card at address 0007
[   20.760110] mmcblk0: mmc3:0007 SD8GB 8007680KiB (ro)
[   20.760145]  mmcblk0:<3>mmcblk0: error -84 transferring data
[   20.760324] end_request: I/O error, dev mmcblk0, sector 0
[   20.760328] Buffer I/O error on device mmcblk0, logical block 0
[   20.760482] mmcblk0: error -84 transferring data
[   20.760496] end_request: I/O error, dev mmcblk0, sector 0
[   20.760499] Buffer I/O error on device mmcblk0, logical block 0
[   20.760631] mmcblk0: error -84 transferring data
[   20.760633] end_request: I/O error, dev mmcblk0, sector 0
[   20.760635] Buffer I/O error on device mmcblk0, logical block 0
[   20.760777] mmcblk0: error -84 transferring data
[   20.760780] end_request: I/O error, dev mmcblk0, sector 0
[   20.760782] Buffer I/O error on device mmcblk0, logical block 0
[   20.760915] mmcblk0: error -84 transferring data
[   20.760917] end_request: I/O error, dev mmcblk0, sector 0
[   20.760920] Buffer I/O error on device mmcblk0, logical block 0
[   20.760926] ldm_validate_partition_table(): Disk read failed.
[   20.761060] mmcblk0: error -84 transferring data
[   20.761062] end_request: I/O error, dev mmcblk0, sector 0
[   20.761064] Buffer I/O error on device mmcblk0, logical block 0
[   20.761192] mmcblk0: error -84 transferring data
[   20.761194] end_request: I/O error, dev mmcblk0, sector 0
[   20.761196] Buffer I/O error on device mmcblk0, logical block 0
[   20.761506] mmcblk0: error -84 transferring data
[   20.761508] end_request: I/O error, dev mmcblk0, sector 0
[   20.761621] mmcblk0: error -84 transferring data
[   20.761623] end_request: I/O error, dev mmcblk0, sector 0
[   20.761628] Dev mmcblk0: unable to read RDB block 0
[   20.761772] mmcblk0: error -84 transferring data
[   20.761774] end_request: I/O error, dev mmcblk0, sector 0
[   20.761914] mmcblk0: error -84 transferring data
[   20.761916] end_request: I/O error, dev mmcblk0, sector 0
[   20.762036] mmcblk0: error -84 transferring data
[   20.762038] end_request: I/O error, dev mmcblk0, sector 24
[   20.762198] mmcblk0: error -84 transferring data
[   20.762201] end_request: I/O error, dev mmcblk0, sector 24
[   20.762364] mmcblk0: error -84 transferring data
[   20.762366] end_request: I/O error, dev mmcblk0, sector 0
[   20.762487] mmcblk0: error -84 transferring data
[   20.762489] end_request: I/O error, dev mmcblk0, sector 0
[   20.762494]  unable to read partition table
[   20.767146] mmcblk0: error -84 transferring data
[   20.767151] end_request: I/O error, dev mmcblk0, sector 0
[   20.767156] end_request: I/O error, dev mmcblk0, sector 8
[   20.767159] end_request: I/O error, dev mmcblk0, sector 16
[   20.767161] end_request: I/O error, dev mmcblk0, sector 24
[   20.767291] mmcblk0: error -84 transferring data
[   20.767293] end_request: I/O error, dev mmcblk0, sector 0
[   20.789411] intel8x0_measure_ac97_clock: measured 55480 usecs
[   20.789414] intel8x0: clocking to 48000
[   20.897961] lp: driver loaded but no devices found
[   21.074930] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   21.156049] EXT3 FS on sda1, internal journal
[   21.211809] device-mapper: uevent: version 1.0.3
[   21.211840] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   21.843292] No dock devices found.
[   22.490631] apm: BIOS not found.
[   22.557201] ppdev: user-space parallel port driver
[   22.595585] NET: Registered protocol family 10
[   22.596066] lo: Disabled Privacy Extensions
[   22.635805] audit(1231538214.354:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5189 profile="/usr/sbin/cupsd" namespace="default"
[   49.427519] Marking TSC unstable due to: cpufreq changes.
[   50.766264] mmcblk0: error -84 transferring data
[   50.766289] end_request: I/O error, dev mmcblk0, sector 0
[   50.766296] printk: 13 messages suppressed.
[   50.766301] Buffer I/O error on device mmcblk0, logical block 0
[   50.766311] end_request: I/O error, dev mmcblk0, sector 8
[   50.766316] Buffer I/O error on device mmcblk0, logical block 1
[   50.766322] end_request: I/O error, dev mmcblk0, sector 16
[   50.766327] end_request: I/O error, dev mmcblk0, sector 24
[   50.768151] mmcblk0: error -84 transferring data
[   50.768158] end_request: I/O error, dev mmcblk0, sector 0
[   50.851673] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   51.044333] Bluetooth: Core ver 2.11
[   51.045146] NET: Registered protocol family 31
[   51.045152] Bluetooth: HCI device and connection manager initialized
[   51.045160] Bluetooth: HCI socket layer initialized
[   51.098263] Bluetooth: L2CAP ver 2.9
[   51.098270] Bluetooth: L2CAP socket layer initialized
[   23.647252] Bluetooth: RFCOMM socket layer initialized
[   23.647441] Bluetooth: RFCOMM TTY layer initialized
[   23.647445] Bluetooth: RFCOMM ver 1.8
[   52.682915] NET: Registered protocol family 17
[   25.439248] [drm] Initialized drm 1.1.0 20060810
[   25.448515] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 22
[   25.448524] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.448597] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   59.181151] eth0: no IPv6 routers present
[ 7350.097541] tifm0 : demand removing card from socket 0:3
[ 7350.097597] mmc3: card 0007 removed
[ 7376.151500] tifm_core: MMC/SD card detected in socket 0:3
[ 7376.266180] mmc3: new SDHC card at address 0007
[ 7376.266629] mmcblk0: mmc3:0007 SD8GB 8007680KiB (ro)
[ 7376.266689]  mmcblk0:<3>mmcblk0: error -84 transferring data
[ 7376.267148] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.267154] printk: 3 messages suppressed.
[ 7376.267159] Buffer I/O error on device mmcblk0, logical block 0
[ 7376.267740] mmcblk0: error -84 transferring data
[ 7376.267746] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.267751] Buffer I/O error on device mmcblk0, logical block 0
[ 7376.268166] mmcblk0: error -84 transferring data
[ 7376.268172] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.268178] Buffer I/O error on device mmcblk0, logical block 0
[ 7376.269077] mmcblk0: error -84 transferring data
[ 7376.269083] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.269089] Buffer I/O error on device mmcblk0, logical block 0
[ 7376.269561] mmcblk0: error -84 transferring data
[ 7376.269566] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.269572] Buffer I/O error on device mmcblk0, logical block 0
[ 7376.269585] ldm_validate_partition_table(): Disk read failed.
[ 7376.270600] mmcblk0: error -84 transferring data
[ 7376.270606] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.270611] Buffer I/O error on device mmcblk0, logical block 0
[ 7376.271165] mmcblk0: error -84 transferring data
[ 7376.271170] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.271175] Buffer I/O error on device mmcblk0, logical block 0
[ 7376.272468] mmcblk0: error -84 transferring data
[ 7376.272475] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.272480] Buffer I/O error on device mmcblk0, logical block 0
[ 7376.272989] mmcblk0: error -84 transferring data
[ 7376.272995] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.273000] Buffer I/O error on device mmcblk0, logical block 0
[ 7376.273011] Dev mmcblk0: unable to read RDB block 0
[ 7376.273818] mmcblk0: error -84 transferring data
[ 7376.273824] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.273829] Buffer I/O error on device mmcblk0, logical block 0
[ 7376.274580] mmcblk0: error -84 transferring data
[ 7376.274586] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.275177] mmcblk0: error -84 transferring data
[ 7376.275184] end_request: I/O error, dev mmcblk0, sector 24
[ 7376.275689] mmcblk0: error -84 transferring data
[ 7376.275696] end_request: I/O error, dev mmcblk0, sector 24
[ 7376.276201] mmcblk0: error -84 transferring data
[ 7376.276208] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.276708] mmcblk0: error -84 transferring data
[ 7376.276715] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.276725]  unable to read partition table
[ 7376.298475] mmcblk0: error -84 transferring data
[ 7376.298486] end_request: I/O error, dev mmcblk0, sector 0
[ 7376.299124] mmcblk0: error -84 transferring data
[ 7376.299131] end_request: I/O error, dev mmcblk0, sector 8
[ 7376.299138] end_request: I/O error, dev mmcblk0, sector 16
[ 7376.299144] end_request: I/O error, dev mmcblk0, sector 24
[ 7376.300328] mmcblk0: error -84 transferring data
[ 7376.300335] end_request: I/O error, dev mmcblk0, sector 0
[ 7407.148157] tifm0 : demand removing card from socket 0:3
[ 7407.148208] mmc3: card 0007 removed
[ 7432.249601] tifm_core: MMC/SD card detected in socket 0:3
[ 7432.364748] mmc3: new SDHC card at address 0007
[ 7432.365182] mmcblk0: mmc3:0007 SD8GB 8007680KiB (ro)
[ 7432.365243]  mmcblk0:<3>mmcblk0: error -84 transferring data
[ 7432.365779] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.365785] printk: 10 messages suppressed.
[ 7432.365790] Buffer I/O error on device mmcblk0, logical block 0
[ 7432.366666] mmcblk0: error -84 transferring data
[ 7432.366673] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.366678] Buffer I/O error on device mmcblk0, logical block 0
[ 7432.367203] mmcblk0: error -84 transferring data
[ 7432.367209] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.367214] Buffer I/O error on device mmcblk0, logical block 0
[ 7432.367909] mmcblk0: error -84 transferring data
[ 7432.367915] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.367921] Buffer I/O error on device mmcblk0, logical block 0
[ 7432.368701] mmcblk0: error -84 transferring data
[ 7432.368708] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.368714] Buffer I/O error on device mmcblk0, logical block 0
[ 7432.368727] ldm_validate_partition_table(): Disk read failed.
[ 7432.369669] mmcblk0: error -84 transferring data
[ 7432.369676] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.369681] Buffer I/O error on device mmcblk0, logical block 0
[ 7432.370434] mmcblk0: error -84 transferring data
[ 7432.370440] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.370446] Buffer I/O error on device mmcblk0, logical block 0
[ 7432.371144] mmcblk0: error -84 transferring data
[ 7432.371151] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.371156] Buffer I/O error on device mmcblk0, logical block 0
[ 7432.371854] mmcblk0: error -84 transferring data
[ 7432.371861] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.371866] Buffer I/O error on device mmcblk0, logical block 0
[ 7432.371878] Dev mmcblk0: unable to read RDB block 0
[ 7432.372683] mmcblk0: error -84 transferring data
[ 7432.372690] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.372695] Buffer I/O error on device mmcblk0, logical block 0
[ 7432.373493] mmcblk0: error -84 transferring data
[ 7432.373500] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.374084] mmcblk0: error -84 transferring data
[ 7432.374091] end_request: I/O error, dev mmcblk0, sector 24
[ 7432.374594] mmcblk0: error -84 transferring data
[ 7432.374601] end_request: I/O error, dev mmcblk0, sector 24
[ 7432.375106] mmcblk0: error -84 transferring data
[ 7432.375113] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.375616] mmcblk0: error -84 transferring data
[ 7432.375623] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.375633]  unable to read partition table
[ 7432.399891] mmcblk0: error -84 transferring data
[ 7432.399915] end_request: I/O error, dev mmcblk0, sector 0
[ 7432.400512] mmcblk0: error -84 transferring data
[ 7432.400520] end_request: I/O error, dev mmcblk0, sector 8
[ 7432.400527] end_request: I/O error, dev mmcblk0, sector 16
[ 7432.400533] end_request: I/O error, dev mmcblk0, sector 24
[ 7432.401850] mmcblk0: error -84 transferring data
[ 7432.401857] end_request: I/O error, dev mmcblk0, sector 0
[ 7448.493774] tifm0 : demand removing card from socket 0:3
[ 7448.493823] mmc3: card 0007 removed
[ 7450.473800] tifm_core: MMC/SD card detected in socket 0:3
[ 7450.593620] mmc3: new SDHC card at address 0007
[ 7450.594219] mmcblk0: mmc3:0007 SD8GB 8007680KiB (ro)
[ 7450.594280]  mmcblk0:<3>mmcblk0: error -84 transferring data
[ 7450.595041] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.595047] printk: 10 messages suppressed.
[ 7450.595052] Buffer I/O error on device mmcblk0, logical block 0
[ 7450.595802] mmcblk0: error -84 transferring data
[ 7450.595809] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.595814] Buffer I/O error on device mmcblk0, logical block 0
[ 7450.596729] mmcblk0: error -84 transferring data
[ 7450.596736] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.596742] Buffer I/O error on device mmcblk0, logical block 0
[ 7450.597622] mmcblk0: error -84 transferring data
[ 7450.597629] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.597634] Buffer I/O error on device mmcblk0, logical block 0
[ 7450.598330] mmcblk0: error -84 transferring data
[ 7450.598337] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.598343] Buffer I/O error on device mmcblk0, logical block 0
[ 7450.598355] ldm_validate_partition_table(): Disk read failed.
[ 7450.599202] mmcblk0: error -84 transferring data
[ 7450.599209] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.599215] Buffer I/O error on device mmcblk0, logical block 0
[ 7450.599968] mmcblk0: error -84 transferring data
[ 7450.599974] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.599980] Buffer I/O error on device mmcblk0, logical block 0
[ 7450.600332] mmcblk0: error -84 transferring data
[ 7450.600337] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.600343] Buffer I/O error on device mmcblk0, logical block 0
[ 7450.601239] mmcblk0: error -84 transferring data
[ 7450.601245] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.601250] Buffer I/O error on device mmcblk0, logical block 0
[ 7450.601262] Dev mmcblk0: unable to read RDB block 0
[ 7450.601725] mmcblk0: error -84 transferring data
[ 7450.601730] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.601735] Buffer I/O error on device mmcblk0, logical block 0
[ 7450.602737] mmcblk0: error -84 transferring data
[ 7450.602743] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.603317] mmcblk0: error -84 transferring data
[ 7450.603323] end_request: I/O error, dev mmcblk0, sector 24
[ 7450.603926] mmcblk0: error -84 transferring data
[ 7450.603932] end_request: I/O error, dev mmcblk0, sector 24
[ 7450.604545] mmcblk0: error -84 transferring data
[ 7450.604552] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.605052] mmcblk0: error -84 transferring data
[ 7450.605059] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.605070]  unable to read partition table
[ 7450.629846] mmcblk0: error -84 transferring data
[ 7450.629871] end_request: I/O error, dev mmcblk0, sector 0
[ 7450.630458] mmcblk0: error -84 transferring data
[ 7450.630466] end_request: I/O error, dev mmcblk0, sector 8
[ 7450.630473] end_request: I/O error, dev mmcblk0, sector 16
[ 7450.630478] end_request: I/O error, dev mmcblk0, sector 24
[ 7450.631829] mmcblk0: error -84 transferring data
[ 7450.631836] end_request: I/O error, dev mmcblk0, sector 0
[ 9360.032380] mmcblk0: error -84 transferring data
[ 9360.032404] end_request: I/O error, dev mmcblk0, sector 0
[ 9360.032410] printk: 10 messages suppressed.
[ 9360.032415] Buffer I/O error on device mmcblk0, logical block 0
[ 9360.032425] end_request: I/O error, dev mmcblk0, sector 8
[ 9360.032429] Buffer I/O error on device mmcblk0, logical block 1
[ 9360.032436] end_request: I/O error, dev mmcblk0, sector 16
[ 9360.032440] Buffer I/O error on device mmcblk0, logical block 2
[ 9360.032447] end_request: I/O error, dev mmcblk0, sector 24
[ 9360.032451] Buffer I/O error on device mmcblk0, logical block 3
[ 9360.034720] mmcblk0: error -84 transferring data
[ 9360.034727] end_request: I/O error, dev mmcblk0, sector 0
[ 9360.034733] Buffer I/O error on device mmcblk0, logical block 0
[ 9360.035512] mmcblk0: error -84 transferring data
[ 9360.035519] end_request: I/O error, dev mmcblk0, sector 0
[ 9360.035525] Buffer I/O error on device mmcblk0, logical block 0
[ 9360.035533] end_request: I/O error, dev mmcblk0, sector 8
[ 9360.035537] Buffer I/O error on device mmcblk0, logical block 1
[ 9360.035544] end_request: I/O error, dev mmcblk0, sector 16
[ 9360.035548] Buffer I/O error on device mmcblk0, logical block 2
[ 9360.035554] end_request: I/O error, dev mmcblk0, sector 24
[ 9360.035559] Buffer I/O error on device mmcblk0, logical block 3
[ 9360.037581] mmcblk0: error -84 transferring data
[ 9360.037588] end_request: I/O error, dev mmcblk0, sector 0
[ 9360.037594] Buffer I/O error on device mmcblk0, logical block 0
[ 9361.344961] tifm0 : demand removing card from socket 0:3
[ 9361.345013] mmc3: card 0007 removed
[ 9386.395979] tifm_core: MMC/SD card detected in socket 0:3
[ 9386.524631] mmc3: new SDHC card at address 0007
[ 9386.525111] mmcblk0: mmc3:0007 SD8GB 8007680KiB (ro)
[ 9386.525176]  mmcblk0:<3>mmcblk0: error -84 transferring data
[ 9386.525646] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.525653] Buffer I/O error on device mmcblk0, logical block 0
[ 9386.526144] mmcblk0: error -84 transferring data
[ 9386.526150] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.526155] Buffer I/O error on device mmcblk0, logical block 0
[ 9386.526876] mmcblk0: error -84 transferring data
[ 9386.526883] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.526888] Buffer I/O error on device mmcblk0, logical block 0
[ 9386.527592] mmcblk0: error -84 transferring data
[ 9386.527598] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.527604] Buffer I/O error on device mmcblk0, logical block 0
[ 9386.528304] mmcblk0: error -84 transferring data
[ 9386.528311] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.528316] Buffer I/O error on device mmcblk0, logical block 0
[ 9386.528330] ldm_validate_partition_table(): Disk read failed.
[ 9386.529161] mmcblk0: error -84 transferring data
[ 9386.529168] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.529173] Buffer I/O error on device mmcblk0, logical block 0
[ 9386.529985] mmcblk0: error -84 transferring data
[ 9386.529992] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.529998] Buffer I/O error on device mmcblk0, logical block 0
[ 9386.530702] mmcblk0: error -84 transferring data
[ 9386.530708] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.530714] Buffer I/O error on device mmcblk0, logical block 0
[ 9386.531413] mmcblk0: error -84 transferring data
[ 9386.531419] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.531425] Buffer I/O error on device mmcblk0, logical block 0
[ 9386.531438] Dev mmcblk0: unable to read RDB block 0
[ 9386.532251] mmcblk0: error -84 transferring data
[ 9386.532258] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.532263] Buffer I/O error on device mmcblk0, logical block 0
[ 9386.533020] mmcblk0: error -84 transferring data
[ 9386.533026] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.533598] mmcblk0: error -84 transferring data
[ 9386.533605] end_request: I/O error, dev mmcblk0, sector 24
[ 9386.534141] mmcblk0: error -84 transferring data
[ 9386.534148] end_request: I/O error, dev mmcblk0, sector 24
[ 9386.534655] mmcblk0: error -84 transferring data
[ 9386.534662] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.535167] mmcblk0: error -84 transferring data
[ 9386.535173] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.535185]  unable to read partition table
[ 9386.556698] mmcblk0: error -84 transferring data
[ 9386.556722] end_request: I/O error, dev mmcblk0, sector 0
[ 9386.557301] mmcblk0: error -84 transferring data
[ 9386.557308] end_request: I/O error, dev mmcblk0, sector 8
[ 9386.557316] end_request: I/O error, dev mmcblk0, sector 16
[ 9386.557321] end_request: I/O error, dev mmcblk0, sector 24
[ 9386.558550] mmcblk0: error -84 transferring data
[ 9386.558557] end_request: I/O error, dev mmcblk0, sector 0
[ 9403.925403] tifm0 : demand removing card from socket 0:3
[ 9403.925452] mmc3: card 0007 removed
[ 9405.014971] tifm_core: MMC/SD card detected in socket 0:3
[ 9405.110714] mmc3: new SDHC card at address 0007
[ 9405.111158] mmcblk0: mmc3:0007 SD8GB 8007680KiB (ro)
[ 9405.111218]  mmcblk0:<3>mmcblk0: error -84 transferring data
[ 9405.111684] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.111690] printk: 10 messages suppressed.
[ 9405.111695] Buffer I/O error on device mmcblk0, logical block 0
[ 9405.112289] mmcblk0: error -84 transferring data
[ 9405.112295] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.112300] Buffer I/O error on device mmcblk0, logical block 0
[ 9405.112737] mmcblk0: error -84 transferring data
[ 9405.112743] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.112748] Buffer I/O error on device mmcblk0, logical block 0
[ 9405.113639] mmcblk0: error -84 transferring data
[ 9405.113645] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.113650] Buffer I/O error on device mmcblk0, logical block 0
[ 9405.114129] mmcblk0: error -84 transferring data
[ 9405.114134] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.114140] Buffer I/O error on device mmcblk0, logical block 0
[ 9405.114154] ldm_validate_partition_table(): Disk read failed.
[ 9405.115170] mmcblk0: error -84 transferring data
[ 9405.115176] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.115181] Buffer I/O error on device mmcblk0, logical block 0
[ 9405.115753] mmcblk0: error -84 transferring data
[ 9405.115759] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.115764] Buffer I/O error on device mmcblk0, logical block 0
[ 9405.117061] mmcblk0: error -84 transferring data
[ 9405.117068] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.117073] Buffer I/O error on device mmcblk0, logical block 0
[ 9405.117581] mmcblk0: error -84 transferring data
[ 9405.117587] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.117592] Buffer I/O error on device mmcblk0, logical block 0
[ 9405.117604] Dev mmcblk0: unable to read RDB block 0
[ 9405.118413] mmcblk0: error -84 transferring data
[ 9405.118419] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.118425] Buffer I/O error on device mmcblk0, logical block 0
[ 9405.119181] mmcblk0: error -84 transferring data
[ 9405.119188] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.119766] mmcblk0: error -84 transferring data
[ 9405.119773] end_request: I/O error, dev mmcblk0, sector 24
[ 9405.120276] mmcblk0: error -84 transferring data
[ 9405.120282] end_request: I/O error, dev mmcblk0, sector 24
[ 9405.120794] mmcblk0: error -84 transferring data
[ 9405.120800] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.121303] mmcblk0: error -84 transferring data
[ 9405.121309] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.121321]  unable to read partition table
[ 9405.142706] mmcblk0: error -84 transferring data
[ 9405.142730] end_request: I/O error, dev mmcblk0, sector 0
[ 9405.143313] mmcblk0: error -84 transferring data
[ 9405.143321] end_request: I/O error, dev mmcblk0, sector 8
[ 9405.143328] end_request: I/O error, dev mmcblk0, sector 16
[ 9405.143334] end_request: I/O error, dev mmcblk0, sector 24
[ 9405.144535] mmcblk0: error -84 transferring data
[ 9405.144542] end_request: I/O error, dev mmcblk0, sector 0
catalina@catalina-hp:~$ 

Any help would be appreciated.
Catalina.

---

### Post by lilbluegremlin on 2009-01-11
Anyone have any ideas on helping us with this problem? 
please?

---

