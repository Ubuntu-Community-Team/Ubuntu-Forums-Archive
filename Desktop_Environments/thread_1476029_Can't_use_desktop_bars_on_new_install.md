---
title: "Can't use desktop bars on new install"
date: 2010-05-07
forum: Desktop Environments
---

### Post by gauchotodd on 2010-05-07
I am new to Linux and Ubuntu, have seen it used before, but just installed 10.04 for the first time a few days ago.  Within five minutes, I made a moronic, rookie mistake and now I can't do anything whatsoever haha.

I didn't like the bar on top so I switched it to be on the bottom while the bottom bar was still there.  On top of that, I wasn't thinking and dropped the pixel size for the bar from 24 to 23.  I guess I assumed that the bars would either combine or one would be replaced; I don't know.  But now I can't use anything from either bar, even though it shows some of the information from the first one.  When I click it, it doesn't do anything.  It's "under" the other bar, so to speak, rendering both of them useless.

Luckily I am dual-booting from Win7, so I can still use my system.  I noticed that Ubuntu loads much slower than Win7, which really surprised me.  It could be that the drivers need to be installed on Ubuntu, but I can't get to the driver installer.

Is there a way I can fix this problem?  Or should I do an uninstall, reinstall, and try not to be such an idiot next time?

---

### Post by jerrrys on 2010-05-07
nothing wrong with stacking panels, this will not combine the panels.  right click on the existing panel; create a new panel; drag it to the top; right click on this panel and select the add to panel option and from there refill your panel

---

### Post by SteveDee on 2010-05-07
> **gauchotodd said:**
> I am new to Linux and Ubuntu, have seen it used before, but just installed 10.04 for the first time a few days ago.  Within five minutes, I made a moronic, rookie mistake...

...no, you didn't make a mistake, its probably a bug in Gnome.

I just did something similar. I installed Avant Windows Manager and moved both Gnome panels to the top...Gnome then crashed and it was a devil of a job to even boot into my desktop.

The solution was to reset to default panels as described here: [http://ubuntuforums.org/showthread.php?t=1475584&highlight=panels](http://ubuntuforums.org/showthread.php?t=1475584&highlight=panels)

---

### Post by gauchotodd on 2010-05-09
Fantastic!  That sounds like it should do the trick, I will try it and get back to you asap.  I can't right click on the toolbar, it's totally inoperable.

---

### Post by binamenator on 2010-05-10
> **SteveDee said:**
> ...no, you didn't make a mistake, its probably a bug in Gnome.

I just did something similar. I installed Avant Windows Manager and moved both Gnome panels to the top...Gnome then crashed and it was a devil of a job to even boot into my desktop.

The solution was to reset to default panels as described here: [http://ubuntuforums.org/showthread.php?t=1475584&highlight=panels](http://ubuntuforums.org/showthread.php?t=1475584&highlight=panels)

How did you add a new panel in Avant Windows Manager?

---

### Post by SteveDee on 2010-05-10
> **binamenator said:**
> How did you add a new panel in Avant Windows Manager?

Sorry for the confusion. I didn't add a new panel. I installed AWM to show my son I could match his RocketDock in Windows. While AWM was running I dragged the lower Gnome panel out of the way (to the top of the screen) to show off the groovy icons. This resulted in a freeze and a single blank panel at the top of the screen.

I think Gnome caused the freeze, because I've had problems before (I tend to arrange my desktop with the top panel at the bottom, and bottom at the top) but I un-installed AWM and haven't tried to reinstall it. The only way I could boot into my desktop was to start another account first, then switch users.

---

### Post by binamenator on 2010-05-11
Oh... It's okay.

---

### Post by gauchotodd on 2010-05-14
Interesting turn of events: I went to try this, and when I boot ubuntu, it waits on the black screen and finally says "Gave up waiting for root device." and lets me enter a command after (initramfs), but none of the commands seem to do anything.  Not that I would really know where to go from there if they did, but... I can't even get back to the desktop, much less the login screen.  Does this mean I have to do an uninstall of the OS because it had a bug?  If so, where do I start?

EDIT: In the process of reinstalling... will update when it's done.

EDIT2: Reinstalled and now have no problems... yet ;)  Thanks for the help!

---

