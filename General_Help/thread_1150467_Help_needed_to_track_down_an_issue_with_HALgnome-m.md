---
title: "Help needed to track down an issue with HAL/gnome-mount"
date: 2009-05-06
forum: General Help
---

### Post by Azdour on 2009-05-06
Hi all,

I believe this may be quite a techie issue, but on one of my machines running Ubuntu 8.04 the USB detection is not working correctly.

My investigation so far tells me that when I plug in the USB stick that HAL detects it. That is to say the USB Corsair stick appears in the list produced running 'lshal'. 

It also appears as sdb in /dev.

Under Places | Computer it has the USB but it's labelled as 'USB Drive', not 'Corsair'. I cannot access it, because it says it cannot mount the file...

If I run gnome-mount it mounts correctly from the command line. Is there any way of tracking down what the issue is? Is there a tech place I can go to and ask how HAL and gnome-mount work with each other to auto-mount USB devices?

---

### Post by Azdour on 2009-05-06
When I try:

killall gnome-volume-manager
gnome-volume-manager -n 2>&1 | tee /tmp/gvm.log

This appears in the gvm.log:

manager.c/2950: Device added: /org/freedesktop/Hal/devices/usb_device_1b1c_ad0_000802218427B87A132E
manager.c/2950: Device added: /org/freedesktop/Hal/devices/usb_device_1b1c_ad0_000802218427B87A132E_if0
manager.c/2950: Device added: /org/freedesktop/Hal/devices/usb_device_1b1c_ad0_000802218427B87A132E_if0_scsi_host
manager.c/2950: Device added: /org/freedesktop/Hal/devices/usb_device_1b1c_ad0_000802218427B87A132E_if0_scsi_host_scsi_device_lun0
manager.c/2950: Device added: /org/freedesktop/Hal/devices/usb_device_1b1c_ad0_000802218427B87A132E_if0_scsi_host_scsi_device_lun0_scsi_generic
manager.c/2950: Device added: /org/freedesktop/Hal/devices/volume_uuid_F04C_4288
manager.c/2733: Changed: /dev/sdb1
manager.c/2950: Device added: /org/freedesktop/Hal/devices/storage_serial_Corsair_Flash_Voyager_000802218427B87A132E_0_0
manager.c/2687: not a mountable volume: /org/freedesktop/Hal/devices/storage_serial_Corsair_Flash_Voyager_000802218427B87A132E_0_0

---

