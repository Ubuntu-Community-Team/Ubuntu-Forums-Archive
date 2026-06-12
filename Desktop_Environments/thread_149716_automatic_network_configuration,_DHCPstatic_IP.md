---
title: "automatic network configuration, DHCP/static IP?"
date: 2006-03-24
forum: Desktop Environments
---

### Post by Heliix on 2006-03-24
I wonder how to "teach" my laptop to detect the network automatically. I mean how to write a script that would run at the boot..
at school, the laptop is connected to a linux server and receives the IP address via DHCP. at work, it has static IP address (and is part of windows network)
now, I have either to run dhclient or to configure the network manually which is just ](*,) . my idea is to have some script that would try to get the IP address from DHCP server, and if there wasn´t any, it would set the static IP, gateway, DNS etc., and start samba as well.
thanks,
Heliix

(and yes, you´re right: I have no experiences in programming)

---

### Post by adamonduty on 2006-03-28
You can actually tell dhclient in its config file to configure a static IP if no DHCP lease is offered. Check /etc/dhcp3/dhclient.conf .

It sounds like you might also be interested in using network-manager. Search for it in Synaptic. It will automatically change between networks as it feels best, and will make the internet connection process very slick.

---

