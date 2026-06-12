---
title: "fsck has multiple inode erros, new HDs, both on 8.10 and 8.04"
date: 2009-01-07
forum: General Help
---

### Post by tomthumb99 on 2009-01-07
I am new to Linux, but old hack at PC HW. I have a dual/triple boot HP pavilion a1610 using GRUB (OS: win xp, ubuntu 8.04 AMD64, 8.10 AMD64) with 3 HDs (2-SATA, 1-IDE).  All the OS boot and come up (ie: past hard lessons with GRUB). My HDs are all new and fs errors occur on all three drives under ubuntu,with both version. I getting a large amount of inode iblock errors. On my 8.10 install on partition /dev/sda2, the full OS is under this single /-root partition (IDE hd).  Please advise on next steps...

More details -- I am finding that after some I/O disk activity or half way thru a apk-get/dpkg  install, the /-root fs remounts and becomes ro and then must manually reboot.   Upon reboot, I need choose GRUB recover option and run fsck manually on ro mount partition 'fskc -t exte -c /dev/sda2' at times the system auto restarts e2fsck command again. I get a large amount of errors duing fsck. My Win XP OS is fine, able to install all software needed. 
 
ACTIONS TAKEN:
a) I installed a new IDE drive to get round ubuntu error report on the SATA drives, it helped, triple boot process and GRUB is now working.  
b) Moved the 8.10 swap partition onto the the IDE drive. Adjusted - did not fix
c) found that the fstab had swap and /-root partitions crossed (ran CD-live install multiple time in past). The ext3 /-root partition '/dev/sda2' was listed to be mount a swap. Adjusted - did not fix. 
d) installed smartmontools, ran 'smartctl -t long /dev/sda', and the  result -->  === START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
e) Did not run badblocks, but ran fsck multiple times with -c option on /dev/sda2 partition, the 'dumpe2fs -b /dev/sda2' output was empty 

NIVIDA POINTS
- Loaded new Nivida drivers on XP side ( have GeForce 7600 GT,  and Nivida SATS chip set on motherboard)
- ubuntu GeForce 7600 GT diver install is good, dual screen work fine, even under X-windows

SOME QUESTIONS
- AMD CPUs are 64 bit, 3 Gigs RAM is 64 bit, Nivida PCI bridge & SATA controller is 32 bit -- Is this problem?
- not using UIDD names, but still  /dev/sda, /dev/sdb, /dev/sdc drive name -- Is this problem?

==== dmsg listing w/ errors at bottom ====

