---
title: "Encrypted/corrupted read-only Ext3 filesystem?"
date: 2009-03-12
forum: General Help
---

### Post by webfx on 2009-03-12
Hi there,

I have an Ubuntu system that I installed with a LUKS encrypted filesystem. It's been working great, but yesterday, something happened and it stopped responding ... I couldn't SSH in or wake up the terminal w/ mouse/keyboard. So I had to reboot it manually.

Since then, starting today, the disk or system has been experiencing some kind of error, and the FS has been going into read-only mode.

I searched the forum for answers, and tried 

shutdown -Fr now

To force a fsck on reboot.

It found some errors that it fixed, but it looks like it is still mounting parts of the filesystem as read-only.

Can I fix/salvage this at all, or do I need to do a full reinstall?

Here is my fsck log and dmesg below:

```
lolcat:/var/log/fsck# cat checkfs
Log of fsck -C -R -A -a -f
Thu Mar 12 20:01:26 2009

fsck 1.40-WIP (14-Nov-2006)
/dev/hda1: 29/62248 files (10.3% non-contiguous), 26653/248976 blocks
/dev/mapper/lolcat-home: 10335/3866624 files (2.8% non-contiguous), 195711/7731200 blocks
/dev/mapper/lolcat-tmp: 13/100352 files (15.4% non-contiguous), 22960/401408 blocks
/dev/mapper/lolcat-usr: 74464/625248 files (0.3% non-contiguous), 494703/1250304 blocks
/dev/mapper/lolcat-var: recovering journal
/dev/mapper/lolcat-var: Deleted inode 97972 has zero dtime.  FIXED.
/dev/mapper/lolcat-var: 13069/375360 files (4.5% non-contiguous), 281559/750592 blocks
fsck died with exit status 1

Thu Mar 12 20:07:00 2009
----------------

```



dmesg:

