---
title: "No monitor power control function since kde4.x/8.10"
date: 2008-11-21
forum: Desktop Environments
---

### Post by johnnyhop on 2008-11-21
Since upgrading to 8.10/KDE4 monitor won't suspend, standby or power off once logged in.  Monitor will standby at login splash screen.

Late April upgrade to 9.04 problem persisted.  Late May did clean install of 9.04, now both screensaver and monitor power control work!

---

### Post by GameManK on 2008-11-22
Have you tried the settings in System Settings > Display > Power Control

---

### Post by johnnyhop on 2008-11-22
Yes, I've tried enabling power control w/standby, suspend and power off at progressively increasing time intervals, the same time interval and any two disabled and one enabled.  From my understanding of the three settings, suspend is what I prefer to use and was working prior to 8.10/KDE4.  This is the case on both the home and work Kubuntu systems.

---

### Post by yamick on 2008-12-02
I have the same problem and I've tried different configurations - the only effect is that my screen saver still working and monitor can't rich standby mode. I think it's probably KDE4.1 problem.

Any ideas how to solve this problem...

---

### Post by betnexrel on 2008-12-07
Seems there are still problems even with KDE 4.1.3:

[https://bugs.kde.org/show_bug.cgi?id=165368](https://bugs.kde.org/show_bug.cgi?id=165368)

---

### Post by johnnyhop on 2008-12-24
It appears KDE 4.1.x supports screensaver or power saving, not both. As updates occur I'll keep checking or if I ever toss this CRT monitor power saving is less of an issue.

---

### Post by jtiangco on 2009-02-02
Try installing kpowersave.  It worked for me.

---

### Post by txcrackers on 2009-02-03
Monitor powersave came back in 4.2 - but there's a very interesting bug (no link handy): you have to turn **off** the screensaver.

I've got both the "normal" monitor powersave settings and the new power management applet (PowerDevil?) set to the same timeouts, so I'm not sure which one (or both) are actually turning off the monitor. But it *does* turn off, which is the major point.

---

### Post by dalesd on 2009-02-16
> **johnnyhop said:**
> It appears KDE 4.1.x supports screensaver or power saving, not both. As updates occur I'll keep checking or if I ever toss this CRT monitor power saving is less of an issue.

I have this bug too, and this workaround works for me.   Disabling the screensaver makes my monitor turn off like it should.

But I also need the screen to lock when the computer is idle.  How else can I do that without a screensaver?

---

### Post by txcrackers on 2009-02-17
> **dalesd said:**
> But I also need the screen to lock when the computer is idle.  How else can I do that without a screensaver?
There's an option in the Power Management in System Settings - go to the *Edit Profiles* section, select whichever profile you want to lock the screen in (as a desktop system, I'm only using the Performance profile). The "When the system is idle for more than..." option is essentially the same as the screen saver lock.

---

### Post by dalesd on 2009-02-17
> **txcrackers said:**
> There's an option in the Power Management in System Settings - go to the *Edit Profiles* section, select whichever profile you want to lock the screen in (as a desktop system, I'm only using the Performance profile). The "When the system is idle for more than..." option is essentially the same as the screen saver lock.

Maybe I'm still a KDE noob, but I can't find the section you're describing.
From the K menu I go to Applications -> System -> System Settings, and there's no power management there.

---

### Post by txcrackers on 2009-02-18
It's in 4.2 - for 4.1.x I believe you have to install "powerdevil" (you might want to research that one).

---

### Post by johnnyhop on 2009-03-24
> **jtiangco said:**
> Try installing kpowersave.  It worked for me.

I still have to disable the screen saver in System Settings>Desktop>Screen Saver, uncheck Start automatically.  Is there a winning combination of settings between KPowersave and System Settings that enables screen saver then monitor standby?

Late April upgrade to 9.04 problem persisted. Late May did clean install of 9.04, now both screensaver and monitor power control work!

---

### Post by johnnyhop on 2009-06-18
With the online distribution-upgrade to 9.04 neither screensaver or monitor power saver settings would have any effect.  A clean install of 9.04 fixed both screensaver and power settings.  Just goes to show you, a clean install while more trouble, just plain does the Ubuntu experience more justice and satisfaction.

---

### Post by at165db on 2010-03-26
Thanks, this also fixed my issue.  I'm going to miss Asciiquarium!

So here is a quirk, I've not tested yet.  We have essentially 2 different places to set the display power management.
One is in the System Settings->Advanced->Power Management->Edit Profiles->Screen.
The other is System Settings->Display->Power Control.

I hope the lowest time wins.

---

