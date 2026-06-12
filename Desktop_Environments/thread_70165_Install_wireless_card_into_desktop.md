---
title: "Install wireless card into desktop"
date: 2005-09-29
forum: Desktop Environments
---

### Post by Shun on 2005-09-29
Hi all,

   I had a problem about the wireless connection. Currently i using cabling to connect to Internet. And now i want to change to wireless. I bought a D-Link PCI card (Model = DWL-G520+) and i had problem with the setup. 
   Do anyone know how to setup? When i type iwconfig in terminal, it show as below:

wlan0     IEEE 802.11b+/g+  ESSID:"STA646DB1"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Channel:1  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

   Is it the access point should be have some figure? Is there have any website can be reference? Please advice.

Thanks for help!

Regards,
Shun

---

### Post by xristos on 2005-09-29
```
man iwconfig
```

```
man iwlist
```

---

### Post by Shun on 2005-09-29
Hi,

   What is the command use for?

---

