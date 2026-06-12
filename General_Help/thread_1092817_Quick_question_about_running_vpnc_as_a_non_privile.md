---
title: "Quick question about running vpnc as a non privileged user"
date: 2009-03-10
forum: General Help
---

### Post by ukchucktown on 2009-03-10
I have a quick question about running vpnc as non-root. I created a new group and assigned my personal account to the group and updated group membership on the /etc/vpnc directory. I don't have problems running vpnc as root or using sudo. When I try to run as myself I get the permission error:

```

vpnc: Error binding to source port
Failed to bind to 0.0.0.0:500: Permission denied

```

Is there a permission I can modify to run vpnc as non-root? Thanks.

Grant

---

