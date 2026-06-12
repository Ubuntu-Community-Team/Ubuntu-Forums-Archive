---
title: "Display out of bounds?"
date: 2011-02-05
forum: Desktop Environments
---

### Post by arhar on 2011-02-05
Hi,

I just put a HTPC together, it's a MSI 890GXM-G65 RT motherboard (on-board video, no video card) connected to a TV (SAMSUNG LED UN40B70) via an HDMI cable. I've put latest Ubuntu Desktop 10.10 on it. Installation went beautifully, the screen placed correctly, no issues. 

However, once it was actually running, the display is totally wrong. Looks like it's too far to the left and up - there's nothing on the screen except for background, at 1920x1080 resolution.

Once I change the resolution to lower, it works. 

How do I fix this? Any help would be appreciated

---

### Post by arhar on 2011-02-05
More info: the on-board card is ATI Radeon HD 4290. I've installed the latest ATI drivers and ATI Control Center.. didn't help.

---

### Post by arhar on 2011-02-05
Figured it out!

If you're reading this and have the same problem: Catalyst Control Center -> Display Manager (expand) -> DTV (1), go to "Adjustments" tab, and play around with "Scaling Options" - you have adjust underscan/overscan.

---

