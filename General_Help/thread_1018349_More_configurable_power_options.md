---
title: "More configurable power options?"
date: 2008-12-22
forum: General Help
---

### Post by Fox5 on 2008-12-22
I'm currently running Ubuntu 8.10 with Boxee as a media center. However, I don't like the idea that it's on all the time. I'd like it to automatically suspend/hibernate/power off after a specific amount of time but a few problems:
Suspending through the OS (and not using Boxee's built in option) causes boxee to lock up.
Hibernating causes certain functionality of Boxee to randomly fail. Sometimes it loses internet connectivity, sometimes it loses track of lirc input, but in general it's bad.
Ubuntu provides no options to automatically power off. Since the other two options don't work, an auto power off after a certain amount of time would be acceptable, though I might need to do some boot time optimizing.

Additionally, the time limits ubuntu allows for its power settings are too small. It will only allow up to a 1 hour time limit, which is less than the time it takes to finish watching a DVD. It's very likely there would be no input for up to 2 hours in that case.

---

### Post by ajcham on 2008-12-22
Does Ubuntu regard the computer as inactive while watching a DVD? Although there is no input, the system usually identifies DVD viewing as active behaviour (screensavers don't kick in, for example).  Although, I watch DVDs in VLC, rather than Boxee, so maybe that makes a difference.

---

### Post by Fox5 on 2008-12-22
I'm not sure how boxee effects the activity settings. If boxee does indicate the system as being in use, then that's also no good, since then the system would never enter a low power mode. (though I set the timer to 1 minute and it would suspend, even as I'm sending input from the remote control, so I guess boxee and lirc don't count as activity)

---

