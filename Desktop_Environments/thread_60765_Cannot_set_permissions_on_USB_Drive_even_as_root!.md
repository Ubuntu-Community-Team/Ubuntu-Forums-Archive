---
title: "Cannot set permissions on USB Drive even as root!"
date: 2005-08-29
forum: Desktop Environments
---

### Post by Nolgthorn on 2005-08-29
I have just started a fresh install of Hoary Hedgehog and installed a few things as outlined in ubuntuguide.org now I notice I can't seem to set permissions like I want them on my USB Drive.

Setting it up so that my websites directory can be accessed by apache. When I try and change the permissions as 'nathan' it says I am not the owner, but that 'nathan - Nathan Jawgaping' is... When I launch nautilus as root then try and change the permissions, it keeps switching the permissions I change back to what they were.

Help please! I need to change my permissions from 700 anywhere else and I can change them fine.

---

### Post by Nolgthorn on 2005-08-29
[QUOTE=Nolgthorn]I have just started a fresh install of Hoary Hedgehog and installed a few things as outlined in ubuntuguide.org now I notice I can't seem to set permissions like I want them on my USB Drive.

Setting it up so that my websites directory can be accessed by apache. When I try and change the permissions as 'nathan' it says I am not the owner, but that 'nathan - Nathan Jawgaping' is... When I launch nautilus as root then try and change the permissions, it keeps switching the permissions I change back to what they were.

Help please! I need to change my permissions from 700 anywhere else and I can change them fine.[/QUOTE]
 bump.

---

### Post by cwaldbieser on 2005-08-29
[QUOTE=Nolgthorn]bump.[/QUOTE]
If you mount the USB drive and then cd to the mountpoint (probably in /media somewhere), and then do an ls -l, do the files appear to to be owned by your user, or does some number show up where the user and group normally appears?

Also, do you know what kind of filesystem is on the USB drive?

---

### Post by jdodson on 2005-08-29
if you are using a generic FAT filesystem, you can not get permission support to persist.

---

### Post by Nolgthorn on 2005-08-29
The partitions are definately Fat32... when I do ls -l this is what I get:
```
drwx------  14 nathan nathan 32768 1979-12-31 23:00 Websites
```
There it is "nathan" is definately my Administrator account and I'm the only one who uses this computer. But I can't change the permissions or sudo change it's permissions.

---

### Post by ubuntme on 2005-08-30
How is your drive mounted? i.e. what does you fstab look like?

cat /etc/fstab

---

### Post by Nolgthorn on 2005-08-31
Thanks ubuntme for your response. I assume it is mounted in the default way that Ubuntu likes to mount things as it is a fresh install and I did not configure anything to do with my USB drive yet. My fstab makes no mention of the individual partitions on the drive, the only mention is my USB drive as a whole as such:
> /dev/sda        /media/usb0     auto    rw,user,noauto  0       0
But I am using /media/STORAGE2/Websites as the folder apache should access. STORAGE2 is the name I've chosen for the partition on the drive and it does try and access the device because I get 403 Forbidden from my web browser at localhost/Url-path/.

Is there any way I can give apache administrator rights, or do I not want to do that?

---

### Post by schdefan on 2005-08-31
Maybe you set some read and write options on windows to your directory WebSites.
schdefan

---

### Post by Nolgthorn on 2005-08-31
"/" => Read none none, Read none none, Read none none (444) root [no way to change permissions]
"/media" => Read Write Execute, Read Write Execute, Read Write Execute (777) root [changed permissions as root]
"/media/STORAGE2" => Read Write Execute, none none none, none none none (700) nathan [no way to change permissions]
"/media/STORAGE2/Websites" => Same as above

My CD-RW works and that is located in /media so I would assume I'd be able to change permissions to the USB drive too. I did format as FAT 32, and I checked now with that (nifty) Gparted System Tool to confirm again the external drive is Fat32.

Darn it that is very frustrating I lost all of my SQL tables in the format because I forgot to back them up. I'm going to go cry now that I broke absolutely everything!

Maybe my best solution would be just move all the Website stuff onto the internal drive, then use USB for backing it up periodically? I went ahead with the format because I had time for it, but with the SQL tables I'm going to fall behind pretty soon.

