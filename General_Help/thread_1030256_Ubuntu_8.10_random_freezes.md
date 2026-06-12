---
title: "Ubuntu 8.10 random freezes"
date: 2009-01-04
forum: General Help
---

### Post by K.Morgan on 2009-01-04
I have installed Ubuntu 8.10 on my PC running on a M2N-MX SE motherboard which has the Nvidia nforce 430/GeForce 6100 chipset.  Everything installed fine and once up and running i was presented with installing the Nvidia drivers and everything ran smoothly.  But every now and again in completely random time-frames my computer will freeze and there's nothing that can be done apart from turning the power off.

Sometimes this will happen after just a few minutes of booting up or it could be fine for a couple of hours.  I'm really struggling to figure out what it could be, I've gone back to a previous kernel and updated the kernel and have the same problem.

I'm also using the infamous Netgear WG111v2 wireless adapter which doesn't work unless i use the ndiswrapper driver so not sure if it could be the wireless that's causing the problem and if it is how can i sort this out as Ubuntu 8.04 seemed to recognize this adapter without having to use ndiswrapper.

---

### Post by Piro24 on 2009-01-04
Does the same thing happen when you are working purely in a console? For example, start up your system, but don't run any X scripts at all. No graphical login, No GNOME/KDE/XFCE , just a command line.

Try using the computer from there, and if no problems occur, then it is probably a problem with your graphics card/driver, or with your desktop enviroment. Try turning all your desktop effects down to none as well. That might help.

I don't think it would be your network driver, though I am unfamiliar with the NetgearWG111v2's errors and such.

---

### Post by K.Morgan on 2009-01-04
I'm not sure about running in console as i wouldn't know what to do in that environment anyway, but i have tried running with no desktop effects at all and keep getting the same problem

---

### Post by linux_tech on 2009-01-04
What are your system specs?

Try posting output of ```
dmesg
``` after the next crash

If your system crashes, its usually best to go to minimal setup as possible and add back components one at a time until you find the cause

A few suggestions-

Use top to check processes running

use memtest86; run at start up, see if there are any errors 

try different drivers if possible for wireless and video; reload drivers;
Is there a different video driver available?

Have you run Hardy OS updates recently?

---

### Post by K.Morgan on 2009-01-04
There are 3 Nvidia drivers available iv'e tried the 177 version which says recommended  but still freezes, tried the 173 version still the same so now on the 96 version.  There's No other wireless drivers that work apart from the ndiswrapper.

Here's output of dmesg:

