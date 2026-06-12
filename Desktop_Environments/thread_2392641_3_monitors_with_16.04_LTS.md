---
title: "3 monitors with 16.04 LTS"
date: 2018-05-23
forum: Desktop Environments
---

### Post by jsonfn on 2018-05-23
The default environment can detect 3 monitors after bootup. And it works fine without a problem. However I notice if unplugging and then replugging the thunderbolt, it can only detect 2 monitors. The third one connected with HDMI would have message on screen saying something like "... in power saving ...". After running`disper -d auto -e` manually in terminal, the problem still remains - 2 monitors are detected and function correctly, but the third one is blank. The docking station is TB16, connecting to monitors with DP and HDMI .  

xrandr produces output (not sure why monitors get auto detected are all DP after starting up)

```

Screen 0: minimum 8 x 8, current 5760 x 1200, maximum 16384 x 16384
eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 346mm x 194mm
   1920x1080     59.93*+
...
DP-1-2-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 527mm x 296mm
   1920x1080     60.00*+  50.00    59.94  
...
DP-1-1-2 connected 1920x1200+3840+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+
...




```

Where to check the possible causes and messages, or how to fix this? Thanks

---

### Post by Autodave on 2018-05-23
Hopefully someone else will have a better answer for you, but I have noticed the same issue on several of my machines: any monitor that is unplugged while machine is running will not be recognized when reconnected. I also have one machine that HAS to have the monitor (only one monitor connected) ON before I start the machine or it is not recognized.

---

