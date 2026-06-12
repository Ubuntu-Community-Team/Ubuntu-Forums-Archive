---
title: "DVD Drive will not mount"
date: 2005-07-19
forum: Desktop Environments
---

### Post by Dragonmantank on 2005-07-19
Whenever I try to mount a CD (either with 'mount' or by going to 'Computer' and double-clicking the drive) it just seems to hang. I don't even notice the seek light on the drive turning on.

What should I check to get this drive working? Ubuntu seems to know that it is there at least.

---

### Post by fizgig on 2005-07-20
It might not matter but more info is useful:

1. The contents of your /etc/fstab file
2. The mount command you execute
3. Any feedback from the mount command
4. The contents of your /media folder

---

### Post by exile on 2005-07-20
also are there any specific messages about it when you run dmesg?

---

### Post by Dragonmantank on 2005-07-20
Here is my fstab:

======================================================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
======================================================

I have tried this as a mount command:
======================================================
sudo mount /dev/hdd /media/cdrom1
======================================================

All that happens is I get a blinking cursor on the next line after hitting enter. The DVD drive doesn't blink nor spin.

In Media I have:
======================================================
cdrom  cdrom0  cdrom1  floppy  floppy0  usb  usb0  usbdisk
======================================================

When I run dmesg after trying to mount/open the DVD-drive:
======================================================
served)
 BIOS-e820: 0000000000100000 - 0000000017ffc000 (usable)
 BIOS-e820: 0000000017ffc000 - 0000000017fff000 (ACPI data)
 BIOS-e820: 0000000017fff000 - 0000000018000000 (ACPI NVS)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
