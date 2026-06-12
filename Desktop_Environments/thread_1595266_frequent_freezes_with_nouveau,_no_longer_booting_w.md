---
title: "frequent freezes with nouveau, no longer booting with nvidia"
date: 2010-10-13
forum: Desktop Environments
---

### Post by reto on 2010-10-13
I made a fresh installation of Ubuntu 10.10 (64 bit) on a Sony PCG-81112M, the graphic cards is identified by lspci as "nVidia Corporation GT216 [GeForce FT 330M]". Quite frequently everything but the mouse pointer freezed on the screen, I found no way to recover from these situations but to restart the computer using the power button.

I decided to install the proprietary driver (as this is the recommended driver, I was confident this would solve the problem). As a consequence the system now hangs on boot after showing the Ubuntu 10.10 inial logo/text.

I could start in recovery mode, but I'm not sure to which driver I should try to change to. I really need no fancy 3d stuff, just a robust computer to which I can attach and detach an external screen.

---

### Post by P4man on 2010-10-13
Can you try the recovery mode, then failsafeX and then select the low graphics mode, and see if your PC works okay then? Its just that the problem might something entirely different as the nouveau driver.

---

### Post by reto on 2010-10-13
So after failsafe mode I couldn't configure display settings as it started the nvidia tool which in turn compalined about nvidia drivers not being in use, so I disabled the nvidia drivers using the "Additional Drivers" Control Panel and I'n now back to nouveau. Can I use that failsafe driver while still having a decent resolution?

With nouveau the problem only occured after some time (up to several hours) of actually working at the computer, it never occured by just letting the computer on over night.

---

### Post by P4man on 2010-10-13
Im not sure. On my laptop with intel IGP, "low graphics" is full resolution, but on other PCs its not.

Anyway, Im just asking because I suspect your problem may have nothing to do with the nouveau drivers, which generally work fine. The problem you describe sounds more like an issue being reported on this forum in relation with atheros wifi drivers, but it could be anything.

Can you post the output of these three commands:

```
dmesg
```

```
lsusb
```

```
lspci
```

---

