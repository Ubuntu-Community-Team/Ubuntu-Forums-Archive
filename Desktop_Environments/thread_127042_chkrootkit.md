---
title: "chkrootkit"
date: 2006-02-08
forum: Desktop Environments
---

### Post by gammagoat on 2006-02-08
This turned up when I ran chkrootkit. Can someone tell me what this means. 

eth0: PACKET SNIFFER(/sbin/dhclient3[6533])

---

### Post by User_Program on 2006-02-08
Most likely its just a false positive.  Chkrootkit is picking up your dhcp and it thinks its a rootkit.   This is normal I wouldnt be to worried.   Are you running DHCP ?  If so thats what it is.

---