383MB LOWMEM available.
On node 0 totalpages: 98300
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 94204 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 ASUS                                  ) @ 0x000f62a0
ACPI: RSDT (v001 ASUS   A7V600   0x42302e31 MSFT 0x31313031) @ 0x17ffc000
ACPI: FADT (v001 ASUS   A7V600   0x42302e31 MSFT 0x31313031) @ 0x17ffc0b2
ACPI: BOOT (v001 ASUS   A7V600   0x42302e31 MSFT 0x31313031) @ 0x17ffc030
ACPI: MADT (v001 ASUS   A7V600   0x42302e31 MSFT 0x31313031) @ 0x17ffc058
ACPI: DSDT (v001   ASUS A7V600   0x00001000 MSFT 0x0100000b) @ 0x00000000
ACPI: PM-Timer IO Port: 0xe408
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 6:8 APIC version 16
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hdb1 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1791.593 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 382108k/393200k available (1436k kernel code, 10448k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3547.13 BogoMIPS (lpj=1773568)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000020 00000000 00000000
CPU: AMD Athlon(TM) XP 2200+ stepping 01
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xf1970, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12)
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12) *15, disabled.
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Via IRQ fixup
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 14 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:01: ioport range 0xe400-0xe47f could not be reserved
pnp: 00:01: ioport range 0xe800-0xe81f has been reserved
pnp: 00:0d: ioport range 0x290-0x297 has been reserved
pnp: 00:0d: ioport range 0x370-0x375 has been reserved
Simple Boot Flag at 0x3a set to 0x1
audit: initializing netlink socket (disabled)
audit(1121897567.657:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 7
Cannot allocate resource for EISA slot 8
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 PCI1 USB0 USB1 USB2 USB3 SU20 MC97
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:0f.1
ACPI: PCI interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
    ide0: BM-DMA at 0x9000-0x9007, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0x9008-0x900f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: Maxtor 6Y080L0, ATA DISK drive
hdb: QUANTUM FIREBALLlct20 30, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2
hdb: max request size: 128KiB
hdb: 58633344 sectors (30020 MB) w/418KiB Cache, CHS=58168/16/63
hdb: cache flushes not supported
 /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: LITE-ON LTR-52327S, ATAPI CD/DVD-ROM drive
hdd: Pioneer DVD-ROM ATAPIModel DVD-120S, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1124508k swap on /dev/hdb5.  Priority:-1 extents:1
EXT3 FS on hdb1, internal journal
hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 40X DVD-ROM drive, 256kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA KT400/KT400A/KT600 chipset
agpgart: Maximum main memory to use for agp memory: 321M
agpgart: AGP aperture is 64M @ 0xf8000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 18
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 18
eth0: 3Com Gigabit LOM (3C940)
      PrefPort:A  RlmtMode:Check Link State
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:0d.0[A] -> GSI 16 (level, low) -> IRQ 16
eth1: RealTek RTL8139 at 0xb400, 00:30:bd:28:d2:45, IRQ 16
eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
SCSI subsystem initialized
libata version 1.10 loaded.
eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
sata_via version 1.1
ACPI: PCI interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
sata_via(0000:00:0f.0): routed to hard irq line 4
ata1: SATA max UDMA/133 cmd 0xB000 ctl 0xA802 bmdma 0x9800 irq 20
ata2: SATA max UDMA/133 cmd 0xA400 ctl 0xA002 bmdma 0x9808 irq 20
ata1: no device found (phy stat 00000000)
scsi0 : sata_via
ata2: no device found (phy stat 00000000)
scsi1 : sata_via
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0x8800
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0x8400
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
NET: Registered protocol family 17
uhci_hcd 0000:00:10.2: irq 21, io base 0x8000
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
usb 1-1: new low speed USB device using uhci_hcd and address 2
uhci_hcd 0000:00:10.3: irq 21, io base 0x7800
uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 2-1: new full speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.4: irq 21, pci mem 0xe9000000
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
usb 2-1: device not accepting address 2, error -71
usb 1-1: USB disconnect, address 2
ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:11.5 to 64
usb 1-1: new low speed USB device using uhci_hcd and address 3
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-1
usb 2-1: new full speed USB device using uhci_hcd and address 4
hub 2-1:1.0: USB hub found
hub 2-1:1.0: 2 ports detected
usb 2-1.1: new full speed USB device using uhci_hcd and address 5
usb 2-1.2: new full speed USB device using uhci_hcd and address 6
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x043D pid 0x0069
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[drm] Initialized radeon 1.14.0 20050125 on minor 0: ATI Technologies Inc Radeon RV250 If [Radeon 9000]
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Device is in legacy mode, falling back to 2.x
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[drm] Loading R200 Microcode
eth1: no IPv6 routers present
hdd: request sense failure: status=0x51 { DriveReady SeekComplete Error }
hdd: request sense failure: error=0x04Aborted Command
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
======================================================

---

### Post by gcranston on 2005-08-03
I am getting similar errors.  I can mount cd's and sometimes dvd's.  When ripping (either dvdrip/transcode, or acidrip/mencoder) fails, dvd appers unmounted and will not remount.  I get no medium found error.  I can still mount cd's at this point (very strange).

My /var/log/messages ends with:

```
Aug  3 23:10:23 localhost kernel:     ACPI-0405: *** Error: Handler for [EmbeddedControl] returned AE_TIME
Aug  3 23:10:23 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.LPCB.BAT1._BST] (Node c14defc0), AE_TIME
Aug  3 23:12:29 localhost kernel: cdrom: open failed.
Aug  3 23:12:29 localhost kernel: hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
Aug  3 23:12:29 localhost kernel: hdc: packet command error: error=0x30
Aug  3 23:12:29 localhost kernel: ide: failed opcode was 100
Aug  3 23:12:29 localhost kernel: ATAPI device hdc:
Aug  3 23:12:29 localhost kernel:   Error: Medium error -- (Sense key=0x03)
Aug  3 23:12:29 localhost kernel:   (reserved error code) -- (asc=0x57, ascq=0x00)
Aug  3 23:12:29 localhost kernel:   The failed "Read Cd/Dvd Capacity" packet command was:
Aug  3 23:12:29 localhost kernel:   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
Aug  3 23:12:29 localhost kernel: cdrom: open failed.
``` 


My /etc/fstab looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/sda1      /media/usb      auto    rw,user         0       0
``` 

I'd really love some help on this...

---

