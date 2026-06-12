---
title: "*identd does not work for ipv4 but ipv6 works ok"
date: 2006-06-22
forum: Desktop Environments
---

### Post by eosin on 2006-06-22
I've been through many of the ident demons available trying to solve this. No ident demons may bind to the ipv4 auth socket. Ipv6 works fine (returns the correct username). When I connect to an ipv4 irc server to test the protocol with a sniffer running, I get:

[B]56770 , 6667

56770 , 6667 : ERROR : NO-USER[/B]

But when using an ipv6 server, it works fine.
I am running **oidentd** in debug mode and get the following..
[B]Jun 22 15:28:39 mithrandir oidentd[30695]: Connection from efnet.xs4all.nl (194.109.129.220):0
Jun 22 15:28:39 mithrandir oidentd[30695]: [efnet.xs4all.nl] 64816 , 6667 : ERROR : NO-USER
[/B]
.. same thing
But connecting to an ipv6 server works just great. 
There is no identd enabled in inetd (if ubuntu even uses it)

I use ss (part of iproute2) to check my listening ports and connections and looking for auth, or identd with it (ss -ap | grep -i auth) I get..
** LISTEN     0      0                      :::auth                    :::* **
It does this no matter what protocol I use (6, or 4) it shows this. 
-p means to show what process is using the connection/port and as you can see it does not show me any proc listening but the port is open.

Weird. Does anyone else get this problem? I wonder if a recent upgrade killed the proc tables for v4 in the way that breaks identd access 

Any help would be appreciated.

---

