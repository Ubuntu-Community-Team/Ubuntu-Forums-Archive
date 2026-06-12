---
title: "Serious Hardy System Hangs!"
date: 2008-04-28
forum: Desktop Environments
---

### Post by MaddMatt on 2008-04-28
Hi All, 

So far the Hardy installation hasn't been too big of a trouble, minus some grub errors which weren't too difficult, the fact that none of my users were transferred from existing systems, and that multiheading is not yet operational but I digress... This is the main error:

Serious hangs. Sometimes nothing works, but sometimes the mouse works, but GDM doesn't respond, and the keyboard doesn't work, so no ctrl+alt+backspace. The TTY hotkeys are also not working in general which is very odd, and the keyboard and mouse are both USB so I don't understand why one would work and the other wouldn't. I don't have to be doing anything for it to hang, and it often happens in the middle of the night. I haven't been able to figure out what's been causing it in the logs, but here they are:

```

Apr 28 05:51:20 Sparta -- MARK --
Apr 28 06:11:20 Sparta -- MARK --
Apr 28 06:31:20 Sparta -- MARK --
Apr 28 03:04:46 Sparta syslogd 1.5.0#1ubuntu1: restart.
Apr 28 03:04:46 Sparta kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 28 03:04:46 Sparta kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 28 03:04:46 Sparta kernel: Symbols match kernel version 2.6.24.
Apr 28 03:04:46 Sparta kernel: Loaded 18336 symbols from 89 modules.
Apr 28 03:04:46 Sparta kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 28 03:04:46 Sparta kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 28 03:04:46 Sparta kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 28 03:04:46 Sparta kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 28 03:04:46 Sparta kernel: [    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
Apr 28 03:04:46 Sparta kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
Apr 28 03:04:46 Sparta kernel: [    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
Apr 28 03:04:46 Sparta kernel: [    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
Apr 28 03:04:46 Sparta kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
Apr 28 03:04:46 Sparta kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 28 03:04:46 Sparta kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Apr 28 03:04:46 Sparta kernel: [    0.000000] 1151MB HIGHMEM available.
Apr 28 03:04:46 Sparta kernel: [    0.000000] 896MB LOWMEM available.
Apr 28 03:04:46 Sparta kernel: [    0.000000] found SMP MP-table at 000ff780
Apr 28 03:04:46 Sparta kernel: [    0.000000] Zone PFN ranges:
Apr 28 03:04:46 Sparta kernel: [    0.000000]   DMA             0 ->     4096
Apr 28 03:04:46 Sparta kernel: [    0.000000]   Normal       4096 ->   229376
Apr 28 03:04:46 Sparta kernel: [    0.000000]   HighMem    229376 ->   524208
Apr 28 03:04:46 Sparta kernel: [    0.000000] Movable zone start PFN for each node
Apr 28 03:04:46 Sparta kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 28 03:04:46 Sparta kernel: [    0.000000]     0:        0 ->   524208
Apr 28 03:04:46 Sparta kernel: [    0.000000] DMI present.
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7E10 checksum 0
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: RSDP 000F7E10, 0014 (r0 ACPIAM)
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: RSDT 7FFB0000, 0034 (r1 A M I  OEMRSDT   4000724 MSFT       97)
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: FACP 7FFB0200, 0084 (r2 A M I  OEMFACP   4000724 MSFT       97)
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: DSDT 7FFB0450, 4AED (r1  4CDVT 4CDVT161      161 INTL  2002026)
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: FACS 7FFC0000, 0040
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: APIC 7FFB0390, 0078 (r1 A M I  OEMAPIC   4000724 MSFT       97)
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: MCFG 7FFB0410, 003C (r1 A M I  OEMMCFG   4000724 MSFT       97)
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: OEMB 7FFC0040, 0051 (r1 A M I  AMI_OEM   4000724 MSFT       97)
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr 28 03:04:46 Sparta kernel: [    0.000000] Processor #0 6:15 APIC version 20
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr 28 03:04:46 Sparta kernel: [    0.000000] Processor #1 6:15 APIC version 20
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 28 03:04:46 Sparta kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
Apr 28 03:04:46 Sparta kernel: [    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 28 03:04:46 Sparta kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Apr 28 03:04:46 Sparta kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Apr 28 03:04:46 Sparta kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 28 03:04:46 Sparta kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
Apr 28 03:04:46 Sparta kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 28 03:04:46 Sparta kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
Apr 28 03:04:46 Sparta kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
Apr 28 03:04:46 Sparta kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520113
Apr 28 03:04:46 Sparta kernel: [    0.000000] Kernel command line: root=UUID=79e4908b-a2d2-47e6-895b-084c0f57b6db ro quiet splash
Apr 28 03:04:46 Sparta kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 28 03:04:46 Sparta kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 28 03:04:46 Sparta kernel: [    0.000000] Initializing CPU#0
Apr 28 03:04:46 Sparta kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 28 03:04:46 Sparta kernel: [    0.000000] Detected 1607.233 MHz processor.
Apr 28 03:04:46 Sparta kernel: [   35.646050] Console: colour VGA+ 80x25
Apr 28 03:04:46 Sparta kernel: [   35.646054] console [tty0] enabled
Apr 28 03:04:46 Sparta kernel: [   35.646376] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 28 03:04:46 Sparta kernel: [   35.646665] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 28 03:04:46 Sparta kernel: [   35.745105] Memory: 2066464k/2096832k available (2157k kernel code, 29056k reserved, 998k data, 364k init, 1179328k highmem)
Apr 28 03:04:46 Sparta kernel: [   35.745112] virtual kernel memory layout:
Apr 28 03:04:46 Sparta kernel: [   35.745113]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 28 03:04:46 Sparta kernel: [   35.745115]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 28 03:04:46 Sparta kernel: [   35.745116]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 28 03:04:46 Sparta kernel: [   35.745117]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 28 03:04:46 Sparta kernel: [   35.745118]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 28 03:04:46 Sparta kernel: [   35.745119]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 28 03:04:46 Sparta kernel: [   35.745120]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 28 03:04:46 Sparta kernel: [   35.745124] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 28 03:04:46 Sparta kernel: [   35.745168] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 28 03:04:46 Sparta kernel: [   35.825184] Calibrating delay using timer specific routine.. 3216.89 BogoMIPS (lpj=6433795)
Apr 28 03:04:46 Sparta kernel: [   35.825214] Security Framework initialized
Apr 28 03:04:46 Sparta kernel: [   35.825221] SELinux:  Disabled at boot.
Apr 28 03:04:46 Sparta kernel: [   35.825236] AppArmor: AppArmor initialized
Apr 28 03:04:46 Sparta kernel: [   35.825240] Failure registering capabilities with primary security module.
Apr 28 03:04:46 Sparta kernel: [   35.825249] Mount-cache hash table entries: 512
Apr 28 03:04:46 Sparta kernel: [   35.825399] monitor/mwait feature present.
Apr 28 03:04:46 Sparta kernel: [   35.825401] using mwait in idle threads.
Apr 28 03:04:46 Sparta kernel: [   35.825405] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 28 03:04:46 Sparta kernel: [   35.825407] CPU: L2 cache: 1024K
Apr 28 03:04:46 Sparta kernel: [   35.825410] CPU: Physical Processor ID: 0
Apr 28 03:04:46 Sparta kernel: [   35.825412] CPU: Processor Core ID: 0
Apr 28 03:04:46 Sparta kernel: [   35.825424] Compat vDSO mapped to ffffe000.
Apr 28 03:04:46 Sparta kernel: [   35.825438] Checking 'hlt' instruction... OK.
Apr 28 03:04:46 Sparta kernel: [   35.841571] SMP alternatives: switching to UP code
Apr 28 03:04:46 Sparta kernel: [   35.843246] Early unpacking initramfs... done
Apr 28 03:04:46 Sparta kernel: [   36.215235] ACPI: Core revision 20070126
Apr 28 03:04:46 Sparta kernel: [   36.215278] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 28 03:04:46 Sparta kernel: [   36.652820] CPU0: Intel Genuine Intel(R) CPU            2140  @ 1.60GHz stepping 02
Apr 28 03:04:46 Sparta kernel: [   36.652837] SMP alternatives: switching to SMP code
Apr 28 03:04:46 Sparta kernel: [   36.653545] Booting processor 1/1 eip 3000
Apr 28 03:04:46 Sparta kernel: [   36.663636] Initializing CPU#1
Apr 28 03:04:46 Sparta kernel: [   36.741042] Calibrating delay using timer specific routine.. 3214.65 BogoMIPS (lpj=6429306)
Apr 28 03:04:46 Sparta kernel: [   36.741054] monitor/mwait feature present.
Apr 28 03:04:46 Sparta kernel: [   36.741057] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 28 03:04:46 Sparta kernel: [   36.741059] CPU: L2 cache: 1024K
Apr 28 03:04:46 Sparta kernel: [   36.741061] CPU: Physical Processor ID: 0
Apr 28 03:04:46 Sparta kernel: [   36.741062] CPU: Processor Core ID: 1
Apr 28 03:04:46 Sparta kernel: [   36.741467] CPU1: Intel Genuine Intel(R) CPU            2140  @ 1.60GHz stepping 02
Apr 28 03:04:46 Sparta kernel: [   36.741492] Total of 2 processors activated (6431.55 BogoMIPS).
Apr 28 03:04:46 Sparta kernel: [   36.741807] ENABLING IO-APIC IRQs
Apr 28 03:04:46 Sparta kernel: [   36.741986] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 28 03:04:46 Sparta kernel: [   36.889139] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 28 03:04:46 Sparta kernel: [   36.909152] Brought up 2 CPUs
Apr 28 03:04:46 Sparta kernel: [   36.909417] net_namespace: 64 bytes
Apr 28 03:04:46 Sparta kernel: [   36.909428] Booting paravirtualized kernel on bare hardware
Apr 28 03:04:46 Sparta kernel: [   36.909957] Time:  9:03:41  Date: 04/28/08
Apr 28 03:04:46 Sparta kernel: [   36.909985] NET: Registered protocol family 16
Apr 28 03:04:46 Sparta kernel: [   36.910190] EISA bus registered
Apr 28 03:04:46 Sparta kernel: [   36.910194] ACPI: bus type pci registered
Apr 28 03:04:46 Sparta kernel: [   36.910339] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=128
Apr 28 03:04:46 Sparta kernel: [   36.910341] PCI: Using configuration type 1
Apr 28 03:04:46 Sparta kernel: [   36.910343] Setting up standard PCI resources
Apr 28 03:04:46 Sparta kernel: [   36.922960] ACPI: Interpreter enabled
Apr 28 03:04:46 Sparta kernel: [   36.922964] ACPI: (supports S0 S1 S3 S4 S5)
Apr 28 03:04:46 Sparta kernel: [   36.922980] ACPI: Using IOAPIC for interrupt routing
Apr 28 03:04:46 Sparta kernel: [   36.930804] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 28 03:04:46 Sparta kernel: [   36.946097] ACPI: PCI Root Bridge [PCI1] (0000:80)
Apr 28 03:04:46 Sparta kernel: [   36.946407] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Apr 28 03:04:46 Sparta kernel: [   36.946525] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Apr 28 03:04:46 Sparta kernel: [   36.946640] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Apr 28 03:04:46 Sparta kernel: [   36.946754] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Apr 28 03:04:46 Sparta kernel: [   36.946868] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Apr 28 03:04:46 Sparta kernel: [   36.946983] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Apr 28 03:04:46 Sparta kernel: [   36.947097] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Apr 28 03:04:46 Sparta kernel: [   36.947212] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Apr 28 03:04:46 Sparta kernel: [   36.947341] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  1A, should be 0D [20070126]
Apr 28 03:04:46 Sparta kernel: [   36.947348] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 28 03:04:46 Sparta kernel: [   36.947380] pnp: PnP ACPI init
Apr 28 03:04:46 Sparta kernel: [   36.947388] ACPI: bus type pnp registered
Apr 28 03:04:46 Sparta kernel: [   36.951793] pnp: PnP ACPI: found 13 devices
Apr 28 03:04:46 Sparta kernel: [   36.951796] ACPI: ACPI bus type pnp unregistered
Apr 28 03:04:46 Sparta kernel: [   36.951800] PnPBIOS: Disabled by ACPI PNP
Apr 28 03:04:46 Sparta kernel: [   36.952054] PCI: Using ACPI for IRQ routing
Apr 28 03:04:46 Sparta kernel: [   36.952057] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 28 03:04:46 Sparta kernel: [   37.212991] NET: Registered protocol family 8
Apr 28 03:04:46 Sparta kernel: [   37.212994] NET: Registered protocol family 20
Apr 28 03:04:46 Sparta kernel: [   37.213059] AppArmor: AppArmor Filesystem Enabled
Apr 28 03:04:46 Sparta kernel: [   37.216983] Time: tsc clocksource has been installed.
Apr 28 03:04:46 Sparta kernel: [   37.229023] system 00:07: ioport range 0x295-0x296 has been reserved
Apr 28 03:04:46 Sparta kernel: [   37.229026] system 00:07: ioport range 0x3e0-0x3e7 has been reserved
Apr 28 03:04:46 Sparta kernel: [   37.229029] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Apr 28 03:04:46 Sparta kernel: [   37.229031] system 00:07: ioport range 0x800-0x87f has been reserved
Apr 28 03:04:46 Sparta kernel: [   37.229034] system 00:07: ioport range 0x400-0x41f has been reserved
Apr 28 03:04:46 Sparta kernel: [   37.229037] system 00:07: iomem range 0xfffffff0-0xffffffff could not be reserved
Apr 28 03:04:46 Sparta kernel: [   37.229040] system 00:07: iomem range 0xffb80000-0xffbfffff could not be reserved
Apr 28 03:04:46 Sparta kernel: [   37.229047] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
Apr 28 03:04:46 Sparta kernel: [   37.229050] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
Apr 28 03:04:46 Sparta kernel: [   37.229056] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Apr 28 03:04:46 Sparta kernel: [   37.229063] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Apr 28 03:04:46 Sparta kernel: [   37.229066] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
Apr 28 03:04:46 Sparta kernel: [   37.229069] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
Apr 28 03:04:46 Sparta kernel: [   37.229071] system 00:0b: iomem range 0x100000-0x7fffffff could not be reserved
Apr 28 03:04:46 Sparta kernel: [   37.229074] system 00:0b: iomem range 0xfff80000-0xffffffff could not be reserved
Apr 28 03:04:46 Sparta kernel: [   37.259527] PCI: Bridge: 0000:00:01.0
Apr 28 03:04:46 Sparta kernel: [   37.259529]   IO window: disabled.
Apr 28 03:04:46 Sparta kernel: [   37.259535]   MEM window: fc800000-fe8fffff
Apr 28 03:04:46 Sparta kernel: [   37.259540]   PREFETCH window: cff00000-dfefffff
Apr 28 03:04:46 Sparta kernel: [   37.259545] PCI: Bridge: 0000:00:02.0
Apr 28 03:04:46 Sparta kernel: [   37.259547]   IO window: disabled.
Apr 28 03:04:46 Sparta kernel: [   37.259552]   MEM window: fe900000-fe9fffff
Apr 28 03:04:46 Sparta kernel: [   37.259557]   PREFETCH window: disabled.
Apr 28 03:04:46 Sparta kernel: [   37.259603] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
Apr 28 03:04:46 Sparta kernel: [   37.259622] NET: Registered protocol family 2
Apr 28 03:04:46 Sparta kernel: [   37.297034] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 28 03:04:46 Sparta kernel: [   37.297278] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 28 03:04:46 Sparta kernel: [   37.297782] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 28 03:04:46 Sparta kernel: [   37.298112] TCP: Hash tables configured (established 131072 bind 65536)
Apr 28 03:04:46 Sparta kernel: [   37.298115] TCP reno registered
Apr 28 03:04:46 Sparta kernel: [   37.309152] checking if image is initramfs... it is
Apr 28 03:04:46 Sparta kernel: [   38.043979] Freeing initrd memory: 7704k freed
Apr 28 03:04:46 Sparta kernel: [   38.044880] audit: initializing netlink socket (disabled)
Apr 28 03:04:46 Sparta kernel: [   38.044896] audit(1209373421.752:1): initialized
Apr 28 03:04:46 Sparta kernel: [   38.045121] highmem bounce pool size: 64 pages
Apr 28 03:04:46 Sparta kernel: [   38.047252] VFS: Disk quotas dquot_6.5.1
Apr 28 03:04:46 Sparta kernel: [   38.047332] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 28 03:04:46 Sparta kernel: [   38.047472] io scheduler noop registered
Apr 28 03:04:46 Sparta kernel: [   38.047475] io scheduler anticipatory registered
Apr 28 03:04:46 Sparta kernel: [   38.047477] io scheduler deadline registered
Apr 28 03:04:46 Sparta kernel: [   38.047488] io scheduler cfq registered (default)
Apr 28 03:04:46 Sparta kernel: [   38.047501] PCI: VIA PCI bridge detected. Disabling DAC.
Apr 28 03:04:46 Sparta kernel: [   38.047762] assign_interrupt_mode Found MSI capability
Apr 28 03:04:46 Sparta kernel: [   38.048134] isapnp: Scanning for PnP cards...
Apr 28 03:04:46 Sparta kernel: [   38.402403] isapnp: No Plug & Play device found
Apr 28 03:04:46 Sparta kernel: [   38.429984] Real Time Clock Driver v1.12ac
Apr 28 03:04:46 Sparta kernel: [   38.430101] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 28 03:04:46 Sparta kernel: [   38.430224] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 28 03:04:46 Sparta kernel: [   38.430936] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 28 03:04:46 Sparta kernel: [   38.431750] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 28 03:04:46 Sparta kernel: [   38.431819] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 28 03:04:46 Sparta kernel: [   38.431978] PNP: No PS/2 controller found. Probing ports directly.
Apr 28 03:04:46 Sparta kernel: [   38.432368] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 28 03:04:46 Sparta kernel: [   38.432373] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 28 03:04:46 Sparta kernel: [   38.456831] mice: PS/2 mouse device common for all mice
Apr 28 03:04:46 Sparta kernel: [   38.456958] EISA: Probing bus 0 at eisa.0
Apr 28 03:04:46 Sparta kernel: [   38.457001] EISA: Detected 0 cards.
Apr 28 03:04:46 Sparta kernel: [   38.457005] cpuidle: using governor ladder
Apr 28 03:04:46 Sparta kernel: [   38.457006] cpuidle: using governor menu
Apr 28 03:04:46 Sparta kernel: [   38.457095] NET: Registered protocol family 1
Apr 28 03:04:46 Sparta kernel: [   38.457123] Using IPI No-Shortcut mode
Apr 28 03:04:46 Sparta kernel: [   38.457153] registered taskstats version 1
Apr 28 03:04:46 Sparta kernel: [   38.457263]   Magic number: 4:557:71
Apr 28 03:04:46 Sparta kernel: [   38.457334] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 28 03:04:46 Sparta kernel: [   38.457336] EDD information not available.
Apr 28 03:04:46 Sparta kernel: [   38.457506] Freeing unused kernel memory: 364k freed
Apr 28 03:04:46 Sparta kernel: [   40.275661] fuse init (API version 7.9)
Apr 28 03:04:46 Sparta kernel: [   40.305955] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Apr 28 03:04:46 Sparta kernel: [   40.305970] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Apr 28 03:04:46 Sparta kernel: [   40.679307] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Apr 28 03:04:46 Sparta kernel: [   40.693177] 8139too Fast Ethernet driver 0.9.28
Apr 28 03:04:46 Sparta kernel: [   40.693258] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 17
Apr 28 03:04:46 Sparta kernel: [   40.694142] eth0: RealTek RTL8139 at 0xc800, 00:05:1c:10:ba:0d, IRQ 17
Apr 28 03:04:46 Sparta kernel: [   40.729172] usbcore: registered new interface driver usbfs
Apr 28 03:04:46 Sparta kernel: [   40.729197] usbcore: registered new interface driver hub
Apr 28 03:04:46 Sparta kernel: [   40.733171] usbcore: registered new device driver usb
Apr 28 03:04:46 Sparta kernel: [   40.753140] USB Universal Host Controller Interface driver v3.0
Apr 28 03:04:46 Sparta kernel: [   40.753221] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 18
Apr 28 03:04:46 Sparta kernel: [   40.753232] uhci_hcd 0000:00:10.0: UHCI Host Controller
Apr 28 03:04:46 Sparta kernel: [   40.753434] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Apr 28 03:04:46 Sparta kernel: [   40.753463] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000e080
Apr 28 03:04:46 Sparta kernel: [   40.753607] usb usb1: configuration #1 chosen from 1 choice
Apr 28 03:04:46 Sparta kernel: [   40.753632] hub 1-0:1.0: USB hub found
Apr 28 03:04:46 Sparta kernel: [   40.753637] hub 1-0:1.0: 2 ports detected
Apr 28 03:04:46 Sparta kernel: [   40.812427] SCSI subsystem initialized
Apr 28 03:04:46 Sparta kernel: [   40.817720] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Apr 28 03:04:46 Sparta kernel: [   40.857195] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 19
Apr 28 03:04:46 Sparta kernel: [   40.857208] uhci_hcd 0000:00:10.1: UHCI Host Controller
Apr 28 03:04:46 Sparta kernel: [   40.857233] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Apr 28 03:04:46 Sparta kernel: [   40.857259] uhci_hcd 0000:00:10.1: irq 19, io base 0x0000e400
Apr 28 03:04:46 Sparta kernel: [   40.857375] usb usb2: configuration #1 chosen from 1 choice
Apr 28 03:04:46 Sparta kernel: [   40.857399] hub 2-0:1.0: USB hub found
Apr 28 03:04:46 Sparta kernel: [   40.857404] hub 2-0:1.0: 2 ports detected
Apr 28 03:04:46 Sparta kernel: [   40.871163] Floppy drive(s): fd0 is 1.44M
Apr 28 03:04:46 Sparta kernel: [   40.889021] FDC 0 is a post-1991 82077
Apr 28 03:04:46 Sparta kernel: [   40.961197] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 20
Apr 28 03:04:46 Sparta kernel: [   40.961210] uhci_hcd 0000:00:10.2: UHCI Host Controller
Apr 28 03:04:46 Sparta kernel: [   40.961235] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Apr 28 03:04:46 Sparta kernel: [   40.961260] uhci_hcd 0000:00:10.2: irq 20, io base 0x0000e480
Apr 28 03:04:46 Sparta kernel: [   40.961377] usb usb3: configuration #1 chosen from 1 choice
Apr 28 03:04:46 Sparta kernel: [   40.961401] hub 3-0:1.0: USB hub found
Apr 28 03:04:46 Sparta kernel: [   40.961406] hub 3-0:1.0: 2 ports detected
Apr 28 03:04:46 Sparta kernel: [   41.065173] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 21
Apr 28 03:04:46 Sparta kernel: [   41.065186] uhci_hcd 0000:00:10.3: UHCI Host Controller
Apr 28 03:04:46 Sparta kernel: [   41.065211] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Apr 28 03:04:46 Sparta kernel: [   41.065237] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000ec00
Apr 28 03:04:46 Sparta kernel: [   41.065355] usb usb4: configuration #1 chosen from 1 choice
Apr 28 03:04:46 Sparta kernel: [   41.065380] hub 4-0:1.0: USB hub found
Apr 28 03:04:46 Sparta kernel: [   41.065385] hub 4-0:1.0: 2 ports detected
Apr 28 03:04:46 Sparta kernel: [   41.169323] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 20
Apr 28 03:04:46 Sparta kernel: [   41.169341] ehci_hcd 0000:00:10.4: EHCI Host Controller
Apr 28 03:04:46 Sparta kernel: [   41.169370] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Apr 28 03:04:46 Sparta kernel: [   41.169409] ehci_hcd 0000:00:10.4: irq 20, io mem 0xfebff800
Apr 28 03:04:46 Sparta kernel: [   41.227993] usb 1-2: new full speed USB device using uhci_hcd and address 2
Apr 28 03:04:46 Sparta kernel: [   41.236994] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 28 03:04:46 Sparta kernel: [   41.237118] usb usb5: configuration #1 chosen from 1 choice
Apr 28 03:04:46 Sparta kernel: [   41.237150] hub 5-0:1.0: USB hub found
Apr 28 03:04:46 Sparta kernel: [   41.237156] hub 5-0:1.0: 8 ports detected
Apr 28 03:04:46 Sparta kernel: [   41.341165] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 21
Apr 28 03:04:46 Sparta kernel: [   41.341444] eth1: VIA Rhine II at 0xfebffc00, 00:19:66:28:42:ec, IRQ 21.
Apr 28 03:04:46 Sparta kernel: [   41.342153] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
Apr 28 03:04:46 Sparta kernel: [   41.348307] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 20
Apr 28 03:04:46 Sparta kernel: [   41.348363] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
Apr 28 03:04:46 Sparta kernel: [   41.352490] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 20
Apr 28 03:04:46 Sparta kernel: [   41.352521] sata_via 0000:00:0f.0: routed to hard irq line 5
Apr 28 03:04:46 Sparta kernel: [   41.353128] scsi0 : sata_via
Apr 28 03:04:46 Sparta kernel: [   41.353365] scsi1 : sata_via
Apr 28 03:04:46 Sparta kernel: [   41.354666] ata1: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd480 irq 20
Apr 28 03:04:46 Sparta kernel: [   41.354669] ata2: SATA max UDMA/133 cmd 0xd880 ctl 0xd800 bmdma 0xd488 irq 20
Apr 28 03:04:46 Sparta kernel: [   41.555903] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 28 03:04:46 Sparta kernel: [   41.720181] ata1.00: ATA-7: WDC WD800JD-00LSA0, 06.01D06, max UDMA/133
Apr 28 03:04:46 Sparta kernel: [   41.720185] ata1.00: 156301488 sectors, multi 16: LBA48 
Apr 28 03:04:46 Sparta kernel: [   41.728196] ata1.00: configured for UDMA/133
Apr 28 03:04:46 Sparta kernel: [   41.931828] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Apr 28 03:04:46 Sparta kernel: [   41.942721] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JD-00LS 06.0 PQ: 0 ANSI: 5
Apr 28 03:04:46 Sparta kernel: [   41.943180] scsi2 : pata_via
Apr 28 03:04:46 Sparta kernel: [   41.943345] scsi3 : pata_via
Apr 28 03:04:46 Sparta kernel: [   41.945157] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Apr 28 03:04:46 Sparta kernel: [   41.945161] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Apr 28 03:04:46 Sparta kernel: [   41.950063] Driver 'sd' needs updating - please use bus_type methods
Apr 28 03:04:46 Sparta kernel: [   41.950154] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 28 03:04:46 Sparta kernel: [   41.950168] sd 0:0:0:0: [sda] Write Protect is off
Apr 28 03:04:46 Sparta kernel: [   41.950188] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 03:04:46 Sparta kernel: [   41.950243] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 28 03:04:46 Sparta kernel: [   41.950254] sd 0:0:0:0: [sda] Write Protect is off
Apr 28 03:04:46 Sparta kernel: [   41.950273] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 03:04:46 Sparta kernel: [   41.950276]  sda: sda1
Apr 28 03:04:46 Sparta kernel: [   41.969783] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 28 03:04:46 Sparta kernel: [   41.974455] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 28 03:04:46 Sparta kernel: [   42.284298] ata3.00: ATA-6: ST3200822A, 3.01, max UDMA/100
Apr 28 03:04:46 Sparta kernel: [   42.284302] ata3.00: 390721968 sectors, multi 16: LBA48 
Apr 28 03:04:46 Sparta kernel: [   42.285267] ata3.01: ATA-5: WDC WD400BB-00DEA0, 05.03E05, max UDMA/100
Apr 28 03:04:46 Sparta kernel: [   42.285270] ata3.01: 78165360 sectors, multi 16: LBA 
Apr 28 03:04:46 Sparta kernel: [   42.299721] usb 5-2: new high speed USB device using ehci_hcd and address 2
Apr 28 03:04:46 Sparta kernel: [   42.300148] ata3.00: configured for UDMA/100
Apr 28 03:04:46 Sparta kernel: [   42.316850] ata3.01: configured for UDMA/100
Apr 28 03:04:46 Sparta kernel: [   42.432184] usb 5-2: configuration #1 chosen from 1 choice
Apr 28 03:04:46 Sparta kernel: [   42.432354] hub 5-2:1.0: USB hub found
Apr 28 03:04:46 Sparta kernel: [   42.432452] hub 5-2:1.0: 7 ports detected
Apr 28 03:04:46 Sparta kernel: [   42.799985] ata4.00: ATAPI: PLEXTOR CD-R   PX-W4824A, 1.01, max UDMA/33
Apr 28 03:04:46 Sparta kernel: [   42.800016] ata4.01: ATAPI: COMPAQ DVD-ROM GD-2000, 0056, max MWDMA2
Apr 28 03:04:46 Sparta kernel: [   42.964824] ata4.00: configured for UDMA/33
Apr 28 03:04:46 Sparta kernel: [   43.135797] ata4.01: configured for MWDMA2
Apr 28 03:04:46 Sparta kernel: [   43.135934] scsi 2:0:0:0: Direct-Access     ATA      ST3200822A       3.01 PQ: 0 ANSI: 5
Apr 28 03:04:46 Sparta kernel: [   43.136029] sd 2:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Apr 28 03:04:46 Sparta kernel: [   43.136042] sd 2:0:0:0: [sdb] Write Protect is off
Apr 28 03:04:46 Sparta kernel: [   43.136064] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 03:04:46 Sparta kernel: [   43.136116] sd 2:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Apr 28 03:04:46 Sparta kernel: [   43.136128] sd 2:0:0:0: [sdb] Write Protect is off
Apr 28 03:04:46 Sparta kernel: [   43.136147] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 03:04:46 Sparta kernel: [   43.136151]  sdb: sdb1 sdb2 sdb3 sdb4 <<6>usb 2-1: new low speed USB device using uhci_hcd and address 2
Apr 28 03:04:46 Sparta kernel: [   43.172576]  sdb5 >
Apr 28 03:04:46 Sparta kernel: [   43.172709] sd 2:0:0:0: [sdb] Attached SCSI disk
Apr 28 03:04:46 Sparta kernel: [   43.172752] sd 2:0:0:0: Attached scsi generic sg1 type 0
Apr 28 03:04:46 Sparta kernel: [   43.172853] scsi 2:0:1:0: Direct-Access     ATA      WDC WD400BB-00DE 05.0 PQ: 0 ANSI: 5
Apr 28 03:04:46 Sparta kernel: [   43.172928] sd 2:0:1:0: [sdc] 78165360 512-byte hardware sectors (40021 MB)
Apr 28 03:04:46 Sparta kernel: [   43.172940] sd 2:0:1:0: [sdc] Write Protect is off
Apr 28 03:04:46 Sparta kernel: [   43.172961] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 03:04:46 Sparta kernel: [   43.173006] sd 2:0:1:0: [sdc] 78165360 512-byte hardware sectors (40021 MB)
Apr 28 03:04:46 Sparta kernel: [   43.173017] sd 2:0:1:0: [sdc] Write Protect is off
Apr 28 03:04:46 Sparta kernel: [   43.173037] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 03:04:46 Sparta kernel: [   43.173040]  sdc: sdc1
Apr 28 03:04:46 Sparta kernel: [   43.187043] sd 2:0:1:0: [sdc] Attached SCSI disk
Apr 28 03:04:46 Sparta kernel: [   43.187076] sd 2:0:1:0: Attached scsi generic sg2 type 0
Apr 28 03:04:46 Sparta kernel: [   43.187969] scsi 3:0:0:0: CD-ROM            PLEXTOR  CD-R   PX-W4824A 1.01 PQ: 0 ANSI: 5
Apr 28 03:04:46 Sparta kernel: [   43.188041] scsi 3:0:0:0: Attached scsi generic sg3 type 5
Apr 28 03:04:46 Sparta kernel: [   43.190076] scsi 3:0:1:0: CD-ROM            COMPAQ   DVD-ROM GD-2000  0056 PQ: 0 ANSI: 5
Apr 28 03:04:46 Sparta kernel: [   43.190151] scsi 3:0:1:0: Attached scsi generic sg4 type 5
Apr 28 03:04:46 Sparta kernel: [   43.219334] Driver 'sr' needs updating - please use bus_type methods
Apr 28 03:04:46 Sparta kernel: [   43.222584] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Apr 28 03:04:46 Sparta kernel: [   43.222589] Uniform CD-ROM driver Revision: 3.20
Apr 28 03:04:46 Sparta kernel: [   43.225219] sr1: scsi3-mmc drive: 8x/20x cd/rw xa/form2 cdda tray
Apr 28 03:04:46 Sparta kernel: [   43.327948] usb 2-1: configuration #1 chosen from 1 choice
Apr 28 03:04:46 Sparta kernel: [   43.568415] usb 2-2: new low speed USB device using uhci_hcd and address 3
Apr 28 03:04:46 Sparta kernel: [   43.685480] Attempting manual resume
Apr 28 03:04:46 Sparta kernel: [   43.697820] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr 28 03:04:46 Sparta kernel: [   43.697824] EXT3-fs: write access will be enabled during recovery.
Apr 28 03:04:46 Sparta kernel: [   43.753796] usb 2-2: configuration #1 chosen from 1 choice
Apr 28 03:04:46 Sparta kernel: [   43.955342] usb 5-2.6: new full speed USB device using ehci_hcd and address 5
Apr 28 03:04:46 Sparta kernel: [   44.048081] usb 5-2.6: configuration #1 chosen from 1 choice
Apr 28 03:04:46 Sparta kernel: [   44.048603] usbcore: registered new interface driver hiddev
Apr 28 03:04:46 Sparta kernel: [   44.100184] input: Microsoft Microsoft Wireless Optical Mouse\Uffffffff 1.00 as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input1
Apr 28 03:04:46 Sparta kernel: [   44.119315] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse\Uffffffff 1.00] on usb-0000:00:10.1-1
Apr 28 03:04:46 Sparta kernel: [   44.132851] input: Microsoft Natural\Uffffffff Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input2
Apr 28 03:04:46 Sparta kernel: [   44.143312] input,hidraw1: USB HID v1.11 Keyboard [Microsoft Natural\Uffffffff Ergonomic Keyboard 4000] on usb-0000:00:10.1-2
Apr 28 03:04:46 Sparta kernel: [   44.163763] input: Microsoft Natural\Uffffffff Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.1/input/input3
Apr 28 03:04:46 Sparta kernel: [   44.183304] input,hidraw2: USB HID v1.11 Device [Microsoft Natural\Uffffffff Ergonomic Keyboard 4000] on usb-0000:00:10.1-2
Apr 28 03:04:46 Sparta kernel: [   44.183330] usbcore: registered new interface driver usbhid
Apr 28 03:04:46 Sparta kernel: [   44.183334] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Apr 28 03:04:46 Sparta kernel: [   44.673671] kjournald starting.  Commit interval 5 seconds
Apr 28 03:04:46 Sparta kernel: [   44.673684] EXT3-fs: sdb3: orphan cleanup on readonly fs
Apr 28 03:04:46 Sparta kernel: [   44.724787] EXT3-fs: sdb3: 15 orphan inodes deleted
Apr 28 03:04:46 Sparta kernel: [   44.724789] EXT3-fs: recovery complete.
Apr 28 03:04:46 Sparta kernel: [   44.804470] EXT3-fs: mounted filesystem with ordered data mode.
Apr 28 03:04:46 Sparta kernel: [   50.479501] Linux agpgart interface v0.102
Apr 28 03:04:46 Sparta kernel: [   50.529493] agpgart: Detected VIA PT880 Ultra chipset
Apr 28 03:04:46 Sparta kernel: [   50.532985] agpgart: AGP aperture is 64M @ 0xf8000000
Apr 28 03:04:46 Sparta kernel: [   50.561759] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 28 03:04:46 Sparta kernel: [   50.597974] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 28 03:04:46 Sparta kernel: [   50.599287] ath_hal: module license 'Proprietary' taints kernel.
Apr 28 03:04:46 Sparta kernel: [   50.617721] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Apr 28 03:04:46 Sparta kernel: [   50.745707] wlan: 0.9.4
Apr 28 03:04:46 Sparta kernel: [   50.801690] ath_pci: 0.9.4
Apr 28 03:04:46 Sparta kernel: [   50.801792] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 28 03:04:46 Sparta kernel: [   51.421638] input: Power Button (FF) as /devices/virtual/input/input4
Apr 28 03:04:46 Sparta kernel: [   51.445489] ACPI: Power Button (FF) [PWRF]
Apr 28 03:04:46 Sparta kernel: [   51.445597] input: Power Button (CM) as /devices/virtual/input/input5
Apr 28 03:04:46 Sparta kernel: [   51.469483] ACPI: Power Button (CM) [PWRB]
Apr 28 03:04:46 Sparta kernel: [   52.453467] ath_rate_sample: 1.2 (0.9.4)
Apr 28 03:04:46 Sparta kernel: [   52.454000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Apr 28 03:04:46 Sparta kernel: [   52.454007] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Apr 28 03:04:46 Sparta kernel: [   52.454016] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Apr 28 03:04:46 Sparta kernel: [   52.454023] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Apr 28 03:04:46 Sparta kernel: [   52.454027] wifi0: mac 7.9 phy 4.5 radio 5.6
Apr 28 03:04:46 Sparta kernel: [   52.454031] wifi0: Use hw queue 1 for WME_AC_BE traffic
Apr 28 03:04:46 Sparta kernel: [   52.454034] wifi0: Use hw queue 0 for WME_AC_BK traffic
Apr 28 03:04:46 Sparta kernel: [   52.454036] wifi0: Use hw queue 2 for WME_AC_VI traffic
Apr 28 03:04:46 Sparta kernel: [   52.454038] wifi0: Use hw queue 3 for WME_AC_VO traffic
Apr 28 03:04:46 Sparta kernel: [   52.454040] wifi0: Use hw queue 8 for CAB traffic
Apr 28 03:04:46 Sparta kernel: [   52.454041] wifi0: Use hw queue 9 for beacons
Apr 28 03:04:46 Sparta kernel: [   52.557113] wifi0: Atheros 5212: mem=0xfebe0000, irq=22
Apr 28 03:04:46 Sparta kernel: [   52.578996] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 23
Apr 28 03:04:46 Sparta kernel: [   52.579019] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
Apr 28 03:04:46 Sparta kernel: [   52.709516] usbcore: registered new interface driver usbserial
Apr 28 03:04:46 Sparta kernel: [   52.709536] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Apr 28 03:04:46 Sparta kernel: [   52.709566] usbcore: registered new interface driver usbserial_generic
Apr 28 03:04:46 Sparta kernel: [   52.709568] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Apr 28 03:04:46 Sparta kernel: [   52.721974] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
Apr 28 03:04:46 Sparta kernel: [   52.721979] /build/buildd/linux-2.6.24/drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
Apr 28 03:04:46 Sparta kernel: [   52.722026] ipaq 5-2.6:1.0: PocketPC PDA converter detected
Apr 28 03:04:46 Sparta kernel: [   52.722466] usb 5-2.6: PocketPC PDA converter now attached to ttyUSB0
Apr 28 03:04:46 Sparta kernel: [   52.722480] usbcore: registered new interface driver ipaq
Apr 28 03:04:46 Sparta kernel: [   52.789861] input: PC Speaker as /devices/platform/pcspkr/input/input6
Apr 28 03:04:46 Sparta kernel: [   53.146386] parport_pc 00:06: reported by Plug and Play ACPI
Apr 28 03:04:46 Sparta kernel: [   53.146498] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Apr 28 03:04:46 Sparta kernel: [   55.010262] lp0: using parport0 (interrupt-driven).
Apr 28 03:04:46 Sparta kernel: [   55.063471] Adding 979956k swap on /dev/sdb5.  Priority:-1 extents:1 across:979956k
Apr 28 03:04:46 Sparta kernel: [   55.601065] EXT3 FS on sdb3, internal journal
Apr 28 03:04:46 Sparta kernel: [   99.940843] kjournald starting.  Commit interval 5 seconds
Apr 28 03:04:46 Sparta kernel: [   99.941035] EXT3 FS on sdb2, internal journal
Apr 28 03:04:46 Sparta kernel: [   99.941041] EXT3-fs: mounted filesystem with ordered data mode.
Apr 28 03:04:46 Sparta kernel: [   99.965289] kjournald starting.  Commit interval 5 seconds
Apr 28 03:04:46 Sparta kernel: [   99.969697] EXT3 FS on sdc1, internal journal
Apr 28 03:04:46 Sparta kernel: [   99.969702] EXT3-fs: mounted filesystem with ordered data mode.
Apr 28 03:04:46 Sparta kernel: [  100.042537] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
Apr 28 03:04:46 Sparta kernel: [  100.042548] ReiserFS: sda1: using ordered data mode
Apr 28 03:04:46 Sparta kernel: [  100.050344] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Apr 28 03:04:46 Sparta kernel: [  100.050587] ReiserFS: sda1: checking transaction log (sda1)
Apr 28 03:04:46 Sparta kernel: [  100.089705] ReiserFS: sda1: Using r5 hash to sort names
Apr 28 03:04:46 Sparta kernel: [  100.141555] ReiserFS: sdb1: found reiserfs format "3.6" with standard journal
Apr 28 03:04:46 Sparta kernel: [  100.141572] ReiserFS: sdb1: using ordered data mode
Apr 28 03:04:46 Sparta kernel: [  100.144348] ReiserFS: sdb1: journal params: device sdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Apr 28 03:04:46 Sparta kernel: [  100.144680] ReiserFS: sdb1: checking transaction log (sdb1)
Apr 28 03:04:46 Sparta kernel: [  100.196523] ReiserFS: sdb1: Using r5 hash to sort names
Apr 28 03:04:46 Sparta kernel: [  100.838434] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 28 03:04:46 Sparta kernel: [  101.194510] No dock devices found.
Apr 28 03:04:47 Sparta kernel: [  102.104140] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
Apr 28 03:04:47 Sparta kernel: [  102.104145] apm: disabled - APM is not SMP safe.
Apr 28 03:04:47 Sparta kernel: [  102.227250] ppdev: user-space parallel port driver
Apr 28 03:04:47 Sparta kernel: [  102.312543] audit(1209373487.385:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6226 profile="/usr/sbin/cupsd" namespace="default"
Apr 28 03:04:47 Sparta dhcdbd: Started up.
Apr 28 03:04:49 Sparta kernel: [  104.672780] eth1: link down
Apr 28 03:04:49 Sparta kernel: [  104.686653] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 28 03:04:49 Sparta dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr 28 03:04:49 Sparta kernel: [  104.737806] Bluetooth: Core ver 2.11
Apr 28 03:04:49 Sparta kernel: [  104.738601] NET: Registered protocol family 31
Apr 28 03:04:49 Sparta kernel: [  104.738605] Bluetooth: HCI device and connection manager initialized
Apr 28 03:04:49 Sparta kernel: [  104.738609] Bluetooth: HCI socket layer initialized
Apr 28 03:04:49 Sparta kernel: [  104.764348] Bluetooth: L2CAP ver 2.9
Apr 28 03:04:49 Sparta kernel: [  104.764353] Bluetooth: L2CAP socket layer initialized
Apr 28 03:04:49 Sparta kernel: [  104.816545] Bluetooth: RFCOMM socket layer initialized
Apr 28 03:04:49 Sparta kernel: [  104.816559] Bluetooth: RFCOMM TTY layer initialized
Apr 28 03:04:49 Sparta kernel: [  104.816561] Bluetooth: RFCOMM ver 1.8
Apr 28 03:04:51 Sparta kernel: [  106.868564] NET: Registered protocol family 17
Apr 28 03:05:33 Sparta dhcdbd: Unrequested down ?:3
Apr 28 03:05:33 Sparta kernel: [  148.310436] NET: Registered protocol family 10
Apr 28 03:05:33 Sparta kernel: [  148.310744] lo: Disabled Privacy Extensions
Apr 28 03:05:33 Sparta kernel: [  148.312570] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 28 03:05:38 Sparta pulseaudio[6925]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Apr 28 03:05:38 Sparta pulseaudio[6925]: alsa-util.c: Cannot find fallback mixer control "PCM".
Apr 28 03:05:45 Sparta kernel: [  160.032839] UDF-fs: No VRS found
Apr 28 10:38:58 Sparta syslogd 1.5.0#1ubuntu1: restart.

```


