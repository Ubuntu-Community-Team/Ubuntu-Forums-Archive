---
title: "need advice on static IP"
date: 2006-02-26
forum: Desktop Environments
---

### Post by Spano on 2006-02-26
As pointed out in posts in the forum assigning a static IP can speed boot time.
I assign mine in the file /etc/network/interfaces.  Is there a downside to doing this?  Security risks?  And how would you answer this question when configuring the Firestarter firewall with static IP:
> IP address is assigned via DHCP

Any comments appreciated.

---

### Post by slazh on 2006-02-26
I can't really think of a downside. DHCP is verry usefull with large LAN's. Instead of assigning a IP adress to every workstation, the workstation gets one from a DHCP server. 

On a small LAN, I'd go for static IP adress. It's easier to know what IP another workstation has in the LAN if this workstation has a static IP. This might be a security risk, but I can't think of anything risky atm :P.

The answere to the Firestarter question is "no". If you have a static IP adress, you're not getting your IP adress from a DHCP server.

---

