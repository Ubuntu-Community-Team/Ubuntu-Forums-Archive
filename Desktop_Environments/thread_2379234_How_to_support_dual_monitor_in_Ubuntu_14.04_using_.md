---
title: "How to support dual monitor in Ubuntu 14.04 using single Intel HD graphics"
date: 2017-12-02
forum: Desktop Environments
---

### Post by myownxanadu on 2017-12-02
Hi, I am new to Linux and have a problem with dual monitor setup using an integral graphics card by Intel.

1. Software and hardware environment
CPU: i7-8700K with Intel HD 630
OS: Ubuntu 14.04.5
Motherboard: Asus Z370-e
2 monitors: connected to the I/O of motherboard via HDMI and DVI respectively.

2. Problems
Both of the monitors have output signal but they are just mirror to each other, not the extension that I wanted.
I found some tips suggesting using xrandr to fix the problem. But when I try either 'xrandr' or 'sudo xrandr', I got a error as follows,
   xrandr: Failed to get size of gamma for output default
   Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
   default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080      77.0*

 3. Object:
Support dual monitor setup where the second monitor is an extension to the first, not duplicate.

Thanks for looking!

---

### Post by mörgæs on 2017-12-04
Hi, welcome to the fora.

Your processor is the latest generation, that is at most half a year old. 
Most of your 14.04 software is three and a half years old though parts of it is newer. 

How should the developers back in 2014 be able to write software supporting future processors?

Your best option is a fresh install of 17.10, maybe even jump onto 18.04 a little before the official release. Post again if you still have problems here.

---

### Post by deadflowr on 2017-12-04
Displays doesn't you give an option to disable mirroring?
(System Settings >> Displays)

---

