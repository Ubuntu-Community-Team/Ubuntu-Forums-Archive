---
title: "&quot;TSC calibrated against HPET'' takes up 20sec to boot"
date: 2008-12-25
forum: General Help
---

### Post by afeasfaerw23231233 on 2008-12-25
"TSC calibrated against HPET'' takes up 20sec to boot
I ran dmesg in terminal and this showed up. Why  [    0.000000]  "TSC calibrated against HPET'' takes up 20sec and [   25.824898] EXT3-fs: mounted filesystem with ordered data mode ~10sec? Is it normal? If not then how can I make it run faster? 
I also attach my bootchart.
Thanks! 

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-22-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 24 19:35:06 UTC 2008 (Ubuntu 2.6.24-22.45-generic)
[    0.000000] Command line: root=UUID=f4659fbf-000d-49b8-9934-99a69ffec0e1 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff90000 (usable)
[    0.000000]  BIOS-e820: 000000003ff90000 - 000000003ff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff9e000 - 000000003ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ffe0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262032) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FAD20 checksum 0
[    0.000000] ACPI: RSDP 000FAD20, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FF90000, 0038 (r1 A_M_I_ OEMRSDT  12000726 MSFT       97)
[    0.000000] ACPI: FACP 3FF90200, 0081 (r1 A_M_I_ OEMFACP  12000726 MSFT       97)
[    0.000000] ACPI: DSDT 3FF90590, 859A (r1  A0355 A0355000        0 INTL 20051117)
[    0.000000] ACPI: FACS 3FF9E000, 0040
[    0.000000] ACPI: APIC 3FF90390, 0080 (r1 A_M_I_ OEMAPIC  12000726 MSFT       97)
[    0.000000] ACPI: OEMB 3FF9E040, 0066 (r1 A_M_I_ AMI_OEM  12000726 MSFT       97)
[    0.000000] ACPI: HPET 3FF98B30, 0038 (r1 A_M_I_ OEMHPET  12000726 MSFT       97)
[    0.000000] ACPI: MCFG 3FF98B70, 003C (r1 A_M_I_ OEMMCFG  12000726 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003ff90000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262032) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff90000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   262032
[    0.000000] On node 0 totalpages: 261935
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1219 pages reserved
[    0.000000]   DMA zone: 2724 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3526 pages used for memmap
[    0.000000]   DMA32 zone: 254410 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 257134
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=f4659fbf-000d-49b8-9934-99a69ffec0e1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
**[   20.566587] time.c: Detected 3706.131 MHz processor.**
[   20.567876] Console: colour VGA+ 80x25
[   20.567879] console [tty0] enabled
[   20.567893] Checking aperture...
[   20.567901] Calgary: detecting Calgary via BIOS EBDA area
[   20.567903] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   20.577524] Memory: 1020724k/1048128k available (2490k kernel code, 27016k reserved, 1317k data, 320k init)
[   20.577561] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   20.656479] Calibrating delay using timer specific routine.. 7418.19 BogoMIPS (lpj=14836380)
[   20.656508] Security Framework initialized
[   20.656514] SELinux:  Disabled at boot.
[   20.656527] AppArmor: AppArmor initialized
[   20.656531] Failure registering capabilities with primary security module.
[   20.656671] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.657253] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   20.657578] Mount-cache hash table entries: 256
[   20.657722] Initializing cgroup subsys ns
[   20.657727] Initializing cgroup subsys cpuacct
[   20.657745] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   20.657747] CPU: L2 cache: 1024K
[   20.657750] CPU 0/0 -> Node 0
[   20.657751] using mwait in idle threads.
[   20.657753] CPU: Hyper-Threading is disabled
[   20.657763] CPU0: Thermal monitoring enabled (TM1)
[   20.657775] SMP alternatives: switching to UP code
[   20.658654] Early unpacking initramfs... done
[   20.918719] ACPI: Core revision 20070126
[   20.918777] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.962183] Using local APIC timer interrupts.
[   20.989142] APIC timer calibration result 11581580
[   20.989144] Detected 11.581 MHz APIC timer.
[   20.989187] Brought up 1 CPUs
[   20.989247] CPU0 attaching sched-domain:
[   20.989250]  domain 0: span 01
[   20.989251]   groups: 01
[   20.989399] net_namespace: 120 bytes
[   20.989711] Time:  2:37:25  Date: 12/26/08
[   20.989735] NET: Registered protocol family 16
[   20.989913] ACPI: bus type pci registered
[   20.989982] PCI: Using configuration type 1
[   20.992549] ACPI: EC: Look up EC in DSDT
[   21.000090] ACPI: Interpreter enabled
[   21.000093] ACPI: (supports S0 S1 S3 S4 S5)
[   21.000107] ACPI: Using IOAPIC for interrupt routing
[   21.006776] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.007308] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   21.007312] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   21.007841] PCI: Transparent bridge - 0000:00:1e.0
[   21.007869] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.007994] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   21.008067] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   21.008172] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   21.008250] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   21.010239] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   21.010346] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   21.010451] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   21.010556] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   21.010661] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   21.010765] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.010870] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.010975] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   21.011079] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  D5, should be D0 [20070126]
[   21.011088] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.011117] pnp: PnP ACPI init
[   21.011124] ACPI: bus type pnp registered
[   21.014855] pnp: PnP ACPI: found 16 devices
[   21.014858] ACPI: ACPI bus type pnp unregistered
[   21.015088] PCI: Using ACPI for IRQ routing
[   21.015091] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.017218] NET: Registered protocol family 8
[   21.017220] NET: Registered protocol family 20
[   21.017250] PCI-GART: No AMD northbridge found.
[   21.017255] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   21.017258] hpet0: 3 64-bit timers, 14318180 Hz
[   21.018296] AppArmor: AppArmor Filesystem Enabled
[   21.021115] Time: tsc clocksource has been installed.
[   21.029144] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   21.029151] system 00:07: ioport range 0x290-0x297 has been reserved
[   21.029156] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   21.029158] system 00:08: ioport range 0x800-0x87f has been reserved
[   21.029159] system 00:08: ioport range 0x480-0x4bf has been reserved
[   21.029161] system 00:08: ioport range 0x900-0x91f has been reserved
[   21.029163] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   21.029165] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   21.029167] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   21.029169] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   21.029175] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   21.029177] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   21.029181] system 00:0e: iomem range 0xf0000000-0xf3ffffff has been reserved
[   21.029186] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   21.029188] system 00:0f: iomem range 0xc0000-0xdffff has been reserved
[   21.029190] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   21.029192] system 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
[   21.029193] system 00:0f: iomem range 0x0-0x0 could not be reserved
[   21.029550] PCI: Bridge: 0000:00:01.0
[   21.029553]   IO window: e000-efff
[   21.029556]   MEM window: dc000000-dfffffff
[   21.029558]   PREFETCH window: e0000000-efffffff
[   21.029561] PCI: Bridge: 0000:00:1c.0
[   21.029563]   IO window: d000-dfff
[   21.029567]   MEM window: disabled.
[   21.029569]   PREFETCH window: disabled.
[   21.029573] PCI: Bridge: 0000:00:1c.3
[   21.029575]   IO window: c000-cfff
[   21.029579]   MEM window: dbf00000-dbffffff
[   21.029581]   PREFETCH window: disabled.
[   21.029585] PCI: Bridge: 0000:00:1e.0
[   21.029587]   IO window: b000-bfff
[   21.029591]   MEM window: disabled.
[   21.029593]   PREFETCH window: disabled.
[   21.029611] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.029615] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.029630] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.029634] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.029650] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   21.029653] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   21.029662] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.029671] NET: Registered protocol family 2
[   21.065142] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   21.065513] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   21.066620] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   21.067229] TCP: Hash tables configured (established 131072 bind 65536)
[   21.067233] TCP reno registered
[   21.077239] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   21.319170]  it is
[   21.579766] Freeing initrd memory: 7553k freed
[   21.584988] audit: initializing netlink socket (disabled)
[   21.585009] audit(1230259045.000:1): initialized
[   21.586686] VFS: Disk quotas dquot_6.5.1
[   21.586744] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   21.586860] io scheduler noop registered
[   21.586862] io scheduler anticipatory registered
[   21.586863] io scheduler deadline registered
[   21.586947] io scheduler cfq registered (default)
[   21.587378] Boot video device is 0000:04:00.0
[   21.587515] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.587546] assign_interrupt_mode Found MSI capability
[   21.587573] Allocate Port Service[0000:00:01.0:pcie00]
[   21.587640] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.587677] assign_interrupt_mode Found MSI capability
[   21.587707] Allocate Port Service[0000:00:1c.0:pcie00]
[   21.587737] Allocate Port Service[0000:00:1c.0:pcie02]
[   21.587808] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   21.587843] assign_interrupt_mode Found MSI capability
[   21.587873] Allocate Port Service[0000:00:1c.3:pcie00]
[   21.611198] Real Time Clock Driver v1.12ac
[   21.611362] hpet_resources: 0xfed00000 is busy
[   21.611385] Linux agpgart interface v0.102
[   21.611387] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.611504] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.612110] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.612733] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.612789] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.612874] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   21.615491] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.615495] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.620612] mice: PS/2 mouse device common for all mice
[   21.620646] cpuidle: using governor ladder
[   21.620648] cpuidle: using governor menu
[   21.620724] NET: Registered protocol family 1
[   21.620776] registered taskstats version 1
[   21.620856]   Magic number: 4:780:612
[   21.620896]   hash matches device ptye2
[   21.620943]   hash matches device tty
[   21.620964] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   21.620966] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.620968] EDD information not available.
[   21.620975] Freeing unused kernel memory: 320k freed
[   21.621301] Write protecting the kernel read-only data: 1036k
[   21.648429] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.811713] fuse init (API version 7.9)
[   22.826480] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.826494] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   22.826506] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   22.826515] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.350539] r8169 Gigabit Ethernet driver 2.2LK loaded
[   23.350568] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   23.350590] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   23.350838] eth0: RTL8168b/8111b at 0xffffc200004f2000, 00:13:d4:fb:db:ba, XID 30000000 IRQ 508
[   23.394302] usbcore: registered new interface driver usbfs
[   23.394328] usbcore: registered new interface driver hub
[   23.402459] usbcore: registered new device driver usb
[   23.407492] USB Universal Host Controller Interface driver v3.0
[   23.407555] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   23.407565] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.407569] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.407823] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.407850] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00008000
[   23.407964] usb usb1: configuration #1 chosen from 1 choice
[   23.407985] hub 1-0:1.0: USB hub found
[   23.407991] hub 1-0:1.0: 2 ports detected
[   23.438796] SCSI subsystem initialized
[   23.464835] libata version 3.00 loaded.
[   23.510414] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[   23.510425] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.510429] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.510450] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   23.510478] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00008400
[   23.510567] usb usb2: configuration #1 chosen from 1 choice
[   23.510586] hub 2-0:1.0: USB hub found
[   23.510591] hub 2-0:1.0: 2 ports detected
[   23.618264] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.618276] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.618280] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.618316] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   23.618343] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008800
[   23.618434] usb usb3: configuration #1 chosen from 1 choice
[   23.618457] hub 3-0:1.0: USB hub found
[   23.618463] hub 3-0:1.0: 2 ports detected
[   23.722162] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[   23.722174] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   23.722177] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   23.722198] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   23.722226] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00009000
[   23.722316] usb usb4: configuration #1 chosen from 1 choice
[   23.722337] hub 4-0:1.0: USB hub found
[   23.722342] hub 4-0:1.0: 2 ports detected
[   23.826190] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   23.826339] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.826345] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.826391] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   23.830288] ehci_hcd 0000:00:1d.7: debug port 1
[   23.830294] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   23.830300] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdbeffc00
[   23.845916] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.846023] usb usb5: configuration #1 chosen from 1 choice
[   23.846045] hub 5-0:1.0: USB hub found
[   23.846053] hub 5-0:1.0: 8 ports detected
[   23.949991] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
[   23.950029] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.950040] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   23.950063] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
[   23.950080] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.950088] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   23.954091] ata_piix 0000:00:1f.1: version 2.12
[   23.954109] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
[   23.954143] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.955322] scsi0 : ata_piix
[   23.955957] scsi1 : ata_piix
[   23.957114] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   23.957116] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   24.321096] ata1.00: ATA-7: ST3160812A, 3.AAJ, max UDMA/100
[   24.321100] ata1.00: 312581808 sectors, multi 16: LBA48 
[   24.321116] ata1.01: ATAPI: HL-DT-ST DVDRAM GSA-4082B, A208, max UDMA/66
[   24.404211] ata1.00: configured for UDMA/100
[   24.581336] ata1.01: configured for UDMA/66
[   24.752140] scsi 0:0:0:0: Direct-Access     ATA      ST3160812A       3.AA PQ: 0 ANSI: 5
[   24.757664] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4082B A208 PQ: 0 ANSI: 5
[   24.757742] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   24.757762] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
[   24.757795] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.758645] scsi2 : ata_piix
[   24.760888] scsi3 : ata_piix
[   24.760936] ata3: SATA max UDMA/133 cmd 0xa800 ctl 0xa400 bmdma 0x9400 irq 23
[   24.760938] ata4: SATA max UDMA/133 cmd 0xa000 ctl 0x9800 bmdma 0x9408 irq 23
[   25.111778] Driver 'sd' needs updating - please use bus_type methods
[   25.111865] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   25.111878] sd 0:0:0:0: [sda] Write Protect is off
[   25.111881] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.111901] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.111945] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   25.111956] sd 0:0:0:0: [sda] Write Protect is off
[   25.111958] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.111978] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.111982]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   25.140444]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[   25.225302] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.231191] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.231228] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   25.248242] sr0: scsi3-mmc drive: 32x/32x writer dvd-ram cd/rw xa/form2 cdda tray
[   25.248247] Uniform CD-ROM driver Revision: 3.20
[   25.248291] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   25.766059] Attempting manual resume
[   25.766063] swsusp: Resume From Partition 8:10
[   25.766064] PM: Checking swsusp image.
[   25.766273] PM: Resume from disk failed.
[   25.824884] kjournald starting.  Commit interval 5 seconds
**[   25.824898] EXT3-fs: mounted filesystem with ordered data mode.**
[   33.448105] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.465121] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.591465] intel_rng: FWH not detected
[   33.642277] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   33.755464] input: Power Button (FF) as /devices/virtual/input/input3
[   33.766631] ACPI: Power Button (FF) [PWRF]
[   33.766768] input: Power Button (CM) as /devices/virtual/input/input4
[   33.782590] ACPI: Power Button (CM) [PWRB]
[   33.782643] iTCO_vendor_support: vendor-support=0
[   33.806583] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   33.806670] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   33.806699] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   34.729669] nvidia: module license 'NVIDIA' taints kernel.
[   35.082456] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   35.082613] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.629428] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   35.642810] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.642819] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   35.642930] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   35.663001] parport_pc 00:06: reported by Plug and Play ACPI
[   35.663112] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   37.754199] lp0: using parport0 (interrupt-driven).
[   37.838662] Adding 1461872k swap on /dev/sda10.  Priority:-1 extents:1 across:1461872k
[   38.382713] EXT3 FS on sda8, internal journal
[   39.449569] kjournald starting.  Commit interval 5 seconds
[   39.449693] EXT3 FS on sda9, internal journal
[   39.449697] EXT3-fs: mounted filesystem with ordered data mode.
[   39.490398] kjournald starting.  Commit interval 5 seconds
[   39.490567] EXT3 FS on sda7, internal journal
[   39.490570] EXT3-fs: mounted filesystem with ordered data mode.
[   39.515140] kjournald starting.  Commit interval 5 seconds
[   39.515278] EXT3 FS on sda6, internal journal
[   39.515281] EXT3-fs: mounted filesystem with ordered data mode.
[   39.981566] ip_tables: (C) 2000-2006 Netfilter Core Team


```

---

### Post by spiderbatdad on 2008-12-25
there is an hpet=force parameter you might try. For example my kernel boots with:```
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=XXXXXX ro lapic hpet=force pci=routeirq 
``` This is a line edited by user in /boot/grub/menu.lst

---

### Post by afeasfaerw23231233 on 2008-12-26
i've added the parameter hpet=force but it's just the same.
```

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,8)
kernel		/vmlinuz-2.6.24-22-generic root=UUID=f4659fbf-000d-49b8-9934-99a69ffec0e1 ro quiet splash hpet=force 
initrd		/initrd.img-2.6.24-22-generic
quiet
```


```

[    0.000000] TSC calibrated against HPET
[   20.566587] time.c: Detected 3706.131 MHz processor.
```

---

### Post by afeasfaerw23231233 on 2008-12-26
bump

---

### Post by afeasfaerw23231233 on 2008-12-28
bump

---

### Post by afeasfaerw23231233 on 2009-01-01
bump

---

### Post by happyhamster on 2009-01-01
Try the parameter clocksource=hpet instead of hpet=force. See:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414)

Good luck.

---

