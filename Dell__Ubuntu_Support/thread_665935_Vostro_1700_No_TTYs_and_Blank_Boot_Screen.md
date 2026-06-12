---
title: "Vostro 1700 No TTYs and Blank Boot Screen"
date: 2008-01-12
forum: Dell  Ubuntu Support
---

### Post by MrObvious on 2008-01-12
Hello all. I've been playing with Ubuntu and I actually got Gutsy 64 bit to load. Now I want several things fixed:

1) When I load Ubuntu, the screen gets to kinit: no resume image, doing normal boot... and then doesn't display anything until I load Grub, in which case I can log in fine and everything. Using the nosplash option *does* work, but isn't pretty. :D
2) I don't have any TTYs. When I push CTRL+ALT+(F2-F6) it is blank. CTRL+ALT+F1 shows the kinit error stated in # 1. I can get back to X fine from CTRL+ALT+F7.
3) Rebooting doesn't seem to work, it hangs. I haven't given it a while to see if it's just me but if anyone has any ideas shoot them my way.

Fourtinately I'm more experienced than most people and could search and find solutions for video, sound, and wi-fi. :D If you're reading this getting jealous with me being able to get it working, send me a PM or reply here and I'll help ya out with it.

Thanks,

Paul

P.S., here is DMESG if it's helpful:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] Command line: root=UUID=831ebf03-195a-4a1b-9410-1ca4021fbb74 ro quiet splash top
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe92400 (usable)
[    0.000000]  BIOS-e820: 000000007fe92400 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 155) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 523922) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FBBF0 checksum 0
[    0.000000] ACPI: RSDP 000FBBF0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7FE93E00, 005C (r1 DELL    M08     27D7060E ASL        61)
[    0.000000] ACPI: FACP 7FE93C9C, 00F4 (r4 DELL    M08     27D7060E ASL        61)
[    0.000000] ACPI: DSDT 7FE94400, 5615 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7FEA2C00, 0040
[    0.000000] ACPI: HPET 7FE93F00, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7FE94000, 0068 (r1 DELL    M08     27D7060E ASL        47)
[    0.000000] ACPI: MCFG 7FE93FC0, 003E (r16 DELL    M08     27D7060E ASL        61)
[    0.000000] ACPI: SLIC 7FE9409C, 0176 (r1 DELL    M08     27D7060E ASL        61)
[    0.000000] ACPI: BOOT 7FE93BC0, 0028 (r1 DELL    M08     27D7060E ASL        61)
[    0.000000] ACPI: SSDT 7FE92A35, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fe92000
[    0.000000] Entering add_active_range(0, 0, 155) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 523922) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fe92000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      155
[    0.000000]     0:      256 ->   523922
[    0.000000] On node 0 totalpages: 523821
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1127 pages reserved
[    0.000000]   DMA zone: 2812 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7106 pages used for memmap
[    0.000000]   DMA32 zone: 512720 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:74000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515532
[    0.000000] Kernel command line: root=UUID=831ebf03-195a-4a1b-9410-1ca4021fbb74 ro quiet splash top
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   11.295080] time.c: Detected 1595.999 MHz processor.
[   11.297613] Console: colour VGA+ 80x25
[   11.297639] Checking aperture...
[   11.297654] Calgary: detecting Calgary via BIOS EBDA area
[   11.297657] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   11.321590] Memory: 2054740k/2095688k available (2274k kernel code, 40544k reserved, 1181k data, 296k init)
[   11.321649] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   11.400317] Calibrating delay using timer specific routine.. 3195.97 BogoMIPS (lpj=6391947)
[   11.400357] Security Framework v1.0.0 initialized
[   11.400366] SELinux:  Disabled at boot.
[   11.400681] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   11.402113] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.402778] Mount-cache hash table entries: 256
[   11.402954] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.402959] CPU: L2 cache: 2048K
[   11.402963] CPU 0/0 -> Node 0
[   11.402965] using mwait in idle threads.
[   11.402968] CPU: Physical Processor ID: 0
[   11.402971] CPU: Processor Core ID: 0
[   11.402980] CPU0: Thermal monitoring enabled (TM2)
[   11.402994] SMP alternatives: switching to UP code
[   11.403329] Early unpacking initramfs... done
[   11.951458] ACPI: Core revision 20070126
[   11.951519] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.997053] Using local APIC timer interrupts.
[   12.059655] result 12468734
[   12.059657] Detected 12.468 MHz APIC timer.
[   12.059768] SMP alternatives: switching to SMP code
[   12.059862] Booting processor 1/2 APIC 0x1
[   12.070259] Initializing CPU#1
[   12.147608] Calibrating delay using timer specific routine.. 3192.06 BogoMIPS (lpj=6384127)
[   12.147618] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.147621] CPU: L2 cache: 2048K
[   12.147625] CPU 1/1 -> Node 0
[   12.147628] CPU: Physical Processor ID: 0
[   12.147630] CPU: Processor Core ID: 1
[   12.147638] CPU1: Thermal monitoring enabled (TM2)
[   12.148096] Intel(R) Core(TM)2 Duo CPU     T5470  @ 1.60GHz stepping 0d
[   12.151621] Brought up 2 CPUs
[   12.292633] migration_cost=17
[   12.292854] NET: Registered protocol family 16
[   12.292960] ACPI: bus type pci registered
[   12.292969] PCI: Using configuration type 1
[   12.302927] ACPI: EC: Look up EC in DSDT
[   12.363060] ACPI: Interpreter enabled
[   12.363066] ACPI: (supports S0 S3 S4 S5)
[   12.363090] ACPI: Using IOAPIC for interrupt routing
[   12.392870] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.392887] PCI: Probing PCI hardware (bus 00)
[   12.395798] PCI: Transparent bridge - 0000:00:1e.0
[   12.395925] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.396702] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   12.396942] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   12.397098] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   12.397290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   12.397471] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   12.397651] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   12.415028] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[   12.415201] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[   12.415411] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[   12.415581] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *4
[   12.415749] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   12.415921] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   12.416093] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   12.416248] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   12.416419] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.416437] pnp: PnP ACPI init
[   12.416448] ACPI: bus type pnp registered
[   12.472211] pnp: PnP ACPI: found 12 devices
[   12.472215] ACPI: ACPI bus type pnp unregistered
[   12.472282] PCI: Using ACPI for IRQ routing
[   12.472285] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.472455] NET: Registered protocol family 8
[   12.472458] NET: Registered protocol family 20
[   12.472485] PCI-GART: No AMD northbridge found.
[   12.472493] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   12.472499] hpet0: 3 64-bit timers, 14318180 Hz
[   12.473564] pnp: 00:05: ioport range 0xc80-0xcff could not be reserved
[   12.473574] pnp: 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[   12.473582] pnp: 00:09: ioport range 0x900-0x97f has been reserved
[   12.473586] pnp: 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   12.473590] pnp: 00:09: ioport range 0x1000-0x1005 has been reserved
[   12.473594] pnp: 00:09: ioport range 0x1008-0x100f has been reserved
[   12.473601] pnp: 00:0a: ioport range 0xf400-0xf4fe has been reserved
[   12.473605] pnp: 00:0a: ioport range 0x1006-0x1007 has been reserved
[   12.473609] pnp: 00:0a: ioport range 0x100a-0x1059 could not be reserved
[   12.473614] pnp: 00:0a: ioport range 0x1060-0x107f has been reserved
[   12.473618] pnp: 00:0a: ioport range 0x1080-0x10bf has been reserved
[   12.473621] pnp: 00:0a: ioport range 0x10c0-0x10df has been reserved
[   12.473625] pnp: 00:0a: ioport range 0x1010-0x102f has been reserved
[   12.473633] pnp: 00:0b: iomem range 0x0-0x9efff could not be reserved
[   12.473637] pnp: 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[   12.473641] pnp: 00:0b: iomem range 0xc0000-0xd3fff has been reserved
[   12.473645] pnp: 00:0b: iomem range 0xe0000-0xfffff has been reserved
[   12.474064] PCI: Bridge: 0000:00:01.0
[   12.474068]   IO window: e000-efff
[   12.474073]   MEM window: fa000000-feafffff
[   12.474078]   PREFETCH window: e0000000-efffffff
[   12.474083] PCI: Bridge: 0000:00:1c.0
[   12.474085]   IO window: disabled.
[   12.474092]   MEM window: disabled.
[   12.474098]   PREFETCH window: disabled.
[   12.474105] PCI: Bridge: 0000:00:1c.1
[   12.474107]   IO window: disabled.
[   12.474115]   MEM window: f9f00000-f9ffffff
[   12.474121]   PREFETCH window: disabled.
[   12.474128] PCI: Bridge: 0000:00:1c.2
[   12.474132]   IO window: d000-dfff
[   12.474140]   MEM window: f9d00000-f9efffff
[   12.474146]   PREFETCH window: disabled.
[   12.474153] PCI: Bridge: 0000:00:1c.3
[   12.474158]   IO window: c000-cfff
[   12.474165]   MEM window: f9a00000-f9cfffff
[   12.474172]   PREFETCH window: f0000000-f01fffff
[   12.474180] PCI: Bridge: 0000:00:1e.0
[   12.474182]   IO window: disabled.
[   12.474190]   MEM window: f9900000-f99fffff
[   12.474195]   PREFETCH window: disabled.
[   12.474216] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.474223] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   12.474250] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.474258] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   12.474287] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   12.474295] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   12.474324] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   12.474332] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   12.474360] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   12.474368] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   12.474385] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   12.474400] NET: Registered protocol family 2
[   12.475303] Time: hpet clocksource has been installed.
[   12.511366] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   12.512431] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   12.516127] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   12.516748] TCP: Hash tables configured (established 262144 bind 65536)
[   12.516752] TCP reno registered
[   12.531441] checking if image is initramfs... it is
[   13.614865] Freeing initrd memory: 7199k freed
[   13.618915] Simple Boot Flag at 0x79 set to 0x1
[   13.619655] audit: initializing netlink socket (disabled)
[   13.619678] audit(1200176245.276:1): initialized
[   13.622565] VFS: Disk quotas dquot_6.5.1
[   13.622633] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   13.622747] io scheduler noop registered
[   13.622750] io scheduler anticipatory registered
[   13.622753] io scheduler deadline registered
[   13.622885] io scheduler cfq registered (default)
[   13.625940] Boot video device is 0000:01:00.0
[   13.626109] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.626156] assign_interrupt_mode Found MSI capability
[   13.626161] Allocate Port Service[0000:00:01.0:pcie00]
[   13.626216] Allocate Port Service[0000:00:01.0:pcie02]
[   13.626320] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.626389] assign_interrupt_mode Found MSI capability
[   13.626392] Allocate Port Service[0000:00:1c.0:pcie00]
[   13.626431] Allocate Port Service[0000:00:1c.0:pcie02]
[   13.626552] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.626621] assign_interrupt_mode Found MSI capability
[   13.626625] Allocate Port Service[0000:00:1c.1:pcie00]
[   13.626668] Allocate Port Service[0000:00:1c.1:pcie02]
[   13.626788] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   13.626857] assign_interrupt_mode Found MSI capability
[   13.626860] Allocate Port Service[0000:00:1c.2:pcie00]
[   13.626902] Allocate Port Service[0000:00:1c.2:pcie02]
[   13.627024] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   13.627093] assign_interrupt_mode Found MSI capability
[   13.627096] Allocate Port Service[0000:00:1c.3:pcie00]
[   13.627140] Allocate Port Service[0000:00:1c.3:pcie02]
[   13.656177] Real Time Clock Driver v1.12ac
[   13.656371] hpet_resources: 0xfed00000 is busy
[   13.656445] Linux agpgart interface v0.102 (c) Dave Jones
[   13.656449] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.657766] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.657937] input: Macintosh mouse button emulation as /class/input/input0
[   13.658038] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   13.661244] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.661250] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.661476] mice: PS/2 mouse device common for all mice
[   13.661636] TCP cubic registered
[   13.661718] NET: Registered protocol family 1
[   13.661993] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   13.662003] Freeing unused kernel memory: 296k freed
[   13.670320] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.913849] AppArmor: AppArmor initialized<5>audit(1200176246.568:2):  type=1505 info="AppArmor initialized" pid=1282
[   14.937371] fuse init (API version 7.8)
[   14.945982] Failure registering capabilities with primary security module.
[   14.970579] ACPI: SSDT 7FE92F01, 04B6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   14.970994] Monitor-Mwait will be used to enter C-1 state
[   14.970998] Monitor-Mwait will be used to enter C-2 state
[   14.971002] Monitor-Mwait will be used to enter C-3 state
[   14.971007] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   14.971014] ACPI: Processor [CPU0] (supports 8 throttling states)
[   14.971339] ACPI: SSDT 7FE933B7, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   14.988882] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   14.988891] ACPI: Processor [CPU1] (supports 8 throttling states)
[   15.003456] ACPI: Thermal Zone [THM] (33 C)
[   15.661196] usbcore: registered new interface driver usbfs
[   15.661230] usbcore: registered new interface driver hub
[   15.661260] usbcore: registered new device driver usb
[   15.662524] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 22
[   15.663301] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   15.663310] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   15.663481] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   15.663527] ehci_hcd 0000:00:1a.7: debug port 1
[   15.663535] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   15.663552] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[   15.667437] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.667587] usb usb1: configuration #1 chosen from 1 choice
[   15.667627] hub 1-0:1.0: USB hub found
[   15.667642] hub 1-0:1.0: 4 ports detected
[   15.676717] USB Universal Host Controller Interface driver v3.0
[   15.768457] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   15.769216] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   15.769224] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   15.769282] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   15.769332] ehci_hcd 0000:00:1d.7: debug port 1
[   15.769340] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   15.769354] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[   15.773233] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.773363] usb usb2: configuration #1 chosen from 1 choice
[   15.773401] hub 2-0:1.0: USB hub found
[   15.773411] hub 2-0:1.0: 6 ports detected
[   15.783843] SCSI subsystem initialized
[   15.790407] libata version 2.21 loaded.
[   15.876342] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 20
[   15.876358] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   15.876364] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   15.876394] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   15.876428] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[   15.876563] usb usb3: configuration #1 chosen from 1 choice
[   15.876599] hub 3-0:1.0: USB hub found
[   15.876607] hub 3-0:1.0: 2 ports detected
[   15.980163] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   15.980179] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   15.980184] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   15.980213] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   15.980250] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[   15.980384] usb usb4: configuration #1 chosen from 1 choice
[   15.980419] hub 4-0:1.0: USB hub found
[   15.980427] hub 4-0:1.0: 2 ports detected
[   16.018239] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   16.018255] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   16.018261] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   16.018299] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   16.018332] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[   16.018479] usb usb5: configuration #1 chosen from 1 choice
[   16.018514] hub 5-0:1.0: USB hub found
[   16.018523] hub 5-0:1.0: 2 ports detected
[   16.022026] usb 2-6: new high speed USB device using ehci_hcd and address 2
[   16.043615] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
[   16.043630] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   16.043635] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   16.043672] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   16.043704] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[   16.043839] usb usb6: configuration #1 chosen from 1 choice
[   16.043874] hub 6-0:1.0: USB hub found
[   16.043882] hub 6-0:1.0: 2 ports detected
[   16.109776] usb 2-6: configuration #1 chosen from 1 choice
[   16.147520] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
[   16.147537] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   16.147543] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   16.147576] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   16.147610] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[   16.147753] usb usb7: configuration #1 chosen from 1 choice
[   16.147792] hub 7-0:1.0: USB hub found
[   16.147800] hub 7-0:1.0: 2 ports detected
[   16.252736] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[   16.349248] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f99fd800-f99fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   16.353347] ata_piix 0000:00:1f.1: version 2.11
[   16.353414] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   16.353457] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   16.353627] scsi0 : ata_piix
[   16.353683] scsi1 : ata_piix
[   16.353956] ata1: PATA max UDMA/100 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x0000000000016fa0 irq 14
[   16.353962] ata2: PATA max UDMA/100 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x0000000000016fa8 irq 15
[   16.408971] ata1.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
[   16.424251] ata1.00: configured for UDMA/33
[   16.424289] ata2: port disabled. ignoring.
[   16.425576] scsi 0:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
[   16.425694] b44.c:v1.01 (Jun 16, 2006)
[   16.425716] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   16.429282] eth0: Broadcom 4400 10/100BaseT Ethernet 00:1c:23:8a:ea:38
[   16.429593] ahci 0000:00:1f.2: version 2.2
[   16.429619] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   16.430346] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match
[   16.479039] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   16.479046] Uniform CD-ROM driver Revision: 3.20
[   16.479394] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   16.483636] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   16.545571] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[314fc000231d3d81]
[   16.559372] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[   16.559378] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   16.559386] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   16.559542] scsi2 : ahci
[   16.559626] scsi3 : ahci
[   16.559686] scsi4 : ahci
[   16.560060] ata3: SATA max UDMA/133 cmd 0xffffc20000abc900 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   16.560064] ata4: DUMMY
[   16.560069] ata5: SATA max UDMA/133 cmd 0xffffc20000abca00 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   16.581792] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   16.582026] ata3.00: ATA-7: ST9160821AS, 3.CDD, max UDMA/133
[   16.582032] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   16.582364] ata3.00: configured for UDMA/133
[   16.597342] ata5: SATA link down (SStatus 0 SControl 300)
[   16.597482] scsi 2:0:0:0: Direct-Access     ATA      ST9160821AS      3.CD PQ: 0 ANSI: 5
[   16.597577] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   16.606020] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   16.606036] sd 2:0:0:0: [sda] Write Protect is off
[   16.606040] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.606060] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.606122] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   16.606135] sd 2:0:0:0: [sda] Write Protect is off
[   16.606138] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.606158] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.606162]  sda: sda1 sda2 < sda5 >
[   16.623097] sd 2:0:0:0: [sda] Attached SCSI disk
[   16.772406] Attempting manual resume
[   16.772410] swsusp: Resume From Partition 8:5
[   16.772413] PM: Checking swsusp image.
[   16.772595] PM: Resume from disk failed.
[   16.816952] kjournald starting.  Commit interval 5 seconds
[   16.816967] EXT3-fs: mounted filesystem with ordered data mode.
[   19.721785] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.725354] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.775764] input: PC Speaker as /class/input/input2
[   20.222038] input: PS/2 Mouse as /class/input/input3
[   20.239096] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   20.422677] ieee80211_crypt: registered algorithm 'NULL'
[   20.425794] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   20.425799] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   20.436752] sdhci: Secure Digital Host Controller Interface driver
[   20.436758] sdhci: Copyright(c) Pierre Ossman
[   20.436825] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
[   20.436848] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 18
[   20.437693] mmc0: SDHCI at 0xf99fd400 irq 18 DMA
[   20.458118] Linux video capture interface: v2.00
[   20.525199] nvidia: module license 'NVIDIA' taints kernel.
[   20.779169] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.779184] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   20.779303] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   20.796695] bcm43xx driver
[   20.796830] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   20.796849] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   20.820583] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   20.821122] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   20.821207] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   20.821212] uvcvideo: Failed to initialize the device (-5).
[   20.821242] usbcore: registered new interface driver uvcvideo
[   20.821246] USB Video Class driver (v0.1.0)
[   20.988118] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   20.988885] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   21.384607] lp: driver loaded but no devices found
[   21.602660] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
[   21.712967] EXT3 FS on sda1, internal journal
[   22.845066] input: Lid Switch as /class/input/input5
[   22.845096] ACPI: Lid Switch [LID]
[   22.845149] input: Power Button (CM) as /class/input/input6
[   22.845173] ACPI: Power Button (CM) [PBTN]
[   22.845224] input: Sleep Button (CM) as /class/input/input7
[   22.845242] ACPI: Sleep Button (CM) [SBTN]
[   22.952614] ACPI: Battery Slot [BAT0] (battery present)
[   22.992908] ACPI: AC Adapter [AC] (off-line)
[   23.006301] No dock devices found.
[   23.045858] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   23.057873] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   23.057991] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   24.233065] ppdev: user-space parallel port driver
[   24.458580] audit(1200176264.553:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5267 profile="/usr/sbin/cupsd"
[   25.454751] Failure registering capabilities with primary security module.
[   25.600182] Bluetooth: Core ver 2.11
[   25.600245] NET: Registered protocol family 31
[   25.600248] Bluetooth: HCI device and connection manager initialized
[   25.600253] Bluetooth: HCI socket layer initialized
[   25.614546] Bluetooth: L2CAP ver 2.8
[   25.614551] Bluetooth: L2CAP socket layer initialized
[   25.664048] Bluetooth: RFCOMM socket layer initialized
[   25.664165] Bluetooth: RFCOMM TTY layer initialized
[   25.664168] Bluetooth: RFCOMM ver 1.8
[   26.102141] b44: eth0: Link is up at 100 Mbps, full duplex.
[   26.102147] b44: eth0: Flow control is off for TX and off for RX.
[   29.616633] NET: Registered protocol family 17
[   33.042666] NET: Registered protocol family 10
[   33.042780] lo: Disabled Privacy Extensions
[   33.044805] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   34.403795] eth0: no IPv6 routers present
[   40.227558] UDF-fs: No VRS found
[   40.253582] ISO 9660 Extensions: Microsoft Joliet Level 3
[   40.598768] ISO 9660 Extensions: RRIP_1991A
[   54.309543] usb 5-1: new low speed USB device using uhci_hcd and address 2
[   54.342018] usb 5-1: configuration #1 chosen from 1 choice
[   54.420121] usbcore: registered new interface driver hiddev
[   54.424208] input: Logitech USB-PS/2 Optical Mouse as /class/input/input8
[   54.424916] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
[   54.424936] usbcore: registered new interface driver usbhid
[   54.424941] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[ 3054.306119] SoftMAC: Authentication timed out with 00:40:10:10:00:03
[ 3057.257060] SoftMAC: Open Authentication completed with 00:40:10:10:00:03
[ 3066.112865] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3070.299119] eth0: no IPv6 routers present
[ 3089.985165] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 3089.985173] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 3090.279392] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 3090.279400] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 3093.153124] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 3093.153132] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 3093.693097] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 3093.693105] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 3097.985167] eth0: no IPv6 routers present
[ 3126.486436] SoftMAC: Authentication timed out with 00:40:10:10:00:03
[ 3979.264720] b44: eth0: Link is down.
[ 4002.243265] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 4002.243272] b44: eth0: Flow control is off for TX and off for RX.
[ 4002.247859] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4012.705275] eth0: no IPv6 routers present
[ 4039.008613] eth0: no IPv6 routers present
[ 5416.434612] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 5426.524590] eth1: no IPv6 routers present
[ 7099.402713] SoftMAC: Open Authentication completed with 00:40:10:10:00:03
[ 7195.717125] SoftMAC: Open Authentication completed with 00:40:10:10:00:03
[ 7195.742197] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 7200.246656] SoftMAC: Open Authentication completed with 00:40:10:10:00:03
[ 7206.157208] eth1: no IPv6 routers present
[ 7210.983244] SoftMAC: Open Authentication completed with 00:40:10:10:00:03
[ 7215.395330] SoftMAC: Open Authentication completed with 00:40:10:10:00:03
[ 7217.422794] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 7230.929981] eth1: no IPv6 routers present
[ 7235.297912] eth0: no IPv6 routers present
[ 7302.830871] SoftMAC: Open Authentication completed with 00:40:10:10:00:03
[ 7316.884362] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 7332.798482] eth0: no IPv6 routers present
[ 7349.179124] eth1: no IPv6 routers present
[ 7635.010669] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[ 8284.108852] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[ 8284.256305] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[ 8284.259019] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[ 8284.259447] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 8284.259633] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[ 8284.265425] ndiswrapper: using IRQ 17
[ 8284.628856] wlan0: ethernet device 00:1c:26:26:81:87 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[ 8284.628956] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 8284.630724] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[ 8284.640501] usbcore: registered new interface driver ndiswrapper
[ 8284.730982] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 8333.071198] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 8351.033753] eth1: no IPv6 routers present
[ 8394.665045] ndiswrapper (iw_set_freq:334): setting configuration failed (00010003)
[ 8407.464964] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 8411.058094] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 8426.115363] eth1: no IPv6 routers present
[ 8460.359346] b44: eth0: Link is down.
[ 8463.356614] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 8463.356621] b44: eth0: Flow control is off for TX and off for RX.
[ 8463.360965] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 8473.530940] eth0: no IPv6 routers present
[ 9847.012578] b44: eth0: Link is down.
[ 9916.847577] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 9916.847585] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9917.714941] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 9917.714948] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9923.169497] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 9923.169503] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9924.324975] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 9924.324983] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9926.361955] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[ 9926.361962] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[ 9927.503142] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[ 9927.503150] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
```

---

### Post by natehall on 2008-01-12
I bet your having problems because you are trying to get your 64 bit chip to work with 32 bit drivers. My Dell 1420N was preloaded with 32 bit Ubuntu because of this issue. If you do manage to get your machine up and running on 64 bits  send Dell your resume and post your workarounds here!

---

### Post by MrObvious on 2008-01-12
Good guess. I'll live with it I guess as at lesat I can load Ubuntu successfully.

---

### Post by MrObvious on 2008-01-13
Unless anyone else has any ideas. :D

---

### Post by MrObvious on 2008-01-13
Ok so I guess no one has any ideas outside of seeing if better drivers become available in the future. So I'll make a new thread with workarounds for video, wi-fi, and sound.

---

### Post by soapytheclown on 2008-01-14
yes please a proper howto for the 1700 is desperately needed!! (by me anyways!!lol) look forward to it!

---

### Post by MrObvious on 2008-01-14
See if this works for you:
[https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700?highlight=%28dell%29%7C%281700%29](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700?highlight=%28dell%29%7C%281700%29)

I followed most of the stuff on here. If you have any quesitons post back.

Also 7.10 automatically should fetch BCM drivers and NVidia drivers if you enable the drivers, but I would do ndiswrapper for the wi-fi instead and blacklist the card as encryption don't work.

---

### Post by soapytheclown on 2008-01-15
> **MrObvious said:**
> See if this works for you:
[https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700?highlight=%28dell%29%7C%281700%29](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700?highlight=%28dell%29%7C%281700%29)

I followed most of the stuff on here. If you have any quesitons post back.

Also 7.10 automatically should fetch BCM drivers and NVidia drivers if you enable the drivers, but I would do ndiswrapper for the wi-fi instead and blacklist the card as encryption don't work.

hi again, well vista pissed me off again yesterday so with seeing yr link above i braved all and did a clean install of ubuntu, but i still had the persisting problem of no sound after installing the modem driver thingy off the dell page, anything  else u can recommend or anything else i should have done after the install i REALLY dont want to go back to vista.

other than that everything else has worked perfectly
but with no sound im not likley to stay with ubuntu on this laptop :(

-edit-

got it to work with the backports method but after my 2nd restart the sound has dissapeared :(

so close hopefully it'll be something simple to fix

---

### Post by MrObvious on 2008-01-16
I forget what you modprobe but I just added the module to /etc/modules. Here's my /etc/modules:
paul@paul-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
coretemp
i8k force=1
ndiswrapper

I hope that helps.

---

### Post by soapytheclown on 2008-01-17
well i got it working thanks for your help but the system just seemed far too unstable for the time being random crashes random net drop outs and not really a fan of all the "hacks" just to get it working so i reluctanly have reinstalled vista and just hope that april will sort it all out :)

---

### Post by Rever75 on 2008-01-17
Not sure what your talking about with all the "hacks"? I have had both Ubuntu and Kubuntu up and running on my Vostro 1700 along with my co-worker. The only thing we needed to do is enable linux-restricted-drivers for Nvidia. I run ndiswrapper for my wifi since the native driver gives on 1MBps verse ndiswrappers 54MBps. The only real issue was sound but easily resolved with compiling ALSA 1.0.15rc3 myself instead of using the backports. Everything works and works great. I did not need to "hack" anything. Were you tring to use the x86_64? If so I would suggest sticking to x86 since 64bit is nothing special unless you have over 4Gb of ram and use memory intensive 64bit compiled apps.

---

### Post by soapytheclown on 2008-01-18
i supose it depends on yr particular build, i noticed at the time of purchase that the US build specs were quite difffernet to the Uk ones, my wireless had regular speeds bu default but the range wasnt so great and the connection used to drop out concequently, it then wouldnt let me switch networks and resulted in some work i was copying over from the office via ssh to get corrupted, i had a load of random lockups when trying to run WoW in wine etc, ill stick with vista till ubuntu runs aswell on my laptop as it did on my desktop (which by the way has almost always been flawless) but hey april is only round the corner so no big deal!

---

### Post by MrObvious on 2008-01-21
Rever:As far as the hacks, I have to do it on Ubuntu 64 bit. Believe it or not I'm actually getting to work pretty good.

Soapy: Which wireless chip do you have? Mine is :00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

:D

---

### Post by soapytheclown on 2008-01-21
i cant get the lspci output of it cause im back vista but from the Dell website i have an:

Intel® Next-Gen Wireless-N Mini-Card - Europe

to be fair it worked out of the box jsut the range was limited compared to my vista machine, and if the signal dropped then i was unable to switch netowrks id stay locked to the dead network at 0% signal even if i moved back into a previously working range

---

