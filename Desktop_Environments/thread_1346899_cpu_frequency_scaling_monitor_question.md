---
title: "cpu frequency scaling monitor question"
date: 2009-12-05
forum: Desktop Environments
---

### Post by expxe on 2009-12-05
in the settings, there are 4 options, conservative, on demand, performance, power save. can anyone tell me the differences between each? im switching between them, they change the CPU speed but not every setting has a change that i can see right away. is there a guide that says exactly what each does? the manual didnt say.

---

### Post by benerivo on 2009-12-05
The settings are collectively known as scaling governors. I have only breifly looked in to them, but this google search brings up pages which describe them ([http://www.google.co.uk/search?q=linux+cpu+scaling+governors&ie=UTF-8&oe=UTF-8](http://www.google.co.uk/search?q=linux+cpu+scaling+governors&ie=UTF-8&oe=UTF-8)).

I know you can also make your own setting, which involves upper/lower limts and how much the cpu steps up/down.

---

### Post by expxe on 2009-12-05
im not looking to set my own preferences (yet) but what do the ones that come default with the program do?

---

### Post by benerivo on 2009-12-05
From the arch linux wiki...```
performance (default) -- The performance governor is built into the kernel and runs the CPU(s) at maximum clock speed 
cpufreq_ondemand (recommended) -- Dynamically increases/decreases the CPU(s) clock speed based on system load 
cpufreq_conservative -- Similar to ondemand, but more conservative (clock speed changes are more graceful) 
cpufreq_powersave -- Runs the CPU at minimum speed 
cpufreq_userspace -- Manually configured clock speeds by user
```Performance governor will run the cpu at it's full Mhz rating and it will respond as quickly as possible. The others run the cpu at lower settings. On Demand is reccomended, as if the cpu is idle and you are not running any demanding processes, then it will use less power. When you start a program (such as watching a video), then it will step up the cpu to be able to do what you want (and therefore use more power).

---

### Post by expxe on 2009-12-06
i set it to conservative, what exactly do they mean by "graceful"?

---

