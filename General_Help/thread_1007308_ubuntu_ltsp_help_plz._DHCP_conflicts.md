---
title: "ubuntu ltsp help plz. DHCP conflicts"
date: 2008-12-10
forum: General Help
---

### Post by wtfacoconut on 2008-12-10
allrighty now! 
Heres the thing, I got an ubuntu ltsp up and running (followed the 2 nic setup) in an AD environment. Unfortunately LTSP's DHCP server seems to be conflicting with the AD's DHCP server which then results in other client computers (running windows and are joined to the domain), not being able to login to their domain accounts. I've been told to turn off the DHCP server on the windows AD server, but many other people tell me that there is another way around this issue if I want both servers running.

Ultimatly here's what I want to do in the end.
1. NOT have the servers conflict with each other.
2. and have things setup so that clients who boot from LTSP are able to login to their AD accounts. 

I plan on using likewise to take care of the linux-lts users being able to login to their AD accounts. So far I've been told that once I take care of this DHCP conflict issue, I can install and configure likewise on the LTSP Server, rebuild the client image, and that should take care of that. At this point I really need some help with this conflict issue that LTSP is causing. Thanks in advance.

---

