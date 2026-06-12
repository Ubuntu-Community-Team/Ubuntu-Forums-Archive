---
title: "Display and mouse freeze, while sound continues to work. restarting gdm fixes it."
date: 2009-08-29
forum: Desktop Environments
---

### Post by Jawher on 2009-08-29
Hi all,
  I have Ubuntu Jaunty installed with all updates, my kernel version is (as yielded by 'uname -r') 2.6.28-15-generic. My graphic card is nvidia GeForce 8400 and I've installed the non free driver version 180.44.

  I'm experiencing an annoying problem : at random time, once in a day I guess, the display and the mouse freeze, whereas the sound continues to play. The display stays at the last desktop state (meaning that it does not turn black or garbage colors).

  the only resort that I've found is to restart gdm : switch to a console (ctrl + alt + f1 for example), then 'sudo killall gdm' and 'sudo gdm'.

  I've been using Jaunty since it's release last April, and this problem showed up only a couple of weeks back ... can't be more precise, sorry. I guess an update messed the things up.

  I googled a bit about this problem, and I've found a post suggesting that this was caused by some themes, but resetting to the default theme didn't help.

Thanks in advance.

---

