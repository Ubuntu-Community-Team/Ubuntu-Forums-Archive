---
title: "Connecting devices to Dell"
date: 2011-08-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rohyt on 2011-08-22
I have got dell vostro 1015 with ubuntu lucid..i installed nokia pc suite through wine..the software installs well but doesnt show mobile connectivity..Similarly canon scanner also doesnt show its connectivity..is there is any method i can use devices through software installed in wine?? Plz

---

### Post by ~!geek!~ on 2011-08-22
You don't need pc suite to use your device. Ubuntu has fair support for nokia devices. If you select mass storage on nokia, phone memory card will be mounted as any other storage device. To connect to internet, select pcsuite mode on device, and than use network manager available in ubuntu to setup your phone...
I don't have any experience with canon scanners, but if ubuntu has driver support for it, you can try to install some frontend software for scanning by searching in software center or synaptic manager, and just try to see if you are able scan..
Also as another check, if your scanner is detected by ubuntu just check the devices connected using usb by typing the command: lsusb in terminal and see there.

---

