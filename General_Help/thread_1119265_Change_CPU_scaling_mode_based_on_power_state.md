---
title: "Change CPU scaling mode based on power state"
date: 2009-04-07
forum: General Help
---

### Post by Dj Dutchman on 2009-04-07
I have installed the CPU Frequency Scaling monitor for the Intrepid install on my laptop and I see that I can change the scaling from Powersave to Performance (with Ondemand and Conservative in between). I was just wondering if it was possible to write a script or something that would set the scaling to Ondemand when the AC power is plugged in, Conservative, when running off the battery and Powersave, when the battery is running low? Just an idea...

---

### Post by sdennie on 2009-04-07
You can but, I don't advise it.  Modern CPUs can switch frequencies so quickly that you can't notice the difference between performance and ondemand (except that your machine will be MUCH hotter with performance).  They also do it so quickly that, under most loads, you will save more power using ondemand than powersave because CPU power savings is a combination of frequency (P-State) and sleep state (C-State).  Deeper sleeper states save more power than slower frequency states so, you are best doing something called, "race to idle" (Go fast so you can get back to sleep quicker).  That's the ondemand governor.

However, a HOWTO/template that does what you are asking can be found here: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773").  It also contains links and tips for how to save power.

---

### Post by Dj Dutchman on 2009-04-07
Thanks for the link. I don't know if I made myself completely clear but the general outline was, AC Power: Ondemand, Battery Power: Conservative and Low Battery: Powersave (the Performance mode was never in the design). Thanks again though...

[EDIT]
I see what you mean with the race-to-idle mentality
[/EDIT]

---

### Post by sdennie on 2009-04-07
> **Dj Dutchman said:**
> Thanks for the link. I don't know if I made myself completely clear but the general outline was, AC Power: Ondemand, Battery Power: Conservative and Low Battery: Powersave (the Performance mode was never in the design). Thanks again though...

Even dropping performance mode, I still don't recommend that.  There are very few loads where ondemand is not the optimal governor for modern processors.  The only two I can think of are:

1) On AC power: You are running a CPU bound application in the background that automatically nices itself (for example, SETI@Home).  In which case, it doesn't cause the ondemand governor to reach max frequency even when the system is idle because it's CPU usage isn't considered when deciding frequency speed.  In that case, yes, the performance governor makes more sense than the ondemand governor.

2) On Battery: You are running a CPU bound application and you know it's going to prevent the CPU from reaching deep C-States but the lowest frequency is fine (for example a game where the FPS is acceptable at the lowest P-State).  In that case, yes, the powersave governor makes more sense than the ondemand governor.

For fairly modern CPUs, I can't think of a single other case where you'd want to use anything but ondemand.  The powersave/conservative/ondemand/performance names are legacy names for when they made a different and when CPUs didn't have C-States.  It's very misleading today.

---

### Post by Dj Dutchman on 2009-04-08
Ok, thanks for explaining it all to me, I actually realized that I knew very little about this stuff...

---

