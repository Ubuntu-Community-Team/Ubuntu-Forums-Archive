---
title: "Remove firewall"
date: 2006-06-06
forum: Desktop Environments
---

### Post by bruenig on 2006-06-06
I am having, at least I think, firewall issues. I am using bittornado and when downloading a torrent, I get the yellow light indicating that I am behind a firewall and this has made me unable to connect to peers or achieve any reasonable download rate.

I don't really care about the low download rate but I feel like a leecher not sharing with anyone.

I would like to remove the firewall altogether.

I've done
```
sudo iptables --flush
```
but I still get the yellow light and can't connect to peers.

anyone know how to remove the firewall?

---

### Post by frenkel on 2006-06-06
Are you behind a router? Or does your modem have router functionality?
In these days most of them have a firewall build in. You'll need to enable port forwarding on the router/modem.

---

### Post by bruenig on 2006-06-06
I have a Zoom ADSL modem that has router functionality, how would i go about enabling port forwarding?

---

### Post by frenkel on 2006-06-06
Look in the manual?

---

### Post by Blind-Summit on 2006-06-14
[QUOTE=frenkel]Look in the manual?[/QUOTE]


That just cracked me up!

I have an issue with aMSN - I forwarded the correct ports yet I am told (by the webcam bit) that I am behind a firewall or NAT with blocked ports.

I have also read that Ubuntu does not have a firewall installed by default?

---

### Post by davmor2 on 2006-06-14
normally 192.168.0.1 or 192.168.1.1 in firefox gets you to the admin page then do the whole port forward thing from there good luck.:D

---

### Post by Blind-Summit on 2006-06-15
Yeah, I forwarded the ports on the router - but it's some Ubuntu config.

I installed Firestarter and I have got some info on forwarding ports and allowing connections, so I will post my results accordingly

---

