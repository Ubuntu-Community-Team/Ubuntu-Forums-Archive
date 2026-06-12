---
title: "Webcam &amp; ubuntu question"
date: 2009-06-01
forum: General Help
---

### Post by texas.chef94 on 2009-06-01
This is my first attempt to use or configure a web cam and obviously its a bit more complicated in amsn. At any rate I have a retired buddy with a Mac who wants to communicate via web cam and he is on MSN.
The amsn forum has not really provided me with a solution nor has googling. So thought I would give ubuntu a shot in hopes someone has some pointers. My web Cam is a creative and I have no windows

As always thanks

Allen

---

### Post by keplerspeed on 2009-06-01
Firstly, does the webcam work out of the box?

To find out, install camorama from synaptic. This little utility will open and show the webcam working if driver is present.

If the webcam doesnt work with camorama, issue this command to the terminal so we know exactly the webcam:
```

lsusb

```
Assuming that its a usb webcam.

---

### Post by texas.chef94 on 2009-06-01
> **keplerspeed said:**
> Firstly, does the webcam work out of the box?

To find out, install camorama from synaptic. This little utility will open and show the webcam working if driver is present.

If the webcam doesnt work with camorama, issue this command to the terminal so we know exactly the webcam:
```

lsusb

```
Assuming that its a usb webcam.

Hey thanks will give it a shot

---

### Post by texas.chef94 on 2009-06-01
It is USB and that is terminal results

allen@allen-desktop:~$ lsusb
Bus 001 Device 004: ID 1058:0702 Western Digital Technologies, Inc. Passport External HDD
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 04b3:3108 IBM Corp. 800dpi Optical Mouse w/ Scroll Point
Bus 003 Device 002: ID 03f0:2f11 Hewlett-Packard PSC 1200
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 041e:4034 Creative Technology, Ltd WebCam Instant
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
allen@allen-desktop:~$

---

