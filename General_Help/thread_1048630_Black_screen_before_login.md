---
title: "Black screen before login"
date: 2009-01-23
forum: General Help
---

### Post by Gibbs on 2009-01-23
Hi all,

Having some serious problems. I can't get to the login screen on Ubuntu. The terminal says it's starting the Gnome Display Manager, flickers back, says something about executing binary formats and then the monitor goes blank...

CTRL-ALT-BACKSPACE and CTRL-ALT-F# doesn't work. The monitor screen simply goes blank.

I figured it's most likely a problem with my monitor or graphics. I've played about with xorg.conf (resetting it, using backups etc) to no avail.

When I boot into recovery mode and run ```
/etc/init.d/gdm start
``` it's fine (except DBUS and my internet doesn't work, which restricts what I can do).

I've searched through system logs and xorg logs but haven't seen anything worth noting.

Any help or suggestions welcome!

**Edit:** I have changed the resolutions supported to 1440x900 (my resolution in xorg.conf) but it makes no difference but I'm not ruling out the Ubuntu is trying to work in a resolution my monitor doesn't support.

---

