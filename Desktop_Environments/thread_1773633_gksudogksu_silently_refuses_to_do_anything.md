---
title: "gksudo/gksu silently refuses to do anything"
date: 2011-06-02
forum: Desktop Environments
---

### Post by Jaken Veina on 2011-06-02
This comes at  some point after installing GNS3 and Dynamips, which require  administrator access as GUI's. Although, the first couple times I tried  to run GNS3 as administrator, it worked fine. I do still receive the password prompt, whether running from the command line or the context menu. Note that GNS3 is the first  application for which I've needed to run gksudo, so this may have been  an issue before the above were installed, although I've always been able  to run "Open as Administrator" in Nautilus and "Synaptic Package  Manager," which now will not run either.

Running Ubuntu 10.10.

Thanks in advance for any advice.

---

### Post by Bonster on 2011-06-02
run "gksu" and try to change some options, like make sure it says root

---

### Post by Jaken Veina on 2011-06-02
No, gksu has had the same reaction.

I've found that the following command gets things working properly again
```

xhost +LOCAL:

```
but is not persistent after a reboot. Any way to make this permanent?

---

### Post by Bonster on 2011-06-02
Maybe add it to autostart programs so it will load up after every boot

---

