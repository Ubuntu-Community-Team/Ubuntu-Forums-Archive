---
title: "Compiz and Beryl + Seamless VirtualBox = Big problem?"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by SH00TER on 2007-11-27
I have windows XP running in Virtualbox, and I can successfully achieve seamless virtualization (with the windows taskbar on the bottom of the screen and the gnome desktop on the rest) if i turn desktop effects OFF. However, when my desktop effects are on, I get this weird effect if I try to use the windows VM. It leaves a residual image all across the gnome desktop, though I can still use gnome and ubuntu just fine. Here's a screen shot of what I mean:

[IMG]http://i16.tinypic.com/6ymd06c.png[/IMG]

Anyone know how to fix this? is there a way to tweak the virtualization to eliminate this problem?

BTW - I'm using the built-in seamless virtualization provided by the latest version of VirtualBox - I didn't set it all up myself (I can't figure out that host-only networking at all). If someone wants to help me out with that, i'd be much obliged...

---

### Post by magiceraser06 on 2007-12-13
Shooter.  Im having the same problem.  A viable work around would be to make the QUICKLAUNCH bar, detached and just move out of the way.  that way you won't get the ghosting.

its a bug that has to do with Compiz-Fusion.  If you switch to the metacity window manager, you won't have that problem anymore.  its a wierd bug and I haven't yet been able to find a permanent fix.

hope that helps.

---

### Post by pjones0404 on 2007-12-14
i followed these instructions here.

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

it worked perfectly the first time. i have compiz enabled and am also running emerald for the windows manager. i would not be much help in resolving your issue. but hopefully these steps will work.

---

### Post by kaffekopp on 2007-12-29
Hi, I had the same problem with Windows running as guest in Virtualbox under Gutsy w/Compiz fusion. 

I can work around the problem by making sure that there is always one window open in Windows (As suggested in the howto mentioned above, I've added the calculator to my startup applications in windows, and try to keep it out of view, hidden under the windows taskbar).

As far as I could see, there were no such problems with seamlessness when running virtualbox in metacity.

---

