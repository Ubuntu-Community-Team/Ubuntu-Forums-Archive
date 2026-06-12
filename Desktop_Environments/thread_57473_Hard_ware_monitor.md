---
title: "Hard ware monitor"
date: 2005-08-16
forum: Desktop Environments
---

### Post by Owdy on 2005-08-16
Is there any good one? I wanna see cpu temp etc. Something with easy install :D

---

### Post by GreyFox503 on 2005-08-16
To see my CPU temp, fan speed, RAM usage etc. I use lm-sensors, with ksensors as a frontend (It even puts a little icon in your system tray if you want it).

In synaptic, search by "name and description" for 'lm-sensors' to see it and a couple front-ends you can use for it.  Mine wasn't too hard to get working.

What I did was run 

```
sudo sensors-detect
```

After installing it, then just 'sensors' after that to see a readout.  Then you can start ksensors or whatever other GUI you want.



If you encounter problems or want to know more, see this thread:

[http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors)

---

### Post by Lu523 on 2005-09-15
I was able to get it set up fairly easy. This is only my second day using Ubuntu. I was using MBM with Windows XP. I like the look of KSensors alot better. Thanks for the tips.

---

