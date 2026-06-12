---
title: "Burned a DVD, now I can't read any CD/DVD's"
date: 2006-09-29
forum: Desktop Environments
---

### Post by Yoshimitsu8 on 2006-09-29
Hello,
I burned a DVD with my DVD player and everything went ok after I reduced the size of the data I was trying to put on my DVD. Now there is just a permanent icon on my desktop that says "Blank DVD-R Disc" even though there isn't a DVD or anything in the CD/DVD rom drive. 

If I put any disc (blank DVD or CD, other burned CD/DVD's, normal DVD (like a movie) or normal music CD) it doesn't recognize it, it just keeps the "Blank DVD-R Disc" there. If I double click on it, it just show the normal DVD/CD burning window (like when you a put a recordable media in, it pops up on the desktop, then you double click on it, add the files you want and click burn).

So basically I can't read/write any CD's or DVD's and it just things that I have a blank DVD in my drive. Any thoughts/help would be great!
PS: Yes I have restarted.

---

### Post by vynsane on 2006-09-29
i'm not an expert by any means, and don't have a burner in either of my xubuntu machines, but did you eject it when it was done burning? right-click and "eject". if that's not an option or doesn't work, try unmounting it by doing the same thing, except clicking "unmount". that might work. but take that with a grain of salt, as i don't really know what i'm talking about! ;)

---

### Post by dannyboy79 on 2006-09-29
try to a computer restart.

---

### Post by Yoshimitsu8 on 2006-09-29
Yes, I have tried ejecting and also restarting (as I stated in the original post). When I do eject, the CD/DVD rom tray does come out, but the same icon is left on the desktop and it doesn't even recognize that the tray door is open and that no CD is in the computer. It still acts as though there is a blank DVD in the DVD-rom tray.

Still looking for help if anyone has some sugguestions ](*,)

---

### Post by pseudonym on 2006-09-29
Open a terminal and type -```
dmesg > Desktop/dmesg.txt
``` Then upload the file in your next post as an attachment...

---

### Post by johnbl on 2006-09-29
Having a very similar problem. CD Drive suddenly wont. Whirs and clicks when disk put in but that's it.

Shows in File Browser as empty.

Disks Manager takes for ever to run but eventually did. CDROM details are greyed out!
 
Tried to upload the smesg.txt file but got this;
<sigh>

Fatal error: Direct Instantiation of vB_Image_Abstract prohibited. in /includes/class_image.php on line 188

However - hope this is enough to give you an insight.
](*,) 
File peppered with cd failed as;

