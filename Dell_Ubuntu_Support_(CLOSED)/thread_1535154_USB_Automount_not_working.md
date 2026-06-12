---
title: "USB Automount not working"
date: 2010-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by saeed_alzubaidi on 2010-07-20
USB Flash memories are not detected by the Laptop but the Discs and local hard disks are detected.

> dmesg

[  197.237127] CE: hpet increasing min_delta_ns to 15000 nsec
[  274.541151] CE: hpet increasing min_delta_ns to 22500 nsec
[  513.528197] usb 3-2: new full speed USB device using uhci_hcd and address 2
[  513.700464] usb 3-2: configuration #1 chosen from 1 choice
[  579.992139] usb 3-2: USB disconnect, address 2
[  579.992196] btusb_intr_complete: hci1 urb f2b63c00 failed to resubmit (19)
[  579.992216] btusb_bulk_complete: hci1 urb f2b63a00 failed to resubmit (19)
[  579.993202] btusb_bulk_complete: hci1 urb f2b63000 failed to resubmit (19)
[  579.993721] btusb_send_frame: hci1 urb f60dbf80 submission failed
[  586.212151] usb 1-4: new high speed USB device using ehci_hcd and address 4
[  586.345317] usb 1-4: configuration #1 chosen from 1 choice
[  586.346302] scsi2 : SCSI emulation for USB Mass Storage devices
[  586.346574] usb-storage: device found at 4
[  586.346579] usb-storage: waiting for device to settle before scanning
[  842.693141] usb 1-4: USB disconnect, address 4
[  947.563587] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[ 1255.896113] usb 1-5: new high speed USB device using ehci_hcd and address 5
[ 1256.029637] usb 1-5: configuration #1 chosen from 1 choice
[ 1256.030172] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1256.030479] usb-storage: device found at 5
[ 1256.030483] usb-storage: waiting for device to settle before scanning


& 


> sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1e3d:2093  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

&


more fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=c213be69-70d2-4a94-b5a0-7f8dd4b3c7e4 /               ext4    errors=remount-ro 0       1
/dev/sda6       /usr            ext4    defaults        0       2
/dev/sda7       none            swap    sw              0       0


&


tail -n 20 /var/log/kern.log
Jul 20 21:50:06 Dell-Linux kernel: [  274.541151] CE: hpet increasing min_delta_ns to 22500 nsec
Jul 20 21:54:05 Dell-Linux kernel: [  513.528197] usb 3-2: new full speed USB device using uhci_hcd and address 2
Jul 20 21:54:05 Dell-Linux kernel: [  513.700464] usb 3-2: configuration #1 chosen from 1 choice
Jul 20 21:55:11 Dell-Linux kernel: [  579.992139] usb 3-2: USB disconnect, address 2
Jul 20 21:55:11 Dell-Linux kernel: [  579.992196] btusb_intr_complete: hci1 urb f2b63c00 failed to resubmit (19)
Jul 20 21:55:11 Dell-Linux kernel: [  579.992216] btusb_bulk_complete: hci1 urb f2b63a00 failed to resubmit (19)
Jul 20 21:55:11 Dell-Linux kernel: [  579.993202] btusb_bulk_complete: hci1 urb f2b63000 failed to resubmit (19)
Jul 20 21:55:11 Dell-Linux kernel: [  579.993721] btusb_send_frame: hci1 urb f60dbf80 submission failed
Jul 20 21:55:17 Dell-Linux kernel: [  586.212151] usb 1-4: new high speed USB device using ehci_hcd and address 4
Jul 20 21:55:18 Dell-Linux kernel: [  586.345317] usb 1-4: configuration #1 chosen from 1 choice
Jul 20 21:55:18 Dell-Linux kernel: [  586.346302] scsi2 : SCSI emulation for USB Mass Storage devices
Jul 20 21:55:18 Dell-Linux kernel: [  586.346574] usb-storage: device found at 4
Jul 20 21:55:18 Dell-Linux kernel: [  586.346579] usb-storage: waiting for device to settle before scanning
Jul 20 21:59:34 Dell-Linux kernel: [  842.693141] usb 1-4: USB disconnect, address 4
Jul 20 22:01:19 Dell-Linux kernel: [  947.563587] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
Jul 20 22:06:27 Dell-Linux kernel: [ 1255.896113] usb 1-5: new high speed USB device using ehci_hcd and address 5
Jul 20 22:06:27 Dell-Linux kernel: [ 1256.029637] usb 1-5: configuration #1 chosen from 1 choice
Jul 20 22:06:27 Dell-Linux kernel: [ 1256.030172] scsi3 : SCSI emulation for USB Mass Storage devices
Jul 20 22:06:27 Dell-Linux kernel: [ 1256.030479] usb-storage: device found at 5
Jul 20 22:06:27 Dell-Linux kernel: [ 1256.030483] usb-storage: waiting for device to settle before scanning

---

### Post by tkoco on 2010-07-24
Ahh, the "DELL laptop won't see the USB" problem. ;) Welcome to the crowd. I have a Latitude C610 which suffers from that very same problem. Near as I can figure out, the root of the problem is in the BIOS of the laptop. I have tested various Dell Laptops using a properly formatted USB stick with Ubuntu. Laptop models, which support booting from USB, have no problems auto-mounting a USB stick or USB external harddrive. Unfortunately, the Latitude C610 does not support booting from USB. Thus no auto-mount! On the plus side, you can manually mount/unmount the USB device once it settles down. I usually use the /mnt filesystem directory for this purpose. Example where "dmesg" id's the USB stick as sdb & sdb1

