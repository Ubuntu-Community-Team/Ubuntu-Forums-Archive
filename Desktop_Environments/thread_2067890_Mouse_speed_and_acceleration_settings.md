---
title: "Mouse speed and acceleration settings"
date: 2012-10-07
forum: Desktop Environments
---

### Post by 1234blizzard on 2012-10-07
Hello, so I was trying to configure my mouse settings in Ubuntu 12.04 with my Microsoft Notebook Laser Mouse 7000. The mouse works fine but I really do not like the acceleration. 

However, whenever I turn off acceleration, the mouse moves at an incredibly low speed. The two setting called acceleration and sensitivity do not seem to do anything. 

I believe the terms acceleration and speed are terms used with Windows 7 but I can't find how to change these. Basically I just want 1:1 distance mouse moved to distance moved on screen.

Thanks!

---

### Post by 1234blizzard on 2012-10-15
I have figured out a solution myself. I simply used the xset command to increase the acceleration and lower the acceleration threshold. 

xset -q | grep accel

This command tells you your current mouse settings.

xset m 2 1

This command can be used to increase the acceleration and the acceleration threshold.

---