Sorry, that's a lot of logs, but note that somehow the time went from a mark at 6:31 am to the next log being at 3:04am... strange no? I didn't reset it either, this must have been a crash, and then somehow it hung again after resetting within a matter of minutes. I didn't notice it until 10:38am according to the logs... but I'm sure I reset it at 9:00am this morning, and the GDM shows me the correct time... really odd, no? 

ANY ideas would be nice. I've already added the dhcdbd bug to the existing bug report in Launchpad, and I've disable bluetooth at start, but so far no luck. Also, this is a fresh install, not upgrade.

Any ideas?
Thanks in advance!
-Matt

---

### Post by ryuko2002 on 2008-04-29
There was this bug about keyboard and mouse don't responding after resuming from suspend. It happened 20% of the times only.
The old solution was to add some scripts binding and unbinding one module but it doesnt work on hardy now and I read that it's because they use /etc/pm scripts instead of the acpi ones.
There is related information here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/83243](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/83243)

---

### Post by MaddMatt on 2008-04-29
I don't think that's the problem as my computer doesn't suspend... it's a desktop and I leave it running 24/7. Thanks for the suggestion!

---

### Post by themtx on 2008-05-01
In the same boat here...  Question - we've got syslog facilites all over the place here - would it make sense to push my syslogs out to a network based syslog server?  I don't know if the nic hangs, but the hdd certainly isn't writing new log entries after a certain point and prior to the "syslogd 1.5.0#1ubuntu1: restart." entry.  I'm thinking maybe it'll capture more log entries even if hdd write activity is hung.

