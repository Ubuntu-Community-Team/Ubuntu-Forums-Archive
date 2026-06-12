---
title: "Blocked ICMP/DNS?"
date: 2006-01-17
forum: Desktop Environments
---

### Post by loadlinux on 2006-01-17
Hi, I am quite new to Linux. (I tried Red Hat Linux 8 quite a number of years before, but gave up then.) I installed Ubuntu Breezy two months before and there have been no big problems at all. I really enjoy it!

However, today I found my Firestarter had a new entry on "Events" which I had never seen (the page was *blank* for months)  It said that it had blocked a connection "from . port 53 protocol=icmp service=dns". I doubt what that is.

I am currently lying behind a firewall, and my Firestarter (1.0.3-1.1ubuntu1) was set by default. Would anyone please help? Thank you!

---

### Post by loadlinux on 2006-01-17
The detail of the connection is as follows:

Direction: Unknown
In: eth0
Out: 
Port: 53
Destination: ubuntu (My Computer)
Length: 56
TOS: 0x00
Protocol: ICMP
Service: DNS

I just doubt why I get this connection block. My box is used as ordinary purpose, i.e. no server services. Is that normal?

---

### Post by loadlinux on 2006-01-17
I suddenly found a relevant log at /var/log/kern.log "ubuntu kernel Inbound IN=eth0 OUT= LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=10 PROTO=ICMP TYPE=3 CODE=3 DST=192"

Oops. What's that?

---

