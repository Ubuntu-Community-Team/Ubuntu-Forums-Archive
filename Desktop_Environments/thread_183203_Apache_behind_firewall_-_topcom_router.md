---
title: "Apache behind firewall - topcom router"
date: 2006-05-27
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-05-27
Hey, I'm having some trouble getting my apache server working. This is the deal:

On my server, I'm running ubuntu, and I've filled in the static IP I got from my isp, the gateway and so forth, and I can get online. Ive set up an apache server, but it's impossible to reach it from anywhere else then the local network. The topcom router I'm using has a firewall. I've tried setting up socalled "virtual server" on the topcom router, where ive opened port 80, and the virtual server is supposed to send all traffic coming through that way, directly to my server, which I have specified with the IP 192.168.1.101. But it just doesn't work.

Im from norway, and I apologize when it comes to my rather poor english skills. I hope that you understand what my problem is, even though my explanation wasn't really that great.

Appreciate all help, thanks.

---

### Post by jones_jj on 2006-05-28
You may need to route through port 8080 to get it to work, but I'm not totally sure about that.

---

