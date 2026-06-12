---
title: "slow startup of leightweight window mamangers since karmic"
date: 2010-01-10
forum: Desktop Environments
---

### Post by anigel on 2010-01-10
Hi,

Since I upgraded in Karmic, I met a very strang problem using light window mamangers like fluxbox or fvwm : startup is very very slow (at least as long as loading gnome !).

I checked a lot of aspects of the system, but found nothing to explane this...

Anyone can help me please ?

Thanks !

---

### Post by HandyAndy on 2010-01-10
I assume you mean startup between login and a fully loaded desktop.

I use fluxbox with karmic and I don't have that problem.

I know that isn't much help, but it does tell you that it's not a universally experienced issue and so must relate to something in your particular set-up.

Is there anything new or unusual in your *~/.fluxbox/startup* file?

Good luck with resolving it. Fluxbox is a joy to use and fast startup is one of its virtues.

---

### Post by anigel on 2010-01-10
Hmmm...

Very strange : it has always been the case since I migrated to Karmic. I recently tried to re-install a fresh karmic : same issue, without any custom change, on a less-than an hour karmic install...

Really I don't understand... :(

---

### Post by bcrowell on 2010-01-15
Anigel, try this: [http://ubuntuforums.org/showthread.php?t=1382348](http://ubuntuforums.org/showthread.php?t=1382348)

I run fluxbox, had the same problem, and this fixed it for me. If it fixes it for you as well, please use launchpad to let the xsplash developers know that it is affecting you: [https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/504403](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/504403)

---

