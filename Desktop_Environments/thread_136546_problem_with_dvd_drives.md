---
title: "problem with dvd drives"
date: 2006-02-26
forum: Desktop Environments
---

### Post by fotisman on 2006-02-26
i have a problem with my dvd-roms. Yesterday they stopped working. I mean when i insert a cd into the drive the light remains open for a while and then it closes. But it does not mount the cd. If i go to my computer and try to mount manually the cd it says: mount: No medium found.

BUT if i insert a dvd-movie its working just fine.

I don't understand...

Please someone help me.
thanx in advance

---

### Post by endy on 2006-02-26
Is it an audio CD? If so you can't mount them, if you are talking about a data CD then you may be unlucky enough to have hardware problems. Can you test the DVD drive in another PC? Or if you have another partition with another Linux / Windows install try to see if it works in that.

---

### Post by fotisman on 2006-02-26
It's not working with any cd, audio or not. But audios cd's arent supposed to play? I don't have any other OS or pc. But drives are new. They worked perfect before with windows and with ubuntu. I dont know what happend.

Is there a solution to fix it for sure? an update or smth?

thank you for your help

---

### Post by endy on 2006-02-26
Audio CDs don't have a file system (AFAIK) so they cannot be mounted - they can still be played though. Can you try mounting some data CDs and post the output of the following:

```
dmesg | tail
```

This may shed more light on what's going on.

---

### Post by fotisman on 2006-02-26
I can't mount anything! Audio cd's, data cd's, nothing! ONly dvd-movies!

WHen i write the command u gave me, i get:

```
atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
```

Any ideas?

---

### Post by endy on 2006-02-26
Ok that doesn't look like error messages coming from your DVD drive, try posting the full output from just "dmesg" after it fails to mount the disc. Hopefully we'll be able to see what's going on.

---

### Post by fotisman on 2006-02-27
Ok. This is what i get from the "dmesg" command:
```
g for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=4
PCI: Using MMCONFIG
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 20 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:07: ioport range 0x290-0x297 has been reserved
audit: initializing netlink socket (disabled)
audit(1141058112.923:0): initialized
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
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
P0P1 P0P3 P0P4 P0P5 P0P6 P0P7 PS2K PS2M UAR1 UAR2 USB1 USB2 USB3 USB4 EUSB MC97
ACPI: (supports S0 S1 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Processor [CPU1] (supports 8 throttling states)
NET: Registered protocol family 1
SCSI subsystem initialized
libata version 1.10 loaded.
ata_piix version 1.03
ACPI: PCI interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ata1: SATA max UDMA/133 cmd 0xAC00 ctl 0xA882 bmdma 0xA400 irq 19
ata2: SATA max UDMA/133 cmd 0xA800 ctl 0xA482 bmdma 0xA408 irq 19
ata1: dev 0 cfg 49:2f00 82:346b 83:7f61 84:4003 85:3469 86:3c41 87:4003 88:207f
ata1: dev 0 ATA, max UDMA/133, 488397168 sectors: lba48
ata1: dev 0 configured for UDMA/133
scsi0 : ata_piix
ATA: abnormal status 0x7F on port 0xA807
ata2: disabling port
scsi1 : ata_piix
elevator: using anticipatory as default io scheduler
  Vendor: ATA       Model: WDC WD2500JD-00H  Rev: 08.0
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda5, internal journal
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH6: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH6: chipset revision 3
ICH6: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
Probing IDE interface ide0...
hda: _NEC DVD_RW ND-3520A, ATAPI CD/DVD-ROM drive
hdb: TSSTcorpDVD-ROM TS-H352A, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
hdb: ATAPI 48X DVD-ROM drive, 512kB Cache
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 915G Chipset.
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: AGP aperture is 256M @ 0x0
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ACPI: PCI interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:1b.0 to 64
ALSA /usr/src/modules/alsa-driver/pci/azx/azx.c:503: codec_mask = 0x1
ALSA /usr/src/modules/alsa-driver/pci/azx/patch_realtek.c:952: hda_codec: Unknown model for ALC880
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
uhci_hcd 0000:00:1d.0: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 23, io base 0x9880
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0x9c00
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xa000
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0xa080
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xd7cff800
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
hw_random: RNG not detected
ACPI: PCI interrupt 0000:01:0b.0[A] -> GSI 22 (level, low) -> IRQ 22
drivers/media/dvb/b2c2/skystar2.c: FlexCopIIB(rev.195) chip found
drivers/media/dvb/b2c2/skystar2.c: the chip has 38 hardware filters
DVB: registering new adapter (SkyStar2).
DVB: registering frontend 0 (ST STV0299 DVB-S)...
sk98lin: no version for "struct_module" found: kernel tainted.
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
sk98lin: Network Device Driver v8.23.1.3
(C)Copyright 1999-2005 Marvell(R).
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:02:00.0 to 64
eth0: Yukon Gigabit Ethernet 10/100/1000Base-T Adapter
      PrefPort:A  RlmtMode:Check Link State
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
ALSA /usr/src/modules/alsa-driver/pci/azx/azx.c:939: azx_pcm_prepare: bufsize=0x10000, fragsize=0x2000, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x5, stream=0x0, channel=0, format=0x0
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x4, stream=0x0, channel=0, format=0x0
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ALSA /usr/src/modules/alsa-driver/pci/azx/azx.c:939: azx_pcm_prepare: bufsize=0x10000, fragsize=0x2000, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/azx.c:939: azx_pcm_prepare: bufsize=0xc030, fragsize=0x6018, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x7, stream=0x0, channel=0, format=0x0
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x5, stream=0x0, channel=0, format=0x0
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x4, stream=0x0, channel=0, format=0x0
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
ALSA /usr/src/modules/alsa-driver/pci/azx/azx.c:939: azx_pcm_prepare: bufsize=0xc030, fragsize=0x6018, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x11
ALSA /usr/src/modules/alsa-driver/pci/azx/hda_codec.c:457: hda_codec_setup_stream: NID=0x7, stream=0x0, channel=0, format=0x0
CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
PPP BSD Compression module registered
PPP Deflate Compression module registered
atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

```

Also yesterday i got this message in a small window:
```
"Error: Failed to initialize hal"
```

I think i saw it once long time ago, but i saw it also yesterday, i don't know what is it.

thanx for all again...

---

### Post by endy on 2006-02-28
Are you sure you had the error occur before running the "dmesg" command, I'm certainly no expert but nothing is glaringly obvious in the output that points to a problem with your DVD drive.

Regarding the HAL failure, this could well be the problem, as although I know little about HAL I know it stands for Hardware Abstraction Layer and could well be where the problem lies. Sorry I can't be more help, maybe someone else will jump in this thread and point out what I missed.

---

