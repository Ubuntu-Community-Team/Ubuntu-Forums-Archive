---
title: "ubuntu 64 bit dell inspiron 1440 wifi and lan problem"
date: 2010-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jamesbon on 2010-08-31
I installed Ubuntu 10.04 64 bit on Dell Inspiron neither my LAN settings worked nor the wifi card was detected even.
Before installation I had used the LV CD and every thing had worked.
For wifi in LIVE CD I used the Broad Com STA option and Wifi had also worked.
So please tell me now when I installed every thing stopped working.
Why is this happening and is there a way to get rid of this and make every thing working?
lspci 

```

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

---

### Post by ziemowitzima on 2010-09-01
I have similar problem with dell studio 1749 but only with wifi signal, which is very weak.
I have new updated driver:
Broadcom STA.
lspci command shows:
BCM4312.

---

### Post by jamesbon on 2010-09-03
I really do not know I rebooted the computer and I was able to  use every thing.

---

