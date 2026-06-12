---
title: "Low performance on Dell M1210"
date: 2007-09-26
forum: Dell  Ubuntu Support
---

### Post by thunderwing on 2007-09-26
I've installed (fresh) Ubuntu 7.04 on my Dell M1210 with the following hardware

Centrino Core 2 duo 2.0Ghz
2g ddr2
Nvidia go7400 (pci-e)

I'm experiencing less the impressive performance results when comparing to older systems with lower specs.

I am currently running the most recent Nvidia drivers (after testing for the bottom up) 

glxgears give me the following results

11707 frames in 5.0 seconds = 2341.075 FPS
11748 frames in 5.0 seconds = 2349.447 FPS
11734 frames in 5.0 seconds = 2346.793 FPS
11660 frames in 5.0 seconds = 2331.755 FPS

which i find slow when comparing to other systems running lower end gfx cards obtaining in the 10000 FPS range

i'm also experiencing slow load times on simple applications like the terminal or network manager.

attached is a copy or my xorg.conf which was configured by the newest nvidia drivers

any suggestion on increasing performance would be apreciated.

---

### Post by irwjager on 2007-09-26
Hey,

Might be worthwhile checking whether your CPU frequency is throttling alright. I've had problems on a Dell M90 which would stay at 1Ghz, no matter what the load was.

You could install cpufrequtils

```
sudo apt-get install cpufrequtils
```

Then use cpufreq-info and cpufreq-set to see what's going on and maybe correct it.

Hope this helps,

Ivo

---

### Post by thunderwing on 2007-09-26
thanks for your quick reply,

I've already written a pair of scripts that run when the AC is plugged or unplugged that set the cpu to either performance or on demand.  I try to stay aware of my freq and my load with applets in my bottom panel .

---

### Post by thunderwing on 2007-10-01
bump (fell to the third page)

---

