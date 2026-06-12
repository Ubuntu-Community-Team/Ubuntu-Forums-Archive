---
title: "xps m1330: Webcam not working in 13.04"
date: 2013-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by giuliocoluccia on 2013-05-17
Hello,
I installed Ubuntu 13.04 32 bit on my (not so) old Dell XPS m1330. Everything seems to be working out of the box, except for the webcam, which is not recognized as a video input device. Here's the output of ```
dmesg | grep -i video
```:
```

[   13.608421] Linux video capture interface: v2.00
[   13.878382] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[   13.878750] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   13.879124] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   13.879199] uvcvideo: Failed to initialize the device (-5).
[   13.879421] usbcore: registered new interface driver uvcvideo
[   13.879423] USB Video Class driver (1.1.1)

```

While ```
lsusb
``` outputs, among the others,
```

Bus 002 Device 003: ID 05a9:7670 OmniVision Technologies, Inc. OV7670 Webcam

```

My kernel is
```

3.8.0-21-generic

```

I've tried some solutions found on the internet (like reloading the uvcvideo kernel module) but nothing seems to be working.

---

### Post by fdrake on 2013-05-17
i don't see a solution without pathing the kernel so that you can use 13.04. Your computer looks fully supported for ubuntu 11.10. I would just keep the most compatible version installed on it or keep more than 1 kernel available .
[https://friendly.ubuntu.com/11.10/Dell%20Inc./XPS%20M1330/I:BqVBWp:RJ:BHe:IZ:BEip:EZE:I8g:BEb:I8g/](https://friendly.ubuntu.com/11.10/Dell%20Inc./XPS%20M1330/I:BqVBWp:RJ:BHe:IZ:BEip:EZE:I8g:BEb:I8g/)

---

### Post by giuliocoluccia on 2013-05-17
Thanks for your reply. So basically you're suggesting to rollback ubuntu to a 2 years old version to preserve compatibility. I'll try with a live version to see if this is working, thanks for the suggestion, even if it always looks strange to me how it is possible that updates break what was working (quite a lot of time ago...).

---

### Post by giuliocoluccia on 2013-05-17
An interesting update: don't ask me why, I retried with
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo
```

and voilà, now it works! So it seems that this is a matter of sorting things during the startup. Indeed, now ```
dmesg | grep -i video
``` doesn't give a failure after enabling the workaround.

Does anybody know how to fix it?

---

### Post by giuliocoluccia on 2013-05-17
I solved it (I cannot mark the thread as "solved"). I bypassed the control that fails by setting the quirks in uvcvideo to 0x100.
So, I created a file /etc/modprobe.d/uvcvideo.conf with the following content
options uvcvideo quirks=0x100

---

### Post by fbiondip on 2013-05-30
I had same problem and solved this way= [http://askubuntu.com/questions/300060/skype-no-video-in-13-04](http://askubuntu.com/questions/300060/skype-no-video-in-13-04)

---

### Post by GediminasPaulauskas on 2013-06-11
> **giuliocoluccia said:**
> I solved it (I cannot mark the thread as "solved"). I bypassed the control that fails by setting the quirks in uvcvideo to 0x100.
So, I created a file /etc/modprobe.d/uvcvideo.conf with the following content
options uvcvideo quirks=0x100

Thank you, this workaround helped to make my webcam work again.

Dell XPS M1330
ID 05a9:7670 OmniVision Technologies, Inc. OV7670 Webcam

---

### Post by cyrs on 2013-12-28
> **giuliocoluccia said:**
> I solved it (I cannot mark the thread as "solved"). I bypassed the control that fails by setting the quirks in uvcvideo to 0x100.
So, I created a file /etc/modprobe.d/uvcvideo.conf with the following content
options uvcvideo quirks=0x100

I just want to thank giuliocoluccia for the above solution.


My problem was with a the integrated webcam in a Dell SP2309W monitor (05a9:2649). This webcam was working fine under Ubuntu 13.04. But after a Ubuntu 13.10 clean install, it didn't work. dmesg was outputting:
```
[   18.403051] Linux video capture interface: v2.00
[   18.461557] uvcvideo: Found UVC 1.00 device Monitor Webcam (05a9:2649)
[   18.461965] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   18.462340] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   18.462344] uvcvideo: Failed to initialize the device (-5).

```

Creating the file /etc/modprobe.d/uvcvideo.conf with the following content
options uvcvideo quirks=0x100
fixed the problem.  My webcam is now working.


For info, now I get the following messages (dmesg)
```
[   18.908804] Linux video capture interface: v2.00
[   18.916327] uvcvideo: Found UVC 1.00 device Monitor Webcam (05a9:2649)
[   18.916330] uvcvideo: Forcing device quirks to 0x100 by module parameter for testing purpose.
[   18.916332] uvcvideo: Please report required quirks to the linux-uvc-devel mailing list.
[   18.916923] input: Monitor Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.1/1-5.1:1.0/input/input4
[   18.916997] usbcore: registered new interface driver uvcvideo
[   18.916999] USB Video Class driver (1.1.1)

```

---

