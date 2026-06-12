---
title: "SMB share problem"
date: 2005-09-12
forum: Desktop Environments
---

### Post by nkessler2000 on 2005-09-12
I'm experiencing a slight problem regarind mounting SMB shares.

Here's what's going on. I want to get a file off my old iMac, so I mount a share using smbmount, and that all works fine. However, when the iMac puts itself into sleep mode after twenty minutes of inactivity, a process on my Ubuntu box called smbiod starts using all my CPU. Waking the iMac up fixes the problem. Also I can't unmount the share until I wake the iMac back up. Is there anything I can do about this, or is it just a bug in Samba?

---

### Post by mlomker on 2005-09-12
Sure sounds like a bug.  If your iMac is plugged into outlet power then I'd recommend just disabling power management as a quick fix.

---

