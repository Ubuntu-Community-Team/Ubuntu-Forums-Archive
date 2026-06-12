---
title: "Xubuntu box refusing WAN VNC requests"
date: 2006-09-28
forum: Desktop Environments
---

### Post by Lunarbunny on 2006-09-28
So I have RealVNC working alright on my Xubuntu machine...except it drops WAN packets. I can access it via LAN but even with port 5901 forwarded on my router and shown listening with netstat -l

I have a url redirected to my external IP that will work from the computer on the same LAN as the VNC is on if the ports are forwarded but not if the ports are not forwarded on my router, which makes me think that the VNC machine itself is refusing the WAN packets.

Machine is a Compaq Presario 7470 ([specs]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dest_page=product&dlc=en&product=94486&docname=c00012507")) with the only non-standard things being 192MB (184MB available) of RAM, an 8GB HDD (the computer had fallen out of use and its original 20 was scavenged when the 40 died in another computer. Maxtor sucks - pass it on), and a Netgear FA311 10/100 NIC.

---

