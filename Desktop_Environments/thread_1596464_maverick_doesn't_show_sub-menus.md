---
title: "maverick doesn't show sub-menus"
date: 2010-10-14
forum: Desktop Environments
---

### Post by Ve5ahchoo8ah on 2010-10-14
sorry for bad title! I couldn't think of a better one!
anyway since I upgraded to Ubuntu 10.10 when I right-click on something and there is another menu in that menu, it doesn't show up for the first time!

for example if I want to create a an "Empty File", I'll right-click on desktop and when I want to go to "Create Document" menu, it doesn't show up! so I must click somewhere else and try again so for the second time it works!!

Please see the pictures I attached so you will understand what I'm saying!
(second picture is for Pidgin menu and I'm trying to change my status)

---

### Post by Ve5ahchoo8ah on 2010-10-15
And even Menus!!

someone help please!!

---

### Post by QIII on 2010-10-15
I was getting this in one of the Alphas, but not by the Beta or RC.

I don't have time to look, but you might try launchpad to see if there is anything there (which is what I would have done for you if I had the time -- lunch break is about over!)

If there is nothing there, submit a bug report.

I know that was happening to me before, but it has resolved.


Edit:

I did a little fiddling around with window managesr, compositing, effects, etc.  I definitely don't have the issue any longer.  What are you using for a window manager?  Do you have compositing or effects enabled?  What happens if you change them around?

---

### Post by figure002 on 2010-10-19
I recently updated from Ubuntu 10.04 to 10.10, and now I'm facing the same problem. It's not just sub menus, but all menus, just like you said. Also, it seems to happen randomly, most of the time menus display fine, but sometimes they don't display. Interestingly, when the menu doesn't appear, and you move your pointer to the place where the menu should appear, the menu suddenly appears.

I did some tests with window decorators and compiz effects. It happens with both GTK and Emerald window decorators. I also tried different compiz settings, but nothing helped. I haven't tried it with compiz disabled yet.

I've searched in Launchpad for a bug report, but this bug doesn't seem to be reported yet. I will probably create a bug report soon.

---

### Post by Ve5ahchoo8ah on 2010-10-21
It's exactly as you said figure002,
please post the bug address here whenever you report it
thanks

---

### Post by figure002 on 2010-10-23
I just created the bug report. This can be found here: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/665546](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/665546)

I put the bug report under "compiz" because it doesn't seem to happen when compiz is disabled.

---

### Post by Ve5ahchoo8ah on 2010-10-23
thanks a lot

---

### Post by manuelb on 2010-11-15
I recently upgraded (10.04->10.10) my system and immediately noticed this problem: you can have the menu appear by just moving the mouse over the area where the menu *should* appear and it *will* appear o_O

---

### Post by radarlog on 2010-11-26
this bug also affected me

---

### Post by figure002 on 2010-11-27
> **radarlog said:**
> this bug also affected me

If you're experiencing the same problem, it's best to visit the link to the bug report above. On that page there's a link "Does this bug affect you?"; click that if it does. Also you can add useful comments regarding that bug there. This might help in finding a fix.

---

### Post by radarlog on 2010-11-30
> **figure002 said:**
> If you're experiencing the same problem, it's best to visit the link to the bug report above. On that page there's a link "Does this bug affect you?"; click that if it does. Also you can add useful comments regarding that bug there. This might help in finding a fix.

already done this!

---

### Post by radarlog on 2010-12-29
I think I fixed this by enabling "indirect rendering" in Compiz.

---

### Post by manuelb on 2010-12-29
This problem also affect the latest daily Natty release: i didn't tried previous versions (alphas..) but today's iso definitely expose the same problem and it's worse than 10.10 since menus (logout/firefox/apps) don't appear at all while hovering the mouse around, it could also be about the new thing where the menus appear into the top panel, but it's really difficult to logout from the system since the menus won't show up o_O

---

### Post by Ve5ahchoo8ah on 2011-02-02
I don't know what has happened but my computer is right now (back to normal)
but as there are some who are experiencing this problem now I don't mark this thread as solved.
If anyone found the final solution please _[COLOR=Blue][inform me]("http://samic.org/mail/")[/COLOR]_ to do so
thanks

---

### Post by nonoitall on 2011-02-02
I am experiencing this same problem, and I've also experienced it on Arch.  The problem isn't with Compiz specifically, but with any sort of compositing being enabled.  (It also occurs in XFCE when compositing is enabled, but not when compositing is disabled.)

Great to hear that your problem has gone away, samic130.  Was there a particular upgrade or configuration change that occurred right beforehand?

---

### Post by Ve5ahchoo8ah on 2011-02-02
I really don't know what happened that fixed it! I just notice after a while that menus are appearing normally!!
I hope your ubuntu become normal too

---

### Post by figure002 on 2011-02-02
> **samic130 said:**
> I really don't know what happened that fixed it! I just notice after a while that menus are appearing normally!!
I hope your ubuntu become normal too
That's so weird! Menus are still not appearing normally for me. Though I do receive all updates.

---

