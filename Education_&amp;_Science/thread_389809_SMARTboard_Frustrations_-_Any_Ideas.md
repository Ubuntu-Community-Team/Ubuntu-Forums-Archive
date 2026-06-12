---
title: "SMARTboard Frustrations - Any Ideas"
date: 2007-03-21
forum: Education &amp; Science
---

### Post by timgayler on 2007-03-21
I need to be able to use an electronic whiteboard as a teacher.

I've installed the software for it from [http://smartboard.co.uk/](http://smartboard.co.uk/) on Ubuntu 6.10

The install has completed with no error messages - and the software (notebook etc) launches on my computer (an Acer Aspire 5100 laptop) with no problems

When I plug in the USB lead from my whiteboard the LED on the whiteboard flashes green briefly - then stabilises at red - indicating a problem (it will work happily if I boot into windows xp)

When I use the softwares control center to detect the board - it cannot detect the board

Using dmesg at the command line I get the following information....

[17182172.812000] usb 1-3: new full speed USB device using ohci_hcd and address 5
[17182173.020000] usb 1-3: configuration #1 chosen from 1 choice
[17182221.144000] usb 1-3: USB disconnect, address 5
[17182244.884000] usb 1-3: new full speed USB device using ohci_hcd and address 6
[17182245.088000] usb 1-3: configuration #1 chosen from 1 choice
[17182245.092000] pl2303 1-3:1.0: pl2303 converter detected
[17182245.092000] usb 1-3: pl2303 converter now attached to ttyUSB0

This seems to indicate to me that it is connecting at ttyUSB0

When I use the softwares control panel to manually connect to ttyUSB0 - no smart board can be detected.

I suspect permissions. So looking at permissions for ttyUSB0 I have

tim@naboo:~$ ls -la /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 0 2007-03-21 09:29 /dev/ttyUSB0

However if I then use chmod to give add rw permissions as so

tim@naboo:~$ sudo chmod a+rw /dev/ttyUSB0

Changing the permissions to

tim@naboo:~$ ls -la /dev/ttyUSB0
crw-rw-rw- 1 root dialout 188, 0 2007-03-21 09:29 /dev/ttyUSB0

When I again manually try get the board to attach at ttyUSB0 it cannot find it.

The installation creates a rules file at /etc/udev/rules.d/SMARTBoard.rules

I've examined the rules file - but am unsure as to any changes that should/could be made here to allow connections

It currently states

BUS=="usb", KERNEL=="hiddev*", SYSFS{idVendor}=="0b8c", NAME="%k", MODE="0666"
SUBSYSTEM=="usb_device", ACTION=="add", SYSFS{idVendor}=="0b8c", MODE="0666"
SUBSYSTEM=="usb", ACTION=="add", ENV{PRODUCT}=="b8c/*", RUN+="/bin/sh -c '/bin/chmod 666 $env{DEVICE}'"
KERNEL=="ttyS*", NAME="%k", MODE="0666"

The software also states that if there are problems '..If you can't access USB devices while logged on as a non-root user, check the permissions of /dev/hiddev*'

I cannot find hiddev at /dev/hiddev*. However I can find it at the following locations

tim@naboo:~$ locate hiddev
/usr/include/linux/hiddev.h
/usr/lib/hal/hald-probe-hiddev
/usr/src/linux-headers-2.6.17-10/include/linux/hiddev.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/usb/hiddev.h
/usr/src/linux-headers-2.6.17-10-generic/include/linux/hiddev.h
/usr/src/linux-headers-2.6.17-11-generic/include/linux/hiddev.h
/usr/src/linux-headers-2.6.17-11-generic/include/config/usb/hiddev.h
/usr/src/linux-headers-2.6.17-11/include/linux/hiddev.h

With the following permissions at the first (most likely?) location

tim@naboo:~$ ls -l /usr/include/linux/hiddev.h
-rw-r--r-- 1 root root 6263 2007-02-01 20:18 /usr/include/linux/hiddev.h

I am unsure how to proceed here, I cannot find anyone else using Google who has had this problem. Any help you can give me would be gratefully received

---

### Post by hizaguchi on 2007-03-21
The only way I've ever used a Smartboard with my laptop (also an Aspire 5100) was to just hook it up to the Smartboard's VGA input and use the fglrx driver's extra monitor feature to output my display to the board.  Then I just use a mouse of whatever I want hooked up to the laptop.  I guess you loose some features that way though. :(

---

### Post by timgayler on 2007-03-22
Thankyou hizaguchi - but I've managed to get the projection side working (through a similar way to what you have described). However it's the active side of using the whiteboard that I need to get working.

!!! All ideas welcome

---

### Post by timgayler on 2007-03-22
Thanks to a very helpful email from SMARTBoard support I now have the active side of the screen working 

The solution is below

sudo mv /etc/udev/rules.d/10-SMARTBoard16.rules  /etc/udev/rules.d/60-SMARTBoard16.rules
 

sudo /sbin/udevcontrol reload_rules


 Unplug and re-plug the USB adapter.

Hope this is useful to other people

---

