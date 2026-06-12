---
title: "gpilot-install-file doesn't actually copy file"
date: 2009-01-12
forum: Desktop Environments
---

### Post by robthebob on 2009-01-12
Hi,

I'm trying to use gpilotd to sync with my Handspring Visor Palm. gpilotd recognises when the hotsync button is pressed and happily backs up everything on the Palm to my local, specified, directory. However, when I try to copy a .pdb file onto the Palm using gpilot-install-file (with either --now or --later), it returns a corba message about being entered into the queue, but when I actually sync, nothings gets copied onto the Palm.

Any thoughts?

Cheers,
Robin

---

### Post by Dngrsone on 2010-02-16
I had the same issue.

Go to System/Preferences/PalmOS Devices and hit the Conduits tab for your device.  Make sure the conduit File is enabled.

---

