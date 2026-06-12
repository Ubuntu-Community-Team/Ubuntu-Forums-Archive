---
title: "Gnome doesn't mount Lexar Jumpdrive USB memory"
date: 2007-08-19
forum: Desktop Environments
---

### Post by ambrosa on 2007-08-19
I've many USB memory stick. Till now I've never had problems in my Ubuntu Feisty 7.04 (Gnome)

Today I've inserted for the first time an old USB memory stick called "Lexar Jumpdrive 256MB" (usb hi-speed).
It's not automagically mounted in Gnome (strange) but I can manually mount it without any problem.
I've also re-partition it and re-format it with vfat without any success: Gnome doesn't auto mount it.

It is recognized by the system. This is my /var/log/message:
-------------
Aug 19 19:27:23 tux kernel: [ 2910.235101] usb 5-4: new high speed USB device using ehci_hcd and address 10
Aug 19 19:27:23 tux kernel: [ 2910.378658] usb 5-4: configuration #1 chosen from 1 choice
Aug 19 19:27:23 tux kernel: [ 2910.379258] scsi10 : SCSI emulation for USB Mass Storage devices
Aug 19 19:27:28 tux kernel: [ 2915.377341] scsi 10:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.25 PQ: 0 ANSI: 0
Aug 19 19:27:28 tux kernel: [ 2915.710445] SCSI device sdc: 512000 512-byte hdwr sectors (262 MB)
Aug 19 19:27:35 tux kernel: [ 2922.107525] sdc: Write Protect is off
Aug 19 19:27:35 tux kernel: [ 2922.107534]  sdc: sdc1
Aug 19 19:27:35 tux kernel: [ 2922.441735] sd 10:0:0:0: Attached scsi removable disk sdc
Aug 19 19:27:35 tux kernel: [ 2922.441781] sd 10:0:0:0: Attached scsi generic sg3 type 0
-------------

I can manually create a dummy dir in /media and mount /dev/sdc1 in it without any problem.

So the question is: why Gnome doesn't auto mount it in desktop ?
There is a problem with HAL or udev ? Some misconfiguration ?

Thanks.

---

### Post by Happy_Man on 2007-08-19
I have the same drive, same problem. I don't know why it happens....

---

### Post by ambrosa on 2007-08-20
Today I've tried in my office with a different PC (Ubuntu 7.04).
At the first time I insert Lexar Jumpdrive, it's recognized and automagically it's (as usual) mounted in Gnome desktop. Yeah !
If I "eject" it and then remove it and reinsert for the second time, now it doesn't work anymore like my original post. I need to reboot the system and now it's recognize, but always for the first time only.

Ghosts in memory chip ???????? :confused::confused::confused::confused:

/var/log/messages is almost identical to previous.

---

### Post by ambrosa on 2007-11-11
And now  the same problem with this old Lexar Jumpdrive 256MB appears in Gutsy also (Gutsy was installed from scratch, was not an upgrade from Feisty)
Other USB memory stick and USB HDD drive work fine without any problem.

But I've done some debug......

