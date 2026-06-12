---
title: "excessive processor use..."
date: 2007-07-22
forum: Dell  Ubuntu Support
---

### Post by mongo51 on 2007-07-22
I just installed UBUNTU a few weeks ago...got it up and running with a few glitches...my roomie writes LINUX stuff so he helped me, as I have been a Windows user...anyway, I have a problem...I am experiencing really gross excessive processor use...I start the machine, a Dell Inspiron 8200...things are fine until at some point something seems to be using a huge amount of processor space...usually, 100% of the processor is taken up...have GNOME System Monitor and it shows a huge jump in usage...when I open the system monitor panel for running processes, I find most stuff sleeping but Mozilla/Firefox BIN is running...also, I find that the GNOME System Montior is running and using anywhere between 70-100% of the processor...this makes any downloads, page changes and anything else very slow and glitchy...it eventually gets to the point that the machine locks up and I have to unplug to shut down...what could be the cause of this...I like UBUNTU, but unless I can solve this, I have no choice but to return to Windows, which I REALLY do not want to do!!!!...also, I have notices lately (today) that whatever it is seems to be making the machine boot very slowly...several times, when the processor is very overloaded, the machine shuts down and I lose what I am working on...any ideas...tks, [email]zencvp@yahoo.com....tks[/email], Charlie

---

### Post by zanglang on 2007-07-22
The System Monitor CPU usage tends to jump pretty high, but I don't think it's the cause of your problem (it's just like the 'Idle process' in Windows). Firefox doesn't usually do that too, unless you go to Flash-heavy sites that your computer can't handle well... Might be some buggy rogue program. Can you try running
> top
from the console and write down what processes seem to be at the top with abnormally high CPU (check the %CPU column) most of the time?

---

### Post by mongo51 on 2007-07-23
Thank your for your reply...have actually been keeping track of the System Monitor panel...only seem to be two processes running at any time that use any processor...one is Firefox BIN, which is minimal...however, the System Monitor shows CPU usage at anywhere between 40-100%...when I put the pointer on the little screen (CPU usage graph on the desktop) it regularly shows maxed out at 100%...at the same time, the System Monitor CPU usage will be jumping all over the place...nothing else seems to be running...all sleeping or zombied...I am watching the desktop monitor screen at the moment and watching IT jump all over the place, usually up around 100%...Does this help...I am so unfamiliar with LINUX that it is a bit mystifying to me...appreciate the help...TKS, Mongo51...zencvp@yahoo.com

---

### Post by zanglang on 2007-07-24
It's normal for System Monitor to be the highest on the list, I think it's something else causing problems.

Can you try opening up a terminal, enter:
> top
and keep an eye on what's on the top of that list when the slowdown happens? (There might be more than 1 with abnormally high CPU, so check the %CPU column)

---

