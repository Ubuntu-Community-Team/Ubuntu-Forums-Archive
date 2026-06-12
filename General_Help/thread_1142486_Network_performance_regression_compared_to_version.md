---
title: "Network performance regression compared to version 8.10?"
date: 2009-04-29
forum: General Help
---

### Post by amn108 on 2009-04-29
Hi all,

I had been running Ubuntu 8.10 x86 32-bit on my Thinkpad T41 laptop with a Intel Wireless 2200ABG card using the supplied default ipw2200 driver. I have a somewhat weak router, meaning it goes down (hangs) if there are too many connections to keep up or something, have not figured what exactly causes it to loose its mind. In 8.10 it hanged usually if Transmission (BitTorrent client) had too many connections up, and reducing simultaneous peers and connections per peer helped a lot. Other than that my connection to the router worked fine, with surfing and streaming videos and all..

I have now upgraded (clean install) to the newer 9.04 version, and have immediately noticed that webpages do not respond as swiftly as they used to with the old version. The throughput of the network however seems to be the same, i.e. only lag and delays are noticeably higher, or something.

The bigger problem is however that now with the new version my router goes down pretty much even with streaming videos and sometimes just surfing too hard. This was not an issue before at all.

I am suspecting folks at Canonical have tweaked some network settings, probably to improve things, but in my case the situation seems to have regressed.

What settings and where can I tweak manually to test what is causing the problem and hopefully rectify this? I am not sure whether this is the ipw2200 driver settings or kernel's TCP stack, or both.

---

