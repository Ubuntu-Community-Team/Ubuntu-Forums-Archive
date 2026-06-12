---
title: "Trouble mounting a device"
date: 2009-04-17
forum: General Help
---

### Post by MASEngr on 2009-04-17
Hello, forum.

I'm having trouble mounting a device. It's a GPS unit, an NVM-4370. The GPS attaches to the USB hub, but it will not mount. I have tried forcing it, logging it, and I just cannot connect. It is likely that I don't know the command for mounting the device specifically:

m@sinister:~$ sudo mount -t vfat  /dev/scsi9 /media/gps
mount: special device /dev/scsi9 does not exist

If I could get a bit of help mounting this device so I can edit the files on it, that would be super. I've spent hours trying to get this to work, and it's just not doing anything useful except sitting there with a black screen saying "Connected to PC via USB". On Win XP, it will only do that for a moment before unplugging itself. 

Output from the various commands follow. Thank you for reading. The device is the Microsoft Corp. one; it runs Windows CE. 

m@sinister:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 014: ID 045e:ffff Microsoft Corp. 
Bus 001 Device 003: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 001 Device 002: ID 04e8:326c Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

m@sinister:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=83bddc90-9378-4884-83c4-3f133d3d8fc7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c778cfa2-8a6c-4a19-8a7c-b518ddd3dcbe none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
m@sinister:~$ 
m@sinister:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x010d010c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9732     1502077+   5  Extended
/dev/sda5            9546        9732     1502046   82  Linux swap / Solaris
m@sinister:~$  tail -f /var/log/messages


Apr 16 20:37:32 sinister -- MARK --
Apr 16 20:43:21 sinister kernel: [ 7576.366454] usb 1-3: USB disconnect, address 13
Apr 16 20:43:25 sinister kernel: [ 7580.517275] usb 1-3: new full speed USB device using ohci_hcd and address 14
Apr 16 20:43:25 sinister kernel: [ 7580.756615] usb 1-3: configuration #1 chosen from 1 choice
Apr 16 20:43:26 sinister kernel: [ 7580.797636] scsi9 : SCSI emulation for USB Mass Storage devices
Apr 16 20:43:31 sinister kernel: [ 7585.976903] usb 1-3: reset full speed USB device using ohci_hcd and address 14
Apr 16 20:43:31 sinister kernel: [ 7586.396261] usb 1-3: reset full speed USB device using ohci_hcd and address 14
Apr 16 20:43:32 sinister kernel: [ 7586.811622] usb 1-3: reset full speed USB device using ohci_hcd and address 14
Apr 16 20:43:32 sinister kernel: [ 7587.226998] usb 1-3: reset full speed USB device using ohci_hcd and address 14


m@sinister:~$ cat /proc/scsi/usb-storage/9
   Host scsi9: usb-storage
       Vendor: Generic Manufacturer (PROTOTYPE--Remember to change idVendor)
      Product: Generic Mass Storage (PROTOTYPE--Remember to change idVendor)
Serial Number: Generic Mass Storage (PROTOTYPE--Remember to change idVendor)
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:
m@sinister:~$ dmesg

[ 7580.797636] scsi9 : SCSI emulation for USB Mass Storage devices
[ 7580.800504] usb-storage: device found at 14
[ 7580.800513] usb-storage: waiting for device to settle before scanning
[ 7585.791115] usb-storage: device scan complete
[ 7585.976903] usb 1-3: reset full speed USB device using ohci_hcd and address 14
[ 7586.396261] usb 1-3: reset full speed USB device using ohci_hcd and address 14
[ 7586.811622] usb 1-3: reset full speed USB device using ohci_hcd and address 14
[ 7587.226998] usb 1-3: reset full speed USB device using ohci_hcd and address 14

---

### Post by HOLOGRAPHICpizza on 2009-04-17
It's device should be at /dev/sdb1, if you only have 1 hard drive. Try doing ```
ls /dev/sd*
```

---

### Post by MASEngr on 2009-04-17
Thank you, I tried to mount with sdb1, but to no avail. 

m@sinister:~$ sudo mount -t vfat  /dev/sdb1 /media/gps
[sudo] password for m: 
mount: special device /dev/sdb1 does not exist

m@sinister:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5


m@sinister:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x010d010c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9732     1502077+   5  Extended
/dev/sda5            9546        9732     1502046   82  Linux swap / Solaris
m@sinister:~$

---

### Post by zeex on 2009-04-17
HI, 

I hate to say it but the OS is not detecting the GPS as a hard drive (flash drive). It should show up in **$ sudo fdisk -l** as **/dev/sdb1 **.

Which version of ubuntu are you using?

Your kernel msgs says 
Apr 16 20:43:26 sinister kernel: [ 7580.797636] **scsi9** : SCSI emulation for USB Mass Storage devices

just a guess why don't you try this 

**$ sudo mount -t vfat /dev/sdc9 /media/gps **

It's on scsi9 but not showing up in fdisk, kinda strange :|

:: attach the device and reboot the system and then do all this (again it's a guess)

Good luck :)

---

### Post by MASEngr on 2009-04-17
Nope, that didn't work. After rebooting (and checking the SCSI setting) it responds with "device does not exist"

---

