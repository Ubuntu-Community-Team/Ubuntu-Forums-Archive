---
title: "WiFi won't work properly"
date: 2005-10-16
forum: Desktop Environments
---

### Post by `GooZ´ on 2005-10-16
When I connect to a wireless network (using either wifi radar or the networking panel) it will connect to the network, but it won't load any webpages.
aMSN and many other internet applications can connect to the internet, but it seems only firefox and synaptic won't. I guess it's not a problem with the DNS because it won't say something like 'URL can't be found' but it really gives a timeout while connecting to the server. Could anyone help me please?

---

### Post by bionnaki on 2005-10-16
firewall?

---

### Post by drogoh on 2005-10-16
Can you at least ping your AP?

---

### Post by apu95 on 2005-10-16
as drogoh said, check to see if you can actually ping the AP. if you can, then check your DNS settings to see that they are actually correct. if your router is set to have DHCP disabled, yet you have ubuntu set to get an IP from DHCP, then that can be a problem. is any security set on the router? WEP? WPA? MAC address filtering?

---

### Post by `GooZ´ on 2005-10-17
There is no security set to the router, and I can connect to it and surf the web in windows. I can also access the router via my web browser.

---

### Post by Alphableeder on 2006-03-12
Sounds like Ubuntu doesn't have your DNS information. Connect to your router and copy the DNS servers they have listed. Add them to your network configuration using whatever manager you use.

---

### Post by joseph.brower on 2006-06-25
I've had a similar issue.  I can ping anywhere (yahoo.com and gmail.com) and I get replies.  Firefox doesn't seem to want to load anything though.  It sits for a while and then times out.  Synaptic can download files and everything but web browsing seems to work on the web.  Any ideas?

---

### Post by joseph.brower on 2007-10-07
Diable IPV6.  I don't have the instructions on me, but it fixes the problems.

---