### Post by reto on 2010-10-13
dmesg:
```
[    2.505513] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.505516] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    2.505518] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    2.505521] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    2.505523] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    2.505526] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    2.505528] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    2.505531] pci_bus 0000:00: resource 13 [mem 0xd0000000-0xfeafffff]
[    2.505534] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    2.505536] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xe30fffff]
[    2.505539] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    2.505541] pci_bus 0000:02: resource 1 [mem 0xe7a00000-0xe8dfffff]
[    2.505544] pci_bus 0000:02: resource 2 [mem 0xe8f00000-0xe90fffff 64bit pref]
[    2.505547] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    2.505549] pci_bus 0000:03: resource 1 [mem 0xe6600000-0xe79fffff]
[    2.505551] pci_bus 0000:03: resource 2 [mem 0xe9100000-0xe92fffff 64bit pref]
[    2.505554] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
[    2.505557] pci_bus 0000:04: resource 1 [mem 0xe5200000-0xe65fffff]
[    2.505559] pci_bus 0000:04: resource 2 [mem 0xe9300000-0xe94fffff 64bit pref]
[    2.505562] pci_bus 0000:05: resource 0 [io  0x9000-0x9fff]
[    2.505564] pci_bus 0000:05: resource 1 [mem 0xe3200000-0xe51fffff]
[    2.505567] pci_bus 0000:05: resource 2 [mem 0xe9500000-0xe96fffff 64bit pref]
[    2.505570] pci_bus 0000:0d: resource 4 [io  0x0000-0x0cf7]
[    2.505572] pci_bus 0000:0d: resource 5 [io  0x0d00-0xffff]
[    2.505574] pci_bus 0000:0d: resource 6 [mem 0x000a0000-0x000bffff]
[    2.505577] pci_bus 0000:0d: resource 7 [mem 0x000d0000-0x000d3fff]
[    2.505579] pci_bus 0000:0d: resource 8 [mem 0x000d4000-0x000d7fff]
[    2.505582] pci_bus 0000:0d: resource 9 [mem 0x000d8000-0x000dbfff]
[    2.505584] pci_bus 0000:0d: resource 10 [mem 0x000dc000-0x000dffff]
[    2.505587] pci_bus 0000:0d: resource 11 [mem 0x000e0000-0x000e3fff]
[    2.505589] pci_bus 0000:0d: resource 12 [mem 0x000e4000-0x000e7fff]
[    2.505592] pci_bus 0000:0d: resource 13 [mem 0xd0000000-0xfeafffff]
[    2.505623] NET: Registered protocol family 2
[    2.505914] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    2.507246] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.510816] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.511245] TCP: Hash tables configured (established 524288 bind 65536)
[    2.511247] TCP reno registered
[    2.511267] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    2.511362] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    2.511526] NET: Registered protocol family 1
[    2.628234] pci 0000:01:00.0: Boot video device
[    2.628390] PCI: CLS 64 bytes, default 64
[    2.628392] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.628395] Placing 64MB software IO TLB between ffff880001fde000 - ffff880005fde000
[    2.628397] software IO TLB at phys 0x1fde000 - 0x5fde000
[    2.628921] Scanning for low memory corruption every 60 seconds
[    2.629036] audit: initializing netlink socket (disabled)
[    2.629045] type=2000 audit(1286954849.450:1): initialized
[    2.647266] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.649082] VFS: Disk quotas dquot_6.5.2
[    2.649150] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.649791] fuse init (API version 7.14)
[    2.649883] msgmni has been set to 11922
[    2.652393] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.652396] io scheduler noop registered
[    2.652398] io scheduler deadline registered
[    2.652441] io scheduler cfq registered (default)
[    2.652569] pcieport 0000:00:03.0: setting latency timer to 64
[    2.652598]   alloc irq_desc for 45 on node -1
[    2.652600]   alloc kstat_irqs on node -1
[    2.652609] pcieport 0000:00:03.0: irq 45 for MSI/MSI-X
[    2.652682] pcieport 0000:00:1c.0: setting latency timer to 64
[    2.652718]   alloc irq_desc for 46 on node -1
[    2.652720]   alloc kstat_irqs on node -1
[    2.652732] pcieport 0000:00:1c.0: irq 46 for MSI/MSI-X
[    2.652819] pcieport 0000:00:1c.1: setting latency timer to 64
[    2.652856]   alloc irq_desc for 47 on node -1
[    2.652858]   alloc kstat_irqs on node -1
[    2.652869] pcieport 0000:00:1c.1: irq 47 for MSI/MSI-X
[    2.652948] pcieport 0000:00:1c.2: setting latency timer to 64
[    2.652984]   alloc irq_desc for 48 on node -1
[    2.652986]   alloc kstat_irqs on node -1
[    2.652998] pcieport 0000:00:1c.2: irq 48 for MSI/MSI-X
[    2.653083] pcieport 0000:00:1c.5: setting latency timer to 64
[    2.653119]   alloc irq_desc for 49 on node -1
[    2.653121]   alloc kstat_irqs on node -1
[    2.653133] pcieport 0000:00:1c.5: irq 49 for MSI/MSI-X
[    2.653357] \_SB_.PCI0:_OSC invalid UUID
[    2.653360] _OSC request data:1 0 1f 
[    2.653364] aer 0000:00:03.0:pcie02: AER service couldn't init device: _OSC failed
[    2.653388] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.653508] \_SB_.PCI0:_OSC invalid UUID
[    2.653510] _OSC request data:1 0 1f 
[    2.653640] \_SB_.PCI0:_OSC invalid UUID
[    2.653642] _OSC request data:1 0 1f 
[    2.653770] \_SB_.PCI0:_OSC invalid UUID
[    2.653772] _OSC request data:1 0 1f 
[    2.653898] \_SB_.PCI0:_OSC invalid UUID
[    2.653900] _OSC request data:1 0 1f 
[    2.654043] \_SB_.PCI0:_OSC invalid UUID
[    2.654045] _OSC request data:1 0 1f 
[    2.654172] \_SB_.PCI0:_OSC invalid UUID
[    2.654174] _OSC request data:1 0 1f 
[    2.654300] \_SB_.PCI0:_OSC invalid UUID
[    2.654302] _OSC request data:1 0 1f 
[    2.654429] \_SB_.PCI0:_OSC invalid UUID
[    2.654431] _OSC request data:1 0 1f 
[    2.654455] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.654532] intel_idle: MWAIT substates: 0x1120
[    2.654534] intel_idle: v0.4 model 0x1E
[    2.654536] intel_idle: lapic_timer_reliable_states 0x2
[    2.655527] ACPI: AC Adapter [ADP1] (on-line)
[    2.655613] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    2.657483] ACPI: Lid Switch [LID0]
[    2.657527] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    2.657539] ACPI: Power Button [PWRB]
[    2.658544] ACPI: acpi_idle yielding to intel_idle
[    2.673698] thermal LNXTHERM:01: registered as thermal_zone0
[    2.673707] ACPI: Thermal Zone [TZ00] (66 C)
[    2.675682] thermal LNXTHERM:02: registered as thermal_zone1
[    2.675689] ACPI: Thermal Zone [TZ01] (66 C)
[    2.675776] ERST: Table is not found!
[    2.676062] Linux agpgart interface v0.103
[    2.676086] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.677433] brd: module loaded
[    2.677929] loop: module loaded
[    2.678387] Fixed MDIO Bus: probed
[    2.678417] PPP generic driver version 2.4.2
[    2.678451] tun: Universal TUN/TAP device driver, 1.6
[    2.678453] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.678527] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.678559] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.678582] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.678591] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.678629] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.678666] ehci_hcd 0000:00:1a.0: debug port 2
[    2.682580] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.682600] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xe8e08000
[    2.708144] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.708264] hub 1-0:1.0: USB hub found
[    2.708269] hub 1-0:1.0: 2 ports detected
[    2.708348]   alloc irq_desc for 23 on node -1
[    2.708351]   alloc kstat_irqs on node -1
[    2.708357] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.708379] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.708387] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.708423] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.708452] ehci_hcd 0000:00:1d.0: debug port 2
[    2.712364] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.712382] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xe8e07000
[    2.723152] ACPI: Battery Slot [BAT0] (battery present)
[    2.738049] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.738172] hub 2-0:1.0: USB hub found
[    2.738176] hub 2-0:1.0: 2 ports detected
[    2.738251] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.738265] uhci_hcd: USB Universal Host Controller Interface driver
[    2.738366] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.743581] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.747401] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.747407] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.747410] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.747413] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.747416] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.747471] mice: PS/2 mouse device common for all mice
[    2.747573] rtc_cmos 00:06: RTC can wake from S4
[    2.747608] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.747647] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.747752] device-mapper: uevent: version 1.0.3
[    2.747830] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    2.747971] device-mapper: multipath: version 1.1.1 loaded
[    2.747974] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.748494] cpuidle: using governor ladder
[    2.748834] cpuidle: using governor menu
[    2.749121] TCP cubic registered
[    2.749254] NET: Registered protocol family 10
[    2.749628] lo: Disabled Privacy Extensions
[    2.749848] NET: Registered protocol family 17
[    2.755692] PM: Resume from disk failed.
[    2.755700] registered taskstats version 1
[    2.756397]   Magic number: 14:666:470
[    2.756501] rtc_cmos 00:06: setting system clock to 2010-10-13 07:27:29 UTC (1286954849)
[    2.756505] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.756506] EDD information not available.
[    2.756579] Freeing unused kernel memory: 908k freed
[    2.756702] Write protecting the kernel read-only data: 10240k
[    2.757095] Freeing unused kernel memory: 416k freed
[    2.757426] Freeing unused kernel memory: 1644k freed
[    2.768580] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.775532] udev[148]: starting version 163
[    2.809827] [Firmware Bug]: ACPI(NGFX) defines _DOD but not _DOS
[    2.863217] [drm] Initialized drm 1.1.0 20060810
[    2.974903] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.974911] nouveau 0000:01:00.0: setting latency timer to 64
[    2.975238] sdhci: Secure Digital Host Controller Interface driver
[    2.975241] sdhci: Copyright(c) Pierre Ossman
[    2.976967] sky2: driver version 1.28
[    2.977091] sky2 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.977205] sky2 0000:04:00.0: setting latency timer to 64
[    2.977439] sky2 0000:04:00.0: Yukon-2 UL 2 chip revision 0
[    2.977755] sdhci-pci 0000:03:00.0: SDHCI controller found [1180:e822] (rev 0)
[    2.978131] sdhci-pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.978338] sdhci-pci 0000:03:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.978460] sdhci-pci 0000:03:00.0: setting latency timer to 64
[    2.978693] Registered led device: mmc0::
[    2.978936] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
[    2.978960]   alloc irq_desc for 50 on node -1
[    2.978962]   alloc kstat_irqs on node -1
[    2.979114] sdhci-pci 0000:03:00.4: SDHCI controller found [1180:e822] (rev 0)
[    2.979262] sky2 0000:04:00.0: irq 50 for MSI/MSI-X
[    2.979483]   alloc irq_desc for 19 on node -1
[    2.979485]   alloc kstat_irqs on node -1
[    2.979491] sdhci-pci 0000:03:00.4: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.979661] sdhci-pci 0000:03:00.4: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.979782] sdhci-pci 0000:03:00.4: setting latency timer to 64
[    2.980004] Registered led device: mmc1::
[    2.980065] mmc1: SDHCI controller on PCI [0000:03:00.4] using DMA
[    2.980275] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x0a5480a2)
[    2.980747] sky2 0000:04:00.0: eth0: addr 00:24:be:c3:61:41
[    2.981119] firewire_ohci 0000:03:00.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.981130] firewire_ohci 0000:03:00.3: setting latency timer to 64
[    2.985973] ahci 0000:00:1f.2: version 3.0
[    2.985998] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.986143]   alloc irq_desc for 51 on node -1
[    2.986145]   alloc kstat_irqs on node -1
[    2.986159] ahci 0000:00:1f.2: irq 51 for MSI/MSI-X
[    2.986195] ahci: SSS flag set, parallel bus scan disabled
[    2.986229] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x23 impl SATA mode
[    2.986233] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part sxs apst 
[    2.986242] ahci 0000:00:1f.2: setting latency timer to 64
[    2.986408] scsi0 : ahci
[    2.986549] scsi1 : ahci
[    2.986696] scsi2 : ahci
[    2.986810] scsi3 : ahci
[    2.986927] scsi4 : ahci
[    2.987015] scsi5 : ahci
[    2.987295] ata1: SATA max UDMA/133 abar m2048@0xe8e06000 port 0xe8e06100 irq 51
[    2.987303] ata2: SATA max UDMA/133 abar m2048@0xe8e06000 port 0xe8e06180 irq 51
[    2.987306] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[    2.987309] ata3: DUMMY
[    2.987311] ata4: DUMMY
[    2.987312] ata5: DUMMY
[    2.987319] ata6: SATA max UDMA/133 abar m2048@0xe8e06000 port 0xe8e06380 irq 51
[    3.077131] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.078320] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    3.078324] [drm] nouveau 0000:01:00.0: BIT BIOS found
[    3.078326] [drm] nouveau 0000:01:00.0: Bios version 70.16.45.00
[    3.078328] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
[    3.078330] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
[    3.078332] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[    3.078335] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 010003f3 00010036
[    3.078337] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02011300 00000000
[    3.078339] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02422362 00020010
[    3.078341] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 0000000e 00000000
[    3.078343] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[    3.078346] [drm] nouveau 0000:01:00.0:   0: 0x00000040: type 0x40 idx 0 tag 0xff
[    3.078348] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[    3.078350] [drm] nouveau 0000:01:00.0:   2: 0x00001261: type 0x61 idx 2 tag 0x07
[    3.078360] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x6AEF
[    3.144724] acpi device:57: registered as cooling_device8
[    3.144812] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:56/LNXVIDEO:02/input/input3
[    3.144842] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[    3.150165] firewire_ohci: Added fw-ohci device 0000:03:00.3, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x0
[    3.157682] [drm] nouveau 0000:01:00.0: 0x6D99: Condition still not met after 20ms, skipping following opcodes
[    3.187648] [drm] nouveau 0000:01:00.0: 0x6D9D: Condition still not met after 20ms, skipping following opcodes
[    3.217631] [drm] nouveau 0000:01:00.0: 0x6F23: Condition still not met after 20ms, skipping following opcodes
[    3.217645] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x6F50
[    3.230740] hub 1-1:1.0: USB hub found
[    3.230969] hub 1-1:1.0: 6 ports detected
[    3.297543] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x7E24
[    3.297560] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x7E46
[    3.340499] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.359038] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0x7FA8
[    3.359043] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    3.359046] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0x800D
[    3.359235] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    3.359544] ata1.00: ATA-8: SAMSUNG HM500JI, 2AC101C4, max UDMA/133
[    3.359552] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.369533] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    3.369743] ata1.00: configured for UDMA/133
[    3.385579] [drm] nouveau 0000:01:00.0: 0x6955: Condition still not met after 20ms, skipping following opcodes
[    3.385593] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    3.385597] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    3.385602] [drm] nouveau 0000:01:00.0: 0x57D7: parsing output script 0
[    3.385615] [drm] nouveau 0000:01:00.0: BIOS FP mode: 1920x1080 (144000kHz pixel clock)
[    3.385623] [drm] nouveau 0000:01:00.0: Detected 1024MiB VRAM
[    3.385754] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM500JI  2AC1 PQ: 0 ANSI: 5
[    3.385890] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.385983] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.386068] sd 0:0:0:0: [sda] Write Protect is off
[    3.386073] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.386107] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.386301]  sda: sda1 sda2 < sda5 >
[    3.446954] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.506273] hub 2-1:1.0: USB hub found
[    3.506485] hub 2-1:1.0: 8 ports detected
[    3.572000] [TTM] Zone  kernel: Available graphics memory: 3053650 kiB.
[    3.572007] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    3.572011] [TTM] Initializing pool allocator.
[    3.589168] usb 1-1.2: new high speed USB device using ehci_hcd and address 3
[    3.629027] firewire_core: created device fw0: GUID 0800460303336522, S400
[    3.649048] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[    3.652315] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[    3.667514] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[    3.669550] [drm] nouveau 0000:01:00.0: Detected a LVDS output
[    3.669557] [drm] nouveau 0000:01:00.0: Detected a DAC output
[    3.669559] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[    3.669562] [drm] nouveau 0000:01:00.0: Detected a LVDS connector
[    3.669608] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[    3.669632] [drm] nouveau 0000:01:00.0: Detected a HDMI connector
[    3.738260] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.740108] ata2.00: ATAPI: Optiarc BD ROM BC-5500S4, 1.Va, max UDMA/100
[    3.742049] ata2.00: configured for UDMA/100
[    3.759371] scsi 1:0:0:0: CD-ROM            Optiarc  BD ROM BC-5500S4 1.Va PQ: 0 ANSI: 5
[    3.762189] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.762192] Uniform CD-ROM driver Revision: 3.20
[    3.762285] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.762333] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.779106] usb 1-1.6: new full speed USB device using ehci_hcd and address 4
[    3.976285] usb 2-1.2: new high speed USB device using ehci_hcd and address 3
[    4.086692] hub 2-1.2:1.0: USB hub found
[    4.086792] hub 2-1.2:1.0: 4 ports detected
[    4.108011] ata6: SATA link down (SStatus 0 SControl 300)
[    4.176103] usb 2-1.5: new full speed USB device using ehci_hcd and address 4
[    4.266019] usb 2-1.5: device descriptor read/64, error -32
[    4.465827] usb 2-1.5: device descriptor read/64, error -32
[    4.499403] [drm] nouveau 0000:01:00.0: allocated 1920x1080 fb: 0x40250000, bo ffff8801a4ff4000
[    4.502333] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    4.502340] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    4.502344] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    4.503660] Console: switching to colour frame buffer device 240x67
[    4.506206] fb0: nouveaufb frame buffer device
[    4.506208] drm: registered panic notifier
[    4.506210] Slow work thread pool: Starting up
[    4.506725] Slow work thread pool: Ready
[    4.506738] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[    4.648184] usb 2-1.5: new full speed USB device using ehci_hcd and address 5
[    4.735613] usb 2-1.5: device descriptor read/64, error -32
[    4.740499] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    4.766429] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.914194] usb 2-1.5: device descriptor read/64, error -32
[    5.104013] usb 2-1.5: new full speed USB device using ehci_hcd and address 6
[    5.523317] usb 2-1.5: device not accepting address 6, error -32
[    5.603423] usb 2-1.5: new full speed USB device using ehci_hcd and address 7
[    6.022764] usb 2-1.5: device not accepting address 7, error -32
[    6.023057] hub 2-1:1.0: unable to enumerate USB device on port 5
[    6.102956] usb 2-1.2.1: new low speed USB device using ehci_hcd and address 8
[    6.302711] usb 2-1.2.2: new low speed USB device using ehci_hcd and address 9
[    6.522507] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 10
[   11.618240] usb 2-1.2.4: device descriptor read/64, error -71
[   13.833115] udev[578]: starting version 163
[   13.919979] Adding 17891324k swap on /dev/sda5.  Priority:-1 extents:1 across:17891324k 
[   13.938336] lp: driver loaded but no devices found
[   13.955437] cfg80211: Calling CRDA to update world regulatory domain
[   13.976221] type=1400 audit(1286954860.722:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=692 comm="apparmor_parser"
[   13.976972] type=1400 audit(1286954860.722:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=692 comm="apparmor_parser"
[   13.977389] type=1400 audit(1286954860.722:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=692 comm="apparmor_parser"
[   14.011029] cfg80211: World regulatory domain updated:
[   14.011033]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.011036]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.011040]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.011042]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.011045]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.011048]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.011672] EDAC MC: Ver: 2.1.0 Oct 10 2010
[   14.015330] EDAC i7core: Device not found: dev 00.0 PCI ID 8086:2c50
[   14.036127] Bluetooth: Core ver 2.15
[   14.036150] NET: Registered protocol family 31
[   14.036153] Bluetooth: HCI device and connection manager initialized
[   14.036156] Bluetooth: HCI socket layer initialized
[   14.098787] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   14.098999] usbcore: registered new interface driver btusb
[   14.124589] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.124591] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   14.124739] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.124769] iwlagn 0000:02:00.0: setting latency timer to 64
[   14.124914] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   14.139419] Linux video capture interface: v2.00
[   14.142944] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.143092]   alloc irq_desc for 52 on node -1
[   14.143095]   alloc kstat_irqs on node -1
[   14.143164] iwlagn 0000:02:00.0: irq 52 for MSI/MSI-X
[   14.156586] sony-laptop: Sony Notebook Control Driver v0.6.
[   14.182864] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SNY5001:00/input/input4
[   14.182943] input: Sony Vaio Jogdial as /devices/virtual/input/input5
[   14.182995] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[   14.197676]   alloc irq_desc for 22 on node -1
[   14.197679]   alloc kstat_irqs on node -1
[   14.197687] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.197759]   alloc irq_desc for 53 on node -1
[   14.197761]   alloc kstat_irqs on node -1
[   14.197771] HDA Intel 0000:00:1b.0: irq 53 for MSI/MSI-X
[   14.197804] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.202923] uvcvideo: Found UVC 1.00 device <unnamed> (064e:2100)
[   14.204526] input: UVC Camera (064e:2100) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input6
[   14.204581] usbcore: registered new interface driver uvcvideo
[   14.204583] USB Video Class driver (v0.1.0)
[   14.205770] iwlagn 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[   14.213091] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.301358] hda_codec: ALC275: BIOS auto-probing.
[   14.302675] hda_codec: ALC275: no valid ADC found; using fallback 0x8
[   14.306306] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.306312] hda_intel: Disable MSI for Nvidia chipset
[   14.306447] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.359891] usbcore: registered new interface driver hiddev
[   14.363996] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.2/2-1.2.2:1.0/input/input7
[   14.364089] generic-usb 0003:046D:C001.0003: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1d.0-1.2.2/input0
[   14.364106] usbcore: registered new interface driver usbhid
[   14.364108] usbhid: USB HID core driver
[   14.520335] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.0/input/input8
[   14.520414] logitech 0003:046D:C30A.0001: input,hidraw1: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1.2.1/input0
[   14.529868] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.1/input/input9
[   14.529983] logitech 0003:046D:C30A.0002: input,hidraw2: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1.2.1/input1
[   14.548320] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.798714] type=1400 audit(1286954861.542:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1299 comm="apparmor_parser"
[   14.798750] type=1400 audit(1286954861.542:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1304 comm="apparmor_parser"
[   14.798773] type=1400 audit(1286954861.542:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1300 comm="apparmor_parser"
[   14.799478] type=1400 audit(1286954861.542:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1300 comm="apparmor_parser"
[   14.799822] type=1400 audit(1286954861.542:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1300 comm="apparmor_parser"
[   14.800063] type=1400 audit(1286954861.542:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1303 comm="apparmor_parser"
[   14.800245] type=1400 audit(1286954861.542:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1301 comm="apparmor_parser"
[   14.922368] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio2/input/input10
[   15.138140] Bluetooth: L2CAP ver 2.14
[   15.138143] Bluetooth: L2CAP socket layer initialized
[   15.143315] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.143318] Bluetooth: BNEP filters: protocol multicast
[   15.147622] Bluetooth: SCO (Voice Link) ver 0.6
[   15.147625] Bluetooth: SCO socket layer initialized
[   15.188535] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.193173] sky2 0000:04:00.0: eth0: enabling interface
[   15.194057] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.213200] Bluetooth: RFCOMM TTY layer initialized
[   15.213208] Bluetooth: RFCOMM socket layer initialized
[   15.213211] Bluetooth: RFCOMM ver 1.11
[   15.327329] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
[   15.342318] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
[   15.638989] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   15.744549] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   16.243500] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.425550] ppdev: user-space parallel port driver
[   16.832547] usb 2-1.2.4: device descriptor read/64, error -71
[   17.022535] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 11
[   18.103304] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   18.497731] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   22.105696] usb 2-1.2.4: device descriptor read/64, error -71
[   27.310170] usb 2-1.2.4: device descriptor read/64, error -71
[   27.500005] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 12
[   32.914015] usb 2-1.2.4: device not accepting address 12, error -71
[   32.994074] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 13
[   38.408217] usb 2-1.2.4: device not accepting address 13, error -71
[   38.408381] hub 2-1.2:1.0: unable to enumerate USB device on port 4
[  133.967424] Intel AES-NI instructions are not detected.
[  134.072373] padlock: VIA PadLock not detected.
[  142.353226] wlan0: authenticate with 00:04:0e:d6:58:ad (try 1)
[  142.355634] wlan0: authenticated
[  142.359079] wlan0: associate with 00:04:0e:d6:58:ad (try 1)
[  142.366080] wlan0: RX AssocResp from 00:04:0e:d6:58:ad (capab=0x451 status=0 aid=2)
[  142.366087] wlan0: associated
[  142.372100] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  152.875042] wlan0: no IPv6 routers present
[  166.895668] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  166.928687] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  166.928700] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  166.929068] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  213.900371] [drm] nouveau 0000:01:00.0: plugged HDMI Type A-1
[  224.607440] [drm] nouveau 0000:01:00.0: unplugged HDMI Type A-1
[  224.765677] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[  224.765680] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  224.765682] <3>00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff  ................
[  224.765684] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765685] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765687] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765688] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765690] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765691] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765693] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765694] 
[  224.769618] [drm] nouveau 0000:01:00.0: DDC responded, but no EDID for HDMI Type A-1
[  225.302346] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  226.072609] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  226.072624] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  226.310803] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  234.545404] [drm] nouveau 0000:01:00.0: plugged HDMI Type A-1
[  236.119430] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  236.140178] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  236.140186] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  236.140478] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  253.125113] [drm] nouveau 0000:01:00.0: unplugged HDMI Type A-1
[  253.652400] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  254.421839] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  254.421854] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  254.660027] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  275.802490] wlan0: deauthenticating from 00:04:0e:d6:58:ad by local choice (reason=3)
[  275.911973] cfg80211: All devices are disconnected, going to restore regulatory settings
[  275.911983] cfg80211: Restoring regulatory settings
[  275.911991] cfg80211: Calling CRDA to update world regulatory domain
[  275.917598] cfg80211: World regulatory domain updated:
[  275.917603]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  275.917610]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  275.917616]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  275.917621]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  275.917627]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  275.917632]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  276.660162] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 2
[  276.999284] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
[  277.014153] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
[  279.892590] [drm] nouveau 0000:01:00.0: plugged HDMI Type A-1
[  280.687280] [drm] nouveau 0000:01:00.0: 0x57D8: parsing output script 1
[  280.687295] [drm] nouveau 0000:01:00.0: 0x57D9: parsing output script 2
[  280.687308] [drm] nouveau 0000:01:00.0: 0x5616: parsing clock script 0
[  280.688086] [drm] nouveau 0000:01:00.0: 0x4E33: parsing clock script 1
[  293.267799] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  293.291111] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  293.291125] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  293.291459] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  297.086745] wlan0: authenticate with 00:04:0e:d6:58:ad (try 1)
[  297.089140] wlan0: authenticated
[  297.092642] wlan0: associate with 00:04:0e:d6:58:ad (try 1)
[  297.099225] wlan0: RX AssocResp from 00:04:0e:d6:58:ad (capab=0x451 status=0 aid=2)
[  297.099232] wlan0: associated
[ 1647.817266] CE: hpet increased min_delta_ns to 7500 nsec

```

