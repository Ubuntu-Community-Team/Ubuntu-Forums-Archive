---
title: "what is my network #"
date: 2006-09-20
forum: Desktop Environments
---

### Post by charles.g.moore on 2006-09-20
I am trying to configure my /etc/network/interfaces to a static IP on my LAMP server 

my ip is 192.168.1.102
netmask 255.255.255.0
bcast 192.168.1.255
gateway 192.168.1.1
network ??????????

I have my router set up to give out 3 ip's starting at 192.168.1.100

I also am using a dyndns to static up my routers ip

any ideas...

---

### Post by reclusivemonkey on 2006-09-25
> **charles.g.moore said:**
> I am trying to configure my /etc/network/interfaces to a static IP on my LAMP server 

my ip is 192.168.1.102
netmask 255.255.255.0
bcast 192.168.1.255
gateway 192.168.1.1
network ??????????

I have my router set up to give out 3 ip's starting at 192.168.1.100

I also am using a dyndns to static up my routers ip

any ideas...

I don't fully understand what you are asking for help with here. Are you asking how to create an EXTERNAL static IP for your Web Server? If so then you need to speak to your ISP; unless they give you a static IP, then you can't simply create your own. If you are asking how to set up a fixed IP internally, then you should be able to do it on the router; most of them have this function. You should be able to assign a specific IP address to a MAC address.

---

