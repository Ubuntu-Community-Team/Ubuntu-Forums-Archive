---
title: "netstat question"
date: 2006-09-18
forum: Desktop Environments
---

### Post by Koori23 on 2006-09-18
I recently installed Azureus, played with it for a while, then uninstalled it. I didn't like the fact that I had an open port on my system. NMap reports that all ports are closed. Netstat has things I don't understand though..

Netstat -tal reports this:

tcp        0      0 localhost:44244         *:*                     LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN
tcp        0      0 localhost:52951         *:*                     LISTEN
tcp        0      0 localhost:smtp          *:*                     LISTEN
tcp        0      0 localhost:56883         localhost:44244    ESTABLISHED 
tcp        0      0 localhost:44244         localhost:56883    ESTABLISHED  
tcp6       0      0 ip6-localhost:smtp      *:*                     LISTEN

what does *.* mean? and why do I see it so much?

---

### Post by bswilson on 2006-09-18
> **Koori23 said:**
> what does *.* mean? and why do I see it so much?

It means that the port is listening but no connection is active either to the localhost or to any remote system.  You'll see that a lot on any UNIX system.  Sockets are how programs communicate with one another.

---

