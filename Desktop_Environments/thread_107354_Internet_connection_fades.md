---
title: "Internet connection fades"
date: 2005-12-22
forum: Desktop Environments
---

### Post by claytonj001 on 2005-12-22
Hi! All..

After a period of time my Internet connectivity becomes slow and sometimes fails. It almost looks like a DNS failure as I can ping the ISP's gateway. When I boot into Win2K everything is good. I use a SMC router on cable. My NIC is a VIA Rhine II Fast Ethernet. I use static IP's on my internal network. Ubuntu is upgraded and up to date. I have configured the name servers but question if using local domain as the domain is a problem for Ubuntu. The problem is most likely me but if you can help me I would appreciate it.

Regards,

Jeff

---

### Post by dcstar on 2005-12-23
[QUOTE=claytonj001]Hi! All..

After a period of time my Internet connectivity becomes slow and sometimes fails. It almost looks like a DNS failure as I can ping the ISP's gateway. When I boot into Win2K everything is good. I use a SMC router on cable. My NIC is a VIA Rhine II Fast Ethernet. I use static IP's on my internal network. Ubuntu is upgraded and up to date. I have configured the name servers but question if using local domain as the domain is a problem for Ubuntu. The problem is most likely me but if you can help me I would appreciate it.

Regards,

Jeff[/QUOTE]
When it happens, open a terminal and post the results of the following commands here for people to look at:

ifconfig
route -rn

Other than that, it could be a driver/power management issue which may be altering your ethernet connection after a time.

BTW, this problem may be better placed in the "Networking" section:

[http://ubuntuforums.org/forumdisplay.php?f=101](http://ubuntuforums.org/forumdisplay.php?f=101)

---

