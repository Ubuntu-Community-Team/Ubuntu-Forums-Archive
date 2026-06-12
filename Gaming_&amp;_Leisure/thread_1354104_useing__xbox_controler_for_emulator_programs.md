---
title: "useing  xbox controler for emulator programs"
date: 2009-12-13
forum: Gaming &amp; Leisure
---

### Post by JohnsShadow on 2009-12-13
hello 
im trying to play my old N64 games (via mupen64) and my old ps1 games (via pcsx) both versions of the applications are the ones in the software channel for 9.10 (ill be back with exact build numbers)

from what i can tell the xbox pad drivers are built into the kernal

but when i try to configure said programs to accept the controller both act like they have never seen a controller in there life

after running dmesg, it seems that the controler is reconized


```
[    0.003900] Initializing cgroup subsys memory
[    0.003914] Initializing cgroup subsys freezer
[    0.003917] Initializing cgroup subsys net_cls
[    0.003942] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.003947] CPU: L2 cache: 512K
[    0.003950] CPU: Hyper-Threading is disabled
[    0.003957] mce: CPU supports 4 MCE banks
[    0.003971] CPU0: Thermal monitoring enabled (TM1)
[    0.003990] Performance Counters: no PMU driver, software counters only.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017023] SMP alternatives: switching to UP code
[    0.028022] Freeing SMP alternatives: 19k freed
[    0.028052] ACPI: Core revision 20090521
[    0.033260]   alloc irq_desc for 22 on node 0
[    0.033264]   alloc kstat_irqs on node 0
[    0.033401] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.073089] CPU0: Intel(R) Pentium(R) 4 CPU 2.50GHz stepping 09
[    0.076001] Brought up 1 CPUs
[    0.076001] Total of 1 processors activated (4981.25 BogoMIPS).
[    0.076001] CPU0 attaching NULL sched-domain.
[    0.076001] Booting paravirtualized kernel on bare hardware
[    0.076001] regulator: core version 0.5
[    0.076001] Time: 11:39:30  Date: 12/13/09
[    0.076001] NET: Registered protocol family 16
[    0.076001] EISA bus registered
[    0.076001] ACPI: bus type pci registered
[    0.076001] PCI: PCI BIOS revision 2.10 entry at 0xf1490, last bus=2
[    0.076001] PCI: Using configuration type 1 for base access
[    0.076208] bio: create slab <bio-0> at 0
[    0.076731] ACPI: EC: Look up EC in DSDT
[    0.080427] ACPI: Interpreter enabled
[    0.080436] ACPI: (supports S0 S1 S3 S4 S5)
[    0.080468] ACPI: Using IOAPIC for interrupt routing
[    0.094362] ACPI: No dock devices found.
[    0.094510] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.094571] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.094749] pci 0000:00:1d.0: reg 20 io port: [0xd800-0xd81f]
[    0.094811] pci 0000:00:1d.1: reg 20 io port: [0xd400-0xd41f]
[    0.094874] pci 0000:00:1d.2: reg 20 io port: [0xd000-0xd01f]
[    0.094946] pci 0000:00:1d.7: reg 10 32bit mmio: [0xdf000000-0xdf0003ff]
[    0.095013] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.095019] pci 0000:00:1d.7: PME# disabled
[    0.095079] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.095082] * this clock source is slow. If you are sure your timer does not have
[    0.095084] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.095132] pci 0000:00:1f.0: Enabled i801 SMBus device
[    0.095139] pci 0000:00:1f.0: quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[    0.095144] pci 0000:00:1f.0: quirk: region ec00-ec3f claimed by ICH4 GPIO
[    0.095173] pci 0000:00:1f.1: reg 10 io port: [0xa800-0xa807]
[    0.095182] pci 0000:00:1f.1: reg 14 io port: [0xa400-0xa403]
[    0.095190] pci 0000:00:1f.1: reg 18 io port: [0xa000-0xa007]
[    0.095198] pci 0000:00:1f.1: reg 1c io port: [0x9800-0x9803]
[    0.095206] pci 0000:00:1f.1: reg 20 io port: [0x9400-0x940f]
[    0.095214] pci 0000:00:1f.1: reg 24 32bit mmio: [0xda800000-0xda8003ff]
[    0.095275] pci 0000:00:1f.3: reg 20 io port: [0xe800-0xe81f]
[    0.095397] pci 0000:02:09.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
[    0.095406] pci 0000:02:09.0: reg 14 32bit mmio: [0xe0000000-0xefffffff]
[    0.095414] pci 0000:02:09.0: reg 18 32bit mmio: [0xdd000000-0xddffffff]
[    0.095436] pci 0000:02:09.0: reg 30 32bit mmio: [0xdffe0000-0xdfffffff]
[    0.095491] pci 0000:02:0a.0: reg 10 32bit mmio: [0xdc800000-0xdc800fff]
[    0.095539] pci 0000:02:0a.0: supports D1 D2
[    0.095542] pci 0000:02:0a.0: PME# supported from D0 D1 D2 D3hot
[    0.095547] pci 0000:02:0a.0: PME# disabled
[    0.095585] pci 0000:02:0a.1: reg 10 32bit mmio: [0xdc000000-0xdc000fff]
[    0.095633] pci 0000:02:0a.1: supports D1 D2
[    0.095636] pci 0000:02:0a.1: PME# supported from D0 D1 D2 D3hot
[    0.095641] pci 0000:02:0a.1: PME# disabled
[    0.095678] pci 0000:02:0a.2: reg 10 32bit mmio: [0xdb800000-0xdb8000ff]
[    0.095726] pci 0000:02:0a.2: supports D1 D2
[    0.095729] pci 0000:02:0a.2: PME# supported from D0 D1 D2 D3hot
[    0.095734] pci 0000:02:0a.2: PME# disabled
[    0.095781] pci 0000:02:0b.0: reg 10 io port: [0xb800-0xb8ff]
[    0.095833] pci 0000:02:0b.0: supports D1 D2
[    0.095873] pci 0000:02:0d.0: reg 10 io port: [0xb400-0xb4ff]
[    0.095882] pci 0000:02:0d.0: reg 14 32bit mmio: [0xdb000000-0xdb0000ff]
[    0.095927] pci 0000:02:0d.0: supports D1 D2
[    0.095929] pci 0000:02:0d.0: PME# supported from D1 D2 D3hot D3cold
[    0.095935] pci 0000:02:0d.0: PME# disabled
[    0.095966] pci 0000:00:1e.0: transparent bridge
[    0.095972] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[    0.095977] pci 0000:00:1e.0: bridge 32bit mmio: [0xdb000000-0xdeffffff]
[    0.095984] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xdff00000-0xefffffff]
[    0.096005] pci_bus 0000:00: on NUMA node 0
[    0.096010] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.096104] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.096156] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.171331] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.171466] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.171597] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.171728] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.171841] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.171974] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.172094] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.172227] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.172496] SCSI subsystem initialized
[    0.172594] libata version 3.00 loaded.
[    0.172703] usbcore: registered new interface driver usbfs
[    0.172728] usbcore: registered new interface driver hub
[    0.172762] usbcore: registered new device driver usb
[    0.172934] ACPI: WMI: Mapper loaded
[    0.172938] PCI: Using ACPI for IRQ routing
[    0.173133] Bluetooth: Core ver 2.15
[    0.173174] NET: Registered protocol family 31
[    0.173178] Bluetooth: HCI device and connection manager initialized
[    0.173182] Bluetooth: HCI socket layer initialized
[    0.173184] NetLabel: Initializing
[    0.173187] NetLabel:  domain hash size = 128
[    0.173189] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.173210] NetLabel:  unlabeled traffic allowed by default
[    0.175571] pnp: PnP ACPI init
[    0.175608] ACPI: bus type pnp registered
[    0.179526] pnp: PnP ACPI: found 14 devices
[    0.179530] ACPI: ACPI bus type pnp unregistered
[    0.179536] PnPBIOS: Disabled by ACPI PNP
[    0.179551] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.179557] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.179561] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[    0.179571] system 00:02: ioport range 0xe400-0xe47f has been reserved
[    0.179576] system 00:02: ioport range 0xe800-0xe81f has been reserved
[    0.179580] system 00:02: ioport range 0xec00-0xec3f has been reserved
[    0.179583] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    0.179588] system 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.179592] system 00:02: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.179596] system 00:02: iomem range 0xfec00000-0xfec000ff could not be reserved
[    0.179604] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.179614] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.179625] system 00:0d: ioport range 0x3f0-0x3f1 has been reserved
[    0.214421] AppArmor: AppArmor Filesystem Enabled
[    0.214450] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.214453] pci 0000:00:01.0:   IO window: disabled
[    0.214460] pci 0000:00:01.0:   MEM window: disabled
[    0.214464] pci 0000:00:01.0:   PREFETCH window: disabled
[    0.214470] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.214475] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.214482] pci 0000:00:1e.0:   MEM window: 0xdb000000-0xdeffffff
[    0.214487] pci 0000:00:1e.0:   PREFETCH window: 0xdff00000-0xefffffff
[    0.214508] pci 0000:00:1e.0: setting latency timer to 64
[    0.214515] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.214518] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.214522] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.214525] pci_bus 0000:02: resource 1 mem: [0xdb000000-0xdeffffff]
[    0.214529] pci_bus 0000:02: resource 2 pref mem [0xdff00000-0xefffffff]
[    0.214532] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.214535] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.214586] NET: Registered protocol family 2
[    0.214716] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.215225] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.216607] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.217402] TCP: Hash tables configured (established 131072 bind 65536)
[    0.217407] TCP reno registered
[    0.217609] NET: Registered protocol family 1
[    0.217724] Trying to unpack rootfs image as initramfs...
[    0.515459] Freeing initrd memory: 8317k freed
[    0.529876] Simple Boot Flag at 0x3a set to 0x1
[    0.529988] cpufreq-nforce2: No nForce2 chipset.
[    0.530025] Scanning for low memory corruption every 60 seconds
[    0.530184] audit: initializing netlink socket (disabled)
[    0.530211] type=2000 audit(1260704370.528:1): initialized
[    0.539165] highmem bounce pool size: 64 pages
[    0.539174] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.540885] VFS: Disk quotas dquot_6.5.2
[    0.540956] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.541675] fuse init (API version 7.12)
[    0.541788] msgmni has been set to 1732
[    0.542055] alg: No test for stdrng (krng)
[    0.542073] io scheduler noop registered
[    0.542076] io scheduler anticipatory registered
[    0.542079] io scheduler deadline registered
[    0.542144] io scheduler cfq registered (default)
[    0.542227] pci 0000:02:09.0: Boot video device
[    0.542347] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.542380] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.542546] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.542551] ACPI: Power Button [PWRF]
[    0.542614] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.542618] ACPI: Power Button [PWRB]
[    0.542778] ACPI: Invalid PBLK length [5]
[    0.542826] processor LNXCPU:00: registered as cooling_device0
[    0.553663] isapnp: Scanning for PnP cards...
[    0.716065] Switched to high resolution mode on CPU 0
[    0.907956] isapnp: No Plug & Play device found
[    0.909534] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.909655] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.910114] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.911384] brd: module loaded
[    0.911951] loop: module loaded
[    0.912106] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.912252] ata_piix 0000:00:1f.1: version 2.13
[    0.912278]   alloc irq_desc for 18 on node -1
[    0.912281]   alloc kstat_irqs on node -1
[    0.912293] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.912369] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.912512] scsi0 : ata_piix
[    0.912651] scsi1 : ata_piix
[    0.913508] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x9400 irq 14
[    0.913512] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x9408 irq 15
[    0.914533] Fixed MDIO Bus: probed
[    0.914582] PPP generic driver version 2.4.2
[    0.914729] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.914757] ehci_hcd 0000:00:1d.7: enabling device (0004 -> 0006)
[    0.914768]   alloc irq_desc for 23 on node -1
[    0.914771]   alloc kstat_irqs on node -1
[    0.914780] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.914803] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.914809] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.914875] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.918793] ehci_hcd 0000:00:1d.7: debug port 1
[    0.918802] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.919123] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdf000000
[    0.932010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.932132] usb usb1: configuration #1 chosen from 1 choice
[    0.932174] hub 1-0:1.0: USB hub found
[    0.932186] hub 1-0:1.0: 6 ports detected
[    0.932260] ehci_hcd 0000:02:0a.2: enabling device (0014 -> 0016)
[    0.932270]   alloc irq_desc for 20 on node -1
[    0.932272]   alloc kstat_irqs on node -1
[    0.932280] ehci_hcd 0000:02:0a.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.932296] ehci_hcd 0000:02:0a.2: EHCI Host Controller
[    0.932351] ehci_hcd 0000:02:0a.2: new USB bus registered, assigned bus number 2
[    0.956044] ehci_hcd 0000:02:0a.2: irq 20, io mem 0xdb800000
[    0.968011] ehci_hcd 0000:02:0a.2: USB 2.0 started, EHCI 1.00
[    0.968091] usb usb2: configuration #1 chosen from 1 choice
[    0.968128] hub 2-0:1.0: USB hub found
[    0.968139] hub 2-0:1.0: 5 ports detected
[    0.968225] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.968255] ohci_hcd 0000:02:0a.0: enabling device (0014 -> 0016)
[    0.968262] ohci_hcd 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.968277] ohci_hcd 0000:02:0a.0: OHCI Host Controller
[    0.968320] ohci_hcd 0000:02:0a.0: new USB bus registered, assigned bus number 3
[    0.968347] ohci_hcd 0000:02:0a.0: irq 22, io mem 0xdc800000
[    1.053883] usb usb3: configuration #1 chosen from 1 choice
[    1.053927] hub 3-0:1.0: USB hub found
[    1.053939] hub 3-0:1.0: 3 ports detected
[    1.053999] ohci_hcd 0000:02:0a.1: enabling device (0014 -> 0016)
[    1.054006] ohci_hcd 0000:02:0a.1: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    1.054019] ohci_hcd 0000:02:0a.1: OHCI Host Controller
[    1.054068] ohci_hcd 0000:02:0a.1: new USB bus registered, assigned bus number 4
[    1.054087] ohci_hcd 0000:02:0a.1: irq 23, io mem 0xdc000000
[    1.096299] ata1.00: ATAPI: LITE-ON DVDRW SHW-1635S, YS06, max UDMA/66
[    1.096348] ata1.01: ATAPI: SAMSUNG CD-R/RW SW-248F, R602, max UDMA/33
[    1.137788] ata2.00: ATA-7: ST3160212A, 3.AAJ, max UDMA/100
[    1.137793] ata2.00: 312581808 sectors, multi 16: LBA48 
[    1.138107] ata1.00: configured for UDMA/66
[    1.138238] ata2.01: ATA-7: Maxtor 4R080L0, RAMC1TU0, max UDMA/133
[    1.138242] ata2.01: 160086528 sectors, multi 16: LBA 
[    1.138272] ata2.00: limited to UDMA/33 due to 40-wire cable
[    1.138275] ata2.01: limited to UDMA/33 due to 40-wire cable
[    1.138458] usb usb4: configuration #1 chosen from 1 choice
[    1.138497] hub 4-0:1.0: USB hub found
[    1.138511] hub 4-0:1.0: 2 ports detected
[    1.138578] uhci_hcd: USB Universal Host Controller Interface driver
[    1.138649]   alloc irq_desc for 16 on node -1
[    1.138652]   alloc kstat_irqs on node -1
[    1.138661] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.138671] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.138675] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.138724] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.138761] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[    1.138864] usb usb5: configuration #1 chosen from 1 choice
[    1.138904] hub 5-0:1.0: USB hub found
[    1.138917] hub 5-0:1.0: 2 ports detected
[    1.138971]   alloc irq_desc for 19 on node -1
[    1.138974]   alloc kstat_irqs on node -1
[    1.138980] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.138989] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.138993] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.139044] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.139076] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d400
[    1.139176] usb usb6: configuration #1 chosen from 1 choice
[    1.139212] hub 6-0:1.0: USB hub found
[    1.139229] hub 6-0:1.0: 2 ports detected
[    1.139290] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.139299] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.139304] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.139345] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.139377] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d000
[    1.139479] usb usb7: configuration #1 chosen from 1 choice
[    1.139515] hub 7-0:1.0: USB hub found
[    1.139527] hub 7-0:1.0: 2 ports detected
[    1.139655] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.139659] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.140088] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.140177] mice: PS/2 mouse device common for all mice
[    1.140298] rtc_cmos 00:05: RTC can wake from S4
[    1.140345] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.140369] rtc0: alarms up to one month, 242 bytes nvram
[    1.140524] device-mapper: uevent: version 1.0.3
[    1.140676] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.140780] device-mapper: multipath: version 1.1.0 loaded
[    1.140784] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.140949] EISA: Probing bus 0 at eisa.0
[    1.140989] EISA: Detected 0 cards.
[    1.141048] cpuidle: using governor ladder
[    1.141052] cpuidle: using governor menu
[    1.141725] TCP cubic registered
[    1.141882] NET: Registered protocol family 10
[    1.142412] lo: Disabled Privacy Extensions
[    1.142816] NET: Registered protocol family 17
[    1.142845] Bluetooth: L2CAP ver 2.13
[    1.142847] Bluetooth: L2CAP socket layer initialized
[    1.142852] Bluetooth: SCO (Voice Link) ver 0.6
[    1.142854] Bluetooth: SCO socket layer initialized
[    1.142910] Bluetooth: RFCOMM TTY layer initialized
[    1.142914] Bluetooth: RFCOMM socket layer initialized
[    1.142916] Bluetooth: RFCOMM ver 1.11
[    1.142962] Using IPI No-Shortcut mode
[    1.143067] PM: Resume from disk failed.
[    1.143090] registered taskstats version 1
[    1.143231]   Magic number: 5:312:681
[    1.143327] rtc_cmos 00:05: setting system clock to 2009-12-13 11:39:31 UTC (1260704371)
[    1.143333] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.143335] EDD information not available.
[    1.152475] ata1.01: configured for UDMA/33
[    1.154140] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-1635S  YS06 PQ: 0 ANSI: 5
[    1.158354] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.158360] Uniform CD-ROM driver Revision: 3.20
[    1.158488] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.158566] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.160147] scsi 0:0:1:0: CD-ROM            SAMSUNG  CD-R/RW SW-248F  R602 PQ: 0 ANSI: 5
[    1.163640] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.163735] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    1.163798] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.206943] ata2.00: configured for UDMA/33
[    1.220394] ata2.01: configured for UDMA/33
[    1.220513] scsi 1:0:0:0: Direct-Access     ATA      ST3160212A       3.AA PQ: 0 ANSI: 5
[    1.220659] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    1.220752] scsi 1:0:1:0: Direct-Access     ATA      Maxtor 4R080L0   RAMC PQ: 0 ANSI: 5
[    1.220873] sd 1:0:1:0: Attached scsi generic sg3 type 0
[    1.220924] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.220989] sd 1:0:0:0: [sda] Write Protect is off
[    1.220993] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.221025] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.221191]  sda:
[    1.254874] sd 1:0:1:0: [sdb] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    1.254935] sd 1:0:1:0: [sdb] Write Protect is off
[    1.254939] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.254970] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.255132]  sdb: sda1 sda2 sda3 < sdb1 sdb3 < sda5 sda6 >
[    1.300357]  sdb5 sdb6 >
[    1.300702] sd 1:0:1:0: [sdb] Attached SCSI disk
[    1.300813] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.300831] Freeing unused kernel memory: 540k freed
[    1.301661] Write protecting the kernel text: 4568k
[    1.301695] Write protecting the kernel read-only data: 1836k
[    1.579444] Linux agpgart interface v0.103
[    1.584044] usb 3-3: new low speed USB device using ohci_hcd and address 2
[    1.584096] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    1.593875] Floppy drive(s): fd0 is 1.44M
[    1.599923] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.599965] 8139cp 0000:02:0d.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.612173] FDC 0 is a post-1991 82077
[    1.630937] 8139too Fast Ethernet driver 0.9.28
[    1.631005]   alloc irq_desc for 17 on node -1
[    1.631009]   alloc kstat_irqs on node -1
[    1.631019] 8139too 0000:02:0d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.632347] eth0: RealTek RTL8139 at 0xb400, 00:0c:6e:fd:df:1e, IRQ 17
[    1.710118] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    1.854014] usb 3-3: configuration #1 chosen from 1 choice
[    1.865633] usbcore: registered new interface driver hiddev
[    1.871270] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1e.0/0000:02:0a.0/usb3/3-3/3-3:1.0/input/input3
[    1.871394] generic-usb 0003:0461:4D16.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:02:0a.0-3/input0
[    1.871420] usbcore: registered new interface driver usbhid
[    1.871425] usbhid: v2.6:USB HID core driver
[    1.968039] usb 7-2: new low speed USB device using uhci_hcd and address 2
[    2.146547] usb 7-2: configuration #1 chosen from 1 choice
[    2.173732] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input4
[    2.173836] generic-usb 0003:0A81:0205.0002: input,hidraw1: USB HID v1.10 Keyboard [CHESEN PS2 to USB Converter] on usb-0000:00:1d.2-2/input0
[    2.201840] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input5
[    2.201972] generic-usb 0003:0A81:0205.0003: input,hidraw2: USB HID v1.10 Mouse [CHESEN PS2 to USB Converter] on usb-0000:00:1d.2-2/input1
[    4.016407] xor: automatically using best checksumming function: pIII_sse
[    4.036008]    pIII_sse  :  3181.000 MB/sec
[    4.036011] xor: using function: pIII_sse (3181.000 MB/sec)
[    4.048118] device-mapper: dm-raid45: initialized v0.2594b
[    5.328999] PM: Starting manual resume from disk
[    5.329005] PM: Resume from partition 8:22
[    5.329008] PM: Checking hibernation image.
[    5.340032] PM: Resume from disk failed.
[    5.349016] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    5.349023] EXT4-fs (sda6): write access will be enabled during recovery
[    5.356524] EXT4-fs (sda6): barriers enabled
[    8.937012] kjournald2 starting: pid 365, dev sda6:8, commit interval 5 seconds
[    8.937048] EXT4-fs (sda6): delayed allocation enabled
[    8.937053] EXT4-fs: file extents enabled
[    8.937345] EXT4-fs: mballoc enabled
[    8.937365] EXT4-fs (sda6): orphan cleanup on readonly fs
[    8.937376] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 129
[    8.937421] EXT4-fs (sda6): 1 orphan inode deleted
[    8.937426] EXT4-fs (sda6): recovery complete
[    9.005475] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    9.654521] type=1505 audit(1260704380.009:2): operation="profile_load" pid=388 name=/usr/share/gdm/guest-session/Xsession
[    9.670686] type=1505 audit(1260704380.024:3): operation="profile_load" pid=389 name=/sbin/dhclient3
[    9.671356] type=1505 audit(1260704380.024:4): operation="profile_load" pid=389 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.671720] type=1505 audit(1260704380.024:5): operation="profile_load" pid=389 name=/usr/lib/connman/scripts/dhclient-script
[    9.732579] type=1505 audit(1260704380.088:6): operation="profile_load" pid=390 name=/usr/bin/evince
[    9.743984] type=1505 audit(1260704380.096:7): operation="profile_load" pid=390 name=/usr/bin/evince-previewer
[    9.750653] type=1505 audit(1260704380.104:8): operation="profile_load" pid=390 name=/usr/bin/evince-thumbnailer
[    9.790085] type=1505 audit(1260704380.144:9): operation="profile_load" pid=392 name=/usr/lib/cups/backend/cups-pdf
[    9.790869] type=1505 audit(1260704380.144:10): operation="profile_load" pid=392 name=/usr/sbin/cupsd
[    9.821733] type=1505 audit(1260704380.176:11): operation="profile_load" pid=393 name=/usr/sbin/tcpdump
[   22.351929] Adding 939760k swap on /dev/sda5.  Priority:-1 extents:1 across:939760k 
[   22.364267] udev: starting version 147
[   22.382238] Adding 2128540k swap on /dev/sdb6.  Priority:-2 extents:1 across:2128540k 
[   22.531097] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.579879] lp: driver loaded but no devices found
[   22.580084] parport_pc 00:0a: reported by Plug and Play ACPI
[   22.580165] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   22.594134] intel_rng: FWH not detected
[   22.676250] lp0: using parport0 (interrupt-driven).
[   23.127419] nvidia: module license 'NVIDIA' taints kernel.
[   23.127426] Disabling lock debugging due to kernel taint
[   23.423854] EXT4-fs (sda6): internal journal on sda6:8
[   23.445061] ppdev: user-space parallel port driver
[   23.488306] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.675586] C-Media PCI 0000:02:0b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   24.040363] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   24.094706]   alloc irq_desc for 21 on node -1
[   24.094712]   alloc kstat_irqs on node -1
[   24.094723] nvidia 0000:02:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   24.095346] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   24.212068] type=1505 audit(1260725994.568:12): operation="profile_replace" pid=916 name=/usr/share/gdm/guest-session/Xsession
[   24.214821] type=1505 audit(1260725994.568:13): operation="profile_replace" pid=917 name=/sbin/dhclient3
[   24.215489] type=1505 audit(1260725994.568:14): operation="profile_replace" pid=917 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   24.215853] type=1505 audit(1260725994.568:15): operation="profile_replace" pid=917 name=/usr/lib/connman/scripts/dhclient-script
[   24.225730] type=1505 audit(1260725994.580:16): operation="profile_replace" pid=918 name=/usr/bin/evince
[   24.244812] type=1505 audit(1260725994.600:17): operation="profile_replace" pid=918 name=/usr/bin/evince-previewer
[   24.251690] type=1505 audit(1260725994.604:18): operation="profile_replace" pid=918 name=/usr/bin/evince-thumbnailer
[   24.263197] type=1505 audit(1260725994.616:19): operation="profile_replace" pid=922 name=/usr/lib/cups/backend/cups-pdf
[   24.263986] type=1505 audit(1260725994.616:20): operation="profile_replace" pid=922 name=/usr/sbin/cupsd
[   24.276685] type=1505 audit(1260725994.632:21): operation="profile_replace" pid=923 name=/usr/sbin/tcpdump
[   34.440035] eth0: no IPv6 routers present
[ 6307.544037] usb 7-1: new full speed USB device using uhci_hcd and address 3
[ 6307.692617] usb 7-1: configuration #1 chosen from 1 choice
[ 6307.696658] hub 7-1:1.0: USB hub found
[ 6307.706035] hub 7-1:1.0: 3 ports detected
[ 6307.985457] usb 7-1.1: new full speed USB device using uhci_hcd and address 4
[ 6308.097579] usb 7-1.1: configuration #1 chosen from 1 choice
[ 6308.185447] input: Microsoft X-Box pad v2 (US) as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.1/7-1.1:1.0/input/input6
[ 6308.185536] usbcore: registered new interface driver xpad
[ 6308.185541] xpad: X-Box pad driver

```

and from the last lines of the code it seems that the controller is recognized 

i installed joystick,  which is apparently the new adaptation of jscallibrator

i gotta leave for work i will come back and post more info

---

