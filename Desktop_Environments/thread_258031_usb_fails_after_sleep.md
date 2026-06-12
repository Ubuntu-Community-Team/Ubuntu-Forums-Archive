---
title: "usb fails after sleep"
date: 2006-09-15
forum: Desktop Environments
---

### Post by mathgenius on 2006-09-15
After the machine goes to sleep (i think this is when
the screensaver comes up?) my usb devices are not detected anymore.
Eg. when I unplug/plug stuff in. Nothing works (keyboard/mouse/headphones).

I get these msgs spewing out in dmesg:
[17430850.192000] drivers/usb/input/hid-core.c: input irq status -71 received
(...)

The only way i found to fix this is to shut down apps until usb works again.
Today I had to shutdown X (gdm) so it's really starting to cut into productivity :p 

Here is what then happens in dmesg:
[17430850.204000] usbcore: deregistering driver hiddev
[17430850.204000] usb 5-2.1.3: USB disconnect, address 30
[17430850.332000] usb 5-2.1.4: USB disconnect, address 31
[17430858.384000] usb 5-2.1.3: new low speed USB device using ehci_hcd and address 33
[17430858.692000] usbcore: registered new driver hiddev
[17430858.708000] input: USB Optical Mouse as /class/input/input15
[17430858.712000] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2
[17430858.720000] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input16
[17430858.720000] input: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:1d.7-2.1.3
[17430858.732000] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input17
[17430858.732000] input: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:1d.7-2.1.3
[17430858.732000] usbcore: registered new driver usbhid
[17430858.732000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17430894.248000] usb 5-2.1.4: new low speed USB device using ehci_hcd and address 34
[17430894.360000] input: Forward USB Optical Mouse as /class/input/input18
[17430894.360000] input: USB HID v1.10 Mouse [Forward USB Optical Mouse] on usb-0000:00:1d.7-2.1.4
[17431670.672000] usb 5-6.1: new full speed USB device using ehci_hcd and address 35


This exact same thing happens both on my desktop:
Linux mother 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux

and on my intel celeron laptop (with the UP 2.6.15 kernel).

#-o 

Today ive disabled screensaver; i hope i dont burn out my LCD monitors.

Simon.

---

