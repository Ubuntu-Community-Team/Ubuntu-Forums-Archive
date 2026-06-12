---
title: "CounterStrike server port problem"
date: 2005-05-12
forum: Gaming &amp; Leisure
---

### Post by pappo on 2005-05-12
I am running Hoary and I created a dedicated server for CounterStrike Source.

I can see the server from my other PC's on the home lan, but I my son could not see the server (port 27015) until I made the Ubuntu server a DMZ, on my DLink router.

I am using a cable modem, into a DLink router which acts as my gateway (192.160.0.1).

I don't want to make my Ubuntu server a DMZ because it will always be seen by the internet.
Does anyone know why Ubuntu is denying access to the 27015 port from my router/gateway, but is allowing access to the port from any other computer on my home (192.168.0.X) network ?

I am not running DHCP.  All four home PC's have a static IP.
The network consists of the Ubuntu machine, two WinXP's, and one Win2000Pro machines.

Thanks.
Phil

---

### Post by Ctrl on 2005-05-13
Guessing by your question. DMZ in router works. Then its the router and not Ubuntu
thats need a config. 
What you need to do is a portforwarding. Think its called virtual server in the router settings.

I dont know what model of Dlink router you have but there are plenty sites that describe how to do it.
[http://portforward.com/routers.htm](http://portforward.com/routers.htm) should be able to help you.

---

### Post by pappo on 2005-05-13
Ctrl - Thanks for the reply.
I do have a virtual server setup forwarding port 27015 to the Ubuntu machines IP address.  I had that before I used the DMZ option.
Yes, with DMZ set to my Ubuntu machine, outside people can see my CS server, but just using Virtual Server they cannot.

---

