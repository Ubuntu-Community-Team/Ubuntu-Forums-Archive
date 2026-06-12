---
title: "Hardy Xorg freezes often (unkillable at 99% cpu)"
date: 2009-04-04
forum: General Help
---

### Post by nmsmith on 2009-04-04
I've had this problem for about a week now.

Symptoms:[LIST]
[*]My display often freezes, with only the mouse responding, and some text/icons corrupt.
[*]It often happens just after login, but occasionally will let me use the system for hours before locking up.
[*]Waiting for a while (5 mins, I guess) at GDM can improve my chances of logging in successfully.
[*]I can't use Ctrl+Alt+F2 etc to get to a different terminal.
[*]I can ssh in to reboot cleanly.
[*]It tends to happen on or just after user input (i.e. logging in, launching a program, using the menus in mythtv). But sometimes not!
[*]top reports that xorg, owned by root, is at 99% cpu. I can't kill it.
[/LIST]

Other information:
[LIST]
[*]This is a desktop machine, with a Nvidia 6150 PCIE video card
[*]I have no particularly unusal repositories enabled (as in [this widely read blog]("http://blag.xkcd.com/2009/04/03/what-happened-to-my-laptop/")) although nm-applet has stopped working in one of my user accounts
[*]I have proprietary nvidia drivers disabled
[*]I don't know how to do the equivalent of what used to be ```
sudo dpkg-reconfigure xserver-xorg
```
[*]A diff of kern.log, dmesg and Xorg.0.log all report no change between before and after the hang.
[/LIST]

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:13:11 UTC 2009 (Ubuntu 2.6.24-23.48-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262064) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262064
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262064
[    0.000000] On node 0 totalpages: 262064
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32433 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8880 checksum 0
[    0.000000] ACPI: RSDP 000F8880, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFB0000, 0034 (r1 A M I  OEMRSDT   9000619 MSFT       97)
[    0.000000] ACPI: FACP 3FFB0200, 0084 (r2 A M I  OEMFACP   9000619 MSFT       97)
[    0.000000] ACPI: DSDT 3FFB0440, 49AD (r1  AS2GL AS2GL000        0 INTL  2002026)
[    0.000000] ACPI: FACS 3FFC0000, 0040
[    0.000000] ACPI: APIC 3FFB0390, 0068 (r1 A M I  OEMAPIC   9000619 MSFT       97)
[    0.000000] ACPI: MCFG 3FFB0400, 003C (r1 A M I  OEMMCFG   9000619 MSFT       97)
[    0.000000] ACPI: OEMB 3FFC0040, 0050 (r1 A M I  AMI_OEM   9000619 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260017
[    0.000000] Kernel command line: root=UUID=c4d3c1c1-42a7-4867-a5dd-5bbbba3f4c2d ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fecc0000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1998.920 MHz processor.
[   31.562726] Console: colour VGA+ 80x25
[   31.562730] console [tty0] enabled
[   31.563145] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   31.563565] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.587589] Memory: 1027100k/1048256k available (2179k kernel code, 20484k reserved, 1008k data, 368k init, 130752k highmem)
[   31.587597] virtual kernel memory layout:
[   31.587598]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   31.587599]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   31.587600]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   31.587601]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   31.587602]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   31.587603]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   31.587604]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[   31.587607] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.587645] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   31.667630] Calibrating delay using timer specific routine.. 4000.64 BogoMIPS (lpj=8001291)
[   31.667658] Security Framework initialized
[   31.667665] SELinux:  Disabled at boot.
[   31.667681] AppArmor: AppArmor initialized
[   31.667685] Failure registering capabilities with primary security module.
[   31.667693] Mount-cache hash table entries: 512
[   31.667817] Initializing cgroup subsys ns
[   31.667820] Initializing cgroup subsys cpuacct
[   31.667831] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   31.667840] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   31.667842] CPU: L2 Cache: 512K (64 bytes/line)
[   31.667844] CPU 0(2) -> Core 0
[   31.667846] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000001f 00000000
[   31.667857] Compat vDSO mapped to ffffe000.
[   31.667868] Checking 'hlt' instruction... OK.
[   31.683915] SMP alternatives: switching to UP code
[   31.685184] Early unpacking initramfs... done
[   31.991121] ACPI: Core revision 20070126
[   31.991183] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   32.004497] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   32.004514] SMP alternatives: switching to SMP code
[   32.004956] Booting processor 1/1 eip 3000
[   32.013837] Initializing CPU#1
[   32.094310] Calibrating delay using timer specific routine.. 3998.10 BogoMIPS (lpj=7996207)
[   32.094317] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   32.094323] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   32.094325] CPU: L2 Cache: 512K (64 bytes/line)
[   32.094327] CPU 1(2) -> Core 1
[   32.094329] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000001f 00000000
[   32.095551] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   32.095568] Total of 2 processors activated (7998.74 BogoMIPS).
[   32.095771] ENABLING IO-APIC IRQs
[   32.095946] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   32.243458] Brought up 2 CPUs
[   32.243491] CPU0 attaching sched-domain:
[   32.243493]  domain 0: span 03
[   32.243495]   groups: 01 02
[   32.243498] CPU1 attaching sched-domain:
[   32.243500]  domain 0: span 03
[   32.243501]   groups: 02 01
[   32.243694] net_namespace: 64 bytes
[   32.243702] Booting paravirtualized kernel on bare hardware
[   32.244147] Time: 10:38:54  Date: 04/04/09
[   32.244175] NET: Registered protocol family 16
[   32.244348] EISA bus registered
[   32.244352] ACPI: bus type pci registered
[   32.245141] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=128
[   32.245144] PCI: Using configuration type 1
[   32.245154] Setting up standard PCI resources
[   32.254082] ACPI: EC: Look up EC in DSDT
[   32.258935] ACPI: Interpreter enabled
[   32.258937] ACPI: (supports S0 S1 S3 S4 S5)
[   32.258950] ACPI: Using IOAPIC for interrupt routing
[   32.266563] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   32.268596] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   32.268755] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   32.268825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[   32.268900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[   32.268974] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP1._PRT]
[   32.269048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP2._PRT]
[   32.269122] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP3._PRT]
[   32.269212] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   32.287276] ACPI: PCI Root Bridge [PCI1] (0000:80)
[   32.287411] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   32.287651] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   32.287756] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   32.287859] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   32.287961] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   32.288062] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.288166] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.288268] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.288371] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   32.288478] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  62, should be 3B [20070126]
[   32.288484] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.288510] pnp: PnP ACPI init
[   32.288517] ACPI: bus type pnp registered
[   32.292640] pnp: PnP ACPI: found 14 devices
[   32.292642] ACPI: ACPI bus type pnp unregistered
[   32.292646] PnPBIOS: Disabled by ACPI PNP
[   32.292843] PCI: Using ACPI for IRQ routing
[   32.292846] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   32.595180] NET: Registered protocol family 8
[   32.595182] NET: Registered protocol family 20
[   32.595247] AppArmor: AppArmor Filesystem Enabled
[   32.607199] system 00:08: ioport range 0x295-0x296 has been reserved
[   32.607202] system 00:08: ioport range 0x3e0-0x3e7 has been reserved
[   32.607204] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   32.607207] system 00:08: ioport range 0x800-0x87f has been reserved
[   32.607209] system 00:08: ioport range 0x400-0x41f has been reserved
[   32.607212] system 00:08: iomem range 0xfebfc000-0xfebfffff has been reserved
[   32.607218] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[   32.607221] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[   32.607227] system 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   32.607232] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   32.607235] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   32.607238] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   32.607240] system 00:0c: iomem range 0x100000-0x3fffffff could not be reserved
[   32.607243] system 00:0c: iomem range 0xff380000-0xffffffff could not be reserved
[   32.637599] PCI: Bridge: 0000:00:01.0
[   32.637601]   IO window: disabled.
[   32.637605]   MEM window: disabled.
[   32.637608]   PREFETCH window: disabled.
[   32.637613] PCI: Bridge: 0000:00:02.0
[   32.637614]   IO window: disabled.
[   32.637618]   MEM window: fc000000-feafffff
[   32.637621]   PREFETCH window: d0000000-dfffffff
[   32.637625] PCI: Bridge: 0000:00:03.0
[   32.637626]   IO window: disabled.
[   32.637630]   MEM window: disabled.
[   32.637634]   PREFETCH window: cff00000-cfffffff
[   32.637639] PCI: Bridge: 0000:00:03.1
[   32.637640]   IO window: disabled.
[   32.637644]   MEM window: disabled.
[   32.637648]   PREFETCH window: cfe00000-cfefffff
[   32.637653] PCI: Bridge: 0000:00:03.2
[   32.637655]   IO window: e000-efff
[   32.637660]   MEM window: fbf00000-fbffffff
[   32.637663]   PREFETCH window: disabled.
[   32.637668] PCI: Bridge: 0000:00:03.3
[   32.637671]   IO window: d000-dfff
[   32.637675]   MEM window: fbe00000-fbefffff
[   32.637679]   PREFETCH window: disabled.
[   32.637700] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   32.637715] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
[   32.637720] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   32.637735] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17
[   32.637740] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   32.637754] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 35 (level, low) -> IRQ 18
[   32.637759] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   32.637773] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 39 (level, low) -> IRQ 19
[   32.637778] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   32.637792] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 43 (level, low) -> IRQ 20
[   32.637797] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   32.637810] NET: Registered protocol family 2
[   32.639151] Time: acpi_pm clocksource has been installed.
[   32.639166] Switched to high resolution mode on CPU 0
[   32.638149] Switched to high resolution mode on CPU 1
[   32.675156] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.675444] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   32.676393] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   32.676881] TCP: Hash tables configured (established 131072 bind 65536)
[   32.676884] TCP reno registered
[   32.687225] checking if image is initramfs... it is
[   33.277381] Freeing initrd memory: 7307k freed
[   33.277111] audit: initializing netlink socket (disabled)
[   33.277126] audit(1238841534.576:1): initialized
[   33.277283] highmem bounce pool size: 64 pages
[   33.279078] VFS: Disk quotas dquot_6.5.1
[   33.279145] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.279257] io scheduler noop registered
[   33.279259] io scheduler anticipatory registered
[   33.279260] io scheduler deadline registered
[   33.279269] io scheduler cfq registered (default)
[   33.279275] PCI: MSI quirk detected. MSI deactivated.
[   33.279282] PCI: VIA PCI bridge detected. Disabling DAC.
[   33.279376] Boot video device is 0000:06:00.0
[   33.279504] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.279538] assign_interrupt_mode Found MSI capability
[   33.279540] Allocate Port Service[0000:00:02.0:pcie00]
[   33.279575] Allocate Port Service[0000:00:02.0:pcie02]
[   33.279655] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   33.279694] assign_interrupt_mode Found MSI capability
[   33.279696] Allocate Port Service[0000:00:03.0:pcie00]
[   33.279727] Allocate Port Service[0000:00:03.0:pcie02]
[   33.279808] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   33.279846] assign_interrupt_mode Found MSI capability
[   33.279849] Allocate Port Service[0000:00:03.1:pcie00]
[   33.279880] Allocate Port Service[0000:00:03.1:pcie02]
[   33.279961] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   33.280000] assign_interrupt_mode Found MSI capability
[   33.280002] Allocate Port Service[0000:00:03.2:pcie00]
[   33.280038] Allocate Port Service[0000:00:03.2:pcie02]
[   33.280119] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   33.280158] assign_interrupt_mode Found MSI capability
[   33.280160] Allocate Port Service[0000:00:03.3:pcie00]
[   33.280194] Allocate Port Service[0000:00:03.3:pcie02]
[   33.280444] isapnp: Scanning for PnP cards...
[   33.634165] isapnp: No Plug & Play device found
[   33.660594] Real Time Clock Driver v1.12ac
[   33.660712] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.660830] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.660954] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.661709] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.662492] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.662554] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   33.662699] PNP: No PS/2 controller found. Probing ports directly.
[   33.663054] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.663058] serio: i8042 AUX port at 0x60,0x64 irq 12
[   33.678429] mice: PS/2 mouse device common for all mice
[   33.678559] EISA: Probing bus 0 at eisa.0
[   33.678598] EISA: Detected 0 cards.
[   33.678601] cpuidle: using governor ladder
[   33.678603] cpuidle: using governor menu
[   33.678690] NET: Registered protocol family 1
[   33.678714] Using IPI No-Shortcut mode
[   33.678749] registered taskstats version 1
[   33.678881]   Magic number: 5:925:627
[   33.679055] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   33.679057] EDD information not available.
[   33.679332] Freeing unused kernel memory: 368k freed
[   33.679359] Write protecting the kernel read-only data: 806k
[   34.897806] fuse init (API version 7.9)
[   35.273958] SCSI subsystem initialized
[   35.290968] r8169 Gigabit Ethernet driver 2.2LK loaded
[   35.290996] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 36 (level, low) -> IRQ 21
[   35.291014] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   35.291026] r8169 0000:03:00.0: no MSI. Back to INTx.
[   35.291233] eth0: RTL8168b/8111b at 0xf8840000, 00:13:8f:de:f6:35, XID 38000000 IRQ 21
[   35.297688] libata version 3.00 loaded.
[   35.298833] usbcore: registered new interface driver usbfs
[   35.298855] usbcore: registered new interface driver hub
[   35.299280] usbcore: registered new device driver usb
[   35.300680] ahci 0000:02:00.0: version 3.0
[   35.300713] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 40 (level, low) -> IRQ 22
[   35.302889] USB Universal Host Controller Interface driver v3.0
[   36.300872] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   36.300877] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   36.300884] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   36.301085] scsi0 : ahci
[   36.301332] scsi1 : ahci
[   36.301395] ata1: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe100 irq 22
[   36.301399] ata2: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe180 irq 22
[   36.944452] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   36.963849] ata1.00: ATA-8: SAMSUNG HD321KJ, CP100-10, max UDMA7
[   36.963854] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   36.965846] ata1.00: configured for UDMA/133
[   37.284243] ata2: SATA link down (SStatus 0 SControl 300)
[   37.284350] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD321KJ  CP10 PQ: 0 ANSI: 5
[   37.284030] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 23
[   37.284047] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   37.284364] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[   37.284407] ehci_hcd 0000:00:10.4: irq 23, io mem 0xfbdffc00
[   37.291978] Driver 'sd' needs updating - please use bus_type methods
[   37.296110] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.296234] usb usb1: configuration #1 chosen from 1 choice
[   37.296255] hub 1-0:1.0: USB hub found
[   37.296260] hub 1-0:1.0: 8 ports detected
[   37.301280] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   37.301294] sd 0:0:0:0: [sda] Write Protect is off
[   37.301297] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.301312] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.301360] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   37.301368] sd 0:0:0:0: [sda] Write Protect is off
[   37.301370] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.301383] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.301386]  sda: sda1 sda2 sda3
[   37.349178] sd 0:0:0:0: [sda] Attached SCSI disk
[   37.353748] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   37.401317] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 24
[   37.401332] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   37.401374] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[   37.401404] uhci_hcd 0000:00:10.0: irq 24, io base 0x0000b480
[   37.401530] usb usb2: configuration #1 chosen from 1 choice
[   37.401554] hub 2-0:1.0: USB hub found
[   37.401560] hub 2-0:1.0: 2 ports detected
[   37.508211] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 25
[   37.508224] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   37.508247] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[   37.508274] uhci_hcd 0000:00:10.1: irq 25, io base 0x0000b800
[   37.508376] usb usb3: configuration #1 chosen from 1 choice
[   37.508398] hub 3-0:1.0: USB hub found
[   37.508403] hub 3-0:1.0: 2 ports detected
[   37.608144] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 23
[   37.608159] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   37.608183] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[   37.608205] uhci_hcd 0000:00:10.2: irq 23, io base 0x0000b880
[   37.608315] usb usb4: configuration #1 chosen from 1 choice
[   37.608343] hub 4-0:1.0: USB hub found
[   37.608348] hub 4-0:1.0: 2 ports detected
[   37.712033] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 26
[   37.712039] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   37.712056] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[   37.712078] uhci_hcd 0000:00:10.3: irq 26, io base 0x0000bc00
[   37.712163] usb usb5: configuration #1 chosen from 1 choice
[   37.712180] hub 5-0:1.0: USB hub found
[   37.712184] hub 5-0:1.0: 2 ports detected
[   37.816968] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[   37.816983] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 41 (level, low) -> IRQ 27
[   37.817035] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   37.817114] scsi2 : pata_jmicron
[   37.817165] scsi3 : pata_jmicron
[   37.817189] ata3: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 27
[   37.817192] ata4: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 27
[   37.823953] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   37.999982] usb 2-1: configuration #1 chosen from 1 choice
[   38.139562] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 23
[   38.139612] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[   38.141582] sata_via 0000:00:0f.0: version 2.3
[   38.141593] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 23
[   38.141620] sata_via 0000:00:0f.0: routed to hard irq line 11
[   38.141659] scsi4 : sata_via
[   38.141703] scsi5 : sata_via
[   38.142729] ata5: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 23
[   38.142731] ata6: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 23
[   38.343567] ata5: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   38.555438] ata6: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   38.565028] pata_via 0000:00:0f.1: version 0.3.3
[   38.565143] scsi6 : pata_via
[   38.565207] scsi7 : pata_via
[   38.566167] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   38.566169] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   38.883609] ata7.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB02, max UDMA/33
[   38.894132] usbcore: registered new interface driver hiddev
[   38.907416] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input1
[   38.919121] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:10.0-1
[   38.947198] Fixing up Logitech keyboard report descriptor
[   38.947704] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1/input/input2
[   38.971114] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:10.0-1
[   38.971131] usbcore: registered new interface driver usbhid
[   38.971135] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   39.055384] ata7.00: configured for UDMA/33
[   39.222040] scsi 6:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB02 PQ: 0 ANSI: 5
[   39.222116] scsi 6:0:0:0: Attached scsi generic sg1 type 5
[   39.229229] Driver 'sr' needs updating - please use bus_type methods
[   39.237636] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   39.237640] Uniform CD-ROM driver Revision: 3.20
[   39.237684] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   39.320375] Attempting manual resume
[   39.320379] swsusp: Resume From Partition 8:2
[   39.320381] PM: Checking swsusp image.
[   39.320528] PM: Resume from disk failed.
[   39.361634] kjournald starting.  Commit interval 5 seconds
[   39.360529] EXT3-fs: mounted filesystem with ordered data mode.
[   44.603815] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   44.739645] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.799774] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.023422] Linux video capture interface: v2.00
[   45.152764] input: Power Button (FF) as /devices/virtual/input/input4
[   45.172237] ACPI: Power Button (FF) [PWRF]
[   45.172335] input: Power Button (CM) as /devices/virtual/input/input5
[   45.203548] ACPI: Power Button (CM) [PWRB]
[   45.243843] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   45.243915] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ 28
[   45.243974] cx88[0]: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18,autodetected]
[   45.243977] cx88[0]: TV tuner type 4, Radio tuner type -1
[   45.271793] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   45.348082] irda_init()
[   45.348105] NET: Registered protocol family 23
[   45.389602] tveeprom 1-0050: Hauppauge model 90002, rev C176, serial# 248272
[   45.389607] tveeprom 1-0050: MAC address is 00-0D-FE-03-C9-D0
[   45.389609] tveeprom 1-0050: tuner model is Thompson DTT7592 (idx 76, type 4)
[   45.389612] tveeprom 1-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   45.389615] tveeprom 1-0050: audio processor is None (idx 0)
[   45.389617] tveeprom 1-0050: decoder processor is CX882 (idx 25)
[   45.389619] tveeprom 1-0050: has no radio, has IR receiver, has no IR transmitter
[   45.389622] cx88[0]: hauppauge eeprom: model=90002
[   45.389723] input: cx88 IR (Hauppauge Nova-T DVB-T as /devices/pci0000:00/0000:00:09.0/input/input6
[   45.414078] cx88[0]/0: found at 0000:00:09.0, rev: 5, irq: 28, latency: 32, mmio: 0xf8000000
[   45.414164] cx88[0]/0: registered device video0 [v4l2]
[   45.414185] cx88[0]/0: registered device vbi0
[   45.414300] cx88[0]/2: cx2388x 8802 Driver Manager
[   45.414318] ACPI: PCI Interrupt 0000:00:09.2[A] -> GSI 16 (level, low) -> IRQ 28
[   45.414327] cx88[0]/2: found at 0000:00:09.2, rev: 5, irq: 28, latency: 32, mmio: 0xf9000000
[   45.556969] parport_pc 00:06: reported by Plug and Play ACPI
[   45.557078] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   45.769631] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   45.769639] cx88/2: registering cx8802 driver, type: dvb access: shared
[   45.769643] cx88[0]/2: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18]
[   45.769646] cx88[0]/2: cx2388x based DVB/ATSC card
[   46.019365] DVB: registering new adapter (cx88[0])
[   46.019371] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[   46.050933] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 29
[   46.064551] phy0: Selected rate control algorithm 'simple'
[   46.114833] Linux agpgart interface v0.102
[   46.325397] ACPI: PCI Interrupt 0000:80:01.0[A] -> GSI 17 (level, low) -> IRQ 30
[   46.325423] PCI: Setting latency timer of device 0000:80:01.0 to 64
[   46.356307] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   47.927015] lp0: using parport0 (interrupt-driven).
[   47.973309] Adding 1574360k swap on /dev/sda2.  Priority:-1 extents:1 across:1574360k
[   48.515323] EXT3 FS on sda1, internal journal
[   49.239833] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   49.241302] SGI XFS Quota Management subsystem
[   49.278306] XFS mounting filesystem sda3
[   49.351454] Ending clean XFS mount for filesystem: sda3
[   49.932535] ip_tables: (C) 2000-2006 Netfilter Core Team
[   50.423434] No dock devices found.
[   50.648631] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[   50.649764] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[   50.649769] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[   50.649771] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   51.418004] NET: Registered protocol family 10
[   51.418291] lo: Disabled Privacy Extensions
[   53.670390] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   53.670396] apm: disabled - APM is not SMP safe.
[   53.880284] ppdev: user-space parallel port driver
[   54.274080] audit(1238841556.431:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5528 profile="/usr/sbin/cupsd" namespace="default"
[   55.011145] Clocksource tsc unstable (delta = -110021401 ns)
[   55.744859] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   55.763512] r8169: eth0: link down
[   55.764628] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.645511] Bluetooth: Core ver 2.11
[   56.645585] NET: Registered protocol family 31
[   56.645587] Bluetooth: HCI device and connection manager initialized
[   56.645591] Bluetooth: HCI socket layer initialized
[   56.692746] Bluetooth: L2CAP ver 2.9
[   56.692751] Bluetooth: L2CAP socket layer initialized
[   56.721396] Bluetooth: RFCOMM socket layer initialized
[   56.721412] Bluetooth: RFCOMM TTY layer initialized
[   56.721414] Bluetooth: RFCOMM ver 1.8
[   61.472445] hda-intel: Invalid position buffer, using LPIB read method instead.
[  479.498909] NET: Registered protocol family 17
[  480.465675] wlan0: Initial auth_alg=0
[  480.465683] wlan0: authenticate with AP 00:23:4e:9d:a9:87
[  480.467226] wlan0: RX authentication from 00:23:4e:9d:a9:87 (alg=0 transaction=2 status=0)
[  480.467230] wlan0: authenticated
[  480.467234] wlan0: associate with AP 00:23:4e:9d:a9:87
[  480.469729] wlan0: RX AssocResp from 00:23:4e:9d:a9:87 (capab=0x11 status=0 aid=4)
[  480.469734] wlan0: associated
[  480.469772] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  480.469777] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  480.469781] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  480.469784] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  480.471016] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  480.720819] padlock: VIA PadLock not detected.
[  492.210024] wlan0: no IPv6 routers present

```

