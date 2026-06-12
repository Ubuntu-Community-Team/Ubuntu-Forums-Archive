---
title: "LM Sensors &amp; Freq Scaling"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by skymera on 2007-06-12
i wanted to use LM sensors to detect and change my fan speeds.
but reading elsewhere people say dell make their fans undetectable or something?
im running a Dimension E520, Dual Core.

oh and a\nother question, i read about frequency scaling on ubuntuguide.
i enabled speed step in my setup like it said.
but when i went to use

sudo modprobe speedstep-centrino

in the Terminal and it said device was busy..
anyone know what to do?

thanks :)

---

### Post by kill4killin on 2007-07-06
When I tried to download an app that controlled my frequency scaling it made my fans spin up really load and dropped my battery time down to less than an hour...so I uninstalled it...personally, when it comes to power managerment, I say let Ubuntu do it's thing out of the box and don't mess with it...it gets worse when you try from what I have found.

---

### Post by neptho on 2007-07-06
> **skymera said:**
> i wanted to use LM sensors to detect and change my fan speeds.
but reading elsewhere people say dell make their fans undetectable or something?
im running a Dimension E520, Dual Core.

oh and a\nother question, i read about frequency scaling on ubuntuguide.
i enabled speed step in my setup like it said.
but when i went to use

sudo modprobe speedstep-centrino

in the Terminal and it said device was busy..
anyone know what to do?

thanks :)

Many of the machines do not work with lmsensors, but the E520 may be different.  The reason it said it was busy is that you already have a module loaded; it may be the acpi module; My Core Duo uses the acpi_cpufreq module:

```
%lsmod | grep cpufreq
acpi_cpufreq           10056  1
cpufreq_stats           7360  0
cpufreq_ondemand        9228  0
cpufreq_userspace       5408  0
cpufreq_conservative     8200  0
cpufreq_powersave       2688  0
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
processor              31048  2 thermal,acpi_cpufreq
```

Try that and see if you already have a module installed; then it's as simple as seeing if it's already running.  If it is, there are various tools you can use.  You can use powernowd, cpufreqd, and powersaved.  I've been using powernowd with no ill effects.

Good luck!

---

