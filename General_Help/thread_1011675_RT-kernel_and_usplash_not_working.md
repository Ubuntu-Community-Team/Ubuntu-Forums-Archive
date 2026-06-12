---
title: "RT-kernel and usplash not working"
date: 2008-12-15
forum: General Help
---

### Post by maddis on 2008-12-15
Hi,

I have Ubuntu system and in it I have my own custom usplash. So far it's been working ok. Then I installed linux-rt - package to get rt-patched(mingo patched?) kernel to get more predictable scheduling. 

Now the usplash shows at startup for awhile (the progress bar does that left/right thingie), but then it disappears and either startup texts start rolling or nothing is shown. When booting normal kernel the startup texts shows and if booting to rt-kernel only blank screen with blinking cursor is shown.

If I don't install the linux-rt - package then the usplash works just fine. After installing linux-rt I tried to reinstall my usplash and regenerated initramfs, but no help. When shutting down the usplash is shown ok with both normal and rt-kernel.

I'm using Ubuntu 8.04. Anyone experienced similar problem with rt-kernel?

---

### Post by maddis on 2008-12-15
Okay, it seems that after reinstalling the system, the usplash works just fine with rt-linux. Not sure what was wrong in the old system.

---

