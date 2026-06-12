---
title: "mode master with RT2400"
date: 2005-11-15
forum: Desktop Environments
---

### Post by gdcondor on 2005-11-15
Hi,

My wireless card (0000:01:07.0 Network controller: RaLink Wireless PCI Adpator RT2400 / RT2460) is working out of the box with Breezy but i can't set it in master mode :
```

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

```
(eth1 corresponds to my wireless card)
other modes like managed, monitor or ad-hoc are working

i tried to build a new module with module-assistant but it's not changing anything :( (and it seems that there is a bug as building the module failed while looking for some kernel-image-2.6.12-9-386 package which is in fact linux-image-2.6.12-9-386 : i corrected it and managed to install the module)

any idea ?
-- 
GdCondor

---

