---
title: "GDM (Face Browser) question"
date: 2007-12-26
forum: Desktop Environments
---

### Post by BreathEasy on 2007-12-26
I've set up my mother's laptop with Ubuntu, and have been trying to tweak it to reduce the number of extra steps necessary to perform most tasks. One thing I've been trying to find out is how to optimize the GDM face browser.

In XP, if there's just one user account and the account is password protected, the login screen will automatically select the user's name on startup, so all that's necessary is to start typing the password. Using the GDM face browser in Ubuntu however, with the same scenario, the user has to first select the account from the list by clicking it, and then enter a password (or type in the name themselves).

Is there a way so that when GDM starts, it *automatically* selects a particular user account, ready for a password, bypassing the need to click it first (like XP does)? Not a huge deal, but it would be nice if this was possible.

(Note: I'm **not** talking about auto-login, because that bypasses the need to type in a password and we still want that protection. I just want it to require a password immediately instead of a username first.)

---

### Post by smartboyathome on 2007-12-26
You can configure GDM to automatically log her in. I do this because I don't really have much to fear because I don't travel much with my laptop (people wouldn't be likely to steal it). But, anyway, edit the login preferences so that it automatically logs her in, and then you are done.

---

### Post by BreathEasy on 2007-12-26
Like I mentioned before, I'm not talking about and am not interested in the auto-login functionality. I just want GDM to automatically select the username from the list, ready for entering a password, like XP (and Vista for that matter). It's a subtle GUI feature Microsoft realized was useful, so I was thinking maybe there was a capability in GDM as well.

---

