---
title: "Unity Problems When Switching User"
date: 2015-01-19
forum: Desktop Environments
---

### Post by KenF on 2015-01-19
1.  I'm using Ubuntu 14.04 with Unity.  Everything is a default install (lightdm, etc.).

2.  When I switch from one user to another, it now takes a long time.  In the process of switching users, Unity (or the DM?) completely turns off the monitor.  Specifically, the monitor goes through the steps of looking for a signal on the various inputs (HDMI, VGA, DVI, etc.).  As an aside:  by "long time" I'm talking 10 seconds ... which is the same amount of time as a reboot!!!

3.  This only started happening after an update 3 or 4 weeks ago.  Before that, user switching was pretty quick.  [ My only issue at that time was that after about a week of use compiz would freeze/lockup and I would need to restart or kill compiz et al.]

4.  I should note that this only happens when switching users.  If I'm just unlocking and using the same session as the last one used, there is no issue.

Thanks in advance for any help.  My wife now uses this machine more than the Mac so the slow (and flashing monitor) for user switches is becoming increasingly annoying.

KenF
[I've received no replies, but I'll add some more info in case someone else has this issue.

We've given up using "switch user" via the unity dropdown and/or greeter.  There are usually two or three (home users) so we just use ctrl-alt-f7 (or ctrl-alt-f8 or ctrl-alt-f9) to choose the appropriate X11 session.

The reading I have done suggests it is a problem with the new unity greeter.  It's a bit uglier, but one can use other greeters e.g.  lightdm-gtk-greeter.  It would probably fix this problem, but the above workaround is working well enough for us.
]

---

