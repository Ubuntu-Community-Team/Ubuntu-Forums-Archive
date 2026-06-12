---
title: "Suspending and Hibernating"
date: 2009-09-10
forum: Desktop Environments
---

### Post by thundaraptor on 2009-09-10
My system is terrible at either of these.  It rarely makes it back out.  How do I better understand what is happening and attempt to make necessary changes?

Thanks,

TR

---

### Post by aeiouna on 2009-09-10
How did you install Ubuntu?

If you used Wubi on a Windows system, it says in the documentation not to try to suspend/hibernate the system while in Ubuntu cause it won't work.

---

### Post by krazyd on 2009-09-10
can you give some details of your system? especially graphics card / driver.

---

### Post by thundaraptor on 2009-09-10
Sure, I have a custom built box with a AMD 2.6 ghz core, 4gb ram and a ATI Radeo HD 4670 dual head video card.  There is also an onboard (to the motherboard) ATI HD 3100 card but to date I don't know how to get the cards to work together (crossfire is complicated).  I had enough trouble getting the secondary card to work in big desktop mode.  In fact, the system was sleeping/hibernating ok before I got the big desktop mode to work properly so there maybe something there.  My ubuntu is Jaunty Jackelop 64 bit.

---

### Post by dE_logics on 2009-09-10
> ATI Radeo HD 4670

This is the issue.

Choose and download - 

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

If you wanna enable hybrid crossfire, you need to switch a jumper on the motherboard...that's all I know.

---

### Post by thundaraptor on 2009-09-10
I am not sure what you are saying.  Download a new video driver?  I don't really want to do that, configuring my xorg to get big desktop to work was a lot of work.  I don't want to start over at ground zero, anyways I think I have the most recent version of the driver installed anyways.  How do I know for sure what version of cayalyst I have?  This is something I wonder about, when I open the proprietary catalyst control center I can't tell what version of catalyst I am using, nice ATI.

---

