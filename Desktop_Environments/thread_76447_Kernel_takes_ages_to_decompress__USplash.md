---
title: "Kernel takes ages to decompress / USplash"
date: 2005-10-15
forum: Desktop Environments
---

### Post by CbrPad on 2005-10-15
Hi all,

I'd been running Hoary since release and it booted up fairly quickly for me.  I installed a Breezy preview about a month ago which worked fine for a day or two til the first updates came in.  At this point USplash stopped working, the splashscreen would appear with 'modules' at the bottom.  But it seemed to be timing out as it waited for the kernel to decompress and would disappear back to the normal text bootup once that had finished.  

I've just installed the release ver of Breezy but things remain the same.
I've tried the suggestions in other posts about reconfiguring the kernel and usplash, reinstalling them and installing BUM to make sure USplash is actually started which it is, but still nothing which is why I think this is a timeout problem.

I've tried both the 386 and K7 kernels, but they both still take about 10-15 seconds to initially decompress and start loading.  Is there anyway to get this to speed up or how long should it be taking ?

My system is...

Amd 64 3200+
Abit AV8 Socket 939 motherboard
1024 megs ram
NVidia GeForce FX5700 Ultra with 128 megs ram (driver Nvidia 1.0.7667)
Kernel 2.6.12-9-k7

Fingers crossed someone can help :)

---

### Post by Curufir on 2005-10-15
You're not alone :) .

[http://ubuntuforums.org/showthread.php?t=76309](http://ubuntuforums.org/showthread.php?t=76309)

---

### Post by CbrPad on 2005-10-15
Sweet.  My first attempt did nothing, in fact the splash screen never even appeared.  I'll try some different timeout values.  Though it beats me why the kernel is so slow getting started as my machine is fairly high-spec :confused:

---

### Post by jdong on 2005-10-15
Try booting with the word "splash" edited out from the GRUB boot commands (ESC, "e" at the GRUB countdown)

Are there still slowdowns?

---

### Post by CbrPad on 2005-10-15
Fraid so.   I've been doing that since I found it was clashing with my nvidia drivers on logout/shutdown.

---

### Post by jdong on 2005-10-15
Remove the word "quiet", too. Is there a particular spot where it likes to hang?


Note that with Breezy, "initramfs" has replaced "initrd", and peforms significantly more bootstrapping actions (including primitive hardware detection routines, RAID setup routines, suspend/resume routines, and so on), which could translate into a longer boot time. On my system (A64 3000+), about 5 seconds is spent on this step. The time it takes to perform these actions is primarily related to how fast your hardware initializes upon being detected.

Back in Hoary, this step would've been a part of the Hotplug step in bootup, so theoretically your Hotplug step should be taking less time now.

---

### Post by CbrPad on 2005-10-15
Excellent, finally got it, I had to set the timeout all the way up to 200.  

I timed going from grub to the login to take exactly 61 seconds.  It used to be about half that in Hoary so I guess some things haven't improved, but c'est la vie ;)    Other than that Breezy rocks so congrats to all involved !  
And many thanks for the help, much appreciated \\:D/

---

### Post by CbrPad on 2005-10-15
Actually, I spoke too soon.  I rebooted to admire my nice new usplash and it was gone ](*,)    I've tried every timeout from 100 to 420 and still haven't been able to get it back.  

From hitting enter on grub to the actual login appearing is taking anything from 60 secs to 1min30 and I'm presuming this variability is what's causing it to fail. 

E.g. it says "Decompressing Linux, ok booting the kernel" then "Loading, please wait", and it takes up to 40 seconds before the next string appears, "version 2.86" or something, and the boot process continues.

So I'm giving up, it's too maddening and I'll just have to remember that one time it did work, dem were the days  :-({|=

---

### Post by jdong on 2005-10-15
Ok, then the time is being spent in the initramfs image (Loading please wait....)

Boot into recovery mode, which spits out more text during the loading cycle, and try to pinpoint at which stage (what it says on the screen) initramfs hangs.

---