---

### Post by MaddMatt on 2008-05-01
That may help for sure - I know I've attempted to connect to my computer via the network (FTP) while it's been hung and it connects, but you just can't do anything like login... so I think the NIC works but it cant't do anything after that. I wish there was just an easy way of core-dumping or something... argh!

---

### Post by crocowhile on 2008-05-01
Same thing here. It is extremely annoying.
I think it is a problem with gdm as when I do a shutdown after the keyboard hangs I get message saying gdm went to segfault and error 4, whatever it means.

---

### Post by onehotcutey on 2008-05-02
Just wanted to chime in the same (if not a very similar issue).  My can hang at several points:

1. When I am attempting to log in I get a black screen with mouse but will not complete the log in no matter how long let it sit for.  My keyboard does respond so I do <alt-ctl-f2> log in and restart GDM which generally resets my log in screen.  I can then attempt the log in again. 

I have found that the log in often more successful if I choose my session before logging in, rather than letting it go with the default.

2. Sometimes after I restart GDM I get a blank screen, X for the mouse cursor (which is movable) but no response from anything else including the keyboard.  At this point I have to hit the power button and let it shutdown (sometimes the system responds to the powerbutton and will shutdown, other times I have to hold in the power button.)

3. In the middle of a Gnome or XFCE session I will experience a hang. Same as above only difference is I don't get a blank screen, the background stays but inputs are not recognized.

