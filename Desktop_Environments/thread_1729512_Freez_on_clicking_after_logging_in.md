---
title: "Freez on clicking after logging in"
date: 2011-04-15
forum: Desktop Environments
---

### Post by Jagoly on 2011-04-15
OK. So since last night, I haven&#8217;t been able to use ubuntu in normal mode. It starts up, lets me log in, and shows the desktop. At this point everything is fine, if I move the mouse around over icons, they highlight and unhiglight. However, as soon as I click anywhere, the desktop freezes. The pointer will still move, but nothing else. I can run fine in failsafeX.

I have no idea what is causing this. The last thing I did was install morrowind (a game in wine), then attempt to run it. Each time it would start loading and show in the panel, but after a few seconds disappear, like alot of things in wine. On the 3rd or 4th try, the screen froze (as described above. Now I can only use failsafeX.

What's going on? Please help me :(

edit: oh no. I spelled freeze as freez in the title.

---

### Post by Jagoly on 2011-04-15
Please I need it fixed by tomorrow. Will explain later!

EDIT: we (me + my family) are going camping to stay in Darwin city tomorrow for my grandparents birthdays, and my laptop wil be used as a DVD player for my little brother. FailsafeX fails at DVD's! I need accelerated graphics!

Please oh Please the internet won't be on for much longer. Sorry for the double post but this could get me in a lot of trouble.

---

### Post by Krytarik on 2011-04-15
Although this may come a little late, but try this, to disable Compiz:

- log in to "Failsafe GNOME" or boot into "failsafeX", like you did before

- set "Visual Effects" in "System -> Preferences -> Appearance" to "None", or run:
```

gconftool-2 /desktop/gnome/session/required_components/windowmanager --type string --set metacity
gconftool-2 /desktop/gnome/applications/window_manager/current --type string --set /usr/bin/metacity
gconftool-2 /desktop/gnome/applications/window_manager/default --type string --set /usr/bin/metacity
```[INDENT]The values for Compiz are "compiz" and "/usr/bin/compiz" respectively.
[/INDENT]- enable compositing for Metacity:
```
gconftool-2 /apps/metacity/general/compositing_manager --type bool --set true
```- reboot/relogin

Hope it helps!

---

### Post by Jagoly on 2011-04-17
Thankyou! I managed to see this just before we left yesterday morning! With compiz disabled, we could run normally.

I didn't expect compiz to be the problem, as I hadn't changed any settings in compizconfig. I had a whole lot of customised stuff there. I exported a profile before I disabled it, so now I'll try booting with certain things disabled to try and narrow down the problem. Is there anything in particular that is likely to be causing this?

---

### Post by Jagoly on 2011-04-17
UPDATE: Ok, the problem is being caused by "mouse position polling". Why is it playing up? A few other things depend on this, so I'd like to get it back. Anyone got any ideas?

---

