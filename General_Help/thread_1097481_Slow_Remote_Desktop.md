---
title: "Slow Remote Desktop"
date: 2009-03-16
forum: General Help
---

### Post by paragonconcept on 2009-03-16
I have remote desktop enabled. I'm coneecting to my ubuntu machine on a LAN and it's super slow. I've used a similar setup to access my work machine using Cisco VPN over apple remote desktop and there's minimal latency. This setup has about a 2 second lag on any action, and i'm not leaving the LAN. 

Any ideas on where i should begin troubleshooting?

---

### Post by askreet on 2009-03-16
Your case sounds extreme for a LAN-based VNC.  I use VNC over my lan with wireless and it's not nearly as responsive as, say, Microsoft Remote Desktop, but it's far more usable.

Over slower links I like to recommend NX ([www.nomachine.com](www.nomachine.com)) as a remote solution.  It uses a self-contained highly-tuned X-forwarding system.  It's actually very usabled over the Internet.

---

### Post by paragonconcept on 2009-03-16
That's so weird. Even when i did real vnc on on windows it worked fine. Any other ideas for native ubuntu solutions.

---

### Post by paragonconcept on 2009-09-19
The problem was with Chicken VNV on OS X. I switched to JollyFastVNC and it worked fine.

I dont not reccomend anyone use Chicken VNC at this point.

~Jack

---