lsusb
```
Bus 002 Device 009: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 008: ID 046d:c30a Logitech, Inc. iTouch Composite
Bus 002 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 064e:2100 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lspci
```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
3f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
3f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
3f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
3f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
3f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
3f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
3f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
3f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
3f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
3f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
3f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
```

Cheers,
Reto

---

### Post by P4man on 2010-10-13
Do you have an external monitor connected to this machine (which is a laptop I assume) ?

---

### Post by P4man on 2010-10-13
BTW, I have no idea if this is related to your problem, but your log shows a problem with the EDID of your monitor. I suspect that is why the restricted driver gives you a black screen, and perhaps its part of the problem with nouveau. If you can boot windows. then try this:
[http://ubuntuforums.org/showthread.php?t=316985](http://ubuntuforums.org/showthread.php?t=316985)

If you dont have a xorg.conf, or you need help editing it, feel free to ask.

---

### Post by reto on 2010-10-13
Yes I have an external monitor connected. No, I don't have windows installed and the only reason to try the nvidia drivers was to prevent this freezes, but if this is cause by something else i'm happy with noveau.

---

### Post by P4man on 2010-10-13
I cant see anything particularly wrong in that log, aside from nouveau complaining about the invalid EDID. Im not sure if that is about the external monitor or the built-in one though. Did you run that dmesg with the external connected? Does the problem also occur if you disconnect it? 

And lastly, can you run dmesg again after you suffered from freezing issues (assuming you dont have to reboot, if you do have to reboot, attach the contents of the previous log which you can find in /var/log/dmesg.0

---

### Post by reto on 2010-10-13
I almost always have the external monitor connected, I'm not sure I had the situation without.

Here's the dmesg output when the machine doesn't react to mouse or keyborad actions (except moving the mouse pointer):
```
dmesg 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 (Ubuntu 2.6.35-22.34-generic 2.6.35.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=ce699be7-7964-4b80-9659-0d7dad70238c ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cee75000 (usable)
[    0.000000]  BIOS-e820: 00000000cee75000 - 00000000ceeb5000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ceeb5000 - 00000000ceec6000 (reserved)
[    0.000000]  BIOS-e820: 00000000ceec6000 - 00000000ceedc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ceedc000 - 00000000cef0d000 (reserved)
[    0.000000]  BIOS-e820: 00000000cef0d000 - 00000000cef0e000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cef0e000 - 00000000cef11000 (reserved)
[    0.000000]  BIOS-e820: 00000000cef11000 - 00000000cef13000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cef13000 - 00000000cef16000 (reserved)
[    0.000000]  BIOS-e820: 00000000cef16000 - 00000000cef19000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cef19000 - 00000000cef1d000 (reserved)
[    0.000000]  BIOS-e820: 00000000cef1d000 - 00000000cef2c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cef2c000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001b0000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x1b0000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF0000000 write-back
[    0.000000]   3 base 100000000 mask F80000000 write-back
[    0.000000]   4 base 180000000 mask FC0000000 write-back
[    0.000000]   5 base 1B0000000 mask FF0000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcee75 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e800 (usable)
[    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cee75000 (usable)
[    0.000000]  modified: 00000000cee75000 - 00000000ceeb5000 (ACPI NVS)
[    0.000000]  modified: 00000000ceeb5000 - 00000000ceec6000 (reserved)
[    0.000000]  modified: 00000000ceec6000 - 00000000ceedc000 (ACPI NVS)
[    0.000000]  modified: 00000000ceedc000 - 00000000cef0d000 (reserved)
[    0.000000]  modified: 00000000cef0d000 - 00000000cef0e000 (ACPI NVS)
[    0.000000]  modified: 00000000cef0e000 - 00000000cef11000 (reserved)
[    0.000000]  modified: 00000000cef11000 - 00000000cef13000 (ACPI NVS)
[    0.000000]  modified: 00000000cef13000 - 00000000cef16000 (reserved)
[    0.000000]  modified: 00000000cef16000 - 00000000cef19000 (ACPI data)
[    0.000000]  modified: 00000000cef19000 - 00000000cef1d000 (reserved)
[    0.000000]  modified: 00000000cef1d000 - 00000000cef2c000 (ACPI NVS)
[    0.000000]  modified: 00000000cef2c000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 00000001b0000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000fc980] fc980
[    0.000000] init_memory_mapping: 0000000000000000-00000000cee75000
[    0.000000]  0000000000 - 00cee00000 page 2M
[    0.000000]  00cee00000 - 00cee75000 page 4k
[    0.000000] kernel direct mapping tables up to cee75000 @ 16000-1c000
[    0.000000] init_memory_mapping: 0000000100000000-00000001b0000000
[    0.000000]  0100000000 - 01b0000000 page 2M
[    0.000000] kernel direct mapping tables up to 1b0000000 @ 1a000-22000
[    0.000000] RAMDISK: 3700a000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02   Sony)
[    0.000000] ACPI: XSDT 00000000cef17e18 0005C (v01   Sony     VAIO 20091207 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000cef11d98 000F4 (v04   Sony     VAIO 20091207 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20100428/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xCEF28F40/0x00000000CEF2BD40, using 32 (20100428/tbfadt-486)
[    0.000000] ACPI: DSDT 00000000ceec6018 0A9B5 (v01   Sony     VAIO 20091207 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cef28f40 00040
[    0.000000] ACPI: APIC 00000000cef16f18 0008C (v02   Sony     VAIO 20091207 MSFT 00010013)
[    0.000000] ACPI: MCFG 00000000cef2ad18 0003C (v01   Sony     VAIO 20091207 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cef2ac98 00038 (v01   Sony     VAIO 20091207 MSFT 00000003)
[    0.000000] ACPI: SLIC 00000000cef23a18 00176 (v01   Sony     VAIO 20091207 Sony 01000000)
[    0.000000] ACPI: SSDT 00000000cef12018 009F1 (v01   Sony     VAIO 20091207 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cef11c18 0011D (v01   Sony     VAIO 20091207 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000001b0000000
[    0.000000] Initmem setup node 0 0000000000000000-00000001b0000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea0005ffffff] PMD -> [ffff880100200000-ffff8801057fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x001b0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cee75
[    0.000000]     0: 0x00100000 -> 0x001b0000
[    0.000000] On node 0 totalpages: 1568259
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3926 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 829101 pages, LIFO batch:31
[    0.000000]   Normal zone: 9856 pages used for memmap
[    0.000000]   Normal zone: 711040 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1d000 - 1d7ff]
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cee75000 - 00000000ceeb5000
[    0.000000] PM: Registered nosave memory: 00000000ceeb5000 - 00000000ceec6000
[    0.000000] PM: Registered nosave memory: 00000000ceec6000 - 00000000ceedc000
[    0.000000] PM: Registered nosave memory: 00000000ceedc000 - 00000000cef0d000
[    0.000000] PM: Registered nosave memory: 00000000cef0d000 - 00000000cef0e000
[    0.000000] PM: Registered nosave memory: 00000000cef0e000 - 00000000cef11000
[    0.000000] PM: Registered nosave memory: 00000000cef11000 - 00000000cef13000
[    0.000000] PM: Registered nosave memory: 00000000cef13000 - 00000000cef16000
[    0.000000] PM: Registered nosave memory: 00000000cef16000 - 00000000cef19000
[    0.000000] PM: Registered nosave memory: 00000000cef19000 - 00000000cef1d000
[    0.000000] PM: Registered nosave memory: 00000000cef1d000 - 00000000cef2c000
[    0.000000] PM: Registered nosave memory: 00000000cef2c000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed1b000
[    0.000000] PM: Registered nosave memory: 00000000fed1b000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:28000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] early_res array is doubled to 128 at [1d800 - 1e7ff]
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1544067
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=ce699be7-7964-4b80-9659-0d7dad70238c ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (73 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [003700a000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d18218]             BRK
[    0.000000]   #4 [00000fc990 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000fc980 - 00000fc990]    MP-table mpf
[    0.000000]   #6 [000009e800 - 00000fc6e0]   BIOS reserved
[    0.000000]   #7 [00000fc914 - 00000fc980]   BIOS reserved
[    0.000000]   #8 [00000fc6e0 - 00000fc914]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 000001a000]         PGTABLE
[    0.000000]   #12 [000001a000 - 000001d000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d18240 - 0001d19240]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d175c0]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0105800000]        MEMMAP 0
[    0.000000]   #19 [0001d175c0 - 0001d17740]         BOOTMEM
[    0.000000]   #20 [0001d19240 - 0001d31240]         BOOTMEM
[    0.000000]   #21 [0001d31240 - 0001d49240]         BOOTMEM
[    0.000000]   #22 [0001d4a000 - 0001d4b000]         BOOTMEM
[    0.000000]   #23 [0001d17740 - 0001d17781]         BOOTMEM
[    0.000000]   #24 [0001d177c0 - 0001d17803]         BOOTMEM
[    0.000000]   #25 [0001d17840 - 0001d17d80]         BOOTMEM
[    0.000000]   #26 [0001d17d80 - 0001d17de8]         BOOTMEM
[    0.000000]   #27 [0001d17e00 - 0001d17e68]         BOOTMEM
[    0.000000]   #28 [0001d17e80 - 0001d17ee8]         BOOTMEM
[    0.000000]   #29 [0001d17f00 - 0001d17f68]         BOOTMEM
[    0.000000]   #30 [0001d17f80 - 0001d17fe8]         BOOTMEM
[    0.000000]   #31 [0001d49240 - 0001d492a8]         BOOTMEM
[    0.000000]   #32 [0001d492c0 - 0001d49328]         BOOTMEM
[    0.000000]   #33 [0001d49340 - 0001d493a8]         BOOTMEM
[    0.000000]   #34 [0001d493c0 - 0001d49428]         BOOTMEM
[    0.000000]   #35 [0001d49440 - 0001d494a8]         BOOTMEM
[    0.000000]   #36 [0001d494c0 - 0001d49528]         BOOTMEM
[    0.000000]   #37 [0001d49540 - 0001d495a8]         BOOTMEM
[    0.000000]   #38 [0001d495c0 - 0001d49628]         BOOTMEM
[    0.000000]   #39 [0001d49640 - 0001d496a8]         BOOTMEM
[    0.000000]   #40 [0001d496c0 - 0001d49728]         BOOTMEM
[    0.000000]   #41 [0001d49740 - 0001d497a8]         BOOTMEM
[    0.000000]   #42 [0001d497c0 - 0001d49828]         BOOTMEM
[    0.000000]   #43 [0001d49840 - 0001d498a8]         BOOTMEM
[    0.000000]   #44 [0001d498c0 - 0001d49928]         BOOTMEM
[    0.000000]   #45 [0001d49940 - 0001d499a8]         BOOTMEM
[    0.000000]   #46 [0001d499c0 - 0001d49a28]         BOOTMEM
[    0.000000]   #47 [0001d49a40 - 0001d49aa8]         BOOTMEM
[    0.000000]   #48 [0001d49ac0 - 0001d49b28]         BOOTMEM
[    0.000000]   #49 [0001d49b40 - 0001d49b60]         BOOTMEM
[    0.000000]   #50 [0001d49b80 - 0001d49ba0]         BOOTMEM
[    0.000000]   #51 [0001d49bc0 - 0001d49c2a]         BOOTMEM
[    0.000000]   #52 [0001d49c40 - 0001d49caa]         BOOTMEM
[    0.000000]   #53 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #54 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #55 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #56 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #57 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #58 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #59 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #60 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #61 [0001d49cc0 - 0001d49cc8]         BOOTMEM
[    0.000000]   #62 [0001d49d00 - 0001d49d08]         BOOTMEM
[    0.000000]   #63 [0001d49d40 - 0001d49d60]         BOOTMEM
[    0.000000]   #64 [0001d49d80 - 0001d49dc0]         BOOTMEM
[    0.000000]   #65 [0001d49dc0 - 0001d49ee0]         BOOTMEM
[    0.000000]   #66 [0001d49f00 - 0001d49f48]         BOOTMEM
[    0.000000]   #67 [0001d49f80 - 0001d49fc8]         BOOTMEM
[    0.000000]   #68 [0001d4b000 - 0001d53000]         BOOTMEM
[    0.000000]   #69 [0001fde000 - 0005fde000]         BOOTMEM
[    0.000000]   #70 [0001d53000 - 0001d73000]         BOOTMEM
[    0.000000]   #71 [0001d73000 - 0001db3000]         BOOTMEM
[    0.000000]   #72 [000001e800 - 0000026800]         BOOTMEM
[    0.000000] Memory: 6088052k/7077888k available (5708k kernel code, 804852k absent, 184984k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:744
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 62914560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 1595.801 MHz processor.
[    0.000011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.60 BogoMIPS (lpj=15958010)
[    0.000018] pid_max: default: 32768 minimum: 301
[    0.000034] Security Framework initialized
[    0.000047] AppArmor: AppArmor initialized
[    0.000048] Yama: becoming mindful.
[    0.000663] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002845] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003776] Mount-cache hash table entries: 256
[    0.003864] Initializing cgroup subsys ns
[    0.003867] Initializing cgroup subsys cpuacct
[    0.003870] Initializing cgroup subsys memory
[    0.003876] Initializing cgroup subsys devices
[    0.003877] Initializing cgroup subsys freezer
[    0.003879] Initializing cgroup subsys net_cls
[    0.003896] CPU: Physical Processor ID: 0
[    0.003897] CPU: Processor Core ID: 0
[    0.003901] mce: CPU supports 9 MCE banks
[    0.003908] CPU0: Thermal monitoring handled by SMI
[    0.003914] using mwait in idle threads.
[    0.003915] Performance Events: PEBS fmt1+, Nehalem events, Intel PMU driver.
[    0.003920] ... version:                3
[    0.003921] ... bit width:              48
[    0.003922] ... generic registers:      4
[    0.003923] ... value mask:             0000ffffffffffff
[    0.003925] ... max period:             000000007fffffff
[    0.003926] ... fixed-purpose events:   3
[    0.003927] ... event mask:             000000070000000f
[    0.005583] ACPI: Core revision 20100428
[    0.026428] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.026433] ftrace: allocating 22680 entries in 89 pages
[    0.032632] Setting APIC routing to flat
[    0.032947] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.132847] CPU0: Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz stepping 05
[    0.248198] Booting Node   0, Processors  #1
[    0.407979] CPU1: Thermal monitoring handled by SMI
[    0.428056]  #2
[    0.587815] CPU2: Thermal monitoring handled by SMI
[    0.607964]  #3
[    0.767643] CPU3: Thermal monitoring handled by SMI
[    0.787759]  #4
[    0.947474] CPU4: Thermal monitoring handled by SMI
[    0.967602]  #5
[    1.127300] CPU5: Thermal monitoring handled by SMI
[    1.147403]  #6
[    1.307128] CPU6: Thermal monitoring handled by SMI
[    1.327302]  #7 Ok.
[    1.486957] CPU7: Thermal monitoring handled by SMI
[    1.507038] Brought up 8 CPUs
[    1.507041] Total of 8 processors activated (25535.56 BogoMIPS).
[    1.511095] devtmpfs: initialized
[    1.512310] regulator: core version 0.5
[    1.512341] Time:  7:27:28  Date: 10/13/10
[    1.512375] NET: Registered protocol family 16
[    1.512469] Trying to unpack rootfs image as initramfs...
[    1.512490] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    1.512493] ACPI: bus type pci registered
[    1.512571] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    1.512575] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    1.526887] PCI: Using configuration type 1 for base access
[    1.527804] bio: create slab <bio-0> at 0
[    1.530355] ACPI: EC: Look up EC in DSDT
[    1.532599] ACPI: Executed 1 blocks of module-level executable AML code
[    1.538288] ACPI: BIOS _OSI(Linux) query ignored
[    1.544510] ACPI: SSDT 00000000cef15a98 002DA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.545151] ACPI: Dynamic OEM Table Load:
[    1.545155] ACPI: SSDT (null) 002DA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.545447] ACPI: SSDT 00000000cef14618 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.546066] ACPI: Dynamic OEM Table Load:
[    1.546069] ACPI: SSDT (null) 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.546689] ACPI: SSDT 00000000cef15718 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.547414] ACPI: Dynamic OEM Table Load:
[    1.547417] ACPI: SSDT (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.547634] ACPI: SSDT 00000000cef13d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.548320] ACPI: Dynamic OEM Table Load:
[    1.548324] ACPI: SSDT (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.948918] Freeing initrd memory: 16280k freed
[    2.346572] ACPI: Interpreter enabled
[    2.346578] ACPI: (supports S0 S3 S4 S5)
[    2.346610] ACPI: Using IOAPIC for interrupt routing
[    2.377924] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    2.378291] ACPI: No dock devices found.
[    2.378295] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    2.379191] \_SB_.PCI0:_OSC invalid UUID
[    2.379193] _OSC request data:1 8 1f 
[    2.379198] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    2.380395] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    2.380399] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    2.380402] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    2.380405] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    2.380408] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    2.380411] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    2.380414] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    2.380417] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    2.380420] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    2.380423] pci_root PNP0A08:00: host bridge window [mem 0xd0000000-0xfeafffff]
[    2.380530] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    2.380534] pci 0000:00:03.0: PME# disabled
[    2.380868] pci 0000:00:1a.0: reg 10: [mem 0xe8e08000-0xe8e083ff]
[    2.380935] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    2.380944] pci 0000:00:1a.0: PME# disabled
[    2.380997] pci 0000:00:1b.0: reg 10: [mem 0xe8e00000-0xe8e03fff 64bit]
[    2.381050] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    2.381059] pci 0000:00:1b.0: PME# disabled
[    2.381143] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    2.381152] pci 0000:00:1c.0: PME# disabled
[    2.381239] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    2.381248] pci 0000:00:1c.1: PME# disabled
[    2.381331] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    2.381340] pci 0000:00:1c.2: PME# disabled
[    2.381424] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    2.381433] pci 0000:00:1c.5: PME# disabled
[    2.381492] pci 0000:00:1d.0: reg 10: [mem 0xe8e07000-0xe8e073ff]
[    2.381558] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    2.381567] pci 0000:00:1d.0: PME# disabled
[    2.381793] pci 0000:00:1f.2: reg 10: [io  0xe070-0xe077]
[    2.381804] pci 0000:00:1f.2: reg 14: [io  0xe060-0xe063]
[    2.381814] pci 0000:00:1f.2: reg 18: [io  0xe050-0xe057]
[    2.381825] pci 0000:00:1f.2: reg 1c: [io  0xe040-0xe043]
[    2.381836] pci 0000:00:1f.2: reg 20: [io  0xe020-0xe03f]
[    2.381847] pci 0000:00:1f.2: reg 24: [mem 0xe8e06000-0xe8e067ff]
[    2.381889] pci 0000:00:1f.2: PME# supported from D3hot
[    2.381898] pci 0000:00:1f.2: PME# disabled
[    2.381944] pci 0000:00:1f.3: reg 10: [mem 0xe8e05000-0xe8e050ff 64bit]
[    2.381963] pci 0000:00:1f.3: reg 20: [io  0xe000-0xe01f]
[    2.382044] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff]
[    2.382055] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.382065] pci 0000:01:00.0: reg 1c: [mem 0xe0000000-0xe1ffffff 64bit pref]
[    2.382072] pci 0000:01:00.0: reg 24: [io  0xd000-0xd07f]
[    2.382078] pci 0000:01:00.0: reg 30: [mem 0xe3000000-0xe307ffff pref]
[    2.382132] pci 0000:01:00.1: reg 10: [mem 0xe3080000-0xe3083fff]
[    2.382187] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    2.382191] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    2.382195] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xe30fffff]
[    2.382201] pci 0000:00:03.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.382804] pci 0000:02:00.0: reg 10: [mem 0xe7a00000-0xe7a01fff 64bit]
[    2.383730] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    2.383786] pci 0000:02:00.0: PME# disabled
[    2.383993] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    2.384001] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    2.384010] pci 0000:00:1c.0:   bridge window [mem 0xe7a00000-0xe8dfffff]
[    2.384021] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.384142] pci 0000:03:00.0: reg 10: [mem 0xe6603000-0xe66030ff]
[    2.384233] pci 0000:03:00.0: supports D1 D2
[    2.384235] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.384241] pci 0000:03:00.0: PME# disabled
[    2.384302] pci 0000:03:00.1: reg 10: [mem 0xe6602000-0xe66020ff]
[    2.384392] pci 0000:03:00.1: supports D1 D2
[    2.384394] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    2.384403] pci 0000:03:00.1: PME# disabled
[    2.384464] pci 0000:03:00.3: reg 10: [mem 0xe6601000-0xe66017ff]
[    2.384554] pci 0000:03:00.3: supports D1 D2
[    2.384556] pci 0000:03:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    2.384565] pci 0000:03:00.3: PME# disabled
[    2.384625] pci 0000:03:00.4: reg 10: [mem 0xe6600000-0xe66000ff]
[    2.384714] pci 0000:03:00.4: supports D1 D2
[    2.384716] pci 0000:03:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    2.384726] pci 0000:03:00.4: PME# disabled
[    2.384760] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    2.384769] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    2.384778] pci 0000:00:1c.1:   bridge window [mem 0xe6600000-0xe79fffff]
[    2.384789] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.385259] pci 0000:04:00.0: reg 10: [mem 0xe5220000-0xe5223fff 64bit]
[    2.385356] pci 0000:04:00.0: reg 18: [io  0xa000-0xa0ff]
[    2.385680] pci 0000:04:00.0: reg 30: [mem 0xe5200000-0xe521ffff pref]
[    2.386187] pci 0000:04:00.0: supports D1 D2
[    2.386189] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.386239] pci 0000:04:00.0: PME# disabled
[    2.386490] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    2.386499] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    2.386508] pci 0000:00:1c.2:   bridge window [mem 0xe5200000-0xe65fffff]
[    2.386519] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.386572] pci 0000:00:1c.5: PCI bridge to [bus 05-0c]
[    2.386581] pci 0000:00:1c.5:   bridge window [io  0x9000-0x9fff]
[    2.386589] pci 0000:00:1c.5:   bridge window [mem 0xe3200000-0xe51fffff]
[    2.386601] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.386679] pci 0000:00:1e.0: PCI bridge to [bus 0d-0d] (subtractive decode)
[    2.386688] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    2.386697] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.386708] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.386711] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    2.386714] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    2.386717] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    2.386720] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    2.386723] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    2.386726] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    2.386728] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    2.386731] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    2.386734] pci 0000:00:1e.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    2.386737] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    2.386778] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.387116] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    2.387300] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    2.387504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    2.387736] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    2.387921] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG3._PRT]
[    2.388397] \_SB_.PCI0:_OSC invalid UUID
[    2.388399] _OSC request data:1 19 1f 
[    2.404189] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 3f])
[    2.405323] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    2.405486] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    2.405650] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    2.405810] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    2.405970] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    2.406131] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    2.406292] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    2.406453] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    2.406525] HEST: Table is not found!
[    2.406605] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    2.406618] vgaarb: loaded
[    2.406757] SCSI subsystem initialized
[    2.406911] libata version 3.00 loaded.
[    2.406966] usbcore: registered new interface driver usbfs
[    2.406977] usbcore: registered new interface driver hub
[    2.406999] usbcore: registered new device driver usb
[    2.407125] ACPI: WMI: Mapper loaded
[    2.407127] PCI: Using ACPI for IRQ routing
[    2.407130] PCI: pci_cache_line_size set to 64 bytes
[    2.407546] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    2.407549] reserve RAM buffer: 00000000cee75000 - 00000000cfffffff 
[    2.407641] NetLabel: Initializing
[    2.407643] NetLabel:  domain hash size = 128
[    2.407644] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.407659] NetLabel:  unlabeled traffic allowed by default
[    2.407692]   alloc irq_desc for 40 on node 0
[    2.407694]   alloc kstat_irqs on node 0
[    2.407705]   alloc irq_desc for 41 on node 0
[    2.407707]   alloc kstat_irqs on node 0
[    2.407715]   alloc irq_desc for 42 on node 0
[    2.407717]   alloc kstat_irqs on node 0
[    2.407726]   alloc irq_desc for 43 on node 0
[    2.407727]   alloc kstat_irqs on node 0
[    2.407735]   alloc irq_desc for 44 on node 0
[    2.407737]   alloc kstat_irqs on node 0
[    2.407741] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    2.407750] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    2.407758] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    2.416305] hpet: hpet2 irq 40 for MSI
[    2.436357] hpet: hpet3 irq 41 for MSI
[    2.446409] hpet: hpet4 irq 42 for MSI
[    2.456363] hpet: hpet5 irq 43 for MSI
[    2.466384] hpet: hpet6 irq 44 for MSI
[    2.486394] Switching to clocksource tsc
[    2.495114] AppArmor: AppArmor Filesystem Enabled
[    2.495126] pnp: PnP ACPI init
[    2.495138] ACPI: bus type pnp registered
[    2.499060] pnp: PnP ACPI: found 11 devices
[    2.499062] ACPI: ACPI bus type pnp unregistered
[    2.499076] system 00:05: [io  0x0680-0x069f] has been reserved
[    2.499079] system 00:05: [io  0xff00-0xff0f] has been reserved
[    2.499082] system 00:05: [io  0xff10-0xff13] has been reserved
[    2.499085] system 00:05: [io  0x0800-0x0803] has been reserved
[    2.499088] system 00:05: [io  0x0400-0x047f] has been reserved
[    2.499091] system 00:05: [io  0x0500-0x057f] has been reserved
[    2.499094] system 00:05: [io  0x164e-0x164f] has been reserved
[    2.499101] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    2.499105] system 00:09: [mem 0xfed1b000-0xfed1bfff] has been reserved
[    2.499108] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    2.499111] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    2.499114] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    2.499117] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    2.499121] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    2.499124] system 00:09: [mem 0xe8e0b000-0xe8e0bfff] has been reserved
[    2.505155] pci 0000:00:1c.0: BAR 15: assigned [mem 0xe8f00000-0xe90fffff 64bit pref]
[    2.505160] pci 0000:00:1c.1: BAR 15: assigned [mem 0xe9100000-0xe92fffff 64bit pref]
[    2.505164] pci 0000:00:1c.2: BAR 15: assigned [mem 0xe9300000-0xe94fffff 64bit pref]
[    2.505168] pci 0000:00:1c.5: BAR 15: assigned [mem 0xe9500000-0xe96fffff 64bit pref]
[    2.505172] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    2.505175] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    2.505180] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xe30fffff]
[    2.505184] pci 0000:00:03.0:   bridge window [mem pref disabled]
[    2.505189] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    2.505192] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    2.505202] pci 0000:00:1c.0:   bridge window [mem 0xe7a00000-0xe8dfffff]
[    2.505211] pci 0000:00:1c.0:   bridge window [mem 0xe8f00000-0xe90fffff 64bit pref]
[    2.505223] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    2.505231] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    2.505240] pci 0000:00:1c.1:   bridge window [mem 0xe6600000-0xe79fffff]
[    2.505250] pci 0000:00:1c.1:   bridge window [mem 0xe9100000-0xe92fffff 64bit pref]
[    2.505261] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    2.505268] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    2.505278] pci 0000:00:1c.2:   bridge window [mem 0xe5200000-0xe65fffff]
[    2.505287] pci 0000:00:1c.2:   bridge window [mem 0xe9300000-0xe94fffff 64bit pref]
[    2.505299] pci 0000:00:1c.5: PCI bridge to [bus 05-0c]
[    2.505306] pci 0000:00:1c.5:   bridge window [io  0x9000-0x9fff]
[    2.505316] pci 0000:00:1c.5:   bridge window [mem 0xe3200000-0xe51fffff]
[    2.505325] pci 0000:00:1c.5:   bridge window [mem 0xe9500000-0xe96fffff 64bit pref]
[    2.505336] pci 0000:00:1e.0: PCI bridge to [bus 0d-0d]
[    2.505338] pci 0000:00:1e.0:   bridge window [io  disabled]
[    2.505347] pci 0000:00:1e.0:   bridge window [mem disabled]
[    2.505356] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    2.505374]   alloc irq_desc for 16 on node -1
[    2.505376]   alloc kstat_irqs on node -1
[    2.505382] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.505386] pci 0000:00:03.0: setting latency timer to 64
[    2.505399] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.505408] pci 0000:00:1c.0: setting latency timer to 64
[    2.505428]   alloc irq_desc for 17 on node -1
[    2.505430]   alloc kstat_irqs on node -1
[    2.505434] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.505439] pci 0000:00:1c.1: setting latency timer to 64
[    2.505451]   alloc irq_desc for 18 on node -1
[    2.505453]   alloc kstat_irqs on node -1
[    2.505457] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.505462] pci 0000:00:1c.2: setting latency timer to 64
[    2.505479] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.505488] pci 0000:00:1c.5: setting latency timer to 64
[    2.505499] pci 0000:00:1e.0: setting latency timer to 64
[    2.505508] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.505511] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.505513] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.505516] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    2.505518] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    2.505521] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    2.505523] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    2.505526] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    2.505528] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    2.505531] pci_bus 0000:00: resource 13 [mem 0xd0000000-0xfeafffff]
[    2.505534] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    2.505536] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xe30fffff]
[    2.505539] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    2.505541] pci_bus 0000:02: resource 1 [mem 0xe7a00000-0xe8dfffff]
[    2.505544] pci_bus 0000:02: resource 2 [mem 0xe8f00000-0xe90fffff 64bit pref]
[    2.505547] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    2.505549] pci_bus 0000:03: resource 1 [mem 0xe6600000-0xe79fffff]
[    2.505551] pci_bus 0000:03: resource 2 [mem 0xe9100000-0xe92fffff 64bit pref]
[    2.505554] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
[    2.505557] pci_bus 0000:04: resource 1 [mem 0xe5200000-0xe65fffff]
[    2.505559] pci_bus 0000:04: resource 2 [mem 0xe9300000-0xe94fffff 64bit pref]
[    2.505562] pci_bus 0000:05: resource 0 [io  0x9000-0x9fff]
[    2.505564] pci_bus 0000:05: resource 1 [mem 0xe3200000-0xe51fffff]
[    2.505567] pci_bus 0000:05: resource 2 [mem 0xe9500000-0xe96fffff 64bit pref]
[    2.505570] pci_bus 0000:0d: resource 4 [io  0x0000-0x0cf7]
[    2.505572] pci_bus 0000:0d: resource 5 [io  0x0d00-0xffff]
[    2.505574] pci_bus 0000:0d: resource 6 [mem 0x000a0000-0x000bffff]
[    2.505577] pci_bus 0000:0d: resource 7 [mem 0x000d0000-0x000d3fff]
[    2.505579] pci_bus 0000:0d: resource 8 [mem 0x000d4000-0x000d7fff]
[    2.505582] pci_bus 0000:0d: resource 9 [mem 0x000d8000-0x000dbfff]
[    2.505584] pci_bus 0000:0d: resource 10 [mem 0x000dc000-0x000dffff]
[    2.505587] pci_bus 0000:0d: resource 11 [mem 0x000e0000-0x000e3fff]
[    2.505589] pci_bus 0000:0d: resource 12 [mem 0x000e4000-0x000e7fff]
[    2.505592] pci_bus 0000:0d: resource 13 [mem 0xd0000000-0xfeafffff]
[    2.505623] NET: Registered protocol family 2
[    2.505914] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    2.507246] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.510816] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.511245] TCP: Hash tables configured (established 524288 bind 65536)
[    2.511247] TCP reno registered
[    2.511267] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    2.511362] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    2.511526] NET: Registered protocol family 1
[    2.628234] pci 0000:01:00.0: Boot video device
[    2.628390] PCI: CLS 64 bytes, default 64
[    2.628392] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.628395] Placing 64MB software IO TLB between ffff880001fde000 - ffff880005fde000
[    2.628397] software IO TLB at phys 0x1fde000 - 0x5fde000
[    2.628921] Scanning for low memory corruption every 60 seconds
[    2.629036] audit: initializing netlink socket (disabled)
[    2.629045] type=2000 audit(1286954849.450:1): initialized
[    2.647266] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.649082] VFS: Disk quotas dquot_6.5.2
[    2.649150] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.649791] fuse init (API version 7.14)
[    2.649883] msgmni has been set to 11922
[    2.652393] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.652396] io scheduler noop registered
[    2.652398] io scheduler deadline registered
[    2.652441] io scheduler cfq registered (default)
[    2.652569] pcieport 0000:00:03.0: setting latency timer to 64
[    2.652598]   alloc irq_desc for 45 on node -1
[    2.652600]   alloc kstat_irqs on node -1
[    2.652609] pcieport 0000:00:03.0: irq 45 for MSI/MSI-X
[    2.652682] pcieport 0000:00:1c.0: setting latency timer to 64
[    2.652718]   alloc irq_desc for 46 on node -1
[    2.652720]   alloc kstat_irqs on node -1
[    2.652732] pcieport 0000:00:1c.0: irq 46 for MSI/MSI-X
[    2.652819] pcieport 0000:00:1c.1: setting latency timer to 64
[    2.652856]   alloc irq_desc for 47 on node -1
[    2.652858]   alloc kstat_irqs on node -1
[    2.652869] pcieport 0000:00:1c.1: irq 47 for MSI/MSI-X
[    2.652948] pcieport 0000:00:1c.2: setting latency timer to 64
[    2.652984]   alloc irq_desc for 48 on node -1
[    2.652986]   alloc kstat_irqs on node -1
[    2.652998] pcieport 0000:00:1c.2: irq 48 for MSI/MSI-X
[    2.653083] pcieport 0000:00:1c.5: setting latency timer to 64
[    2.653119]   alloc irq_desc for 49 on node -1
[    2.653121]   alloc kstat_irqs on node -1
[    2.653133] pcieport 0000:00:1c.5: irq 49 for MSI/MSI-X
[    2.653357] \_SB_.PCI0:_OSC invalid UUID
[    2.653360] _OSC request data:1 0 1f 
[    2.653364] aer 0000:00:03.0:pcie02: AER service couldn't init device: _OSC failed
[    2.653388] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.653508] \_SB_.PCI0:_OSC invalid UUID
[    2.653510] _OSC request data:1 0 1f 
[    2.653640] \_SB_.PCI0:_OSC invalid UUID
[    2.653642] _OSC request data:1 0 1f 
[    2.653770] \_SB_.PCI0:_OSC invalid UUID
[    2.653772] _OSC request data:1 0 1f 
[    2.653898] \_SB_.PCI0:_OSC invalid UUID
[    2.653900] _OSC request data:1 0 1f 
[    2.654043] \_SB_.PCI0:_OSC invalid UUID
[    2.654045] _OSC request data:1 0 1f 
[    2.654172] \_SB_.PCI0:_OSC invalid UUID
[    2.654174] _OSC request data:1 0 1f 
[    2.654300] \_SB_.PCI0:_OSC invalid UUID
[    2.654302] _OSC request data:1 0 1f 
[    2.654429] \_SB_.PCI0:_OSC invalid UUID
[    2.654431] _OSC request data:1 0 1f 
[    2.654455] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.654532] intel_idle: MWAIT substates: 0x1120
[    2.654534] intel_idle: v0.4 model 0x1E
[    2.654536] intel_idle: lapic_timer_reliable_states 0x2
[    2.655527] ACPI: AC Adapter [ADP1] (on-line)
[    2.655613] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    2.657483] ACPI: Lid Switch [LID0]
[    2.657527] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    2.657539] ACPI: Power Button [PWRB]
[    2.658544] ACPI: acpi_idle yielding to intel_idle
[    2.673698] thermal LNXTHERM:01: registered as thermal_zone0
[    2.673707] ACPI: Thermal Zone [TZ00] (66 C)
[    2.675682] thermal LNXTHERM:02: registered as thermal_zone1
[    2.675689] ACPI: Thermal Zone [TZ01] (66 C)
[    2.675776] ERST: Table is not found!
[    2.676062] Linux agpgart interface v0.103
[    2.676086] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.677433] brd: module loaded
[    2.677929] loop: module loaded
[    2.678387] Fixed MDIO Bus: probed
[    2.678417] PPP generic driver version 2.4.2
[    2.678451] tun: Universal TUN/TAP device driver, 1.6
[    2.678453] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.678527] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.678559] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.678582] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.678591] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.678629] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.678666] ehci_hcd 0000:00:1a.0: debug port 2
[    2.682580] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.682600] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xe8e08000
[    2.708144] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.708264] hub 1-0:1.0: USB hub found
[    2.708269] hub 1-0:1.0: 2 ports detected
[    2.708348]   alloc irq_desc for 23 on node -1
[    2.708351]   alloc kstat_irqs on node -1
[    2.708357] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.708379] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.708387] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.708423] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.708452] ehci_hcd 0000:00:1d.0: debug port 2
[    2.712364] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.712382] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xe8e07000
[    2.723152] ACPI: Battery Slot [BAT0] (battery present)
[    2.738049] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.738172] hub 2-0:1.0: USB hub found
[    2.738176] hub 2-0:1.0: 2 ports detected
[    2.738251] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.738265] uhci_hcd: USB Universal Host Controller Interface driver
[    2.738366] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.743581] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.747401] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.747407] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.747410] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.747413] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.747416] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.747471] mice: PS/2 mouse device common for all mice
[    2.747573] rtc_cmos 00:06: RTC can wake from S4
[    2.747608] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.747647] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.747752] device-mapper: uevent: version 1.0.3
[    2.747830] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    2.747971] device-mapper: multipath: version 1.1.1 loaded
[    2.747974] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.748494] cpuidle: using governor ladder
[    2.748834] cpuidle: using governor menu
[    2.749121] TCP cubic registered
[    2.749254] NET: Registered protocol family 10
[    2.749628] lo: Disabled Privacy Extensions
[    2.749848] NET: Registered protocol family 17
[    2.755692] PM: Resume from disk failed.
[    2.755700] registered taskstats version 1
[    2.756397]   Magic number: 14:666:470
[    2.756501] rtc_cmos 00:06: setting system clock to 2010-10-13 07:27:29 UTC (1286954849)
[    2.756505] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.756506] EDD information not available.
[    2.756579] Freeing unused kernel memory: 908k freed
[    2.756702] Write protecting the kernel read-only data: 10240k
[    2.757095] Freeing unused kernel memory: 416k freed
[    2.757426] Freeing unused kernel memory: 1644k freed
[    2.768580] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.775532] udev[148]: starting version 163
[    2.809827] [Firmware Bug]: ACPI(NGFX) defines _DOD but not _DOS
[    2.863217] [drm] Initialized drm 1.1.0 20060810
[    2.974903] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.974911] nouveau 0000:01:00.0: setting latency timer to 64
[    2.975238] sdhci: Secure Digital Host Controller Interface driver
[    2.975241] sdhci: Copyright(c) Pierre Ossman
[    2.976967] sky2: driver version 1.28
[    2.977091] sky2 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.977205] sky2 0000:04:00.0: setting latency timer to 64
[    2.977439] sky2 0000:04:00.0: Yukon-2 UL 2 chip revision 0
[    2.977755] sdhci-pci 0000:03:00.0: SDHCI controller found [1180:e822] (rev 0)
[    2.978131] sdhci-pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.978338] sdhci-pci 0000:03:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.978460] sdhci-pci 0000:03:00.0: setting latency timer to 64
[    2.978693] Registered led device: mmc0::
[    2.978936] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
[    2.978960]   alloc irq_desc for 50 on node -1
[    2.978962]   alloc kstat_irqs on node -1
[    2.979114] sdhci-pci 0000:03:00.4: SDHCI controller found [1180:e822] (rev 0)
[    2.979262] sky2 0000:04:00.0: irq 50 for MSI/MSI-X
[    2.979483]   alloc irq_desc for 19 on node -1
[    2.979485]   alloc kstat_irqs on node -1
[    2.979491] sdhci-pci 0000:03:00.4: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.979661] sdhci-pci 0000:03:00.4: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.979782] sdhci-pci 0000:03:00.4: setting latency timer to 64
[    2.980004] Registered led device: mmc1::
[    2.980065] mmc1: SDHCI controller on PCI [0000:03:00.4] using DMA
[    2.980275] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x0a5480a2)
[    2.980747] sky2 0000:04:00.0: eth0: addr 00:24:be:c3:61:41
[    2.981119] firewire_ohci 0000:03:00.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.981130] firewire_ohci 0000:03:00.3: setting latency timer to 64
[    2.985973] ahci 0000:00:1f.2: version 3.0
[    2.985998] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.986143]   alloc irq_desc for 51 on node -1
[    2.986145]   alloc kstat_irqs on node -1
[    2.986159] ahci 0000:00:1f.2: irq 51 for MSI/MSI-X
[    2.986195] ahci: SSS flag set, parallel bus scan disabled
[    2.986229] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x23 impl SATA mode
[    2.986233] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part sxs apst 
[    2.986242] ahci 0000:00:1f.2: setting latency timer to 64
[    2.986408] scsi0 : ahci
[    2.986549] scsi1 : ahci
[    2.986696] scsi2 : ahci
[    2.986810] scsi3 : ahci
[    2.986927] scsi4 : ahci
[    2.987015] scsi5 : ahci
[    2.987295] ata1: SATA max UDMA/133 abar m2048@0xe8e06000 port 0xe8e06100 irq 51
[    2.987303] ata2: SATA max UDMA/133 abar m2048@0xe8e06000 port 0xe8e06180 irq 51
[    2.987306] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[    2.987309] ata3: DUMMY
[    2.987311] ata4: DUMMY
[    2.987312] ata5: DUMMY
[    2.987319] ata6: SATA max UDMA/133 abar m2048@0xe8e06000 port 0xe8e06380 irq 51
[    3.077131] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.078320] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    3.078324] [drm] nouveau 0000:01:00.0: BIT BIOS found
[    3.078326] [drm] nouveau 0000:01:00.0: Bios version 70.16.45.00
[    3.078328] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
[    3.078330] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
[    3.078332] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[    3.078335] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 010003f3 00010036
[    3.078337] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02011300 00000000
[    3.078339] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02422362 00020010
[    3.078341] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 0000000e 00000000
[    3.078343] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[    3.078346] [drm] nouveau 0000:01:00.0:   0: 0x00000040: type 0x40 idx 0 tag 0xff
[    3.078348] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[    3.078350] [drm] nouveau 0000:01:00.0:   2: 0x00001261: type 0x61 idx 2 tag 0x07
[    3.078360] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x6AEF
[    3.144724] acpi device:57: registered as cooling_device8
[    3.144812] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:56/LNXVIDEO:02/input/input3
[    3.144842] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[    3.150165] firewire_ohci: Added fw-ohci device 0000:03:00.3, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x0
[    3.157682] [drm] nouveau 0000:01:00.0: 0x6D99: Condition still not met after 20ms, skipping following opcodes
[    3.187648] [drm] nouveau 0000:01:00.0: 0x6D9D: Condition still not met after 20ms, skipping following opcodes
[    3.217631] [drm] nouveau 0000:01:00.0: 0x6F23: Condition still not met after 20ms, skipping following opcodes
[    3.217645] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x6F50
[    3.230740] hub 1-1:1.0: USB hub found
[    3.230969] hub 1-1:1.0: 6 ports detected
[    3.297543] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x7E24
[    3.297560] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x7E46
[    3.340499] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.359038] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0x7FA8
[    3.359043] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    3.359046] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0x800D
[    3.359235] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    3.359544] ata1.00: ATA-8: SAMSUNG HM500JI, 2AC101C4, max UDMA/133
[    3.359552] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.369533] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    3.369743] ata1.00: configured for UDMA/133
[    3.385579] [drm] nouveau 0000:01:00.0: 0x6955: Condition still not met after 20ms, skipping following opcodes
[    3.385593] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    3.385597] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    3.385602] [drm] nouveau 0000:01:00.0: 0x57D7: parsing output script 0
[    3.385615] [drm] nouveau 0000:01:00.0: BIOS FP mode: 1920x1080 (144000kHz pixel clock)
[    3.385623] [drm] nouveau 0000:01:00.0: Detected 1024MiB VRAM
[    3.385754] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM500JI  2AC1 PQ: 0 ANSI: 5
[    3.385890] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.385983] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.386068] sd 0:0:0:0: [sda] Write Protect is off
[    3.386073] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.386107] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.386301]  sda: sda1 sda2 < sda5 >
[    3.446954] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.506273] hub 2-1:1.0: USB hub found
[    3.506485] hub 2-1:1.0: 8 ports detected
[    3.572000] [TTM] Zone  kernel: Available graphics memory: 3053650 kiB.
[    3.572007] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    3.572011] [TTM] Initializing pool allocator.
[    3.589168] usb 1-1.2: new high speed USB device using ehci_hcd and address 3
[    3.629027] firewire_core: created device fw0: GUID 0800460303336522, S400
[    3.649048] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[    3.652315] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[    3.667514] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[    3.669550] [drm] nouveau 0000:01:00.0: Detected a LVDS output
[    3.669557] [drm] nouveau 0000:01:00.0: Detected a DAC output
[    3.669559] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[    3.669562] [drm] nouveau 0000:01:00.0: Detected a LVDS connector
[    3.669608] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[    3.669632] [drm] nouveau 0000:01:00.0: Detected a HDMI connector
[    3.738260] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.740108] ata2.00: ATAPI: Optiarc BD ROM BC-5500S4, 1.Va, max UDMA/100
[    3.742049] ata2.00: configured for UDMA/100
[    3.759371] scsi 1:0:0:0: CD-ROM            Optiarc  BD ROM BC-5500S4 1.Va PQ: 0 ANSI: 5
[    3.762189] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.762192] Uniform CD-ROM driver Revision: 3.20
[    3.762285] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.762333] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.779106] usb 1-1.6: new full speed USB device using ehci_hcd and address 4
[    3.976285] usb 2-1.2: new high speed USB device using ehci_hcd and address 3
[    4.086692] hub 2-1.2:1.0: USB hub found
[    4.086792] hub 2-1.2:1.0: 4 ports detected
[    4.108011] ata6: SATA link down (SStatus 0 SControl 300)
[    4.176103] usb 2-1.5: new full speed USB device using ehci_hcd and address 4
[    4.266019] usb 2-1.5: device descriptor read/64, error -32
[    4.465827] usb 2-1.5: device descriptor read/64, error -32
[    4.499403] [drm] nouveau 0000:01:00.0: allocated 1920x1080 fb: 0x40250000, bo ffff8801a4ff4000
[    4.502333] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    4.502340] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    4.502344] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    4.503660] Console: switching to colour frame buffer device 240x67
[    4.506206] fb0: nouveaufb frame buffer device
[    4.506208] drm: registered panic notifier
[    4.506210] Slow work thread pool: Starting up
[    4.506725] Slow work thread pool: Ready
[    4.506738] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[    4.648184] usb 2-1.5: new full speed USB device using ehci_hcd and address 5
[    4.735613] usb 2-1.5: device descriptor read/64, error -32
[    4.740499] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[    4.766429] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.914194] usb 2-1.5: device descriptor read/64, error -32
[    5.104013] usb 2-1.5: new full speed USB device using ehci_hcd and address 6
[    5.523317] usb 2-1.5: device not accepting address 6, error -32
[    5.603423] usb 2-1.5: new full speed USB device using ehci_hcd and address 7
[    6.022764] usb 2-1.5: device not accepting address 7, error -32
[    6.023057] hub 2-1:1.0: unable to enumerate USB device on port 5
[    6.102956] usb 2-1.2.1: new low speed USB device using ehci_hcd and address 8
[    6.302711] usb 2-1.2.2: new low speed USB device using ehci_hcd and address 9
[    6.522507] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 10
[   11.618240] usb 2-1.2.4: device descriptor read/64, error -71
[   13.833115] udev[578]: starting version 163
[   13.919979] Adding 17891324k swap on /dev/sda5.  Priority:-1 extents:1 across:17891324k 
[   13.938336] lp: driver loaded but no devices found
[   13.955437] cfg80211: Calling CRDA to update world regulatory domain
[   13.976221] type=1400 audit(1286954860.722:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=692 comm="apparmor_parser"
[   13.976972] type=1400 audit(1286954860.722:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=692 comm="apparmor_parser"
[   13.977389] type=1400 audit(1286954860.722:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=692 comm="apparmor_parser"
[   14.011029] cfg80211: World regulatory domain updated:
[   14.011033]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.011036]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.011040]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.011042]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.011045]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.011048]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.011672] EDAC MC: Ver: 2.1.0 Oct 10 2010
[   14.015330] EDAC i7core: Device not found: dev 00.0 PCI ID 8086:2c50
[   14.036127] Bluetooth: Core ver 2.15
[   14.036150] NET: Registered protocol family 31
[   14.036153] Bluetooth: HCI device and connection manager initialized
[   14.036156] Bluetooth: HCI socket layer initialized
[   14.098787] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   14.098999] usbcore: registered new interface driver btusb
[   14.124589] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.124591] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   14.124739] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.124769] iwlagn 0000:02:00.0: setting latency timer to 64
[   14.124914] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   14.139419] Linux video capture interface: v2.00
[   14.142944] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.143092]   alloc irq_desc for 52 on node -1
[   14.143095]   alloc kstat_irqs on node -1
[   14.143164] iwlagn 0000:02:00.0: irq 52 for MSI/MSI-X
[   14.156586] sony-laptop: Sony Notebook Control Driver v0.6.
[   14.182864] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SNY5001:00/input/input4
[   14.182943] input: Sony Vaio Jogdial as /devices/virtual/input/input5
[   14.182995] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[   14.197676]   alloc irq_desc for 22 on node -1
[   14.197679]   alloc kstat_irqs on node -1
[   14.197687] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.197759]   alloc irq_desc for 53 on node -1
[   14.197761]   alloc kstat_irqs on node -1
[   14.197771] HDA Intel 0000:00:1b.0: irq 53 for MSI/MSI-X
[   14.197804] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.202923] uvcvideo: Found UVC 1.00 device <unnamed> (064e:2100)
[   14.204526] input: UVC Camera (064e:2100) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input6
[   14.204581] usbcore: registered new interface driver uvcvideo
[   14.204583] USB Video Class driver (v0.1.0)
[   14.205770] iwlagn 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[   14.213091] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.301358] hda_codec: ALC275: BIOS auto-probing.
[   14.302675] hda_codec: ALC275: no valid ADC found; using fallback 0x8
[   14.306306] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.306312] hda_intel: Disable MSI for Nvidia chipset
[   14.306447] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.359891] usbcore: registered new interface driver hiddev
[   14.363996] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.2/2-1.2.2:1.0/input/input7
[   14.364089] generic-usb 0003:046D:C001.0003: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1d.0-1.2.2/input0
[   14.364106] usbcore: registered new interface driver usbhid
[   14.364108] usbhid: USB HID core driver
[   14.520335] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.0/input/input8
[   14.520414] logitech 0003:046D:C30A.0001: input,hidraw1: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1.2.1/input0
[   14.529868] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.1/input/input9
[   14.529983] logitech 0003:046D:C30A.0002: input,hidraw2: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1.2.1/input1
[   14.548320] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.798714] type=1400 audit(1286954861.542:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1299 comm="apparmor_parser"
[   14.798750] type=1400 audit(1286954861.542:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1304 comm="apparmor_parser"
[   14.798773] type=1400 audit(1286954861.542:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1300 comm="apparmor_parser"
[   14.799478] type=1400 audit(1286954861.542:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1300 comm="apparmor_parser"
[   14.799822] type=1400 audit(1286954861.542:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1300 comm="apparmor_parser"
[   14.800063] type=1400 audit(1286954861.542:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1303 comm="apparmor_parser"
[   14.800245] type=1400 audit(1286954861.542:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1301 comm="apparmor_parser"
[   14.922368] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio2/input/input10
[   15.138140] Bluetooth: L2CAP ver 2.14
[   15.138143] Bluetooth: L2CAP socket layer initialized
[   15.143315] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.143318] Bluetooth: BNEP filters: protocol multicast
[   15.147622] Bluetooth: SCO (Voice Link) ver 0.6
[   15.147625] Bluetooth: SCO socket layer initialized
[   15.188535] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.193173] sky2 0000:04:00.0: eth0: enabling interface
[   15.194057] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.213200] Bluetooth: RFCOMM TTY layer initialized
[   15.213208] Bluetooth: RFCOMM socket layer initialized
[   15.213211] Bluetooth: RFCOMM ver 1.11
[   15.327329] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
[   15.342318] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
[   15.638989] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   15.744549] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   16.243500] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.425550] ppdev: user-space parallel port driver
[   16.832547] usb 2-1.2.4: device descriptor read/64, error -71
[   17.022535] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 11
[   18.103304] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   18.497731] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   22.105696] usb 2-1.2.4: device descriptor read/64, error -71
[   27.310170] usb 2-1.2.4: device descriptor read/64, error -71
[   27.500005] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 12
[   32.914015] usb 2-1.2.4: device not accepting address 12, error -71
[   32.994074] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 13
[   38.408217] usb 2-1.2.4: device not accepting address 13, error -71
[   38.408381] hub 2-1.2:1.0: unable to enumerate USB device on port 4
[  133.967424] Intel AES-NI instructions are not detected.
[  134.072373] padlock: VIA PadLock not detected.
[  142.353226] wlan0: authenticate with 00:04:0e:d6:58:ad (try 1)
[  142.355634] wlan0: authenticated
[  142.359079] wlan0: associate with 00:04:0e:d6:58:ad (try 1)
[  142.366080] wlan0: RX AssocResp from 00:04:0e:d6:58:ad (capab=0x451 status=0 aid=2)
[  142.366087] wlan0: associated
[  142.372100] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  152.875042] wlan0: no IPv6 routers present
[  166.895668] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  166.928687] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  166.928700] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  166.929068] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  213.900371] [drm] nouveau 0000:01:00.0: plugged HDMI Type A-1
[  224.607440] [drm] nouveau 0000:01:00.0: unplugged HDMI Type A-1
[  224.765677] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[  224.765680] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  224.765682] <3>00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff  ................
[  224.765684] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765685] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765687] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765688] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765690] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765691] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765693] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  224.765694] 
[  224.769618] [drm] nouveau 0000:01:00.0: DDC responded, but no EDID for HDMI Type A-1
[  225.302346] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  226.072609] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  226.072624] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  226.310803] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  234.545404] [drm] nouveau 0000:01:00.0: plugged HDMI Type A-1
[  236.119430] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  236.140178] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  236.140186] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  236.140478] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  253.125113] [drm] nouveau 0000:01:00.0: unplugged HDMI Type A-1
[  253.652400] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  254.421839] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  254.421854] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  254.660027] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  275.802490] wlan0: deauthenticating from 00:04:0e:d6:58:ad by local choice (reason=3)
[  275.911973] cfg80211: All devices are disconnected, going to restore regulatory settings
[  275.911983] cfg80211: Restoring regulatory settings
[  275.911991] cfg80211: Calling CRDA to update world regulatory domain
[  275.917598] cfg80211: World regulatory domain updated:
[  275.917603]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  275.917610]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  275.917616]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  275.917621]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  275.917627]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  275.917632]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  276.660162] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 2
[  276.999284] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
[  277.014153] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
[  279.892590] [drm] nouveau 0000:01:00.0: plugged HDMI Type A-1
[  280.687280] [drm] nouveau 0000:01:00.0: 0x57D8: parsing output script 1
[  280.687295] [drm] nouveau 0000:01:00.0: 0x57D9: parsing output script 2
[  280.687308] [drm] nouveau 0000:01:00.0: 0x5616: parsing clock script 0
[  280.688086] [drm] nouveau 0000:01:00.0: 0x4E33: parsing clock script 1
[  293.267799] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  293.291111] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  293.291125] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  293.291459] [drm] nouveau 0000:01:00.0: Couldn't find matching output script table
[  297.086745] wlan0: authenticate with 00:04:0e:d6:58:ad (try 1)
[  297.089140] wlan0: authenticated
[  297.092642] wlan0: associate with 00:04:0e:d6:58:ad (try 1)
[  297.099225] wlan0: RX AssocResp from 00:04:0e:d6:58:ad (capab=0x451 status=0 aid=2)
[  297.099232] wlan0: associated
[ 1647.817266] CE: hpet increased min_delta_ns to 7500 nsec
[ 2168.209566] usb 2-1.5: new full speed USB device using ehci_hcd and address 14
[ 2168.289475] usb 2-1.5: device descriptor read/64, error -32
[ 2168.479375] usb 2-1.5: device descriptor read/64, error -32
[ 2168.672314] usb 2-1.5: new full speed USB device using ehci_hcd and address 15
[ 2168.748964] usb 2-1.5: device descriptor read/64, error -32
[ 2168.890539] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: can't reset device, 0000:00:1d.0-1.2.1/input0, status -71
[ 2168.894528] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: can't reset device, 0000:00:1d.0-1.2.2/input0, status -71
[ 2168.898495] usb 2-1.2: clear tt 1 (0080) error -71
[ 2168.902620] usb 2-1.2: clear tt 2 (0090) error -71
[ 2168.906640] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: can't reset device, 0000:00:1d.0-1.2.1/input0, status -71
[ 2168.910638] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: can't reset device, 0000:00:1d.0-1.2.2/input0, status -71
[ 2168.938791] usb 2-1.5: device descriptor read/64, error -32
[ 2169.128635] usb 2-1.5: new full speed USB device using ehci_hcd and address 16
[ 2169.548002] usb 2-1.5: device not accepting address 16, error -32
[ 2169.628152] usb 2-1.5: new full speed USB device using ehci_hcd and address 17
[ 2170.047479] usb 2-1.5: device not accepting address 17, error -32
[ 2170.047572] hub 2-1:1.0: unable to enumerate USB device on port 5
[ 2170.048051] usb 2-1.2: USB disconnect, address 3
[ 2170.048056] usb 2-1.2.1: USB disconnect, address 8
[ 2170.048073] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: can't reset device, 0000:00:1d.0-1.2.1/input1, status -108
[ 2170.048082] usb 2-1.2: clear tt 1 (0080) error -19
[ 2170.048088] usb 2-1.2: clear tt 2 (0090) error -19
[ 2170.590362] usb 2-1.2.2: USB disconnect, address 9
[15748.777239] usb 2-1.2: new high speed USB device using ehci_hcd and address 18
[15748.886972] hub 2-1.2:1.0: USB hub found
[15748.887048] hub 2-1.2:1.0: 4 ports detected
[15748.968935] usb 2-1.5: new full speed USB device using ehci_hcd and address 19
[15749.047358] usb 2-1.5: device descriptor read/64, error -32
[15749.236175] usb 2-1.5: device descriptor read/64, error -32
[15749.428368] usb 2-1.5: new full speed USB device using ehci_hcd and address 20
[15749.506387] usb 2-1.5: device descriptor read/64, error -32
[15749.698097] usb 2-1.5: device descriptor read/64, error -32
[15749.887947] usb 2-1.5: new full speed USB device using ehci_hcd and address 21
[15750.307228] usb 2-1.5: device not accepting address 21, error -32
[15750.387302] usb 2-1.5: new full speed USB device using ehci_hcd and address 22
[15750.804976] usb 2-1.5: device not accepting address 22, error -32
[15750.805147] hub 2-1:1.0: unable to enumerate USB device on port 5
[15750.886675] usb 2-1.2.1: new low speed USB device using ehci_hcd and address 23
[15751.009751] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.0/input/input11
[15751.009976] logitech 0003:046D:C30A.0004: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1.2.1/input0
[15751.019608] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.1/2-1.2.1:1.1/input/input12
[15751.019979] logitech 0003:046D:C30A.0005: input,hidraw1: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1.2.1/input1
[15751.096686] usb 2-1.2.2: new low speed USB device using ehci_hcd and address 24
[15751.218185] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.2/2-1.2.2:1.0/input/input13
[15751.218456] generic-usb 0003:046D:C001.0006: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1d.0-1.2.2/input0
[15751.296355] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 25
[15756.380367] usb 2-1.2.4: device descriptor read/64, error -71
[15761.575358] usb 2-1.2.4: device descriptor read/64, error -71
[15761.764697] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 26
[15766.849643] usb 2-1.2.4: device descriptor read/64, error -71
[15772.054121] usb 2-1.2.4: device descriptor read/64, error -71
[15772.241172] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 27
[15777.657977] usb 2-1.2.4: device not accepting address 27, error -71
[15777.734894] usb 2-1.2.4: new high speed USB device using ehci_hcd and address 28
[15783.152195] usb 2-1.2.4: device not accepting address 28, error -71
[15783.152290] hub 2-1.2:1.0: unable to enumerate USB device on port 4 

