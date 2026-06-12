---
title: "intrepid slow boot"
date: 2008-12-16
forum: General Help
---

### Post by OliverN on 2008-12-16
I upgraded hardy->intrepid and am experiencing very slow boot times...

some dmesg sections:

```
[   22.758056] firmware: requesting iwlwifi-3945-1.ucode
[   22.879471] Registered led device: iwl-phy0:radio
[   22.879559] Registered led device: iwl-phy0:assoc
[   22.879601] Registered led device: iwl-phy0:RX
[   22.879641] Registered led device: iwl-phy0:TX
[   24.333201] NET: Registered protocol family 17
[  106.021275] ACPI: WMI: Mapper loaded
[  107.451380] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  107.616088] apm: BIOS not found.
[  107.999830] ppdev: user-space parallel port driver
```

```
[  120.414289] padlock: VIA PadLock not detected.
[  120.800394] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  120.800408] [fglrx] Reserved FB block: Unshared offset:7fb7000, size:44000 
[  120.800412] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000 
[  128.445072] wlan0: no IPv6 routers present
[ 3615.340083] CPU0 attaching NULL sched-domain.
[ 3615.340106] CPU1 attaching NULL sched-domain.
[ 3615.342774] CPU0 attaching sched-domain:

```

```
[ 3615.342807] CPU1 attaching sched-domain:
[ 3615.342813]  domain 0: span 0-1 level MC
[ 3615.342819]   groups: 1 0
[ 3889.405971] iwl3945 0000:0b:00.0: PCI INT A disabled
[ 3889.847040] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3889.847222] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)

```

```
[ 3891.428758] wlan0: associated
[ 3891.429563] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3902.032072] wlan0: no IPv6 routers present
[ 4414.561614] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[ 4414.561624] [fglrx] Reserved FB block: Unshared offset:7fb7000, size:44000 
[ 4414.561628] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000 

```

the second one seems absolutely absurd. little help?

---

### Post by OliverN on 2008-12-17
I did some researching and found out that I could safely disable ipv6, so I did it by taking the steps in [this]("http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html") thread. It seems I've been successful - ipv6 is no longer loaded. My boot time hasn't changed however, and I don't get that at all! Below is the output of dmesg as of now. Could time stamps be wrong? Am I reading dmesg wrong? What could I do to speed things up?

