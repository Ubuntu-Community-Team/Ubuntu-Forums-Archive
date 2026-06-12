---
title: "hdparm -- hdparm.conf not affected"
date: 2009-01-21
forum: General Help
---

### Post by dsiefert on 2009-01-21
Hi,

I am trying to disable write-back cache on my /dev/sda1 device.  To do so, I issue the following command:
> sudo /sbin/hdparm -W0 /dev/sda1

The output claims it is disabled the feature, however when I check hdparm.conf nothing has been modified.  I am not sure if this is supposed to be the case or not and the setting is maintained elsewhere.  When I rerun the above command it still reports that the feature was not disabled before--so it appears as if it had no effect running hdparm the first time.

How can I disable write-back cache so it is persistent (continues to stay that way)?

Thanks,
David

---

