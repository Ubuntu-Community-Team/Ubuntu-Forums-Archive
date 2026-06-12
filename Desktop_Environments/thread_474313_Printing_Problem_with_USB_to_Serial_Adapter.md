---
title: "Printing Problem with USB to Serial Adapter"
date: 2007-06-14
forum: Desktop Environments
---

### Post by fwallace99 on 2007-06-14
Hello all --

Hope you can help. I am running Feisty Fawn on a Toshiba Satellite A135-S2276, so far so good. I can add OK a network printer (shared through a Wireless network from a Mac OS X computer).

BUT ... I cannot add a printer (either the System->Printing app or CUPS through the web interface) to my USB interface.

I have an old Apple LaserWriter Select 360. I can connect with a Mac Laptop using the Keyspan Parallel to USB connector since the Printer lacks a USB port, just parallel and Serial (and Appletalk). It works fine.

But I can't add the printer on my own USB port on my Feist Fawn Toshiba Laptop.

Here's a bit of the /var/log/message file:
Jun 14 20:02:38 Prytania kernel: [  332.160000] usb 1-2: USB disconnect, address 8
Jun 14 20:02:38 Prytania kernel: [  332.160000] drivers/usb/class/usblp.c: usblp0: removed
Jun 14 20:02:43 Prytania kernel: [  337.260000] usb 1-2: new full speed USB device using ohci_hcd and address 9
Jun 14 20:02:44 Prytania kernel: [  337.464000] usb 1-2: configuration #1 chosen from 1 choice
Jun 14 20:02:44 Prytania kernel: [  337.544000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 9 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
Jun 14 20:17:36 Prytania -- MARK --
Jun 14 20:32:12 Prytania kernel: [ 2105.660000] usb 1-2: USB disconnect, address 9
Jun 14 20:32:12 Prytania kernel: [ 2105.664000] drivers/usb/class/usblp.c: usblp0: removed
Jun 14 20:43:58 Prytania kernel: [ 2811.288000] usb 1-2: new full speed USB device using ohci_hcd and address 10
Jun 14 20:43:58 Prytania kernel: [ 2811.492000] usb 1-2: configuration #1 chosen from 1 choice
Jun 14 20:43:58 Prytania kernel: [ 2811.572000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 10 if 0 alt 1 proto 2 vid 0x067B pid 0x2305


So I assume that My laptop "Prytania" is recognizing the converter, but for whatever reason I can't add the printer. I've looked through the threads and googled it, no luck.

Anyone else run across this? I sure would like to be able to print to this printer, it may be old but it has genuine postscript and 8 MB of RAM. It's not a bad printer. Thanks for any help.

---

### Post by fwallace99 on 2007-06-15
Bump. And it's a parallel adapter, sorry not serial.

---

### Post by abc123456 on 2007-06-16
If cups won't work then apt-get install lprng magicfilter
then run magicfilterconfig tell it where the printer is /dev/lp0? then should work.:popcorn:

---

