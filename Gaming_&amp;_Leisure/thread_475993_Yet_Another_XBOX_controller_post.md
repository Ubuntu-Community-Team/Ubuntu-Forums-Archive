---
title: "Yet Another XBOX controller post"
date: 2007-06-16
forum: Gaming &amp; Leisure
---

### Post by robog2 on 2007-06-16
Hey guys.  My xbox controller worked before I upgraded to feisty, but now it wont.  Jscalibrator does not recognize it, nor do any games, and js0 does not show up in /dev/input/.  I have already read all other posts in the forums on xbox controllers, and have even tried installing the xbox360 version of the xpad to get this to work.  I followed the advice of another post and ran:
> 
$ sudo modprobe -r xpad
$ sudo tail -fn0 /var/log/messages

This is what I got:

> Jun 16 18:09:36 localhost kernel: [ 2926.496341] usbcore: registered new interface driver xpad
Jun 16 18:09:36 localhost kernel: [ 2926.496363] /home/garrett/.xpad360/xpad.c: X-Box pad driver:v0.0.7

Any help would be greatly appreciated.

Thanks

---

### Post by robog2 on 2007-06-17
Any Ideas?

(sorry for the bump)

---

### Post by kitfrog on 2007-06-18
Hey,

Do you have the device /dev/input/js0 ? Try the following:

```
cat /dev/input/js0
```

and press some buttons. If you see some characters being printed to the terminal then the pad is connected. Otherwise it's something else.

I have had an issue with feisty where the xbox pad isn't recognised if I leave it plugged in at boot. Unplugging and plugging it back in fixes it.

Good luck!

---

### Post by robog2 on 2007-06-18
Here's what I get:

```
garrett@garrett-laptop:~$ cat /dev/input/js0
cat: /dev/input/js0: No such file or directory

```

I tried plugging it into all usb ports, and still get the same result.

---

### Post by po0f on 2007-06-19
robog2,

When running the `sudo tail...` command and plugging your controller in, is that all the output you get?  Mine is similar to the following (vanilla Xbox controller, modified-for-360 xpad driver):

```
Jun 19 17:10:40 po0fbox kernel: [842476.620340] usb 3-1: new full speed USB device using uhci_hcd and address 2
Jun 19 17:10:40 po0fbox kernel: [842476.782069] usb 3-1: configuration #1 chosen from 1 choice
Jun 19 17:10:40 po0fbox kernel: [842476.784985] hub 3-1:1.0: USB hub found
Jun 19 17:10:40 po0fbox kernel: [842476.787906] hub 3-1:1.0: 3 ports detected
Jun 19 17:10:41 po0fbox kernel: [842477.129196] usb 3-1.1: new full speed USB device using uhci_hcd and address 3
Jun 19 17:10:41 po0fbox kernel: [842477.247088] usb 3-1.1: configuration #1 chosen from 1 choice
Jun 19 17:10:41 po0fbox kernel: [842477.694871] input: Microsoft Xbox Controller S as /class/input/input7
Jun 19 17:10:41 po0fbox kernel: [842477.696028] usbcore: registered new interface driver xpad
Jun 19 17:10:41 po0fbox kernel: [842477.696380] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
Jun 19 17:10:43 po0fbox kernel: [842478.974166] drivers/usb/input/xpad.c: opening device
Jun 19 17:10:43 po0fbox kernel: [842478.974199] drivers/usb/input/xpad.c: closing device
Jun 19 17:10:43 po0fbox kernel: [842478.993629] drivers/usb/input/xpad.c: opening device
Jun 19 17:10:43 po0fbox kernel: [842478.996457] drivers/usb/input/xpad.c: closing device
Jun 19 17:10:43 po0fbox kernel: [842479.059260] drivers/usb/input/xpad.c: opening device
Jun 19 17:10:43 po0fbox kernel: [842479.059330] drivers/usb/input/xpad.c: closing device
```

As far as you can tell you have no other USB issues?  And the driver version you appear to be using is the stock Ubuntu one (v0.0.7).

I just thought of something: are you using the original, football-sized Xbox controller?  Mine is the smaller one.  And did you modify this controller yourself or purchase one of the adapter dongles?

---

