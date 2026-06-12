---
title: "Screen tearing on desktop, video and browser"
date: 2014-11-12
forum: Desktop Environments
---

### Post by f(fanta) on 2014-11-12
I get constant screen tearing when moving windows around, scrolling Mozilla Firefox pages, watching videos on YouTube. 

Graphics adapter is an NVIDA GeForce GTX-670. Ubuntu version 14.10 64-bt. I have two displays connected.

Action I have taken to try to solve the issue:
- Under CompizConf, enabled "OpenGL > Sync to VBlank"
- Under NVIDIA X Server Settings, enabled "X Screen 0 > OpenGL Settings > Sync to VBlank" and "Allow Flipping"
- Installed different video drivers (NVIDIA binary driver 331.89, manually installed latest driver from NVIDIA 340.58)

Any advice?

Thanks!

---

### Post by f(fanta) on 2014-11-25
After re-installing ubuntu, I am finding that with Nouveau there is no screen tearing, therefore I will remeain with it.

---

### Post by megmamusic on 2014-12-12
Same issue here with xubuntu on several machines with different graphics cards.. Driver doesnt solve the issue, i think its the compositing manager.

---

