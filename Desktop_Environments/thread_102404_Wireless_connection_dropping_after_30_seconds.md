---
title: "Wireless connection dropping after 30 seconds?"
date: 2005-12-12
forum: Desktop Environments
---

### Post by Auto|MaG on 2005-12-12
Quick question, I hope this is an easy one. After I connect to my AP, everything worked great for about 30 seconds. After that, the connection stop's working(Im not sure exactly what happens, but I cant ping). For example, I can connect to my AP and start pinging an IP. After 30 seconds, it stops pinging, at this point I can do a dhclient, and grab an IP and it immedinatly starts pinging and and getting a reply. Same thing again a minute later, and typing dhclient fixes it agian.

Any ideas?

Heres an iwconfig ath0

ath0      IEEE 802.11g  ESSID:"linksys_SES_28942"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:28:94:97
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:*************   Security mode:restricted
          Power Management:off
          Link Quality=48/94  Signal level=-47 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:26  Invalid misc:26   Missed beacon:47

---

