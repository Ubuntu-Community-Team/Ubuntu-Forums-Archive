---
title: "Ubuntu Network Analyzer"
date: 2008-04-13
forum: Desktop Environments
---

### Post by sardion on 2008-04-13
You sound like you know what you're doing so I'll give you the overview.

You know how to set up 2 NIC firewall boxes.... I assume that means you know how to set up NAT inside your firewall.

The same trick will work for your needs.  Build a machine with 2 NICs.  One connects to the LAN in place of the router.  The other connects to the router.  Your machine plays a NAT game so that the LAN is NAT'ed with respect to the router. (Treat the router like you would the internets).

You shouldn'e havt to change any settings on anything that way.

---

