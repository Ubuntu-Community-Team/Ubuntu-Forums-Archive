---
title: "Lost support for Direct Rendering?"
date: 2007-07-13
forum: Desktop Effects &amp; Customization
---

### Post by sra136 on 2007-07-13
Hi,
I have been using the native xorg drivers for my videoo card in my notebook because it supported direct rendering when I typed "glxinfo | grep direct" in terminal.  I have used Beryl and Compiz-Fusion because of this.  However, I had a recent crash of Beryl and now I have lost support for Direct Rendering.  When I type in glxinfo | grep direct, direct rendering is NO.  

Any suggestions?

---

### Post by bdtgp on 2007-07-13
In your xorg file under the device section for your video card do you have the line:
```
Option "RenderAccel" "True"
```

I'm not sure if that's direct rendering, to be honest, but its worth a shot.

---

