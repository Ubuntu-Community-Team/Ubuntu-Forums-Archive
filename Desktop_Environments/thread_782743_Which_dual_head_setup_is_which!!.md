---
title: "Which dual head setup is which??!??!?"
date: 2008-05-05
forum: Desktop Environments
---

### Post by e-dard on 2008-05-05
Hi All,

I have two monitors now and am playing with dual head.  I am confused though about which configuration is which, as there seem to be many ways to configure dual head monitors up.  

1)  Given a normal setup of 4 workspaces in Ubuntu, is it possible to display one on each monitor at a time.  For example, workspace1 would be on the left monitor and workspace2 would be on the right.  Were you then to move workspaces to the right, workspace2 would be on the left monitor and workspace3 on the right.  Could this also be done with compiz???

2)  With regard to running two separate sessions, so that each monitor has its own set of workspaces, how have people that have done that found it to be?

Cheers,

e-dard

---

### Post by foolsh on 2008-05-05
You'll probably be messing with dual head setups a lot if your like I was, I setup what is call a multi-seat multi-head system here at home some time ago. What it comprised of were 2 monitors, 2 usb keyboards, 2 usb mice, 2 video cards, 1 p4 cpu. It was pretty cool allowing two people to share one computer each with their own monitor and keyboard/mouse.  But sound was shared and only one video card was accelerated. But was still pretty cool.

there is a package in the repositories that is supposed to set it all up for you but its non-free. If you do some research on the interwebs you should be able to figure it out.

---

### Post by RAOF on 2008-05-06
In order:
1) While this is technically possible, I don't know of any window manager that implements this behaviour.  Generally you will have 4 workspaces, each spanning both monitors and they change in lockstep.

2) There are two ways of doing this; Xinerama and Zaphod mode.  Xinerama is deprecated and generally doesn't play very nicely with other parts of X, but gives you two separate screens that you can drag windows between.  Zaphod mode is where your card pretends that it's really two cards and you essentially run different X servers on each - they're almost entirely separate, and can't share windows etc.

I don't use (2).

How you can actually get dual-head working properly depends on what drivers you're using; the nvidia drivers do their own thing (TwinView, which is different to everyone else), the fglrx drivers probably do something similar, and all the open-source drivers should now do XRandR 1.2 - which means System->Preferences->Screen Resolution should work.  Except for adding a Virtual line to your xorg.conf :(.

---

### Post by e-dard on 2008-05-06
Hi,

thanks for the reply.  For some reason I presumed that the 4 workspaces were just one after the other, that they were always "there" and that the monitors just looked at a certain section of them (i.e. one at a time).  

What I mean is I thought that perhaps they were laid out like they were in the window switcher and that I could position viewpoints from monitors along them.  Never mind!

Also, I am thinking of getting an Nvidia card instead of my ati x850.  The fglrx have a big bug which overheats the card and the open source drivers for the ati card don't work very well with dual head and compiz.  I presume twinview works well??

e-dard

---

### Post by RAOF on 2008-05-06
> **e-dard said:**
> Hi,

thanks for the reply.  For some reason I presumed that the 4 workspaces were just one after the other, that they were always "there" and that the monitors just looked at a certain section of them (i.e. one at a time).  

For Compiz, this is actually the case (except that compiz treats both monitors as a single object).  For metacity, this isn't the case - a metacity workspace that isn't visible doesn't really exist :).

> **e-dard said:**
> 
...
Also, I am thinking of getting an Nvidia card instead of my ati x850.  The fglrx have a big bug which overheats the card and the open source drivers for the ati card don't work very well with dual head and compiz.  I presume twinview works well??

Yeah.  With the free drivers you'll have the 2048x2048 maximum texture size limitation.  Twinview isn't *bad*, as long as you don't want to dynamically change things too often :|.

---

