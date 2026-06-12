---
title: "Madcatz Controller in 9.10 64bit"
date: 2010-02-09
forum: Gaming &amp; Leisure
---

### Post by Enialis on 2010-02-09
I need some help getting a Madcatz Xbox 360 controller working in Ubuntu 9.10 64bit.

I tried every method of installing a normal 360 controller with no luck what so ever. 

Here are the last few lines of "dmesg" after plugging the controller in.

> [   34.721357] ppdev: user-space parallel port driver
[   34.831611] Intel AES-NI instructions are not detected.
[   34.902155] padlock: VIA PadLock not detected.
[   34.974144] padlock: VIA PadLock Hash Engine not detected.
[   36.080345] Adding 1020088k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:1020088k 
[   44.910028] eth0: no IPv6 routers present
[   75.250005] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x014f000c
[  133.230073] usb 7-1: new full speed USB device using uhci_hcd and address 2
[  133.442095] usb 7-1: configuration #1 chosen from 1 choice


And here is the relevant (or what seems to be relevant to me) output of "lsub -v" 
> Bus 007 Device 002: ID 1bad:f016 Harmonix Music 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x1bad Harmonix Music
  idProduct          0xf016 
  bcdDevice            4.90
  iManufacturer           1 Mad Catz, Inc.
  iProduct                2 MadCatz GamePad
  iSerial                 3 02CA585B
  bNumConfigurations      1


If someone needs more info, just let me know.
It seems like it recognizes the manufacturer, but doesn't recognized it as gamepad. 
I have no idea what to try next, I would really appreciate any help; I was looking forward to some heavy emulation on this laptop until I ran into this problem.
Thanks in advance.

---

### Post by PhazzedOut on 2010-05-09
Bump for Interest. 

I have one of these controllers as well and it would be awesome to use it to play games on it.

---

### Post by phDaemon on 2011-10-03
I usually dont revive old threads, but this is exactly my current problem and i've been searching for a solution for a while...would very much like to know if anyone has solved this... Thank you!!

---

### Post by thatguruguy on 2011-10-03
You should consider starting a new thread, stating exactly the problems you're having.

My MadCatz 360 controllers have worked OOTB with Ubuntu 10.10 and 11.04.

---

