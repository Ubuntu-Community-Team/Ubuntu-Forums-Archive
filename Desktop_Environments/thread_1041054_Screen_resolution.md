---
title: "Screen resolution"
date: 2009-01-16
forum: Desktop Environments
---

### Post by simonlugi on 2009-01-16
I have been running Ubuntu 8.40 for months with no hassle. Couple of days ago as I booted up the system which did a driver check and threw up some odd comments. dont ask what they were but I had to CNTR+D to go back to GRUB and then restart which went back into driver check, back to CNT+D etc. 

When I  ESC to skip drive check and my desktop resolution will was all incorrect. My NVIDIA driver was gone.
I got the NVIDIA enabled but it still doesnt allow me the correct resolution 1440 x 900. I have had to settle for the closest 1280 x 800. 
Can anyone help

---

### Post by ajgreeny on 2009-01-16
I would bet on this being a kernel update which came a few days ago, and requires you to reinstall your nvidia driver.  You say you have enabled this, but not whether you reinstalled it through System- Administration-Hardware Drivers, which is what is probably needed.  If you did this already, I don't know what else to suggest.

---

### Post by simonlugi on 2009-01-16
I have been in Hardware drivers and NVIDIA is enabled and the green dot is on saying it in use.Not sure if there is anything eklse I am supposed to do?

---

### Post by oaqster on 2009-01-16
try using EnvyNG it's suppose to detect, download & install the appropriate driver for your GPU.  supports ATI & NVIDIA cards.
I kindof had this issue when I initially installed my card (GeForce4 MX 4000), nothing worked for me, the default ubuntu "nv" driver as well as a number of drivers from nvidia's web site gave me various issues.  EnvyNG was my happy ending.
hope this helps
- oaqster

---

### Post by FIONEX on 2009-01-16
Hey man, look into editing /etc/X11/xorg.conf manually to change the resolution to what you want.  Sometimes I find GUI to limit what you can do...  Paste your /etc/X11/xorg.conf in here so we can see what's up.

---

### Post by simonlugi on 2009-01-17
Thanks everyone for suggestions.  i tried the EnvyNG option which made matters worse. could only get 800 x 600 res. unfortunately got me on a bad day and I really didnt want to spend half my day trying this and that. I loaded fedora 10 and so far its actaully amazed me how well it works and easy getting video and mp3 etc running. 
I believe that ajgreeny comment that it has something to do with a kernel upgrade is correct. As a non computer person I really cannot understand how an upgrade can actually makes things get worse. Seems to me that upgrading the kernel is not always a good thing.
Thanks again

---

