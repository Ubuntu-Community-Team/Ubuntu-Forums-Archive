---
title: "USB MP3 player problems"
date: 2005-11-16
forum: Desktop Environments
---

### Post by Grimlock on 2005-11-16
I have searched through all the froums till I was dizzy today and I still cannot get my Oracom ORC-200M MP3 Player working ](*,) It is being recognised as when I 
richie@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0f19:0103 Oracom Co., Ltd
Bus 001 Device 002: ID 062a:0000 Creative Labs
Bus 001 Device 001: ID 0000:0000

You can see it is their in the output.

When doing I disconnect and reconnect with dmesg I get 

[4305152.373000] usb 1-2: USB disconnect, address 5
[4305161.300000] usb 1-2: new full speed USB device using ohci_hcd and address 6[4305161.410000] scsi3 : SCSI emulation for USB Mass Storage devices
[4305161.414000] usb-storage: device found at 6
[4305161.414000] usb-storage: waiting for device to settle before scanning
[4305166.442000] usb-storage: device scan complete
[4305355.123000] usb 1-2: USB disconnect, address 6
[4305357.800000] usb 1-2: new full speed USB device using ohci_hcd and address 7

Bit more info for you

richie@ubuntu:~$ tail /var/log/messages
Nov 16 21:28:17 localhost kernel: [4305138.580000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
Nov 16 21:28:17 localhost scsi.agent[12394]:      sd_mod: loaded sucessfully (for disk)
Nov 16 21:28:31 localhost kernel: [4305152.373000] usb 1-2: USB disconnect, address 5
Nov 16 21:28:40 localhost kernel: [4305161.300000] usb 1-2: new full speed USB device using ohci_hcd and address 6
Nov 16 21:28:40 localhost kernel: [4305161.410000] scsi3 : SCSI emulation for USB Mass Storage devices
Nov 16 21:28:40 localhost usb.agent[12592]:      usb-storage: already loaded
Nov 16 21:31:53 localhost kernel: [4305355.123000] usb 1-2: USB disconnect, address 6
Nov 16 21:31:56 localhost kernel: [4305357.800000] usb 1-2: new full speed USB device using ohci_hcd and address 7
Nov 16 21:31:56 localhost kernel: [4305358.049000] scsi4 : SCSI emulation for USB Mass Storage devices
Nov 16 21:31:56 localhost usb.agent[12732]:      usb-storage: already loaded

Can anyone help me please?? I do not want to keep having to goto Windoze to use my mp3 player [-X 

Cheers in advance.

---

### Post by Ampersand on 2005-11-16
Has it appeared in the /media folder at all when you plug it in? What happens if you try running
```

sudo mkdir /media/mp3
sudo mount -t vfat /dev/sda1 /media/mp3

```

---

### Post by Grimlock on 2005-11-16
richie@:~$ sudo mkdir /media/mp3
richie@:~$ sudo mount -t vfat /dev/sda1 /media/mp3
mount: special device /dev/sda1 does not exist

This is doing my head in as my pen drive is recognised straight away??? >_<

---

### Post by Ampersand on 2005-11-16
Try having a look in the hardware manager after plugging it in (under system - administration I think. Not sure what it's called off hand since I'm not in Gnome at the moment but you should see it). If you look t6owards the bottom at the USB devices, it should be listed and should say where in /dev it is. Try replacing /dev/sda1 with that if it's different.

Also, I've sometimes found that it helps if you plug it into Windows and reformat it as fat32 (although I've not had any experience with that particular player, so I can't guarantee anything).

---

