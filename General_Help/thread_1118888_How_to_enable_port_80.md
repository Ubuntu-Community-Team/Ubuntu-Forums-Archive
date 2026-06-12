---
title: "How to enable port 80"
date: 2009-04-07
forum: General Help
---

### Post by mermulade on 2009-04-07
I am running a home server, and am only able to access my server locally with my local IP. I know what my outside IP is, but cannot get over the stupid port configuration. If anyone could tell me how to enable port 80, the help would be greatly appreciated.

--Mermulade :popcorn:

---

### Post by 3Miro on 2009-04-07
So you have probably a modem that connects to a router and your computer has internal IP (something like 192.168.x.x or 10.10.x.x).

The problem is not with Linux, if you can access the server from the local network, then it is working fine. You have to "forward" or "redirect" the port from the Modem/Router to the internal IP of the computer running the server. How to do that, depends on the modem/router that you have, read the manual.

---

### Post by mermulade on 2009-04-07
Thanks a lot! I will fiddle with my router now:p

---

