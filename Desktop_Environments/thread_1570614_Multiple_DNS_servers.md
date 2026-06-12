---
title: "Multiple DNS servers"
date: 2010-09-08
forum: Desktop Environments
---

### Post by treacl on 2010-09-08
Because of latency problems with my ISP's DNS servers, I switched to using OpenDNS by inserting a prepend... line in /etc/dhcp3/dhclient.conf. (I am also using dnsmasq to cache results locally.) But I find that often I get considerable latency with OpenDNS as well. Is there any way, in dhclient.conf or elsewhere, to send each query to two servers simultaneously (one OpenDNS and the other my ISP) and use whichever result comes back fastest?

Thanks,
treacl

---

### Post by kidders on 2010-09-09
Hi there,

The only way to perform two queries in parallel like that is to set up your own DNS server. Pdns, for example, has the ability to perform parallel queries, and is specifically designed with caching in mind. The next best option would be to periodically query your ISP & OpenDNS serially, measure their response times, and rewrite your system's DNS configuration accordingly. That would be quite a bit simpler (ie just a quick script), but not *nearly* as effective.

---

### Post by areeda on 2010-09-09
I've had pretty good luck setting up systems to use google's dns (8.8.8.8 and 8.8.4.4)

---

### Post by treacl on 2010-09-10
Many thanks for the ideas. As a matter of principle, I do not use Google's services unless I absolutely have to. But pdns looks interesting; I will have to see how involved the setup is. --treacl

---

