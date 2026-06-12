---
title: "Ubuntu 12.04 x64 - Dual Monitor Malfunctioning"
date: 2012-07-03
forum: Desktop Environments
---

### Post by Thesord on 2012-07-03
I've recently done a clean install of this version of Ubuntu and my dual-monitor setup stopped working (it worked in a previous version, 11.04 I believe... And also works fine in Windows 7 x64, so it is not a hardware issue). I have a single GPU (NVIDIA 8800GTX), and both monitors are connected to it via DVI. My current drivers are the option "NVIDIA accelerated graphics driver (post-release updates) (version current-updates)".

After tweaking around, I managed to get the second monitor to display the background image instead of just a plain white image. I can hover the mouse cursor correctly from the main monitor to the secondary one (the monitors are both the same model in this desktop setup), but I'm unable to use the real estate provided by the second monitor to keep applications open or drag any window to the second monitor.

To obtain this, I configured the NVIDIA settings to have an individual profile per monitor. One has absolute coordinates at offset +0+0 and the other one is configured relatively to the other (using a "Left/Right Of" option).

Would anyone here be able to tell me what do I need to do to have a propper dual-monitor desktop setup? This would be simmilar to what you get in Windows 7 when you configure it to extend the desktop, effectively (for my case) doubling the available width.

I thank you for your time, and cast my best wishes to the development teams!

---

### Post by msammels on 2012-07-03
It all depends on your monitor. The easiest way you can try is first of all make sure your system is up to date with:

```
sudo apt-get update
```

Next, you would want to make sure that the restricted drivers for your nVidia graphics card are on and up to date (this will be so if you are using Ubuntu 12.04).

The first way you can try to fix the monitor section is by using the built in display control panel. You can find it in system settings under displays.

Once you have arranged the monitors how you like, click the one that's not working, and turn it off in the control panel and back on. Also - make sure the resolution you use on it is not too high.

I'm not strong when it comes to nvidia-settings, however as far as I remember the absolute offset coordinates need to be the pixel length of your first monitor. Example:

```
Monitor 1: 1920x1200, offset+0+0
Monitor 2: 1920x1200, offset+1920+0
```

But again, I'm not sure, so please don't quote me on that one - I don't want to damage your system!

---

### Post by Thesord on 2012-07-03
I forgot to mention, but the Display entry in System Settings only recognizes one monitor, and strangely calls it "Laptop" for some reason. Only the NVIDIA settings recognize both monitors. Yeah I took care with that detail being the amount of pixels of the other...

I've made sure it is up to date, and the current restricted drivers I'm using is, as stated in the option's description, the latest one, not just the one that came with 12.04. I had to do this because I was having some bug where the system interface was completelly sluggish (both windows and Unity)

---

### Post by msammels on 2012-07-03
Oh yeah - my only monitor is called "Laptop" for some reason well... bizarre stuff. So as I understand it, you're using the nVidia drivers from the website... or are you using the noveau drivers? Because depending on which you're using, there is a major difference in support.

---

### Post by etricks on 2012-07-15
Any update?  I am having the exact same issue...

---

