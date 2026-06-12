---
title: "A Problem using External Monitor with X"
date: 2010-02-20
forum: Desktop Environments
---

### Post by Roinator on 2010-02-20
I should start by saying this isn't really an Ubuntu problem.  It is a problem with X I believe.  I am using a laptop with a broken partialy broken display.  So, I don't use the built in screen on the laptop.  I just hook it up to my external monitor.  X seems to size itself properly, but something ( I don't really know what) is a little off, because I get these moving horizontal lines up and down my display.  It looks like I have a bad connection with my VGA or something, but I know that's not the problem.

In ubuntu I can stop this odd effect by turning on my normal monitor, so I am using both screens.  So, I know it's not a hardware problem, because If I use both screens then it works fine.  It's just when I go to a single external monitor that the problem occurs.  I've also had this problem with Arch linux.  So, it's not a gnome or ubuntu specific problem.  I am quite confident it is X.  So, can anyone help? I'll post my Xorg.conf.  Any info would be great.

---

### Post by efflandt on 2010-02-21
/var/log/Xorg.0.conf should show whatever resolutions X can gather from EDID of the monitor, and why it may not think it can use some (even if they may work).

When you boot a laptop with external connected X initially tries to match up a common resolution for both displays, which in my case for 1280x800 laptop screen is 1024x768 regardless of higher resolution external VGA display.

If you are switching resolution after you disable the laptop display, that may be your issue, because it may not have optimum timings for that resolution.  Even though the kernel uses a perfect 720p resolution for the external display when I boot, if I select 1280x720 in X Display Preferences even with laptop display off, the HDTV image is overscanned off screen.  I have since determined that the best resolution for that supposedly 1366x768 LCD is 1360x765 in X (WinXP calls it 1360x764).  I used **cvt 1360 765 **to find a modeline and **xrandr** in a script to set and switch to that mode (and turn off laptop display).

But cvt does not necessarily come up with a perfect mode.  For a 1080p display I had to get a proper modeline from Xorg.0.log of a DVI to HDMI connected desktop, because cvt 1920 1080 on the laptop came up with a mode that was way off in horizontal timing (off center pillar boxed).

Is your monitor CRT, LCD, or other?  What is its native resolution and do you have specs about refresh or sync rates?  Maybe it  works, but you are using a mode that stresses it.

---

