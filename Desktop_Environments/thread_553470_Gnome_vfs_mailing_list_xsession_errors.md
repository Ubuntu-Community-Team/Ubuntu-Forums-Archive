---
title: "Gnome vfs mailing list xsession errors"
date: 2007-09-17
forum: Desktop Environments
---

### Post by johnbl on 2007-09-17
My system is filing with zero length files /dev/ as it attempts boot, something that now takes 6 or 7 minutes.  The .xsession error log contains multiple entries along the lines of;

checking for valid crashreport now
** Message: Failed to write /home/john/Data/Client Web Sites/TheScooterShop/public_html/Scooter83.JPG to thumbnail pixbuf loader: Error interpreting JPEG image file (Unsupported marker type 0x6c)

followed by;

** (nautilus:5364): WARNING **: No description found for mime type "x-special/fifo" (file is "xconsole"), please tell the gnome-vfs mailing list.

** (nautilus:5364): WARNING **: No description found for mime type "x-special/device-char" (file is "tty"), please tell the gnome-vfs mailing list.

** (nautilus:5364): WARNING **: No description found for mime type "x-special/socket" (file is "log"), please tell the gnome-vfs mailing list.

** (nautilus:5364): WARNING **: No description found for mime type "x-special/device-block" (file is "sda1"), please tell the gnome-vfs mailing list.

Could the former mean that an old job, that failed is simply repeating repeating etc OR ??

The system on a couple of occasions simply hung with apparent dick thrash in that the HD was seeking / running but no buttons / key board would work. Only way to kill it was to pull the plug and battery!

Once started the system displays the following error message;

---------------------------

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in
-----------------------------

Then apparently works ok...

ifconfig shows 
-----------------------
eth0      Link encap:Ethernet  HWaddr 00:03:0D:28:4B:2D  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:165345381 (157.6 MiB)  TX bytes:7323193 (6.9 MiB)
          Interrupt:5 Base address:0x400 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:B8:FD:3E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xa000 Memory:ffbff000-ffbfffff 

----------------------------------------------
dmesg doesn't seem to have any obvious err messages, other than the apparent pause..

-----------------------------------------------------------

