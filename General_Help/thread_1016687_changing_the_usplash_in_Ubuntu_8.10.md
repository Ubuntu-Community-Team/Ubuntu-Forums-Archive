---
title: "changing the usplash in Ubuntu 8.10"
date: 2008-12-20
forum: General Help
---

### Post by PatrickIIDX on 2008-12-20
ok I have this file: 87584-usplash-theme-greenman-64bit-20080820.tar.gz

and what is in this file is the .so theme

I tried a few copy and pastes to the .so file in the /usr/lib/usplash and stuff and none of this seems to work.

startupmanager will not start and let me select my usplash because I am dualbooting with other OS's. and if I use it, it just erases my boot enteries.

Is there any way I can replace the orange ubuntu bootup splash screen with this one?

---

### Post by mshipman on 2008-12-23
1. Copy the .so file for your splash screen to the /usr/lib/usplash directory.
2. Run ln -sf /usr/lib/[name of your .so] /usr/lib/usplash-artwork.so
3. Regenerate initramfs: sudo dpkg-reconfigure linux-image-`uname -r`
4. Pray.

Hope this helps!

---