```

[    0.000000] Detected 2209.982 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1803404k/1834752k available (2576k kernel code, 29956k reserved, 1165k data, 424k init, 917248k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4419.96 BogoMIPS (lpj=8839928)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(2) -> Core 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017464] ACPI: Core revision 20080609
[    0.019343] ACPI: Checking initramfs for custom DSDT
[    0.327279] ACPI: setting ELCR to 0200 (from 8c00)
[    0.327649] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.328020] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4420.03 BogoMIPS (lpj=8840070)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.412209] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.412235] Brought up 2 CPUs
[    0.412237] Total of 2 processors activated (8839.99 BogoMIPS).
[    0.412249] CPU0 attaching sched-domain:
[    0.412252]  domain 0: span 0-1 level CPU
[    0.412255]   groups: 0 1
[    0.412261] CPU1 attaching sched-domain:
[    0.412263]  domain 0: span 0-1 level CPU
[    0.412265]   groups: 1 0
[    0.412322] net_namespace: 840 bytes
[    0.412322] Booting paravirtualized kernel on bare hardware
[    0.412322] Time: 15:22:45  Date: 01/04/09
[    0.412322] NET: Registered protocol family 16
[    0.412322] EISA bus registered
[    0.412322] ACPI: bus type pci registered
[    0.412322] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.412322] PCI: Not using MMCONFIG.
[    0.412631] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.412634] PCI: Using configuration type 1 for base access
[    0.412891] ACPI: EC: Look up EC in DSDT
[    0.428145] ACPI: Interpreter enabled
[    0.428149] ACPI: (supports S0 S1 S3 S4 S5)
[    0.428166] ACPI: Using PIC for interrupt routing
[    0.428225] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.435792] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.435794] PCI: Using MMCONFIG for extended config space
[    0.448230] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.448230] PCI: 0000:00:01.1 reg 10 io port: [ec00, ec3f]
[    0.448230] PCI: 0000:00:01.1 reg 20 io port: [600, 63f]
[    0.448230] PCI: 0000:00:01.1 reg 24 io port: [700, 73f]
[    0.448230] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.448230] pci 0000:00:01.1: PME# disabled
[    0.448267] PCI: 0000:00:02.0 reg 10 32bit mmio: [dffff000, dfffffff]
[    0.448287] pci 0000:00:02.0: supports D1
[    0.448289] pci 0000:00:02.0: supports D2
[    0.448291] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448294] pci 0000:00:02.0: PME# disabled
[    0.448314] PCI: 0000:00:02.1 reg 10 32bit mmio: [dfffec00, dfffecff]
[    0.448337] pci 0000:00:02.1: supports D1
[    0.448338] pci 0000:00:02.1: supports D2
[    0.448340] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448344] pci 0000:00:02.1: PME# disabled
[    0.448393] PCI: 0000:00:05.0 reg 10 32bit mmio: [dfff8000, dfffbfff]
[    0.448416] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.448419] pci 0000:00:05.0: PME# disabled
[    0.448447] PCI: 0000:00:06.0 reg 20 io port: [ffa0, ffaf]
[    0.448480] PCI: 0000:00:07.0 reg 10 32bit mmio: [dfffd000, dfffdfff]
[    0.448484] PCI: 0000:00:07.0 reg 14 io port: [e480, e487]
[    0.448502] pci 0000:00:07.0: supports D1
[    0.448504] pci 0000:00:07.0: supports D2
[    0.448506] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448510] pci 0000:00:07.0: PME# disabled
[    0.448526] PCI: 0000:00:08.0 reg 10 io port: [e400, e407]
[    0.448530] PCI: 0000:00:08.0 reg 14 io port: [e080, e083]
[    0.448534] PCI: 0000:00:08.0 reg 18 io port: [e000, e007]
[    0.448537] PCI: 0000:00:08.0 reg 1c io port: [dc00, dc03]
[    0.448541] PCI: 0000:00:08.0 reg 20 io port: [d880, d88f]
[    0.448545] PCI: 0000:00:08.0 reg 24 32bit mmio: [dfffc000, dfffcfff]
[    0.448584] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448586] pci 0000:00:09.0: PME# disabled
[    0.448610] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448613] pci 0000:00:0b.0: PME# disabled
[    0.448636] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448639] pci 0000:00:0c.0: PME# disabled
[    0.448651] PCI: 0000:00:0d.0 reg 10 32bit mmio: [de000000, deffffff]
[    0.448656] PCI: 0000:00:0d.0 reg 14 64bit mmio: [c0000000, cfffffff]
[    0.448661] PCI: 0000:00:0d.0 reg 1c 64bit mmio: [dd000000, ddffffff]
[    0.448666] PCI: 0000:00:0d.0 reg 30 32bit mmio: [dffc0000, dffdffff]
[    0.448773] pci 0000:00:04.0: transparent bridge
[    0.448888] bus 00 -> node 0
[    0.448894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.449171] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.449336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.449463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.449590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.456490] ACPI: PCI Interrupt Link [LNKA] (IRQs 7 10 11 14) *0, disabled.
[    0.460104] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 10 11 14) *0, disabled.
[    0.460335] ACPI: PCI Interrupt Link [LNKC] (IRQs 7 10 11 14) *0, disabled.
[    0.460567] ACPI: PCI Interrupt Link [LNKD] (IRQs 7 10 11 14) *0, disabled.
[    0.460798] ACPI: PCI Interrupt Link [LNEA] (IRQs 7 10 11 14) *0, disabled.
[    0.461029] ACPI: PCI Interrupt Link [LNEB] (IRQs 7 10 11 14) *0, disabled.
[    0.461261] ACPI: PCI Interrupt Link [LNEC] (IRQs 7 10 11 14) *0, disabled.
[    0.461493] ACPI: PCI Interrupt Link [LNED] (IRQs 7 10 11 14) *0, disabled.
[    0.461724] ACPI: PCI Interrupt Link [LUB0] (IRQs 7 10 *11 14)
[    0.461955] ACPI: PCI Interrupt Link [LUB2] (IRQs 7 *10 11 14)
[    0.462186] ACPI: PCI Interrupt Link [LMAC] (IRQs 7 10 *11 14)
[    0.462416] ACPI: PCI Interrupt Link [LAZA] (IRQs 7 10 *11 14)
[    0.462648] ACPI: PCI Interrupt Link [LACI] (IRQs 7 10 11 14) *0, disabled.
[    0.462880] ACPI: PCI Interrupt Link [LMC9] (IRQs 7 10 *11 14)
[    0.463110] ACPI: PCI Interrupt Link [LSMB] (IRQs 7 *10 11 14)
[    0.463341] ACPI: PCI Interrupt Link [LPMU] (IRQs 7 10 11 14) *0, disabled.
[    0.463573] ACPI: PCI Interrupt Link [LSA0] (IRQs *15)
[    0.463803] ACPI: PCI Interrupt Link [LSA1] (IRQs 5) *0, disabled.
[    0.464091] ACPI: PCI Interrupt Link [LATA] (IRQs 7 10 11 14) *0, disabled.
[    0.464152] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 20, should be 13 [20080609]
[    0.464152] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.464152] pnp: PnP ACPI init
[    0.464152] ACPI: bus type pnp registered
[    0.473020] pnp: PnP ACPI: found 16 devices
[    0.473023] ACPI: ACPI bus type pnp unregistered
[    0.473026] PnPBIOS: Disabled by ACPI PNP
[    0.473043] PCI: Using ACPI for IRQ routing
[    0.480040] NET: Registered protocol family 8
[    0.480042] NET: Registered protocol family 20
[    0.480062] NetLabel: Initializing
[    0.480064] NetLabel:  domain hash size = 128
[    0.480066] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.480079] NetLabel:  unlabeled traffic allowed by default
[    0.480087] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.480092] hpet0: 3 32-bit timers, 25000000 Hz
[    0.481671] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.481673]    actual entries 65620
[    0.481809] AppArmor: AppArmor Filesystem Enabled
[    0.481835] ACPI: RTC can wake from S4
[    0.484044] Switched to high resolution mode on CPU 0
[    0.484251] Switched to high resolution mode on CPU 1
[    0.488046] system 00:07: ioport range 0xa30-0xa37 has been reserved
[    0.488049] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.488052] system 00:07: ioport range 0x800-0x80f has been reserved
[    0.488055] system 00:07: ioport range 0x500-0x57f has been reserved
[    0.488058] system 00:07: ioport range 0x580-0x5ff has been reserved
[    0.488061] system 00:07: ioport range 0x800-0x87f could not be reserved
[    0.488064] system 00:07: ioport range 0x880-0x8ff has been reserved
[    0.488067] system 00:07: ioport range 0xd00-0xd7f has been reserved
[    0.488069] system 00:07: ioport range 0xd80-0xdff has been reserved
[    0.488072] system 00:07: ioport range 0x2000-0x207f has been reserved
[    0.488075] system 00:07: ioport range 0x2080-0x20ff has been reserved
[    0.488079] system 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.488082] system 00:07: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.488085] system 00:07: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.488088] system 00:07: iomem range 0xffb80000-0xffffffff could not be reserved
[    0.488091] system 00:07: iomem range 0xff300000-0xff3fffff has been reserved
[    0.488099] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.488102] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.488105] system 00:09: iomem range 0x70000000-0x7fffffff has been reserved
[    0.488112] system 00:0c: ioport range 0x230-0x23f has been reserved
[    0.488115] system 00:0c: ioport range 0x290-0x29f has been reserved
[    0.488118] system 00:0c: ioport range 0xa00-0xa0f has been reserved
[    0.488121] system 00:0c: ioport range 0xa10-0xa1f has been reserved
[    0.488127] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    0.488132] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.488135] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
[    0.488138] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.488141] system 00:0f: iomem range 0x100000-0x6fffffff could not be reserved
[    0.488144] system 00:0f: iomem range 0xff780000-0xffffffff could not be reserved
[    0.523365] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.523367] pci 0000:00:04.0:   IO window: disabled
[    0.523371] pci 0000:00:04.0:   MEM window: disabled
[    0.523374] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.523378] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.523380] pci 0000:00:09.0:   IO window: disabled
[    0.523383] pci 0000:00:09.0:   MEM window: disabled
[    0.523385] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.523389] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.523391] pci 0000:00:0b.0:   IO window: disabled
[    0.523393] pci 0000:00:0b.0:   MEM window: disabled
[    0.523396] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.523399] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.523401] pci 0000:00:0c.0:   IO window: disabled
[    0.523404] pci 0000:00:0c.0:   MEM window: disabled
[    0.523407] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.523415] pci 0000:00:04.0: setting latency timer to 64
[    0.523421] pci 0000:00:09.0: setting latency timer to 64
[    0.523425] pci 0000:00:0b.0: setting latency timer to 64
[    0.523429] pci 0000:00:0c.0: setting latency timer to 64
[    0.523432] bus: 00 index 0 io port: [0, ffff]
[    0.523435] bus: 00 index 1 mmio: [0, ffffffff]
[    0.523437] bus: 01 index 0 mmio: [0, 0]
[    0.523439] bus: 01 index 1 mmio: [0, 0]
[    0.523441] bus: 01 index 2 mmio: [0, 0]
[    0.523443] bus: 01 index 3 io port: [0, ffff]
[    0.523445] bus: 01 index 4 mmio: [0, ffffffff]
[    0.523447] bus: 02 index 0 mmio: [0, 0]
[    0.523449] bus: 02 index 1 mmio: [0, 0]
[    0.523451] bus: 02 index 2 mmio: [0, 0]
[    0.523453] bus: 02 index 3 mmio: [0, 0]
[    0.523454] bus: 03 index 0 mmio: [0, 0]
[    0.523456] bus: 03 index 1 mmio: [0, 0]
[    0.523458] bus: 03 index 2 mmio: [0, 0]
[    0.523460] bus: 03 index 3 mmio: [0, 0]
[    0.523462] bus: 04 index 0 mmio: [0, 0]
[    0.523463] bus: 04 index 1 mmio: [0, 0]
[    0.523465] bus: 04 index 2 mmio: [0, 0]
[    0.523467] bus: 04 index 3 mmio: [0, 0]
[    0.523478] NET: Registered protocol family 2
[    0.536056] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.536332] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.536996] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.537340] TCP: Hash tables configured (established 131072 bind 65536)
[    0.537344] TCP reno registered
[    0.544086] NET: Registered protocol family 1
[    0.544207] checking if image is initramfs... it is
[    1.177704] Freeing initrd memory: 8009k freed
[    1.178655] audit: initializing netlink socket (disabled)
[    1.178675] type=2000 audit(1231082565.177:1): initialized
[    1.184177] highmem bounce pool size: 64 pages
[    1.184183] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.186713] VFS: Disk quotas dquot_6.5.1
[    1.186800] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.186901] msgmni has been set to 1748
[    1.187018] io scheduler noop registered
[    1.187020] io scheduler anticipatory registered
[    1.187022] io scheduler deadline registered
[    1.187033] io scheduler cfq registered (default)
[    1.187065] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.610737] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.610753] pci 0000:00:05.0: Enabling HT MSI Mapping
[    1.610779] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.610794] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.610808] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.610823] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.610838] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.610852] pci 0000:00:0d.0: Boot video device
[    1.610958] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.610981] pcieport-driver 0000:00:09.0: found MSI capability
[    1.611002] pci_express 0000:00:09.0:pcie00: allocate port service
[    1.611046] pci_express 0000:00:09.0:pcie03: allocate port service
[    1.611121] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.611142] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.611158] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.611198] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.611275] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.611297] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.611313] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.611353] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.611663] isapnp: Scanning for PnP cards...
[    1.965074] isapnp: No Plug & Play device found
[    1.999671] hpet_resources: 0xfed00000 is busy
[    1.999763] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.999890] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.000586] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.002470] brd: module loaded
[    2.002541] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.002666] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.003067] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.003072] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.003381] mice: PS/2 mouse device common for all mice
[    2.003509] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.003538] rtc0: alarms up to one year, y3k, hpet irqs
[    2.003672] EISA: Probing bus 0 at eisa.0
[    2.003681] Cannot allocate resource for EISA slot 2
[    2.003697] EISA: Detected 0 cards.
[    2.003701] cpuidle: using governor ladder
[    2.003703] cpuidle: using governor menu
[    2.004193] TCP cubic registered
[    2.004219] Using IPI No-Shortcut mode
[    2.004406] registered taskstats version 1
[    2.004522]   Magic number: 9:680:385
[    2.004721] rtc_cmos 00:02: setting system clock to 2009-01-04 15:22:46 UTC (1231082566)
[    2.004725] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.004727] EDD information not available.
[    2.005022] Freeing unused kernel memory: 424k freed
[    2.005080] Write protecting the kernel text: 2580k
[    2.005117] Write protecting the kernel read-only data: 940k
[    2.023627] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.163290] fuse init (API version 7.9)
[    2.239405] processor ACPI0007:00: registered as cooling_device0
[    2.239468] processor ACPI0007:01: registered as cooling_device1
[    2.597572] usbcore: registered new interface driver usbfs
[    2.597599] usbcore: registered new interface driver hub
[    2.597634] usbcore: registered new device driver usb
[    2.643045] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.643404] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 11
[    2.643407] PCI: setting IRQ 11 as level-triggered
[    2.643412] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 11 (level, low) -> IRQ 11
[    2.643426] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.643429] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.643484] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.643501] ohci_hcd 0000:00:02.0: irq 11, io mem 0xdffff000
[    2.657591] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.659514] No dock devices found.
[    2.707159] usb usb1: configuration #1 chosen from 1 choice
[    2.707185] hub 1-0:1.0: USB hub found
[    2.707195] hub 1-0:1.0: 8 ports detected
[    2.734926] SCSI subsystem initialized
[    2.829409] libata version 3.00 loaded.
[    2.913648] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 10
[    2.913652] PCI: setting IRQ 10 as level-triggered
[    2.913657] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 10 (level, low) -> IRQ 10
[    2.913671] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.913674] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.913698] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    2.913726] ehci_hcd 0000:00:02.1: debug port 1
[    2.913730] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.913740] ehci_hcd 0000:00:02.1: irq 10, io mem 0xdfffec00
[    2.925040] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.925198] usb usb2: configuration #1 chosen from 1 choice
[    2.925230] hub 2-0:1.0: USB hub found
[    2.925239] hub 2-0:1.0: 8 ports detected
[    3.132230] pata_amd 0000:00:06.0: version 0.3.10
[    3.132276] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.132345] scsi0 : pata_amd
[    3.132426] scsi1 : pata_amd
[    3.133222] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.133224] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.245017] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    3.305286] ata1.01: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB06, max UDMA/33
[    3.305301] ata1: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc00000) ACPI=0x701f (900:60:0x14)
[    3.320227] ata1.01: configured for UDMA/33
[    3.320251] ata2: port disabled. ignoring.
[    3.321183] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB06 PQ: 0 ANSI: 5
[    3.321300] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.321628] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 11
[    3.321632] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 11 (level, low) -> IRQ 11
[    3.321636] forcedeth 0000:00:07.0: setting latency timer to 64
[    3.381535] usb 2-3: configuration #1 chosen from 1 choice
[    3.840512] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x1374 @ 1, addr 00:1b:fc:34:19:52
[    3.840516] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[    3.840877] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 15
[    3.840880] PCI: setting IRQ 15 as level-triggered
[    3.840884] pata_acpi 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 15 (level, low) -> IRQ 15
[    3.840915] pata_acpi 0000:00:08.0: setting latency timer to 64
[    3.840927] pata_acpi 0000:00:08.0: PCI INT A disabled
[    3.848740] sata_nv 0000:00:08.0: version 3.5
[    3.848754] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 15 (level, low) -> IRQ 15
[    3.848789] sata_nv 0000:00:08.0: setting latency timer to 64
[    3.848837] scsi2 : sata_nv
[    3.848911] scsi3 : sata_nv
[    3.849105] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 15
[    3.849109] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 15
[    3.857437] scsi 0:0:1:0: Attached scsi generic sg0 type 5
[    3.877115] Driver 'sr' needs updating - please use bus_type methods
[    3.883694] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.883700] Uniform CD-ROM driver Revision: 3.20
[    3.883789] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    4.628034] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.636224] ata4.00: ATA-7: ST3250310AS, 3.AAF, max UDMA/133
[    4.636227] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.652223] ata4.00: configured for UDMA/133
[    4.652323] scsi 3:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[    4.652482] scsi 3:0:0:0: Attached scsi generic sg1 type 0
[    4.671543] Driver 'sd' needs updating - please use bus_type methods
[    4.671649] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.671665] sd 3:0:0:0: [sda] Write Protect is off
[    4.671668] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.671691] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.671750] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.671762] sd 3:0:0:0: [sda] Write Protect is off
[    4.671765] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.671785] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.671789]  sda: sda1 sda2 < sda5 > sda3
[    4.713159] sd 3:0:0:0: [sda] Attached SCSI disk
[    4.905679] PM: Starting manual resume from disk
[    4.905683] PM: Resume from partition 8:5
[    4.905685] PM: Checking hibernation image.
[    4.905830] PM: Resume from disk failed.
[    4.954386] kjournald starting.  Commit interval 5 seconds
[    4.954398] EXT3-fs: mounted filesystem with ordered data mode.
[    9.357861] udevd version 124 started
[    9.861125] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    9.933157] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.097729] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[   10.097786] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[   10.123132] Linux agpgart interface v0.103
[   10.183202] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   10.208028] ACPI: Power Button (FF) [PWRF]
[   10.208133] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   10.240035] ACPI: Power Button (CM) [PWRB]
[   10.332355] nvidia: module license 'NVIDIA' taints kernel.
[   10.712323] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 11
[   10.712329] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 11 (level, low) -> IRQ 11
[   10.712335] nvidia 0000:00:0d.0: setting latency timer to 64
[   10.712596] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.09  Mon Oct 27 14:23:30 PST 2008
[   10.721606] parport_pc 00:06: reported by Plug and Play ACPI
[   10.721651] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.912641] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   11.074217] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   11.164025] usb 2-3: reset high speed USB device using ehci_hcd and address 2
[   11.406826] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 11
[   11.406832] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 11 (level, low) -> IRQ 11
[   11.406850] HDA Intel 0000:00:05.0: setting latency timer to 64
[   11.425399] ndiswrapper: driver net111v2 (NETGEAR Inc.,3/16/2006,5.1213.06.0316) loaded
[   11.516743] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   14.580361] wlan0: ethernet device 00:18:4d:b5:49:14 using NDIS driver: net111v2, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:6A00.F.conf
[   14.580385] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   14.580420] usbcore: registered new interface driver ndiswrapper
[   15.336260] lp0: using parport0 (interrupt-driven).
[   15.439367] Adding 5686968k swap on /dev/sda5.  Priority:-1 extents:1 across:5686968k
[   15.989779] EXT3 FS on sda3, internal journal
[   16.921021] type=1505 audit(1231082581.699:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4058
[   17.111947] type=1505 audit(1231082581.887:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4063
[   17.112167] type=1505 audit(1231082581.891:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4063
[   17.257064] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.739315] ACPI: WMI: Mapper loaded
[   18.041969] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
[   18.042022] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xe
[   18.042025] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x10
[   18.042028] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
[   18.042030] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   18.756529] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.848178] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   18.848186] apm: disabled - APM is not SMP safe.
[   19.079863] ppdev: user-space parallel port driver
[   21.570656] Bluetooth: Core ver 2.13
[   21.571370] NET: Registered protocol family 31
[   21.571373] Bluetooth: HCI device and connection manager initialized
[   21.571377] Bluetooth: HCI socket layer initialized
[   21.599930] Bluetooth: L2CAP ver 2.11
[   21.599935] Bluetooth: L2CAP socket layer initialized
[   21.629139] Bluetooth: SCO (Voice Link) ver 0.6
[   21.629145] Bluetooth: SCO socket layer initialized
[   21.653615] Bluetooth: RFCOMM socket layer initialized
[   21.653633] Bluetooth: RFCOMM TTY layer initialized
[   21.653635] Bluetooth: RFCOMM ver 1.10
[   21.659525] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.659532] Bluetooth: BNEP filters: protocol multicast
[   21.703617] Bridge firewalling registered
[   22.500015] Clocksource tsc unstable (delta = -91512539 ns)
[   25.805310] eth0: no link during initialization.
[   25.954089] NET: Registered protocol family 17
[  114.324635] ppdev0: registered pardevice
[  114.372386] ppdev0: unregistered pardevice
[  116.581484] ppdev0: registered pardevice
[  116.632221] ppdev0: unregistered pardevice
[  118.821221] ppdev0: registered pardevice
[  118.868058] ppdev0: unregistered pardevice

```

---

