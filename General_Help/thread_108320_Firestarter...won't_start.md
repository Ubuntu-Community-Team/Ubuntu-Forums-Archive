---
title: "Firestarter...won't start?"
date: 2005-12-25
forum: General Help
---

### Post by chimera on 2005-12-25
This is the error message I recieve:

Failed to start the firewall

The device eth0 is not ready

Please check your network device settings and make sure your internet connection is active


I've tried turning off the DHCP, restarting the connection with poff and pon dsl-provider, I even did killall pppd and ran pppoeconf again, and it still won't start the firewall. What should I do?

---

### Post by chimera on 2005-12-26
/bump

---

### Post by kaamos on 2005-12-26
make sure that in firestarter preferences it is set to the correct interface. For example ppp0 instead of eth0

---

### Post by chimera on 2005-12-26
It's set to the correct one - ppp0 is for dialup, eth0 is for ethernet. I don't have dialup, so it's eth0. (according to pppoeconf, which I suppose is correct)

Also, eth0 isn't even listed as an active connection in firestarter, even though the connection is working.

---

