---
title: "DNS without changing all the /etc/hosts files"
date: 2005-12-07
forum: General Help
---

### Post by siennalizard on 2005-12-07
Hello everyone.

I thought I would save myself changing all the /etc/hosts and windows hosts files on my home network to keep all my name lookups up-to-date, so I installed dnsmasq on a box that's always on, and made sure that the /etc/hosts file was correct on that box.

On the other machines, I cleared all the other computer references from the /etc/hosts files.

I then tried to make sure that this dns server was being taken into account when doing name lookups by following [https://wiki.ubuntu.com/StaticDnsWithDhcp]("https://wiki.ubuntu.com/StaticDnsWithDhcp").

The result is that on the box I'm testing, the resolv.conf file looks like this:
```

search fourwinds
nameserver 192.168.2.4
nameserver 192.168.2.1

```

The first named server is ny new one. The second is my Belkin router. I'd like to keep a DNS service when the in-house server is down, even if I can't get my machines.

The problem is that I cannot seem to ping the hosts in the dnsmasq server's /etc/hosts file. I just get the "Unknown" error. All dns requests for internet domains go through fine: my router must be handling them.

Any ideas? I'd be very grateful.
J.

---

### Post by mgor on 2005-12-07
if you ask your dns server directly
```
dig <host> @192.168.2.4
```
does it give you a vaild answer?

i haven't tried dnsmasq myself, i use bind or djbdns.
i've got a guide on howto setup djbdns for a local domain, thought it's in
swedish. let me know if you want to try it out and i'll translate it for you.

---

### Post by siennalizard on 2005-12-07
Problem solved. I was thinking about the way I normally refer to machines on my network: without a domain: ixon, rather than ixon.fourwinds. In the /etc/dnsmasq.conf file, be sure to give a domain name and turn on the expand feature. That will let you "ping ixon", for example, as you were used to:

```

james@garnet:/home/james# ping ixon
PING ixon.fourwinds (192.168.2.2) 56(84) bytes of data.
64 bytes from ixon.fourwinds (192.168.2.2): icmp_seq=1 ttl=128 time=3.32 ms
64 bytes from ixon.fourwinds (192.168.2.2): icmp_seq=3 ttl=128 time=1.26 ms
64 bytes from ixon.fourwinds (192.168.2.2): icmp_seq=4 ttl=128 time=1.04 ms
64 bytes from ixon.fourwinds (192.168.2.2): icmp_seq=5 ttl=128 time=16.2 ms

--- ixon.fourwinds ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4002ms
rtt min/avg/max/mdev = 1.048/5.476/16.268/6.294 ms

```


Let me know if you need this explaining better: it's been a long day, and what I wrote above might not make much sense!

Cheers,
J.

P.S. Thanks for your help, mgor. Hadn't thought to try a pure dig, but I did remove my router from /etc/resolv.conf and was still able to hit internet domains, so I knew the server was working.

---

