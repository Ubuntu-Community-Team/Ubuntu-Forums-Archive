---
title: "External Monitor issue...Dell 14z"
date: 2012-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hogfan on 2012-11-01
Hello, this is not Ubuntu specific, but Linux Mint 13 is Ubuntu-based and this is a Dell machine, so I thought some here might be able to assist better than on the Linux Mint forum.  I have posted this over there as well:


I am loving Linux Mint 13 on my Dell 1400z laptop but have a couple of minor issues I'd like to resolve regarding my external display. I am also using the Jupiter applet for power management and that is working great. I am running Mint 13 with the Cinnamon desktop. I am able to easily mirror to my external display, extend my desktop to the external display, and use the external display only (internal display is off). I have had to temporarily disable my "Turn off monitor" after x mins in Mint because once the display goes to sleep I am unable to bring it back by moving the mouse on my Mint machine (Mint machine is connected to HDMI on my external monitor). My Mac machine is connected the DVI port on same external monitor (different input). If I move the mouse for the Mac, the monitor wakes up and then I can just toggle the input back over to the Mint machine and I'm at the desktop/lockscreen. When I attempt to wake up the monitor from the Mint machine, the display shows a no video signal message. Any suggestions of a fix for this so that I can wake the Acer 23" monitor from the Mint machine?

Question 2: 

If I set the Video mode on the Mint laptop to external display only, and don't change the setting back before unplugging from the external monitor, it never defaults back to the laptop LCD when the external monitor is disconnected. The only way to get video back to the laptop display is to plug the laptop back into the external display and change the setting back there. This could be bad if I took the laptop with me somewhere and did not have an external display to connect to. How can I make mint default back to the primary display if no external display is detected? Thanks for any suggestions.

-hogfan

---

### Post by hogfan on 2012-11-01
I ran across this thread scouring the web and apparently Jupiter saves the current display settings and automatically reloads them on reboot.

[http://askubuntu.com/questions/102356/external-monitor-set-as-primary-even-when-disconnected-from-laptop](http://askubuntu.com/questions/102356/external-monitor-set-as-primary-even-when-disconnected-from-laptop)

So that appears to be part of the problem. I guess there is no good way for this to be handled automatically.  I want my internal display to be off when the external monitor is connected, and automatically back on as the primary when the external is disconnected. 

Would it be possible to write a bash script to run on startup that could check if an external display was connected to the HDMI port on the laptop?  

I'm still digging into my second question but no good info yet.

-hogfan

---

