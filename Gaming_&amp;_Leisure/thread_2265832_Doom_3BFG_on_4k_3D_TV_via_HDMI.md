---
title: "Doom 3BFG on 4k 3D TV via HDMI"
date: 2015-02-18
forum: Gaming &amp; Leisure
---

### Post by MikeCyber on 2015-02-18
Hi
I've connected my huge 3D 4K LG TV via HDMI. Now Doom3BFG only displays on my PC but not on the TV.
What to do? I've got a GTX770. X-Plane for ex. is ok.
Many thanks

---

### Post by Gustaf_Alhll on 2015-02-18
The issue is simple: Multi-screen.

Open the system settings (Or enter "unity-control-center" in the terminal as I do) and go to the screen settings. On the top, you should see two squares that's differently colored. That means your desktop has expanded instead of mirrored to the other screen. Right below it, there should be a checkbox with the text "Mirror screens". Check that, and apply.

For short: System settings >> Screens >> Mirror screens, check that.
Remember that the names I specified could be different from what you'll actually see, since I have a swedish desktop.

---

### Post by MikeCyber on 2015-02-18
Thanks. Now Doom3BFG won't start but I'll try tomorrow to remove preferences and see if that helps. Curious about Doom in 3D. :P

---

### Post by tgalati4 on 2015-02-18
Check /var/log/Xorg.0.log for errors.  It's possible that you have run out of video RAM or super desktop pixels (8096 x 8096) perhaps because of the way 3D is handled.  Try lower resolutions for the TV, then ramp up until it fails.

```
grep EE /var/log/Xorg.0.log
```

---

### Post by MikeCyber on 2015-02-19
I've managed to get it to run on my TV by playing around with nvidia-settings. But as soon as I've set 3D on I got a black screen. Even now rebooting back on my pc monitor the screen is still black.
Any ideas on what to change back? Can't find any config files.
Anyone got this game running on a 3D TV?

---

