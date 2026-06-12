---
title: "Crystal cs4235 SoundCard Problem"
date: 2006-01-17
forum: General Help
---

### Post by MeanEYE on 2006-01-17
Hiho people. Well am heaving A problem.

For Crystal cs4235 sound card there should be kernel module named **snd-cs4235.ko** in **/lib/modules/<kernel version>/kernel/sound/isa**. The problem is, it's not there! Well, I digged a bit around internet and it turns out **snd-cs4236.ko** supports cs4235 based sound cards.

So I try to load that module:
[FONT="Courier New"]**[INDENT]   sudo modprobe snd-cs4236[/INDENT]**[/FONT]
and in return I get [COLOR="Red"]No such device[/COLOR] error. Now I have tested the sound card and it works perfectly in windows. Any instruction I have found on internet tells me to load this module. I have tried every way, with any possible paramters and it **DIDNT** work.

Am using old Fujitsu-Siemens x400 which when it comes to drivers (windows or linux) is real pain...

If anyone can at least try to assist me, I would be greatfull!

---

### Post by chaumurky on 2006-01-17
Well that should work. My IBM 300PL has an onboard CS4235 chip and all I had to do was add snd-cs4236 in /etc/modules. What does **lspci** and **lsmod** give?

---

### Post by MeanEYE on 2006-02-07
Well **lspci** will show nothing since CS4235 based cards are ISA not PCI, but I have never tried **lsmod** because whenever I try to add module result is:

[INDENT][B]No such device...
Error inserting module.[/B][/INDENT]

Hm, my computer gives me creeps, really... Seams to me, that everyone has been able to use their sound cards based on CS4235 chips and I cant! None the less I will not quit searching for solution!

---

