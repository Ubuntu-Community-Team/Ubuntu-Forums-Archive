---
title: "Dist-upgrade, linux-686-smp, NVIDIA oh my"
date: 2006-06-09
forum: Desktop Environments
---

### Post by kundalinikat on 2006-06-09
Here's my problem (besides not rebooting more often and taking things once at a time) :)

I did a dist-upgrade to Dapper, saw nothing seriously wrong, added a "apt-get install linux-686**-smp**" cause I have dual Pentium IIIs, downloaded the thing from nVidia's website to get the latest version of their driver.

I rebooted, X windows failed to load and dumped me to the prompt, and the nVidia program says it can't find the suitable thingy for my kernel.

Should I try the nvidia-glx package? Is there a way to get the nVidia program to work with linux-686-smp?

---

### Post by mcduck on 2006-06-09
Have you got restricted modules for your kernel?

Also, I think the nvidia-glx package is worth a try.

---

### Post by tseliot on 2006-06-09
Read my guide and/or try my script:
[http://ubuntuforums.org/showthread.php?t=139264]("http://ubuntuforums.org/showthread.php?t=139264")

---

