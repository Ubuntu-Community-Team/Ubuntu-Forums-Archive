---
title: "CPU Not At Full Speed"
date: 2009-02-06
forum: General Help
---

### Post by rizlmilk on 2009-02-06
I bought a laptop for $10. The only thing wrong with it was a broken screen so I thought I could make it into a decent desktop for a cheap price. Although the laptop was fairly new, it ran fairly slow. After checking the processor information I found out that it was running at 800 MHz. Considering the laptop was made in the last few years (and it wasn't a netbook) I found it highly unlikely that it would have such a slow processor. I found out how to find the minimum and maximum capabilities of the processor which gave me this:

cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq gives 800000
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq gives 800000
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq gives 1800000

If I'm not mistaken, this means that the cpu is currently running at 800 MHz and its full potential is 1.8 GHZ. What I would like to do is change the CPU to run at the max given from the cpuinfo_max_freq output.

I have tried using the CPU scaler in the gnome taskbar. I found a command that supposedly gives me the option to choose the frequency (sudo dpkg-reconfigure gnome-applets), but it didn't work.

I also tried a gnome taskbar add-on called gfreqlet. It shows up in the available choices to add on to my taskbar, but it doesn't actually show up when I try to add it...rendering it useless.

I also tried using gconf-editor to go to apps -> gnome-power-manager -> cpufreq. The 'cpufreq' option doesn't actually exist...I'm using 8.10 which I'm assuming doesn't have the option.

Any help would be greatly appreciated.

---

### Post by carl99fan on 2009-02-06
I would try System-Administration-Services-
and de-select CPU-Frequency manager. 
I have found that it will then run at full speed all the time.
hope that helps, worth a try.

---

### Post by rizlmilk on 2009-02-06
I tried disabling CPU-Frequency Manager from Administrative Services and it initially made the CPU-Frequency Monitor jump up to 100% but after a reboot it went back to 44% (800 MHz). I double checked and CPU-Frequency Manager is still disabled.

---

### Post by ridetheteapot on 2009-02-06
did you try turning off cpu scaling in the bios? probably is an option there.
unless scaling is broken i would think about keeping it, its a good battery saver

---

### Post by rizlmilk on 2009-02-07
> **ridetheteapot said:**
> did you try turning off cpu scaling in the bios? probably is an option there.
unless scaling is broken i would think about keeping it, its a good battery saver

I am going to use this computer as a desktop, so increasing battery life has no point when it is connected to a monitor. I have tried looking in the BIOS and it says that the processor is running at 1.8 GHz and there is no option to scale the CPU.

---

### Post by sdennie on 2009-02-07
Are you sure the scaling wasn't working right?  Frequency scaling is so fast that humans can't notice the difference between a scaling and a max speed CPU.  It's also good for the hardware as it keeps the CPU much cooler.

---

### Post by geoffrian on 2009-02-07
I've have the same problem too.  I have a netbook with a VIA C7-M 1200Mhz processor.  I've tried every suggestion in this thread and read through other resources.  This is just confusing.  I wonder if Windows has the same problem with this cpu as Linux does. --Ryan

---

### Post by rizlmilk on 2009-02-08
> **sdennie said:**
> Are you sure the scaling wasn't working right?  Frequency scaling is so fast that humans can't notice the difference between a scaling and a max speed CPU.  It's also good for the hardware as it keeps the CPU much cooler.

The problem isn't whether scaling is working properly or not, it is the fact that the CPU is being bottlenecked. I just want my computer to run at 1.8 GHz instead of 800 MHz.

And again, I don't want to max my battery life, decrease the heat of the computer, or anything like that. I just want the CPU to run at 1.8 GHz.

---

### Post by sdennie on 2009-02-08
> **rizlmilk said:**
> The problem isn't whether scaling is working properly or not, it is the fact that the CPU is being bottlenecked. I just want my computer to run at 1.8 GHz instead of 800 MHz.

And again, I don't want to max my battery life, decrease the heat of the computer, or anything like that. I just want the CPU to run at 1.8 GHz.

Try:

```

sudo cpufreq-selector -g performance

```

To verify it works use:

```

cpufreq-info

```

Not to sound like a broken record but, this won't help any "CPU bottlenecks" if the scaling ("ondemand") governor was previously working.  The only way you are likely to notice a difference with this is if you are running niced programs like SETI@Home because niced programs aren't considered when computing what the optimal CPU speed should be.

---

### Post by rizlmilk on 2009-02-24
> **sdennie said:**
> Try:

```

sudo cpufreq-selector -g performance

```

To verify it works use:

```

cpufreq-info

```



That did the trick. Thanks for the help.

---

