---
title: "Apps are unresponsive for a few seconds after waking"
date: 2009-05-02
forum: General Help
---

### Post by vegetto721 on 2009-05-02
Hi everyone,
I just recently updated from hardy to jaunty when I heard news of monodevelop 2.0 being available in the repositories. I updated in two steps, one to intrepid and another to jaunty. I did this so that my settings would remain (Does installing Ubuntu on an existing partition wipe all data or only update the relevant system files, can someone confirm this?). But I've noticed some behaviours that are different from hardy. 

1. VNC while running compiz leaves a black screen although it works (mouse and keyboard input are captured). On hardy, vnc would just lag while running compiz but the screens were still being refreshed.

2. After the screen turns off (due to idle) or locking the screen, when I wake it every program is unresponsive for a few seconds. This includes but is not limited to compiz, opera, amarok, gnome termina. It feels like each program is starting fresh, as though the processes were just created. After this initial unresponsiveness, the app is back to normal. This is a thrill killer especially when I'm running a relatively fast rig (e4500 @3.3, 2 GB ram, 7900 GS oc'ed, ...) for such lightweight applications. Has this been a common issue or has some of my configs quietly changed on me that I need to set?

I'd just like to add that there is significiant disk activity/trashing during this period. I have 1 GB for swap space but I don't think that's the reason. Unless jaunty has decided to throw everything into the swap space during sleep/idle and then load them back when awaken.

---

### Post by vegetto721 on 2009-09-22
I'd like to follow this up with a solution to the unresponsive/disk thrashing I was experiencing when my machine idles. It turns out that this has to do with the gnome personal screensaver (the one that you add --location= switch to in order to use a different folder for slideshow pictures). Upon upgrading, The directory path to the old folder no longer exist and I guess the behaviour that the screensaver took was to search the disk for who knows what. Need less to say, my disk feels much better now that the senseless violence against it has ended and everything is hunky dory once again.

---

