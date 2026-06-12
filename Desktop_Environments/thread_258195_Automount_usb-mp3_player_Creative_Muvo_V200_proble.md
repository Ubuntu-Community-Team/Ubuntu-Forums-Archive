---
title: "Automount usb-mp3 player Creative Muvo V200 problem"
date: 2006-09-15
forum: Desktop Environments
---

### Post by isTHEr3mOr3 on 2006-09-15
Hi, 

This has been a problem since the first day I bought my MP3 player (more than a jear ago). In Hoary it didn't work at all and in Dapper it works a bit better but not flawless. 
I can automount the mp3 player when I do a clean start and it is possible to browse the player and exchange files. After u(n)mounting it, Ubuntu can't automount my player anymore. 

I was hoping some kernel upgrades would fix this, but it's still not working as it should. It doesn't work on another Ubuntu Dapper PC as well. 

dmesg|grep -i usb gives (I'm also using a usb mouse):

[17179575.448000] usbcore: registered new driver usbfs
[17179575.448000] usbcore: registered new driver hub
[17179575.448000] USB Universal Host Controller Interface driver v2.3
[17179575.452000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179575.452000] hub 1-0:1.0: USB hub found
[17179575.556000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179575.556000] hub 2-0:1.0: USB hub found
[17179575.660000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.660000] hub 3-0:1.0: USB hub found
[17179575.764000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179575.768000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.768000] hub 4-0:1.0: USB hub found
[17179575.796000] usb 1-2: new low speed USB device using uhci_hcd and address 2[17179576.596000] usb 1-2: new low speed USB device using uhci_hcd and address 3[17179577.008000] usb 2-2: new low speed USB device using uhci_hcd and address 2[17179586.916000] input: X10 Wireless Technology Inc USB Receiver as /class/input/input1
[17179586.920000] usbcore: registered new driver ati_remote
[17179586.920000] drivers/usb/input/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1
[17179586.920000] usbcore: registered new driver hiddev
[17179586.924000] drivers/usb/input/ati_remote.c: Weird data, len=1 ff 00 00 00 00 00 ...
[17179586.940000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[17179586.940000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
[17179586.940000] usbcore: registered new driver usbhid
[17179586.940000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17253182.412000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 89 f6 24 63 00 ...
[17258180.188000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 34 f4 a5 8c 00 ...
[17265473.912000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 0c 7f e1 c1 00 ...
[17267307.836000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 20 7c 53 4b 00 ...
[17271549.676000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 44 7f e0 23 00 ...
[17648261.768000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 ff fb ff fc 00 ...
[17648611.948000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 3f fb bf ff 00 ...
[17651481.840000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 cf bf f7 ff 00 ...
[17652979.784000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 e7 ff ff fd 00 ...
[17657865.592000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 3f a5 7f ff 00 ...
[17737592.704000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 ff fe e6 f8 00 ...
[17748873.628000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[17748875.348000] Initializing USB Mass Storage driver...
[17748875.348000] scsi0 : SCSI emulation for USB Mass Storage devices
[17748875.352000] usb-storage: device found at 4
[17748875.352000] usb-storage: waiting for device to settle before scanning
[17748875.352000] usbcore: registered new driver usb-storage
[17748875.352000] USB Mass Storage support registered.
[17748880.368000] usb-storage: device scan complete
[17750318.608000] usb 4-1: USB disconnect, address 4
[17811327.696000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 02 7f ff ff 00 ...
[17902731.900000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 f0 13 ec 94 00 ...
[17922454.128000] usbcore: deregistering driver usb-storage
[17922512.232000] Initializing USB Mass Storage driver...
[17922512.232000] usbcore: registered new driver usb-storage
[17922512.232000] USB Mass Storage support registered.
[17922570.528000] usbcore: deregistering driver usb-storage
[17922601.308000] Initializing USB Mass Storage driver...
[17922601.308000] usbcore: registered new driver usb-storage
[17922601.308000] USB Mass Storage support registered.
[17922796.104000] usbcore: deregistering driver usb-storage
[17922816.304000] Initializing USB Mass Storage driver...
[17922816.304000] usbcore: registered new driver usb-storage
[17922816.304000] USB Mass Storage support registered.
[17965462.096000] drivers/usb/input/ati_remote.c: Weird data, len=5 20 1f d3 f8 c7 00 ...

I've tried this as well: 

sudo modprobe -r usb-storage (without mp3 player connected)
sudo modprobe -r usb-storage

and again automount failed. 

Hope someone can help me with this, I'm not happy with restarting my PC daily to transfer a podcast.

---

