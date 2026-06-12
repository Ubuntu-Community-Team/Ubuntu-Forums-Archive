---
title: "overlay scrollbar for synaptic (root)"
date: 2015-12-17
forum: Desktop Environments
---

### Post by phorminx on 2015-12-17
With xubuntu 15.10, synaptic run as root gives me overlay scrollbars, though the package overlay-scrollbar is not installed.  How can I get regular (non-overlay) scrollbars instead?  If I run synaptic as regular user, I get the non-overlay scrollbars I want; but of course I only need synaptic as root.  I haven't found other applications that give me overlay scrollbars (neither as root nor as regular user).  But as root I hardly need anything else besides a plain terminal and synaptic.  There has been no such problem with xubuntu 14.04.
Thanks for any help. Overlay scrollbars suck!

---

### Post by buzzingrobot on 2015-12-19
Try adding "export GTK_OVERLAY_SCROLLING=0" to ~/.profile" and starting a new session.

---

### Post by phorminx on 2015-12-20
thank you, you saved my day

---

### Post by phorminx on 2015-12-21
> **buzzingrobot said:**
> Try adding "export GTK_OVERLAY_SCROLLING=0" to ~/.profile"

I looked more carefully into this:
The file /etc/X11/Xsession.d/56xubuntu-session contains the line
[INDENT]export GTK_OVERLAY_SCROLLING=0[/INDENT]
which is the reason why as regular user I already had this setting in my environment. I guess that if I run synaptic as root, this file is not processed so that I missed this setting.  Oh well.

---

