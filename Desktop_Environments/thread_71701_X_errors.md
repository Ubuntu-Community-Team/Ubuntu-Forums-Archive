---
title: "X errors"
date: 2005-10-04
forum: Desktop Environments
---

### Post by myha on 2005-10-04
Hi all!

When I start X I always get the following errors:
```
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Synaptics Touchpad no synaptics event device found (checked 5 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/CID, removing from list!
Could not init font path element unix/:7100, removing from list!
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/CID, removing from list!
```

I uncommented unix/:7100 and /var/lib/defoma/x-ttcidfont-conf.d/dirs/CID and the last 4 errors were gone, what can I do about the other errors? btw touchpad is working without problems...

Also: How to know which fonts do I have to use? It looks like I dont even need unix/:7100 path and defoma fonts...

thanks,
Miha

---

