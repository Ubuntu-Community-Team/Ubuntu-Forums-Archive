---
title: "Video Playback and CheckGmail Slowness With Compiz"
date: 2007-10-15
forum: Desktop Effects &amp; Customization
---

### Post by yochaigal on 2007-10-15
Hi. After upgrading to Gutsy I've been having this weird issue with compiz enabled:

If I get an e-mail while playing a video full screen, and checkgmail tries to notify me, the whole system freezes up.  The video playback stops (not the audio), then the whole system locks up until the mail notification box goes away (albeit slowly).  

This makes watching movies while connected to gmail very very annoying.

I posted this in launchpad thinking it was a checkgmail issue... which it may not be.

My impression is that it has something to do with an nvidia drivers update or a linux-restricted-modules update.  

Anyone?

Oh an one more thing:  occasionally my video playback is very bad, like fuzzy colored lines.  I saw some other posts about this same issue but I'm not sure if it's related to the checkgmail.

Thanks

---

### Post by linuxwizard on 2007-10-17
This is 1 issue what else is effected with it.

CheckGmail and XGL/Compiz
Not being able to use the action links for each mail message is a known issue with XGL/Compiz/Beryl/etc. The problem stems from the popup window losing focus when the eventbox is clicked, causing the popup to close before the action is carried out. There may be a fix up soon, although I don't actually have a system which can run XGL and as such it's hard to debug.

[http://checkgmail.sourceforge.net/#faq](http://checkgmail.sourceforge.net/#faq)

---

