---
title: "Sessions not restoring properly on login"
date: 2007-06-04
forum: Desktop Environments
---

### Post by QwUo173Hy on 2007-06-04
I choose the "Save the current session" in the Sessions dialog, as well as "Automatically save changes", but it's not working.

[LIST=1]
[*]Some applications I no longer want are still loading on startup.
[*]Some applications I want, do not load.
[/LIST]

For #1) Exaile was starting at startup and I no longer want it so I unchecked the box in the Startup Programs list. No effect. So then I deleted it from the list. No effect. I also tried closing the application and saving the sessions. No effect.

For #2) When I save the session, GMail notifier does not start. I haven't tried adding it to the list yet because.. I'm afraid :)

I also get 2 amarok loading instead of one. I never had 2 amaroks running at the same time to begin with.

I think the Sessions application is very buggy and I should report a bug but I'd like some feedback first before I go adding to the bugs there - just to be sure it's not just me.

Thanks for listening,
Jarlath

---

### Post by Obor on 2007-06-04
I think its related to this bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/34321](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/34321)

---

### Post by QwUo173Hy on 2007-06-04
Thanks Obor, the workaround the reporter posted worked for me. I deleted ~/.gnome2/session and logged out and back in. Then I just added whatever I wanted to the list instead of using the broken Save feature.

The effects didn't kick in for another two logins and I'd say I'll have more trouble again, but they are aware of it upstream so I guess there will be a fix at some stage. Although with a priority of normal, that could be  a while

Thanks again Obor,
Jarlath

---

