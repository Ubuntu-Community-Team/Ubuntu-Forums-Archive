---
title: "Window borders on Beryl but not CF"
date: 2007-09-21
forum: Desktop Effects &amp; Customization
---

### Post by DDRFreak21 on 2007-09-21
I have a sort of different situation then most on the forum, I have had Beryl installed and running for nearly 6 months now and love it!

I was able to install compiz fusion without a problem but now the borders do not show on any of the windows.  I have already added the composite extension and both the following to xorg.conf
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"

I just find it weird that they work in one and not the other.

---

### Post by smartboyathome on 2007-09-21
Try *compiz --replace -c emerald* if you are on Trevino's repo, or *compiz --replace && emerald --replace* if you are on amaranth's.

---

