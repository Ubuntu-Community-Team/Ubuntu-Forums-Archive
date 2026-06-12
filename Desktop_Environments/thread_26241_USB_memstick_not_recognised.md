---
title: "USB memstick not recognised"
date: 2005-04-12
forum: Desktop Environments
---

### Post by vermeersch on 2005-04-12
PC at work:
USB memstick plugged in 
when I give command fdisk -l, there should be an sda* mention somewhere.
But this is the result of fdisk -l:
root@cmtc58:/home/u80lve # fdisk -l

Schijf /dev/hda: 20.5 GB, 20547841536 bytes
16 koppen, 63 sectoren/spoor, 39813 cylinders
Eenheden = cylinders van 1008 * 512 = 516096 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1       24321    12257563+   7  HPFS/NTFS
/dev/hda2           24321       39812     7807590    f  W95 Ext'd (LBA)
/dev/hda5           24321       26409     1052226    b  W95 FAT32
/dev/hda6           26616       32481     2955928+  83  Linux
/dev/hda7           38777       39812      522081   82  Linux swap / Solaris
/dev/hda8           32481       38776     3172806   83  Linux

Partitietabel ingangen zijn niet in schijfvolgorde
root@cmtc58:/home/u80lve #

where is /dev/sda1?

same problem in mandrake

not in windows.

On my home PC, hoary recognises sda1 without problem.
Qué pasa?

Thx

---

### Post by vermeersch on 2005-04-13
anybody home?

---

### Post by Klin'Targ on 2005-04-13
Could you post the last 10 or so lines of dmesg after plugging it it? If there is a problem reading the stick for some reason, it would spit an error there. Also, try plugging it into a different USB port.

---

### Post by vermeersch on 2005-04-13
plugging in the memstick in other USB port gives same results

dmesg gives the following messages:

    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: MAXTOR 6L020L1, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 40132503 sectors (20547 MB) w/1819KiB Cache, CHS=39813/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3
