---
title: "Static IP - no WAN, only LAN"
date: 2005-12-21
forum: General Help
---

### Post by rhy7s on 2005-12-21
This seems really odd, if I configure this Kubuntu machine to use a static IP address, I lose all internet connectivity. Switch back to DHCP and it's all go again. ifconfig info for eth0 when using a static IP is identical to dhcp except for the IP. Windows machines can use static addresses on the network without any problem. Router is a Linksys AG241 which I've rebooted. Can't ping internet hosts via dns or hostnames.

To reiterate; netmask, broadcast address, gateway & nameservers are all the same. Everything within the LAN works fine with either configuration.

Any ideas?

---

### Post by scokar on 2005-12-22
can you ping the router?

is your default gateway correct?  How are you setting it?  via the KDE applet?  In my experience, the default gateway was NOT being set and I had to manually edit the file:

/etc/network/interfaces

and add a gateway entry

---

### Post by rhy7s on 2005-12-22
[QUOTE=scokar]via the KDE applet?[/QUOTE]
Yeah, I can ping the router and access everything else in the LAN. I am changing settings in the applet though, so I'll manually add the gateway as you suggest tomorrow.

---

### Post by rdsingh on 2006-08-01
Your router works as a DNS forwarder to the DNS of your ISP. When you get your IP dynamically from the router, DNS information is set by the router. When you assign static IP, it's your responsibility to set the DNS. 

Find out your ISP's DNS address and set it in your Kubuntu machine. That should fix it.

---

