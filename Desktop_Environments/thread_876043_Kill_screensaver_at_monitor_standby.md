---
title: "Kill screensaver at monitor standby?"
date: 2008-07-31
forum: Desktop Environments
---

### Post by allywilson on 2008-07-31
Hi all,
       I've just noticed that my screensaver (currently F-Spot scrolling through pics) continues to run even though my monitor goes into standby.

Is there a way to stop this? 
Does the monitor have a standby daemon that I could detect perhaps?

Just trying to save the planet - my cpu spikes with every new image displayed ;-)

Cheers

Ally

---

### Post by prshah on 2008-07-31
> **allywilson said:**
> 
       I've just noticed that my screensaver (currently F-Spot scrolling through pics) continues to run even though my monitor goes into standby.
Is there a way to stop this?

Take a look at the file "/usr/lib/pm-utils/sleep.d/20video"; maybe you should add suitable commands to the suspend_video() function?

I don't really know what I'm suggesting; it's a guess, but an educated/intelligent one. In other words: Use at your own risk.

---

