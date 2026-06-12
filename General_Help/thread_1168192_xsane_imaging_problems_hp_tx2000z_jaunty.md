---
title: "xsane imaging problems hp tx2000z jaunty"
date: 2009-05-23
forum: General Help
---

### Post by sha.goyjo on 2009-05-23
I have an HP TX2000z CTO laptop, running (or perhaps failing to run) a CanoScan N 650u usb powered scanner.

It might be worth noting that my laptop also has a built-in webcam. Webcam functions in Ekiga perfectly. I don't know if its interfering with xsane.

Whenever I attempt to start xsane, I recieve the following error
"Failed to open device `v4l:/dev/video0': Invalid argument"

Any advice guys?

---

### Post by rudy.b on 2009-05-24
If you haven't done so, check the output of the following terminal commands to see if your scanner is properly detected:

```
$ lsusb
$ sudo sane-find-scanner
$ scanimage -L
```

Further reference: [ScanningHowTo]("https://help.ubuntu.com/community/ScanningHowTo")

---

### Post by sha.goyjo on 2009-05-24
lsusb output:
```

Bus 002 Device 013: ID 04a9:2206 Canon, Inc. CanoScan N650U/N656U
Bus 002 Device 012: ID 056a:0093 Wacom Co., Ltd 
Bus 002 Device 011: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 010: ID 064e:a110 Suyin Corp. 
Bus 002 Device 009: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
sudo sane-find-image output:
```

found USB scanner (vendor=0x04a9, product=0x2206, chip=LM983x?) at libusb:002:013
found USB scanner (vendor=0x08ff, product=0x1600 [Fingerprint Sensor]) at libusb:002:011

```
scanimage -L output:
```

device `v4l:/dev/video0' is a Noname HP Webcam virtual device

```

It might also be worth noting that the device output of scanimage -L is the same as the error xsane is reporting.

---

### Post by rudy.b on 2009-05-25
It looks like your system is detecting your scanner (from the lsusb and sane-find-scanner output) but for some reason it's not in the list of available devices (the scanimage -L output).  From a bug report[1] I found in launchpad, it looks like a problem that was introduced with Jaunty.

[1][Sane can't find Canon CanoScan N650U]("https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/361278")

---

### Post by sha.goyjo on 2009-05-26
Yes, but has anybody figured out how to fix it?

---

