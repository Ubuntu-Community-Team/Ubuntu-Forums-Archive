---
title: "Fluxbox drains battery fast...cpu options?"
date: 2009-04-16
forum: Desktop Environments
---

### Post by pw_f100_220 on 2009-04-16
Hi, I have Fluxbox over Ubuntu, and I don't know a way to change my cpu speed in Fluxbox, and the battery goes down in half the time of Gnome.  

I can monitor the cpu but I don't know how to make it calm down.  Any suggestions for slowing it down or other battery saving tips for Flux?

Thanks!

---

### Post by psteph222 on 2009-04-16
It's not specifically 'gnome' or 'fluxbox' that's varying the battery usage.  By default gnome installs a power monitor in the desktop menu.  You can download similar power management tools through your ubuntu package manager - Fluxbox just doesn't do this automatically for you since it's geared towards being a simpler lightweight window manager.  I'm a big fan of Fluxbox, Whitebox, and Blackbox.

---

### Post by pw_f100_220 on 2009-04-16
...and which tools should i look up?

---

### Post by Daisuke_Aramaki on 2009-04-16
> **pw_f100_220 said:**
> ...and which tools should i look up?

Try gkrellm. although i am doubtful that fluxbox is draining your battery.

---

### Post by pw_f100_220 on 2009-04-16
i tried gkrellm...is it just a monitor?  because i have those...i just want something to keep the cpu running on power saver mode or whatever.  

i wouldn't think fluxbox is draining my battery, but i still observe twice the battery life in Gnome and I haven't found a way to tell Fluxbox to stay at low cpu speeds...so I'm starting there

---

### Post by Daisuke_Aramaki on 2009-04-16
> **pw_f100_220 said:**
> i tried gkrellm...is it just a monitor?  because i have those...i just want something to keep the cpu running on power saver mode or whatever.  

i wouldn't think fluxbox is draining my battery, but i still observe twice the battery life in Gnome and I haven't found a way to tell Fluxbox to stay at low cpu speeds...so I'm starting there

Oh you want to monitor it like the power manager does. obviosuly gkrellm is a status monitor. anyway one can always add gnome power manager on the fluxbox panel as well. but that is not the solution

---

### Post by psteph222 on 2009-04-17
I don't have any recommendations I can name since I haven't used an alternative window manager on a laptop in a long time but it's easy enough to try searching the package manager for acpi or power management or battery monitor.

---

### Post by Anzan on 2009-04-18
If you add 

   [exec] (GNOME Control) { /usr/bin/gnome-control-center }

to your menu file then you can access all of the GNOME config stuff.

If you want more detailed control add

   [exec] (Gconf) { /usr/bin/gconf-editor}

---

### Post by torgils on 2009-09-28
powertop, is a very nice app to "analyze" you power usage, and it comes with suggestions to increase your battery life..

---

### Post by montitan on 2010-05-07
a bit late..
anyone knows an applet which can reduce the cpu-clock? the default gnome-applet wont run in my flux, or does anyone know how to do that?

---

### Post by pw_f100_220 on 2010-05-08
the more i get into flux, the less i use applets...or gui's in general.  if you can stomach it, look up "cpufrequtils."  I don't know how it installs in ubuntu, but eventually you can control it from terminal easily:

```

cpufreq-set -g powersave

```

for example.

---

