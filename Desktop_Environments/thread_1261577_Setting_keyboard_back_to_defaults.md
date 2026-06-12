---
title: "Setting keyboard back to defaults"
date: 2009-09-08
forum: Desktop Environments
---

### Post by ptader on 2009-09-08
I can't seem to set the Alt/Win key behavior back to its defaults in gnome.  No matter if I choose the "Default" radio button and/or "Reset to Defaults" (see image), the setting persist - remapping my Alt key to Ctrl.  It must be in a system-wide config file because it effects multiple users, even newly created users.

Where are the system keyboard settings configurations are saved?  I've been looking through the /etc directory to no avail.

Ubuntu 9.04

Paul

---

### Post by matt! on 2010-03-28
Hi,

Did you ever solve this? I have the same thing.

I tracked down the preference to ~/.gconf/desktop/gnome/peripherals/keyboard/kbd/%gconf.xml

but the setting persists even after trashing that from the recovery/root prompt.

Any ideas?

Thanks,
matt

---

