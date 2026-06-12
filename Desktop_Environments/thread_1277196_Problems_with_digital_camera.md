---
title: "Problems with digital camera"
date: 2009-09-28
forum: Desktop Environments
---

### Post by barna on 2009-09-28
Hi,
I would like to access my digital camera (PTP) from dolphin, as a file system (and not through digikam). In Ubuntu 7.10 this worked fine, in 9.04 and 9.10 I have problems. When opening the camera as
dolphin camera:/, I get sometimes the error message:
```

Unknown error code 150
Bad parameters

```
or if I try several times switching on/off the camera, I can get a list of files sometimes, but when I select some pics and want to copy them via Ctrl+C/Ctrl+V, I get the error message: could not lock device.
Is this a kde issue? Should I post there?
Thanks

---

### Post by barna on 2009-09-28
To give more info: it's a Nikon D90, and the related lines from dmesg:

```

[  912.520050] usb 1-2: new high speed USB device using ehci_hcd and address 6
[  912.653219] usb 1-2: configuration #1 chosen from 1 choice
[  914.769067] kio_kamera[1727]: segfault at 95515ac8 ip 02c2bfb8 sp bf82f510 error 4 in libc-2.10.1.so[2bfd000+151000]
[  915.689883] kio_kamera[1693]: segfault at 95515ac8 ip 02c2bfb8 sp bf82f510 error 4 in libc-2.10.1.so[2bfd000+151000]
[  916.501627] kio_kamera[1720]: segfault at 95515ac8 ip 02c2bfb8 sp bf82f510 error 4 in libc-2.10.1.so[2bfd000+151000]
[  916.730058] kio_kamera[1737]: segfault at 95515ac8 ip 02c2bfb8 sp bf82f510 error 4 in libc-2.10.1.so[2bfd000+151000]
[  916.954605] kio_kamera[1739]: segfault at 95515ac8 ip 02c2bfb8 sp bf82f510 error 4 in libc-2.10.1.so[2bfd000+151000]
[  926.401336] kio_kamera[1745]: segfault at 95515ac8 ip 02c2bfb8 sp bf82f510 error 4 in libc-2.10.1.so[2bfd000+151000]
[  926.817660] kio_kamera[1736]: segfault at 95515ac8 ip 02c2bfb8 sp bf82f510 error 4 in libc-2.10.1.so[2bfd000+151000]
[  926.987479] kio_kamera[1749]: segfault at 95515ac8 ip 02c2bfb8 sp bf82f510 error 4 in libc-2.10.1.so[2bfd000+151000]

```

---

### Post by krazyd on 2009-09-28
your camera doesn't work as a mass storage device?

are you running the latest stable KDE? (4.3.1)

---

### Post by barna on 2009-09-28
Hi,
Sorry, I forgot to specify: my camera is a PTP camera (Nikon D90), which does not work as a usb mass storage device.
It worked very nicely in ubuntu 7.10. I am using KDE 4.3.1 shipped with Ubuntu 9.10 alpha, but I had the same problem in the stable 9.04 as well.
I filed a bug report to KDE.

---

