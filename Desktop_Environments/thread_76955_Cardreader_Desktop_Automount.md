---
title: "Cardreader Desktop Automount"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Aphorism on 2005-10-16
Ok... this appears to be happening across TWO of my home desktops running the current Ubuntu 5.10.  It also happened with 5.04.

**SYMPTOM**:  Desktop case cardreader officially listed via Gnome's Places->Computer.  Once the kernel is adjusted via Synaptic Package Manager, and upon reboot, it is completely gone.

**CASES**:  
[LIST]
[*]amd64 box with MSI-RS480M2 board and an Athlon-64 3000+ in an Antec Aria case with built in card reader.  Initial install of Ubuntu amd64 5.10 resulted in both the CF and SD card reader appearing.  After a twiddle of kernel via Synaptic, they are now both gone.  Can't seem to get either back through various rebooting / rekerneling.

[*]i386 box with ASUS A7N9X-VM board and AthlonXP 2500+ in an Antec Aria case with built in card reader.  Initial install of Ubuntu i386 5.04 resulted in card reader working for the CF slot, but failed for the SD side.  Kernel tweak in 5.04 and poof -- gone.  Further still, after an install of 5.10, the card reader fails to show up.
[/LIST]

BOTH systems have IDENTICAL cases, and BOTH card readers have worked at various times.  Does anyone have any clues on how to detect the damn card readers and why Gnome *used* to automount the damn cards but now fails.

Thanks to anyone and everyone who helps...

Here is the 64 bit dmesg:

