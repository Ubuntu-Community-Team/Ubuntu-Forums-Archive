---
title: "strange gnome login behavior - many file browsers"
date: 2007-04-01
forum: Desktop Environments
---

### Post by twelve17 on 2007-04-01
OS:  Ubuntu 6.10 -  Edgy Eft
Gnome: 2.16.1 (via System -> About Gnome)

I'm experiencing strange behavior when logging in to my gnome desktop. It happens with multiple users on the machine.  The behavior does not always occur, and I am unable to find a pattern on when it happens.

When I log in, between three and six "File Browser" windows pop up.  The number seems to vary.  Also, my background image doesn't show up.  If I log out and log back in, the desktop will typically work again (meaning, no "File Browser" windows show up, and the background image shows up).  I've gone to Preferences -> Sessions and disabled saving of the session to see if it matters.  I also deleted the "Default" session.  Neither seems to have any effect.

I've logged in via the console and did a "tail -f" on the following files while logging in, but did not see any messages that seemed relevant:

$HOME/.xsession-errors
/var/log/Xorg.0.log
/var/log/scrollkeeper.log

Any help would be appreciated.

Thanks,

--Alex

---

