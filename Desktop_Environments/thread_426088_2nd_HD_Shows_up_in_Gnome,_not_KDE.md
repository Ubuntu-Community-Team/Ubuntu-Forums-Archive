---
title: "2nd HD Shows up in Gnome, not KDE"
date: 2007-04-28
forum: Desktop Environments
---

### Post by unnes on 2007-04-28
As a longtime casual Ubuntu user, when upgrading to Feisty I decided to also install kubuntu-desktop so I could play around with KDE. Overall, I loved it, perhaps more than Gnome, but one thing was distressing: My 2nd hard drive did not show up like it did in Gnome. There is no mention of it in any directory listings, device listings, or system settings that I could find

I don't know where the line is drawn between a desktop environment and the actual operating system, but this seems to be a KDE issue since the drive is recognized properly in Gnome.

Any suggestions on where I can look to enable the drive?

---

### Post by hellblade on 2007-04-28
Open a konqueror window and go to "media:/". Is it listed in there? Also is it listed in "/etc/fstab"?

---

### Post by unnes on 2007-04-28
Never mind, after going to System Settings > Advanced > Disk & Filesystems, I was able to mount the drive properly.

Everything works as it should now. Thanks anyways!

---

