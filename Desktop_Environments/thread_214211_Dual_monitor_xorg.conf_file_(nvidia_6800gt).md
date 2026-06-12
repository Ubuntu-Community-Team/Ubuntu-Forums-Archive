---
title: "Dual monitor xorg.conf file (nvidia 6800gt)"
date: 2006-07-12
forum: Desktop Environments
---

### Post by RoyB (Aus) on 2006-07-12
I'm hoping that one of you fine people has a working xorg.conf file that supports an Nvidia 6800 GT that has two monitors (with different max resolution) connected.

I hope to configure something like the nvidia "Dualview" mode where the two monitors (Viewsonic 2030B, 1600X1200) and hp1730 (1280x1024) operate as a common desktop.

I've slogged through everything I can find on the web but at this point have given up in frustration.

I'm happy to adjust a working version with different resolutions.  The part I don't understand is how to let X know that both monitors are on one card with differing resolutions - and also how to tell the driver I want to operate in Dualview mode.

Thanks in advance.

---

### Post by rquint on 2006-07-12
Take a look at 

[http://www.ublug.org/fedora/twinview/twinview-howto-fedora.html](http://www.ublug.org/fedora/twinview/twinview-howto-fedora.html)

It helped me.

---

### Post by hurrrtin on 2006-07-12
I had a hard time setting up dualview for my tv-out. But after much playing and trying, I came up with a xorg.conf file that works! I have attached my working config; its set up for tv-out, with the resolution for the tv being 800x600 though. You should be able to play with this file and make it work for your setup. This of course assumes you have the nVidia drivers set up...

---

