---
title: "Help Resolve Window Refresh Rate"
date: 2011-07-22
forum: Desktop Environments
---

### Post by Zixus on 2011-07-22
Hi, I recently upgraded to 11.04(fresh install) and tried out unity. After getting everything installed and working, I'm still trying to narrow down the cause of the random choppiness. On a couple forums vsync is thought to be the cause, but now I'm not so sure. I think I have narrowed it down to something like a window repaint event not getting called properly, or not enough(I'm a windows developer, so I don't know too much about how the window painter works in ubuntu). At this point, I'm out of ideas as this seems to be a core issue, or something so blatantly obvious that I cant see it. Heres what I have done and my troubleshooting steps.

I have verified that opengl is working with my gpu (I'm not software rendering).
My first run of glmark2 showed all framerates locked at 60fps, so I forced vsync off in the gpu control panel. Now glmark2 shows upward of 4000fps for all tests. The only problem is that I only see the last frame from each test.
I have disabled the 'Detect Refresh Rate' in the Composite plugin for compiz.
I have disabled 'Sync to VBlank' in the OpenGL plugin for compiz.

I cant think of anywhere else a vsync option would be. But I started thinking that vsync isnt the issue due to the fact that the choppiness, from say moving a window around, gets an estimated 2-10fps depending on the speed the window is dragged. If this really was a vsync issue, i should be getting 60fps moving a window. It doesn't seem feasible that my gpu can handle the expo zoom and not handle moving a window at 60fps(especially since moving windows in classic are perfectly smooth).

I also notice expo lag occasionally when I working quickly with the machine, but when I use it again while paying attention, it works smoothly. I found out that if the mouse is moving while I execute expo, expo lags. If  the mouse is still, expo is smooth. Thats when I tried a theory with the glmark2 issue I had. I opened a scrollable page in firefox, ran glmark2, and continuously scrolled up and down causing the screen to repaint which caused the glmark2 window to render smoothly as well.

I don't know enough about ubuntu to know where to begin looking further. I've gone through all enabled plugins in compiz and found nothing more along the lines of refresh/vsync options. And I dont see anything beyond the gpu control panel for system settings to try. Has anyone overcome this issue? Does anyone have any tips for where to look or what to try next?

---

### Post by gordintoronto on 2011-07-23
I can't help you. However, it might be useful if you said what video adapter you have (lspci will tell you) and whether you ran "Additional Drivers" to install a driver for it. Also, what CPU?

---

### Post by Zixus on 2011-07-23
I have run the aditional drivers and installed(or activated) the driver for my gpu. I have also tried the drivers directly from ATI, but they seem to be the same one. As for hardware, I have 2 gpus but only one is being used on the linux side. Both of my monitors are plugged into the same gpu. Some specs, let me know if anything else is needed.

CPU: AMD Phenom X4 9950 @3GHz
GPU: 2x Radeon HD 4870

---

