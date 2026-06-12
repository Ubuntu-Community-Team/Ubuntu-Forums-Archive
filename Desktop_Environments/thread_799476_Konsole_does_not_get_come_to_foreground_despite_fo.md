---
title: "Konsole does not get come to foreground despite focus"
date: 2008-05-19
forum: Desktop Environments
---

### Post by sfjohnsen on 2008-05-19
Hello,

I have observed the following problem on Ubuntu 8.04 (64 bit, core 2 laptop, generic kernel) with kde-core (kde 3.5) desktop and konsole:
When I switch to a desktop on which konsole is running in full-screen mode (that is the case on 2 of my 4 standard desktops), then it often happens that the kde panel is in the foreground despite konsole having the focus and keyboard input.
Is this a true bug, or simply due to some settings issue, i.e. are there other users who can report the same problem, or have a similar set-up but no such trouble?

Thanks in advance.

---

### Post by p_quarles on 2008-05-19
There is a Kwin setting that affects the placement of windows relative to one another. You can find this in the kcontrol application under Desktop >> Window-specific behavior. Play around with the relevant options in there and see if you can get the full-screen konsole acting the way you want it to.

---

### Post by sfjohnsen on 2008-05-21
Thank you for your reply.
Unfortunately the focus behavior was the same with the focus-follows-mouse variants, and more alternatives that could really make a change there aren't.
So I guess this is really some kind of bug:
* when the panel has the focus when switching to a desktop where konsole is running in full-screen mode it cannot be raised.
* if konsole gets the focus before leaving, the desktops are switched back and forth, it is raised when returning to the respective desktop.
==>so it's kind of reproducible. 
Though only a detail, it might be easy to fix for someone who knows the code. Whom should I address?

---

