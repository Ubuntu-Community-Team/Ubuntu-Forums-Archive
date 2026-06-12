---
title: "Wanted - Monitors properly configured before I login (12.10)"
date: 2013-10-22
forum: Desktop Environments
---

### Post by ArlieS on 2013-10-22
I've got a laptop that ideally would sometimes run standalone, but would normally run with 2 external monitors, both tilted 90 degrees. In that mode, I usually want it to ignore the laptop screen entirely. 

I'd like to have my login prompt displayed in a readable orientation, but it seems as if the screen arrangement is known only within the desktop environment, and needs to be configured separately for each account and each desktop environment used on the machine. 

I've been digging through what I can find about the login manager(s) - lightdm apparently being the default - and I've seen no sign of any ability to specify this - instead I'm apparently supposed to use some xrandr wrapper (varying by desktop environment) when logged into the specific desktop manager (unity, kde, etc.) to create and update an appropriate configuration file... which I usually don't know where to find to edit by hand. 

Is there a better way? I've got a rather flaky set of displays, and getting them configured right (repeatedly) is a major PITA, which has currently resulted in me running Windows on the offending laptop. [Difficulty recovering from the latest problem. *sigh*] I believe the issue there is that the hardware can't handle all 3 screens at once unless they are mirrored, and various tools tend to crash or freeze because of this.

At the very least, do these tools at least all understand the same config. syntax, or better yet the same config. file? This ought to be a property of X, which AFAIK is already running at the point of graphical login. (Except maybe for Unity, which seems to be moving away from X.)

---

