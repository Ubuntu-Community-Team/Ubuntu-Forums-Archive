---
title: "Send IP packets to the outside world"
date: 2009-06-04
forum: General Help
---

### Post by amarjarubula on 2009-06-04
Hi all,

I have 2 computers that have IP addresses xxx.xxx.xxx.195 and xxx.xxx.xxx.196 which both have Ubuntu 8.04 and are connected to the same router. When I tried to send an IP packet from one PC the router sends the IP packet to the second one in just one hop. However I wanna make the packet go outside my router into the real world and take a loop back. I need to check the quality, packet-loss and packet-order and stuff like that, but I couldn't do it because of this router. I don't know if a proxy server could help. If so where can I get a GUI Proxy server for Ubuntu?

---

### Post by Boondoklife on 2009-06-04
Could you give a little more information here, are you trying to ping the other computer or tracepath? If so then the result that you are getting is perfectly normal. The only way that you would get it to leave your network would be if each box had an external IP which if you are behind a router is prolly not the case.

If you are trying to check your response time then just ping an outside server or you can use one of the webbased traceroute pages and then see what it tells you and tracepath to its domain to see a full round trip.

---

### Post by blueridgedog on 2009-06-04
Typically you would ping the next hope up to your isp (the next hope from your router) to determine link quality.  To do that you need to look in your router and see what public IP it has been assigned and what the next hope (gateway) is.

---

### Post by amarjarubula on 2009-06-04
Hi,

tx for replying. I am not either pinging or either finding the tracepath. Yes my router decides what IP do my computer should have and has routing tables for that. However, I have a voice engine with I actually could talk to a computer originating at a different place or either my second computer. My first scenario is the origin is US and destination is in India where I have low bandwidth and the quality of my call is considerably bad. There could lot of conditions which effect the quality which includes bandwidth. However in the second scenario of the call from the 2 computers originating from the same router is far better than one from the 1st scenario. As I would like find out if the bandwidth is the reason for the quality or if there are any other reasons I need to find out by making this call from my 2 computers only if the call originates through the Internet and not through my router. The reason is the router is very near and there could be no loss of IP packets, or disarray of IP packets or some other conditions like that. If anybody could help me how I can originate a call from my 2 computers and make it go through the internet and come back please help me. This would be a great help for me.

---

### Post by gamblor01 on 2009-06-04
> **amarjarubula said:**
> If anybody could help me how I can originate a call from my 2 computers and make it go through the internet and come back please help me. This would be a great help for me.

You should be able to do this by setting up dynamic DNS for your IP address.  Just register with [www.dyndns.org]("http://www.dyndns.org")

Once you have registered you can setup dynamic DNS for your IP -- something like amarjarubula.homelinux.org (or whatever you pick).  Then test the speed from one system hitting the amarjarubula.homelinux.org address.

This happens on my system because I have a web server running on one system.  If I enter in the IP address of the system (such as 192.168.0.100) then the connection goes directly through my router and I can get like 30 MB/s downloads (yes that's megaBYTES; I'm on a gigabit LAN).  If I visit the web site/perform a wget for a file using the dynamic DNS then I wind up getting only about 35-40 KB/s.

Note that my router is configured to forward HTTP traffic to the appropriate system.

---

### Post by dcstar on 2009-06-05
> **amarjarubula said:**
> Hi all,

I have 2 computers that have IP addresses xxx.xxx.xxx.195 and xxx.xxx.xxx.196 which both have Ubuntu 8.04 and are connected to the same router. When I tried to send an IP packet from one PC the router sends the IP packet to the second one in just one hop. However I wanna make the packet go outside my router into the real world and take a loop back. I need to check the quality, packet-loss and packet-order and stuff like that, but I couldn't do it because of this router. I don't know if a proxy server could help. If so where can I get a GUI Proxy server for Ubuntu?

And where exactly do you think this "loop back" is going to occur if both your addresses are on the same network?

The whole design of TCP/IP is to ensure packets take the shortest (and best) path between two network points.

If you want to check "packet loss" etc, do it to an external destination.

---

### Post by blueridgedog on 2009-06-05
> **amarjarubula said:**
> Hi,

I have a voice engine...the origin is US and destination is in India where I have low bandwidth and the quality of my call is considerably bad...I would like find out if the bandwidth is the reason for the quality

Now this clarifies what you want to do.  I can't give you a way to make a call from one PC on your LAN to another PC on your LAN and have the call routed through another router that is at least one hop upstream.  

One way of testing your connection to the US would be to trace the route to the end system, then ping (or flood ping for a 5 second interval) each hop along the way.

Alternatively, you can locate others with the same voice application in India and test the connection with them, some sharing your internet connection provider and some not.  

Just ideas and i wish you luck.

---

