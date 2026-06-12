---
title: "cpu freq scaling"
date: 2006-08-18
forum: Desktop Environments
---

### Post by clickwir on 2006-08-18
There was a recent post on digg.com about getting better performance out of linux on a laptop. It also gave some specifics on Ubuntu. However, my Kubuntu already seems to have this done. I think.

[http://martin.ankerl.org/2006/08/16/how-to-make-firefox-40-percent-faster/](http://martin.ankerl.org/2006/08/16/how-to-make-firefox-40-percent-faster/)
and
[http://dietrich.wordpress.com/2006/06/22/ubuntu-ondemand-cpu-frequency/](http://dietrich.wordpress.com/2006/06/22/ubuntu-ondemand-cpu-frequency/)

I read through both of these before even attempting anything. I find it quite interesting that there might be something already there that might get me some better performance and possibly battery life.

However, I started checking a few of the things they said to set. Such as setting echo "ondemand" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

However, I just cat that and it's already set to ondemand. I checked out another file in that same directory, I think it was something to the effect of cpu_avaliable_govenors and in there it listed several different ones, including powernowd, ondemand, powersave, performance and something else too. 

So, I guess what I'm looking for is some more info. I like having the option in my GUI to be able to right click on the plug/battery and select Dynamic, Performance, and Powersave. Yet using powernowd, according to these sites, is not beneficial. I guess I want to know if it's ever using powernowd or not. If it's not then I guess there's no point really, but if it is switching between powernowd and ondemand, ondemand sounds like it would be the prefered option. 

BTW I'm using Ubuntu 6.06 with KDE/Kubuntu theme on an Acer Aspire 3004WLCi laptop with an AMD Sempron 3100+.

---

### Post by sunitram on 2006-08-19
> **clickwir said:**
> However, I just cat that and it's already set to ondemand.

If this is already on ondemand, then you do not need to do anything. If powernowd is running you can safely remove it. Only when your current governor is "userspace", tools like powernowd work. Otherwise the kernel module takes over the scaling functionality.

> So, I guess what I'm looking for is some more info. I like having the option in my GUI to be able to right click on the plug/battery and select Dynamic, Performance, and Powersave.

klaptop has a nice GUI for the governor settings, there you can choose the ondemand governor per default (if the module is loaded).

---

