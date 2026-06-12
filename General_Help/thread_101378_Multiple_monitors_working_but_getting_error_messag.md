---
title: "Multiple monitors working but getting error message"
date: 2005-12-09
forum: General Help
---

### Post by pjman on 2005-12-09
Hello,

I followed the guide on wiki ([https://wiki.ubuntu.com/XineramaMultipleMonitors](https://wiki.ubuntu.com/XineramaMultipleMonitors)) to get a second monitor working with my Dell D600 using the ATI video drivers. I now have to separate monitors (works really well!) but I'm unable go get into System > Preferences > Screen Resolution. I get this error message:

"The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."

Any ideas?

Thanks,
-pjman

---

### Post by blueplazma on 2005-12-09
It seems Xorg is unable, as it said, to handle changing the resolution of multiple monitors without a restart.  Unless you need to change the resolution, just don't launch that app.  If you do, you'll need to perform some edits in your xorg.conf

---

