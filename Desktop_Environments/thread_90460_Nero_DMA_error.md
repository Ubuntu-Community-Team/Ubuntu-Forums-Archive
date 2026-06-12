---
title: "Nero DMA error"
date: 2005-11-15
forum: Desktop Environments
---

### Post by smoshe on 2005-11-15
Just installed the native linux version of Nero on my new breezy box.

When I start up, it gives me an error telling me that neither of my cd writer drives have DMA acceleration set up. I looked everywhere, but can't seem to find any documentation on how to do this.

Any ideas?

Thanks

---

### Post by uberlinux on 2005-11-15
hdparm -d1 /dev/yourdrives

p.s.  k3b is 1,000,000,000,000,000,872 times better than nero.  Ask me how to do anything in it and its easier. And 100% free too.

---

### Post by smoshe on 2005-11-15
Awesome!
Thanks for the config help.

I generally, agree but have been experiencing issues with it since I upgraded ubuntu from Hoary to Breezy. ISO files I've been using for years are suddenly unbootable when burned. Tried everything I could think of. Up and down graded k3b and every componant I could pin point (seems like half of KDE). Recompiled it from the source several times. Even went so far as to try to debug it. Then I heard Ahead released a native version of NBR for Linux in Debian package format. I admit, I don't like it as much as K3b in many respects, but it works, at least until I can get this figured out.

---

