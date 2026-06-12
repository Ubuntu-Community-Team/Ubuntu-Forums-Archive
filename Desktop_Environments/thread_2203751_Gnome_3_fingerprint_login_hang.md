---
title: "Gnome 3 fingerprint login hang"
date: 2014-02-04
forum: Desktop Environments
---

### Post by danagoyette on 2014-02-04
I'm using Gnome 3 on Ubuntu 13.10, with GDM (so I can have lock-screen notifications).

On my system with Intel Haswell graphics, if I log in with my fingerprint reader, the system stays stuck at the login screen, forever.
If I log in via password, the desktop logs in fine.  I can also log into unity via fingerprint, I believe.

Just today, I switched to the console and killed off my user's processes one by one, to try to figure out what was hanging.  The desktop unfroze only once I killed ibus (ibus-daemon, I think).
Does anyone else see this behavior?

EDIT: I may just remove ibus, since I'm not actually using it -- but better to find out if it's just me.  
I'm also having some odd behavior in GDM: sometimes, I'll click my username, and the window will just disappears for a few seconds, then reappears saying "verification timed out".

---

