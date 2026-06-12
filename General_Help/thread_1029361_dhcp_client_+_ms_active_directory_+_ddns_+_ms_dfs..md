---
title: "dhcp client + ms active directory + ddns + ms dfs... is this all going to work?"
date: 2009-01-03
forum: General Help
---

### Post by adealey on 2009-01-03
I'm trying to build a project using a bunch of Linux-based clients in a Microsoft environment.

The client boxes have to meet for four requirements. Its a deal killer if any of the four is a no-go.

1. Must be DHCP clients (w/MS DHCP servers): This one is a piece o' cake. No problems.

2. Must be Active Directory domain members: This certainly seems doable. I started trying a quick & dirty Proof of Concept using Likewise-Open just because it seemed it would be quicker to configure than doing all the pieces of the puzzle (Samba, windbind, etc) separately. However, after a little bit of knocking my head against Likewise-Open I'd be willing to accept it might not be the way to go.

3. Clients IP addresses must be added to DNS via DDNS updates (MS DNS servers): I haven't looked at this yet but surely it should be straightforward, right?

4. Clients have to be able to access CIFS shares via MS Dfs references: This, I fear, is going to be the deal killer.


So, anybody want to chime in on whether they think this is all achievable or not?

---

