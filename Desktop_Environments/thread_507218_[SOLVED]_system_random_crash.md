---
title: "[SOLVED] system random crash"
date: 2007-07-22
forum: Desktop Environments
---

### Post by holyskeleton on 2007-07-22
heres the system log messages:

Jul 22 15:39:05 hh-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul 22 15:39:19 hh-desktop exiting on signal 15
Jul 22 15:40:49 hh-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul 22 15:40:50 hh-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic
Jul 22 15:40:50 hh-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Jul 22 15:40:50 hh-desktop kernel: Symbols match kernel version 2.6.20.
Jul 22 15:40:50 hh-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] sanitize start
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] sanitize end
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fbf0000 end: 000000003fcf0000 type: 1
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcf0000 size: 000000000000f000 end: 000000003fcff000 type: 3
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcff000 size: 0000000000001000 end: 000000003fd00000 type: 4
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fd00000 size: 0000000000180000 end: 000000003fe80000 type: 1
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fe80000 size: 0000000000180000 end: 0000000040000000 type: 2
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fcf0000 (usable)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcf0000 - 000000003fcff000 (ACPI data)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcff000 - 000000003fd00000 (ACPI NVS)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fd00000 - 000000003fe80000 (usable)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fe80000 - 0000000040000000 (reserved)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] 126MB HIGHMEM available.
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] 896MB LOWMEM available.
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] found SMP MP-table at 000f6690
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]   HighMem    229376 ->   261760
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul 22 15:40:50 hh-desktop kernel: [    0.000000]     0:        0 ->   261760
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] DMI present.
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] Processor #0 15:2 APIC version 20
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf800000)
Jul 22 15:40:50 hh-desktop kernel: [    0.000000] Detected 1993.579 MHz processor.
Jul 22 15:40:50 hh-desktop kernel: [   17.103370] Built 1 zonelists.  Total pages: 259715
Jul 22 15:40:50 hh-desktop kernel: [   17.103377] Kernel command line: root=UUID=cec7c039-003b-47b3-93fd-9645c20ab27d ro quiet splash
Jul 22 15:40:50 hh-desktop kernel: [   17.103598] Enabling fast FPU save and restore... done.
Jul 22 15:40:50 hh-desktop kernel: [   17.103602] Enabling unmasked SIMD FPU exception support... done.
Jul 22 15:40:50 hh-desktop kernel: [   17.103618] Initializing CPU#0
Jul 22 15:40:50 hh-desktop kernel: [   17.103713] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jul 22 15:40:50 hh-desktop kernel: [   17.105483] Console: colour VGA+ 80x25
Jul 22 15:40:50 hh-desktop kernel: [   17.106398] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 22 15:40:50 hh-desktop kernel: [   17.107864] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 22 15:40:50 hh-desktop kernel: [   17.143931] Memory: 1026548k/1047040k available (1992k kernel code, 19696k reserved, 893k data, 328k init, 129472k highmem)
Jul 22 15:40:50 hh-desktop kernel: [   17.143946] virtual kernel memory layout:
Jul 22 15:40:50 hh-desktop kernel: [   17.143948]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jul 22 15:40:50 hh-desktop kernel: [   17.143949]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 22 15:40:50 hh-desktop kernel: [   17.143951]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jul 22 15:40:50 hh-desktop kernel: [   17.143952]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jul 22 15:40:50 hh-desktop kernel: [   17.143953]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Jul 22 15:40:50 hh-desktop kernel: [   17.143955]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Jul 22 15:40:50 hh-desktop kernel: [   17.143956]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Jul 22 15:40:50 hh-desktop kernel: [   17.143960] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul 22 15:40:50 hh-desktop kernel: [   17.223571] Calibrating delay using timer specific routine.. 3990.93 BogoMIPS (lpj=7981870)
Jul 22 15:40:50 hh-desktop kernel: [   17.223643] Security Framework v1.0.0 initialized
Jul 22 15:40:50 hh-desktop kernel: [   17.223657] SELinux:  Disabled at boot.
Jul 22 15:40:50 hh-desktop kernel: [   17.223684] Mount-cache hash table entries: 512
Jul 22 15:40:50 hh-desktop kernel: [   17.223962] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jul 22 15:40:50 hh-desktop kernel: [   17.223966] CPU: L2 cache: 128K
Jul 22 15:40:50 hh-desktop kernel: [   17.223969] CPU: Hyper-Threading is disabled
Jul 22 15:40:50 hh-desktop kernel: [   17.223991] Compat vDSO mapped to ffffe000.
Jul 22 15:40:50 hh-desktop kernel: [   17.223998] Remapping vsyscall page to ffffe000
Jul 22 15:40:50 hh-desktop kernel: [   17.224018] Checking 'hlt' instruction... OK.
Jul 22 15:40:50 hh-desktop kernel: [   17.239707] SMP alternatives: switching to UP code
Jul 22 15:40:50 hh-desktop kernel: [   17.240109] Freeing SMP alternatives: 11k freed
Jul 22 15:40:50 hh-desktop kernel: [   17.240447] Early unpacking initramfs... done
Jul 22 15:40:50 hh-desktop kernel: [   17.670164] ACPI: Core revision 20060707
Jul 22 15:40:50 hh-desktop kernel: [   17.671357] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jul 22 15:40:50 hh-desktop kernel: [   17.676213] CPU0: Intel(R) Celeron(R) CPU 2.00GHz stepping 07
Jul 22 15:40:50 hh-desktop kernel: [   17.676353] Total of 1 processors activated (3990.93 BogoMIPS).
Jul 22 15:40:50 hh-desktop kernel: [   17.676678] ENABLING IO-APIC IRQs
Jul 22 15:40:50 hh-desktop kernel: [   17.677010] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jul 22 15:40:50 hh-desktop kernel: [   17.823053] Brought up 1 CPUs
Jul 22 15:40:50 hh-desktop kernel: [   17.823537] Booting paravirtualized kernel on bare hardware
Jul 22 15:40:50 hh-desktop kernel: [   17.823705] Time: 20:39:55  Date: 06/22/107
Jul 22 15:40:50 hh-desktop kernel: [   17.823756] NET: Registered protocol family 16
Jul 22 15:40:50 hh-desktop kernel: [   17.823979] EISA bus registered
Jul 22 15:40:50 hh-desktop kernel: [   17.823993] ACPI: bus type pci registered
Jul 22 15:40:50 hh-desktop kernel: [   17.826672] PCI: PCI BIOS revision 2.10 entry at 0xfd99a, last bus=2
Jul 22 15:40:50 hh-desktop kernel: [   17.826675] PCI: Using configuration type 1
Jul 22 15:40:50 hh-desktop kernel: [   17.826677] Setting up standard PCI resources
Jul 22 15:40:50 hh-desktop kernel: [   17.871958] ACPI: Interpreter enabled
Jul 22 15:40:50 hh-desktop kernel: [   17.871966] ACPI: Using IOAPIC for interrupt routing
Jul 22 15:40:50 hh-desktop kernel: [   17.872852] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 22 15:40:50 hh-desktop kernel: [   17.875525] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jul 22 15:40:50 hh-desktop kernel: [   17.875527] * this clock source is slow. If you are sure your timer does not have
Jul 22 15:40:50 hh-desktop kernel: [   17.875529] * this bug, please use "acpi_pm_good" to disable the workaround
Jul 22 15:40:50 hh-desktop kernel: [   17.875583] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Jul 22 15:40:50 hh-desktop kernel: [   17.875587] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
Jul 22 15:40:50 hh-desktop kernel: [   17.876056] PCI: Transparent bridge - 0000:00:1e.0
Jul 22 15:40:50 hh-desktop kernel: [   17.883587] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 15:40:50 hh-desktop kernel: [   17.884033] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 15:40:50 hh-desktop kernel: [   17.884476] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
Jul 22 15:40:50 hh-desktop kernel: [   17.884932] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jul 22 15:40:50 hh-desktop kernel: [   17.885393] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 15:40:50 hh-desktop kernel: [   17.885834] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 15:40:50 hh-desktop kernel: [   17.886274] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 15:40:50 hh-desktop kernel: [   17.886724] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 15:40:50 hh-desktop kernel: [   17.890953] ACPI: Power Resource [FN01] (on)
Jul 22 15:40:50 hh-desktop kernel: [   17.891240] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 22 15:40:50 hh-desktop kernel: [   17.891274] pnp: PnP ACPI init
Jul 22 15:40:50 hh-desktop kernel: [   17.937457] pnp: PnP ACPI: found 13 devices
Jul 22 15:40:50 hh-desktop kernel: [   17.937483] PnPBIOS: Disabled by ACPI PNP
Jul 22 15:40:50 hh-desktop kernel: [   17.937788] PCI: Using ACPI for IRQ routing
Jul 22 15:40:50 hh-desktop kernel: [   17.937796] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 22 15:40:50 hh-desktop kernel: [   17.944291] NET: Registered protocol family 8
Jul 22 15:40:50 hh-desktop kernel: [   17.944302] NET: Registered protocol family 20
Jul 22 15:40:50 hh-desktop kernel: [   17.946195] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
Jul 22 15:40:50 hh-desktop kernel: [   17.946214] PCI: Bridge: 0000:00:1e.0
Jul 22 15:40:50 hh-desktop kernel: [   17.946218]   IO window: 2000-2fff
Jul 22 15:40:50 hh-desktop kernel: [   17.946225]   MEM window: e8100000-e81fffff
Jul 22 15:40:50 hh-desktop kernel: [   17.946230]   PREFETCH window: disabled.
Jul 22 15:40:50 hh-desktop kernel: [   17.946294] NET: Registered protocol family 2
Jul 22 15:40:50 hh-desktop kernel: [   17.982765] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 22 15:40:50 hh-desktop kernel: [   17.983117] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 22 15:40:50 hh-desktop kernel: [   17.984817] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 22 15:40:50 hh-desktop kernel: [   17.985673] TCP: Hash tables configured (established 131072 bind 65536)
Jul 22 15:40:50 hh-desktop kernel: [   17.985681] TCP reno registered
Jul 22 15:40:50 hh-desktop kernel: [   17.994860] checking if image is initramfs... it is
Jul 22 15:40:50 hh-desktop kernel: [   19.263792] Freeing initrd memory: 7012k freed
Jul 22 15:40:50 hh-desktop kernel: [   19.264206] Simple Boot Flag at 0x3b set to 0x1
Jul 22 15:40:50 hh-desktop kernel: [   19.264889] audit: initializing netlink socket (disabled)
Jul 22 15:40:50 hh-desktop kernel: [   19.264911] audit(1185136796.244:1): initialized
Jul 22 15:40:50 hh-desktop kernel: [   19.265095] highmem bounce pool size: 64 pages
Jul 22 15:40:50 hh-desktop kernel: [   19.265255] VFS: Disk quotas dquot_6.5.1
Jul 22 15:40:50 hh-desktop kernel: [   19.265288] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 22 15:40:50 hh-desktop kernel: [   19.265393] io scheduler noop registered
Jul 22 15:40:50 hh-desktop kernel: [   19.265399] io scheduler anticipatory registered
Jul 22 15:40:50 hh-desktop kernel: [   19.265402] io scheduler deadline registered
Jul 22 15:40:50 hh-desktop kernel: [   19.265421] io scheduler cfq registered (default)
Jul 22 15:40:50 hh-desktop kernel: [   19.265984] isapnp: Scanning for PnP cards...
Jul 22 15:40:50 hh-desktop kernel: [   19.619880] isapnp: No Plug & Play device found
Jul 22 15:40:50 hh-desktop kernel: [   19.755302] Real Time Clock Driver v1.12ac
Jul 22 15:40:50 hh-desktop kernel: [   19.755447] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 22 15:40:50 hh-desktop kernel: [   19.755661] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 15:40:50 hh-desktop kernel: [   19.757922] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 15:40:50 hh-desktop kernel: [   19.758696] mice: PS/2 mouse device common for all mice
Jul 22 15:40:50 hh-desktop kernel: [   19.760634] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 22 15:40:50 hh-desktop kernel: [   19.760992] input: Macintosh mouse button emulation as /class/input/input0
Jul 22 15:40:50 hh-desktop kernel: [   19.761098] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 22 15:40:50 hh-desktop kernel: [   19.761106] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 22 15:40:50 hh-desktop kernel: [   19.761570] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Jul 22 15:40:50 hh-desktop kernel: [   19.764714] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 22 15:40:50 hh-desktop kernel: [   19.764725] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 22 15:40:50 hh-desktop kernel: [   19.765095] EISA: Probing bus 0 at eisa.0
Jul 22 15:40:50 hh-desktop kernel: [   19.765108] Cannot allocate resource for EISA slot 1
Jul 22 15:40:50 hh-desktop kernel: [   19.765112] Cannot allocate resource for EISA slot 2
Jul 22 15:40:50 hh-desktop kernel: [   19.765138] EISA: Detected 0 cards.
Jul 22 15:40:50 hh-desktop kernel: [   19.795444] TCP cubic registered
Jul 22 15:40:50 hh-desktop kernel: [   19.795488] NET: Registered protocol family 1
Jul 22 15:40:50 hh-desktop kernel: [   19.795589] Using IPI No-Shortcut mode
Jul 22 15:40:50 hh-desktop kernel: [   19.796013] ACPI: (supports S0 S1 S3 S4 S5)
Jul 22 15:40:50 hh-desktop kernel: [   19.796113]   Magic number: 15:912:700
Jul 22 15:40:50 hh-desktop kernel: [   19.796411] Time: tsc clocksource has been installed.
Jul 22 15:40:50 hh-desktop kernel: [   19.796854] Freeing unused kernel memory: 328k freed
Jul 22 15:40:50 hh-desktop kernel: [   19.812457] input: AT Translated Set 2 keyboard as /class/input/input1
Jul 22 15:40:50 hh-desktop kernel: [   21.445293] Capability LSM initialized
Jul 22 15:40:50 hh-desktop kernel: [   22.016570] ACPI: Transitioning device [FAN1] to D0
Jul 22 15:40:50 hh-desktop kernel: [   22.016576] ACPI: Transitioning device [FAN1] to D0
Jul 22 15:40:50 hh-desktop kernel: [   22.016583] ACPI: Fan [FAN1] (off)
Jul 22 15:40:50 hh-desktop kernel: [   22.023676] ACPI: Processor [CPU0] (supports 8 throttling states)
Jul 22 15:40:50 hh-desktop kernel: [   22.032761] ACPI: Thermal Zone [THRM] (-264 C)
Jul 22 15:40:50 hh-desktop kernel: [   32.287755] usbcore: registered new interface driver usbfs
Jul 22 15:40:50 hh-desktop kernel: [   32.287810] usbcore: registered new interface driver hub
Jul 22 15:40:50 hh-desktop kernel: [   32.287874] usbcore: registered new device driver usb
Jul 22 15:40:50 hh-desktop kernel: [   32.289376] USB Universal Host Controller Interface driver v3.0
Jul 22 15:40:50 hh-desktop kernel: [   32.289468] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 15:40:50 hh-desktop kernel: [   32.289491] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 22 15:40:50 hh-desktop kernel: [   32.289693] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jul 22 15:40:50 hh-desktop kernel: [   32.289734] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
Jul 22 15:40:50 hh-desktop kernel: [   32.289947] usb usb1: configuration #1 chosen from 1 choice
Jul 22 15:40:50 hh-desktop kernel: [   32.290003] hub 1-0:1.0: USB hub found
Jul 22 15:40:50 hh-desktop kernel: [   32.290020] hub 1-0:1.0: 2 ports detected
Jul 22 15:40:50 hh-desktop kernel: [   32.396225] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Jul 22 15:40:50 hh-desktop kernel: [   32.396249] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 22 15:40:50 hh-desktop kernel: [   32.396301] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jul 22 15:40:50 hh-desktop kernel: [   32.396337] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
Jul 22 15:40:50 hh-desktop kernel: [   32.396504] usb usb2: configuration #1 chosen from 1 choice
Jul 22 15:40:50 hh-desktop kernel: [   32.396554] hub 2-0:1.0: USB hub found
Jul 22 15:40:50 hh-desktop kernel: [   32.396568] hub 2-0:1.0: 2 ports detected
Jul 22 15:40:50 hh-desktop kernel: [   32.475020] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jul 22 15:40:50 hh-desktop kernel: [   32.500081] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 22 15:40:50 hh-desktop kernel: [   32.500105] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 22 15:40:50 hh-desktop kernel: [   32.500155] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jul 22 15:40:50 hh-desktop kernel: [   32.500201] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Jul 22 15:40:50 hh-desktop kernel: [   32.500379] usb usb3: configuration #1 chosen from 1 choice
Jul 22 15:40:50 hh-desktop kernel: [   32.500430] hub 3-0:1.0: USB hub found
Jul 22 15:40:50 hh-desktop kernel: [   32.500447] hub 3-0:1.0: 2 ports detected
Jul 22 15:40:50 hh-desktop kernel: [   32.604911] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Jul 22 15:40:50 hh-desktop kernel: [   32.604943] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 22 15:40:50 hh-desktop kernel: [   32.605009] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jul 22 15:40:50 hh-desktop kernel: [   32.605081] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe8080000
Jul 22 15:40:50 hh-desktop kernel: [   32.608977] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 22 15:40:50 hh-desktop kernel: [   32.609133] usb usb4: configuration #1 chosen from 1 choice
Jul 22 15:40:50 hh-desktop kernel: [   32.609184] hub 4-0:1.0: USB hub found
Jul 22 15:40:50 hh-desktop kernel: [   32.609201] hub 4-0:1.0: 6 ports detected
Jul 22 15:40:50 hh-desktop kernel: [   32.638004] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jul 22 15:40:50 hh-desktop kernel: [   32.638462] SCSI subsystem initialized
Jul 22 15:40:50 hh-desktop kernel: [   32.716223] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Jul 22 15:40:50 hh-desktop kernel: [   32.716230] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
Jul 22 15:40:50 hh-desktop kernel: [   32.719152] 8139too Fast Ethernet driver 0.9.28
Jul 22 15:40:50 hh-desktop kernel: [   32.719237] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 20
Jul 22 15:40:50 hh-desktop kernel: [   32.719633] eth0: RealTek RTL8139 at 0xf8848000, 00:40:2b:41:30:ec, IRQ 20
Jul 22 15:40:50 hh-desktop kernel: [   32.720134] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Jul 22 15:40:50 hh-desktop kernel: [   32.720145] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Jul 22 15:40:50 hh-desktop kernel: [   32.720294] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
Jul 22 15:40:50 hh-desktop kernel: [   32.720369] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
Jul 22 15:40:50 hh-desktop kernel: [   32.720401] scsi0 : ata_piix
Jul 22 15:40:50 hh-desktop kernel: [   32.888505] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 15:40:50 hh-desktop kernel: [   32.888512] ata1.00: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
Jul 22 15:40:50 hh-desktop kernel: [   32.888516] ata1.00: 78165360 sectors, multi 16: LBA 
Jul 22 15:40:50 hh-desktop kernel: [   32.900777] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 15:40:50 hh-desktop kernel: [   32.900783] ata1.00: configured for UDMA/100
Jul 22 15:40:50 hh-desktop kernel: [   32.900803] scsi1 : ata_piix
Jul 22 15:40:50 hh-desktop kernel: [   33.160429] Floppy drive(s): fd0 is 1.44M
Jul 22 15:40:50 hh-desktop kernel: [   33.182732] FDC 0 is a post-1991 82077
Jul 22 15:40:50 hh-desktop kernel: [   33.223216] ata2.00: ATAPI, max MWDMA2
Jul 22 15:40:50 hh-desktop kernel: [   33.387261] ata2.00: configured for MWDMA2
Jul 22 15:40:50 hh-desktop kernel: [   33.390721] usb 1-1: new full speed USB device using uhci_hcd and address 3
Jul 22 15:40:50 hh-desktop kernel: [   33.390764] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
Jul 22 15:40:50 hh-desktop kernel: [   33.392567] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-240B  R400 PQ: 0 ANSI: 5
Jul 22 15:40:50 hh-desktop kernel: [   33.581052] usb 1-1: configuration #1 chosen from 1 choice
Jul 22 15:40:50 hh-desktop kernel: [   34.013940] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 15:40:50 hh-desktop kernel: [   34.014917] sda: Write Protect is off
Jul 22 15:40:50 hh-desktop kernel: [   34.018900] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 15:40:50 hh-desktop kernel: [   34.022902] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 15:40:50 hh-desktop kernel: [   34.025885] sda: Write Protect is off
Jul 22 15:40:50 hh-desktop kernel: [   34.029882] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 15:40:50 hh-desktop kernel: [   34.029889]  sda: sda1 sda2 < sda5 >
Jul 22 15:40:50 hh-desktop kernel: [   34.088782] sd 0:0:0:0: Attached scsi disk sda
Jul 22 15:40:50 hh-desktop kernel: [   34.096151] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 22 15:40:50 hh-desktop kernel: [   34.096192] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 22 15:40:50 hh-desktop kernel: [   34.100631] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jul 22 15:40:50 hh-desktop kernel: [   34.100639] Uniform CD-ROM driver Revision: 3.20
Jul 22 15:40:50 hh-desktop kernel: [   34.257788] usbcore: registered new interface driver hiddev
Jul 22 15:40:50 hh-desktop kernel: [   34.274112] input: Logitech USB Gaming Mouse as /class/input/input2
Jul 22 15:40:50 hh-desktop kernel: [   34.274160] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 15:40:50 hh-desktop kernel: [   34.279968] hiddev96: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 15:40:50 hh-desktop kernel: [   34.279995] usbcore: registered new interface driver usbhid
Jul 22 15:40:50 hh-desktop kernel: [   34.279999] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul 22 15:40:50 hh-desktop kernel: [   35.927841] Attempting manual resume
Jul 22 15:40:50 hh-desktop kernel: [   36.550684] kjournald starting.  Commit interval 5 seconds
Jul 22 15:40:50 hh-desktop kernel: [   36.550711] EXT3-fs: mounted filesystem with ordered data mode.
Jul 22 15:40:50 hh-desktop kernel: [   59.163971] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 22 15:40:50 hh-desktop kernel: [   60.656532] NET: Registered protocol family 17
Jul 22 15:40:50 hh-desktop kernel: [   62.026175] Linux agpgart interface v0.102 (c) Dave Jones
Jul 22 15:40:50 hh-desktop kernel: [   62.029011] agpgart: Detected an Intel 845G Chipset.
Jul 22 15:40:50 hh-desktop kernel: [   62.029139] agpgart: Detected 892K stolen memory.
Jul 22 15:40:50 hh-desktop kernel: [   62.249494] agpgart: AGP aperture is 128M @ 0xf0000000
Jul 22 15:40:50 hh-desktop kernel: [   62.407520] iTCO_vendor_support: vendor-support=0
Jul 22 15:40:50 hh-desktop kernel: [   62.409389] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Jul 22 15:40:50 hh-desktop kernel: [   62.409618] iTCO_wdt: No card detected
Jul 22 15:40:50 hh-desktop kernel: [   62.444269] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 22 15:40:50 hh-desktop kernel: [   62.451638] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 22 15:40:50 hh-desktop kernel: [   62.512473] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Jul 22 15:40:50 hh-desktop kernel: [   62.813134] input: PC Speaker as /class/input/input3
Jul 22 15:40:50 hh-desktop kernel: [   62.954627] parport: PnPBIOS parport detected.
Jul 22 15:40:50 hh-desktop kernel: [   62.954686] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul 22 15:40:50 hh-desktop kernel: [   63.773311] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
Jul 22 15:40:50 hh-desktop kernel: [   63.810560] usbcore: registered new interface driver xpad
Jul 22 15:40:50 hh-desktop kernel: [   63.810567] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
Jul 22 15:40:50 hh-desktop kernel: [   64.086948] intel8x0_measure_ac97_clock: measured 55026 usecs
Jul 22 15:40:50 hh-desktop kernel: [   64.086953] intel8x0: clocking to 48000
Jul 22 15:40:50 hh-desktop kernel: [   64.383185] fuse init (API version 7.8)
Jul 22 15:40:50 hh-desktop kernel: [   64.416671] lp0: using parport0 (interrupt-driven).
Jul 22 15:40:50 hh-desktop kernel: [   64.482043] Adding 1646620k swap on /dev/disk/by-uuid/b35569b7-a093-4d4e-b5f8-cbe0e1cf4b6c.  Priority:-1 extents:1 across:1646620k
Jul 22 15:40:50 hh-desktop kernel: [   64.669272] EXT3 FS on sda1, internal journal
Jul 22 15:40:50 hh-desktop kernel: [   64.953103] NET: Registered protocol family 10
Jul 22 15:40:50 hh-desktop kernel: [   64.953273] lo: Disabled Privacy Extensions
Jul 22 15:40:50 hh-desktop kernel: [   71.106562] input: Power Button (FF) as /class/input/input4
Jul 22 15:40:50 hh-desktop kernel: [   71.114514] ACPI: Power Button (FF) [PWRF]
Jul 22 15:40:50 hh-desktop kernel: [   71.160216] input: Power Button (CM) as /class/input/input5
Jul 22 15:40:50 hh-desktop kernel: [   71.168079] ACPI: Power Button (CM) [PWRB]
Jul 22 15:40:50 hh-desktop kernel: [   71.221849] Using specific hotkey driver
Jul 22 15:40:50 hh-desktop kernel: [   71.359915] No dock devices found.
Jul 22 15:40:50 hh-desktop kernel: [   71.629757] pcc_acpi: loading...
Jul 22 15:40:54 hh-desktop dhcdbd: Started up.
Jul 22 15:40:55 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 15:40:55 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 15:40:55 hh-desktop kernel: [   78.163366] ppdev: user-space parallel port driver
Jul 22 15:40:56 hh-desktop kernel: [   78.804072] [drm] Initialized drm 1.1.0 20060810
Jul 22 15:40:56 hh-desktop kernel: [   78.813252] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 15:40:56 hh-desktop kernel: [   78.818044] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul 22 15:40:57 hh-desktop hpiod: 1.7.3 accepting connections at 2208... 
Jul 22 15:40:58 hh-desktop kernel: [   80.887587] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 22 15:40:58 hh-desktop kernel: [   80.887595] apm: overridden by ACPI.
Jul 22 15:40:59 hh-desktop kernel: [   81.361573] Bluetooth: Core ver 2.11
Jul 22 15:40:59 hh-desktop kernel: [   81.361682] NET: Registered protocol family 31
Jul 22 15:40:59 hh-desktop kernel: [   81.361686] Bluetooth: HCI device and connection manager initialized
Jul 22 15:40:59 hh-desktop kernel: [   81.361692] Bluetooth: HCI socket layer initialized
Jul 22 15:40:59 hh-desktop kernel: [   81.479055] Bluetooth: L2CAP ver 2.8
Jul 22 15:40:59 hh-desktop kernel: [   81.479063] Bluetooth: L2CAP socket layer initialized
Jul 22 15:40:59 hh-desktop kernel: [   81.623174] Bluetooth: RFCOMM socket layer initialized
Jul 22 15:40:59 hh-desktop kernel: [   81.623198] Bluetooth: RFCOMM TTY layer initialized
Jul 22 15:40:59 hh-desktop kernel: [   81.623201] Bluetooth: RFCOMM ver 1.8
Jul 22 15:41:01 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 22 15:41:01 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 22 15:41:01 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 22 15:41:07 hh-desktop gconfd (hh-5474): starting (version 2.18.0.1), pid 5474 user 'hh'
Jul 22 15:41:07 hh-desktop gconfd (hh-5474): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 15:41:07 hh-desktop gconfd (hh-5474): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 15:41:07 hh-desktop gconfd (hh-5474): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 15:41:07 hh-desktop gconfd (hh-5474): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 15:41:07 hh-desktop gconfd (hh-5474): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 15:41:14 hh-desktop gconfd (hh-5474): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 0
Jul 22 15:43:37 hh-desktop gconfd (hh-5474): SIGHUP received, reloading all databases
Jul 22 15:43:37 hh-desktop gconfd (hh-5474): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 15:43:37 hh-desktop gconfd (hh-5474): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 15:43:37 hh-desktop gconfd (hh-5474): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 15:43:37 hh-desktop gconfd (hh-5474): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 15:43:37 hh-desktop gconfd (hh-5474): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 15:44:03 hh-desktop kernel: [  263.154075] ACPI: Critical trip point
Jul 22 15:44:05 hh-desktop gconfd (hh-5474): Received signal 15, shutting down cleanly
Jul 22 15:44:05 hh-desktop gconfd (hh-5474): Exiting
Jul 22 15:44:12 hh-desktop exiting on signal 15
Jul 22 15:45:42 hh-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul 22 15:45:42 hh-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic
Jul 22 15:45:42 hh-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Jul 22 15:45:42 hh-desktop kernel: Symbols match kernel version 2.6.20.
Jul 22 15:45:42 hh-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] sanitize start
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] sanitize end
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fbf0000 end: 000000003fcf0000 type: 1
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcf0000 size: 000000000000f000 end: 000000003fcff000 type: 3
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcff000 size: 0000000000001000 end: 000000003fd00000 type: 4
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fd00000 size: 0000000000180000 end: 000000003fe80000 type: 1
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fe80000 size: 0000000000180000 end: 0000000040000000 type: 2
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fcf0000 (usable)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcf0000 - 000000003fcff000 (ACPI data)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcff000 - 000000003fd00000 (ACPI NVS)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fd00000 - 000000003fe80000 (usable)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fe80000 - 0000000040000000 (reserved)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] 126MB HIGHMEM available.
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] 896MB LOWMEM available.
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] found SMP MP-table at 000f6690
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]   HighMem    229376 ->   261760
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul 22 15:45:42 hh-desktop kernel: [    0.000000]     0:        0 ->   261760
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] DMI present.
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] Processor #0 15:2 APIC version 20
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf800000)
Jul 22 15:45:42 hh-desktop kernel: [    0.000000] Detected 1993.687 MHz processor.
Jul 22 15:45:42 hh-desktop kernel: [   14.945970] Built 1 zonelists.  Total pages: 259715
Jul 22 15:45:42 hh-desktop kernel: [   14.945977] Kernel command line: root=UUID=cec7c039-003b-47b3-93fd-9645c20ab27d ro quiet splash
Jul 22 15:45:42 hh-desktop kernel: [   14.946197] Enabling fast FPU save and restore... done.
Jul 22 15:45:42 hh-desktop kernel: [   14.946202] Enabling unmasked SIMD FPU exception support... done.
Jul 22 15:45:42 hh-desktop kernel: [   14.946218] Initializing CPU#0
Jul 22 15:45:42 hh-desktop kernel: [   14.946314] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jul 22 15:45:42 hh-desktop kernel: [   14.948064] Console: colour VGA+ 80x25
Jul 22 15:45:42 hh-desktop kernel: [   14.948991] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 22 15:45:42 hh-desktop kernel: [   14.950415] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 22 15:45:42 hh-desktop kernel: [   14.989583] Memory: 1026548k/1047040k available (1992k kernel code, 19696k reserved, 893k data, 328k init, 129472k highmem)
Jul 22 15:45:42 hh-desktop kernel: [   14.989600] virtual kernel memory layout:
Jul 22 15:45:42 hh-desktop kernel: [   14.989601]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jul 22 15:45:42 hh-desktop kernel: [   14.989603]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 22 15:45:42 hh-desktop kernel: [   14.989604]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jul 22 15:45:42 hh-desktop kernel: [   14.989606]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jul 22 15:45:42 hh-desktop kernel: [   14.989607]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Jul 22 15:45:42 hh-desktop kernel: [   14.989609]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Jul 22 15:45:42 hh-desktop kernel: [   14.989611]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Jul 22 15:45:42 hh-desktop kernel: [   14.989615] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul 22 15:45:42 hh-desktop kernel: [   15.066173] Calibrating delay using timer specific routine.. 3991.00 BogoMIPS (lpj=7982016)
Jul 22 15:45:42 hh-desktop kernel: [   15.066251] Security Framework v1.0.0 initialized
Jul 22 15:45:42 hh-desktop kernel: [   15.066267] SELinux:  Disabled at boot.
Jul 22 15:45:42 hh-desktop kernel: [   15.066292] Mount-cache hash table entries: 512
Jul 22 15:45:42 hh-desktop kernel: [   15.066566] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jul 22 15:45:42 hh-desktop kernel: [   15.066570] CPU: L2 cache: 128K
Jul 22 15:45:42 hh-desktop kernel: [   15.066574] CPU: Hyper-Threading is disabled
Jul 22 15:45:42 hh-desktop kernel: [   15.066597] Compat vDSO mapped to ffffe000.
Jul 22 15:45:42 hh-desktop kernel: [   15.066603] Remapping vsyscall page to ffffe000
Jul 22 15:45:42 hh-desktop kernel: [   15.066621] Checking 'hlt' instruction... OK.
Jul 22 15:45:42 hh-desktop kernel: [   15.082307] SMP alternatives: switching to UP code
Jul 22 15:45:42 hh-desktop kernel: [   15.082707] Freeing SMP alternatives: 11k freed
Jul 22 15:45:42 hh-desktop kernel: [   15.083043] Early unpacking initramfs... done
Jul 22 15:45:42 hh-desktop kernel: [   15.512567] ACPI: Core revision 20060707
Jul 22 15:45:42 hh-desktop kernel: [   15.513758] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jul 22 15:45:42 hh-desktop kernel: [   15.518618] CPU0: Intel(R) Celeron(R) CPU 2.00GHz stepping 07
Jul 22 15:45:42 hh-desktop kernel: [   15.518759] Total of 1 processors activated (3991.00 BogoMIPS).
Jul 22 15:45:42 hh-desktop kernel: [   15.519084] ENABLING IO-APIC IRQs
Jul 22 15:45:42 hh-desktop kernel: [   15.519416] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jul 22 15:45:42 hh-desktop kernel: [   15.665545] Brought up 1 CPUs
Jul 22 15:45:42 hh-desktop kernel: [   15.665952] Booting paravirtualized kernel on bare hardware
Jul 22 15:45:42 hh-desktop kernel: [   15.666272] Time: 20:44:46  Date: 06/22/107
Jul 22 15:45:42 hh-desktop kernel: [   15.666396] NET: Registered protocol family 16
Jul 22 15:45:42 hh-desktop kernel: [   15.666910] EISA bus registered
Jul 22 15:45:42 hh-desktop kernel: [   15.666946] ACPI: bus type pci registered
Jul 22 15:45:42 hh-desktop kernel: [   15.670323] PCI: PCI BIOS revision 2.10 entry at 0xfd99a, last bus=2
Jul 22 15:45:42 hh-desktop kernel: [   15.670330] PCI: Using configuration type 1
Jul 22 15:45:42 hh-desktop kernel: [   15.670336] Setting up standard PCI resources
Jul 22 15:45:42 hh-desktop kernel: [   15.724400] ACPI: Interpreter enabled
Jul 22 15:45:42 hh-desktop kernel: [   15.724418] ACPI: Using IOAPIC for interrupt routing
Jul 22 15:45:42 hh-desktop kernel: [   15.726014] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 22 15:45:42 hh-desktop kernel: [   15.729005] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jul 22 15:45:42 hh-desktop kernel: [   15.729010] * this clock source is slow. If you are sure your timer does not have
Jul 22 15:45:42 hh-desktop kernel: [   15.729015] * this bug, please use "acpi_pm_good" to disable the workaround
Jul 22 15:45:42 hh-desktop kernel: [   15.729136] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Jul 22 15:45:42 hh-desktop kernel: [   15.729148] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
Jul 22 15:45:42 hh-desktop kernel: [   15.730071] PCI: Transparent bridge - 0000:00:1e.0
Jul 22 15:45:42 hh-desktop kernel: [   15.738993] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 15:45:42 hh-desktop kernel: [   15.739722] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 15:45:42 hh-desktop kernel: [   15.740535] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
Jul 22 15:45:42 hh-desktop kernel: [   15.740995] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jul 22 15:45:42 hh-desktop kernel: [   15.741512] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 15:45:42 hh-desktop kernel: [   15.742334] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 15:45:42 hh-desktop kernel: [   15.743150] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 15:45:42 hh-desktop kernel: [   15.743614] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 15:45:42 hh-desktop kernel: [   15.748428] ACPI: Power Resource [FN01] (on)
Jul 22 15:45:42 hh-desktop kernel: [   15.748712] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 22 15:45:42 hh-desktop kernel: [   15.748743] pnp: PnP ACPI init
Jul 22 15:45:42 hh-desktop kernel: [   15.803548] pnp: PnP ACPI: found 13 devices
Jul 22 15:45:42 hh-desktop kernel: [   15.803574] PnPBIOS: Disabled by ACPI PNP
Jul 22 15:45:42 hh-desktop kernel: [   15.803902] PCI: Using ACPI for IRQ routing
Jul 22 15:45:42 hh-desktop kernel: [   15.803919] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 22 15:45:42 hh-desktop kernel: [   15.811958] NET: Registered protocol family 8
Jul 22 15:45:42 hh-desktop kernel: [   15.811969] NET: Registered protocol family 20
Jul 22 15:45:42 hh-desktop kernel: [   15.813841] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
Jul 22 15:45:42 hh-desktop kernel: [   15.813860] PCI: Bridge: 0000:00:1e.0
Jul 22 15:45:42 hh-desktop kernel: [   15.813864]   IO window: 2000-2fff
Jul 22 15:45:42 hh-desktop kernel: [   15.813871]   MEM window: e8100000-e81fffff
Jul 22 15:45:42 hh-desktop kernel: [   15.813876]   PREFETCH window: disabled.
Jul 22 15:45:42 hh-desktop kernel: [   15.813941] NET: Registered protocol family 2
Jul 22 15:45:42 hh-desktop kernel: [   15.849365] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 22 15:45:42 hh-desktop kernel: [   15.849726] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 22 15:45:42 hh-desktop kernel: [   15.851428] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 22 15:45:42 hh-desktop kernel: [   15.852321] TCP: Hash tables configured (established 131072 bind 65536)
Jul 22 15:45:42 hh-desktop kernel: [   15.852329] TCP reno registered
Jul 22 15:45:42 hh-desktop kernel: [   15.861463] checking if image is initramfs... it is
Jul 22 15:45:42 hh-desktop kernel: [   17.298363] Freeing initrd memory: 7012k freed
Jul 22 15:45:42 hh-desktop kernel: [   17.298778] Simple Boot Flag at 0x3b set to 0x1
Jul 22 15:45:42 hh-desktop kernel: [   17.299462] audit: initializing netlink socket (disabled)
Jul 22 15:45:42 hh-desktop kernel: [   17.299484] audit(1185137087.436:1): initialized
Jul 22 15:45:42 hh-desktop kernel: [   17.299655] highmem bounce pool size: 64 pages
Jul 22 15:45:42 hh-desktop kernel: [   17.299816] VFS: Disk quotas dquot_6.5.1
Jul 22 15:45:42 hh-desktop kernel: [   17.299850] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 22 15:45:42 hh-desktop kernel: [   17.299951] io scheduler noop registered
Jul 22 15:45:42 hh-desktop kernel: [   17.299957] io scheduler anticipatory registered
Jul 22 15:45:42 hh-desktop kernel: [   17.299961] io scheduler deadline registered
Jul 22 15:45:42 hh-desktop kernel: [   17.299979] io scheduler cfq registered (default)
Jul 22 15:45:42 hh-desktop kernel: [   17.300553] isapnp: Scanning for PnP cards...
Jul 22 15:45:42 hh-desktop kernel: [   17.654450] isapnp: No Plug & Play device found
Jul 22 15:45:42 hh-desktop kernel: [   17.806281] Real Time Clock Driver v1.12ac
Jul 22 15:45:42 hh-desktop kernel: [   17.806422] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 22 15:45:42 hh-desktop kernel: [   17.806635] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 15:45:42 hh-desktop kernel: [   17.809620] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 15:45:42 hh-desktop kernel: [   17.810433] mice: PS/2 mouse device common for all mice
Jul 22 15:45:42 hh-desktop kernel: [   17.812368] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 22 15:45:42 hh-desktop kernel: [   17.812735] input: Macintosh mouse button emulation as /class/input/input0
Jul 22 15:45:42 hh-desktop kernel: [   17.812846] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 22 15:45:42 hh-desktop kernel: [   17.812854] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 22 15:45:42 hh-desktop kernel: [   17.813341] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Jul 22 15:45:42 hh-desktop kernel: [   17.816503] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 22 15:45:42 hh-desktop kernel: [   17.816513] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 22 15:45:42 hh-desktop kernel: [   17.816900] EISA: Probing bus 0 at eisa.0
Jul 22 15:45:42 hh-desktop kernel: [   17.816913] Cannot allocate resource for EISA slot 1
Jul 22 15:45:42 hh-desktop kernel: [   17.816916] Cannot allocate resource for EISA slot 2
Jul 22 15:45:42 hh-desktop kernel: [   17.816943] EISA: Detected 0 cards.
Jul 22 15:45:42 hh-desktop kernel: [   17.847215] TCP cubic registered
Jul 22 15:45:42 hh-desktop kernel: [   17.847270] NET: Registered protocol family 1
Jul 22 15:45:42 hh-desktop kernel: [   17.847371] Using IPI No-Shortcut mode
Jul 22 15:45:42 hh-desktop kernel: [   17.847817] ACPI: (supports S0 S1 S3 S4 S5)
Jul 22 15:45:42 hh-desktop kernel: [   17.848001]   Magic number: 15:465:751
Jul 22 15:45:42 hh-desktop kernel: [   17.848018]   hash matches device ttyS2
Jul 22 15:45:42 hh-desktop kernel: [   17.848814] Freeing unused kernel memory: 328k freed
Jul 22 15:45:42 hh-desktop kernel: [   17.850748] Time: tsc clocksource has been installed.
Jul 22 15:45:42 hh-desktop kernel: [   17.864104] input: AT Translated Set 2 keyboard as /class/input/input1
Jul 22 15:45:42 hh-desktop kernel: [   19.524728] Capability LSM initialized
Jul 22 15:45:42 hh-desktop kernel: [   20.095226] ACPI: Transitioning device [FAN1] to D0
Jul 22 15:45:42 hh-desktop kernel: [   20.095232] ACPI: Transitioning device [FAN1] to D0
Jul 22 15:45:42 hh-desktop kernel: [   20.095239] ACPI: Fan [FAN1] (off)
Jul 22 15:45:42 hh-desktop kernel: [   20.102275] ACPI: Processor [CPU0] (supports 8 throttling states)
Jul 22 15:45:42 hh-desktop kernel: [   20.111318] ACPI: Thermal Zone [THRM] (-264 C)
Jul 22 15:45:42 hh-desktop kernel: [   30.124222] usbcore: registered new interface driver usbfs
Jul 22 15:45:42 hh-desktop kernel: [   30.124274] usbcore: registered new interface driver hub
Jul 22 15:45:42 hh-desktop kernel: [   30.124339] usbcore: registered new device driver usb
Jul 22 15:45:42 hh-desktop kernel: [   30.125758] USB Universal Host Controller Interface driver v3.0
Jul 22 15:45:42 hh-desktop kernel: [   30.125854] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 15:45:42 hh-desktop kernel: [   30.125877] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 22 15:45:42 hh-desktop kernel: [   30.126066] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jul 22 15:45:42 hh-desktop kernel: [   30.126106] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
Jul 22 15:45:42 hh-desktop kernel: [   30.126312] usb usb1: configuration #1 chosen from 1 choice
Jul 22 15:45:42 hh-desktop kernel: [   30.126365] hub 1-0:1.0: USB hub found
Jul 22 15:45:42 hh-desktop kernel: [   30.126383] hub 1-0:1.0: 2 ports detected
Jul 22 15:45:42 hh-desktop kernel: [   30.228617] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Jul 22 15:45:42 hh-desktop kernel: [   30.228641] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 22 15:45:42 hh-desktop kernel: [   30.228694] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jul 22 15:45:42 hh-desktop kernel: [   30.228730] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
Jul 22 15:45:42 hh-desktop kernel: [   30.228902] usb usb2: configuration #1 chosen from 1 choice
Jul 22 15:45:42 hh-desktop kernel: [   30.228951] hub 2-0:1.0: USB hub found
Jul 22 15:45:42 hh-desktop kernel: [   30.228968] hub 2-0:1.0: 2 ports detected
Jul 22 15:45:42 hh-desktop kernel: [   30.307342] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jul 22 15:45:42 hh-desktop kernel: [   30.332455] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 22 15:45:42 hh-desktop kernel: [   30.332480] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 22 15:45:42 hh-desktop kernel: [   30.332530] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jul 22 15:45:42 hh-desktop kernel: [   30.332574] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Jul 22 15:45:42 hh-desktop kernel: [   30.332754] usb usb3: configuration #1 chosen from 1 choice
Jul 22 15:45:42 hh-desktop kernel: [   30.332810] hub 3-0:1.0: USB hub found
Jul 22 15:45:42 hh-desktop kernel: [   30.332829] hub 3-0:1.0: 2 ports detected
Jul 22 15:45:42 hh-desktop kernel: [   30.436779] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Jul 22 15:45:42 hh-desktop kernel: [   30.436809] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 22 15:45:42 hh-desktop kernel: [   30.436878] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jul 22 15:45:42 hh-desktop kernel: [   30.436946] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe8080000
Jul 22 15:45:42 hh-desktop kernel: [   30.440839] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 22 15:45:42 hh-desktop kernel: [   30.440992] usb usb4: configuration #1 chosen from 1 choice
Jul 22 15:45:42 hh-desktop kernel: [   30.441052] hub 4-0:1.0: USB hub found
Jul 22 15:45:42 hh-desktop kernel: [   30.441070] hub 4-0:1.0: 6 ports detected
Jul 22 15:45:42 hh-desktop kernel: [   30.468111] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jul 22 15:45:42 hh-desktop kernel: [   30.483305] SCSI subsystem initialized
Jul 22 15:45:42 hh-desktop kernel: [   30.544661] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Jul 22 15:45:42 hh-desktop kernel: [   30.544667] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
Jul 22 15:45:42 hh-desktop kernel: [   30.547584] 8139too Fast Ethernet driver 0.9.28
Jul 22 15:45:42 hh-desktop kernel: [   30.547667] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 20
Jul 22 15:45:42 hh-desktop kernel: [   30.548093] eth0: RealTek RTL8139 at 0xf8848000, 00:40:2b:41:30:ec, IRQ 20
Jul 22 15:45:42 hh-desktop kernel: [   30.548583] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Jul 22 15:45:42 hh-desktop kernel: [   30.548592] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Jul 22 15:45:42 hh-desktop kernel: [   30.548742] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
Jul 22 15:45:42 hh-desktop kernel: [   30.548815] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
Jul 22 15:45:42 hh-desktop kernel: [   30.548847] scsi0 : ata_piix
Jul 22 15:45:42 hh-desktop kernel: [   30.713022] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 15:45:42 hh-desktop kernel: [   30.713029] ata1.00: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
Jul 22 15:45:42 hh-desktop kernel: [   30.713033] ata1.00: 78165360 sectors, multi 16: LBA 
Jul 22 15:45:42 hh-desktop kernel: [   30.720961] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 15:45:42 hh-desktop kernel: [   30.720967] ata1.00: configured for UDMA/100
Jul 22 15:45:42 hh-desktop kernel: [   30.720986] scsi1 : ata_piix
Jul 22 15:45:42 hh-desktop kernel: [   30.971528] usb 1-1: new full speed USB device using uhci_hcd and address 3
Jul 22 15:45:42 hh-desktop kernel: [   30.996771] Floppy drive(s): fd0 is 1.44M
Jul 22 15:45:42 hh-desktop kernel: [   31.015241] FDC 0 is a post-1991 82077
Jul 22 15:45:42 hh-desktop kernel: [   31.039715] ata2.00: ATAPI, max MWDMA2
Jul 22 15:45:42 hh-desktop kernel: [   31.158795] usb 1-1: configuration #1 chosen from 1 choice
Jul 22 15:45:42 hh-desktop kernel: [   31.203522] ata2.00: configured for MWDMA2
Jul 22 15:45:42 hh-desktop kernel: [   31.207262] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
Jul 22 15:45:42 hh-desktop kernel: [   31.209049] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-240B  R400 PQ: 0 ANSI: 5
Jul 22 15:45:42 hh-desktop kernel: [   31.959063] usbcore: registered new interface driver hiddev
Jul 22 15:45:42 hh-desktop kernel: [   31.984705] input: Logitech USB Gaming Mouse as /class/input/input2
Jul 22 15:45:42 hh-desktop kernel: [   31.984822] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 15:45:42 hh-desktop kernel: [   31.986373] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jul 22 15:45:42 hh-desktop kernel: [   31.986381] Uniform CD-ROM driver Revision: 3.20
Jul 22 15:45:42 hh-desktop kernel: [   31.993918] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Jul 22 15:45:42 hh-desktop kernel: [   31.993968] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 22 15:45:42 hh-desktop kernel: [   31.994574] hiddev96: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 15:45:42 hh-desktop kernel: [   31.994601] usbcore: registered new interface driver usbhid
Jul 22 15:45:42 hh-desktop kernel: [   31.994605] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul 22 15:45:42 hh-desktop kernel: [   32.221089] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 15:45:42 hh-desktop kernel: [   32.222061] sda: Write Protect is off
Jul 22 15:45:42 hh-desktop kernel: [   32.226065] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 15:45:42 hh-desktop kernel: [   32.230047] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 15:45:42 hh-desktop kernel: [   32.233043] sda: Write Protect is off
Jul 22 15:45:42 hh-desktop kernel: [   32.237035] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 15:45:42 hh-desktop kernel: [   32.237042]  sda: sda1 sda2 < sda5 >
Jul 22 15:45:42 hh-desktop kernel: [   32.293601] sd 0:0:0:0: Attached scsi disk sda
Jul 22 15:45:42 hh-desktop kernel: [   33.880877] Attempting manual resume
Jul 22 15:45:42 hh-desktop kernel: [   34.507432] kjournald starting.  Commit interval 5 seconds
Jul 22 15:45:42 hh-desktop kernel: [   34.507458] EXT3-fs: mounted filesystem with ordered data mode.
Jul 22 15:45:42 hh-desktop kernel: [   58.001916] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 22 15:45:42 hh-desktop kernel: [   59.502039] NET: Registered protocol family 17
Jul 22 15:45:42 hh-desktop kernel: [   61.317029] iTCO_vendor_support: vendor-support=0
Jul 22 15:45:42 hh-desktop kernel: [   61.333352] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Jul 22 15:45:42 hh-desktop kernel: [   61.333576] iTCO_wdt: No card detected
Jul 22 15:45:42 hh-desktop kernel: [   61.462183] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Jul 22 15:45:42 hh-desktop kernel: [   61.630947] Linux agpgart interface v0.102 (c) Dave Jones
Jul 22 15:45:42 hh-desktop kernel: [   61.634318] agpgart: Detected an Intel 845G Chipset.
Jul 22 15:45:42 hh-desktop kernel: [   61.634538] agpgart: Detected 892K stolen memory.
Jul 22 15:45:42 hh-desktop kernel: [   61.653380] agpgart: AGP aperture is 128M @ 0xf0000000
Jul 22 15:45:42 hh-desktop kernel: [   61.679920] input: PC Speaker as /class/input/input3
Jul 22 15:45:42 hh-desktop kernel: [   61.706289] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 22 15:45:42 hh-desktop kernel: [   61.711166] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 22 15:45:42 hh-desktop kernel: [   61.896957] parport: PnPBIOS parport detected.
Jul 22 15:45:42 hh-desktop kernel: [   61.897016] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul 22 15:45:42 hh-desktop kernel: [   62.453962] usbcore: registered new interface driver xpad
Jul 22 15:45:42 hh-desktop kernel: [   62.453979] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
Jul 22 15:45:42 hh-desktop kernel: [   62.766976] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
Jul 22 15:45:42 hh-desktop kernel: [   63.081783] intel8x0_measure_ac97_clock: measured 55003 usecs
Jul 22 15:45:42 hh-desktop kernel: [   63.081789] intel8x0: clocking to 48000
Jul 22 15:45:42 hh-desktop kernel: [   63.388621] fuse init (API version 7.8)
Jul 22 15:45:42 hh-desktop kernel: [   63.422157] lp0: using parport0 (interrupt-driven).
Jul 22 15:45:42 hh-desktop kernel: [   63.487030] Adding 1646620k swap on /dev/disk/by-uuid/b35569b7-a093-4d4e-b5f8-cbe0e1cf4b6c.  Priority:-1 extents:1 across:1646620k
Jul 22 15:45:42 hh-desktop kernel: [   63.672656] EXT3 FS on sda1, internal journal
Jul 22 15:45:42 hh-desktop kernel: [   63.991454] NET: Registered protocol family 10
Jul 22 15:45:42 hh-desktop kernel: [   63.991636] lo: Disabled Privacy Extensions
Jul 22 15:45:42 hh-desktop kernel: [   70.078059] input: Power Button (FF) as /class/input/input4
Jul 22 15:45:42 hh-desktop kernel: [   70.085940] ACPI: Power Button (FF) [PWRF]
Jul 22 15:45:42 hh-desktop kernel: [   70.131026] input: Power Button (CM) as /class/input/input5
Jul 22 15:45:42 hh-desktop kernel: [   70.138900] ACPI: Power Button (CM) [PWRB]
Jul 22 15:45:42 hh-desktop kernel: [   70.195788] Using specific hotkey driver
Jul 22 15:45:42 hh-desktop kernel: [   70.335485] No dock devices found.
Jul 22 15:45:42 hh-desktop kernel: [   70.618141] pcc_acpi: loading...
Jul 22 15:45:47 hh-desktop dhcdbd: Started up.
Jul 22 15:45:48 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 15:45:48 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 15:45:48 hh-desktop kernel: [   77.922445] ppdev: user-space parallel port driver
Jul 22 15:45:49 hh-desktop kernel: [   78.457079] [drm] Initialized drm 1.1.0 20060810
Jul 22 15:45:49 hh-desktop kernel: [   78.528561] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 15:45:49 hh-desktop kernel: [   78.533295] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul 22 15:45:50 hh-desktop hpiod: 1.7.3 accepting connections at 2208... 
Jul 22 15:45:51 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 22 15:45:51 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 22 15:45:51 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 22 15:45:51 hh-desktop kernel: [   80.651217] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 22 15:45:51 hh-desktop kernel: [   80.651225] apm: overridden by ACPI.
Jul 22 15:45:51 hh-desktop kernel: [   80.975750] Bluetooth: Core ver 2.11
Jul 22 15:45:51 hh-desktop kernel: [   80.975863] NET: Registered protocol family 31
Jul 22 15:45:51 hh-desktop kernel: [   80.975867] Bluetooth: HCI device and connection manager initialized
Jul 22 15:45:51 hh-desktop kernel: [   80.975872] Bluetooth: HCI socket layer initialized
Jul 22 15:45:51 hh-desktop kernel: [   81.047597] Bluetooth: L2CAP ver 2.8
Jul 22 15:45:51 hh-desktop kernel: [   81.047618] Bluetooth: L2CAP socket layer initialized
Jul 22 15:45:52 hh-desktop kernel: [   81.239854] Bluetooth: RFCOMM socket layer initialized
Jul 22 15:45:52 hh-desktop kernel: [   81.239879] Bluetooth: RFCOMM TTY layer initialized
Jul 22 15:45:52 hh-desktop kernel: [   81.239882] Bluetooth: RFCOMM ver 1.8
Jul 22 15:46:01 hh-desktop gconfd (hh-5468): starting (version 2.18.0.1), pid 5468 user 'hh'
Jul 22 15:46:01 hh-desktop gconfd (hh-5468): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 15:46:01 hh-desktop gconfd (hh-5468): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 15:46:01 hh-desktop gconfd (hh-5468): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 15:46:01 hh-desktop gconfd (hh-5468): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 15:46:01 hh-desktop gconfd (hh-5468): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 15:46:10 hh-desktop gconfd (hh-5468): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 0
Jul 22 15:47:50 hh-desktop kernel: [  199.917386] ACPI: Critical trip point
Jul 22 15:47:51 hh-desktop gconfd (hh-5468): Received signal 15, shutting down cleanly
Jul 22 15:47:58 hh-desktop exiting on signal 15
Jul 22 16:36:56 hh-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul 22 16:36:57 hh-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic
Jul 22 16:36:57 hh-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Jul 22 16:36:57 hh-desktop kernel: Symbols match kernel version 2.6.20.
Jul 22 16:36:57 hh-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] sanitize start
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] sanitize end
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fbf0000 end: 000000003fcf0000 type: 1
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcf0000 size: 000000000000f000 end: 000000003fcff000 type: 3
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcff000 size: 0000000000001000 end: 000000003fd00000 type: 4
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fd00000 size: 0000000000180000 end: 000000003fe80000 type: 1
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fe80000 size: 0000000000180000 end: 0000000040000000 type: 2
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fcf0000 (usable)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcf0000 - 000000003fcff000 (ACPI data)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcff000 - 000000003fd00000 (ACPI NVS)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fd00000 - 000000003fe80000 (usable)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fe80000 - 0000000040000000 (reserved)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] 126MB HIGHMEM available.
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] 896MB LOWMEM available.
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] found SMP MP-table at 000f6690
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]   HighMem    229376 ->   261760
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul 22 16:36:57 hh-desktop kernel: [    0.000000]     0:        0 ->   261760
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] DMI present.
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] Processor #0 15:2 APIC version 20
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf800000)
Jul 22 16:36:57 hh-desktop kernel: [    0.000000] Detected 1993.691 MHz processor.
Jul 22 16:36:57 hh-desktop kernel: [   12.197821] Built 1 zonelists.  Total pages: 259715
Jul 22 16:36:57 hh-desktop kernel: [   12.197827] Kernel command line: root=UUID=cec7c039-003b-47b3-93fd-9645c20ab27d ro quiet splash
Jul 22 16:36:57 hh-desktop kernel: [   12.198048] Enabling fast FPU save and restore... done.
Jul 22 16:36:57 hh-desktop kernel: [   12.198053] Enabling unmasked SIMD FPU exception support... done.
Jul 22 16:36:57 hh-desktop kernel: [   12.198069] Initializing CPU#0
Jul 22 16:36:57 hh-desktop kernel: [   12.198167] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jul 22 16:36:57 hh-desktop kernel: [   12.199940] Console: colour VGA+ 80x25
Jul 22 16:36:57 hh-desktop kernel: [   12.200857] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 22 16:36:57 hh-desktop kernel: [   12.202249] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 22 16:36:57 hh-desktop kernel: [   12.238336] Memory: 1026548k/1047040k available (1992k kernel code, 19696k reserved, 893k data, 328k init, 129472k highmem)
Jul 22 16:36:57 hh-desktop kernel: [   12.238350] virtual kernel memory layout:
Jul 22 16:36:57 hh-desktop kernel: [   12.238352]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jul 22 16:36:57 hh-desktop kernel: [   12.238353]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 22 16:36:57 hh-desktop kernel: [   12.238355]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jul 22 16:36:57 hh-desktop kernel: [   12.238356]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jul 22 16:36:57 hh-desktop kernel: [   12.238357]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Jul 22 16:36:57 hh-desktop kernel: [   12.238359]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Jul 22 16:36:57 hh-desktop kernel: [   12.238360]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Jul 22 16:36:57 hh-desktop kernel: [   12.238364] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul 22 16:36:57 hh-desktop kernel: [   12.318026] Calibrating delay using timer specific routine.. 3990.95 BogoMIPS (lpj=7981900)
Jul 22 16:36:57 hh-desktop kernel: [   12.318098] Security Framework v1.0.0 initialized
Jul 22 16:36:57 hh-desktop kernel: [   12.318112] SELinux:  Disabled at boot.
Jul 22 16:36:57 hh-desktop kernel: [   12.318139] Mount-cache hash table entries: 512
Jul 22 16:36:57 hh-desktop kernel: [   12.318415] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jul 22 16:36:57 hh-desktop kernel: [   12.318420] CPU: L2 cache: 128K
Jul 22 16:36:57 hh-desktop kernel: [   12.318423] CPU: Hyper-Threading is disabled
Jul 22 16:36:57 hh-desktop kernel: [   12.318445] Compat vDSO mapped to ffffe000.
Jul 22 16:36:57 hh-desktop kernel: [   12.318451] Remapping vsyscall page to ffffe000
Jul 22 16:36:57 hh-desktop kernel: [   12.318470] Checking 'hlt' instruction... OK.
Jul 22 16:36:57 hh-desktop kernel: [   12.334162] SMP alternatives: switching to UP code
Jul 22 16:36:57 hh-desktop kernel: [   12.334565] Freeing SMP alternatives: 11k freed
Jul 22 16:36:57 hh-desktop kernel: [   12.334900] Early unpacking initramfs... done
Jul 22 16:36:57 hh-desktop kernel: [   12.764424] ACPI: Core revision 20060707
Jul 22 16:36:57 hh-desktop kernel: [   12.765617] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jul 22 16:36:57 hh-desktop kernel: [   12.769066] CPU0: Intel(R) Celeron(R) CPU 2.00GHz stepping 07
Jul 22 16:36:57 hh-desktop kernel: [   12.769124] Total of 1 processors activated (3990.95 BogoMIPS).
Jul 22 16:36:57 hh-desktop kernel: [   12.769269] ENABLING IO-APIC IRQs
Jul 22 16:36:57 hh-desktop kernel: [   12.769510] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jul 22 16:36:57 hh-desktop kernel: [   12.913374] Brought up 1 CPUs
Jul 22 16:36:57 hh-desktop kernel: [   12.913771] Booting paravirtualized kernel on bare hardware
Jul 22 16:36:57 hh-desktop kernel: [   12.913933] Time: 21:36:03  Date: 06/22/107
Jul 22 16:36:57 hh-desktop kernel: [   12.913985] NET: Registered protocol family 16
Jul 22 16:36:57 hh-desktop kernel: [   12.914192] EISA bus registered
Jul 22 16:36:57 hh-desktop kernel: [   12.914206] ACPI: bus type pci registered
Jul 22 16:36:57 hh-desktop kernel: [   12.916144] PCI: PCI BIOS revision 2.10 entry at 0xfd99a, last bus=2
Jul 22 16:36:57 hh-desktop kernel: [   12.916147] PCI: Using configuration type 1
Jul 22 16:36:57 hh-desktop kernel: [   12.916149] Setting up standard PCI resources
Jul 22 16:36:57 hh-desktop kernel: [   12.946815] ACPI: Interpreter enabled
Jul 22 16:36:57 hh-desktop kernel: [   12.946824] ACPI: Using IOAPIC for interrupt routing
Jul 22 16:36:57 hh-desktop kernel: [   12.947739] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 22 16:36:57 hh-desktop kernel: [   12.949809] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jul 22 16:36:57 hh-desktop kernel: [   12.949811] * this clock source is slow. If you are sure your timer does not have
Jul 22 16:36:57 hh-desktop kernel: [   12.949813] * this bug, please use "acpi_pm_good" to disable the workaround
Jul 22 16:36:57 hh-desktop kernel: [   12.949868] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Jul 22 16:36:57 hh-desktop kernel: [   12.949873] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
Jul 22 16:36:57 hh-desktop kernel: [   12.950346] PCI: Transparent bridge - 0000:00:1e.0
Jul 22 16:36:57 hh-desktop kernel: [   12.957139] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 16:36:57 hh-desktop kernel: [   12.957664] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 16:36:57 hh-desktop kernel: [   12.958109] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
Jul 22 16:36:57 hh-desktop kernel: [   12.958562] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jul 22 16:36:57 hh-desktop kernel: [   12.959025] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 16:36:57 hh-desktop kernel: [   12.959478] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 16:36:57 hh-desktop kernel: [   12.959926] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 16:36:57 hh-desktop kernel: [   12.960389] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 16:36:57 hh-desktop kernel: [   12.964540] ACPI: Power Resource [FN01] (on)
Jul 22 16:36:57 hh-desktop kernel: [   12.964836] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 22 16:36:57 hh-desktop kernel: [   12.964869] pnp: PnP ACPI init
Jul 22 16:36:57 hh-desktop kernel: [   12.998131] pnp: PnP ACPI: found 13 devices
Jul 22 16:36:57 hh-desktop kernel: [   12.998141] PnPBIOS: Disabled by ACPI PNP
Jul 22 16:36:57 hh-desktop kernel: [   12.998282] PCI: Using ACPI for IRQ routing
Jul 22 16:36:57 hh-desktop kernel: [   12.998288] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 22 16:36:57 hh-desktop kernel: [   13.003159] NET: Registered protocol family 8
Jul 22 16:36:57 hh-desktop kernel: [   13.003163] NET: Registered protocol family 20
Jul 22 16:36:57 hh-desktop kernel: [   13.004644] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
Jul 22 16:36:57 hh-desktop kernel: [   13.004664] PCI: Bridge: 0000:00:1e.0
Jul 22 16:36:57 hh-desktop kernel: [   13.004668]   IO window: 2000-2fff
Jul 22 16:36:57 hh-desktop kernel: [   13.004675]   MEM window: e8100000-e81fffff
Jul 22 16:36:57 hh-desktop kernel: [   13.004680]   PREFETCH window: disabled.
Jul 22 16:36:57 hh-desktop kernel: [   13.004745] NET: Registered protocol family 2
Jul 22 16:36:57 hh-desktop kernel: [   13.037266] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 22 16:36:57 hh-desktop kernel: [   13.037618] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 22 16:36:57 hh-desktop kernel: [   13.039318] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 22 16:36:57 hh-desktop kernel: [   13.040217] TCP: Hash tables configured (established 131072 bind 65536)
Jul 22 16:36:57 hh-desktop kernel: [   13.040225] TCP reno registered
Jul 22 16:36:57 hh-desktop kernel: [   13.049360] checking if image is initramfs... it is
Jul 22 16:36:57 hh-desktop kernel: [   13.868552] Freeing initrd memory: 7012k freed
Jul 22 16:36:57 hh-desktop kernel: [   13.868950] Simple Boot Flag at 0x3b set to 0x1
Jul 22 16:36:57 hh-desktop kernel: [   13.869601] audit: initializing netlink socket (disabled)
Jul 22 16:36:57 hh-desktop kernel: [   13.869622] audit(1185140163.760:1): initialized
Jul 22 16:36:57 hh-desktop kernel: [   13.869778] highmem bounce pool size: 64 pages
Jul 22 16:36:57 hh-desktop kernel: [   13.869933] VFS: Disk quotas dquot_6.5.1
Jul 22 16:36:57 hh-desktop kernel: [   13.869966] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 22 16:36:57 hh-desktop kernel: [   13.870069] io scheduler noop registered
Jul 22 16:36:57 hh-desktop kernel: [   13.870075] io scheduler anticipatory registered
Jul 22 16:36:57 hh-desktop kernel: [   13.870078] io scheduler deadline registered
Jul 22 16:36:57 hh-desktop kernel: [   13.870097] io scheduler cfq registered (default)
Jul 22 16:36:57 hh-desktop kernel: [   13.870671] isapnp: Scanning for PnP cards...
Jul 22 16:36:57 hh-desktop kernel: [   14.224570] isapnp: No Plug & Play device found
Jul 22 16:36:57 hh-desktop kernel: [   14.356968] Real Time Clock Driver v1.12ac
Jul 22 16:36:57 hh-desktop kernel: [   14.357111] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 22 16:36:57 hh-desktop kernel: [   14.357321] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 16:36:57 hh-desktop kernel: [   14.359547] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 16:36:57 hh-desktop kernel: [   14.360338] mice: PS/2 mouse device common for all mice
Jul 22 16:36:57 hh-desktop kernel: [   14.362210] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 22 16:36:57 hh-desktop kernel: [   14.362586] input: Macintosh mouse button emulation as /class/input/input0
Jul 22 16:36:57 hh-desktop kernel: [   14.362705] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 22 16:36:57 hh-desktop kernel: [   14.362713] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 22 16:36:57 hh-desktop kernel: [   14.363200] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Jul 22 16:36:57 hh-desktop kernel: [   14.366454] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 22 16:36:57 hh-desktop kernel: [   14.366464] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 22 16:36:57 hh-desktop kernel: [   14.366829] EISA: Probing bus 0 at eisa.0
Jul 22 16:36:57 hh-desktop kernel: [   14.366841] Cannot allocate resource for EISA slot 1
Jul 22 16:36:57 hh-desktop kernel: [   14.366844] Cannot allocate resource for EISA slot 2
Jul 22 16:36:57 hh-desktop kernel: [   14.366872] EISA: Detected 0 cards.
Jul 22 16:36:57 hh-desktop kernel: [   14.396984] TCP cubic registered
Jul 22 16:36:57 hh-desktop kernel: [   14.397001] NET: Registered protocol family 1
Jul 22 16:36:57 hh-desktop kernel: [   14.397047] Using IPI No-Shortcut mode
Jul 22 16:36:57 hh-desktop kernel: [   14.397236] ACPI: (supports S0 S1 S3 S4 S5)
Jul 22 16:36:57 hh-desktop kernel: [   14.397310]   Magic number: 15:468:652
Jul 22 16:36:57 hh-desktop kernel: [   14.398036] Freeing unused kernel memory: 328k freed
Jul 22 16:36:57 hh-desktop kernel: [   14.399469] Time: tsc clocksource has been installed.
Jul 22 16:36:57 hh-desktop kernel: [   14.414460] input: AT Translated Set 2 keyboard as /class/input/input1
Jul 22 16:36:57 hh-desktop kernel: [   16.024599] Capability LSM initialized
Jul 22 16:36:57 hh-desktop kernel: [   16.595740] ACPI: Transitioning device [FAN1] to D0
Jul 22 16:36:57 hh-desktop kernel: [   16.595748] ACPI: Transitioning device [FAN1] to D0
Jul 22 16:36:57 hh-desktop kernel: [   16.595755] ACPI: Fan [FAN1] (off)
Jul 22 16:36:57 hh-desktop kernel: [   16.602966] ACPI: Processor [CPU0] (supports 8 throttling states)
Jul 22 16:36:57 hh-desktop kernel: [   16.611976] ACPI: Thermal Zone [THRM] (-269 C)
Jul 22 16:36:57 hh-desktop kernel: [   26.735530] usbcore: registered new interface driver usbfs
Jul 22 16:36:57 hh-desktop kernel: [   26.735583] usbcore: registered new interface driver hub
Jul 22 16:36:57 hh-desktop kernel: [   26.735648] usbcore: registered new device driver usb
Jul 22 16:36:57 hh-desktop kernel: [   26.737120] USB Universal Host Controller Interface driver v3.0
Jul 22 16:36:57 hh-desktop kernel: [   26.737211] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 16:36:57 hh-desktop kernel: [   26.737234] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 22 16:36:57 hh-desktop kernel: [   26.737435] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jul 22 16:36:57 hh-desktop kernel: [   26.737475] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
Jul 22 16:36:57 hh-desktop kernel: [   26.737683] usb usb1: configuration #1 chosen from 1 choice
Jul 22 16:36:57 hh-desktop kernel: [   26.737734] hub 1-0:1.0: USB hub found
Jul 22 16:36:57 hh-desktop kernel: [   26.737753] hub 1-0:1.0: 2 ports detected
Jul 22 16:36:57 hh-desktop kernel: [   26.843492] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Jul 22 16:36:57 hh-desktop kernel: [   26.843516] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 22 16:36:57 hh-desktop kernel: [   26.843570] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jul 22 16:36:57 hh-desktop kernel: [   26.843606] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
Jul 22 16:36:57 hh-desktop kernel: [   26.843787] usb usb2: configuration #1 chosen from 1 choice
Jul 22 16:36:57 hh-desktop kernel: [   26.843840] hub 2-0:1.0: USB hub found
Jul 22 16:36:57 hh-desktop kernel: [   26.843859] hub 2-0:1.0: 2 ports detected
Jul 22 16:36:57 hh-desktop kernel: [   26.947378] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 22 16:36:57 hh-desktop kernel: [   26.947401] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 22 16:36:57 hh-desktop kernel: [   26.947452] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jul 22 16:36:57 hh-desktop kernel: [   26.947494] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Jul 22 16:36:57 hh-desktop kernel: [   26.947670] usb usb3: configuration #1 chosen from 1 choice
Jul 22 16:36:57 hh-desktop kernel: [   26.947735] hub 3-0:1.0: USB hub found
Jul 22 16:36:57 hh-desktop kernel: [   26.947752] hub 3-0:1.0: 2 ports detected
Jul 22 16:36:57 hh-desktop kernel: [   27.052739] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Jul 22 16:36:57 hh-desktop kernel: [   27.052770] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 22 16:36:57 hh-desktop kernel: [   27.052836] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jul 22 16:36:57 hh-desktop kernel: [   27.052904] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe8080000
Jul 22 16:36:57 hh-desktop kernel: [   27.056785] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 22 16:36:57 hh-desktop kernel: [   27.056937] usb usb4: configuration #1 chosen from 1 choice
Jul 22 16:36:57 hh-desktop kernel: [   27.056994] hub 4-0:1.0: USB hub found
Jul 22 16:36:57 hh-desktop kernel: [   27.057011] hub 4-0:1.0: 6 ports detected
Jul 22 16:36:57 hh-desktop kernel: [   27.077993] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jul 22 16:36:57 hh-desktop kernel: [   27.082985] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jul 22 16:36:57 hh-desktop kernel: [   27.163516] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Jul 22 16:36:57 hh-desktop kernel: [   27.163523] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
Jul 22 16:36:57 hh-desktop kernel: [   27.166322] 8139too Fast Ethernet driver 0.9.28
Jul 22 16:36:57 hh-desktop kernel: [   27.166406] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 20
Jul 22 16:36:57 hh-desktop kernel: [   27.166790] eth0: RealTek RTL8139 at 0xf8848000, 00:40:2b:41:30:ec, IRQ 20
Jul 22 16:36:57 hh-desktop kernel: [   27.252217] SCSI subsystem initialized
Jul 22 16:36:57 hh-desktop kernel: [   27.264174] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Jul 22 16:36:57 hh-desktop kernel: [   27.264183] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Jul 22 16:36:57 hh-desktop kernel: [   27.264312] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
Jul 22 16:36:57 hh-desktop kernel: [   27.264383] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
Jul 22 16:36:57 hh-desktop kernel: [   27.264414] scsi0 : ata_piix
Jul 22 16:36:57 hh-desktop kernel: [   27.431699] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 16:36:57 hh-desktop kernel: [   27.431706] ata1.00: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
Jul 22 16:36:57 hh-desktop kernel: [   27.431710] ata1.00: 78165360 sectors, multi 16: LBA 
Jul 22 16:36:57 hh-desktop kernel: [   27.443679] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 16:36:57 hh-desktop kernel: [   27.443688] ata1.00: configured for UDMA/100
Jul 22 16:36:57 hh-desktop kernel: [   27.443710] scsi1 : ata_piix
Jul 22 16:36:57 hh-desktop kernel: [   27.475200] Floppy drive(s): fd0 is 1.44M
Jul 22 16:36:57 hh-desktop kernel: [   27.502325] FDC 0 is a post-1991 82077
Jul 22 16:36:57 hh-desktop kernel: [   27.766387] ata2.00: ATAPI, max MWDMA2
Jul 22 16:36:57 hh-desktop kernel: [   27.837997] usb 1-1: new full speed USB device using uhci_hcd and address 3
Jul 22 16:36:57 hh-desktop kernel: [   27.930409] ata2.00: configured for MWDMA2
Jul 22 16:36:57 hh-desktop kernel: [   27.933888] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
Jul 22 16:36:57 hh-desktop kernel: [   27.935687] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-240B  R400 PQ: 0 ANSI: 5
Jul 22 16:36:57 hh-desktop kernel: [   28.029805] usb 1-1: configuration #1 chosen from 1 choice
Jul 22 16:36:57 hh-desktop kernel: [   28.486155] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 16:36:57 hh-desktop kernel: [   28.489204] sda: Write Protect is off
Jul 22 16:36:57 hh-desktop kernel: [   28.493139] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 16:36:57 hh-desktop kernel: [   28.497162] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 16:36:57 hh-desktop kernel: [   28.498119] sda: Write Protect is off
Jul 22 16:36:57 hh-desktop kernel: [   28.502111] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 16:36:57 hh-desktop kernel: [   28.502118]  sda: sda1 sda2 < sda5 >
Jul 22 16:36:57 hh-desktop kernel: [   28.557595] sd 0:0:0:0: Attached scsi disk sda
Jul 22 16:36:57 hh-desktop kernel: [   28.564484] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 22 16:36:57 hh-desktop kernel: [   28.564517] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Jul 22 16:36:57 hh-desktop kernel: [   28.602384] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jul 22 16:36:57 hh-desktop kernel: [   28.602392] Uniform CD-ROM driver Revision: 3.20
Jul 22 16:36:57 hh-desktop kernel: [   28.835820] usbcore: registered new interface driver hiddev
Jul 22 16:36:57 hh-desktop kernel: [   28.857689] input: Logitech USB Gaming Mouse as /class/input/input2
Jul 22 16:36:57 hh-desktop kernel: [   28.857735] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 16:36:57 hh-desktop kernel: [   28.864522] hiddev96: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 16:36:57 hh-desktop kernel: [   28.864549] usbcore: registered new interface driver usbhid
Jul 22 16:36:57 hh-desktop kernel: [   28.864553] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul 22 16:36:57 hh-desktop kernel: [   30.502943] Attempting manual resume
Jul 22 16:36:57 hh-desktop kernel: [   31.129787] kjournald starting.  Commit interval 5 seconds
Jul 22 16:36:57 hh-desktop kernel: [   31.129813] EXT3-fs: mounted filesystem with ordered data mode.
Jul 22 16:36:57 hh-desktop kernel: [   53.638736] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 22 16:36:57 hh-desktop kernel: [   55.121622] NET: Registered protocol family 17
Jul 22 16:36:57 hh-desktop kernel: [   56.392550] iTCO_vendor_support: vendor-support=0
Jul 22 16:36:57 hh-desktop kernel: [   56.394285] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Jul 22 16:36:57 hh-desktop kernel: [   56.394506] iTCO_wdt: No card detected
Jul 22 16:36:57 hh-desktop kernel: [   56.448271] Linux agpgart interface v0.102 (c) Dave Jones
Jul 22 16:36:57 hh-desktop kernel: [   56.467159] agpgart: Detected an Intel 845G Chipset.
Jul 22 16:36:57 hh-desktop kernel: [   56.467288] agpgart: Detected 892K stolen memory.
Jul 22 16:36:57 hh-desktop kernel: [   56.485483] agpgart: AGP aperture is 128M @ 0xf0000000
Jul 22 16:36:57 hh-desktop kernel: [   56.808117] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 22 16:36:57 hh-desktop kernel: [   56.848708] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Jul 22 16:36:57 hh-desktop kernel: [   57.074318] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 22 16:36:57 hh-desktop kernel: [   57.176270] usbcore: registered new interface driver xpad
Jul 22 16:36:57 hh-desktop kernel: [   57.176278] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
Jul 22 16:36:57 hh-desktop kernel: [   57.383057] input: PC Speaker as /class/input/input3
Jul 22 16:36:57 hh-desktop kernel: [   57.515390] parport: PnPBIOS parport detected.
Jul 22 16:36:57 hh-desktop kernel: [   57.515448] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul 22 16:36:57 hh-desktop kernel: [   57.852082] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
Jul 22 16:36:57 hh-desktop kernel: [   58.166706] intel8x0_measure_ac97_clock: measured 55049 usecs
Jul 22 16:36:57 hh-desktop kernel: [   58.166712] intel8x0: clocking to 48000
Jul 22 16:36:57 hh-desktop kernel: [   58.443465] fuse init (API version 7.8)
Jul 22 16:36:57 hh-desktop kernel: [   58.487603] lp0: using parport0 (interrupt-driven).
Jul 22 16:36:57 hh-desktop kernel: [   58.552540] Adding 1646620k swap on /dev/disk/by-uuid/b35569b7-a093-4d4e-b5f8-cbe0e1cf4b6c.  Priority:-1 extents:1 across:1646620k
Jul 22 16:36:57 hh-desktop kernel: [   58.738072] EXT3 FS on sda1, internal journal
Jul 22 16:36:57 hh-desktop kernel: [   59.046338] NET: Registered protocol family 10
Jul 22 16:36:57 hh-desktop kernel: [   59.046512] lo: Disabled Privacy Extensions
Jul 22 16:36:57 hh-desktop kernel: [   65.059607] input: Power Button (FF) as /class/input/input4
Jul 22 16:36:57 hh-desktop kernel: [   65.067501] ACPI: Power Button (FF) [PWRF]
Jul 22 16:36:57 hh-desktop kernel: [   65.111426] input: Power Button (CM) as /class/input/input5
Jul 22 16:36:57 hh-desktop kernel: [   65.119199] ACPI: Power Button (CM) [PWRB]
Jul 22 16:36:57 hh-desktop kernel: [   65.176763] Using specific hotkey driver
Jul 22 16:36:57 hh-desktop kernel: [   65.315816] No dock devices found.
Jul 22 16:36:57 hh-desktop kernel: [   65.594580] pcc_acpi: loading...
Jul 22 16:37:01 hh-desktop dhcdbd: Started up.
Jul 22 16:37:01 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 16:37:01 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 16:37:02 hh-desktop kernel: [   71.787884] ppdev: user-space parallel port driver
Jul 22 16:37:02 hh-desktop kernel: [   72.309177] [drm] Initialized drm 1.1.0 20060810
Jul 22 16:37:03 hh-desktop kernel: [   72.372108] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 16:37:03 hh-desktop kernel: [   72.411561] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul 22 16:37:04 hh-desktop hpiod: 1.7.3 accepting connections at 2208... 
Jul 22 16:37:05 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 22 16:37:05 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 22 16:37:05 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 22 16:37:05 hh-desktop kernel: [   74.513812] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 22 16:37:05 hh-desktop kernel: [   74.513820] apm: overridden by ACPI.
Jul 22 16:37:05 hh-desktop kernel: [   74.838338] Bluetooth: Core ver 2.11
Jul 22 16:37:05 hh-desktop kernel: [   74.838461] NET: Registered protocol family 31
Jul 22 16:37:05 hh-desktop kernel: [   74.838465] Bluetooth: HCI device and connection manager initialized
Jul 22 16:37:05 hh-desktop kernel: [   74.838470] Bluetooth: HCI socket layer initialized
Jul 22 16:37:05 hh-desktop kernel: [   74.983488] Bluetooth: L2CAP ver 2.8
Jul 22 16:37:05 hh-desktop kernel: [   74.983496] Bluetooth: L2CAP socket layer initialized
Jul 22 16:37:05 hh-desktop kernel: [   75.142778] Bluetooth: RFCOMM socket layer initialized
Jul 22 16:37:05 hh-desktop kernel: [   75.142801] Bluetooth: RFCOMM TTY layer initialized
Jul 22 16:37:05 hh-desktop kernel: [   75.142804] Bluetooth: RFCOMM ver 1.8
Jul 22 16:41:40 hh-desktop gconfd (hh-5461): starting (version 2.18.0.1), pid 5461 user 'hh'
Jul 22 16:41:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:41:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 16:41:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:41:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:41:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:41:49 hh-desktop gconfd (hh-5461): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 0
Jul 22 16:47:40 hh-desktop gconfd (hh-5461): SIGHUP received, reloading all databases
Jul 22 16:47:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:47:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 16:47:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:47:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:47:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:48:45 hh-desktop gconfd (root-6079): starting (version 2.18.0.1), pid 6079 user 'root'
Jul 22 16:48:45 hh-desktop gconfd (root-6079): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:48:45 hh-desktop gconfd (root-6079): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 22 16:48:45 hh-desktop gconfd (root-6079): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:48:45 hh-desktop gconfd (root-6079): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:48:45 hh-desktop gconfd (root-6079): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:49:00 hh-desktop gconfd (root-6079): Exiting
Jul 22 16:49:10 hh-desktop gconfd (hh-5461): SIGHUP received, reloading all databases
Jul 22 16:49:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:49:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 16:49:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:49:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:49:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:49:28 hh-desktop gconfd (root-6324): starting (version 2.18.0.1), pid 6324 user 'root'
Jul 22 16:49:28 hh-desktop gconfd (root-6324): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:49:28 hh-desktop gconfd (root-6324): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 22 16:49:28 hh-desktop gconfd (root-6324): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:49:28 hh-desktop gconfd (root-6324): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:49:28 hh-desktop gconfd (root-6324): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:49:58 hh-desktop gconfd (root-6324): GConf server is not in use, shutting down.
Jul 22 16:49:58 hh-desktop gconfd (root-6324): Exiting
Jul 22 16:50:10 hh-desktop gconfd (hh-5461): SIGHUP received, reloading all databases
Jul 22 16:50:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:50:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 16:50:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:50:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:50:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:50:40 hh-desktop gconfd (hh-5461): SIGHUP received, reloading all databases
Jul 22 16:50:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:50:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 16:50:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:50:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:50:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:50:45 hh-desktop gconfd (root-6924): starting (version 2.18.0.1), pid 6924 user 'root'
Jul 22 16:50:45 hh-desktop gconfd (root-6924): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:50:45 hh-desktop gconfd (root-6924): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 22 16:50:45 hh-desktop gconfd (root-6924): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:50:45 hh-desktop gconfd (root-6924): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:50:45 hh-desktop gconfd (root-6924): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:51:10 hh-desktop gconfd (hh-5461): SIGHUP received, reloading all databases
Jul 22 16:51:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:51:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 16:51:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:51:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:51:10 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:51:29 hh-desktop gconfd (root-6924): Exiting
Jul 22 16:51:40 hh-desktop gconfd (hh-5461): SIGHUP received, reloading all databases
Jul 22 16:51:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:51:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 16:51:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:51:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:51:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:52:05 hh-desktop gconfd (hh-5461): Exiting
Jul 22 16:52:16 hh-desktop exiting on signal 15
Jul 22 16:53:30 hh-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul 22 16:53:30 hh-desktop kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jul 22 16:53:31 hh-desktop kernel: Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.
Jul 22 16:53:31 hh-desktop kernel: Symbols match kernel version 2.6.20.
Jul 22 16:53:31 hh-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] sanitize start
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] sanitize end
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fbf0000 end: 000000003fcf0000 type: 1
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcf0000 size: 000000000000f000 end: 000000003fcff000 type: 3
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcff000 size: 0000000000001000 end: 000000003fd00000 type: 4
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fd00000 size: 0000000000180000 end: 000000003fe80000 type: 1
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fe80000 size: 0000000000180000 end: 0000000040000000 type: 2
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fcf0000 (usable)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcf0000 - 000000003fcff000 (ACPI data)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcff000 - 000000003fd00000 (ACPI NVS)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fd00000 - 000000003fe80000 (usable)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fe80000 - 0000000040000000 (reserved)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] 126MB HIGHMEM available.
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] 896MB LOWMEM available.
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] found SMP MP-table at 000f6690
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]   HighMem    229376 ->   261760
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul 22 16:53:31 hh-desktop kernel: [    0.000000]     0:        0 ->   261760
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] DMI present.
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] Processor #0 15:2 APIC version 20
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf800000)
Jul 22 16:53:31 hh-desktop kernel: [    0.000000] Detected 1993.615 MHz processor.
Jul 22 16:53:31 hh-desktop kernel: [    8.518764] Built 1 zonelists.  Total pages: 259715
Jul 22 16:53:31 hh-desktop kernel: [    8.518771] Kernel command line: root=UUID=cec7c039-003b-47b3-93fd-9645c20ab27d ro quiet splash
Jul 22 16:53:31 hh-desktop kernel: [    8.518991] Enabling fast FPU save and restore... done.
Jul 22 16:53:31 hh-desktop kernel: [    8.518996] Enabling unmasked SIMD FPU exception support... done.
Jul 22 16:53:31 hh-desktop kernel: [    8.519011] Initializing CPU#0
Jul 22 16:53:31 hh-desktop kernel: [    8.519102] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jul 22 16:53:31 hh-desktop kernel: [    8.520844] Console: colour VGA+ 80x25
Jul 22 16:53:31 hh-desktop kernel: [    8.521773] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 22 16:53:31 hh-desktop kernel: [    8.523245] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 22 16:53:31 hh-desktop kernel: [    8.559490] Memory: 1026796k/1047040k available (1992k kernel code, 19476k reserved, 900k data, 328k init, 129472k highmem)
Jul 22 16:53:31 hh-desktop kernel: [    8.559507] virtual kernel memory layout:
Jul 22 16:53:31 hh-desktop kernel: [    8.559508]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jul 22 16:53:31 hh-desktop kernel: [    8.559509]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 22 16:53:31 hh-desktop kernel: [    8.559511]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jul 22 16:53:31 hh-desktop kernel: [    8.559512]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jul 22 16:53:31 hh-desktop kernel: [    8.559514]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Jul 22 16:53:31 hh-desktop kernel: [    8.559515]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
Jul 22 16:53:31 hh-desktop kernel: [    8.559516]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
Jul 22 16:53:31 hh-desktop kernel: [    8.559520] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul 22 16:53:31 hh-desktop kernel: [    8.638960] Calibrating delay using timer specific routine.. 3991.02 BogoMIPS (lpj=7982055)
Jul 22 16:53:31 hh-desktop kernel: [    8.639033] Security Framework v1.0.0 initialized
Jul 22 16:53:31 hh-desktop kernel: [    8.639048] SELinux:  Disabled at boot.
Jul 22 16:53:31 hh-desktop kernel: [    8.639076] Mount-cache hash table entries: 512
Jul 22 16:53:31 hh-desktop kernel: [    8.639364] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jul 22 16:53:31 hh-desktop kernel: [    8.639367] CPU: L2 cache: 128K
Jul 22 16:53:31 hh-desktop kernel: [    8.639371] CPU: Hyper-Threading is disabled
Jul 22 16:53:31 hh-desktop kernel: [    8.639391] Compat vDSO mapped to ffffe000.
Jul 22 16:53:31 hh-desktop kernel: [    8.639396] Remapping vsyscall page to ffffe000
Jul 22 16:53:31 hh-desktop kernel: [    8.639416] Checking 'hlt' instruction... OK.
Jul 22 16:53:31 hh-desktop kernel: [    8.655090] SMP alternatives: switching to UP code
Jul 22 16:53:31 hh-desktop kernel: [    8.655493] Freeing SMP alternatives: 11k freed
Jul 22 16:53:31 hh-desktop kernel: [    8.655828] Early unpacking initramfs... done
Jul 22 16:53:31 hh-desktop kernel: [    9.075795] ACPI: Core revision 20060707
Jul 22 16:53:31 hh-desktop kernel: [    9.076955] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jul 22 16:53:31 hh-desktop kernel: [    9.082176] CPU0: Intel(R) Celeron(R) CPU 2.00GHz stepping 07
Jul 22 16:53:31 hh-desktop kernel: [    9.082235] Total of 1 processors activated (3991.02 BogoMIPS).
Jul 22 16:53:31 hh-desktop kernel: [    9.082382] ENABLING IO-APIC IRQs
Jul 22 16:53:31 hh-desktop kernel: [    9.082592] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jul 22 16:53:31 hh-desktop kernel: [    9.226323] Brought up 1 CPUs
Jul 22 16:53:31 hh-desktop kernel: [    9.226722] Booting paravirtualized kernel on bare hardware
Jul 22 16:53:31 hh-desktop kernel: [    9.226887] Time: 21:52:36  Date: 06/22/107
Jul 22 16:53:31 hh-desktop kernel: [    9.226942] NET: Registered protocol family 16
Jul 22 16:53:31 hh-desktop kernel: [    9.227164] EISA bus registered
Jul 22 16:53:31 hh-desktop kernel: [    9.227176] ACPI: bus type pci registered
Jul 22 16:53:31 hh-desktop kernel: [    9.229082] PCI: PCI BIOS revision 2.10 entry at 0xfd99a, last bus=2
Jul 22 16:53:31 hh-desktop kernel: [    9.229085] PCI: Using configuration type 1
Jul 22 16:53:31 hh-desktop kernel: [    9.229088] Setting up standard PCI resources
Jul 22 16:53:31 hh-desktop kernel: [    9.260276] ACPI: Interpreter enabled
Jul 22 16:53:31 hh-desktop kernel: [    9.260285] ACPI: Using IOAPIC for interrupt routing
Jul 22 16:53:31 hh-desktop kernel: [    9.261197] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 22 16:53:31 hh-desktop kernel: [    9.263659] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jul 22 16:53:31 hh-desktop kernel: [    9.263661] * this clock source is slow. If you are sure your timer does not have
Jul 22 16:53:31 hh-desktop kernel: [    9.263663] * this bug, please use "acpi_pm_good" to disable the workaround
Jul 22 16:53:31 hh-desktop kernel: [    9.263718] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Jul 22 16:53:31 hh-desktop kernel: [    9.263723] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
Jul 22 16:53:31 hh-desktop kernel: [    9.264193] PCI: Transparent bridge - 0000:00:1e.0
Jul 22 16:53:31 hh-desktop kernel: [    9.271156] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 16:53:31 hh-desktop kernel: [    9.271625] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 16:53:31 hh-desktop kernel: [    9.272113] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
Jul 22 16:53:31 hh-desktop kernel: [    9.272604] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jul 22 16:53:31 hh-desktop kernel: [    9.273101] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 16:53:31 hh-desktop kernel: [    9.273593] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 16:53:31 hh-desktop kernel: [    9.274077] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 16:53:31 hh-desktop kernel: [    9.274609] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 16:53:31 hh-desktop kernel: [    9.278855] ACPI: Power Resource [FN01] (on)
Jul 22 16:53:31 hh-desktop kernel: [    9.279134] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 22 16:53:31 hh-desktop kernel: [    9.279161] pnp: PnP ACPI init
Jul 22 16:53:31 hh-desktop kernel: [    9.318006] pnp: PnP ACPI: found 13 devices
Jul 22 16:53:31 hh-desktop kernel: [    9.318017] PnPBIOS: Disabled by ACPI PNP
Jul 22 16:53:31 hh-desktop kernel: [    9.318160] PCI: Using ACPI for IRQ routing
Jul 22 16:53:31 hh-desktop kernel: [    9.318167] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 22 16:53:31 hh-desktop kernel: [    9.323049] NET: Registered protocol family 8
Jul 22 16:53:31 hh-desktop kernel: [    9.323052] NET: Registered protocol family 20
Jul 22 16:53:31 hh-desktop kernel: [    9.324551] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
Jul 22 16:53:31 hh-desktop kernel: [    9.324570] PCI: Bridge: 0000:00:1e.0
Jul 22 16:53:31 hh-desktop kernel: [    9.324575]   IO window: 2000-2fff
Jul 22 16:53:31 hh-desktop kernel: [    9.324582]   MEM window: e8100000-e81fffff
Jul 22 16:53:31 hh-desktop kernel: [    9.324588]   PREFETCH window: disabled.
Jul 22 16:53:31 hh-desktop kernel: [    9.324651] NET: Registered protocol family 2
Jul 22 16:53:31 hh-desktop kernel: [    9.362200] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 22 16:53:31 hh-desktop kernel: [    9.362536] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 22 16:53:31 hh-desktop kernel: [    9.364236] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 22 16:53:31 hh-desktop kernel: [    9.365131] TCP: Hash tables configured (established 131072 bind 65536)
Jul 22 16:53:31 hh-desktop kernel: [    9.365138] TCP reno registered
Jul 22 16:53:31 hh-desktop kernel: [    9.374294] checking if image is initramfs... it is
Jul 22 16:53:31 hh-desktop kernel: [   10.164381] Freeing initrd memory: 6787k freed
Jul 22 16:53:31 hh-desktop kernel: [   10.164793] Simple Boot Flag at 0x3b set to 0x1
Jul 22 16:53:31 hh-desktop kernel: [   10.165466] audit: initializing netlink socket (disabled)
Jul 22 16:53:31 hh-desktop kernel: [   10.165488] audit(1185141156.724:1): initialized
Jul 22 16:53:31 hh-desktop kernel: [   10.165644] highmem bounce pool size: 64 pages
Jul 22 16:53:31 hh-desktop kernel: [   10.165805] VFS: Disk quotas dquot_6.5.1
Jul 22 16:53:31 hh-desktop kernel: [   10.165839] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 22 16:53:31 hh-desktop kernel: [   10.165944] io scheduler noop registered
Jul 22 16:53:31 hh-desktop kernel: [   10.165951] io scheduler anticipatory registered
Jul 22 16:53:31 hh-desktop kernel: [   10.165954] io scheduler deadline registered
Jul 22 16:53:31 hh-desktop kernel: [   10.165975] io scheduler cfq registered (default)
Jul 22 16:53:31 hh-desktop kernel: [   10.166567] isapnp: Scanning for PnP cards...
Jul 22 16:53:31 hh-desktop kernel: [   10.520468] isapnp: No Plug & Play device found
Jul 22 16:53:31 hh-desktop kernel: [   10.653517] Real Time Clock Driver v1.12ac
Jul 22 16:53:31 hh-desktop kernel: [   10.653649] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 22 16:53:31 hh-desktop kernel: [   10.653871] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 16:53:31 hh-desktop kernel: [   10.656064] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 16:53:31 hh-desktop kernel: [   10.656938] mice: PS/2 mouse device common for all mice
Jul 22 16:53:31 hh-desktop kernel: [   10.658743] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 22 16:53:31 hh-desktop kernel: [   10.659311] input: Macintosh mouse button emulation as /class/input/input0
Jul 22 16:53:31 hh-desktop kernel: [   10.659422] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 22 16:53:31 hh-desktop kernel: [   10.659429] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 22 16:53:31 hh-desktop kernel: [   10.659882] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Jul 22 16:53:31 hh-desktop kernel: [   10.663032] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 22 16:53:31 hh-desktop kernel: [   10.663043] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 22 16:53:31 hh-desktop kernel: [   10.663434] EISA: Probing bus 0 at eisa.0
Jul 22 16:53:31 hh-desktop kernel: [   10.663445] Cannot allocate resource for EISA slot 1
Jul 22 16:53:31 hh-desktop kernel: [   10.663449] Cannot allocate resource for EISA slot 2
Jul 22 16:53:31 hh-desktop kernel: [   10.663476] EISA: Detected 0 cards.
Jul 22 16:53:31 hh-desktop kernel: [   10.693587] TCP cubic registered
Jul 22 16:53:31 hh-desktop kernel: [   10.693606] NET: Registered protocol family 1
Jul 22 16:53:31 hh-desktop kernel: [   10.693649] Using IPI No-Shortcut mode
Jul 22 16:53:31 hh-desktop kernel: [   10.693830] ACPI: (supports S0 S1 S3 S4 S5)
Jul 22 16:53:31 hh-desktop kernel: [   10.693904]   Magic number: 15:227:905
Jul 22 16:53:31 hh-desktop kernel: [   10.694031]   hash matches device ptyz1
Jul 22 16:53:31 hh-desktop kernel: [   10.694632] Freeing unused kernel memory: 328k freed
Jul 22 16:53:31 hh-desktop kernel: [   10.696430] Time: tsc clocksource has been installed.
Jul 22 16:53:31 hh-desktop kernel: [   10.710863] input: AT Translated Set 2 keyboard as /class/input/input1
Jul 22 16:53:31 hh-desktop kernel: [   12.325703] Capability LSM initialized
Jul 22 16:53:31 hh-desktop kernel: [   13.000490] ACPI: Transitioning device [FAN1] to D0
Jul 22 16:53:31 hh-desktop kernel: [   13.000496] ACPI: Transitioning device [FAN1] to D0
Jul 22 16:53:31 hh-desktop kernel: [   13.000503] ACPI: Fan [FAN1] (off)
Jul 22 16:53:31 hh-desktop kernel: [   13.007533] ACPI: Processor [CPU0] (supports 8 throttling states)
Jul 22 16:53:31 hh-desktop kernel: [   13.016690] ACPI: Thermal Zone [THRM] (-265 C)
Jul 22 16:53:31 hh-desktop kernel: [   23.339534] usbcore: registered new interface driver usbfs
Jul 22 16:53:31 hh-desktop kernel: [   23.339586] usbcore: registered new interface driver hub
Jul 22 16:53:31 hh-desktop kernel: [   23.339664] usbcore: registered new device driver usb
Jul 22 16:53:31 hh-desktop kernel: [   23.341198] USB Universal Host Controller Interface driver v3.0
Jul 22 16:53:31 hh-desktop kernel: [   23.341292] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 16:53:31 hh-desktop kernel: [   23.341315] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 22 16:53:31 hh-desktop kernel: [   23.341519] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jul 22 16:53:31 hh-desktop kernel: [   23.341561] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
Jul 22 16:53:31 hh-desktop kernel: [   23.341774] usb usb1: configuration #1 chosen from 1 choice
Jul 22 16:53:31 hh-desktop kernel: [   23.341841] hub 1-0:1.0: USB hub found
Jul 22 16:53:31 hh-desktop kernel: [   23.341859] hub 1-0:1.0: 2 ports detected
Jul 22 16:53:31 hh-desktop kernel: [   23.448644] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Jul 22 16:53:31 hh-desktop kernel: [   23.448668] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 22 16:53:31 hh-desktop kernel: [   23.448734] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jul 22 16:53:31 hh-desktop kernel: [   23.448771] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
Jul 22 16:53:31 hh-desktop kernel: [   23.448960] usb usb2: configuration #1 chosen from 1 choice
Jul 22 16:53:31 hh-desktop kernel: [   23.449017] hub 2-0:1.0: USB hub found
Jul 22 16:53:31 hh-desktop kernel: [   23.449034] hub 2-0:1.0: 2 ports detected
Jul 22 16:53:31 hh-desktop kernel: [   23.522172] SCSI subsystem initialized
Jul 22 16:53:31 hh-desktop kernel: [   23.551413] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jul 22 16:53:31 hh-desktop kernel: [   23.556479] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 22 16:53:31 hh-desktop kernel: [   23.556503] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 22 16:53:31 hh-desktop kernel: [   23.556555] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jul 22 16:53:31 hh-desktop kernel: [   23.556602] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Jul 22 16:53:31 hh-desktop kernel: [   23.556780] usb usb3: configuration #1 chosen from 1 choice
Jul 22 16:53:31 hh-desktop kernel: [   23.556844] hub 3-0:1.0: USB hub found
Jul 22 16:53:31 hh-desktop kernel: [   23.556861] hub 3-0:1.0: 2 ports detected
Jul 22 16:53:31 hh-desktop kernel: [   23.665381] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Jul 22 16:53:31 hh-desktop kernel: [   23.665412] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 22 16:53:31 hh-desktop kernel: [   23.665483] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jul 22 16:53:31 hh-desktop kernel: [   23.665554] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe8080000
Jul 22 16:53:31 hh-desktop kernel: [   23.669437] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 22 16:53:31 hh-desktop kernel: [   23.669602] usb usb4: configuration #1 chosen from 1 choice
Jul 22 16:53:31 hh-desktop kernel: [   23.669665] hub 4-0:1.0: USB hub found
Jul 22 16:53:31 hh-desktop kernel: [   23.669683] hub 4-0:1.0: 6 ports detected
Jul 22 16:53:31 hh-desktop kernel: [   23.688139] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jul 22 16:53:31 hh-desktop kernel: [   23.776719] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Jul 22 16:53:31 hh-desktop kernel: [   23.776728] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Jul 22 16:53:31 hh-desktop kernel: [   23.776880] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
Jul 22 16:53:31 hh-desktop kernel: [   23.776955] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
Jul 22 16:53:31 hh-desktop kernel: [   23.776987] scsi0 : ata_piix
Jul 22 16:53:31 hh-desktop kernel: [   23.944989] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 16:53:31 hh-desktop kernel: [   23.944997] ata1.00: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
Jul 22 16:53:31 hh-desktop kernel: [   23.945001] ata1.00: 78165360 sectors, multi 16: LBA 
Jul 22 16:53:31 hh-desktop kernel: [   23.956952] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 16:53:31 hh-desktop kernel: [   23.956959] ata1.00: configured for UDMA/100
Jul 22 16:53:31 hh-desktop kernel: [   23.956978] scsi1 : ata_piix
Jul 22 16:53:31 hh-desktop kernel: [   24.073006] Floppy drive(s): fd0 is 1.44M
Jul 22 16:53:31 hh-desktop kernel: [   24.095338] FDC 0 is a post-1991 82077
Jul 22 16:53:31 hh-desktop kernel: [   24.279704] ata2.00: ATAPI, max MWDMA2
Jul 22 16:53:31 hh-desktop kernel: [   24.443191] usb 1-1: new full speed USB device using uhci_hcd and address 3
Jul 22 16:53:31 hh-desktop kernel: [   24.447514] ata2.00: configured for MWDMA2
Jul 22 16:53:31 hh-desktop kernel: [   24.450071] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
Jul 22 16:53:31 hh-desktop kernel: [   24.451987] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-240B  R400 PQ: 0 ANSI: 5
Jul 22 16:53:31 hh-desktop kernel: [   24.458031] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Jul 22 16:53:31 hh-desktop kernel: [   24.458037] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
Jul 22 16:53:31 hh-desktop kernel: [   24.460818] 8139too Fast Ethernet driver 0.9.28
Jul 22 16:53:31 hh-desktop kernel: [   24.460902] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 20
Jul 22 16:53:31 hh-desktop kernel: [   24.461285] eth0: RealTek RTL8139 at 0xf8854000, 00:40:2b:41:30:ec, IRQ 20
Jul 22 16:53:31 hh-desktop kernel: [   24.638879] usb 1-1: configuration #1 chosen from 1 choice
Jul 22 16:53:31 hh-desktop kernel: [   24.962560] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 16:53:31 hh-desktop kernel: [   24.962879] sda: Write Protect is off
Jul 22 16:53:31 hh-desktop kernel: [   24.966864] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 16:53:31 hh-desktop kernel: [   24.970863] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 16:53:31 hh-desktop kernel: [   24.974508] sda: Write Protect is off
Jul 22 16:53:31 hh-desktop kernel: [   24.978501] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 16:53:31 hh-desktop kernel: [   24.978509]  sda: sda1 sda2 < sda5 >
Jul 22 16:53:31 hh-desktop kernel: [   25.040855] sd 0:0:0:0: Attached scsi disk sda
Jul 22 16:53:31 hh-desktop kernel: [   25.069610] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 22 16:53:31 hh-desktop kernel: [   25.069648] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Jul 22 16:53:31 hh-desktop kernel: [   25.083628] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jul 22 16:53:31 hh-desktop kernel: [   25.083637] Uniform CD-ROM driver Revision: 3.20
Jul 22 16:53:31 hh-desktop kernel: [   25.319017] usbcore: registered new interface driver hiddev
Jul 22 16:53:31 hh-desktop kernel: [   25.334949] input: Logitech USB Gaming Mouse as /class/input/input2
Jul 22 16:53:31 hh-desktop kernel: [   25.334994] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 16:53:31 hh-desktop kernel: [   25.340805] hiddev96: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 16:53:31 hh-desktop kernel: [   25.340832] usbcore: registered new interface driver usbhid
Jul 22 16:53:31 hh-desktop kernel: [   25.340837] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul 22 16:53:31 hh-desktop kernel: [   27.096332] Attempting manual resume
Jul 22 16:53:31 hh-desktop kernel: [   27.723129] kjournald starting.  Commit interval 5 seconds
Jul 22 16:53:31 hh-desktop kernel: [   27.723158] EXT3-fs: mounted filesystem with ordered data mode.
Jul 22 16:53:31 hh-desktop kernel: [   50.513707] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 22 16:53:31 hh-desktop kernel: [   51.981188] NET: Registered protocol family 17
Jul 22 16:53:31 hh-desktop kernel: [   52.988281] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Jul 22 16:53:31 hh-desktop kernel: [   53.038819] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 22 16:53:31 hh-desktop kernel: [   53.042340] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 22 16:53:31 hh-desktop kernel: [   53.206792] iTCO_vendor_support: vendor-support=0
Jul 22 16:53:31 hh-desktop kernel: [   53.208646] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Jul 22 16:53:31 hh-desktop kernel: [   53.208860] iTCO_wdt: No card detected
Jul 22 16:53:31 hh-desktop kernel: [   53.299540] Linux agpgart interface v0.102 (c) Dave Jones
Jul 22 16:53:31 hh-desktop kernel: [   53.303462] agpgart: Detected an Intel 845G Chipset.
Jul 22 16:53:31 hh-desktop kernel: [   53.303589] agpgart: Detected 892K stolen memory.
Jul 22 16:53:31 hh-desktop kernel: [   53.321777] agpgart: AGP aperture is 128M @ 0xf0000000
Jul 22 16:53:31 hh-desktop kernel: [   54.099205] input: PC Speaker as /class/input/input3
Jul 22 16:53:31 hh-desktop kernel: [   54.166720] usbcore: registered new interface driver xpad
Jul 22 16:53:31 hh-desktop kernel: [   54.166728] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
Jul 22 16:53:31 hh-desktop kernel: [   54.380601] parport: PnPBIOS parport detected.
Jul 22 16:53:31 hh-desktop kernel: [   54.380659] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul 22 16:53:31 hh-desktop kernel: [   54.916803] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
Jul 22 16:53:31 hh-desktop kernel: [   55.232541] intel8x0_measure_ac97_clock: measured 55070 usecs
Jul 22 16:53:31 hh-desktop kernel: [   55.232547] intel8x0: clocking to 48000
Jul 22 16:53:31 hh-desktop kernel: [   55.487549] fuse init (API version 7.8)
Jul 22 16:53:31 hh-desktop kernel: [   55.522321] lp0: using parport0 (interrupt-driven).
Jul 22 16:53:31 hh-desktop kernel: [   55.587435] Adding 1646620k swap on /dev/disk/by-uuid/b35569b7-a093-4d4e-b5f8-cbe0e1cf4b6c.  Priority:-1 extents:1 across:1646620k
Jul 22 16:53:31 hh-desktop kernel: [   55.772661] EXT3 FS on sda1, internal journal
Jul 22 16:53:31 hh-desktop kernel: [   56.063378] NET: Registered protocol family 10
Jul 22 16:53:31 hh-desktop kernel: [   56.063549] lo: Disabled Privacy Extensions
Jul 22 16:53:31 hh-desktop kernel: [   62.206498] input: Power Button (FF) as /class/input/input4
Jul 22 16:53:31 hh-desktop kernel: [   62.214462] ACPI: Power Button (FF) [PWRF]
Jul 22 16:53:31 hh-desktop kernel: [   62.258024] input: Power Button (CM) as /class/input/input5
Jul 22 16:53:31 hh-desktop kernel: [   62.266040] ACPI: Power Button (CM) [PWRB]
Jul 22 16:53:31 hh-desktop kernel: [   62.318757] Using specific hotkey driver
Jul 22 16:53:31 hh-desktop kernel: [   62.461789] No dock devices found.
Jul 22 16:53:31 hh-desktop kernel: [   62.736169] pcc_acpi: loading...
Jul 22 16:53:35 hh-desktop dhcdbd: Started up.
Jul 22 16:53:35 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 16:53:35 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 16:53:36 hh-desktop kernel: [   68.950755] ppdev: user-space parallel port driver
Jul 22 16:53:36 hh-desktop kernel: [   69.600797] [drm] Initialized drm 1.1.0 20060810
Jul 22 16:53:36 hh-desktop kernel: [   69.641051] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 16:53:36 hh-desktop kernel: [   69.645737] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul 22 16:53:37 hh-desktop hpiod: 1.7.3 accepting connections at 2208... 
Jul 22 16:53:38 hh-desktop kernel: [   71.435577] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 22 16:53:38 hh-desktop kernel: [   71.435586] apm: overridden by ACPI.
Jul 22 16:53:39 hh-desktop kernel: [   71.820071] Bluetooth: Core ver 2.11
Jul 22 16:53:39 hh-desktop kernel: [   71.820192] NET: Registered protocol family 31
Jul 22 16:53:39 hh-desktop kernel: [   71.820197] Bluetooth: HCI device and connection manager initialized
Jul 22 16:53:39 hh-desktop kernel: [   71.820202] Bluetooth: HCI socket layer initialized
Jul 22 16:53:39 hh-desktop kernel: [   71.906708] Bluetooth: L2CAP ver 2.8
Jul 22 16:53:39 hh-desktop kernel: [   71.906715] Bluetooth: L2CAP socket layer initialized
Jul 22 16:53:39 hh-desktop kernel: [   71.911795] Bluetooth: RFCOMM socket layer initialized
Jul 22 16:53:39 hh-desktop kernel: [   71.911817] Bluetooth: RFCOMM TTY layer initialized
Jul 22 16:53:39 hh-desktop kernel: [   71.911820] Bluetooth: RFCOMM ver 1.8
Jul 22 16:53:41 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 22 16:53:41 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 22 16:53:41 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 22 16:54:11 hh-desktop gconfd (hh-5458): starting (version 2.18.0.1), pid 5458 user 'hh'
Jul 22 16:54:11 hh-desktop gconfd (hh-5458): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 16:54:11 hh-desktop gconfd (hh-5458): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 16:54:11 hh-desktop gconfd (hh-5458): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:54:11 hh-desktop gconfd (hh-5458): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:54:11 hh-desktop gconfd (hh-5458): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:54:18 hh-desktop gconfd (hh-5458): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 0
Jul 22 17:01:40 hh-desktop kernel: [  552.404627] ACPI: Critical trip point
Jul 22 17:01:41 hh-desktop gconfd (hh-5458): Received signal 15, shutting down cleanly
Jul 22 17:01:41 hh-desktop gconfd (hh-5458): Exiting
Jul 22 17:01:48 hh-desktop exiting on signal 15
Jul 22 17:03:20 hh-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul 22 17:03:20 hh-desktop kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jul 22 17:03:20 hh-desktop kernel: Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.
Jul 22 17:03:20 hh-desktop kernel: Symbols match kernel version 2.6.20.
Jul 22 17:03:20 hh-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] sanitize start
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] sanitize end
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fbf0000 end: 000000003fcf0000 type: 1
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcf0000 size: 000000000000f000 end: 000000003fcff000 type: 3
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcff000 size: 0000000000001000 end: 000000003fd00000 type: 4
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fd00000 size: 0000000000180000 end: 000000003fe80000 type: 1
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fe80000 size: 0000000000180000 end: 0000000040000000 type: 2
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fcf0000 (usable)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcf0000 - 000000003fcff000 (ACPI data)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcff000 - 000000003fd00000 (ACPI NVS)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fd00000 - 000000003fe80000 (usable)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fe80000 - 0000000040000000 (reserved)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] 126MB HIGHMEM available.
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] 896MB LOWMEM available.
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] found SMP MP-table at 000f6690
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]   HighMem    229376 ->   261760
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul 22 17:03:20 hh-desktop kernel: [    0.000000]     0:        0 ->   261760
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] DMI present.
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] Processor #0 15:2 APIC version 20
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf800000)
Jul 22 17:03:20 hh-desktop kernel: [    0.000000] Detected 1993.682 MHz processor.
Jul 22 17:03:20 hh-desktop kernel: [   11.965247] Built 1 zonelists.  Total pages: 259715
Jul 22 17:03:20 hh-desktop kernel: [   11.965255] Kernel command line: root=UUID=cec7c039-003b-47b3-93fd-9645c20ab27d ro quiet splash
Jul 22 17:03:20 hh-desktop kernel: [   11.965476] Enabling fast FPU save and restore... done.
Jul 22 17:03:20 hh-desktop kernel: [   11.965480] Enabling unmasked SIMD FPU exception support... done.
Jul 22 17:03:20 hh-desktop kernel: [   11.965495] Initializing CPU#0
Jul 22 17:03:20 hh-desktop kernel: [   11.965587] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jul 22 17:03:20 hh-desktop kernel: [   11.967361] Console: colour VGA+ 80x25
Jul 22 17:03:20 hh-desktop kernel: [   11.968277] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 22 17:03:20 hh-desktop kernel: [   11.969745] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 22 17:03:20 hh-desktop kernel: [   12.005983] Memory: 1026796k/1047040k available (1992k kernel code, 19476k reserved, 900k data, 328k init, 129472k highmem)
Jul 22 17:03:20 hh-desktop kernel: [   12.005999] virtual kernel memory layout:
Jul 22 17:03:20 hh-desktop kernel: [   12.006000]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jul 22 17:03:20 hh-desktop kernel: [   12.006002]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 22 17:03:20 hh-desktop kernel: [   12.006003]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jul 22 17:03:20 hh-desktop kernel: [   12.006004]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jul 22 17:03:20 hh-desktop kernel: [   12.006006]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Jul 22 17:03:20 hh-desktop kernel: [   12.006007]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
Jul 22 17:03:20 hh-desktop kernel: [   12.006008]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
Jul 22 17:03:20 hh-desktop kernel: [   12.006012] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul 22 17:03:20 hh-desktop kernel: [   12.085446] Calibrating delay using timer specific routine.. 3990.98 BogoMIPS (lpj=7981966)
Jul 22 17:03:20 hh-desktop kernel: [   12.085519] Security Framework v1.0.0 initialized
Jul 22 17:03:20 hh-desktop kernel: [   12.085535] SELinux:  Disabled at boot.
Jul 22 17:03:20 hh-desktop kernel: [   12.085563] Mount-cache hash table entries: 512
Jul 22 17:03:20 hh-desktop kernel: [   12.085852] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jul 22 17:03:20 hh-desktop kernel: [   12.085856] CPU: L2 cache: 128K
Jul 22 17:03:20 hh-desktop kernel: [   12.085859] CPU: Hyper-Threading is disabled
Jul 22 17:03:20 hh-desktop kernel: [   12.085881] Compat vDSO mapped to ffffe000.
Jul 22 17:03:20 hh-desktop kernel: [   12.085886] Remapping vsyscall page to ffffe000
Jul 22 17:03:20 hh-desktop kernel: [   12.085906] Checking 'hlt' instruction... OK.
Jul 22 17:03:20 hh-desktop kernel: [   12.101578] SMP alternatives: switching to UP code
Jul 22 17:03:20 hh-desktop kernel: [   12.101982] Freeing SMP alternatives: 11k freed
Jul 22 17:03:20 hh-desktop kernel: [   12.102319] Early unpacking initramfs... done
Jul 22 17:03:20 hh-desktop kernel: [   12.520624] ACPI: Core revision 20060707
Jul 22 17:03:20 hh-desktop kernel: [   12.521811] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jul 22 17:03:20 hh-desktop kernel: [   12.528205] CPU0: Intel(R) Celeron(R) CPU 2.00GHz stepping 07
Jul 22 17:03:20 hh-desktop kernel: [   12.528350] Total of 1 processors activated (3990.98 BogoMIPS).
Jul 22 17:03:20 hh-desktop kernel: [   12.528682] ENABLING IO-APIC IRQs
Jul 22 17:03:20 hh-desktop kernel: [   12.529094] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jul 22 17:03:20 hh-desktop kernel: [   12.676945] Brought up 1 CPUs
Jul 22 17:03:20 hh-desktop kernel: [   12.677618] Booting paravirtualized kernel on bare hardware
Jul 22 17:03:20 hh-desktop kernel: [   12.677781] Time: 22:02:23  Date: 06/22/107
Jul 22 17:03:20 hh-desktop kernel: [   12.677840] NET: Registered protocol family 16
Jul 22 17:03:20 hh-desktop kernel: [   12.678355] EISA bus registered
Jul 22 17:03:20 hh-desktop kernel: [   12.678380] ACPI: bus type pci registered
Jul 22 17:03:20 hh-desktop kernel: [   12.681966] PCI: PCI BIOS revision 2.10 entry at 0xfd99a, last bus=2
Jul 22 17:03:20 hh-desktop kernel: [   12.681970] PCI: Using configuration type 1
Jul 22 17:03:20 hh-desktop kernel: [   12.681972] Setting up standard PCI resources
Jul 22 17:03:20 hh-desktop kernel: [   12.742697] ACPI: Interpreter enabled
Jul 22 17:03:20 hh-desktop kernel: [   12.742723] ACPI: Using IOAPIC for interrupt routing
Jul 22 17:03:20 hh-desktop kernel: [   12.743846] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 22 17:03:20 hh-desktop kernel: [   12.747813] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jul 22 17:03:20 hh-desktop kernel: [   12.747818] * this clock source is slow. If you are sure your timer does not have
Jul 22 17:03:20 hh-desktop kernel: [   12.747824] * this bug, please use "acpi_pm_good" to disable the workaround
Jul 22 17:03:20 hh-desktop kernel: [   12.747949] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Jul 22 17:03:20 hh-desktop kernel: [   12.747961] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
Jul 22 17:03:20 hh-desktop kernel: [   12.748898] PCI: Transparent bridge - 0000:00:1e.0
Jul 22 17:03:20 hh-desktop kernel: [   12.759030] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 17:03:20 hh-desktop kernel: [   12.759485] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 17:03:20 hh-desktop kernel: [   12.760333] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
Jul 22 17:03:20 hh-desktop kernel: [   12.761139] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jul 22 17:03:20 hh-desktop kernel: [   12.761960] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 17:03:20 hh-desktop kernel: [   12.762730] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 17:03:20 hh-desktop kernel: [   12.763197] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 17:03:20 hh-desktop kernel: [   12.764219] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 17:03:20 hh-desktop kernel: [   12.770003] ACPI: Power Resource [FN01] (on)
Jul 22 17:03:20 hh-desktop kernel: [   12.770283] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 22 17:03:20 hh-desktop kernel: [   12.770309] pnp: PnP ACPI init
Jul 22 17:03:20 hh-desktop kernel: [   12.836374] pnp: PnP ACPI: found 13 devices
Jul 22 17:03:20 hh-desktop kernel: [   12.836401] PnPBIOS: Disabled by ACPI PNP
Jul 22 17:03:20 hh-desktop kernel: [   12.836783] PCI: Using ACPI for IRQ routing
Jul 22 17:03:20 hh-desktop kernel: [   12.836801] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 22 17:03:20 hh-desktop kernel: [   12.845293] NET: Registered protocol family 8
Jul 22 17:03:20 hh-desktop kernel: [   12.845297] NET: Registered protocol family 20
Jul 22 17:03:20 hh-desktop kernel: [   12.846725] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
Jul 22 17:03:20 hh-desktop kernel: [   12.846744] PCI: Bridge: 0000:00:1e.0
Jul 22 17:03:20 hh-desktop kernel: [   12.846749]   IO window: 2000-2fff
Jul 22 17:03:20 hh-desktop kernel: [   12.846756]   MEM window: e8100000-e81fffff
Jul 22 17:03:20 hh-desktop kernel: [   12.846762]   PREFETCH window: disabled.
Jul 22 17:03:20 hh-desktop kernel: [   12.846829] NET: Registered protocol family 2
Jul 22 17:03:20 hh-desktop kernel: [   12.880603] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 22 17:03:20 hh-desktop kernel: [   12.880958] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 22 17:03:20 hh-desktop kernel: [   12.882665] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 22 17:03:20 hh-desktop kernel: [   12.883563] TCP: Hash tables configured (established 131072 bind 65536)
Jul 22 17:03:20 hh-desktop kernel: [   12.883570] TCP reno registered
Jul 22 17:03:20 hh-desktop kernel: [   12.892706] checking if image is initramfs... it is
Jul 22 17:03:20 hh-desktop kernel: [   14.361235] Freeing initrd memory: 6787k freed
Jul 22 17:03:20 hh-desktop kernel: [   14.361644] Simple Boot Flag at 0x3b set to 0x1
Jul 22 17:03:20 hh-desktop kernel: [   14.362275] audit: initializing netlink socket (disabled)
Jul 22 17:03:20 hh-desktop kernel: [   14.362297] audit(1185141744.484:1): initialized
Jul 22 17:03:20 hh-desktop kernel: [   14.362449] highmem bounce pool size: 64 pages
Jul 22 17:03:20 hh-desktop kernel: [   14.362606] VFS: Disk quotas dquot_6.5.1
Jul 22 17:03:20 hh-desktop kernel: [   14.362650] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 22 17:03:20 hh-desktop kernel: [   14.362778] io scheduler noop registered
Jul 22 17:03:20 hh-desktop kernel: [   14.362784] io scheduler anticipatory registered
Jul 22 17:03:20 hh-desktop kernel: [   14.362787] io scheduler deadline registered
Jul 22 17:03:20 hh-desktop kernel: [   14.362809] io scheduler cfq registered (default)
Jul 22 17:03:20 hh-desktop kernel: [   14.363403] isapnp: Scanning for PnP cards...
Jul 22 17:03:20 hh-desktop kernel: [   14.717298] isapnp: No Plug & Play device found
Jul 22 17:03:20 hh-desktop kernel: [   14.879665] Real Time Clock Driver v1.12ac
Jul 22 17:03:20 hh-desktop kernel: [   14.879804] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 22 17:03:20 hh-desktop kernel: [   14.880027] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 17:03:20 hh-desktop kernel: [   14.882909] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 17:03:20 hh-desktop kernel: [   14.883680] mice: PS/2 mouse device common for all mice
Jul 22 17:03:20 hh-desktop kernel: [   14.885485] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 22 17:03:20 hh-desktop kernel: [   14.885857] input: Macintosh mouse button emulation as /class/input/input0
Jul 22 17:03:20 hh-desktop kernel: [   14.885968] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 22 17:03:20 hh-desktop kernel: [   14.885976] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 22 17:03:20 hh-desktop kernel: [   14.886468] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Jul 22 17:03:20 hh-desktop kernel: [   14.889638] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 22 17:03:20 hh-desktop kernel: [   14.889648] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 22 17:03:20 hh-desktop kernel: [   14.890031] EISA: Probing bus 0 at eisa.0
Jul 22 17:03:20 hh-desktop kernel: [   14.890102] Cannot allocate resource for EISA slot 1
Jul 22 17:03:20 hh-desktop kernel: [   14.890107] Cannot allocate resource for EISA slot 2
Jul 22 17:03:20 hh-desktop kernel: [   14.890134] EISA: Detected 0 cards.
Jul 22 17:03:20 hh-desktop kernel: [   14.920245] TCP cubic registered
Jul 22 17:03:20 hh-desktop kernel: [   14.920262] NET: Registered protocol family 1
Jul 22 17:03:20 hh-desktop kernel: [   14.920306] Using IPI No-Shortcut mode
Jul 22 17:03:20 hh-desktop kernel: [   14.920483] ACPI: (supports S0 S1 S3 S4 S5)
Jul 22 17:03:20 hh-desktop kernel: [   14.920555]   Magic number: 15:953:47
Jul 22 17:03:20 hh-desktop kernel: [   14.921271] Freeing unused kernel memory: 328k freed
Jul 22 17:03:20 hh-desktop kernel: [   14.921958] Time: tsc clocksource has been installed.
Jul 22 17:03:20 hh-desktop kernel: [   14.936916] input: AT Translated Set 2 keyboard as /class/input/input1
Jul 22 17:03:20 hh-desktop kernel: [   16.507611] Capability LSM initialized
Jul 22 17:03:20 hh-desktop kernel: [   17.083424] ACPI: Transitioning device [FAN1] to D0
Jul 22 17:03:20 hh-desktop kernel: [   17.083430] ACPI: Transitioning device [FAN1] to D0
Jul 22 17:03:20 hh-desktop kernel: [   17.083438] ACPI: Fan [FAN1] (off)
Jul 22 17:03:20 hh-desktop kernel: [   17.090590] ACPI: Processor [CPU0] (supports 8 throttling states)
Jul 22 17:03:20 hh-desktop kernel: [   17.099797] ACPI: Thermal Zone [THRM] (-264 C)
Jul 22 17:03:20 hh-desktop kernel: [   27.083457] usbcore: registered new interface driver usbfs
Jul 22 17:03:20 hh-desktop kernel: [   27.083503] usbcore: registered new interface driver hub
Jul 22 17:03:20 hh-desktop kernel: [   27.083572] usbcore: registered new device driver usb
Jul 22 17:03:20 hh-desktop kernel: [   27.084994] USB Universal Host Controller Interface driver v3.0
Jul 22 17:03:20 hh-desktop kernel: [   27.085092] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 17:03:20 hh-desktop kernel: [   27.085115] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 22 17:03:20 hh-desktop kernel: [   27.085313] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jul 22 17:03:20 hh-desktop kernel: [   27.085354] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
Jul 22 17:03:20 hh-desktop kernel: [   27.085554] usb usb1: configuration #1 chosen from 1 choice
Jul 22 17:03:20 hh-desktop kernel: [   27.085618] hub 1-0:1.0: USB hub found
Jul 22 17:03:20 hh-desktop kernel: [   27.085632] hub 1-0:1.0: 2 ports detected
Jul 22 17:03:20 hh-desktop kernel: [   27.187343] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Jul 22 17:03:20 hh-desktop kernel: [   27.187367] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 22 17:03:20 hh-desktop kernel: [   27.187419] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jul 22 17:03:20 hh-desktop kernel: [   27.187455] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
Jul 22 17:03:20 hh-desktop kernel: [   27.187634] usb usb2: configuration #1 chosen from 1 choice
Jul 22 17:03:20 hh-desktop kernel: [   27.187699] hub 2-0:1.0: USB hub found
Jul 22 17:03:20 hh-desktop kernel: [   27.187715] hub 2-0:1.0: 2 ports detected
Jul 22 17:03:20 hh-desktop kernel: [   27.291197] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 22 17:03:20 hh-desktop kernel: [   27.291220] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 22 17:03:20 hh-desktop kernel: [   27.291273] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jul 22 17:03:20 hh-desktop kernel: [   27.291316] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Jul 22 17:03:20 hh-desktop kernel: [   27.291499] usb usb3: configuration #1 chosen from 1 choice
Jul 22 17:03:20 hh-desktop kernel: [   27.291559] hub 3-0:1.0: USB hub found
Jul 22 17:03:20 hh-desktop kernel: [   27.291576] hub 3-0:1.0: 2 ports detected
Jul 22 17:03:20 hh-desktop kernel: [   27.396607] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Jul 22 17:03:20 hh-desktop kernel: [   27.396639] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 22 17:03:20 hh-desktop kernel: [   27.396706] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jul 22 17:03:20 hh-desktop kernel: [   27.396774] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe8080000
Jul 22 17:03:20 hh-desktop kernel: [   27.400646] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 22 17:03:20 hh-desktop kernel: [   27.400808] usb usb4: configuration #1 chosen from 1 choice
Jul 22 17:03:20 hh-desktop kernel: [   27.400868] hub 4-0:1.0: USB hub found
Jul 22 17:03:20 hh-desktop kernel: [   27.400884] hub 4-0:1.0: 6 ports detected
Jul 22 17:03:20 hh-desktop kernel: [   27.426856] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jul 22 17:03:20 hh-desktop kernel: [   27.438188] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jul 22 17:03:20 hh-desktop kernel: [   27.503395] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Jul 22 17:03:20 hh-desktop kernel: [   27.503402] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
Jul 22 17:03:20 hh-desktop kernel: [   27.506065] 8139too Fast Ethernet driver 0.9.28
Jul 22 17:03:20 hh-desktop kernel: [   27.506150] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 20
Jul 22 17:03:20 hh-desktop kernel: [   27.506551] eth0: RealTek RTL8139 at 0xf8848000, 00:40:2b:41:30:ec, IRQ 20
Jul 22 17:03:20 hh-desktop kernel: [   27.611606] SCSI subsystem initialized
Jul 22 17:03:20 hh-desktop kernel: [   27.622836] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Jul 22 17:03:20 hh-desktop kernel: [   27.622844] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Jul 22 17:03:20 hh-desktop kernel: [   27.622980] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
Jul 22 17:03:20 hh-desktop kernel: [   27.623048] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
Jul 22 17:03:20 hh-desktop kernel: [   27.623082] scsi0 : ata_piix
Jul 22 17:03:20 hh-desktop kernel: [   27.787594] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 17:03:20 hh-desktop kernel: [   27.787602] ata1.00: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
Jul 22 17:03:20 hh-desktop kernel: [   27.787606] ata1.00: 78165360 sectors, multi 16: LBA 
Jul 22 17:03:20 hh-desktop kernel: [   27.795614] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 17:03:20 hh-desktop kernel: [   27.795623] ata1.00: configured for UDMA/100
Jul 22 17:03:20 hh-desktop kernel: [   27.795647] scsi1 : ata_piix
Jul 22 17:03:20 hh-desktop kernel: [   27.812438] Floppy drive(s): fd0 is 1.44M
Jul 22 17:03:20 hh-desktop kernel: [   27.840297] FDC 0 is a post-1991 82077
Jul 22 17:03:20 hh-desktop kernel: [   27.930225] usb 1-1: new full speed USB device using uhci_hcd and address 3
Jul 22 17:03:20 hh-desktop kernel: [   28.114327] ata2.00: ATAPI, max MWDMA2
Jul 22 17:03:20 hh-desktop kernel: [   28.118074] usb 1-1: configuration #1 chosen from 1 choice
Jul 22 17:03:20 hh-desktop kernel: [   28.278110] ata2.00: configured for MWDMA2
Jul 22 17:03:20 hh-desktop kernel: [   28.281829] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
Jul 22 17:03:20 hh-desktop kernel: [   28.283639] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-240B  R400 PQ: 0 ANSI: 5
Jul 22 17:03:20 hh-desktop kernel: [   28.941305] usbcore: registered new interface driver hiddev
Jul 22 17:03:20 hh-desktop kernel: [   28.972918] input: Logitech USB Gaming Mouse as /class/input/input2
Jul 22 17:03:20 hh-desktop kernel: [   28.973019] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 17:03:20 hh-desktop kernel: [   28.973078] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 17:03:20 hh-desktop kernel: [   28.973722] sda: Write Protect is off
Jul 22 17:03:20 hh-desktop kernel: [   28.975677] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 17:03:20 hh-desktop kernel: [   28.976991] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 17:03:20 hh-desktop kernel: [   28.977669] sda: Write Protect is off
Jul 22 17:03:20 hh-desktop kernel: [   28.978752] hiddev96: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 17:03:20 hh-desktop kernel: [   28.978778] usbcore: registered new interface driver usbhid
Jul 22 17:03:20 hh-desktop kernel: [   28.978784] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul 22 17:03:20 hh-desktop kernel: [   28.979894] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 17:03:20 hh-desktop kernel: [   28.979905]  sda: sda1 sda2 < sda5 >
Jul 22 17:03:20 hh-desktop kernel: [   29.043146] sd 0:0:0:0: Attached scsi disk sda
Jul 22 17:03:20 hh-desktop kernel: [   29.050615] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 22 17:03:20 hh-desktop kernel: [   29.050653] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 22 17:03:20 hh-desktop kernel: [   29.055171] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jul 22 17:03:20 hh-desktop kernel: [   29.055179] Uniform CD-ROM driver Revision: 3.20
Jul 22 17:03:20 hh-desktop kernel: [   30.950948] Attempting manual resume
Jul 22 17:03:20 hh-desktop kernel: [   31.601239] kjournald starting.  Commit interval 5 seconds
Jul 22 17:03:20 hh-desktop kernel: [   31.601266] EXT3-fs: mounted filesystem with ordered data mode.
Jul 22 17:03:20 hh-desktop kernel: [   55.868926] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 22 17:03:20 hh-desktop kernel: [   57.382059] NET: Registered protocol family 17
Jul 22 17:03:20 hh-desktop kernel: [   58.421197] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Jul 22 17:03:20 hh-desktop kernel: [   58.672230] iTCO_vendor_support: vendor-support=0
Jul 22 17:03:20 hh-desktop kernel: [   58.674322] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Jul 22 17:03:20 hh-desktop kernel: [   58.674876] iTCO_wdt: No card detected
Jul 22 17:03:20 hh-desktop kernel: [   58.727587] Linux agpgart interface v0.102 (c) Dave Jones
Jul 22 17:03:20 hh-desktop kernel: [   58.731137] agpgart: Detected an Intel 845G Chipset.
Jul 22 17:03:20 hh-desktop kernel: [   58.731267] agpgart: Detected 892K stolen memory.
Jul 22 17:03:20 hh-desktop kernel: [   58.750226] agpgart: AGP aperture is 128M @ 0xf0000000
Jul 22 17:03:20 hh-desktop kernel: [   59.508364] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 22 17:03:20 hh-desktop kernel: [   59.511970] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 22 17:03:20 hh-desktop kernel: [   60.108111] input: PC Speaker as /class/input/input3
Jul 22 17:03:20 hh-desktop kernel: [   60.118929] parport: PnPBIOS parport detected.
Jul 22 17:03:20 hh-desktop kernel: [   60.119031] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul 22 17:03:20 hh-desktop kernel: [   60.401246] usbcore: registered new interface driver xpad
Jul 22 17:03:20 hh-desktop kernel: [   60.401255] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
Jul 22 17:03:20 hh-desktop kernel: [   60.862200] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
Jul 22 17:03:20 hh-desktop kernel: [   61.177849] intel8x0_measure_ac97_clock: measured 55083 usecs
Jul 22 17:03:20 hh-desktop kernel: [   61.177855] intel8x0: clocking to 48000
Jul 22 17:03:20 hh-desktop kernel: [   61.432995] fuse init (API version 7.8)
Jul 22 17:03:20 hh-desktop kernel: [   61.467578] lp0: using parport0 (interrupt-driven).
Jul 22 17:03:20 hh-desktop kernel: [   61.532183] Adding 1646620k swap on /dev/disk/by-uuid/b35569b7-a093-4d4e-b5f8-cbe0e1cf4b6c.  Priority:-1 extents:1 across:1646620k
Jul 22 17:03:20 hh-desktop kernel: [   61.715829] EXT3 FS on sda1, internal journal
Jul 22 17:03:20 hh-desktop kernel: [   61.976924] NET: Registered protocol family 10
Jul 22 17:03:20 hh-desktop kernel: [   61.977106] lo: Disabled Privacy Extensions
Jul 22 17:03:20 hh-desktop kernel: [   68.077908] input: Power Button (FF) as /class/input/input4
Jul 22 17:03:20 hh-desktop kernel: [   68.085756] ACPI: Power Button (FF) [PWRF]
Jul 22 17:03:20 hh-desktop kernel: [   68.136213] input: Power Button (CM) as /class/input/input5
Jul 22 17:03:20 hh-desktop kernel: [   68.144296] ACPI: Power Button (CM) [PWRB]
Jul 22 17:03:20 hh-desktop kernel: [   68.199832] Using specific hotkey driver
Jul 22 17:03:20 hh-desktop kernel: [   68.343308] No dock devices found.
Jul 22 17:03:20 hh-desktop kernel: [   68.622882] pcc_acpi: loading...
Jul 22 17:03:25 hh-desktop dhcdbd: Started up.
Jul 22 17:03:26 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 17:03:26 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 17:03:26 hh-desktop kernel: [   76.017082] ppdev: user-space parallel port driver
Jul 22 17:03:27 hh-desktop kernel: [   76.677227] [drm] Initialized drm 1.1.0 20060810
Jul 22 17:03:27 hh-desktop kernel: [   76.728664] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 17:03:27 hh-desktop kernel: [   76.733386] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul 22 17:03:29 hh-desktop hpiod: 1.7.3 accepting connections at 2208... 
Jul 22 17:03:29 hh-desktop kernel: [   78.875566] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 22 17:03:29 hh-desktop kernel: [   78.875574] apm: overridden by ACPI.
Jul 22 17:03:30 hh-desktop kernel: [   79.185418] Bluetooth: Core ver 2.11
Jul 22 17:03:30 hh-desktop kernel: [   79.185539] NET: Registered protocol family 31
Jul 22 17:03:30 hh-desktop kernel: [   79.185544] Bluetooth: HCI device and connection manager initialized
Jul 22 17:03:30 hh-desktop kernel: [   79.185550] Bluetooth: HCI socket layer initialized
Jul 22 17:03:30 hh-desktop kernel: [   79.261284] Bluetooth: L2CAP ver 2.8
Jul 22 17:03:30 hh-desktop kernel: [   79.261291] Bluetooth: L2CAP socket layer initialized
Jul 22 17:03:30 hh-desktop kernel: [   79.417195] Bluetooth: RFCOMM socket layer initialized
Jul 22 17:03:30 hh-desktop kernel: [   79.417253] Bluetooth: RFCOMM TTY layer initialized
Jul 22 17:03:30 hh-desktop kernel: [   79.417259] Bluetooth: RFCOMM ver 1.8
Jul 22 17:03:31 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 22 17:03:31 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 22 17:03:31 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 22 17:03:39 hh-desktop gconfd (hh-5461): starting (version 2.18.0.1), pid 5461 user 'hh'
Jul 22 17:03:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 17:03:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 17:03:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 17:03:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 17:03:40 hh-desktop gconfd (hh-5461): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 17:03:49 hh-desktop gconfd (hh-5461): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 0
Jul 22 17:05:27 hh-desktop kernel: [  196.909314] ACPI: Critical trip point
Jul 22 17:05:29 hh-desktop gconfd (hh-5461): Received signal 15, shutting down cleanly
Jul 22 17:05:29 hh-desktop gconfd (hh-5461): Exiting
Jul 22 17:05:35 hh-desktop exiting on signal 15
Jul 22 17:09:55 hh-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul 22 17:09:55 hh-desktop kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jul 22 17:09:56 hh-desktop kernel: Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.
Jul 22 17:09:56 hh-desktop kernel: Symbols match kernel version 2.6.20.
Jul 22 17:09:56 hh-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] sanitize start
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] sanitize end
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fbf0000 end: 000000003fcf0000 type: 1
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcf0000 size: 000000000000f000 end: 000000003fcff000 type: 3
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fcff000 size: 0000000000001000 end: 000000003fd00000 type: 4
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fd00000 size: 0000000000180000 end: 000000003fe80000 type: 1
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() start: 000000003fe80000 size: 0000000000180000 end: 0000000040000000 type: 2
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fcf0000 (usable)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcf0000 - 000000003fcff000 (ACPI data)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fcff000 - 000000003fd00000 (ACPI NVS)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fd00000 - 000000003fe80000 (usable)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]  BIOS-e820: 000000003fe80000 - 0000000040000000 (reserved)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] 126MB HIGHMEM available.
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] 896MB LOWMEM available.
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] found SMP MP-table at 000f6690
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]   HighMem    229376 ->   261760
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul 22 17:09:56 hh-desktop kernel: [    0.000000]     0:        0 ->   261760
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] DMI present.
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] Processor #0 15:2 APIC version 20
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf800000)
Jul 22 17:09:56 hh-desktop kernel: [    0.000000] Detected 1993.593 MHz processor.
Jul 22 17:09:56 hh-desktop kernel: [   11.298317] Built 1 zonelists.  Total pages: 259715
Jul 22 17:09:56 hh-desktop kernel: [   11.298326] Kernel command line: root=UUID=cec7c039-003b-47b3-93fd-9645c20ab27d ro quiet splash
Jul 22 17:09:56 hh-desktop kernel: [   11.298546] Enabling fast FPU save and restore... done.
Jul 22 17:09:56 hh-desktop kernel: [   11.298550] Enabling unmasked SIMD FPU exception support... done.
Jul 22 17:09:56 hh-desktop kernel: [   11.298564] Initializing CPU#0
Jul 22 17:09:56 hh-desktop kernel: [   11.298657] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jul 22 17:09:56 hh-desktop kernel: [   11.300401] Console: colour VGA+ 80x25
Jul 22 17:09:56 hh-desktop kernel: [   11.301329] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 22 17:09:56 hh-desktop kernel: [   11.302799] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 22 17:09:56 hh-desktop kernel: [   11.339005] Memory: 1026796k/1047040k available (1992k kernel code, 19476k reserved, 900k data, 328k init, 129472k highmem)
Jul 22 17:09:56 hh-desktop kernel: [   11.339021] virtual kernel memory layout:
Jul 22 17:09:56 hh-desktop kernel: [   11.339023]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jul 22 17:09:56 hh-desktop kernel: [   11.339024]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 22 17:09:56 hh-desktop kernel: [   11.339026]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jul 22 17:09:56 hh-desktop kernel: [   11.339027]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jul 22 17:09:56 hh-desktop kernel: [   11.339029]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Jul 22 17:09:56 hh-desktop kernel: [   11.339030]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
Jul 22 17:09:56 hh-desktop kernel: [   11.339031]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
Jul 22 17:09:56 hh-desktop kernel: [   11.339036] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul 22 17:09:56 hh-desktop kernel: [   11.418516] Calibrating delay using timer specific routine.. 3990.99 BogoMIPS (lpj=7981986)
Jul 22 17:09:56 hh-desktop kernel: [   11.418588] Security Framework v1.0.0 initialized
Jul 22 17:09:56 hh-desktop kernel: [   11.418604] SELinux:  Disabled at boot.
Jul 22 17:09:56 hh-desktop kernel: [   11.418633] Mount-cache hash table entries: 512
Jul 22 17:09:56 hh-desktop kernel: [   11.418919] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jul 22 17:09:56 hh-desktop kernel: [   11.418924] CPU: L2 cache: 128K
Jul 22 17:09:56 hh-desktop kernel: [   11.418927] CPU: Hyper-Threading is disabled
Jul 22 17:09:56 hh-desktop kernel: [   11.418949] Compat vDSO mapped to ffffe000.
Jul 22 17:09:56 hh-desktop kernel: [   11.418953] Remapping vsyscall page to ffffe000
Jul 22 17:09:56 hh-desktop kernel: [   11.418973] Checking 'hlt' instruction... OK.
Jul 22 17:09:56 hh-desktop kernel: [   11.434646] SMP alternatives: switching to UP code
Jul 22 17:09:56 hh-desktop kernel: [   11.435051] Freeing SMP alternatives: 11k freed
Jul 22 17:09:56 hh-desktop kernel: [   11.435387] Early unpacking initramfs... done
Jul 22 17:09:56 hh-desktop kernel: [   11.854724] ACPI: Core revision 20060707
Jul 22 17:09:56 hh-desktop kernel: [   11.855881] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jul 22 17:09:56 hh-desktop kernel: [   11.860951] CPU0: Intel(R) Celeron(R) CPU 2.00GHz stepping 07
Jul 22 17:09:56 hh-desktop kernel: [   11.861011] Total of 1 processors activated (3990.99 BogoMIPS).
Jul 22 17:09:56 hh-desktop kernel: [   11.861159] ENABLING IO-APIC IRQs
Jul 22 17:09:56 hh-desktop kernel: [   11.861366] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jul 22 17:09:56 hh-desktop kernel: [   12.005877] Brought up 1 CPUs
Jul 22 17:09:56 hh-desktop kernel: [   12.006271] Booting paravirtualized kernel on bare hardware
Jul 22 17:09:56 hh-desktop kernel: [   12.006436] Time: 22:09:01  Date: 06/22/107
Jul 22 17:09:56 hh-desktop kernel: [   12.006494] NET: Registered protocol family 16
Jul 22 17:09:56 hh-desktop kernel: [   12.006710] EISA bus registered
Jul 22 17:09:56 hh-desktop kernel: [   12.006722] ACPI: bus type pci registered
Jul 22 17:09:56 hh-desktop kernel: [   12.008629] PCI: PCI BIOS revision 2.10 entry at 0xfd99a, last bus=2
Jul 22 17:09:56 hh-desktop kernel: [   12.008632] PCI: Using configuration type 1
Jul 22 17:09:56 hh-desktop kernel: [   12.008635] Setting up standard PCI resources
Jul 22 17:09:56 hh-desktop kernel: [   12.039683] ACPI: Interpreter enabled
Jul 22 17:09:56 hh-desktop kernel: [   12.039693] ACPI: Using IOAPIC for interrupt routing
Jul 22 17:09:56 hh-desktop kernel: [   12.040604] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 22 17:09:56 hh-desktop kernel: [   12.043027] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jul 22 17:09:56 hh-desktop kernel: [   12.043029] * this clock source is slow. If you are sure your timer does not have
Jul 22 17:09:56 hh-desktop kernel: [   12.043031] * this bug, please use "acpi_pm_good" to disable the workaround
Jul 22 17:09:56 hh-desktop kernel: [   12.043086] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Jul 22 17:09:56 hh-desktop kernel: [   12.043092] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
Jul 22 17:09:56 hh-desktop kernel: [   12.043561] PCI: Transparent bridge - 0000:00:1e.0
Jul 22 17:09:56 hh-desktop kernel: [   12.051710] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 17:09:56 hh-desktop kernel: [   12.052173] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 17:09:56 hh-desktop kernel: [   12.052640] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
Jul 22 17:09:56 hh-desktop kernel: [   12.053105] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jul 22 17:09:56 hh-desktop kernel: [   12.053593] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 17:09:56 hh-desktop kernel: [   12.054108] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jul 22 17:09:56 hh-desktop kernel: [   12.054583] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jul 22 17:09:56 hh-desktop kernel: [   12.055076] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jul 22 17:09:56 hh-desktop kernel: [   12.059221] ACPI: Power Resource [FN01] (on)
Jul 22 17:09:56 hh-desktop kernel: [   12.059503] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 22 17:09:56 hh-desktop kernel: [   12.059531] pnp: PnP ACPI init
Jul 22 17:09:56 hh-desktop kernel: [   12.097281] pnp: PnP ACPI: found 13 devices
Jul 22 17:09:56 hh-desktop kernel: [   12.097291] PnPBIOS: Disabled by ACPI PNP
Jul 22 17:09:56 hh-desktop kernel: [   12.097416] PCI: Using ACPI for IRQ routing
Jul 22 17:09:56 hh-desktop kernel: [   12.097422] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 22 17:09:56 hh-desktop kernel: [   12.102314] NET: Registered protocol family 8
Jul 22 17:09:56 hh-desktop kernel: [   12.102317] NET: Registered protocol family 20
Jul 22 17:09:56 hh-desktop kernel: [   12.103767] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
Jul 22 17:09:56 hh-desktop kernel: [   12.103785] PCI: Bridge: 0000:00:1e.0
Jul 22 17:09:56 hh-desktop kernel: [   12.103790]   IO window: 2000-2fff
Jul 22 17:09:56 hh-desktop kernel: [   12.103797]   MEM window: e8100000-e81fffff
Jul 22 17:09:56 hh-desktop kernel: [   12.103803]   PREFETCH window: disabled.
Jul 22 17:09:56 hh-desktop kernel: [   12.103868] NET: Registered protocol family 2
Jul 22 17:09:56 hh-desktop kernel: [   12.141744] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 22 17:09:56 hh-desktop kernel: [   12.142090] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 22 17:09:56 hh-desktop kernel: [   12.143790] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 22 17:09:56 hh-desktop kernel: [   12.144690] TCP: Hash tables configured (established 131072 bind 65536)
Jul 22 17:09:56 hh-desktop kernel: [   12.144697] TCP reno registered
Jul 22 17:09:56 hh-desktop kernel: [   12.153845] checking if image is initramfs... it is
Jul 22 17:09:56 hh-desktop kernel: [   12.946933] Freeing initrd memory: 6787k freed
Jul 22 17:09:56 hh-desktop kernel: [   12.947330] Simple Boot Flag at 0x3b set to 0x1
Jul 22 17:09:56 hh-desktop kernel: [   12.947926] audit: initializing netlink socket (disabled)
Jul 22 17:09:56 hh-desktop kernel: [   12.947946] audit(1185142141.728:1): initialized
Jul 22 17:09:56 hh-desktop kernel: [   12.948097] highmem bounce pool size: 64 pages
Jul 22 17:09:56 hh-desktop kernel: [   12.948252] VFS: Disk quotas dquot_6.5.1
Jul 22 17:09:56 hh-desktop kernel: [   12.948285] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 22 17:09:56 hh-desktop kernel: [   12.948385] io scheduler noop registered
Jul 22 17:09:56 hh-desktop kernel: [   12.948391] io scheduler anticipatory registered
Jul 22 17:09:56 hh-desktop kernel: [   12.948394] io scheduler deadline registered
Jul 22 17:09:56 hh-desktop kernel: [   12.948417] io scheduler cfq registered (default)
Jul 22 17:09:56 hh-desktop kernel: [   12.949012] isapnp: Scanning for PnP cards...
Jul 22 17:09:56 hh-desktop kernel: [   13.302903] isapnp: No Plug & Play device found
Jul 22 17:09:56 hh-desktop kernel: [   13.434810] Real Time Clock Driver v1.12ac
Jul 22 17:09:56 hh-desktop kernel: [   13.434946] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 22 17:09:56 hh-desktop kernel: [   13.435164] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 17:09:56 hh-desktop kernel: [   13.437414] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 22 17:09:56 hh-desktop kernel: [   13.438216] mice: PS/2 mouse device common for all mice
Jul 22 17:09:56 hh-desktop kernel: [   13.440195] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 22 17:09:56 hh-desktop kernel: [   13.440632] input: Macintosh mouse button emulation as /class/input/input0
Jul 22 17:09:56 hh-desktop kernel: [   13.440738] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 22 17:09:56 hh-desktop kernel: [   13.440746] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 22 17:09:56 hh-desktop kernel: [   13.441195] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Jul 22 17:09:56 hh-desktop kernel: [   13.444320] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 22 17:09:56 hh-desktop kernel: [   13.444330] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 22 17:09:56 hh-desktop kernel: [   13.444708] EISA: Probing bus 0 at eisa.0
Jul 22 17:09:56 hh-desktop kernel: [   13.444720] Cannot allocate resource for EISA slot 1
Jul 22 17:09:56 hh-desktop kernel: [   13.444724] Cannot allocate resource for EISA slot 2
Jul 22 17:09:56 hh-desktop kernel: [   13.444750] EISA: Detected 0 cards.
Jul 22 17:09:56 hh-desktop kernel: [   13.474857] TCP cubic registered
Jul 22 17:09:56 hh-desktop kernel: [   13.474873] NET: Registered protocol family 1
Jul 22 17:09:56 hh-desktop kernel: [   13.474914] Using IPI No-Shortcut mode
Jul 22 17:09:56 hh-desktop kernel: [   13.475079] ACPI: (supports S0 S1 S3 S4 S5)
Jul 22 17:09:56 hh-desktop kernel: [   13.475150]   Magic number: 15:609:199
Jul 22 17:09:56 hh-desktop kernel: [   13.475237]   hash matches device ttype
Jul 22 17:09:56 hh-desktop kernel: [   13.475847] Freeing unused kernel memory: 328k freed
Jul 22 17:09:56 hh-desktop kernel: [   13.475987] Time: tsc clocksource has been installed.
Jul 22 17:09:56 hh-desktop kernel: [   13.491907] input: AT Translated Set 2 keyboard as /class/input/input1
Jul 22 17:09:56 hh-desktop kernel: [   15.097041] Capability LSM initialized
Jul 22 17:09:56 hh-desktop kernel: [   15.668062] ACPI: Transitioning device [FAN1] to D0
Jul 22 17:09:56 hh-desktop kernel: [   15.668069] ACPI: Transitioning device [FAN1] to D0
Jul 22 17:09:56 hh-desktop kernel: [   15.668076] ACPI: Fan [FAN1] (off)
Jul 22 17:09:56 hh-desktop kernel: [   15.675061] ACPI: Processor [CPU0] (supports 8 throttling states)
Jul 22 17:09:56 hh-desktop kernel: [   15.684159] ACPI: Thermal Zone [THRM] (-265 C)
Jul 22 17:09:56 hh-desktop kernel: [   26.005275] usbcore: registered new interface driver usbfs
Jul 22 17:09:56 hh-desktop kernel: [   26.005319] usbcore: registered new interface driver hub
Jul 22 17:09:56 hh-desktop kernel: [   26.005390] usbcore: registered new device driver usb
Jul 22 17:09:56 hh-desktop kernel: [   26.006853] USB Universal Host Controller Interface driver v3.0
Jul 22 17:09:56 hh-desktop kernel: [   26.006943] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 17:09:56 hh-desktop kernel: [   26.006970] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 22 17:09:56 hh-desktop kernel: [   26.007165] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jul 22 17:09:56 hh-desktop kernel: [   26.007205] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
Jul 22 17:09:56 hh-desktop kernel: [   26.007403] usb usb1: configuration #1 chosen from 1 choice
Jul 22 17:09:56 hh-desktop kernel: [   26.007467] hub 1-0:1.0: USB hub found
Jul 22 17:09:56 hh-desktop kernel: [   26.007482] hub 1-0:1.0: 2 ports detected
Jul 22 17:09:56 hh-desktop kernel: [   26.111777] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Jul 22 17:09:56 hh-desktop kernel: [   26.111801] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 22 17:09:56 hh-desktop kernel: [   26.111855] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jul 22 17:09:56 hh-desktop kernel: [   26.111892] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
Jul 22 17:09:56 hh-desktop kernel: [   26.112078] usb usb2: configuration #1 chosen from 1 choice
Jul 22 17:09:56 hh-desktop kernel: [   26.112136] hub 2-0:1.0: USB hub found
Jul 22 17:09:56 hh-desktop kernel: [   26.112154] hub 2-0:1.0: 2 ports detected
Jul 22 17:09:56 hh-desktop kernel: [   26.194753] SCSI subsystem initialized
Jul 22 17:09:56 hh-desktop kernel: [   26.215621] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul 22 17:09:56 hh-desktop kernel: [   26.215645] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 22 17:09:56 hh-desktop kernel: [   26.215695] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jul 22 17:09:56 hh-desktop kernel: [   26.215732] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Jul 22 17:09:56 hh-desktop kernel: [   26.215909] usb usb3: configuration #1 chosen from 1 choice
Jul 22 17:09:56 hh-desktop kernel: [   26.215967] hub 3-0:1.0: USB hub found
Jul 22 17:09:56 hh-desktop kernel: [   26.215983] hub 3-0:1.0: 2 ports detected
Jul 22 17:09:56 hh-desktop kernel: [   26.223215] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jul 22 17:09:56 hh-desktop kernel: [   26.319926] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Jul 22 17:09:56 hh-desktop kernel: [   26.319957] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 22 17:09:56 hh-desktop kernel: [   26.320025] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jul 22 17:09:56 hh-desktop kernel: [   26.320100] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe8080000
Jul 22 17:09:56 hh-desktop kernel: [   26.323975] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 22 17:09:56 hh-desktop kernel: [   26.324129] usb usb4: configuration #1 chosen from 1 choice
Jul 22 17:09:56 hh-desktop kernel: [   26.324197] hub 4-0:1.0: USB hub found
Jul 22 17:09:56 hh-desktop kernel: [   26.324215] hub 4-0:1.0: 6 ports detected
Jul 22 17:09:56 hh-desktop kernel: [   26.351252] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jul 22 17:09:56 hh-desktop kernel: [   26.431785] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Jul 22 17:09:56 hh-desktop kernel: [   26.431791] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
Jul 22 17:09:56 hh-desktop kernel: [   26.434538] 8139too Fast Ethernet driver 0.9.28
Jul 22 17:09:56 hh-desktop kernel: [   26.434623] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 20
Jul 22 17:09:56 hh-desktop kernel: [   26.435005] eth0: RealTek RTL8139 at 0xf8854000, 00:40:2b:41:30:ec, IRQ 20
Jul 22 17:09:56 hh-desktop kernel: [   26.435522] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Jul 22 17:09:56 hh-desktop kernel: [   26.435531] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Jul 22 17:09:56 hh-desktop kernel: [   26.435677] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
Jul 22 17:09:56 hh-desktop kernel: [   26.435774] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
Jul 22 17:09:56 hh-desktop kernel: [   26.435808] scsi0 : ata_piix
Jul 22 17:09:56 hh-desktop kernel: [   26.600108] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 17:09:56 hh-desktop kernel: [   26.600114] ata1.00: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
Jul 22 17:09:56 hh-desktop kernel: [   26.600118] ata1.00: 78165360 sectors, multi 16: LBA 
Jul 22 17:09:56 hh-desktop kernel: [   26.612138] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Jul 22 17:09:56 hh-desktop kernel: [   26.612147] ata1.00: configured for UDMA/100
Jul 22 17:09:56 hh-desktop kernel: [   26.612168] scsi1 : ata_piix
Jul 22 17:09:56 hh-desktop kernel: [   26.732962] Floppy drive(s): fd0 is 1.44M
Jul 22 17:09:56 hh-desktop kernel: [   26.754471] FDC 0 is a post-1991 82077
Jul 22 17:09:56 hh-desktop kernel: [   26.934789] ata2.00: ATAPI, max MWDMA2
Jul 22 17:09:56 hh-desktop kernel: [   27.098553] ata2.00: configured for MWDMA2
Jul 22 17:09:56 hh-desktop kernel: [   27.098772] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
Jul 22 17:09:56 hh-desktop kernel: [   27.100615] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-240B  R400 PQ: 0 ANSI: 5
Jul 22 17:09:56 hh-desktop kernel: [   27.106282] usb 1-1: new full speed USB device using uhci_hcd and address 3
Jul 22 17:09:56 hh-desktop kernel: [   27.292516] usb 1-1: configuration #1 chosen from 1 choice
Jul 22 17:09:56 hh-desktop kernel: [   27.725513] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 17:09:56 hh-desktop kernel: [   27.726476] sda: Write Protect is off
Jul 22 17:09:56 hh-desktop kernel: [   27.730441] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 17:09:56 hh-desktop kernel: [   27.734446] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Jul 22 17:09:56 hh-desktop kernel: [   27.737455] sda: Write Protect is off
Jul 22 17:09:56 hh-desktop kernel: [   27.741444] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 22 17:09:56 hh-desktop kernel: [   27.741452]  sda: sda1 sda2 < sda5 >
Jul 22 17:09:56 hh-desktop kernel: [   27.801501] sd 0:0:0:0: Attached scsi disk sda
Jul 22 17:09:56 hh-desktop kernel: [   27.809002] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 22 17:09:56 hh-desktop kernel: [   27.809041] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 22 17:09:56 hh-desktop kernel: [   27.813495] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jul 22 17:09:56 hh-desktop kernel: [   27.813503] Uniform CD-ROM driver Revision: 3.20
Jul 22 17:09:56 hh-desktop kernel: [   28.079227] usbcore: registered new interface driver hiddev
Jul 22 17:09:56 hh-desktop kernel: [   28.095436] input: Logitech USB Gaming Mouse as /class/input/input2
Jul 22 17:09:56 hh-desktop kernel: [   28.095482] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 17:09:56 hh-desktop kernel: [   28.101281] hiddev96: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1
Jul 22 17:09:56 hh-desktop kernel: [   28.101305] usbcore: registered new interface driver usbhid
Jul 22 17:09:56 hh-desktop kernel: [   28.101310] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul 22 17:09:56 hh-desktop kernel: [   29.751242] Attempting manual resume
Jul 22 17:09:56 hh-desktop kernel: [   30.378095] kjournald starting.  Commit interval 5 seconds
Jul 22 17:09:56 hh-desktop kernel: [   30.378123] EXT3-fs: mounted filesystem with ordered data mode.
Jul 22 17:09:56 hh-desktop kernel: [   53.228980] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 22 17:09:56 hh-desktop kernel: [   54.669131] NET: Registered protocol family 17
Jul 22 17:09:56 hh-desktop kernel: [   55.654992] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Jul 22 17:09:56 hh-desktop kernel: [   56.073371] Linux agpgart interface v0.102 (c) Dave Jones
Jul 22 17:09:56 hh-desktop kernel: [   56.119123] iTCO_vendor_support: vendor-support=0
Jul 22 17:09:56 hh-desktop kernel: [   56.120815] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Jul 22 17:09:56 hh-desktop kernel: [   56.120943] iTCO_wdt: No card detected
Jul 22 17:09:56 hh-desktop kernel: [   56.186025] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 22 17:09:56 hh-desktop kernel: [   56.189605] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 22 17:09:56 hh-desktop kernel: [   56.387069] agpgart: Detected an Intel 845G Chipset.
Jul 22 17:09:56 hh-desktop kernel: [   56.387208] agpgart: Detected 892K stolen memory.
Jul 22 17:09:56 hh-desktop kernel: [   56.405372] agpgart: AGP aperture is 128M @ 0xf0000000
Jul 22 17:09:56 hh-desktop kernel: [   56.748116] usbcore: registered new interface driver xpad
Jul 22 17:09:56 hh-desktop kernel: [   56.748123] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
Jul 22 17:09:56 hh-desktop kernel: [   57.050757] input: PC Speaker as /class/input/input3
Jul 22 17:09:56 hh-desktop kernel: [   57.059082] parport: PnPBIOS parport detected.
Jul 22 17:09:56 hh-desktop kernel: [   57.059140] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul 22 17:09:56 hh-desktop kernel: [   57.444822] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
Jul 22 17:09:56 hh-desktop kernel: [   57.758567] intel8x0_measure_ac97_clock: measured 55069 usecs
Jul 22 17:09:56 hh-desktop kernel: [   57.758573] intel8x0: clocking to 48000
Jul 22 17:09:56 hh-desktop kernel: [   58.015651] fuse init (API version 7.8)
Jul 22 17:09:56 hh-desktop kernel: [   58.050213] lp0: using parport0 (interrupt-driven).
Jul 22 17:09:56 hh-desktop kernel: [   58.114772] Adding 1646620k swap on /dev/disk/by-uuid/b35569b7-a093-4d4e-b5f8-cbe0e1cf4b6c.  Priority:-1 extents:1 across:1646620k
Jul 22 17:09:56 hh-desktop kernel: [   58.298405] EXT3 FS on sda1, internal journal
Jul 22 17:09:56 hh-desktop kernel: [   58.485454] NET: Registered protocol family 10
Jul 22 17:09:56 hh-desktop kernel: [   58.485650] lo: Disabled Privacy Extensions
Jul 22 17:09:56 hh-desktop kernel: [   64.628492] input: Power Button (FF) as /class/input/input4
Jul 22 17:09:56 hh-desktop kernel: [   64.636422] ACPI: Power Button (FF) [PWRF]
Jul 22 17:09:56 hh-desktop kernel: [   64.681083] input: Power Button (CM) as /class/input/input5
Jul 22 17:09:56 hh-desktop kernel: [   64.689079] ACPI: Power Button (CM) [PWRB]
Jul 22 17:09:56 hh-desktop kernel: [   64.750997] Using specific hotkey driver
Jul 22 17:09:56 hh-desktop kernel: [   65.011390] No dock devices found.
Jul 22 17:09:56 hh-desktop kernel: [   65.294480] pcc_acpi: loading...
Jul 22 17:09:59 hh-desktop dhcdbd: Started up.
Jul 22 17:10:00 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 17:10:00 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 22 17:10:01 hh-desktop kernel: [   71.628810] ppdev: user-space parallel port driver
Jul 22 17:10:01 hh-desktop kernel: [   72.286096] [drm] Initialized drm 1.1.0 20060810
Jul 22 17:10:01 hh-desktop kernel: [   72.319235] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 22 17:10:01 hh-desktop kernel: [   72.323934] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul 22 17:10:02 hh-desktop hpiod: 1.7.3 accepting connections at 2208... 
Jul 22 17:10:03 hh-desktop kernel: [   74.145882] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 22 17:10:03 hh-desktop kernel: [   74.145890] apm: overridden by ACPI.
Jul 22 17:10:04 hh-desktop kernel: [   74.455518] Bluetooth: Core ver 2.11
Jul 22 17:10:04 hh-desktop kernel: [   74.455641] NET: Registered protocol family 31
Jul 22 17:10:04 hh-desktop kernel: [   74.455646] Bluetooth: HCI device and connection manager initialized
Jul 22 17:10:04 hh-desktop kernel: [   74.455651] Bluetooth: HCI socket layer initialized
Jul 22 17:10:04 hh-desktop kernel: [   74.531524] Bluetooth: L2CAP ver 2.8
Jul 22 17:10:04 hh-desktop kernel: [   74.531532] Bluetooth: L2CAP socket layer initialized
Jul 22 17:10:04 hh-desktop kernel: [   74.600088] Bluetooth: RFCOMM socket layer initialized
Jul 22 17:10:04 hh-desktop kernel: [   74.600114] Bluetooth: RFCOMM TTY layer initialized
Jul 22 17:10:04 hh-desktop kernel: [   74.600117] Bluetooth: RFCOMM ver 1.8
Jul 22 17:10:05 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 22 17:10:05 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 22 17:10:05 hh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 22 17:10:18 hh-desktop gconfd (hh-5452): starting (version 2.18.0.1), pid 5452 user 'hh'
Jul 22 17:10:18 hh-desktop gconfd (hh-5452): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 22 17:10:18 hh-desktop gconfd (hh-5452): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 1
Jul 22 17:10:18 hh-desktop gconfd (hh-5452): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 17:10:18 hh-desktop gconfd (hh-5452): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 17:10:18 hh-desktop gconfd (hh-5452): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 17:10:28 hh-desktop gconfd (hh-5452): Resolved address "xml:readwrite:/home/hh/.gconf" to a writable configuration source at position 0

it said it was "doing wacom setup"??
and caught signal 15???
can someone help me?

---

### Post by upbeat.linux on 2007-07-24
Can you post your Xorg.0.log file? Do you have compiz or beryl installed and running on startup?

Try this in a failsafe terminal if you cannot get the "splash" screen:

```
rmmod wacom
modprobe wacom
```

---