[17179592.204000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179592.372000] 8139too Fast Ethernet driver 0.9.27
[17179592.448000] ipw2200: Radio Frequency Kill Switch is On:
[17179592.448000] Kill switch must be turned off for wireless networking to work.
[17179592.448000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[17179592.448000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179592.448000] eth1: RealTek RTL8139 at 0xf8b24400, 00:03:0d:28:4b:2d, IRQ 5
[17179592.448000] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179592.456000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179592.576000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x20f 0x4d0-0x4d7
[17179592.576000] cs: IO port probe 0xc00-0xcf7: clean.
[17179592.576000] cs: IO port probe 0xa00-0xaff: clean.
[17179592.952000] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179593.240000] lp: driver loaded but no devices found
[17179593.312000] SCSI subsystem initialized
[17179593.332000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179593.332000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179593.332000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179593.608000] Adding 3059704k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 extents:1 across:3059704k
[17179593.720000] EXT3 FS on dm-0, internal journal
[17179593.936000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.936000] md: bitmap version 4.39
[17179593.992000] NET: Registered protocol family 17
[17179595.224000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179595.224000] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179595.224000] ide: failed opcode was: unknown
[17179595.224000] cdrom: open failed.
[17179596.020000] kjournald starting.  Commit interval 5 seconds
[17179596.020000] EXT3 FS on hda1, internal journal
[17179596.020000] EXT3-fs: mounted filesystem with ordered data mode.
[17179597.936000] ACPI: AC Adapter [AC0] (on-line)
[17179597.948000] ACPI: Battery Slot [BAT0] (battery present)
[17179598.028000] ACPI: Power Button (FF) [PWRF]
[17179598.028000] ACPI: Lid Switch [LID]
[17179598.028000] ACPI: Sleep Button (CM) [SLPB]
[17179598.028000] ACPI: Power Button (CM) [PWRB]
[17179598.104000] ibm_acpi: ec object not found
[17179598.136000] pcc_acpi: loading...
[17179598.216000] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[17179598.420000] NET: Registered protocol family 10
[17179598.420000] lo: Disabled Privacy Extensions
[17179598.420000] IPv6 over IPv4 tunneling driver
[17179600.740000] input: PS/2 Generic Mouse as /class/input/input6
[17179600.940000] psmouse.c: Failed to enable mouse on isa0060/serio3
[17179603.332000] ppdev: user-space parallel port driver
[17179605.316000] [drm] Initialized drm 1.0.1 20051102
[17179605.320000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179605.320000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179605.320000] [drm] Initialized i915 1.4.0 20060119 on minor 1
[17179607.888000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179607.888000] apm: overridden by ACPI.
[17179609.396000] eth1: no IPv6 routers present
[17179609.784000] Bluetooth: Core ver 2.8
[17179609.784000] NET: Registered protocol family 31
[17179609.784000] Bluetooth: HCI device and connection manager initialized
[17179609.784000] Bluetooth: HCI socket layer initialized
[17179609.916000] Bluetooth: L2CAP ver 2.8
[17179609.916000] Bluetooth: L2CAP socket layer initialized
[17179610.000000] Bluetooth: RFCOMM socket layer initialized
[17179610.000000] Bluetooth: RFCOMM TTY layer initialized
[17179610.000000] Bluetooth: RFCOMM ver 1.7
[17179727.508000] cdrom: open failed.
[17180236.416000] cdrom: open failed.
[17195700.240000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!

---

### Post by pseudonym on 2006-09-30
I was getting similar errors. I think they have to do with interrupt assignment to the IDE controller. It appears to have been fixed by doing this - ```
sudo gedit /etc/modules
add 'ide-cd' as the first module in the list
Save and exit gedit
Reboot
``` This file prioritises the loading of modules listed in it, AFAIK. 

I'm used to the cd module being inserted into the file automatically by the system, but it doesn't seem to be happening in this Ubuntu release???

---

### Post by johnbl on 2006-09-30
I have;

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq
piix
ide-core
ide-cd
ide-disk
ide-generic

ENDS
So the ide-cd is there but should this be reordered or?

confused here ](*,) 

John

---