### Post by Curufir on 2005-10-15
Take a sledgehammer to it :) 

Edit /etc/init.d/module-init-tools

Change all instances of  usplash_write "TIMEOUT ..." to something like 240.

Actually, that won't help with the slow load of the kernel. Post the results of dmesg.

---

### Post by CbrPad on 2005-10-15
Sorry, was off fighting a war in Call of Duty :D 

Ok, here's what dmesg says... (are ye really gonna read this ??)

1000] mtrr: v2.0 (20020519)
[4294671.821000] ACPI: Subsystem revision 20050729
[4294671.830000] ACPI: Interpreter enabled
[4294671.830000] ACPI: Using IOAPIC for interrupt routing
[4294671.830000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.831000] PCI: Probing PCI hardware (bus 00)
[4294671.831000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.834000] Boot video device is 0000:01:00.0
[4294671.890000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.892000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
[4294671.893000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[4294671.893000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[4294671.893000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12)
[4294671.894000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, dis abled.
[4294671.894000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, dis abled.
[4294671.894000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 *10 11 12)
[4294671.895000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *5
[4294671.895000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *11
[4294671.896000] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[4294671.896000] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[4294671.896000] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
[4294671.898000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.898000] pnp: PnP ACPI init
[4294671.902000] pnp: PnP ACPI: found 12 devices
[4294671.902000] PnPBIOS: Disabled by ACPI PNP
[4294671.902000] PCI: Using ACPI for IRQ routing
[4294671.902000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps , post a report
[4294671.929000] pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
[4294671.929000] pnp: 00:01: ioport range 0x5000-0x500f has been reserved
[4294671.930000] Simple Boot Flag at 0x37 set to 0x1
[4294671.930000] audit: initializing netlink socket (disabled)
[4294671.930000] audit: initialized
[4294671.930000] highmem bounce pool size: 64 pages
[4294671.930000] VFS: Disk quotas dquot_6.5.1
[4294671.930000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.930000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.930000] devfs: boot_options: 0x0
[4294671.930000] Initializing Cryptographic API
[4294671.930000] isapnp: Scanning for PnP cards...
[4294672.283000] isapnp: No Plug & Play device found
[4294672.295000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 i rq 1,12
[4294672.297000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.297000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.297000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shari ng enabled
[4294672.297000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.298000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.298000] io scheduler noop registered
[4294672.299000] io scheduler anticipatory registered
[4294672.299000] io scheduler deadline registered
[4294672.299000] io scheduler cfq registered
[4294672.299000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294672.299000] NET: Registered protocol family 2
[4294672.309000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294672.309000] TCP established hash table entries: 262144 (order: 9, 2097152 b ytes)
[4294672.311000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294672.311000] TCP: Hash tables configured (established 262144 bind 65536)
[4294672.311000] NET: Registered protocol family 8
[4294672.311000] NET: Registered protocol family 20
[4294672.311000] ACPI wakeup devices:
[4294672.311000] PCI0 USB0 USB1 USB2 USB3 USB4 USB5 USB6 AC97 MC97 UAR1
[4294672.311000] ACPI: (supports S0 S3 S4 S5)
[4294672.312000] Freeing unused kernel memory: 168k freed
[4294672.327000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.341000] Capability LSM initialized
[4294672.350000] NET: Registered protocol family 1
[4294672.361000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.362000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294672.362000] ACPI: bus type ide registered
[4294672.368000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[4294672.368000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 11, using IRQ  20
[4294672.368000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[4294672.368000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (l evel, low) -> IRQ 20
[4294672.368000] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 4
[4294672.368000] VP_IDE: chipset revision 6
[4294672.369000] VP_IDE: not 100% native mode: will probe irqs later
[4294672.369000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:0 0:0f.1
[4294672.369000]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb: DMA
[4294672.369000]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd: DMA
[4294672.369000] Probing IDE interface ide0...
[4294672.753000] hda: Maxtor 6E040L0, ATA DISK drive
[4294673.008000] hdb: Maxtor 6B200P0, ATA DISK drive
[4294673.062000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.062000] Probing IDE interface ide1...
[4294699.647000] hdc: HL-DT-ST DVDRAM GSA-4040B, ATAPI CD/DVD-ROM drive
[4294699.902000] hdd: SAMSUNG SP1604N, ATA DISK drive
[4294699.954000] ide1 at 0x170-0x177,0x376 on irq 15
[4294699.954000] Probing IDE interface ide2...
[4294700.467000] Probing IDE interface ide3...
[4294700.979000] Probing IDE interface ide4...
[4294701.491000] Probing IDE interface ide5...
[4294702.005000] hda: max request size: 128KiB
[4294704.134000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/ 63, UDMA(133)
[4294704.134000] hda: cache flushes supported
[4294704.134000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
[4294704.139000] hdb: max request size: 1024KiB
[4294704.160000] hdb: 398297088 sectors (203928 MB) w/8192KiB Cache, CHS=24792/2 55/63, UDMA(133)
[4294704.161000] hdb: cache flushes supported
[4294704.161000]  /dev/ide/host0/bus0/target1/lun0: p1
[4294704.166000] hdd: max request size: 1024KiB
[4294704.167000] hdd: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/2 55/63, UDMA(100)
[4294704.167000] hdd: cache flushes supported
[4294704.167000]  /dev/ide/host0/bus1/target1/lun0: p1 p2 < p5 > p3
[4294704.186000] hdc: ATAPI 32X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[4294704.186000] Uniform CD-ROM driver Revision: 3.20
[4294704.397000] Attempting manual resume
[4294704.398000] swsusp: Suspend partition has wrong signature?
[4294704.454000] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.13
[4294704.454000] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
[4294704.454000] Copyright (c) 2004 Red Hat Inc.
[4294704.454000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 22 (level, low) -> I RQ 22
[4294704.454000] PCI: Via IRQ fixup for 0000:00:0e.0, from 10 to 6
[4294704.454000] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter
[4294704.454000] eth0: Ethernet Address: 00:50:8D:D1:9B:E8
[4294704.472000] SCSI subsystem initialized
[4294704.473000] libata version 1.11 loaded.
[4294704.473000] sata_via version 1.1
[4294704.473000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (l evel, low) -> IRQ 20
[4294704.473000] PCI: Via IRQ fixup for 0000:00:0f.0, from 11 to 4
[4294704.474000] sata_via(0000:00:0f.0): routed to hard irq line 4
[4294704.474000] ata1: SATA max UDMA/133 cmd 0xBC00 ctl 0xC002 bmdma 0xCC00 irq 20
[4294704.474000] ata2: SATA max UDMA/133 cmd 0xC400 ctl 0xC802 bmdma 0xCC08 irq 20
[4294704.675000] ata1: no device found (phy stat 00000000)
[4294704.675000] scsi0 : sata_via
[4294704.876000] ata2: no device found (phy stat 00000000)
[4294704.876000] scsi1 : sata_via
[4294704.889000] usbcore: registered new driver usbfs
[4294704.889000] usbcore: registered new driver hub
[4294704.890000] USB Universal Host Controller Interface driver v2.2
[4294704.890000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> I RQ 21
[4294704.890000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI US B 1.1 Controller
[4294704.952000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus num ber 1
[4294704.952000] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d800
[4294704.952000] hub 1-0:1.0: USB hub found
[4294704.952000] hub 1-0:1.0: 2 ports detected
[4294704.955000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> I RQ 21
[4294704.955000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI US B 1.1 Controller (#2)
[4294705.017000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus num ber 2
[4294705.017000] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000dc00
[4294705.017000] hub 2-0:1.0: USB hub found
[4294705.017000] hub 2-0:1.0: 2 ports detected
[4294705.020000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> I RQ 21
[4294705.020000] PCI: Via IRQ fixup for 0000:00:10.2, from 11 to 5
[4294705.020000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI US B 1.1 Controller (#3)
[4294705.082000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus num ber 3
[4294705.082000] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[4294705.082000] hub 3-0:1.0: USB hub found
[4294705.082000] hub 3-0:1.0: 2 ports detected
[4294705.085000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> I RQ 21
[4294705.085000] PCI: Via IRQ fixup for 0000:00:10.3, from 11 to 5
[4294705.085000] uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI US B 1.1 Controller (#4)
[4294705.147000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus num ber 4
[4294705.147000] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e400
[4294705.147000] hub 4-0:1.0: USB hub found
[4294705.147000] hub 4-0:1.0: 2 ports detected
[4294705.173000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> I RQ 21
[4294705.173000] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 5
[4294705.173000] ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
[4294705.173000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus num ber 5
[4294705.173000] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfa032000
[4294705.173000] ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 1 0 Dec 2004
[4294705.173000] hub 5-0:1.0: USB hub found
[4294705.173000] hub 5-0:1.0: 8 ports detected
[4294706.316000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[4294707.263000] Initializing USB Mass Storage driver...
[4294707.265000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294707.265000] usb-storage: device found at 2
[4294707.265000] usb-storage: waiting for device to settle before scanning
[4294707.265000] usbcore: registered new driver usb-storage
[4294707.265000] USB Mass Storage support registered.
[4294707.487000] ACPI: CPU0 (power states: C1[C1])
[4294707.630000] Attempting manual resume
[4294707.630000] swsusp: Suspend partition has wrong signature?
[4294707.642000] kjournald starting.  Commit interval 5 seconds
[4294707.642000] EXT3-fs: mounted filesystem with ordered data mode.
[4294708.988000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294711.419000] Adding 499928k swap on /dev/hda1.  Priority:-1 extents:1
[4294711.552000] EXT3 FS on hda2, internal journal
[4294712.269000]   Vendor: CBOX3     Model: USB Storage-SMC   Rev: 300A
[4294712.269000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294712.273000]   Vendor: CBOX3     Model: USB Storage-CFC   Rev: 300A
[4294712.273000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294712.277000]   Vendor: CBOX3     Model: USB Storage-MMC   Rev: 300A
[4294712.277000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294712.280000]   Vendor: CBOX3     Model: USB Storage-MSC   Rev: 300A
[4294712.280000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294712.282000] usb-storage: device scan complete
[4294716.366000] parport: PnPBIOS parport detected.
[4294716.366000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294716.461000] lp0: using parport0 (interrupt-driven).
[4294716.496000] mice: PS/2 mouse device common for all mice
[4294716.524000] ieee1394: Initialized config rom entry `ip1394'
[4294716.530000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294716.557000] Linux agpgart interface v0.101 (c) Dave Jones
[4294716.575000] nvidia: module license 'NVIDIA' taints kernel.
[4294716.579000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> I RQ 16
[4294716.579000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667 Fri Jun 17 07:01:04 PDT 2005
[4294716.645000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun  0
[4294716.659000] Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun  1
[4294716.677000] Attached scsi removable disk sdc at scsi2, channel 0, id 0, lun  2
[4294716.692000] Attached scsi removable disk sdd at scsi2, channel 0, id 0, lun  3
[4294716.723000] logips2pp: Detected unknown logitech mouse model 62
[4294716.777000] input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
[4294716.985000] ts: Compaq touchscreen protocol output
[4294720.073000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294720.740000] cdrom: open failed.
[4294721.494000] kjournald starting.  Commit interval 5 seconds
[4294721.494000] EXT3 FS on hda3, internal journal
[4294721.494000] EXT3-fs: mounted filesystem with ordered data mode.
[4294721.534000] kjournald starting.  Commit interval 5 seconds
[4294721.534000] EXT3 FS on hdb1, internal journal
[4294721.534000] EXT3-fs: mounted filesystem with ordered data mode.
[4294722.463000] agpgart: Detected AGP bridge 0
[4294722.477000] agpgart: AGP aperture is 128M @ 0xf0000000
[4294722.665000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294722.674000] shpchp: shpc_init : shpc_cap_offset == 0
[4294722.674000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294722.742000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294722.742000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 23 (level, low) -> I RQ 23
[4294722.742000] PCI: Via IRQ fixup for 0000:00:07.0, from 5 to 7
[4294722.798000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[23]  MMIO=[fa0310 00-fa0317ff]  Max Packet=[2048]
[4294723.337000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> I RQ 22
[4294723.337000] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 6
[4294723.337000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294724.064000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508d0000d09be8]
[4294726.319000] Real Time Clock Driver v1.12
[4294726.368000] input: PC Speaker
[4294726.431000] Floppy drive(s): fd0 is 1.44M
[4294726.453000] FDC 0 is a post-1991 82077
[4294728.043000] Velocity is AUTO mode
[4294728.055000] NET: Registered protocol family 17
[4294729.723000] eth0: Link autonegation speed 100M bps full duplex
[4294747.954000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294747.954000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4294747.954000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[4294748.209000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294748.209000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4294748.209000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[4294751.462000] NET: Registered protocol family 10
[4294751.462000] Disabled Privacy Extensions on device c0321b80(lo)
[4294751.462000] IPv6 over IPv4 tunneling driver
[4294761.898000] eth0: no IPv6 routers present

---

### Post by Curufir on 2005-10-15
What is it you've actually got on USB? A disk or something like a camera?

USB mass storage isn't something I've played with much, but I'd imagine it starts up quite a bit slower than IDE/SCSI especially if Ubuntu is trying to automount it later in the boot process.

---

### Post by CbrPad on 2005-10-15
I don't actually have anything attached on USB, though there is a front panel card reader which could be what you mean ?

---

### Post by Ferio on 2005-10-15
It didn't work for me, the splash disappears as soon as the Configuring Network Interfaces... appears; it's taking more than 40 seconds for it to finish. I'm using the 686-smp kernel, it didn't fails with the 386 one.

---

### Post by Curufir on 2005-10-15
[QUOTE=CbrPad]I don't actually have anything attached on USB, though there is a front panel card reader which could be what you mean ?[/QUOTE]

I guess that could be it (And it _is_ a guess :) ).

Breezy doesn't exactly boot quickly on my system either (30+ seconds) and I've got a lot less stuff in my box. Might be that you're just gonna have to live without the pretty boot screen for now :D .

---

### Post by CbrPad on 2005-10-15
Well the splash would be nice but I've managed without it so far.  It's the bootup time that's really annonying, averaging 1min 20, a good three times longer than Hoary.  I guess I'll pull out that reader and see what happens, plus find some services I can do without.  Thanks once more for your help.

---

### Post by Curufir on 2005-10-15
Odd stuff. I'd go with jdong's suggestion and boot in 'rescue' mode to see where the big delays are happening. My guess would be network, ntpdate and hotplug.

---

### Post by pardasaniman on 2005-10-17
Try editing your kernel boot parameters to take out splash and quiet.. You'll be able to see where you get frozen... and perhaps even fix it.


It should not take that long to boot!

---

### Post by Ferio on 2005-10-28
Well, if you asked me to explain it, I couldn't do it: Breezy was working really bad for me, so I tried Fedora Core 4 (which I would never do again, I swear!) and went back to Breezy, and now everything works better than fine. My Usplash is not going away and the time my system spends loading is shorter than Hoary by a minute, more or less. Well done, ramdomness! ;)

---

### Post by sabaoth on 2005-10-29
Well, it is cleaner if you do that in the script which loads Usplash :) And that way you make sure nothing happens between the load of Usplash and the setting of the timeout, as it is just the next step...

[http://ubuntuforums.org/showpost.php?p=452411&postcount=17](http://ubuntuforums.org/showpost.php?p=452411&postcount=17)

---

### Post by docmanny on 2005-10-30
1 min 20 seconds?? I'm jealous!! I'm averaging 3:45. 
Why, I don't know.. Hotplug is part of it, but its quite painful.

I'm running a P4-3GHz processor with 1Gb of RAM. Any suggestions?

---

