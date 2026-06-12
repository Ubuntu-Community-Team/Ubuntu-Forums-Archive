---
title: "HLDS and external IP. IPTables anyone?"
date: 2008-01-24
forum: Gaming &amp; Leisure
---

### Post by constchar* on 2008-01-24
Hey guys!

I'm running Ubuntu 7.10 Server Edition and HLDS and I've got this problem where
when I use the +ip parameter, unlike Windows, HLDS complains it cannot bind
to my external IP which makes sense but on Windows it automatically binds with
the local IP insted.

Now the reason this is a problem is because the Steam servers use the IP from
+ip parameter to establish an assortment of connections and since I can't give
it my external IP due to the reasons given above it uses the local IP and as a
result the Steam connections fail and the server doesn't get listed on the master
game server.

Now how can I use iptables, or some other tool, to route my external IP
to my local IP?

The local IP is 192.168.1.102 going through a Linksys router that has
had port forwarding setup properly.

Thanks!

---

