---
title: "Disable Notification: Mouse Battery Low"
date: 2009-03-24
forum: General Help
---

### Post by Taggart.BBS on 2009-03-24
Is there a way to disable the "Mouse Battery Low" notification from popping up? A google search reveals that this has been asked before, but has not yet been answered.

---

### Post by kanikilu on 2009-03-24
Seems to have been reported as a bug, but I don't see any fix or workaround...

[https://bugs.launchpad.net/ubuntu/+bug/163649](https://bugs.launchpad.net/ubuntu/+bug/163649)

Sorry this isn't more help, but maybe at least add to that report so hopefully this gets fixed...

---

### Post by Taggart.BBS on 2009-03-24
I appreciate the response, but that bug doesn't apply here. The mouse battery notification works as intended (only popping up when the battery is below 15%) I just want to turn it off.

Perhaps what this needs is a request for inclusion in the next version, a notification manager (that would also let you control when/what messages pop up.)

---

### Post by kanikilu on 2009-03-24
Oh I see. Yeah, I've found notifications in general are not very configurable yet.

Out of curiosity, if you run *gconf-editor* and then browse to apps > gnome-power-manager, is there anything in there that relates to the mouse battery (rather than a laptop battery)?

---

### Post by Taggart.BBS on 2009-03-24
Unfortunately, no, everything there is related to a laptop battery and shutting down at times of critical power. 

I tried a search in gconf-editor for both mouse and notif, but neither yielded results.

---

