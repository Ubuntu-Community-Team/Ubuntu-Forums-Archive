---
title: "Mouse and Keyboard not working at login screen"
date: 2010-12-26
forum: Desktop Environments
---

### Post by whochismo on 2010-12-26
Hello,

I've been having this problem for a week or so. I'm using Ubuntu Maverick 10.10. When ubuntu shows the login screen (gdm), I must wait about 3 minutes until the usb mouse and keyboard start working. Then, they seem to work properly, but other usb devices such as a logitech webcam do not work at all. I get the following error messages:

```

[   46.920259] usb 2-2: device descriptor read/64, error -110
[   62.150272] usb 2-2: device descriptor read/64, error -110
[   67.411857] usb 2-2: device descriptor read/8, error -110
[   72.540299] usb 2-2: device descriptor read/8, error -110
[   77.800304] usb 2-2: device descriptor read/8, error -110
[   82.930649] usb 2-2: device descriptor read/8, error -110
[   83.040256] hub 2-0:1.0: unable to enumerate USB device on port 2
[   98.660266] usb 4-2: device descriptor read/64, error -110
[  113.950260] usb 4-2: device descriptor read/64, error -110
[  129.420261] usb 4-2: device descriptor read/64, error -110
[  144.710266] usb 4-2: device descriptor read/64, error -110
[  150.030997] usb 4-2: device descriptor read/8, error -110
[  155.160318] usb 4-2: device descriptor read/8, error -110
[  160.481199] usb 4-2: device descriptor read/8, error -110
[  165.611541] usb 4-2: device descriptor read/8, error -110
[  165.720274] hub 4-0:1.0: unable to enumerate USB device on port 2

```

EDIT: I even reinstalled all my system and went back to ubuntu 10.04, but the problem was still there. Later on, I realised it was my webcam's fault. I disconnected it and the problem was gone!

---

