---
title: "Possible Xorg/Kwin screensaver bug"
date: 2008-10-20
forum: Desktop Environments
---

### Post by DigitalXeron on 2008-10-20
Hi,

This isn't as much a support request as much as seeing if other people are having this issue, the issue being On the occasion after returning from having the screensaver running per-se overnight, Xorg is at that point taking 99-100% of the CPU, and kwin window decorations cease to function. The last foreground application remains functional as long as I don't attempt to switch windows. I am at this point required to restart X.

One workaround to restarting X I've had 50% success rate with is to SSH in from another machine and execute 'export DISPLAY=":0"' then 'kwin --replace'

I'm also curious if the latest ubuntu install fixes this fully (I'm operating on 7.04 at the moment)

---

