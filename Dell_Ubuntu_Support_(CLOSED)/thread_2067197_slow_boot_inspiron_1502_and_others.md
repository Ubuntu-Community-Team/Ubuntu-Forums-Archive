---
title: "slow boot inspiron 1502 and others"
date: 2012-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DrScum on 2012-10-06
I operate a Inspiron 1501, a Inspiron 6400 and a Vostro 1520 on lubuntu 12.04, ubuntu 10.04 and on ubuntu 12.04 LTS respectively. All show the following phenomenon:
after power on a flashing cursor in the upper left hand corner on a black screen for 1-2min after that grub seems to kick in (with GRUB_HIDDEN_TIMEOUT=10 in the grub.cfg one can see the countdown from 10 to 0 AFTER the two min waiting time) at this point boot proceeds with expected speed.

What happens during those 1-2min? How could I diagnose this?

Help is greatly appreciated. From the forum activities I conclude that I am not the only one dealing with this problem.

---

### Post by 2F4U on 2012-10-06
Did you look into the system log file /var/log/syslog It should give you information what the system is doing during that time. Are you using wireless LAN or are there external devices attached, e.g. via usb?

---

### Post by DrScum on 2012-10-06
Thanks for the syslog hint.
I looked in the syslog and found the first entry of the last boot at
18:38:52  the last entry of the sequence is time stamped with:
18:39:32
Doesn't that mean that the boot sequence should have taken like 40s?
I would be more than happy with that. But in real time it takes over 2min!

I do use WLAN but no usb devices attached. I tried to boot without mouse attached and without LAN cable attached, with WLAN switched off but the flashing cursor/blank screen doesn't disappear.

Would't the conclusion be that the culprit is situated before the Ubuntu kernel starts up? That would put grub on the spot, wouldn't it?. I checked that too in the grub.cfg (see original post). The flashing cursor/blank screen sequence happens BEFORE grub counts down from 10 to 0.

What would be the culprit then and how to diagnose it is my question.

---

