---
title: "Latitude E5410 - Mobile Broadband (Dell Wireless 5620)"
date: 2011-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ColdFFF on 2011-02-15
I'm running lucid on one of these laptops, and really having a hard time getting mobile broadband working.

I have done a fair bit of research on this, and as far as I can tell the 5620 is actually a Qualcomm GOBI 2000. Further research led me to various guides and launchpad bugs related to this hardware (unfortunately very little specific to the Dell branded version).

Of particular interest was [_this bug report_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/+index?comments=all").
TLDR of this report is kernels 2.6.32 and later fail to load the hardware correctly, workaround is to install backport, gobi-loader and the necessary firmware.

So, I installed the appropriate backport:
linux-backports-modules-wwan-lucid-generic

Installed gobi-loader:
choice of compiling from source or installing from [_this_]("https://launchpad.net/~linrunner/+archive/thinkpad-extras") ppa

And extracted the firmware from the windows installer and moved the 3 required files to /lib/firmware/gobi


Unfortunately, at this point I feel like I have made no progress at all. Network Manager does not allow me to use mobile broadband (the tab is there, but when I click "add" the device selection is greyed out).

I have absolutely no idea what my next step would be from here. Any ideas on what I can do?



For reference:

```

uname -a
Linux glidex5 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux


lsusb
Bus 002 Device 002: ID 8087:0020 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 413c:8185 Dell Computer Corp.
Bus 001 Device 002: ID 8087:0020 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lsmod | grep -i qcserial
qcserial                4356  0
usb_wwan               12209  1 qcserial
usbserial              39131  2 qcserial,usb_wwan


dmesg | grep -i usb
--trimmed--
[   15.451862] usbcore: registered new interface driver usbserial
[   15.451896] USB Serial support registered for generic
[   15.451925] usbcore: registered new interface driver usbserial_generic
[   15.451927] usbserial: USB Serial Driver core
[   15.637031] USB Serial support registered for Qualcomm USB modem
[   15.637116] qcserial 1-1.6:1.1: Qualcomm USB modem converter detected
[   15.637212] usb 1-1.6: Qualcomm USB modem converter now attached to ttyUSB0
[   15.637229] usbcore: registered new interface driver qcserial

```


Additionally, I'm not really sure if this is in anyway related, but I was digging through syslog for any errors related to the device and came across this:
```

Feb 15 15:50:14 glidex5 init: udevtrigger post-stop process (575) terminated with status 1
Feb 15 15:50:14 glidex5 kernel: [  195.187145] padlock: VIA PadLock Hash Engine not detected.
Feb 15 15:50:14 glidex5 modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.32-28-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
Feb 15 15:50:14 glidex5 udevd[460]: worker [468] unexpectedly returned with status 0x0100
Feb 15 15:50:14 glidex5 udevd[460]: worker [468] failed while handling '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/ttyUSB0/tty/ttyUSB0'
Feb 15 15:50:14 glidex5 kernel: [  195.594726] Adding 6384632k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:6384632k
Feb 15 15:51:23 glidex5 ntpd[1874]: synchronized to 91.189.94.4, stratum 2

```
however, I'm not going to pretend that I understand any of that.

---