Alright that's all for now.  I tend to agree that it's GDM, but part of me thinks it's something other.  I'll post Log's when I get a chance.

---

### Post by themtx on 2008-05-02
OK, after setting up syslog to forward - no hang overnight...  First time in 4 or 5 consecutive nights it HASN'T paniced.

One change I made that might be of significance - changed from xscreensaver "pyro" to blank screen only - perhaps not working the cpu too hard overnight prevented it from doing the nasty?

I'm going to leave it logging to network syslog host, change screensavers to a complex one, then leave for lunch, see what happens.  It usually has taken overnight to panic, so if it doesn't, I'll leave it in that config over the weekend and post back Monday w/results.

---

### Post by MaddMatt on 2008-05-02
Yeah, the screen saver is definitely not it for me... I don't have one at all. I'm starting to suspect it might have something to do with the system's handling of the network... maybe because of roaming mode or DHCP requests? Not sure. How did you set up the external logging? I'm not aware of how that's done. Cheers!

---

### Post by themtx on 2008-05-06
Locked / paniced over the weekend, appears to have been as early as Friday 10PM - at least that's the last syslog msg it forwarded - and it was a --MARK--.  Dangit.

Following some more research, I updated my kernel to 2.6.24-17-generic (added Hardy Proposed repos in Synaptic, ran an apt-get update, off we went) and this box didnt hang last night for the first time since I clean-installed Xubuntu Beta.

