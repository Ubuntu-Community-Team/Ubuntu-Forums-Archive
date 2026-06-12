---
title: "lucid lynx high xorg cpu"
date: 2010-06-05
forum: Desktop Environments
---

### Post by t8sh on 2010-06-05
Why is xorg utilizing so much cpu all the time? My system is so slow...


It seems that my cpu is always around 50% or higher for xorg. I did free -m below as well. Do I not have enough RAM? I've noticed a lot of other people having the problem too in other forums, but I haven't found an answer yet.  This is getting so frustrating that I'm considering going back to Windows.  I love Ubuntu, don't get me wrong, but I need performance...is this a bug? is this a hardware problem?



root@desktop:~# free -m
             total       used       free     shared    buffers     cached
Mem:           867        727        140          0         73        365
-/+ buffers/cache:        287        579
Swap:         1608          0       1608

---

### Post by Carl Heymann on 2010-06-09
I suddenly ran into what appears to be a similar issue.  My CPU usage  shot up, with xorg using most of it.  Anything I do seems to use more  CPU than needed.  Booting up is much slower than before.  I didn't  perform any update between the last good boot and now.. maybe its a  hardware issue.

It doesn't matter if I use compiz or not, the CPU is still very slow.   Can anyone suggest some diagnostics?

---

### Post by quequotion on 2010-06-09
I'm having similar problems. Everything is slow. I've been through the logs but I can't find anything that seems relevant. Two days ago my machine froze, suddenly rebooted, and then everything just slowed down...
I did some hardware diagnostics just in case but everything checks out.

---

### Post by Carl Heymann on 2010-06-09
I've isolated my specific problem: it's related to the power supply or charging circuitry of the laptop.  If the power supply is connected, the CPU is slow.  If the power supply is disconnected, everything is fine.

So, it's almost certainly a hardware issue in my case, I'll have IT sort it out (it's my work laptop).

---

### Post by quequotion on 2010-06-10
I also figured mine out, which was a BIOS problem. My desktop has APM features to reduce CPU usage when overheating or even shutdown in case of component failure. These features cause system-wide slowdown when enabled. Not sure if that's a bug in the BIOS, the hardware, or if it's a bug at all (the manual and the BIOS description are both in terrible English). Anyway, it seems mine was also not an Ubuntu problem.

Perhaps your laptop has power management settings to run at different CPU levels based on status? (Plugged In, Battery only, Full Charge, etc) I have another pc, a Toshiba laptop, with these features and often forget. They may be set in software on the desktop or in BIOS.

---

### Post by lcnrj on 2010-07-28
I have the same problem, but in my desktop.
No matter wich program I'm using whem xorg goes drivers cpu to 100% everything freezes

---

### Post by eumetaxas on 2010-08-08
the same here, compaq nx9010. Upgraded just a week ago and the problems started

---

### Post by eumetaxas on 2010-08-08
After **re-installing sun-java** according to this thread
[http://ubuntuaddict.com/solved-xorg-high-cpu-usage/](http://ubuntuaddict.com/solved-xorg-high-cpu-usage/)
everything is back to normal.

I love open source but functionality is essential.

---

### Post by blur xc on 2010-08-30
> **eumetaxas said:**
> After **re-installing sun-java** according to this thread
[http://ubuntuaddict.com/solved-xorg-high-cpu-usage/](http://ubuntuaddict.com/solved-xorg-high-cpu-usage/)
everything is back to normal.

I love open source but functionality is essential.

That link doesn't seem to be working.

I've been noticing this off and on.  Today when I sat down in front of my computer, xorg was using 40% cpu, with nothing running, except a firefox window.

Thanks
BM

---

