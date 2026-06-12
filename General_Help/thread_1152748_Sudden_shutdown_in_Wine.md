---
title: "Sudden shutdown in Wine"
date: 2009-05-08
forum: General Help
---

### Post by thegreger on 2009-05-08
Hi everybody! Complete newbie here.
I have been using Ubuntu 9.04 for the last week now (had a short fling with Ubuntu 8 a while ago, but I couldn't make it work properly on my laptop), and I'm slowly getting settled in. But I have encountered a problem.
When I try to emulate Mafia (the game) in Wine, everything seems to work. But after a while the pc speaker beeps three times, and my computer shuts down. If I try to boot it up instantly again, nothing happens. The power led lights up for a second or so and then it dies again. Is my computer (HP tx2020) overheating or could it be something else? Is there any way to find logs of this kind of events?
Thanks for the help (as well as all the help I have found in previous threads trying to get everything to work)
Greger

---

### Post by milton1 on 2009-05-08
It does sound like an overheat or under-power problem. Have you tried searching for beep codes for your model of motherboard? The three beeps is probably trying to tell you exactly what is wrong.

---

### Post by thegreger on 2009-05-09
All info I can find about beep codes is that on my model should mean something related to the memory. But when I (rather cunningly) stacks up my computer with a couple of remote controls in order to get airflow under it, the problem seems to have disappeared. It might be something that occur pretty infrequently, of course. Can Wine mess with the laptop charge settings? So that the computer switch to battery power even though it's connected to AC?
Thanks for helping! If nothing more happens then I'll just continue playing with something beneath the computer, and assume it was overheating.

---

### Post by thegreger on 2009-05-09
> **milton1 said:**
> It does sound like an overheat or under-power problem.
It appears as if you were right. I found the syslog, and moments before my computer shut down (again) it reads:
May  9 23:18:27 simon-TX2020 kernel: [  835.449972] ACPI: Critical trip point
May  9 23:18:27 simon-TX2020 kernel: [  835.449984] Critical temperature reached (95 C), shutting down.
May  9 23:18:27 simon-TX2020 kernel: [  835.948570] ACPI: Critical trip point
May  9 23:18:27 simon-TX2020 kernel: [  835.948583] Critical temperature reached (95 C), shutting down.
May  9 23:18:28 simon-TX2020 kernel: [  836.449555] ACPI: Critical trip point
May  9 23:18:28 simon-TX2020 kernel: [  836.449569] Critical temperature reached (95 C), shutting down.
May  9 23:18:28 simon-TX2020 kernel: [  836.950180] Critical temperature reached (88 C), shutting down.

Nothing to do but buying one of those fancy laptop cooling things with fans, I suppose.

---

### Post by milton1 on 2009-05-10
You might also consider cleaning the fans and heatsink. Poor airflow can easily lead to overheating problems in laptops.

---

### Post by thegreger on 2009-05-10
> **milton1 said:**
> You might also consider cleaning the fans and heatsink. Poor airflow can easily lead to overheating problems in laptops.

Thanks for the tip. I'll open it up and take a look at it. The computer is only six months old, but fur from the cat seems to cover everything in my apartment anyway.

---