### Post by Yoshimitsu8 on 2006-10-01
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ff87000 (usable)
[17179569.184000]  BIOS-e820: 000000001ff87000 - 000000001ffa6000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ffa6000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fe710
[17179569.184000] On node 0 totalpages: 130951
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126855 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fd730
[17179569.184000] ACPI: RSDT (v001 DELL   DIM 8100 0x00000005 ASL  0x00000061) @ 0x000fd744
[17179569.184000] ACPI: FADT (v001 DELL   DIM 8100 0x00000005 ASL  0x00000061) @ 0x000fd774
[17179569.184000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000b) @ 0xfffe6f39
[17179569.184000] ACPI: BOOT (v001 DELL    8100    0x00000005 ASL  0x00000061) @ 0x000fd7e8
[17179569.184000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Intel MultiProcessor Specification v1.4
[17179569.184000]     IMCR and PIC compatibility mode.
[17179569.184000] SMP mptable: null local APIC address!
[17179569.184000] BIOS bug, MP table errors detected!...
[17179569.184000] ... disabling SMP support. (tell your hw vendor)
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01401000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1695.210 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.844000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.848000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.864000] Memory: 508468k/523804k available (1976k kernel code, 14808k reserved, 606k data, 288k init, 0k highmem)
[17179569.864000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.944000] Calibrating delay using timer specific routine.. 3393.75 BogoMIPS (lpj=6787513)
[17179569.944000] Security Framework v1.0.0 initialized
[17179569.944000] SELinux:  Disabled at boot.
[17179569.944000] Mount-cache hash table entries: 512
[17179569.944000] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.944000] CPU: After vendor identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.944000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179569.944000] CPU: L2 cache: 256K
[17179569.944000] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00000080 00000000 00000000 00000000
[17179569.944000] mtrr: v2.0 (20020519)
[17179569.944000] CPU: Intel(R) Pentium(R) 4 CPU 1700MHz stepping 0a
[17179569.944000] Enabling fast FPU save and restore... done.
[17179569.944000] Enabling unmasked SIMD FPU exception support... done.
[17179569.944000] Checking 'hlt' instruction... OK.
[17179569.960000] checking if image is initramfs... it is
[17179570.800000] Freeing initrd memory: 6616k freed
[17179570.816000] ACPI: Looking for DSDT ... not found!
[17179570.840000] ACPI: setting ELCR to 0200 (from 0e08)
[17179570.840000] NET: Registered protocol family 16
[17179570.840000] EISA bus registered
[17179570.840000] ACPI: bus type pci registered
[17179570.852000] PCI: PCI BIOS revision 2.10 entry at 0xfc10e, last bus=2
[17179570.852000] PCI: Using configuration type 1
[17179570.852000] ACPI: Subsystem revision 20051216
[17179570.868000] ACPI: Interpreter enabled
[17179570.868000] ACPI: Using PIC for interrupt routing
[17179570.872000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.872000] PCI: Probing PCI hardware (bus 00)
[17179570.872000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.880000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179570.880000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179570.880000] Boot video device is 0000:01:00.0
[17179570.880000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.880000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.884000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179570.892000] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 9 10 11 12 15)
[17179570.892000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179570.896000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179570.896000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179570.896000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179570.896000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179570.900000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179570.900000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179570.900000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.900000] pnp: PnP ACPI init
[17179570.920000] pnp: PnP ACPI: found 10 devices
[17179570.920000] PnPBIOS: Disabled by ACPI PNP
[17179570.920000] PCI: Using ACPI for IRQ routing
[17179570.920000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.932000] pnp: 00:09: ioport range 0x800-0x85f could not be reserved
[17179570.932000] pnp: 00:09: ioport range 0xc00-0xc7f has been reserved
[17179570.932000] pnp: 00:09: ioport range 0x860-0x8ff could not be reserved
[17179570.932000] PCI: Bridge: 0000:00:01.0
[17179570.932000]   IO window: disabled.
[17179570.932000]   MEM window: fd000000-feffffff
[17179570.932000]   PREFETCH window: f0000000-f7ffffff
[17179570.932000] PCI: Bridge: 0000:00:1e.0
[17179570.932000]   IO window: e000-efff
[17179570.932000]   MEM window: ff100000-ff2fffff
[17179570.932000]   PREFETCH window: 30000000-300fffff
[17179570.932000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.932000] Simple Boot Flag at 0x7d set to 0x1
[17179570.932000] audit: initializing netlink socket (disabled)
[17179570.932000] audit(1158817151.932:1): initialized
[17179570.932000] VFS: Disk quotas dquot_6.5.1
[17179570.932000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.932000] Initializing Cryptographic API
[17179570.932000] io scheduler noop registered
[17179570.932000] io scheduler anticipatory registered
[17179570.932000] io scheduler deadline registered
[17179570.932000] io scheduler cfq registered
[17179570.932000] isapnp: Scanning for PnP cards...
[17179571.288000] isapnp: No Plug & Play device found
[17179571.316000] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
[17179571.316000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.316000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.316000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.316000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.316000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.320000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.320000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.320000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.320000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.320000] mice: PS/2 mouse device common for all mice
[17179571.324000] EISA: Probing bus 0 at eisa.0
[17179571.324000] EISA: Detected 0 cards.
[17179571.324000] NET: Registered protocol family 2
[17179571.364000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179571.364000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.364000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.364000] TCP: Hash tables configured (established 32768 bind 32768)
[17179571.364000] TCP reno registered
[17179571.364000] TCP bic registered
[17179571.364000] NET: Registered protocol family 1
[17179571.364000] NET: Registered protocol family 8
[17179571.364000] NET: Registered protocol family 20
[17179571.364000] Using IPI Shortcut mode
[17179571.364000] ACPI wakeup devices: 
[17179571.364000] VBTN PCI0 USB0 USB1 PCI1  KBD 
[17179571.364000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.364000] Freeing unused kernel memory: 288k freed
[17179571.440000] vga16fb: initializing
[17179571.440000] vga16fb: mapped to 0xc00a0000
[17179571.452000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.592000] Console: switching to colour frame buffer device 80x25
[17179571.592000] fb0: VGA16 VGA frame buffer device
[17179572.732000] Capability LSM initialized
[17179573.732000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[17179573.732000] ICH2: chipset revision 4
[17179573.732000] ICH2: not 100% native mode: will probe irqs later
[17179573.732000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179573.732000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[17179573.732000] Probing IDE interface ide0...
[17179574.020000] hda: IC35L120AVVA07-0, ATA DISK drive
[17179574.692000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.692000] Probing IDE interface ide1...
[17179575.432000] hdc: TSSTcorpCD/DVDW TS-H552U, ATAPI CD/DVD-ROM drive
[17179576.104000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.116000] hda: max request size: 128KiB
[17179576.128000] hda: 241254720 sectors (123522 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.128000] hda: cache flushes supported
[17179576.128000]  hda: hda1 hda2 hda3 hda4
[17179576.160000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.160000] Uniform CD-ROM driver Revision: 3.20
[17179576.568000] usbcore: registered new driver usbfs
[17179576.568000] usbcore: registered new driver hub
[17179576.568000] USB Universal Host Controller Interface driver v2.3
[17179576.568000] **** SET: Misaligned resource pointer: de920502 Type 07 Len 0
[17179576.572000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179576.572000] PCI: setting IRQ 11 as level-triggered
[17179576.572000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179576.572000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179576.572000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179576.572000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179576.572000] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ff80
[17179576.572000] hub 1-0:1.0: USB hub found
[17179576.572000] hub 1-0:1.0: 2 ports detected
[17179576.676000] **** SET: Misaligned resource pointer: de920202 Type 07 Len 0
[17179576.676000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[17179576.676000] PCI: setting IRQ 9 as level-triggered
[17179576.676000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[17179576.676000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[17179576.676000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[17179576.676000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[17179576.676000] uhci_hcd 0000:00:1f.4: irq 9, io base 0x0000ff60
[17179576.676000] hub 2-0:1.0: USB hub found
[17179576.676000] hub 2-0:1.0: 2 ports detected
[17179576.944000] Attempting manual resume
[17179577.008000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.008000] kjournald starting.  Commit interval 5 seconds
[17179577.020000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179577.440000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[17179577.580000] hub 2-2:1.0: USB hub found
[17179577.580000] hub 2-2:1.0: 4 ports detected
[17179577.896000] usb 2-2.3: new full speed USB device using uhci_hcd and address 4
[17179587.312000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.320000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.328000] agpgart: Detected an Intel i850 Chipset.
[17179587.336000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179587.356000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.388000] hw_random: RNG not detected
[17179587.604000] nvidia: module license 'NVIDIA' taints kernel.
[17179587.612000] **** SET: Misaligned resource pointer: daeaff02 Type 07 Len 0
[17179587.612000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[17179587.612000] PCI: setting IRQ 3 as level-triggered
[17179587.612000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[17179587.612000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179588.340000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x6004
[17179588.340000] usbcore: registered new driver usblp
[17179588.340000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179588.628000] gameport: EMU10K1 is pci0000:02:0a.1/gameport0, io 0xecd8, speed 917kHz
[17179588.644000] parport: PnPBIOS parport detected.
[17179588.644000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[17179588.784000] Floppy drive(s): fd0 is 1.44M
[17179588.796000] usbcore: registered new driver hiddev
[17179588.800000] FDC 0 is a National Semiconductor PC87306
[17179588.816000] input: Microsoft Microsoft Wheel Mouse Optical® as /class/input/input1
[17179588.816000] input: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical®] on usb-0000:00:1f.4-1
[17179588.816000] usbcore: registered new driver usbhid
[17179588.816000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179588.852000] **** SET: Misaligned resource pointer: dc23f202 Type 07 Len 0
[17179588.852000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179588.852000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179588.852000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[17179588.852000] 0000:02:0c.0: 3Com PCI 3c905C Tornado at e08c0c00. Vers LK1.1.19
[17179589.132000] Real Time Clock Driver v1.12
[17179589.136000] input: PC Speaker as /class/input/input2
[17179589.236000] ts: Compaq touchscreen protocol output
[17179589.376000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179589.904000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179590.624000] lp0: using parport0 (interrupt-driven).
[17179590.704000] Adding 1172736k swap on /dev/hda3.  Priority:-1 extents:1 across:1172736k
[17179590.868000] EXT3 FS on hda1, internal journal
[17179590.960000] NET: Registered protocol family 17
[17179591.104000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179591.104000] md: bitmap version 4.39
[17179591.776000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179592.680000] cdrom: open failed.
[17179592.856000] NET: Registered protocol family 10
[17179592.856000] lo: Disabled Privacy Extensions
[17179592.856000] IPv6 over IPv4 tunneling driver
[17179593.232000] kjournald starting.  Commit interval 5 seconds
[17179593.232000] EXT3 FS on hda2, internal journal
[17179593.232000] EXT3-fs: mounted filesystem with ordered data mode.
[17179600.544000] ACPI: Power Button (FF) [PWRF]
[17179600.544000] ACPI: Power Button (CM) [VBTN]
[17179600.696000] ibm_acpi: ec object not found
[17179600.736000] pcc_acpi: loading...
[17179602.860000] eth1: no IPv6 routers present
[17179605.384000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179605.388000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179605.388000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179606.756000] ppdev: user-space parallel port driver
[17179607.128000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179607.128000] apm: overridden by ACPI.
[17179612.528000] Bluetooth: Core ver 2.8
[17179612.528000] NET: Registered protocol family 31
[17179612.528000] Bluetooth: HCI device and connection manager initialized
[17179612.528000] Bluetooth: HCI socket layer initialized
[17179612.556000] Bluetooth: L2CAP ver 2.8
[17179612.556000] Bluetooth: L2CAP socket layer initialized
[17179612.560000] Bluetooth: RFCOMM socket layer initialized
[17179612.560000] Bluetooth: RFCOMM TTY layer initialized
[17179612.560000] Bluetooth: RFCOMM ver 1.7
[17180319.968000] cdrom: This disc doesn't have any tracks I recognize!
[17180801.928000] cdrom: This disc doesn't have any tracks I recognize!
[17181953.500000] usb 2-2.2: new full speed USB device using uhci_hcd and address 5
[17181954.348000] SCSI subsystem initialized
[17181954.376000] Initializing USB Mass Storage driver...
[17181954.376000] scsi0 : SCSI emulation for USB Mass Storage devices
[17181954.376000] usb-storage: device found at 5
[17181954.376000] usb-storage: waiting for device to settle before scanning
[17181954.376000] usbcore: registered new driver usb-storage
[17181954.376000] USB Mass Storage support registered.
[17181959.380000]   Vendor: GENERIC   Model: USB FLASH DISK    Rev: CCCC
[17181959.380000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17181959.380000] usb-storage: device scan complete
[17181959.448000] Driver 'sd' needs updating - please use bus_type methods
[17181959.456000] SCSI device sda: 69632 512-byte hdwr sectors (36 MB)
[17181959.456000] sda: Write Protect is off
[17181959.456000] sda: Mode Sense: 00 00 00 00
[17181959.456000] sda: assuming drive cache: write through
[17181959.472000] SCSI device sda: 69632 512-byte hdwr sectors (36 MB)
[17181959.476000] sda: Write Protect is off
[17181959.476000] sda: Mode Sense: 00 00 00 00
[17181959.476000] sda: assuming drive cache: write through
[17181959.476000]  sda: sda1
[17181959.484000] sd 0:0:0:0: Attached scsi removable disk sda
[17181959.500000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17181961.072000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17181982.860000] usb 2-2.2: USB disconnect, address 5
[17182137.732000] hdc: request sense failure: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17182137.732000] hdc: request sense failure: error=0x00 { }
[17182137.732000] hdc: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17182137.732000] hdc: status error: error=0x00 { }
[17182137.732000] ide: failed opcode was: unknown
[17182137.732000] hdc: drive not ready for command
[17430134.964000] usb 2-2.2: new full speed USB device using uhci_hcd and address 6
[17430135.072000] scsi1 : SCSI emulation for USB Mass Storage devices
[17430135.072000] usb-storage: device found at 6
[17430135.072000] usb-storage: waiting for device to settle before scanning
[17430140.076000]   Vendor: GENERIC   Model: USB FLASH DISK    Rev: CCCC
[17430140.076000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17430140.080000] SCSI device sda: 69632 512-byte hdwr sectors (36 MB)
[17430140.084000] sda: Write Protect is off
[17430140.084000] sda: Mode Sense: 00 00 00 00
[17430140.084000] sda: assuming drive cache: write through
[17430140.096000] SCSI device sda: 69632 512-byte hdwr sectors (36 MB)
[17430140.096000] sda: Write Protect is off
[17430140.096000] sda: Mode Sense: 00 00 00 00
[17430140.096000] sda: assuming drive cache: write through
[17430140.096000]  sda: sda1
[17430140.104000] sd 1:0:0:0: Attached scsi removable disk sda
[17430140.104000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17430140.104000] usb-storage: device scan complete
[17430141.164000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17430176.032000] usb 2-2.2: USB disconnect, address 6
[17470910.360000] ibm_acpi: ec object not found
[17525823.904000] usb 2-2.4: new full speed USB device using uhci_hcd and address 7
[17525955.512000] usb 2-2.4: USB disconnect, address 7
[17571790.552000] usb 2-2.4: new full speed USB device using uhci_hcd and address 8
[17572355.220000] usb 2-2.4: USB disconnect, address 8
[18075706.696000] ibm_acpi: ec object not found

-I don't have time to try other things then this, but I'll update here sometime later today.

---

