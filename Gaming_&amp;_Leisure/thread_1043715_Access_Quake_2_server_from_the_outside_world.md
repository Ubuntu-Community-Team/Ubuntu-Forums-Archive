---
title: "Access Quake 2 server from the outside world"
date: 2009-01-18
forum: Gaming &amp; Leisure
---

### Post by TheFuzz4 on 2009-01-18
Hey Everyone,

Ok I have googled to my hearts content on this one.  Starting Friday night I began setting up a Quake 2 server here at my house.  Yes I am aware that this is an old game but however my friends and I decided to start playing this again since we used to have such a blast playing this years ago. So anyways I have this IBM Xseries server here at the house that I recently installed kubuntu on and I decided that it had more than the required guts in it to be a kickin quake2 server so here is my problem.  First I am going to write a great how to on this when I get a chance on how to setup one of these servers at your house because it just took me way too many different sites and time then should've been required to do this so to help out anyone else I will put together a how to on this.
Ok so my server is now up and running like a champ and I can access it from inside my house with no problems whatsoever however if I check to see if it is available from outside I cannot connect to it.  
When I was first setting up my server I used wine to run the server and that worked fairly well except for the fact that I needed to be on the server to get it to run and that was unacceptable for me since my server is in a closet now and to hook a monitor up to it is not easy.   However while it was running with wine you could see the server from outside my network.  
So now I have the server up and running using r1q2ded-old since that package is designed for linux and fixes some of the security holes.  But since I started to use that the server is now not accessible from outside so I was thinking that there was something in iptables blocking it so I ran this:
iptables -A INPUT -p udp -m udp --dport 27910:27912 -j ACCEPT that way it wasn't blocking any requests although I'm not really sure if it truly was since I can access it from inside but I am not really all that familiar with iptables.  So anyways it comes down to I need to figure out how to get this thing accessible from the outside but I am now at a loss with this.  The ports on my firewall are opened up and forwarded to the server properly.  
I appreciate all help anyone can provide on this and thank you everyone in advance for your help with this.

---

### Post by TheFuzz4 on 2009-01-18
Ok so I'm retarded turns out my server.cfg file had my port listed as 27912 and not 27910.  So after doing that my server is now open to the outside world.  Anyone wanna play?

---