We'll see if this issue has been truly resovled in 2.6.24-17, but so far so good.  FWIW, I'm on Xubuntu 64bit on an (Intel) Core2Duo Dell Optiplex 755 w/full hardware virtualization enabled in the BIOS.

---

### Post by Silenus on 2008-05-06
I am using a toshiba a215-27422 laptop and I get these system hangs as well; I will open an application such as gnome-terminal and the system will become unresponsive, the same happens with opening links, etc.

Help is appreciated.

---

### Post by MaddMatt on 2008-05-16
I think it had something to do with my internet... wifi specifically. I'm using madwifi-ng, and since i turned it off I haven't frozen. Anyone else?

---

### Post by crashcoredump on 2008-05-16
Does anyone know what the final resolution to this issue is?

I have the same output in my messages and syslog.

```
**papa@Painhu:~$ uname -a**
Linux Painhu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
papa@Painhu:~$ **tail -10 /var/log/messages**

May 16 06:01:37 Painhu -- MARK --
May 16 06:16:22 Painhu pulseaudio[1143]: pid.c: Stale PID file, overwriting.
May 16 06:16:22 Painhu pulseaudio[1143]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
May 16 06:16:22 Painhu pulseaudio[1143]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
papa@Painhu:~$ **tail -10 /var/log/syslog**
May 16 06:16:00 Painhu gdm[27557]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 16 06:16:22 Painhu pulseaudio[1143]: pid.c: Stale PID file, overwriting.
May 16 06:16:22 Painhu pulseaudio[1143]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
May 16 06:16:22 Painhu pulseaudio[1143]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May 16 06:16:24 Painhu hcid[5614]: Default passkey agent (:1.129, /org/bluez/passkey) registered
May 16 06:16:24 Painhu hcid[5614]: Default authorization agent (:1.129, /org/bluez/auth) registered
May 16 06:16:25 Painhu NetworkManager: <info>  Updating allowed wireless network lists. 
May 16 06:16:25 Painhu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May 16 06:17:01 Painhu /USR/SBIN/CRON[1343]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 16 06:25:01 Painhu /USR/SBIN/CRON[1439]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
papa@Painhu:~$ 


```


