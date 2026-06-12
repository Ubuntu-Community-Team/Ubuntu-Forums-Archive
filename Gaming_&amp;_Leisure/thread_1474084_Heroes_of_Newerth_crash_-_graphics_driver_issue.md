---
title: "Heroes of Newerth crash - graphics driver issue?"
date: 2010-05-05
forum: Gaming &amp; Leisure
---

### Post by ShadowMage on 2010-05-05
Hey everyone,

First, I wasn't sure where to post this, so I'm sorry if this is not the right place.

Okay, so I'm trying to get Heroes of Newerth open beta to work in Ubuntu (Lucid Lynx 64-bit). The game has installed, successfully updated to latest patch, etc. I can login and everything, but any time I try to play a match or even the tutorial, the game crashes as soon as it loads.

On the same machine, everything works in Windows 7. After doing some googling it seems like it might have something to do with my graphics driver.

Here is some information regarding my graphics card:
```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```So, do I need a newer version of xserver-xorg-video-intel? Is this a package that gets updated in the Ubuntu repositories or do I  need to add a source in order to receive any updates for it?

Thanks in advance for any help.

P.S.: I've also attached the full output of lspci

---

### Post by ShadowMage on 2010-05-07
Forgot to mention, the version I have for xserver-xorg-video-intel is 2:2.9.1-3ubuntu5.

---

### Post by ShadowMage on 2010-05-08
Nevermind, looks like I figured out what the problem was. Apparently this graphics issue has something to do with shaders. So I was playing around with the in-game graphics settings... setting Shader Quality to Low seemed to do the trick.

Options -> Graphics -> Shader Quality: Low

Of course, this doesn't "fix" the shader issue itself but now the game doesn't crash anymore. I have marked this thread as solved. :)

---

