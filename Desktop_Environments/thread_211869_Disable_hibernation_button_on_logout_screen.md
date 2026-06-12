---
title: "Disable hibernation button on logout screen"
date: 2006-07-09
forum: Desktop Environments
---

### Post by RawMustard on 2006-07-09
Can it be done?

On 4 systems at work, hibernation just borks the machines and people insist on clicking the hibernate button.  If I could hide it, then I don't have to keep telling them why it doesn't work.  On my own system at home, it sort of works, but it seems slower to bring the machine out of hibernation than to just do a strait shutdown and start up again, so what's the use of it?

---

### Post by Viper666 on 2006-07-09
Hibernating and restoring from hibernate is generally faster than a cold boot and, if necessary, can be done without user interaction (unlike shutting down, which often requires the user to specify if open documents should be saved). To use hibernation the hard disk needs to have at least as much free space as there is RAM on the system.

I tryed it once and did shutdown but didn't boot. I had to reboot so i don't think it's working, or is chipset dependent.

---

### Post by RawMustard on 2006-07-09
All the machines I'm taking about have 2 gig or more of ram and 250 gig drives, so plenty of free space :)

> or is chipset dependent.

Hardware support for it is a big problem I think, it never worked well on windows either.

I would sooner have the ability to completely hide it from users until such time as it works 100% of the time, it's not a necessity IMHO.

---

### Post by sup on 2006-07-10
```
gconf-editor
```
/apps/gnome-power-manager uncheck can suspend and can hibernate

---

