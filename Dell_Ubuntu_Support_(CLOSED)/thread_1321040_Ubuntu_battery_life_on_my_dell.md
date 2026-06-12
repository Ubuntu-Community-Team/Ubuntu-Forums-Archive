---
title: "Ubuntu battery life on my dell"
date: 2009-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nihonbun on 2009-11-09
I dual boot Windows and Ubuntu 9.10.  I use a Dell 1545 with a 9 cell battery.  Normally, I'm able to get around 8 hours gaged on my battery life running from vista, but only just over 4 hours on Karmic, in laptop mode, with the screen brightness turned all the way down.  I run powertop to put things down, but it still eats up my battery like a sumo at a buffet.  Is there anything I can do to make it compare at all to Vista's battery life?

---

### Post by TheHolm on 2009-11-09
> **nihonbun said:**
> I dual boot Windows and Ubuntu 9.10.  I use a Dell 1545 with a 9 cell battery.  Normally, I'm able to get around 8 hours gaged on my battery life running from vista, but only just over 4 hours on Karmic, in laptop mode, with the screen brightness turned all the way down.  I run powertop to put things down, but it still eats up my battery like a sumo at a buffet.  Is there anything I can do to make it compare at all to Vista's battery life?

Just check CPU speed and usage on idle PC. "CPU Frequency Scaling Monitor" applet and "top"  can do it for you. If you see that CPU not running on lowest speed and utilisation is above 20%. Than you probably got some problem with power management in your system. 

I have run "Watch movie till battery fully discharged" tests on my XPS 16. I got about 45 min longer battery life under Ubuntu 9.10 - 64 than VIsta Home 64. I used mplayer under both OS-es.

---

### Post by nihonbun on 2009-11-11
> **TheHolm said:**
> Just check CPU speed and usage on idle PC. "CPU Frequency Scaling Monitor" applet and "top"  can do it for you. If you see that CPU not running on lowest speed and utilisation is above 20%. Than you probably got some problem with power management in your system. 
So, on my 2.1 GHz processor, I can only scale it down to 1.20 GHz, which is 57%.  Is that what you're talking about, or do I need to do something more to scale things down?

---

### Post by TheHolm on 2009-11-12
1.20 GHz minimal speed is bit high. 
I assume that you laptop build on Intel T4300 CPU? Is it right? 
2.56GHz CPU in my laptop can be scaled down to 800Mz.

Just open terminal and run ```
top
```. It will show you CPU usage of all running processes. On idle system CPU usage should be well bellow 20%.

---

### Post by mikewhatever on 2009-11-12
nihonbun, let's take a look at you CPU specs. Can you post the output of 

```
cat /proc/cpuinfo
```.

---

