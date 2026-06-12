---
title: "Strange colors with nVidia drivers"
date: 2007-05-24
forum: Desktop Environments
---

### Post by lramshaw on 2007-05-24
When I enable the nVidia restricted device drivers and reboot, the colors on my desplay become very strange. The mostly black sky in a picture of night seen displays as alternating bands of bright and dark blue. 

When I turn the nVidia drivers off and reboot, the colors go back to normal.  I'm running Feisty on a machine with an nVidia GeForce 3 TI 200 video card.

Does anybody have a thought as to what's going wrong?

---

### Post by ryanVickers on 2007-05-24
Very strange.  As many people that have said how easy the drivers has become in 7.04, there is as many or more that have had problems.  I think that there are no real drivers from nVidia, so people are writting their own.  Most of them are work in progress, but work ok.  I have noticed significantly more problems on old card like a geForce 3.  Seems strange because ubuntu was origionally designed to run on old, slow hardware better than anything else.  But they are being updated all the time, just wait and see.  Leave them off for now.

---

### Post by troy001 on 2007-05-25
I have a similar problem, the only thing is that when enable the nVidia restricted device drivers and reboot nothing comes on, I mean the initial progress bar comes on, but then everything goes black, I can hear the small sound when the password screen comes on, but don't see anything. I am kind of new at this, and since it was a new install I just reformatted and installed again. I have a Nvidia GeForce4 420 Go, it is installed in a Sony vaio pcg-nvr23. Any advices on how to make this work?
Thanks
Troy.

---

### Post by ryanVickers on 2007-05-25
Interesting.  Usually, if the drivers have broken something, what will happen is it will fail to even get to the logon screen and you'll just get a full screen command line.  Now, your card would also be classified under "legacy", but like I said, those drivers seem to have difficulties.  My guess, because of your description, is that all is up and running in the background, but when it starts up the driver (right before logon screen) your not seeing anything because, my guess, is that it doesn't have any (or enough/correct) info on your monitor.  Is it old/uncommon?  Just a thought, it might have not recognized and configured it properly.  It may be something else though; like instead of one thing wrong, like the video output, it may be only one thing good, like say the only functionality was the sound device.

I would just leave them off for now, and wait for news of drastic updates to the drivers.  You would think with so many people having these problems, some one would have fixed more of it by now, but oh well.  If anyone else has some advice?

---

### Post by Reodor Felgen on 2007-05-27
NVidia drivers after 76.64 no longer support certain GeForce3 cards. I have the same problem.

---

### Post by tnilsson on 2007-06-17
I have the same problems with my GeForce3 Ti 500 card, strange colours.
What cards are supported?
It was working well in the previous version of ubuntu.

Any sugestion of another low end Nvidia card?

---

### Post by imagining on 2007-07-18
> **troy001 said:**
> I have a similar problem, the only thing is that when enable the nVidia restricted device drivers and reboot nothing comes on, I mean the initial progress bar comes on, but then everything goes black, I can hear the small sound when the password screen comes on, but don't see anything. I am kind of new at this, and since it was a new install I just reformatted and installed again. I have a Nvidia GeForce4 420 Go, it is installed in a Sony vaio pcg-nvr23. Any advices on how to make this work?
Thanks
Troy.

I have the same problem. I installed Ubuntu 7.04 (Feisty Fawn) on my Sony Vaio PCG-NVR23 that has a nVidia GeForce4 420 Go graphics chip with 32 MB of DDR SRAM and 3D hardware acceleration. It worked fine at first but after I enabled  the restricted device drivers and reboot nothing comes on. "I mean the initial progress bar comes on, but then everything goes black, I can hear the small sound when the password screen comes on, but don't see anything." is an excellent description of the situation. How can I rollback the restricted device drivers installation? Or is there a fix for this? Please help... Any input is appreciated. :confused: (it is my first attempt to leave behind the Microsoft Windows world)

Thank you!

---

### Post by Writh on 2007-07-19
Check how your monitor's connected to the PC itself. If you're using DVI, try switching to VGA. At least in my case, switching to an analog connection fixed the problem. It's a known bug with the new nVidia drivers.

---

### Post by imagining on 2007-07-19
> **Writh said:**
> Check how your monitor's connected to the PC itself. If you're using DVI, try switching to VGA. At least in my case, switching to an analog connection fixed the problem. It's a known bug with the new nVidia drivers.

Goo idea, but the computer on which I have installed Ubuntu is a Sony Vaio laptop. I do not think that I can change the way the monitor is connected, can I?

---

### Post by imagining on 2007-07-19
> **Writh said:**
> Check how your monitor's connected to the PC itself. If you're using DVI, try switching to VGA. At least in my case, switching to an analog connection fixed the problem. It's a known bug with the new nVidia drivers.

Good idea, but the computer on which I have installed Ubuntu is a Sony Vaio laptop. I do not think that I can change the way the monitor is connected, can I?

---

### Post by imagining on 2007-07-19
> **Writh said:**
> Check how your monitor's connected to the PC itself. If you're using DVI, try switching to VGA. At least in my case, switching to an analog connection fixed the problem. It's a known bug with the new nVidia drivers.

Good idea, but the computer on which I have installed Ubuntu is a laptop (Sony Vaio PCG-NVR23). I do not think that I can change the way the monitor is connected, can I?

---

### Post by imagining on 2007-07-19
> **Writh said:**
> Check how your monitor's connected to the PC itself. If you're using DVI, try switching to VGA. At least in my case, switching to an analog connection fixed the problem. It's a known bug with the new nVidia drivers.

Good idea, but the computer on which I have installed Ubuntu 7.04 is a laptop (Sony Vaio PCG-NVR23). I do not think that I can change the way the monitor is connected, can I?

---

