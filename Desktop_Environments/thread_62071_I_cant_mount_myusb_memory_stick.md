---
title: "I cant mount myusb memory stick"
date: 2005-09-03
forum: Desktop Environments
---

### Post by codraider on 2005-09-03
i have Transcend 256mb usb flash memory stick.When i use gnome desktop enviroment,it works but Xfce 4.2.1 doesnt recognize it.
I cant mount it and see its content.What should i do?? 


(Ubuntu Hoary Minimal Install with Xfce4.2.1)

---

### Post by buldir on 2005-09-03
I am not too familiar with Xfce, but there may be a setting that is turned off by default which shows/hides mounted drives on the desktop.  If there is no such setting something to try would be:

1) Plug in your pen drive
2) Open up a command line interface (terminal)
3) Type:
```
dmesg
```
and look for something towards the bottom that may list the name of your pen drive.  In addition, it should say something like "sda" or "sda1".  This is where the drive can be mounted.

4) As root, or using sudo, put the following code in your /etc/fstab file:
```
/dev/sda1 /media/flash vfat users,defaults,umask=000 0 0
```
5)  Now, choose a mount directory name ("flash" accoring to the code above) and create it in /media, by typing:
```
sudo mkdir /media/flash
```
6. Now type:
```
mount /media/flash
```
which now should be accessible from the Xfce file manager or whatever.

7.  To unmount it, close all open file manager windows or anything used to access the drive and type:
```
umount /media/flash
```

---

### Post by codraider on 2005-09-03
first of all ,thank u for helping
1)dmesg
-------------------------------------------------------------------------------------------------------------------------------------------------------
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using uhci_hcd and address 2
SCSI subsystem initialized
Initializing USB Mass Storage driver...
usb 1-2: new full speed USB device using uhci_hcd and address 3
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usb 1-2: modprobe timed out on ep0in
usbcore: registered new driver speedtch
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usb 1-2: modprobe timed out on ep0in
usbcore: registered new driver speedtch
usb 1-2: no stage 1 firmware found!<6>ACPI: PCI interrupt 0000:00:1f.5[B -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49053 usecs
intel8x0: clocking to 48000
Linux video capture interface: v1.00
bttv: driver version 0.9.15 loaded
[b]bttv: using 8 buffers with 2080k (520 pages) each for capture
  Vendor: JetFlash  Model: TS256MJF2L        Rev: 2.00
  Type:   Direct-Access                      ANSI SCSI revision: 02[/b]
bttv: Bt8xx card found (0).
ACPI: PCI interrupt 0000:01:09.0[A] -> GSI 18 (level, low) -> IRQ 18
bttv0: Bt878 (rev 2) at 0000:01:09.0, irq: 18, latency: 132, mmio: 0xf4108000
bttv0: detected: FlyVideo 98FM (LR50)/ Typhoon TView TV/FM Tuner [card=36], PCI subsystem ID is 1852:1852
bttv0: using: Lifeview FlyVideo 98FM LR50 / Typhoon TView TV/FM Tuner [card=36,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00f4ff00 [init]
bttv0: FlyVideo Radio=yes RemoteControl=yes Tuner=5 gpio=0xf4ff00
bttv0: FlyVideo  LR90=no  tda9821/tda9820=no  capture_only=no
bttv0: using tuner=5
bttv0: i2c: checking for MSP34xx @ 0x80... <7>usb-storage: device scan complete
not found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
bttv0: i2c: checking for TDA9887 @ 0x86... not found
tuner: chip found at addr 0xc2 i2c-bus bt878 #0 [sw]
tuner: type set to 5 (Philips PAL_BG (FI1216 and compatibles)) by bt878 #0 [sw]
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: registered device radio0
bttv0: PLL: 28636363 => 35468950 .. ok
SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: unknown partition table
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
ACPI: PCI interrupt 0000:01:09.1[A] -> GSI 18 (level, low) -> IRQ 18
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
usbcore: deregistering driver speedtch
CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
HDLC line discipline: version $Revision: 4.8 $, maxframe=4096
N_HDLC line discipline registered.
usb 1-2: modem_run timed out on ep5in
usb 1-2: usbfs: USBDEVFS_BULK failed ep 0x85 len 512 ret -110
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hda1.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hda1.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hda1.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hda1.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hda1.
------------------------------------------------------------------------------------------------------------
above layout is result of dmesg command

2)my etc/fstab is =
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

and i add this = /dev/hda1 /media/flash vfat users,defaults,umask=000 0 0

3)sudo mkdir /media/flash command is ok and.........
4)when i type this
```

mount /media/flash
```

i get this =```
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

what should i do???

---

### Post by buldir on 2005-09-05
OK, it recognizes the pen drive, but seems confused about the file system.  This is because I am a putz and gave you misinformation.  Edit the line in your /etc/fstab file for the pen drive and change "/dev/hda1" to "/dev/sda1".  Change the "h" to an "s". Big difference!  Sorry about that.  You should be able to mount it now.  I will edit my previous post so no one else has the same problem.  See [this thread](http://ubuntuforums.org/showthread.php?t=62514) for tips on how to quickly mount your pen drive in Xfce.

---

### Post by codraider on 2005-09-05
i re-install my ubuntu again.during the installation i plug my usb stick and problem is solved.it mounts.and my fstab is 
```

/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

```



@thank you for your help buldir

---

