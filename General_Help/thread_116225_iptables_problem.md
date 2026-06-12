---
title: "iptables problem"
date: 2006-01-12
forum: General Help
---

### Post by trawler on 2006-01-12
I've recently re-installed my breezy.
Before erasing the previous installation, i copied my /etc/firestarter folder, thinking it might come handy.
so, after re-installing i copied that folder instead of the newly installed firestarter and saw that all my old rules were back, which wasn't bad :)

however, i just installed Azureus and found that it's unable to download.
It can see the no. of seeds and sometimes is kind enough to actually try and connect to few, but the connection is easily dropped.
Every now and then a message popps up to say that there a problem with "the distributed database port".

eventually i removed firestarter completely and re-installed, adding only a rule to open ports 6881-6889.

still same result, except that now, after about 30 minutes of having azureus up i noticed it connected to 1 peer (out of 2000 and something) but still not downloading.

here's my current iptables list:
```
 Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6889
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  dns2.bezeqint.net    anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  dns2.bezeqint.net    anywhere
ACCEPT     tcp  --  dnsdrp.bezeqint.net  anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  dnsdrp.bezeqint.net  anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  bzq-82-81-202-249.cablep.bezeqint.net  dns2.bezeqint.net   tcp dpt:domain
ACCEPT     udp  --  bzq-82-81-202-249.cablep.bezeqint.net  dns2.bezeqint.net   udp dpt:domain
ACCEPT     tcp  --  bzq-82-81-202-249.cablep.bezeqint.net  dnsdrp.bezeqint.net tcp dpt:domain
ACCEPT     udp  --  bzq-82-81-202-249.cablep.bezeqint.net  dnsdrp.bezeqint.net udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'


```

Any suggestions?
(p.s. i'm not connected behind a firewall)

---

### Post by trawler on 2006-01-12
I'm starting to think i got myself into a real mess here... *sigh*

I tried to --purge firestarter and got this:

dpkg: error processing firestarter (--purge):
firestarter: subprocess post-removal script returned error exit status

---

### Post by trawler on 2006-01-12
For information sake, i thought i'd update that it seems the problem was with java, not iptables...

I fount the solution [here]("http://ubuntuforums.org/showthread.php?t=76086") :D :D :D :KS

---

### Post by Mr_Grieves on 2006-01-12
**EDIT* DOH! Well.. I guess this information may be useful in the future. Great that you got things working. *EDIT**


Yea. Check with tcpdump if any data is send/recieved from the hosts.
You might have to install tcpdump first.

```

sudo apt-get install tcpdump

```

Try this command to check all traffic to/from a specific ip host.

```

tcpdump ip host <IP-adress>

```

You may aswell turn on logging in iptables using:

```

-j LOG

```

In the end of the rule you want to log.

---

