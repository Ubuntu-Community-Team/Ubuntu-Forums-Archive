---
title: "Latitude D620 CPU Frequency Scaling issues"
date: 2008-03-14
forum: Dell  Ubuntu Support
---

### Post by tonybaloney on 2008-03-14
I'm having trouble getting my CPU (a Core Duo) to set frequency scaling correctly. Basically, it's stuck at the lowest setting (1.0GHz) no matter which governor I choose. Even if I set the frequency manually, it remains at 1.0GHz. I've tried both the gnome panel applet and using cpufreq-set from cpufreqtools.

The following output from cpufreq-info gave me a clue as to what it might be but I don't really know how to proceed. I did try changing the number contained in the file scaling_max_freq in /sys/devices/system/cpu/cpu0/cpufreq as well as the one in /sys/devices/system/cpu/cpu1/cpufreq to 1833000, which I think is the correct number based on the scaling_available_frequencies file in the same directory. The computer appears to ignore the change since the CPU speed doesn't change and the contents of the file reset to the old value of 1000000 (which I assume to mean 1.0GHz) 

```

tony@Aristotle:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 1.83 GHz
  available frequency steps: 1.83 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, powersave, userspace, performance
  current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 1.83 GHz
  available frequency steps: 1.83 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, powersave, userspace, performance
  current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
tony@Aristotle:~$  

```

---

### Post by tonybaloney on 2008-03-14
Okay, it seems that the Ondemand governor works just fine when I start up the computer. In fact it works perfectly until I change the governor to anything else. Conservative is a favorite of mine when I'm on battery. Scaling doesn't work and cpufreq-info gives pretty much the same as above. Also the "performance" governor, which I use for compiles, photo editing and the like, causes this to occur, as you can see from the above snippet.

If people need more info, I'd be happy to post it. I didn't see anything suspicious in dmesg though I could have missed something. 

Thanks in advance :)

---

### Post by theproc64 on 2008-03-14
I don't have any solution to this problem but I have the same problem with my d620.  It seems whenever I am doing something processor intensive it gets stuck at 1ghz.  I just stopped using it.

---

### Post by valep on 2008-03-16
hello

i also have the d620 and the scaling is working fine here. I am managing it from the scaling monitor applet.

Do you have the powernowd installed?

---

### Post by tonybaloney on 2008-03-20
Yes, I have the Gnome scaling applet installed, along with powernowd. In fact, I first noticed this annoying problem using the panel applet to try to change the CPU speed. I was able to change which governor I was using and set the CPU speed by hand using the userspace governor with the panel applet and it was working quite well until about a month ago.
It stopped working (I think) after a round of updates. After noticing my system becoming sluggish and CPU scaling not working, I decided to install cpufrequtils to see what was going on in addition to checking the files in the appropriate /sys folders.

---

### Post by valep on 2008-03-23
It sounds like a kernel related update.

I found this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132271") in launchpad, maybe it helps.

I just upgraded to hardy(8.04) beta, with kernel 2.6.24-12 generic, and scaling works fine.

---

### Post by tonybaloney on 2008-03-30
Okay, this issue has been fixed, though not without a lot of difficulty. It turns out that my laptop has a hardware problem and Dell is replacing the entire system board and CPU. I noticed it when I booted back into Windows to run MS Office to open up documents that Openoffice couldn't handle. It was also slow in Windows! I checked the CPU speed in Windows and it was also at 1 GHz instead of the 1.83GHz. So, I called Dell and they ended up diagnosing it as needing a full system board replacement. Now, it's fixed only because I had to bring it to a place that does Dell warranty work and they kept it for a few days. Works great now!

---

