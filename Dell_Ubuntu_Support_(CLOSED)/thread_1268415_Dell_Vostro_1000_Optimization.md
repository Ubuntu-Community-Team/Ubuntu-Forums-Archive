---
title: "Dell Vostro 1000 Optimization"
date: 2009-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by walesmd on 2009-09-16
I installed Xubuntu on my Dell Vostro 1000 approximately 3 months ago, primarily for the performance gains. The laptop came with Vista, I don't need to explain any more and XP wasn't much better.

I know this laptop isn't the best thing in the world but even now, on Xubuntu, I'm just not seeing the performance I would expect. The laptop is now at 9.04.

Below is a copy/paste of the free command after a fresh reboot:
```

             total       used       free     shared    buffers     cached
Mem:        433268     402044      31224          0      12560     144944
-/+ buffers/cache:     244540     188728
Swap:      1293192          0    1293192

```

---

### Post by Boondoklife on 2009-09-16
Well are you looking for more horsepower or more battery life, if it is the later then try the command: sudo powertop
It will give you recommendations on how to lower your power usage.

---

### Post by walesmd on 2009-09-16
Battery life is a non-issue - not worried at all about that. Trying to get more horsepower out of it I guess - minimizing the system down to as little as possible.

I just find it odd that this system is taking 10-12 seconds to launch a Terminal - that shouldn't be the case. Unfortunataly, I don't know enough to work the optimization myself.

---

### Post by Boondoklife on 2009-09-16
well I would start by taking a look at what all you have running, try ps -Al

This will give you a list of the apps running and you can try to identify any apps you dont want running and try to kill them. Ya might want to write down the apps you kill to see if you need to disable them from the startup applications.

Becareful with disabling startup apps though, make sure you know what you are disabling!

---