```
sudo mount /dev/sdb1 /mnt
```

One last thought, check the BIOS settings and make sure USB support is fully turned on. Good Luck!


> **saeed_alzubaidi said:**
> USB Flash memories are not detected by the Laptop but the Discs and local hard disks are detected.

> dmesg

[  197.237127] CE: hpet increasing min_delta_ns to 15000 nsec
[  274.541151] CE: hpet increasing min_delta_ns to 22500 nsec
[  513.528197] usb 3-2: new full speed USB device using uhci_hcd and address 2
[  513.700464] usb 3-2: configuration #1 chosen from 1 choice
[  579.992139] usb 3-2: USB disconnect, address 2
[  579.992196] btusb_intr_complete: hci1 urb f2b63c00 failed to resubmit (19)
[  579.992216] btusb_bulk_complete: hci1 urb f2b63a00 failed to resubmit (19)
[  579.993202] btusb_bulk_complete: hci1 urb f2b63000 failed to resubmit (19)
[  579.993721] btusb_send_frame: hci1 urb f60dbf80 submission failed
[  586.212151] usb 1-4: new high speed USB device using ehci_hcd and address 4
[  586.345317] usb 1-4: configuration #1 chosen from 1 choice
[  586.346302] scsi2 : SCSI emulation for USB Mass Storage devices
[  586.346574] usb-storage: device found at 4
[  586.346579] usb-storage: waiting for device to settle before scanning
[  842.693141] usb 1-4: USB disconnect, address 4
[  947.563587] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[ 1255.896113] usb 1-5: new high speed USB device using ehci_hcd and address 5
[ 1256.029637] usb 1-5: configuration #1 chosen from 1 choice
[ 1256.030172] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1256.030479] usb-storage: device found at 5
[ 1256.030483] usb-storage: waiting for device to settle before scanning


& 


> sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1e3d:2093  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

&


more fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=c213be69-70d2-4a94-b5a0-7f8dd4b3c7e4 /               ext4    errors=remount-ro 0       1
/dev/sda6       /usr            ext4    defaults        0       2
/dev/sda7       none            swap    sw              0       0


&


tail -n 20 /var/log/kern.log
Jul 20 21:50:06 Dell-Linux kernel: [  274.541151] CE: hpet increasing min_delta_ns to 22500 nsec
Jul 20 21:54:05 Dell-Linux kernel: [  513.528197] usb 3-2: new full speed USB device using uhci_hcd and address 2
Jul 20 21:54:05 Dell-Linux kernel: [  513.700464] usb 3-2: configuration #1 chosen from 1 choice
Jul 20 21:55:11 Dell-Linux kernel: [  579.992139] usb 3-2: USB disconnect, address 2
Jul 20 21:55:11 Dell-Linux kernel: [  579.992196] btusb_intr_complete: hci1 urb f2b63c00 failed to resubmit (19)
Jul 20 21:55:11 Dell-Linux kernel: [  579.992216] btusb_bulk_complete: hci1 urb f2b63a00 failed to resubmit (19)
Jul 20 21:55:11 Dell-Linux kernel: [  579.993202] btusb_bulk_complete: hci1 urb f2b63000 failed to resubmit (19)
Jul 20 21:55:11 Dell-Linux kernel: [  579.993721] btusb_send_frame: hci1 urb f60dbf80 submission failed
Jul 20 21:55:17 Dell-Linux kernel: [  586.212151] usb 1-4: new high speed USB device using ehci_hcd and address 4
Jul 20 21:55:18 Dell-Linux kernel: [  586.345317] usb 1-4: configuration #1 chosen from 1 choice
Jul 20 21:55:18 Dell-Linux kernel: [  586.346302] scsi2 : SCSI emulation for USB Mass Storage devices
Jul 20 21:55:18 Dell-Linux kernel: [  586.346574] usb-storage: device found at 4
Jul 20 21:55:18 Dell-Linux kernel: [  586.346579] usb-storage: waiting for device to settle before scanning
Jul 20 21:59:34 Dell-Linux kernel: [  842.693141] usb 1-4: USB disconnect, address 4
Jul 20 22:01:19 Dell-Linux kernel: [  947.563587] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
Jul 20 22:06:27 Dell-Linux kernel: [ 1255.896113] usb 1-5: new high speed USB device using ehci_hcd and address 5
Jul 20 22:06:27 Dell-Linux kernel: [ 1256.029637] usb 1-5: configuration #1 chosen from 1 choice
Jul 20 22:06:27 Dell-Linux kernel: [ 1256.030172] scsi3 : SCSI emulation for USB Mass Storage devices
Jul 20 22:06:27 Dell-Linux kernel: [ 1256.030479] usb-storage: device found at 5
Jul 20 22:06:27 Dell-Linux kernel: [ 1256.030483] usb-storage: waiting for device to settle before scanning

---

### Post by saeed_alzubaidi on 2010-07-26
Thanks a lot for the reply. 

Actually I tested your proposal but still not working.

In addition to that, I remembered that I have installed the driver of "Huawei E1550" USB 3G Wireless modem earlier using the below link:

[http://franklinchua.wordpress.com/2010/05/03/huawei-e1550-on-ubuntu-10-04-lucid-lynx/](http://franklinchua.wordpress.com/2010/05/03/huawei-e1550-on-ubuntu-10-04-lucid-lynx/)

What I have done was just removing this driver then automount started working perfectly.

Now I am partially happy since I can do only one of them at once (either the 3G modem or USB Flash mounting)

Thanks again tkoco:p

---

