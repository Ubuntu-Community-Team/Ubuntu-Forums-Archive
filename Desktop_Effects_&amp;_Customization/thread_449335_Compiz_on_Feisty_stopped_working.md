---
title: "Compiz on Feisty stopped working"
date: 2007-05-20
forum: Desktop Effects &amp; Customization
---

### Post by Gannin on 2007-05-20
I'm running feisty with the latest nVidia drivers which I manually downloaded and installed from nVidia's website.

For a while, I had Compiz running by way of the Enable Desktop Effects button, and everything worked fine.  I got tired of having to turn it off to play games though, so I eventually just left it off.  Tonight I wanted to turn it back on, but when I did, the window borders / window manager disappeared.  All the menus faded and everything had the proper Compiz effects, but no window manager.

I tried reinstalling all the Compiz and desktop effects packages, but that didn't help.  Any ideas?

---

### Post by Kobalt on 2007-05-20
You must have lost your "ARGBGLX visuals" line in your section screen. Run this to get it back : ```
sudo nvidia-xconfig --add-argb-glx-visuals
```

---

### Post by Gannin on 2007-05-20
That did the trick, thanks :).

---

