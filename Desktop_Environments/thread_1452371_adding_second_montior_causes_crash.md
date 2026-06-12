---
title: "adding second montior causes crash"
date: 2010-04-11
forum: Desktop Environments
---

### Post by jeff.sadowski on 2010-04-11
I have an eeepc. I am running linux mint 8 which is from my understanding ubuntu 9.10. I am up to date on updates as of today (April 11, 2010).
With no montiors plugged in xrandr shows 2 default resolutions 1024x600, and 640x480. 

If I plugin my monitor while it is running at its default resolution (1024x600) and run "xrandr" it crashes. If I set it to 640x480 first I can get it working. My second monitor can do the following 640x480, 800x600, 1024x768, 1152x864, and 1360x768. I'd like to use scaling on my defaults screen to match the resolutions on the plugged in monitor but it seems when I do the virtual resolutions and try and match a real resolution on the plugged in monitor it stops outputting to the second monitor.
ex:
xrandr --fb 1024x768 --fbmm 1024x600 --output LVDS1 -s 1024x768 --scale 1x1.28 --panning 1024x768+0+0 --pos 0x0 --output VGA1 -s 1024x768 --same-as LVDS1

---

### Post by wilee-nilee on 2010-04-11
Have you tried the screen resolution gui in system-preferences. I am using Lucid it is now called monitors, I forget what it's called in earlier releases.

---

### Post by jeff.sadowski on 2010-04-11
> **wilee-nilee said:**
> Have you tried the screen resolution gui in system-preferences. I am using Lucid it is now called monitors, I forget what it's called in earlier releases.
It crashes as soon as I start Hardware->Display from the control center.
It appears to crash if the current resolution is not compatible with any of the resolutions that the new monitor is not capable of. If I lower the resolution first with xrandr I can then use it.

I was wondering what the best way is to get info on what is causing X11 to crash the operating system. I can't even do ctrl+alt+(F1 through F6)

---

