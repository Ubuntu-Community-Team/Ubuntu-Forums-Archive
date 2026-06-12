---
title: "screen lock problem after upgrading to KDE 4.2.2"
date: 2009-04-12
forum: Desktop Environments
---

### Post by bmorency on 2009-04-12
HI,

I have Intrepid 64-bit and I have just upgraded KDE to 4.2.2 and screen lock seems to be enabled even though I did not enable it. I checked under the screensaver settings and "require password to stop" is NOT checked. I have enabled that setting and than disabled it to reapply the settings but it will still ask for a password when I come back to my computer. Has anyone else heard of this or should I file a bug report?

Would I file it at launchpad or kde.org?

Thanks for any help.

---

### Post by Monsieur Gonzalez on 2009-04-12
Hi,

You might take a look at Powerdevil settings (Settings Manager, Advanced, Energy Management) and check that "Lock screen" is not enabled somewhere.

---

### Post by Dragonslicer on 2009-04-12
I have the same problem. "Lock screen on resume" is disabled in the Power Management settings.

---

### Post by inobe on 2009-04-12
i had that exact problem on opensuse with kde 4.2.2, i never found a way to disable it.

so this has to be some type of bug.

i couldn't even watch a dvd lols

i am using kubuntu 64bit with kde 4.2 now and i am not experiencing this

---

### Post by bmorency on 2009-04-12
> **Monsieur Gonzalez said:**
> Hi,

You might take a look at Powerdevil settings (Settings Manager, Advanced, Energy Management) and check that "Lock screen" is not enabled somewhere.

Thanks a lot. That fixed the problem for me.

---

### Post by Dragonslicer on 2009-04-13
For anyone else that sees this thread, there's one more place to set the session lock. In System Settings -> Advanced -> Power Management, there are profile assignments, even if you aren't using a laptop. The profile for a desktop is the one for "When AC Adapter is plugged in", which defaults to Performance. The Performance profile is set to lock the screen after being idle for 15 minutes. You can either change the Performance profile to not lock the screen, or create a new profile that doesn't lock the screen and use that profile instead.

---

