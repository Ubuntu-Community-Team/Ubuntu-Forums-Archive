---
title: "Static IP with Network Manager?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by Cable on 2006-09-08
Is it possible to have a static IP while using Network Manager?  If so, how?

---

### Post by galileon on 2006-09-08
System>Administration>Networking


Click on Ethernet Connection,

click on Properties,

CLick on DHCP and change to Static IP address...enter ip,mask,gateway...

---

### Post by wieman01 on 2006-09-08
No, NetworkManager has a number of known constraints:

1. No hidden ESSIDs.
2. No static IPs (DHCP only).
3. Can't connect to unsecured networks.

---

### Post by wieman01 on 2006-09-08
If you need static IPs, try these threads:

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")
[http://www.ubuntuforums.org/showthread.php?t=225290&page=11&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=225290&page=11&highlight=wpa2+rsn")

---

