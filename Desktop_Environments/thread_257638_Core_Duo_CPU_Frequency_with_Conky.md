---
title: "Core Duo CPU Frequency with Conky?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Wilb on 2006-09-14
Hi,

I'm trying to configure my Conky to show the frequency of both cores of my Intel Core Duo much like you can with the Gnome CPU Frequency Applet. I've got it displaying the individual CPU usage percentages using:

CPU1 ${cpu cpu1}% ${cpubar cpu1}
CPU2 ${cpu cpu2}% ${cpubar cpu2}

However using:

CPU1 ${freq cpu1}
CPU2 ${freq cpu2}

It is just displaying the same frequency for both cores at all times. It does appear to be dynamic, but its always the same value for both. I'm using the apt-getable conky - is it a feature thats only available in a new version, or is it just something out of conkys bounds for now?

Thanks in advance.

Wilb

---

### Post by m.musashi on 2006-10-14
I'm looking for a solution to this too. I seem to have a somewhat different version than you and I can't quite decipher it.

However, I think CPUs are numbered 0 and 1. Try changing the numbers and see what happens.

---

### Post by gambrjl on 2008-03-20
well.. I'm bring back an extremely old thread but I'd got the same thing...

I've got a dual core 1.5 machine but when I use the ${freq} settings it starts out as 1500MHz but then settles in at 1000MHz

under System -> Hardware information.  The 2 cores are shown until linux.acpi_path as CPU0 and CPU1 which I have set in my conkyrc file.

What gives?  Shouldn't it be showing 1500MHz all the time or am I missing something?

---

### Post by biasedopiniondrummer on 2008-06-21
i'm experiencing the same thing with an amd 6000+, has anyone resolved it yet?

---

### Post by cl0ckwork on 2008-06-21
im using ${freq_g} (for Ghz) on my AMD turion X2 on dynamic and its working fine. also, even though your system labels the processors as 0 and 1 conky sets 0 as total or average CPU and then uses 1 and 2 for the seperate cores.
and yes, both cores usually change at the same time while on dynamic settings

are you using the latest versions available?
post your conkyrc code if you are still having problems

---

