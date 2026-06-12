---
title: "problems with ti_usb_3410_5052 in ubuntu 8.04"
date: 2009-06-21
forum: General Help
---

### Post by amoya on 2009-06-21
Hi all,

I'm trying to make working the Texas Instruments MSP-eZ430U board.
I have done a lot of things posted in internet but when i plug the device it always says the same:

[COLOR=Navy][B][I][ 7716.254363] usb 1-2: new full speed USB device using uhci_hcd and address 9
[ 2890.313925] usb 1-2: configuration #1 chosen from 1 choice
[ 2890.319617] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: This device cannot do calls on its own. It is no modem.
[ 7727.587701] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[ 7727.588266] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: timeout initializing reports
[ 7727.588416] hiddev96hidraw1: USB HID v1.01 Device [Texas Instruments Texas Instruments MSP-FET430UIF] on usb-0000:00:1d.0-2[/I][/B][/COLOR]

Why does the system read cdc-acm and hid-core??? How can i change this? i think the system must read usbserial or register ti_usb_3410_5052 module.
Thank you in advance.
Aldo

---

