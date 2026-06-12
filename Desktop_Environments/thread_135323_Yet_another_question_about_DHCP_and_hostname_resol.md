---
title: "Yet another question about DHCP and hostname resolution"
date: 2006-02-23
forum: Desktop Environments
---

### Post by dpm on 2006-02-23
Hi everyone,

Although I've seen this question posted here before, I could not find a clear answer to the problem after looking at the related threads in the forum.

My problem is the following:

I've got a computer connected to a router with integrated firewall (AVM Fritz!Box Fon WLAN 7050) from which it obtains an IP address assigned via DHCP from the router. So far, everything works as expected, I can connect to the internet and also to the local network.

However, I would like to use a hostname by which other clients on the local network can access my computer, instead of using the IP address  (yes, I know, I could use a static IP address, that's not the point). I know it is maybe a bad example, but with that I mean the way it is done in windows, where for example I can ping my computer by hostname instead of IP address.

Other people seem to have had success by modyfying the configuration file of the dhcp3 client that comes per default with ubuntu (uncommenting the line send host-name "myhostname"; in /etc/dhcp3/dhclient.conf ), but that does not seem to work for me.

Any ideas? Can this be done with the dhcp3 client? If possible, I'd like to stick to the default, but if someone confirms that that cannot be done with this client, I guess I'll just have to start having a look at other dhcp clients.

Thanks in advance.

---

### Post by nickmcg on 2006-02-24
I've got similar problems:

network mixture win & linux. Netgear router.

Using win, I can access all other machines on the lan except those running ubuntu by name.
The ubuntu machines cannot access any of the other machines on the lan by name, but they can by ip address.

All machines can access the internet via netgear router.

Note: ubuntu machines *CAN* browse the win network and see the win computers, but cannot ping them by name!

Nick

---

### Post by dcstar on 2006-02-26
[QUOTE=nickmcg]
.....
Note: ubuntu machines *CAN* browse the win network and see the win computers, but cannot ping them by name!

Nick[/QUOTE]
Check this out:

[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

---

### Post by nickmcg on 2006-02-27
Many thanks for that - it works.

I'd tried many searches, but hadn't made the netbios link.

Thanks again

Nick

---

