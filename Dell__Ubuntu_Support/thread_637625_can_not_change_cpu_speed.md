---
title: "can not change cpu speed"
date: 2007-12-11
forum: Dell  Ubuntu Support
---

### Post by mahmoodn on 2007-12-11
Hi,
I run ubuntu on inspiron 510m, but I can not manually change cpu speed. what should I do?

---

### Post by saru411 on 2007-12-11
you can not manually change the speed because its a dell. dells arent overclocking boards. if you are using a laptop overclocking is rather dangerous. laptop cpus are not ment to be overclocked. if its a desktop your problem is that you have a dell motherboard

---

### Post by mahmoodn on 2007-12-12
It is laptop. I can change the speed in windows via "speedswitchxp" and fedora 5. I wonder why I can not change it in gutsy???!!

---

### Post by timseal on 2007-12-12
What did you try?
If you did not already, try
```
sudo cpufreq-selector -c 0 -g performance
```
and do a man cpufreq-selector to find out more.

Alternatively, try this:
```
sudo dpkg-reconfigure gnome-applets
```
and answer Yes to the question about installing cpufreq-selector with SUID root.

Then, add the CPU frequency scaling applet to the Gnome panel.  You should be able to change it from there.

-tka

---

### Post by mahmoodn on 2007-12-13
thanks for these packages. I can now change cpu speed manually

---

### Post by Littl3King on 2007-12-15
I performed the alternative as timseal instructed... it worked fine... but how would i get that to load on startup... i know the applet will load but when i reboot it always says CPU Frequency Unsupported type message.  Then i have to enter these commands manually for it to work.  Take note that i DO have these commands in my sessions:

modprobe p4-clockmod
--and
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

Now given all of that is there a way i could autoload these commands when i start the GUI ?
--When i do run these manually i have to restart my x-server for the dropdown on the applet to work... the dropdown being the frequency choices.   

Any help at all would be appreciated.  OH BTW this is where i got my Info from :

[http://xlife.zuavra.net/index.php/70/](http://xlife.zuavra.net/index.php/70/)


[B][U]1.  Load those commands on startup w/o having to restart the x-server.  
2.  How to bypass or enable su on startup to run these commands or add commands to root user. 
 :) :) [/U][/B]
Thanks for your help community.

---