```

I could connet to the machine via ssh. Xorg is using a lot of resources:
```
2194 root      20   0  156m  19m 9928 S   73  0.3   6:41.86 Xorg
```

---

### Post by P4man on 2010-10-13
Looks like something is (very) wrong with your USB. A device acting up or a bad hub? Powered hub without power? What does your config look like, are you onboard USB with a hub, or your newly purchased USB PCI controller ?

Anyway, this is not my area of expertise and google isnt too helpful on this one. But it doesnt look like nouveau has anything to do with it.

---

### Post by reto on 2010-10-13
No, the only things I've change is:
Ubuntu 10.04 -> 10.10
32 bits -> 64 bits
mvidia -> nouveau

I have mouse and keyboard attached via the hub in the monitor and I had a scanner connected to the laptop (the scanner is by far the oldest of these things and I've detached it now).

---

### Post by P4man on 2010-10-13
well.. in that case Id be (very) suspecious of the monitor USB hub, especially since the external monitor already seemed to cause problems, even if EDID shouldnt be related to USB. Perhaps you can attach your devices straight to your PC for a while?

---

### Post by reto on 2010-10-14
no luck, X still freezes after using it a bit.

---

### Post by eliasv on 2010-10-14
I can also support that this is a nouveau problem, as I was getting the same everything-freeze-except-the-cursor issue in 10.04 and switching to nvidia drivers fixed it (came with it's own problems though). Now I am using 10.10 nvidia has stopped booting and using nouveau the random freeze problem persists.

I have also managed to break nouveau now by trying to use the drivers directly from nvidia (as was reccommended for my laptop somewhere else - vaio F11 - nvidia 330m) but this is a seperate issue :)...

So anyway, it does in fact look to me like the freeze issue is related to nouveau somehow, assuming my problem is the same one... Any other thoughts?

p.s. I'm not using any external monitors or usb ports at the moment if that's helpful at all.

---

### Post by reto on 2010-10-14
After trying the latest driver from nvidia.com and having the same problem as with the nvidia driver provider by ubuntu (no working x) I evntaully managed to get things working with the nv driver. The problem here is that the external monitor doesn't work when connceted vis hdmi but only when connceted via the vga port, the image is less sharp using this port.

---

### Post by reto on 2010-10-24
With the nv driver I have the following problems:
- No full screen mode in flash
- System doesn't recover from suspend (when opening the lid, the system reboots)

---

### Post by eliasv on 2010-10-25
Just to confirm once more, I still have the exact same issues as reto. I also have the system working using nv only now with the system resume problem. Also, the system doesn't work at all on battery power for some reason. Just suspends until plugged back in then reboots when you try to resume.

Sorry I can't be more help :).

---