Anyhooo,
I come down in the morning to find my system hung and with just a blank logon box on the screen, of course I cannot logon.

I can however alt+ctrl+backspace and kill X and then start a new session.


I was suspecting pulseaudio was the culprit.


Any help would be great, I too run the 24/7 desktop and find this a wee bit annoying.

---

### Post by MaddMatt on 2008-05-29
I think there are two separate problems in this thread right now. Mine definitely does not have to do with pulse audio, and results in a system hang that is NOT responsive to keyboard or mouse. My theory is still something to do with WPAsupplicant and the Madwifi-ng driver. Does anyone else have this specific setup?  Why I think that the supplicant is to blame: this happened this morning. 


```

May 29 01:57:46 Sparta -- MARK --
May 29 02:02:55 Sparta NetworkManager: <info>  Supplicant state changed: 0 
May 29 02:02:56 Sparta NetworkManager: <info>  Supplicant state changed: 1 
May 29 02:17:01 Sparta /USR/SBIN/CRON[28148]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 29 02:20:15 Sparta NetworkManager: <info>  Supplicant state changed: 0 
May 29 02:20:16 Sparta NetworkManager: <info>  Supplicant state changed: 1 
May 29 02:22:25 Sparta NetworkManager: <info>  Supplicant state changed: 0 
May 29 02:22:27 Sparta NetworkManager: <info>  Supplicant state changed: 1 
May 29 02:37:46 Sparta -- MARK --
May 29 02:44:05 Sparta NetworkManager: <info>  Supplicant state changed: 0 
May 29 02:44:07 Sparta NetworkManager: <info>  Supplicant state changed: 1 
May 29 09:48:07 Sparta syslogd 1.5.0#1ubuntu1: restart.
May 29 09:48:07 Sparta NetworkManager: <info>  starting... 

```

