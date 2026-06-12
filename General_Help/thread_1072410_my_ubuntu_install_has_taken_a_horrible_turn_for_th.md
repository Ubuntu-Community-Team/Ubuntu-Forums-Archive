---
title: "my ubuntu install has taken a horrible turn for the worse"
date: 2009-02-17
forum: General Help
---

### Post by Embiggens on 2009-02-17
When I started up my computer today (ubuntu 8.04 on a dell inspiron 1720), I encountered some serious new  problems. (1) My nvidia driver failed to install.  Usually that's not a big problem, that happens sometimes and I need to make sure the generic drivers aren't getting in the way and reinstall the nvidia driver. However, in this case I can't fix that.  (2) My ethernet appears to not be installing correctly.  It stalls on negotiating address. (my windows partition does this fine)

I would assume there are other hardware interface issues, as this appears to be something general and horrible.

So here's what I changed before I shutdown the computer last time: (1) removed usb 2.0 module ("rmmod ehci_hc"). I had to do this get my stupid zune to not crash my vmware windows xp install.
(2) 'apt-get update' and 'apt-get dist-upgrade'.  I can't remember what it upgraded...maybe something involving 'hal'?

Here's my 'dmesg' output. Please please any help would be greatly appreciated!

```
 [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:13:11 UTC 2009 (Ubuntu 2.6.24-23.48-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe92400 (usable)
[    0.000000]  BIOS-e820: 00000000dfe92400 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100002000 - 0000000120000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 6400 pages used for memmap
[    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FBBF0 checksum 0
[    0.000000] ACPI: RSDP 000FBBF0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT DFE93E00, 005C (r1 DELL    M08     27D70810 ASL        61)
[    0.000000] ACPI: FACP DFE93C9C, 00F4 (r4 DELL    M08     27D70810 ASL        61)
[    0.000000] ACPI: DSDT DFE94400, 565E (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS DFEA2C00, 0040
[    0.000000] ACPI: HPET DFE93F00, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC DFE94000, 0068 (r1 DELL    M08     27D70810 ASL        47)
[    0.000000] ACPI: MCFG DFE93FC0, 003E (r16 DELL    M08     27D70810 ASL        61)
[    0.000000] ACPI: SLIC DFE9409C, 0176 (r1 DELL    M08     27D70810 ASL        61)
[    0.000000] ACPI: BOOT DFE93BC0, 0028 (r1 DELL    M08     27D70810 ASL        61)
[    0.000000] ACPI: SSDT DFE925BC, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at e2000000 (gap: e0000000:14000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1040384
[    0.000000] Kernel command line: root=UUID=1e85828f-73ea-4b62-84f3-aa120a603c32 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2193.938 MHz processor.
[   12.050571] Console: colour VGA+ 80x25
[   12.050574] console [tty0] enabled
[   12.050845] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.051102] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.213067] Memory: 3621740k/4194304k available (2179k kernel code, 45528k reserved, 1008k data, 368k init, 2751048k highmem)
[   12.213073] virtual kernel memory layout:
[   12.213073]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   12.213074]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.213075]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   12.213076]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   12.213077]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   12.213077]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   12.213078]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[   12.213081] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.213114] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   12.213232] hpet clockevent registered
[   12.293109] Calibrating delay using timer specific routine.. 4392.69 BogoMIPS (lpj=8785389)
[   12.293127] Security Framework initialized
[   12.293132] SELinux:  Disabled at boot.
[   12.293143] AppArmor: AppArmor initialized
[   12.293146] Failure registering capabilities with primary security module.
[   12.293153] Mount-cache hash table entries: 512
[   12.293251] Initializing cgroup subsys ns
[   12.293256] Initializing cgroup subsys cpuacct
[   12.293265] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000001
[   12.293270] monitor/mwait feature present.
[   12.293271] using mwait in idle threads.
[   12.293274] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.293276] CPU: L2 cache: 4096K
[   12.293278] CPU: Physical Processor ID: 0
[   12.293280] CPU: Processor Core ID: 0
[   12.293281] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e3bd 00000000 00000001 00000001
[   12.293289] Compat vDSO mapped to ffffe000.
[   12.293299] Checking 'hlt' instruction... OK.
[   12.309396] SMP alternatives: switching to UP code
[   12.310696] Early unpacking initramfs... done
[   12.585113] ACPI: Core revision 20070126
[   12.585147] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.588317] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[   12.588329] SMP alternatives: switching to SMP code
[   12.588895] Booting processor 1/1 eip 3000
[   12.599277] Initializing CPU#1
[   12.676481] Calibrating delay using timer specific routine.. 4387.68 BogoMIPS (lpj=8775376)
[   12.676486] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000001
[   12.676490] monitor/mwait feature present.
[   12.676492] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.676493] CPU: L2 cache: 4096K
[   12.676495] CPU: Physical Processor ID: 0
[   12.676496] CPU: Processor Core ID: 1
[   12.676497] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e3bd 00000000 00000001 00000001
[   12.677109] CPU1: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[   12.677128] Total of 2 processors activated (8780.38 BogoMIPS).
[   12.677323] ENABLING IO-APIC IRQs
[   12.677508] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.824328] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   12.844307] Brought up 2 CPUs
[   12.844327] CPU0 attaching sched-domain:
[   12.844329]  domain 0: span 03
[   12.844330]   groups: 01 02
[   12.844333] CPU1 attaching sched-domain:
[   12.844334]  domain 0: span 03
[   12.844335]   groups: 02 01
[   12.844496] net_namespace: 64 bytes
[   12.844505] Booting paravirtualized kernel on bare hardware
[   12.844870] Time:  9:26:08  Date: 02/17/09
[   12.844891] NET: Registered protocol family 16
[   12.845028] EISA bus registered
[   12.845031] ACPI: bus type pci registered
[   12.855628] PCI: PCI BIOS revision 2.10 entry at 0xfad46, last bus=14
[   12.855630] PCI: Using configuration type 1
[   12.855642] Setting up standard PCI resources
[   12.862460] ACPI: EC: Look up EC in DSDT
[   12.900293] ACPI: Interpreter enabled
[   12.900296] ACPI: (supports S0 S3 S4 S5)
[   12.900305] ACPI: Using IOAPIC for interrupt routing
[   12.918324] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.919218] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   12.919222] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[   12.920419] PCI: Transparent bridge - 0000:00:1e.0
[   12.920464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.920821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   12.920944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   12.921025] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   12.921121] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   12.921217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   12.929885] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[   12.929980] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[   12.930071] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[   12.930162] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[   12.930253] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   12.930346] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   12.930439] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   12.930524] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   12.930633] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.930654] pnp: PnP ACPI init
[   12.930660] ACPI: bus type pnp registered
[   12.962924] pnpacpi: exceeded the max number of mem resources: 12
[   12.963086] pnp: PnP ACPI: found 12 devices
[   12.963088] ACPI: ACPI bus type pnp unregistered
[   12.963090] PnPBIOS: Disabled by ACPI PNP
[   12.963243] PCI: Using ACPI for IRQ routing
[   12.963245] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.047887] NET: Registered protocol family 8
[   13.047889] NET: Registered protocol family 20
[   13.047913] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   13.047916] hpet0: 3 64-bit timers, 14318180 Hz
[   13.048943] AppArmor: AppArmor Filesystem Enabled
[   13.051876] Time: tsc clocksource has been installed.
[   13.051882] Switched to high resolution mode on CPU 0
[   13.051965] Switched to high resolution mode on CPU 1
[   13.067835] system 00:05: ioport range 0xc80-0xcff could not be reserved
[   13.067841] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[   13.067847] system 00:09: ioport range 0x900-0x97f has been reserved
[   13.067849] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   13.067851] system 00:09: ioport range 0x1000-0x1005 has been reserved
[   13.067853] system 00:09: ioport range 0x1008-0x100f has been reserved
[   13.067857] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[   13.067859] system 00:0a: ioport range 0x1006-0x1007 has been reserved
[   13.067861] system 00:0a: ioport range 0x100a-0x1059 could not be reserved
[   13.067863] system 00:0a: ioport range 0x1060-0x107f has been reserved
[   13.067865] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[   13.067867] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[   13.067869] system 00:0a: ioport range 0x1010-0x102f has been reserved
[   13.067871] system 00:0a: ioport range 0x809-0x809 has been reserved
[   13.067876] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[   13.067878] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[   13.067880] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[   13.067882] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   13.067884] system 00:0b: iomem range 0x100000-0xdfe923ff could not be reserved
[   13.067886] system 00:0b: iomem range 0xdfe92400-0xdfefffff could not be reserved
[   13.067888] system 00:0b: iomem range 0xdff00000-0xdfffffff could not be reserved
[   13.067890] system 00:0b: iomem range 0xdff00000-0xe06fffff could not be reserved
[   13.067893] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
[   13.067895] system 00:0b: iomem range 0xffa00000-0xffafffff has been reserved
[   13.067897] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   13.067899] system 00:0b: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   13.098159] PCI: Bridge: 0000:00:01.0
[   13.098161]   IO window: e000-efff
[   13.098164]   MEM window: fa000000-feafffff
[   13.098167]   PREFETCH window: e0000000-efffffff
[   13.098170] PCI: Bridge: 0000:00:1c.0
[   13.098171]   IO window: disabled.
[   13.098176]   MEM window: disabled.
[   13.098180]   PREFETCH window: disabled.
[   13.098185] PCI: Bridge: 0000:00:1c.1
[   13.098186]   IO window: disabled.
[   13.098192]   MEM window: f9f00000-f9ffffff
[   13.098196]   PREFETCH window: f0000000-f00fffff
[   13.098201] PCI: Bridge: 0000:00:1c.3
[   13.098204]   IO window: d000-dfff
[   13.098209]   MEM window: f9c00000-f9efffff
[   13.098213]   PREFETCH window: f0100000-f03fffff
[   13.098219] PCI: Bridge: 0000:00:1e.0
[   13.098220]   IO window: disabled.
[   13.098225]   MEM window: f9b00000-f9bfffff
[   13.098229]   PREFETCH window: disabled.
[   13.098244] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.098248] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.098270] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.098275] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.098298] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   13.098304] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.098327] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[   13.098332] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   13.098346] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.098354] NET: Registered protocol family 2
[   13.135740] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.135905] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.136223] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.136373] TCP: Hash tables configured (established 131072 bind 65536)
[   13.136375] TCP reno registered
[   13.147775] checking if image is initramfs... it is
[   13.685883] Freeing initrd memory: 7727k freed
[   13.686005] Simple Boot Flag at 0x79 set to 0x1
[   13.686468] audit: initializing netlink socket (disabled)
[   13.686478] audit(1234862768.349:1): initialized
[   13.686683] highmem bounce pool size: 64 pages
[   13.688115] VFS: Disk quotas dquot_6.5.1
[   13.688171] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.688270] io scheduler noop registered
[   13.688271] io scheduler anticipatory registered
[   13.688273] io scheduler deadline registered
[   13.688283] io scheduler cfq registered (default)
[   13.688432] Boot video device is 0000:01:00.0
[   13.688517] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.688549] assign_interrupt_mode Found MSI capability
[   13.688575] Allocate Port Service[0000:00:01.0:pcie00]
[   13.688600] Allocate Port Service[0000:00:01.0:pcie02]
[   13.688664] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.688721] assign_interrupt_mode Found MSI capability
[   13.688767] Allocate Port Service[0000:00:1c.0:pcie00]
[   13.688789] Allocate Port Service[0000:00:1c.0:pcie02]
[   13.688880] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.688938] assign_interrupt_mode Found MSI capability
[   13.688983] Allocate Port Service[0000:00:1c.1:pcie00]
[   13.689008] Allocate Port Service[0000:00:1c.1:pcie02]
[   13.689098] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   13.689156] assign_interrupt_mode Found MSI capability
[   13.689201] Allocate Port Service[0000:00:1c.3:pcie00]
[   13.689224] Allocate Port Service[0000:00:1c.3:pcie02]
[   13.689422] isapnp: Scanning for PnP cards...
[   14.043334] isapnp: No Plug & Play device found
[   14.061305] Real Time Clock Driver v1.12ac
[   14.061415] hpet_resources: 0xfed00000 is busy
[   14.061459] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.062315] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.062364] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   14.062432] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   14.065611] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.065615] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.086303] mice: PS/2 mouse device common for all mice
[   14.086380] EISA: Probing bus 0 at eisa.0
[   14.086435] EISA: Mainboard A__FFFF detected.
[   14.086459] Cannot allocate resource for EISA slot 1
[   14.086488] EISA: Detected 0 cards.
[   14.086491] cpuidle: using governor ladder
[   14.086492] cpuidle: using governor menu
[   14.086551] NET: Registered protocol family 1
[   14.086571] Using IPI No-Shortcut mode
[   14.086592] registered taskstats version 1
[   14.086692]   Magic number: 13:578:424
[   14.086738] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.086739] EDD information not available.
[   14.086878] Freeing unused kernel memory: 368k freed
[   14.086896] Write protecting the kernel read-only data: 806k
[   14.089936] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   15.248307] fuse init (API version 7.9)
[   15.263040] ACPI: SSDT DFE930F2, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   15.263198] ACPI: SSDT DFE92A88, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   15.263640] Monitor-Mwait will be used to enter C-1 state
[   15.263642] Monitor-Mwait will be used to enter C-2 state
[   15.263644] Monitor-Mwait will be used to enter C-3 state
[   15.263736] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   15.263740] ACPI: Processor [CPU0] (supports 8 throttling states)
[   15.263907] ACPI: SSDT DFE93378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   15.264051] ACPI: SSDT DFE9306D, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   15.264689] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   15.264693] ACPI: Processor [CPU1] (supports 8 throttling states)
[   15.270193] ACPI: Thermal Zone [THM] (52 C)
[   15.369953] usbcore: registered new interface driver usbfs
[   15.369970] usbcore: registered new interface driver hub
[   15.369990] usbcore: registered new device driver usb
[   15.381939] USB Universal Host Controller Interface driver v3.0
[   15.381981] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 19
[   15.381991] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   15.381995] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   15.382153] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   15.382183] uhci_hcd 0000:00:1a.0: irq 19, io base 0x00006f20
[   15.382280] usb usb1: configuration #1 chosen from 1 choice
[   15.382297] hub 1-0:1.0: USB hub found
[   15.382301] hub 1-0:1.0: 2 ports detected
[   15.487928] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[   15.487938] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   15.487942] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   15.487959] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   15.487990] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00006f00
[   15.488075] usb usb2: configuration #1 chosen from 1 choice
[   15.488092] hub 2-0:1.0: USB hub found
[   15.488095] hub 2-0:1.0: 2 ports detected
[   15.532975] SCSI subsystem initialized
[   15.591776] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[   15.591787] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   15.591791] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   15.591809] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   15.591837] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00006f80
[   15.591926] usb usb3: configuration #1 chosen from 1 choice
[   15.591943] hub 3-0:1.0: USB hub found
[   15.591946] hub 3-0:1.0: 2 ports detected
[   15.598331] libata version 3.00 loaded.
[   15.695606] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[   15.695616] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   15.695620] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   15.695639] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   15.695667] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00006f60
[   15.695753] usb usb4: configuration #1 chosen from 1 choice
[   15.695771] hub 4-0:1.0: USB hub found
[   15.695774] hub 4-0:1.0: 2 ports detected
[   15.727487] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   15.799435] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[   15.799443] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   15.799447] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   15.799464] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   15.799495] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00006f40
[   15.799582] usb usb5: configuration #1 chosen from 1 choice
[   15.799600] hub 5-0:1.0: USB hub found
[   15.799603] hub 5-0:1.0: 2 ports detected
[   15.886395] usb 1-2: configuration #1 chosen from 1 choice
[   15.887245] hub 1-2:1.0: USB hub found
[   15.888669] hub 1-2:1.0: 3 ports detected
[   15.900428] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
[   15.900438] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   15.900441] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   15.900458] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   15.904353] ehci_hcd 0000:00:1a.7: debug port 1
[   15.904359] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   15.904363] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xfed1c400
[   15.919180] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.919258] usb usb6: configuration #1 chosen from 1 choice
[   15.919275] hub 6-0:1.0: USB hub found
[   15.919278] hub 6-0:1.0: 4 ports detected
[   16.023101] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[   16.023113] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   16.023118] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   16.023148] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   16.027041] ehci_hcd 0000:00:1d.7: debug port 1
[   16.027047] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   16.027050] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfed1c000
[   16.038982] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.039063] usb usb7: configuration #1 chosen from 1 choice
[   16.039080] hub 7-0:1.0: USB hub found
[   16.039083] hub 7-0:1.0: 6 ports detected
[   16.143036] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[   16.195639] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f9bfd800-f9bfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   16.201913] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   16.201944] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   16.201955] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   16.201975] ahci 0000:00:1f.2: version 3.0
[   16.201995] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   16.202036] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   16.202038] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   16.226751] usb 1-2: USB disconnect, address 2
[   16.330500] Clocksource tsc unstable (delta = -5504401191 ns)
[   16.334796] Time: hpet clocksource has been installed.
[   16.384381] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   16.405405] usb 1-2: configuration #1 chosen from 1 choice
[   16.406412] hub 1-2:1.0: USB hub found
[   16.408355] hub 1-2:1.0: 3 ports detected
[   16.414624] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   16.414630] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   16.414637] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   16.414900] scsi0 : ahci
[   16.415080] scsi1 : ahci
[   16.415197] scsi2 : ahci
[   16.415404] ata1: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 219
[   16.415407] ata2: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb980 irq 219
[   16.415410] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 219
[   16.449973] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc000135989a1]
[   16.459119] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   16.472410] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   16.472833] ata1.00: ATA-8: FUJITSU MHY2250BH, 0085000B, max UDMA/100
[   16.472837] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   16.473411] ata1.00: configured for UDMA/100
[   16.481733] usb 4-2: configuration #1 chosen from 1 choice
[   16.566523] usb 1-2.1: new full speed USB device using uhci_hcd and address 4
[   16.595562] ata2: SATA link down (SStatus 0 SControl 0)
[   16.618114] usb 1-2.1: configuration #1 chosen from 1 choice
[   16.708004] usb 1-2.2: new full speed USB device using uhci_hcd and address 5
[   16.734690] ata3: SATA link down (SStatus 0 SControl 300)
[   16.734912] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHY2250B 0085 PQ: 0 ANSI: 5
[   16.735007] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   16.741497] Driver 'sd' needs updating - please use bus_type methods
[   16.743830] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   16.743847] sd 0:0:0:0: [sda] Write Protect is off
[   16.743850] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.743872] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.743928] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   16.743942] sd 0:0:0:0: [sda] Write Protect is off
[   16.743945] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.743973] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.743975]  sda:<6>ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   16.747626] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   16.747635] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   16.787584] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   16.787602] b44.c:v2.0
[   16.807864] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:af:54:59
[   16.811703] ata_piix 0000:00:1f.1: version 2.12
[   16.811715] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   16.811745] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   16.812085] scsi3 : ata_piix
[   16.812380] usb 1-2.2: configuration #1 chosen from 1 choice
[   16.812399] scsi4 : ata_piix
[   16.812921] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   16.812924] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   16.824586]  sda1 sda2 < sda5 sda6 sda7 sda8 > sda3
[   16.893365] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.896422] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   17.018028] usb 1-2.3: new full speed USB device using uhci_hcd and address 6
[   17.148451] ata4.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D200, max UDMA/33
[   17.148931] usb 1-2.3: configuration #1 chosen from 1 choice
[   17.157394] usbcore: registered new interface driver hiddev
[   17.208205] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /devices/pci0000:00/0000:00:1d.1/usb4/4-2/4-2:1.0/input/input2
[   17.212658] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:00:1d.1-2
[   17.216567] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.2/1-2.2:1.0/input/input3
[   17.229466] input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2
[   17.234668] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.3/1-2.3:1.0/input/input4
[   17.248561] input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3
[   17.248579] usbcore: registered new interface driver usbhid
[   17.248583] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   17.268654] ata4.00: configured for UDMA/33
[   17.268748] ata5: port disabled. ignoring.
[   17.269652] scsi 3:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D200 PQ: 0 ANSI: 5
[   17.269746] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   17.275111] Driver 'sr' needs updating - please use bus_type methods
[   17.283640] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   17.283644] Uniform CD-ROM driver Revision: 3.20
[   17.283702] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   17.330658] Attempting manual resume
[   17.330660] swsusp: Resume From Partition 8:7
[   17.330661] PM: Checking swsusp image.
[   17.330794] PM: Resume from disk failed.
[   17.381014] kjournald starting.  Commit interval 5 seconds
[   17.381046] EXT3-fs: mounted filesystem with ordered data mode.
[   25.203862] Adding 1951856k swap on /dev/sda7.  Priority:-1 extents:1 across:1951856k
[   25.510098] EXT3 FS on sda8, internal journal
[   26.143829] kjournald starting.  Commit interval 5 seconds
[   26.144189] EXT3 FS on sda3, internal journal
[   26.144195] EXT3-fs: mounted filesystem with ordered data mode.
[   31.342369] /dev/vmmon[5241]: Module vmmon: registered with major=10 minor=165
[   31.342379] /dev/vmmon[5241]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
[   31.342382] /dev/vmmon[5241]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
[   31.342384] /dev/vmmon[5241]: Module vmmon: initialized
[   31.446487] /dev/vmci[5253]: VMCI: Driver initialized.
[   31.446519] /dev/vmci[5253]: Module vmci: registered with major=10 minor=63
[   31.446521] /dev/vmci[5253]: Module vmci: initialized
[   32.610427] /dev/vmnet: open called by PID 5814 (vmnet-dhcpd)
[   32.610438] /dev/vmnet: hub 1 does not exist, allocating memory.
[   32.610452] /dev/vmnet: port on hub 1 successfully opened
[   32.662256] /dev/vmnet: open called by PID 5818 (vmnet-netifup)
[   32.662263] /dev/vmnet: port on hub 1 successfully opened
[   32.700425] /dev/vmnet: open called by PID 5821 (vmnet-dhcpd)
[   32.700437] /dev/vmnet: hub 8 does not exist, allocating memory.
[   32.700451] /dev/vmnet: port on hub 8 successfully opened
[   32.779260] /dev/vmnet: open called by PID 5823 (vmnet-natd)
[   32.779266] /dev/vmnet: port on hub 8 successfully opened
[   32.818791] /dev/vmnet: open called by PID 5827 (vmnet-netifup)
[   32.818798] /dev/vmnet: port on hub 8 successfully opened
[   33.615076] audit(1234884399.581:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5868 profile="/usr/sbin/cupsd" namespace="default"
[   38.679518] b44: eth0: Link is up at 100 Mbps, full duplex.
[   38.679522] b44: eth0: Flow control is off for TX and off for RX.
[   38.681039] /dev/vmnet: open called by PID 5297 (vmnet-bridge)
[   38.681046] /dev/vmnet: hub 0 does not exist, allocating memory.
[   38.681054] /dev/vmnet: port on hub 0 successfully opened
[   38.681066] bridge-eth0: up
[   38.681069] bridge-eth0: attached
[   53.242219] CPU0 attaching NULL sched-domain.
[   53.242223] CPU1 attaching NULL sched-domain.
[   53.271394] CPU0 attaching sched-domain:
[   53.271398]  domain 0: span 03
[   53.271400]   groups: 01 02
[   53.271402] CPU1 attaching sched-domain:
[   53.271403]  domain 0: span 03
[   53.271405]   groups: 02 01

```

---

### Post by Embiggens on 2009-02-17
bump.  Please, I really need to fix this or I at least need a hint on how to proceed!

---

### Post by Embiggens on 2009-02-18
Umm, so I typed "depmod -a usbcore", and at least the ethernet worked.  Then I re-loaded my graphics driver, and I'm good.  Could it have been this simple, that module dependencies got globally screwed by removing the usb 2.0 driver?

---

### Post by jordan420 on 2009-05-31
dont suppose you ever got it fixed huh?

---

