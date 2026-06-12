---
title: "squid access denied on other subnets."
date: 2009-06-10
forum: General Help
---

### Post by ant2ne on 2009-06-10
My goal: This proxy is a webcache only. It does not need to do any filtering or security. I’d like anyone regardless of IP to be able to use this webcache if they want. Any idiot from outside the lan who wants to use this webcache can go right ahead and suffer through our T1 based bottlenecks.

My Problem: I’ve got the server and squid running. Its ip is 10.60.140.251.. My IP is 10.60.140.225 and it functions just fine. When logged into a computer on any other subnet, the proxy answers with the access denied webpage. It is the squid’s access denied webpage so I know that the client computer can contact squid, squid just isn’t letting the client through to the internet. I can only assume this is an acl issue with other subnets. Do you have any acl suggestions?

I’d include my squid.conf file, but it is the modified default and it is huge and hard to read. If you would like to have me grep a certain line out of the conf file for evaluation, please ask.

I’m trying to use webmin for configuration as much as possible. Not that I can’t use a conf file, but If I get hit by a bus on Tuesday, I think anyone who takes over this project may need a gui interface to manage it.

---

### Post by ant2ne on 2009-06-18
I got it working, I don't know how, exactly. But I backed up my squid.conf onto a different server.

---

