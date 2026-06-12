---
title: "Linux bridge networking?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by xela321 on 2006-09-19
Here's my dilemna: at my school, when a computer with a particular MAC address requests and IP via DHCP, the DHCP server assigns the machine an IP and updates an entry in the DNS server to point to that IP.  The reason is that each building on campus is on a different subnet, but the effect is that your hostname follows you.  

So, I want to have multiple hostnames resolve to my computer (so that I can do virtual hosting).  I can't set the IP manually because the campus firewall won't allow "unofficial" IP addresses.  (ifconfig eth0:0 IP aliasing won't work).  I don't want to put multiple NICs in my computer (it's a small-form factor PC).  I know it's possible to bridge together dummy devices, but I can't find a good tutorial.  I tried [this one]("http://www.google.com/search?q=cache:y3flhX5-el4J:fnord.no/sysadmin/virtual-servers/linux-vserver-and-dhcp/+linux+network+bridge+dummy0&hl=en&gl=us&ct=clnk&cd=1&lr=lang_en"), but for some reason it didn't work.

Can anyone help me?  Remember, each dummy device needs to broadcast a DHCP request from a **unique** MAC address.  From there, I'm assuming Apache is smart enough to determine which hostname a request is coming in from.

Thanks to anyone who even read this far!!!

---

