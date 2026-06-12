---
title: "No sound in Kubuntu 8.04 after kernel recompile"
date: 2009-02-14
forum: General Help
---

### Post by jdb2 on 2009-02-14
I recently compiled my own flavor of the Ubuntu kernel using [this]("http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid-using-git/") guide as a reference as recommended by the Ubuntu [KernelCompile]("https://help.ubuntu.com/community/Kernel/Compile") howto. I used the latest kernel in the Hardy git tree, ( git://kernel.ubuntu.com/ubuntu/ubuntu-hardy.git ) specifically Ubuntu-2.6.24-23.49 . The only change I made to my current config was setting the build system to compile to the athlon/k7 processor type -- nothing else was changed. Upon rebooting and selecting the new kernel from the GRUB boot menu, I noticed that I had no sound and that there was a warning notification on top of the Kmix icon -- hovering over it produces the tooltip "Mixer cannot be found" - other than that everything works fine. What is strange is that 'sudo lspci -vvvv' lists the Nvidia APU ( Audio Processing Unit ) but there's no trace of it in the output of dmesg.

'sudo lspci -vvvv' output :

```
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 0c11
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (250ns min, 3000ns max)
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at e1000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
	Subsystem: ASUSTeK Computer Inc. nForce2 AC97 Audio Controler (MCP)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 5
	Region 0: I/O ports at d000 [size=256]
	Region 1: I/O ports at d400 [size=128]
	Region 2: Memory at e1080000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

dmesg output :

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-athlon (root@jdb2-Kubuntu-temp) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Sat Feb 14 11:14:05 CST 2009 (Ubuntu 2.6.24-23.49-athlon)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
[    0.000000]  BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 393200) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   393200
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   393200
[    0.000000] On node 0 totalpages: 393200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1279 pages used for memmap
[    0.000000]   HighMem zone: 162545 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F75E0 checksum 0
[    0.000000] ACPI: RSDP 000F75E0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 5FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 5FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 5FFF30C0, 4561 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 5FFF0000, 0040
[    0.000000] ACPI: APIC 5FFF7640, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390129
[    0.000000] Kernel command line: root=UUID=e9898828-666b-46e3-bc88-cd4202074e03 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1921.042 MHz processor.
[   52.368775] Console: colour VGA+ 80x25
[   52.368779] console [tty0] enabled
[   52.369365] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   52.369870] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   52.437537] Memory: 1546888k/1572800k available (2175k kernel code, 24644k reserved, 1003k data, 368k init, 655296k highmem)
[   52.437546] virtual kernel memory layout:
[   52.437547]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[   52.437549]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   52.437550]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   52.437551]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   52.437552]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   52.437554]       .data : 0xc031fe98 - 0xc041adc4   (1003 kB)
[   52.437555]       .text : 0xc0100000 - 0xc031fe98   (2175 kB)
[   52.437559] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   52.437609] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   52.517632] Calibrating delay using timer specific routine.. 3845.30 BogoMIPS (lpj=7690618)
[   52.517668] Security Framework initialized
[   52.517676] SELinux:  Disabled at boot.
[   52.517698] AppArmor: AppArmor initialized
[   52.517702] Failure registering capabilities with primary security module.
[   52.517714] Mount-cache hash table entries: 512
[   52.517863] Initializing cgroup subsys ns
[   52.517868] Initializing cgroup subsys cpuacct
[   52.517880] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   52.517889] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   52.517892] CPU: L2 Cache: 512K (64 bytes/line)
[   52.517895] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000 00000000
[   52.517906] Compat vDSO mapped to ffffe000.
[   52.517920] Checking 'hlt' instruction... OK.
[   52.533874] SMP alternatives: switching to UP code
[   52.534992] Freeing SMP alternatives: 11k freed
[   52.535111] Early unpacking initramfs... done
[   52.874079] ACPI: Core revision 20070126
[   52.874160] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   52.877039] CPU0: AMD Athlon(tm) XP 2600+ stepping 00
[   52.877057] Total of 1 processors activated (3845.30 BogoMIPS).
[   52.877252] ENABLING IO-APIC IRQs
[   52.877454] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   53.021686] Brought up 1 CPUs
[   53.021717] CPU0 attaching sched-domain:
[   53.021720]  domain 0: span 01
[   53.021722]   groups: 01
[   53.021921] net_namespace: 64 bytes
[   53.021929] Booting paravirtualized kernel on bare hardware
[   53.022415] Time: 20:51:19  Date: 02/14/09
[   53.022443] NET: Registered protocol family 16
[   53.022671] EISA bus registered
[   53.022698] ACPI: bus type pci registered
[   53.054647] PCI: PCI BIOS revision 2.10 entry at 0xfb410, last bus=3
[   53.054649] PCI: Using configuration type 1
[   53.054659] Setting up standard PCI resources
[   53.060523] ACPI: EC: Look up EC in DSDT
[   53.065385] ACPI: Interpreter enabled
[   53.065388] ACPI: (supports S0 S1 S3 S4 S5)
[   53.065403] ACPI: Using IOAPIC for interrupt routing
[   53.073975] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   53.074054] PCI: nForce2 C1 Halt Disconnect fixup
[   53.074929] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   53.075081] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   53.075342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   53.126442] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   53.126591] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   53.126740] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   53.126885] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   53.127029] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   53.127176] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   53.127322] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   53.127465] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   53.127607] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   53.127748] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   53.127889] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   53.128031] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   53.128172] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   53.128316] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   53.128457] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   53.128598] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   53.128721] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[   53.128834] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
[   53.128946] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
[   53.129057] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[   53.129168] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   53.129338] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[   53.129502] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[   53.129668] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[   53.129831] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0
[   53.129992] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
[   53.130152] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[   53.130266] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[   53.130424] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[   53.130585] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0
[   53.130747] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[   53.130909] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   53.131054] Linux Plug and Play Support v0.97 (c) Adam Belay
[   53.131092] pnp: PnP ACPI init
[   53.131099] ACPI: bus type pnp registered
[   53.135977] pnp: PnP ACPI: found 16 devices
[   53.135980] ACPI: ACPI bus type pnp unregistered
[   53.135984] PnPBIOS: Disabled by ACPI PNP
[   53.136245] PCI: Using ACPI for IRQ routing
[   53.136250] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   53.201635] NET: Registered protocol family 8
[   53.201638] NET: Registered protocol family 20
[   53.201717] AppArmor: AppArmor Filesystem Enabled
[   53.205625] Time: tsc clocksource has been installed.
[   53.213665] system 00:00: ioport range 0x4000-0x407f has been reserved
[   53.213668] system 00:00: ioport range 0x4080-0x40ff has been reserved
[   53.213671] system 00:00: ioport range 0x4400-0x447f has been reserved
[   53.213674] system 00:00: ioport range 0x4480-0x44ff has been reserved
[   53.213677] system 00:00: ioport range 0x4200-0x427f has been reserved
[   53.213680] system 00:00: ioport range 0x4280-0x42ff has been reserved
[   53.213685] system 00:01: ioport range 0x5000-0x503f has been reserved
[   53.213688] system 00:01: ioport range 0x5500-0x553f has been reserved
[   53.213694] system 00:02: iomem range 0xd7000-0xd7fff has been reserved
[   53.213697] system 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[   53.213700] system 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[   53.213703] system 00:02: iomem range 0xfc000-0xfffff could not be reserved
[   53.213706] system 00:02: iomem range 0x5fff0000-0x5fffffff could not be reserved
[   53.213709] system 00:02: iomem range 0xffff0000-0xffffffff could not be reserved
[   53.213712] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[   53.213715] system 00:02: iomem range 0x100000-0x5ffeffff could not be reserved
[   53.213718] system 00:02: iomem range 0xfec00000-0xfec00fff could not be reserved
[   53.213721] system 00:02: iomem range 0xfee00000-0xfee00fff could not be reserved
[   53.213727] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   53.244173] PCI: Bridge: 0000:00:08.0
[   53.244176]   IO window: a000-bfff
[   53.244181]   MEM window: df000000-e0ffffff
[   53.244185]   PREFETCH window: 70000000-700fffff
[   53.244190] PCI: Bridge: 0000:00:1e.0
[   53.244192]   IO window: disabled.
[   53.244195]   MEM window: dd000000-deffffff
[   53.244199]   PREFETCH window: d4000000-dbffffff
[   53.244210] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   53.244225] NET: Registered protocol family 2
[   53.281713] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   53.282078] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   53.283407] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   53.284070] TCP: Hash tables configured (established 131072 bind 65536)
[   53.284072] TCP reno registered
[   53.293780] checking if image is initramfs... it is
[   53.745619] Switched to high resolution mode on CPU 0
[   53.939686] Freeing initrd memory: 7406k freed
[   53.940412] audit: initializing netlink socket (disabled)
[   53.940429] audit(1234644679.396:1): initialized
[   53.940603] highmem bounce pool size: 64 pages
[   53.942618] VFS: Disk quotas dquot_6.5.1
[   53.942696] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   53.942838] io scheduler noop registered
[   53.942840] io scheduler anticipatory registered
[   53.942843] io scheduler deadline registered
[   53.942853] io scheduler cfq registered (default)
[   53.997586] Boot video device is 0000:03:00.0
[   53.997879] isapnp: Scanning for PnP cards...
[   54.352349] isapnp: No Plug & Play device found
[   54.382388] Real Time Clock Driver v1.12ac
[   54.382506] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   54.382650] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.382799] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   54.383379] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.383616] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   54.384469] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   54.384540] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   54.384644] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   54.384647] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   54.385071] serio: i8042 KBD port at 0x60,0x64 irq 1
[   54.389673] mice: PS/2 mouse device common for all mice
[   54.389793] EISA: Probing bus 0 at eisa.0
[   54.389814] Cannot allocate resource for EISA slot 4
[   54.389817] Cannot allocate resource for EISA slot 5
[   54.389832] EISA: Detected 0 cards.
[   54.389835] cpuidle: using governor ladder
[   54.389837] cpuidle: using governor menu
[   54.389988] NET: Registered protocol family 1
[   54.390016] Using IPI No-Shortcut mode
[   54.390050] registered taskstats version 1
[   54.390165]   Magic number: 13:487:902
[   54.390257]   hash matches device ptyvf
[   54.390327] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   54.390329] EDD information not available.
[   54.390725] Freeing unused kernel memory: 368k freed
[   54.390751] Write protecting the kernel read-only data: 803k
[   54.421471] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   55.625083] fuse init (API version 7.9)
[   56.477738] usbcore: registered new interface driver usbfs
[   56.477764] usbcore: registered new interface driver hub
[   56.490369] usbcore: registered new device driver usb
[   56.502840] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   56.503159] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   56.503167] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 16
[   56.503175] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   56.509243] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   56.564325] SCSI subsystem initialized
[   56.630745] libata version 3.00 loaded.
[   56.745971] Floppy drive(s): fd0 is 1.44M
[   56.768983] FDC 0 is a post-1991 82077
[   57.021556] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:11:2f:95:a1:98
[   57.021562] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[   57.022008] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   57.022017] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, high) -> IRQ 17
[   57.022031] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   57.022035] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   57.022311] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   57.022330] ohci_hcd 0000:00:02.0: irq 17, io mem 0xe1087000
[   57.079233] usb usb1: configuration #1 chosen from 1 choice
[   57.079260] hub 1-0:1.0: USB hub found
[   57.079270] hub 1-0:1.0: 3 ports detected
[   57.181494] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[   57.181504] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 20 (level, high) -> IRQ 18
[   57.181520] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   57.181524] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   57.181551] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   57.181570] ohci_hcd 0000:00:02.1: irq 18, io mem 0xe1082000
[   57.239176] usb usb2: configuration #1 chosen from 1 choice
[   57.239203] hub 2-0:1.0: USB hub found
[   57.239212] hub 2-0:1.0: 3 ports detected
[   57.341737] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   57.341743] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 22 (level, high) -> IRQ 16
[   57.341756] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   57.341760] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   57.341793] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   57.341827] ehci_hcd 0000:00:02.2: debug port 1
[   57.341832] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   57.341844] ehci_hcd 0000:00:02.2: irq 16, io mem 0xe1083000
[   57.485029] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   57.497022] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   57.497148] usb usb3: configuration #1 chosen from 1 choice
[   57.497174] hub 3-0:1.0: USB hub found
[   57.497180] hub 3-0:1.0: 6 ports detected
[   57.601588] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   57.601598] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [APC2] -> GSI 17 (level, high) -> IRQ 19
[   57.601643] skge 1.13 addr 0xe0000000 irq 19 chip Yukon-Lite rev 7
[   57.601964] skge eth1: addr 00:11:2f:95:93:de
[   57.602123] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   57.605042] sata_sil 0000:01:0b.0: version 2.3
[   57.605250] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   57.605258] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 20
[   57.606754] scsi0 : sata_sil
[   57.607134] scsi1 : sata_sil
[   57.607165] ata1: SATA max UDMA/100 mmio m512@0xe0004000 tf 0xe0004080 irq 20
[   57.607170] ata2: SATA max UDMA/100 mmio m512@0xe0004000 tf 0xe00040c0 irq 20
[   57.916975] ata1: SATA link down (SStatus 0 SControl 310)
[   58.228928] ata2: SATA link down (SStatus 0 SControl 310)
[   58.229408] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 21
[   58.229413] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [APCM] -> GSI 21 (level, high) -> IRQ 17
[   58.229421] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   58.281211] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[e1084000-e10847ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   58.293836] pata_amd 0000:00:09.0: version 0.3.10
[   58.293904] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   58.294726] scsi2 : pata_amd
[   58.295085] scsi3 : pata_amd
[   58.295765] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   58.295768] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   58.613234] ata3.00: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-120, 1.23, max UDMA/66
[   58.785126] ata3.00: configured for UDMA/66
[   58.948824] usb 3-6: new high speed USB device using ehci_hcd and address 5
[   59.082310] usb 3-6: configuration #1 chosen from 1 choice
[   59.105154] ata4.00: ATAPI: HL-DT-ST GCE-8481B, C102, max UDMA/33
[   59.277026] ata4.00: configured for UDMA/33
[   59.278822] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-ROM DVD-120  1.23 PQ: 0 ANSI: 5
[   59.279453] scsi 3:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8481B  C102 PQ: 0 ANSI: 5
[   59.292673] Driver 'sr' needs updating - please use bus_type methods
[   59.296751] sr0: scsi3-mmc drive: 94x/125x cd/rw xa/form2 cdda tray
[   59.296757] Uniform CD-ROM driver Revision: 3.20
[   59.296843] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   59.297792] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   59.297830] sr 3:0:0:0: Attached scsi CD-ROM sr1
[   59.305485] sr 2:0:0:0: Attached scsi generic sg0 type 5
[   59.305506] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   59.384768] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   59.669629] usb 2-1: configuration #1 chosen from 1 choice
[   59.976681] usb 2-2: new low speed USB device using ohci_hcd and address 3
[   60.190511] usb 2-2: configuration #1 chosen from 1 choice
[   60.204712] usbcore: registered new interface driver libusual
[   60.204823] usbcore: registered new interface driver hiddev
[   60.213545] Initializing USB Mass Storage driver...
[   60.500607] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   60.713396] usb 1-2: configuration #1 chosen from 1 choice
[   60.717307] hiddev96hidraw0: USB HID v1.10 Device [DMI      WD5000AAJB-00UHA] on usb-0000:00:02.2-6
[   60.737245] scsi4 : SCSI emulation for USB Mass Storage devices
[   60.738418] usb-storage: device found at 5
[   60.738421] usb-storage: waiting for device to settle before scanning
[   61.819098] hiddev97hidraw1: USB HID v1.10 Device [American Power Conversion Back-UPS XS  900 FW:830.E6 .D USB FW:E6 ] on usb-0000:00:02.1-1
[   61.824270] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.1/usb2/2-2/2-2:1.0/input/input2
[   61.836450] input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.1-2
[   61.844084] hiddev98hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.1-2
[   61.844107] usbcore: registered new interface driver usbhid
[   61.844111] /home/jdb2/hardy/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   61.844210] usbcore: registered new interface driver usb-storage
[   61.844214] USB Mass Storage support registered.
[   65.735973] usb-storage: device scan complete
[   65.736478] scsi 4:0:0:0: Direct-Access     DMI      WD5000AAJB-00UHA 3.53 PQ: 0 ANSI: 0
[   65.736773] scsi 4:0:0:0: Attached scsi generic sg2 type 0
[   65.743153] Driver 'sd' needs updating - please use bus_type methods
[   65.744212] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   65.745081] sd 4:0:0:0: [sda] Write Protect is off
[   65.745085] sd 4:0:0:0: [sda] Mode Sense: 86 0b 00 02
[   65.745087] sd 4:0:0:0: [sda] Assuming drive cache: write through
[   65.745826] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   65.746450] sd 4:0:0:0: [sda] Write Protect is off
[   65.746453] sd 4:0:0:0: [sda] Mode Sense: 86 0b 00 02
[   65.746455] sd 4:0:0:0: [sda] Assuming drive cache: write through
[   65.746458]  sda: sda2 sda3
[   65.763026] sd 4:0:0:0: [sda] Attached SCSI disk
[   65.921750] Attempting manual resume
[   65.921755] swsusp: Resume From Partition 8:2
[   65.921757] PM: Checking swsusp image.
[   65.922419] PM: Resume from disk failed.
[   65.975553] kjournald starting.  Commit interval 5 seconds
[   65.975566] EXT3-fs: mounted filesystem with ordered data mode.
[   74.912580] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   74.986692] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   75.134733] Linux agpgart interface v0.102
[   75.206686] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   75.206709] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5500
[   75.237078] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   75.303648] agpgart: Detected NVIDIA nForce2 chipset
[   75.307650] agpgart: AGP aperture is 64M @ 0xd0000000
[   75.324163] input: Power Button (FF) as /devices/virtual/input/input4
[   75.326603] ACPI: Power Button (FF) [PWRF]
[   75.326707] input: Power Button (CM) as /devices/virtual/input/input5
[   75.338552] ACPI: Power Button (CM) [PWRB]
[   77.864098] parport_pc 00:0c: reported by Plug and Play ACPI
[   77.864161] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   79.606200] lp0: using parport0 (interrupt-driven).
[   79.849897] Adding 20482864k swap on /dev/sda2.  Priority:-1 extents:1 across:20482864k
[   80.498969] EXT3 FS on sda3, internal journal
[   80.716517] device-mapper: uevent: version 1.0.3
[   80.716551] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   82.209384] ip_tables: (C) 2000-2006 Netfilter Core Team
[   84.278902] No dock devices found.
[   87.436889] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   87.436896] apm: overridden by ACPI.
[   87.590618] scsi5 : vhba
[   93.276089] ppdev: user-space parallel port driver
[   93.777779] audit(1234644720.254:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5853 profile="/usr/sbin/cupsd" namespace="default"
[  101.604848] skge eth1: enabling interface
[  101.650643] eth0: no link during initialization.
[  101.764675] Bluetooth: Core ver 2.11
[  101.765390] NET: Registered protocol family 31
[  101.765395] Bluetooth: HCI device and connection manager initialized
[  101.765400] Bluetooth: HCI socket layer initialized
[  101.851171] Bluetooth: L2CAP ver 2.9
[  101.851177] Bluetooth: L2CAP socket layer initialized
[  102.010390] Bluetooth: RFCOMM socket layer initialized
[  102.010408] Bluetooth: RFCOMM TTY layer initialized
[  102.010411] Bluetooth: RFCOMM ver 1.8
[  103.291619] skge eth1: Link is up at 100 Mbps, full duplex, flow control both
[  103.850826] NET: Registered protocol family 10
[  103.851071] lo: Disabled Privacy Extensions
[  103.851576] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  105.751019] NET: Registered protocol family 17
[  109.414135] CIFS: Unknown mount option sync
[  119.000444] eth1: no IPv6 routers present

```

Does anyone know what might be causing the above?

Thanks,

jdb2

---

### Post by jdb2 on 2009-02-14
Man I feel stupid. I just need to recompile linux-(ubuntu|restricted)-modules . Sorry for the dumb question. :biggrin:

jdb2

---

