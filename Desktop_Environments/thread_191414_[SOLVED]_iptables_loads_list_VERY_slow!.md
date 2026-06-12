---
title: "[SOLVED] iptables loads list VERY slow!"
date: 2006-06-07
forum: Desktop Environments
---

### Post by RavenOfOdin on 2006-06-07
After upgrading iptables from 1.3.1 to 1.3.5, using my system directory as an install point, the command 

```

iptables -L

```

starts loading the list at a rate of about 2 entries every 5 seconds.  

Would Internet connectivity problems or a network hardware upgrade cause this?
I've recently had some issues with my ISP.

---

### Post by steve.horsley on 2006-06-07
Try ```
iptables -Ln
``` to disable the reverse DNS IP->name lookup.

---

### Post by RavenOfOdin on 2006-06-07
[QUOTE=steve.horsley]Try ```
iptables -Ln
``` to disable the reverse DNS IP->name lookup.[/QUOTE]

Ah.

If its related to DNS lookup, that may very well be an ISP issue.  At least I know that's going to resolve itself in a couple of hours since they're fixing whatever it is they broke.

Thanks.

---

### Post by steve.horsley on 2006-06-07
It's only a guess. I could be wrong.

---

### Post by bthatcher on 2006-08-16
Im having the same issue. However when I do a iptables -Ln is get 


# iptables -Ln
iptables: No chain/target/match by that name

Any ideas?

Thanks,
Brandon

---

### Post by amcouper on 2008-05-21
# iptables -Ln
iptables: No chain/target/match by that name

use iptables -L -n

---

