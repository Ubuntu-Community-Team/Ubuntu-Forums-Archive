---
title: "Network Manager not working properly"
date: 2006-06-06
forum: Desktop Environments
---

### Post by phaed on 2006-06-06
I have a Dell Inspiron E1505 laptop with a Dell Wireless 1390 WLAN MiniCard (Broadcome BCM4311 chipset).  I've been able to get this card to work.  At some point, I'm not sure exactly when, although I think it was after an upgrade, I lost the "Wireless Network," "Connect to Other Wireless Network..." and so on in the Network Manager menu.  The wireless card still worked, though.

I followed the instructions to remove mentions of eth0 and wlan0 in /etc/network/preferences, and that brought the Wireless options up on the menu.  It seems to be active, since it lists the wireless network that is available, but I can't connect to it.  It's an open network, so I should be able to.  I can add wlan0 back to /etc/network/preferences, reboot, and access that network, but I can't seem to access it when it is listed in Network Manager.

Also, there is a second network which requires a WEP key, and when I click to access that, it brings up a dialog box asking for the key, which I have and I know works, but it fails to log me onto the network.

Any ideas?

---