d: 000000003efd0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003efd0000 size: 000000000000f000 end: 000000003efdf000 type: 3
[    0.000000] copy_e820_map() start: 000000003efdf000 size: 0000000000021000 end: 000000003f000000 type: 4
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003efd0000 (usable)
[    0.000000]  BIOS-e820: 000000003efd0000 - 000000003efdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003efdf000 - 000000003f000000 (ACPI NVS)
[    0.000000] 111MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 258000) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   258000
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   258000
[    0.000000] On node 0 totalpages: 258000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 223 pages used for memmap
[    0.000000]   HighMem zone: 28401 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f6540
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x03000523 MSFT 0x00000097) @ 0x3efd0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x03000523 MSFT 0x00000097) @ 0x3efd0200
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x03000523 MSFT 0x00000097) @ 0x3efdf040
[    0.000000] ACPI: SSDT (v001    AMI   CPU1PM 0x00000001 INTL 0x02002026) @ 0x3efd3a80
[    0.000000] ACPI: DSDT (v001  1ABWG 1ABWG001 0x00000001 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f000000:c1000000)
[    0.000000] Detected 2000.156 MHz processor.
[    8.102252] Built 1 zonelists.  Total pages: 255985
[    8.102256] Kernel command line: root=UUID=3c40d6ed-5807-4662-a3bf-50cb661bea78 ro quiet splash
[    8.102403] Found and enabled local APIC!
[    8.102406] mapped APIC to ffffd000 (fee00000)
[    8.102410] Enabling fast FPU save and restore... done.
[    8.102413] Enabling unmasked SIMD FPU exception support... done.
[    8.102423] Initializing CPU#0
[    8.102498] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    8.103957] Console: colour VGA+ 80x25
[    8.104357] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.104822] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.136411] Memory: 1011944k/1032000k available (1993k kernel code, 19328k reserved, 900k data, 328k init, 114496k highmem)
[    8.136420] virtual kernel memory layout:
[    8.136420]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    8.136422]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.136423]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.136424]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.136425]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    8.136426]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[    8.136427]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[    8.136430] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.214293] Calibrating delay using timer specific routine.. 4002.66 BogoMIPS (lpj=8005320)
[    8.214330] Security Framework v1.0.0 initialized
[    8.214337] SELinux:  Disabled at boot.
[    8.214351] Mount-cache hash table entries: 512
[    8.214474] CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[    8.214485] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.214487] CPU: L2 cache: 2048K
[    8.214489] CPU: After all inits, caps: afe9fbbf 00000000 00000000 00002040 00000180 00000000 00000000
[    8.214497] Compat vDSO mapped to ffffe000.
[    8.214501] Remapping vsyscall page to ffffe000
[    8.214510] Checking 'hlt' instruction... OK.
[    8.230349] SMP alternatives: switching to UP code
[    8.230540] Freeing SMP alternatives: 11k freed
[    8.230698] Early unpacking initramfs... done
[    8.510406] ACPI: Core revision 20060707
[    8.511080] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    8.512425] ACPI: setting ELCR to 0200 (from 0e28)
[    8.581592] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 06
[    8.581597] SMP motherboard not detected.
[    8.689444] Brought up 1 CPUs
[    8.689659] Booting paravirtualized kernel on bare hardware
[    8.689724] Time: 21:26:52  Date: 08/17/107
[    8.689749] NET: Registered protocol family 16
[    8.689825] EISA bus registered
[    8.689828] ACPI: bus type pci registered
[    8.690885] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    8.690887] PCI: Using configuration type 1
[    8.690889] Setting up standard PCI resources
[    8.700909] ACPI: Interpreter enabled
[    8.700911] ACPI: Using PIC for interrupt routing
[    8.701183] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.701190] PCI: Probing PCI hardware (bus 00)
[    8.701450] Boot video device is 0000:00:02.0
[    8.701721] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    8.701724] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[    8.702029] PCI: Transparent bridge - 0000:00:1e.0
[    8.702072] PCI: Bus #02 (-#05) is hidden behind transparent bridge #01 (-#01) (try 'pci=assign-busses')
[    8.702075] Please report the result to linux-kernel to fix this permanently
[    8.702088] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.727763] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    8.734226] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    8.734491] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    8.734758] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    8.735020] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    8.735284] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.735546] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.735807] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.736070] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    8.736185] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.736192] pnp: PnP ACPI init
[    8.738062] pnp: PnP ACPI: found 10 devices
[    8.738067] PnPBIOS: Disabled by ACPI PNP
[    8.738104] PCI: Using ACPI for IRQ routing
[    8.738107] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.741442] NET: Registered protocol family 8
[    8.741444] NET: Registered protocol family 20
[    8.741926] pnp: 00:08: ioport range 0x1100-0x113f has been reserved
[    8.741929] pnp: 00:08: ioport range 0x1254-0x1254 has been reserved
[    8.741931] pnp: 00:08: ioport range 0x12d4-0x12d4 has been reserved
[    8.741933] pnp: 00:08: ioport range 0x1300-0x1375 has been reserved
[    8.741936] pnp: 00:08: ioport range 0x1377-0x137f has been reserved
[    8.742136] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    8.742148] PCI: Bus 2, cardbus bridge: 0000:01:03.0
[    8.742150]   IO window: 0000c000-0000c0ff
[    8.742153]   IO window: 0000c400-0000c4ff
[    8.742157]   PREFETCH window: 40000000-43ffffff
[    8.742161]   MEM window: 48000000-4bffffff
[    8.742164] PCI: Bridge: 0000:00:1e.0
[    8.742166]   IO window: c000-cfff
[    8.742171]   MEM window: ffb00000-ffbfffff
[    8.742175]   PREFETCH window: 40000000-43ffffff
[    8.742185] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.742367] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 3
[    8.742370] PCI: setting IRQ 3 as level-triggered
[    8.742373] ACPI: PCI Interrupt 0000:01:03.0[A] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[    8.742378] PCI: Setting latency timer of device 0000:01:03.0 to 64
[    8.742399] NET: Registered protocol family 2
[    8.781286] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.781384] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.782233] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.782837] TCP: Hash tables configured (established 131072 bind 65536)
[    8.782840] TCP reno registered
[    8.793368] checking if image is initramfs... it is
[    9.347274] Freeing initrd memory: 6767k freed
[    9.347716] audit: initializing netlink socket (disabled)
[    9.347733] audit(1190064412.260:1): initialized
[    9.347801] highmem bounce pool size: 64 pages
[    9.347861] VFS: Disk quotas dquot_6.5.1
[    9.347879] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.347931] io scheduler noop registered
[    9.347934] io scheduler anticipatory registered
[    9.347936] io scheduler deadline registered
[    9.347945] io scheduler cfq registered (default)
[    9.348256] isapnp: Scanning for PnP cards...
[    9.701326] isapnp: No Plug & Play device found
[    9.723042] Real Time Clock Driver v1.12ac
[    9.723092] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.723740] mice: PS/2 mouse device common for all mice
[    9.724228] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.724422] input: Macintosh mouse button emulation as /class/input/input0
[    9.724451] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.724454] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.724668] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.730644] i8042.c: Detected active multiplexing controller, rev 1.0.
[    9.731609] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.731613] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.731616] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.731618] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.731620] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.731733] EISA: Probing bus 0 at eisa.0
[    9.731775] EISA: Detected 0 cards.
[    9.761818] TCP cubic registered
[    9.761827] NET: Registered protocol family 1
[    9.761880] Testing NMI watchdog ... OK.
[    9.801515] Using IPI No-Shortcut mode
[    9.801565] ACPI: (supports S0 S3 S4 S5)
[    9.801604]   Magic number: 7:897:449
[    9.801927] Freeing unused kernel memory: 328k freed
[    9.802637] input: AT Translated Set 2 keyboard as /class/input/input1
[    9.803331] Time: tsc clocksource has been installed.
[   10.993905] Capability LSM initialized
[   11.022224] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.022229] ACPI: Processor [CPU1] (supports 8 throttling states)
[   11.022926] ACPI: Thermal Zone [THRM] (11 C)
[   11.320846] usbcore: registered new interface driver usbfs
[   11.320873] usbcore: registered new interface driver hub
[   11.320891] usbcore: registered new device driver usb
[   11.321597] USB Universal Host Controller Interface driver v3.0
[   11.321879] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   11.321882] PCI: setting IRQ 11 as level-triggered
[   11.321885] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.321896] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.321899] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.322056] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.322078] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000e480
[   11.322170] usb usb1: configuration #1 chosen from 1 choice
[   11.322189] hub 1-0:1.0: USB hub found
[   11.322194] hub 1-0:1.0: 2 ports detected
[   11.396175] ieee1394: Initialized config rom entry `ip1394'
[   11.405219] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   11.424707] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[   11.424711] PCI: setting IRQ 5 as level-triggered
[   11.424714] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   11.424725] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.424729] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.424749] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.424773] uhci_hcd 0000:00:1d.1: irq 5, io base 0x0000e800
[   11.424858] usb usb2: configuration #1 chosen from 1 choice
[   11.424879] hub 2-0:1.0: USB hub found
[   11.424885] hub 2-0:1.0: 2 ports detected
[   11.528473] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   11.528478] PCI: setting IRQ 9 as level-triggered
[   11.528481] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   11.528492] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.528495] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.528515] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.528536] uhci_hcd 0000:00:1d.2: irq 9, io base 0x0000e880
[   11.528619] usb usb3: configuration #1 chosen from 1 choice
[   11.528645] hub 3-0:1.0: USB hub found
[   11.528650] hub 3-0:1.0: 2 ports detected
[    3.304000] Time: acpi_pm clocksource has been installed.
[    3.368000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.368000] PCI: setting IRQ 10 as level-triggered
[    3.368000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.368000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.368000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.368000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.368000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.368000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.368000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xffdffc00
[    3.372000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.372000] usb usb4: configuration #1 chosen from 1 choice
[    3.372000] hub 4-0:1.0: USB hub found
[    3.372000] hub 4-0:1.0: 6 ports detected
[    3.480000] SCSI subsystem initialized
[    3.484000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[    3.532000] libata version 2.20 loaded.
[    3.536000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[ffbfe800-ffbfefff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.536000] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.536000] 8139cp 0000:01:0c.0: Try the "8139too" driver instead.
[    3.540000] 8139too Fast Ethernet driver 0.9.28
[    3.540000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[    3.540000] eth0: RealTek RTL8139 at 0xf88a0400, 00:03:0d:28:4b:2d, IRQ 5
[    3.540000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.540000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.540000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.540000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[    3.540000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.540000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    3.540000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    3.540000] scsi0 : ata_piix
[    3.704000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.704000] ata1.00: ATA-6: ST980829A, 3.04, max UDMA/100
[    3.704000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    3.712000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.712000] ata1.00: configured for UDMA/100
[    3.712000] scsi1 : ata_piix
[    4.188000] ata2.00: ATAPI, max UDMA/33
[    4.300000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.352000] ata2.00: configured for UDMA/33
[    4.352000] scsi 0:0:0:0: Direct-Access     ATA      ST980829A        3.04 PQ: 0 ANSI: 5
[    4.352000] scsi 1:0:0:0: CD-ROM            QSI      DVD+-RW SDW-082S LX06 PQ: 0 ANSI: 5
[    4.364000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.364000] sda: Write Protect is off
[    4.364000] sda: Mode Sense: 00 3a 00 00
[    4.364000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.364000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.364000] sda: Write Protect is off
[    4.364000] sda: Mode Sense: 00 3a 00 00
[    4.364000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.364000]  sda: sda1 sda2 < sda5 >
[    4.404000] sd 0:0:0:0: Attached scsi disk sda
[    4.408000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.408000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.416000] sr0: scsi3-mmc drive: 12x/24x writer cd/rw xa/form2 cdda tray
[    4.416000] Uniform CD-ROM driver Revision: 3.20
[    4.416000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.472000] usb 2-1: configuration #1 chosen from 1 choice
[    4.700000] Attempting manual resume
[    4.700000] swsusp: Resume From Partition 8:5
[    4.700000] PM: Checking swsusp image.
[    4.700000] PM: Resume from disk failed.
[    4.716000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    4.748000] kjournald starting.  Commit interval 5 seconds
[    4.748000] EXT3-fs: mounted filesystem with ordered data mode.
[    4.808000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d492230be1f]
[    4.868000] usb 3-2: configuration #1 chosen from 1 choice
[    4.872000] hub 3-2:1.0: USB hub found
[    4.872000] hub 3-2:1.0: 4 ports detected
[    5.188000] usb 3-2.4: new low speed USB device using uhci_hcd and address 3
[    5.328000] usb 3-2.4: configuration #1 chosen from 1 choice
[    5.332000] usbcore: registered new interface driver hiddev
[    5.352000] input: Logitech USB RECEIVER as /class/input/input2
[    5.352000] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.1-1
[    5.364000] input: Logitech USB Receiver as /class/input/input3
[    5.364000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2.4
[    5.396000] input: Logitech USB Receiver as /class/input/input4
[    5.396000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2.4
[    5.396000] usbcore: registered new interface driver usbhid
[    5.396000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   17.972000] intel_rng: FWH not detected
[   18.008000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.012000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.144000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.180000] iTCO_vendor_support: vendor-support=0
[   18.180000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   18.180000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0460)
[   18.180000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.352000] agpgart: Detected an Intel 855 Chipset.
[   18.352000] agpgart: Detected 16252K stolen memory.
[   18.360000] agpgart: AGP aperture is 128M @ 0xf0000000
[   18.752000] Yenta: CardBus bridge found at 0000:01:03.0 [1584:3200]
[   18.752000] Yenta: adjusting diagnostic: 40 -> 60
[   18.752000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   18.752000] Yenta: Routing CardBus interrupts to PCI
[   18.752000] Yenta TI: socket 0000:01:03.0, mfunc 0x000c1002, devctl 0x44
[   18.772000] input: PC Speaker as /class/input/input5
[   18.784000] usbcore: registered new interface driver lmpcm_usb
[   18.784000] ubuntu/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   18.824000] ieee80211_crypt: registered algorithm 'NULL'
[   18.828000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.828000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.984000] Yenta: ISA IRQ mask 0x00d0, PCI irq 3
[   18.984000] Socket status: 30000006
[   18.984000] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   18.984000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   18.984000] cs: IO port probe 0xc000-0xcfff: clean.
[   18.984000] pcmcia: parent PCI bridge Memory window: 0xffb00000 - 0xffbfffff
[   18.984000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   19.044000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   19.044000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.044000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   19.044000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.296000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   19.512000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x926eb1, caps: 0x804719/0x0
[   19.552000] input: SynPS/2 Synaptics TouchPad as /class/input/input6
[   19.648000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   19.648000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   19.756000] psmouse.c: Failed to reset mouse on isa0060/serio3
[   19.852000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[   19.852000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.856000] cs: IO port probe 0x820-0x8ff: clean.
[   19.856000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.856000] cs: IO port probe 0xa00-0xaff: clean.
[   20.916000] AC'97 1 does not respond - RESET
[   20.916000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   20.916000] Unable to initialize codec #1
[   20.972000] intel8x0_measure_ac97_clock: measured 55627 usecs
[   20.972000] intel8x0: clocking to 48000
[   29.156000] input: PS/2 Generic Mouse as /class/input/input7
[   29.356000] psmouse.c: Failed to enable mouse on isa0060/serio3
[   29.700000] fuse init (API version 7.8)
[   29.772000] lp: driver loaded but no devices found
[   29.892000] ACPI: PCI Interrupt 0000:00:1f.3[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   30.012000] Adding 2980016k swap on /dev/disk/by-uuid/a304571e-9f4a-4144-884a-96951ebea191.  Priority:-1 extents:1 across:2980016k
[   30.168000] EXT3 FS on sda1, internal journal
[   31.504000] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[   31.656000] input: Power Button (FF) as /class/input/input8
[   31.656000] ACPI: Power Button (FF) [PWRF]
[   31.688000] input: Lid Switch as /class/input/input9
[   31.688000] ACPI: Lid Switch [LID]
[   31.720000] input: Sleep Button (CM) as /class/input/input10
[   31.720000] ACPI: Sleep Button (CM) [SLPB]
[   31.752000] input: Power Button (CM) as /class/input/input11
[   31.752000] ACPI: Power Button (CM) [PWRB]
[   31.768000] ibm_acpi: ec object not found
[   31.800000] Using specific hotkey driver
[   31.840000] No dock devices found.
[   31.852000] ACPI: AC Adapter [AC0] (on-line)
[   31.880000] ACPI: Battery Slot [BAT0] (battery present)
[   31.920000] pcc_acpi: loading...
[   33.468000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   34.592000] [drm] Initialized drm 1.1.0 20060810
[   34.600000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   34.600000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   34.600000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   35.400000] ppdev: user-space parallel port driver
[   35.872000] NET: Registered protocol family 17
[   36.300000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   36.300000] apm: overridden by ACPI.
[  901.864000] eth0: link down
[  902.120000] usb 3-2.4: USB disconnect, address 3
[  902.220000] hub 3-2:1.0: hub_port_status failed (err = -71)
[  902.220000] hub 3-2:1.0: connect-debounce failed, port 4 disabled
[  902.220000] hub 3-2:1.0: cannot disable port 4 (err = -71)
[  902.504000] usb 3-2: USB disconnect, address 2
[  931.304000] usb 3-2: new full speed USB device using uhci_hcd and address 4
[  931.456000] usb 3-2: configuration #1 chosen from 1 choice
[  931.460000] hub 3-2:1.0: USB hub found
[  931.460000] hub 3-2:1.0: 4 ports detected
[  931.776000] usb 3-2.4: new low speed USB device using uhci_hcd and address 5
[  931.916000] usb 3-2.4: configuration #1 chosen from 1 choice
[  931.932000] input: Logitech USB Receiver as /class/input/input12
[  931.932000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-2.4
[  931.968000] input: Logitech USB Receiver as /class/input/input13
[  931.968000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2.4
[  932.372000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2823.984000] usb 3-2.3: new full speed USB device using uhci_hcd and address 6
[ 2824.084000] usb 3-2.3: not running at top speed; connect to a high speed hub
[ 2824.112000] usb 3-2.3: configuration #1 chosen from 1 choice
[ 2824.308000] usbcore: registered new interface driver libusual
[ 2824.320000] Initializing USB Mass Storage driver...
[ 2824.320000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2824.320000] usbcore: registered new interface driver usb-storage
[ 2824.320000] USB Mass Storage support registered.
[ 2824.320000] usb-storage: device found at 6
[ 2824.320000] usb-storage: waiting for device to settle before scanning
[ 2829.320000] usb-storage: device scan complete
[ 2829.324000] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer Crossfire 2.01 PQ: 0 ANSI: 2
[ 2829.336000] SCSI device sdb: 8026552 512-byte hdwr sectors (4110 MB)
[ 2829.344000] sdb: Write Protect is off
[ 2829.344000] sdb: Mode Sense: 03 00 00 00
[ 2829.344000] sdb: assuming drive cache: write through
[ 2829.368000] SCSI device sdb: 8026552 512-byte hdwr sectors (4110 MB)
[ 2829.372000] sdb: Write Protect is off
[ 2829.372000] sdb: Mode Sense: 03 00 00 00
[ 2829.372000] sdb: assuming drive cache: write through
[ 2829.372000]  sdb:
[ 2829.384000] sd 2:0:0:0: Attached scsi removable disk sdb
[ 2829.384000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 3659.548000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3659.548000] ata2.00: cmd a0/00:00:00:00:20/00:00:00:00:00/a0 tag 0 cdb 0x0 data 0 
[ 3659.548000]          res 58/00:01:00:00:20/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[ 3659.548000] ata2: soft resetting port
[ 3660.188000] ata2.00: configured for UDMA/33
[ 3660.188000] ata2: EH complete
[ 9398.940000] usb 3-2.3: USB disconnect, address 6

-----------------------------------------------

Being stumped any assistance would be great!

John

---

