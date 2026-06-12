---
title: "Dell Inspiron 1520 Webcam not working"
date: 2011-05-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kd4hey on 2011-05-16
Edit 2013-03-21:
In a fresh install of 13.04 (beta) the webcam works without any modifications / *Mörgæs*.

= = = 

Running Ubuntu 10.10 (tried 11.04 & reverted with a fresh install).  Before the "upgrade" to 11.04 the webcam did work.  

I think I'm just missing drivers.

Any help appreciated.

---

### Post by kd4hey on 2011-05-20
Nobody got any ideas?

---

### Post by dyem1 on 2011-05-22
Do you know what webcam you have?
If it is the integrated webcam use ```
lsusb
``` in a terminal and post the output

---

### Post by kd4hey on 2011-05-22
Thank You!

Yes it is intergrated & I see the line that recognizes it, but skype & Cheese don't seem to work.  (They both say "No Devices").

From Terminal:

jim@jim-Inspiron-1520:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Thanks for the reply,

---

### Post by dyem1 on 2011-05-26
Well, upgrading ubuntu version sometimes can do bad things. Your webcam (Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam) is supported in the uvc drivers (it appears in [http://www.ideasonboard.org/uvc/#devices](http://www.ideasonboard.org/uvc/#devices)), so there shouldn't be problems...
I certainly don't know the solution of the problem, but try posting here the output of```
dmesg | grep Webcam
```
after running cheese. That might lead to what the error is.

---

### Post by nmthien on 2011-05-28
I got the same problem when upgrading to 11.04, I'm having the same webcam too. Here's the output on my machine:

[   26.418504] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[33297.788110] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[33297.793518] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input12
[33311.684231] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[33311.685848] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input13
[81374.916325] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[81374.918080] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input14
[81477.190995] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[81477.193777] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input15
[83194.789472] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[83194.794861] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input16

---

### Post by kd4hey on 2011-06-01
[QUOTE=nmthien;10873399]I got the same problem when upgrading to 11.04, I'm having the same webcam too. Here's the output on my machine:

I tried 11.04 & hated it, so I did a clean install of 10.10.  That's when my trouble started.

It was actually Unity that I didn't like & at the time I did not realize I could select Ubuntu classic at log in (I have mine set for auto login), but am considering upgrading again & selecting this.

---

### Post by kd4hey on 2011-06-01
> **dyem1 said:**
> Well, upgrading ubuntu version sometimes can do bad things. Your webcam (Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam) is supported in the uvc drivers (it appears in [http://www.ideasonboard.org/uvc/#devices](http://www.ideasonboard.org/uvc/#devices)), so there shouldn't be problems...
I certainly don't know the solution of the problem, but try posting here the output of```
dmesg | grep Webcam
```
after running cheese. That might lead to what the error is.

I will give it a shot tonight, (I'm currently on my work computer).

Thanks!

---

### Post by kd4hey on 2011-06-01
> **kd4hey said:**
> I will give it a shot tonight, (I'm currently on my work computer).

Thanks!

Here's what Terminal came up with:

[   17.692332] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   17.700689] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input10


Opened Cheese & it works!  Opened Skype & it worked too, there must have been an update or something because I couldn't get it to work last week.

Thanks to everyone for your tips!

---

### Post by GrouchyGaijin on 2012-02-26
> **kd4hey said:**
> Here's what Terminal came up with:

[   17.692332] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   17.700689] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input10



Hi Guys,

I'm actually on Mint 12 which is based on Ubuntu.
I have the same machine and can't get my webcam to work.
when I run the above code I get  

```

john@mint-12 ~ $ dmesg | grep Webcam
[   20.657982] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)

```

Any idea on how I should proceed?

Thanks.

---

