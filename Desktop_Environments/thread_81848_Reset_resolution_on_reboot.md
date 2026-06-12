---
title: "Reset resolution on reboot"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Ma8thew on 2005-10-25
I have a 17 inch monitor (SyncMaster 173P). When I originally installed Ubuntu the max res was 1024x1280. I looked at the Ubuntu wiki and found [this page]("https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28resolution%29"). As explained on the Wiki, I added the extra resolution to my Xorg configuration files, but after reboot the desktop was using a virtual desktop, ie. when the cursor is moved to the edge of the screen, it scrolls around the desktop. If I select 1024x768 on the system settings, then change back to 1280x1024, then it will run at 1280x1024, however after a reboot it reverts to a the virtual scrolling desktop. How can I keep it at 1280x1024?:confused:

---

### Post by Ma8thew on 2005-10-25
Bump.

---

### Post by rickmans on 2005-10-25
It sounds like a similar problem I had. When you boot is your monitor turned on, or do you turn it on while / after booting? Try boot with your monitor turned on from the first moment.

---

### Post by Ma8thew on 2005-10-26
I always have the monitor turned on when it's booting. The resolution also reverts when I log off and on again.
[EDIT]
Fixed! Re-ran Auto-detection.

---

