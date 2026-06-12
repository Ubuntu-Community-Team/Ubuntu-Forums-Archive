---
title: "Gnome Panel hell after trying HDMI output"
date: 2012-09-25
forum: Desktop Environments
---

### Post by Jouleregedit on 2012-09-25
Hi guys,

I had the bad idea to try connecting my notebook with Ubuntu 12.04.1 (Compaq AMD64 - NVidia video chip 8200M) to my TV with HDMI.

Note: I'm using Gnome Classic (no effects) as desktop environment. <snip>

Since I had done this before with 10.04 without significant issues, I went to the Nvidia control panel and I started messing around with the settings, trying to get something out of it. Obviously, I had to save the settings on xorg.conf
BAD IDEA: I should have backed it up in a safe place before!

Now, after several retries, obviously restarting the window manager, I haven't been able to achieve the desired result, but this isn't the problem.

The real problem is that now the upper and lower Gnome panels, seem to have MULTIPLIED (obviously there's been some love behind the scene ;)) making it impossible to run any application from the GUI because I can't even see the applications menu as there is another panel overlapping it.
Imagine a whole line of "volume, date, user, logout", repeated 4 times.
The screen real estate has been much reduced because there are 4 grey lines (panels) on the upper and lower end of the screen.

Obviously I tried Nvidia Panel to change it back to default but it doesn't allow me to change back the dual monitor setting from "separate x-screen" to "disabled" (options are greied out).

I tried replacing xorg.conf with xorg.conf.failsafe, (xorg.conf.backup wasn't useful as it contained one of my many retries to achieve my objective), but Ubuntu doesn't even boot with it (it stays on the Ubuntu splash screen).

I tried editing manually xorg.conf, eliminating all instances of dual monitor use, but the situation didn't change.

I have to mention that if I boot with Unity, everything is fine! :lolflag:

So, since I really don't want to use unity, what do I have to delete or edit to change the actual situation?

Sorry if my english is sketchy, I'm italian.
Thank you very much for your attention!
G.

---

