---
title: "MX518: disable resolution switching?"
date: 2006-12-05
forum: Gaming &amp; Leisure
---

### Post by Landslide on 2006-12-05
I love ubuntu. But one of the main annoyances I have with it for gaming (as regards first-person shooters especially) is that I have an MX518 mouse, which has two buttons on either side of the scroll wheel that change the resolution of the mouse. It defaults to 800, but can toggle up to 1600 or down to 400.

I've tried many ways of disabling the resolution switching. I installed lomoco, but all that is able to do is change the resolution initially. What I want, ideally, is to be able to bind other functions to the two resolution switching buttons, and have them not change the resolution at all. But I'm not sure how that's possible-- when you hit either of those buttons, the resolution changes, but NOTHING shows up in xev, which leads me to believe that the resolution change is handled by the mouse internally.

But on the other hand, the windows drivers for the MX518 (SetPoint) let you do exactly what I'm aiming for, so surely it is possible in Linux.

Can anyone help me out with this?

---

### Post by themightychris on 2006-12-26
SetPoint in windows is more of an accompanying application than the actual drivers.  As far as I know, the resolution switching is done internally in the mouse, and being able to turn it off in the mouse is a feature of using the Logitech software which is only available for windows.  It isn't controlled by the mouse driver.

Don't hit the buttons?  Do you have a problem with hitting them accidentally or are you hoping to assign them to something else?

---