---

### Post by jpitzo on 2008-06-06
arggg.  I've been having the same problem!  My computer lock ups up almost every other day, always when using either firefox ( I've tried 2, 3 beta 5 and 3 rc2 now ).  Firefox or rythmbox goes grey and within a minute I'm hard locked. no keyboard, mouse. ick.  these are the only entries in any log right before it locks up.

```
daemon.log:Jun  6 22:05:47 jpwn-ubuntu NetworkManager: <info>  Supplicant state changed: 0 
daemon.log:Jun  6 22:05:48 jpwn-ubuntu NetworkManager: <info>  Supplicant state changed: 1 
syslog:Jun  6 22:05:47 jpwn-ubuntu NetworkManager: <info>  Supplicant state changed: 0 
syslog:Jun  6 22:05:48 jpwn-ubuntu NetworkManager: <info>  Supplicant state changed: 1 

```

Has anyone found a fix for this?

---

### Post by Brando569 on 2008-06-06
i think its just a general problem with 8.04 since my box hangs like crazy and im using kubuntu. at first i thought it was somthing to do with compiz/new nvidia driver/superkaramba because it only seemed to happen when i had a lot of widgets open and most were hidden by compiz and ram usage was  >=1GB (i have 2gb) i had xconfig rewrite a basic xconfig file and i thought that seemed to fix it, wrong, it froze again when the ram was only at ~700mb and i was using kwin and not compiz. Ive also tried both 24-16,17 and 18 and none of them seem to have any effect on them. I seem to think its either a problem with the xserver or 8.04 in general. i was thinking it might have been kde related by as i see most of you are running gnome so we can rule out the DEs.

---

### Post by uzi09 on 2008-06-09
I agree that there seems to be multiple issues going on, and unfortunately, I think I've had a taste of them all :S

Specs:
- Laptop Dell Inspiron 6400

- Ubuntu 8.04 Hardy Heron (installed Xubuntu-desktop -- which is what I thought was the problem the whole time, and I saw that somebody also mentioned that they were using Xubuntu. Can anyone else confirm/deny whether they're having this issue with Xubuntu as well?)

- Kernal 2.6.24-18-generic

- Firefox 3 beta 5/Swiftfox (some problems seem to be browser related, however it seems to happen with both the browsers)

Problem 1:
My battery is shot, and so if my power supply is unplugged, it'll go to sleep in a couple minutes automatically. When I resume, my mouse and keyboard is frozen. However, if I manually put it to sleep, it'll wake up fine :)

Problem 2:
Hardy seems to hang for a variety of different reasons. Once it happened while I was connecting through RealVNC in Firefox 3. Once or twice it worked okay, but more often than not, it's a sure-fire way to kill my Hardy. I tried this with Swiftfox and it was the same issue. When this would happen, when I would restart (or sometimes gdm would restart itself) and try to log into my xubuntu-desktop, the screen would hang at the blue background and I would just have a mouse. I'd have to manually restart and then log into gnome, reinstall xubuntu-desktop, and then I'd be able to log into xubuntu-desktop again.

[https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/237248](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/237248)

