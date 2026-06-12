---
title: "long pause at post"
date: 2009-08-09
forum: Desktop Environments
---

### Post by jcarr911 on 2009-08-09
here is a problem that I can't seem to get to the bottom of can anyone help me. I have installed ubuntu 9.04 and xp on different drives but now it takes about 4 minutes to go from post to a os.. i like the os but i get a string of errors on boot and on shut down, it all seems to be usb related, and maybe nvida graphics card. I am running a intel mb(d875pbz),2.60 cpu,4g of ram,gforce3 card,sound blaster...any help would be greatly appreciated.here is dmesg.  
```
 	 	 	 	 	 	   0.004000]       .data : 0xc0504def - 0xc0729e60   (2196 kB)  
 [    0.004000]       .text : 0xc0100000 - 0xc0504def   (4115 kB)  
 [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.  
 [    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1  
 [    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 5186.88 BogoMIPS (lpj=10373776)  
 [    0.004032] Security Framework initialized  
 [    0.004043] SELinux:  Disabled at boot.  
 [    0.004064] AppArmor: AppArmor initialized  
 [    0.004077] Mount-cache hash table entries: 512  
 [    0.004239] Initializing cgroup subsys ns  
 [    0.004244] Initializing cgroup subsys cpuacct  
 [    0.004248] Initializing cgroup subsys memory  
 [    0.004254] Initializing cgroup subsys freezer  
 [    0.004271] CPU: Trace cache: 12K uops, L1 D cache: 8K  
 [    0.004275] CPU: L2 cache: 512K  
 [    0.004279] CPU: Physical Processor ID: 0  
 [    0.004283] CPU: Processor Core ID: 0  
 [    0.004299] Checking 'hlt' instruction... OK.  
 [    0.022999] ACPI: Core revision 20080926  
 [    0.024899] ACPI: Checking initramfs for custom DSDT  
 [    0.348890] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1  
 [    0.388582] CPU0: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09  
 [    0.392001] Booting processor 1 APIC 0x1 ip 0x6000  
 [    0.004000] Initializing CPU#1  
 [    0.004000] Calibrating delay using timer specific routine.. 5187.34 BogoMIPS (lpj=10374695)  
 [    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K  
 [    0.004000] CPU: L2 cache: 512K  
 [    0.004000] CPU: Physical Processor ID: 0  
 [    0.004000] CPU: Processor Core ID: 0  
 [    0.476195] CPU1: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09  
 [    0.476220] checking TSC synchronization [CPU#0 -> CPU#1]: passed.  
 [    0.480055] Brought up 2 CPUs  
 [    0.480061] Total of 2 processors activated (10374.23 BogoMIPS).  
 [    0.480111] CPU0 attaching sched-domain:  
 [    0.480116]  domain 0: span 0-1 level SIBLING  
 [    0.480120]   groups: 0 1  
 [    0.480129] CPU1 attaching sched-domain:  
 [    0.480134]  domain 0: span 0-1 level SIBLING  
 [    0.480137]   groups: 1 0  
 [    0.480221] net_namespace: 776 bytes 
 [    0.480221] Booting paravirtualized kernel on bare hardware  
 [    0.480479] Time: 15:11:47  Date: 08/09/09  
 [    0.480479] regulator: core version 0.5  
 [    0.480479] NET: Registered protocol family 16  
 [    0.480479] EISA bus registered  
 [    0.480479] ACPI: bus type pci registered  
 [    0.481491] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3  
 [    0.481495] PCI: Using configuration type 1 for base access  
 [    0.485217] ACPI: EC: Look up EC in DSDT  
 [    0.493426] ACPI: Interpreter enabled  
 [    0.493434] ACPI: (supports S0 S1 S4 S5)  
 [    0.493461] ACPI: Using IOAPIC for interrupt routing  
 [    0.501563] ACPI: No dock devices found.  
 [    0.501580] ACPI: PCI Root Bridge [PCI0] (0000:00)  
 [    0.501646] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]  
 [    0.501804] pci 0000:00:1d.0: reg 20 io port: [0xcc00-0xcc1f]  
 [    0.501859] pci 0000:00:1d.1: reg 20 io port: [0xd000-0xd01f]  
 [    0.501914] pci 0000:00:1d.2: reg 20 io port: [0xd400-0xd41f]  
 [    0.501968] pci 0000:00:1d.3: reg 20 io port: [0xd800-0xd81f]  
 [    0.502031] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe100000-0xfe1003ff]  
 [    0.502079] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold  
 [    0.502085] pci 0000:00:1d.7: PME# disabled  
 [    0.502176] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000  
 [    0.502183] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO  
 [    0.502188] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH4 GPIO  
 [    0.502210] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]  
 [    0.502218] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]  
 [    0.502226] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]  
 [    0.502234] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]  
 [    0.502242] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]  
 [    0.502250] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]  
 [    0.502280] pci 0000:00:1f.2: reg 10 io port: [0xec00-0xec07]  
 [    0.502288] pci 0000:00:1f.2: reg 14 io port: [0xe800-0xe803]  
 [    0.502295] pci 0000:00:1f.2: reg 18 io port: [0xe400-0xe407]  
 [    0.502303] pci 0000:00:1f.2: reg 1c io port: [0xe000-0xe003]  
 [    0.502310] pci 0000:00:1f.2: reg 20 io port: [0xdc00-0xdc0f]  
 [    0.502364] pci 0000:00:1f.3: reg 20 io port: [0xc800-0xc81f]  
 [    0.502420] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]  
 [    0.502428] pci 0000:01:00.0: reg 14 32bit mmio: [0xe8000000-0xefffffff]  
 [    0.502435] pci 0000:01:00.0: reg 18 32bit mmio: [0xf0000000-0xf007ffff]  
 [    0.502453] pci 0000:01:00.0: reg 30 32bit mmio: [0xfd000000-0xfd00ffff]  
 [    0.502504] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]  
 [    0.502509] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe8000000-0xf7ffffff]  
 [    0.502545] pci 0000:02:01.0: reg 10 32bit mmio: [0xfe000000-0xfe01ffff]  
 [    0.502557] pci 0000:02:01.0: reg 18 io port: [0xac00-0xac1f]  
 [    0.502583] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold  
 [    0.502588] pci 0000:02:01.0: PME# disabled  
 [    0.502629] pci 0000:00:03.0: bridge io port: [0xa000-0xafff]  
 [    0.502634] pci 0000:00:03.0: bridge 32bit mmio: [0xfe000000-0xfe0fffff]  
 [    0.502674] pci 0000:03:02.0: reg 10 io port: [0xb800-0xb81f]  
 [    0.502712] pci 0000:03:02.0: supports D1 D2  
 [    0.502744] pci 0000:03:02.1: reg 10 io port: [0xbc00-0xbc07]  
 [    0.502782] pci 0000:03:02.1: supports D1 D2  
 [    0.502824] pci 0000:03:04.0: reg 10 io port: [0xb400-0xb407]  
 [    0.502862] pci 0000:03:04.0: supports D2  
 [    0.502865] pci 0000:03:04.0: PME# supported from D0 D2 D3hot D3cold  
 [    0.502870] pci 0000:03:04.0: PME# disabled  
 [    0.502910] pci 0000:00:1e.0: transparent bridge  
 [    0.502916] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]  
 [    0.502938] bus 00 -> node 0  
 [    0.502946] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]  
 [    0.503109] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]  
 [    0.503216] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]  
 [    0.503314] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]  
 [    0.506090] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)  
 [    0.506300] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)  
 [    0.506514] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)  
 [    0.506720] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)  
 [    0.506933] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.  
 [    0.507148] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.  
 [    0.507358] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.  
 [    0.507568] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)  
 [    0.507728] ACPI: Power Resource [URP1] (off)  
 [    0.507777] ACPI: Power Resource [FDDP] (off)  
 [    0.507823] ACPI: Power Resource [LPTP] (off)  
 [    0.507960] ACPI: WMI: Mapper loaded 
 [    0.508183] SCSI subsystem initialized  
 [    0.508210] libata version 3.00 loaded.  
 [    0.508210] usbcore: registered new interface driver usbfs  
 [    0.508210] usbcore: registered new interface driver hub  
 [    0.508210] usbcore: registered new device driver usb  
 [    0.508210] PCI: Using ACPI for IRQ routing  
 [    0.516014] Bluetooth: Core ver 2.13 
 [    0.516040] NET: Registered protocol family 31  
 [    0.516040] Bluetooth: HCI device and connection manager initialized  
 [    0.516040] Bluetooth: HCI socket layer initialized  
 [    0.516040] NET: Registered protocol family 8  
 [    0.516040] NET: Registered protocol family 20  
 [    0.516055] NetLabel: Initializing  
 [    0.516058] NetLabel:  domain hash size = 128  
 [    0.516060] NetLabel:  protocols = UNLABELED CIPSOv4  
 [    0.516079] NetLabel:  unlabeled traffic allowed by default  
 [    0.516190] hpet clockevent registered  
 [    0.516195] HPET: 3 timers in total, 0 timers will be used for per-cpu timer  
 [    0.516203] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0  
 [    0.516211] hpet0: 3 comparators, 64-bit 14.318180 MHz counter  
 [    0.520095] AppArmor: AppArmor Filesystem Enabled  
 [    0.528014] pnp: PnP ACPI init  
 [    0.528030] ACPI: bus type pnp registered  
 [    0.532483] pnp: PnP ACPI: found 13 devices  
 [    0.532487] ACPI: ACPI bus type pnp unregistered  
 [    0.532493] PnPBIOS: Disabled by ACPI PNP  
 [    0.532512] system 00:09: ioport range 0x4d0-0x4d1 has been reserved  
 [    0.532522] system 00:0b: ioport range 0x400-0x47f has been reserved  
 [    0.532526] system 00:0b: ioport range 0x680-0x6ff has been reserved  
 [    0.532530] system 00:0b: ioport range 0x500-0x53f has been reserved  
 [    0.532534] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved  
 [    0.532538] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved  
 [    0.532542] system 00:0b: iomem range 0xfed20000-0xfed9ffff has been reserved  
 [    0.532551] system 00:0c: iomem range 0x0-0x9ffff could not be reserved  
 [    0.532555] system 00:0c: iomem range 0xc0000-0xdffff could not be reserved  
 [    0.532559] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved  
 [    0.532563] system 00:0c: iomem range 0x100000-0xe7ffffff could not be reserved  
 [    0.567342] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01  
 [    0.567345] pci 0000:00:01.0:   IO window: disabled  
 [    0.567352] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff  
 [    0.567357] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000f7ffffff  
 [    0.567365] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02  
 [    0.567369] pci 0000:00:03.0:   IO window: 0xa000-0xafff  
 [    0.567375] pci 0000:00:03.0:   MEM window: 0xfe000000-0xfe0fffff  
 [    0.567380] pci 0000:00:03.0:   PREFETCH window: disabled  
 [    0.567387] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03  
 [    0.567391] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff  
 [    0.567398] pci 0000:00:1e.0:   MEM window: disabled  
 [    0.567403] pci 0000:00:1e.0:   PREFETCH window: disabled  
 [    0.567425] pci 0000:00:1e.0: setting latency timer to 64  
 [    0.567430] bus: 00 index 0 io port: [0x00-0xffff]  
 [    0.567433] bus: 00 index 1 mmio: [0x000000-0xffffffff]  
 [    0.567437] bus: 01 index 0 mmio: [0x0-0x0]  
 [    0.567440] bus: 01 index 1 mmio: [0xfc000000-0xfdffffff]  
 [    0.567443] bus: 01 index 2 mmio: [0xe8000000-0xf7ffffff]  
 [    0.567446] bus: 01 index 3 mmio: [0x0-0x0]  
 [    0.567449] bus: 02 index 0 io port: [0xa000-0xafff]  
 [    0.567452] bus: 02 index 1 mmio: [0xfe000000-0xfe0fffff]  
 [    0.567455] bus: 02 index 2 mmio: [0x0-0x0]  
 [    0.567458] bus: 02 index 3 mmio: [0x0-0x0]  
 [    0.567461] bus: 03 index 0 io port: [0xb000-0xbfff]  
 [    0.567464] bus: 03 index 1 mmio: [0x0-0x0]  
 [    0.567467] bus: 03 index 2 mmio: [0x0-0x0]  
 [    0.567470] bus: 03 index 3 io port: [0x00-0xffff]  
 [    0.567473] bus: 03 index 4 mmio: [0x000000-0xffffffff]  
 [    0.567484] NET: Registered protocol family 2  
 [    0.580085] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)  
 [    0.580470] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)  
 [    0.580954] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)  
 [    0.581251] TCP: Hash tables configured (established 131072 bind 65536)  
 [    0.581255] TCP reno registered  
 [    0.588120] NET: Registered protocol family 1  
 [    0.588283] checking if image is initramfs... it is  
 [    1.016324] Switched to high resolution mode on CPU 1  
 [    1.020047] Switched to high resolution mode on CPU 0  
 [    1.259261] Freeing initrd memory: 7385k freed  
 [    1.259328] cpufreq: No nForce2 chipset.  
 [    1.259495] audit: initializing netlink socket (disabled)  
 [    1.259515] type=2000 audit(1249830707.257:1): initialized  
 [    1.266734] highmem bounce pool size: 64 pages  
 [    1.266741] HugeTLB registered 4 MB page size, pre-allocated 0 pages  
 [    1.268541] VFS: Disk quotas dquot_6.5.1  
 [    1.268633] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)  
 [    1.269512] fuse init (API version 7.10)  
 [    1.269628] msgmni has been set to 1655  
 [    1.270070] alg: No test for stdrng (krng)  
 [    1.270093] io scheduler noop registered  
 [    1.270099] io scheduler anticipatory registered  
 [    1.270104] io scheduler deadline registered  
 [    1.270133] io scheduler cfq registered (default)  
 [    1.270252] pci 0000:01:00.0: Boot video device  
 [    1.274027] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    1.274044] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    1.274221] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0  
 [    1.274225] ACPI: Power Button (FF) [PWRF]  
 [    1.274307] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1  
 [    1.274316] ACPI: Sleep Button (CM) [SLPB]  
 [    1.274570] processor ACPI_CPU:00: registered as cooling_device0  
 [    1.274576] ACPI: Processor [CPU1] (supports 8 throttling states)  
 [    1.274695] processor ACPI_CPU:01: registered as cooling_device1  
 [    1.274702] ACPI: Processor [CPU2] (supports 8 throttling states)  
 [    1.277089] isapnp: Scanning for PnP cards...  
 [    1.630791] isapnp: No Plug & Play device found  
 [    1.641182] Serial: 8250/16550 driver4 ports, IRQ sharing enabled  
 [    1.641280] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A  
 [    1.641683] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A  
 [    1.641837] serial 0000:03:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    1.641918] 0000:03:04.0: ttyS1 at I/O 0xb400 (irq = 18) is a 16550A  
 [    1.642943] brd: module loaded  
 [    1.643404] loop: module loaded  
 [    1.643518] Fixed MDIO Bus: probed  
 [    1.643526] PPP generic driver version 2.4.2  
 [    1.643604] input: Macintosh mouse button emulation as /devices/virtual/input/input2  
 [    1.643650] Driver 'sd' needs updating - please use bus_type methods  
 [    1.643663] Driver 'sr' needs updating - please use bus_type methods  
 [    1.643763] ata_piix 0000:00:1f.1: version 2.12  
 [    1.643772] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)  
 [    1.643779] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    1.643829] ata_piix 0000:00:1f.1: setting latency timer to 64  
 [    1.643952] scsi0 : ata_piix  
 [    1.644099] scsi1 : ata_piix  
 [    1.645728] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14  
 [    1.645733] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15  
 [    1.854125] ata1.00: ATA-7: ST3160815A, 3.AAC, max UDMA/100  
 [    1.854129] ata1.00: 312581808 sectors, multi 16: LBA48  
 [    1.920698] ata1.00: configured for UDMA/100  
 [    2.092288] ata2.00: ATAPI: ATAPI   iHAP322   8, UL14, max UDMA/66  
 [    2.092331] ata2.01: ATAPI: PLEXTOR CD-R   PX-W1210A, 1.10, max MWDMA2  
 [    2.108234] ata2.00: configured for UDMA/66  
 [    2.124280] ata2.01: configured for MWDMA2  
 [    2.125326] scsi 0:0:0:0: Direct-Access     ATA      ST3160815A       3.AA PQ: 0 ANSI: 5  
 [    2.125467] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)  
 [    2.125492] sd 0:0:0:0: [sda] Write Protect is off  
 [    2.125496] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    2.125535] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    2.125628] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)  
 [    2.125650] sd 0:0:0:0: [sda] Write Protect is off  
 [    2.125654] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    2.125693] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    2.125698]  sda: sda1 sda2 < sda5 >  
 [    2.168192] sd 0:0:0:0: [sda] Attached SCSI disk  
 [    2.168263] sd 0:0:0:0: Attached scsi generic sg0 type 0  
 [    2.169459] scsi 1:0:0:0: CD-ROM            ATAPI    iHAP322   8      UL14 PQ: 0 ANSI: 5  
 [    2.175434] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray  
 [    2.175438] Uniform CD-ROM driver Revision: 3.20  
 [    2.175579] sr 1:0:0:0: Attached scsi CD-ROM sr0  
 [    2.175641] sr 1:0:0:0: Attached scsi generic sg1 type 5  
 [    2.176480] scsi 1:0:1:0: CD-ROM            PLEXTOR  CD-R   PX-W1210A 1.10 PQ: 0 ANSI: 5  
 [    2.178712] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray  
 [    2.178808] sr 1:0:1:0: Attached scsi CD-ROM sr1  
 [    2.178866] sr 1:0:1:0: Attached scsi generic sg2 type 5  
 [    2.178894] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    2.178900] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]  
 [    2.178952] ata_piix 0000:00:1f.2: setting latency timer to 64  
 [    2.179045] scsi2 : ata_piix  
 [    2.179146] scsi3 : ata_piix  
 [    2.180172] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18  
 [    2.180177] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18  
 [    2.507710] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    2.507741] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23  
 [    2.507771] ehci_hcd 0000:00:1d.7: setting latency timer to 64  
 [    2.507776] ehci_hcd 0000:00:1d.7: EHCI Host Controller  
 [    2.507862] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1  
 [    2.511777] ehci_hcd 0000:00:1d.7: debug port 1  
 [    2.511785] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported  
 [    2.511802] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe100000  
 [    2.524014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00  
 [    2.524123] usb usb1: configuration #1 chosen from 1 choice  
 [    2.524164] hub 1-0:1.0: USB hub found  
 [    2.524177] hub 1-0:1.0: 8 ports detected  
 [    2.524346] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    2.524371] uhci_hcd: USB Universal Host Controller Interface driver  
 [    2.524414] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    2.524423] uhci_hcd 0000:00:1d.0: setting latency timer to 64  
 [    2.524428] uhci_hcd 0000:00:1d.0: UHCI Host Controller  
 [    2.524495] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2  
 [    2.524526] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00  
 [    2.524626] usb usb2: configuration #1 chosen from 1 choice  
 [    2.524664] hub 2-0:1.0: USB hub found  
 [    2.524673] hub 2-0:1.0: 2 ports detected  
 [    2.524791] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19  
 [    2.524799] uhci_hcd 0000:00:1d.1: setting latency timer to 64  
 [    2.524803] uhci_hcd 0000:00:1d.1: UHCI Host Controller  
 [    2.524866] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3  
 [    2.524895] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000  
 [    2.524989] usb usb3: configuration #1 chosen from 1 choice  
 [    2.525026] hub 3-0:1.0: USB hub found  
 [    2.525037] hub 3-0:1.0: 2 ports detected  
 [    2.525148] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18  
 [    2.525156] uhci_hcd 0000:00:1d.2: setting latency timer to 64  
 [    2.525160] uhci_hcd 0000:00:1d.2: UHCI Host Controller  
 [    2.525221] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4  
 [    2.525243] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400  
 [    2.525348] usb usb4: configuration #1 chosen from 1 choice  
 [    2.525384] hub 4-0:1.0: USB hub found  
 [    2.525394] hub 4-0:1.0: 2 ports detected  
 [    2.525507] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    2.525514] uhci_hcd 0000:00:1d.3: setting latency timer to 64  
 [    2.525518] uhci_hcd 0000:00:1d.3: UHCI Host Controller  
 [    2.525588] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5  
 [    2.525609] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800  
 [    2.525707] usb usb5: configuration #1 chosen from 1 choice  
 [    2.525743] hub 5-0:1.0: USB hub found  
 [    2.525754] hub 5-0:1.0: 2 ports detected  
 [    2.525938] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1  
 [    2.525942] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp  
 [    2.526431] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    2.528067] mice: PS/2 mouse device common for all mice  
 [    2.540087] rtc_cmos 00:02: RTC can wake from S4  
 [    2.540136] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0  
 [    2.540162] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs  
 [    2.540261] device-mapper: uevent: version 1.0.3  
 [    2.540404] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]  
 [    2.540526] device-mapper: multipath: version 1.0.5 loaded  
 [    2.540533] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    2.540653] EISA: Probing bus 0 at eisa.0  
 [    2.540694] EISA: Detected 0 cards.  
 [    2.540776] cpuidle: using governor ladder  
 [    2.540781] cpuidle: using governor menu  
 [    2.541587] TCP cubic registered  
 [    2.541687] NET: Registered protocol family 10  
 [    2.542324] lo: Disabled Privacy Extensions  
 [    2.542852] NET: Registered protocol family 17  
 [    2.542878] Bluetooth: L2CAP ver 2.11  
 [    2.542881] Bluetooth: L2CAP socket layer initialized  
 [    2.542885] Bluetooth: SCO (Voice Link) ver 0.6  
 [    2.542888] Bluetooth: SCO socket layer initialized  
 [    2.542952] Bluetooth: RFCOMM socket layer initialized  
 [    2.542968] Bluetooth: RFCOMM TTY layer initialized  
 [    2.542973] Bluetooth: RFCOMM ver 1.10  
 [    2.543049] Using IPI No-Shortcut mode  
 [    2.543168] registered taskstats version 1  
 [    2.543322]   Magic number: 5:893:183  
 [    2.543405] rtc_cmos 00:02: setting system clock to 2009-08-09 15:11:49 UTC (1249830709)  
 [    2.543409] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    2.543412] EDD information not available.  
 [    2.543837] Freeing unused kernel memory: 532k freed  
 [    2.544067] Write protecting the kernel text: 4116k  
 [    2.544146] Write protecting the kernel read-only data: 1524k  
 [    2.568390] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3  
 [    2.819940] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI  
 [    2.819945] Copyright (c) 1999-2006 Intel Corporation.  
 [    2.819997] e1000 0000:02:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    2.820008] e1000 0000:02:01.0: setting latency timer to 64  
 [    2.925156] usb 1-3: new high speed USB device using ehci_hcd and address 2  
 [    3.089237] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:07:e9:54:91:1c  
 [    3.160449] Floppy drive(s): fd0 is 1.44M  
 [    3.183857] FDC 0 is a post-1991 82077  
 [    3.561495] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection  
 [    3.932222] PM: Starting manual resume from disk  
 [    3.932227] PM: Resume from partition 8:5  
 [    3.932230] PM: Checking hibernation image.  
 [    3.932434] PM: Resume from disk failed.  
 [    3.986945] kjournald starting.  Commit interval 5 seconds  
 [    3.986957] EXT3-fs: mounted filesystem with ordered data mode.  
 [    8.934212] udev: starting version 141  
 [    9.097908] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4  
 [    9.284390] Linux agpgart interface v0.103  
 [    9.291133] agpgart-intel 0000:00:00.0: Intel i875 Chipset  
 [    9.294676] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000  
 [    9.296810] Intel 82802 RNG detected 
 [    9.362776] parport_pc 00:08: reported by Plug and Play ACPI  
 [    9.362809] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]  
 [    9.433235] input: PC Speaker as /devices/platform/pcspkr/input/input4  
 [    9.598735] EDAC MC: Ver: 2.1.0 Jul 25 2009  
 [    9.744705] iTCO_vendor_support: vendor-support=0  
 [    9.747368] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05  
 [    9.747517] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)  
 [    9.747622] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)  
 [    9.766287] EDAC i82875p: i82875p init one  
 [    9.766323] pci 0000:00:06.0: reg 10 32bit mmio: [0xfecf0000-0xfecf0fff]  
 [    9.766655] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01  
 [    9.766659] pci 0000:00:01.0:   IO window: disabled  
 [    9.766667] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff  
 [    9.766673] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000f7ffffff  
 [    9.766683] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02  
 [    9.766688] pci 0000:00:03.0:   IO window: 0xa000-0xafff  
 [    9.766695] pci 0000:00:03.0:   MEM window: 0xfe000000-0xfe0fffff  
 [    9.766701] pci 0000:00:03.0:   PREFETCH window: disabled  
 [    9.766710] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03  
 [    9.766715] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff  
 [    9.766722] pci 0000:00:1e.0:   MEM window: disabled  
 [    9.766729] pci 0000:00:1e.0:   PREFETCH window: disabled  
 [    9.767010] EDAC MC0: Giving out device to 'i82875p_edac' 'i82875p': DEV 0000:00:00.0  
 [    9.767052] EDAC PCI0: Giving out device to module 'i82875p_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)  
 [    9.774092] ppdev: user-space parallel port driver  
 [    9.780896] gameport: EMU10K1 is pci0000:03:02.1/gameport0, io 0xbc00, speed 1046kHz  
 [    9.973010] EMU10K1_Audigy 0000:03:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [   10.248713] lp0: using parport0 (interrupt-driven).  
 [   10.377873] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k  
 [   10.947085] EXT3 FS on sda1, internal journal  
 [   12.190321] type=1505 audit(1249830719.144:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1947  
 [   12.248818] type=1505 audit(1249830719.204:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1951  
 [   12.248981] type=1505 audit(1249830719.204:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1951  
 [   12.249055] type=1505 audit(1249830719.204:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1951  
 [   12.249111] type=1505 audit(1249830719.204:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1951  
 [   12.406720] type=1505 audit(1249830719.360:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1956  
 [   12.406933] type=1505 audit(1249830719.360:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1956  
 [   12.443548] type=1505 audit(1249830719.396:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1960 
 [   15.037476] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  
 [   15.037484] Bluetooth: BNEP filters: protocol multicast  
 [   15.059899] Bridge firewalling registered  
 [   18.036020] usb 1-3: device descriptor read/64, error -110  
 [   33.252019] usb 1-3: device descriptor read/64, error -110  
 [   33.468018] usb 1-3: new high speed USB device using ehci_hcd and address 3  
 [   48.580020] usb 1-3: device descriptor read/64, error -110  
 [   63.796019] usb 1-3: device descriptor read/64, error -110  
 [   64.012017] usb 1-3: new high speed USB device using ehci_hcd and address 4  
 [   69.032056] usb 1-3: device descriptor read/8, error -110  
 [   74.152056] usb 1-3: device descriptor read/8, error -110  
 [   74.368018] usb 1-3: new high speed USB device using ehci_hcd and address 5  
 [   79.388172] usb 1-3: device descriptor read/8, error -110  
 [   84.508176] usb 1-3: device descriptor read/8, error -110  
 [   84.612028] hub 1-0:1.0: unable to enumerate USB device on port 3  
 [   84.748017] usb 1-4: new high speed USB device using ehci_hcd and address 6  
 [   84.881940] usb 1-4: configuration #1 chosen from 1 choice  
 [   85.176017] usb 3-1: new full speed USB device using uhci_hcd and address 2  
 [  100.288018] usb 3-1: device descriptor read/64, error -110  
 [  115.504017] usb 3-1: device descriptor read/64, error -110  
 [  115.720027] usb 3-1: new full speed USB device using uhci_hcd and address 3  
 [  130.832017] usb 3-1: device descriptor read/64, error -110  
 [  146.048019] usb 3-1: device descriptor read/64, error -110  
 [  146.264016] usb 3-1: new full speed USB device using uhci_hcd and address 4  
 [  151.285351] usb 3-1: device descriptor read/8, error -110  
 [  156.405606] usb 3-1: device descriptor read/8, error -110  
 [  156.620016] usb 3-1: new full speed USB device using uhci_hcd and address 5  
 [  161.641845] usb 3-1: device descriptor read/8, error -110  
 [  166.761099] usb 3-1: device descriptor read/8, error -110  
 [  166.864024] hub 3-0:1.0: unable to enumerate USB device on port 1  
 [  167.104028] usb 4-1: new low speed USB device using uhci_hcd and address 2  
 [  167.287262] usb 4-1: configuration #1 chosen from 1 choice  
 [  167.484783] usbcore: registered new interface driver hiddev  
 [  167.500875] input: Microsoft Microsoft IntelliMouse&#65533; Explorer as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input5  
 [  167.502901] generic-usb 0003:045E:001E.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse&#65533; Explorer] on usb-0000:00:1d.2-1/input0  
 [  167.502939] usbcore: registered new interface driver usbhid  
 [  167.502947] usbhid: v2.6:USB HID core driver  
 [  172.045031] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [  172.048433] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX  
 [  172.049515] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready  
 [  182.500012] eth0: no IPv6 routers present  
 jcarr911
```

---

