---
title: "Problems with fingerprint on Lenovo N200"
date: 2009-04-15
forum: General Help
---

### Post by Mozes251 on 2009-04-15
First 10q for inventing this OS. It is absolutly fantastic. Second, please excuse my english, I`m trying to inprove it.

The problem:

I had install thinkfinger-0.3 on my OS using wiki tutorial for fingeprints on laptop using Ubuntu 8.10. But (it's always a BUT :)) when i type tf-tool --acquire in my console the message is:
ThinkFinger 0.3 ([http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/))
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.
mozes@inside:~$ 

When I type lsusb:

mozes@inside:~$ lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 003: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

..the fingerprint sensor is there.
I also install fprint-demo to see if it works. And it does.
Can u help me please?

Like I said, please excuse my english.
Thank you very much

---

### Post by Mozes251 on 2009-04-15
No solution to my problem?

---

### Post by cooltml2142 on 2009-04-16
Try uninstalling the driver and do it over. That worked for me.

---

