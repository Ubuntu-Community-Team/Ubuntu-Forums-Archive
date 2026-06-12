---
title: "[SOLVED] Ubuntu 8.04.1, kernel 2.6.24-19-generic  stuck at clock"
date: 2008-07-03
forum: Desktop Environments
---

### Post by ramaswamyps on 2008-07-03
updated fully with adept updater from new install 8.04
the new kernel Ubuntu 8.04.1, kernel 2.6.24-19-generic
does not boot up.
it goes upto clock setting and stays there.
no error message.
even the recovery of the new kernel does same.
any body got same problem?
what is remedy?
i have posted dmesg for ref.

padoor ramaswamy # cat /mnt/hda9/var/log/dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fee0000 (usable)
[    0.000000]  BIOS-e820: 000000001fee0000 - 000000001fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fef0000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130784) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130784
[    0.000000]   HighMem    130784 ->   130784
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130784
[    0.000000] On node 0 totalpages: 130784
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125699 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
[    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
[    0.000000] ACPI: RSDT 1FEE0000, 002C (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: FACP 1FEE0054, 0084 (r2 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: DSDT 1FEE00D8, 6EF1 (r1 TOSHIB 9000     20020610 MSFT  100000A)
[    0.000000] ACPI: FACS 000EEE00, 0040
[    0.000000] ACPI: BOOT 1FEE002C, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0xee08
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000ee000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ee000 - 00000000000ef000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ef000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129763
[    0.000000] Kernel command line: root=UUID=84ed9228-5000-4825-9cb4-c230ef8ae89b ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0140d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 996.699 MHz processor.
[   17.216282] Console: colour VGA+ 80x25
[   17.216291] console [tty0] enabled
[   17.216766] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.217343] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.248457] Memory: 506276k/523136k available (2157k kernel code, 16304k reserved, 998k data, 364k init, 0k highmem)
[   17.248475] virtual kernel memory layout:
[   17.248478]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   17.248481]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.248484]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   17.248486]     lowmem  : 0xc0000000 - 0xdfee0000   ( 510 MB)
[   17.248489]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   17.248492]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   17.248495]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   17.248501] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.248569] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   17.328570] Calibrating delay using timer specific routine.. 1995.12 BogoMIPS (lpj=3990258)
[   17.328621] Security Framework initialized
[   17.328636] SELinux:  Disabled at boot.
[   17.328663] AppArmor: AppArmor initialized
[   17.328670] Failure registering capabilities with primary security module.
[   17.328687] Mount-cache hash table entries: 512
[   17.328910] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   17.328932] CPU: L1 I cache: 16K, L1 D cache: 16K
[   17.328937] CPU: L2 cache: 512K
[   17.328942] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   17.328960] Compat vDSO mapped to ffffe000.
[   17.328980] Checking 'hlt' instruction... OK.
[   17.345064] SMP alternatives: switching to UP code
[   17.347792] Freeing SMP alternatives: 11k freed
[   17.348001] Early unpacking initramfs... done
[   18.029391] ACPI: Core revision 20070126
[   18.029581] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.033854] ACPI: setting ELCR to 0200 (from 0a00)
[   18.034053] CPU0: Intel(R) Pentium(R) III Mobile CPU      1000MHz stepping 01
[   18.034065] SMP motherboard not detected.
[   18.034070] Local APIC not detected. Using dummy APIC emulation.
[   18.034169] Brought up 1 CPUs
[   18.034205] CPU0 attaching sched-domain:
[   18.034211]  domain 0: span 01
[   18.034215]   groups: 01
[   18.034615] net_namespace: 64 bytes
[   18.034629] Booting paravirtualized kernel on bare hardware
[   18.035848] Time: 20:16:58  Date: 07/02/08
[   18.035909] NET: Registered protocol family 16
[   18.036454] EISA bus registered
[   18.036477] ACPI: bus type pci registered
[   18.036861] PCI: PCI BIOS revision 2.10 entry at 0xfd772, last bus=5
[   18.036867] PCI: Using configuration type 1
[   18.036871] Setting up standard PCI resources
[   18.044720] ACPI: EC: Look up EC in DSDT
[   18.050591] ACPI: Interpreter enabled
[   18.050597] ACPI: (supports S0 S1 S3 S4 S5)
[   18.050627] ACPI: Using PIC for interrupt routing
[   18.062357] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.062716] PCI quirk: region ee00-ee7f claimed by ICH4 ACPI/GPIO/TCO
[   18.062723] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[   18.063303] PCI: Transparent bridge - 0000:00:1e.0
[   18.063554] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.063625] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   18.063765] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   18.070110] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[   18.070349] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12)
[   18.070589] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12)
[   18.070825] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12)
[   18.071061] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12)
[   18.071298] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12)
[   18.071534] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12)
[   18.071770] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12)
[   18.072149] ACPI: Power Resource [PFAN] (off)
[   18.072235] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.072303] pnp: PnP ACPI init
[   18.072337] ACPI: bus type pnp registered
[   18.082496] pnp: PnP ACPI: found 12 devices
[   18.082501] ACPI: ACPI bus type pnp unregistered
[   18.082508] PnPBIOS: Disabled by ACPI PNP
[   18.082992] PCI: Using ACPI for IRQ routing
[   18.082999] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.096340] NET: Registered protocol family 8
[   18.096344] NET: Registered protocol family 20
[   18.096481] AppArmor: AppArmor Filesystem Enabled
[   18.100304] Time: tsc clocksource has been installed.
[   18.108379] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   18.108386] system 00:00: iomem range 0xe0000-0xeffff could not be reserved
[   18.108393] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   18.108399] system 00:00: iomem range 0x100000-0x1fedffff could not be reserved
[   18.108405] system 00:00: iomem range 0x1fee0000-0x1feeffff could not be reserved
[   18.108412] system 00:00: iomem range 0x1fef0000-0x1ff7ffff could not be reserved
[   18.108418] system 00:00: iomem range 0x1ff80000-0x1fffffff could not be reserved
[   18.108425] system 00:00: iomem range 0xffb80000-0xffbfffff could not be reserved
[   18.108431] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[   18.108450] system 00:08: ioport range 0x480-0x48f has been reserved
[   18.108456] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   18.108462] system 00:08: ioport range 0x680-0x6ff has been reserved
[   18.108468] system 00:08: ioport range 0xe000-0xe07f has been reserved
[   18.108473] system 00:08: ioport range 0xe080-0xe0ff has been reserved
[   18.108479] system 00:08: ioport range 0xe400-0xe47f has been reserved
[   18.108485] system 00:08: ioport range 0xe480-0xe4ff has been reserved
[   18.108491] system 00:08: ioport range 0xe800-0xe87f has been reserved
[   18.108496] system 00:08: ioport range 0xe880-0xe8ff has been reserved
[   18.108502] system 00:08: ioport range 0xec00-0xec7f has been reserved
[   18.108508] system 00:08: ioport range 0xec80-0xecff has been reserved
[   18.108514] system 00:08: ioport range 0xee00-0xee87 could not be reserved
[   18.108520] system 00:08: ioport range 0xeeac-0xeeac has been reserved
[   18.108526] system 00:08: ioport range 0xeeb0-0xeebf has been reserved
[   18.108532] system 00:08: ioport range 0xeec0-0xeeff has been reserved
[   18.108537] system 00:08: ioport range 0xef00-0xef1f has been reserved
[   18.108543] system 00:08: ioport range 0xef20-0xef3f has been reserved
[   18.139422] PCI: Bridge: 0000:00:01.0
[   18.139426]   IO window: disabled.
[   18.139432]   MEM window: ffe00000-ffefffff
[   18.139437]   PREFETCH window: d6000000-dfffffff
[   18.139474] PCI: Bus 3, cardbus bridge: 0000:02:0a.0
[   18.139479]   IO window: 0000d000-0000d0ff
[   18.139485]   IO window: 0000d400-0000d4ff
[   18.139490]   PREFETCH window: 34000000-37ffffff
[   18.139496]   MEM window: 38000000-3bffffff
[   18.139502] PCI: Bus 5, cardbus bridge: 0000:02:0b.0
[   18.139506]   IO window: 0000d800-0000d8ff
[   18.139511]   IO window: 0000dc00-0000dcff
[   18.139517]   PREFETCH window: 3c000000-3fffffff
[   18.139523]   MEM window: 40000000-43ffffff
[   18.139529] PCI: Bus 9, cardbus bridge: 0000:02:0b.1
[   18.139533]   IO window: 00001c00-00001cff
[   18.139539]   IO window: 00002000-000020ff
[   18.139545]   PREFETCH window: 44000000-47ffffff
[   18.139551]   MEM window: 48000000-4bffffff
[   18.139556] PCI: Bridge: 0000:00:1e.0
[   18.139561]   IO window: d000-dfff
[   18.139567]   MEM window: ff900000-ff9fffff
[   18.139572]   PREFETCH window: disabled.
[   18.139591] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.139613] PCI: Enabling device 0000:02:0a.0 (0000 -> 0003)
[   18.140042] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[   18.140049] PCI: setting IRQ 11 as level-triggered
[   18.140054] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[   18.140077] PCI: Enabling device 0000:02:0b.0 (0000 -> 0003)
[   18.140451] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   18.140456] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   18.140479] PCI: Enabling device 0000:02:0b.1 (0000 -> 0003)
[   18.140841] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   18.140846] ACPI: PCI Interrupt 0000:02:0b.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   18.140877] NET: Registered protocol family 2
[   18.180438] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   18.180926] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   18.181185] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   18.181488] TCP: Hash tables configured (established 16384 bind 16384)
[   18.181493] TCP reno registered
[   18.192577] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   18.793535]  it is
[   19.498435] Freeing initrd memory: 7695k freed
[   19.498891] Simple Boot Flag at 0x7c set to 0x1
[   19.499631] audit: initializing netlink socket (disabled)
[   19.499663] audit(1215029819.252:1): initialized
[   19.504460] VFS: Disk quotas dquot_6.5.1
[   19.504654] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.504988] io scheduler noop registered
[   19.504994] io scheduler anticipatory registered
[   19.504998] io scheduler deadline registered
[   19.505028] io scheduler cfq registered (default)
[   19.505092] Boot video device is 0000:01:00.0
[   19.505104] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   19.505694] isapnp: Scanning for PnP cards...
[   19.858479] isapnp: No Plug & Play device found
[   19.921897] Real Time Clock Driver v1.12ac
[   19.922114] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.922281] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.923450] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.923782] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[   19.923799] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   19.923814] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   19.925147] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.925296] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.925511] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.931554] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.931565] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.943623] mice: PS/2 mouse device common for all mice
[   19.943854] EISA: Probing bus 0 at eisa.0
[   19.943866] Cannot allocate resource for EISA slot 1
[   19.943871] Cannot allocate resource for EISA slot 2
[   19.943893] EISA: Detected 0 cards.
[   19.943899] cpuidle: using governor ladder
[   19.943904] cpuidle: using governor menu
[   19.944210] NET: Registered protocol family 1
[   19.944272] Using IPI No-Shortcut mode
[   19.944338] registered taskstats version 1
[   19.944558]   Magic number: 0:995:294
[   19.944566]   hash matches device hpet
[   19.944587]   hash matches device ttyz8
[   19.944600]   hash matches device ttywb
[   19.944705]   hash matches device tty27
[   19.944752] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.944756] EDD information not available.
[   19.945206] Freeing unused kernel memory: 364k freed
[   19.971527] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   21.354086] fuse init (API version 7.9)
[   21.384281] ACPI: Transitioning device [FAN] to D3
[   21.384289] ACPI: Transitioning device [FAN] to D3
[   21.384296] ACPI: Fan [FAN] (off)
[   21.396311] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   21.399504] ACPI: Thermal Zone [THRM] (44 C)
[   22.914481] usbcore: registered new interface driver usbfs
[   22.914532] usbcore: registered new interface driver hub
[   22.938266] usbcore: registered new device driver usb
[   23.038021] SCSI subsystem initialized
[   23.058177] USB Universal Host Controller Interface driver v3.0
[   23.058312] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   23.058334] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.058342] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.058786] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.058823] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000efe0
[   23.059108] usb usb1: configuration #1 chosen from 1 choice
[   23.059158] hub 1-0:1.0: USB hub found
[   23.059171] hub 1-0:1.0: 2 ports detected
[   23.162822] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   23.162831] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   23.162854] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.162861] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.162913] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   23.162947] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000ef80
[   23.163173] usb usb2: configuration #1 chosen from 1 choice
[   23.163229] hub 2-0:1.0: USB hub found
[   23.163242] hub 2-0:1.0: 2 ports detected
[   23.266236] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
[   23.266730] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   23.266737] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   23.266757] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.266763] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.266813] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   23.266846] uhci_hcd 0000:00:1d.2: irq 11, io base 0x000018c0
[   23.267073] usb usb3: configuration #1 chosen from 1 choice
[   23.267122] hub 3-0:1.0: USB hub found
[   23.267134] hub 3-0:1.0: 2 ports detected
[   23.269196] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   23.269204] e100: Copyright(c) 1999-2006 Intel Corporation
[   23.278402] libata version 3.00 loaded.
[   23.370857] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   23.370867] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   23.395597] e100: eth0: e100_probe: addr 0xff9ff000, irq 11, MAC addr 00:00:39:70:d8:e2
[   23.395661] PCI: Enabling device 0000:02:07.0 (0000 -> 0002)
[   23.396132] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[   23.396139] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[   23.445993] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[ff907000-ff9077ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   23.446042] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   23.562023] ata_piix 0000:00:1f.1: version 2.12
[   23.562062] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   23.562132] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.569266] scsi0 : ata_piix
[   23.581985] scsi1 : ata_piix
[   23.583466] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xcfa0 irq 14
[   23.583473] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xcfa8 irq 15
[   23.627776] usb 1-2: configuration #1 chosen from 1 choice
[   23.746310] ata1.00: ATA-6: ST980815A, 3.ALD, max UDMA/100
[   23.746320] ata1.00: 156301488 sectors, multi 0: LBA48
[   23.762299] ata1.00: configured for UDMA/100
[   24.082014] ata2.00: ATAPI: DW-224E-C, F.8A, max UDMA/33
[   24.253873] ata2.00: configured for UDMA/33
[   24.254130] scsi 0:0:0:0: Direct-Access     ATA      ST980815A        3.AL PQ: 0 ANSI: 5
[   24.256243] scsi 1:0:0:0: CD-ROM            TEAC     DW-224E-C        F.8A PQ: 0 ANSI: 5
[   24.399267] Driver 'sd' needs updating - please use bus_type methods
[   24.402202] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.402235] sd 0:0:0:0: [sda] Write Protect is off
[   24.402241] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.402285] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.402386] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.402411] sd 0:0:0:0: [sda] Write Protect is off
[   24.402416] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.402457] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.402466]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.420851]  sda1 sda2 <<6>usbcore: registered new interface driver hiddev
[   24.432664]  sda5 sda6 sda7<6>input: Microsoft Microsoft USB Wireless Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
[   24.436465]  sda8 sda9 sda10 >
[   24.438263] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.450249] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:1d.0-2
[   24.450288] usbcore: registered new interface driver usbhid
[   24.450296] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.455268] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.455318] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   24.457268] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   24.457280] Uniform CD-ROM driver Revision: 3.20
[   24.457379] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.633461] Clocksource tsc unstable (delta = -202441434 ns)
[   24.637429] Time: acpi_pm clocksource has been installed.
[   24.669326] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00003900001c367e]
[   24.724519] Attempting manual resume
[   24.724527] swsusp: Resume From Partition 8:8
[   24.724531] PM: Checking swsusp image.
[   24.724906] PM: Resume from disk failed.
[   24.768766] kjournald starting.  Commit interval 5 seconds
[   24.768792] EXT3-fs: mounted filesystem with ordered data mode.
[   28.912330] Linux agpgart interface v0.102
[   28.971130] agpgart: Detected an Intel 830M Chipset.
[   29.032317] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.128180] agpgart: AGP aperture is 256M @ 0xe0000000
[   29.128261] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.635961] intel_rng: FWH not detected
[   30.022922] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   30.111777] iTCO_vendor_support: vendor-support=0
[   30.183786] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.184017] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0xee60)
[   30.184095] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.993055] input: Power Button (FF) as /devices/virtual/input/input4
[   31.003396] ACPI: Power Button (FF) [PWRF]
[   31.003572] input: Lid Switch as /devices/virtual/input/input5
[   31.003703] ACPI: Lid Switch [LID]
[   31.112933] ACPI: AC Adapter [ADP1] (on-line)
[   31.363754] ACPI: Battery Slot [BAT1] (battery present)
[   31.363847] ACPI: Battery Slot [BAT2] (battery absent)
[   33.900113] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/LNXVIDEO:00/input/input6
[   33.928823] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   34.921666] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[   34.921683] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   34.921710] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   35.493258] intel8x0_measure_ac97_clock: measured 55408 usecs
[   35.493267] intel8x0: clocking to 48000
[   35.495425] Yenta: CardBus bridge found at 0000:02:0a.0 [12a3:ab01]
[   35.495447] Yenta: Enabling burst memory read transactions
[   35.495453] Yenta: Using CSCINT to route CSC interrupts to PCI
[   35.495457] Yenta: Routing CardBus interrupts to PCI
[   35.495464] Yenta TI: socket 0000:02:0a.0, mfunc 0x01000002, devctl 0x60
[   35.725838] Yenta: ISA IRQ mask 0x0000, PCI irq 11
[   35.725847] Socket status: 30000011
[   35.725856] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   35.725862] cs: IO port probe 0xd000-0xdfff: clean.
[   35.726279] pcmcia: parent PCI bridge Memory window: 0xff900000 - 0xff9fffff
[   35.773462] Yenta: CardBus bridge found at 0000:02:0b.0 [1179:0001]
[   35.901874] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   35.901882] Socket status: 30000007
[   35.901888] Yenta: Raising subordinate bus# of parent bus (#02) from #05 to #08
[   35.901899] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   35.901906] cs: IO port probe 0xd000-0xdfff: clean.
[   35.902322] pcmcia: parent PCI bridge Memory window: 0xff900000 - 0xff9fffff
[   35.955861] Yenta: CardBus bridge found at 0000:02:0b.1 [1179:0001]
[   36.081685] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   36.081693] Socket status: 30000007
[   36.081698] Yenta: Raising subordinate bus# of parent bus (#02) from #08 to #0c
[   36.081710] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   36.081717] cs: IO port probe 0xd000-0xdfff: clean.
[   36.082132] pcmcia: parent PCI bridge Memory window: 0xff900000 - 0xff9fffff
[   36.408846] pccard: PCMCIA card inserted into slot 0
[   37.291643] irda_init()
[   37.291680] NET: Registered protocol family 23
[   37.303436] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   37.350756] Detected unconfigured Toshiba laptop with Intel 82801CAM ISA bridge SMSC IrDA chip, pre-configuring device.
[   37.350767] Setting up Intel 82801 controller and SMSC device
[   37.350787] Detected Chip id: 0x5a, setting up registers...
[   37.350882] found SMC SuperIO Chip (devid=0x5a rev=00 base=0x002e): LPC47N227
[   37.350889] smsc_superio_flat(): IrDA not enabled
[   37.350904] smsc_superio_flat(): fir: 0x130, sir: 0x3f8, dma: 03, irq: 3, mode: 0x02
[   37.350914] smsc_ircc_present: can't get sir_base of 0x3f8
[   37.366552] parport_pc 00:0b: activated
[   37.366561] parport_pc 00:0b: reported by Plug and Play ACPI
[   37.366929] parport_pc 00:0b: disabled
[   40.191137] cs: memory probe 0xff900000-0xff9fffff: excluding 0xff900000-0xff90ffff 0xff9f0000-0xff9fffff
[   40.198648] pcmcia: registering new device pcmcia0.0
[   40.602596] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   40.608662] cs: IO port probe 0x100-0x3af: excluding 0x130-0x137
[   40.609587] cs: IO port probe 0x3e0-0x4ff: clean.
[   40.609982] cs: IO port probe 0x820-0x8ff: clean.
[   40.610343] cs: IO port probe 0xc00-0xcf7: clean.
[   40.610949] cs: IO port probe 0xa00-0xaff: clean.
[   40.616931] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   40.619133] cs: IO port probe 0x100-0x3af: excluding 0x130-0x137
[   40.620107] cs: IO port probe 0x3e0-0x4ff: clean.
[   40.620501] cs: IO port probe 0x820-0x8ff: clean.
[   40.620863] cs: IO port probe 0xc00-0xcf7: clean.
[   40.621470] cs: IO port probe 0xa00-0xaff: clean.
[   40.623259] cs: IO port probe 0x100-0x3af: excluding 0x130-0x137
[   40.624185] cs: IO port probe 0x3e0-0x4ff: clean.
[   40.624580] cs: IO port probe 0x820-0x8ff: clean.
[   40.624943] cs: IO port probe 0xc00-0xcf7: clean.
[   40.625551] cs: IO port probe 0xa00-0xaff: clean.
[   40.626200] pcmcia: request for exclusive IRQ could not be fulfilled.
[   40.626205] pcmcia: the driver needs updating to supported shared IRQ lines.
[   40.708325] eth1: Hardware identity 0005:0002:0001:0002
[   40.708442] eth1: Station identity  001f:0001:0006:000e
[   40.708449] eth1: Firmware determined as Lucent/Agere 6.14
[   40.708453] eth1: Ad-hoc demo mode supported
[   40.708457] eth1: IEEE standard IBSS ad-hoc mode supported
[   40.708460] eth1: WEP supported, 104-bit key
[   40.708540] eth1: MAC address 00:02:2d:34:c0:5f
[   40.708634] eth1: Station name "HERMES I"
[   40.709172] eth1: ready
[   40.710088] eth1: orinoco_cs at 0.0, irq 11, io 0xd100-0xd13f
[   40.906984] lp: driver loaded but no devices found
[   41.003281] Adding 1405648k swap on /dev/sda8.  Priority:-1 extents:1 across:1405648k
[   41.148257] EXT3 FS on sda9, internal journal
[   41.265387] device-mapper: uevent: version 1.0.3
[   41.265446] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   42.139590] ip_tables: (C) 2000-2006 Netfilter Core Team
padoor ramaswamy #

[B][B]after waiting for 10 minutes it drops me into (iniramfs) shell

can anybody suggest how to get back old boot atleast short of reinstall[/B][/B]

---

### Post by ramaswamyps on 2008-07-04
i reinstalled after backing up the apt/archives
it updates ok with new kernel.
the problem was because after i installed kubuntu-desktop the adept has installed kernel for ubuntu .
now it works ok

for installing kde we should run aptitude install kde
then suitable ubuntu packages installed.

this may help some one.

---

