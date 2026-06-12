---
title: "Treo 650 Help?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by penncon on 2006-07-26
I have searched this site and a few others.  I just installed Ubuntu today and have performed all of the updates.  The only problem that I'm having thus far is that I cannot sync my Treo 650 with Evolution.  If, after attempting to sync while running the Gnome Pilot setup from within Evolution, I run 'dmesg | grep usb' I get the following:

> [17179578.688000] usbcore: registered new driver usbfs
[17179578.688000] usbcore: registered new driver hub
[17179579.644000] usb 2-2: new low speed USB device using uhci_hcd and address 2[17179593.436000] usbcore: registered new driver hiddev
[17179593.452000] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.1-2
[17179593.452000] usbcore: registered new driver usbhid
[17179593.452000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17181008.988000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[17181009.112000] usb 2-1: device descriptor read/64, error -71
[17181009.340000] usb 2-1: device descriptor read/64, error -71
[17181009.556000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[17181009.680000] usb 2-1: device descriptor read/64, error -71
[17181009.908000] usb 2-1: device descriptor read/64, error -71
[17181010.124000] usb 2-1: new full speed USB device using uhci_hcd and address 5
[17181010.532000] usb 2-1: device not accepting address 5, error -71
[17181010.644000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[17181011.052000] usb 2-1: device not accepting address 6, error -71
[17181797.748000] usb 2-1: new full speed USB device using uhci_hcd and address 7
[17181797.868000] usb 2-1: device descriptor read/64, error -71
[17181798.092000] usb 2-1: device descriptor read/64, error -71
[17181798.308000] usb 2-1: new full speed USB device using uhci_hcd and address 8
[17181798.428000] usb 2-1: device descriptor read/64, error -71
[17181798.652000] usb 2-1: device descriptor read/64, error -71
[17181798.868000] usb 2-1: new full speed USB device using uhci_hcd and address 9
[17181799.276000] usb 2-1: device not accepting address 9, error -71
[17181799.388000] usb 2-1: new full speed USB device using uhci_hcd and address 10
[17181799.796000] usb 2-1: device not accepting address 10, error -71

I'm pretty frustrated at this point, and any help would be greatly appreciated.

---

### Post by penncon on 2006-07-26
**UPDATE:** Okay, I tried setting the device up to point to /dev/tts/USB1 because I read somewhere that that might work.  Now, my dmesg output is as follows:
> [17179575.752000] usbcore: registered new driver usbfs
[17179575.752000] usbcore: registered new driver hub
[17179576.708000] usb 2-2: new low speed USB device using uhci_hcd and address 2[17179590.412000] usbcore: registered new driver hiddev
[17179590.428000] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.1-2
[17179590.428000] usbcore: registered new driver usbhid
[17179590.428000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17183779.816000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[17183779.936000] usb 2-1: device descriptor read/64, error -71
[17183780.160000] usb 2-1: device descriptor read/64, error -71
[17183780.376000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[17183780.496000] usb 2-1: device descriptor read/64, error -71
[17183780.720000] usb 2-1: device descriptor read/64, error -71
[17183780.992000] usb 2-1: new full speed USB device using uhci_hcd and address 5
[17183781.404000] usb 2-1: device not accepting address 5, error -71
[17183781.516000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[17183781.932000] usb 2-1: device not accepting address 6, error -71
[17184040.888000] usb 2-1: new full speed USB device using uhci_hcd and address 7
[17184041.252000] usbcore: registered new driver usbserial
[17184041.252000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[17184041.252000] usbcore: registered new driver usbserial_generic
[17184041.252000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[17184041.256000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
[17184041.260000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
[17184041.260000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
[17184041.260000] usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
[17184041.260000] usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
[17184041.264000] usbcore: registered new driver visor
[17184041.264000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[17184131.368000] usb 2-1: USB disconnect, address 7
[17184155.800000] usb 2-1: new full speed USB device using uhci_hcd and address 8
[17184155.920000] usb 2-1: device descriptor read/64, error -71
[17184156.144000] usb 2-1: device descriptor read/64, error -71
[17184156.360000] usb 2-1: new full speed USB device using uhci_hcd and address 9
[17184156.480000] usb 2-1: device descriptor read/64, error -71
[17184156.728000] usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
[17184156.728000] usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
[17184157.576000] usb 2-1: USB disconnect, address 9
[17184267.940000] usb 2-1: new full speed USB device using uhci_hcd and address 10
[17184268.084000] usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
[17184268.084000] usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
[17184287.608000] usb 2-1: USB disconnect, address 10

I'm getting closer...but still no sync.  Any help?

---

### Post by Marc Higgins on 2006-07-30
I have had issues getting my treo600 to sync with evolution too, it works sometimes but I always seem to end up with duplicate errors.

My solution was to install jpilot. Once I had done this & told it that the plam was on /dev/pilot (connected via usb / cradle) it was rocking. 

Ended up dropping evolution for thunderbird for mail, miss the address book & schedule gnow applets / evol intergration with the desktop but i will live with that, anyway thats what worked for me, hope it does for you

---

