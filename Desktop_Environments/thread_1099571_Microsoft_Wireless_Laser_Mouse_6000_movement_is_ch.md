---
title: "Microsoft Wireless Laser Mouse 6000 movement is choppy"
date: 2009-03-18
forum: Desktop Environments
---

### Post by mw007x on 2009-03-18
Hi All,

As stated in the title, I have the microsoft wireless laser mouse 6000. On the bottom, it says model 1052.

When moving the mouse (not clicking, dragging, etc) the mouse is very choppy. For instance, if I move the mouse vertically from the top to the bottom of the screen, every so often, the mouse cursor will jump to the left or right. This obviously makes it very difficult to click on links when surfing the web, navigate menu items in different applications, etc.

I've tried this in other distributions (mainly Gentoo) and could not get the mouse working properly there, either.

This does not happen in windows, which makes me assume it is a driver configuration issue.

Here is some info on my machine. I am running Ubuntu 8.10 Intrepid Ibex with Gnome 2.24.1. If needed, I can post my xorg.conf file up on a pastebin.

I've tried searching google, more than a share of forums and seem to only get results on how to config the extra buttons to work properly.

If anyone can shed light on the situation about the mouse movement being choppy, I would appreciate it. 

Thanks!
mw007

---

### Post by walterflanagan on 2009-03-25
I've had this same problem.  With this mouse I've also experienced it in all of the big 3 -- Ubuntu, Mac, and Windows (XP, Vista, 7).  I'm wondering if it has to do with the surface on which the mouse is placed.  

Anybody else??

---

### Post by mw007x on 2009-03-25
I think the surface might have been the problem. I tried more than a few different surfaces, and finally found one that works well.

It's a piece of compressed particle board.

It seems like this mouse only works well on smooth, non-reflective surfaces. Even tried this on windows, and the mouse works better than before.

Can anyone else confirm this?

---

### Post by kellymartinv on 2010-01-06
Verified. I've been using a mousepad for the last several months with choppy movement. Took the mousepad away and just used the flat surface of the desk, and back to crisp movement.

---

### Post by revup on 2010-03-21
I have the jerky movement problem with the microsoft6000 lasermouse and Karmic.
The problem does not exist under windoze,
When I disable wireless via the network manager icon, mouse movement becomes smooth again.

The problem is more apparent when there is a poor internet connection.
For example, When the mouse motion is too bad, I can jump onto my neighbors wifi, and the motion becomes smooth again, but returning to my own (broadband) connection, the problem returns.

I checked the above replies, and it is definitely NOT a surface problem.
And it definitely does NOT exist under Windoze.

A Linux laptop (Karmic) connected to the same router using the same mouse does not show this problem.

---

### Post by LeeDaugherty on 2011-05-30
This is just a possible random thought.  I use a MS6000 now (and btw I got mine super super cheap...so I figured it was junk to start)...but in any case...this is my second MS setup.  My first one would randomly spit out "unknown key please map" errors in my syslog.  I researched this imensley and came across a finding that MS keyboards/mice send out "ping"-like probes telling Windows their batteries are ok.  (Seems stupid right?  Look at who we are buying our mice from).  In any case, I'll look to see if someone patch to supress those errors or they still do that.  It causes the mice/keyboards to have problems on other OS's besides Windows.  Imagine that...I just can't imaging MS would do that on purpose.  I'll do some research and check back.

---

