---
title: "DHCP server and VMWare"
date: 2006-07-25
forum: Desktop Environments
---

### Post by alkaboy on 2006-07-25
My desktop has 2 network interfaces, eth0 and wlan0. I currently connect to my home network via wlan0. I'm running Windows XP inside VMWare and currently have the networking running off of NAT. I'd like to be able to access the home network (specifically the tivo box that is connected to the router) from within VMWare. 

Unfortunately, I cannot bridge the connection to wlan0 in VMware, as it freezes up the computer. I read something about how wireless standards only allow traffic from the one MAC address that is hard-connected to the wireless network, thus preventing VMWare from creating a temp MAC to connect to the router on top of wlan0. I also read about a possible solution for using a DHCP server and iptables to set it up such that eth0 would be on the same network as wlan0, without having eth0 physically plugged in. This would then allow me to bridge VMware to eth0 and access the home network within VMware. Can anyone provide an explanation on how to setup DHCP server and iptables in order to do this? Thanks!

---

