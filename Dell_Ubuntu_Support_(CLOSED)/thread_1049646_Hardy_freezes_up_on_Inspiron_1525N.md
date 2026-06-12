---
title: "Hardy freezes up on Inspiron 1525N"
date: 2009-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Madwand on 2009-01-24
I have a Dell Inspiron 1525N running Ubuntu Hardy. Unfortunately, the computer sometimes (unpredictably) freezes up on me during normal activities, such as browsing the web using firefox. Ctrl-Alt-Backspace will just leave the graphical environment and give me a bunch of text I don't understand, instead of allowing me to login again. I have to hold down the power button for several seconds to turn off the laptop, then turn it back on to get a usable machine. Can anyone help me understand what is going on and how I can fix it?

Thanks!

---

### Post by starcannon on 2009-01-24
> **Madwand said:**
> I have a Dell Inspiron 1525N running Ubuntu Hardy. Unfortunately, the computer sometimes (unpredictably) freezes up on me during normal activities, such as browsing the web using firefox. Ctrl-Alt-Backspace will just leave the graphical environment and give me a bunch of text I don't understand, instead of allowing me to login again. I have to hold down the power button for several seconds to turn off the laptop, then turn it back on to get a usable machine. Can anyone help me understand what is going on and how I can fix it?

Thanks!
Start by going through some log files, I'd look at kernel and xorg logs. 
I am not adept enough to say more than that to salvage your install; however, I will say that I have really found that 8.10 has been my laptop distro of choice, every laptop(with exception of SiS based models) that I have thrown 8.10 at have worked perfectly out of the box. I'd recommend doing a clean install of 8.10 on your laptop. Other than that, if I had no option I'd start looking at logs, posting errors, and of course searching them.

---

### Post by heapy on 2009-01-25
i hav been getting seemingly random freezes myself mate, but it turned out to be a hardware problem rather than software. 
 Do you get the same system lockup using another operating system? I installed vista, so my advice is to check and make sure.

are you using a NVIDIA card? I found I got more crashes after installing the drivers. Maybe your problem is nothing like mine, but its just my 2p.

---

### Post by Madwand on 2009-01-25
The Inspiron uses "Intel Graphics Media Accelerator X3100", so NVidia problems are likely not the culprit here.

I haven't tried Windows on the laptop, and probably won't.

The next time the laptop freezes, I'll try to see if the logs say anything helpful. A remote login with SSH might work.

---

### Post by heapy on 2009-01-26
the only reason i mentioned windows is to rule out linux as the problem. If you get the same or similar lockups using other operating systems, you can rule out a software conflict.

i for one am getting random freezing using linux., so installed windows from a formatted hdd. then got a bunch of BSOD's, then I had an idea what the problem was. Im not good at diagnosing pure linux problems, all I know is that no operating system runs on bad hardware.

I really hope your computer is not suffering the same fate as mine.

---

### Post by Madwand on 2009-01-26
Well, I've looked at the various logs (including the kernel and x.org logs) in /var/log, but I don't know what to look for to determine what the problem might be. How do I figure out where an error may have occurred and what it might be? Are there troubleshooting steps I can follow? Or should I try to find some way to post the entire logs on these forums to have someone else take a look?

---

