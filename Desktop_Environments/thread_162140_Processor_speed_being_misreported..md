---
title: "Processor speed being misreported."
date: 2006-04-18
forum: Desktop Environments
---

### Post by Exile29 on 2006-04-18
I've noticed a problem in Ubuntu. 
In several different bug reports (Nvidia, etc...) I've noticed that my AMD 3200+ processor speed is being detected at 1000 when it should be 2000. 
I know that it is still running at full speed, but it bothers me anyhow.
Is there a fix for this (other than just ignoring it?).

---

### Post by Exile29 on 2006-04-18
Oh... I forgot to mention that I have the CPU monitor desklet enabled and running. It is also misreporting the processor speed.

---

### Post by pulsharc on 2006-04-18
Are you on a laptop? If so it is the CPU throttling feature of your processor, it will jump up only when more power is needed to save battery life.

---

### Post by Exile29 on 2006-04-19
No. I have a desktop system.

AMD 3200+
Biostar 6100 - 939 Mobo
1 Gb (512 x 2) Ram
XFX Nvidia 7300 GS (256 onboard + 256 shared)
250 Gb SATAII HDD

There shouldn't be any processor throttling going on here. I know the processor is running at 2 Gig, I just don't know why the system doesn't know. Ya' know?

I'd switch to the AMD64 kernel, but since I've only been on Linux for about 2 weeks, I'm not ready to start tweaking yet.

---

### Post by Miguel on 2006-04-19
There is a known bug where AMD64 processors report (on /proc/cpuinfo and similar) their speed wrong by a factor of 2. I don't remember if it is half or double, or if it only appeared on the x86 ubuntu or the 64 bit version.

Have a look at the forums for "clock .bug" or similar. You can also browse malone. Sorry for not being more informative :(

---

### Post by Exile29 on 2006-04-19
Cool. 
Thanks guys! As long as I know what I'm looking for, I'm bound to find the answer. :-D 

I'll start looking into clock.bug and see what I come up with.

---

### Post by Miguel on 2006-04-19
Hi again Exile,

You don't need the dot. It's a typo I made. I'll correct it. BTW, you can further refine your search with AMD or AMD64 or similar.

---

