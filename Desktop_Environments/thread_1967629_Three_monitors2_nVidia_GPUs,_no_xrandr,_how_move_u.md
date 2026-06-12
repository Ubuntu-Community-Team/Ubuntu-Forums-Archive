---
title: "Three monitors/2 nVidia GPUs, no xrandr, how move unity launcher?"
date: 2012-04-28
forum: Desktop Environments
---

### Post by rahaydenuk on 2012-04-28
Hi,

I'm running 12.04.

I have two nVidia GPUs, one of which has two monitors connected to it and another with one. I have them setup as all being on separate xscreens, using xinerama to join all 3 of them. This breaks the nice effects but I don't believe there is a better option, and I am, for the most part prepared to live with this (although I think it's ridiculous it hasn't been fixed yet!).

My problem is that the unity launcher is on the wrong monitor. The "display" applet in settings doesn't work because nvidia seems to block the xrandr extension when xinerama is enabled. I therefore cannot use xrandr on the commandline to change the default xscreen either. My question then is how do I move the unity launcher to a different screen? All responses to this query on Google seem to suggest using xrandr which, as I mentioned, is not an option for me.

Thanks,

Richard.

---

### Post by rahaydenuk on 2012-04-28
OK I was able to resolve this by changing the Screen indexes in the ServerLayout block of xorg.conf. Screen 0 is the default.

---

