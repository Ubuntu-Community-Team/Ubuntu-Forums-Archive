---
title: "wireless card"
date: 2006-03-06
forum: Desktop Environments
---

### Post by kc8pdr on 2006-03-06
I have a labtop . I would like to know what labtop wireless card works with ubuntu ?

---

### Post by IYY on 2006-03-06
I have a **D-Link DWL G650 revision B**. It uses the atheros chipset, so the ath driver works very well with it. 

If you get it, make sure you get revision B! The other revisions don't use the same chipset and will not work.

---

### Post by rodrigoed on 2006-03-06
How I Kown it is the revision B?Thanks...

---

### Post by Ramses de Norre on 2006-03-06
Run lshw in terminal and search for the lines about your wireless card.

---

### Post by ravening on 2006-03-06
description: Wireless interface
          product: Ralink RT2500 802.11 Cardbus Reference Card
          vendor: RaLink
          physical id: 0
          bus info: pci@07:00.0
          logical name: ra0
          version: 01
          serial: 00:08:a1:77:41:a8
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=rt2500 ip=X.Y.Z.R multicast=yes wireless=RT2500 Wireless
          resources: iomemory:21000000-21001fff irq:11

Although mine is pcmcia, but works really good out of the box ;)

---

### Post by IYY on 2006-03-06
It should say it's revision B somewhere on the back of the box.

---

