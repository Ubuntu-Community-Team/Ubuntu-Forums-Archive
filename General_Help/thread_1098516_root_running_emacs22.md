---
title: "root running emacs22?"
date: 2009-03-17
forum: General Help
---

### Post by kmads on 2009-03-17
hi,

I have just noticed I whole lot of disc-activity on my laptop. 'top' showed me that root was running 'emacs22'...? 

Does anyone which process that starts emacs? (and why)

Thanks,
kmads

---

### Post by bgilbert on 2009-09-21
Hi,

Did you ever figure this out? I just had the same issue...emacs22 (run under root) was using 80-90% CPU. Just appeared out of the blue, and only noticed because my CPU temps jumped up suddenly. 

Thanks,
Bryan

---

### Post by jpkotta on 2009-09-21
I'll assume that you were not editing any files as root with emacs, since that's an obvious explanation.  (BTW, if you do need to edit files as root, use Tramp instead of running emacs as root).

Did you recently install or upgrade any packages?  I'm pretty sure if you install any elisp packages, part of the installation involves emacs byte-compiling the .el files.  Maybe there was an error that left a rogue emacs process going.  

Maybe there is a cron job that invokes emacs (unlikely)?

That's all I can think of.

---

### Post by rpi+ on 2009-09-22
> **bgilbert said:**
> Did you ever figure this out? I just had the same issue...emacs22 (run under root) was using 80-90% CPU. Just appeared out of the blue, and only noticed because my CPU temps jumped up suddenly. Bryan

Me too: I noticed much activity on my hard disk, and [FONT=Courier New]'$ top'[/FONT] showed me 70 % CPU for emacs22 run under root (for about 30 seconds after login), but I did not start emac22.

Any ideas? Thanks in advance,

rpi.

---

