---
title: "Ethernet card not listed in lspci - Dell Inspiron Mini 10"
date: 2012-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bennis on 2012-02-27
Not sure what other version information to give.
I have 11.04 on this machine and have the wireless working fine. The ethernet card isn't listed in lspci and the wireless is listed as eth1 in ifconfig. Obviously the ethernet card isn't showing up in ifconfig either... Same situation when i boot from an install medium for 11.04. I'll be downloading 11.10 to see if there's any more luck tonight, but downloading an ISO is a full night as i'm on satellite internet.
Any theories? Buttons to push? Thingies to fanagle?
Thanks for any help.

---

### Post by wildmanne39 on 2012-02-28
Hi, please post the output of:
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by bennis on 2012-02-28
The only thing that comes up is the wireless controller. As i have to type it across, i'm going to type the important bits.

Network controller [0280] broadcom bcm4312 14e4:4315
subsystem dell wireless 1397 minicard 1028:000c
kernel driver wl

---

### Post by wildmanne39 on 2012-02-28
Hi, check in your bios and see if your lan is turned off. 

Does your wireless work? eth1 is correct for the driver your wireless is using.
thanks

---

### Post by bennis on 2012-02-28
Of course!! I turned it off to save power. Thank you xD

---

### Post by wildmanne39 on 2012-02-28
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

