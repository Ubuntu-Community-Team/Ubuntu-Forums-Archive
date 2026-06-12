---
title: "slow window controls and bad sleep/stand-by mode"
date: 2009-12-23
forum: Desktop Environments
---

### Post by john.yarger on 2009-12-23
My HP laptop suffered the following symptoms after a fresh install of Ubuntu 9.10 64-bit:
- Window controls (minimize, maximize, close) were slow in responding -- delayed up to 3-5 seconds following mouse button release.  Moving windows worked properly.
- Upon entering standby / going to sleep, the laptop would not come back and appeared to remain off despite pushing the on/off button.

Since my previous install of 9.10 had worked properly on this laptop, I searched for what was different.  After some troubleshooting, I realized that the GPL video driver was still installed for my nvidia graphic chip.  Upon installation of the proprietary Nvidia driver, the symptoms disappeared and the laptop worked as expected.

---

