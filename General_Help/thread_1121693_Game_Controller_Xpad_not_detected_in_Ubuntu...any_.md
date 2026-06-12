---
title: "Game Controller Xpad not detected in Ubuntu...any help appreciated."
date: 2009-04-10
forum: General Help
---

### Post by akol37 on 2009-04-10
Hello all,

I recently bought an xpad game controller. Specifically, it is a Pelican Blade-C Type, PL-2057. It normally has an xbox connector, but I also bought a xbox-to-usb cable converter, and plugged it in, naively thinking that windows (I swear by linux, but dual-boot for purely academic reasons) would detect it. No go. Neither does ubuntu (I have Hardy Heron). My computer is a custom build, and after hours of unfruitful research, I'm beginning to think my controller is, too. ;)

Ahem -- any tips would be great!

Thanks...

---

### Post by tjwoosta on 2009-04-10
well first check if its even being registered as a usb device 
(ie see if your usb converter is working)

```
lsusb
```

if you see it, thats good

you could try the xpad drivers

also this link may help
[http://ubuntuforums.org/showthread.php?t=452590]("http://ubuntuforums.org/showthread.php?t=452590")

as for windows have you tried xbcd?

[http://www.redcl0ud.com/xbcd.html]("http://www.redcl0ud.com/xbcd.html")

---

### Post by akol37 on 2009-04-10
Hi tjwoosta, thanx for the quick reply. Yep, have tried xbcd in XP...no go. I've got XP Pro SP3. 

Here's the output when I run lsusb.

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 03f0:7604 Hewlett-Packard Deskjet 3940
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Only my printer is detected. Now, on the other hand, XP will detect *something*, but always complains that I doesn't know what.

I followed your ubuntu link, which took me to a second one, which told me to install jscalibrator. I did, but when I ran it, it complained about not finding a driver. Keep in mind that I'm still wet behind the ears when it comes to linux. I might have missed something in that link that was obvious to you.

---

### Post by akol37 on 2009-04-11
And here's the output of dmesg when I run it...

[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 518081
[    0.000000] Kernel command line: root=UUID=6053a1f8-debb-4a70-b43c-cc0b77698c14 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2793.117 MHz processor.
[   14.519640] Console: colour VGA+ 80x25
[   14.519644] console [tty0] enabled
[   14.519937] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.520282] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.643144] Memory: 2058368k/2088640k available (2179k kernel code, 29044k reserved, 1008k data, 368k init, 1171136k highmem)
[   14.643152] virtual kernel memory layout:
[   14.643153]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   14.643154]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.643155]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.643156]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.643157]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   14.643158]       .data : 0xc0320c78 - 0xc041cdc4   (1008 kB)
[   14.643159]       .text : 0xc0100000 - 0xc0320c78   (2179 kB)
[   14.643162] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.643203] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.643299] hpet clockevent registered
[   14.723167] Calibrating delay using timer specific routine.. 5591.23 BogoMIPS (lpj=11182466)
[   14.723190] Security Framework initialized
[   14.723197] SELinux:  Disabled at boot.
[   14.723211] AppArmor: AppArmor initialized
[   14.723216] Failure registering capabilities with primary security module.
[   14.723225] Mount-cache hash table entries: 512
[   14.723357] Initializing cgroup subsys ns
[   14.723362] Initializing cgroup subsys cpuacct
[   14.723375] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
[   14.723385] monitor/mwait feature present.
[   14.723388] using mwait in idle threads.
[   14.723394] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   14.723397] CPU: L2 cache: 1024K
[   14.723400] CPU: Physical Processor ID: 0
[   14.723403] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043180 0000441d 00000000 00000000 00000000
[   14.723414] Compat vDSO mapped to ffffe000.
[   14.723431] Checking 'hlt' instruction... OK.
[   14.739630] SMP alternatives: switching to UP code
[   14.741672] Early unpacking initramfs... done
[   15.073747] ACPI: Core revision 20070126
[   15.073801] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.087698] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 04
[   15.087719] SMP alternatives: switching to SMP code
[   15.088557] Booting processor 1/1 eip 3000
[   15.098660] Initializing CPU#1
[   15.178374] Calibrating delay using timer specific routine.. 5586.07 BogoMIPS (lpj=11172149)
[   15.178386] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
[   15.178393] monitor/mwait feature present.
[   15.178400] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.178403] CPU: L2 cache: 1024K
[   15.178406] CPU: Physical Processor ID: 0
[   15.178408] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043180 0000441d 00000000 00000000 00000000
[   15.178798] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 04
[   15.178843] Total of 2 processors activated (11177.30 BogoMIPS).
[   15.178992] ENABLING IO-APIC IRQs
[   15.179171] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.326266] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   15.346250] Brought up 2 CPUs
[   15.346279] CPU0 attaching sched-domain:
[   15.346283]  domain 0: span 03
[   15.346285]   groups: 01 02
[   15.346289]   domain 1: span 03
[   15.346291]    groups: 03
[   15.346294] CPU1 attaching sched-domain:
[   15.346296]  domain 0: span 03
[   15.346298]   groups: 02 01
[   15.346301]   domain 1: span 03
[   15.346304]    groups: 03
[   15.346594] net_namespace: 64 bytes
[   15.346602] Booting paravirtualized kernel on bare hardware
[   15.347374] Time:  6:13:06  Date: 04/11/09
[   15.347403] NET: Registered protocol family 16
[   15.347695] EISA bus registered
[   15.347704] ACPI: bus type pci registered
[   15.347907] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[   15.347909] PCI: Using configuration type 1
[   15.347916] Setting up standard PCI resources
[   15.359669] ACPI: EC: Look up EC in DSDT
[   15.367649] ACPI: Interpreter enabled
[   15.367652] ACPI: (supports S0 S1 S3 S4 S5)
[   15.367673] ACPI: Using IOAPIC for interrupt routing
[   15.367952] Error attaching device data
[   15.368012] Error attaching device data
[   15.368072] Error attaching device data
[   15.368136] Error attaching device data
[   15.380990] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.381663] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   15.381668] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   15.382289] PCI: Transparent bridge - 0000:00:1e.0
[   15.382323] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.382493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   15.382627] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   15.382724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   15.392691] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   15.392831] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   15.392967] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   15.393103] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   15.393239] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   15.393378] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   15.393516] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   15.393654] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   15.393824] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  21, should be 14 [20070126]
[   15.393835] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.393881] pnp: PnP ACPI init
[   15.393891] ACPI: bus type pnp registered
[   15.402638] pnp: PnP ACPI: found 19 devices
[   15.402642] ACPI: ACPI bus type pnp unregistered
[   15.402646] PnPBIOS: Disabled by ACPI PNP
[   15.403006] PCI: Using ACPI for IRQ routing
[   15.403011] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.442085] NET: Registered protocol family 8
[   15.442088] NET: Registered protocol family 20
[   15.442135] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   15.442141] hpet0: 3 64-bit timers, 14318180 Hz
[   15.443184] AppArmor: AppArmor Filesystem Enabled
[   15.445919] Time: tsc clocksource has been installed.
[   15.445937] Switched to high resolution mode on CPU 0
[   15.446073] Switched to high resolution mode on CPU 1
[   15.458919] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   15.458934] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   15.458937] system 00:08: ioport range 0x800-0x87f has been reserved
[   15.458940] system 00:08: ioport range 0x480-0x4bf has been reserved
[   15.458943] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   15.458946] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   15.458954] system 00:0b: iomem range 0xffc00000-0xfff7ffff could not be reserved
[   15.458961] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   15.458964] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   15.458973] system 00:0f: ioport range 0xa00-0xa0f has been reserved
[   15.458977] system 00:0f: ioport range 0xa10-0xa1f has been reserved
[   15.458980] system 00:0f: ioport range 0xa20-0xa2f has been reserved
[   15.458983] system 00:0f: ioport range 0xa30-0xa3f has been reserved
[   15.458990] system 00:11: iomem range 0xe0000000-0xe3ffffff has been reserved
[   15.458997] system 00:12: iomem range 0x0-0x9ffff could not be reserved
[   15.459000] system 00:12: iomem range 0xc0000-0xcffff could not be reserved
[   15.459003] system 00:12: iomem range 0xe0000-0xfffff could not be reserved
[   15.459006] system 00:12: iomem range 0x100000-0x7f7fffff could not be reserved
[   15.459009] system 00:12: iomem range 0x0-0x0 could not be reserved
[   15.489601] PCI: Bridge: 0000:00:1c.0
[   15.489603]   IO window: disabled.
[   15.489609]   MEM window: disabled.
[   15.489613]   PREFETCH window: disabled.
[   15.489618] PCI: Bridge: 0000:00:1c.3
[   15.489621]   IO window: d000-dfff
[   15.489627]   MEM window: fea00000-feafffff
[   15.489630]   PREFETCH window: disabled.
[   15.489636] PCI: Bridge: 0000:00:1e.0
[   15.489639]   IO window: e000-efff
[   15.489644]   MEM window: feb00000-febfffff
[   15.489648]   PREFETCH window: disabled.
[   15.489680] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.489687] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.489709] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[   15.489715] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   15.489726] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   15.489739] NET: Registered protocol family 2
[   15.526823] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.527142] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.527762] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.528069] TCP: Hash tables configured (established 131072 bind 65536)
[   15.528072] TCP reno registered
[   15.538904] checking if image is initramfs... it is
[   16.192711] Freeing initrd memory: 7719k freed
[   16.193708] audit: initializing netlink socket (disabled)
[   16.193722] audit(1239430386.420:1): initialized
[   16.193979] highmem bounce pool size: 64 pages
[   16.196611] VFS: Disk quotas dquot_6.5.1
[   16.196718] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.196877] io scheduler noop registered
[   16.196880] io scheduler anticipatory registered
[   16.196882] io scheduler deadline registered
[   16.196895] io scheduler cfq registered (default)
[   16.196906] Boot video device is 0000:00:02.0
[   16.197117] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.197165] assign_interrupt_mode Found MSI capability
[   16.197205] Allocate Port Service[0000:00:1c.0:pcie00]
[   16.197254] Allocate Port Service[0000:00:1c.0:pcie02]
[   16.197359] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   16.197406] assign_interrupt_mode Found MSI capability
[   16.197444] Allocate Port Service[0000:00:1c.3:pcie00]
[   16.197492] Allocate Port Service[0000:00:1c.3:pcie02]
[   16.197835] isapnp: Scanning for PnP cards...
[   16.548939] isapnp: No Plug & Play device found
[   16.589123] Real Time Clock Driver v1.12ac
[   16.589338] hpet_resources: 0xfed00000 is busy
[   16.589378] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.589519] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.590478] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.591553] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.591637] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.591788] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   16.592149] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.592156] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.612024] mice: PS/2 mouse device common for all mice
[   16.612194] EISA: Probing bus 0 at eisa.0
[   16.612227] EISA: Detected 0 cards.
[   16.612231] cpuidle: using governor ladder
[   16.612233] cpuidle: using governor menu
[   16.612320] NET: Registered protocol family 1
[   16.612353] Using IPI No-Shortcut mode
[   16.612385] registered taskstats version 1
[   16.612491]   Magic number: 5:614:215
[   16.612596] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.612598] EDD information not available.
[   16.612803] Freeing unused kernel memory: 368k freed
[   16.612832] Write protecting the kernel read-only data: 806k
[   16.629556] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.881264] fuse init (API version 7.9)
[   17.907244] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.907259] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.908681] ACPI: Thermal Zone [THRM] (40 C)
[   18.119357] usbcore: registered new interface driver usbfs
[   18.119404] usbcore: registered new interface driver hub
[   18.119466] usbcore: registered new device driver usb
[   18.122483] USB Universal Host Controller Interface driver v3.0
[   18.122570] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   18.122589] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   18.122596] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   18.122905] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   18.122950] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000c880
[   18.123209] usb usb1: configuration #1 chosen from 1 choice
[   18.123261] hub 1-0:1.0: USB hub found
[   18.123274] hub 1-0:1.0: 2 ports detected
[   18.226218] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   18.226234] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   18.226240] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   18.226276] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   18.226311] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000c800
[   18.226491] usb usb2: configuration #1 chosen from 1 choice
[   18.226531] hub 2-0:1.0: USB hub found
[   18.226540] hub 2-0:1.0: 2 ports detected
[   18.330947] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   18.330963] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   18.330968] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   18.331007] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   18.331041] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000c480
[   18.331219] usb usb3: configuration #1 chosen from 1 choice
[   18.331260] hub 3-0:1.0: USB hub found
[   18.331269] hub 3-0:1.0: 2 ports detected
[   18.433897] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   18.433914] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   18.433920] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   18.433960] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   18.433996] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c400
[   18.434203] usb usb4: configuration #1 chosen from 1 choice
[   18.434247] hub 4-0:1.0: USB hub found
[   18.434259] hub 4-0:1.0: 2 ports detected
[   18.528630] SCSI subsystem initialized
[   18.537718] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   18.537736] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   18.537742] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   18.537782] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   18.541698] ehci_hcd 0000:00:1d.7: debug port 1
[   18.541706] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   18.541715] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfe937c00
[   18.570405] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   18.572514] libata version 3.00 loaded.
[   18.581515] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.581688] usb usb5: configuration #1 chosen from 1 choice
[   18.581732] hub 5-0:1.0: USB hub found
[   18.581743] hub 5-0:1.0: 8 ports detected
[   18.685433] r8169 Gigabit Ethernet driver 2.2LK loaded
[   18.685468] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[   18.685502] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   18.686028] eth0: RTL8101e at 0xf884c000, 00:21:97:8b:c0:e3, XID 34200000 IRQ 221
[   18.688420] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   18.688464] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   18.688481] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   18.688513] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[   18.688548] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.688562] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   18.692173] Floppy drive(s): fd0 is 1.44M
[   18.704196] ata_piix 0000:00:1f.1: version 2.12
[   18.704218] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   18.704325] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   18.706093] scsi0 : ata_piix
[   18.706445] scsi1 : ata_piix
[   18.708578] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   18.708585] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   18.713014] FDC 0 is a post-1991 82077
[   19.028245] ata1.00: ATAPI: IDE5232CO, VER K043, max UDMA/66
[   19.028268] ata1.00: limited to UDMA/33 due to 40-wire cable
[   19.239696] ata1.00: configured for UDMA/33
[   19.239757] ata2: port disabled. ignoring.
[   19.332558] scsi 0:0:0:0: CD-ROM            COMBO    IDE5232CO        K043 PQ: 0 ANSI: 5
[   19.332688] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   19.332716] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[   19.332762] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   19.352705] scsi2 : ata_piix
[   19.352991] scsi3 : ata_piix
[   19.353052] ata3: SATA max UDMA/133 cmd 0xc080 ctl 0xc000 bmdma 0xb800 irq 17
[   19.353057] ata4: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb808 irq 17
[   19.482903] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   19.557347] ata3.00: ATA-7: ST3160815AS, 3.AAC, max UDMA/133
[   19.557352] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   19.623874] ata3.00: configured for UDMA/133
[   19.667017] usb 2-2: configuration #1 chosen from 1 choice
[   19.792664] scsi 2:0:0:0: Direct-Access     ATA      ST3160815AS      3.AA PQ: 0 ANSI: 5
[   19.808498] Driver 'sd' needs updating - please use bus_type methods
[   19.808648] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   19.808669] sd 2:0:0:0: [sda] Write Protect is off
[   19.808674] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.808705] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.808781] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   19.808799] sd 2:0:0:0: [sda] Write Protect is off
[   19.808803] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.808834] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.808839]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   19.817591] sr0: scsi3-mmc drive: 24x/52x writer cd/rw xa/form2 cdda tray
[   19.817596] Uniform CD-ROM driver Revision: 3.20
[   19.817661] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   19.829760]  sda1 sda2 sda3 sda4 < sda5 >
[   19.865235] sd 2:0:0:0: [sda] Attached SCSI disk
[   19.871524] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   19.871561] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   19.906180] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   20.025961] usb 4-1: device descriptor read/64, error -71
[   20.249578] usb 4-1: device descriptor read/64, error -71
[   20.250373] Attempting manual resume
[   20.250378] swsusp: Resume From Partition 8:2
[   20.250380] PM: Checking swsusp image.
[   20.250516] PM: Resume from disk failed.
[   20.286613] kjournald starting.  Commit interval 5 seconds
[   20.286637] EXT3-fs: mounted filesystem with ordered data mode.
[   20.465200] usb 4-1: new full speed USB device using uhci_hcd and address 3
[   20.584985] usb 4-1: device descriptor read/64, error -71
[   21.219878] usb 4-1: device not accepting address 3, error -75
[   21.331684] usb 4-1: new full speed USB device using uhci_hcd and address 4
[   21.742968] usb 4-1: device not accepting address 4, error -71
[   21.850782] usb 4-1: new full speed USB device using uhci_hcd and address 5
[   22.258069] usb 4-1: device not accepting address 5, error -71
[   26.275644] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.355896] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.526719] Linux agpgart interface v0.102
[   26.562714] iTCO_vendor_support: vendor-support=0
[   26.586907] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   26.587094] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   26.587111] iTCO_wdt: No card detected
[   26.731684] agpgart: Detected an Intel 945G Chipset.
[   26.732090] agpgart: Detected 7932K stolen memory.
[   26.747016] agpgart: AGP aperture is 256M @ 0xd0000000
[   26.837235] intel_rng: FWH not detected
[   26.958194] input: Power Button (FF) as /devices/virtual/input/input2
[   26.993033] ACPI: Power Button (FF) [PWRF]
[   26.993207] input: Power Button (CM) as /devices/virtual/input/input3
[   27.009876] ACPI: Power Button (CM) [PWRB]
[   28.370993] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.371024] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.590433] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   28.782287] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7604
[   28.782312] usbcore: registered new interface driver usblp
[   29.184249] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   29.368367] parport_pc 00:07: reported by Plug and Play ACPI
[   29.368451] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   30.790821] lp0: using parport0 (interrupt-driven).
[   30.862093] Adding 9767512k swap on /dev/sda2.  Priority:-1 extents:1 across:9767512k
[   31.431362] EXT3 FS on sda3, internal journal
[   31.582876] device-mapper: uevent: version 1.0.3
[   31.582921] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   32.933755] ip_tables: (C) 2000-2006 Netfilter Core Team
[   33.346943] No dock devices found.
[   34.829779] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   34.829787] apm: disabled - APM is not SMP safe.
[   34.960657] ppdev: user-space parallel port driver
[   35.180545] audit(1239430405.516:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5094 profile="/usr/sbin/cupsd" namespace="default"
[   36.955625] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   36.955633] vboxdrv: Successfully done.
[   36.955637] vboxdrv: Found 2 processor cores.
[   36.956686] vboxdrv: fAsync=0 offMin=0x49f offMax=0x3bc6
[   36.957085] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   36.957092] vboxdrv: Successfully loaded version 2.1.4 (interface 0x000a0009).
[   38.932384] r8169: eth0: link up
[   38.932396] r8169: eth0: link up
[   39.234058] Bluetooth: Core ver 2.11
[   39.234385] NET: Registered protocol family 31
[   39.234390] Bluetooth: HCI device and connection manager initialized
[   39.234396] Bluetooth: HCI socket layer initialized
[   39.293462] usb 4-1: new full speed USB device using uhci_hcd and address 6
[   39.298882] Bluetooth: L2CAP ver 2.9
[   39.298889] Bluetooth: L2CAP socket layer initialized
[   39.363194] Bluetooth: RFCOMM socket layer initialized
[   39.363563] Bluetooth: RFCOMM TTY layer initialized
[   39.363572] Bluetooth: RFCOMM ver 1.8
[   39.819537] usb 4-1: device not accepting address 6, error -71
[   39.931354] usb 4-1: new full speed USB device using uhci_hcd and address 7
[   40.056126] usb 4-1: device descriptor read/64, error -71
[   40.278751] usb 4-1: device descriptor read/64, error -71
[   40.494371] usb 4-1: new full speed USB device using uhci_hcd and address 8
[   40.901654] usb 4-1: device not accepting address 8, error -71
[   41.013480] usb 4-1: new full speed USB device using uhci_hcd and address 9
[   41.424744] usb 4-1: device not accepting address 9, error -71
[   42.053264] NET: Registered protocol family 17
[   43.486663] NET: Registered protocol family 10
[   43.487128] lo: Disabled Privacy Extensions
[   44.091981] [drm] Initialized drm 1.1.0 20060810
[   44.098631] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.098645] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   44.098731] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   53.731342] eth0: no IPv6 routers present
[  105.569218] usb 4-1: new full speed USB device using uhci_hcd and address 10
[  105.748908] usb 4-1: device descriptor read/64, error -71
[  106.028421] usb 4-1: device descriptor read/64, error -71
[  106.244052] usb 4-1: new full speed USB device using uhci_hcd and address 11
[  106.363835] usb 4-1: device descriptor read/64, error -71
[  106.994738] usb 4-1: device not accepting address 11, error -71
[  107.106544] usb 4-1: new full speed USB device using uhci_hcd and address 12
[  107.513836] usb 4-1: device not accepting address 12, error -71
[  107.625640] usb 4-1: new full speed USB device using uhci_hcd and address 13
[  108.032934] usb 4-1: device not accepting address 13, error -75
[  132.603242] usb 4-1: new full speed USB device using uhci_hcd and address 14
[  133.189195] usb 4-1: device not accepting address 14, error -71
[  133.301001] usb 4-1: new full speed USB device using uhci_hcd and address 15
[  133.420792] usb 4-1: device descriptor read/64, error -71
[  134.055686] usb 4-1: device not accepting address 15, error -71
[  134.167504] usb 4-1: new full speed USB device using uhci_hcd and address 16
[  134.574783] usb 4-1: device not accepting address 16, error -71
[  134.686591] usb 4-1: new full speed USB device using uhci_hcd and address 17
[  135.093882] usb 4-1: device not accepting address 17, error -71

Thoughts?

---

### Post by akol37 on 2009-04-15
Bump! :)

---

### Post by Sutur on 2009-09-01
Bump! I'm stuck with this issue also.

Both windows and linux claim that the device **fails enumeration**.

If the above means anything to anyone please speak up because it might help me solve the issue myself!

---

