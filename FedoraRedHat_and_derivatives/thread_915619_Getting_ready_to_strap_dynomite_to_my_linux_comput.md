---
title: "Getting ready to strap dynomite to my linux computer"
date: 2008-09-10
forum: Fedora/RedHat and derivatives
---

### Post by arscaptain45 on 2008-09-10
Ok after giving up on the old system everyone was helping me with I have set up a old compaq desktop as a temp server. I had to do something. Our Rescue Squads site has been down for over a year now and I am the closest thing to a admin we have. Now I have learned a little bit by playing with the system. To make things easier for myself I have setup the server at home. The problem I am having is that I can access the web site from inside my local network fine. 

I can load the site by using 192.168.0.200 on any local computer or localhost on the servers browser. But when I try my url (arborrescue.org) the connection will timeout after a few minutes. A few times I was able to load some of the sites home page. It seems that when accessing the server over the web it is extremely slow. 

Here is a quick run down on the system and local network

I am using a D-link DI-624 router and a motorola surf board cable modem. The router is set up to have 192.168.0.200 as a virtual server on port 80. I have also tried setting DMZ for 192.168.0.200 with no luck.

In linux my apache configuration is set to listen to all addresses on port 80. Server name is still set to localhost

under network configuration I am using a static address, My router is 192.168.0.1 so I set it up this way,
address     192.168.0.200
Subnet mask 255.255.255.0
Gateway     192.168.0.1

Please can someone take a few minutes and help me out here. Also I forgot to say that I set up the router with the virtual server since that was the closest thing to port forwarding on the router. Thanks again

---

### Post by arscaptain45 on 2008-09-11
Ok I have fixed the problem but I still don't know why there was problem.

First my ISP has started blocking port 80, Second problem is im not that bright at times. After finding a working port I still could not connect to the server even though Canyouseeme.org could see the server through the new port settings. So now I turned back to looking at my router. I rest it many time and tried many different ways to set it up with no luck. I really would like to use this router since it has wireless and lan. I had a new D-link(EBR 2310) router without wireless sitting in my car for a few months now so I tried it just to be sure. And sure enough it worked like a charm. Now I know my D-link router w/o wireless had no port forwarding but it did have DMZ and Virtual Server settings  so why wouldn't it work when it seemed to be set up right. I tried to update the firmware but D-link has not come out  with a firmware update for my model version. Can some please tell me what im not seeing here. If I have a no-ip.org account with port forwarding shouldn't using DMZ and having the server listen to the forwarded port # on all addresses work?

---

### Post by starcannon on 2008-09-11
I'm not able to really help "fix" the problem, but I thought I'd spit ball a possible alternative your direction. A entry level web host costs $10 a month and has none of the problems, and a hulluva lot more bandwidth. First time payment may cost $30 by the time you register or transfer your domain, but then its pretty cheap after that.

Anyway, just something to consider.

GL and if your mostly just wanting to do this from home, then I will defer advice to someone with more network tunneling knowledge than I have.

---

