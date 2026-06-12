---
title: "Fatal &quot;no screens found&quot; when starting X session"
date: 2015-12-17
forum: Desktop Environments
---

### Post by krelverehan on 2015-12-17
Hey guys,

I am having some major problems here when trying to get my X session going after a kernel upgrade. Pretty much I can't load my X session on anything past Linux 3.16.

```

$ cat /var/log/Xorg.0.log | grep EE
(EE) failed to load module "nvidia" (module does not exist, 0)
(EE) failed to load module "nouveau" (module does not exist, 0)
(EE) failed to load module "fbdev" (module does not exist, 0)
(EE) failed to load module "vesa" (module does not exist, 0)
(EE) failed to load module "nvidia" (module does not exist, 0)
(EE) failed to load module "nouveau" (module does not exist, 0)
(EE) failed to load module "fbdev" (module does not exist, 0)
(EE) failed to load module "vesa" (module does not exist, 0)

(EE) no screens found(EE)

(EE) Server terminated with error (1). Closing log file.

```
this is the case with even a trying a new install of any variant of Ubuntu that uses any kernel newer than Linux 3.16 it seems.

I have a nvidia GeForce gtx 970 graphics card.

Any help would be appreciated! Let me know if you need more system details.

Thanks,
-Krel

---

### Post by deepakdeshp on 2015-12-17
Hello 
In your grub there will be option to boot from your old working Kernel . Did you use it?

---

### Post by krelverehan on 2015-12-18
Yes, I can do that, but that isn't a permanent fix. I would like to keep using a modern kernel.

---