---

### Post by schdefan on 2005-09-01
You can build an extra partition on your external drive with an ext3 format and then copy your data on that partition. But it sounds very strange that you can´t read data from the fat32 partition. Does that problem appear onl y when you use it as web space for apache.
Maybe its an apache configuration issue.
So try to copy paste some files in nautilus although i think you have already tried this.
Post the parts of ```
dmesg
``` regarding your drive.

schdefan

---

### Post by Nolgthorn on 2005-09-01
I am using fat32 because this information normally needs to be accessed across several operating systems. It shouldn't be an issue with an apache configuration because I haven't changed anything but rather followed the direction on ubuntuguide to the t.

The only strange thing is that I can't seem to change the permissions on the USB drive away from just owner-access. If I could somehow change the configuration of apache so that it runs as root... or so it gathers the information off my hard drive as I do, then everything would work.

I have no idea what dmesg is, but I looked it up and tried to execute it. The information I got back is way too dificult for me to read and I'm sorry I don't know which parts of it will help:

```
nathan@ubuntuMilkcube:~$ dmesg
disabled) audit(1125361708.445:0): initialized
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
ACPI: (supports S0 S1 S4 S4bios S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
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
hda: Maxtor 6Y080L0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
Probing IDE interface ide1...
hdc: Pioneer DVD-ROM ATAPIModel DVD-104S 011, ATAPI CD/DVD-ROM drive
hdd: LITE-ON LTR-48246S, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: hda2: orphan cleanup on readonly fs
ext3_orphan_cleanup: deleting unreferenced inode 669723
ext3_orphan_cleanup: deleting unreferenced inode 669709
ext3_orphan_cleanup: deleting unreferenced inode 669654
ext3_orphan_cleanup: deleting unreferenced inode 669651
ext3_orphan_cleanup: deleting unreferenced inode 669647
EXT3-fs: hda2: 5 orphan inodes deleted
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 851404k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
hdc: ATAPI DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
ts: Compaq touchscreen protocol output
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 19 (level, high) -> IRQ 19
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
DOR0=4
floppy interrupt on bizarre fdc 1
handler=00000000
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected NVIDIA nForce2 chipset
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 64M @ 0xe0000000
i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5500
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 22 (level, high) -> IRQ 22
ohci_hcd 0000:00:02.0: nVidia Corporation nForce2 USB Controller
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 22, pci mem 0xe9003000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 21 (level, high) -> IRQ 21
ohci_hcd 0000:00:02.1: nVidia Corporation nForce2 USB Controller (#2)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ohci_hcd 0000:00:02.1: irq 21, pci mem 0xe9004000
ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 19 (level, high) -> IRQ 19
ohci_hcd 0000:02:01.0: NEC Corporation USB
ohci_hcd 0000:02:01.0: irq 19, pci mem 0xe7004000
ohci_hcd 0000:02:01.0: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
ACPI: PCI interrupt 0000:02:01.1[B] -> GSI 16 (level, high) -> IRQ 16
ohci_hcd 0000:02:01.1: NEC Corporation USB (#2)
ohci_hcd 0000:02:01.1: irq 16, pci mem 0xe7005000
ohci_hcd 0000:02:01.1: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 1 port detected
ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 20 (level, high) -> IRQ 20
ehci_hcd 0000:00:02.2: nVidia Corporation nForce2 USB Controller
PCI: Setting latency timer of device 0000:00:02.2 to 64
ehci_hcd 0000:00:02.2: irq 20, pci mem 0xe9005000
ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 5
ohci_hcd 0000:00:02.1: wakeup
PCI: cache line size of 64 is not supported by device 0000:00:02.2
ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 6 ports detected
ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
ACPI: PCI interrupt 0000:02:01.2[C] -> GSI 17 (level, high) -> IRQ 17
ehci_hcd 0000:02:01.2: NEC Corporation USB 2.0
ehci_hcd 0000:02:01.2: irq 17, pci mem 0xe7006000
ehci_hcd 0000:02:01.2: new USB bus registered, assigned bus number 6
ehci_hcd 0000:02:01.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 3 ports detected
usb 5-4: new high speed USB device using ehci_hcd and address 2
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.30.
ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:04.0[A] -> GSI 22 (level, high) -> IRQ 22
PCI: Setting latency timer of device 0000:00:04.0 to 64
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
eth0: no link during initialization.
ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 21 (level, high) -> IRQ 21
PCI: Setting latency timer of device 0000:00:06.0 to 64
intel8x0_measure_ac97_clock: measured 49447 usecs
intel8x0: clocking to 47469
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
eth0: link up.
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
NET: Registered protocol family 17
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ACPI: PCI interrupt 0000:01:09.0[A] -> GSI 17 (level, high) -> IRQ 17
gameport: pci0000:01:09.1 speed 817 kHz
acx100: It looks like you've been coaxed into buying a wireless network card
acx100: that uses the mysterious ACX100/ACX111 chip from Texas Instruments.
acx100: You should better have bought e.g. a PRISM(R) chipset based card,
acx100: since that would mean REAL vendor Linux support.
acx100: Given this info, it's evident that this driver is quite EXPERIMENTAL,
acx100: thus your mileage may vary. Visit http://acx100.sf.net for support.
acx100: Warning: compiled to use 16bit I/O access only (compatibility mode). Set Makefile ACX_IO_WIDTH=32 to use slightly problematic 32bit mode.
acx_init_module: dev_info is: TI acx_pci
acx_init_module: TI acx_pci.o: Ver 0.2.0pre8 Driver initialized, waiting for cards to probe...
ACPI: PCI interrupt 0000:01:0a.0[A] -> GSI 16 (level, high) -> IRQ 16
Found ACX100-based wireless network card at 0000:01:0a.0, irq:16, phymem1:0xe8010000, phymem2:0xe8000000, mem1:0xe0a92000, mem1_size:4096, mem2:0xe0c80000, mem2_size:65536
initial debug setting is 0x001b
acx_select_io_register_set: using ACX100 io resource addresses (size: 56)
hw_unavailable = 1
acx_probe_pci: TI acx_pci: Using IRQ 16
reset hw_unavailable++
acx_reset_mac: enable soft reset...
acx_reset_mac: disable soft reset and go to init mode...
Attention: no custom firmware directory specified (via module parameter firmware_dir), thus using our default firmware directory /lib/hotplug/firmware
Trying to load firmware: '/lib/hotplug/firmware/WLANGEN.BIN-2.6.10-5-386'
Allocated 40636 bytes for firmware module loading.
not using auto increment for firmware loading.
acx_write_fw: Firmware written.
acx_write_fw (firmware): 0, acx_validate_fw: 0
acx_reset_dev: boot up eCPU and wait for complete...
acx_reset_dev: Received signal that card is ready to be configured :) (the eCPU has woken up)
reset hw_unavailable--
acx100: allocated net device wlan0, driver compiled against wireless extensions v17 and Linux 2.6.10-5-386
******************************************
************* acx_init_mac_1 *************
******************************************
==> Get the mailbox pointers from the scratch pad registers
CmdMailboxOffset = fdc8
InfoMailboxOffset = ff4c
<== Get the mailbox pointers from the scratch pad registers
CommandParameters = [ 0xe0c8fdcc ]
InfoParameters = [ 0xe0c8ff50 ]
Allocated 964 bytes for firmware module loading.
not using auto increment for firmware loading.
acx_write_fw: Firmware written.
acx_write_fw (radio): 0, acx_validate_fw: 0
CodeEnd:A26C
acx_init_wep: writing WEP options.
get_mask 0x00004182, set_mask 0x00000000
Got sensitivity value 187
Got antenna value 0x8F
Got regulatory domain 0x10
get_mask 0x00000000, set_mask 0x00000000 - after update
new ratevector: 82 84 8b 96 2c
SSID = STA0C12BD, len = 9
Beacon length:61
SSID = STA0C12BD, len = 9
hw_unavailable--
acx100: form factor 0x00 (unspecified), radio type 0x11 (RFMD), EEPROM version 0x04. Uploaded firmware 'Rev 1.9.8.b' (0x01020505).
creating /proc entry driver/acx_wlan0
creating /proc entry driver/acx_wlan0_diag
creating /proc entry driver/acx_wlan0_eeprom
creating /proc entry driver/acx_wlan0_phy
acx_probe_pci: TI acx_pci.o: Ver 0.2.0pre8 Loaded Successfully
r8169 Gigabit Ethernet driver 1.2 loaded
ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 18 (level, high) -> IRQ 18
eth1: Identified chip type is 'RTL8169s/8110s'.
eth1: RTL8169 at 0xe0a94000, 00:01:08:00:00:7d, IRQ 18
  Vendor: WDC WD25  Model: 00JB-00GVA0       Rev:  0 0
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
sda: assuming drive cache: write through
SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 p6 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:03.0[A] -> GSI 17 (level, high) -> IRQ 17
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[e7007000-e70077ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000108000000007c]
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
NTFS volume version 3.1.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Access to /proc/cpufreq is deprecated and will be removed from (new) 2.6. kernels soon after 2005-01-01
usb 5-2: new high speed USB device using ehci_hcd and address 3
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1088
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
VFS: Can't find ext3 filesystem on dev sda.
VFS: Can't find ext3 filesystem on dev sda.
VFS: Can't find ext3 filesystem on dev sda.

```

