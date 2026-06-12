---
title: "disable ipv6 DNS queries"
date: 2011-02-03
forum: Desktop Environments
---

### Post by surfer on 2011-02-03
i'm on a local network with ubuntu servers and clients only. recently, network connections started to take very long to respond. i found out that DNS resolution would first send an ipv6 (AAAA) query, wait for the timeout, and only then send an ipv4 (A) query to the server.

none of my DNS servers have an ipv6 address and there are no ipv6 entries for the DNS server.

i configured my machine not to use ipv6 (in /etc/default/grub: GRUB_CMDLINE_LINUX_DEFAULT=”ipv6.disable=1") but the problem still remains!

in know how to turn ipv6 queries off in firefox and ssh, but i would like to have a global way that tells all applications not to use ipv6 DNS queries. is there a way to do that? and how is this done?

(this is all for ubuntu 10.04 lucid lynx LTS)

---

