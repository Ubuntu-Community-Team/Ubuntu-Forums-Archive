---
title: "Problems after updating from 8.04.02 to 8.04.03"
date: 2009-07-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by QiShen on 2009-07-04
I have an old Dell Inspiron 2500. Been using Kubuntu for a long while now and was very satisfied until the last update that took me from version 8.04.02 to version 8.04.03. Since the update, I noticed that the system is very slow, loading programs takes for ever. There seems to be a problem with either or both HDD access and/or RAM access and/or memory swapping from and/or to RAM/HDD. It's driving me nuts!!! There is a lot more HDD access than before. Is anyone experiencing the same problems?

Also, as anyone successfully upgraded from 8.04.02 or 8.04.03 to 9.04? I am tempted do do it but since my laptop dates back to 1999... I'm not convinced that it's a good idea.

Thanks for your help.

---

### Post by philcamlin on 2009-07-05
upgrades cause so much problems...

fresh install is always bettrer

if you want you could back up your files and fresh install 9.04 and it would work better

---

### Post by QiShen on 2009-07-06
Kubuntu 9.04 will not install on my Inspiron 2500, Celeron 800Mhz laptop. Is there any way I can go back to 8.04.2 from 8.04.3? Thanks.

---

### Post by ugm6hr on 2009-07-06
> **QiShen said:**
> Kubuntu 9.04 will not install on my Inspiron 2500, Celeron 800Mhz laptop. Is there any way I can go back to 8.04.2 from 8.04.3? Thanks.

No.

8.04.02 and 8.04.03 are the same OS, just with a further 12 months of updates.

I would not recommend using an OS online without recent security updates.

Perhaps if you post your full specs, we can recommend a solution.

---

### Post by QiShen on 2009-07-06
Thanks for your reply ugm6hr.

By "full specs", what do you mean? All software titles and versions installed? Hardware specs? I know there exists console commands I can use to fish out information about my installation. I would appreciate if you could list them for me in a reply and I'll be able to send all the information you need.

Thanks.

---

### Post by QiShen on 2009-07-07
SOLVED!

I was running KDE System Monitor last evening to look at  what was going on with the CPU and Memory access and noticed that te System Monitor was only reporting half of my total amount of the physical memory installed in my laptop!!! I closed Kubuntu, rebooted into the system setup utility that confirmed that only half of the memory was recognized. Removed both of my memory DIMM modules, reinstalled them, went back into the system setup utility that now showed that all the physical memory installed was recognized. Booted into Kubuntu, which loaded much faster (no wonder!). I'm now back to normal use. Just a coincidence that, for some reason, one of my memory modules was not recognized right after I updated Kubuntu... Thanks.

---

