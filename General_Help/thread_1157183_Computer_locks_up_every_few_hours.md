---
title: "Computer locks up every few hours"
date: 2009-05-12
forum: General Help
---

### Post by psycovic23 on 2009-05-12
Hi,

I've got a pretty old P4 machine with a fresh install of Jaunty on it, but it keeps on freezing every few hours.  I used to have an 8.10 install on it that worked for a few months, but then the freezing started so I reformatted with Jaunty.  I suspect a hardware issue (at one point, the file system corrupted on the second reboot), but I'm not sure how to test it. Kernel logs don't show anything when it does freeze either.  Any suggestions?

---

### Post by LoneWolfJack on 2009-05-12
if this is a hardware issue, you probably have an overheating CPU or GPU.

there are some nice tools for ubuntu that can monitor CPU temp, but I found them rather complicated to set up and half of the sensors don't seem to work anyway, so my advice would be to check CPU and GPU temperature through your system BIOS right after a lockup.

CPU temperature should be less than 50°C to be on the safe side. if it's more than say 70°C it is too hot any may lock up. no consumer CPU will survive 80°C or more for longer periods of time. hit 120°C and your CPU will be dead becaue the physical structure of the CPU die will break down. no worries though, as your CPU will be dead long before you reach that temp. ;)

---

### Post by psycovic23 on 2009-05-12
> **LoneWolfJack said:**
> if this is a hardware issue, you probably have an overheating CPU or GPU.


I ran memtest for a few hours and it went fine. Temperatures after lock up are normal (40c for cpu, 20c for mobo).

---

### Post by LoneWolfJack on 2009-05-12
ok, go to system->system log and check the log files if you see anything fishy around the time of the last lockup

---

### Post by nacho32 on 2009-05-12
> **psycovic23 said:**
> I ran memtest for a few hours and it went fine. Temperatures after lock up are normal (40c for cpu, 20c for mobo).
what program are you using? to monitor the temp?, if your going straight to your bois under non stress the reading is inaccurate. The bios shows temp under no stress. If you are running a dual boot see if the manufacture of the mother board has a application for this. Then do a bench mark. usually under the bios non stress add 15c under stress depending on your cooling system

---

### Post by albinootje on 2009-05-12
> **psycovic23 said:**
> Kernel logs don't show anything when it does freeze either.  Any suggestions?

What about installing a debug kernel ? Just an idea.
```

apt-cache search kernel|grep debug

```

---