Thank you all for your help so far.

---

### Post by schdefan on 2005-09-01
> dmesg - print or control the kernel ring buffer
mmh there is no information about the permissions 
Execute ```
tail  /var/log/syslog
``` right after the permission denied message from apache  and look if there is some information about your fat32 partition.

You can`t change the fat32 permissions in Linux. 
Is it possible to access from nautilus?
schdefan

---

### Post by Nolgthorn on 2005-09-01
No it doesn't make any mention of the partition or the folders on it, only something about when my IP will be renewed.

I can access all of my files in Nautilus and do. This is how i've been trying to fix my permissions on the folder I want apache to access. I cannot change these permissions running Nautilus as either user or root.

edited for clarity.

---

### Post by plb on 2005-09-01
[QUOTE=][/QUOTE]
 check the last post

[http://www.daniweb.com/techtalkforums/thread22358.html](http://www.daniweb.com/techtalkforums/thread22358.html)

hope this helps

---

### Post by Nolgthorn on 2005-09-02
Interesting read thank you.

When I boot my machine Ubuntu will mount the Fat32 partitions on my USB Drive into /media. Now I don't know what that is or where the documentation is as to how to set the permissions before it is mounted into that directory or how to change anything about it really.

When I unmount one of the partitions on my USB hard drive, it disappears from /media and I am not sure how to get it back again or how to change it's permissions after I do that. So I'm stuck with a mounted volume that I cannot set the partitions on because it's mounted and I cannot set the permissions once it's been unmounted because it completely disappears.

Can someone suggest me how to set up my /etc/fstab in a way that I have more control over how the drives have been mounted? I would like the drives to be mounted into /mnt and I would like the drives not to be mounted the way that Ubuntu is set up right now to mount them into /media.

But I do not know how to turn off that feature.

---

### Post by Nolgthorn on 2005-09-02
Also I would be just as happy to figure out how to control the mounting that is going on into that strange /media. I never had to deal with it before, I had to mount all my stuff by hand with the previous stable version.

This is my fstab, which was automatically generated when I had Ubuntu installed:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
```

---

### Post by ubuntme on 2005-09-05
yeah, If someone could explain that weird /media mounting stuff in ubuntu it would be great, It seams to automount things that arn't in my fstab... weird.

Anyway, You can't change permissions on a fat32 drive.  You have to set them when you mount them, this was explained in the link in a previous post.

This is the options you want for your :
 /dev/sda /media/usb0 vfat users,defaults,umask=000 0 0

Or, if the drive is partitioned, prolly something like:
 /dev/sda1 /<whereever you want this partition> vfat users,defaults,umask=000 0 0
and
 /dev/sda2 /<whereever you want this partition> vfat users,defaults,umask=000 0 0

I have an internal and external fat32 drive
The internal one is in fstab as above, the extenal one is in with 
/dev/sda1        /media/usb0     auto    rw,users,noauto  0       0
but I can still read /write fine.

another weird ubuntu thing, I can't run mtab (should display how things are mounted)
I can cat /etc/mtab but I am not sure if this is correct to do.  Maybe someone can clarify that?

Anyway, what do you get when you cat /etc/mtab?

---

