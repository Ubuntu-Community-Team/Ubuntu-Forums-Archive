---
title: "Update killed Ubuntu"
date: 2010-05-17
forum: Desktop Environments
---

### Post by dlmcmurr on 2010-05-17
I setup Ubuntu 10.04 as dual boot, not using wubi, alongside Windows XP on my Gateway laptop. Got it working fine, ran the updates a week ago, and it was still happy. On power-up, it offered XP or ubuntu. When selecting ubuntu, it previously offered about 4 options. After updating, it added another ubuntu option for a newer kernel. Still, everything seemed to work well.

Got it out last night, updated Windows. Rebooted and updated ubuntu. It didn't require a reboot, so I worked for about an hour, then needed windows again. After finishing with Windows, I rebooted back into ubuntu.

That's where the problem started. I get the Windows/ubuntu selection menu from Windows, but now upon selecting ubuntu, it clears the screen and that's the last I hear from it. No disk activity at all and I never get the ubuntu selection screen, just a cursor in the top left.

I went through something similar to this when I used wubi several months ago. The reading I did about it suggested wubi was not the most reliable way to install ubuntu, so I waited until 10.04 came out and started the installation from scratch.

I'm about ready to get some ubuntu experience in other areas than just installation. I know I can just start over again, but I'd like to know what went wrong. I'm a pretty good Windows person and can read and follow instructions pretty well, plus I've gotten just enough linux experience to be dangerous maintaining and hacking my Tivos. If someone can give me some pointers, I'd appreciate it.

Thanks,
Dave

---

### Post by dlmcmurr on 2010-05-23
Just a quick update for anyone else that might experience this same issue. I reinstalled 10.04 and it still did the same thing, so I started looking at the steps for setting up dual boot with XP. It turns out that re-creating the ubuntu.bin file fixed the problem. Then when I applied the current updates, it died again. Once again, creating a new ubuntu.bin fixed it again.

I haven't researched what goes into this file, but evidently it needs to be rebuilt after certain updates?

Dave

---

