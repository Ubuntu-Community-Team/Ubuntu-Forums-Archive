---
title: "Ubuntu Fades Away for No Reason"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by FreedomFromNinjas on 2007-05-19
I'm a longtime Windows user and linux dabbler.  I installed Ubuntu 7.04 last night, and I'm having a problem: twice now, Ubuntu decided to fade my entire monitor to black over the course of 3 or 4 seconds, then when it's done, it immediately goes back to normal, like nothing ever happened.  I was actively using the computer in both instances (once I was in the middle of typing a forum post), so I can safely assume it's not the screensaver kicking in.  I have an nVidia GeForce 6800 and two monitors, running two X sessions using the nvidia-settings utility.

EDIT:  more info:  While the screen is fading, no applications respond, but the mouse remains free and visible.
(I think I chose the wrong section of this forum for this post, sorry if that's the case).

EDIT2: Hypothesis: could the idling X session on my second monitor be activating the screen saver on both sessions?

EDIT3: Confirmed, my extra idle X session is activating the screen saver in both sessions.  I've worked around the issue by disabling the screen saver, but it's not really a fix.

Thank you.

---

### Post by veloce on 2007-05-20
> **FreedomFromNinjas said:**
> I'm a longtime Windows user and linux dabbler.  I installed Ubuntu 7.04 last night, and I'm having a problem: twice now, Ubuntu decided to fade my entire monitor to black over the course of 3 or 4 seconds, then when it's done, it immediately goes back to normal, like nothing ever happened.  I was actively using the computer in both instances (once I was in the middle of typing a forum post), so I can safely assume it's not the screensaver kicking in.  I have an nVidia GeForce 6800 and two monitors, running two X sessions using the nvidia-settings utility.

EDIT:  more info:  While the screen is fading, no applications respond, but the mouse remains free and visible.
(I think I chose the wrong section of this forum for this post, sorry if that's the case).

EDIT2: Hypothesis: could the idling X session on my second monitor be activating the screen saver on both sessions?

EDIT3: Confirmed, my extra idle X session is activating the screen saver in both sessions.  I've worked around the issue by disabling the screen saver, but it's not really a fix.

Thank you.
yep, its a bug.  It's been reported.

---