/etc/apt/sources.list
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://packages.medibuntu.org/ hardy free non-free

#globalmenu
#deb http://ppa.launchpad.net/globalmenu-team/ubuntu intrepid main

#mythexport
deb http://ppa.launchpad.net/mythbuntu-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/mythbuntu-testing/ubuntu hardy main

```

xorg.conf
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

I promise that I have done lots of searching before posting this. Apologies if the solution is already known.

---

### Post by nmsmith on 2009-04-05
I should add that this problem first occurred on several websites which had flash on the page. I thought it was a bug in flashplugin-nonfree (as it has several issues around the forum) and uninstalled it. This appeared to stop the crashing for a while.

However the system has become gradually more unusable over the past few days. I can't really get to a desktop session at the moment.

I have tried logging in to fluxbox too, with similar corruption as soon as I load a program.

On one attempt to load gnome I got very low colour-depth, and on another occasion when the freeze happened the mouse started moving the wrong way (right instead of down, down instead of left etc)

---

### Post by nmsmith on 2009-04-05
I have made even more discoveries:

I have tried booting a USB edition of Jaunty UNR, as I had it handy. The display was buggy and eventually froze on that too. I hadn't installed openssh-server so was unable to tell what the Xorg process was doing.

I then tried again with the very 8.04 live CD that I originally installed this system from. On loading the Gnome desktop the screen froze, with only the mouse movable.

So is this a hardware issue?

The cards I have installed are:
Nvidia GeForce 6150 PCIE
Belkin Wi-fi PCI
Hauppauge Nova-T

The only evidence that singles any one out is the visual corruptions pointing to the video card. Are there diagnostic programs I can run? When the system is frozen I can still ssh in. Is there a way to test the cards there and then, or to tell which one might have frozen? Otherwise, of course it may be the motherboard or the processor, but being able to ssh in would suggest that they're not having problems.

Any advice is welcome.

---

### Post by nmsmith on 2009-04-05
Hmm, now it's stopped booting altogether and I'm getting a video-memory error beep from the bios. Problem sorted I guess.

Heck, it's been a blast posting four times on my own support 'blog'. Thanks for reading; you've been a great audience, but I feel that I have to move on in my life, like buying a new video card.

---

### Post by nmsmith on 2009-04-16
A new graphics card didn't fix it (in fact it caused more problems still, as I bought a GeForce 9500GT, which isn't very well supported by Hardy) but buying a new motherboard did.

Annoying.

---

### Post by lavinog on 2009-04-16
So did the motherboard fix it?
I would have recommended doing a memory test.
Sometimes reseating the memory modules can do wonders

---

### Post by nmsmith on 2009-04-17
Well, something fixed it, among the many changes I tried. Now it's running happily with the new motherboard and the old graphics card (although I'm frustrated because the old motherboard was cheaper and yet had more SATA and IDE channels).

Memtest86 (on the live CD) did one complete pass with no errors.

The problems I was getting in /var/log/messages and dmesg (after the above posts, I'm afraid) were occasional complaints about the SATA ports, and frequent complaints about the PCIE slots. As my old motherboard has the SATAII slots driven from the PCIE controller, rather than the south bridge, this suggests that there was a common link, and that hopefully the motherboard (or its PCIE controller) was at fault.

I only discovered this fact about the SATAII slots in the manual after removing it. I think I could have tested it by plugging my hard disk into the SATA (1) slots and seeing whether that cleared anything up.

I really hope it was an unrecoverable error, because I don't want to have to replace the old motherboard, it's such a big job (even if it would save me £50).

---

### Post by ibuclaw on 2009-04-17
I had a similar problem with my first Desktop Linux Machine too back in the day, only it was just the PCI interface with the Atheros wireless card. As soon as  small amount of network activity started, BAM, it deadlocked.

Thrown out the WinFast Motherboard and replaced it with an AMiTrends ... have never had an issue since (4 years) using the exact same peripherals.


Although, knowing what I know now. It may have only taken a few tweaks in the boot and modprobe config files to fix it.

Disable apci in the boot line of /boot/grub/menu.lst ... give each PCI/PCI-E device a static IRQ Line in the /etc/modprobe.d configuration.

---

### Post by nmsmith on 2009-04-18
Without wanting to sound sarcastic (because I'm not!): it's easy to say that now... If I'd known about the way IRQ is assigned, and that it is easy enough to modify it, then I would have fiddled about with grub and modprobe. But the new mobo is now safely installed, and the old one is sitting in a box, and I have no spare hardware to test it with. Ah well. Thanks for the info.

---

