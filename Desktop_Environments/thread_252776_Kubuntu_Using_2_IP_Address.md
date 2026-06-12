---
title: "Kubuntu Using 2 IP Address"
date: 2006-09-07
forum: Desktop Environments
---

### Post by jonnymccullagh on 2006-09-07
I am using Kubuntu Breezy at work but the Network Admin recently noticed that I am using 2 IP addresses on the network (both showing up with my hostname) i.e.
192.168.1.1    JonnyUbuntu Live
192.168.1.187  JonnyUbuntu Live

When I unplug my machine from the network both IP addresses appear dead, and when I plug back in they appear live. I also shut down VMServer in case that was the problem but I am still getting this issue.
Also in the network scan my machine did not show a MAC address whereas all the Windows machines do. I don't know if that is connected.
What confuses me is that my machine is using 2 IP addresses with only 1 network device. 
I manually assign IP addresses as we do not really use DHCP (although there is a DHCP service running on the network so I assume something is acquiring the *.1 address by DHCP).
Can anyone give me any insight into what is up here? I would like to release the *.1 address as it is needed.
Thanks,
jonny

---

### Post by jonnymccullagh on 2006-09-08
bump :(

---

### Post by alecjw on 2006-09-08
Usually, there is a limited DCHP range (eg. on my network it's 192.;168.2.1-100). When giving computers manual IPs, make them outside the DCHP range eg 192.168.2.101.

---

### Post by jonnymccullagh on 2006-09-11
Thanks for replying. During install I manually set the address to *.187 but my Kubuntu installation seems to be using 2 IP addresses at the same time. I don't know how this is possible? and it is getting me into trouble with the network admin.

---

