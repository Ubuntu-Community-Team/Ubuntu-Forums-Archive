---
title: "Odd behaviour of computer's clock"
date: 2009-04-25
forum: General Help
---

### Post by Chris62 on 2009-04-25
Hi,

Can anyone explain this strange behaviour? I have a dual boot Windows XP/Ubuntu 8.10 machine and the clock in both OS is set to Central European Time, and both OS are set to the same timezone.

Whenever I boot into Windows immediately after using Ubuntu, the computer clock is always exactly two hours behind the time that it should be displaying.

While this is not a problem, merely an irritation, I would like to know why this happens since the parameters relating to the time and the time zone in both OS are the same.

Can anyone suggest why this happens and what, if anything, can be done to stop it?

Many thanks,
Chris

---

### Post by CatKiller on 2009-04-25
Linux sets the hardware clock to UTC. Window sets the hardware clock to local time.

You can tell Linux to use local time for the hardware clock by putting ```
UTC=no
``` in your /etc/default/rcS. This is the default in Jaunty because of dual-boot users like yourself.

---

### Post by Chris62 on 2009-04-26
Manythanks for your help CatKiller

Regards,
Chris

---

