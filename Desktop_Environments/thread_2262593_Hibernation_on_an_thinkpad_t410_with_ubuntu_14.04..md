---
title: "Hibernation on an thinkpad t410 with ubuntu 14.04."
date: 2015-01-26
forum: Desktop Environments
---

### Post by Frank_Brner on 2015-01-26
Hello.

I have the problem, that my t410 goes to hibernation normally and without error message. But when I turn it on again, it freezes a few seconds after showing the loading screen.
It's ubuntu mate version and I use full encryption of my ssd.

On Ubuntu 13.04. hibernation worked fantastic. 

What may be wrong? Is an intel onboard graphic chip version of the t410.

Regards
Frank

---

### Post by tgalati4 on 2015-01-26
Your swap space needs to be larger than your RAM.  How large is your RAM?  How large is your swap partition?

```
free
```

> 
tgalati4@Mint17 ~ $ free
             total       used       free     shared    buffers     cached
Mem:       **2040640**    1919960     120680      54248      41880     175348
-/+ buffers/cache:    1702732     337908
Swap:      **2578428**     903232    1675196


There are log files in /var/log (pm-suspend.log, pm-powersave.log, etc).  Go through those and post any errors.

Were you using full disk encryption in 13.10 and an SSD?

Welcome to the forums.

---

### Post by Frank_Brner on 2015-01-26
Hi.

I tried it with 14.04. LTS, which I wanted to use in future. There it does not work. The logs, you named, have only entries with "success" after each line - no errors!

In 13.04. I only use home folder encryption.

Regards
Frank

---

### Post by Frank_Brner on 2015-01-28
Hello.

Meanwhile I found out, what's the problem...
The kernels from ubuntu 14.04. are complete crap! When I use the kernels from tuxonice for 12.04. or 13.04. for example, all works perfectly without errors or freezes or anything else.

Regards

---

