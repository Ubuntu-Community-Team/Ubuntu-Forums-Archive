---
title: "Dual monitors + nVidia + CRASHING"
date: 2009-07-29
forum: Desktop Environments
---

### Post by Ck.asdf on 2009-07-29
Hello, I have a desktop with an nVidia GeForce 7300 GT running Ubuntu 9.04
I just recently fresh-installed 9.04 and enabled the non-free nVidia drivers for the best experience.  

All was fine, but then I started getting weird glitches in which the mouse would get trapped on one monitor or the other.

I figured out a clever work-around by using keyboard commands to move a window from one monitor to the other which would cause the mouse to be forced to follow and all would be well.

Now, though, every time I move my mouse to the second monitor it gets trapped there and every time I try that trick to bring it back, X crashes and I'm kicked back to the log-in window.


As far as I know, I've not done anything in particular to cause this.  Did an update maybe break dual monitor stuff or something?



In a slightly unrelated comment, I cannot get compiz fusion working while in dual monitor mode, though it works just fine with one monitor.  Is the GeForce 7300 not powerful enough to handle two monitors with fancy graphics?

---

### Post by Happy_Man on 2009-07-29
It's definitely not a question of power; my 5200 can handle 3360x1050 just fine, so yours should definitely do better.

My money would be on some sort of conflict between the drivers and something else you're running.... does this only happen if you have a certain application open? Or only when you run Compiz Fusion?

---

### Post by Ck.asdf on 2009-07-29
I don't think it's any specific application, as I could log in, open nautilus or firefox or such and the same thing happen; as I mentioned before, Compiz won't turn on while I have dual monitors enabled, so I've been using it without, unless maybe the display managers or something are getting confused and still half-using compiz?

I'll have to check when I get back to linux to see what display manager it's trying to use - metacity or compiz (emerald?).

But anyway, the basic happening is this:
I log in, I move the mouse to the secondary monitor, and it gets stuck.  If I try to force it over by means of the trick described earlier, X crashes.

---

### Post by c-shadow on 2009-07-29
> **Ck.asdf said:**
> I don't think it's any specific application, as I could log in, open nautilus or firefox or such and the same thing happen; as I mentioned before, Compiz won't turn on while I have dual monitors enabled, so I've been using it without, unless maybe the display managers or something are getting confused and still half-using compiz?

I'll have to check when I get back to linux to see what display manager it's trying to use - metacity or compiz (emerald?).

But anyway, the basic happening is this:
I log in, I move the mouse to the secondary monitor, and it gets stuck.  If I try to force it over by means of the trick described earlier, X crashes.

Do you have Twinview or separate X screens set up in nvidia settings?
I think there are some problems with the xorg/nvidia/gnome magic circle in jaunty. I have 2 separate screens with nvidia 7600 GS and a very big issue making 9.04 unusable: x server crashes when switching users. It happens on two fresh installs, one i386 and one x64 (not using compiz). Login user A, switch (login via fast user switch applet) user B, switch back to user A: bang, X from user A crashes! 
After a crash, log back in and try to look at a /var/log/Xorg.0.log.old, at the end of a file could be some useful data

---

### Post by Ck.asdf on 2009-07-29
Hmmm, got into linux, and no problem, oddly enough.  Still no compiz, but I went to look at which option is enabled, and I went to System -> Preferences -> Display.
After that, it showed:

> **Could not get screen information**
RANDR extension is not present

System -> Preferences -> Appearance -> "Visual effects" tab, "Normal" option - I get "The composite extension is not available."

---

### Post by T_Tom on 2010-05-31
Did you ever find a solution to this problem?  I have EXACTLY the same problem.

---

### Post by Ck.asdf on 2010-05-31
Sorry, no, I never found a solution.  Maybe now someone will since the thread has been "bumped."

Question - are you still using 9.04?  Perhaps you can install 10.04 & see if it improves any.  I am soon going to do that on my computer, but the computer I mentioned here was my desktop, which I don't use very often any more because I use my laptop mostly these days.

---

### Post by nerdzero on 2010-06-03
I've found that enabling TwinView makes a lot of those weird hard to reproduce bugs with multiple monitors go away.  You can enable this in the NVIDIA Settings tool that gets installed with the drivers.

The CompizFusionIcon tray applet also makes it easy to reload Compiz when it gets fussy.  I think its available from the "fusion-icon" package.

---

### Post by David006 on 2010-07-04
I'm getting the same issue, with Ubuntu 10.04, Nvidia, and 'separate X windows'.

To reproduce: (WARNING - will lock up GUI interface)
Move cursor close to edge, between left and right screens, and then rapidly move cursor back/forth over boundary three or four times.  ( This can also be triggered accidentally, when hitting back-arrow on browser (on right screen) or close/minimize window (on left). )

I put the issue down to logical transition.  The mouse events are across two separate X windows, and they either collide or report as negative (outside range).  The software mistakenly tries to redraw the mouse cursor in both logical screens simultaneously.  This is a lockup, rather than a crash.

It should be possible to identify in the code, and/or create a 'watch dog' trap to auto-escape this condition.


Meanwhile, I will try using 'TwinView'.

Can someone please document the 'keyboard shortcut' to escape this lockup?

---