1) I insert the stick. Kernel recognized it (from dmesg):
```
[10454.820660] usb 5-4: new high speed USB device using ehci_hcd and address 16
[10454.958835] usb 5-4: configuration #1 chosen from 1 choice
[10454.959430] scsi17 : SCSI emulation for USB Mass Storage devices
[10454.959480] usb-storage: device found at 16
[10454.959481] usb-storage: waiting for device to settle before scanning
[10459.950328] usb-storage: device scan complete
[10459.951206] scsi 17:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.25 PQ: 0 ANSI: 0
[10460.284096] sd 17:0:0:0: [sdd] 512000 512-byte hardware sectors (262 MB)
[10460.400982] usb 5-4: reset high speed USB device using ehci_hcd and address 16
[10460.984175] usb 5-4: reset high speed USB device using ehci_hcd and address 16
[10461.567373] usb 5-4: reset high speed USB device using ehci_hcd and address 16
[10462.150569] usb 5-4: reset high speed USB device using ehci_hcd and address 16
[10462.733765] usb 5-4: reset high speed USB device using ehci_hcd and address 16
[10463.316964] usb 5-4: reset high speed USB device using ehci_hcd and address 16
[10463.452616] sd 17:0:0:0: [sdd] Write Protect is off
[10463.452619] sd 17:0:0:0: [sdd] Mode Sense: 02 00 00 00
[10463.452621] sd 17:0:0:0: [sdd] Assuming drive cache: write through
[10463.787220] sd 17:0:0:0: [sdd] 512000 512-byte hardware sectors (262 MB)
[10463.904157] usb 5-4: reset high speed USB device using ehci_hcd and address 16
[10464.487346] usb 5-4: reset high speed USB device using ehci_hcd and address 16
[10465.070549] usb 5-4: reset high speed USB device using ehci_hcd and address 16
[10465.657743] usb 5-4: reset high speed USB device using ehci_hcd and address 16
[10466.126097] sd 17:0:0:0: [sdd] Write Protect is off
[10466.126103] sd 17:0:0:0: [sdd] Mode Sense: 02 00 00 00
[10466.126105] sd 17:0:0:0: [sdd] Assuming drive cache: write through
[10466.126109]  sdd: sdd1
[10466.128775] sd 17:0:0:0: [sdd] Attached SCSI removable disk
[10466.128819] sd 17:0:0:0: Attached scsi generic sg4 type 0
```

*lsusb* command is ok:
```
Bus 005 Device 010: ID 05dc:a300 Lexar Media, Inc.
Bus 005 Device 003: ID 04b8:0121 Seiko Epson Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

And also HAL recognize it (from /var/log/daemon.log):
```
Nov 11 08:15:27 lion NetworkManager: <debug> [1194765327.452462] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a300_2900001230'). 
Nov 11 08:15:27 lion NetworkManager: <debug> [1194765327.487034] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a300_2900001230_if0'). 
Nov 11 08:15:27 lion NetworkManager: <debug> [1194765327.503624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a300_2900001230_usbraw'). 
Nov 11 08:15:35 lion NetworkManager: <debug> [1194765335.469603] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a300_2900001230_if0_scsi_host'). 
Nov 11 08:15:35 lion NetworkManager: <debug> [1194765335.477597] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a300_2900001230_if0_scsi_host_scsi_device_lun0'). 
Nov 11 08:15:38 lion NetworkManager: <debug> [1194765338.225886] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a300_2900001230_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
```

But my stick is only mountable with a *sudo mount /dev/sdd1 /media/test* and after this, icon appear in my desktop (but only read-only because was mounted as root. Permissione problem).
Gnome doesn't recognized automatically it. I need manually to mount it.

2) I've tried a simple test using *gnome-mount*:
with a working usb stick:
```
root@lion:/media# gnome-mount --device /dev/sdd1
gnome-mount 0.6
X display not available - using text-based operation.
Mounted /dev/sdd1 at "/media/AMBROSA_USB"
```

with Lexar:
```
root@lion:/media# gnome-mount --device /dev/sdd1
gnome-mount 0.6
X display not available - using text-based operation.
** (gnome-mount:3921): WARNING **: Given device '/dev/sdd1' is not a volume or a drive.
```

Wow ! Why Gnome doesn't recognize /dev/sdd1 ads a drive ? If I mount it with *mount* , it works !

3) With the Lexar stick inserted, I restart hal  *sudo /etc/init.d/hal restart*
Magically immediately after HAL restart, in my desktop appear the USB device icon of my stick and it works as any other sub stick.
If I remove Lexar, I restart HAL and I reinsert Lexar, nothing happen.

4) You can see that during USB negotiation, there are many "usb 5-4: reset high speed USB device using ehci_hcd and address 16". Only during negotiation, not durng normal work (transfer files and so on).
These "reset" add some delay (>> 1 seconds) so I can suppose that some type of timeout inhibit Gnome to recognize it.
Some problem with HAL <-> GNOME-VOLUME-MANAGER ???


I want to do more debug.
After HAL recognizes the stick, what happened ? Which software and process are involved after HAL ????

---

### Post by karlwilbur on 2008-03-01
Having same trouble. Only with older/smaller ( <512MB ) drives. Larger/newer drives are working just fine.

---