[    0.004036] Security Framework initialized
[    0.004044] SELinux:  Disabled at boot.
[    0.004061] AppArmor: AppArmor initialized
[    0.004435] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.007564] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008929] Mount-cache hash table entries: 256
[    0.009119] Initializing cgroup subsys ns
[    0.009122] Initializing cgroup subsys cpuacct
[    0.009125] Initializing cgroup subsys memory
[    0.009139] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.009141] CPU: L2 Cache: 512K (64 bytes/line)
[    0.009143] CPU 0/0 -> Node 0
[    0.009145] tseg: 00bff00000
[    0.009147] CPU: Physical Processor ID: 0
[    0.009148] CPU: Processor Core ID: 0
[    0.009156] using C1E aware idle routine
[    0.010451] ACPI: Core revision 20080609
[    0.012861] ACPI: Checking initramfs for custom DSDT
[    0.336658] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.344021] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.344021] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.344021] ..... (found apic 0 pin 0) ...
[    0.352022] ....... failed.
[    0.352022] ...trying to set up timer as Virtual Wire IRQ...
[    0.352022] ..... failed.
[    0.352022] ...trying to set up timer as ExtINT IRQ...
[    0.395490] ..... works.
[    0.395492] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.395496] Using local APIC timer interrupts.
[    0.396027] APIC timer calibration result 12525838
[    0.396028] Detected 12.525 MHz APIC timer.
[    0.396203] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.452028] Calibrating delay using timer specific routine.. 4409.19 BogoMIPS (lpj=8818398)
[    0.452028] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.452028] CPU: L2 Cache: 512K (64 bytes/line)
[    0.452028] CPU 1/1 -> Node 0
[    0.452028] CPU: Physical Processor ID: 0
[    0.452028] CPU: Processor Core ID: 1
[    0.484159] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.484181] Brought up 2 CPUs
[    0.484183] Total of 2 processors activated (8818.28 BogoMIPS).
[    0.484279] CPU0 attaching sched-domain:
[    0.484282]  domain 0: span 0-1 level CPU
[    0.484285]   groups: 0 1
[    0.484289]   domain 1: span 0-1 level NODE
[    0.484291]    groups: 0-1
[    0.484296] CPU1 attaching sched-domain:
[    0.484297]  domain 0: span 0-1 level CPU
[    0.484299]   groups: 1 0
[    0.484302]   domain 1: span 0-1 level NODE
[    0.484304]    groups: 0-1
[    0.484393] net_namespace: 1552 bytes
[    0.484393] Booting paravirtualized kernel on bare hardware
[    0.484393] Time: 14:02:11  Date: 01/07/09
[    0.484400] NET: Registered protocol family 16
[    0.484424] node 0 link 0: io port [1000, ffff]
[    0.484424] TOM: 00000000c0000000 aka 3072M
[    0.484424] node 0 link 0: mmio [a0000, bffff]
[    0.484424] node 0 link 0: mmio [c0000000, efffffff]
[    0.484424] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.484424] node 0 link 0: mmio [f0000000, f03fffff]
[    0.484424] bus: [00,03] on node 0 link 0
[    0.484424] bus: 00 index 0 io port: [0, ffff]
[    0.484424] bus: 00 index 1 mmio: [a0000, bffff]
[    0.484424] bus: 00 index 2 mmio: [c0000000, f3ffffff]
[    0.484424] bus: 00 index 3 mmio: [f4000000, fcffffffff]
[    0.484424] ACPI: bus type pci registered
[    0.484424] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.484424] PCI: MCFG area at f0000000 reserved in E820
[    0.488283] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.488285] PCI: Using configuration type 1 for base access
[    0.489119] ACPI: EC: Look up EC in DSDT
[    0.501981] ACPI: Interpreter enabled
[    0.501984] ACPI: (supports S0 S1 S3 S4 S5)
[    0.502002] ACPI: Using IOAPIC for interrupt routing
[    0.513314] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.516080] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516084] pci 0000:00:02.0: PME# disabled
[    0.516109] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516111] pci 0000:00:04.0: PME# disabled
[    0.516277] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.516318] PCI: 0000:00:0a.1 reg 20 io port: [4c00, 4c3f]
[    0.516324] PCI: 0000:00:0a.1 reg 24 io port: [4c40, 4c7f]
[    0.516342] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.516347] pci 0000:00:0a.1: PME# disabled
[    0.516405] PCI: 0000:00:0b.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    0.516430] pci 0000:00:0b.0: supports D1
[    0.516432] pci 0000:00:0b.0: supports D2
[    0.516434] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516437] pci 0000:00:0b.0: PME# disabled
[    0.516459] PCI: 0000:00:0b.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
[    0.516486] pci 0000:00:0b.1: supports D1
[    0.516487] pci 0000:00:0b.1: supports D2
[    0.516489] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516492] pci 0000:00:0b.1: PME# disabled
[    0.516525] PCI: 0000:00:0d.0 reg 20 io port: [f400, f40f]
[    0.516564] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.516569] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.516573] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.516577] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.516582] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]
[    0.516586] PCI: 0000:00:0e.0 reg 24 32bit mmio: [fe02d000, fe02dfff]
[    0.516623] PCI: 0000:00:0f.0 reg 10 io port: [9e0, 9e7]
[    0.516627] PCI: 0000:00:0f.0 reg 14 io port: [be0, be3]
[    0.516632] PCI: 0000:00:0f.0 reg 18 io port: [960, 967]
[    0.516636] PCI: 0000:00:0f.0 reg 1c io port: [b60, b63]
[    0.516640] PCI: 0000:00:0f.0 reg 20 io port: [cc00, cc0f]
[    0.516645] PCI: 0000:00:0f.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
[    0.516713] PCI: 0000:00:10.1 reg 10 32bit mmio: [fe024000, fe027fff]
[    0.516741] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.516745] pci 0000:00:10.1: PME# disabled
[    0.516770] PCI: 0000:00:14.0 reg 10 32bit mmio: [fe02b000, fe02bfff]
[    0.516775] PCI: 0000:00:14.0 reg 14 io port: [c800, c807]
[    0.516796] pci 0000:00:14.0: supports D1
[    0.516797] pci 0000:00:14.0: supports D2
[    0.516799] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516802] pci 0000:00:14.0: PME# disabled
[    0.516910] PCI: bridge 0000:00:02.0 io port: [b000, bfff]
[    0.516912] PCI: bridge 0000:00:02.0 32bit mmio: [fdb00000, fdbfffff]
[    0.516916] PCI: bridge 0000:00:02.0 64bit mmio pref: [fdc00000, fdcfffff]
[    0.516937] PCI: 0000:02:00.0 reg 10 32bit mmio: [fa000000, faffffff]
[    0.516942] PCI: 0000:02:00.0 reg 14 32bit mmio: [e0000000, efffffff]
[    0.516951] PCI: 0000:02:00.0 reg 1c 64bit mmio: [fb000000, fbffffff]
[    0.516955] PCI: 0000:02:00.0 reg 24 io port: [9c00, 9c7f]
[    0.516959] PCI: 0000:02:00.0 reg 30 32bit mmio: [fcfe0000, fcffffff]
[    0.517002] PCI: bridge 0000:00:04.0 io port: [9000, 9fff]
[    0.517004] PCI: bridge 0000:00:04.0 32bit mmio: [fa000000, fcffffff]
[    0.517008] PCI: bridge 0000:00:04.0 64bit mmio pref: [e0000000, efffffff]
[    0.517045] pci 0000:00:10.0: transparent bridge
[    0.517048] PCI: bridge 0000:00:10.0 io port: [a000, afff]
[    0.517051] PCI: bridge 0000:00:10.0 32bit mmio: [fde00000, fdefffff]
[    0.517054] PCI: bridge 0000:00:10.0 32bit mmio pref: [fdd00000, fddfffff]
[    0.517070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.517545] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.642978] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.642978] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.642978] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.644273] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.644544] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 *7 9 10 11 14 15)
[    0.644813] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.645082] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.645351] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.645622] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.645890] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.646161] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.646429] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.646701] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.646969] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.647238] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.647509] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.647779] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 *7 9 10 11 14 15)
[    0.648055] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.648327] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[    0.648597] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[    0.648931] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.649252] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.649573] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.649894] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.650215] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    0.650535] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.650855] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.651175] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.651496] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.651817] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.652146] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.652468] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.652789] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.653111] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.653436] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.653758] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.654079] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.654401] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.654722] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.655045] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.655366] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.655454] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.655454] pnp: PnP ACPI init
[    0.655454] ACPI: bus type pnp registered
[    0.661126] pnp: PnP ACPI: found 11 devices
[    0.661126] ACPI: ACPI bus type pnp unregistered
[    0.661126] PCI: Using ACPI for IRQ routing
[    0.676042] NET: Registered protocol family 8
[    0.676044] NET: Registered protocol family 20
[    0.676073] NetLabel: Initializing
[    0.676074] NetLabel:  domain hash size = 128
[    0.676076] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.676090] NetLabel:  unlabeled traffic allowed by default
[    0.677305] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.677307]    actual entries 65586
[    0.677433] AppArmor: AppArmor Filesystem Enabled
[    0.677463] ACPI: RTC can wake from S4
[    0.692069] system 00:01: ioport range 0x4000-0x407f has been reserved
[    0.692072] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.692079] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.692081] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.692084] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.692086] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.692089] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.692091] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.692098] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.692101] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.692112] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.692119] system 00:0a: iomem range 0xf0000-0xf3fff could not be reserved
[    0.692122] system 00:0a: iomem range 0xf4000-0xf7fff could not be reserved
[    0.692124] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.692127] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.692129] system 00:0a: iomem range 0xbfef0000-0xbfefffff could not be reserved
[    0.692132] system 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.692135] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.692137] system 00:0a: iomem range 0x100000-0xbfeeffff could not be reserved
[    0.692140] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.692143] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.692145] system 00:0a: iomem range 0xfefff000-0xfeffffff could not be reserved
[    0.692148] system 00:0a: iomem range 0xfff80000-0xfff80fff could not be reserved
[    0.692151] system 00:0a: iomem range 0xfff90000-0xfffbffff could not be reserved
[    0.692153] system 00:0a: iomem range 0xfffed000-0xfffeffff could not be reserved
[    0.697380] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.697382] pci 0000:00:02.0:   IO window: 0xb000-0xbfff
[    0.697386] pci 0000:00:02.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.697389] pci 0000:00:02.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.697393] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.697395] pci 0000:00:04.0:   IO window: 0x9000-0x9fff
[    0.697397] pci 0000:00:04.0:   MEM window: 0xfa000000-0xfcffffff
[    0.697400] pci 0000:00:04.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.697403] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.697406] pci 0000:00:10.0:   IO window: 0xa000-0xafff
[    0.697409] pci 0000:00:10.0:   MEM window: 0xfde00000-0xfdefffff
[    0.697412] pci 0000:00:10.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.697423] pci 0000:00:02.0: setting latency timer to 64
[    0.697428] pci 0000:00:04.0: setting latency timer to 64
[    0.697432] pci 0000:00:10.0: setting latency timer to 64
[    0.697435] bus: 00 index 0 io port: [0, ffff]
[    0.697437] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.697439] bus: 01 index 0 io port: [b000, bfff]
[    0.697441] bus: 01 index 1 mmio: [fdb00000, fdbfffff]
[    0.697443] bus: 01 index 2 mmio: [fdc00000, fdcfffff]
[    0.697445] bus: 01 index 3 mmio: [0, 0]
[    0.697446] bus: 02 index 0 io port: [9000, 9fff]
[    0.697448] bus: 02 index 1 mmio: [fa000000, fcffffff]
[    0.697450] bus: 02 index 2 mmio: [e0000000, efffffff]
[    0.697451] bus: 02 index 3 mmio: [0, 0]
[    0.697453] bus: 03 index 0 io port: [a000, afff]
[    0.697455] bus: 03 index 1 mmio: [fde00000, fdefffff]
[    0.697457] bus: 03 index 2 mmio: [fdd00000, fddfffff]
[    0.697459] bus: 03 index 3 io port: [0, ffff]
[    0.697460] bus: 03 index 4 mmio: [0, ffffffffffffffff]
[    0.697475] NET: Registered protocol family 2
[    0.700049] Switched to high resolution mode on CPU 0
[    0.700198] Switched to high resolution mode on CPU 1
[    0.736178] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.737872] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.743419] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.744091] TCP: Hash tables configured (established 524288 bind 65536)
[    0.744094] TCP reno registered
[    0.756120] NET: Registered protocol family 1
[    0.756237] checking if image is initramfs... it is
[    1.436778] Freeing initrd memory: 8444k freed
[    1.444282] audit: initializing netlink socket (disabled)
[    1.444298] type=2000 audit(1231336931.444:1): initialized
[    1.449787] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.453197] VFS: Disk quotas dquot_6.5.1
[    1.453307] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.453428] msgmni has been set to 6030
[    1.453563] io scheduler noop registered
[    1.453565] io scheduler anticipatory registered
[    1.453567] io scheduler deadline registered
[    1.453714] io scheduler cfq registered (default)
[    1.453727] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.453763] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.453771] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.453794] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.484051] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.484063] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.484072] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.484084] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.484105] pci 0000:02:00.0: Boot video device
[    1.484261] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.484281] pcieport-driver 0000:00:02.0: found MSI capability
[    1.484307] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.484381] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.484476] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.484494] pcieport-driver 0000:00:04.0: found MSI capability
[    1.484509] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.484579] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.535631] Linux agpgart interface v0.103
[    1.535636] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.539040] brd: module loaded
[    1.539147] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.539326] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.541997] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.542009] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.553196] mice: PS/2 mouse device common for all mice
[    1.553385] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.553418] rtc0: alarms up to one year, y3k
[    1.553484] cpuidle: using governor ladder
[    1.553487] cpuidle: using governor menu
[    1.553900] TCP cubic registered
[    1.554192] registered taskstats version 1
[    1.554348]   Magic number: 9:937:29
[    1.554362] tty ttydc: hash matches
[    1.554523] rtc_cmos 00:04: setting system clock to 2009-01-07 14:02:12 UTC (1231336932)
[    1.554526] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.554528] EDD information not available.
[    1.554572] Freeing unused kernel memory: 536k freed
[    1.554845] Write protecting the kernel read-only data: 4348k
[    1.580917] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.649406] fuse init (API version 7.9)
[    1.663310] fan PNP0C0B:00: registered as cooling_device0
[    1.663318] ACPI: Fan [FAN] (on)
[    1.669384] processor ACPI0007:00: registered as cooling_device1
[    1.669470] processor ACPI0007:01: registered as cooling_device2
[    1.673189] thermal LNXTHERM:01: registered as thermal_zone0
[    1.675335] ACPI: Thermal Zone [THRM] (40 C)
[    2.073499] usbcore: registered new interface driver usbfs
[    2.073528] usbcore: registered new interface driver hub
[    2.078567] usbcore: registered new device driver usb
[    2.078820] No dock devices found.
[    2.086627] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.087228] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    2.087243] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    2.087260] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.087263] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.087343] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.087382] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xfe02f000
[    2.098684] SCSI subsystem initialized
[    2.130179] libata version 3.00 loaded.
[    2.143221] usb usb1: configuration #1 chosen from 1 choice
[    2.143253] hub 1-0:1.0: USB hub found
[    2.143265] hub 1-0:1.0: 8 ports detected
[    2.350524] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    2.350540] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    2.350557] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.350560] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.350590] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    2.350626] ehci_hcd 0000:00:0b.1: debug port 1
[    2.350630] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    2.350654] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xfe02e000
[    2.361039] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.361238] usb usb2: configuration #1 chosen from 1 choice
[    2.361268] hub 2-0:1.0: USB hub found
[    2.361278] hub 2-0:1.0: 8 ports detected
[    2.569378] pata_amd 0000:00:0d.0: version 0.3.10
[    2.569441] pata_amd 0000:00:0d.0: setting latency timer to 64
[    2.569596] scsi0 : pata_amd
[    2.569730] scsi1 : pata_amd
[    2.570934] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    2.570937] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    2.681031] usb 2-8: new high speed USB device using ehci_hcd and address 2
[    2.732510] ata1.00: ATA-7: Maxtor 6Y250P0, YAR41BW0, max UDMA/133
[    2.732513] ata1.00: 490234752 sectors, multi 1: LBA48 
[    2.732524] ata1: nv_mode_filter: 0x7f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc600c0c0) ACPI=0x3f01f (20:600:0x13)
[    2.749421] ata1.00: configured for UDMA/100
[    2.829565] usb 2-8: configuration #1 chosen from 1 choice
[    2.936317] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-H652L, 0803, max UDMA/33
[    2.936330] ata2.01: ATAPI: ATAPI CD-RW 52X32, M.GD, max UDMA/33
[    2.936341] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc600c0c0) ACPI=0x701f (60:60:0x1f)
[    2.936345] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc600c0c0) ACPI=0x701f (60:60:0x1f)
[    2.977251] ata2.00: configured for UDMA/33
[    2.985380] ata2.01: configured for UDMA/33
[    2.985431] isa bounce pool size: 16 pages
[    2.985520] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y250P0   YAR4 PQ: 0 ANSI: 5
[    2.987451] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H652L 0803 PQ: 0 ANSI: 5
[    2.988891] scsi 1:0:1:0: CD-ROM            ATAPI    CD-RW 52X32      M.GD PQ: 0 ANSI: 5
[    2.989025] sata_nv 0000:00:0e.0: version 3.5
[    2.989550] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[    2.989561] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
[    2.989565] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    2.989606] sata_nv 0000:00:0e.0: setting latency timer to 64
[    2.991146] scsi2 : sata_nv
[    2.992106] scsi3 : sata_nv
[    2.992373] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 21
[    2.992376] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 21
[    3.322525] ata3: SATA link down (SStatus 0 SControl 310)
[    3.796051] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    3.842273] ata4.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
[    3.842277] ata4.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    3.908899] ata4.00: configured for UDMA/133
[    3.909035] scsi 3:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
[    3.911277] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[    3.911290] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
[    3.911293] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    3.911333] sata_nv 0000:00:0f.0: setting latency timer to 64
[    3.911507] scsi4 : sata_nv
[    3.912670] scsi5 : sata_nv
[    3.912922] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 20
[    3.912925] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 20
[    4.384050] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    4.434951] ata5.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
[    4.434955] ata5.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    4.501579] ata5.00: configured for UDMA/133
[    4.830524] ata6: SATA link down (SStatus 0 SControl 310)
[    4.830647] scsi 4:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
[    4.830835] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.831413] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    4.831417] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    4.831422] forcedeth 0000:00:14.0: setting latency timer to 64
[    4.831453] nv_probe: set workaround bit for reversed mac addr
[    5.348514] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:18:f3:a5:82:b4
[    5.348519] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    5.377574] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.377615] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.377650] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    5.377686] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[    5.377729] scsi 4:0:0:0: Attached scsi generic sg4 type 0
[    5.379569] usbcore: registered new interface driver libusual
[    5.389191] Initializing USB Mass Storage driver...
[    5.389322] scsi6 : SCSI emulation for USB Mass Storage devices
[    5.389439] usbcore: registered new interface driver usb-storage
[    5.389442] USB Mass Storage support registered.
[    5.389589] usb-storage: device found at 2
[    5.389591] usb-storage: waiting for device to settle before scanning
[    5.407921] Driver 'sr' needs updating - please use bus_type methods
[    5.411529] Driver 'sd' needs updating - please use bus_type methods
[    5.411680] sd 0:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[    5.411741] sd 0:0:0:0: [sda] Write Protect is off
[    5.411744] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.411780] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.411861] sd 0:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[    5.411879] sd 0:0:0:0: [sda] Write Protect is off
[    5.411881] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.411912] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.411917]  sda:sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.418104] Uniform CD-ROM driver Revision: 3.20
[    5.418215] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.420385] sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    5.420480] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    5.427552]  sda1 sda2 sda3
[    5.443718] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.443843] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[    5.443866] sd 3:0:0:0: [sdb] Write Protect is off
[    5.443868] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.443904] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.443974] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[    5.443992] sd 3:0:0:0: [sdb] Write Protect is off
[    5.443995] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.444046] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.444050]  sdb: sdb1 sdb2 < sdb5 >
[    5.485512] sd 3:0:0:0: [sdb] Attached SCSI disk
[    5.488898] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[    5.488925] sd 4:0:0:0: [sdc] Write Protect is off
[    5.488927] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.488967] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.489105] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[    5.489125] sd 4:0:0:0: [sdc] Write Protect is off
[    5.489127] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.489165] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.489169]  sdc: sdc1 sdc2 sdc3 sdc4
[    5.507664] sd 4:0:0:0: [sdc] Attached SCSI disk
[    5.874203] PM: Starting manual resume from disk
[    5.874208] PM: Resume from partition 8:21
[    5.874210] PM: Checking hibernation image.
[    5.874379] PM: Resume from disk failed.
[    5.923420] kjournald starting.  Commit interval 5 seconds
[    5.923447] EXT3-fs: mounted filesystem with ordered data mode.
[   10.388258] usb-storage: device scan complete
[   10.394611] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   10.401641] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   10.408721] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   10.415709] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   10.417563] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[   10.417680] sd 6:0:0:0: Attached scsi generic sg5 type 0
[   10.418653] sd 6:0:0:1: [sde] Attached SCSI removable disk
[   10.418710] sd 6:0:0:1: Attached scsi generic sg6 type 0
[   10.419634] sd 6:0:0:2: [sdf] Attached SCSI removable disk
[   10.419688] sd 6:0:0:2: Attached scsi generic sg7 type 0
[   10.420659] sd 6:0:0:3: [sdg] Attached SCSI removable disk
[   10.420708] sd 6:0:0:3: Attached scsi generic sg8 type 0
[   11.029614] udevd version 124 started
[   11.376036] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.441544] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.499283] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   11.520049] ACPI: Power Button (FF) [PWRF]
[   11.520152] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   11.539435] ACPI: I/O resource nForce2_smbus [0x4c00-0x4c3f] conflicts with ACPI region SM00 [0x4c00-0x4c05]
[   11.539439] ACPI: Device needs an ACPI driver
[   11.539485] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   11.539515] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   11.556052] ACPI: Power Button (CM) [PWRB]
[   12.567202] nvidia: module license 'NVIDIA' taints kernel.
[   12.823432] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   12.823447] nvidia 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   12.823453] nvidia 0000:02:00.0: setting latency timer to 64
[   12.823764] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   12.916390] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   13.557208] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   13.557215] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   13.557237] HDA Intel 0000:00:10.1: setting latency timer to 64
[   13.592091] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.737129] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   15.269460] Adding 15358132k swap on /dev/sda3.  Priority:-1 extents:1 across:15358132k
[   15.273040] Adding 9044552k swap on /dev/sdb5.  Priority:-2 extents:1 across:9044552k
[   15.670009] EXT3 FS on sda2, internal journal
[   16.153684] type=1505 audit(1231336947.229:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4416
[   16.330629] type=1505 audit(1231336947.405:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4421
[   16.330856] type=1505 audit(1231336947.405:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4421
[   16.469217] ip_tables: (C) 2000-2006 Netfilter Core Team

 

===== PC HW INFO ==== before swap move to /dev/sda3 ===

$ cat pc_info.txt |more
crested
    description: Desktop Computer
    product: RC652AA-ABA a1610n
    vendor: HP Pavilion 061
    version: 0nx1114RE101NODM300
    serial: MXF6430JNL NA680
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00CDA687-CFD2-1110-A4F4-A2FECF015B7C
  *-core
       description: Motherboard
       product: NODUSM3
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.05
       serial: MS1C6AS20602716
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.10 (12/13/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 
int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipb
oot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          slot: Socket AM2
          size: 2200MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflus
h mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legac
y svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: d
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 5
          bus info: cpu@1
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          slot: Socket AM2
          size: 2200MHz
          capacity: 3700MHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: e
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 35
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: G70 [GeForce 7600 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi0
          logical name: scsi1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-disk
             description: ATA Disk
             product: Maxtor 6Y250P0
             vendor: Maxtor
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: YAR4
             serial: Y64A8PME
             size: 233GiB (251GB)

             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=f150eaaf
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: d8bc59cf-6667-054d-b22c-9dfe8ffbae7e
                size: 29GiB
                capacity: 29GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2008-12-20 23:50:33 filesystem=ntfs label=win xp os state=clean
           *-volume:1
                description: EXT3 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: 31334a26-e238-440e-bf8a-7a1bfb1bc93b
                size: 170GiB
                capacity: 170GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 i
nitialized
                configuration: created=2008-12-26 20:39:27 filesystem=ext3 modified=2009-01-03 14:24:42 mount.fstype=ex
t3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-01-03 14:24:42 state=mounted
        *-cdrom:0
             description: DVD-RAM writer
             product: CD/DVDW TS-H652L
             vendor: TSSTcorp
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 0803
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: CD-R/CD-RW writer
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/scd1
             logical name: /dev/sr1
             capabilities: audio cd-r cd-rw
             configuration: status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi3
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: MAXTOR STM332062
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 3.AA
             serial: 6QF1TTRK
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00000001
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: 3606a635-9525-4425-95c5-6fb6f21620ec
                size: 116GiB
                capacity: 116GiB
                capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialize
d
                configuration: created=2009-01-01 19:10:49 filesystem=ext3 modified=2009-01-03 16:08:21 mounted=2009-01
-03 20:56:44 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sdb2
                size: 8832MiB
                capacity: 8832MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 8832MiB
                   capabilities: nofs
     *-ide:2
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          logical name: scsi4
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: MAXTOR STM332062
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
             version: 3.AA
             serial: 6QF1KFXA
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000396c1
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdc1
                version: 1.0
                serial: 55fb3163-9b35-44d8-b62f-43bbe745fa3a
                size: 14GiB
                capacity: 14GiB

==== more info possible if needed ====

---

### Post by Yashiro on 2009-01-07
> - AMD CPUs are 64 bit, 3 Gigs RAM is 64 bit, Nivida PCI bridge & SATA controller is 32 bit -- Is this problem?
- not using UIDD names, but still /dev/sda, /dev/sdb, /dev/sdc drive name -- Is this problem?
No. Sounds like a drive controller issue perhaps?

I suppose you've messed around in the bios already? I'm reluctant to say update it because my nforce2/amd939 setup runs fine with a bios from 2005 but you never know, I guess.
I'd also be inclined to not run nvidia blob drivers for the time being.

---

### Post by tomthumb99 on 2009-01-09
Thanks for the direction, was thinking of getting a PCI SATA card and disabling the motherboad SATA controlers.  Before that, I would like to try and update motherbpard PIC Bridge BISO/firmware first (it does boot after all ).  Where can I find that, HP des not support linux on the box.  Does Nivida or the motherboard maker supply this.  I have the latest HP BIOS for model

After more research, it appears that maxtor drives have many linux probs.  All three on my drives are maxtors, so there could be a something here   Looks like some folks like to adjust 'hdparm' settings.  Sound like another nice small next step to attempt.  Where to I find the correct Maxtor 'hdparm' settings?? (I found nothing on maxtor's Web site, hopefully it not a trial by fire or guess thing) Is this a false or bad action plan to look into? 

Does anybody see definite problems in the dmsg log listing above (sorry its a sloppy text paste), I do not know what a clean dmsg should look like, any points or guidance will help. 

Thanks in advance..Tom H.

---

### Post by adamlau on 2009-01-09
Like yourself, I am an old HW hack. The easy answer and the route I always take with challenged disk drives is to verify (check and reallocate bad blocks) the media with manufacturer diagnostic hardware before writing zeros to the drive. I allow the entire process to complete, if the verify passes and the zero write process fails, you may indeed have a faulty controller.

---

### Post by tomthumb99 on 2009-01-19
Folks, I found the soluition,  'calestyo' in Germany located an AMD CPU and NVIDIA mobo SATA chip set problem. Others had found this prob, this is a two year old issue (Dec 06).  On this thread there in a Nvidia staff admitting to the issue; funny though you can't find it off the official NVIDIA site.

[http://www.nvnews.net/vbulletin/showthread.php?t=82909&highlight=LKML]("http://www.nvnews.net/vbulletin/showthread.php?t=82909&highlight=LKML")

 My fix: on grub/kernel boot-up line have "iommun=soft mem=1g" set, also on the hdparm utility I have 'write cache" off on drives.  My 8.10 install is stable, fs corruption has been reduced ( ie: I am not reinstall from the live-CD once a week).  It kills me to reduce my 3g ram to 1gig, but much better than a regular re-install.

I think there needs be a HW woodshed that flags particular vendors to avoid. I wasted 2 months on this prob.  I bought a Geforce 7600GT in the past, it just rubs salt to my wounds. I am now a ATI video card customer for life. 

Look at all the postings Nvidia has here with its multiple probs, shamefull.

---

### Post by Yashiro on 2009-01-19
If you ever feel like replacing your motherboard I can tell you that the Asus A8N does not require any of these workarounds and is fine under 8.04/64 and above.

---

### Post by tomthumb99 on 2009-10-27
mea culpa, I found that I had a bad DIMM board.  Running the memory check for 4 hrs found the problem.  Now down to 2 gigs RAM  with 9.04 using ext4 partition, all is stable.  Does not look to be nividia controller.

---

