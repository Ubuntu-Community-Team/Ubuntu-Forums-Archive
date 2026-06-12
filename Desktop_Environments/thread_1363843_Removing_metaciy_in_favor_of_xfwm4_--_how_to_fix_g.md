---
title: "Removing metaciy in favor of xfwm4 -- how to fix gnome-appearance-properties?"
date: 2009-12-25
forum: Desktop Environments
---

### Post by TwistedLincoln on 2009-12-25
I'm currently running xfwm4 instead of metacity.  I use "xfwm4 --replace" in sessions to automatically start it at login.  When one enables compiz from gnome-appearance-properties (from the Visual Effects tab), everything works as it should.  But when one uses the same dialog to switch back to "none," it wants to switch to metacity.

If I uninstall metacity, the system still works just fine, except now that dialog provides an error when switching to "none" rather than return to xfwm4.

Can anyone point me in the right direction on how to fix this?  Apparently the gconf string indicating the default window manager isn't used anymore, and editing the /usr/bin/gnome-wm file as noted in this thread ([http://ubuntuforums.org/showthread.php?t=88393](http://ubuntuforums.org/showthread.php?t=88393)) doesn't seem to have any effect.

Really, I could just use fusion-icon instead (which works fine), but in that case I'd like to completely remove the Visual Effects tab in gnome-appearance-properties so that users won't get error messages when they try to use it.

Can anyone offer any suggestions?

---

### Post by TwistedLincoln on 2010-01-19
Bump!  Can anyone give me a hand with this?

---

