---
title: "kcontrol + themes = !?!?!?!"
date: 2005-06-23
forum: Desktop Environments
---

### Post by CuRoi on 2005-06-23
Ok, well I've tried just about everything and none of its working.

The problem: kcontrol (Control Center) completely ignores all non-default themes. 
- I can't install new themes. It won't even recognize .themerc files.
- The only themes that are listed are the default kde ones.
- No kubuntu theme listed???!?!?! (& search for kubuntu.themerc proves fruitless)

Tried:
- Upgrading to kde 3.4.1
- Running kcontrol from kpanel in both 3.4.0 and 3.4.1
- Running sudo kcontrol from console in both 3.4.0 and 3.4.1
- Commented out "Theme=path/to/kubuntu/dir/here" in /etc/kde3/kdm/kdmrc

Everything I try results in the same thing: theme manager stays the exact same: default kde themes with NO kubuntu theme listed. I can create brand new themes... but not install new themes. 

If it helps I get this message when running sudo kcontrol:
Error: "/tmp/ksocket-jhartl88" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"


Any ideas??? 
TIA!!
~CuRoi

Edit: When I create my own themes from within kcontrol, weird things happen.
- Icons in the kpanel disappear. 
- Random settings don't get changed. (Even tho it says they are inside Theme Manager).

---

### Post by elsewhere on 2005-06-23
[QUOTE=CuRoi]Ok, well I've tried just about everything and none of its working.


If it helps I get this message when running sudo kcontrol:
Error: "/tmp/ksocket-jhartl88" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"


Any ideas??? 
TIA!!
~CuRoi

[/QUOTE]

Have you been having these problems running kcontrol as yourself, rather than with sudo?  Theme settings are user-level and don't require admin / root privileges, so there's no need to use sudo. In fact, if you alter theme settings under sudo you're actually modifying the desktop profile for the root account, and not your own.  Could cause some conflicts that way, maybe ?

Otherwise, if you're intentionally running kcontrol with admin privileges, try using kdesu instead of sudo.  Sometimes avoids conflicts.

EDIT:  Sorry, just re-read the message, saw that you did use kcontrol both ways so please ignore this post...  D'oh!

Cheers,
KV

---

