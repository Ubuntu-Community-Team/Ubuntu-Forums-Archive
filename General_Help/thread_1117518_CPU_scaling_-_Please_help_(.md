---
title: "CPU scaling - Please help :("
date: 2009-04-06
forum: General Help
---

### Post by marklfca on 2009-04-06
Hi everyone,

My CPU is overheating (I know it needs to be replaced, but can't do it just now).  It's a Core 2 Duo @ 1.86GHz.

I'm able to lower its frequency in WIN VISTA so it runs around 64C but in Ubuntu (cpufreq) it won't go under 1.60GHz (temperature is 81C).

Only TWO options present in Gnome CPU thingy are: 1.86 GHz and 1.60 GHz.

[B][I]$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

1862000 1596000 [/I][/B]

I really need to lower this to around 1.20 GHz so I can run @ 60-70C. 

Is there any way how to add lower frequencies to this? Please help. I spent last 14 hours googling everything about CPU scaling in Ubuntu and still no luck.

Running new 9.04 beta ATM, but same problem in prev. version.


THANKS

---

### Post by marklfca on 2009-04-06
No one?

---

### Post by JohnLau on 2009-04-06
> **marklfca said:**
> Hi everyone,

My CPU is overheating (I know it needs to be replaced, but can't do it just now).  It's a Core 2 Duo @ 1.86GHz.

I'm able to lower its frequency in WIN VISTA so it runs around 64C but in Ubuntu (cpufreq) it won't go under 1.60GHz (temperature is 81C).

Only TWO options present in Gnome CPU thingy are: 1.86 GHz and 1.60 GHz.

[B][I]$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

1862000 1596000 [/I][/B]

I really need to lower this to around 1.20 GHz so I can run @ 60-70C. 

Is there any way how to add lower frequencies to this? Please help. I spent last 14 hours googling everything about CPU scaling in Ubuntu and still no luck.

Running new 9.04 beta ATM, but same problem in prev. version.


THANKS
Can you set it in the BIOS? :lolflag:

---

### Post by marklfca on 2009-04-06
> **JohnLau said:**
> Can you set it in the BIOS? :lolflag:

Yes, but when I boot to Ubuntu it's back @ 1.86 GHz.

---

### Post by JohnLau on 2009-07-09
Has you problem bene solved yet?
... I think the best way is to replace your heatsink of your CPU :(

---

### Post by t4thfavor on 2009-07-09
All CPU's come with a heatsink rated for their thermal output. I suggest cleaning out your heatsink, fan, and maybe applying some new thermal paste between your CPU, and heatsink. Its not as hard as it sounds, and thats a fairly new machine to be "replacing".

Im still using some PIII's for light workstations. So a core duo is more than good enough to be keeping around for a few more years.

---

### Post by JohnLau on 2009-07-10
Yes... you are right, but there is a chance of having a broken heatsink, especially intel's push pins are quite easy to breal :lolflag:

---

### Post by XCan on 2009-07-10
> **marklfca said:**
> Yes, but when I boot to Ubuntu it's back @ 1.86 GHz.

If you lower the multiplier or FSB in BIOS, it WILL stick. The frequency monitor is kind of dodgy, as I believe it only pulls the information from the factory set values. For example, I've overclocked my machine and benchmarks clearly show a near linear performance gain for FFT. Still the frequency monitor displays the factory values.

---