```
Linux version 2.6.18-6-486 (Debian 2.6.18.dfsg.1-22etch3) (dannf@debian.org) (gcc version 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)) #1 Thu Oct 9 15:23:10 UTC 2008
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000dc000 - 00000000000e2000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000005ff0000 (usable)
 BIOS-e820: 0000000005ff0000 - 0000000005ff8000 (ACPI data)
 BIOS-e820: 0000000005ff8000 - 0000000006000000 (ACPI NVS)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
95MB LOWMEM available.
On node 0 totalpages: 24560
  DMA zone: 4096 pages, LIFO batch:0
  Normal zone: 20464 pages, LIFO batch:3
DMI 2.3 present.
ACPI: RSDP (v000 AMI                                   ) @ 0x000fa730
ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x05ff0000
ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x05ff0030
ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 MSFT 0x0100000d) @ 0x00000000
ACPI: PM-Timer IO Port: 0x808
Allocating PCI resources starting at 10000000 (gap: 06000000:f8c00000)
Detected 1600.256 MHz processor.
Built 1 zonelists.  Total pages: 24560
Kernel command line: root=/dev/mapper/lolcat-root ro 
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (010c1000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 512 (order: 9, 2048 bytes)
Console: colour VGA+ 80x25
Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
Memory: 88892k/98240k available (1499k kernel code, 8900k reserved, 599k data, 256k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 3203.82 BogoMIPS (lpj=6407643)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Capability LSM initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000
Compat vDSO mapped to ffffe000.
CPU: AMD mobile AMD Athlon(tm) XP-M 1900+ stepping 00
Checking 'hlt' instruction... OK.
ACPI: Core revision 20060707
ACPI: setting ELCR to 0200 (from 0c20)
checking if image is initramfs... it is
Freeing initrd memory: 5411k freed
NET: Registered protocol family 16
EISA bus registered
ACPI: bus type pci registered
PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
PCI: Using configuration type 1
Setting up standard PCI resources
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Probing PCI hardware (bus 00)
PCI quirk: region 0800-087f claimed by vt8235 PM
PCI quirk: region 0400-040f claimed by vt8235 SMB
Boot video device is 0000:01:00.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: Power Resource [URP1] (off)
ACPI: Power Resource [URP2] (off)
ACPI: Power Resource [FDDP] (off)
ACPI: Power Resource [LPTP] (off)
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 8 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
PCI: Bridge: 0000:00:01.0
  IO window: disabled.
  MEM window: dfd00000-dfefffff
  PREFETCH window: cfc00000-dfbfffff
PCI: Setting latency timer of device 0000:00:01.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
TCP established hash table entries: 4096 (order: 2, 16384 bytes)
TCP bind hash table entries: 2048 (order: 1, 8192 bytes)
TCP: Hash tables configured (established 4096 bind 2048)
TCP reno registered
audit: initializing netlink socket (disabled)
audit(1236878233.940:1): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Initializing Cryptographic API
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
PNP: No PS/2 controller found. Probing ports directly.
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
mice: PS/2 mouse device common for all mice
EISA: Probing bus 0 at eisa.0
EISA: Detected 0 cards.
TCP bic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
NET: Registered protocol family 8
NET: Registered protocol family 20
Using IPI Shortcut mode
ACPI: (supports S0 S1 S4 S5)
Time: tsc clocksource has been installed.
Freeing unused kernel memory: 256k freed
ACPI: Processor [CPU1] (supports 16 throttling states)
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v3.0
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:10.0: UHCI Host Controller
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
uhci_hcd 0000:00:10.0: irq 11, io base 0x0000e400
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
via-rhine.c:v1.10-LK1.4.1 July-24-2006 Written by Donald Becker
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
uhci_hcd 0000:00:10.1: UHCI Host Controller
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:10.1: irq 5, io base 0x0000e800
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
uhci_hcd 0000:00:10.2: UHCI Host Controller
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:10.2: irq 5, io base 0x0000ec00
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
VP_IDE: IDE controller at PCI slot 0000:00:11.1
ACPI: Unable to derive IRQ for device 0000:00:11.1
ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
PCI: VIA IRQ fixup for 0000:00:11.1, from 255 to 15
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
    ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: Maxtor 6E040L0, ATA DISK drive
usb 3-1: new low speed USB device using uhci_hcd and address 2
usb 3-1: configuration #1 chosen from 1 choice
usb 3-2: new low speed USB device using uhci_hcd and address 3
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
usb 3-2: configuration #1 chosen from 1 choice
usbcore: registered new driver hiddev
input: Dell Dell USB Optical Mouse as /class/input/input0
input: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:10.2-1
input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input1
input: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:10.2-2
input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input2
input: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:10.2-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
hdc: AOPEN CD-RW CRW5232 1.03 20031013, ATAPI CD/DVD-ROM drive
hdd: GCR-8523B, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
eth0: VIA Rhine II at 0x1dc00, 00:0d:87:af:f5:67, IRQ 11.
eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
ehci_hcd 0000:00:10.3: EHCI Host Controller
ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:10.3: irq 10, io mem 0xdfffff00
ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
hda: max request size: 128KiB
hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
hda: cache flushes supported
 hda: hda1 hda2 < hda5 >
hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
usb 3-1: USB disconnect, address 2
usb 3-1: new low speed USB device using uhci_hcd and address 4
device-mapper: ioctl: 4.7.0-ioctl (2006-06-24) initialised: dm-devel@redhat.com
usb 3-1: configuration #1 chosen from 1 choice
input: Dell Dell USB Optical Mouse as /class/input/input3
input: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:10.2-1
usb 3-2: USB disconnect, address 3
usb 3-2: new low speed USB device using uhci_hcd and address 5
usb 3-2: configuration #1 chosen from 1 choice
input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input4
input: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:10.2-2
input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input5
input: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:10.2-2
Attempting manual resume
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
ts: Compaq touchscreen protocol output
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
input: PC Speaker as /class/input/input6
irda_init()
NET: Registered protocol family 23
Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected VIA PM266/KM266 chipset
agpgart: AGP aperture is 64M @ 0xe0000000
Real Time Clock Driver v1.12ac
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
PCI: Setting latency timer of device 0000:00:11.5 to 64
EXT3 FS on dm-1, internal journal
loop: loaded (max 8 devices)
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on dm-6, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on dm-5, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on dm-2, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on dm-3, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
Adding 282616k swap on /dev/mapper/lolcat-swap_1.  Priority:-1 extents:1 across:282616k
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=811852, sector=811852
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 811852
EXT3-fs error (device dm-1): ext3_get_inode_loc: unable to read inode block - inode=38592, block=155667
Remounting filesystem read-only
EXT3-fs error (device dm-1) in ext3_reserve_inode_write: IO failure
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
IPv6 over IPv4 tunneling driver
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=811852, sector=811852
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 811852
EXT3-fs error (device dm-1): ext3_get_inode_loc: unable to read inode block - inode=38591, block=155667
eth0: no IPv6 routers present
ACPI: Power Button (FF) [PWRF]
ACPI: Power Button (CM) [PWRB]
ACPI: Sleep Button (CM) [SLPB]
lp0: using parport0 (interrupt-driven).
ppdev: user-space parallel port driver
[drm] Initialized drm 1.0.1 20051102
ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[drm] Initialized savage 2.4.1 20050313 on minor 0
mtrr: base(0xd2000000) is not aligned on a size(0x5000000) boundary
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=811852, sector=811852
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 811852
EXT3-fs error (device dm-1): ext3_get_inode_loc: unable to read inode block - inode=38585, block=155667

```

---

### Post by Herman on 2009-03-12
Here are a couple of links that might help you,  [Running fsck on a LUKS encrypted partition in LVM]("http://iquaid.org/2008/03/04/running-fsck-on-a-luks-encrypted-partition-in-lvm/"), and [Rescue an encrypted LUKS LVM volume]("http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html").

Regards, Herman :D

---

### Post by webfx on 2009-03-13
Hey Herman, thanks for the links.

I was doing some more investigating in my syslog, and realized that the system was reporting several errors like this,

Mar 12 11:34:13 lolcat kernel: hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Mar 12 11:34:13 lolcat kernel: hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=17102118, sector=17102118
Mar 12 11:34:13 lolcat kernel: ide: failed opcode was: unknown
Mar 12 11:34:13 lolcat kernel: end_request: I/O error, dev hda, sector 17102118

which led to the first system freeze which I had to hard reset, from .. I THOUGHT the hard reset was responsible, but it seems like the underlying problem was probably bad sectors on the HD causing the crash in the first place.

The SeekComplete errors have been getting reported in different sectors since, so this is leading me to believe that the problem may be the (old) hard drive and that I should replace it.

Does this make sense?

---

### Post by flyingbrass on 2009-03-13
Probably time for a new drive.  You could check the drive's SMART error log and run some tests.  Install smartmontools.

sudo smartctl -a /dev/hda shows all info.  

Short test: sudo smartctl -t short /dev/hda

Man smartctl for more.

---

