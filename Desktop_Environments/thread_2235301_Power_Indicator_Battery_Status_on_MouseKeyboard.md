---
title: "Power Indicator Battery Status on Mouse/Keyboard"
date: 2014-07-20
forum: Desktop Environments
---

### Post by ter062424 on 2014-07-20
Hello all,

I have an Apple MagicMouse and wireless keyboard that I've paired to my Ubuntu laptop.  They work perfectly, however the power indicator does not show their batteries correctly.  It looks like UPower doesn't really know what these are and lists them as having rechargeable batteries that are at 0%.  What transpires is that each time I boot up, I get ugly warnings saying that my mouse/keyboard batteries are dead and notifications doing likewise.

If UPower cannot understand these, that is fine and hopefully one day it'll be updated.  However, in the interim is there a way to just get rid of the power indicators while still retaining it for my laptop battery?  I even tried using XFCE Power Manager but it looks like the root issue is with UPower.  Let me know if any additional information is needed and I'll be glad to supply it.

Thanks,
Tom

---

### Post by rick-ucker on 2015-06-07
I have this issue as well. Someone opened a bug report over on Launchpad about this and even submitted a patch, but there hasn't been any activity lately. 

It was requested that the reporter file a bug upstream, but it looks like he never did. So today, I reported [upstream bug #90886]("http://bugs.freedesktop.org/show_bug.cgi?id=90886") against UPower.

if you have a Launchpad account, you might want to visit the original LP bug report and click the "does it affect you?" link: [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/1245287](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/1245287)

---

