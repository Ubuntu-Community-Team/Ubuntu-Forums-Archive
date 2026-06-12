---
title: "/etc/network/interfaces ip-alias problem"
date: 2006-01-18
forum: General Help
---

### Post by jumpslu7 on 2006-01-18
Hi.  I've configured my eth0 card to have an ip-alias - eth0:0

I've specified in /etc/network/interfaces the config for eth0:0 (pasted below).
When I reboot, the eth0 comes up fine, but eth0:0 does not.  This in turn causes my http service to fail (frustrating!)

To resolve, I simply do a sudo ifconfig eth0:0 192.168.0.45 up

Is there something missing in the interface file below that might cause the ip alias not to be assigned at boot time?

many thanks
j

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.0.50
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.50
        dns-search gibberish.net

iface eth0:0 inet static
        address 192.168.0.45
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

auto eth0 eth0:0

---