**amd64 box**
```
 low level)
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 3bf00000 (gap: 3bf00000:a4100000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 58c2000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hda1 ro no_timer_check quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 1790.874 MHz processor.
[   15.807063] time.c: Using PIT/TSC based timekeeping.
[   15.808728] Console: colour VGA+ 80x25
[   15.809514] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.810474] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   15.824926] Memory: 957488k/981952k available (1620k kernel code, 23684k reserved, 997k data, 136k init)
[   15.824972] Calibrating delay loop... 3522.56 BogoMIPS (lpj=1761280)
[   15.845081] Security Framework v1.0.0 initialized
[   15.845085] SELinux:  Disabled at boot.
[   15.845094] Mount-cache hash table entries: 256
[   15.845158] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.845161] CPU: L2 Cache: 512K (64 bytes/line)
[   15.845165] CPU: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[   15.845256] checking if image is initramfs... it is
[   16.250324] ACPI: Looking for DSDT in initrd... not found!
[   16.342874]  not found!
[   16.355143] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   16.355165]  failed.
[   16.355167] timer doesn't work through the IO-APIC - disabling NMI Watchdog!
[   16.355872] Uhhuh. NMI received for unknown reason 3d.
[   16.355875] Dazed and confused, but trying to continue
[   16.355877] Do you have a strange power saving mode enabled?
[   16.365006]  works.
[   16.365008] Using local APIC timer interrupts.
[   16.420871] Detected 12.436 MHz APIC timer.
[   16.420885] testing NMI watchdog ... CPU#0: NMI appears to be stuck (1->1)!
[   16.430898] NET: Registered protocol family 16
[   16.430916] ACPI: bus type pci registered
[   16.430922] PCI: Using configuration type 1
[   16.430925] mtrr: v2.0 (20020519)
[   16.431201] ACPI: Subsystem revision 20050729
[   16.443427] ACPI: Interpreter enabled
[   16.443429] ACPI: Using IOAPIC for interrupt routing
[   16.443857] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.443860] PCI: Probing PCI hardware (bus 00)
[   16.443921] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[   16.443925] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   16.445695] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[   16.445956] Boot video device is 0000:01:05.0
[   16.446238] PCI: Transparent bridge - 0000:00:14.4
[   16.462879] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.463500] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   16.463692] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   16.463882] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   16.464071] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   16.464272] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11)
[   16.464460] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11)
[   16.464649] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11), disabled.
[   16.464837] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *10 11)
[   16.465118] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   16.466955] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   16.467133] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.467139] pnp: PnP ACPI init
[   16.469770] pnp: PnP ACPI: found 13 devices
[   16.469835] usbcore: registered new driver usbfs
[   16.469854] usbcore: registered new driver hub
[   16.469881] PCI: Using ACPI for IRQ routing
[   16.469885] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.469894] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   16.469984] PCI-DMA: Disabling IOMMU.
[   16.470415] pnp: 00:00: ioport range 0x228-0x22f has been reserved
[   16.470419] pnp: 00:00: ioport range 0x40b-0x40b has been reserved
[   16.470422] pnp: 00:00: ioport range 0x4d6-0x4d6 has been reserved
[   16.470425] pnp: 00:00: ioport range 0xc00-0xc01 has been reserved
[   16.470429] pnp: 00:00: ioport range 0xc14-0xc14 has been reserved
[   16.470432] pnp: 00:00: ioport range 0xc50-0xc52 has been reserved
[   16.470435] pnp: 00:00: ioport range 0xc6c-0xc6d has been reserved
[   16.470439] pnp: 00:00: ioport range 0xc6f-0xc6f has been reserved
[   16.470686] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   16.470852] audit: initializing netlink socket (disabled)
[   16.470859] audit: initialized
[   16.470943] VFS: Disk quotas dquot_6.5.1
[   16.470957] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.470980] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   16.470985] devfs: boot_options: 0x0
[   16.471009] Initializing Cryptographic API
[   16.485970] Linux agpgart interface v0.101 (c) Dave Jones
[   16.486034] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.031035] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.031620] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.031625] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   17.031803] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.033392] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.033463] io scheduler noop registered
[   17.033474] io scheduler anticipatory registered
[   17.033479] io scheduler deadline registered
[   17.033486] io scheduler cfq registered
[   17.033751] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.033803] NET: Registered protocol family 2
[   17.056332] IP: routing cache hash table of 8192 buckets, 64Kbytes
[   17.056466] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.057362] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.057652] TCP: Hash tables configured (established 131072 bind 65536)
[   17.057717] NET: Registered protocol family 8
[   17.057719] NET: Registered protocol family 20
[   17.059245] ACPI wakeup devices: 
[   17.059248] PCI0 USB0 USB1 USB2 AUDO  P2P  MAC 
[   17.059252] ACPI: (supports S0 S1 S3 S4bios S5)
[   17.059399] Freeing unused kernel memory: 136k freed
[   17.092873] input: AT Translated Set 2 keyboard on isa0060/serio0
[   17.097498] vga16fb: initializing
[   17.097501] vga16fb: mapped to 0xffff8100000a0000
[   17.188032] Console: switching to colour frame buffer device 80x30
[   17.188036] fb0: VGA16 VGA frame buffer device
[   18.298970] Capability LSM initialized
[   18.307338] NET: Registered protocol family 1
[   18.315597] SCSI subsystem initialized
[   18.316652] libata version 1.11 loaded.
[   18.317818] sata_sil version 0.9
[   18.317838] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 23
[   18.317890] ata1: SATA max UDMA/100 cmd 0xFFFFC2000003A080 ctl 0xFFFFC2000003A08A bmdma 0xFFFFC2000003A000 irq 23
[   18.317912] ata2: SATA max UDMA/100 cmd 0xFFFFC2000003A0C0 ctl 0xFFFFC2000003A0CA bmdma 0xFFFFC2000003A008 irq 23
[   18.518575] ata1: no device found (phy stat 00000000)
[   18.518578] scsi0 : sata_sil
[   18.719615] ata2: no device found (phy stat 00000000)
[   18.719617] scsi1 : sata_sil
[   18.720361] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   18.720393] ata3: SATA max UDMA/100 cmd 0xFFFFC2000003C080 ctl 0xFFFFC2000003C08A bmdma 0xFFFFC2000003C000 irq 22
[   18.720414] ata4: SATA max UDMA/100 cmd 0xFFFFC2000003C0C0 ctl 0xFFFFC2000003C0CA bmdma 0xFFFFC2000003C008 irq 22
[   18.920653] ata3: no device found (phy stat 00000000)
[   18.920655] scsi2 : sata_sil
[   19.121692] ata4: no device found (phy stat 00000000)
[   19.121695] scsi3 : sata_sil
[   19.135634] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.135644] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.135647] ACPI: bus type ide registered
[   19.141852] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   19.141871] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   19.141882] ATIIXP: chipset revision 0
[   19.141884] ATIIXP: not 100% native mode: will probe irqs later
[   19.141894]     ide0: BM-DMA at 0xf300-0xf307, BIOS settings: hda:pio, hdb:pio
[   19.141908]     ide1: BM-DMA at 0xf308-0xf30f, BIOS settings: hdc:pio, hdd:pio
[   19.141916] Probing IDE interface ide0...
[   19.406169] hda: Maxtor 6Y120P0, ATA DISK drive
[   19.814247] hdb: HL-DT-ST GCE-8525B, ATAPI CD/DVD-ROM drive
[   19.865026] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   19.865102] Probing IDE interface ide1...
[   20.383964] Probing IDE interface ide1...
[   20.902033] Probing IDE interface ide2...
[   21.414132] Probing IDE interface ide3...
[   21.926232] Probing IDE interface ide4...
[   22.438331] Probing IDE interface ide5...
[   22.953447] hda: max request size: 128KiB
[   22.967635] hda: 240121728 sectors (122942 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(100)
[   22.967762] hda: cache flushes supported
[   22.967811]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[   23.000020] hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[   23.000026] Uniform CD-ROM driver Revision: 3.20
[   23.216845] Attempting manual resume
[   23.220594] swsusp: Suspend partition has wrong signature?
[   23.242678] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   23.242719] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   23.242736] ohci_hcd 0000:00:13.0: PCI device 1002:4374 (ATI Technologies Inc)
[   23.265605] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   23.265615] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02d000
[   23.320531] hub 1-0:1.0: USB hub found
[   23.320543] hub 1-0:1.0: 4 ports detected
[   23.325519] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   23.325530] ohci_hcd 0000:00:13.1: PCI device 1002:4375 (ATI Technologies Inc)
[   23.348537] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   23.348542] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02c000
[   23.403534] hub 2-0:1.0: USB hub found
[   23.403545] hub 2-0:1.0: 4 ports detected
[   23.417779] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   23.417794] ehci_hcd 0000:00:13.2: PCI device 1002:4373 (ATI Technologies Inc)
[   23.417845] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   23.417853] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02b000
[   23.417896] ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   23.417961] hub 3-0:1.0: USB hub found
[   23.417967] hub 3-0:1.0: 8 ports detected
[   23.485427] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   23.485455] 8139cp: pci dev 0000:02:03.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   23.485458] 8139cp: Try the "8139too" driver instead.
[   23.486796] 8139too Fast Ethernet driver 0.9.27
[   23.486840] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   23.487475] eth0: RealTek RTL8139 at 0xffffc20000048000, 00:13:d3:21:50:72, IRQ 20
[   23.487478] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   23.711582] usb 3-7: new high speed USB device using ehci_hcd and address 2
[   25.821286] ACPI: CPU0 (power states: C1[C1])
[   25.821291] ACPI: Processor [CPU0] (supports 8 throttling states)
[   25.963402] Attempting manual resume
[   25.963558] swsusp: Suspend partition has wrong signature?
[   25.982153] kjournald starting.  Commit interval 5 seconds
[   25.982161] EXT3-fs: mounted filesystem with ordered data mode.
[   26.774249] usb 3-7: device descriptor read/64, error -110
[   27.008790] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   29.959983] Adding 2803300k swap on /dev/hda5.  Priority:-1 extents:1
[   30.222048] EXT3 FS on hda1, internal journal
[   36.040932] parport: PnPBIOS parport detected.
[   36.040978] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   36.127194] lp0: using parport0 (interrupt-driven).
[   36.145807] mice: PS/2 mouse device common for all mice
[   36.178887] Real Time Clock Driver v1.12
[   36.199151] ieee1394: Initialized config rom entry `ip1394'
[   36.203482] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[   36.581948] input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
[   37.515223] ts: Compaq touchscreen protocol output
[   38.521314] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   39.363958] cdrom: open failed.
[   41.170014] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.174171] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[   41.174191] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[   41.678730] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   41.981357] usb 3-7: device descriptor read/64, error -110
[   42.148402] usb 3-7: new high speed USB device using ehci_hcd and address 3
[   42.246473] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[   42.246499] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[   42.246507] PCI: Via IRQ fixup for 0000:02:04.0, from 11 to 5
[   42.302700] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fdcfe000-fdcfe7ff]  Max Packet=[2048]
[   43.567621] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000aa82b3]
[   45.211045] usb 3-7: device descriptor read/64, error -110
[   60.377435] usb 3-7: device descriptor read/64, error -110
[   60.540464] usb 3-7: new high speed USB device using ehci_hcd and address 4
[   70.944754] usb 3-7: device not accepting address 4, error -110
[   71.006770] usb 3-7: new high speed USB device using ehci_hcd and address 5
[   81.411110] usb 3-7: device not accepting address 5, error -110
[   82.561965] input: PC Speaker
[   82.702197] FDC 0 is a post-1991 82077
[   84.239982] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   84.247991] NET: Registered protocol family 17
[   86.776522] NET: Registered protocol family 10
[   86.776616] Disabled Privacy Extensions on device ffffffff8035a5a0(lo)
[   86.776734] IPv6 over IPv4 tunneling driver
[   87.944692] ACPI: Power Button (FF) [PWRF]
[   87.944702] ACPI: Power Button (CM) [PWRB]
[   88.026640] ibm_acpi: ec object not found
[   94.097338] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[   94.097581] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6 (1400 mV)
[   94.097587] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[   94.097766] cpu_init done, current fid 0xa, vid 0x6
[   94.415011] Bluetooth: Core ver 2.7
[   94.415019] NET: Registered protocol family 31
[   94.415023] Bluetooth: HCI device and connection manager initialized
[   94.415033] Bluetooth: HCI socket layer initialized
[   94.451285] Bluetooth: L2CAP ver 2.7
[   94.451289] Bluetooth: L2CAP socket layer initialized
[   94.534295] Bluetooth: RFCOMM ver 1.5
[   94.534303] Bluetooth: RFCOMM socket layer initialized
[   94.534315] Bluetooth: RFCOMM TTY layer initialized
[   97.385120] eth0: no IPv6 routers present
[  526.464658] cdrom: open failed.
[  735.607740] APIC error on CPU0: 00(40)
[  879.648729] APIC error on CPU0: 40(40)

```

---

