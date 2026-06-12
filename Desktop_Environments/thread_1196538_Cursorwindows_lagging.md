---
title: "Cursor/windows lagging"
date: 2009-06-25
forum: Desktop Environments
---

### Post by enriquethepirate on 2009-06-25
Newly installed Kubuntu 9.04 on my Acer Aspire 4530 laptop (1.9 Ghz, 2GB RAM, nVidia GeForce 8200).  Cursor movement, window-rendering, loading webpages and scrolling are all extremely slow.

When I run 'top' the most CPU intensive processes are Xorg (usually around 20-50% CPU) and Konqueror (~10% which I'm using right now). Desktop effects are turned off, and I haven't been able to find a thread regarding display lag of similar or such astounding magnitude.

I haven't tested video since there are some flashplayer driver problems I haven't worked out yet.

Please let me know if there's any more info that might make this problem clearer.
What could be going on?

---

### Post by Monsieur Gonzalez on 2009-06-25
Are you using the restricted drivers for the nvidia card?

---

### Post by enriquethepirate on 2009-06-25
My apologies, problem resolved by going:

Applications -> System -> Hardware Drivers

...and then installing the recommended nVidia driver. <self-slap>

---

