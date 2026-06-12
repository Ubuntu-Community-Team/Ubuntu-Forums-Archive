---
title: "Sound fails with gstreamer / esd"
date: 2005-08-04
forum: Desktop Environments
---

### Post by bingobango on 2005-08-04
I am a new user of Ubuntu, and, like many others, i want to be able to play mp3s on my computer.  after installing gstreamer the other day, everything was working perfectly playing music with rhythmbox.

today, however, i get no sound.  :(  rather, i get some errors from rhythmbox saying

1.  "Could not pause playback"
and
2.  "Could not open resource for writing"

i have tried playing sound with xmms, rhythmbox, and even the system sounds don't work.  the speakers work when i try them on another machine.  someone on #ubuntu said this problem is due to an ESD/gstreamer conflict, but i'm not sure what this means.

i'm using an nVidia nForce2 to play the music, and, again, this worked in the past, and i don't recall doing anything to the audio setup that might have borked it.  can someone help?

thanks!
bingo

---

### Post by ^NoX on 2005-08-04
try the following:
```
sudo apt-get install beep-media-player
sudo beep-media-player

``` 
try to play mp3s with this player, as root.

in addition, work as instructed in this howto:
[http://ubuntuforums.org/showthread.php?t=44753&highlight=howto+ALSA](http://ubuntuforums.org/showthread.php?t=44753&highlight=howto+ALSA)

---

### Post by bingobango on 2005-08-04
hi!  thanks for the feedback.  there's good news and bad news...

good news:  i have a snappy new media player!  ;P

bad news:  still no audio.  i followed the instructions on the link you gave me, but it didn't help.  when trying to play an mp3 as user/root, i get the following error message from beep-media-player:

Couldn't open audio.

Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.


any ideas about where to go from here?  thanks!!

bingo

---

### Post by bingobango on 2005-08-05
not sure if this helps, but when i try running gedit (!) i get this ALSA error message.

ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave

cause you know there's some pretty awesome sounds on gedit.   :roll: 

bingo

---

### Post by bingobango on 2005-08-05
bump

---

### Post by bingobango on 2005-08-08
bump again?  does anyone out there think they can help?

bingo

---

### Post by aveline on 2005-08-09
[QUOTE=bingobango]bump again?  does anyone out there think they can help?

bingo[/QUOTE]
 go to the unofficial guide & find the sound section where it says "install sound properly"

aveline

---

### Post by bingobango on 2005-08-09
hi aveline,

thanks for the reply!

i still get the same error messages, even after following the unofficial ubuntu guide's instructions.  do you or anyone else have any other suggestions or sources of knowledge?

bingo

---

### Post by aveline on 2005-08-09
[QUOTE=bingobango]hi aveline,

thanks for the reply!

i still get the same error messages, even after following the unofficial ubuntu guide's instructions.  do you or anyone else have any other suggestions or sources of knowledge?

bingo[/QUOTE]
 post output of dmesg after a reboot *specifically look for lines with the word audio or soundcard or something like that in it...* just type "dmesg" in a term after booting, then cut paste relevant lines.

do same ... put "lspci" in a term pls.  No quotes mind you! :P

aveline

---

### Post by bingobango on 2005-08-09
hi aveline.  thanks so much for the help.  here's the output for lspci:

```

$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (r ev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller  (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia a udio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 139 4) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 96 00]
0000:02:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Se condary)

```

here's some grepped dmesg output
$ dmesg | grep -i audio
usbcore: registered new driver snd-usb-audio

$ dmesg | grep -i nvidia
ACPI: RSDP (v000 Nvidia                                ) @ 0x000f6b60
ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff79c0
ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
agpgart: Detected NVIDIA nForce2 chipset
ohci_hcd 0000:00:02.0: nVidia Corporation nForce2 USB Controller
ohci_hcd 0000:00:02.1: nVidia Corporation nForce2 USB Controller (#2)
ehci_hcd 0000:00:02.2: nVidia Corporation nForce2 USB Controller


here's the whole dmesg output
```

$ dmesg
ges, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.2 present.
ACPI: RSDP (v000 Nvidia                                ) @ 0x000f6b60
ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff79c0
ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
ACPI: PM-Timer IO Port: 0x4008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 6:10 APIC version 16
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: BIOS IRQ0 pin2 override ignored.
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1830.244 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 511772k/524224k available (1436k kernel code, 11864k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3620.86 BogoMIPS (lpj=1810432)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000020 00000000 00000000
CPU: AMD Athlon(tm) XP 2500+ stepping 00
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=0 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfb420, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: nForce2 C1 Halt Disconnect fixup
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 10 11 *12 14 15)
ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 10 11 *12 14 15)
ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
ACPI: PCI Interrupt Link [APCE] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 13 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
pnp: 00:00: ioport range 0x4400-0x447f has been reserved
pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
pnp: 00:00: ioport range 0x4200-0x427f has been reserved
pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
pnp: 00:01: ioport range 0x5000-0x503f has been reserved
pnp: 00:01: ioport range 0x5100-0x513f has been reserved
audit: initializing netlink socket (disabled)
audit(1123637100.145:0): initialized
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
Cannot allocate resource for EISA slot 4
Cannot allocate resource for EISA slot 5
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
HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1 
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Fan [FAN] (on)
ACPI: Thermal Zone [THRM] (32 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
NFORCE2: IDE controller at PCI slot 0000:00:09.0
NFORCE2: chipset revision 162
NFORCE2: not 100% native mode: will probe irqs later
NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: Maxtor 93073U6, ATA DISK drive
hdb: ST3120026A, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 60030432 sectors (30735 MB) w/2048KiB Cache, CHS=59554/16/63, UDMA(66)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
hdb: max request size: 1024KiB
hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
hdb: cache flushes supported
 /dev/ide/host0/bus0/target1/lun0: p1
Probing IDE interface ide1...
hdc: Hewlett-Packard CD-Writer Plus 8000, ATAPI CD/DVD-ROM drive
hdd: TOSHIBA DVD-ROM SD-M1302, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory...  -\|/done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1244996k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 20X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 40X DVD-ROM drive, 256kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected NVIDIA nForce2 chipset
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 64M @ 0xe0000000
i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 22 (level, high) -> IRQ 22
ohci_hcd 0000:00:02.0: nVidia Corporation nForce2 USB Controller
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 22, pci mem 0xe8080000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 21 (level, high) -> IRQ 21
ohci_hcd 0000:00:02.1: nVidia Corporation nForce2 USB Controller (#2)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ohci_hcd 0000:00:02.1: irq 21, pci mem 0xe8083000
ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
usb 1-1: new low speed USB device using ohci_hcd and address 2
ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 20 (level, high) -> IRQ 20
ehci_hcd 0000:00:02.2: nVidia Corporation nForce2 USB Controller
PCI: Setting latency timer of device 0000:00:02.2 to 64
ehci_hcd 0000:00:02.2: irq 20, pci mem 0xe8086000
ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
PCI: cache line size of 64 is not supported by device 0000:00:02.2
ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 6 ports detected
usb 2-2: new full speed USB device using ohci_hcd and address 2
usbcore: registered new driver hiddev
usbhid: probe of 1-1:1.0 failed with error -5
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 1-1: USB disconnect, address 2
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.30.
ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:04.0[A] -> GSI 22 (level, high) -> IRQ 22
PCI: Setting latency timer of device 0000:00:04.0 to 64
ohci_hcd 0000:00:02.0: wakeup
ohci_hcd 0000:00:02.1: wakeup
eth0: forcedeth.c: subsystem: 0147b:1c00 bound to 0000:00:04.0
usb 1-1: new low speed USB device using ohci_hcd and address 3
input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-1
ts: Compaq touchscreen protocol output
usb 2-2: new full speed USB device using ohci_hcd and address 3
eth0: no link during initialization.
eth0: link up.
ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 21 (level, high) -> IRQ 21
PCI: Setting latency timer of device 0000:00:06.0 to 64
usbcore: registered new driver snd-usb-audio
intel8x0_measure_ac97_clock: measured 49008 usecs
intel8x0: clocking to 50409
NET: Registered protocol family 17
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI Interrupt Link [APCM] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:0d.0[A] -> GSI 20 (level, high) -> IRQ 20
PCI: Setting latency timer of device 0000:00:0d.0 to 64
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[e8084000-e80847ff]  Max Packet=[2048]
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ohci1394: fw-host0: SelfID received outside of bus reset sequence
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000000508df643d3]
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present

```

i didn't see anything glaringly obvious for why it didn't work.  can you recommend something?

thanks!

bingo

---

### Post by bingobango on 2005-08-09
WHOA

ok, apparently i can hear sound through flash.  what gives?  why can i hear sound from a browser, but not from an audio player?

bingo

---

### Post by aveline on 2005-08-10
[QUOTE=bingobango]WHOA

ok, apparently i can hear sound through flash.  what gives?  why can i hear sound from a browser, but not from an audio player?

bingo[/QUOTE]
 that is very strange indeed... hm... which audio players are you trying?? i assume you've tried unmuting things?  If you're using Xmms, in prefs try changing its sound outputs to Arts or OSS.

you can also put at the end of the kernel line in grub (try these in this order and reboot after each... pita i know but it may help): 

- acpi=off 
- nolacpi  (for VIA chipsets on mobos usually but it may work here too)
- hw-detect/start_pcmcia=false (this is relevant to debian distros which I got from the help screens when booting Ubuntu, on one of my desktops ubunut crazily enough detects pcmcia things but it has no pcmcia slots or cards???  telling it not to install or detect this helped run an NIC once)

Out of desperation, from your dmesg output I saw this & thought you can try it too:

PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.

so put the pci=routeirq at the end of the kernel line in grub too... see if it works.

aveline

---

### Post by bingobango on 2005-08-17
aveline,

THANK YOU!

i finally was horsing around in xmms and changed the output plugin to alsa (again), but this time, i changed my hardware output device from "default" to "hw1,0".  that made the difference!

thanks for your suggestions and patience.  people like you are the reason ubuntu is going to be a success!  :)

bingo

---

