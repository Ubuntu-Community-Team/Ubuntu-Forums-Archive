---
title: "Another USB Problem Post (Feisty Fawn)"
date: 2007-05-05
forum: Desktop Environments
---

### Post by JohnBoy55 on 2007-05-05
](*,)   I'll go ahead and add another post on the apparently wide-spread USB device mounting problems in Feisty Fawn. I'm running on an AMD Athlon(tm) XP 1800+ processor with 512 Gb ram. I was running previously on Edgy Eft. All USB devices worked beautifully there, including an Epson Scanner. Now, with Fawn, nothing USB works.

The following is my var/log/dmesg file contents
```
    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fff0000 size: 0000000000003000 end: 000000001fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000001fff3000 size: 000000000000d000 end: 0000000020000000 type: 3
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f7390
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff7700
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:6 APIC version 16
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
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:e0000000)
[    0.000000] Detected 1531.007 MHz processor.
[   31.507399] Built 1 zonelists.  Total pages: 130033
[   31.507403] Kernel command line: root=UUID=7af1fa5b-d814-4101-9003-042b83d91210 ro quiet splash
[   31.507609] mapped APIC to ffffd000 (fee00000)
[   31.507612] mapped IOAPIC to ffffc000 (fec00000)
[   31.507616] Enabling fast FPU save and restore... done.
[   31.507619] Enabling unmasked SIMD FPU exception support... done.
[   31.507631] Initializing CPU#0
[   31.507694] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   31.509161] Console: colour VGA+ 80x25
[   31.509500] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.509793] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.524281] Memory: 508480k/524224k available (1992k kernel code, 15184k reserved, 893k data, 328k init, 0k highmem)
[   31.524294] virtual kernel memory layout:
[   31.524295]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   31.524297]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   31.524299]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   31.524300]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   31.524302]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   31.524304]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   31.524305]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   31.524309] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.603584] Calibrating delay using timer specific routine.. 3064.60 BogoMIPS (lpj=6129216)
[   31.603635] Security Framework v1.0.0 initialized
[   31.603643] SELinux:  Disabled at boot.
[   31.603663] Mount-cache hash table entries: 512
[   31.603833] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[   31.603843] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   31.603847] CPU: L2 Cache: 256K (64 bytes/line)
[   31.603850] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[   31.603863] Compat vDSO mapped to ffffe000.
[   31.603869] Remapping vsyscall page to ffffe000
[   31.603880] Checking 'hlt' instruction... OK.
[   31.619704] SMP alternatives: switching to UP code
[   31.619995] Freeing SMP alternatives: 11k freed
[   31.620288] Early unpacking initramfs... done
[   32.015381] ACPI: Core revision 20060707
[   32.022290] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   32.026070] CPU0: AMD Athlon(tm) XP 1800+ stepping 02
[   32.026096] Total of 1 processors activated (3064.60 BogoMIPS).
[   32.026299] ENABLING IO-APIC IRQs
[   32.026497] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   32.170963] Brought up 1 CPUs
[   32.171267] Booting paravirtualized kernel on bare hardware
[   32.171353] Time: 11:28:26  Date: 04/05/107
[   32.171394] NET: Registered protocol family 16
[   32.171517] EISA bus registered
[   32.171523] ACPI: bus type pci registered
[   32.203724] PCI: PCI BIOS revision 2.10 entry at 0xfbbd0, last bus=2
[   32.203727] PCI: Using configuration type 1
[   32.203729] Setting up standard PCI resources
[   32.220017] ACPI: Interpreter enabled
[   32.220022] ACPI: Using IOAPIC for interrupt routing
[   32.220819] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   32.220824] PCI: Probing PCI hardware (bus 00)
[   32.221892] Boot video device is 0000:02:00.0
[   32.221945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   32.289174] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   32.289825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   32.291318] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   32.291730] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.292139] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.292546] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   32.292952] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.293361] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   32.293767] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   32.294177] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   32.294583] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.295001] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   32.295420] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.295829] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   32.296234] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   32.296646] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.297057] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.297465] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.297841] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[   32.298201] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[   32.298557] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[   32.298951] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[   32.299305] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   32.299765] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[   32.300231] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[   32.300683] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[   32.301141] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[   32.301596] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[   32.302049] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[   32.302404] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[   32.302890] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[   32.303341] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[   32.303795] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[   32.304244] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   32.307937] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.307952] pnp: PnP ACPI init
[   32.314903] pnp: PnP ACPI: found 15 devices
[   32.314909] PnPBIOS: Disabled by ACPI PNP
[   32.314977] PCI: Using ACPI for IRQ routing
[   32.314984] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   32.354967] NET: Registered protocol family 8
[   32.354970] NET: Registered protocol family 20
[   32.355749] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[   32.355754] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   32.355757] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   32.355761] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[   32.355765] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[   32.355768] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[   32.355776] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[   32.355780] pnp: 00:01: ioport range 0x5040-0x507f has been reserved
[   32.356153] PCI: Bridge: 0000:00:08.0
[   32.356157]   IO window: 9000-afff
[   32.356164]   MEM window: ee000000-eeffffff
[   32.356169]   PREFETCH window: 30000000-300fffff
[   32.356175] PCI: Bridge: 0000:00:1e.0
[   32.356176]   IO window: disabled.
[   32.356181]   MEM window: ec000000-edffffff
[   32.356186]   PREFETCH window: e0000000-e7ffffff
[   32.356199] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   32.356235] NET: Registered protocol family 2
[   32.394748] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   32.394860] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   32.395062] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   32.395165] TCP: Hash tables configured (established 16384 bind 8192)
[   32.395168] TCP reno registered
[   32.406788] checking if image is initramfs... it is
[   33.159882] Freeing initrd memory: 6998k freed
[   33.160459] audit: initializing netlink socket (disabled)
[   33.160477] audit(1178364507.732:1): initialized
[   33.160610] VFS: Disk quotas dquot_6.5.1
[   33.160635] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.160692] io scheduler noop registered
[   33.160695] io scheduler anticipatory registered
[   33.160698] io scheduler deadline registered
[   33.160708] io scheduler cfq registered (default)
[   33.213988] isapnp: Scanning for PnP cards...
[   33.568136] isapnp: No Plug & Play device found
[   33.605999] Real Time Clock Driver v1.12ac
[   33.606068] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.606216] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.606487] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.607282] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.607677] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.608021] mice: PS/2 mouse device common for all mice
[   33.608745] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.609045] input: Macintosh mouse button emulation as /class/input/input0
[   33.609086] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.609092] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.609414] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   33.612328] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.612336] serio: i8042 AUX port at 0x60,0x64 irq 12
[   33.612535] EISA: Probing bus 0 at eisa.0
[   33.612560] Cannot allocate resource for EISA slot 4
[   33.612563] Cannot allocate resource for EISA slot 5
[   33.612580] EISA: Detected 0 cards.
[   33.642654] TCP cubic registered
[   33.642662] NET: Registered protocol family 1
[   33.642692] Using IPI No-Shortcut mode
[   33.642764] ACPI: (supports S0 S1 S4 S5)
[   33.642825]   Magic number: 7:459:478
[   33.643448] Freeing unused kernel memory: 328k freed
[   33.645148] Time: tsc clocksource has been installed.
[   33.661064] input: AT Translated Set 2 keyboard as /class/input/input1
[   34.924986] Capability LSM initialized
[   34.969259] ACPI: Fan [FAN] (on)
[   34.976805] ACPI: Thermal Zone [THRM] (39 C)
[   35.621519] usbcore: registered new interface driver usbfs
[   35.621550] usbcore: registered new interface driver hub
[   35.621581] usbcore: registered new device driver usb
[   35.622556] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   35.623152] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   35.623163] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 16
[   35.623179] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   35.623183] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   35.623356] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   35.623381] ohci_hcd 0000:00:02.0: irq 16, io mem 0xef003000
[   35.647296] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   35.698160] SCSI subsystem initialized
[   35.704407] libata version 2.20 loaded.
[   35.718936] usb usb1: configuration #1 chosen from 1 choice
[   35.718975] hub 1-0:1.0: USB hub found
[   35.718990] hub 1-0:1.0: 3 ports detected
[   35.819359] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[   35.819373] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 17
[   35.819393] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   35.819397] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   35.819427] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   35.819450] ohci_hcd 0000:00:02.1: irq 17, io mem 0xef004000
[   35.856313] Floppy drive(s): fd0 is 1.44M
[   35.876715] usb usb2: configuration #1 chosen from 1 choice
[   35.876753] hub 2-0:1.0: USB hub found
[   35.876768] hub 2-0:1.0: 3 ports detected
[   35.925583] FDC 0 is a post-1991 82077
[   35.979229] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   35.979243] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 18
[   35.979258] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   35.979262] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   35.979294] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   35.979338] ehci_hcd 0000:00:02.2: debug port 1
[   35.979345] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   35.979358] ehci_hcd 0000:00:02.2: irq 18, io mem 0xef005000
[   35.979367] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   35.979461] usb usb3: configuration #1 chosen from 1 choice
[   35.979502] hub 3-0:1.0: USB hub found
[   35.979513] hub 3-0:1.0: 6 ports detected
[   36.083139] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   36.083147] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 16
[   36.083155] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   36.597962] eth0: forcedeth.c: subsystem: 01462:570c bound to 0000:00:04.0
[   36.604634] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[   36.604665] NFORCE2: chipset revision 162
[   36.604668] NFORCE2: not 100% native mode: will probe irqs later
[   36.604675] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   36.604683] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[   36.604695]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   36.604708]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   36.604718] Probing IDE interface ide0...
[   36.669643] usb 3-4: new high speed USB device using ehci_hcd and address 2
[   36.801962] usb 3-4: configuration #1 chosen from 1 choice
[   36.802141] hub 3-4:1.0: USB hub found
[   36.802231] hub 3-4:1.0: 4 ports detected
[   36.893483] hda: WDC WD400EB-00CPF0, ATA DISK drive
[   37.145067] usb 3-5: new high speed USB device using ehci_hcd and address 3
[   37.326893] usb 3-5: configuration #1 chosen from 1 choice
[   37.558311] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   37.560578] usb 3-6: new high speed USB device using ehci_hcd and address 4
[   37.577666] Probing IDE interface ide1...
[   37.694262] usb 3-6: configuration #1 chosen from 1 choice
[   37.694560] hub 3-6:1.0: USB hub found
[   37.694899] hub 3-6:1.0: 4 ports detected
[   37.996322] usb 3-6.2: new high speed USB device using ehci_hcd and address 5
[   38.090210] usb 3-6.2: configuration #1 chosen from 1 choice
[   38.288007] usb 3-6.3: new high speed USB device using ehci_hcd and address 6
[   38.311816] hdc: HL-DT-ST GCE-8527B, ATAPI CD/DVD-ROM drive
[   38.392001] usb 3-6.3: configuration #1 chosen from 1 choice
[   38.394307] usbcore: registered new interface driver libusual
[   38.399987] Initializing USB Mass Storage driver...
[   38.400116] scsi0 : SCSI emulation for USB Mass Storage devices
[   38.400182] usb-storage: device found at 5
[   38.400185] usb-storage: waiting for device to settle before scanning
[   38.400232] scsi1 : SCSI emulation for USB Mass Storage devices
[   38.400275] usb-storage: device found at 6
[   38.400278] usb-storage: waiting for device to settle before scanning
[   38.400288] usbcore: registered new interface driver usb-storage
[   38.400291] USB Mass Storage support registered.
[   39.090900] hdd: PLEXTOR DVDR PX-708A, ATAPI CD/DVD-ROM drive
[   39.187044] ide1 at 0x170-0x177,0x376 on irq 15
[   39.200922] CMD649: IDE controller at PCI slot 0000:01:07.0
[   39.201235] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   39.201246] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 19
[   39.201261] CMD649: chipset revision 2
[   39.201282] CMD649: 100% native mode on irq 19
[   39.201291]     ide2: BM-DMA at 0xa000-0xa007, BIOS settings: hde:pio, hdf:pio
[   39.201308]     ide3: BM-DMA at 0xa008-0xa00f, BIOS settings: hdg:pio, hdh:pio
[   39.201321] Probing IDE interface ide2...
[   39.218266] hda: max request size: 128KiB
[   39.296554] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   39.296564] hda: cache flushes not supported
[   39.296618]  hda: hda1 hda2 < hda5 >
[   39.358224] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[   39.358236] Uniform CD-ROM driver Revision: 3.20
[   39.359757] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   39.486604] hde: Maxtor 6Y080L0, ATA DISK drive
[   39.621159] Attempting manual resume
[   39.621164] swsusp: Resume From Partition 3:5
[   39.621166] PM: Checking swsusp image.
[   39.621347] PM: Resume from disk failed.
[   39.686786] kjournald starting.  Commit interval 5 seconds
[   39.686802] EXT3-fs: mounted filesystem with ordered data mode.
[   40.157728] ide2 at 0x9000-0x9007,0x9402 on irq 19
[   40.157814] hde: max request size: 128KiB
[   40.158422] hde: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   40.158570] hde: cache flushes supported
[   40.158621]  hde: hde1 hde2 < hde5 > hde3
[   40.195098] Probing IDE interface ide3...
[   40.481440] hdg: WDC WD2000JB-00GVA0, ATA DISK drive
[   41.149656] ide3 at 0x9800-0x9807,0x9c02 on irq 19
[   41.149747] hdg: max request size: 512KiB
[   41.164900] hdg: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[   41.166841] hdg: cache flushes supported
[   41.166886]  hdg: hdg1
[   43.369966] usb-storage: device scan complete
[   43.370101] usb-storage: device scan complete
[   43.370283] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.370649] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.370899] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.371147] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.371397] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.371400] hub 3-6:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[   43.371648] hub 3-6:1.0: cannot disable port 3 (err = -71)
[   43.371898] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.372146] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.372397] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.372647] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.372929] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.372932] hub 3-6:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[   43.373145] hub 3-6:1.0: cannot disable port 3 (err = -71)
[   43.373396] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.373644] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.373894] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.374145] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.374393] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.374396] hub 3-6:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[   43.374643] hub 3-6:1.0: cannot disable port 3 (err = -71)
[   43.374894] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.375145] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.375393] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.375643] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.375893] hub 3-6:1.0: cannot reset port 3 (err = -71)
[   43.375896] hub 3-6:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[   43.376141] hub 3-6:1.0: cannot disable port 3 (err = -71)
[   43.376392] hub 3-6:1.0: cannot disable port 3 (err = -71)
[   43.376645] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.376892] hub 3-6:1.0: hub_port_status failed (err = -71)
[   43.377141] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.377392] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.377642] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.377890] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.377893] hub 3-6:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   43.378141] hub 3-6:1.0: cannot disable port 2 (err = -71)
[   43.378391] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.378639] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.378890] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.379140] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.379388] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.379391] hub 3-6:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   43.379639] hub 3-6:1.0: cannot disable port 2 (err = -71)
[   43.379889] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.380137] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.380388] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.380639] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.380886] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.380889] hub 3-6:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   43.381137] hub 3-6:1.0: cannot disable port 2 (err = -71)
[   43.381388] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.381635] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.381887] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.382137] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.382384] hub 3-6:1.0: cannot reset port 2 (err = -71)
[   43.382387] hub 3-6:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   43.382635] hub 3-6:1.0: cannot disable port 2 (err = -71)
[   43.382886] hub 3-6:1.0: cannot disable port 2 (err = -71)
[   43.383138] hub 3-6:1.0: hub_port_status failed (err = -71)
[   43.383385] hub 3-6:1.0: hub_port_status failed (err = -71)
[   46.974722] usb 3-6.2: USB disconnect, address 5
[   46.974972] usb 3-6.3: USB disconnect, address 6
[   47.085388] usb 3-6: reset high speed USB device using ehci_hcd and address 4
[   47.197250] usb 3-6: device descriptor read/64, error -71
[   47.413000] usb 3-6: device descriptor read/64, error -71
[   47.628748] usb 3-6: reset high speed USB device using ehci_hcd and address 4
[   47.740628] usb 3-6: device descriptor read/64, error -71
[   47.956391] usb 3-6: device descriptor read/64, error -71
[   48.168127] usb 3-6: reset high speed USB device using ehci_hcd and address 4
[   48.571645] usb 3-6: device not accepting address 4, error -71
[   48.683542] usb 3-6: reset high speed USB device using ehci_hcd and address 4
[   49.087051] usb 3-6: device not accepting address 4, error -71
[   49.087079] hub 3-6:1.0: activate --> -19
[   49.190937] usb 3-6: USB disconnect, address 4
[   49.302802] usb 3-6: new high speed USB device using ehci_hcd and address 7
[   49.414680] usb 3-6: device descriptor read/64, error -71
[   49.630427] usb 3-6: device descriptor read/64, error -71
[   49.846168] usb 3-6: new high speed USB device using ehci_hcd and address 8
[   49.954042] usb 3-6: device descriptor read/64, error -71
[   50.169797] usb 3-6: device descriptor read/64, error -71
[   50.385531] usb 3-6: new high speed USB device using ehci_hcd and address 9
[   50.793043] usb 3-6: device not accepting address 9, error -71
[   50.904927] usb 3-6: new high speed USB device using ehci_hcd and address 10
[   51.312438] usb 3-6: device not accepting address 10, error -71
[   53.760803] NET: Registered protocol family 17
[   55.089271] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   55.092819] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   55.195129] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   55.195179] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5040
[   55.225016] input: PC Speaker as /class/input/input2
[   55.419160] Linux agpgart interface v0.102 (c) Dave Jones
[   55.656872] parport: PnPBIOS parport detected.
[   55.656937] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   55.668087] agpgart: Detected NVIDIA nForce2 chipset
[   55.673110] agpgart: AGP aperture is 64M @ 0xe8000000
[   55.736745] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   55.791191] nvidia: module license 'NVIDIA' taints kernel.
[   55.795508] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   55.795521] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 20
[   55.796010] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7184  Tue Aug  1 18:38:58 PDT 2006
[   56.484799] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[   56.484807] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 17
[   56.484840] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   56.801984] intel8x0_measure_ac97_clock: measured 54687 usecs
[   56.801989] intel8x0: clocking to 47439
[   57.004787] fuse init (API version 7.8)
[   57.041245] lp0: using parport0 (interrupt-driven).
[   57.274691] Adding 1502036k swap on /dev/disk/by-uuid/903007bd-4a5f-4f2d-9f53-8fb1eba1d9ce.  Priority:-1 extents:1 across:1502036k
[   57.546672] EXT3 FS on hda1, internal journal
[   57.803744] NET: Registered protocol family 10
[   57.803858] lo: Disabled Privacy Extensions
 
```

