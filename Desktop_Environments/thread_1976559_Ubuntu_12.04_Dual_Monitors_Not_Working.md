---
title: "Ubuntu 12.04 Dual Monitors Not Working"
date: 2012-05-08
forum: Desktop Environments
---

### Post by N00b4Now on 2012-05-08
Hello All,
  It is my first posting, please let me know what I can do to improve my presentation skill.
 

  My issue is getting Dual Monitor working under Ubuntu 12.04.  I have just upgraded to the AMD Video Driver for Ubuntu (amd-driver-installer-12-4-x86.x86_64) and when I tried to have Multi Desktop setup with two monitors, the 2nd monitor shows a white screen with black X as the cursor.
 

  Would you please helping me solving this issue?

  Please find the attached xorg.conf for my current duo monitor setup.
 

   Thank you very much for your help,
 

 Noob4Now

---

### Post by cortman on 2012-05-08
Hi, what's the output of 

```
xrandr
```

with the second monitor plugged in?

---

### Post by N00b4Now on 2012-05-09
Hello Cortman,
  The output of xrandr is the following:
*********************************************************************************************
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       75.0     60.0  
   1152x864       60.0     75.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)
********************************************************************************
  
  The 2nd LCD monitor is showing white screen with black cursor when I did xrandr.

  Thank you for your time,

N00b4Now

---

### Post by cortman on 2012-05-09
Have you been setting the dual monitors with the Catalyst Control center?
If so, and it still isn't working, you may want to try the open source driver instead- I quote- 

> This driver is not as fast as the closed-source, proprietary "fglrx" driver from AMD/ATI Inc. for some cards, but has better dual-head support, and supports some older chipsets that fglrx does not.

See [here]("https://help.ubuntu.com/community/RadeonDriver") for open source driver details.

---

### Post by scottbomb on 2012-05-09
This might also help:


[http://ubuntuforums.org/showthread.php?t=1965529](http://ubuntuforums.org/showthread.php?t=1965529)

---

### Post by N00b4Now on 2012-05-09
Thank you all for the quick responses.  I tried all the suggestion and no resolution.

I ended up enabling the CrossFireX functionality of the GPUs and Enable Tear Free Desktop to make the dual monitor work.

In Windows 7, I usually don't activate CrossFireX when I am not gaming and the old habit does not work in Ubuntu 12.04.

Now all is well, I learn something new today.  

Thank you again for your help and have a nice day.

N00b4Now.

---

### Post by houston schmitt on 2013-03-08
This worked for me (after 12.04 Ubuntu install) and may be a simpler solution.  The install had found an ATI/AMD proprietary FGKRX graphics driver and installed it.  When I deactivated it (system settings...hardware...additional drivers) , I was able to get the dual displays to work through the Displays program.  It appears that the generic driver for 12.04 works just fine and the proprietary driver does drive dual monitors correctly. 

(Caveat: I am not a linux expert)

---