The same issue seemed to happen with mplayer a few times. Often when I would play a particular file (mainly flv's, but not always) it would crash in a similar manner. And I'd have to get it up and running by reinstalling xubuntu-desktop.

Both these crashes seem to be more frequent in xubuntu-desktop, however I've had both of them happen in ubuntu-desktop a few times as well.

There seems to be a thread that discusses a similar issue here:

[http://ubuntuforums.org/showthread.php?t=793457&highlight=xubuntu](http://ubuntuforums.org/showthread.php?t=793457&highlight=xubuntu)

Since I'm still a newbie at linux, I unfortunately forgot where the logs were and didn't bother looking them up. However now that I look at them, I recall that when I was connecting to a remote desktop through RealVNC, I was testing out my samba file server and so the issue occurred a few times when I connected to samba from the remote machine. I don't know why it didn't click earlier that the issue might have been with Samba :S. Anyway, here's part of the log.

Any help is much appreciated, and if I'm bringing up issues that aren't really related to the original post, please forgive me and let me know.

```

uzair@mybochs:~$ tail -50 /var/log/syslog
Jun  9 10:51:27 mybochs NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jun  9 10:51:27 mybochs NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jun  9 10:51:27 mybochs NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Jun  9 10:51:27 mybochs NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun  9 10:51:27 mybochs ntpd[6596]: ntpd exiting on signal 15
Jun  9 10:51:28 mybochs ntpdate[4852]: step time server 199.212.17.22 offset 1.487477 sec
Jun  9 10:51:30 mybochs avahi-daemon[5027]: Registering new address record for fe80::213:2ff:fe2f:1513 on wlan0.*.
Jun  9 10:51:30 mybochs ntpd[4895]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Jun  9 10:51:30 mybochs ntpd[4896]: precision = 1.000 usec
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #1 wildcard, ::#123 Disabled
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #2 lo, ::1#123 Enabled
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #3 wlan0, fe80::213:2ff:fe2f:1513#123 Enabled
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #5 wlan0, 192.168.10.100#123 Enabled
Jun  9 10:51:30 mybochs ntpd[4896]: kernel time sync status 0040
Jun  9 10:51:30 mybochs ntpd[4896]: frequency initialized -68.868 PPM from /var/lib/ntp/ntp.drift
Jun  9 10:51:39 mybochs kernel: [   36.339805] wlan0: no IPv6 routers present
Jun  9 10:55:50 mybochs ntpd[4896]: synchronized to 199.212.17.21, stratum 2
Jun  9 10:55:50 mybochs ntpd[4896]: kernel time sync status change 0001
Jun  9 10:58:02 mybochs winbindd[11849]: [2008/06/09 10:58:02, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Jun  9 10:58:02 mybochs winbindd[11849]:   ERROR: Initialization failed for alloc backend, deferred! 
Jun  9 10:58:02 mybochs smbd[7628]: [2008/06/09 10:58:02, 0] auth/auth_util.c:create_builtin_administrators(792) 
Jun  9 10:58:02 mybochs smbd[7628]:   create_builtin_administrators: Failed to create Administrators 
Jun  9 10:58:02 mybochs winbindd[11849]: [2008/06/09 10:58:02, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Jun  9 10:58:02 mybochs winbindd[11849]:   ERROR: Initialization failed for alloc backend, deferred! 
Jun  9 10:58:02 mybochs smbd[7628]: [2008/06/09 10:58:02, 0] auth/auth_util.c:create_builtin_users(758) 
Jun  9 10:58:02 mybochs smbd[7628]:   create_builtin_users: Failed to create Users 
Jun  9 10:58:02 mybochs winbindd[5393]: [2008/06/09 10:58:02, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Jun  9 10:58:02 mybochs winbindd[5393]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Jun  9 10:58:02 mybochs winbindd[5393]: [2008/06/09 10:58:02, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Jun  9 10:58:02 mybochs winbindd[5393]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Jun  9 11:02:19 mybochs ntpd[4896]: synchronized to 199.212.17.22, stratum 2
Jun  9 11:09:01 mybochs /USR/SBIN/CRON[11871]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun  9 11:13:56 mybochs smbd[11848]: [2008/06/09 11:13:56, 0] lib/util_sock.c:read_data(534) 
Jun  9 11:13:56 mybochs smbd[11848]:   read_data: read failure for 4 bytes to client 192.168.1.100. Error = Connection timed out 
Jun  9 11:17:01 mybochs /USR/SBIN/CRON[14857]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  9 11:30:01 mybochs winbindd[11849]: [2008/06/09 11:30:01, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Jun  9 11:30:01 mybochs winbindd[11849]:   ERROR: Initialization failed for alloc backend, deferred! 
Jun  9 11:30:01 mybochs smbd[19713]: [2008/06/09 11:30:01, 0] auth/auth_util.c:create_builtin_administrators(792) 
Jun  9 11:30:01 mybochs smbd[19713]:   create_builtin_administrators: Failed to create Administrators 
Jun  9 11:30:01 mybochs winbindd[11849]: [2008/06/09 11:30:01, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Jun  9 11:30:01 mybochs winbindd[11849]:   ERROR: Initialization failed for alloc backend, deferred! 
Jun  9 11:30:01 mybochs smbd[19713]: [2008/06/09 11:30:01, 0] auth/auth_util.c:create_builtin_users(758) 
Jun  9 11:30:01 mybochs smbd[19713]:   create_builtin_users: Failed to create Users 
Jun  9 11:30:01 mybochs winbindd[5393]: [2008/06/09 11:30:01, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Jun  9 11:30:01 mybochs winbindd[5393]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Jun  9 11:30:01 mybochs winbindd[5393]: [2008/06/09 11:30:01, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Jun  9 11:30:01 mybochs winbindd[5393]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Jun  9 11:39:01 mybochs /USR/SBIN/CRON[23054]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

```

---

### Post by crocowhile on 2008-06-09
My problem has disappeared after I removed the usb bluetooth dongle, although keyboard was not a bluetooth one.
Go figure.

---

### Post by uzi09 on 2008-06-10
> **uzi09 said:**
> I agree that there seems to be multiple issues going on, and unfortunately, I think I've had a taste of them all :S

Specs:
- Laptop Dell Inspiron 6400

- Ubuntu 8.04 Hardy Heron (installed Xubuntu-desktop -- which is what I thought was the problem the whole time, and I saw that somebody also mentioned that they were using Xubuntu. Can anyone else confirm/deny whether they're having this issue with Xubuntu as well?)

- Kernal 2.6.24-18-generic

- Firefox 3 beta 5/Swiftfox (some problems seem to be browser related, however it seems to happen with both the browsers)

Problem 1:
My battery is shot, and so if my power supply is unplugged, it'll go to sleep in a couple minutes automatically. When I resume, my mouse and keyboard is frozen. However, if I manually put it to sleep, it'll wake up fine :)

Problem 2:
Hardy seems to hang for a variety of different reasons. Once it happened while I was connecting through RealVNC in Firefox 3. Once or twice it worked okay, but more often than not, it's a sure-fire way to kill my Hardy. I tried this with Swiftfox and it was the same issue. When this would happen, when I would restart (or sometimes gdm would restart itself) and try to log into my xubuntu-desktop, the screen would hang at the blue background and I would just have a mouse. I'd have to manually restart and then log into gnome, reinstall xubuntu-desktop, and then I'd be able to log into xubuntu-desktop again.

[https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/237248](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/237248)

The same issue seemed to happen with mplayer a few times. Often when I would play a particular file (mainly flv's, but not always) it would crash in a similar manner. And I'd have to get it up and running by reinstalling xubuntu-desktop.

Both these crashes seem to be more frequent in xubuntu-desktop, however I've had both of them happen in ubuntu-desktop a few times as well.

There seems to be a thread that discusses a similar issue here:

[http://ubuntuforums.org/showthread.php?t=793457&highlight=xubuntu](http://ubuntuforums.org/showthread.php?t=793457&highlight=xubuntu)

Since I'm still a newbie at linux, I unfortunately forgot where the logs were and didn't bother looking them up. However now that I look at them, I recall that when I was connecting to a remote desktop through RealVNC, I was testing out my samba file server and so the issue occurred a few times when I connected to samba from the remote machine. I don't know why it didn't click earlier that the issue might have been with Samba :S. Anyway, here's part of the log.

Any help is much appreciated, and if I'm bringing up issues that aren't really related to the original post, please forgive me and let me know.

```

uzair@mybochs:~$ tail -50 /var/log/syslog
Jun  9 10:51:27 mybochs NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jun  9 10:51:27 mybochs NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jun  9 10:51:27 mybochs NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Jun  9 10:51:27 mybochs NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun  9 10:51:27 mybochs ntpd[6596]: ntpd exiting on signal 15
Jun  9 10:51:28 mybochs ntpdate[4852]: step time server 199.212.17.22 offset 1.487477 sec
Jun  9 10:51:30 mybochs avahi-daemon[5027]: Registering new address record for fe80::213:2ff:fe2f:1513 on wlan0.*.
Jun  9 10:51:30 mybochs ntpd[4895]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Jun  9 10:51:30 mybochs ntpd[4896]: precision = 1.000 usec
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #1 wildcard, ::#123 Disabled
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #2 lo, ::1#123 Enabled
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #3 wlan0, fe80::213:2ff:fe2f:1513#123 Enabled
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jun  9 10:51:30 mybochs ntpd[4896]: Listening on interface #5 wlan0, 192.168.10.100#123 Enabled
Jun  9 10:51:30 mybochs ntpd[4896]: kernel time sync status 0040
Jun  9 10:51:30 mybochs ntpd[4896]: frequency initialized -68.868 PPM from /var/lib/ntp/ntp.drift
Jun  9 10:51:39 mybochs kernel: [   36.339805] wlan0: no IPv6 routers present
Jun  9 10:55:50 mybochs ntpd[4896]: synchronized to 199.212.17.21, stratum 2
Jun  9 10:55:50 mybochs ntpd[4896]: kernel time sync status change 0001
Jun  9 10:58:02 mybochs winbindd[11849]: [2008/06/09 10:58:02, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Jun  9 10:58:02 mybochs winbindd[11849]:   ERROR: Initialization failed for alloc backend, deferred! 
Jun  9 10:58:02 mybochs smbd[7628]: [2008/06/09 10:58:02, 0] auth/auth_util.c:create_builtin_administrators(792) 
Jun  9 10:58:02 mybochs smbd[7628]:   create_builtin_administrators: Failed to create Administrators 
Jun  9 10:58:02 mybochs winbindd[11849]: [2008/06/09 10:58:02, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Jun  9 10:58:02 mybochs winbindd[11849]:   ERROR: Initialization failed for alloc backend, deferred! 
Jun  9 10:58:02 mybochs smbd[7628]: [2008/06/09 10:58:02, 0] auth/auth_util.c:create_builtin_users(758) 
Jun  9 10:58:02 mybochs smbd[7628]:   create_builtin_users: Failed to create Users 
Jun  9 10:58:02 mybochs winbindd[5393]: [2008/06/09 10:58:02, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Jun  9 10:58:02 mybochs winbindd[5393]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Jun  9 10:58:02 mybochs winbindd[5393]: [2008/06/09 10:58:02, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Jun  9 10:58:02 mybochs winbindd[5393]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Jun  9 11:02:19 mybochs ntpd[4896]: synchronized to 199.212.17.22, stratum 2
Jun  9 11:09:01 mybochs /USR/SBIN/CRON[11871]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun  9 11:13:56 mybochs smbd[11848]: [2008/06/09 11:13:56, 0] lib/util_sock.c:read_data(534) 
Jun  9 11:13:56 mybochs smbd[11848]:   read_data: read failure for 4 bytes to client 192.168.1.100. Error = Connection timed out 
Jun  9 11:17:01 mybochs /USR/SBIN/CRON[14857]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  9 11:30:01 mybochs winbindd[11849]: [2008/06/09 11:30:01, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Jun  9 11:30:01 mybochs winbindd[11849]:   ERROR: Initialization failed for alloc backend, deferred! 
Jun  9 11:30:01 mybochs smbd[19713]: [2008/06/09 11:30:01, 0] auth/auth_util.c:create_builtin_administrators(792) 
Jun  9 11:30:01 mybochs smbd[19713]:   create_builtin_administrators: Failed to create Administrators 
Jun  9 11:30:01 mybochs winbindd[11849]: [2008/06/09 11:30:01, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Jun  9 11:30:01 mybochs winbindd[11849]:   ERROR: Initialization failed for alloc backend, deferred! 
Jun  9 11:30:01 mybochs smbd[19713]: [2008/06/09 11:30:01, 0] auth/auth_util.c:create_builtin_users(758) 
Jun  9 11:30:01 mybochs smbd[19713]:   create_builtin_users: Failed to create Users 
Jun  9 11:30:01 mybochs winbindd[5393]: [2008/06/09 11:30:01, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Jun  9 11:30:01 mybochs winbindd[5393]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Jun  9 11:30:01 mybochs winbindd[5393]: [2008/06/09 11:30:01, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Jun  9 11:30:01 mybochs winbindd[5393]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Jun  9 11:39:01 mybochs /USR/SBIN/CRON[23054]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

```


So it crashed yet again, checked the syslog and noticed that I was getting an error that [this]("http://ubuntuforums.org/showthread.php?t=96068") link seems to be related to. Perhaps this is where the problem lies. Apparently it seems to be some video/gdm issues. Makes sense since it always seems to happen when a task that requires a lot of graphics or something is occurring.

---

