---
title: "[SOLVED] Gnome error, did KDE sneak in unbidden?"
date: 2007-10-29
forum: Desktop Environments
---

### Post by pinkunicorn on 2007-10-29
I'm tinkering with an almost newly installed Gutsy system. After a reboot, I got an error dialog at login saying

```
An error occured when starting the GNOME configuration demon.

Some things like themes, sound or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to start the configuration demon the next time you log in.

```

(parts of this message reverse translated from Swedish, so it may not be entirely accurate)

When I try to start for instance the theme configuration window, I get:

```
Can't start the configuration handler "gnome-settings-daemon'.
If the GNOME configuration handler isn't running some settings can't be applied. This may indicate a problem with Bonobo or that a configuration handler from something else than GNOME (like KDE) is already running and is in conflict with the GNOME configuration handler.
```

(likewise translated)

After closing this window, the theme configurator does appear.

Also, my desktop looks different than before (different icons in many places) and the window titles are now blue instead of brown.

I haven't done much in the menus, so I doubt that I've caused anything there.

I have installed a number of new packages, including at least k3b, so in some sense I have touched KDE. I never intended for it to take over my system, though. My previous Feisty system had k3b installed on it without any of these problems. 

How can I get back to using GNOME again?

---

### Post by pinkunicorn on 2007-10-30
Is there really no one out there who knows what's happening here?

---

### Post by pinkunicorn on 2007-11-15
A couple of reboots later, this problem just silently disappeared. *shrug*

---

### Post by lavajumper on 2007-11-15
I got this error after an upgrade, rebooting one more time cleared it out. It hasn't returned.

---

