---
title: "Bind - DNS server"
date: 2009-04-29
forum: General Help
---

### Post by Firete on 2009-04-29
Dear,

I have a DNS server (bind 9.4.1) set up on my Linux machine (Ubuntu) and I have found a really extrange behaviour.

I have defined a domain name, both with IPv4 and IPv6 entries, as follows:
[www.fax.com]("http://www.fax.com") IN AAAA 2001:32::1
[www.fax.xom]("http://www.fax.xom") IN A       1.5.6.7

When  I make a request: [www.fax.com]("http://www.fax.com") and capture the traffic (snoop), it always tries to make a nslooup for IPv6 and then, although it has succeed, it does the same for IPv4, and of course, it succees again.

If the domain name has only IPv4, it behaves exactly the same as explaine before.

Any solution?
Than you for your help

---

