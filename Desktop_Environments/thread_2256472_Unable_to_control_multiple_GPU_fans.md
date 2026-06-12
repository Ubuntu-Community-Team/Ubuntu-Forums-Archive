---
title: "Unable to control multiple GPU fans"
date: 2014-12-12
forum: Desktop Environments
---

### Post by Ryan_Carr on 2014-12-12
I have 3 graphics cards installing into my computer. 2 670 with SLI cable connected and 1 550ti. At the current moment, I have driver version 340.65 and able to control only one GPU fan.

I have used the following the commands so far

```
sudo nvidia-settings -a GPUFanControlState=1
sudo nvidia-settings -a [fan:0]/GPUCurrentFanSpeed=70
```

I am able to see a fan control on GPU:0 but done of the others. Picture below

[IMG]http://i.imgur.com/YaIp2W0.png[/IMG]

---

