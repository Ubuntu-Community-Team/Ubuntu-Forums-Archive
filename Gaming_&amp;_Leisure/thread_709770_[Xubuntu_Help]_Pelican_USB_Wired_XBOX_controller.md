---
title: "[Xubuntu Help] Pelican USB Wired XBOX controller"
date: 2008-02-27
forum: Gaming &amp; Leisure
---

### Post by xaer0knight on 2008-02-27
okay here is a quick round down. Using Xubuntu 7.10, i have this Pelican PL-2023 XBOX Controller that fashioned into a USB controller. Works flawlessly in Windows XP SP2 for the last 3 years. I can't seem to get it to work at all. I've gone threw every forum post and still no luck seeing if this controller will work. I've connected it straight to the back of the computer via USB Port and have tried it via my USB Hub, still no luck. I have followed this tutorial: [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller) too the T's and I's but still no luck. Ya, i know its for the XBOX360 but I am at wits end. jscalibrator doesn't see it nor the "cat" command see the device!

Below is a list of things, I've encounter while in the Terminal. I NEED HELP FROM ANYONE at this point.

jason@jason-desktop:~/xpad$ dmesg

[15108.112221] usbcore: registered new interface driver xpad
[15108.113143] /home/jason/xpad/xpad.c: driver for Xbox controllers v0.1.7

jason@jason-desktop:~/xpad$ jscalibrator

jason@jason-desktop:~/xpad$ cat /dev/input/js0
cat: /dev/input/js0: No such file or directory

jason@jason-desktop:~/xpad$ lsusb

Bus 001 Device 016: ID 0e6f:8802  
Bus 001 Device 015: ID 0e6f:8801  
Bus 001 Device 012: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 003: ID 13b1:000d Linksys 
Bus 001 Device 001: ID 0000:0000  

jason@jason-desktop:~/xpad$ tail -f /var/log/messagesFeb 27 18:06:36 jason-desktop kernel: [14894.680806] usb 1-1.3.1: USB disconnect, address 14

Feb 27 18:06:59 jason-desktop kernel: [14917.168822] usb 1-1.3: new full speed USB device using uhci_hcd and address 15
Feb 27 18:06:59 jason-desktop kernel: [14917.293197] usb 1-1.3: configuration #1 chosen from 1 choice
Feb 27 18:06:59 jason-desktop kernel: [14917.296207] hub 1-1.3:1.0: USB hub found
Feb 27 18:06:59 jason-desktop kernel: [14917.297772] hub 1-1.3:1.0: 3 ports detected
Feb 27 18:06:59 jason-desktop kernel: [14917.608638] usb 1-1.3.1: new full speed USB device using uhci_hcd and address 16
Feb 27 18:07:00 jason-desktop kernel: [14917.733026] usb 1-1.3.1: configuration #1 chosen from 1 choice
Feb 27 18:10:04 jason-desktop kernel: [15102.477845] usbcore: deregistering interface driver xpad
Feb 27 18:10:10 jason-desktop kernel: [15108.112221] usbcore: registered new interface driver xpad
Feb 27 18:10:10 jason-desktop kernel: [15108.113143] /home/jason/xpad/xpad.c: driver for Xbox controllers v0.1.7

Thanks so much!

---

### Post by acoustibop on 2008-02-27
For starters, I'd recommend getting rid of jscalibrator, xaer0knight.  You shouldn't really need a calibrator for a USB controller, and jscalibrator has a nasty habit of disabling controls, particularly directional ones, often still reporting them itself as working.  The version that's native to Kubuntu is, apparently, Ok, but all other versions...  If you do remove it, remove its configuration as well.

If you really need a calibrator, there's joystick (also in the repositories), which installs two command line utilities, jscal and jstest.

---

### Post by hdanak on 2008-03-31
I have almost exactly the same problem with an old xbox controller (converted to usb), which everyone says should work out-of-the-box with ubuntu gutsy. I have tried almost everything (including jscalibrator, which i later removed, still doesn't work; also tried joystick: jscal and jstest, and the kde joystick utility). It detects in usb (dmesg and lsusb) but there are no /dev/input/js[0-3] nodes made. Thanks for any help.

---

