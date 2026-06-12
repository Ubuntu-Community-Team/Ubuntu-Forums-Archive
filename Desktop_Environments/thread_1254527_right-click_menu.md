---
title: "right-click menu"
date: 2009-08-31
forum: Desktop Environments
---

### Post by 01000111 on 2009-08-31
Hey there... I'm running Xubumtu 9.04 and just installed Compiz and Emerald.  Everything works fine, except if I right-click on the desktop, I get a menu that includes "Change Desktop Background".  If I click on that, it brings up the Gnome desktop manager and messes up a bunch things, including my mouse buttons ( I normally have the buttons set for  left-handed, but they get switched back to right-handed. ).

If I click Settings, Desktop, I get the xfce desktop manager and all's well.

Ok, I know the simple solution... "don't click on that!", but what's the correct solution here?    Shouldn't there be a xfce right-click menu?

Thanks in advance.

Binary-G

---

### Post by Brandon Williams on 2009-08-31
It sounds like you may be running nautilus in the background. Use ps or the Processes tab in the System Monitor to figure out whether or not that is the case.

If I'm correct and you _are_ running nautilus, we'll have to figure out what's starting it. The most likely culprit is a startup file in your ~/.config/autostart/ directory. The next most likely is the session manager. Both of these can be checked from the 'Settings -> Session and Startup' dialog.

First, check the 'Application Autostart' tab. Is there an entry there for nautilus? If so, uncheck that one and you should be OK. If not, then look at the 'Session' tab. Is nautilus listed there somewhere? If so, highlight the entry and click the 'Quit Program' button. After nautilus has stopped, click the 'Save Session' button.

If either nautilus is not running or the above suggestions do not correct the problem, then give us an update and someone will help you diagnose further.

---

### Post by 01000111 on 2009-08-31
> **Brandon Williams said:**
> .... If not, then look at the 'Session' tab. Is nautilus listed there somewhere? If so, highlight the entry and click the 'Quit Program' button. After nautilus has stopped, click the 'Save Session' button.


That did it.  Many thanks!!!

01000111

---

