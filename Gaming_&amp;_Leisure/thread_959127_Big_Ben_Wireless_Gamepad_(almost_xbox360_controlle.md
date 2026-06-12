---
title: "Big Ben Wireless Gamepad (almost xbox360 controller) doesn't connect"
date: 2008-10-26
forum: Gaming &amp; Leisure
---

### Post by dreamer84 on 2008-10-26
Hello everyone, (and sorry for the cross-posting, but in hardware/laptop noone cared...)
if I plug the USB-Receiver of my Big Ben Wireless Game Pad (which is almost a xbox360-controller) on ubuntu 8.04, it is found immediately


```

$ sudo tail -fn0 /var/log/messages
Oct 26 11:02:44 tobias-laptop kernel: [ 6880.176356] usb 2-2.3: new low speed USB device using uhci_hcd and address 12
Oct 26 11:02:45 tobias-laptop kernel: [ 6880.388523] usb 2-2.3: configuration #1 chosen from 1 choice
Oct 26 11:02:45 tobias-laptop kernel: [ 6880.468415] input: ACRUX RF USB GAMEPAD 8206 as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input17
Oct 26 11:02:45 tobias-laptop kernel: [ 6880.495144] input,hidraw1: USB HID v1.00 Joystick [ACRUX RF USB GAMEPAD 8206] on usb-0000:00:10.1-2.3

$ lsusb
...
Bus 002 Device 012: ID 1a34:0801  
...
$ dmesg | grep input
...
[ 6880.468415] input: ACRUX RF USB GAMEPAD 8206 as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input17
[ 6880.495144] input,hidraw1: USB HID v1.00 Joystick [ACRUX RF USB GAMEPAD 8206] on usb-0000:00:10.1-2.3

```

and jscalibrator correctly identifies the properties of /dev/input/js0 (7 axis, 10 buttons), but after pressing a button on the pad to connect it just blinks like it doesn't find the receiver. Also the label ACRUX RF USB GAMEPAD 8206 seems strange. The Win-driver from CD (TF0801.Inf) was tested with ndiswrapper and installed correctly but didn't change anything. Does anyone have an idea what to do? It seems like the receiver needs an order to activate listening for the pad.
I also tried ubuntu's xpad module without success. Now before I try [http://ubuntuforums.org/showthread.php?t=825464](http://ubuntuforums.org/showthread.php?t=825464) grumbels xpad-driver I first would like to know whether that try would be worth the pain or there may be other solutions...
Thanks & regards
dreamer84

edit: I tried grumbels xboxdrv (see [http://ubuntuforums.org/showpost.php?p=6035924&postcount=77]("http://ubuntuforums.org/showpost.php?p=6035924&postcount=77")) without much success, now I'll use [http://sourceforge.net/projects/usbsnoop/]("http://sourceforge.net/projects/usbsnoop/") and try to find the windows driver sync part... (the usb stick does not have a sync like the xbox one has, so there must be a software instruction)
this may take a while though...

---

### Post by dreamer84 on 2008-11-10
Using [SnoopyPro 0.22]("http://www.sourceforge.net/projects/usbsnoop/") I could log the URB for the pad, however I don't know much about USB, so could someone experienced with it please tell me how I can make the pad work under linux?

In Windows it's recognized as USB\Vid_1a34&Pid_0801&Rev_0102,USB\Vid_1a34&Pid_0801 BBI USB WIRELESS CONRTOLLER

The attached log contains the log when I plug in the receiver, wait about five seconds, push a button to connect the pad, then push some random buttons and finally pull the plug again. If additional logs are required I'll happily deliver them if there is hope to have the pad connect in linux...

---

### Post by flesh1911 on 2009-08-07
It certanly works with kernel version 2.6.24.

---

### Post by dreamer84 on 2009-08-19
> **flesh1911 said:**
> It certanly works with kernel version 2.6.24.

I cannot confirm that (2.6.24-24-generic). Which ubuntu do you use? I'm still using hardy.

---

### Post by flesh1911 on 2009-08-28
> **dreamer84 said:**
> I cannot confirm that (2.6.24-24-generic). Which ubuntu do you use? I'm still using hardy.

It was tested in Gentoo using gentoo-sources.

---

