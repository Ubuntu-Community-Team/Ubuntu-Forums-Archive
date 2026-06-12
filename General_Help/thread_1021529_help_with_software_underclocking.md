---
title: "help with software underclocking?"
date: 2008-12-25
forum: General Help
---

### Post by geodeath on 2008-12-25
Hi all!
I just installed latest ubuntu (8.10) on an old sempron 3000 processor so i can use it as a file server (just dumping all my files there) and i noticed that it might run a little hot as after some time ubuntu starts crawling. Of course when a cpu overheats it either freezes or the mobo restarts in fear of burning the cpu. I just installed to my panel the temperature sensors so i can monitor what happens. What i want to do is have this system 100% fanless. I installed a huge Genesis 2 heatsink that almost covers the motherboard and i originally planned to underclock the cpu so it can stay fanless. I am not really aware if this is possible via software generally (i mean even in windows) but i mostly care about doing it in ubuntu. Why? Because my motherboard wont allow me to run the cpu lower than it should since its multiplier is locked and the fsb cannot get lower than 200...

Any ideas? :popcorn:

(another idea that comes to mind is to buy another, recent am2 cpu that is considerably cooler-if there is one but i would prefer not for $$$ sake)

---

### Post by dcstar on 2008-12-25
> **geodeath said:**
> Hi all!
I just installed latest ubuntu (8.10) on an old sempron 3000 processor so i can use it as a file server (just dumping all my files there) and i noticed that it might run a little hot as after some time ubuntu starts crawling. Of course when a cpu overheats it either freezes or the mobo restarts in fear of burning the cpu. I just installed to my panel the temperature sensors so i can monitor what happens. What i want to do is have this system 100% fanless. I installed a huge Genesis 2 heatsink that almost covers the motherboard and i originally planned to underclock the cpu so it can stay fanless. I am not really aware if this is possible via software generally (i mean even in windows) but i mostly care about doing it in ubuntu. Why? Because my motherboard wont allow me to run the cpu lower than it should since its multiplier is locked and the fsb cannot get lower than 200...

Any ideas? :popcorn:

(another idea that comes to mind is to buy another, recent am2 cpu that is considerably cooler-if there is one but i would prefer not for $$$ sake)

If that CPU supports Powernow-k8 (I think that it does) then you can set the CPU to run at the lowest clock rate possible. Check your syslog for any messages like that.

Make sure you have the powernowd packages installed.

---

