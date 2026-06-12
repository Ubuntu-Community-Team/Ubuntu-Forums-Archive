---
title: "XBOX360 Controller Troubles"
date: 2008-08-24
forum: Gaming &amp; Leisure
---

### Post by BoGs on 2008-08-24
I have done all the tutorials I can think of and still nothing works.... tried the xpad and the driver itsself and still doesnt work.

if anyone has any ideas please let me know.

```
bogdan@bogdan-linux:~/Desktop/xpad360$ sudo lsmod | grep xpad
xpad                   11140  0 
usbcore               146028  6 xpad,ossusb,usbhid,ehci_hcd,uhci_hcd
bogdan@bogdan-linux:~/Desktop/xpad360$ sudo lsmod | grep joydev
joydev                 13120  0 

```

```
bogdan@bogdan-linux:~/Desktop/xpad360$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 006: ID 045e:028f Microsoft Corp. Xbox360 Wireless Controller
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046d:c512 Logitech, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

```

```
bogdan@bogdan-linux:~/Desktop/xpad360$ uname -a
Linux bogdan-linux 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

```



```
[  767.014193] usb 4-1: USB disconnect, address 3
[  771.752660] usb 4-1: new full speed USB device using uhci_hcd and address 4
[  771.917444] usb 4-1: configuration #1 chosen from 1 choice
[ 1303.601032] usb 4-1: USB disconnect, address 4
[ 1321.758814] usbcore: registered new interface driver xpad
[ 1321.758818] /home/bogdan/Desktop/xpad360/xpad.c: driver for Xbox controllers v0.1.7
[ 1343.385139] usb 4-1: new full speed USB device using uhci_hcd and address 5
[ 1343.548931] usb 4-1: configuration #1 chosen from 1 choice
[ 1471.559160] usbcore: deregistering interface driver xpad
[ 1509.078413] usbcore: registered new interface driver xpad
[ 1509.078418] /home/bogdan/Desktop/xpad360/xpad.c: driver for Xbox controllers v0.1.7
[ 1512.988711] usb 4-1: USB disconnect, address 5
[ 1517.072472] usb 4-1: new full speed USB device using uhci_hcd and address 6
[ 1517.236261] usb 4-1: configuration #1 chosen from 1 choice
[ 1574.492405] usbcore: deregistering interface driver xpad
[ 1577.230694] usbcore: registered new interface driver xpad
[ 1577.230698] /home/bogdan/Desktop/xpad360/xpad.c: driver for Xbox controllers v0.1.7

```

```

bogdan@bogdan-linux:~/Desktop/xpad360$ ls /dev/input
by-id    event0  event2  event4  mice    mouse1
by-path  event1  event3  event5  mouse0  uinput

```

---

### Post by rundy on 2008-09-10
Hi,
I'm in a similar situation to you,
I've read through literally all the documentation around this issue and I can't figure it out (yet) either,

I did have a controller working in hardy
then I purchased a new one, (it is in fine working order) the new controller plugs in and identifies, the xpad module loads, the led in the centre chooses a 'player number', /dev/input/js0 exists but apart from all that it isn't usable, 


```

brian@mobiler:~$ lsmod | grep xpad
xpad                   11784  0 
led_class               6020  1 xpad
ff_memless              6792  1 xpad
usbcore               146028  5 xpad,hci_usb,ehci_hcd,uhci_hcd

brian@mobiler:~$ lsmod | grep joydev
joydev                 13120  0 

brian@mobiler:~$ lsusb
Bus 004 Device 002: ID 045e:028e Microsoft Corp. Xbox360 Controller

brian@mobiler:~$ tail /var/log/messages
Sep 11 13:27:35 mobiler kernel: [  654.649887] usb 4-2: new full speed USB device using uhci_hcd and address 2
Sep 11 13:27:36 mobiler kernel: [  654.660864] usb 4-2: configuration #1 chosen from 1 choice
Sep 11 13:27:50 mobiler kernel: [  655.996212] Registered led device: xpad0
Sep 11 13:27:50 mobiler kernel: [  655.996335] input: Microsoft X-Box 360 pad as /devices/pci0000:00/0000:00:1d.0/usb4/4-2/4-2:1.0/input/input11
Sep 11 13:27:50 mobiler kernel: [  656.037487] usbcore: registered new interface driver xpad
Sep 11 13:27:50 mobiler kernel: [  656.037500] /build/buildd/linux-2.6.24/drivers/input/joystick/xpad.c: X-Box pad driver:


```

My Device ID is slightly different to yours, I'll try to get the original controller that worked again and test it, and report back... It might be a problem with some controllers.

---

### Post by rundy on 2008-09-12
I managed to get my controller operating, I had to compile a different version of the module and replace the original one,

I followed the instruction given on this page
[http://ubuntuforums.org/showthread.php?t=404577&page=13]("http://ubuntuforums.org/showthread.php?t=404577&page=13")

This gave me a driver that would crash my usb subsystem making the machine unusable until I restarted, the solution was to integrate the patch, this fixed the usb problems. I noticed that the controller led continues to blink using this method.

I can't find the site I got the patch from, so I've zipped the files I used to make this work, and attached them to this post.
The zip contains xpad.o that I built here, you may be able to just overwrite this with the one in /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick
as per the Makefile.
Remember to backup your existing file just in case.

---

