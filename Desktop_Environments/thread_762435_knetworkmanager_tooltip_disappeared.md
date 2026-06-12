---
title: "knetworkmanager tooltip disappeared"
date: 2008-04-22
forum: Desktop Environments
---

### Post by christian.t on 2008-04-22
Hi,
im am running kubuntu gutsy. Some days ago i wanted to connect to a wireless lan, where no dhcp was running - without success. The manual configuration failed, an since then the tooltip that showed up when moving the mouse cursor over the knetworkmanager symbol in the taskbar is not showing up anymore (that tooltip showed the availabe wlans). How can i get this tooltip back?
Regards, Christian

---

### Post by slatemine on 2008-04-22
when there is a manual configuration that overides knetworkmanager, which sits with a different icon to indicate it is deferring to the manual config. As I remember, (check in the documentation), the manual configuration is stored in a file somewhere in /etc/networks. If you remove the manual configuration from this file, knetworkmanager springs back to life :-)

Hope that that helps!

---

### Post by christian.t on 2008-04-24
unfortunately clearing /etc/network/interfaces does not help. the doku [http://en.opensuse.org/Projects/KNetworkManager](http://en.opensuse.org/Projects/KNetworkManager) does not say anything about config files.

---

### Post by warp99 on 2008-04-24
> **christian.t said:**
> unfortunately clearing /etc/network/interfaces does not help. the doku [http://en.opensuse.org/Projects/KNetworkManager](http://en.opensuse.org/Projects/KNetworkManager) does not say anything about config files.

Did you remove the ~/.kde/share/config/knetworkmanagerrc file? Close knetworkmanager, delete the file, then starting knetworkmanager again will set the manager back to the default settings.

---

