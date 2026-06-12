---
title: "Latitude e6500 wireless problem"
date: 2010-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jasonlfunk on 2010-05-12
I have a Latitude e6500. I am currently using the Broadcom STA driver as enabled in the Hardware Drivers.

> lspci | grep Network
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Yet, Network Manager doesn't show any wireless interfaces.

> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:bc:cc:d9  
          ...

lo        Link encap:Local Loopback  
          ...

My wireless switch is on. Any ideas?

---

### Post by jasonlfunk on 2010-05-12
Also, the hardware drivers says the STA driver is enabled but not currently in use.

---

