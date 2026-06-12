---
title: "Dell Inspiron upgrade to Ocelot Fan Noise"
date: 2011-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by appalbarry on 2011-10-15
Let Ubuntu upgrade to Ocelot yesterday, and since then the Dell has a fan running non-stop.  I've also been unable to to load the proprietary AMD drivers.

AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ × 2 
Running 32 bit Ubuntu

---

### Post by mrkennie on 2011-10-15
There is an outstanding bug with the kernel since 2.6.38. the details and a possible workaround you can try can be found here:

[http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1)

---

### Post by appalbarry on 2011-10-15
The critical bit of info from that page is:

[INDENT]Namely, most people affected by this issue will want to add "pcie_aspm=force" to their boot command line. Simply adding this will force Active-State Power Management to be enabled.[/INDENT]

Instructions how to do that are [_here_]("https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Temporarily_for_an_Existing_Installation").

I tried this on a temp basis and it seemed to work, so I'll now add it permanently.

---

