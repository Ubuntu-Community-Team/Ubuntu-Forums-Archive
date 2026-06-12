---
title: "wireless"
date: 2010-09-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by appletech67 on 2010-09-15
hey guys ive got a 2 year old dell inspiron 1545 (i think) at home and downloaded ubuntu cuz well its the closest thing i can get to to the mac OS on a PC but i can not for the life of me get on the internet i have a wireless network at home and ive tried so many different ways to connect using vpn, wireless and nothing works help me please

your friendly apple advisor

---

### Post by TwelveGauge on 2010-09-15
so you can see the network?
or can you not even get your computer to recognize it?

for VPN help:
[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

---

### Post by Joe of loath on 2010-09-15
You need to install the drivers for the built in wireless. They're in the repository, so plug in a network cable and open up synaptic. Search for 'Broadcom', and install 'bcmwl-kernel-source', 'b43-fwcutter' and 'bcmwl-modaliases'. Reboot, and it should work.

I have the same laptop, and wireless works perfectly once these are installed.

---

### Post by TwelveGauge on 2010-09-15
> **Joe of loath said:**
> You need to install the drivers for the built in wireless. They're in the repository, so plug in a network cable and open up synaptic. Search for 'Broadcom', and install 'bcmwl-kernel-source', 'b43-fwcutter' and 'bcmwl-modaliases'. Reboot, and it should work.

I have the same laptop, and wireless works perfectly once these are installed.

>_>;;; i should have thought of that, but now I know :P for future reference :P

---

