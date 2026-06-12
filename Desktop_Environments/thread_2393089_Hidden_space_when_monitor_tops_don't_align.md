---
title: "Hidden space when monitor tops don't align"
date: 2018-05-29
forum: Desktop Environments
---

### Post by turbo2ltr on 2018-05-29
Warning: Noob to linux desktops.

The Display Arrangement interface in 18.04 leaves quite a bit to be desired.  I probably spent a total of an hour or more trying to get the on-screen arrangement to match the physical monitor setup. It was very frustrating because for whatever reason the monitors on the screen get locked into certain axis, instead of being completely free like it is on windows.  I know this is a known issue as I had the same issue in 16.04 even though I read bug reports it had been fixed.  I assure you it has not.

My current setup has 4 monitors. From left to right: 1920x1080, 1920x1200, 1280x1024, 1280x1024 in Portrait.

After a lot of playing and a lot switching cables around, I finally got it to match:

[ATTACH=CONFIG]279919[/ATTACH]

At least it was the best I could do. #2 is my main monitor. There is actually a tiny gap between monitors 2 and 3 that I cannot get rid of.  I have no idea why they made the monitors in the interface so damn small.  The gap I don't notice so not a huge deal. It's maybe 15px wide if that.

The bigger issue is how I set up monitor #1.  Physically, it is mounted higher that the rest of them so in order to get the mouse to not jump when crossing the border, I set it up the same way in the Display Interface. This worked, but after I set it up, I kept losing my mouse pointer. After a lot of confusion as to where it was disappearing to, I finally figured out that there is "hidden" desktop above monitors 4,2, and 3, assumingly because #1 is that high.  

I don't claim to know how the back end works for arranging all this stuff. Clearly it's not easy if it's been this long and still not fixed.  But it would be really great if this whole thing worked as well as the Windows interface worked.  Windows does not create empty hidden space when monitors don't line up....and it allows you to place them anywhere, easily snapping to any nearby monitor.

Additionally, the "Find Right Package" page [https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage) linked to from the Reporting bugs page has instructions that don't seem to work for noobs like me.  "1: [COLOR=#333333][FONT=&quot]Launch System -> Preferences -> Main Menu."  Couldn't find this.

[/FONT][/COLOR]

---

### Post by Autodave on 2018-05-29
Can we start by knowing what video card is in your machine? Did you install a driver for it? If so, what driver and where where did you get it from?

---

### Post by turbo2ltr on 2018-05-29
GeForce GTX 1070
NVIDIA Driver Version: 390.48

In Software->Additional Drivers says I'm using "NVIDIA driver matapackage from nvidia-driver-390 (proprietary,tested)"

In looking for this stuff, I found the NVIDIA X Server settings which also has a Display Arrangement screen and I was able to remove the gap between the monitors.
And now the hidden desktop is gone too.  Hmm.  I'll have to do more research as to when the hidden space appears.  Not sure exactly when it disappeared.  I'm going to guess it was when I applied the settings in the Nvidia settings... I'll report back.

---

