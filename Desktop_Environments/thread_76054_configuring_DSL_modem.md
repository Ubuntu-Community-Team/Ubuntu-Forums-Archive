---
title: "configuring DSL modem"
date: 2005-10-14
forum: Desktop Environments
---

### Post by greengrass on 2005-10-14
Does ubuntu detect  ethernet cards automatically?   If not how do you configure it to get online with a DSL modem?

---

### Post by Ampersand on 2005-10-14
Does 'sudo pppoeconf' work?

---

### Post by Stormy Eyes on 2005-10-14
If the Linux kernel has a compatible driver for your NIC, then Ubuntu will auto-detect it and try to configure it with DHCP. You should be able to hook your DSL to a router if the modem's got ethernet and USB ports. What sort of network card do you have? Can you post the brand and model number?

---

### Post by greengrass on 2005-10-14
Im using a linksys  10/100  LAN card  When I originally installed ubuntu I remember I chose install network later.  So I dont know if DHCS is working

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=greengrass]Im using a linksys  10/100  LAN card  When I originally installed ubuntu I remember I chose install network later.  So I dont know if DHCS is working[/QUOTE]

OK. Linksys gear is pretty widespread, so chances are that Ubuntu will support it. I'd like you to go to "System - > Administration -> Network", type in your password, and have a look at everything marked **eth0**. If there's nothing there marked **eth0**, then Ubuntu hasn't found your card.

I always configure my networking when I install, so I'm not sure how to go about "installing later" off the top of my head.

---

### Post by greengrass on 2005-10-14
The window says the interface etho is not configured

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=greengrass]The window says the interface eth0 is not configured[/QUOTE]

OK. The Ubuntu Guide hasn't been updated for Breezy yet, but it should still be helpful to you. I suggest reading the [Configure Network Connections](http://ubuntuguide.org/#configurenetworkconnections) section first. If you've got the DSL modem hooked directly to your machine and not to a router, try [Configure Broadband Connections](http://ubuntuguide.org/#configurebroadbandconnections).

---

