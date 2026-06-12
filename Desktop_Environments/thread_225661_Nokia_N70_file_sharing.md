---
title: "Nokia N70 file sharing"
date: 2006-07-30
forum: Desktop Environments
---

### Post by ramiro on 2006-07-30
I am trying to transfer files between my computer and a Nokia N70. Unfortunately, bluetooth is not available on the computer, so I am trying to connect them with the provided USB cable.

Ubuntu doesn't seem to recognise it when I plug it in. This is the output of my /var/log/messages file:

> Jul 30 17:14:36 localhost kernel: [17180357.304000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Jul 30 17:14:36 localhost kernel: [17180357.452000] cdc_acm 1-2:1.8: ttyACM0: USB ACM device

any ideas?

---

### Post by cvmostert on 2006-08-15
> **ramiro said:**
> I am trying to transfer files between my computer and a Nokia N70. Unfortunately, bluetooth is not available on the computer, so I am trying to connect them with the provided USB cable.

Ubuntu doesn't seem to recognise it when I plug it in. This is the output of my /var/log/messages file:



any ideas?

Try lsusb

my n70 is recognised... I can connect to the internet... but not share files yet... but i have just started to play with it in ubuntu.... so just give me some more time.

take care

---