It is interesting that as soon as the 'usb-storage: device scan complete' occurs, the usb ports can no longer be reset or disabled.

I am using the default etc/fstab file, so no modifications have been made there. 

The results from the following commands are as follows

```

x@x-desktop:~$ lsusb
Bus 003 Device 002: ID 0409:005a NEC Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
x@x-desktop:~$ 

x@x-desktop:~$ sudo sane-find-scanner
Password:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
x@x-desktop:~$ 


```
 There really is an Epson 3490 scanner connected up to the computer. I also have no idea what the NEC corp device is. It shows up even when I disconnect all the usb devices and run the command. If anybody has any ideas, I would sure appreciate any help.

---

### Post by Stinger on 2007-05-06
It seems to be a kernel bug , somthing to do with the USB_SUSPEND option ,  but I dont understand how this kinda regression could pass into the final release of Feisty ???

You can read more about it here
[URL="http://82.211.81.186/showthread.php?t=389113"]
http://82.211.81.186/showthread.php?t=389113[/URL]

or here
[URL="http://82.211.81.186/showthread.php?t=414474"]
http://82.211.81.186/showthread.php?t=414474[/URL]

bugs are here

[COLOR="Red"][https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488]("https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488")[/COLOR]

here
[URL="https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/93515"]
https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/93515[/URL]

