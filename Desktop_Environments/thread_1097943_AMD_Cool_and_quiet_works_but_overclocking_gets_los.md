---
title: "AMD Cool and quiet works but overclocking gets lost"
date: 2009-03-16
forum: Desktop Environments
---

### Post by illmatic on 2009-03-16
Hey guys,

i got the following problem:
I got my amd x² 3800 running at 2400Mhz at each core (Standart is 2000).
Now if i activate Cool and Quiet in my Bios, Linux kind of takes my Clocking down and even if the Computer has something to do and the Multiplier is at 10 the core speed is only at 2000Mhz instead of 2400.
After testing my cpu, before activating c&c and after, i had to consider that without it was quite faster.

Has anyone any idea?

Regards,
Illmatic

---

### Post by illmatic on 2009-03-17
has someony any idea?

---

### Post by illmatic on 2009-03-18
still none of you with any idea?

---

### Post by illmatic on 2009-03-18
is really none of you using cool and quiet and has overclocked his cpu ?

---

### Post by mcduck on 2009-03-18
We had a thread about this a while ago, and it seems that overclocking works just fine, even with cool&quiet enabled, but your CPU speed is reported based on the default speed the processor would have if it wasn't overclocked.

This was confirmed by running CPU-intensive performance test both with overclocked machine and non-overclocked machine (which both reported same CPU frequency while overclocked setup ran the test faster.)

In other words you probably shouldn't worry about it. Actually you really wouldn't be able to see any difference between 2GHz and 2,4GHz in any normal use, only on tasks that really need CPU power. But if you want to confirm this yourself I recommend installing Superpi and testing your setup with that. There's a thread about Superpi in the Cafe section: [http://ubuntuforums.org/showthread.php?t=60264]("http://ubuntuforums.org/showthread.php?t=60264")

(By the way, you shouldn't bump your threads too often. IF you must, max once per day. People will answer questions when they see something they can help with, bumping threads won't help anything. Actually it might prevent you from getting answers as many people search for threads with no answers, if you bump your thread it won't show as unanswered any more)

---

### Post by illmatic on 2009-03-18
> **mcduck said:**
> We had a thread about this a while ago, and it seems that overclocking works just fine, even with cool&quiet enabled, but your CPU speed is reported based on the default speed the processor would have if it wasn't overclocked.

This was confirmed by running CPU-intensive performance test both with overclocked machine and non-overclocked machine (which both reported same CPU frequency while overclocked setup ran the test faster.)

In other words you probably shouldn't worry about it. Actually you really wouldn't be able to see any difference between 2GHz and 2,4GHz in any normal use, only on tasks that really need CPU power. But if you want to confirm this yourself I recommend installing Superpi and testing your setup with that. There's a thread about Superpi in the Cafe section: [http://ubuntuforums.org/showthread.php?t=60264]("http://ubuntuforums.org/showthread.php?t=60264")

(By the way, you shouldn't bump your threads too often. IF you must, max once per day. People will answer questions when they see something they can help with, bumping threads won't help anything. Actually it might prevent you from getting answers as many people search for threads with no answers, if you bump your thread it won't show as unanswered any more)
Okay well.
In my Bios i got 240Mhz *10 -> 2400Mhz for each core
And if i boot now in ubuntu the frequency is normally 2400 too, but if I enable Cool and Quiet in the bios, the max freq is only 2000.
I tried to edit 

/etc/sysfs.conf

and add there the following

```
devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
devices/system/cpu/cpu0/cpufreq/scaling_min_freq=1000000
devices/system/cpu/cpu0/cpufreq/scaling_max_freq=2500000
devices/system/cpu/cpu1/cpufreq/scaling_governor=ondemand
devices/system/cpu/cpu1/cpufreq/scaling_min_freq=1000000
devices/system/cpu/cpu1/cpufreq/scaling_max_freq=2500000
```
But that didn't change the CPU speed
That's kind of my problem :)

---

### Post by mcduck on 2009-03-18
> **illmatic said:**
> Okay well.
In my Bios i got 240Mhz *10 -> 2400Mhz for each core
And if i boot now in ubuntu the frequency is normally 2400 too, but if I enable Cool and Quiet in the bios, the max freq is only 2000.
I tried to edit 

/etc/sysfs.conf

and add there the following

```
devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
devices/system/cpu/cpu0/cpufreq/scaling_min_freq=1000000
devices/system/cpu/cpu0/cpufreq/scaling_max_freq=2500000
devices/system/cpu/cpu1/cpufreq/scaling_governor=ondemand
devices/system/cpu/cpu1/cpufreq/scaling_min_freq=1000000
devices/system/cpu/cpu1/cpufreq/scaling_max_freq=2500000
```
But that didn't change the CPU speed
That's kind of my problem :)
Like I said, most likely ( and based on what we found out in the previous thread about this) your processor *is* running at 2400MHz, the system just reports wrong speed, as it probably doesn't poll it from the CPU but instead just calculates it based on the processor model.

So everything is working fine, just ignore the reported speed.

edit: here's a link to that thread, in case you want to read it: [http://ubuntuforums.org/showthread.php?t=1051456&highlight=superpi]("http://ubuntuforums.org/showthread.php?t=1051456&highlight=superpi")

---

### Post by illmatic on 2009-03-18
okay you're right xD
overclocked it was 30 seconds and not overclocked 35 :o

---

