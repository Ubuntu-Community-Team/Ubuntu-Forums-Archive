---
title: "[SOLVED] Frozen Mouse"
date: 2009-01-06
forum: Desktop Environments
---

### Post by WelterPelter on 2009-01-06
I just reinstalled 8.10 on a system that was previously running it fine.
My /home is intact from the earlier system.
When I boot from the hard drive, the mouse is totally frozen.
If I boot from the live CD, there's no problem with the mouse.

I figure this might be due to the custom mouse cursor I had in my old setup (maybe some configuration file in /home no longer working correctly). 

Any hints as to how to fix this?

---

### Post by WelterPelter on 2009-01-06
Well, it turns out not to be the configuration files. I overwrote all of /home.

Mouse was still frozen until I rebooted and switched to an earlier kernel. 

Then I was able to download all updates and reboot again.

Now the mouse works.

---