Probing IDE interface ide1...
hdc: HL-DT-ST CD-RW GCE-8080N, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 313228k swap on /dev/hda6.  Priority:-1 extents:1
EXT3 FS on hda3, internal journal
hdc: ATAPI 24X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
hdc: packet command error: error=0x50
ide: failed opcode was 100
cdrom: open failed.
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
input: PC Speaker
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel i845 Chipset.
agpgart: Maximum main memory to use for agp memory: 203M
agpgart: AGP aperture is 64M @ 0xf0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
hw_random: RNG not detected
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
uhci_hcd 0000:00:1f.2: Intel Corp. 82801BA/BAM USB (Hub #1)
PCI: Setting latency timer of device 0000:00:1f.2 to 64
uhci_hcd 0000:00:1f.2: irq 19, io base 0xff80
uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
uhci_hcd 0000:00:1f.4: Intel Corp. 82801BA/BAM USB (Hub #2)
PCI: Setting latency timer of device 0000:00:1f.4 to 64
uhci_hcd 0000:00:1f.4: irq 18, io base 0xff60
uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49712 usecs
intel8x0: clocking to 41141
3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
0000:02:0c.0: 3Com PCI 3c905C Tornado at 0xdc80. Vers LK1.1.19
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
eth0: no IPv6 routers present
[drm] Initialized drm 1.0.0 20040925
[drm] Initialized r128 2.5.0 20030725 on minor 0: ATI Technologies Inc Rage 128 Pro Ultra TF
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode

---

### Post by vermeersch on 2005-04-13
????

---

### Post by Klin'Targ on 2005-04-13
Hmm interesting... I don't see anything in dmesg relating to your USB Flash drive. After plugging it in, you should see something like this:```
hub.c: new USB device 02:01.2-4, assigned address 2
usb.c: USB device 2 (vend/prod 0x781/0x5150) is not claimed by any active driver.
Initializing USB Mass Storage driver...
usb.c: registered new driver usb-storage
scsi1 : SCSI emulation for USB Mass Storage devices
  Vendor: SanDisk   Model: Cruzer Mini       Rev: 0.1
  Type:   Direct-Access                      ANSI SCSI revision: 02
WARNING: USB Mass Storage data integrity not assured
USB Mass Storage device found at 2
USB Mass Storage support registered.
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
SCSI device sda: 250879 512-byte hdwr sectors (128 MB)
sda: Write Protect is off
 sda: sda1

```on the end of your dmesg list.

Is the flash drive getting enough power (does the LED turn on on it)?

---

### Post by vermeersch on 2005-04-14
I suppose so, because it works without a problem in win2k (have a dual boot on this PC) and on my PC at home it works both in windows and in ubuntu, so it has to be a problem with this PC at my work (DELL). When I run fdisk -l, neither sda nor sda1 appear in the list (at home they do). I don't think it is distro-related either, because before I had a triple boot with win, ubuntu and mandrake, and both ubuntu and mandrake didn't show the sda* in fdisk -l. Linux does not seem to recognise the USBstick on this specific machine. Changing stick to other USB-port does not help. Sthing BIOS-related, hardware-related? But then why does it work in windows? I made two nodes (sda anbd sda1) manually in /dev, but when I mounted them, got the message it was not a valid block-device.

---

### Post by vermeersch on 2005-04-14
this is the result of fdisk -l on my home PC:

 # fdisk -l

Schijf /dev/hda: 40.9 GB, 40982151168 bytes
255 koppen, 63 sectoren/spoor, 4982 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

Apparaat Boot Start Einde Blokken Id Systeem
/dev/hda1 * 1 769 6176961 b W95 FAT32
/dev/hda2 770 4131 27005265 f W95 Ext'd (LBA)
/dev/hda3 4132 4982 6835657+ 83 Linux
/dev/hda5 770 2144 11044656 b W95 FAT32
/dev/hda6 2145 4090 15631213+ b W95 FAT32
/dev/hda7 4091 4131 329301 82 Linux swap / Solaris

Schijf /dev/sda: 261 MB, 261372928 bytes
9 koppen, 63 sectoren/spoor, 900 cylinders
Eenheden = cylinders van 567 * 512 = 290304 bytes

Apparaat Boot Start Einde Blokken Id Systeem
/dev/sda1 * 1 900 255118+ 6 FAT16


sda1 stick is formatted in FAT16. I'll try formatting it in FAT32, maybe it has to do sthing with the format.

---

### Post by vermeersch on 2005-04-14
formatted stick in FAT32
still not recognised when fdisk -l

but this is interesting: dmesg gave me the following messages:

scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
[drm] Initialized drm 1.0.0 20040925
[drm] Initialized r128 2.5.0 20030725 on minor 0: ATI Technologies Inc Rage 128 Pro Ultra TF
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
eth0: no IPv6 routers present
usb 2-2: USB disconnect, address 4
usb-storage: device scan complete
usb 2-2: new full speed USB device using uhci_hcd and address 5
usb 2-2: khubd timed out on ep0in
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
usb 2-2: USB disconnect, address 5
scsi: Device offlined - not ready after error recovery: host 1 channel 0 id 0 lun 0
usb-storage: device scan complete
usb 2-2: new full speed USB device using uhci_hcd and address 6
usb 2-2: khubd timed out on ep0in
usb 2-2: device not accepting address 6, error -71
usb 2-2: new full speed USB device using uhci_hcd and address 8
usb 2-2: khubd timed out on ep0in
usb 2-2: string descriptor 0 read error: -71
usb 2-2: string descriptor 0 read error: -71
scsi2 : SCSI emulation for USB Mass Storage devices
usb 2-2: USB disconnect, address 8
usb-storage: device found at 8
usb-storage: waiting for device to settle before scanning
usb 2-2: new full speed USB device using uhci_hcd and address 9
usb 2-2: khubd timed out on ep0in
usb 2-2: device not accepting address 9, error -71
usb 2-2: new full speed USB device using uhci_hcd and address 11
usb 2-2: khubd timed out on ep0in

---

### Post by vermeersch on 2005-04-14
POBLEM SOLVED!!

wrote NOAPIC and ACPI=OFF in /boot/grub/menu.lst

USB icon is automatically mounted on desktop.

What do these NOAPIC and ACPI=OFF mean? 

Thx for yor help

---

### Post by Klin'Targ on 2005-04-14
Glad to hear it. ACPI is a power management interface. Your computer may not support it nicely (some don't), which sounds like it was causing the problem. ACPI=OFF and NOACPI will disable ACPI, probably forcing your machine to use the older APM power management interface that some machines support better.

---

