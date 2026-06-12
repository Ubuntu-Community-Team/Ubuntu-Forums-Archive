---
title: "Dell Inspiron 530s Ubuntu 11.10 Wireless Firmware Not Installed"
date: 2011-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Armaniboy on 2011-10-14
I installed Ubuntu 11.10 and now my wireless card does not have a firmware.

I tried looking for "additional drivers", but nothing comes up.

I typed in iwconfig and it tells me the following:

lo - no wireless extension.

eth0- no wireless extension.

wlan0 IEEE 802.11g         ESSID: off

Can I get some step by step help such as:

1. DO this.

2. Do this.

3. Do this and you should be good.?

Thanks,
Armaniboy:KS

---

### Post by Armaniboy on 2011-10-14
Also, it cannot recognize the firmware for broadcom corporation bcm 4318 (air force one 54g) 802.11g

---

### Post by mikewhatever on 2011-10-14
Can you post the output of **lspci** from a terminal window. Different wireless cards require different firmware, and since we don't know which model is yours, helping you is not going to be easy.

---

### Post by wcorey on 2011-10-14
I don't want to or mean to hijack this issue but I have the same exact problem. One thing I can add, is the Ubuntu 11.04 release I replaced with 11.10 worked fine and found a restricted hardware driver for this machine. In my case it is a Dell XPS M140

lspci -

Boradcom Corporation BCM4318 [Airforce One 54g]802.11g Wireless LAN controller (rev 2)

This is a serious regression, I vaguely recall years back Ubuntu had this issue with this same laptop but it's be a couple of years  * 2/year where it worked fine.

NOTE: I happened across the following which worked for me...

# **sudo apt-get install firmware-b43-installer**

It would be nice if someone could explain why Canonical could not ship with the restricted drivers. I always thought that was what separated them from Fedora.

---

### Post by Armaniboy on 2011-10-15
Thank you! That worked. I had to literally bring my computer to the wall jack with the ethernet cord. Hook up to the internet that way, and then run that command in the terminal :)

---

### Post by dave0109 on 2011-10-16
For the sake of the archives - I'm using a Dell Latitude D620 with the Broadcom 4311 adapter.  Using Xubuntu 11.10, the STA driver offered by default does not work and the firmware-b43-installer package was needed instead.

---

### Post by wcorey on 2011-10-26
That's great. For completeness you should mark this as solved. Also, somewhere, in researching this for myself (have have a Dell XPS M140) someone (don't know how authoritative) that Canonical can no longer offer the restricted drives for copyright reason. Had I already mentioned that?

---

