---
title: "how to see what made my wireless work"
date: 2008-11-11
forum: Desktop Environments
---

### Post by cli168 on 2008-11-11
I was trying to get my netgear wireless card to work with Fedora core 6, without success.  When I try it with Ubuntu, it recognized  the card and everything worked.  Is there a way to see what made it  work in Ubuntu and try to reproduce it in Fedora?  Mostly for my own learning...

Thanks.

---

### Post by ohzopants on 2008-11-14
As far as I can tell success with wireless in linux is strongly linked to the alignment of the planets and the birth rate of pixies.  It's all very magical and sketchy.

Seriously though, recently my wireless started working beautifully since I started using the hal branch of madwifi ([http://madwifi-project.org/browser/madwifi/branches/madwifi-hal-0.10.5.6](http://madwifi-project.org/browser/madwifi/branches/madwifi-hal-0.10.5.6)).  I *believe* that 8.10 ships with this version included, whereas fedora might not.

The first place I would look for differences between fedora and ubuntu for wireless success is the versions of the kernel and madwifi.

---

