---
title: "xfce-session and X crashing on logout."
date: 2013-08-21
forum: Desktop Environments
---

### Post by jimford on 2013-08-21
After using the xfce desktop for at least 10 years with no problems whatsoever, I'm finding that after 'upgrading'(!) from Xubuntu 12.10 to 13.04 it always crashes on logout. On rebooting I get a report that xfce-session has crashed, and sometimes that Xorg has crashed.

I see that various permutations of this and similar problems have been posted in the past, with varying 'fixes' - but is there a definitive fix for the problem now, or do I have to change the desktop to Gnome or KDE?

Jim

---

### Post by Toz on 2013-08-23
A couple of things:

1. Try clearing out your saved sessions cache. (Settings Manager -> Sessions and Startup -> Session and click the "Clear saved sessions" button). Then try logging out.
2. Post back your ~/.xsession-errors.old log file to see if there is any diagnostic information:
```
pastebinit $HOME/.xsession-errors.old
```
...and post back the link that is generated.

---

