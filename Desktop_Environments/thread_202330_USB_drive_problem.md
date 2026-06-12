---
title: "USB drive problem"
date: 2006-06-23
forum: Desktop Environments
---

### Post by trucker_jim3000 on 2006-06-23
Hi, I wonder if anyone knows a fix for this:

If I plug in a USB flash drive, or an external USB hard drive the following happens:

1) I get a relevant icon appear on the desktop
2) A window opens up displaying the contents of the drive
3) After a few seconds the window reverts to my home folder and the icon disappears

This happens in a loop until I unplug the device. 

I've searched the internet for the solution but can't find anyone else who is having this problem...

BTW, Ubuntu is great, this is the only problem I have found on my system.

---

### Post by trucker_jim3000 on 2006-06-23
Hi, I have a DMESG report on this issue

Any pointers would be much appreciated!


*****************************************************************************


[17179569.184000] Detected 2075.430 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.460000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.460000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179569.476000] Memory: 508852k/524224k available (1976k kernel code, 14800k reserved, 606k data, 288k init, 0k highmem)
[17179569.476000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.556000] Calibrating delay using timer specific routine.. 4153.59 BogoMIPS (lpj=8307182)
[17179569.556000] Security Framework v1.0.0 initialized
[17179569.556000] SELinux:  Disabled at boot.
[17179569.556000] Mount-cache hash table entries: 512
[17179569.556000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.556000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.556000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.556000] CPU: L2 Cache: 256K (64 bytes/line)
[17179569.556000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179569.556000] mtrr: v2.0 (20020519)
[17179569.556000] CPU: AMD Athlon(tm) XP 2600+ stepping 01
[17179569.556000] Enabling fast FPU save and restore... done.
[17179569.556000] Enabling unmasked SIMD FPU exception support... done.
[17179569.556000] Checking 'hlt' instruction... OK.
[17179569.572000] checking if image is initramfs... it is
[17179570.076000] Freeing initrd memory: 6613k freed
[17179570.092000] ACPI: Looking for DSDT ... not found!
[17179570.116000] ENABLING IO-APIC IRQs
[17179570.116000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.260000] NET: Registered protocol family 16
[17179570.260000] EISA bus registered
[17179570.260000] ACPI: bus type pci registered
[17179570.264000] PCI: PCI BIOS revision 2.10 entry at 0xfb3c0, last bus=1
[17179570.264000] PCI: Using configuration type 1
[17179570.264000] ACPI: Subsystem revision 20051216
[17179570.272000] ACPI: Interpreter enabled
[17179570.272000] ACPI: Using IOAPIC for interrupt routing
[17179570.272000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.272000] PCI: Probing PCI hardware (bus 00)
[17179570.272000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.276000] PCI quirk: region 4000-407f claimed by vt8235 PM
[17179570.276000] PCI quirk: region 5000-500f claimed by vt8235 SMB
[17179570.276000] Boot video device is 0000:01:00.0
[17179570.276000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.304000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179570.304000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179570.304000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[17179570.304000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[17179570.304000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.304000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.304000] ACPI: PCI Interrupt Link [LNK0] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.304000] ACPI: PCI Interrupt Link [LNK1] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.304000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179570.304000] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[17179570.304000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[17179570.304000] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[17179570.308000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.308000] pnp: PnP ACPI init
[17179570.312000] pnp: PnP ACPI: found 15 devices
[17179570.312000] PnPBIOS: Disabled by ACPI PNP
[17179570.312000] PCI: Using ACPI for IRQ routing
[17179570.312000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.336000] pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
[17179570.336000] pnp: 00:01: ioport range 0x5000-0x500f has been reserved
[17179570.336000] PCI: Bridge: 0000:00:01.0
[17179570.336000]   IO window: disabled.
[17179570.336000]   MEM window: e8000000-e9ffffff
[17179570.336000]   PREFETCH window: e4000000-e7ffffff
[17179570.336000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.336000] audit: initializing netlink socket (disabled)
[17179570.336000] audit(1151068382.336:1): initialized
[17179570.336000] VFS: Disk quotas dquot_6.5.1
[17179570.336000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.336000] Initializing Cryptographic API
[17179570.336000] io scheduler noop registered
[17179570.336000] io scheduler anticipatory registered
[17179570.336000] io scheduler deadline registered
[17179570.336000] io scheduler cfq registered
[17179570.336000] isapnp: Scanning for PnP cards...
[17179570.692000] isapnp: No Plug & Play device found
[17179570.704000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.704000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.704000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.704000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.704000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.704000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.704000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.704000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.704000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.704000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.704000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.704000] mice: PS/2 mouse device common for all mice
[17179570.704000] EISA: Probing bus 0 at eisa.0
[17179570.704000] Cannot allocate resource for EISA slot 4
[17179570.704000] Cannot allocate resource for EISA slot 5
[17179570.704000] EISA: Detected 0 cards.
[17179570.704000] NET: Registered protocol family 2
[17179570.732000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.744000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179570.744000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.744000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.744000] TCP: Hash tables configured (established 32768 bind 32768)
[17179570.744000] TCP reno registered
[17179570.744000] TCP bic registered
[17179570.744000] NET: Registered protocol family 1
[17179570.744000] NET: Registered protocol family 8
[17179570.744000] NET: Registered protocol family 20
[17179570.744000] Using IPI Shortcut mode
[17179570.744000] ACPI wakeup devices:
[17179570.744000] SLPB PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 LAN0 MC97 UAR1 LPT1
[17179570.744000] ACPI: (supports S0 S1 S4 S5)
[17179570.744000] Freeing unused kernel memory: 288k freed
[17179570.784000] vga16fb: initializing
[17179570.784000] vga16fb: mapped to 0xc00a0000
[17179570.924000] Console: switching to colour frame buffer device 80x25
[17179570.924000] fb0: VGA16 VGA frame buffer device
[17179571.936000] Capability LSM initialized
[17179572.060000] ACPI: Fan [FAN] (on)
[17179572.064000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.064000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179572.064000]     ACPI-0351: *** Error: Looking up [RTMP] in namespace, AE_NOT_FOUND
[17179572.064000]     ACPI-0517: *** Error: Method parse/execution failed [\_TZ_.THRM._TMP] (Node dffda680), AE_NOT_FOUND
[17179572.588000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179572.588000] **** SET: Misaligned resource pointer: dfc880c2 Type 07 Len 0
[17179572.588000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[17179572.588000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179572.588000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 169
[17179572.588000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 9
[17179572.588000] VP_IDE: chipset revision 6
[17179572.588000] VP_IDE: not 100% native mode: will probe irqs later
[17179572.588000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179572.588000]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:DMA
[17179572.588000]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:DMA
[17179572.588000] Probing IDE interface ide0...
[17179573.004000] hda: ST320410A, ATA DISK drive
[17179573.452000] hdb: TSSTcorpCD/DVDW TS-H552U, ATAPI CD/DVD-ROM drive
[17179573.512000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.516000] Probing IDE interface ide1...
[17179573.932000] hdc: ST320014A, ATA DISK drive
[17179574.380000] hdd: MSI CD-RW MS-8348, ATAPI CD/DVD-ROM drive
[17179574.500000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.508000] hda: max request size: 128KiB
[17179574.524000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[17179574.524000] hda: cache flushes not supported
[17179574.524000]  hda: hda1 hda2 < hda5 >
[17179574.596000] hdc: max request size: 128KiB
[17179574.596000] hdc: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[17179574.600000] hdb: ATAPI 63X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.600000] Uniform CD-ROM driver Revision: 3.20
[17179574.632000] hdc: cache flushes supported
[17179574.632000]  hdc: hdc1
[17179574.680000] hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.964000] usbcore: registered new driver usbfs
[17179574.964000] usbcore: registered new driver hub
[17179574.968000] USB Universal Host Controller Interface driver v2.3
[17179574.968000] **** SET: Misaligned resource pointer: dfb12d02 Type 07 Len 0
[17179574.968000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[17179574.968000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179574.968000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179574.968000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 1
[17179574.968000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179574.968000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179574.968000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000c800
[17179574.968000] hub 1-0:1.0: USB hub found
[17179574.968000] hub 1-0:1.0: 2 ports detected
[17179575.072000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.072000] PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 1
[17179575.072000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179575.072000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179575.072000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000cc00
[17179575.072000] hub 2-0:1.0: USB hub found
[17179575.072000] hub 2-0:1.0: 2 ports detected
[17179575.176000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.176000] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 1
[17179575.176000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179575.176000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179575.176000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000d000
[17179575.176000] hub 3-0:1.0: USB hub found
[17179575.176000] hub 3-0:1.0: 2 ports detected
[17179575.280000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179575.280000] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 1
[17179575.280000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179575.280000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179575.280000] ehci_hcd 0000:00:10.3: irq 177, io mem 0xea001000
[17179575.280000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.280000] hub 4-0:1.0: USB hub found
[17179575.280000] hub 4-0:1.0: 6 ports detected
[17179575.480000] Attempting manual resume
[17179575.496000] kjournald starting.  Commit interval 5 seconds
[17179575.496000] EXT3-fs: mounted filesystem with ordered data mode.
[17179587.228000] hub 4-0:1.0: over-current change on port 1
[17179587.332000] hub 4-0:1.0: over-current change on port 2
[17179587.984000] hub 4-0:1.0: over-current change on port 1
[17179588.088000] hub 4-0:1.0: over-current change on port 2
[17179588.236000] hub 4-0:1.0: over-current change on port 1
[17179588.340000] hub 4-0:1.0: over-current change on port 2
[17179588.740000] hub 4-0:1.0: over-current change on port 1
[17179588.844000] hub 4-0:1.0: over-current change on port 2
[17179589.128000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.140000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.180000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.244000] hub 4-0:1.0: over-current change on port 1
[17179589.260000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[17179589.264000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179589.308000] 8139too Fast Ethernet driver 0.9.27
[17179589.308000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 19 (level, low) -> IRQ 185
[17179589.308000] eth0: RealTek RTL8139 at 0xe0884000, 00:10:b5:93:d6:8c, IRQ 185
[17179589.308000] eth0:  Identified 8139 chip type 'RTL-8139A'
[17179589.348000] hub 4-0:1.0: over-current change on port 2
[17179589.376000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 193
[17179589.496000] hub 4-0:1.0: over-current change on port 1
[17179589.592000] Real Time Clock Driver v1.12
[17179589.656000] nvidia: module license 'NVIDIA' taints kernel.
[17179589.704000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179589.748000] hub 4-0:1.0: over-current change on port 1
[17179589.780000] irda_init()
[17179589.780000] NET: Registered protocol family 23
[17179589.800000] input: PC Speaker as /class/input/input1
[17179589.852000] hub 4-0:1.0: over-current change on port 2
[17179589.892000] FDC 0 is a post-1991 82077
[17179589.904000] parport: PnPBIOS parport detected.
[17179589.904000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179590.252000] hub 4-0:1.0: over-current change on port 1
[17179590.356000] hub 4-0:1.0: over-current change on port 2
[17179590.524000] **** SET: Misaligned resource pointer: da9c87e2 Type 07 Len 0
[17179590.524000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[17179590.524000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[17179590.524000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 201
[17179590.524000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 9
[17179590.528000] eth1: VIA Rhine II at 0x1e000, 00:50:70:63:19:f7, IRQ 201.
[17179590.528000] eth1: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179590.532000] **** SET: Misaligned resource pointer: da9c87e2 Type 07 Len 0
[17179590.532000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179590.532000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179590.532000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 209
[17179590.532000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 1
[17179590.532000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179590.560000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179590.588000] ts: Compaq touchscreen protocol output
[17179590.752000] eth0: link down
[17179591.056000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 217
[17179591.056000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179591.356000] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179591.792000] NET: Registered protocol family 17
[17179592.776000] lp0: using parport0 (interrupt-driven).
[17179592.832000] Adding 835340k swap on /dev/hda5.  Priority:-1 extents:1 across:835340k
[17179592.976000] EXT3 FS on hda1, internal journal
[17179593.116000] NET: Registered protocol family 10
[17179593.116000] lo: Disabled Privacy Extensions
[17179593.116000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179593.116000] IPv6 over IPv4 tunneling driver
[17179593.172000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.172000] md: bitmap version 4.39
[17179593.736000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179597.556000] cdrom: open failed.
[17179598.064000] hub 4-0:1.0: over-current change on port 1
[17179598.168000] hub 4-0:1.0: over-current change on port 2
[17179599.576000] hub 4-0:1.0: over-current change on port 1
[17179599.828000] hub 4-0:1.0: over-current change on port 1
[17179599.932000] hub 4-0:1.0: over-current change on port 2
[17179600.836000] hub 4-0:1.0: over-current change on port 1
[17179600.940000] hub 4-0:1.0: over-current change on port 2
[17179602.772000] ACPI: Power Button (FF) [PWRF]
[17179602.772000] ACPI: Power Button (CM) [PWRB]
[17179602.772000] ACPI: Sleep Button (CM) [SLPB]
[17179602.852000] hub 4-0:1.0: over-current change on port 1
[17179602.872000] ibm_acpi: ec object not found
[17179602.900000] pcc_acpi: loading...
[17179603.436000] eth1: no IPv6 routers present
[17179605.624000] hub 4-0:1.0: over-current change on port 1
[17179605.728000] hub 4-0:1.0: over-current change on port 2
[17179608.264000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179608.264000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179608.264000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179609.820000] ppdev: user-space parallel port driver
[17179610.168000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179610.168000] apm: overridden by ACPI.
[17179610.664000] hub 4-0:1.0: over-current change on port 1
[17179610.916000] hub 4-0:1.0: over-current change on port 1
[17179611.168000] hub 4-0:1.0: over-current change on port 1
[17179611.272000] hub 4-0:1.0: over-current change on port 2
[17179611.672000] hub 4-0:1.0: over-current change on port 1
[17179611.776000] hub 4-0:1.0: over-current change on port 2
[17179612.932000] hub 4-0:1.0: over-current change on port 1
[17179613.820000] Bluetooth: Core ver 2.8
[17179613.820000] NET: Registered protocol family 31
[17179613.820000] Bluetooth: HCI device and connection manager initialized
[17179613.820000] Bluetooth: HCI socket layer initialized
[17179613.868000] Bluetooth: L2CAP ver 2.8
[17179613.868000] Bluetooth: L2CAP socket layer initialized
[17179613.920000] Bluetooth: RFCOMM socket layer initialized
[17179613.920000] Bluetooth: RFCOMM TTY layer initialized
[17179613.920000] Bluetooth: RFCOMM ver 1.7
[17179614.192000] hub 4-0:1.0: over-current change on port 1
[17179615.200000] hub 4-0:1.0: over-current change on port 1
[17179615.452000] hub 4-0:1.0: over-current change on port 1
[17179615.556000] hub 4-0:1.0: over-current change on port 2
[17179615.956000] hub 4-0:1.0: over-current change on port 1
[17179616.060000] hub 4-0:1.0: over-current change on port 2
[17179624.524000] hub 4-0:1.0: over-current change on port 1
[17179624.628000] hub 4-0:1.0: over-current change on port 2
[17179628.304000] hub 4-0:1.0: over-current change on port 1
[17179632.004000] UDF-fs: No VRS found
[17179632.696000] UDF-fs: No VRS found
[17179633.520000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179633.548000] ISOFS: changing to secondary root
[17179638.888000] hub 4-0:1.0: over-current change on port 1
[17179639.140000] hub 4-0:1.0: over-current change on port 1
[17179639.392000] hub 4-0:1.0: over-current change on port 1
[17179639.496000] hub 4-0:1.0: over-current change on port 2
[17179639.896000] hub 4-0:1.0: over-current change on port 1
[17179640.000000] hub 4-0:1.0: over-current change on port 2
[17179662.576000] hub 4-0:1.0: over-current change on port 1
[17179698.600000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[17179698.920000] SCSI subsystem initialized
[17179698.944000] Initializing USB Mass Storage driver...
[17179698.948000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179698.948000] usb-storage: device found at 2
[17179698.948000] usb-storage: waiting for device to settle before scanning
[17179698.948000] usbcore: registered new driver usb-storage
[17179698.948000] USB Mass Storage support registered.
[17179703.956000]   Vendor:           Model: USB Flash Memory  Rev: 1.00
[17179703.956000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179703.968000] usb-storage: device scan complete
[17179704.000000] Driver 'sd' needs updating - please use bus_type methods
[17179704.008000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17179704.008000] sda: Write Protect is off
[17179704.008000] sda: Mode Sense: 0b 00 00 08
[17179704.008000] sda: assuming drive cache: write through
[17179704.028000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17179704.032000] sda: Write Protect is off
[17179704.032000] sda: Mode Sense: 0b 00 00 08
[17179704.032000] sda: assuming drive cache: write through
[17179704.032000]  sda: sda1
[17179704.032000] sd 0:0:0:0: Attached scsi removable disk sda
[17179704.100000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179704.488000] usb 4-1: USB disconnect, address 2
[17179704.488000]  0:0:0:0: rejecting I/O to dead device
[17179704.488000]  0:0:0:0: rejecting I/O to dead device
[17179704.488000]  0:0:0:0: rejecting I/O to dead device
[17179704.488000]  0:0:0:0: rejecting I/O to dead device
[17179704.488000] sda : READ CAPACITY failed.
[17179704.488000] sda : status=0, message=00, host=1, driver=00
[17179704.488000] sda : sense not available.
[17179704.488000]  0:0:0:0: rejecting I/O to dead device
[17179704.488000] sda: Write Protect is off
[17179704.488000] sda: Mode Sense: 00 00 00 00
[17179704.488000] sda: assuming drive cache: write through
[17179704.488000]  0:0:0:0: rejecting I/O to dead device
[17179704.488000]  0:0:0:0: rejecting I/O to dead device
[17179704.488000]  0:0:0:0: rejecting I/O to dead device
[17179704.488000]  0:0:0:0: rejecting I/O to dead device
[17179704.488000] sda : READ CAPACITY failed.
[17179704.488000] sda : status=0, message=00, host=1, driver=00
[17179704.488000] sda : sense not available.
[17179704.488000]  0:0:0:0: rejecting I/O to dead device
[17179704.488000] sda: Write Protect is off
[17179704.488000] sda: Mode Sense: 00 00 00 00
[17179704.488000] sda: assuming drive cache: write through
[17179704.492000]  sda:<3> 0:0:0:0: rejecting I/O to dead device
[17179704.492000] Buffer I/O error on device sda, logical block 0
[17179704.492000]  0:0:0:0: rejecting I/O to dead device
[17179704.492000] Buffer I/O error on device sda, logical block 0
[17179704.492000]  unable to read partition table
[17179779.504000] hub 4-0:1.0: over-current change on port 1
[17179860.396000] hub 4-0:1.0: over-current change on port 1
[17179864.428000] hub 4-0:1.0: over-current change on port 1
[17179867.956000] hub 4-0:1.0: over-current change on port 1
[17179870.476000] hub 4-0:1.0: over-current change on port 1
[17179871.736000] hub 4-0:1.0: over-current change on port 1
[17179871.840000] hub 4-0:1.0: over-current change on port 2
[17179925.916000] hub 4-0:1.0: over-current change on port 1
[17179926.020000] hub 4-0:1.0: over-current change on port 2
[17179952.628000] hub 4-0:1.0: over-current change on port 1
[17179952.732000] hub 4-0:1.0: over-current change on port 2
[17179952.880000] hub 4-0:1.0: over-current change on port 1
[17179952.984000] hub 4-0:1.0: over-current change on port 2
[17179953.132000] hub 4-0:1.0: over-current change on port 1
[17179953.384000] hub 4-0:1.0: over-current change on port 1
[17179953.488000] hub 4-0:1.0: over-current change on port 2
[17179953.636000] hub 4-0:1.0: over-current change on port 1
[17179953.740000] hub 4-0:1.0: over-current change on port 2
[17179965.732000] hub 4-0:1.0: over-current change on port 1
[17179965.836000] hub 4-0:1.0: over-current change on port 2
[17179976.820000] hub 4-0:1.0: over-current change on port 1
[17179976.924000] hub 4-0:1.0: over-current change on port 2
[17180060.484000] hub 4-0:1.0: over-current change on port 1
[17180060.588000] hub 4-0:1.0: over-current change on port 2
[17180083.416000] hub 4-0:1.0: over-current change on port 1
[17180112.396000] hub 4-0:1.0: over-current change on port 1
[17180112.648000] hub 4-0:1.0: over-current change on port 1
[17180112.752000] hub 4-0:1.0: over-current change on port 2
[17180112.900000] hub 4-0:1.0: over-current change on port 1
[17180124.996000] hub 4-0:1.0: over-current change on port 1
[17180125.100000] hub 4-0:1.0: over-current change on port 2
[17180138.352000] hub 4-0:1.0: over-current change on port 1
[17180141.880000] hub 4-0:1.0: over-current change on port 1
[17180142.132000] hub 4-0:1.0: over-current change on port 1
[17180143.644000] hub 4-0:1.0: over-current change on port 1
[17180149.944000] hub 4-0:1.0: over-current change on port 1
[17180152.716000] hub 4-0:1.0: over-current change on port 1
[17180152.820000] hub 4-0:1.0: over-current change on port 2
[17180250.240000] hub 4-0:1.0: over-current change on port 1
[17180250.344000] hub 4-0:1.0: over-current change on port 2
[17180259.312000] hub 4-0:1.0: over-current change on port 1
[17180259.416000] hub 4-0:1.0: over-current change on port 2
[17180262.588000] hub 4-0:1.0: over-current change on port 1
[17180262.692000] hub 4-0:1.0: over-current change on port 2
[17180266.368000] hub 4-0:1.0: over-current change on port 1
[17180266.472000] hub 4-0:1.0: over-current change on port 2
[17180266.620000] hub 4-0:1.0: over-current change on port 1
[17180266.724000] hub 4-0:1.0: over-current change on port 2
[17180277.456000] hub 4-0:1.0: over-current change on port 1
[17180277.708000] hub 4-0:1.0: over-current change on port 1
[17180277.812000] hub 4-0:1.0: over-current change on port 2
[17180277.960000] hub 4-0:1.0: over-current change on port 1
[17180278.064000] hub 4-0:1.0: over-current change on port 2
[17180286.276000] hub 4-0:1.0: over-current change on port 1
[17180286.380000] hub 4-0:1.0: over-current change on port 2
[17180287.788000] hub 4-0:1.0: over-current change on port 1
[17180288.040000] hub 4-0:1.0: over-current change on port 1
[17180288.292000] hub 4-0:1.0: over-current change on port 1
[17180288.396000] hub 4-0:1.0: over-current change on port 2
[17180288.544000] hub 4-0:1.0: over-current change on port 1
[17180288.796000] hub 4-0:1.0: over-current change on port 1
[17180288.900000] hub 4-0:1.0: over-current change on port 2
[17180301.900000] hub 4-0:1.0: over-current change on port 1
[17180302.004000] hub 4-0:1.0: over-current change on port 2
[17180302.152000] hub 4-0:1.0: over-current change on port 1
[17180306.940000] hub 4-0:1.0: over-current change on port 1
[17180307.044000] hub 4-0:1.0: over-current change on port 2
[17180321.304000] hub 4-0:1.0: over-current change on port 1
[17180322.312000] hub 4-0:1.0: over-current change on port 1
[17180322.416000] hub 4-0:1.0: over-current change on port 2
[17180333.904000] hub 4-0:1.0: over-current change on port 1
[17180334.008000] hub 4-0:1.0: over-current change on port 2
[17180346.252000] hub 4-0:1.0: over-current change on port 1
[17180346.356000] hub 4-0:1.0: over-current change on port 2
[17180348.268000] hub 4-0:1.0: over-current change on port 1
[17180348.372000] hub 4-0:1.0: over-current change on port 2
[17180350.788000] hub 4-0:1.0: over-current change on port 1
[17180355.072000] hub 4-0:1.0: over-current change on port 1
[17180355.176000] hub 4-0:1.0: over-current change on port 2


******************************************************************************

---

### Post by ifokkema on 2006-06-23
Your USB ports (1&2) are already throwing error messages right while booting. Since there is a glitch in two of your ports, connecting your drives on those fail.

I'm not experienced enough with this to state it's a hardware issue, but it does look like it in my opinion. Try connecting your drives to your other USB ports. If you have a different OS on the same machine, try the ports on that OS to rule out Ubuntu driver problems.

---

### Post by trucker_jim3000 on 2006-06-24
Both drives work fine in an XP boot, so I think the USB ports are ok.

---

### Post by ifokkema on 2006-06-24
[QUOTE=trucker_jim3000]Both drives work fine in an XP boot, so I think the USB ports are ok.[/QUOTE]
OK, did you try your USB devices on different ports on you system? In the dmesg, there are just two ports throwing errors all the time, but you seem to have more that are OK. If you attach your device to one of those working ports, it should have no interruption from your ports continuously failing.

---

### Post by trucker_jim3000 on 2006-06-24
Yes, I tried the same ports in XP that I was trying in ubuntu, both of them responded normally when in XP..

Very mysterious. I wonder if it's a matter of compatibility with ubuntu and my motherboard chipset. The motherboard's outdated by todays standards....an Athlon Socket A with a Via chipset....?

---

### Post by ifokkema on 2006-06-24
I got an Athlon with Via chipset right here as well, but that's running fine (Breezy, though).
If you've tried all USB ports on Ubuntu to no avail, I'm afraid I'm lost as well. But Google shows some 435 hits on "over-current change on port". There may be some help [there]("http://www.google.com/search?hl=nl&q=%22over-current+change+on+port%22&btnG=Google+zoeken&meta=")?

---

