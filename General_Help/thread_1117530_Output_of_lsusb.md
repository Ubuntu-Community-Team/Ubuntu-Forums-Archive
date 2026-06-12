---
title: "Output of lsusb"
date: 2009-04-06
forum: General Help
---

### Post by spatil on 2009-04-06
Hi,

I am using the command lsusb for the first time i am not aware of what the output explains, can any one help out to identify the fields of the lsusb output

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Just wanted to know that what the Device 001 means in the above output

---

### Post by geraldm on 2009-04-06
bus number 
device number
vendorId: USB vendor code, as mandated by USB standard; hex code
productId manufacturer's product identification code; hex code
Description of the device at that bus number and device number.

regards,
Gerald

---

