---
title: "using hostfile of Debian router on local network"
date: 2019-03-01
forum: Debian
---

### Post by bartgrefte on 2019-03-01
Until a couple of months ago I was using router-distro IPFire which had a handy webpage where I could enter local IP-addresses and names (like devicehostname.mydomain.com) after which devicehostname.mydomain.com could be used on any client to access the associated local IP-address.

Now I'm using Debian as a router and I'm trying to accomplish the same thing. I thought it was as simple as editing /etc/hosts, but it seems it is not.

If I run nslookup from a Windows client, like for example with localhost, I get this expected result:
```
nslookup localhost 192.168.1.1
Server:  UnKnown
Address:  192.168.1.1

Name:    localhost
Addresses:  ::1
          127.0.0.1
```
the same with my routers hostname:
```
nslookup hellmouth 192.168.1.1
Server:  UnKnown
Address:  192.168.1.1

Name:    hellmouth
Address:  127.0.1.1
```

However, with devicename.mydomainname.com I keep getting "UnKnown can't find devicename.mydomainname.com: Query refused"

Pinging devicename.mydomainname.com on the Debian router itself works, so the change in the hostfile has been picked up, but apparently the client isn't getting access to that change in the hostfile. Not with nslookup, ping or tracert.

Since the router's hostname and localhost do work, I'm a bit :confused:

---

### Post by TheFu on 2019-03-01
This post should probably be in the Debian sub-forum.

IPFire probably was running a DNS.
If you want debian to run a DNS, then you'll need to set it up.  Perhaps this is trivial now, but I'm positive that setting up 'bind' is non-trivial. Bind is the most popular DNS, but with great power, comes more complexity.

[https://superuser.com/questions/407236/simplest-way-to-setup-a-internal-dns-server-to-serve-very-simple-names](https://superuser.com/questions/407236/simplest-way-to-setup-a-internal-dns-server-to-serve-very-simple-names) has an answer that uses DNSmasq. I've used it inside a consumer router and the config files are ugly. If you use DHCP, then you'll probably want to use DHCP reservations, which DNSmasq can do as well.  

Just don't have 2 DHCP servers on the same subnet concurrently.  When that happens, the faster answer is what counts.

---

### Post by wildmanne39 on 2019-03-01
*Thread moved to **Debian a more appropriate sub-forum**.*

---

### Post by bartgrefte on 2019-03-02
> **TheFu said:**
> This post should probably be in the Debian sub-forum.

Woops, didn't see that one, I thought since Ubuntu is based of Debian the networking forum was the right place.

> **TheFu said:**
> IPFire probably was running a DNS.

After having a look at (the end of) [https://github.com/ipfire/ipfire-2.x/blob/master/html/cgi-bin/hosts.cgi](https://github.com/ipfire/ipfire-2.x/blob/master/html/cgi-bin/hosts.cgi) , it looks like IPFire is using Unbound for that. 

> **TheFu said:**
> If you want debian to run a DNS, then you'll need to set it up.  Perhaps this is trivial now, but I'm positive that setting up 'bind' is non-trivial. Bind is the most popular DNS, but with great power, comes more complexity.It seems I not knowingly already did that, see below.

> **TheFu said:**
> [https://superuser.com/questions/407236/simplest-way-to-setup-a-internal-dns-server-to-serve-very-simple-names](https://superuser.com/questions/407236/simplest-way-to-setup-a-internal-dns-server-to-serve-very-simple-names) has an answer that uses DNSmasq. I've used it inside a consumer router and the config files are ugly. If you use DHCP, then you'll probably want to use DHCP reservations, which DNSmasq can do as well.  DNSmasq is already installed and running since I thought it was required for router-purposes (from what I remember of the many Linux-router howto's I read quite some time ago), never configured it though, thought it was a dependency for something. I'm using isc-dhcp-server for DHCP.

According to your link:
1. Install a DNS Server, dnsmasq for example. -> check
2. Add entries to the host file of that server. -> check
3. Start the dnsmasq daemon -> already running automatically
4. Tell the people to use this server as DNS server in their network configuration. -> 192.168.1.1 is set as primary DNS on this host, 1.1.1.1 as secondary. Still added 192.168.1.1 to the nslookup command though.

So... it should work already? It does when requesting the IP's for hellmouth and localhost, but not for the entry I added under those two in the host file, that entry still only works on Debian itself.

> **TheFu said:**
> Just don't have 2 DHCP servers on the same subnet concurrently.  When that happens, the faster answer is what counts.I have never made the mistake of doing that ;)

> **wildmanne39 said:**
> *Thread moved to **Debian a more appropriate sub-forum**.*
Thanks :)

---