and here

[https://bugs.launchpad.net/ubuntu/+source/libusb/+bug/99802]("https://bugs.launchpad.net/ubuntu/+source/libusb/+bug/99802")

Kernelbug here
[URL="http://bugzilla.kernel.org/show_bug.cgi?id=8231"]
http://bugzilla.kernel.org/show_bug.cgi?id=8231[/URL]

Notice ! there seems to be a fix , now we can only wait until the developers decide to patch the current kernel.

[COLOR="Red"]As a temporarely workaround "scan button daemon" can be used
Read about it here[/COLOR]
[URL="https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/141"]
https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/141[/URL]

What a mess...

And if you take a look at this post it dosn't seem to be solved in Feisty at all......

[https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/180]("https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/180")

I simply dont know what to say...................

---

### Post by JohnBoy55 on 2007-05-07
:confused: I can't believe this! It isn't the fact that the scanner doesn't work that bothers me most. I use an mp3 player and several usb flash drives quite a bit. The fact that NO usb devices work is the biggest problem!

---

### Post by JohnBoy55 on 2007-05-09
Finally found a work-around for the issue. It seems that if you give it a swift kick, i.e. reload the driver, it will then work.
```
modprobe -r ehci_hcd
```

Running the above command gets the USB devices to work. It,s not pretty, but at least I can use the flash drives, MP3 player, and scanner. I just put a launcher containing the command on my desktop. Who knows, maybe they'll fix it eventually.

---