```
[    1.119192] pci 0000:03:01.2: PME# disabled
[    1.119247] PCI: 0000:03:01.3 reg 10 32bit mmio: [df9fd600, df9fd6ff]
[    1.119330] pci 0000:03:01.3: supports D1
[    1.119335] pci 0000:03:01.3: supports D2
[    1.119340] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    1.119351] pci 0000:03:01.3: PME# disabled
[    1.119406] PCI: 0000:03:01.4 reg 10 32bit mmio: [df9fd700, df9fd7ff]
[    1.119487] pci 0000:03:01.4: supports D1
[    1.119492] pci 0000:03:01.4: supports D2
[    1.119498] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    1.119508] pci 0000:03:01.4: PME# disabled
[    1.119590] pci 0000:00:1e.0: transparent bridge
[    1.119604] PCI: bridge 0000:00:1e.0 32bit mmio: [df900000, df9fffff]
[    1.119652] bus 00 -> node 0
[    1.119667] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.120945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    1.121223] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    1.121599] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.121953] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.144318] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
[    1.144645] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[    1.144964] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    1.145284] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    1.145613] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    1.145944] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    1.146274] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    1.146604] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    1.148177] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.148177] pnp: PnP ACPI init
[    1.148177] ACPI: bus type pnp registered
[    1.231316] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    1.231316] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    1.231316] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    1.231316] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    1.231316] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    1.231316] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    1.233419] pnp: PnP ACPI: found 11 devices
[    1.233425] ACPI: ACPI bus type pnp unregistered
[    1.233433] PnPBIOS: Disabled by ACPI PNP
[    1.233473] PCI: Using ACPI for IRQ routing
[    1.240057] NET: Registered protocol family 8
[    1.240064] NET: Registered protocol family 20
[    1.240104] NetLabel: Initializing
[    1.240104] NetLabel:  domain hash size = 128
[    1.240104] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.240125] NetLabel:  unlabeled traffic allowed by default
[    1.240276] hpet clockevent registered
[    1.240286] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.240299] hpet0: 3 64-bit timers, 14318180 Hz
[    1.242633] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.242640]    actual entries 65620
[    1.242809] AppArmor: AppArmor Filesystem Enabled
[    1.242848] ACPI: RTC can wake from S4
[    1.244050] Switched to high resolution mode on CPU 0
[    1.245021] Switched to high resolution mode on CPU 1
[    1.248059] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    1.248067] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    1.248076] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    1.248084] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    1.248092] system 00:00: iomem range 0x100000-0x3fed33ff could not be reserved
[    1.248101] system 00:00: iomem range 0x3fed3400-0x3fefffff could not be reserved
[    1.248109] system 00:00: iomem range 0x3ff00000-0x3fffffff could not be reserved
[    1.248118] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
[    1.248126] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    1.248135] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    1.248143] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[    1.248152] system 00:00: iomem range 0xf0000000-0xf0003fff could not be reserved
[    1.248160] system 00:00: iomem range 0xf0004000-0xf0004fff could not be reserved
[    1.248169] system 00:00: iomem range 0xf0005000-0xf0005fff could not be reserved
[    1.248177] system 00:00: iomem range 0xf0006000-0xf0006fff could not be reserved
[    1.248186] system 00:00: iomem range 0xf0008000-0xf000bfff could not be reserved
[    1.248194] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[    1.248214] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    1.248230] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    1.248239] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    1.248247] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    1.248255] system 00:03: ioport range 0x809-0x809 has been reserved
[    1.248278] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    1.248285] system 00:08: ioport range 0x910-0x91f has been reserved
[    1.248293] system 00:08: ioport range 0x920-0x92f has been reserved
[    1.248300] system 00:08: ioport range 0x930-0x97f has been reserved
[    1.284588] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.284597] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    1.284607] pci 0000:00:01.0:   MEM window: 0xdfd00000-0xdfefffff
[    1.284617] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    1.284629] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    1.284635] pci 0000:00:1c.0:   IO window: disabled
[    1.284647] pci 0000:00:1c.0:   MEM window: 0xdfc00000-0xdfcfffff
[    1.284657] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.284672] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0c
[    1.284680] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    1.284693] pci 0000:00:1c.3:   MEM window: 0xdfa00000-0xdfbfffff
[    1.284704] pci 0000:00:1c.3:   PREFETCH window: 0x000000d0000000-0x000000d01fffff
[    1.284719] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    1.284725] pci 0000:00:1e.0:   IO window: disabled
[    1.284737] pci 0000:00:1e.0:   MEM window: 0xdf900000-0xdf9fffff
[    1.284747] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.284777] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.284787] pci 0000:00:01.0: setting latency timer to 64
[    1.284803] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.284814] pci 0000:00:1c.0: setting latency timer to 64
[    1.284833] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.284843] pci 0000:00:1c.3: setting latency timer to 64
[    1.284859] pci 0000:00:1e.0: setting latency timer to 64
[    1.284868] bus: 00 index 0 io port: [0, ffff]
[    1.284874] bus: 00 index 1 mmio: [0, ffffffff]
[    1.284880] bus: 01 index 0 io port: [e000, efff]
[    1.284886] bus: 01 index 1 mmio: [dfd00000, dfefffff]
[    1.284892] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    1.284898] bus: 01 index 3 mmio: [0, 0]
[    1.284904] bus: 0b index 0 mmio: [0, 0]
[    1.284909] bus: 0b index 1 mmio: [dfc00000, dfcfffff]
[    1.284915] bus: 0b index 2 mmio: [0, 0]
[    1.284921] bus: 0b index 3 mmio: [0, 0]
[    1.284926] bus: 0c index 0 io port: [d000, dfff]
[    1.284932] bus: 0c index 1 mmio: [dfa00000, dfbfffff]
[    1.284939] bus: 0c index 2 mmio: [d0000000, d01fffff]
[    1.284945] bus: 0c index 3 mmio: [0, 0]
[    1.284950] bus: 03 index 0 mmio: [0, 0]
[    1.284956] bus: 03 index 1 mmio: [df900000, df9fffff]
[    1.284962] bus: 03 index 2 mmio: [0, 0]
[    1.284967] bus: 03 index 3 io port: [0, ffff]
[    1.284973] bus: 03 index 4 mmio: [0, ffffffff]
[    1.284993] NET: Registered protocol family 2
[    1.300126] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.300668] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.301563] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.302008] TCP: Hash tables configured (established 131072 bind 65536)
[    1.302016] TCP reno registered
[    1.308169] NET: Registered protocol family 1
[    1.308433] checking if image is initramfs... it is
[    2.241022] Clocksource tsc unstable (delta = 2062700782 ns)
[    3.057415] Freeing initrd memory: 8002k freed
[    3.057755] Simple Boot Flag at 0x79 set to 0x1
[    3.060161] audit: initializing netlink socket (disabled)
[    3.060202] type=2000 audit(1229550785.057:1): initialized
[    3.075758] highmem bounce pool size: 64 pages
[    3.075773] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.082414] VFS: Disk quotas dquot_6.5.1
[    3.082654] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.082908] msgmni has been set to 1761
[    3.083212] io scheduler noop registered
[    3.083219] io scheduler anticipatory registered
[    3.083225] io scheduler deadline registered
[    3.083256] io scheduler cfq registered (default)
[    3.083443] pci 0000:01:00.0: Boot video device
[    3.083732] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    3.083805] pcieport-driver 0000:00:01.0: found MSI capability
[    3.083867] pci_express 0000:00:01.0:pcie00: allocate port service
[    3.083982] pci_express 0000:00:01.0:pcie03: allocate port service
[    3.084192] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    3.084264] pcieport-driver 0000:00:1c.0: found MSI capability
[    3.084336] pci_express 0000:00:1c.0:pcie00: allocate port service
[    3.084461] pci_express 0000:00:1c.0:pcie02: allocate port service
[    3.084594] pci_express 0000:00:1c.0:pcie03: allocate port service
[    3.084818] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    3.084890] pcieport-driver 0000:00:1c.3: found MSI capability
[    3.084961] pci_express 0000:00:1c.3:pcie00: allocate port service
[    3.085097] pci_express 0000:00:1c.3:pcie02: allocate port service
[    3.085232] pci_express 0000:00:1c.3:pcie03: allocate port service
[    3.086156] isapnp: Scanning for PnP cards...
[    3.441254] isapnp: No Plug & Play device found
[    3.538246] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.544278] brd: module loaded
[    3.544466] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.544788] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.548117] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.548132] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.552330] mice: PS/2 mouse device common for all mice
[    3.552699] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.552757] rtc0: alarms up to one month, y3k, hpet irqs
[    3.553120] EISA: Probing bus 0 at eisa.0
[    3.553135] Cannot allocate resource for EISA slot 1
[    3.553185] EISA: Detected 0 cards.
[    3.553192] cpuidle: using governor ladder
[    3.553198] cpuidle: using governor menu
[    3.554516] TCP cubic registered
[    3.554570] Using IPI No-Shortcut mode
[    3.555109] registered taskstats version 1
[    3.555402]   Magic number: 4:881:904
[    3.555458] tty ptyz0: hash matches
[    3.555570] rtc_cmos 00:06: setting system clock to 2008-12-17 21:53:06 UTC (1229550786)
[    3.555578] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.555584] EDD information not available.
[    3.555592] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.555990] Freeing unused kernel memory: 424k freed
[    3.556126] Write protecting the kernel text: 2576k
[    3.556200] Write protecting the kernel read-only data: 936k
[    3.871008] fuse init (API version 7.9)
[    3.998049] ACPI: SSDT 3FED41B3, 01F1 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    3.998824] ACPI: SSDT 3FED3F68, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    4.000284] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    4.000457] processor ACPI0007:00: registered as cooling_device0
[    4.000468] ACPI: Processor [CPU0] (supports 8 throttling states)
[    4.001279] ACPI: SSDT 3FED43A4, 0090 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    4.002011] ACPI: SSDT 3FED412E, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    4.003591] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    4.003753] processor ACPI0007:01: registered as cooling_device1
[    4.003765] ACPI: Processor [CPU1] (supports 8 throttling states)
[    4.039368] thermal LNXTHERM:01: registered as thermal_zone0
[    4.045385] ACPI: Thermal Zone [THM] (25 C)
[    4.828902] usbcore: registered new interface driver usbfs
[    4.828954] usbcore: registered new interface driver hub
[    4.829098] usbcore: registered new device driver usb
[    4.865666] USB Universal Host Controller Interface driver v3.0
[    4.865757] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.865777] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.865786] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.865884] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.865942] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    4.866251] usb usb1: configuration #1 chosen from 1 choice
[    4.866319] hub 1-0:1.0: USB hub found
[    4.866336] hub 1-0:1.0: 2 ports detected
[    4.972527] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.972548] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.972557] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.972634] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.972692] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    4.972922] usb usb2: configuration #1 chosen from 1 choice
[    4.972992] hub 2-0:1.0: USB hub found
[    4.973009] hub 2-0:1.0: 2 ports detected
[    4.984915] No dock devices found.
[    5.025840] SCSI subsystem initialized
[    5.080530] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    5.080549] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.080559] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.080620] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    5.080680] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    5.080902] usb usb3: configuration #1 chosen from 1 choice
[    5.080970] hub 3-0:1.0: USB hub found
[    5.080986] hub 3-0:1.0: 2 ports detected
[    5.143829] libata version 3.00 loaded.
[    5.184565] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    5.184584] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    5.184593] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    5.184664] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    5.184727] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    5.184966] usb usb4: configuration #1 chosen from 1 choice
[    5.185036] hub 4-0:1.0: USB hub found
[    5.185053] hub 4-0:1.0: 2 ports detected
[    5.292853] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.292882] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.292890] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.292957] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    5.296876] ehci_hcd 0000:00:1d.7: debug port 1
[    5.296890] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.296906] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    5.312043] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.312314] usb usb5: configuration #1 chosen from 1 choice
[    5.312386] hub 5-0:1.0: USB hub found
[    5.312404] hub 5-0:1.0: 8 ports detected
[    5.416773] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.416836] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    5.416866] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    5.424404] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.477255] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[df9fd800-df9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.484588] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.548142] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    5.559701] b44.c:v2.0
[    5.560040] ata_piix 0000:00:1f.2: version 2.12
[    5.560062] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.560073] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    5.560157] ata_piix 0000:00:1f.2: setting latency timer to 64
[    5.561460] scsi0 : ata_piix
[    5.561687] scsi1 : ata_piix
[    5.563891] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    5.563900] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    5.580830] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:ac:34:c0
[    6.198809] ata1.00: failed to set max address (err_mask=0x1)
[    6.198818] ata1.00: device aborted resize (153356490 -> 156301488), skipping HPA handling
[    6.198833] ata1.00: ATA-7: SAMSUNG HM080II, YE100-15, max UDMA7
[    6.198841] ata1.00: 153356490 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    6.212476] ata1.00: configured for UDMA/133
[    6.392630] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE04, max UDMA/33
[    6.424513] ata2.00: configured for UDMA/33
[    6.424750] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM080II  YE10 PQ: 0 ANSI: 5
[    6.440515] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE04 PQ: 0 ANSI: 5
[    6.465543] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.465641] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    6.495816] Driver 'sr' needs updating - please use bus_type methods
[    6.512436] Driver 'sd' needs updating - please use bus_type methods
[    6.512650] sd 0:0:0:0: [sda] 153356490 512-byte hardware sectors (78519 MB)
[    6.512700] sd 0:0:0:0: [sda] Write Protect is off
[    6.512707] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.512789] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.512952] sd 0:0:0:0: [sda] 153356490 512-byte hardware sectors (78519 MB)
[    6.512998] sd 0:0:0:0: [sda] Write Protect is off
[    6.513010] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.513096] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.513106]  sda: sda1 sda2 sda3 < sda5 >
[    6.565913] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.568594] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    6.568603] Uniform CD-ROM driver Revision: 3.20
[    6.568798] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.753396] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[424fc00007ccb450]
[    6.932764] PM: Starting manual resume from disk
[    6.932773] PM: Resume from partition 8:2
[    6.932778] PM: Checking hibernation image.
[    6.933082] PM: Resume from disk failed.
[    7.013022] kjournald starting.  Commit interval 5 seconds
[    7.013058] EXT3-fs: mounted filesystem with ordered data mode.
[   17.737304] udevd version 124 started
[   18.887728] Linux agpgart interface v0.103
[   19.037683] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.166319] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.431670] iTCO_vendor_support: vendor-support=0
[   19.473611] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   19.473798] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   19.473993] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.815598] ACPI: Battery Slot [BAT0] (battery present)
[   19.836929] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[   19.837600] ACPI: Lid Switch [LID]
[   19.837781] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   19.861047] ACPI: Power Button (CM) [PBTN]
[   19.861293] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   19.877029] ACPI: Sleep Button (CM) [SBTN]
[   19.989241] intel_rng: FWH not detected
[   20.041702] ACPI: AC Adapter [AC] (off-line)
[   20.634960] ricoh-mmc: Ricoh MMC Controller disabling driver
[   20.634968] ricoh-mmc: Copyright(c) Philip Langdale
[   20.635033] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
[   20.635069] ricoh-mmc: Controller is now disabled.
[   20.736716] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   21.008514] [fglrx] Maximum main memory to use for locked dma buffers: 926 MBytes.
[   21.009920] [fglrx]   vendor: 1002 device: 7145 count: 1
[   21.011978] [fglrx] ioport: bar 1, base 0xee00, size: 0x100
[   21.012036] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.012053] pci 0000:01:00.0: setting latency timer to 64
[   21.014982] [fglrx] PAT is enabled successfully!
[   21.015048] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   21.107597] sdhci: Secure Digital Host Controller Interface driver
[   21.107605] sdhci: Copyright(c) Pierre Ossman
[   21.169455] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[   21.169491] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   21.172627] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   21.718974] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:20/device:21/input/input5
[   21.745044] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   21.746598] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:26/input/input6
[   21.777038] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   21.777425] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/input/input7
[   21.809057] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   22.019431] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   22.019441] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   22.019594] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.019615] iwl3945 0000:0b:00.0: setting latency timer to 64
[   22.019646] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   22.174313] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   22.243276] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.374610] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   22.413119] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   22.458966] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   22.733143] iwl3945 0000:0b:00.0: PCI INT A disabled
[   23.121057] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   23.121097] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   25.784833] lp: driver loaded but no devices found
[   26.191474] Adding 3903784k swap on /dev/sda2.  Priority:-1 extents:1 across:3903784k
[   26.242403] EXT3 FS on sda1, internal journal
[   27.380944] type=1505 audit(1229550810.022:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4042
[   27.839884] type=1505 audit(1229550810.482:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4047
[   27.840301] type=1505 audit(1229550810.482:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4047
[   28.113512] ip_tables: (C) 2000-2006 Netfilter Core Team
[   28.225317] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.225487] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   28.225810] firmware: requesting iwlwifi-3945-1.ucode
[   28.343487] Registered led device: iwl-phy0:radio
[   28.343575] Registered led device: iwl-phy0:assoc
[   28.343620] Registered led device: iwl-phy0:RX
[   28.343668] Registered led device: iwl-phy0:TX
[   29.849262] NET: Registered protocol family 17
[  111.433872] ACPI: WMI: Mapper loaded
[  113.183757] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  113.338005] apm: BIOS not found.
[  113.654688] ppdev: user-space parallel port driver
[  116.739626] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  116.739645] vboxdrv: Successfully done.
[  116.739650] vboxdrv: Found 2 processor cores.
[  116.740616] vboxdrv: fAsync=1 offMin=0xc445db44 offMax=0xc445db44
[  116.740652] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[  116.740660] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[  124.109933] iwl3945 0000:0b:00.0: PCI INT A disabled
[  124.393877] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  124.394036] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[  124.442532] Registered led device: iwl-phy0:radio
[  124.443832] Registered led device: iwl-phy0:assoc
[  124.445016] Registered led device: iwl-phy0:RX
[  124.447045] Registered led device: iwl-phy0:TX
[  124.854223] wlan0: authenticate with AP 00:12:bf:2e:73:ff
[  124.854256] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  124.860429] wlan0: authenticate with AP 00:12:bf:2e:73:ff
[  124.865483] wlan0: authenticated
[  124.865495] wlan0: associate with AP 00:12:bf:2e:73:ff
[  124.880535] wlan0: RX AssocResp from 00:12:bf:2e:73:ff (capab=0x431 status=0 aid=3)
[  124.880545] wlan0: associated
[  125.765301] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  125.765315] [fglrx] Reserved FB block: Unshared offset:7fb7000, size:44000 
[  125.765319] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000 
[  127.614784] padlock: VIA PadLock not detected.
[  162.099953] CPU0 attaching NULL sched-domain.
[  162.099968] CPU1 attaching NULL sched-domain.
[  162.109091] CPU0 attaching sched-domain:
[  162.109102]  domain 0: span 0-1 level MC
[  162.109106]   groups: 0 1
[  162.109114]   domain 1: span 0-1 level CPU
[  162.109117]    groups: 0-1
[  162.109125] CPU1 attaching sched-domain:
[  162.109128]  domain 0: span 0-1 level MC
[  162.109131]   groups: 1 0
[  162.109136]   domain 1: span 0-1 level CPU
[  162.109139]    groups: 0-1
[  422.697230] CPU0 attaching NULL sched-domain.
[  422.697251] CPU1 attaching NULL sched-domain.
[  422.700131] CPU0 attaching sched-domain:
[  422.700145]  domain 0: span 0-1 level MC
[  422.700152]   groups: 0 1
[  422.700165] CPU1 attaching sched-domain:
[  422.700171]  domain 0: span 0-1 level MC
[  422.700177]   groups: 1 0
[ 9794.312541] CPU0 attaching NULL sched-domain.
[ 9794.312566] CPU1 attaching NULL sched-domain.
[ 9794.336161] CPU0 attaching sched-domain:
[ 9794.336171]  domain 0: span 0-1 level MC
[ 9794.336175]   groups: 0 1
[ 9794.336191]   domain 1: span 0-1 level CPU
[ 9794.336195]    groups: 0-1
[ 9794.336201] CPU1 attaching sched-domain:
[ 9794.336204]  domain 0: span 0-1 level MC
[ 9794.336207]   groups: 1 0
[ 9794.336222]   domain 1: span 0-1 level CPU
[ 9794.336225]    groups: 0-1
[ 9821.046866] CPU0 attaching NULL sched-domain.
[ 9821.046880] CPU1 attaching NULL sched-domain.
[ 9821.050239] CPU0 attaching sched-domain:
[ 9821.050247]  domain 0: span 0-1 level MC
[ 9821.050251]   groups: 0 1
[ 9821.050258] CPU1 attaching sched-domain:
[ 9821.050261]  domain 0: span 0-1 level MC
[ 9821.050264]   groups: 1 0
```

(bump)

---

### Post by ion072002 on 2009-01-12
I also have the same problem... it takes about 5 min for it to start... anybody?

---

### Post by OliverN on 2009-01-12
in any case your problem needs to be diagnosed in relation to your specific setup. one way you can do that is by posting the output of **dmesg**. however, unless your problem turns out to be either **ACPI: WMI: Mapper loaded** or **CPU0 attaching NULL sched-domain.** I'd advise you to create your own thread.

Anyway, I'll use your bump to ask more specifically if anyone has any knowledge on why **CPU0 attaching NULL sched-domain** is stalling my system this much.

my cpu is the Intel Core Duo T2050

---

