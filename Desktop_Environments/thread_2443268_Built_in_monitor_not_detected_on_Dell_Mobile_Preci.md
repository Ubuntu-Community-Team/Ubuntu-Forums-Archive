---
title: "Built in monitor not detected on Dell Mobile Precision 7740 ubuntu 20.04"
date: 2020-05-13
forum: Desktop Environments
---

### Post by pha3drus2 on 2020-05-13
Just did a clean install of 20.04 on my Dell Precision 7740. After install it worked perfectly for a while. Then suddenly booting does not seem to get past the Dell logo, along with the Ubuntu logo and the spinner. 
I connected the laptop to my external HP monitor and all of the sudden everything worked again. Booting today I notice my external HP monitor still works, but the main display of the laptop is not detected (the built in monitor does not show up in the monitor section of settings). The built-in display stays at the splash screen with the Dell and Ubuntu logo and the spinner. 
I've tried the following things:

[LIST]
[*]Reverting from Nvidia driver 440 to 435
[*]Switching graphics cards to sudo prime-select intel and then back again to sudo prime-select nvidia
[*]Every advice from this thread: [Ubuntu 20.04 does not recognize second monitor]("https://askubuntu.com/questions/1230924/ubuntu-20-04-does-not-recognize-second-monitor")
[/LIST]
Any help or pointers is greatly appreciated. Below is my output of xrandr when the primary screen isn't working. If any other logging output is necessary, please let me know.


```
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+  74.94  
   1920x1080     60.00    59.94    50.00    23.98  
   1680x1050     59.95  
   1600x1200     60.00  
   1600x900      60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)

```

---

### Post by pha3drus2 on 2020-05-21
An update from my side. The issue appears to be intermittent and almost seems time-based or clock-related. Note that this machine dual boots with Windows 10, which does not have the issue at all, ruling out hardware issues like a bad connector to the screen etc. When I boot my machine early in the morning, both screens are available. Booting in the evening mostly results in the default screen not detected. I'm not sure about any of this and it's all anecdotal. Any advice or pointer where to look would be greatly appreciated.

---

