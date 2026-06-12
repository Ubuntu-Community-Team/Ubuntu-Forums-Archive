---
title: "DNS-resolv doesnt work anymore."
date: 2005-10-07
forum: Desktop Environments
---

### Post by mariux on 2005-10-07
Hi, i have my ubuntu-pc connected directly to another pc that shares its internet-connection with it. Its always worked great but now suddenly my ubuntu-pc doesnt want to resolv dns anymore.

My /etc/network/interfaces looks something like this (the most important parts)
iface eth0 inet static
address 192.168.0.7
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.2 [which is the ip of the connection sharing pc]
dns-nameservers 195.134.40.14

and my /etc/resolv.conf looks like this:
195.134.40.14

On the connection sharing pc everything works and on the client pinging 192.168.0.2 and pinging any internet ip works, f.eks. 195.134.40.14

So the pc DOES have connection with the dns-server but doesnt seem to use it.
What could be wrong?

---

### Post by KingBahamut on 2005-10-07
assuming that 195.135.40.14 is your nameserver 

just make it 

namserver 195.134.40.14 

or 

if you need a decent nameserver set, here is what my resolv.conf looks like 


nameserver 64.94.1.1
nameserver 64.94.1.33


those are Internaps DNS servers, got a friend over there. They have very few if any DNS class restrictions.

---

### Post by mariux on 2005-10-07
Thanks

---

