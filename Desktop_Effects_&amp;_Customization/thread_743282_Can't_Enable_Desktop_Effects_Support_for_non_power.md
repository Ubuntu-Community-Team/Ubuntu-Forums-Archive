---
title: "Can't Enable Desktop Effects: Support for non power of two textures missing?"
date: 2008-04-02
forum: Desktop Effects &amp; Customization
---

### Post by harbertc on 2008-04-02
Sorry for the post being so close to the other threads, but I've tried following all the articles I can find and nothing has worked so far.

I HAD the visual effects working after a fresh install of Gutsy. But in an attempt to update my video driver so Google Earth would work, I've broken things.

Here's my card information...

$ lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

Compiz outputs the following...

$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator

When I try to enable normal visual effects, Compiz bombs out with...

/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

---

### Post by harbertc on 2008-04-03
It wound up being faster to just re-install the OS.

---

### Post by phirestalker on 2008-04-26
I am also having the exact same problem, it may have something to do with me having my resolution at an equivalent of 1080p on my television through hdmi. I would like to know how to resolve the problem because without effects enabled the desktop runs SLOOOOW (go figure?).

Thanks

---

