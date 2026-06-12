---
title: "Is PAN blocked by my Firewall?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by mibadt on 2006-08-17
Hi,
Just installed PAN (News group reader) in my Kubuntu Dapper.
Initially, PAN couldn't connect to my ISP's news server, yet after I temporarily disabled the Guarddog firewall, PAN connected flawlessly. I couldn't find which protocol PAN uses and couldn't find how to configure Guarddog accordingly.

By the way, I'm behind a router-could this be related (maybe IPV6 problem which is **NOT** supported by the router). Maybe this is nor firewall related?

TIA

---

### Post by Darrena on 2006-08-17
> **mibadt said:**
> Hi,
Just installed PAN (News group reader) in my Kubuntu Dapper.
Initially, PAN couldn't connect to my ISP's news server, yet after I temporarily disabled the Guarddog firewall, PAN connected flawlessly. I couldn't find which protocol PAN uses and couldn't find how to configure Guarddog accordingly.

By the way, I'm behind a router-could this be related (maybe IPV6 problem which is **NOT** supported by the router). Maybe this is nor firewall related?

TIA

NNTP is tcp port 119, so you need to allow tcp port 119 outbound.

---

### Post by mibadt on 2006-08-18
Bless you !

You solved my problem !
:D

---

