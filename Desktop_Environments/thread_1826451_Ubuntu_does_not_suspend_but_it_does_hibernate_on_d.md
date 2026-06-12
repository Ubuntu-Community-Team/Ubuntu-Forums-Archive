---
title: "Ubuntu does not suspend but it does hibernate on desktop"
date: 2011-08-16
forum: Desktop Environments
---

### Post by dr1094 on 2011-08-16
Some background info: I am running Ubuntu Natty (11.04) on a desktop pc with 1.7 GB of memory, and AMD Athlon 64 X2 Dual Core 5200+. When I installed Natty a message came up saying something about inadequate hardware, but i think I have all the hardware necessary, if not, can someone please tell me which hardware i need to replace or purchase. Currently the natty works fine as a desktop system except for one thing, and that's my question.

The desktop computer does not suspend.Although It will hibernate, upon clicking suspend a black screen comes up with white text (which is gibberish to me). At that moment the computer is frozen, I have to hold the power button to shut it off and restart it. The way I see it is that since it hibernates, it should suspend as well.Why does it not suspend properly?

Thank you for your help

---

### Post by dr1094 on 2011-08-27
anyone?? anything?

---

### Post by wildmanne39 on 2011-08-27
Hi, there have been some suspend issues with natty.

How much swap do you have? you need at least 2 gigs to suspend.

---

### Post by dr1094 on 2011-08-29
I have 1.7 Gig, I am in doubt that this is indeed the problem since the computer has little problem hibernating. Though for now, thank you for your help, I will upgrade the pc, and get back to you if i have more problems.

Also i will leave the thread as unsolved for some more time just in case of more insight from others.

---

### Post by adotomov on 2011-08-29
I was struggling with this problem for a while on a laptop. I believe the problem is with natty not mounting the swap partition after resume. The swap is not the same as the system memory. If I understand correctly you have 1.7GB of RAM. Check your partitioning if you have at least 2GB of HDD space for swap and that the SWAP is set as a primary partition.

---

### Post by wildmanne39 on 2011-08-29
Hi, I was talking about 2 gigs of swap space on the hard drive not ram.

---

### Post by dr1094 on 2012-10-23
so over the past few months I have installed ubuntu on various personal computers, and discovered that those that have problem hibernating or sleeping have the same exact issues in windows. So it was likely a hardware issue. Thanks for all the answers, greatly appreciated.

One new thing I learned due to this thread and online readings is that we definitely need SWAP memory.

---

