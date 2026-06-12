---
title: "Virtual Box (not OSE) has no Network"
date: 2009-06-21
forum: General Help
---

### Post by 3Miro on 2009-06-21
Hi,

I need VB for some windows apps and especially for my printer. I also need to share the printer on the network. Before I was able to bridge the Virtual Machine to the host controller network and everything worked fine (before is kubuntu 8.10 and 9.04)

Now when I install VBox there is no network from within the VBox. I cannot even register (the not OSE).

I am using Ubuntu 9.04 64-bit (host) and I have tried:

Ubuntu 8.10 32-bit and Windows XP 32-bit, bridged or NAT interfaces do not work. (The machines work fine and I am able to print and all, just there is no network) Host has working network.

I tried WICD and the standard Gnome Network Manager for the host. I tried both static and dynamic IP (local network 192.168.1.*)

I read many treads, however, I have no vboxnet file in either /etc/vbox/ nor /etc/init.d/ (there is vboxdrv and interfaces, but no vboxnet)

I have reinstalled VirtualBox several times, both directly downloading it from the VB page and adding their repository. The file that I downloaded is virtualbox-2.2_2.2.4-47978_Ubuntu_jaunty_amd64.deb. Repository also doesn't fix the problem.

I am out of ideas, please help :confused:

---

