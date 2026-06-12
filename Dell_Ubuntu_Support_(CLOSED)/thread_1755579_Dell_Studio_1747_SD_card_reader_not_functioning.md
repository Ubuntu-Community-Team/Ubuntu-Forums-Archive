---
title: "Dell Studio 1747 SD card reader not functioning"
date: 2011-05-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mpnordland on 2011-05-11
Here is the output from dmesg | tail

```
[11767.294076] sdhci: ===========================================
[12227.450617] usb 2-1.1: new low speed USB device using ehci_hcd and address 6
[12227.568448] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input12
[12227.568797] generic-usb 0003:046D:C016.0002: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1.1/input0
[12694.125859] dell-wmi: Unknown key 3a pressed
[12695.509434] dell-wmi: Unknown key 3a pressed
[12696.565291] dell-wmi: Unknown key 3a pressed
[12697.833830] dell-wmi: Unknown key 3a pressed
[12760.018340] mmc0: ADMA error
[12760.018403] mmc0: error -5 whilst initialising SD card

```
I get that error -5 consistently.
System specs:
```
micah@micah-dell:~$ uname -a
Linux micah-dell 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by oly on 2011-06-19
I have been hit by this as well, on a dell studio there is a bug open for it here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774385](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774385) but the bug has been there for quite a while and its still not fixed so i dont hold out much hope, but may be worth subscribing to the bug incase someone does fix it, i am considering upgrading to the next beta dont really want to but dont have much choice as my slr is not much use with out a working sd card reader :/

---

### Post by mpnordland on 2011-06-20
I added that it affects me, I hope it will get fixed, cause I like shotwell, and for some reason it won't copy files larger than 1 GB from my camera, so I use the gphoto2 command, and that works just dandy. I am hoping that maybe once it works I'll be able to just use shotwell. I don't know if it will be working in oneric, however, I've been using Ubuntu since karmic, and it has never worked. I keep hoping that with each new release that I'll be surprised, but I keep getting let down.

---

