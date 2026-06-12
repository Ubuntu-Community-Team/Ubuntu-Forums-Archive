---
title: "Please help with bug: Linux headers 2.6.22-14"
date: 2009-01-12
forum: General Help
---

### Post by No More Windows on 2009-01-12
I'm still pretty green. I was going to do a cold install upgrade from 7.10 to 8.10, but Ubuntu does not recommend it unless a condition exists regarding the partition.  That's over my head at this point, so I have a problem to resolve to bring my updates current so I can upgrade to 8.04, and then 8.10.

When I try to get updates, I get an error message: "A unresolvable problem occurred while initializing the package information.  Please report this bug against the 'update manager' package (which I do not know how to do) and include the following error message: 'E: The package linux-headers-2.6.22-14 needs to be reinstalled, but I can't find an archive for it.'"

How can I resolve this?

---

### Post by dcstar on 2009-01-14
> **No More Windows said:**
> I'm still pretty green. I was going to do a cold install upgrade from 7.10 to 8.10, but Ubuntu does not recommend it unless a condition exists regarding the partition.  That's over my head at this point, so I have a problem to resolve to bring my updates current so I can upgrade to 8.04, and then 8.10.

When I try to get updates, I get an error message: "A unresolvable problem occurred while initializing the package information.  Please report this bug against the 'update manager' package (which I do not know how to do) and include the following error message: 'E: The package linux-headers-2.6.22-14 needs to be reinstalled, but I can't find an archive for it.'"

How can I resolve this?

If you have a kernel installed that is later than 2.6.22-14, then you should be able to remove all of the 2.6.22-14 packages using Synaptic.

---

