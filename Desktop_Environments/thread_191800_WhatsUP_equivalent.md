---
title: "WhatsUP equivalent?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by z_diver on 2006-06-08
Does anyone know if a program exists for linux that can be used to monitor servers and services on a network in a similar fashion to how Ipswitch's "[[COLOR=DarkRed]What's Up Pro[/COLOR]]("http://www.ipswitch.com/products/whatsup/professional/index.asp")" works on windows?

I just want to see if the servers are online, no need to manage them or anything.

Thanks!

---

### Post by z_diver on 2006-06-10
[quote=z_diver]Does anyone know if a program exists for linux that can be used to monitor servers and services on a network in a similar fashion to how Ipswitch's "[[COLOR=DarkRed]What's Up Pro[/COLOR]]("http://www.ipswitch.com/products/whatsup/professional/index.asp")" works on windows?

I just want to see if the servers are online, no need to manage them or anything.

Thanks![/quote]

I guess there is nothing like this.  It sure would be a good server side program and since it functions with ping and snmp, seems like it wouldn't be too difficult to design.

---

### Post by fargle on 2006-06-10
No offense dude, but if you don't know much about the subject at hand (and you obviously don't) then it's not cool to post a definitive no.

Check out [Nagios]("http://nagios.org"), the premier uptime monitoring solution.

---

### Post by PeterWolf on 2006-06-11
[QUOTE=fargle]No offense dude, but if you don't know much about the subject at hand (and you obviously don't) then it's not cool to post a definitive no.

Check out [Nagios]("http://nagios.org"), the premier uptime monitoring solution.[/QUOTE]

Actually, Cheops is more like WhatsUp. Unfortunately Cheops (or Cheops-ng) don't seem  to be being developed (and haven't been for sometime). Nagios is probably a little more complex than the poster is looking for. And I would hate to think that the complexity and power of Nagios is described as an "uptime monitoring solution".

---

### Post by z_diver on 2006-06-11
Thank you!  Kinda knew there must be something as good or better for such a server centric platform as Ubuntu(debian).

I think much of the trouble finding something was due to the fact I had synaptic set to search just "name" so it wasn't finding anything when searching for "network monitor".  After looking up nagios by name and seeing network monitor in the description field I figured out synaptic wasn't reverting to the "name and description" behavior after restarting it, and once I had that squared away I started finding a LOT of good stuff. 

Ultimately this service is to run on a headless debian server and be accessible through browser so I'll look into setting up Nagios or maybe even [Zabbix]("http://www.zabbix.com") for that.  The WAP interface on nagios looks pretty slick so might go and set that up next but for now I have cheops giving me the basic headsup.  

btw, cheops took 10 seconds to install + 10 more to figure out to run as root but then it instantly produced a visual display of hosts on the network.  Right clicking those hosts allows scanning them which produces a great rundown on what services were running and which version of those daemons they use.  Really helpful!!!!

I had forgotten all about MRTG and the many similar RRDtool utilis that take after it also, so I'll have to go and check all of that out as well.

Anyway thanks for the helpful responses.  There ARE tons of good tools out there.

---

### Post by coreyt on 2006-06-11
I'm glad I looked here.  Zabbix is exactly what I'm looking for for some extra monitoring at work.

---

