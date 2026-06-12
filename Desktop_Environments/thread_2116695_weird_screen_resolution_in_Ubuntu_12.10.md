---
title: "weird screen resolution in Ubuntu 12.10"
date: 2013-02-16
forum: Desktop Environments
---

### Post by psychowants2bgeek on 2013-02-16
I have Dell 7520 with AMD Raedon graphics card, thankfully, I got to make it work. But the problem now is screen resolution, as I have screen resolution of 1920 X 1080 for 15.6" laptop, which is way too much. In the Display Monitor settings, I cannot change it to whatever I want, only the resolution with 16:9 works perfectly.  I have options for other resolution setting but, selecting others brings the screen edges near, that means it leaves gap on both sides of screens. And to read contents from such high resolution is too small, as I need magnifying glass. 

I have other suitable 16:9 resolution as 1360 X 768 but thats too big. I want something like 1600 X 1024 which would be good resolution for me. But when I change that via Display Monitor settings, again the edge becomes narrow.

I don't have the option of widening the layout from keyboard shortcuts too, if there is any way to fix this then it'd be very great...

---

### Post by temporos on 2013-02-16
I've had the same experience, of starting my computer up and watching as the display gives itself a *really* strange (i.e., uncommonly or never used by me) resolution.

In my situation, I know what is causing the issue, so it is easy (yet annoying) to fix.  I have Ubuntu 12.04 LTS installed using LXDE on an old ASUS netbook, and I'm using a VGA cable to connect my HDTV to use as a primary display.  For some reason, this confuses the graphics card (an integrated Intel 945GM), and resolutions of both the TV and the attached display are set to 800x600.  Since they're different physical sizes, it looks *really* strange and distorted.

What I do to fix this is go into Preferences > Monitor Settings, and I disable the XVGA port (but I leave the DVI Monitor active).  Log out, log back in, and then re-enable the XVGA port, and it seems to work perfectly, allowing me to set whichever resolution I wish.

Your graphics card might mistakenly believe that you have a secondary display attached, and it can't figure out what kind it is, because there's not really one there.  Try disabling all graphics ports that you are not using, and see what happens.

---

### Post by ohrus on 2013-02-19
Hi psychowants2bgeek, while I don't have an answer to your question, I was hoping you might shed some light on how you got your radeon card working with the dell 7520?  This has been an ongoing issue for many owners of this laptop and I'm curious if you in fact have both cards working (switchable) and if so what drivers are you using?  Did you follow any particular guide (I've followed many with no luck).  Many many thanks for any info you could share on this issue.

---

