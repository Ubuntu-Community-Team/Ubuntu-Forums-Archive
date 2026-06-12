---
title: "startup apps aren't running after start up anymore"
date: 2012-01-17
forum: Desktop Environments
---

### Post by oneiota on 2012-01-17
A few days ago I suddenly lost my network connection and nm-applet in the middle of a skype call.  After rebooting, I've found that even though nm-applet is one of the applications in the Startup Applications list, it doesn't appear to be running after rebooting. 

At first I thought this was a problem with the nm-applet or the Notification Area as there are several posts about problems with these disappearing.

However, in my case, **none** of the applications listed in the Startup Applications list seem to be running after logging in, even the GNOME login sound is not running after login.

Any idea how to fix this, or what further debugging I should look to do?

---

### Post by Krytarik on 2012-01-17
Try removing the content of "~/.config/gnome-session/saved-session".

Hope that helps.

---

### Post by oneiota on 2012-01-17
> **Krytarik said:**
> Try removing the content of "~/.config/gnome-session/saved-session".


Thanks for responding.  I just tried removing the contents of that directory - there were three files there.  Unfortunately, the startup apps are still not running after rebooting.

Further ideas (or things to check) welcome!

---

