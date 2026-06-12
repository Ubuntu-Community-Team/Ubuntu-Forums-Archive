---
title: "Multiple monitors, different resolutions, and visual effects help (ATI)"
date: 2011-03-12
forum: Desktop Environments
---

### Post by hotrod6657 on 2011-03-12
Hey folks.  I just moved back to the Linux world and am working on getting my desktop set up with 10.10 (64 bit).

I run multiple monitors, two all the time and a third (my TV) when I want to watch movies/online content, ect.

My video card is an ATI Radeon HD 5770.  My two all the time monitors are a 20 inch widescreen (1600 x 900 native) and a 19 inch traditional aspect ratio monitor (1280 x 1024 native).

I've downloaded the Catalyst Control Center and drivers recommended.  I tried setting up the monitors as a multi display desktop but I get nasty looking lines over the extra pixels of height on the 1600x900 monitor.  It looked like crap so I tried the single display desktop option.  That gives me the proper resolutions and gets rid of the lines, but doesn't allow me to drag windows between monitors.

I tried enabling Xinerama which did correct this issue, however it made me no long able to use desktop effects.

Are there any alternatives or work around I could be trying?


Thanks for the help,

hotrod

---

### Post by hotrod6657 on 2011-03-13
I've done some more searching and it seems that Xinerama and Compiz just don't work well together.

Are there any other ways of moving windows between both monitors without using Xinerama?  All I need is a way to drag between them.

---

### Post by Krytarik on 2011-03-13
Basically it's like you said, at least imo. If you use Xinerama, you can move windows between them, but Compiz is disabled. And if you use separate xscreens, Compiz works, but you can't move windows between them. Unfortunately.

---

### Post by hotrod6657 on 2011-03-13
That really stinks...

It doesn't seem right that something so simple is not possible in Ubuntu...  I've run the same dual monitors with a NVIDA video card and had no problem.  I haven't checked 10.10 with the NVIDA to see if it still works.

Is there any way to use this as a single desktop but get rid of the lines caused by the different resolutions?

---

### Post by Krytarik on 2011-03-13
Nvidia cards, running with the proprietary driver, should work with its TwinView option to have Compiz working *and* be able to move windows.

As for the lines you mention, could you provide screenshots of both screens!?

I set up dual monitors one time with Xinerama at my mom's machine, the first (left) monitor is a 17'' 4/3 CRT, and the second one is a new 24'' 16/9 LCD. And I had no such lines.

---

### Post by hotrod6657 on 2011-03-13
Well, upon a second look the lines are gone...

Must have been something that fixed itself after a restart or something.  Maybe updates.

I'm good to go now, and I have the same massive desktop cube that i remember from before.  (though i have to admit it was neat to have the two separate desktops...)  

Thanks for asking to see the lines or I wouldn't have realized they weren't a problem.

---

