---
title: "Changing resolution in Gutsy Kubuntu"
date: 2007-10-19
forum: Desktop Environments
---

### Post by TygerFish on 2007-10-19
I just put down a fresh install of Gutsy Kubuntu on a partition of my desktop.  Since I have a 21" monitor, the default (largest) resolution always makes things a bit too tiny, so I went to change it in the Settings panel.  I change to a lower resolution, click Apply, and the confirmation box (keep these settings?) pops up without any change.  Strange, I think, but I click okay.  Then, later, I log out and log back in and notice that the resolution has changed to what I'd set it as before.  I then confirmed that this behavior was replicable: the new resolution doesn't kick in until I log in again.  How might I go about fixing this?

---

### Post by TygerFish on 2007-10-26
I remembered that in some other KDE installations that I've seen, there is an option in the display settings to delay changes in resolution until either an X server restart or a fresh login (can't remember which).  The Kubuntu System Settings has no such option.  Maybe the problem is that this missing option is "stuck" in the wrong setting.  If so, how would I fix it?  (And, if not, where else should I look?)

---

### Post by gatewayasteroid on 2007-10-26
> **TygerFish said:**
> I remembered that in some other KDE installations that I've seen, there is an option in the display settings to delay changes in resolution until either an X server restart or a fresh login (can't remember which).  The Kubuntu System Settings has no such option.  Maybe the problem is that this missing option is "stuck" in the wrong setting.  If so, how would I fix it?  (And, if not, where else should I look?)

try editing this file:

/usr/share/applications/kde/display.desktop

at the end you should find something like "nodisplay=true", change it to "false" and restart KDE.

---

