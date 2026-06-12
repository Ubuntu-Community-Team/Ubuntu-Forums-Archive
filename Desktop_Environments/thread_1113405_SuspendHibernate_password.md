---
title: "Suspend/Hibernate password"
date: 2009-04-01
forum: Desktop Environments
---

### Post by psyberpnk on 2009-04-01
I am trying to stop from needing a password when my computer comes back from standby or hibernating.

Currently, I have disabled passwords in the screen saver (per advice from IRC) and have unchecked everything in gconf:gnome_power_management_lock.

Anyone have any suggestions where to look next?
Thanks,
Psyberpnk

---

### Post by psyberpnk on 2009-04-03
Bump.  Anyone have any suggestions?

---

### Post by kellysontheroad on 2009-06-16
In 9.04 Jaunty Jackalope

Press ALT-F2
type gconf-editor
Go to apps / gnome-power-manager / lock
Un check suspend (and hibernate, and or the keyring options if you wish )

It's similar in the previous version, but the names have been arbitrarily changed

---

