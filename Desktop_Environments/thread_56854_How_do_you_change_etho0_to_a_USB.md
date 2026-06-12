---
title: "How do you change etho0 to a USB"
date: 2005-08-14
forum: Desktop Environments
---

### Post by BKK on 2005-08-14
Kubuntu knows that there is a USB broadband modem on the USB port. The driver and all that shows up.

How do you configure it to look at the USB port instead of a Ethernet port?

---

### Post by nad on 2005-08-14
You need to run the pppoe setup tool.

Once configured, eth0 will be automatically bound to your usb device.

---

### Post by BKK on 2005-08-14
[QUOTE=nad]You need to run the pppoe setup tool.

Once configured, eth0 will be automatically bound to your usb device.[/QUOTE]

Thanks are you refering to ppoeconf? I tried that and it looks only to the NIC for a network not to the USB.

Is there something else I can try? Sorry but I am new to this.

adsl-setup is not a recognized command either

---

