---
title: "Can connect to the network, but Firefox won't browse"
date: 2006-09-19
forum: Desktop Environments
---

### Post by alcyst on 2006-09-19
I installed Ubuntu on a Dell Optiplex. Seemed to go fine. The PC can now browse the (company) windows network. The Updates Notification has appeared to tell me that there are 27 (24?) updates available. "Network Tools" will ping and whois internal and external addresses.

But Firefox will not browse.
I get the standard "Server not found  Firefox can't find....". 

We do have a firewall and proxy server box (oh and everything works fine on WinXP).

Thoughts, suggestions, rants, anything please.

---

### Post by kidders on 2006-09-19
I suppose it's worth checking whether you told Firefox that you have a web proxy.

Now that the "Have you plugged it in?" question is out of the way, are you able to access internal websites?

---

### Post by alcyst on 2006-09-20
Some update since the original post. I havn't given the machine details about a web proxy. I am now getting intermittent connection, sometimes I log on and get to browse, & sometimes I logon & don't. I am getting an IP address using DHCP, I have been able to print to a network printer. I have been able to install the standard updates.

---

### Post by madbawa on 2006-09-20
Go to about:config and set network.dns.disableIPv6 to "true".

---

### Post by bigken on 2006-09-20
> **madbawa said:**
> Go to about:config and set network.dns.disableIPv6 to "true".

in the firefox browser type about:config the in the filter type ipv6 double click to change value

---

