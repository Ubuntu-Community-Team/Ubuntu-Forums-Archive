---
title: "Dell Vostro 1510 Wifi"
date: 2010-01-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Maxamuz on 2010-01-19
I have a dell vostro 1510 that I installed Ubuntu (9.04) on and am having trouble with getting my wifi to co-operate.  

Any tips?:popcorn:

Broadcom STA Wireless driver FYI

---

### Post by jml on 2010-01-19
Broadcom wireless cards are the bane of any Linux user's existance.  They will not release their hardware or driver specs to the open source community.  A quick search of this forum and the internet via Google yields a lot of postings citing problems with the Vostro/Broadcom combination.  Not a lot of solutions that seem to universally work are offered.  All is not lost, however.  One option is to try to utilize the Windows driver for the card, (which is usually on the restore CD or driver CD supplied with the laptop) with an application called ndiswrapper.  Alternatively,since most of the posts were discussing earlier versions of Ubuntu, you can download a copy of Ubuntu 9.10, run it as a live cd and see if the newer version works with the card.  Good luck.

Joe

---

### Post by mikewhatever on 2010-01-19
> **Maxamuz said:**
> I have a dell vostro 1510 that I installed Ubuntu (9.04) on and am having trouble with getting my wifi to co-operate.  

Any tips?:popcorn:

Broadcom STA Wireless driver FYI

Your help request is too vague. Can you elaborate on what's the problem exactly, and also, provide your wireless card's model. These days, more often then not, all you have to do is go to System->Admin->Hardware Drivers and install the driver by point and clicking.

---

### Post by scheck32 on 2010-02-09
I have a Vostro 1510 for work and have 9.10 on it. All I needed to do was go to System -> Administration -> Hardware Drivers and they were listed right in there for the broadcom wireless card. One thing to point out though is that I needed to be connected to the internet by ethernet before I was given the option for those drivers.

---

