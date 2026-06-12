---
title: "dmesg is reporting the following error codes"
date: 2006-08-24
forum: Desktop Environments
---

### Post by uberjohn on 2006-08-24
After recovering from the Xorg fiasco I keep seeing the following error in dmesg:

*"[17179616.144000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed."*

Is anyone else seeing this?  Any ideas on the problem?  Possible fixes?

Thanks,
John

---

### Post by dutchman25 on 2006-08-25
I'm assuming your wireless does not work because of the error message.  I used to have that until I used bcm43xx-fwcutter to create the correct firmware for my wireless card (Broadcom 4319).

---

