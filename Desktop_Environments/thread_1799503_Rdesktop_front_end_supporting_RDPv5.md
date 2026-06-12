---
title: "Rdesktop front end supporting RDPv5"
date: 2011-07-07
forum: Desktop Environments
---

### Post by MaryW on 2011-07-07
Hello all,

By default, rdesktop uses RDP version 5. However, all the front-end GUIs that I've found for Gnome (Gnome-RDP, TSClient) seem to run rdesktop with a '-4' option, bringing it down to RDP version 4.

Can anyone either recommend a UI that does not do this (curious if there is a reason why they all do?) or a way to get around this? I've looked at the .tsclient/*.rdp files and the .gnome-rdp.db sqlite database to see if I could change the version 4 to version 5, but it doesn't look like I can hack my way around it.

This seems like an easy thing to fix, so I'm a bit baffled why the option isn't there. Should I submit a bug/feature request?

Thanks,
Mary

---

