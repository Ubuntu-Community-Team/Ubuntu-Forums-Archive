---
title: "has anyone had problems with the gnome-applet cpu frequency and scaling monitor?"
date: 2008-06-21
forum: Desktop Environments
---

### Post by robert.cooper on 2008-06-21
if you have debugged at all with this program, please help me out. My problem currently is that the values in 
cd /sys/devices/system/cpu/cpu0/cpufreq/cpu_min_freq
and
 cd /sys/devices/system/cpu/cpu0/cpufreq/cpu_max_freq,
seemingly at random (and when i plug in or unplug the cord for the laptop), change to values other those specified by the filename.

---

### Post by sdennie on 2008-06-21
What values are they changing to?  Can you post the output of the following while both on and off battery power:

```

cpufreq-info 

```

You will probably have to install that first:

```

sudo apt-get install cpufrequtils

```

---

### Post by robert.cooper on 2008-06-23
on battery:

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 1.33 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 1.33 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

on ac power:
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.73 GHz and 1.73 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.73 GHz and 1.73 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.

it seems that on ac power, it is harder to keep the value in cpu_min_freq low; it seems to automatically jump up when on ac power. by the way, for an intel chip, is 70+C ok?

---

### Post by sdennie on 2008-06-23
If you are using the performance governor it wouldn't surprise me if it ignored your frequency settings.  If you want to manually change frequencies I think you will have to use the userspace governor or ondemand governor.  Unless you specifically have some dire need to use conservative and performance, I highly recommend you set both AC and battery to ondemand.  It's better at power savings than conservative and the likelihood that you will notice any difference between ondemand and performance is very, very low.

Edit:
70C seems very hot for an idle temperature.  If it's under load, that's fairly normal though.

---

### Post by robert.cooper on 2008-06-24
please provide a link or explain to me how to set the governor. I would be very thankful for instructions, as i have made numerous google queries on this matter.. along the lines of "cpu freq ubuntu, etc."
edit: 70C at load.. makes my fingers and or lap burn.. would like freq to go no higher than second from highest on ac power, ondemand on battery is fine.

---

### Post by sdennie on 2008-06-24
[code]
cpufreq-selector -g governor_name
[code]

Where "governor_name" is one of the governors listed by "cpufreq-info".

---

### Post by robert.cooper on 2008-06-24
ok. frequency, now on ac power, is stuck at max. unplugged, applet indicates "power save", and frequency (as indicated by the applet) is stuck at second from lowest. not exactly what you expected, eh? by the way, the last kernel update killed my wifi. i know there are active hotspots around, but nothing shows up. have you heard of a similar problem?

---

### Post by sdennie on 2008-06-24
> **robert.cooper said:**
> ok. frequency, now on ac power, is stuck at max. unplugged, applet indicates "power save", and frequency (as indicated by the applet) is stuck at second from lowest. not exactly what you expected, eh? 


This is what I'd expect if you have somehow configured gnome to control your frequency scaling.  I'd recommend turning that off if you are going to manually control it with cpufreq-selector.

> 
by the way, the last kernel update killed my wifi. i know there are active hotspots around, but nothing shows up. have you heard of a similar problem?

You'd have to make another post about this.  I only use Intel wireless so can't help.

---

### Post by robert.cooper on 2008-06-24
isn't there a way to somehow trace backwards or something? like list running modules or some shinanigans like that? i haven't even installed another scaling program like powernowd or anything other than cpu-freq. maybe a "complete reinstall" would reset any settings i fudged? i'll try that and print cpufreq-info

---

### Post by robert.cooper on 2008-06-24
completely reinstalled:
cpufreqd
cpufrequtils
libcpufreq0
75C under full load! my lap is frying and this is silly! won't it melt at some point?

cpufreq-info:
r@r-laptop:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.73 GHz and 1.73 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.73 GHz and 1.73 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.


I searched for cpu scal and gnome applets and cpufreqd are only things installed. i think this thing doesn't work from the start; i don't think something else is affecting it.

---

### Post by robert.cooper on 2008-06-24
what kind of a help forum is this :p. so i have to make a new thread (that probably won't get answered) about how to find something that i don't know where to look for or even if it exists? then suppose i find out exactly what's causing it.. then i have to make a new thread about how to adjust it? sorry for the brusqueness, but if only it were as simple as "turning it off". a flick of the switch would be nice. i would be content to rest if as a result my processor didn't melt all over me. do you have any recommendations?

---

### Post by sdennie on 2008-06-24
Try:

```

sudo cpufreq-selector -g userspace -f 1330000

```

---

### Post by robert.cooper on 2008-06-24
1330000 was what it was already. 800000 and 1733000 didn't change the value, however, if that's the information you wanted.

---

### Post by robert.cooper on 2008-06-24
thanks for trying, i guess

---

