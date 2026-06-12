---
title: "[SOLVED] Nvidia Twinview with different sized monitors"
date: 2007-05-07
forum: Desktop Environments
---

### Post by starfry on 2007-05-07
Hello,
I have successfully got my two screens running nicely using my Nvidia card and Twinview. Now, one of the screens is smaller so I have "dead space" below it that I can not access.

I would like to make the second screen behave as a view-port so I can move it up/down to see that dead space.

I want to do this because I have an application that sticks a toolbar across the entire bottom of the screen and I can't get to the right hand side of it.

I have display 1 = 1920x1200 and display 2 = 1024 x768. I'd like display 2 to be  viewport on a screen space of 1024x1200. 

Is there a way to do this?

---

### Post by orb9220 on 2007-05-07
> I have successfully got my two screens running nicely using my Nvidia card and Twinview.

Twinview does not do seperate resolutions that is xinerama.
This may help don't know but here it is.   [http://www.zulustips.com/2007/04/01/dual-monitors-howto.html](http://www.zulustips.com/2007/04/01/dual-monitors-howto.html)

> I want to do this because I have an application that sticks a toolbar across the entire bottom of the screen and I can't get to the right hand side of it.

A workaround for this is to right click panel and turn off Expand.

See my sig for tutorials that might help.

---

### Post by Schapie123 on 2007-05-08
You can use panning to use a virtual resolution of 1024x1024 on the smaller screen. you can set this in xorg.conf by changing the resolution of your second screen from 1024x768 to 1024x1024@1024x768 I think.

---

### Post by starfry on 2007-05-14
Yes, that works nicely. However I have decided it is not desirable because moving the mouse up and down the main (larger) screen causs the viewport on the smaller monitor to move too. This is very distracting and most annoying.

I've decided to switch it back and live with the dead space. I have another monitor on order with the same vertical resolution as the first so my problem will go away in a few days :)

---

