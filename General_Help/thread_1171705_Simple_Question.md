---
title: "Simple Question"
date: 2009-05-27
forum: General Help
---

### Post by GnubbyaBush on 2009-05-27
So I've actually gotten my proftpd server working with TLS authentication as well. The only problem is it only works locally, the only adress I know for it is a 192.168.x.x. This local adress doesn't work from other networks nor does the external adress of the server computer (just found by googling my ip). I know i don't need a masquarade, what do i do to get an external adress?

---

### Post by Ms_Angel_D on 2009-05-27
If your on a router you'll need to open port 21 so that the incoming port 21 traffic is directed at your internal ip (ie... 192.168.x.x)

---

### Post by GnubbyaBush on 2009-05-27
oh ok, i could have swore i did that, but maybe its set up for another port. Thanks for the advise.

---

### Post by Iowan on 2009-05-27
Open the port(22) - or forward it?  Unless you have a static address, your external address will likely change.  You may need a service like dyndns.com or no-ip.com.

---

### Post by GnubbyaBush on 2009-05-27
oh ok so dyndns is a service that will keep my external ip static? do the ppl outside my network need to use my external adress? Or will it work to use my local adress. Turns out I had the ports forwarded already, maybe i will try to dmz.

---

