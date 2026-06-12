---
title: "Kdm not bringing up anything - and the solution"
date: 2005-04-27
forum: Desktop Environments
---

### Post by Disorder2 on 2005-04-27
Just in case anybody else comes across this really strange one..

Problem:

both Gnome and KDE start and work fine from gdm .
When changing the window manager to kdm there is the login splash. You would enter username, password, press enter and then - nothing for a while, afterwards same login splash again. And again.
The ~/.xsession-err says:
"run_parts: Command not found"
And right: It isn't there

Solution:
open /etc/X11/Xsession.d/30xorg-common_xresources

Replace line 9:
RESOURCEFILES=$(run_parts $SYSRESOURCES)

with
RESOURCEFILES=$(run-parts $SYSRESOURCES)

Bottom Line:
Yes, it does look stupid
No, I have no clue if this is the recommended way but
yes, it works
 \\:D/

---

