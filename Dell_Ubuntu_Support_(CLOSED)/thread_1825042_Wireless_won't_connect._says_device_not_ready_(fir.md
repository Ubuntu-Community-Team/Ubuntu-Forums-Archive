---
title: "Wireless won't connect. says device not ready (firmware missing"
date: 2011-08-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stemgeek on 2011-08-14
Hi, i have a dell inspiron 1520 with a BCM4311 802.11b/g WLAN.
I have tried some of the other forums to solve my wireless problem. But none are working or are confusing me. i have no pervious programming experience. I know to use terminal and everything, but nothing besides that. Please help.

---

### Post by MARP1961 on 2011-08-14
If you have already enabled the Broadcom STA driver then try removing it in 'Additional Drivers'. Then open Synaptic Package Manager and search for and install the 'firmware b43 installer'. Reboot and left click the Network Manager to see if your router is listed.If it is then click on it to see if it connects. If it doesn't then select Edit Connections and make sure it is set for ALL USERS.

---

### Post by stemgeek on 2011-10-19
When i tried that, i had nothing installed in additional drivers and couldn't find firmware b43 installer

---

### Post by collisionystm on 2011-10-19
Open software center

Firmware-b43 

Search. Hit button for view technical results

---

